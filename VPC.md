# *__**Amazon EC2**__*

Amazon EC2 service provides scalable computing in the AWS Cloud. Amazon EC2 can be used to launch as many or as few virtual servers as needed. It enables users to scale up or scale down to handle changes in requirements. With Amazon EC2 service, virtual servers can be launched, configure security and networking and manage storage.

Amazon EC2 is having two storage options i.e. `EBS & instance store`. Pre-configured templates are available known as Amazon Machine Image (AMI).

 By default limit of instance per EC2 region is `maximum 20 instances` with two default high I/O instances.


## __Features of Amazon EC2__

>1. Virtual Computing Environment (Instances).
>2. Pre-configured templates for Instances (AMI) including operating system and additional software.
>3. Various configurations of CPU, memory, storage and networking capacity. (Instance types)
>4. Secure login information for instances using key pairs.
>5. Storage volumes for temporary data that deleted when instance stop, hibernate or terminates. (Known as instance store volumes).
>6. Persistent storage volumes for data using EBS volumes.
>7. Multiple physical locations for resources on AWS (known as Regions & Availability zones).
>8. A firewall that enables to specify the protocols, ports and source IP ranges that can reach EC2 instance using security groups.
>9. Static IPv4 addresses for dynamic cloud computing, known as Elastic IP addresses.
>10. Metadata, known as tags that can be created and assigned to Amazon EC2 resources.
>11. Virtual network can be created that are logically isolated from rest of the AWS cloud and that can be optinally connected to own network, known as Virtual Private Cloud (VPCs).


## __Types of EC2 Instances__

1. ___General Purpose:___
>General purpose instances provide a balance of compute, memory and networking resources and can be used for a wide range of workloads.
Ex.: `M5, M5a, M5zn, M6g and M6a, M6i, Mac, T2, T3, T3a and T4g` instances.

2. ___Compute Optimized:___
>Compute optimized instances are ideal for compute-bound applications that benefits from high performance processors.
Instances belonging to this family are well suited for batch processing workloads, media transcoding, dedicated gaming servers, high performance web servers, high performance computing (HPC), scientific modeling and other compute intensive applications.
Compute optimized type consist only C-series instances i.e. `C4, C5, C5n, C5a, C6i, C6g, C6gn, C6a`

3. ___Memory Optimized:___
>Memory optimized instances are designed to deliver fast performance for workloads that process large data sets in memory.
Features of Memory Optimized instances are real-time analytics, in-memory databases, memory intensive.
It consists of `R` series, `X` series & `Z` series.

>>___R Series:___ `R4, R5, R5a, R5b, R5n, R6i, R6g.`
- High performance Relational & NoSQL databases.
- vCPU 2 to 96 & RAM 16-768 GB.
- Storage EBS only & NVM SSD.

>>___X Series:___ `X1, X1e, X2iezn, X2iedn, X2idn, X2gd`
- High performance database
- Memory intensive enterprise application
- In memory databases such as SAP, HANA.
- vCPU 4 to 128, RAM 122 to 3904 GB.

>>Z Series: `Z1d`
- High frequency, AWS Nitro System.

4. ___Accelerated Computing:___
>Accelerated Computing instances uses hardware accelerators or co-processors to perform some functions such as floating point number calculations, graphics processing or data pattern matching, more efficiently.
`P series, G series, F series & V, I & T series`.
`P4, P3, P2, G5, G5g, G4dn, G4ad, G3, F1`

5. ___Storage Optimized:___
>Storage optimized instances are designed for workloads that require high, sequential read and write access to very large data sets on local storage. They are optimized to deliver tens of thousands of low latency, random I/O operations per second (IOPS) to applications.

>This Class has following instances:

>>__D-Series:__ `D2, D3, D3en`

>>__I-Series:__ I3, I3en, I4i, Is4gen, Im4gn

>>__H-Series:__ H1

    
## ___EC2 Instances Purchasing Options___

