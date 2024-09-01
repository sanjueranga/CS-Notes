# Testing Strategies


## Top down testing
• Test starts from the top level of the system.
• Later tests detailed components.
• Should use with Top Down Program Development practice. So that each component can test soon as it is developed.

## Bottom up testing
• Low level components are integrated and tested before higher level.
• Better to use with OO development practices and when system re uses & modifies components taken from other systems.


## Thread testing
• Used to test real time systems when test is based on events of the system actions.


## Black Box Testing

• Treat the system as a black box.
• Also known as functional testing.
• Internal workings of the item being tested are not known by the tester.
• The tester does not examine the programming code or does not need any further knowledge of the program other than its specifications.


BBT attempts to find errors in the following areas.
• Incorrect or missing functions
• Interface errors
• Performance errors
• Initialization or termination errors


Applicable to following levels of software testing
• Integration testing
• System testing
• Acceptance testing


**Advantages**
i. The test is unbiased because the designer and the tester are independent of each other.
ii. The tester does not need knowledge of any specific programming languages.
iii. The test is done from the point of view of the user, not the designer.
iv. Test cases can be designed as soon as the specifications are complete.

**Disadvantages**
i. The test can be redundant if the software designer has already run a test case.
ii. The test cases are difficult to design.
iii. Testing every possible input stream is unrealistic because it would take an enormous amount of time; therefore, many program paths
will go untested.



## White Box Testing

• **White box testing is also called as glass, structural, open box or clear box testing.**
•This strategy deals with the internal logic and structure of the code.

The SW engineer must derive test cases in order to guarantee that,

• All independent paths within a module have been tested at least once.
• All the logical decisions on their true and false sides are tested.
• All loops at their boundaries and within their operational bounds are tested.
• Internal data structures are tested to assure their validity.
• This is mainly applied to unit testing

**Advantages**
i. As the knowledge of internal coding structure is prerequisite, it becomes very easy to find out which type of input/data can help in testing the application effectively.
ii. The other advantage of white box testing is that it helps in optimizing the code.
iii.It helps in removing the extra lines of code, which can bring in hidden defects.


**Disadvantages**
i.Skilled testers are needed to carry out thistype of testing, which increases the cost.
ii. It is nearly impossible to look into every bit of code to find out hidden errors, which may create problems, resulting in
failure of the application.

