:original_name: nosql_05_0002.html

.. _nosql_05_0002:

Creating a Parameter Template
=============================

You can use database parameter templates to manage the DB engine configuration. A database parameter template acts as a container for engine configuration values that can be applied to one or more DB instances.

Each user can create up to 100 parameter templates. All types of instances in the same project can share the quota.

Procedure
---------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. In the navigation pane on the left, choose **Parameter Template Management**.
#. On the **Parameter Template Management** page, click **Create Parameter Template**.
#. Select a compatible DB engine version, name the parameter group, add the parameter group description, and click **OK** to create a parameter group template.

   -  **Compatible API**: Select the API type that is compatible with your DB engine parameter template.
   -  **DB Engine Version**: Select a DB engine version, for example, 3.11.
   -  **Parameter Template Name**: The template name must consist of 1 to 64 characters. It can contain only uppercase letters, lowercase letters, digits, hyphens (-), underscores (_), and periods (.).
   -  **Description**: The description can contain a maximum of 256 characters except the carriage return character and the following special characters: > ! < " & ' =

#. On the **Parameter Template Management** page, view the created parameter template.
