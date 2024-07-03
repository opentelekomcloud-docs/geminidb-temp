:original_name: nosql_01_0009.html

.. _nosql_01_0009:

Related Services
================

:ref:`Table 1 <nosql_01_0009__table4822192916310>` shows the relationship between GeminiDB and other services.

.. _nosql_01_0009__table4822192916310:

.. table:: **Table 1** Relationship between GeminiDB and other services

   +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Service   | Description                                                                                                                                                                                                                                  |
   +===========+==============================================================================================================================================================================================================================================+
   | ECS       | Elastic Cloud Server (ECS) provides GeminiDB with elastic computing resources and a running environment for DB instances.                                                                                                                    |
   +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | VPC       | GeminiDB uses Virtual Private Clouds (VPCs) and network security groups to keep DB instances isolated. VPCs allow you to define which IP addresses are allowed to access a given database. Running a DB instance in a VPC improves security. |
   +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | EIP       | The Elastic IP (EIP) service provides independent public IP addresses and bandwidth for Internet access.                                                                                                                                     |
   +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | OBS       | Backups are stored in Object Storage Service (OBS) to allow for disaster recovery and save space.                                                                                                                                            |
   +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | TMS       | Tag Management Service (TMS) enables you to use tags on the management console to manage resources. TMS works with other cloud services to manage tags. TMS manages tags globally and other cloud services manage their own tags.            |
   +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Cloud Eye | Cloud Eye serves as an open monitoring platform, monitoring GeminiDB resources for you. It reports alarms and issues warnings promptly to ensure that services are running properly.                                                         |
   +-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
