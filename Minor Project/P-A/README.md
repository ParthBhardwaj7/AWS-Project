# Commands used to host MySql Server on AWS EC2 Instance
## Step 1: 
* Update the system
* sudo apt update

## Step 2:
* Install MySql
* sudo apt install mysql-server
* 
![Screenshot 2025-01-10 165940](https://github.com/user-attachments/assets/a36a8ace-928f-46b9-a13c-51997706a21c)


## Step 3: 
* Check the Status of MySql (Active or Inactive)
* sudo systemctl status mysql

## Step 4: 
* Login to MySql as a root
* sudo mysql

## Step 5: 
* Update the password for the MySql Server
* ALTER USER 'root'@'localhost' IDENTIFIED BY 'newpassword';
  
* FLUSH PRIVILEGES;

## Step 6: 
* Test the MySql server if it is working by running sample sql queries
* CREATE DATABASE mysql_test;

* USE mysql_test;

* CREATE TABLE table1 (id INT, name VARCHAR(45));

* INSERT INTO table1 VALUES(1, 'Parth'), (2, 'Gabru'), (3, 'chuchiyang');

* SELECT * FROM table1;

![Screenshot 2025-01-10 165519](https://github.com/user-attachments/assets/1aff0bc5-ad60-48c1-b582-91fa9d7adaf9)
