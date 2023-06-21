# ELA 2023 - VNET Template

This Bicep module is used to deploy a virtual network (VNet) in Azure. It creates a VNet with a subnet and allows customization of various parameters.

## Prerequisites
- Azure subscription
- Bicep CLI installed

## Deployment Steps
This is an Azure Bicep module, which is created for use in higher level deployments.

## Parameters
- `name` (string): The name of the virtual network.
- `location` (string): The Azure region where the virtual network will be created.
- `dnsServer` (string): The DNS server IP address. Leave empty for default Azure DNS servers.
- `VNETPrefix` (string): The address prefix for the virtual network.
- `SubnetName` (string): The name of the subnet within the virtual network.
- `SubnetPrefix` (string): The address prefix for the subnet.

## Resources

### Virtual Network
A virtual network resource is created with the following properties:
- `name`: The name of the virtual network.
- `location`: The Azure region where the virtual network is created.
- `properties.addressSpace.addressPrefixes`: The address prefixes for the virtual network.
- `properties.dhcpOptions`: The DHCP options for the virtual network. If `dnsServer` parameter is provided, the DNS server IP address is set.
- `properties.subnets`: A subnet is defined within the virtual network with the following properties:
  - `name`: The name of the subnet.
  - `properties.addressPrefix`: The address prefix for the subnet.

## Outputs
The Bicep file includes two outputs:
- `id` (string): The ID of the virtual network resource.
- `name` (string): The name of the virtual network resource.

## Customizations
- Modify the parameters to provide custom values for the virtual network name, location, DNS server, VNet address prefix, subnet name, and subnet address prefix.
- Adjust the properties of the `VNET` resource as needed to further customize the virtual network configuration.

Note: This README provides an overview of the Bicep file and its resources. Make sure to customize the parameters and resources according to your specific requirements before deployment.