# Tackling Basic Unit Testing Scenarios

 Core unit testing scenarios :
 - Strings, collections, events, exceptions, …

A unit test should only contain one assert

It’s not about the amount of asserts you’re using in a test, it’s about the behavior you’re testing

```cs
// Assert
 Assert.True(employee.Salary >= 2500 && employee.Salary <= 3500);
 Assert.True(employee.SuggestedBonus > 5000);
```

```cs
// Asserting on Booleans
 Assert.False(...);
 Assert.True(...);

// Asserting on strings
 Assert.Equal(...) / Assert.NotEqual(...)
 Assert.StartsWith(...) / Assert.EndsWith(...)
 Assert.Contains(...) / Assert.DoesNotContain(...)
 Assert.Matches(...) / Assert.DoesNotMatch(...)
 Assert.Empty(...) / Assert.NotEmpty(...)

// Asserting on numeric values
// Asserting on floating points with precision
 Assert.Equal(...) / Assert.NotEqual(...)
 Assert.InRange(...)

// Asserting on arrays and collection content
 Assert.Equal(...) / Assert.NotEqual(...)
 Assert.Contains(...) / Assert.DoesNotContain(...)
 Assert.All(...)

// Asserting asynchronous code
// Asserting on exceptions
 Assert.Throws<T>(...) / Assert.ThrowsAsync<T>(...)
 Assert.ThrowsAny<T>(...) / Assert.ThrowsAnyAsync<T>(...)

 // ThrowsAny(Async)<T> takes derived versions into consideration, while Throws(Async)<T> doesn’t

 // Asserting on events
 Assert.Raises<T>(...) / Assert.RaisesAsync<T>(...)
 Assert.RaisesAny<T>(...) / Assert.RaisesAnyAsync<T>(...)

 // Asserting on object types
 Assert.IsType<T>(...) / Assert.IsNotType<T>(...)
 Assert.IsAssignableFrom<T>(...) / Assert.IsNotAssignableFrom<T>(...)

 // Asserting on Private Methods

/*
 A private method is an implementation detail that doesn’t exist in isolation- Test the behavior of the method that uses the private method
 Making a private method public just to be able to test it breaks encapsulation
 - Use [InternalsVisible] as a slightly less bad alternative
*/

```