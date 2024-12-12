# Hosting a Web Application on AWS
 This project is aimed at hosting a web application on AWS to ensure cost effectiveness, scalabily and high availability.
## How I built a scalable web infrastructure for a retail company
This project will take you through the step by step process I took in building a scalable, cost effective and efficient web infrastructure for SmartShop, a mid-size retail company.
### Creating VPC
Created a VPC(Virtual Priavte Cloud) for smartshop with 4 subnets, 2 public subnet and 2 private subnet in 2 AZ's(Availabilty Zone) to ensure high availability.
#### Steps
1. Log in to AWS console as an IAM user
2. The first thing to do for any AWS resources is to choose a region. I used North Virginia.
3. Search for VPC through the search bar
4. Click on MY VPC
5. Create a VPC using VPC and more option.
This is to ensure the creation of public and private Subnets, Internet Gateways, and Route Tables automatically.
![Image of VPC Created](/Created%20VPC.png)
### Creating NACL(Network Access Control List)
Created NACL to add a layer of security to the subnets by controlling traffic in and out of the subnets.
#### Steps
1. Search for Network ACL through the search bar.
2. Create new NACL by clicking on Create Network ACL.
3. Create NACL with inbound and outboud rules that allows SSH, HHTP, AND HTTPs traffic with rule number in ascending order(i.e 100, 101 etc).
4. Associate the  created NACL to the already created subnets(public) as the server will be in a public subnet. 
![image of created NACL](/New%20NACL.png)
![image of inbound rule to allow SSH and others](/NACL%20Inbound%20edited.png)
### Creating a Security Group
A security group was created to control traffic to and from the EC2 instance to be created. 
1. Edit Inbound rule to allow SSH and HTTP from anywhere(i.e IPV4) 
2. Leave Outbound rule at default (Allow all traffic).
![Image of created security group](/Security%20Group.png)
![Image of security group rule](/SG%20Allow%20SSH.png)
### Launching EC2 Instance
An EC2 instance was launched to host the web server(Apache)
#### Steps
1. Search for EC2 on the search bar
2. Click on launch EC2 instance.
3. Name the instance, select Amazon Linux 2 as the OS and t2micro as the instance type.
4. In the network settings, assign the previously created VPC and security group to the instance and not the default.
5. Create a keypair and save it in a folder to be used later for connecting to the instance via the terminal.
6. Set the auto assign public IP to ENABLED and configuration storage to 8gb.
7. Launch instance.
8. Instance start running once there is a 2/2 check passed.
![Image of Ec2 instance launched](/EC2.png)
### Connecting to the instance.
The instance was connected to via SSH Client on the GitBash terminal.
#### Steps
1. Click on the created instance and click on connect to connect via SSH client.
2. Go to the folder where the keypair was saved, usualy a .pem file.
3. Open the file with Gitbash. 
4. Enter this code ssh-i-"yourkey.pem" ec2-user@Public DNS on your terminal to connect.
![Image showing connecting to the isntance](/Connect%20Via%20SSH.png)
![Image showing successful connection to the instance on Gitbash](/Successful%20SSH%20via%20Gitbash.png)
### Installing Apache
Apache was installed to serve as the web server.
#### Paste this code to install apache
1. sudo yum update -y
2. sudo yum install httpd -y
3. sudo systemctl start httpd
4. sudo systemctl enable httpd
5. Copy the instance public IP address and paste it in the browser to confirm apache is running.
![Image showing successful running of Apache Web Server](/Apache%20Running.png)  

