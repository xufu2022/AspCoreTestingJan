#  Unit Testing ASP.NET Core MVC Controller

Steer away from generalizations like “don’t test repositories”, “don’t test constructors”, …

- Architectures, pattern implementations, … often differ from project to project
- So-called best practices are sometimes diverted from, on purpose or accidentally

## Controllers Types: Thick Controllers

 Thick controllers contain logic that implements the expected behavior
 This is code that should be unit tested

Thin or skinny controllers delegate the actual implementation of the behavior to other 
components
 These typically don’t need to be unit tested


```cs
// Thick Controllers
[HttpGet]
 public async Task<ActionResult<IEnumerable<InternalEmployeeDto>>> GetInternalEmployees()
 {
 var internalEmployees = await _employeeService.FetchInternalEmployeesAsync();
 var internalEmployeeDtos = internalEmployees.Select(e => new InternalEmployeeDto() { 
    Id = e.Id, 
    FirstName = e.FirstName,
    LastName = e.LastName,
    Salary = e.Salary,
    SuggestedBonus = e.SuggestedBonus,
    YearsInService = e.YearsInService });
 return Ok(internalEmployeeDtos);
 }


// Thin Controllers
[HttpGet]
 public async Task<ActionResult<IEnumerable<InternalEmployeeDto>>> GetInternalEmployees()
 {
 var internalEmployeeDtos = await _employeeService.FetchInternalEmployeesAsync(); 
return Ok(internalEmployeeDtos);
 }
```

## Concerns when unit testing controllers:
- Mocking controller dependencies
- Working with ModelState in tests
- Dealing with HttpContext
- Working with HttpClient calls in tests


# HttpContext

An object which encapsulates all HTTP-specific information about an individual HTTP request: a container for a single request

Common Information in HttpContext

- Request
- Response
- Features (connection, server info, …)
- User


## Testing with HttpContext

 Use the built-in default implementation: **DefaultHttpContext**

 Use Moq for mocking: **Mock<HttpContext>**

```cs
//Testing with HttpContext.Features

```

```cs
//Testing with HttpContext.User

```

```cs
//Testing with HttpClient calls
```

## Summary

 - Testing API controllers- ActionResult<T>, DTO models, ModelState, HttpContext, …
 - Use Moq or other test doubles