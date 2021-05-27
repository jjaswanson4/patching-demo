# Red Hat Enterprise Linux Patching Demo
This repository contains the code to provision a demo on patching RHEL systems.

### Provisioned Components:
- A Satellite server that will do provisioning and content management
- An instance of Ansible Tower that will do orchestration and automation
- A pair of SAP HANA + S4 App servers, one "production" and one "non-production"

### Demo Features/Steps
1. Run Red Hat Insights for Red Hat Enterprise Linux to get applicable errata/open CVEs
2. Sync new content to Red Hat Satellite
3. Publish new content views to non-prodution
4. Apply all new packages to S4 app server
5. kpatch SAP HANA database server
6. Get Traces recommendations from Red Hat Satellite for S4 app server
7. Apply Traces recommendations to S4 app server
8. Re-run Red Hat Insights for Red Hat Enterprise Linux

### Requirements:
- An existing Satellite server that can provision infrastructure (compute resources set up)
- A manifest for the Satellite server that will be provisioned
- A manifest for the Ansible Tower instance that will be provisioned

### What Needs to be Provided:
Most variables are self-explanitory, however a few are omitted due to being unique to my environment, namely:
| variable_name | description |
| ------------- | ----------- |
| `dns_pass`| Password for IDM DNS server |
| `ansible_password` | Password to use for SSH access if not using keys |
| `satellite_password` | Password to use to authenticate to Satellite's API |
| `vcenter_password` | Password to be used for authentication to a VMware environment |