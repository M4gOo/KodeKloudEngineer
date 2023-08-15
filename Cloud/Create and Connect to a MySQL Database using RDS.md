

https://docs.aws.amazon.com/rds/index.html

https://aws.amazon.com/getting-started/hands-on/create-mysql-db/?ref=gsrchandson      -    It is a Free Tier  

https://aws.amazon.com/rds/mysql/

### STEPS
* Create an environment to run your MySQL database
* Connect to the database


 
### Choose you Region, my case it will be N.Virginia
 ![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/7351f5db-855d-4ff8-a510-55c4669aee19)

 ![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/841140c9-67ac-4ec6-afa9-08b1a69b0556)



![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/9341ba69-e2f1-4237-afc2-a4b30a0f9578)


You will have to PAY for Multi-AZ deployment (automatically provision and maintain a synchronous standby replica in a different AZ)

https://aws.amazon.com/rds/pricing/

Multi-AZ can have: 
one standby DB instance -  it's called a Multi-AZ DB instance deployment. This deployment provides failover support (60 seconds with zero data loss and no manual intervention), but doesn't serve read traffic.  
two standby DB instances -  it's called a Multi-AZ DB cluster deployment. This deployment has standby DB instances that provide failover support and can also serve read traffic.

#

Synchronous replication - data is written to the primary instance and synchronously replicates the data to an instance in a different AZ 

* Synchronous replication is the process of copying data over a storage area network, local area network or wide area network so there are multiple, current copies of the data.
Synchronous is mainly used for failover and for high-end transactional applications ([ERP-software system for finance, HR, manufacturing, supply chain], [CRM - tracks complex and dynamic data, 
like what emails a contact has opened, what pages customers visited on your website, what customers bought in the webpage.])  



* Asynchronous replication - data is first written to primary storage and then to the replicas

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/040f4ddb-0387-431c-96a8-e728f717d964)


Fill the Settings, in doubt just read some explantions below or above the white spaces. 

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/a523ecd5-f52f-4916-9459-f3f5d78603f1)


* Instances access EBS volumes over network connections. Your application performance is limited by the network bandwidth available to your instances.
    EBS-optimized instance (dedicated networks) connection to storage with throughput options from 500 Mbps to 4000 Mbps with a per instance maximum of 32,000 IOPS.  
    Non EBS-optimized instances (shared networks) network traffic is shared by all traffic storage and non-storage. Shared bandwidth is an issue for apps that use significant network traffic (web/clustered apps)


* Block size is the measure of amount of data written/read in a single IO request. Storage devices store data in units of blocks. They are also able to receive data in sizes of multiples of blocks.
* IOPS (IO operations per second) is a measure of how many IO requests can be completed by the storage device in a second.
* Throughput is the measure of the amount of data transferred from/to a storage device in a second. 
if a storage device can write 1000 blocks of 128K each, throughput is 1000*128K/s = 128MB/s)



#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/798ad3eb-8ea5-4e9d-a4c0-dd6b2c80ea72)

* Autoscaling - If your workload is cyclical or unpredictable, it is good to have enabled so Amazon RDS can automatically scale up your storage when needed. 

* DB instances for Amazon RDS for MySQL, MariaDB, PostgreSQL, Oracle, and Microsoft SQL Server use Amazon EBS volumes for DATABASE and LOG STORAGE.

  Factors that affect storage performance (Multi-AZ standby creation, Read replica creation, Changing storage types, Database workload, DB instance class)
  
###  RDS storage types

* General Purpose SSD – cost-effective storage ideal for a broad range of workloads running on medium-sized DB instances. It is suited for development and testing environments.

* Provisioned IOPS SSD – it is for I/O-intensive workloads, database workloads that require low I/O latency and consistent I/O throughput. Best for production environments.

* Magnetic – backward compatibility. The maximum amount of storage allowed for DB instances on magnetic storage is less than that of the other storage types.

  
#


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/56c8c743-81e8-4eaa-9bf1-22598ee8fa69)


* Connectivity section where you can provide information that Amazon RDS needs to launch your MySQL DB instance. 

* Virtual Private Cloud (VPC)
When you use a VPC, you have control over your virtual networking environment.
You can choose your own IP address range, create subnets, and configure routing and access control lists.
There is no additional cost to run your DB instance in a VPC.
Accounts have a default VPC.
All new DB instances are created in the default VPC unless you specify otherwise.


