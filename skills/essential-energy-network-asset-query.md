---
name: Query Essential Energy physical network assets in an area
description: >-
  Enumerate poles, spans, transformers, substations, streetlights and service points
  within a geographic area of the Essential Energy distribution network, using the
  anonymous ArcGIS REST asset FeatureServers.
api: Essential Energy Network Asset Feature Services
auth: none
base_url: https://services-ap1.arcgis.com/3o0vFs4fJRsuYuBO/arcgis/rest/services
operations:
  - GET /arcgis/rest/services?f=json
  - GET /<service>/FeatureServer?f=json
  - GET /Substation/FeatureServer/0/query
  - GET /transformer__XFMR_/FeatureServer/29/query
  - GET /span__SPAN_/FeatureServer/10/query
  - GET /pole_timber_PTIM_/FeatureServer/0/query
  - GET /streetlight__STLT_/FeatureServer/40/query
  - GET /servicepoint__SRPT_/FeatureServer/28/query
  - GET /zonesubstationsite__ZSSS_/FeatureServer/84/query
grounding: >-
  Service names taken from arcgis/essential-energy-arcgis-services-catalog.json; layer ids
  and field names from arcgis/essential-energy-layer-field-schemas.json, both harvested
  live 2026-07-27.
generated: '2026-07-27'
method: generated
---

# Network asset query

Essential Energy publishes 100 FeatureServers covering essentially every physical asset it
owns. Use this skill for "what network infrastructure is here", asset counts, bushfire and
vegetation context, or streetlight inventories for a council area.

## The trap you must avoid

**Layer ids are per-service and arbitrary.** They are not 0 by default and they are not
sequential across the organisation: `span__SPAN_` uses layer 10, `servicepoint__SRPT_` 28,
`transformer__XFMR_` 29, `streetlight__STLT_` 40, `zonesubstationsite__ZSSS_` 84, while
`Substation` and `pole_timber_PTIM_` use 0. **Always read the FeatureServer descriptor
first:**

```
GET /<service>/FeatureServer?f=json
```

and take the ids from `layers[]` and `tables[]`. Guessing produces
`{"error":{"code":400,"message":"Invalid URL"}}` — with an HTTP 200 status line.

## Steps

1. **Find the right service.** The full catalogue is one call:

   ```
   GET https://services-ap1.arcgis.com/3o0vFs4fJRsuYuBO/arcgis/rest/services?f=json
   ```

   Naming is `<assetname>__<CODE>_`, e.g. `transformer__XFMR_`, `streetlight__STLT_`,
   `fuseset__FUSE_`, `pit__PITT_`, `tower__TWER_`. Poles are split by material:
   `pole_timber_PTIM_`, `pole_concrete_PCON_`, `pole_metal_PMET_`, `pole_composite_PCOM_`.
   Beware near-duplicates — `span__SPAN_` and `span_SPAN_` are both live, as are
   `Sub_Cables` / `Sub_Cables_R1` and `Suitable_Poles` / `Suitable_Poles_2026`. Nothing in
   the API marks which is current; prefer the higher version suffix and say that you did.

2. **Read the layer schema** to get real field names:

   ```
   GET /<service>/FeatureServer/<layerId>?f=json
   ```

   Field names are truncated ten-character shapefile-style names (`ASSET_LABE`,
   `PRIMARY_VO`, `CONSTRUCTI`, `WACS_ID_A`). They cannot be guessed. The harvested
   dictionary in `vocabulary/essential-energy-vocabulary.yml` covers 160 of them.

3. **Size the answer first:**

   ```
   GET /<service>/FeatureServer/<layerId>/query
     ?geometry=<xmin>,<ymin>,<xmax>,<ymax>&geometryType=esriGeometryEnvelope&inSR=4326
     &spatialRel=esriSpatialRelIntersects&returnCountOnly=true&f=json
   ```

   A whole-network count is also cheap: `where=1%3D1&returnCountOnly=true` on
   `Substation/FeatureServer/0` returns 144,569.

4. **Fetch the features, paging deliberately:**

   ```
   GET /<service>/FeatureServer/<layerId>/query
     ?geometry=...&geometryType=esriGeometryEnvelope&inSR=4326
     &spatialRel=esriSpatialRelIntersects
     &outFields=*&outSR=4326&resultOffset=0&resultRecordCount=1000&f=geojson
   ```

   `maxRecordCount` is 2000 on most asset services and 1000 on the planning tables — read
   it from the descriptor. Keep paging while `exceededTransferLimit` is true (top level on
   `f=json`, under `properties` on `f=geojson`).

5. **Join across layers** with the shared identifiers: `WACS_ID_A` (the asset) and
   `WACS_ID_S` (its support/site) tie spans, transformers, streetlights and service points
   back to poles; `FEEDER` ties any asset to the feeder forecasts. These are inferred from
   shared column names, not declared relationship classes — validate the join before you
   rely on it. See `data-model/essential-energy-data-model.yml`.

## Useful field notes

- `pole_timber_PTIM_` carries `BUSHFIRE_R`, `VEG_AREA`, `LANDUSE` and `M_LANDUSE` — this is
  the bushfire and vegetation-management layer as much as the asset layer.
- `streetlight__STLT_` carries `LANTERN_TY`, `NUM_LANTER`, `CONTROL_ME` and `PL_CAT_TAB` —
  the layer councils use for public-lighting inventories.
- `servicepoint__SRPT_` is the network-to-premises boundary and contains **no** customer,
  NMI or account field. `PREMISE_CO` elsewhere is a premise *count*.

## Do not

- Do not attempt writes. 97 of 100 services advertise `Query` or `Query,Extract` only.
  `Suitable_Poles` and `Suitable_Poles_2026` advertise `Query,Update,Editing` — treat them
  as read-only anyway and never send `applyEdits`.
- Do not re-publish bulk extracts as if they were an authoritative asset register; the data
  carries no currency guarantee, and `DATE_E` / the service-area `flight_yea` fields are the
  only currency signals available.
