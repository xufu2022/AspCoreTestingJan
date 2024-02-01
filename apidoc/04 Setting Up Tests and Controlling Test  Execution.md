# Setting Up Tests and Controlling Test Execution

- Constructor and dispose
- Class fixture
- Collection fixture

Integrating test context with ASP.NET Core’s dependency injection system

 - Categorizing tests
 - Skipping tests
 - Customizing test output

## Setting Up Tests and Sharing Test Context

### Constructor and dispose approach

Set up test context in the constructor, potentially clean up in Dispose method
    - Context is recreated for each te

## Class fixture approach

- Create a single test context shared among all tests in the class
    - Context is cleaned up after all tests in the class have finished
- Use when context creation and clean-up is expensive

Don’t let a test depend on changes made to the context by other tests
- Test must remain isolated
- You don’t have control over the order in which tests are run

## Setting Up Tests and Sharing Test Context

 - Constructor and dispose approach
 - Class fixture approach
 - Collection fixture approach

## Collection Fixture

- Create a single test context shared among tests in several test classes
    - Context is cleaned up after all tests across classes have finished
- Use when context creation and clean-up is expensive

## Summary

- Use [Trait] to categorize tests
- Use the Skip property on [Fact] to skip tests
- Use ITestOutputHelper to log additional diagnostics info

