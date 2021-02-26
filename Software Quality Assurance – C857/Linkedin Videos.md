# Introduction

## Set the standard with QA

QA exists to prevent negative experiences.  
This course will explain what QA is and different types of testing.

---

## What is QA?

<u>**Quality Assurance (QA)**</u>: A systematic process used to determine whether a product meets specifications.

---

## How to ensure quality

Quality can be measured with customer happiness, annual revenue, and how well the app functions over time.

Steps for quality software:

1. Clear specifications
2. Code implemented
3. Code tested
4. Code released

---

# 1. The Role of QA

## Roles and responsibilities

Skills needed for QA:

- <u>**Technical Aptitude**</u>: Needed for manual and automated testing. Role includes some programming.
- <u>**Business Knowledge**</u>: Needed for feature scoping and test planning. Requires having an understanding of how the business is using the software.
- <u>**DevOps Principles**</u>: Needed for Configuring tools, set up CI, automate processes, and set up test environments.
- <u>**Process and Release Expertise**</u>: Defining/improving testing practices & Optimizing release processes.

---

## Get involved throughout the SDLC

<u>**SDLC**</u>: Software Development Life Cycle.

6 parts of the SDLC (do this for each feature):

1. <u>**Plan**</u>: Identify risks and use cases of a feature.
2. <u>**Define**</u>: Write specs and acceptance criteria. Decide what's in scope.
3. <u>**Design**</u>: Solidify test scenarios & get feedback from team.
4. <u>**Build**</u>: (see design).
5. <u>**Test**</u>: Manual and automation tests are completed.
6. <u>**Deploy**</u>: Validate functionality.

---

## Collaborate with the team

You should collaborate with the other teammates during each step of the SDLC.

---

## Set expectations and goals

Work together, set and share goals...  
Constantly check in with your team mates.  
Give and receive feedback.

---

---

# 2. Test Planning

## Create a test strategy

Let's others know what is being tested and why.

<u>**Intro**</u>: High level outline.  
<u>**References**</u>: Any links to tools for testing.  
<u>**Deliverables**</u>: What the QA will provide to team.  
<u>**Test Management**</u>: Describes what resources are needed to test.  
<u>**Scope of Testing**</u>: What types of test exist.

---

## Make a test plan

Each feature will have a test plan.

4 main parts of a test plan:

1. <u>**Scenario**</u>: The action that will be executed.
2. <u>**Expected result**</u>: What the result should be.
3. <u>**Latest result**</u>: Pass/fail.
4. <u>**Automated**</u>: True/false. You should automate the important features.

One feature per row. The above 4 items are columns, this is a table.  
Work with the group advanced of release to go through these tests.  
Test plan is a living document that changes a lot.

---

## Write acceptance criteria

<u>**Acceptance Criteria**</u>: Conditions that a software product must satisfy to be accepted by a stakeholder.

These are user stories, explain the look and feel for the user.

<u>**Given**</u>: The before state of the scenario.  
<u>**When**</u>: The action of the scenario.  
<u>**Then**</u>: Expected outcome.

Example:  
<u>**User Story**</u>: Given I am viewing an item, when I press the "Add to cart" button, then the item is added to the cart.

Sometimes there will be expected errors added to the story, like when the item you are adding is sold out.

---

## Identify when testing is complete

The team should decide together and know what the definition of done is. (short video, 1m)

Every user story should have a definition of done.

---

# 3. Types of Testing QA Focuses On

## Box testing

3 types of boxes:

- <u>**Black box testing**</u>: The box is concealed and it's not possible to see what's inside of it.
  - Examines input to the the box & output from the box.
- <u>**Gray box testing**</u>: The box is semi transparent.
  - Includes integration testing, or how different components work together.
- <u>**White box testing**</u>: The box is see through.
  - Tests specific functions of the code itself.
  - Includes unit and system testing.

---

## Manual testing

Follows the steps a user would take. Test scenarios should be identified before hand (including typical and non-typical use cases).  
This is very much what Ellen does for the user testing items.  
Type of black box testing.

---

## UI automation testing

Like manual testing but uses a script to automate scenarios.  
This can be run repeatably and help catch regressions.  
Type of black box testing. Should only be used to on the most important workflows because these types of tests are slow.  
PuppeteerJS is a good tool to use for these types of tests.

---

## Integration testing

Focuses on the interaction between application components.  
Example: How the presentation layer interacts with the business logic, and how that interacts with the database.  
This is gray box testing.  
You can send JSON to an API as a way to test things.

---

## Performance testing

Tests how the application performs under load and scale.  
Black box testing.  
Not as common as the tests above, but very useful.

<u>**Load testing**</u>: Puts the system under load to see how many users/threads can be performed at once.  
<u>**Endurance testing**</u>: Determines in the system can handle the expected load for long periods of time. (checks for errors, like memory leaks)  
<u>**Stress testing**</u>: Puts the application under extreme loads to find the breaking point of the application. Measures stability.

---

## Security testing

Tests for hacking exploits like SQL injection or DOS attempts.  
Typically there is a dedicated security team.

---

---

# 4. Bug Reporting

## Identify bugs

(what the title said)

---

## Report bugs

Bugs should be reported in a bug reporting system.  
Jira, Rally, Github, BugZilla are examples.  
You should use the same tool as the one that manages the project if possible.

---

## Triage bugs

You should regularly review open bugs.  
<u>**Severity**</u>: How impactful the bug is to the business.  
<u>**Priority**</u>: How fast the bug should be fixed.

Use the Eisenhower square to prioritize. Severity is importance, priority is urgency.

---

## Communicate bugs to the team

Talk with your team... Use Jira/other!

---

## Getting bugs fixed

Each software sprint should include bug removing goals/plans.

---

## Have bug bashes

These are dedicated times to find bugs / work on bugs. Could be an hour of bug hunting, or 1 week of only working on bugs (once or twice a year)
