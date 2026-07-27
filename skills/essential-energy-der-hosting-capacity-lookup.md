---
name: Look up DER hosting capacity for a location on the Essential Energy network
description: >-
  Find how much distributed generation (solar/battery export) or load the Essential
  Energy distribution network can absorb near a given point in regional NSW, using the
  anonymous ArcGIS REST hosting-capacity services.
api: Essential Energy Hosting Capacity Feature Services
auth: none
base_url: https://services-ap1.arcgis.com/3o0vFs4fJRsuYuBO/arcgis/rest/services
operations:
  - GET /HostingCapacity_Substation_GEN/FeatureServer/1/query
  - GET /HostingCapacity_Substation_LOAD/FeatureServer/11/query
  - GET /hc_gen_hex_5km/FeatureServer/39/query
  - GET /hc_load_hex_5km/FeatureServer/35/query
  - GET /HostingCapacity_Service_Areas/FeatureServer/10/query
grounding: >-
  Layer ids and field names verified live 2026-07-27 and recorded in
  arcgis/essential-energy-layer-field-schemas.json. Essential Energy publishes no
  OpenAPI, so these are real endpoints rather than operationIds.
generated: '2026-07-27'
method: generated
---

# DER hosting capacity lookup

Use this when someone asks "can I export solar / install a battery / connect load here"
anywhere in Essential Energy's footprint (95% of NSW plus parts of southern Queensland).

## Before you call

- **No authentication.** Anonymous HTTPS GET. Do not send an Authorization header or look
  for a key — there is none.
- **Errors arrive with HTTP 200.** Parse the JSON and check for an `error` key before
  treating a response as data. See `errors/essential-energy-problem-types.yml`.
- **Layer ids are not zero-based.** `HostingCapacity_Substation_GEN` exposes layer **1**;
  `HostingCapacity_Substation_LOAD` exposes layer **11**; `HostingCapacity_Service_Areas`
  exposes layer **10**. Querying `/0/` returns `{"error":{"code":400,"message":"Invalid URL"}}`.
- **Coordinates.** The services default to Web Mercator (wkid 102100). Pass `inSR=4326`
  when you send lon/lat and `outSR=4326` when you want lon/lat back.

## Steps

1. **Confirm the location is in the footprint.** Query the service areas with the point:

   ```
   GET /HostingCapacity_Service_Areas/FeatureServer/10/query
     ?geometry=<lon>,<lat>&geometryType=esriGeometryPoint&inSR=4326
     &spatialRel=esriSpatialRelIntersects
     &outFields=area_name,code,coverage&returnGeometry=false&f=json
   ```

   An empty `features[]` means the location is outside Essential Energy's network — it is
   probably Ausgrid or Endeavour Energy territory. Stop and say so.

2. **Get the coarse picture from the hexbins.** The 5km generation grid is the fastest read:

   ```
   GET /hc_gen_hex_5km/FeatureServer/39/query
     ?geometry=<lon>,<lat>&geometryType=esriGeometryPoint&inSR=4326
     &spatialRel=esriSpatialRelIntersects&outFields=*&returnGeometry=false&f=json
   ```

   Read `sum_Firm_Spare_Capacity_kW`, `mean_Firm_Spare_Capacity_kW` and `Point_Count`
   (how many substations are aggregated into the cell). Swap in `hc_load_hex_5km`
   (layer **35**) for load. `hc_gen_hex_1km` / `hc_gen_hex_15km` and their load twins
   exist if you need a different resolution.

3. **Drill to the substations.** Buffer the point and query the substation-level layer:

   ```
   GET /HostingCapacity_Substation_GEN/FeatureServer/1/query
     ?geometry=<lon>,<lat>&geometryType=esriGeometryPoint&inSR=4326
     &distance=2000&units=esriSRUnit_Meter
     &spatialRel=esriSpatialRelIntersects&outFields=*&outSR=4326&f=json
   ```

   The fields that answer the question:

   | Field | Meaning |
   |---|---|
   | `ASSET_LABE` | Substation label |
   | `substation` / `feeder` | Names for joining to the planning tables |
   | `kVA_rating` | Substation rating |
   | `min_spare_thermal_kW` / `max_spare_thermal_kW` | The headroom numbers |
   | `capacity_label` | The published capacity band |
   | `min_constraint` / `max_constraint` | What is limiting it |
   | `PREMISE_CO` | Premises served (a count, never an identity) |

4. **Repeat for load** against `HostingCapacity_Substation_LOAD/FeatureServer/11`. Its
   fields are the GEN fields with a `_1` suffix (`min_spare_thermal_kW_1`,
   `capacity_label_1`, `feeder_1`) — an artefact of a spatial join, not a different
   vocabulary.

5. **Size before you page.** If you are sweeping a region rather than a point, run the
   same query with `returnCountOnly=true&f=json` first, then page with `resultOffset` and
   `resultRecordCount`. `maxRecordCount` on these services is 2000, and
   `exceededTransferLimit: true` in the response means there is more.

## Reporting the answer

Say plainly that these are **indicative planning figures**, published as a "Hosting
Capacity MVP" dataset, with no stated refresh cadence, no SLA and no version marker. They
do not constitute a connection offer. A real connection requires an enquiry to Essential
Energy through the Network Information Portal, not an API call.

## Do not

- Do not attempt any write. The services are read-only; `/applyEdits` returns
  "This operation is not supported."
- Do not look for customer, NMI, account or consumption data. It does not exist on this
  surface, by design — Essential Energy is a distributor and sits outside the Australian
  Consumer Data Right designation.
