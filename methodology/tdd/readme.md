# Test Driven Development

* functional tests
* performance test
* configuration test
* usability test
* UI test
* Security test
* localization test

## Testing levels

### Unit

    - Testing of code at level of functions (FP) or classes (OOP)
    - one function can have multiple tests for covering all expected cases
    - may include next point
        - static code analyzing
        - data flow analysis
        - metrics analysis
        - peer code analysis
        - code coverage analysis

### Integration

    - Verify interfaces between components against software design
    - The main point is to verify requirements compliance:
        - functional requirements
        - acceptance requirements
        - reliability requirements
    - For Integration testing it is used CIS (Continuous Integration Systems)

### System

    - testing completely integrated system to verify that it meets requirements
    - ensure it doesn't corrupt operating environment
        - corrupting shared memory
        - not consuming excessive resources
        - leave any parallel process unharmed

## Testing methods

### Black Box

    - equivalence partitioning
    - Boundary-value analysis
    - all-pairs testing
    - state transition tables
    - decision table testing
    - fuzz testing
    - model-based testing
    - use case testing
    - exploratory testing
    - specification-based testing

###  White Box

    - Testing internal structure of a program
    - Techniques
        - API testing
            - determine whether API meets expectations in
                - functionality
                - reliability
                - performance
                - security
        - Code Coverage Testing
        - Fault Injection
            - create tests with fault in order to improve code coverage and error handling behavior
        - Mutation testing
            - is used to design new tests in order to evaluate the quality of existing tests
            - testing through creating building applications with minor changes (the are called mutants) in order to define how much mutants will fail existing tests
        - Static testing
            - code sanity
            - algorithm sanity
            - is it documented

### Grey Box


## Testing

### Matrix Testing

May be used to check States correctly

### Regression testing

Rerunning of the test cases if new changes are made

### Pattern Testing

design or architecture and patterns testing (AST?)

### Orthogonal array testing

It is used when the number of inputs to the system is relatively small, but too large to allow for exhaustive testing of every possible input to the systems