
It is a Free Tier 
create MySQL instance
Amazon RDS to create a MySQL DB Instance with db.t2.micro DB instance class, 20 GB of storage, and automated backups enabled with a retention period of one day


### STEPS
* Create an environment to run your MySQL database
* Connect to the database
* Delete the database instance

 
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
Synchronous is mainly used for failover (if the primary node fails and for high-end transactional applications ([ERP-software system for finance, HR, manufacturing, supply chain], [CRM - tracks complex and dynamic data, 
like what emails a contact has opened, what pages customers visited on your website, what customers bought in the webpage.])  
that need instant failover if the primary node fails


Asynchronous replication - data is first written to primary storage and then to the replicas

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/040f4ddb-0387-431c-96a8-e728f717d964)


Fill the Settings, in doubt just read some explantions below or above the white spaces. 

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/a523ecd5-f52f-4916-9459-f3f5d78603f1)


On a non-EBS-Optimized instance, all the traffic including EBS and other traffic(internal & external) is handled through the network link. Other network traffic from your instance or your instance's neighbors can affect the EBS traffic which impacts performance.

What is the difference between EBS optimized and non optimized?
EBS-optimized instances offer dedicated network connection to storage with throughput options from 500 Mbps to 4000 Mbps with a per instance maximum of 32,000 IOPS. 
With non-EBS-optimized instances, network traffic is shared by all traffic – storage and non-storage.

https://www.apptio.com/blog/aws-ebs-performance-confused/

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/798ad3eb-8ea5-4e9d-a4c0-dd6b2c80ea72)

Enable storage autoscaling: If your workload is cyclical or unpredictable, you would enable storage autoscaling to enable Amazon RDS to automatically scale up your storage when needed. This option does not apply to this tutorial.
Allocated storage: Select the default of 20 to allocate 20 GB of storage for your database. You can scale up to a maximum of 64 TB with Amazon RDS for MySQL.

https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_Storage.html

#


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/56c8c743-81e8-4eaa-9bf1-22598ee8fa69)


Connectivity section where you can provide information that Amazon RDS needs to launch your MySQL DB instance. 

Connectivity

Compute resource: Choose Don’t connect to an EC2 compute resource. You can manually set up a connection to a compute resource later.
Virtual Private Cloud (VPC): Select Default VPC. For more information about VPC, see Amazon RDS and Amazon Virtual Private Cloud (VPC).
Additional connectivity configurations

Subnet group: Choose the default subnet group. For more information about subnet groups, see Working with DB Subnet Groups.
Public accessibility: Choose Yes. This will allocate an IP address for your database instance so that you can directly connect to the database from your own device.
RDS assigns a public IP address to the database. Amazon EC2 instances and other resources outside of the VPC can connect to your database. Resources inside the VPC can also connect to the database. Choose one or more VPC security groups that specify which resources can connect to the database.
RDS doesn't assign a public IP address to the database. Only Amazon EC2 instances and other resources inside the VPC can connect to your database. Choose one or more VPC security groups that specify which resources can connect to the database.
VPC security groups: Select Create new VPC security group. This will create a security group that will allow connection from the IP address of the device that you are currently using to the database created.
Availability Zone: Choose No preference. See Regions and Availability Zones for more details.
RDS Proxy: By using Amazon RDS Proxy, you can allow your applications to pool and share database connections to improve their ability to scale. Leave the RDS Proxy unchecked.
Port: Leave the default value of 3306.


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/ce8ba626-79c6-455f-aeff-d3fba91febc3)

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/48d449d8-32e7-4e28-85a4-23996c4a7f60)

Amazon RDS supports several ways to authenticate database users. Choose Password authentication from the list of options

#


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/7d33f42b-068f-4c25-bda0-765385f7c9a6)

Enhanced monitoring: Leave Enable enhanced monitoring unchecked to stay within the Free Tier. Enabling enhanced monitoring will give you metrics in real time for the operating system (OS) that your DB instance runs on. For more information, see Viewing DB Instance Metrics.

#

![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/e0c34afd-54ae-4690-b4f7-7f20ae0cf0a6)


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/7cb6bdd3-82e3-40f5-8d8d-1c3ac67f1e7b)


![image](https://github.com/M4gOo/KodeKloudEngineer/assets/57456345/753d52b2-7992-48e6-8e1a-b27e741a01f6)



In the Additional configurations section:

Database options

Database name: Enter a database name that is 1 to 64 alphanumeric characters. If you do not provide a name, Amazon RDS will not automatically create a database on the DB instance you are creating.
DB parameter group: Leave the default value. For more information, see Working with DB Parameter Groups.
Option group: Leave the default value. Amazon RDS uses option groups to enable and configure additional features. For more information, see Working with Option Groups.
Encryption: This option is not available in the Free Tier. For more information, see Encrypting Amazon RDS Resources. 


Backup

Backup retention period: You can choose the number of days to retain the backup you take. For this tutorial, set this value to 1 day.
Backup window: Use the default of No preference.
Maintenance

Auto minor version upgrade: Select Enable auto minor version upgrade to receive automatic updates when they become available.
Maintenance Window: Select No preference.
Deletion protection: Turn off Enable deletion protection for this tutorial. When this option is enabled, you're prevented from accidentally deleting the database.

## CLICK ON   CREATE DATABASE 

#

Note: Depending on the DB instance class and storage allocated, it could take several minutes for the new DB instance to become available.
The new DB instance appears in the list of DB instances on the RDS console. The DB instance will have a status of creating until the DB instance is created and ready for use. 
When the state changes to available, you can connect to a database on the DB instance. 
