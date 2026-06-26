## VPC Building blocks
## avalabilty zone
## sites
## VPC building blocks:
 - vpc cidr
 - subnets
 - route tables
 - internet gateway
 - ip address in vpc
 - public ip and private ip
 - Elastic ip
 - ipv6 address

## Firewall inside VPC
## Secuirty Groups and deeper dives
## NACL vs SG
## Default VPC


## Demo 

Exercise 1
1. Delete default VPC (We will create our own VPC)
2. Create VPC
a. Go to VPC service => Your VPCs => Create VPC (Name: MyVPC, CIDR: 10.100.0.0/16) => Create
3. Create Internet Gateway
a. Internet Gateways => Create internet gateway
4. Attach Internet Gateway to VPC
a. Select Internet gateway => Actions => Attach to VPC => Select your VPC
5. Create Subnet
a. Subnets => Create subnet (Name: MyVPC-Public, VPC: MyVPC, AZ: Select first AZ - ap-south-1a,
CIDR: 10.100.0.0/24)
b. Select Subnet => Action => Modify Auto Assign Public IP => Enable => Save
6. Create Route table
a. Route Tables => Create Route Table (Name: MyVPC-Public, VPC: MyVPC)
b. Select Route table => Routes => Edit => Add another route (Destination: 0.0.0.0/0, Target: Internet
gateway => igw-xxx) => Save


6. Associate Route table with Subnet to make it Public subnet
a. Select Route table => Subnet Associations => Edit => Check the MyVPC-Public subnet => Save
7. Launch EC2 instance in newly created Public Subnet
a. Go to EC2 Service => Instances
b. Launch EC2 Instance => Select Amazon Linux 2 => Select t2.micro
c. Configure Instance Details:
i. Network: MyVPC
ii. Subnet: MyVPC-Public (rest all defaults)
d. Add storage (all defaults)
e. Add Tags
i. Key=Name, Value=EC2-A
f. Configure Security Group
i. Add rule for SSH port 22 for source as MyIP
g. Review and Launch
8. Connect to EC2 instance (Public IP) from your desktop/laptop using Putty or terminal (ec2-user)

## Demo -VPC with Public and Private Subnet & exersie 

## Setup your own NAT on EC2 (NAT Instance)

## NAT Gateway and NAT Instance

## NAT Gateway with High Availability