Amazon EC2 provides following purchasing options to enable to optimize costs based on usage needs.

a. ***On-Demand Instances:***

>Pay by the second; for the instances that you launch at fixed price. They are used for applications with short term irregular workloads that cannot be interrupted.
    The use of On-Demand instances frees you from the cost and complexities of planning purchasing and maintaining hardware.

b. ___Saving Plans:___

> It reduce EC2 cost by making commitment to consistent amount of usage in USD per hour for a term of 1 or 3 years.

c. ___Reserved Instances:___
>It reduce cost by making a commitment to a consistent instance configuration, including instance types and region for a term 1 or 3 years.

>It provide capacity reservation by purchasing in specific AZ, option to reserve a DB instance for 1 or 3 years.

>Types: Standard RI, COnvertible RI, schedule RI.

`*Q.1. Can I transfer a convertible or standard RI from one region to another?*`
>> No

`Q.2. How do you change the configuration of convertible Reserve Instance?`

>> Using EC2 management console or get reserve instance management quota API

`Q.3. Do i need to pay a fee when I exchange my convertible RI?`
>> No

d. ___Spot Instances:___
>We can request unused EC2 instances which can reduce cost significantly. Spot instances are available upto 90% discount compared to on-demand.
    
>We have option to hibernate, stop or terminate spot instance when EC2 reclaims the capacity back with two minutes of notice.

e. ___Dedicated Hosts:___
>It is physical host that is fully dedicated to running the instances. It allows to use existing  per-socket, per-core, or per-VM software licenses, such as Windows Server, Microsoft SQL Server, SUSE, and Linux Enterprise Server.

>Dedicated Host is available for the following families: T3, A1, C5, M5, R5, C5n, R5n, and M5n.

f. ___Dedicated Instances:___
>These are the instances that runs on single tenant hardware. Dedicated instances that belongs to different AWS account are physically isolated at hardware level. Dedicated instances launch only in Virtual Private Cloud (VPC).

g. ___Capacity Reservations:___
>With capacity reservation, we can reserve the capacity for the EC2 instance in specific Availability Zone for any duration.


>## EC2 Bare Metal Instances

The EC2 bare metal instances are created into non-virtualised environment.
The operating system runs directly on the hardware.
Suitable for licensing restricted tier-1 business critical applications.
Examples of Bare-Metal instances- i3 metal, i5 metal, r5 metal, Z1d metal, V-6tb1 metal.



## Hypervisor

It is a software that creates and runs virtual machines (VMs). It is sometimes called virtual machine monitor (VMM), isolates the hypervisor operating system and resources from virtual machines and enables the creation and management of those VMs.
The physical hardware, when used as a hypervisor, is called the host, while the many VMs that use its resources are called as guests.

### Types of Hypervisor

>a. Type 1:
They are referred as a native or bare metal hypervisor that  runs directly on the host’s hardware to manage guest operating systems.(Firmware hypervisor)

>b. Type 2:
They are also known as a hosted hypervisor, and is run on a conventional operating system as a software layer or application.
They are used for learning and testing purpose.


## Status Check for EC2 Instance

Amazon EC2 performs automated status checks on every running EC2 instances to identify hardware and software issues.
Status check is built into the AWS EC2 instance, they cannot be configured, deleted or disabled.

***Types of status checks involves:***
>a. ***System status check:***
>>It monitors the AWS systems on which the instances runs.

___Causes of System check fails:___
- Loss of network connectivity.
- Loss of system power.
- Software issues on the physical host.
- Hardware issues on physical host that impact network reachability.

>b. ***Instance status checks:***

>>It monitors the software and network configuration of the individual instance by sending an address resolution protocol (ARP) request to network interface (NIC). These problems must be address by users themselves.
        
***Causes of instance check fails:***

      - Failed system checks
      - Incorrect networking or startup configuration
      - Exhausted memory
      - Corrupted file system
      - Incompatible kernel


