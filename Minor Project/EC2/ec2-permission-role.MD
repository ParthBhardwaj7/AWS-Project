# Give EC2 Instance permissions with IAM Role

## Steps
* Go to IAM Dashboard
* Click on User in the left navigation pane
* Add a user and give him programmatic access
* Click Next and Select the Attach Existing policy directly
* Search and add AmazonS3FullAccess Use the search box to search for those policies and click the checkbox
![Image](https://github.com/user-attachments/assets/8e1adf6a-d694-4d33-a9db-1cea0943018b)

* Click Next Tags and review and create a user. 
* Click show and save the access key and secret key somewhere. Or download the CSV file if you want as well.
![Image](https://github.com/user-attachments/assets/72920ca5-c85b-4031-ad50-5b328c5c89b5)


* Launch an Amazon Linux EC2 Instance
* SSH into it
* Let's say you want to work with Amazon S3 from this isntance. Make some buckets and list some buckets. You can use the AWS Command Line interface. Amazon Linux AMI has this installed already.
* Configure the AWS CLI

```
aws configure
```
![Image](https://github.com/user-attachments/assets/04eaf3a1-aa23-4e01-878c-b4c35d4d0918)

* Enter the access key and secret access keys you generated earlier
* Enter the name of your region
* Create a S3 bucket from AWS CLI with a random name. If you have proper permissions you will be able to both create and list s3 buckets.
```
aws s3 mb s3://checkss
```

![Image](https://github.com/user-attachments/assets/c526903a-4dac-4ab6-b156-c867c61455d1)
* List your S3 buckets.
```
aws s3 ls
```
* You just used Access keys to connect to S3 from EC2.
* View the credential file. Hardcoded credentials are insecure from a security perspective.
```cat ~/.aws/credentials```
* Delete the file . This will remove the credentials

![Image](https://github.com/user-attachments/assets/6829442e-3b14-4371-b48f-40b8fa706179)

#PART 2 : Permissions with IAM Roles
* Go to IAM Dashboard and click on Roles 
* Click Create Role and Select EC2 to be the service using this role
* Click next Permissions and select AmazonS3FullAccess policy and attach to this role. Also select AmazonEC2FullAccess policy for this role. We will reuse this role in the next lab.
* Click Next Until you see the screen to enter the Role Name.Enter the name and description for the role. Verify you have S3 and EC2 access policies attached and create the Role.
![Image](https://github.com/user-attachments/assets/5893b0a5-c4f4-425d-b0fd-9b105edee2ad)
* Go to EC2 Instance Page. Select the EC2 instance , Click Actions and Attach IAM Role. Attach the role we created in the previous step.
![Image](https://github.com/user-attachments/assets/411d6f10-6da9-4ae2-bfad-be1673a70326)
* Now go back to the EC2 instance.

* Enter command to list s3 buckets. You should be able to

```
aws s3 ls --region us-east-1
```
* (OPTIONAL) Remove the Role we added a few steps back and try the S3 list command again. It shouldn't work.
* Now you see how to give access to S3 and other AWS services using access keys and Role. And you also know Roles are safer because it uses temporary Credentials.

* Let's keep the same instance for the Next Lab
* How Roles work
* Roles use temporary credentials that rotate every 30 minutes or so and are a lot safer than hardcoding keys.

* Type this command inside your EC2 to view temporary credentials for the role attached to EC2
``` 
curl 169.254.169.254/latest/meta-data/iam/security-credentials/{your-role-name}
```
