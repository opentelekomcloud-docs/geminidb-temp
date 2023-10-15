:original_name: ListSlowLogs.html

.. _ListSlowLogs:

Querying Database Slow Logs
===========================

Function
--------

This API is used to query the latest 2,000 slow query logs of an instance. Searching by keyword is not supported.

Constraints
-----------

-  This API supports GaussDB(for Cassandra) instances.
-  This API can be used to query only the latest 2000 slow query logs in a specified time range.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/slowlog

.. table:: **Table 1** Path parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID                                                                                                    |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                 |
   +=================+=================+=================+=============================================================================================================================================================================================================================+
   | start_date      | Yes             | String          | Start time in the yyyy-mm-ddThh:mm:ssZ format.                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset.                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | The start time is at most 30 days earlier than the current time.                                                                                                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_date        | Yes             | String          | End time in the yyyy-mm-ddThh:mm:ssZ format.                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. You can only query slow query logs generated in the last one month.                                              |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | The end time cannot be later than the current time.                                                                                                                                                                         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Index offset. Its value ranges from **0** to **1999**.                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | If **offset** is set to *N*, the resource query starts from the *N*\ +1 piece of data. The value is **0** by default, indicating that the query starts from the first piece of data. The value cannot be a negative number. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Number of records to be queried. The value ranges from **1** to **100**.                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | The sum of values of **limit** and **offset** must be 2000 or lower.                                                                                                                                                        |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | node_id         | No              | String          | Node ID. If this parameter is not specified, all nodes of the instance are queried.                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | For details about the value, see **id** in table :ref:`Table 10 <nosql_05_0016__response_listinstancesnoderesult>` in :ref:`Querying Instances and Details <nosql_05_0016>`.                                                |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String          | SQL statement type. If this parameter is not specified, all types of SQL statements are queried. You can also specify the following log type:                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                             |
   |                 |                 |                 | -  SELECT                                                                                                                                                                                                                   |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +---------------+------------------------------------------------------------------------------+-----------------------------------+
   | Parameter     | Type                                                                         | Description                       |
   +===============+==============================================================================+===================================+
   | slow_log_list | Array of :ref:`SlowlogResult <listslowlogs__response_slowlogresult>` objects | Information about slow query logs |
   +---------------+------------------------------------------------------------------------------+-----------------------------------+
   | total_record  | Integer                                                                      | Total number of records           |
   +---------------+------------------------------------------------------------------------------+-----------------------------------+

.. _listslowlogs__response_slowlogresult:

.. table:: **Table 5** SlowlogResult

   ============ ====== ========================================
   Parameter    Type   Description
   ============ ====== ========================================
   time         String Execution time
   database     String Database which slow query logs belong to
   query_sample String Execution syntax
   type         String SQL statement type
   start_time   String UTC time when logs are generated
   ============ ====== ========================================

Example Requests
----------------

-  URI example

   Querying slow query logs:

   .. code-block:: text

      GET https://{Endpoint}/v3/0483b6b16e954cb88930a360d2c4e663/instances/6ade8143870047b8999aba8f1891b48ein06/slowlog?start_date=2018-08-06T10:41:14+0800&end_date=2018-08-07T10:41:14+0800

-  URI example

   Querying slow query logs based on specified conditions:

   .. code-block:: text

      GET https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/instances/6ade8143870047b8999aba8f1891b48ein06/slowlog?type=SELECT&offset=1&limit=20&node_id=a7c84462483642798cf159237343135fno06&start_date=2018-08-06T10:41:14+0800&end_date=2018-08-07T10:41:14+0800

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "total_record" : 1,
     "slow_log_list" : [ {
       "time" : "513 ms",
       "database" : "cassandra",
       "query_sample" : "SELECT * FROM cassandra.sz_user_hw LIMIT 100;",
       "type" : "SELECT",
       "start_time" : "2020-11-15T22:49:38.643000Z"
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
