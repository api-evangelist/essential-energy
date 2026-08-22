# Essential Energy (essential-energy)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
