---
title: How to download SAP GUI from SAP?
categories: gui-basis
author: Vasiliy Kharitonov
---

If you need to install SAP GUI on a new machine, you can download it directly
from SAP. You need 2 prerequisites to be able to do it:

- You should have an SAP user (it is used to access most of SAP resources).
- You should have enough authorizations to perform downloads with your SAP user
  account.

The first one is easy, you can even register it yourself. For the second one
your usually need to ask IT department of your employer to provide sufficient
access for your SAP user. In this case you should use the same SAP user that was
provided by your employer.

To download the latest SAP GUI, you should perform the following actions:

1. Navigate to [Software center on SAP ONE Support
   Launchpad](https://launchpad.support.sap.com/#/softwarecenter).
2. SAP ONE Launchpad will ask you to login with your SAP user.
3. Navigate to folder _By Category_, then _SAP Frontend Components_.
4. Select one of the following GUI clients:
   - SAP GUI for Windows. Choose this one if you are using Windows. Generally
     speaking the Windows client is better.
   - SAP GUI for Java. Choose this one if you are using macOS or Linux.
5. In case you use Windows you need to download _CORE_ package and then _Support
   packages and Patches_.
   1. To start downloading _CORE_ press the item name. You __don't__ have to use
      download basket and Download Manager software.
   2. After downloading _CORE_ press _Support Packages and Patches_ button on
      the top right.
   3. Press the name of the patch with the latest Release date (or Patch Level)
      to download it.
6. In case of client for Java you can go directly to _Support Packages and
   Patches_ and download the latest `.JAR` file -- there is no need to download
   anything else.
7. All the files downloaded are just installers, you need first to run the
   install to have SAP GUI software on your system.
