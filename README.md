# Hosting a Web Application on AWS
 This project is aimed at hosting a web application on AWS to ensure cost effectiveness, scalabily and high availability.
## How I built a scalable web infrastructure for a retail company
This project will take you through the step by step process I took in building a scalable, cost effective and efficient web infrastructure for SmartShop, a mid-size retail company.
### Creating VPC
Created a VPC(Virtual Priavte Cloud) for smartshop with 4 subnets, 2 public subnet and 2 private subnet in 2 AZ's(Availabilty Zone) to ensure high availability.
#### Steps
1. Logged in to my AWS console as an IAM user
2. Searched for VPC through the search bar
3. Clicked on MY VPC
4. Created a VPC using VPC and more option.
This is to ensure the creation of public and private Subnets, Internet Gateways, and Route Tables automatically.
![Image of VPC Created](/Created%20VPC.png)
### Creating NACL(Network Access Control List)
Created NACL to add a layer of security to the subnets by controlling traffic in and out of the subnets.
#### Steps
1. Searched Network ACL through the search bar.
2. Created new NACL by clicking on Create Network ACL.
3. Created NACL with inbound and outboud rules that allows SSH, HHTP, AND HTTPs traffic.
4. Associated the  created NACL to the already created subnets(public) as my server will be in a public subnet. 
![image of created NACL](/New%20NACL.png)
![image of inbound rule to allow SSH and others](/NACL%20Inbound%20edited.png)
