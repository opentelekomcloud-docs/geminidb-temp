:original_name: nosql_03_0014.html

.. _nosql_03_0014:

Managing Tags
=============

Scenarios
---------

Tag Management Service (TMS) enables you to use tags on the management console to manage resources. TMS works with other cloud services to manage tags. TMS manages tags globally and other cloud services manage their own tags.

Adding tags to GeminiDB instances helps you better identify and manage them. An instance can be tagged during or after it is created.

After an instance is tagged, you can search for the tag key or value to quickly query the instance details.

Precautions
-----------

-  You are advised to set predefined tags on the TMS console.
-  A tag consists of a key and value. You can add only one value for each key. For details about the naming rules of tag keys and tag values, see :ref:`Table 1 <nosql_03_0014__table197401426182516>`.
-  Up to 20 tags can be added for each instance.

.. _nosql_03_0014__table197401426182516:

.. table:: **Table 1** Naming rules

   +-----------------------+---------------------------------------------------------------------------------------------------+-----------------------+
   | Parameter             | Requirement                                                                                       | Example Value         |
   +=======================+===================================================================================================+=======================+
   | Tag key               | -  The key cannot be left blank.                                                                  | Organization          |
   |                       | -  Each tag key is unique for each instance.                                                      |                       |
   |                       | -  A tag key consists of a maximum of 36 characters.                                              |                       |
   |                       | -  The key can only consist of digits, letters, underscores (_), hyphens (-), and at signs (@).   |                       |
   +-----------------------+---------------------------------------------------------------------------------------------------+-----------------------+
   | Tag value             | -  This tag value can be left blank.                                                              | nosql_01              |
   |                       | -  The value consists of up to 43 characters.                                                     |                       |
   |                       | -  The value can only consist of digits, letters, underscores (_), hyphens (-), and at signs (@). |                       |
   +-----------------------+---------------------------------------------------------------------------------------------------+-----------------------+

Adding a Tag
------------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. On the **Instance Management** page, click the instance you wish to add tags for to go to the **Basic Information** page.
#. In the navigation pane on the left, click **Tags**.
#. On the **Tags** page, click **Add Tag**. In the displayed dialog box, enter a tag key and value, and click **OK**.
#. View and manage tags on the **Tags** page.

Editing a Tag
-------------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`

#. On the **Instance Management** page, click the instance you wish to add tags for to go to the **Basic Information** page.

#. In the navigation pane on the left, click **Tags**.

#. On the **Tags** page, locate the tag to be edited and click **Edit** in the **Operation** column. In the displayed dialog box, change the tag value and click **OK**.

   Only the tag value can be edited when editing a tag.

#. View and manage tags on the **Tags** page.

Deleting a Tag
--------------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. On the **Instance Management** page, click the instance you wish to delete tags for to go to the **Basic Information** page.
#. In the navigation pane on the left, click **Tags**.
#. On the **Tags** page, locate the tag to be deleted and click **Delete** in the **Operation** column. In the displayed dialog box, click **Yes**.
#. After a tag has been deleted, it will not be displayed on the **Tags** page.

Searching an Instance by Tag
----------------------------

#. :ref:`Log in to the GaussDB NoSQL console. <nosql_login>`
#. On the **Instance Management** page, click **Search by Tag** in the upper right corner of the instance list.
#. Enter the key or value of the tag to be queried and click **Search** to query the instance associated with the tag.
