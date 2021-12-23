# Multi-tenancy Incident Response Solution Pack v1.0.0

## Overview

This article describes the FortiSOAR™ Incident Response Solution Pack (solution-pack-multi-tenancy) for Managed Security Service Providers (MSSPs). This solution pack enables users to experience the power and capability of FortiSOAR™ incident response in a multi-tenant architecture.

## Prerequisites

- Deploy the MSSP IR Solution Pack. However, before you deploy the MSSP IR Solution Pack, ensure that you have deployed the FortiSOAR™ Incident Response Solution Pack ([solution-pack-incident-response](https://github.com/fortinet-fortisoar/solution-pack-incident-response)). The steps for deploying a solution pack are mentioned in the [Deploying a Solution Pack](https://github.com/fortinet-fortisoar/how-tos/blob/main/DeployingASolutionPack.md) article.  
  **Important**: You must import the MSSP IR solution pack zip on both the 'Master' and the 'Tenant' nodes.


Once you have completed installing the MSSP IR Solution Pack, you can choose to import other Solution Packs (using the same steps mentioned in the "Deploying a Solution Pack article") based on your requirements:

- [solution-pack-mitre-attack](https://github.com/fortinet-fortisoar/solution-pack-mitre-attack)
- [solution-pack-symantec-solutions](https://github.com/fortinet-fortisoar/solution-pack-symantec-solutions)
- [solution-pack-knowledge-base](https://github.com/fortinet-fortisoar/solution-pack-knowledge-base)
- [solution-pack-vulnerability-management](https://github.com/fortinet-fortisoar/solution-pack-vulnerability-management)
- [solution-pack-soc-simulator](https://github.com/fortinet-fortisoar/solution-pack-soc-simulator)

## Configuring MSSP IR Solution Pack

1. Enable the remote execution flag for all the playbooks in *05-Actions (Remote)* collection on the Tenant systems by executing the “Enable Remote Execution Flag(Tenant Only)” playbook as follows:
    1. Open the FortiSOAR Tenant instance,and from the navigation panel, click the **Alerts** module.
    2. Click **Execute** and then select **Enable Remote Execution Flag (Tenant Only)**.  
       **Important**: Before you execute the “Enable Remote Execution Flag (Tenant Only)” playbook, ensure that there is no “Playbook Mappings” in “Remote Tenant Manager” under “Multitenancy Section” on the Master node.   
        ![Remote Tenant Manager](media/remoteTenantMngr.png)  
       After the “Enable Remote Execution Flag (Tenant Only)” playbook is executed, you will notice that “Playbook Mappings” is added in “Remote Tenant Manager” under “Multitenancy Section” on the Master node.  
        ![Manage Playbook Mapping](media/managePbMappings.png)

2. Map Aliases of remote actions playbooks on the Master node by executing the “Remote Alias Mapping (Master)” playbook as follows:
    1. From the navigation panel,click the **Alerts** module.
    2. Click **Execute** and then select **Remote Alias Mapping (Master Only)**.

3. Disable SLA Playbooks from the *08 - Case Management* collection on the Tenant (“SLA” keyword). This is required because, SLA operations on all records, i.e. records of Master or Tenant, get performed on the Master only.  

      ![Disabling SLA Playbooks](media/disbaleSLAPbs.png)

4. Define Tenant SLA by adding SLA records for the Tenant in the “SLA Templates” module on the Master.  
   ![Adding SLA Templates](media/addSLATemplates.png)