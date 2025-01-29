# AWS x Databases project: Aurora Database with Web Server:

![Image](https://github.com/user-attachments/assets/b5118194-0f9a-4d6b-94c7-5e5f723ac68a)
## Login with your IAM user:
* Head to your AWS Account as the root user.
* Open the AWS IAM console.
* From the left hand navigation panel, choose Users.
* Choose Create user.
* For the User name, use Yourname-IAM-Admin‍
* Make sure to select the checkbox next to Provide user access to the AWS Management Console - optional.‍
* This does not apply to all accounts, but if you're prompted with a pop up panel that says Are you providing access to a person?, choose I want to create an IAM user.
* For the console password, choose Custom password.
* Type in a password that you will be able to remember/access in the future.
* Deselect the checkbox for Users must create a new password at next sign-in - Recommended.
* Choose Next.
* In the permissions set up page, choose Attach policies directly.
* From the list of Permissions policies, select AdministratorAccess.
* Choose Next.
* Choose Create user.
* Voilà - you've just created your new user! Stay on this page.
* Choose Download .csv file.
* Copy the Console sign-in URL.
* Now you're ready to start using your IAM user. 🏁
* Log out of your root user's AWS Account.
* Paste and go to your copied console sign-in URL.
* Open your downloaded .csv file containing your user's access instructions.
* Log in using your IAM user's username and password in the .csv file.

![Image](https://github.com/user-attachments/assets/eecb3c34-c8d0-4561-9e40-a2879e0b3694)
![Image](https://github.com/user-attachments/assets/96dc8f4a-2d68-43db-9589-26962e933a4a)

![Image](https://github.com/user-attachments/assets/ad6a6525-fb0f-4584-b65d-9ea96883b346)

## Launch an EC2 instance:
* In this step, we're going to create an Amazon EC2 instance using our default VPC and default subnets.
* In this step, you're going to:
* Create an EC2 instance to host a web app (we'll create the web app itself in the next project) 
* Open a new tab in your web browser and go to your AWS console (this means we can keep our Aurora database set-up in progress!)
* In the upper-right corner of the AWS Management Console, make sure your AWS Region is the same as that in your Aurora database creation.
* In the AWS console search bar, search for EC2
* Select Instances in the left hand menu and choose Launch instances
* Choose the following settings in the Launch an instance page.
* Under Name and tags, for Name, enter nextwork-ec2-instance-web-server
* Under Application and OS Images (Amazon Machine Image), choose Amazon Linux.
* Choose the Amazon Linux 2023 AMI.
* Keep the defaults for the other choices.
* Under Instance type, choose t2.micro.
* Under Key pair (login), choose a Create new key pair
* For your Key pair name, enter NextWorkAuroraApp
* Leave your Key pair type as RSA
* Leave your Private key file format as .pem since we're using SSH later on to access our EC2 instance.
* Back in our EC2 creation, under Network settings, set these values and keep the other values as their defaults:
* For Allow SSH traffic from, choose your IP address if it's correct (you can check your IP by clicking here). Otherwise select Anywhere.
* Check the boxes for Allow HTTP traffic from the internet.
* Leave the default values for the remaining sections.
* Review the Summary panel of your instance configuration
* When you're ready, choose Launch instance.
* Navigate back to your list of EC2 instances, and then select the checkbox next to your new instance.
* In the Details tab, note the following important details:
* In Instance summary, note the Public IPv4 DNS.
* Note the value for Key pair name.
* Wait until Instance state for your instance is Running before continuing.

## Create an Aurora MySQL Database
![Image](https://github.com/user-attachments/assets/4d9f8b96-f64a-4767-80aa-662f8fb7eb05)

![Image](https://github.com/user-attachments/assets/3330a8e9-d139-4c30-b743-2a0bda2f02b8)
* First things first... we need a relational database. Then we can connect it to our web app server and get cracking. 
* In this step, you're going to:
* Create an Aurora relational database from scratch
* First - check your Region
* Take note of your Region in the top right of your AWS Console.
* It doesn't matter exactly which Region you have, as long as you're aware of it.
* Head to RDS console - search for rds in search bar at the top of the screen.
* Notice that even if you search for Aurora, the same result shows up!
* In the left navigation bar, select Databases.
* In the Database section, select Create Database.
* On the Create database page, choose Standard Create.
* In the Configuration section, make the following changes:
* For Engine type, choose Aurora (MySQL Compatible).For Engine Version, choose Aurora MySQL 3.05.2 (compatible with MySQL 8.0.32) - default for major version 8.
* For Templates, choose Dev/Test
* In the Settings section, set these values:
* DB cluster identifier: nextwork-db-cluster
* Master username: admin
* For Credentials management select Self managed.
* Master password: Type a password (eg. n3xtw0rk)
* Confirm password: Retype the password.
* Make sure you save your database login details somewhere safe! You'll need them later on.

![Image](https://github.com/user-attachments/assets/100016da-831d-4cd3-ace5-15153dbad3b4)

* Leave the Cluster storage configuration settings as default.
* In the Instance configuration section, set these values:
* Burstable classes (includes t classes)
* db.t3.medium
* In the Availability and durability section, use the default values. 
* Finish creating your Aurora Database
* Nice work! Now that we've got our EC2 instance ready to go, we can go back to creating our Aurora database. This time, we'll connect it to our new EC2 instance.
* Navigate back to your open tab that you were creating our Aurora database in.
* We were up to the Connectivity section. But this time we have one big advantage...we have an EC2 instance! Woohoo!
* For Compute resource, choose Connect to an EC2 compute resource.
* Now select the drop down for EC2 instance, and choose nextwork-ec2-instance-web-server.
* NOTE: You may need to select the refresh button to the right of the EC2 instance drop-down.
* Scroll down and open the Additional configuration section.
* Enter sample for Initial database name.
* Keep the default settings for the other options.
* Select Create database.
* Close any pop-ups that appear.
* Your new DB cluster will show in the Databases list with the status Creating.
* Wait for the Status of your new DB cluster to show as Available.
* Select the DB identifier of your top database to take a look at the details.
* Notice that there are two Endpoints in our Database. Cool! This is our cluster in action.
![Image](https://github.com/user-attachments/assets/f287f2a6-ef14-4a29-9c5f-5d4aa388d613)


![Image](https://github.com/user-attachments/assets/ab723570-de37-4dc3-b09e-be94a737cc82)

![Image](https://github.com/user-attachments/assets/3cf7adca-6a59-4271-9928-7ebb679fc4b0)
![Image](https://github.com/user-attachments/assets/e91d45f1-aca4-489b-8647-d73036e192df)

![Image](https://github.com/user-attachments/assets/137a4faa-1f8e-46b1-9bf3-d155c9cdd89b)

