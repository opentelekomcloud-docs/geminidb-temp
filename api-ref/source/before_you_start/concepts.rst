:original_name: nosql_05_0005.html

.. _nosql_05_0005:

Concepts
========

-  Account

   An account is generated after your registration. The account has full access permissions for all the resources and cloud services in it. You can use it to reset user passwords and grant users permissions. The account is a payment entity, which should not be used directly to perform routine management. To ensure account security, create IAM users and grant them permissions for routine management.

-  IAM User

   An IAM user is created using an account to use cloud services. Each IAM user has its own identity credentials (password and access keys).

   The account name, username, and password will be required for API authentication.

-  Region

   A region is a geographic area in which cloud resources are deployed. Availability zones (AZs) in the same region can communicate with each other over an intranet, while AZs in different regions are isolated from each other. Deploying cloud resources in different regions can better suit certain user requirements or comply with local laws or regulations.

-  AZ

   An AZ contains one or more physical data centers. Each AZ has independent cooling, fire extinguishing, moisture-proof, and electricity facilities. Within an AZ, computing, network, storage, and other resources are logically divided into multiple clusters. AZs within a region are connected using high-speed optical fibers to support cross-AZ high-availability systems.

-  Project

   A project corresponds to a region. Projects group and isolate resources (including compute, storage, and network resources) across physical regions. Users can be granted permissions in a default project to access all resources in the region associated with the project. If you need more refined access control, create subprojects under a default project and create resources in subprojects. Then you can assign users the permissions required to access only the resources in specific subprojects.


   .. figure:: /_static/images/en-us_image_0000001354698252.png
      :alt: **Figure 1** Project isolating model

      **Figure 1** Project isolating model

-  Enterprise Project

   Enterprise projects group and manage resources across regions. Resources in enterprise projects are logically isolated. An enterprise project can contain resources of multiple regions, and resources can be added to or removed from the enterprise project.
