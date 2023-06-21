# ELA 2023 - Virtual Machine Template

This Bicep module is used to deploy a virtual machine (VM) in Azure. It creates the necessary resources such as a public IP address, network security group, network interface, and the virtual machine itself. The file defines several parameters that can be customized during deployment.

## Prerequisites
- Azure subscription
- Bicep CLI installed

## Deployment Steps
This is an Azure Bicep module, which is created for use in higher level deployments.

## Parameters
- `VMName` (string): The name of the virtual machine.
- `VNETName` (string): The name of the virtual network.
- `subnetName` (string): The name of the subnet within the virtual network.
- `networkRG` (string): The name of the resource group where the virtual network is located.
- `VMSize` (string): The size of the virtual machine.
- `location` (string): The Azure region where the resources will be deployed.
- `localAdminUser` (string): The local administrator username for the virtual machine.
- `localAdminPasswd` (string): The local administrator password for the virtual machine.

## Resources

### Public IP Address
A public IP address is created with the following properties:
- `name`: The name of the public IP address.
- `location`: The Azure region where the public IP address is created.
- `properties.publicIPAddressVersion`: The IP address version (IPv4).
- `properties.publicIPAllocationMethod`: The IP allocation method (Dynamic).
- `sku.name`: The SKU name of the public IP address (Basic).

### Network Security Group
A network security group is created with the following properties:
- `name`: The name of the network security group.
- `location`: The Azure region where the network security group is created.
- `properties.securityRules`: A security rule allowing inbound RDP (Remote Desktop Protocol) traffic is defined with the following properties:
  - `name`: The name of the security rule.
  - `properties.access`: The access rule for the security rule (Allow).
  - `properties.destinationAddressPrefix`: The destination address prefix for the security rule (*).
  - `properties.destinationPortRange`: The destination port range for the security rule (3389).
  - `properties.protocol`: The protocol for the security rule (*).
  - `properties.sourceAddressPrefix`: The source address prefix for the security rule (*).
  - `properties.sourcePortRange`: The source port range for the security rule (*).
  - `properties.direction`: The direction for the security rule (Inbound).
  - `properties.priority`: The priority of the security rule (100).

### Network Interface
A network interface is created with the following properties:
- `name`: The name of the network interface.
- `location`: The Azure region where the network interface is created.
- `properties.ipConfigurations`: An IP configuration is defined with the following properties:
  - `name`: The name of the IP configuration.
  - `properties.privateIPAllocationMethod`: The private IP allocation method (Dynamic).
  - `properties.publicIPAddress.id`: The ID of the associated public IP address.
  - `properties.subnet.id`: The ID of the subnet where the network interface is connected.

### Virtual Machine
A virtual machine is created with the following properties:
- `name`: The name of the virtual machine.
- `location`: The Azure region where the virtual machine is created.
- `properties.osProfile`: The OS profile of the

 virtual machine, including the administrator username, password, and computer name.
- `properties.hardwareProfile.vmSize`: The size of the virtual machine.
- `properties.storageProfile`: The storage profile of the virtual machine, including the image reference and OS disk settings.
- `properties.networkProfile.networkInterfaces`: The network interfaces associated with the virtual machine.

## Customizations
- You can modify the properties of the `pubIP` resource to change the public IP address configuration.
- Adjust the properties of the `NSG` resource to modify the network security rules.
- Customize the properties of the `netif` resource to configure the network interface settings.
- Update the `VM` resource properties to customize the virtual machine configuration.

Note: This README provides an overview of the Bicep file and its resources. Make sure to customize the parameters and resources according to your specific requirements before deployment.