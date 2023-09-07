:original_name: nosql_03_0018.html

.. _nosql_03_0018:

Querying Traces
===============

After CTS is enabled, the tracker starts recording operations on cloud resources. Operation records for the last 7 days are stored on the CTS console.

This section describes how to query operation records for the last 7 days on the CTS console.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and a project.
#. Click **Service List**. Under **Management & Deployment**, click **Cloud Trace Service**.
#. Choose **Trace List** in the navigation pane on the left.
#. Specify the filters used for querying traces. The following four filters are available:

   -  **Trace Source**, **Resource Type**, **Search By**, and **Operator**

      Select the filter from the drop-down list.

      When you select **Trace name** for **Search By**, you also need to select a specific trace name.

      When you select **Resource ID** for **Search By**, you also need to select or enter a specific resource ID.

      When you select **Resource name** for **Search By**, you also need to select or enter a specific resource name.

   -  **Operator**: Select a specific operator (a user rather than tenant).

   -  **Trace Status**: Available options include **All trace statuses**, **normal**, **warning**, and **incident**. You can only select one of them.

   -  Start time and end time: You can specify the time period for query traces.

#. Click |image2| to the left of the record to be queried to extend its details.
#. Locate a trace and click **View Trace** in the **Operation** column.

.. |image1| image:: /_static/images/en-us_image_0160430768.png
.. |image2| image:: /_static/images/en-us_image_0108820738.png
