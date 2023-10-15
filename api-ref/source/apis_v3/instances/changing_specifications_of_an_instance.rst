:original_name: nosql_05_0100.html

.. _nosql_05_0100:

Changing Specifications of an Instance
======================================

Function
--------

This API is used to change specifications of an instance.

.. note::

   Services will be interrupted for 5 to 10 minutes when you change specifications of an instance. Exercise caution when performing this operation.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

This API can be used to scale up or down specifications of an instance.

The new specifications cannot be the same as the original specifications.

Specifications can be modified only when the instance status is **normal**.

If specifications cannot meet the requirements for running the instance, the specifications cannot be changed.

URI
---

PUT https://{Endpoint}/v3/{project_id}/instances/{instance_id}/resize

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

   +-----------+-----------+----------------------------------------------------------------------------------+----------------------------------+
   | Parameter | Mandatory | Type                                                                             | Description                      |
   +===========+===========+==================================================================================+==================================+
   | resize    | Yes       | :ref:`ResizeInstanceOption <nosql_05_0100__request_resizeinstanceoption>` object | Target specification information |
   +-----------+-----------+----------------------------------------------------------------------------------+----------------------------------+

.. _nosql_05_0100__request_resizeinstanceoption:

.. table:: **Table 4** ResizeInstanceOption

   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                        |
   +==================+=================+=================+====================================================================================================================================================+
   | target_spec_code | Yes             | String          | Target resource specification code.                                                                                                                |
   |                  |                 |                 |                                                                                                                                                    |
   |                  |                 |                 | For the code, see the value of response parameter **flavors.spec_code** in :ref:`Querying Instance Specifications <nosql_instance_specification>`. |
   +------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameters

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   job_id    String Task ID
   ========= ====== ===========

Example Requests
----------------

-  URI example

   .. code-block:: text

      PUT https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in06/resize

-  Changing instance specifications to 16 vCPUs \| 64 GB

   .. code-block::

      {
        "resize" : {
          "target_spec_code" : "geminidb.cassandra.4xlarge.4"
        }
      }

Example Responses
-----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "job_id" : "3711e2ad-5787-49bc-a47f-3f0b066af9f5"
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
