:original_name: nosql_05_0006.html

.. _nosql_05_0006:

Replicating a Parameter Template
================================

Scenarios
---------

You can replicate a parameter template you have created. When you have already created a parameter template and want to include most of the custom parameters and values from that template in a new parameter template, you can replicate that parameter template. You can also export the parameter template to generate a new parameter template for future use.

Default parameter templates cannot be replicated, but you can create parameter templates based on the default templates provided.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. In the navigation pane on the left, click **Parameter Template Management**.

#. On the **Parameter Template Management** page, click the **Custom Templates** tab. Locate the target parameter template and click **Replicate** in the **Operation** column.

   Alternatively, click the target DB instance on the **Instance Management** page. On the **Parameters** page, click **Export** to generate a new parameter template for future use.

#. In the displayed dialog box, enter the parameter template name and description and click **OK**.

   -  The template name can be up to 64 characters long. It can contain only uppercase letters, lowercase letters, numbers, hyphens (-), underscores (_), and periods (.).
   -  The description contains a maximum of 256 characters and cannot include line breaks or the following special characters: >!<"&'=

   After the parameter template is replicated, a new template is generated in the list on the **Parameter Template Management** page.
