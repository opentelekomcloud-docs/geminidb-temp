:original_name: nosql_06_0006.html

.. _nosql_06_0006:

Modifying Parameters of a Specified Instance
============================================

Function
--------

This API is used to modify parameters of a specified instance.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

For configuration item **values**, you can enter system-defined parameters that allow for modification.

This API is an asynchronous API. A successful response does not indicate that the parameters are successfully modified.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/configurations

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

   +-----------+-----------+--------------------+-------------------------------------------------------------------------+
   | Parameter | Mandatory | Type               | Description                                                             |
   +===========+===========+====================+=========================================================================+
   | values    | Yes       | Map<String,String> | Parameter values defined by users based on a default parameter template |
   +-----------+-----------+--------------------+-------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                              |
   +=======================+=======================+==========================================================================+
   | job_id                | String                | ID of the asynchronous task for modifying instance parameters            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+
   | restart_required      | Boolean               | Whether the instance needs to be restarted. The value can be:            |
   |                       |                       |                                                                          |
   |                       |                       | -  **true**: indicates that the instance needs to be restarted.          |
   |                       |                       | -  **false**: indicates that the instance does not need to be restarted. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------+

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/054e292c9880d4992f02c0196d3ea468/instances/3d39c18788b54a919bab633874c159dfin01/configurations

-  Modifying Parameters of a Specified Instance

   .. code-block::

      {
        "values" : {
          "concurrent_reads" : "64"
        }
      }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "job_id" : "463b4b58-d0e8-4e2b-9560-5dea4552fde9",
     "restart_required" : false
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
