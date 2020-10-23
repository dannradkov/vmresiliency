# Compute Resiliency Source Artifacts

## Azure Policy Definitions

* [Audit VM/VMSS Standalone Instances](#Audit-VM/VMSS-Standalone-Instances)
* [Audit Availability Sets With Single Instances](#Audit-Availability-Sets-With-Single-Instances)

## Audit VM/VMSS Standalone Instances

Azure policy definition to **audit standalone single instance VMs that are not protected by a SLA**. It will flag an audit event for all Virtual Machine instances that are not deployed witin an Availability Set or across Availability Zones and are not using Premium Storage for both OS and Data disks. It also encompasses both Virtual Machine and Virtual Machine Scale Set resources.

# NOTE THAT THESE ARE THE ARM TEMPLATES, NOT THE ACTUAL JSON DEFINITIONS

**Resource Types:**

* _Virtual Machines_
* _Virtual Machine Scale Sets_

**Conditional Checks:**

* _Has an expected tag provided to ignore the audit flag?_
* _Does the resource currently exist within an Availability Set?_
* _Does the resource currently have Availability Zones defined?_
* _Are Managed Disks used?_
* _Does the OS Disk use Premium storage?_
* _Are any attached Data Disks using Premium Storage?_
* _Are any attached Data Disks using Premium Storage?_

[Policy Definition](./policydefinition_Audit-VMStandaloneInstances.json)

---

## Audit Availability Sets With Single Instances

Azure policy definition to **audit Availability Sets containing single instance VMs that are not protected by a SLA**. It will flag an audit event for all Availability Sets that does not contain multiple instances.

**Resource Types:**

* _Availability Sets_

**Conditional Checks:**

* _Has an expected tag provided to ignore the audit flag?_
* _Is there more than one Virtual Machine deployed within the Availability Set?_
* _Is the resource SKU defined as Aligned?_
* _Are multiple Fault Domains assigned?_

[Policy Definition](./policydefinition_Audit-AvailabilitySetSingleInstances.json)

## Issues

* It is not possible to identify single instance VMs within Availability Zones unless a naming convention or logical groupings through Resource Groups are assumed.
# Repo description
