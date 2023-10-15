:original_name: nosql_06_0002.html

.. _nosql_06_0002:

Obtaining Parameter Templates
=============================

Function
--------

This API is used to obtain parameter templates, including all of the default and custom parameter templates.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

URI
---

GET https://{Endpoint}/v3.1/{project_id}/configurations

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================================================================================================+
   | offset          | No              | Integer         | Index offset.                                                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                                                                   |
   |                 |                 |                 | -  If **offset** is set to **N**, the resource query starts from the N+1 piece of data. If **action** is set to **filter**, **offset** is set to **0** by default, indicating that the query starts from the first piece of data. |
   |                 |                 |                 | -  The value must be a positive integer.                                                                                                                                                                                          |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | Integer         | Maximum number of instances that can be queried.                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                   |
   |                 |                 |                 | -  The value ranges from **1** to **100**.                                                                                                                                                                                        |
   |                 |                 |                 | -  If this parameter is not transferred, the first 100 records are queried by default.                                                                                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

   +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Parameter      | Type                                                                                                | Description                                                          |
   +================+=====================================================================================================+======================================================================+
   | count          | Integer                                                                                             | Total number of records                                              |
   +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | quota          | Integer                                                                                             | Maximum number of custom parameter templates that a user can create. |
   +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | configurations | Array of :ref:`ListConfigurationsResult <nosql_06_0002__response_listconfigurationsresult>` objects | Parameter templates                                                  |
   +----------------+-----------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+

.. _nosql_06_0002__response_listconfigurationsresult:

.. table:: **Table 5** ListConfigurationsResult

   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                |
   +========================+=======================+============================================================================================================+
   | id                     | String                | Parameter template ID                                                                                      |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | name                   | String                | Parameter template name                                                                                    |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | description            | String                | Parameter template description                                                                             |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_version_name | String                | Database version name                                                                                      |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_name         | String                | Database name                                                                                              |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | created                | String                | Creation time in the yyyy-MM-ddTHH:mm:ssZ format.                                                          |
   |                        |                       |                                                                                                            |
   |                        |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | updated                | String                | Update time in the yyyy-MM-ddTHH:mm:ssZ format.                                                            |
   |                        |                       |                                                                                                            |
   |                        |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | mode                   | String                | Instance type. The value can be:                                                                           |
   |                        |                       |                                                                                                            |
   |                        |                       | **Cluster**, indicating that the instance is of the GaussDB(for Cassandra) cluster type.                   |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | user_defined           | Boolean               | Whether the parameter template is a custom template. The value can be:                                     |
   |                        |                       |                                                                                                            |
   |                        |                       | -  **false**, indicating that the parameter template is a default parameter template.                      |
   |                        |                       | -  **true**, indicating that the parameter template is a custom template.                                  |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3.1/375d8d8fad1f43039e23d3b6c0f60a19/configurations?offset=0&limit=10

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "count" : 2,
     "quota": 100,
     "configurations" : [ {
       "id" : "887ea0d1bb0843c49e8d8e5a09a95652pr06",
       "name" : "configuration_test",
       "description" : "configuration_test",
       "datastore_version_name" : "3.11",
       "datastore_name" : "cassandra",
       "created" : "2019-05-15T11:53:34+0000",
       "updated" : "2019-05-15T11:53:34+0000",
       "mode": "Cluster",
       "user_defined" : true
     }, {
       "id" : "3bc1e9cc0d34404b9225ed7a58fb284epr06",
       "name" : "Default-Cassandra-3.11",
       "description" : "Default parameter group for cassandra 3.11",
       "datastore_version_name" : "3.11",
       "datastore_name" : "cassandra",
       "created" : "2019-05-27T03:38:51+0000",
       "updated" : "2019-05-27T03:38:51+0000",
       "mode": "Cluster",
       "user_defined" : false
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
