# Essential Energy (essential-energy)

Essential Energy is a New South Wales Government-owned statutory corporation and the distribution network service provider (DNSP) for 95 per cent of the geographic area of NSW plus parts of southern Queensland — the poles, wires, substations and streetlights, not the retail energy contract. Headquartered in Port Macquarie and formed in 2011 out of the restructure of Country Energy, it sits in the regulated network layer of the Australian electricity value chain alongside Ausgrid and Endeavour Energy, under Australian Energy Regulator economic regulation. Its API posture splits cleanly and the split is the finding: Essential Energy publishes NO consumer data API and NO developer portal, and it is NOT a designated data holder under the Consumer Data Right energy regime — the CDR energy obligation lands on electricity retailers and AEMO, not on distributors, and Essential Energy does not appear anywhere in the public CDR energy data-holder brand register. What it does publish, anonymously and without a key, is a genuinely open grid-data surface: an ArcGIS Online organisation exposing 100 public ArcGIS REST FeatureServers covering network assets (poles, spans, cables, transformers, substations, streetlights, service points), DER hosting capacity for generation and load, zone substation and distribution feeder forecasts from the Distribution Annual Planning Report, and EV charging suitability analysis. Open market and network data, closed consumer data.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/essential-energy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/essential-energy/refs/heads/main/apis.yml)

## Tags

- Energy
- Australia
- Utilities
- Electricity
- Grid
- Network Distributor
- Open Data
- GIS
- DER
- Hosting Capacity
- EV Charging
- Renewables
- New South Wales

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### Essential Energy Network Asset Feature Services

Anonymous, key-free ArcGIS REST FeatureServer endpoints publishing Essential Energy's physical distribution network as queryable geospatial features — poles (timber, concrete, metal, composite), spans, cables, transformers, substations, zone substation sites, streetlights and controllers, service points, switchgear, fuses, reclosers, pillars, pits, towers, cross-arms, third-party attachments and the network service-area boundaries. Every service supports the standard ArcGIS REST `/query` operation over HTTPS GET with no authentication. These are the services backing Essential Energy's public Network Information Portal map viewer.

