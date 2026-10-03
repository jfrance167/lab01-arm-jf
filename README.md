# Cloud Computing Architecture Lab 1

This repository preserves my first Azure lab from the **Cloud Computing Architecture** course. It shows my early work with Azure Resource Manager templates, storage configuration, lifecycle rules, and access testing.

## What I completed

- Created an Azure resource group and StorageV2 account.
- Verified the storage-account baseline with Azure CLI.
- Enabled blob versioning and a 10-day delete-retention period.
- Created and verified a private blob container.
- Added a lifecycle rule that moves matching block blobs to Cool storage after 30 days.
- Confirmed that anonymous blob access returned `403` while a time-limited SAS request returned `200 OK`.
- Exported the deployment template and parameters for review.

## Repository contents

- `template.json` - exported ARM template for the storage account and related services.
- `parameters.json` - deployment parameter file.
- `README.md.txt` - original course notes retained for historical context.

## Course context

This is an educational lab, not a production-ready Azure architecture. The repository is intentionally retained to show the progression of my cloud skills, including the documentation and exported artifacts produced during the course.

Before reuse, review the region, resource names, network access rules, retention settings, and current Azure API versions.

## Local review and safe reuse

Clone this repository and inspect the Markdown and JSON files locally; no cloud
subscription or deployment is needed to review the coursework. These exports are
historical evidence. Empty parameter files and export placeholders, where noted
above, are not deployable templates and are deliberately preserved.

Use only an isolated subscription you own or are authorized to administer, with
a cost limit and teardown plan, for any future exercise. Review actual network
access, identities, credentials, names and API versions before deploying. Never
commit local credentials or production resource exports. See [SECURITY.md](SECURITY.md).

The retained storage export permits public-network access; private containers
still require authorization and this does not prove anonymous data access.
For a new deployment, evaluate the following storage-account properties together
with private endpoint/DNS configuration and Microsoft Entra role assignments:

```json
{
  "publicNetworkAccess": "Disabled",
  "allowSharedKeyAccess": false,
  "defaultToOAuthAuthentication": true,
  "allowBlobPublicAccess": false,
  "supportsHttpsTrafficOnly": true,
  "minimumTlsVersion": "TLS1_2"
}
```

This is a proposed hardening excerpt, not a complete deployment. Validate clients
and management access before applying it; disabling shared keys can break older
clients. The original course exports have not been rewritten or redeployed.

## Repository map

```text
lab01-arm-jf/
|-- .gitignore
|-- README.md
|-- README.md.txt
|-- SECURITY.md
|-- parameters.json
`-- template.json
```

Follow the setup and safety boundaries above before running or deploying any code.
