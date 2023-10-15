:original_name: ListInstanceTags.html

.. _ListInstanceTags:

Querying Tags of an Instance
============================

Function
--------

This API is used to query tags of a specified instance.

Constraints
-----------

This API supports GaussDB(for Cassandra) instances.

A maximum of 20 tags can be added to a DB instance. The tag key must be unique.

URI
---

GET https://{Endpoint}/v3/{project_id}/instances/{instance_id}/tags

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+----------------------------------------------------------------------------------------------------+----------------------+
   | Parameter | Type                                                                                               | Description          |
   +===========+====================================================================================================+======================+
   | tags      | Array of :ref:`ListInstanceTagsResult <listinstancetags__response_listinstancetagsresult>` objects | Tags of the instance |
   +-----------+----------------------------------------------------------------------------------------------------+----------------------+

.. _listinstancetags__response_listinstancetagsresult:

.. table:: **Table 4** ListInstanceTagsResult

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                         |
   +=======================+=======================+=====================================================================================================+
   | key                   | String                | Tag key. The tag key can contain a maximum of 36 Unicode characters and must be specified.          |
   |                       |                       |                                                                                                     |
   |                       |                       | It is case-sensitive and can contain digits, letters, underscores (_), and hyphens (-).             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+
   | value                 | String                | Tag value. The tag value can contain a maximum of 43 Unicode characters and can be an empty string. |
   |                       |                       |                                                                                                     |
   |                       |                       | It is case-sensitive and can contain digits, letters, underscores (_), and hyphens (-).             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3/375d8d8fad1f43039e23d3b6c0f60a19/instances/9136fd2a9fcd405ea4674276ce36dae8in02/tags

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "tags" : [ {
       "key" : "key1",
       "value" : "value1"
     }, {
       "key" : "key2",
       "value" : "value2"
     } ]
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
