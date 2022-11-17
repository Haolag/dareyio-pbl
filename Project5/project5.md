 #Project 5

 ##Install 2 Ec2 instance. 1 is Sever for database, 2nd is client machine

![alt text](./images/EC2%20client%20server.PNG)
 ![alt text](./images/Screenshot_8.png)

 Server

 `sudo mysql_secure_installation`

![alt text](./images/mysql%20secured%20installation.PNG)
![alt text](./images/Screenshot_1.png)

  `CREATE DATABASE test_db;`

  ![alt text](./images/Screenshot_2.png)

  `GRANT ALL ON test_db.* TO 'remote_user'@'%' WITH GRANT OPTION;`

   ![alt text](./images/Screenshot_3.png)
   ![alt text](./images/remote%20into%20mysql.PNG)

   `FLUSH PRIVILEGES;`
   ![alt text](./images/Screenshot_4.png)

   `sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf`
   `sudo systemctl restart mysql`

 ![alt text](./images/Screenshot_5.png)
 ![alt text](./images/restart%20mysql.PNG)

 ##CLIENT

`sudo apt update`

Install mysql client
![alt text](./images/client%20server.PNG)

`ip addr show`

![alt text](./images/Screenshot_6.png)

Add client private ip to server security inbound rules to allow access to mysql

![alt text](./images/Screenshot_7.png)


sudo mysql -u remote_user -h 172.31.3.117 -p

![alt text](./images/Screenshot_8.png)