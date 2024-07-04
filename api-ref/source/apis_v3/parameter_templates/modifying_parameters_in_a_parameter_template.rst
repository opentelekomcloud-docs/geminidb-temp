:original_name: nosql_06_0004.html

.. _nosql_06_0004:

Modifying Parameters in a Parameter Template
============================================

Function
--------

This API is used to modify parameters in a specified parameter template, including parameter names, descriptions, and values.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

The modified parameter template name must be different from the name of any existing or default parameter template.

Default parameter templates cannot be modified.

For configuration item **values**, you can enter system-defined parameters that allow for modification.

URI
---

PUT https://{Endpoint}/v3/{project_id}/configurations/{config_id}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | config_id  | Yes       | String | Parameter template ID.                                                                                         |
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

   +-------------+-----------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type               | Description                                                                                                                                                                          |
   +=============+===========+====================+======================================================================================================================================================================================+
   | name        | No        | String             | Parameter template name. It can include a maximum of 64 characters and can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.). |
   +-------------+-----------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | No        | String             | Parameter template description. It can include a maximum of 256 characters and cannot contain the following special characters: >!<"&'= The value is left blank by default.          |
   +-------------+-----------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values      | No        | Map<String,String> | Parameter values defined by users based on a default parameter template. If this parameter is not specified, no parameter values are to be changed.                                  |
   +-------------+-----------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

No response parameters

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations/e02e76567ae04662a2753492b77f965bpr06

-  Modifying Parameters in a Parameter Template

   .. note::

      At least one parameter in the request body must be specified. Otherwise, the request cannot be delivered.

   .. code-block::

      {
        "name" : "configuration_test",
        "description" : "configuration_test",
        "values" : {
          "concurrent_reads" : "64"
        }
      }

Example Responses
-----------------

None

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