## ___Instance Metadata___

The instance metadata is used to configure or manage the instance. The instance metadata consist some important information such as IPv4, IPv6 address, DNS hostname, AMI-id, instance id, instance type, local hostname, public keys, security groups.
    Other than the AWS console and AWS CLI, the metadata can also be viewed from the running instance via

    http://169.254.169.254/latest/meta-data/     (IPv4)
                or
    http://[fd00:ec2::254]/latest/meta-data       (IPv6)

The metadata of EC2 instance is not protected by an encryption, anyone who has access to the instance on get the metadata of that instance.

### ___Instance User Data:___
___
It is the data supplied by the user at instance launch in the form of script to be executed during the instance boot.
The user data is limited to 16kb and is not encrypted.
To change user data, the instance has to be stopped first.
___


| Sr No. | Elastic Block Storage | Instance Store Volume |
| --- | --- | --- |
| 1 | Provides block level storage volume for use with EC2 instances. | Provides temporary block-level storage for EC2 instance faster than EBS. |
| 2 | It is a network attached storage (NAS) persistent in nature. | It is a Direct Attached Storage (DAS) but epumeral (volatile) in nature. |
| 3 | EBS backed EC2 instance can stopped, rebooted and terminated. As it is persistent, data can be persist on instance termination. (Optional) | The instance store backed EC2 instance can't be stopped, it only be rebooted and terminated. On termination, all data will delete permanently. |


## __AWS EC2 Launch Templates__

>Launch templates contains the configuration information to launch instance. It is used to store launch parameters so that there will be no need to specify them every time of instance launch.

>___The launch templates can contain the AMI ID, instance type and network settings, storage that are typically used to launch instances.___

>For each template, one or more numbered launch template versions can be created. Each version can have different launch parameters.

>`5000` launch templates can be created `per region` and `10,000 versions per template`. Launch templates can be tagged but versions cannot be.

___Launch templates can be created from:___

    - Parameter define
    - An existing launch templates
    - An instance
        
>Usage: To automate instance launches, simplify permission policies, Auto scaling, spot fleet, spot and on-demand instances.


> ## __EBS Snapshots__

>Snapshots are used to take backup the data on Amazon EBS volumes to Amazon S3. It is incremental backups, in which only the blocks that have changed after most recent snapshot, are saved.

>Each snapshot contains all of the information that is needed to restore data to a new EBS volume. This minimizes the cost by not duplicating data.

>EBS snapshots are point-in-time images/copies of the EBS volumes. Any data written to volume after the snapshot process initiated will not be included in resulting snapshot, but will be included in future as a incremental update.

>Per AWS account --> 5000 EBS volumes and 10,000 EBS snapshots can be created. EBS currently supports a maximum volume size of 64 TiB.

>While EBS volumes are AZ specific, snapshots are region specific. Any AZ in region can make use of snapshot to create EBS volumes.

>EBS snapshots are used to migrate an EBS volume from one AZ to another indirectly. First a volume gets snapshot and transfered to another AZ and then converted back to EBS volume from EBS snapshot.

>The volume created from snapshot is either equal or larger in size compared to that of EBS snapshot, smaller size do not get accepted.
---
### ***EBS Encryption***
---
EBS encryption is supported on all EBS volume types and all EC2 instace families.

The snapshots of encrypted volume are also encrypted.

Creating volumes from an encrypted snapshot will result in an encrypted volumes.
___



## **Elastic Load Balancer (ELB)**

A load balancer distributes workloads/traffic across multiple compute resources such as virtual servers. Using a load balancer increases the availability and fault tolerance of the applications.

Operating at the request level (Application Layer i.e. 7th layer of OSI), Application Load Balancer provides advanced routing.

>Types of Load Balancers:
    
    a. Application Load Balancer
    b. Metwork Load Balancer
    c. Gateway Load Balancer
    d. Classic Load Balancer

