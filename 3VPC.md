
# Virtual Private Cloud (VPC)


A Virtual Private Cloud (VPC) is a virtual network dedicated to AWS account. It is logically isolated from other virtual networks in AWS cloud.

A virtual private cloud (VPC) is a secure isolated private cloud or network hosted within a public cloud. It is a on-demand configurable pool of shared resources allocated within a public cloud environment, providing a certain level of isolation between different organizations using the resources.

| | |
| --- | --- |
| VPC Quota | default limit |
| VPC's per region | 5 |
| Subnets per VPC | 200 |
| IPv6 & IPv4 CIDR per VPC | 5 |
| Elastic IP per region | 5 |
| Internet Gateway per region | 5 |
| Engress only IG/region | 5 |
| Carrier gateways per VPC | 1 |
| ACL per VPC | 200 |
| Rules per ACL | 20 |
| N/W interface per region | 5000 |
| Route tables per VPC | 200 |
| Entries per RT | 50 |
| VPC Security Group per region | 2500 |
| Inbound or Outbound rules per SG | 60 |
| SG per N/W interface | 5 |
| Gateway VPC endpoints per region | 20 |
| Interface and Gateway load balancer endpoints per VPC | 50 |

---

>### Components of VPC

1. ___Subnets___:
> Subnet is a range of IP addresses in your VPC. A subnet is defined by the CIDR block which is a subset of VPC CIDR blocks. Each subnet must reside within one AZ and cannot overlap other zones.

> Types of subnets according to the configurations made:
- Public subnet
- Private subnet
- VPN -only subnet

> {Other types:
- IPv4 only subnet
- Dual-stack
- IPv4 only}

2. ___IP addressing and CIDR___:
> IP addressing enables resources in VPC to communicate with each other and with resources over the internet.

> Classless Inter-Domain Routing (CIDR) notation is the way of representing an IP address and its network mask.

> An IPv4 CIDR has a four groups of upto three decimal digits, 0-255, separated by periods, followed by slash and a number from 0 to 32.
    
3. ___Implied Router and Routing Table___:
> Route table contains a set of rules called routes that are used to determine where network traffic from VPC is directed.

> We can explicitly associate a subnet with a route table, otherwise the subnet is implicitly associated with the main route table.

4. ___Internet Gateways___:
> An IG is a horizontally scaled, redundant and highly available. VPC component that allows communication between VPC and the internet.

> An IG enables resource in public subnets to connect to the internet if the resource has public IPv4 or IPv6 address.

> An IG serves two purposes; to provide a target in VPC route tables for internet routable traffic and perform network address translation (NAT) for instances that have been assigned public IPv4 addresses.

5. ___NAT Gateways___:
> A NAT Gateway is a Network Address Translation (NAT) service. NAT Gateways used for instances in a private subnets to connect to services outside VPC but external services cannot initiate a connection with those instances.

> The NAT Gateway replaces the source IP address of the instances with the IP address of the NAT gateway. For a public NAT gateway this is the elastic IP address of NAT gateway. For a private NAT gateway, this is the private IP address of NAT gateway.

> When sending response traffic to the instances, the NAT device translates the address back to original source IP address.

6. ___Elastic IP address___:

> An Elastic IP address is a static IPv4 address designed for dynamic cloud computing. An Elastic IP address assigned with any instance or network interface in VPC.

> An elastic ip is a property of n/w interface. The advantage of associating elastic IP with n/w interface instead of directly with the instance is that we can more all attributes of n/w interface to another in single step.

7. ___VPC Endpoint___:
> A VPC endpoint enables to privately connect VPC to supported AWS services, instances in VPC do not required public IP address to communicate with resources in the service. Endpoints are virtual devices.

8. ___VPC Reserved IP's___:
> There are five IP addresses are reserved by AWS from the IP range we choose for our VPC. That means first four IP addresses and the last IP address in each subnet CIDR block are not available for us to use.

>The five types of AWS reserved IP address are as follows:
- Network Address:
> This is the very first IP of the subnet CIDR.

