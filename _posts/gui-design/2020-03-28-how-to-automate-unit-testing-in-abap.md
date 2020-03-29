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
And not just small isolated tests, you could immediately check if **any** of
enhanced functionality is impacted. Sounds like magic but it is already an
industry standard in other development environments. If someone makes a small
logic mistake this magic immediately shows that something is wrong. With
automatic unit testing effort for human testing is decreased, first time right
is improved, and most important quality of the product is enhanced.

SAP recognized importance of automated testing as well and there is a test
driven development for it. It might be not as advanced as something you would
encounter in other environments, but it gets the job done.

Unfortunately, in order to use this functionality you will have to change your
development approach and make some additional efforts for developers. First of
all, you would need an improved technical architecture.

## Step 1. Change your technical architecture

In all SAP projects I encountered in my career, the object model for developments
usually looks in one of two ways.

The first one is the bad one. All of the enhanced functionality for some certain
spot, all 2 thousands rows of ABAP code, is just packed into a single object, for
example, into a single ABAP report.

The second one is better but still a bad one. For each development a new
separate object is created. E.g. classes `ZCL_DEV_1`, `ZCL_DEV_2`. Several
sub-objects (e.g. methods) are created for the main object to represent parts of
functionality that are repeated in multiple places.

What is required in the test driven development is an another approach to object
model. Technical architecture is missing in both usual approaches. To improve it
basically you should have separate objects representing separate types of
functionality. Logic for communicating with database should be a separate
object, for example, a class `ZCL_DB_ACCESS`.

Aside from database access object you would also need a separate object for all
custom interactions with users, including dialogs, selection screens, other
buttons and UI elements. For example, you could create a class `ZCL_UI_MANAGER`.
If you have some logic for integration with other systems, you should do the
same for it as well. For example, for custom integration with TM you could
create a class `ZCL_TM_INTEGRATION`.

## Step 2. Create test doubles for database and UI classes

This is essential for good test driven design. With good technical architecture,
you will be able to replace these “integration" objects with some hardcoded test
objects (SAP calls them test doubles). These test doubles should help produce
some static calculated results and also keep your real database safe. You can
use dependency lookup injection to replace objects of real classes with test
doubles. It is a good practice to make both real class and test double class
implementing the same custom interface. There are many reasons for it, but it is
a topic for detailed article (part 2?).

Then your unit tests should be written by developers. Actually it is even better
to first write unit tests and only then start your development. This way
developers can use them not only for regression testing but during development
process as well.

## Step 3. Write unit tests

You can use ABAP Unit framework for writing tests. Good practice is to write
some unit tests for each of your methods (or forms/function modules), doesn’t
matter if it is private or public. E.g. if you have logic for destination bin
filtering and sorting, you could write the following tests (simplified):

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

The next step would be to run the tests automatically in the background and sent
some emails in case of errors. This can be easily accomplished with ABAP report
`RS_AUCV_RUNNER` running using a background job.
