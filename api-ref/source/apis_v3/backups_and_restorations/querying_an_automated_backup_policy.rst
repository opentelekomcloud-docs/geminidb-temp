:original_name: nosql_api_0030.html

.. _nosql_api_0030:

Querying an Automated Backup Policy
===================================

Function
--------

This API is used to query an automated backup policy.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/backups/policy

.. table:: **Table 1** Path parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                    |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                       |
   +=================+=================+=================+===================================================================================================+
   | type            | No              | String          | Backup policy type. This parameter is available only to GaussDB(for Cassandra). The value can be: |
   |                 |                 |                 |                                                                                                   |
   |                 |                 |                 | -  **Instance**, indicating that an instance backup is queried.                                   |
   |                 |                 |                 | -  **DatabaseTable**, indicating that a database or table backup is queried.                      |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================+
   | backup_policy         | object                | Backup policy objects, including backup retention period (days) and start time For details, see :ref:`Table 5 <nosql_api_0030__response_showbackuppolicyresult>`.             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | database_tables       | Array of objects      | Database and table information in the backup. This parameter is available only to GaussDB(for Cassandra). For details, see :ref:`Table 6 <nosql_api_0030__table52261594347>`. |
   |                       |                       |                                                                                                                                                                               |
   |                       |                       | -  Keep this parameter empty or ignore it when you query an instance backup.                                                                                                  |
   |                       |                       | -  Remember to specify this parameter when you query a database or table backup (if any).                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_api_0030__response_showbackuppolicyresult:

.. table:: **Table 5** ShowBackupPolicyResult

   +---------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Type    | Description                                                                                                                                                                                                                                                                                                                                                             |
   +=====================+=========+=========================================================================================================================================================================================================================================================================================================================================================================+
   | keep_days           | Integer | Backup retention days                                                                                                                                                                                                                                                                                                                                                   |
   +---------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | differential_period | String  | Differential backup interval. Interval for automatic differential backup. Its value can be **30**, **60**, **180**, **360**, **720**, or **1440**. The unit is minute. If the value is **0**, differential backup is disabled. Differential backup works based on incremental backup, and differential backup interval must be longer than incremental backup interval. |
   +---------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | incremental_period  | String  | Incremental backup interval, in minutes. If the value is **0**, incremental backup is disabled.                                                                                                                                                                                                                                                                         |
   +---------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time          | String  | Backup time window. Automated backup will be triggered during the backup time window.                                                                                                                                                                                                                                                                                   |
   +---------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | period              | String  | Backup period. After a backup period is specified, data will be automatically backed up on the selected days every week.                                                                                                                                                                                                                                                |
   +---------------------+---------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_api_0030__table52261594347:

.. table:: **Table 6** QueryDatabaseTableInfo

   +-----------------------+-----------------------+-------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                 |
   +=======================+=======================+=============================================================+
   | database_name         | String                | Database name                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------+
   | table_names           | Array of strings      | Table names.                                                |
   |                       |                       |                                                             |
   |                       |                       | -  If this parameter is empty, database names are queried.  |
   |                       |                       | -  If this parameter is not empty, table names are queried. |
   +-----------------------+-----------------------+-------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02/backups/policy?type=Instance

Example Responses
-----------------

**Status code: 200**

Success

Response when an automated backup policy is enabled

.. code-block::

   {
     "backup_policy" : {
       "keep_days" : 7,
       "start_time" : "19:00-20:00",
       "period" : "1,2,4,5,6",
       "incremental_period": "0",
       "differential_period": "0"
     },
      "database_tables" : [ {
        "database_name" : "databaseNameA",
        "table_names" : [ "table_A", "table_B" ]
      }, {
        "database_name" : "databaseNameB",
        "table_names" : null
      } ]
   }

Response when an automated backup policy is disabled

.. code-block::

   {
     "backup_policy" : {
       "keep_days" : 0
     }
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