- **Human URL:** [Network Information Portal](https://essentialenergy.maps.arcgis.com/apps/webappviewer/index.html?id=947af3fb3749427e97a4824dcbd49980)
- **Base URL:** `https://services-ap1.arcgis.com/3o0vFs4fJRsuYuBO/arcgis/rest/services`

#### Tags

- Grid
- GIS
- Network Assets
- Open Data
- Geospatial

#### Properties

- [Reference](arcgis/essential-energy-arcgis-services-catalog.json)
- [Reference](arcgis/essential-energy-ee-service-areas-featureserver.json)
- [Reference](arcgis/essential-energy-substation-featureserver.json)
- [Reference](arcgis/essential-energy-arcgis-public-items.json)
- [Reference](arcgis/essential-energy-arcgis-portal-self.json)
- [API Reference](https://developers.arcgis.com/rest/services-reference/enterprise/feature-service/)
- [Documentation](https://engage.essentialenergy.com.au/access-to-network-data)
- [Portal](https://essentialenergy.maps.arcgis.com/apps/webappviewer/index.html?id=947af3fb3749427e97a4824dcbd49980)

### Essential Energy Hosting Capacity Feature Services

Anonymous ArcGIS REST FeatureServer endpoints publishing Essential Energy's distributed energy resource hosting capacity — how much generation (GEN) and load (LOAD) the network can absorb — at substation level and as 1km, 5km and 15km hexbin aggregations, together with spare-capacity service areas and substation capacity layers. The service descriptions self-identify as "Hosting Capacity MVP – GEN dataset for Experience Builder" and "Hosting Capacity MVP – LOAD dataset for Experience Builder", and back the public network capacity map experience.

- **Human URL:** [Network Capacity Map experience](https://experience.arcgis.com/experience/9e19707948544a3285a3631d0ed576f8)
- **Base URL:** `https://services-ap1.arcgis.com/3o0vFs4fJRsuYuBO/arcgis/rest/services`

#### Tags

- DER
- Hosting Capacity
- Solar
- Grid
- Open Data

#### Properties

- [Reference](arcgis/essential-energy-hostingcapacity-substation-gen-featureserver.json)
- [Reference](arcgis/essential-energy-hostingcapacity-substation-load-featureserver.json)
- [Reference](arcgis/essential-energy-hostingcapacity-service-areas-featureserver.json)
- [Reference](arcgis/essential-energy-arcgis-services-catalog.json)
- [API Reference](https://developers.arcgis.com/rest/services-reference/enterprise/query-feature-service-layer/)
- [Portal](https://experience.arcgis.com/experience/9e19707948544a3285a3631d0ed576f8)

### Essential Energy Network Planning and DAPR Feature Services

Anonymous ArcGIS REST FeatureServer tables and layers publishing Essential Energy's regulated network planning data — zone substation summer and winter ratings and forecasts (`DAPR_ZS_Summer_v2`, `DAPR_ZS_Winter_v2`, `NIP_ZS_Forecast`), transmission line data (`DAPR_TX_Lines`) and distribution feeder forecasts (`Distrib_Feeder_Fcasts`) derived from the Distribution Annual Planning Report that the Australian Energy Regulator requires every distributor to publish, plus EV charging point-of-interest and pole-suitability analysis layers. The human-readable DAPR is separately published through a Rosetta Data Portal web application, which exposes no API of its own.

- **Human URL:** [Essential Energy DAPR — Rosetta Data Portal](https://dapr.essentialenergy.com.au/)
- **Base URL:** `https://services-ap1.arcgis.com/3o0vFs4fJRsuYuBO/arcgis/rest/services`

#### Tags

- Energy Markets
- Network Planning
- Forecasting
- EV Charging
- Open Data

#### Properties

- [Reference](arcgis/essential-energy-dapr-zs-summer-v2-featureserver.json)
- [Reference](arcgis/essential-energy-dapr-tx-lines-featureserver.json)
- [Reference](arcgis/essential-energy-distrib-feeder-fcasts-featureserver.json)
- [Reference](arcgis/essential-energy-nip-zs-forecast-featureserver.json)
- [Reference](arcgis/essential-energy-ev-pois-featureserver.json)
- [Documentation](https://dapr.essentialenergy.com.au/)
- [API Reference](https://developers.arcgis.com/rest/services-reference/enterprise/feature-service/)

## Common Properties

- [Website](https://www.essentialenergy.com.au/)
- [LinkedIn](https://www.linkedin.com/company/essential-energy)
- [Portal](https://essentialenergy.maps.arcgis.com/apps/webappviewer/index.html?id=947af3fb3749427e97a4824dcbd49980)
- [Documentation](https://engage.essentialenergy.com.au/access-to-network-data)
- [Documentation](https://dapr.essentialenergy.com.au/)
- [Reference](arcgis/essential-energy-arcgis-services-catalog.json)
- [Reference](arcgis/essential-energy-arcgis-public-items.json)
- [Reference](arcgis/essential-energy-arcgis-portal-self.json)

## Mandate Posture

| Question | Finding |
| --- | --- |
| Mandate regime | **none** — the Consumer Data Right energy regime does not reach distributors |
| Mandate status | **not-applicable** — verified absent from the public CDR energy data-holder register (84 brands, zero matches for "essential") |
| Data standard | none — no Green Button/ESPI, no CDR Consumer Data Standards, no IEC CIM; the open surface is Esri ArcGIS REST API v12 |
| Consumer data API | **No** |
| Open market/grid data | **Yes** — 100 anonymous ArcGIS REST FeatureServers |
| Access gate | **self-serve** (in practice, fully anonymous — no key, no signup) |
| Auth model | none on the public surface; `/.well-known/openid-configuration` returns 404 |
| Developer portal | none published; `developer.`, `developers.`, `api.`, `docs.`, `data.`, `opendata.` all NXDOMAIN |

Full probe log, HTTP statuses and provenance are in [`review.yml`](review.yml).

## Maintainers

- Kin Lane &lt;kin@apievangelist.com&gt;
