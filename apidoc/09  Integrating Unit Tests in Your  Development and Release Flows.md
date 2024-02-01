#  Integrating Unit Tests in Your Development and Release Flows

- Running tests with the CLI
- Comparing test runners with test frameworks
- Testing in parallel
- Testing against multiple target frameworks
- Integrating testing in your CI/CD pipeline

## Test runner
The program (or maybe a third-party plugin to a program) that is responsible for looking for one or more assemblies with tests in them and activating the test frameworks that it finds in those assemblies

## Test framework
The code that has detailed knowledge of how to discover and run unit tests

Running tests in parallel allows a set of tests to finish faster, locally and on your build server

## Running Tests in Parallel

> Test runner: 
 A runner can support running different test assemblies in parallel

> Test framework: 
 A framework can support running tests within a single assembly in parallel


## Parallelism in test frameworks
## Parallelism in test runners

## Running Tests Against Multiple Target Frameworks

xUnit supports running tests against multiple target frameworks
- Useful when developing frameworks or libraries 

You want to ensure your library correctly functions across target frameworks
