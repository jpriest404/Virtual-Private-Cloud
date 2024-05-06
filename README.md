![image](https://github.com/jpriest404/Virtual-Private-Cloud/assets/156021422/3b912efa-a796-4b40-8bd3-ee23944090b3)  

# AWS Virtual Private Cloud using NAC, Bastion, and Security Groups. 

This guide will walk you through the process of setting up an Amazon Web Services (AWS) Virtual Private Cloud (VPC) in the Ohio region. We will also cover the creation of subnets, EC2 instances, and an RDS instance within this VPC.

## Establish a new VPC

First, establish a new VPC. This will provide a virtual network environment where we can launch AWS resources.

## Create a Subnet

Next, create a fresh subnet within the newly created VPC. This will allow logically isolate sections of the VPC.

## DNS Hostnames and Public IP

Enable the assignment of DNS hostnames for the VPC and configure the public IP address for the subnet within the VPC. This allows the instances to communicate with each other and the internet.

## Internet Gateway

Construct an Internet Gateway and associate it with the VPC. This provides a path for our instances to access the internet.

## Route Tables

Amend the route tables to facilitate the flow of traffic destined for the internet. This ensures that the instances can reach the internet and that the internet can reach our instances.

## EC2 Instance

Initiate an EC2 Instance within the new VPC. This will serve as the server.

## Connectivity and Apache2

After the EC2 instance is up and running, evaluate its connectivity and install Apache2 on the server. This will allow host web pages on our server.

## Security Groups

Modify the security groups to allow traffic into our instance. This ensures that the server can receive incoming connections.

## Amazon RDS Instance

Create an Amazon RDS Instance. This will serve as the database server.

## MySQL Database

Create a MySQL database that listens on port 3306 on the RDS instance. This will allow storage and retrieval of data.

## Secure Communication

Establish secure communication between the Amazon EC2 Instance and the Amazon RDS Instance. This ensures data remains secure while in transit.

## Database Inbound Rules

Configure the database inbound rules for the security group server. This will allow the EC2 instance to communicate with the RDS instance.

## Outbound Rules

Add an outbound rule to allow traffic to the database security group. This will allow the EC2 instance to send requests to the RDS instance.

## MySQL Client

Install the MySQL client on EC2 instance and add an outbound rule on port 80 to allow the installation of the MySQL client. This will allow the EC2 instance to interact with the MySQL database.

## Securing Traffic into a Subnet

Secure traffic into our subnet using Network Access Control Lists (NACLs). These are applied at the subnet layer and impact all instances launched in that subnet. Each rule has a priority, and rules are evaluated in order of priority. If one rule meets the request, all other rules are not evaluated.

## Connecting to Servers on the Private Subnet

Connect to servers on the private subnet using a Bastion Host. This is a secure way of connecting instances in the private subnet and is normally referred to as the jump server. We will apply OS hardening on the Bastion hosts, ensure the right security groups are applied to the Bastion host, and allow incoming traffic from select workstations to the bastion host. For high availability, deploy the AWS bastion host in each availability zone within the region.

## Private Subnet and Route Tables

Create a new subnet for our private subnet and a new route table to custom route our public subnets. Ensure the private subnet does not have any routes that allow traffic onto the internet.

## EC2 Instances in Private and Public Subnets

Launch an EC2 instance in the private and public subnets with the public subnet becoming the bastion host. Then connect to the Bastion Host and ensure the Bastion Host security group only allows traffic from our workstation.

## Secure Connection to Private Server

Connect the Bastion Host to the private server via a secure method of using ssh-port forwarding. 
**Note**: You could copy the private key file to the Bastion Host and then connect to the private server, but it is not secure. For Windows users, download the pageant tool, import the private key to pageant, and use ssh-forwarding in the PuTTY tool. Ensure inbound rules for the private server only allow SSH connections from the bastion security group. 

And that's it! You have now set up a secure AWS VPC. Happy cloud computing!
