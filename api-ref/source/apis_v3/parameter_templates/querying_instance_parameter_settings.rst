:original_name: nosql_06_0007.html

.. _nosql_06_0007:

Querying Instance Parameter Settings
====================================

Function
--------

This API is used to query instance parameter settings.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/configurations

.. table:: **Table 1** Path parameters

   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                    |
   +=============+===========+========+================================================================================================================+
   | project_id  | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | instance_id | Yes       | String | Instance ID.                                                                                                   |
   +-------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter                | Type                                                                                                        | Description                                                                                                |
   +==========================+=============================================================================================================+============================================================================================================+
   | datastore_version_name   | String                                                                                                      | Database version name.                                                                                     |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_name           | String                                                                                                      | Database name.                                                                                             |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | created                  | String                                                                                                      | Creation time in the yyyy-MM-ddTHH:mm:ssZ format.                                                          |
   |                          |                                                                                                             |                                                                                                            |
   |                          |                                                                                                             | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | updated                  | String                                                                                                      | Update time in the yyyy-MM-ddTHH:mm:ssZ format.                                                            |
   |                          |                                                                                                             |                                                                                                            |
   |                          |                                                                                                             | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | id                       | String                                                                                                      | Parameter template ID.                                                                                     |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | mode                     | String                                                                                                      | Instance type. The value can be:                                                                           |
   |                          |                                                                                                             |                                                                                                            |
   |                          |                                                                                                             | **Cluster**, indicating that the instance is of the GeminiDB Cassandra cluster type.                       |
   |                          |                                                                                                             |                                                                                                            |
   |                          |                                                                                                             | **Cluster**, indicating that the instance is of the GeminiDB Influx cluster type.                          |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+
   | configuration_parameters | Array of :ref:`ConfigurationParameterResult <nosql_06_0007__response_configurationparameterresult>` objects | Parameters defined by users based on a default parameter template.                                         |
   +--------------------------+-------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------+

.. _nosql_06_0007__response_configurationparameterresult:

.. table:: **Table 4** ConfigurationParameterResult

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                     |
   +=======================+=======================+=================================================================================================================================================+
   | name                  | String                | Parameter name.                                                                                                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | value                 | String                | Parameter value.                                                                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | restart_required      | Boolean               | Whether the instance needs to be restarted. The value can be:                                                                                   |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  **false**, indicating that the instance does not need to be restarted.                                                                       |
   |                       |                       | -  **true**, indicating that the instance needs to be restarted.                                                                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | readonly              | Boolean               | Whether the parameter is read-only. The value can be:                                                                                           |
   |                       |                       |                                                                                                                                                 |
   |                       |                       | -  **false**, indicating that the parameter is not read-only.                                                                                   |
   |                       |                       | -  **true**, indicating that the parameter is read-only.                                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | value_range           | String                | Value range. For example, the value of the Integer type ranges from **0** to **1**, and the value of the Boolean type is **true** or **false**. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                | Parameter type. The value can be **string**, **integer**, **boolean**, **list**, or **float**.                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Parameter description.                                                                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02/configurations

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "datastore_version_name" : "3.11",
     "datastore_name" : "cassandra",
     "created" : "2020-03-21 11:40:44",
     "updated" : "2020-03-21 11:40:44",
     "id": "9ad6bc82146e4043a50c963ab3bf09adpr06",
     "mode": "Cluster",
     "configuration_parameters" : [ {
       "name" : "concurrent_reads",
       "value" : "64",
       "restart_required" : true,
       "readonly" : true,
       "value_range" : "4-512",
       "type" : "integer",
       "description" : "Number of concurrent read threads."
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
