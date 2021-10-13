# Issues
- creating compliance policy on c.rh.c is broken, follow-up with engineering. For now, use webUI

# To-Dos
- "Deploy HANA" should really just install HANA - SR and pacemaker should be a separate job
- "Meta" satellite config? perhaps map configurations based on OS - if RHEL8.4 needed for demo, auto-include those components
- linux_system_roles --> rhel_system_roles - rebuild EE
- manifests should be kept separate

# Updates to Existing Demos
- add baseline on c.rh.c to patching demo?
- IDM-AD integration demo: add RBAC to IDM based on AD groups

# New/In-Progress Demos
- satellite-as-code
- controller-as-code
- insights
- automation-hub
- pipeline integration - gitlab ci?