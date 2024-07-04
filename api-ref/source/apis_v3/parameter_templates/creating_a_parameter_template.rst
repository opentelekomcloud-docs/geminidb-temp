:original_name: nosql_06_0003.html

.. _nosql_06_0003:

Creating a Parameter Template
=============================

Function
--------

This API is used to create a parameter template and configure the name, description, DB engine version, and parameter values in the parameter template.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

The new parameter template cannot have the same name as any existing parameter template.

For configuration item **values**, you can enter system-defined parameters that allow for modification.

URI
---

POST https://{Endpoint}/v3/{project_id}/configurations

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token.
   ============ ========= ====== ===========

.. table:: **Table 3** Request body parameters

   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type                                                                                             | Description                                                                                                                                                                          |
   +=============+===========+==================================================================================================+======================================================================================================================================================================================+
   | name        | Yes       | String                                                                                           | Parameter template name. It can include a maximum of 64 characters and can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.). |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String                                                                                           | Parameter template description. It can contain a maximum of 256 characters except the following special characters: >!<"&'= The value is left blank by default.                      |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values      | No        | Map<String,String>                                                                               | Parameter values defined by users based on a default parameter template. Keep the parameter values unchanged by default.                                                             |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | datastore   | Yes       | :ref:`ConfigurationDatastoreOption <nosql_06_0003__request_configurationdatastoreoption>` object | Database object.                                                                                                                                                                     |
   +-------------+-----------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _nosql_06_0003__request_configurationdatastoreoption:

.. table:: **Table 4** ConfigurationDatastoreOption

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                      |
   +=================+=================+=================+==================================================================================+
   | type            | Yes             | String          | Database type. The value can be:                                                 |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | **cassandra**, indicating that the instances are of the GeminiDB Cassandra type. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+
   | version         | Yes             | String          | Database version. The value can be:                                              |
   |                 |                 |                 |                                                                                  |
   |                 |                 |                 | **3.11**, indicating that GeminiDB Cassandra 3.11 is supported.                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 5** Response body parameters

   +---------------+---------------------------------------------------------------------------------+---------------------------------+
   | Parameter     | Type                                                                            | Description                     |
   +===============+=================================================================================+=================================+
   | configuration | :ref:`ConfigurationResult <nosql_06_0003__response_configurationresult>` object | Parameter template information. |
   +---------------+---------------------------------------------------------------------------------+---------------------------------+

.. _nosql_06_0003__response_configurationresult:

.. table:: **Table 6** ConfigurationResult

   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                  | Description                                                                                                |
   +========================+=======================+============================================================================================================+
   | id                     | String                | Parameter template ID.                                                                                     |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | name                   | String                | Parameter template name.                                                                                   |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_version_name | String                | Database version name.                                                                                     |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | datastore_name         | String                | Database name.                                                                                             |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | description            | String                | Parameter template description                                                                             |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | created                | String                | Creation time in the yyyy-MM-ddTHH:mm:ssZ format.                                                          |
   |                        |                       |                                                                                                            |
   |                        |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+
   | updated                | String                | Update time in the yyyy-MM-ddTHH:mm:ssZ format.                                                            |
   |                        |                       |                                                                                                            |
   |                        |                       | **T** is the separator between calendar and hourly notation of time. **Z** indicates the time zone offset. |
   +------------------------+-----------------------+------------------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations

-  Creating a parameter template for GeminiDB Cassandra instances

   .. code-block::

      {
        "name" : "configuration_test",
        "description" : "configuration_test",
        "values" : {
          "max_connections" : "10",
          "autocommit" : "OFF"
        },
        "datastore" : {
          "type" : "cassandra",
          "version" : "3.11"
        }
      }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "configuration" : {
       "id" : "463b4b58d0e84e2b95605dea4552fdpr06",
       "name" : "configuration_test",
       "datastore_version_name" : "3.11",
       "datastore_name" : "cassandra",
       "description" : "configuration_test",
       "created" : "2020-03-09T08:27:56+0800",
       "updated" : "2020-03-09T08:27:56+0800"
     }
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
