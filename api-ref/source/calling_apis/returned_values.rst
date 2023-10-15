:original_name: nosql_05_0010.html

.. _nosql_05_0010:

Returned Values
===============

Status Code
-----------

After you send a request, you will receive a response, including a status code, response header, and response body.

A status code is a group of digits ranging from 1xx to 5xx. It indicates the status of a response. For more information, see :ref:`Status Codes <nosql_status_code>`.

If status code 201 is returned for calling the API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__, the request is successful.

Response Header
---------------

Similar to a request, a response also has a header, for example, **Content-Type**.

:ref:`Figure 1 <nosql_05_0010__en-us_topic_0170155703_fig4865141011511>` shows the response header for the API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__, in which **x-subject-token** is the required user token. Then, this token can be used to authenticate the calling of other APIs.

.. _nosql_05_0010__en-us_topic_0170155703_fig4865141011511:

.. figure:: /_static/images/en-us_image_0000001355018024.png
   :alt: **Figure 1** Response header for the API used to obtain a user token

   **Figure 1** Response header for the API used to obtain a user token

(Optional) Response Body
------------------------

This part is optional. A response body is generally returned in a structured format (for example, JSON or XML), corresponding to **Content-Type** in the response header, and is used to transfer content other than the response header.

If the following information is returned for calling the API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__, the request is successful. The following describes part of the request body.

.. code-block::

   {
       "token": {
           "expires_at": "2019-02-13T06:52:13.855000Z",
           "methods": [
               "password"
           ],
           "catalog": [
               {
                   "endpoints": [
                       {
                           "region_id": "aaa",
   ......

If an error occurs during API calling, an error code and error message will be displayed. The following is an error response body:

.. code-block::

   {
       "error_msg": "Parameter error",
       "error_code": "DBS.200001"
   }

In the response, **error_code** indicates an error code, and **error_msg** describes the error.
