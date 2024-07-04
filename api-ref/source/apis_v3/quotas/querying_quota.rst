:original_name: ShowQuotas.html

.. _ShowQuotas:

Querying Quota
==============

Function
--------

This API is used to query GeminiDB resource quotas of a tenant.

URI
---

GET https://{Endpoint}/v3/{project_id}/quotas

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

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------+--------------------------------------------------------------------------------------------------+--------------------+
   | Parameter | Type                                                                                             | Description        |
   +===========+==================================================================================================+====================+
   | quotas    | :ref:`ShowResourcesListResponseBody <showquotas__response_showresourceslistresponsebody>` object | Quota information. |
   +-----------+--------------------------------------------------------------------------------------------------+--------------------+

.. _showquotas__response_showresourceslistresponsebody:

.. table:: **Table 4** ShowResourcesListResponseBody

   +-----------+----------------------------------------------------------------------------------------------------------------+----------------+
   | Parameter | Type                                                                                                           | Description    |
   +===========+================================================================================================================+================+
   | resources | Array of :ref:`ShowResourcesDetailResponseBody <showquotas__response_showresourcesdetailresponsebody>` objects | All resources. |
   +-----------+----------------------------------------------------------------------------------------------------------------+----------------+

.. _showquotas__response_showresourcesdetailresponsebody:

.. table:: **Table 5** ShowResourcesDetailResponseBody

   +-----------------------+-----------------------+----------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                |
   +=======================+=======================+============================================================================+
   | type                  | String                | Quota resource type. Only the instance type is supported.                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------+
   | quota                 | Integer               | Current quota.                                                             |
   |                       |                       |                                                                            |
   |                       |                       | If this parameter is set to **0**, no quantity limit is set for resources. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------+
   | used                  | Integer               | Number of used resources.                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------+

Example Requests
----------------

URI example

.. code-block:: text

   GET https://{Endpoint}/v3/0549b4a43100d4f32f51c01c2fe4acdb/quotas

Example Responses
-----------------

**Status code: 200**

Success

.. code-block::

   {
     "quotas" : {
       "resources" : [ {
         "type" : "instance",
         "quota" : 200,
         "used" : 58
       } ]
     }
   }

Status Codes
------------

For details, see :ref:`Status Codes <nosql_status_code>`.

Error Codes
-----------

For details, see :ref:`Error Codes <nosql_error_code>`.
