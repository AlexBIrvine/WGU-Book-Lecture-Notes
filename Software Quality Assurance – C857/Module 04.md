# The Psychology and Economics of Software Testing

## The Psychology of Testing

We don't test to prove that the program works, we test to prove there are errors in the program.  
Negative reinforcements, remove the suck.  
(The rest of this section was restating that fact. It's okay to find errors, in fact it's good, etc.,)

## The Economics of Testing

The two most common types of testing are black-box testing & white-box testing:

<u>**Black-box Testing**</u>: Don't concern yourself with the inner workings of the program, instead focus if the inputs produce the desired outputs.  
Test data is driven purely from specification using this method.  
In order to find all errors using this method, you need to test every possible input (also known as _exhaustive input testing_).

<u>**White-box testing**</u>: Also called _logic-driven testing_, allows the tester to look at the internal working of the program and test based on the internal logic of the program.  
Instead of doing exhaustive input testing like _black-box_, you would try to test all the different logic paths the program could take.

## Software Testing Principles

There are 10 principles to follow for software testing:

<u>**1-A necessary part of a test case is a definition of the expected output or result**</u>:  
Each test case should consist of:

- A description of the input data to the program.
- A precise description of the correct output of the program for that set of input data.

<u>**2-A programmer should avoid attempting to test his or her own program**</u>:  
It's hard for the programmer to change perspective enough from creation to testing.  
Also, it's hard for some programmers to see teh faults in their code.

<u>**3-A programming organization should not test its own programs**</u>:  
Just like principle 2, those who are affected by the program should not test it.

<u>**4-Any testing process should include a thorough inspection of the results of each test**</u>:  
Test because you don't trust the program, and inspect the test output because you don't trust the test.

<u>**5-Test cases must be written for input conditions that are invalid and unexpected, as well as for those that are valid and expected**</u>:  
Test all inputs, even the stupid ones.

<u>**6-Examining a program to see if it does not do what it is supposed to do is only half the battle; the other half is seeing whether the program does what it is not supposed to do**</u>:

<u>**7-Avoid throwaway test cases unless the program is truly a throwaway program**</u>:

<u>**8-Do not plan a testing effort under the tacit assumption that no errors will be found**</u>:  
Finding errors are good.

<u>**9-The probability of the existence of more errors in a section of a program is proportional to the number of errors already found in that section**</u>:  
If module A has found 5 errors and module B has found 1 error, there are likely to be more errors in A than in B.

<u>**10-Testing is an extremely creative and intellectually challenging task**</u>:
