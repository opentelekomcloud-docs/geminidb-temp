:original_name: BatchTagAction.html

.. _BatchTagAction:

Adding or Deleting Resource Tags in Batches
===========================================

Function
--------

This API is used to add tags to or delete tags from a specified DB instance in batches.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

A maximum of 20 tags can be added to an instance. The tag key must be unique.

If the request body contains duplicated keys, an error message will be reported when the API is called.

If the key in the request body is the same as an existing key in a specified instance, the value of the **value** parameter that corresponds to the existing key is overwritten.

If the tag to be deleted does not exist, the system deems the deletion operation successful by default but does not check whether the tag key and value meets character set rules.

URI
---

POST https://{Endpoint}/v3/{project_id}/instances/{instance_id}/tags/action

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

   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                              | Description                                      |
   +=================+=================+===================================================================================================+==================================================+
   | action          | Yes             | String                                                                                            | Operation identifier. The value can be:          |
   |                 |                 |                                                                                                   |                                                  |
   |                 |                 |                                                                                                   | -  **create**, indicating that tags are added.   |
   |                 |                 |                                                                                                   | -  **delete**, indicating that tags are deleted. |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------+
   | tags            | Yes             | Array of :ref:`BatchTagActionTagOption <batchtagaction__request_batchtagactiontagoption>` objects | All tags                                         |
   +-----------------+-----------------+---------------------------------------------------------------------------------------------------+--------------------------------------------------+

.. _batchtagaction__request_batchtagactiontagoption:

.. table:: **Table 4** BatchTagActionTagOption

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                   |
   +=================+=================+=================+===============================================================================================================================================================================================+
   | key             | Yes             | String          | Tag key. It can contain a maximum of 36 Unicode characters. The **key** value cannot be **null**, an empty string, or spaces. Before using **key**, delete spaces before and after the value. |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | It is case-sensitive and can contain digits, letters, underscores (_), and hyphens (-).                                                                                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Tag value. The tag value can contain a maximum of 43 Unicode characters and can be an empty string.                                                                                           |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | It is case-sensitive and can contain digits, letters, underscores (_), and hyphens (-).                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | -  If **action** is set to **create**, this parameter is mandatory.                                                                                                                           |
   |                 |                 |                 | -  If **action** is set to **delete**, this parameter is optional.                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 | .. note::                                                                                                                                                                                     |
   |                 |                 |                 |                                                                                                                                                                                               |
   |                 |                 |                 |    If **value** is specified, tags are deleted by key and value. If **value** is not specified, tags are deleted by key.                                                                      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

No response parameters

Example Requests
----------------

-  URI example

   .. code-block:: text

      POST https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02/tags/action

-  Adding two tags

   .. code-block::

      {
        "action" : "create",
        "tags" : [ {
          "key" : "key1",
          "value" : "value1"
        }, {
          "key" : "key2",
          "value" : "value2"
        } ]
      }

-  Deleting two tags

   .. code-block::

      {
        "action" : "delete",
        "tags" : [ {
          "key" : "key1"
        }, {
          "key" : "key2",
          "value" : "value3"
        } ]
      }

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   { }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