* Subnet group - Choose the default subnet group. 
Your default VPC has three subnets that you can use to isolate resources inside the VPC.
The default VPC also has an internet gateway that can be used to provide access to resources inside the VPC from outside the VPC.


* Public accessibility: This will allocate an IP address for your database instance
Amazon EC2 instances and other resources outside of the VPC can connect to your database. Resources inside the VPC can also connect to the database.
Choose one or more VPC security groups that specify which resources can connect to the database.


* VPC security groups: Select Create new VPC security group. This will create a security group that will allow connection from the IP address of the device that you are currently using to the database created.
A security group acts as a firewall that controls the traffic allowed to and from the resources in your VPC. You can choose the ports and protocols to allow for inbound/outbound traffic 


* RDS Proxy: By using Amazon RDS Proxy, you can allow your applications to pool and share database connections to improve their ability to scale.

* Port: Leave the default value of 3306.

  
# What is proxy?
Proxy - It’s an intermediary server separating end users from the websites they browse. Proxy servers provide varying levels of functionality, security, and privacy depending on your use case
A proxy server has its own IP address that your computer knows. When you send a web request, your request goes to the proxy server first.

For DB the primary purpose is to improve the performance, scalability, and security of database communication. Proxies allow non-sysadmins to manage and maintain SQL jobs

The proxy server then makes your web request on your behalf, collects the response from the web server, and forwards you the web page data so you can see the page in your browser.
A proxy server can change your IP address, so the web server doesn’t know exactly where you are in the world. It can encrypt your data, so your data is unreadable in transit. And lastly, a proxy server can 
block access to certain web pages, based on IP address.


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/ce8ba626-79c6-455f-aeff-d3fba91febc3)

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/48d449d8-32e7-4e28-85a4-23996c4a7f60)

Amazon RDS supports several ways to authenticate database users. Choose Password authentication from the list of options

#


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/7d33f42b-068f-4c25-bda0-765385f7c9a6)

Enhanced monitoring - unchecked to stay within the Free Tier. 
Enabling enhanced monitoring will give you metrics in real time for the operating system (OS) that your DB instance runs on.
CloudWatch – Shows the Amazon CloudWatch metrics for RDS that you can access in the RDS console.
Monitoring is an important part of maintaining the reliability, availability, and performance

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/e0c34afd-54ae-4690-b4f7-7f20ae0cf0a6)


* EBS Snapshots are a point-in-time copy of your data, and can be used to enable disaster recovery, migrate data across regions and accounts, and improve backup compliance.

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/7cb6bdd3-82e3-40f5-8d8d-1c3ac67f1e7b)


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/753d52b2-7992-48e6-8e1a-b27e741a01f6)


# 

In the Additional configurations section:

* Database options

Database name: Enter a database name that is 1 to 64 alphanumeric characters. If you do not provide a name, Amazon RDS will not automatically create a database on the DB instance you are creating.

DB parameter group -  You manage your database configuration by associating your DB instances and Multi-AZ DB clusters with parameter groups. Amazon RDS defines parameter groups with default settings. 
You can also define your own parameter groups with customized settings.

Option group: Amazon RDS uses option groups to enable and configure additional features. Some DB engines offer additional features that make it easier to manage data and databases, and to provide additional security for your database. Amazon RDS uses option groups to enable and configure these features.

Encryption:  Not available in the Free Tier. Data that is encrypted at rest includes the underlying storage for DB instances, its automated backups, read replicas, and snapshots.
Amazon RDS encrypted DB instances use the industry standard AES-256 encryption algorithm to encrypt your data on the server that hosts your Amazon RDS DB instances. 


* Maintenance

Auto minor version upgrade: Select Enable auto minor version upgrade to receive automatic updates when they become available.
Deletion protection: When this option is enabled, you're prevented from accidentally deleting the database.

# 

## FINALLY  CLICK ON   CREATE DATABASE 

Depending on the DB instance class and storage allocated, it could take several minutes for the new DB instance to become available.


#  Download MySQL Workbench 

with that we can test our DB
Remember to run MySQL Workbench from the same device from which you created the DB instance. The SECURITY GROUPD DB is placed in is configured to allow connection only from the device from which you created the DB instance.

Just add port, username, password and hostname (whch is the endpoint - to see that just click on the DB created earlier)

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/9ad74e47-a6a0-4f0e-b600-b0a7a85d7d6d)












