:original_name: nosql_05_0009.html

.. _nosql_05_0009:

Authentication
==============

GaussDB NoSQL supports token-based authentication.

.. note::

   The validity period of a token is 24 hours. If a token is required, the system caches the token to avoid frequent calling.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to a request to get permissions for calling the API.

If you want to use a token for authentication, you need to obtain the user's token and add **X-Auth-Token** to the request header of the service API to make an API call.

.. code-block:: text

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "password",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                  "name": "xxxxxxxx"
                }
           }
       }
   }

After a token is obtained, add field **X-Auth-Token** to the request header to specify the token when other APIs are called. For example, if the token is **ABCDEFJ....**, add **X-Auth-Token: ABCDEFJ....** to a request header as follows:

.. code-block::


   POST https://{{Endpoint}}/v3/auth/projects
   Content-Type: application/json
   X-Auth-Token: ABCDEFJ....
