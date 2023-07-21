 #Project 5

 Install 2 Ec2 instance. 1 is Sever for database, 2nd is client machine

 ![alt text](./images/EC2%20client%20server.PNG)

 Server

 `sudo mysql_secure_installation`

  ![alt text](./images/mysql%20secured%20installation.PNG)

  `CREATE DATABASE test_db;`

  ![alt text](./images/Screenshot_2.png)

  `GRANT ALL ON test_db.* TO 'remote_user'@'%' WITH GRANT OPTION;`

   ![alt text](./images/Screenshot_3.png)

   `FLUSH PRIVILEGES;`
   ![alt text](./images/Screenshot_4.png)

   `sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf`
   `sudo systemctl restart mysql`

 ![alt text](./images/restart%20mysql.PNG)

 CLIENT

`sudo apt update`

Install mysql client

`ip addr show`

![alt text](./images/client%20server.PNG)

Add client private ip to server security inbound rules to allow access to mysql

![alt text](./images/Screenshot_7.png)


sudo mysql -u remote_user -h 172.31.89.248 -p

![alt text](./images/EC2%20client%20server.PNG)