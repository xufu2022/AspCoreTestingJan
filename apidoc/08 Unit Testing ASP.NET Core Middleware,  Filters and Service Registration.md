# Unit Testing ASP.NET Core Middleware, Filters and Service Registration

## Unit Testing Middleware

- Dependencies that are difficult to mock can lead towards an integration test
- Mostly though, a unit test is advisable for middleware testing

 Typical concerns when unit testing middleware:
 - Mock the HttpContext (or use DefaultHttpContext)
 - Handle the RequestDelegate

## ASP.NET Core Filter

 A filter allows code to run before or after specific stages in the request processing pipeline

  - Error handling
  - Caching


Filters can be used to avoid code duplication

Filters run in the ASP.NET Core action invocation pipeline

## Unit Testing ASP.NET Core Filters

- Action filter
- Authorization filter
- Exception filter
- Resource filter
- Result filter

Action filters:
- Run immediately before and after an action method is called
- Can change the arguments passed into an action
- Can change the result returned from the action

## Unit Testing Service Registrations

 Approach:
 - Create an IServiceCollection
 - Register the services on it
 - Build an IServiceProvider
 - Verify whether the services were registered


## Summary

- Challenges with middleware and filter testing are related to test isolation
- Test service registrations by building an IServiceProvider and testing whether you can get a service instance
