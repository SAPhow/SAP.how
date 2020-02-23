---
title: How to read transaction user default values in SAP EWM?
categories: ewm-developmnet
author: Vasiliy Kharitonov
systems:
  SAP EWM 9.4
---

It is a good practice to use standard defaults in your developments - it keeps them simpler and more seamless with standard system. Most of the times it also saves server resources. This is why it can be useful to be able to read transaction default values for SAP EWM. E.g. you might want to read what is the default Physical inventory procedure for the current used or does he usually blocks storage bins during inventory counting.

To do this you can use class `/SCMB/CL_ESDUS_MANAGER` _Manager for Dynamic User Parameters_. However, it is not so straightforward to use, first you need to understand some basic concepts.

## Dynamic settings action `IV_ACTION`

To use the class you need to create an instance and system requires you to provide 2 parameters: _User name_ and _Action for Which Dynamic Settings Are Held_. The latter represents a collection of user default values for corresponding functionality. For example `IV_ACTION` equal to `/SCWM/PI` will give you all dynamic user default values for physical inventory transaction. If your user already set the corresponding default value - you can find corresponding action in database table `/SCMB/ESDUS`. In all cases from my experience action name equals to the corresponding transaction code. Unfortunately, I didn't find a collection with all possible actions. There are of course standard constants for action names, but I found them spread between objects for different functionalities.

## Dynamic settings element `IV_ELEMENT`

To actually get a value for some parameter you would need to use method `GET` which requires you to provide _Element for Which Dynamic Settings Are Held_. This represents parameter name, for which you want to receive a user default value. Again, - if your user already set the corresponding default value - you can find corresponding element in the table `/SCMB/ESDUS`.

## Changing values

You can also use method `SET` to change user default values and there is a method `PRESET` if you want system to write a system default value for corresponding user parameter. Use `FLUSH` method to write changed values to the database.
