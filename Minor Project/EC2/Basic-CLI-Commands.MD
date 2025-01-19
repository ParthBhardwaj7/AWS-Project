# AWS EC2 Command Line Interface commands
*Use Amazon Linux AMI to launch an EC2 instance with port 22 open Make a note of AMI ID in your region Make

### Create an EC2 instance with the CLI:
```
aws ec2 run-instances --image-id ami-8c1be5f6 --instance-type t2.micro 
```
### Let's launch another instance with Windows AMI
```
aws ec2 run-instances --image-id ami-07a29e78aeb420471 --instance-type t2.micro 
```
###List all the instance and their details.
```
aws ec2 describe-instances
```
###Describe and query specific things( List specific attributes). Let's query IP of all the instances.
```
aws ec2 describe-instances --query 'Reservations[].Instances[].PublicIpAddress'
```
###Describe and filter to show only windows Instance
```
aws ec2 describe-instances --query 'Reservations[].Instances[].PublicIpAddress' --filters "Name=platform,Values=windows"
```
###Stop EC2
```
aws ec2 stop-instances --instance-ids i-0b20d7680fa0e6ba0
```
###Terminate EC2
```
aws ec2 terminate-instances --instance-ids i-0b20d7680fa0e6ba0
```
Congratulations! You now know the basic AWS EC2 CLI Commands.
![Image](https://github.com/user-attachments/assets/ec9b0c10-c003-400d-bc1e-34f6a20d133e)

![Image](https://github.com/user-attachments/assets/ab9b80d3-090e-42bf-a8ae-af2222254093)

![Image](https://github.com/user-attachments/assets/4df6620b-f4da-464c-a523-64519ba061bf)

![Image](https://github.com/user-attachments/assets/c9e5bd88-efba-4633-8a4d-dc43e41b1e2f)

![Image](https://github.com/user-attachments/assets/4aecaad6-0f7c-4f60-8f9e-5a793f11bf8f)

![Image](https://github.com/user-attachments/assets/5d6db370-416c-4115-8e8f-66b11df4c622)
