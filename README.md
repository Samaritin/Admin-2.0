# Admin 2.0






**Lab Details** 

Introduction
Wireshark is a basic tool used for observing messages exchanged between executing protocol entities called a packet sniffer. A packet sniffer passively copies messages being sent from and received by the user’s computer. The packet information displayed includes, but is not limited to various protocol fields.
Objective

The objective of this week’s lab is to familiarize the user with the Wireshark program and observe the network protocols in his or her computer. The following tasks are to be performed:
•	Download and install Wireshark and WinPcap
•	Define key terms
•	Perform live capture of network traffic
•	Analyze captured data
•	Analysis questions
Hardware used to perform analysis:
•	Lenovo Yoga C740 Series
•	Intel(R) Core(TM) i7-1040U CPU @ 1.80GHz 
•	12.00 GB DDR3 RAM
•	64-bit OS
Software and Websites used to perform analysis:
•	Windows 11 Home Premium Service 
•	Virtual Box 7
•	Ubuntu 22.0.7
•	Lighttpd
•	MySql
•	Php
•	phpMyAdmin


Results and Analysis
The first step of the lab is to make sure that the lighttpd dependcy is installed in Ubuntu. The user can check by running ‘dpkg -s lighttpd’. If the output says its in installed in is ok and when the installation date was then the package was already installed to Ubuntu. However, if it displayed there is no installation or no information available. The user will need to install the package. Either way it is best to upgrade the dependency using the ‘sudo apt-get upgrade’ command to make sure all the files are upgraded to the latest version. 

Next the user will install ‘MySql’. The user will run ‘sudo apt-get install mysql-server’ this will install the server. Once MySql has installed successfully, the user will want to login and change the default password. The user first must login as root running ‘sudo mysql’ command. The user will be welcomed with a ‘Welcome to mysql’ message then underneath the message there will be a ‘mysql>’ prompt where the user will be able to add to the mysql database and create tables. The user must first change the password to allow privilege escalation to all databases. By doing so, the user will enter “alter user ‘root’@’localhost’ identified with mysql_native_password by ‘(users choice of password)’;” after the semicolon the user can hit enter and the query has been saved into MySql. It will be followed by another prompt and the user can then type exit to leave the mysql dependency. In the following screenshot the steps will be provided. 

Figure 1: Changing MySql password
 
