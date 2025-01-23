# Step-by-Step guide to setting up a secure Virtual Private Cloud (VPC) in AWS:

![Image](https://github.com/user-attachments/assets/f8cbf228-1fe9-4c0b-b34e-2f45e9033019)

## Step 1: Log in to the AWS Management Console
* Open AWS Management Console.
* Navigate to VPC under the "Networking & Content Delivery" section.
## Step 2: Create a New VPC
* Go to the VPC Dashboard.
* Click Create VPC.
* Choose VPC Only.
* Enter the details:
* Name tag: Provide a name for your VPC (e.g., MySecureVPC).
* IPv4 CIDR block: Enter an IP range (e.g., 10.0.0.0/16).
* IPv6 CIDR block: Select "No IPv6 CIDR block" (optional).
* Click Create VPC.
* The DNS hostnames attribute determines whether instances launched in the VPC receive public DNS hostnames that correspond to their public IP addresses.
![Image](https://github.com/user-attachments/assets/9c3f0a76-35a6-4883-bf33-ee0383d2dd9e)

## Step 3: Create Subnets
* A secure VPC typically has public and private subnets for better isolation.

* Go to Subnets:
* Click Create subnet.
* Create 2 Public Subnet in Different AZ:
* VPC ID: Select the VPC you just created.
* Subnet name: PublicSubnet.
* Availability Zone: Select a zone (e.g., us-east-1a).
* IPv4 CIDR block: Provide a range (e.g., 10.0.1.0/24).
* Click Create subnet.
* Create 4 Private Subnet 2 in each AZ:
* Follow the same steps as above but name it PrivateSubnet.
* Use a different CIDR block (e.g., 10.0.2.0/24).
![Image](https://github.com/user-attachments/assets/d4e874ea-3e7f-4a02-b4c9-2802797cc88b)
![Image](https://github.com/user-attachments/assets/624d2aab-8e59-48e8-8a3d-fd3c8170b4db)

## Step 4: Create an Internet Gateway
* Go to Internet Gateways:
* Click Create internet gateway.
* Provide a name (e.g., MyInternetGateway) and click Create internet gateway.
* Attach it to your VPC:
* Select the internet gateway and click Actions > Attach to VPC.
* Choose your VPC and click Attach internet gateway.

![Image](https://github.com/user-attachments/assets/845154a3-abb7-46cb-bba7-12dca1126f84)

## Step 5: Create a Route Table
* Go to Route Tables:
* Click Create route table.
* Create Public Route Table:
* Name tag: PublicRouteTable.
* VPC: Select your VPC.
* Click Create route table.
* Edit Routes for Public Subnet:
* Select the public route table and click Edit routes.
* Add the following route:
* Destination: 0.0.0.0/0.
* Target: Select the internet gateway.
* Click Save changes.
* Select NAT Gateway on both Private Route Table to their own public Subnet
* Associate Public Subnet:
* Go to the Subnet associations tab in the public route table.
* Click Edit subnet associations.
* Select your PublicSubnet and click Save changes.
![Image](https://github.com/user-attachments/assets/1da072cc-dae9-4989-a9c0-a3f321b750bc)

![Image](https://github.com/user-attachments/assets/4fc36e5f-feec-49eb-bad1-46a8164ccdea)


![Image](https://github.com/user-attachments/assets/0d22b81b-d868-4496-ac87-0e9e89d92834)

## Step 6: Create a NAT Gateway (For Private Subnet Internet Access)
* Go to NAT Gateways:
* Click Create NAT gateway.
* Configure NAT Gateway:
* Name: MyNATGateway.

* Subnet: Select your public subnet.
* Elastic IP allocation ID: Click Allocate Elastic IP and select it.
* Click Create NAT gateway.
* Edit Private Route Table:
* Go to Route Tables and create a PrivateRouteTable as in Step 5.
* Add a route:
* Destination: 0.0.0.0/0.
* Target: Select the NAT gateway.
* Associate the private route table with the PrivateSubnet.

![Image](https://github.com/user-attachments/assets/40dc12d3-5055-4d91-a77d-fd4fb44e5037)

![Image](https://github.com/user-attachments/assets/392ac64d-f4a9-4853-b000-acfdac014ec6)

## Step 7: Security Groups
![Image](https://github.com/user-attachments/assets/67c0730c-cb02-41a4-a630-03def61987ef)
* Create a Security Group for Public Access:
* Go to Security Groups and click Create security group.
* Name: PublicAccessSG.
* VPC: Select your VPC.
* Add inbound rules:
* Allow HTTP (80) and HTTPS (443) from 0.0.0.0/0.
* Allow SSH (22) from your IP (use My IP).
* Create a Security Group for Private Access:
* Name: PrivateAccessSG.
* Add inbound rules:
* Allow traffic from PublicAccessSG for application-specific ports (e.g., 3306 for MySQL).
* Add outbound rules:
* Allow all outbound traffic.
![Image](https://github.com/user-attachments/assets/cf7d4362-45a1-4e35-9e79-7b23b0062e9a)

![Image](https://github.com/user-attachments/assets/60c6716c-4b99-4b60-bcaf-6de695a7fd43)

![Image](https://github.com/user-attachments/assets/684c2ccc-2b22-47b2-a863-d683c43c80dd)

![Image](https://github.com/user-attachments/assets/5f52146c-bacd-4fce-ad5a-149f741b9b36)
## Step 8: Launch EC2 Instances
* Launch Public Instance:
* Go to EC2 > Launch Instance.
* Choose an Amazon Linux 2 AMI.
* Select your public subnet.
* Assign a public IP.
* Attach the PublicAccessSG.
* Launch Private Instance:
* Repeat the above steps but select the private subnet.
* Attach the PrivateAccessSG.

## Step 9: Test Connectivity
* Connect to the public instance using SSH:
```
ssh -i /path/to/key.pem ec2-user@your-public-ip
From the public instance, connect to the private instance:
```
```
ssh -i /path/to/key.pem ec2-user@private-ip
```
## Step 10: Monitor and Enhance Security
* Enable CloudTrail to log API calls in your VPC.
* Use VPC Flow Logs for monitoring network traffic.
* Consider setting up a Web Application Firewall (WAF) for added protection.
