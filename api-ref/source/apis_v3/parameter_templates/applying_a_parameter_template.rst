:original_name: nosql_06_0005.html

.. _nosql_06_0005:

Applying a Parameter Template
=============================

Function
--------

This API is used to apply a parameter template to one or more instances.

Constraints
-----------

This API supports GeminiDB Cassandra instances.

This API is an asynchronous API. A successful response does not indicate that the parameter template is successfully applied.

URI
---

PUT https://{Endpoint}/v3/{project_id}/configurations/{config_id}/apply

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

   ============ ========= ================ =============
   Parameter    Mandatory Type             Description
   ============ ========= ================ =============
   instance_ids Yes       Array of strings Instance IDs.
   ============ ========= ================ =============

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                       |
   +=======================+=======================+===================================================================================================+
   | job_id                | String                | ID of the asynchronous task that applies the parameter template.                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+
   | success               | Boolean               | Whether the task for applying the parameter template is successfully submitted. The value can be: |
   |                       |                       |                                                                                                   |
   |                       |                       | -  **true**, indicating the task is successfully submitted.                                       |
   |                       |                       | -  **false**, indicating the task fails to be submitted.                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations/e02e76567ae04662a2753492b77f965bpr06/apply

-  Applying a Parameter Template

   .. code-block::

      {
        "instance_ids" : [ "73ea2bf70c73497f89ee0ad4ee008aa2in06" ]
      }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "job_id" : "463b4b58-d0e8-4e2b-9560-5dea4552fde9",
     "success" : true
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
