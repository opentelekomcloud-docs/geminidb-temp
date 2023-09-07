:original_name: nosql_02_0010.html

.. _nosql_02_0010:

Creating a GaussDB(for Cassandra) Instance
==========================================

This section describes how to create a DB instance that is compatible with Cassandra APIs.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. On the **Instance Management** page, click **Create DB Instance**.
#. On the displayed page, select your DB instance specifications, and click **Create Now**.

   .. table:: **Table 1** Basic information

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                                                                                                                       |
      +===================================+===================================================================================================================================================================================================================================================================================================================================+
      | Region                            | The region where the tenant is located.                                                                                                                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   | .. important::                                                                                                                                                                                                                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   |    NOTICE:                                                                                                                                                                                                                                                                                                                        |
      |                                   |    Select the region nearest where you will be accessing the DB from so latency can be kept to a minimum and response time will be faster. Also, products deployed in different regions cannot communicate with each other through a private network and you cannot change the region of an instance after creating the instance. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Name                  | The new name can be the same as an existing instance name. It must start with a letter and consist of 4 to 64 characters. Only letters (case-sensitive), digits, hyphens (-), and underscores (_) are allowed.                                                                                                                    |
      |                                   |                                                                                                                                                                                                                                                                                                                                   |
      |                                   | After the DB instance is created, you can change the DB instance name. For details, see section :ref:`Changing a DB Instance Name <nosql_03_0025>`.                                                                                                                                                                               |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Compatible API                    | Cassandra                                                                                                                                                                                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Instance Type                  | Cluster                                                                                                                                                                                                                                                                                                                           |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | DB Engine Version                 | 3.11                                                                                                                                                                                                                                                                                                                              |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AZ                                | An AZ is a part of a region with its own independent power supplies and networks. AZs are physically isolated but can communicate through an internal network connection.                                                                                                                                                         |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 2** Specifications and storage

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                         |
      +===================================+=====================================================================================================================================================================================================================+
      | Instance Specifications           | The CPU and memory of a DB instance.                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                     |
      |                                   | Different performance specifications support different numbers of connections and maximum IOPSs. Select CPU and memory specifications based on your service requirements.                                           |
      |                                   |                                                                                                                                                                                                                     |
      |                                   | After a DB instance is created, you can change its CPU and memory. For details, see :ref:`Changing a DB Instance Class <nosql_03_0026>`.                                                                            |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nodes                             | The number of nodes ranges from 3 to 200. Select the number of nodes based on the site requirements.                                                                                                                |
      |                                   |                                                                                                                                                                                                                     |
      |                                   | After a DB instance is created, you can add nodes. For details, see :ref:`Adding Nodes <nosql_increase_nodes>`.                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Storage Space                     | Storage space depends on the instance specifications. The minimum storage space is 100 GB, and the storage space you set must be an integer. You can select a minimum of 1 GB each time you scale up storage space. |
      |                                   |                                                                                                                                                                                                                     |
      |                                   | After a DB instance is created, you can scale up its storage space. For details, see :ref:`Scaling Up Storage Space <nosql_increase_storage>`.                                                                      |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 3** Network

      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                              |
      +===================================+==========================================================================================================================================================================================+
      | VPC                               | The virtual network where your DB instances are located. A VPC isolates networks for different services. You can select an existing VPC or create a VPC.                                 |
      |                                   |                                                                                                                                                                                          |
      |                                   | If there are no VPCs available, the system allocates resources to you by default.                                                                                                        |
      |                                   |                                                                                                                                                                                          |
      |                                   | For details on how to create a subnet, see the "Creating a VPC" section in the *Virtual Private Cloud User Guide*.                                                                       |
      |                                   |                                                                                                                                                                                          |
      |                                   | .. note::                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                          |
      |                                   |    After the GaussDB(for Cassandra) instance is created, the VPC where the instance resides cannot be changed.                                                                           |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Subnet                            | A subnet provides dedicated network resources that are logically isolated from other networks for network security.                                                                      |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Security Group                    | A security group controls access between GaussDB NoSQL instances and other services. When you select a security group, you must ensure that it allows the client to access DB instances. |
      |                                   |                                                                                                                                                                                          |
      |                                   | If there are no security groups available, the system allocates resources to you by default.                                                                                             |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 4** Database configuration

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                 |
      +===================================+=============================================================================================================================================================================+
      | Administrator                     | The default administrator account is **rwuser**.                                                                                                                            |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Administrator Password            | Set a password for the administrator. The password:                                                                                                                         |
      |                                   |                                                                                                                                                                             |
      |                                   | -  Must be 8 to 32 characters long.                                                                                                                                         |
      |                                   | -  Must contain uppercase letters, lowercase letters, digits, and any of the following special characters: ``~!@#%^*-_=+?``                                                 |
      |                                   | -  For security reasons, you must select a strong password. The system will verify the password strength.                                                                   |
      |                                   |                                                                                                                                                                             |
      |                                   | Keep this password secure. If you lose it, the system cannot retrieve it.                                                                                                   |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Confirm Password                  | Enter the administrator password again.                                                                                                                                     |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter Template                | A parameter template contains engine configuration values that can be applied to one or more instances.                                                                     |
      |                                   |                                                                                                                                                                             |
      |                                   | After a DB instance is created, you can modify parameters to better meet your service requirements. For details, see :ref:`Modifying a Parameter Template <nosql_05_0003>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. table:: **Table 5** Tags

      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                           |
      +===================================+=======================================================================================================================================================================================================================+
      | Tags                              | The setting is optional. Adding tags helps you better identify and manage your DB instances. Each DB instance can have up to 20 tags.                                                                                 |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | A tag is composed of a key-value pair.                                                                                                                                                                                |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | -  Key: Mandatory if the DB instance is going to be tagged                                                                                                                                                            |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    Each tag key must be unique for each DB instance. The key can include up to 36 characters, including digits, letters, underscores (_), and hyphens (-).                                                            |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | -  Value: Optional if the DB instance is going to be tagged                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                                       |
      |                                   |    The value can contain up to 43 characters, including digits, letters, underscores (_), periods (.), and hyphens (-).                                                                                               |
      |                                   |                                                                                                                                                                                                                       |
      |                                   | After a DB instance is created, you can view its tag details on the **Tags** tab. In addition, you can add, modify, and delete tags for existing DB instances. For details, see :ref:`Managing Tags <nosql_03_0014>`. |
      +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. On the displayed page, confirm the DB instance details.

   -  If you need to modify the specifications, click **Previous** to return to the previous page.
   -  If you do not need to modify the specifications, click **Submit** to start creating the instance.

#. On the **Instance Management** page, view and manage your DB instances.

   -  Creating a DB instance takes about 5 to 9 minutes. During the process, the instance status displayed in the DB instance list is **Creating**.

   -  After the creation is complete, the status changes to **Available**.

      You can click |image1| in the upper right corner of the page to refresh the DB instance statuses.

   -  During creation, an automated backup policy is enabled by default. A full backup is automatically triggered after a DB instance is created.

.. |image1| image:: /_static/images/en-us_image_0000001139224537.png
