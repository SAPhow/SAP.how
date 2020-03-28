---
title: How to automate unit testing in ABAP?
author: Vasiliy Kharitonov
categories:
- gui-design
- gui-support
systems:
- SAP EWM 9.4
- SAP S/4HANA 1809
---

Imagine, you could automatically test any change you (or your developer) made.
And not just small isolated tests, but actually you could check if any of
enhanced functionality is impacted. Sounds like magic but it is already an
industry standard in other development environments. If someone makes a small
logic mistake this magic immediately shows that something is wrong. With
automatic unit testing effort for human testing decreases, first time right
chance increases, and most important quality of the product improves.

SAP recognized importance of automated testing as well and there is test driven
development for it. It might be not as advanced as something you would encounter
in other development environments, but it gets the job done.

Unfortunately, to use these kind of functionality you would have to change your
development approach and put some additional effort for developer. First of all,
you would need an improved technical architecture.

## Step 1. Change your technical architecture

In all SAP projects I encountered in my career object model for developments
usually looks in one of two ways.

The first one is the bad one. All of the enhanced functionality for some certain
spot, all 2 thousands of ABAP code are just packed into a single object, for
example, into a single program report.

The second one is better but still a bad one. For each development a new
separate class is created. E.g. classes `ZCL_DEV_1`, `ZCL_DEV_2`. Several
methods are created for the class to represent parts of functionality that are
repeated in multiple places.

What is required in the test driven development is an another approach to object
model. Technical architecture is missing in both usual ways. To improve it
basically you should have separate objects representing separate types of
functionality. Logic for communicating with database should be a separate
object, for example, a class `ZCL_DB_ACCESS`.

Aside from database access object you would need a separate object for all
custom interactions with users, including dialogs, selection screens, other
buttons and you are elements, e.g. `ZCL_UI_MANAGER`. If you have some logic for
integration with other system, you should do the same for it as well.

## Step 2. Create test doubles for database and UI classes

This is essential for a good test driven design. With good technical
architecture, you will be able to replace these “integration objects“ with some
hardcoded test objects (SAP calls them test doubles), that should help produce
some static calculated results and also keep you real database safe. You can use
dependency lookup injection to replace real classes with test doubles. It is a
good practice to make both real class and test double implementing the same
custom interface. There are many reasons for it, but it is a topic for detailed
article (part 2?).

Of course your unit tests should be written by a developer. Actually it is even
better to first write unit tests and only then start your development. This way
you can use it not only for regression testing but during development process as
well.

## Step 3. Write unit tests

You can use ABAP Unit framework for writing tests. Good practice is to write
some unit tests for each of your methods, doesn’t matter if it is private or
public. E.g. if you have logic for destination bin filtering and sorting, you
could write the following tests (simplified):

- Putaway of full pallet into the set of bins, some certain bin should be
  defined.
- Putaway of partial pallet into the set of bins, other certain bin should be
  defined.
- Staging bin determination for picking, certain staging bin should be defined.

Then you will be able to run those tests for each new line of code, to check if
everything works fine or not. Also, you will be able to use old tests for
regression purposes, e.g. when you implement logic for bin dynamic separation
and merging in the same enhancement spot.

## Step 4. Automate unit test execution

The next step would be to run tests in the background and sent some emails in
case of errors. This can be easily accomplished with ABAP report
`RS_AUCV_RUNNER` running using a background job.
