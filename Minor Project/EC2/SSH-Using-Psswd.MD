# SSH With passoword instead of ssh keys
## Steps
* From an SSH client, log in to your EC2 instance. Create one like in the lab 1 if you don't have an EC2 Instance running.

* Set a password for user. The example below uses ec2-user as the user:
```
   sudo passwd ec2-user
```
* Update the PasswordAuthentication parameter in the /etc/ssh/sshd_config file:
* PasswordAuthentication yes
```
sudo vi /etc/ssh/sshd_config
```
* Restart the SSH service. For Amazon Linux, RHEL 5, and SUSE Linux, use this command:
 ```
sudo service sshd restart
```
* For Ubuntu, use this command:
```
sudo service ssh restart
```
* Exit out of the EC2 session, and then log in to test the password authentication.
```
ssh ec2-user@your-instance-up.address
```
You will be prompted for a password. Enter the password and you should be successfully logged in to the ec2 instace

Part 2: Steps to enable password authentication and set password for first login on EC2
Paste this script to your EC2 userdata during launch to enable password ssh for your first login. Change user and pass by changing lines under TODO in the below script.

```
#!/bin/bash
sed 's/PasswordAuthentication no/PasswordAuthentication yes/' -i /etc/ssh/sshd_config
systemctl restart sshd
service sshd restart

#TODO: replace bob with your desired username
useradd bob
# TODO: replace password123 with desired password and change bob to your username chosen in useradd 
echo "password123" | passwd --stdin bob
```

If you make no changes to the script , you can login to EC2 after a few minutes using this command. Passoword is password123 . Replace the IP with your EC2 IP

```
ssh bob@11.22.23.24
```
