:original_name: nosql_05_0004.html

.. _nosql_05_0004:

Exporting a Parameter Template
==============================

Scenarios
---------

-  You can export a parameter template of a DB instance for future use. To learn how to apply the exported parameter template to a DB instance, refer to section :ref:`Applying a Parameter Template <nosql_05_0008>`.
-  You can export the parameter template details (parameter names, values, and descriptions) of a DB instance to a CSV file for review and analysis.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. In the navigation pane on the left, choose **Instance Management**. On the displayed page, click the target DB instance.
#. In the navigation pane on the left, choose **Parameters**. On the **Parameters** tab, above the parameter list, click **Export**.

   -  **Parameter Template**: You can export the parameters of the DB instance to a template for future use.

      In the displayed dialog box, configure required details and click **OK**.

      .. note::

         -  The template name can be up to 64 characters long. It can contain only uppercase letters, lowercase letters, numbers, hyphens (-), underscores (_), and periods (.).
         -  The template description consists of a maximum of 256 characters and cannot include line breaks or the following special characters: >!<"&'=

      After the parameter template is exported, a new template is generated in the list on the **Parameter Template Management** page.

   -  **File**: You can export the parameter template information (parameter names, values, and descriptions) of a DB instance to a CSV file for viewing and analysis.

      In the displayed dialog box, enter the file name and click **OK**.

      .. note::

         The file name must start with a letter and consist of 4 to 81 characters. It can contain only letters, numbers, hyphens (-), and underscores (_).
