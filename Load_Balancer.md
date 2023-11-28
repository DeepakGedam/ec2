# Load Balancer
Elastic load balancer is an intelligent device that handles and manages things, A load balancer takes requests from clients and distributes them across targets in a target group.

load balancer is used to distribute the traffic among multiple targets. target is nothing but target group, ip address and another load balancer.
 
Load Balancer manages the centralized domain with the help of a single DNS that accesses multiple targets.
 
It monitors the health of its registered targets, and routes traffic only to the healthy targets.
 
It is also used to divert public traffic to private traffic.

Using a load balancer increases the high availability, scalability and also fault tolerance of the applications.

## Types of load balancer
    - Classic Load Balancer
    - Application Load Balancer
    - Network Load Balancer
    - Gateway Load Balancer
 
## Working Algorithm of Load Balancer
  >___`Round robin form`___ --> sequential request distribution . distribute the traffic one by one among targets.
 
  >___`Least connection`___ --> first checkout/search the servers whose CPU and Memory utilization is less then distribute the traffic as per less cpu and memory utilization.
 
  >___`IP hash`___ --> In that type LB can manage or distribute the traffic on the server with the help of an ip address.
 
  * To create a load balancer we required target Each target group is used to route requests to one or more registered targets. When you create each listener rule, you specify a target group and conditions. When a rule condition is met, traffic is forwarded to the corresponding target group.
  * 