eg: For subnet 10.0.0.0/24

The network id is 10.0.0.0

The network address is the identifier for a node or host on network.

- IP reserved for VPC Router:
> The second IP of the subnet which get reserved for the routing.

eg: For subnet 10.0.0.0/24

The Router IP is 10.0.0.1

- IP address reserved by AWS for DNS server:
> The IP address of the DNS server is the base of VPC network range plus two (i.e. 10.0.0.0 + 2 => 10.0.0.2) i.e. IP reserved for DNS server is 10.0.0.2

- IP reserved by AWS for future use:
> It is the consecutive 4th IP address from network IP that is reserved by AWS for the future use.

- Network Broadcast Address:
> The AWS do not support broadcast in a VPC, therefore it reserves this IP address.

> It is the last IP of the subnet that gets reserved by the AWS for broadcast the network.

eg: For subnet 10.0.0.0/24

The broadcast IP is 10.0.0.255

### Difference Between Security Groups and NACL

| Sr No. | Security Group | NACL |
| --- | --- | --- |
| 1. | Security group is assocaited with an EC2 instance and it is the first layer of defence. | NACL is associated with a subnet and is a second layer of defence. |
| 2. | It manages the instance traffic. | It manages the subnet traffic. |
| 3. | It is stateful, means any changes made in inbound rule will automatically reflected in the outbound rules. | It is stateless means any changes made in inbound rules will not reflect the outbound rule i.e. need to add separately. |
| 4. | It supports only "Allow" rules and by default all rules are denied. | It supports both "Allow" and "Deny" rules and by default all rules are denied. |
| 5. | Security group can be associated with one or more instances or can be combined with other security groups. | The NACL can have multiple subnets associated with it but one subnet can be bound with single NACL at time. |
| 6. | The security group evaluates all rules and finds the most permissive rule for traffic. | The NACL evaluates rules starting with the lowest numbered rule till a rule matches. |


### Difference Between Default VPC and Custom VPC

| Sr No. | Default VPC | Custom VPC |
| --- | --- | --- |
| 1. | It is a virtual network which is automatically created by AWS for its customers. | It is non-default VPC which has to be created by the user when required. |
| 2. | Default VPC is get auto assigned to EC2 instance when no VPC and subnet is selected while creating EC2 instance. | The custom VPC has to be selected manually to create instance inside it, with the appropriate subnet in VPC. |
| 3. | All subnets in default VPC have internet access by default, with corresponding route table. | The subnets in custom VPC does not have internet connectivity until it given the access. |
| 4. | Default VPC comes with an Internet Gateway included in it by default. | For the custom VPC an Internet Gateway has to be attached manually. |
| 5. | Instances in default VPC have public IP address and private IP address when it is created. | The instances in custom VPC do not get a public IP address they have only private IP address. |
| 6. | Used in launching blogs or simple website. | Used in production environment. |


### Difference Between VPC Peering Connection and Transist Gateway

| Sr No. | Peering Connection | Transist Gateway |
| --- | --- | --- |
| 1. | A VPC peering connection can connect only to two VPCs i.e. no transistive routing. | A transist gateway can make network connection between thousands of VPCs. |
| 2. | The peering connection can be complex at large scale because the number of VPC peering grows exponentially with the number of VPCs that needed to be connect. | The transist gateway removes complexity by managing multiple connections in a single place. It acts as a cloud router to simplify the network architecture. |
| 3. | VPC peering connection can connect two different VPCs in different account from different regions. (i.e. Inter region VPCs and Inter AWS account VPCs) | It cannot connect two VPC from different region directly, but possible through AWS Transist Gateway inter-region peering option. |
| 4. | The peering connection has no aggregate bandwidth limit. | The transist gateway is limited to maximum 50 Gbps bandwidth burst. |
| 5. | VPC peering connection imposes only data transfer fees. | It has hourly charges per attachments in addition to data charges. |


### Difference Between NAT Gateway and NAT Instance

