# Autoscaling 
autoscaling is service of aws which is used for automatic scaling of instances.

why ?

sometime lots of workload lots of traffic flow on our instances which is single instance or no of instance cant handle that  traffic we have to scale up the instances and sometime the traffic gets lesser no of instances wont needed that much so we have to scale down our instances insted of manually we have service autoscaling that we can used automatically scale up and scale down according to condition.

how ?

to create autoscaling first you have to create launch configuration or launch template 
while creating lauch configuratio there are six step after creating launch temple or configuration we will create autoscaling group  we have to mention two thingsone is autoscaling group size and second  is autoscaling policy autoscaling group size it include desire capacity minimum size and maximum size whereas autoscaling group always try to match actual capacity with desired capacity second autoscaling policy there are two types of policy incresing group policy and decresing group policy in increase group policy we create the alarm on the basis of condition. condition like when cpu utilization goes high we can give a threshold as 80% or 70% if cpu ultilization above that threeshold limit   then alarm will trigger then alarm  will create a action to inscrease no of instances  we can mention how many  instances to be increased. this is increse group policy similary we can create decrese group policy for less cpu utilization with the help of two we create autoscaling group.
