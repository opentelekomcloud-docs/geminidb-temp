:original_name: nosql_05_0008.html

.. _nosql_05_0008:

Applying a Parameter Template
=============================

Scenarios
---------

Modifications to parameters in a custom parameter template take effect for DB instances only after you have applied the template to the target DB instances.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. In the navigation pane on the left, click **Parameter Template Management**.

#. On the **Parameter Template Management** page, apply a default template or a custom template to a target DB instance:

   -  To apply a default template, click **Default Templates**, locate the target parameter template, and in the **Operation** column, click **Apply**.
   -  To apply a custom template, click **Custom Templates**, locate the target parameter template, and in the **Operation** column, choose **More** > **Apply**.

   A parameter template can be applied to one or more DB instances.

#. In the displayed dialog box, select one or more DB instances to which the parameter template will be applied and click **OK**.

   After a parameter template is applied, you can :ref:`view its application records <nosql_05_0009>`.
