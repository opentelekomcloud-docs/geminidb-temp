:original_name: nosql_projectid.html

.. _nosql_projectid:

Obtaining a Project ID
======================

Scenarios
---------

When calling APIs, you need to specify the project ID in some URLs. To do so, you need to obtain the project ID first.

You can obtain the required project ID with either of the following methods:

-  :ref:`Obtaining the Project ID by Calling an API <nosql_projectid__section18520151052413>`
-  :ref:`Obtaining a Project ID from the Console <nosql_projectid__section127010198244>`

.. _nosql_projectid__section18520151052413:

Obtaining the Project ID by Calling an API
------------------------------------------

You can obtain the project ID by calling the IAM API used to query project information based on specified criteria.

The API used to obtain a project ID is **GET https://{Endpoint}/v3/projects/**. **{Endpoint}** is the IAM endpoint and can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__. For details about API authentication, see :ref:`Authentication <nosql_05_0009>`.

The following is an example response. The value of **id** is the project ID.

.. code-block::

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180d14e684b",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d14e684b",
               "name": "project_name",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
               },
               "id": "a4a5d4098fb4474fa22cd05f897d6b99",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }

.. _nosql_projectid__section127010198244:

Obtaining a Project ID from the Console
---------------------------------------

#. Sign up and log in to the management console.

#. Move your pointer over the username and select **My Credentials** in the displayed drop-down list.

   On the **Projects** tab page, view project IDs.


   .. figure:: /_static/images/en-us_image_0000001354858484.jpg
      :alt: **Figure 1** Viewing project IDs

      **Figure 1** Viewing project IDs
