# Essential Energy

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

**Areas:** Energy · Australia · Utilities · Electricity · Grid · Network Distributor · Open Data · GIS · DER · Hosting Capacity · EV Charging · Renewables

## Essential Energy on APIs.io

Everything profiled for Essential Energy is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/essential-energy/](https://apis.io/providers/essential-energy/)** — or go straight to one of the APIs or properties below.

### APIs (3)

- [Essential Energy Network Asset Feature Services](https://apis.io/apis/essential-energy/essential-energy-network-asset-feature-services/) — Anonymous, key-free ArcGIS REST FeatureServer endpoints publishing Essential Energy's physical distribution network as queryable geospatial features — poles…
- [Essential Energy Hosting Capacity Feature Services](https://apis.io/apis/essential-energy/essential-energy-hosting-capacity-feature-services/) — Anonymous ArcGIS REST FeatureServer endpoints publishing Essential Energy's distributed energy resource hosting capacity — how much generation (GEN) and…
- [Essential Energy Network Planning and DAPR Feature Services](https://apis.io/apis/essential-energy/essential-energy-network-planning-feature-services/) — Anonymous ArcGIS REST FeatureServer tables and layers publishing Essential Energy's regulated network planning data — zone substation summer and winter…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Essential Energy Agentic Access](https://apis.io/agentic-access/essential-energy/essential-energy-agentic-access/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Essential Energy network data dictionary Vocabulary](https://apis.io/vocabularies/essential-energy/essential-energy-vocabulary/)

#### Examples (5)

Example requests and responses.

- [Essential Energy Dapr Zs Summer Query Response](https://apis.io/examples/essential-energy/essential-energy-dapr-zs-summer-query-response/)
- [Essential Energy Error Invalid Field Response](https://apis.io/examples/essential-energy/essential-energy-error-invalid-field-response/)
- [Essential Energy Hostingcapacity Gen Query Response](https://apis.io/examples/essential-energy/essential-energy-hostingcapacity-gen-query-response/)
- [Essential Energy Service Areas Geojson Response](https://apis.io/examples/essential-energy/essential-energy-service-areas-geojson-response/)
- [Essential Energy Substation Count Response](https://apis.io/examples/essential-energy/essential-energy-substation-count-response/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Essential Energy Authentication](https://apis.io/security/essential-energy/essential-energy-authentication/)
- [Essential Energy Domain Security](https://apis.io/security/essential-energy/essential-energy-domain-security/)
- [Essential Energy Vulnerability Disclosure](https://apis.io/security/essential-energy/essential-energy-vulnerability-disclosure/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.essentialenergy.com.au/)
- [Documentation](https://engage.essentialenergy.com.au/access-to-network-data)
- [Support](https://www.essentialenergy.com.au/contact-us)
- [Blog](https://www.essentialenergy.com.au/media-centre/media-release)
- [Security](https://www.essentialenergy.com.au/about-us/corporate-governance/vulnerability-disclosure-policy)
- [Terms of service](https://www.essentialenergy.com.au/termsofuse)
- [Privacy policy](https://www.essentialenergy.com.au/privacy)

## API Evangelist rating

**Kin Score 28.2** — thin · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 71.4 |
| Contract quality | 6.5 |
| Contract governance | 22.0 |
| Operational transparency | 10.5 |
| Developer ergonomics | 47.0 |
| Access clarity | 21.1 |

**Agent readiness 9.4** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | — |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |

**Regulatory alignment 25.4** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/essential-energy/](https://apis.io/providers/essential-energy/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Essential Energy: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/essential-energy/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
