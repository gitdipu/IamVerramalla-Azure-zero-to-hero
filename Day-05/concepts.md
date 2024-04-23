# Azure Networking

## Virtual Network

A Virtual Network (VNet) in Azure is a logically isolated network that securely connects Azure resources and extends on-premises networks. Key features include:

- **Isolation**: VNets provide isolation at the network level for segmenting resources and controlling traffic.

- **Subnetting**: Divide a VNet into subnets for resource organization and traffic control.

- **Address Space**: VNets have an address space defined using CIDR notation, determining the IP address range.

## Subnets, CIDR

### Subnets

Subnets are subdivisions of a Virtual Network, allowing for better organization and traffic management.

### CIDR (Classless Inter-Domain Routing)

CIDR notation represents IP addresses and their routing prefix, specifying the range of IP addresses for a network.

## Routes and Route Tables

### Routes

Routes dictate how network traffic is directed, specifying the destination and next hop.

### Route Tables

Route Tables are collections of routes associated with subnets, enabling custom routing rules.

## Network Security Groups (NSGs)

NSGs are fundamental for Azure's network security, allowing filtering of inbound and outbound traffic. Key aspects include:

- **Rules**: NSGs define allowed or denied traffic based on source, destination, port, and protocol.

- **Default Rules**: NSGs have default rules for controlling traffic within the Virtual Network and between subnets.

- **Association**: NSGs can be associated with subnets or individual network interfaces.

## Application Security Groups (ASGs)

ASGs group Azure virtual machines based on application requirements, simplifying network security:

- **Simplification**: ASGs allow defining rules based on application roles instead of individual IP addresses.

- **Dynamic Membership**: ASGs support dynamic membership based on tags or other attributes.

- **Rule Association**: Security rules can be associated with ASGs for intuitive and scalable network security management.

## Vnet Integration

VNet integration, in the context of Azure cloud services, refers to the process of connecting an Azure service to a virtual network (VNet). This VNet provides a private network environment for your Azure resources, isolating them from the public internet.

Here's a breakdown of VNet integrations and their key points:

- **Purpose** :

Enhances security by allowing your Azure service to access resources within the VNet privately. This restricts inbound and outbound traffic to authorized sources.
Benefits:

Improved security posture for your Azure resources.
Controlled access to resources within the VNet.
Potential cost savings by minimizing reliance on public internet egress traffic.
How it Works:

- **There are two primary methods for VNet integration**:

Private Endpoints: This method creates a private IP address within your VNet for the Azure service. Your service can then interact with other resources using private IP addresses, effectively bringing the service functionally into your VNet.

Service Endpoints: This method routes traffic destined for specific Azure services (like Azure Storage) through the VNet instead of the public internet. This ensures communication only happens over the private network.

- **Important Considerations** :

VNet integration typically enables outbound connections from your Azure service to resources within the VNet. Inbound access from the internet usually requires additional configuration like public IP addresses with Network Security Groups (NSGs) for access control.

VNet integration supports connecting to various resources:

Resources in the same VNet.
Resources in peered VNets (including global peering).
On-premises networks connected through Azure ExpressRoute or VPN gateways.
- **Use Cases** :

Securely connect your Azure App Service to a private database within the VNet.
Grant access to your Azure virtual machines from resources within the VNet.
Establish private communication between Azure services and on-premises infrastructure.
By leveraging VNet integrations, you can create a more secure and controlled environment for your Azure deployments.

- **Deep Dive into VNet Integration with Examples**
VNet integration in Azure allows you to connect Azure services to a virtual network (VNet) for enhanced security and controlled communication. Here's a detailed explanation with examples:

- **Benefits**:

Improved Security: Resources within the VNet communicate privately using private IP addresses, restricting access from the public internet. This mitigates the risk of unauthorized access and potential security breaches.
Controlled Access: You can define access rules within the VNet using Network Security Groups (NSGs) to control inbound and outbound traffic for your Azure services. This allows granular control over what resources can communicate with your services.
Potential Cost Savings: By minimizing reliance on public internet egress traffic, you can potentially reduce costs associated with data transfer out of Azure.
- **Methods for VNet Integration:

- **Private Endpoints**:
Imagine you have a web app service in Azure that needs to access a private SQL database within your VNet. Here's how private endpoints enable secure communication:

A private IP address is created within your VNet specifically for the web app service.
The web app service can then connect to the SQL database using its private IP address, effectively functioning as if it were directly within the VNet.
All traffic between the web app and the database remains private within the VNet, isolated from the public internet.
- **Service Endpoints** :
Let's say you have a virtual machine (VM) in your VNet that needs to access Azure Storage. Service endpoints offer a secure routing mechanism:

You can configure service endpoints for specific Azure services within your VNet (e.g., Azure Storage).
Traffic destined for the chosen service (e.g., Storage) from your VM will be automatically routed through the VNet instead of the public internet.
This ensures that communication between your VM and Azure Storage happens securely over the private network.
- **Additional Considerations**:

VNet integration typically allows outbound connections from your Azure service to resources within the VNet. For inbound access from the internet, you might need additional configurations like:

Public IP addresses assigned to your Azure service.
Network Security Groups (NSGs) with rules to define allowed inbound traffic.
VNet integration extends connectivity beyond resources within the same VNet. You can connect to:

Resources in peered VNets (including global peering) for seamless communication across virtual networks.
On-premises networks connected through Azure ExpressRoute or VPN gateways for secure hybrid deployments.
- **Real-World Example** :

A company has a critical web application hosted as an Azure App Service. They also have a sensitive customer database stored in a private SQL database within their VNet. To ensure secure communication:

They implement a private endpoint for the web app service within the VNet.
The web app service can now access the customer database using its private IP address, ensuring all data transfer remains private.
Conclusion:

VNet integration offers a powerful approach to create a secure and controlled environment for your Azure deployments. By leveraging private endpoints and service endpoints, you can effectively isolate your Azure resources from the public internet and establish secure communication channels within your VNet or with on-premises infrastructure.
