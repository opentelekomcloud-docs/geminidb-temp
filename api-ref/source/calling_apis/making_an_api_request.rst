:original_name: nosql_05_0008.html

.. _nosql_05_0008:

Making an API Request
=====================

This section describes the structure of a REST API, and uses the IAM API for `obtaining a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__ as an example to describe how to call an API. The obtained token is used to authenticate the calling of other APIs.

Request URI
-----------

A request URI consists of the following:

**{URI-scheme}://{Endpoint}/{resource-path}?{query-string}**

Although a request URI is included in the request header, most programming languages or frameworks require the request URI to be separately transmitted, rather than being conveyed in a request message separately.

.. table:: **Table 1** URI parameter description

   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Description                                                                                                                                                                                                                                                |
   +===============+============================================================================================================================================================================================================================================================+
   | URI-scheme    | Protocol used to transmit requests. All APIs use HTTPS.                                                                                                                                                                                                    |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Endpoint      | Domain name or IP address of the server bearing the REST service endpoint. The endpoint varies depending on services and regions. It can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.            |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource-path | Access path of an API for performing a specified operation. Obtain the path from the URI of the API. For example, the **resource-path** of the API for obtaining a user token is **/v3/auth/tokens**.                                                      |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query-string  | Query parameter, which is optional. Ensure that a question mark (?) is included before each query parameter that is in the format of "Parameter name=Parameter value". For example, **? limit=10** indicates that up to 10 data records will be displayed. |
   +---------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Methods
---------------

The HTTP protocol defines the following request methods that can be used to send a request to the server:

.. table:: **Table 2** HTTP methods

   +--------+----------------------------------------------------------------------------+
   | Method | Description                                                                |
   +========+============================================================================+
   | GET    | Requests a server to return specified resources.                           |
   +--------+----------------------------------------------------------------------------+
   | PUT    | Requests a server to update specified resources.                           |
   +--------+----------------------------------------------------------------------------+
   | POST   | Requests a server to add a resource or perform a special operation.        |
   +--------+----------------------------------------------------------------------------+
   | DELETE | Requests a server to delete a specified resource (for example, an object). |
   +--------+----------------------------------------------------------------------------+

For example, in the URI for `obtaining a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__, the request method is POST. The request is as follows:

.. code-block:: text

   POST https://{{endpoint}}/v3/auth/tokens

Request Header
--------------

You can also add additional header fields to a request, such as the fields required by a specified URI or HTTP method. For example, add **Content-Type** that defines a request body type to request for authentication information.

:ref:`Table 3 <nosql_05_0008__en-us_topic_0121682347_table1986821153312>` lists common request header fields.

.. _nosql_05_0008__en-us_topic_0121682347_table1986821153312:

.. table:: **Table 3** Common request headers

   +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+--------------------------------------------+
   | Parameter       | Description                                                                                                                                                        | Mandatory                                                                          | Example Value                              |
   +=================+====================================================================================================================================================================+====================================================================================+============================================+
   | Content-Type    | MIME type of the request body. Use the default value **application/json**. For APIs used to upload objects or images, the value varies depending on the flow type. | Yes                                                                                | application/json                           |
   +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+--------------------------------------------+
   | Content-Length  | Length of the request body. The unit is byte.                                                                                                                      | This field is optional for POST requests, but must be left blank for GET requests. | 3495                                       |
   +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+--------------------------------------------+
   | X-Project-Id    | Project ID. To obtain the project ID, see :ref:`Obtaining a Project ID <nosql_projectid>`.                                                                         | No                                                                                 | e9993fc787d94b6c886cbaa340f9c0f4           |
   +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+--------------------------------------------+
   | X-Auth-Token    | User token.                                                                                                                                                        | Yes                                                                                | The following is part of an example token: |
   |                 |                                                                                                                                                                    |                                                                                    |                                            |
   |                 | After a request is processed, the value of **X-Subject-Token** in the header is the token value.                                                                   |                                                                                    | MIIPAgYJKoZIhvcNAQcCo...ggg1BBIINPXsidG9rZ |
   +-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------+--------------------------------------------+

The API used to `obtain a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__ does not require authentication. Therefore, this API only requires adding the **Content-Type** field. The following is an example request:

.. code-block:: text

   POST https://{{endpoint}}/v3/auth/tokens
   Content-Type: application/json

(Optional) Request Body
-----------------------

This part is optional. The request body is often sent in a structured format (for example, JSON or XML) as specified in the **Content-Type** header field. If the request body contains full-width characters, these characters must be coded in UTF-8.

Request bodies vary depending on APIs. Some APIs do not require a request body, such as the APIs requested using the GET and DELETE methods.

For the API of `obtaining a user token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__, request parameters and parameter description can be obtained from the API request. The following is an example request with a body included. Replace *username*, *domianname*, ``********`` (login password), and *xxxxxxxxxxxxxxxxxx* (project name) with required values. You can obtain the values from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

.. note::

   The **scope** parameter specifies where a token takes effect. You can set **scope** to an account or a project under an account. In the following example, the token takes effect only for the resources in a specified project. For details, see `Obtaining a User Token <https://docs.otc.t-systems.com/identity-access-management/api-ref/apis/token_management/obtaining_a_user_token.html>`__.

.. code-block::

   POST https://{{endpoint}}/v3/auth/tokens
   Content-Type: application/json

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domianname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "name": "xxxxxxxxxxxxxxxxxx"
               }
           }
       }
   }

If all data required for the API request is available, you can send a request to call an API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding. For the API of obtaining a user token, **x-subject-token** in the response header is the required user token. Then, this token can be used to authenticate the calling of other APIs.