>Types of load distribution schemes (Algorithms):

    a. Round Robin (Alternate distribution of traffic)
    b. Least Connections
    c. Least time (Server with least time of response)
    d. Over Flow


## Difference between Application Load Balancer & Network Load Balancer

| Sr No. | Application Load Balancer | Network Load Balancer |
| --- | --- | --- |
| 1. | It performs the distribution of requests based on multiple variables from network layer to application layer. | It performs distribution of traffic based on network variables such as IP address and destination ports. |
| 2. | It works at 7th layer (i.e. Application Layer) of OSI model. | It works at 4th layer (Transport Layer) of OSI model. |
| 3. | The ALB examines the contents of HTTP request header to define route of request. | It just forwards the requests. It do not performs content based routing. |
| 4. | ALB capable of determine availability based on a successful HTTP. GET of a particular page and verification of content based on input parameters. | NLB cannot determine availability of the application because its decisions based on n/w & TCP layer variables. |
| 5. | ALB differentiate between two applications by examining application layer data available to it. | NLB do not differentiate between two applications when checking availability. (Unless ports are different)



## EC2 Autoscaling

>Amazon EC2 Auto Scaling helps to ensure that the correct number of EC2 instances available to handle the load for the application.

>There can be created collections of EC2 instances, called Auto Scaling Groups where the minimum & maximum number of instances can be specified in each group using scaling policy.

>Autoscaling enables elasticity by scaling horizontally through adding or terminating EC2 instances using the scaling policy.

### *Benefits of Autoscaling*
___
    1. Better fault tolerance
    2. Better availability
    3. Better cost management (Dynamic scaling)

### *Types of Autoscaling*
___
1. ___`Autoscaling Groups`___
>An autoscaling group contains a collection of Amazon EC2 instances that are treated as a logical groupping for the purpose of automatic scaling and management.

>An autoscaling group also enables to use EC2 autoscaling features such as health check replacements and scaling policies. The automatic scaling and maintaining no. of instances in group is a core functionality.

>The size of Auto Scaling group depends upon the number of instances that we set as a desired capacity. Auto scaling group starts by launching enough instances to neet its desired capacity.

>It maintains the desired number of instances by performing periodic health checks on instances in the group. If a instance becomes unhealthy, the group terminates it and launches another instance to replace it.

Types of Autoscaling Groups:
    a. Static
    b. Dynamic
    c. Scheduled


2. ___`Launch Templates`___

>A launch template is similar to a lauch configuration in that it specifies instance configuration information. It includes the id of AMI, the instance type, a key pair, security groups and the other parameters used to launch EC2 isntances.

>Defining a launch template instead of a launch configuration allows to have a multiple features and multiple versions of launch templates.

Key benefits of Launch Templates when used with Auto Scaling Groups:
       
    a. Support for multiple instance types and purchase options in a single Auto Scaling Group.
    b. Launching spot instances with capacity optimized allocation strategy.
    c. Support for unlimited mode for burstable performance instance.
    d. Support dedicated hosts.
    e. Combining CPU architectures such as Intel, AMD and ARM.
    f. Improved governance through IAM controls and versioning.
    g. Automating instance deployment with instance refresh.
    h. Support for launching instances into existing capacity reservations through on Auto Scaling group.

---

>### *Difference between Vertical Scaling and Horizontal Scaling*

---

