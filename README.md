AWS Load Balancing Documentation
Objective
The aim of this task was to make sure our application could be accessed through a Load Balancer. A Load Balancer shares traffic between servers so that no single server becomes overloaded.

Step 1 – Create a Target Group
A Target Group is where the Load Balancer sends traffic.

Go to EC2 in the AWS Console.
Select Target Groups.
Click Create target group.
Choose Instances as the target type.
Give the target group a name ending in -tg.
Example: tech610-tg
Leave the default settings unless instructed otherwise.
Register the EC2 instances that will receive traffic.
Click Create target group.
Step 2 – Create an Application Load Balancer
The Application Load Balancer (ALB) receives requests from users and sends them to the servers in the target group.

Go to Load Balancers.
Click Create Load Balancer.
Choose Application Load Balancer.
Give the Load Balancer a name.
Select Internet-facing.
Select IPv4.
Choose all Availability Zones (Regions selected for deployment).
Attach the target group created earlier.
Click Create.
Step 3 – Create an Auto Scaling Group
An Auto Scaling Group manages the EC2 instances.

Settings used:

Health check: Elastic Load Balancer (ELB)
Desired capacity: 2 instances
Minimum capacity: 2 instances
Maximum capacity: 2 instances
Cooldown period: 90 seconds
This ensures there are always 2 running servers.

How It Works
A user visits the application.
The request goes to the Application Load Balancer.
The Load Balancer checks which server is available.
The request is sent to one of the EC2 instances in the Target Group.
If one server has a problem, the Load Balancer sends traffic to the other healthy server.
Why We Use a Load Balancer
Shares traffic between multiple servers.
Prevents one server from becoming overloaded.
Improves reliability.
Keeps the application available if one server fails.
Works together with Auto Scaling to manage EC2 instances.
Summary
Setting	Value
Load Balancer Type	Application Load Balancer (ALB)
Target Group	Created with -tg at the end of the name
Health Check	Elastic Load Balancer (ELB)
Desired Capacity	2
Minimum Capacity	2
Maximum Capacity	2
Cooldown	90 seconds
