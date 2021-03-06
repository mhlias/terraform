---
layout: "aws"
page_title: "AWS: dc_intra_virtual_interface"
sidebar_current: "docs-aws-resource-dc-intra-virtual-interface"
description: |-
  Provides a resource to create a DirectConnect Virtual Interface to be used on a separate account from the one DirectConnect is on.
---

# aws\_dc\_intra_virtual_interface

  Provides a resource to allocate a DirectConnect Virtual Interface to be used on a separate account from the one DirectConnect is on.

## Example Usage

```
resource "aws_dc_intra_virtual_interface" "vif" {
  connection_id = "dxcon-xyz123"
  virtual_interface_name = "my-vif"
  asn = "12345"
  vlan = "1024"
  auth_key = "my_super_secret_bgp_key"
  amazon_address = "10.0.0.45/30"
  customer_address = "10.0.0.46/30"
  interface_type = "private"
  owner_account_id = "123456789"

}
```

## Argument Reference

The following arguments are supported:

* `connection_id` - (Required) The connection ID for the DirectConnect connection.
* `virtual_interface_name` - (Required) The name of the virtual interface.
* `asn` - (Required) The BGP autonomous system number.
* `vlan` - (Required) The vlan id.
* `auth_key` - (Optional) The BGP secret auth key.
* `amazon_address` - (Optional) The IP along with the subnet mask for amazon's side of the small subnet used for the 2 routers BGP communication.
* `customer_address` - (Optional) The IP along with the subnet mask for your side of the small subnet used for the 2 routers BGP communication.
* `interface_type` - (Required) The type of the virtual interface [private,public].
* `owner_account_id` - (Required) The ID of the foreign account that is going to be allocated the virtual interface.



-> **Note:** For this to actually create the virtual interface it needs to be confirmed on the account that will use it.
You can do that by using the `aws_dc_intra_virtual_interface_confirm` resource. An example is provided there how to accomplish that in a single run if desired.

## Attributes Reference

The following attributes are exported:

* `id` - The ID of virtual interface.
* `amazon_address` - The IP address for amazon's interface (when autogenerated).
* `customer_address` - The IP address for your interface (when autogenerated).