| Sr No. | Vertical Scaling | Horizontal Scaling |
| --- | --- | --- |
| 1. | Vertical scaling is the adding or substracting the computing resources including memory or storage, within the server upto its full capacity. | Horizontal scaling refers to adding more servers to the network rather than adding resources in the same server to handle traffic effciently. |
| 2. | The approach is also refered as "scale up" and "scale down". | This approach is also refered as "scale out" & "scale in". |
| 3. | With vertical scaling the limited scaling of resources is possible. | Horizontal scaling allows to scaling as much as required. |
| 4. | Downtime is required for scale up and scale down resources. | No downtime is required to scale out or in as new instances are launch. |
| 5. | The vertical scaling implementation is cost expensive. | Horizontal scaling is cheaper in cost as servers reduces back. |
| 6. | Vertical scaling comes with finite upgradeability in the future. | Horizontal scaling allows greater upgradeability for the future perspectives. |
| 7. | Vertical scaling cannot manage traffic that much effectively. | Horizontal scaling can handle traffic of major workloads well effectively. |
| 8. | Vertical scaling comes with greater risk of outages and hardware failure. Because the server runs on a single hardware. | IT makes easier tovrun fault tolerance. In case of hardware failure, outages can be avoided by autoscaling group by replacing it to the new one. |
| 9. | Vertical scaling do not provide instant and continuous availability. | Horizontal scaling provides the instant and continuous availability. |
| 10. | The vertical scaling can be used in testing and research purpose and not in production environment. | The horizontal scaling is used in real world production workloads because of its greater flexibility and easy implementations. |

---

>### *Difference between Launch Template (LT) and Launch Configuration (LC)*

---

| Sr No. | Launch Template (LT) | Launch Configuration (LC) |
| --- | --- | --- |
| 1. | It is superior than Launch Configuration and provide more functionality. | It is inferior and has less functionality than launch templates. |
| 2. | LT allows to edit and update the configurations of it. | LC is immutable and do not allows to edit once it configured. |
| 3. | LT maintains its versions containing different configurations. | LC do not maintains its versioning as it is not editable again. |
| 4. | It provide functionality such as use of spot, t2 unlimited burst and dedicated hosting. | It do not provide t2 unlimited burst and dedicated hosting features. |
| 5. | It allows partial configurations for reuse and inheritance. | The launch configuration cannot be used for partial configurations. |
| 6. | The LT can be used for both launching instances from console SDK and CLI whenever required. | The LC can only be used to create instances under autoscaling groups by automated mechanism. |

---


### Placement Groups

 1. ***Cluster:***
>It is a logical grouping of instances within single AZ. It packs instances close together inside an AZ. It is used for low latency n/w performance.
    
![Cluster](https://miro.medium.com/max/500/0*dL_izC8OkbvNvtNC.png)

 2. ***Partition:***
>It spread instances across logical partitions such that groups of instance in one partition do not share the underlying h/w with groups of instances in other partitions.

![Partition](https://miro.medium.com/max/640/0*4KQ2NGzLfLa7Nh-r.png)

 3. ***Spread:***
>It strictly places a small group of instances across distinct underlying h/w to reduce co-related failures.

![Spread](https://miro.medium.com/max/720/0*Fy9htrG7a7ML7PQ_.png)


---

### *EC2 Instance Tenancies*

Tenancy defines how EC2 instances are distributed across physical hardware and affects pricing. There are three tenancy options available:
    
   1. `Shared Tenancy (default)`:
>Multiple AWS accounts may share the same physical hardware.

   2. `Dedicated Instance (dedicated)`:
>The instance in this tenancy runs on single-tenant hardware physically isolated at hardware level from other instances.

   3. `Dedicated Host (host)`:
>The instance run on a physical server with EC2 instance capacity fully dedicated to use, an isolated server with controlled configurations.


---
>### *Difference between Elasticity and Scalability*
---

| Sr No. | Elasticity | Scalability |
| --- | --- | --- |
| 1. | It is ability of a system to automatically expand or compress the infrastructural resources such as storage, networking. | Scalability refers to adoption of increase workloads on its current hardware resources. (Related to software system) |
| 2. | It is ability to match resources capable for a given workloads size. | It is ability of a system to remain responsive as the user load gradually increase. |
| 3. | Elasticity is the feature of cloud computing services to expand and compress computational resources. | Scalability is the cause by which the elasticity is achieved. |
| 4. | It makes infrastructure flexible in nature. | It helps to achieve flexibility by scaling up and down. |

---
