:original_name: nosql_05_0003.html

.. _nosql_05_0003:

Modifying a Parameter Template
==============================

This section describes how to modify parameters in the parameter template that you have created to meet your service requirements and achieve optimal performance.

Note that parameter values in default parameter templates cannot be changed.

.. note::

   Though parameter values in a default template cannot be changed, you can view details about a default parameter template. If a custom parameter template is set incorrectly, the database startup may fail. You can re-configure the custom parameter template according to the configurations of the default parameter template.

Modifying Parameters in Custom Parameter Template
-------------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. In the navigation pane on the left, choose **Parameter Template Management**.

#. In the navigation pane on the left, choose **Parameter Template Management**. On the **Custom Templates** tab, click the parameter template you wish to modify.

#. Change parameter values as required.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After parameters are modified, click **Change History** to view parameter modification details.

   For details about how to view parameter modification details, see :ref:`Viewing Parameter Change History <nosql_05_0012>`.

   .. important::

      -  The modifications take effect only after you apply the parameter template to DB instances. For details, see :ref:`Applying a Parameter Template <nosql_05_0008>`.
      -  The change history page displays only the modifications of the last seven days.

Modifying Parameters of a Specified DB Instance
-----------------------------------------------

#. :ref:`Log in to the GeminiDB console. <nosql_login>`

#. In the navigation pane on the left, choose **Instance Management**. On the displayed page, click the target DB instance.

#. In the navigation pane on the left, choose **Parameters**. On the displayed page, modify parameters as required.

   -  To save the modifications, click **Save**.
   -  To cancel the modifications, click **Cancel**.
   -  To preview the modifications, click **Preview**.

#. After parameters are modified, click **Change History** to view parameter modification details.

   For how to view parameter modification details, see :ref:`Viewing Parameter Change History <nosql_05_0012>`.

   .. important::

      After you modify instance parameters, the modifications immediately take effect for the instance.

      Check the value in the **Effective upon Restart** column.

      -  If the value is **Yes** and the DB instance status on the **Instance Management** page is **Pending restart**, you must restart the DB instance for the modifications to take effect.
      -  If the value is **No**, the modifications take effect immediately.
