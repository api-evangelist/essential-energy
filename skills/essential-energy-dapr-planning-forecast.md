---
name: Pull Essential Energy regulated network planning forecasts (DAPR)
description: >-
  Retrieve zone substation ratings, five-year demand forecasts, embedded generation and
  feeder-level forecasts from the Distribution Annual Planning Report tables Essential
  Energy publishes as anonymous ArcGIS REST tables.
api: Essential Energy Network Planning and DAPR Feature Services
auth: none
base_url: https://services-ap1.arcgis.com/3o0vFs4fJRsuYuBO/arcgis/rest/services
operations:
  - GET /DAPR_ZS_Summer_v2/FeatureServer/0/query
  - GET /DAPR_ZS_Winter_v2/FeatureServer/0/query
  - GET /DAPR_TX_Lines/FeatureServer/0/query
  - GET /NIP_ZS_Forecast/FeatureServer/0/query
  - GET /Distrib_Feeder_Fcasts/FeatureServer/0/query
grounding: >-
  Table ids and field names verified live 2026-07-27; recorded in
  arcgis/essential-energy-layer-field-schemas.json and
  examples/essential-energy-dapr-zs-summer-query-response.json.
generated: '2026-07-27'
method: generated
---

# DAPR planning forecast pull

The Australian Energy Regulator requires every distribution network service provider to
publish a Distribution Annual Planning Report. Essential Energy satisfies it with a
human-readable portal at <https://dapr.essentialenergy.com.au/> (no API) **and** with these
machine-queryable ArcGIS tables. The tables are the only programmatic route to the report.

## Before you call

- **No authentication.** Anonymous HTTPS GET.
- **These are Tables, not Feature Layers** — they have no geometry. Always send
  `returnGeometry=false`; requesting geometry is wasted effort.
- **`maxRecordCount` is 1000 here**, not the 2000 the asset services use.
- **Errors arrive with HTTP 200.** Check for an `error` key in the parsed body.

## The five tables

| Table | Layer id | Grain |
|---|---|---|
| `DAPR_ZS_Summer_v2` | 0 | one row per zone substation, summer |
| `DAPR_ZS_Winter_v2` | 0 | one row per zone substation, winter |
| `DAPR_TX_Lines` | 0 | one row per transmission/subtransmission feeder + season |
| `NIP_ZS_Forecast` | 0 | one row per zone substation site + season, 2025–2030 |
| `Distrib_Feeder_Fcasts` | 0 | long format: site / feeder / year / season / statistic |

Note the `_v2` suffix: `DAPR_ZS_Summer` (no suffix) is still published alongside
`DAPR_ZS_Summer_v2`. Nothing in the API marks the older one as superseded. Use `_v2` and
say which you used.

## Steps

1. **Pull the zone substation position:**

   ```
   GET /DAPR_ZS_Summer_v2/FeatureServer/0/query
     ?where=1%3D1&outFields=*&returnGeometry=false
     &resultOffset=0&resultRecordCount=1000&f=json
   ```

   Fields that matter:

   | Field | Alias | Meaning |
   |---|---|---|
   | `zonesub_id`, `zs_asset_label`, `clean_sub_name`, `Substation` | | identity |
   | `Region`, `owner`, `kV` | | context |
   | `Transformer_Rating__MVA__TX_1..TX_3` | Transformer Rating (MVA) TX.n | per-transformer rating |
   | `Firm_Normal_Cyclic_Rating__MVA_` | Firm Normal Cyclic Rating (MVA) | the firm capacity |
   | `Forecast__MVA__YR1..YR5` | Forecast (MVA) YRn | five-year demand forecast |
   | `Forecast_PF` | Forecast PF | forecast power factor |
   | `Embedded_Generation__MW_` | Embedded Generation (MW) | DER already connected |
   | `F95__Peak_Load_Exceeded___Hrs_` | 95% Peak Load Exceeded (Hrs) | utilisation duration |

   Repeat against `DAPR_ZS_Winter_v2` — in Essential Energy's inland footprint the binding
   season varies by region, so never report a single season as "the" forecast.

2. **Compute headroom** as `Firm_Normal_Cyclic_Rating__MVA_` minus the relevant
   `Forecast__MVA__YRn`. Do the arithmetic client-side; the tables do not publish it.

3. **Go down a level** with the feeder table, which is tidy long-format data and the best
   starting point for analysis:

   ```
   GET /Distrib_Feeder_Fcasts/FeatureServer/0/query
     ?where=zonesub_asset_label%3D%27<label>%27
     &outFields=site_id,zonesub_asset_label,feeder_asset_label,operating_voltage,year,season,unit,statistic,amount
     &returnGeometry=false&f=json
   ```

   Join back to the zone substation tables on `zonesub_asset_label` → `zs_asset_label`.

4. **Add the transmission view** from `DAPR_TX_Lines` (`Feeder`, `FeederVoltagekV`,
   `FeederOrigin`, `FeederDest`, `SupplyArea`, `season`, `MVA`, `F2025`–`F2029`) and the
   six-year movement view from `NIP_ZS_Forecast` (`site_id`, `season`, `F2025`–`F2030`,
   `F2025_to_2030`, `Movement`).

5. **Cross-reference DER headroom** by joining the substation names to
   `HostingCapacity_Substation_GEN` (see the hosting-capacity skill). The join is
   name-based and needs string normalisation — no shared key is published.

## Reporting

State the vintage. These tables are the annual regulatory publication cycle, not a live
feed: the year columns (`F2025`–`F2030`, `YR1`–`YR5`) are the only version marker, and
there is no changelog, no `modified` field and no deprecation notice on the superseded
`_v2` predecessors. Quote the year columns you actually read.

## Do not

- Do not treat these as real-time network state. There is no telemetry, no SCADA and no
  outage feed on this surface.
- Do not attempt writes; these services advertise `Query` only.
