:original_name: nosql_instance_specification.html

.. _nosql_instance_specification:

Querying Instance Specifications
================================

Function
--------

This API is used to query all instance specifications under a specified condition.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

URI
---

GET https://{Endpoint}/v3.1/{project_id}/flavors

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================================================================================================+
   | engine_name     | No              | String          | Database type. The value can be:                                                                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | -  **cassandra**, indicating that the instances are of the GaussDB(for Cassandra) type.                                                                                                                                    |
   |                 |                 |                 | -  If this parameter is not transferred, the default value is **cassandra**.                                                                                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | No              | Integer         | Index offset.                                                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | -  If **offset** is set to **N**, the resource query starts from the N+1 piece of data. If **action** is set to **filter**, **offset** is **0** by default, indicating that the query starts from the first piece of data. |
   |                 |                 |                 | -  The **offset** value must be a number but cannot be a negative number.                                                                                                                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum of specifications that can be queried                                                                                                                                                                              |
   |                 |                 |                 |                                                                                                                                                                                                                            |
   |                 |                 |                 | -  The value ranges from **1** to **100**.                                                                                                                                                                                 |
   |                 |                 |                 | -  If this parameter is not transferred, the first 100 pieces of specification information is queried by default.                                                                                                          |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +-------------+----------------------------------------------------------------------------------+-------------------------+
   | Parameter   | Type                                                                             | Description             |
   +=============+==================================================================================+=========================+
   | total_count | Integer                                                                          | Total number of records |
   +-------------+----------------------------------------------------------------------------------+-------------------------+
   | flavors     | Array of :ref:`Flavors <nosql_instance_specification__response_flavors>` objects | Instance specifications |
   +-------------+----------------------------------------------------------------------------------+-------------------------+

.. _nosql_instance_specification__response_flavors:

.. table:: **Table 5** Flavors

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                               |
   +=======================+=======================+===========================================================================================+
   | engine_name           | String                | Engine name                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | engine_version        | String                | Engine version                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | vcpus                 | String                | Number of vCPUs                                                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | ram                   | String                | Memory size in megabytes (MB)                                                             |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | spec_code             | String                | Resource specification code.                                                              |
   |                       |                       |                                                                                           |
   |                       |                       | Example: **geminidb.cassandra.8xlarge.4**                                                 |
   |                       |                       |                                                                                           |
   |                       |                       | .. note::                                                                                 |
   |                       |                       |                                                                                           |
   |                       |                       |    -  **geminidb.cassandra** indicates the instance is a GaussDB(for Cassandra) instance. |
   |                       |                       |    -  **8xlarge.4** indicates node specifications.                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | availability_zone     | Array of strings      | ID of the AZ that supports the specifications                                             |
   |                       |                       |                                                                                           |
   |                       |                       | .. note::                                                                                 |
   |                       |                       |                                                                                           |
   |                       |                       |    This parameter has been discarded. Do not use it.                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+
   | az_status             | Object                | The status of specifications in an AZ. The value can be:                                  |
   |                       |                       |                                                                                           |
   |                       |                       | -  **normal**, indicating that the specifications are on sale.                            |
   |                       |                       | -  **unsupported**, indicating that the specifications are not supported.                 |
   |                       |                       | -  **sellout**, indicating that the specifications are sold out.                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3.1/375d8d8fad1f43039e23d3b6c0f60a19/flavors?engine_name=cassandra&offset=0&limit=10

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "total_count" : 4,
     "flavors" : [ {
       "engine_name" : "cassandra",
       "engine_version" : "3.11",
       "vcpus" : "4",
       "ram" : "16",
       "spec_code" : "geminidb.cassandra.xlarge.4",
       "availability_zone" : [ "az1", "az2" ],
       "az_status" : {
         "az1" : "normal",
         "az2" : "unsupported"
       }
     }, {
       "engine_name" : "cassandra",
       "engine_version" : "3.11",
       "vcpus" : "8",
       "ram" : "32",
       "spec_code" : "geminidb.cassandra.2xlarge.4",
       "availability_zone" : [ "az1", "az2" ],
       "az_status" : {
         "az1" : "unsupported",
         "az2" : "normal"
       }
     }, {
       "engine_name" : "cassandra",
       "engine_version" : "3.11",
       "vcpus" : "16",
       "ram" : "64",
       "spec_code" : "geminidb.cassandra.4xlarge.4",
       "availability_zone" : [ "az1", "az2" ],
       "az_status" : {
         "az1" : "normal",
         "az2" : "sellout"
       }
     }, {
       "engine_name" : "cassandra",
       "engine_version" : "3.11",
       "vcpus" : "32",
       "ram" : "128",
       "spec_code" : "geminidb.cassandra.8xlarge.4",
       "availability_zone" : [ "az1", "az2" ],
       "az_status" : {
         "az1" : "normal",
         "az2" : "normal"
       }
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
