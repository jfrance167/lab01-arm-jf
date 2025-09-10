CISY 5183 2025 Guided Lab 1 – Onboarding and Storage Essentials

Resource group used: rg-lab01-jf (East US)
Storage account: stjfalfreda46qghnhyiwvk (West US)

I verified the storage account baseline properties with the Azure CLI.
Blob service settings were checked: versioning is enabled, delete retention is enabled with 10 days.

I created and verified the container named docs1. It was confirmed to be private (publicAccess was None).

A lifecycle management rule called “movetocool” was added. It applies to prefix docs/, block blobs, and moves data to Cool storage after 30 days. I verified the policy JSON in Cloud Shell and it showed the rule was enabled, with the right blob type, prefix, and 30 days setting.

For access testing, I generated a SAS for one blob: “Migration Study Part 0 Organizational Assessment.docx.”
Anonymous curl tests returned 403 (as expected), while using the SAS URL returned 200 OK and confirmed access worked.

Immutability policies were not configured in this lab. Blob contents themselves were not exported.