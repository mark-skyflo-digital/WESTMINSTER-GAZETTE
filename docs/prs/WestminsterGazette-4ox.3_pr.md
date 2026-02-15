# PR Title
WestminsterGazette-4ox.3: pull PSS model objects and field inventory

# Summary
This PR pulls the current Public Sector Solutions (PSS) object model from the connected `WestminsterGazette` org into source control and updates the local PSS inventory artifacts.

## What was added/updated
- Updated PSS package manifest:
  - `manifest/pss-model.xml`
- Refreshed inventory outputs:
  - `docs/pss-inventory/pss_objects.csv`
  - `docs/pss-inventory/pss_fields.csv`
  - `docs/pss-inventory/pss_candidate_objects.txt`
  - `docs/pss-inventory/pss_retrieve_result.json`
  - `docs/pss-inventory/describes/*.describe.json`
- Pulled retrieved source metadata for PSS objects into:
  - `force-app/main/default/objects/PublicSector__*`
  - `force-app/main/default/objects/sfsp__*`

## Notable handling
- Manifest excludes non-retrievable managed members (`sfsp__Secret__mdt`, `sfsp__Setting__c`) to keep retrieval clean.

## Why
- Aligns the repo with the actual installed PSS model in the connected org.
- Enables downstream MVP stories to reference real object/field APIs from source.

## Validation
- `sf project retrieve start -o WestminsterGazette -x manifest/pss-model.xml --ignore-conflicts`
- Retrieve completed without manifest errors after excluding non-retrievable members.

## Impact
- Large metadata sync (managed object definitions + fields) and inventory refresh.
- No business logic changes.