![image](https://github.com/user-attachments/assets/1fd36795-bf85-40c5-a8cd-2a49d7d622f0)


Once the user has exited mysql, it is time to configure it. The user will enter the command ‘mysql_secure_installation’. Then it will ask for a password. This will be the password the user just changed to in the previous command. The user will select ‘y’ to continue. Next to choose a password validation policy. This will be the password validation policy for any of the clients using the server. The choices are low, medium, and strong length and vary in what the passwords require. For the purposes of this lab the individual will choose 0 which is low length. Next the user will be asked if the individual would like to change the password for root. However, since the user has already done this the user will select ‘n’ for no, unless the user wishes to change the password again. 

Figure 2: Selecting password strength 

![image](https://github.com/user-attachments/assets/76c21d78-430e-4614-87bf-abab548c5532)


The user will be asked a few more questions but it security purposes it is best to say ‘y’ or yes to all of them. These questions are regarding permissions to other users and test databases that come with MySql as well as remote login. By saying yes to all of these MySql will disallow all of these making it more secure. Once the user is finished answering the questions it will state ‘All done!’ Now when the user attempts to login using ‘sudo mysql’ the command will no longer work. The user will need to enter ‘mysql -u root -p’ this will prompt the mysql server as the user root and the -p flag for the password. Once the user has entered this command, the output will ask for a password. The user will enter the password that was previously made. Then the user will be displayed with “Welcome to MySql monitor….”. The user can see the following screenshot below for further details. 

Figure 3: MySQL login 

![image](https://github.com/user-attachments/assets/d161561f-badf-433e-b32c-26447a977fae)


Now the user will populate the database with data using the MySql insert command. The user will enter in the prompt ‘CREATE DATABASE’ in capital letters then the name of what the user would like the database to be titled. In this example the name of the database will be titled ‘CYB362TestDatabase’. Therefore, the user will enter in the prompt ‘CREATE DATABASE CYB362TestDatabase’ This will first tell MySql to create a database. The user can see if it has been created by entering ‘SHOW DATABASES’ in the prompt as seen below. 

Figure 4: Databases listed 

![image](https://github.com/user-attachments/assets/76e9b53d-c102-4eb9-9519-91a7cbfded8f)


Next the user will have to enter the database, by entering ‘USE CYB362TestDatabase;’ Once the user is prompted with a Database changed output the user has entered that database, in this case it is the CYB362TestDatabase. Next the user will create a table. The user will enter 

‘CREATE TABLE accounts(
Name CHAR(50) NOT NULL, balance
MEDIUMINT DEFAULT 0 );’ Once the user gets an ‘Query OK’ output from the prompt the table has been created. The screenshot below shows what the table will look like after creating the table by entering in the prompt ‘DESCRIBE accounts(title of table)’

Figure 5: Accounts table setup 

![image](https://github.com/user-attachments/assets/2fd99c09-7a39-4222-95b0-d1057327fcd3)


Next the user will insert the value into the accounts table. The user will enter into the prompt ‘INSERT INTO accounts VALUE( “Bob Jones”, 100);’ Now if the user wants to see the selection in the table the user will enter ‘SELECT * FROM accounts;’ Then the table for account will appear as seen below. 

Figure 6: Accounts information table 

![image](https://github.com/user-attachments/assets/82ef21a1-98c3-4730-8e37-ad931b73ae07)


Next the user will need to install php by running ‘sudo apt-get install php’. Once that is done the user will install phpMyAdmin by running ‘sudo apt-get install phpMyAdmin. During installation, the user will choose the webserver of their choice either Apache2 or Lighttpd or both. The installation will then continue until the user will be prompted to enter a password for phpMyAdmin, then confirm the password. Once the installation process has finished the user will open the search browser of their choice and enter in the ip address followed by a forward slash with phpMyAdmin or ‘localhost’ followed by a forward slash with phpMyAdmin. The results with show the following below. 

Figure 7: phpMyAdmin login screen 

![image](https://github.com/user-attachments/assets/c945636d-c3f8-4ba9-9d37-4c3ebb82a6c9)


Once the user has logged into the phpMyAdmin account the user can see the test database that was created in MySQL and if the user clicks on the database the accounts information will appear as well. The screenshot below will show in detail this information. 

Figure 8: phpMyAdmin information 

![image](https://github.com/user-attachments/assets/e63f7b1c-7638-4a1d-9361-551e6b97c413)



Conclusion
Although, this was very user friendly to install and create. There is room for many vulnerabilities. This can be due to the extreme flexibility of these called ‘stacks’ such as LAMP and LLMP acronyms for Linux, Apache, MySQL, and PHP or Linux, Lighttpd, MySQL, and PHP and others. There have been vulnerabilities found in some stacks primarily the LAMP stack. Open source security vulnerability have a patch available approximately 80-85%, however, more than 50% of the open source vulnerabilities don’t receive it. Therefore, leaving them open to an attack. This could be due to many reasons such as the individuals not reassessing the code after its been in use for some time, no evaluation of another individual, or just a simple mistake. These stacks have quite the flexibility allowing different programming like python to be used and other changes allowed within each dependency themselves. The less structure each dependency has the more room for vulnerabilities that allow attacks on each of these stacks. However, with more structure and security there is the less user friendly it will be. Thus, making it not as open source as the industry would call it. Making a label, restriction and rules on it would go against any sort of open source feel and more along the lines of the corporate world. Something some people in the computer industry are totally against. Overall, these can be used for great things to help companies and keep information organized. However, these must be used with other programs to make sure this information is kept secure properly and maintained accordingly. 