| Sr No. | NAT Gateway | NAT Instance |
| --- | --- | --- |
| 1. | Highly available, high redundancy. | It uses a script to manage failover. |
| 2. | Bandwidth can scale upto 40 Gbps. | Bandwidth depends upon instance type. |
| 3. | It managed by AWS, not need to perform maintenance works. | Managed by user and has to be configured by user such as OS, updates, patches. |
| 4. | It has a software optimized for handling NAT traffic. | It has a generic AMI thats configured to perform NAT. |
| 5. | Charged depending on the number of NAT gateways and amount of data transfered through. | Charged depending on the number of NAT instances, duration of usage, and instance type and size. |
| 6. | Uniform offering; no need to decide type or size. | Suitable instance type and size, has to be choosen according to work. |
| 7. | Cannot be used as a Bastion host. | It can be used as a Bastion host. |
| 8. | Port forwarding not possible. | Can be configured manually to forward ports. |


### Transit Gateway:

- A transit gateway enables the users to attach VPCs and VPN connections in the same region and route traffic between them.
- A transit gateway works across two AWS accounts to shared it with RAM.
- Additional route tables can be created inside the transit gateway and change the VPC on VPN association to those route tables. This enables to segmentation of network. (eg. Developer VPC can be associate with one route and Production VPC with other route.)
- Transit gateway supports dynamic and static routing between VPCs and VPN connection.
- To connect two transit gateways from different region, a peering type connection can be established. Transit gateway peering attachments supports static routing only.

### Steps to create transit gaateway:

- Create multiple VPCs in same region and create subnets within each VPCs.
- Launch one instance in public subnet in one of the VPC and also launch one-one instance in private subnet of each VPC.
- Create a Transit gateway.
- To create Tansit gateway to the VPC in a region, create transit gateway attachments.
- One attachment for one VPC can be created.
- Note:- If we check on following options while creating a transit gateway -

a. Default route table association.

b. Default route table propogation.
- It automatically makes entry of each transit gateway attachment to the default route table of transit gateway and also enables the propogation for each attachment connection.
- Modify security group of each VPC and open the ports 22, 80 and all IPv4 ICMP for each other VPCs, CIDR.
- Go to route table of each VPC and make entry of transit gateway connection with CIDR of other VPCs. (Make entry of Internet Gateway in public VPC route)

eg.:-

Destination -- 192.168.0.0/24

Target -- transit gateway

- Get access of a instance in public subnet of one of the VPC and try to connect with the instances from other VPCs via ping or ssh.

### For connecting VPCs in different Regions -

- Make the same setup of VPCs, instances and Transit Gateway as mentioned above but in different regions.
- Create a Transit Gateway attachment in one of the region but now choose attachment type - peering connection and enter the id of transit gateway of the other region's transit gateway.
- Go to the other region transit gateway attachments and accept the peering request.
- Modify the route tables of both transit gateways

eg:-

a. For TG-1 - Create a static route for TG-2 i.e. 10.0.0.0/16

b. For TG-2 - Create static route for TG-1 i.e. 192.168.0.0/16

In both cases, choose destination as other VPC CIDR and choose target -> as peering connection.

Route Type -> Static

i.e. Destination -> CIDR of other VPC

Target -> Peering Connection
- Now try to connect with private instances from public instance.

### Difference Between DOS and DDOS

| Sr No. | DOS | DDOS |
| --- | --- | --- |
| 1. | DOS stands for Denial of Service. | DDOS stands for Distributed Denial of Service. |
| 2. | In DOS, single system targets the victim system from a place. | In DDOS, multiple systems attacks the victim system from multiple places. |
| 3. | DOS attack is slower as compared to DDOS attack. | DDOS attack is faster than the DOS attack. |
| 4. | DOS can be easily blocked as only one system is used. | It is difficult to block a DDOS attack as multiple devices sends packets from multiple locations. |
| 5. | Types of DOS attacks - a) Buffer overflow        b) Ping of Death/ ICMP flood.   c) Teardrop attack. | Types of DDOS attacks- a) Volumetric attack       b) Fragmentation attack         c) Application Layer attack. |

