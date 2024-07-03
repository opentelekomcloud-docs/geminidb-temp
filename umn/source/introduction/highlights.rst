:original_name: nosql_01_0002.html

.. _nosql_01_0002:

Highlights
==========

High Reliability
----------------

**Data backup**

Data can be backed up automatically or manually. In an automated backup, all of the data in a given DB instance is backed up by the system. In a manual backup, the user backs up the data. These backups can be used to restore a DB instance in just a few clicks.

Backups are stored in Object Storage Service (OBS) buckets, which provides disaster recovery capabilities and save space. When you create a DB instance, the automated backup policy is enabled by default. After the creation is complete, an automated full backup is triggered instantly. The backup retention period is 7 days by default. You can set the backup retention period and modify the backup policy. In addition, you can initiate backup at any time according to your service requirements. Manual backups are saved until you manually delete them.

High Security
-------------

**Network isolation**

GeminiDB uses Virtual Private Clouds (VPCs) and network security groups to keep DB instances isolated. VPCs allow you to define which IP addresses are allowed to access a given database. Running a DB instance in a VPC improves security. To further enhance database security, you can configure subnets and security groups to control access to DB instances.

**Access control**

VPC security groups can be configured with rules to control traffic to and from DB instances.

**Encryption**

GeminiDB uses Secure Sockets Layer (SSL) to encrypt transmitted data. You can download the root CA certificate from the management console and upload it for authentication when connecting to a database.

**Security**

GeminiDB supports multi-layer network protection. The security system consists of VPCs, subnets, security groups, Anti-DDoS, and SSL, which collectively can defend against a wide range of attacks and keep your data secure.

-  VPCs isolate resources and control access.
-  SSL connections ensure data security and integrity.
-  Security group rules control traffic to and from specific IP addresses and ports, protecting connections between GeminiDB and other services.

**Performance monitoring**

GeminiDB monitors instance performance, reducing 60% of O&M activities. It provides real-time monitoring information about CPU utilization, disk usage, IOPS, and number of active connections, allowing you to check instance status at any time.

Convenience
-----------

**Ready to use out of the box**

You can create a DB instance on the management console and access the database over a private network to reduce latency and avoid the cost of using a public network.

Scalability
-----------

As a distributed database service with decoupled compute and storage architecture, GeminiDB supports minute-level compute node expansion and second-level storage expansion.
