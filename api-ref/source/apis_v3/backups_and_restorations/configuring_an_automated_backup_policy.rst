:original_name: nosql_api_0031.html

.. _nosql_api_0031:

Configuring an Automated Backup Policy
======================================

Function
--------

This API is used to configuring an automated backup policy.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/backups/policy

.. table:: **Table 1** Path parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                    |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                          |
   +=================+=================+==================+======================================================================================================================================================================================+
   | backup_policy   | Yes             | object           | Backup policy objects, including backup retention period (days) and start time For details, see :ref:`Table 4 <nosql_api_0031__request_backuppolicy>`.                               |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database_tables | No              | Array of objects | Database and table information in the backup policy. This parameter is available only to GaussDB(for Cassandra). For details, see :ref:`Table 5 <nosql_api_0031__table53208596452>`. |
   |                 |                 |                  |                                                                                                                                                                                      |
   |                 |                 |                  | -  If this parameter is empty, an automated backup policy for an instance is set.                                                                                                    |
   |                 |                 |                  | -  If this parameter is not empty, an automated backup policy for a databases or table is set.                                                                                       |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_api_0031__request_backuppolicy:

.. table:: **Table 4** BackupPolicy

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                            |
   +=================+=================+=================+========================================================================================================================================================================================================================================================================+
   | keep_days       | Yes             | Integer         | Backup retention days.                                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                        |
   |                 |                 |                 | The value ranges from **0** to **35**. The value **0** indicates that the automated backup policy is disabled.                                                                                                                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time      | No              | String          | Backup time window. Automated backup will be triggered during the backup time window. This parameter is mandatory if the automated backup policy is enabled. If the policy is disabled, you do not need to transfer this parameter.                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                        |
   |                 |                 |                 | The value must be the UTC time in the hh:mm-HH:MM format.                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                                                                        |
   |                 |                 |                 | -  The **HH** value must be 1 greater than the **hh** value.                                                                                                                                                                                                           |
   |                 |                 |                 | -  The values of **mm** and **MM** must be the same and must be set to **00**, **15**, **30**, or **45**.                                                                                                                                                              |
   |                 |                 |                 | -  Example value: **23:00-00:00**                                                                                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period          | No              | String          | Backup period. After a backup period is specified, data will be automatically backed up on the selected days every week. This parameter is mandatory if the automated backup policy is enabled. If the policy is disabled, you do not need to transfer this parameter. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                        |
   |                 |                 |                 | The value is a list of digits separated by commas (,). Each digit indicates a day of the week. The restrictions on the backup period are as follows:                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                                        |
   |                 |                 |                 | -  If you set **keep_days** to **0**, this parameter is not transferred.                                                                                                                                                                                               |
   |                 |                 |                 | -  If you set **keep_days** to **1** to **6**, set this parameter to **1, 2, 3, 4, 5, 6, 7.**                                                                                                                                                                          |
   |                 |                 |                 | -  If you set **keep_days** to **7** to **35**, select at least one day of the week for the backup cycle. Example value: **1,2,3,4**                                                                                                                                   |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_api_0031__table53208596452:

.. table:: **Table 5** PutDatabaseTablePolicy

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                         |
   +=================+=================+==================+=====================================================================================+
   | database_name   | Yes             | String           | Database name                                                                       |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------+
   | table_names     | No              | Array of strings | Table names.                                                                        |
   |                 |                 |                  |                                                                                     |
   |                 |                 |                  | -  If this parameter is empty, a backup policy for an instance is set.              |
   |                 |                 |                  | -  If this parameter is not empty, a backup policy for a databases or table is set. |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

No response parameters

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02/backups/policy

-  Example request body

   Enabling or modifying the automated backup policy (Set **period** to **1**, **2**, **3**, **4**, **5**, and **6**, **start_time** to **01:00-02:00**, and **keep_days** to **7**.)

   .. code-block::

      {
        "backup_policy" : {
          "keep_days" : 7,
          "start_time" : "01:00-02:00",
          "period" : "1,2,3,4,5,6"
        },
         "database_tables" : [ {
           "database_name" : "databaseNameA",
           "table_names" : [ "table_A", "table_B" ]
         }, {
           "database_name" : "databaseNameB",
           "table_names" : null
         } ]
      }

   Disabling automated backup

   .. code-block::

      {
        "backup_policy" : {
          "keep_days" : 0
        }
      }

Example Responses
-----------------

**Status code: 204**

No Content

.. code-block::

   { }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
