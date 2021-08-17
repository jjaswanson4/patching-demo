# Red Hat Platform Portfolio Demo
This repository contains the code to provision a demo that spans multiple Red Hat products, use cases, and solutions. It is meant to highlight the portfolio offerings and showcase how to leverage them together to build a easily managed, highly automated landscape at scale.

### Included Use Cases
- Infrastructure as code
- Application deployment as code
- Orchestrated patching
- Lifecycle management at scale
- Red Hat + SAP "zero downtime maintenance" of SAP HANA
- SAP/S4HANA deployment using Ansible
- SAP HANA and Pacemaker
- [Red Hat Enterprise Linux Certified Ansible Collection](https://www.ansible.com/blog/announcing-the-red-hat-enterprise-linux-certified-ansible-collection)
- Red Hat Insights for Red Hat Enterprise Linux

### Provisioner
The preferred way to provision this demo is to use Red Hat Ansible Automation Platform 2.0+. There are two execution environments, one for the [provisioner](provisioner/execution-environment/execution-environment.yml) and one for the [demo playbooks](execution-environment/execution-environment.yml). These can be built using [ansible builder](https://www.ansible.com/blog/introduction-to-ansible-builder): `ansible-builder build --file path/to/execution-environment.yml`

Since the execution environment contains content from the [Red Hat Ecosystem Catalog](https://catalog.redhat.com/software/containers/explore) and the [Red Hat Automation Hub](https://www.ansible.com/products/automation-hub) (or your private instance of Automation Hub), the following pre-requisite steps should be taken:

1. Log in to the container registry with podman: `podman login registry.redhat.io`

2. Set up an [ansible configuration file](ansible.cfg.example)

Once built, the playbook [setup-demo-provisioner.yml](provisioner/setup-demo-provisioner.yml) will load inventories, hosts, groups, job templates, workflow templates, and more into the specified instance of Ansible Controller. From there, launch the workflow template `Provision Patching Demo`.

### Provisioned Components:
- A Satellite server that will do provisioning and content management
- A pair of SAP HANA + S4 App servers, one "production" and one "non-production"

### Requirements:
- An existing Satellite server that can provision infrastructure (compute resources set up)
- A manifest for the Satellite server that will be provisioned
- An instance of Ansible Controller to run the demo playbooks

### What Needs to be Provided:
Most variables are self-explanitory, however a few are omitted due to being unique to my environment, namely:
| variable_name | description |
| ------------- | ----------- |
| `dns_pass`| Password for IDM DNS server |
| `ansible_password` | Password to use for SSH access if not using keys |
| `satellite_password` | Password to use to authenticate to Satellite's API |
| `vcenter_password` | Password to be used for authentication to a VMware environment |
| `controller_password` | Password for authentication to Ansible Controller |
