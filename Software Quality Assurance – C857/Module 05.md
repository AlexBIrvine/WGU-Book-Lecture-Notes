# Program Inspections, Walkthroughs, and Reviews

## Inspections and Walkthroughs

There are 3 primary human testing methods:

1. <u>**Code Inspections**</u>
2. <u>**Walkthoughs**</u>
3. <u>**User Testing**</u>: (covered in a future lesson)

Both inspections and walkthroughs involve a group of developers, one being the author, working together and reading through the code.

## Code Inspections

General procedure terminology of code inspections:

- <u>**Inspection Team**</u>: Usually 4 developers, one of them being the author and another being a moderator.
  - Moderator must distrubute materials, lead the session, and record all errors found.
- <u>**Inspection Agenda**</u>: Consists of the design specs and program's listing.
- <u>**Session**</u>: During the session the author will narrate the program, statement by statement, and explain the logic of the program.
  - Each statement is checked against a list of historically common programming errors.

## An Error Checklist for Inspections

(This section goes into detail about each section listed below. I'm only going to summarize for the test, but this is useful information)

There are 7 catagories of common software errors:

1. <u>**Data Reference Errors**</u>: Do referenced variables have value? Are arrays in bounds? Are memory pointers allocated correctly? Are the types what the compiler expects?
2. <u>**Data Declaration Errors**</u>: Are all variables explicitly declared? Are variables properly initialzed?
3. <u>**Computation Errors**</u>: Are data types being used properly (int vs float)? Are variables of proper length/type?
4. <u>**Comparison Errors**</u>: Are types correct? Are operators (<, >, etc.,) correct? Is your boolean algebra correct?
5. <u>**Control-Flow Errors**</u>: Will everything (modules, loops, etc.,) eventually terminate? Off by 1 errors?
6. <u>**Interface Errors**</u>: Is argument parity correct? Are functions used correctly?
7. <u>**I/O Errors**</u>: Are file read/writes being handled correctly?

## Walkthroughs

Similar, but different to code inspections. The biggest difference is that the participants "play computer" and try to walk through the code as if they were the computer. A tester (one of the 4) will bring premade tests and have the participants walk through it to see if the logic makes sense.

## Desk Checking

A single person code inspection involving only the author. Ineffective compared to the methods listed above.

## Peer Ratings

A group of programmers will anonymously read through sample code and rate it based on criteria set by the admin. Such questions could be:

- Was the program easy to understand?
- Was the high-level design visible?
- Would it be easy for you to modify the program?
- Would you be proud to have written this?

After the review, code is ranked.
