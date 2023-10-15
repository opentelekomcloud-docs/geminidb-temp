:original_name: nosql_06_0009.html

.. _nosql_06_0009:

Deleting a Parameter Template
=============================

Function
--------

This API is used to delete a specified parameter template.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

URI
---

DELETE https://{Endpoint}/v3/{project_id}/configurations/{config_id}

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                    |
   +============+===========+========+================================================================================================================+
   | project_id | Yes       | String | Project ID of a tenant in a region. To obtain this value, see :ref:`Obtaining a Project ID <nosql_projectid>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+
   | config_id  | Yes       | String | Parameter template ID                                                                                          |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   ============ ========= ====== ===========
   Parameter    Mandatory Type   Description
   ============ ========= ====== ===========
   X-Auth-Token Yes       String User token
   ============ ========= ====== ===========

Response Parameters
-------------------

**Status code: 200**

No response parameters

Example Requests
----------------

URI example

.. code-block:: text

   DELETE https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/configurations/e02e76567ae04662a2753492b77f965bpr06

Example Responses
-----------------

None

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
