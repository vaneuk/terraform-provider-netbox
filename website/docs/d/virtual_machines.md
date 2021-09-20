---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "netbox_virtual_machines Data Source - terraform-provider-netbox"
subcategory: ""
description: |-
  
---

# netbox_virtual_machines (Data Source)

Per [the docs](https://netbox.readthedocs.io/en/stable/core-functionality/virtualization/):

> A virtual machine represents a virtual compute instance hosted within a cluster. Each VM must be assigned to exactly one cluster.
> Like devices, each VM can be assigned a platform and/or functional role, and must have one of the following operational statuses assigned to it:
> 
> - Active
> - Offline
> - Planned
> - Staged
> - Failed
> - Decommissioning
> 
> Additional fields are available for annotating the vCPU count, memory (GB), and disk (GB) allocated to each VM. A VM may be allocated a partial vCPU count (e.g. 1.5 vCPU).
> Each VM may optionally be assigned to a tenant. Virtual machines may have virtual interfaces assigned to them, but do not support any physical component.

## Example Usage

```terraform
// Assumes vmw-cluster-01 exists as a cluster in Netbox
data "netbox_cluster" "vmw-cluster-01" {
    name = "vmw-cluster-01"
}

data "netbox_virtual_machine" "base-vm" {
    name_regex = "myvm-1"
    filter {
        name  = "cluster_id"
        value = data.netbox_cluster.vmw-cluster-01.id
    }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Optional

- **filter** (Block Set) (see [below for nested schema](#nestedblock--filter))
- **id** (String) The ID of this resource.
- **limit** (Number)
- **name_regex** (String) Regex string to locate the virtual machine

### Read-Only

- **vms** (List of Object) (see [below for nested schema](#nestedatt--vms))

<a id="nestedblock--filter"></a>
### Nested Schema for `filter`

Required:

- **name** (String)
- **value** (String)


<a id="nestedatt--vms"></a>
### Nested Schema for `vms`

Read-Only:

- **cluster_id** (Number)
- **comments** (String)
- **config_context** (String)
- **custom_fields** (Map of String)
- **disk_size_gb** (Number)
- **local_context_data** (String)
- **memory_mb** (Number)
- **name** (String)
- **platform_id** (Number)
- **primary_ip** (String)
- **primary_ip4** (String)
- **primary_ip6** (String)
- **role_id** (Number)
- **site_id** (Number)
- **status** (String)
- **tag_ids** (List of Number)
- **tenant_id** (Number)
- **vcpus** (Number)
- **vm_id** (Number)

