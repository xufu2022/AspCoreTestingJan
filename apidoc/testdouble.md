# Test Double

Understanding the differences between Stubs, Mocks, Fakes, Spies, and Dummies is crucial in the context of unit testing, especially in object-oriented programming like C#. These concepts are part of a broader category known as "Test Doubles" which are used to simulate the behavior of real objects in a controlled way. Here's an in-depth explanation of each, with C# examples:

## Stubs
Purpose: Stubs provide canned answers to calls made during the test, usually not responding at all to anything outside what's programmed in for the test.

Use Case: When you need to test a portion of code that interacts with an external system (like a database or a web service), you use a stub to simulate the responses from that system.

```cs
public interface IDataAccess
{
    int GetNumber();
}

public class StubDataAccess : IDataAccess
{
    public int GetNumber()
    {
        // Always returns a fixed value
        return 5;
    }
}
```

# Mocks
Purpose: Mocks are used to verify interactions between objects. They are configured with expectations which form a specification of the calls they are expected to receive.

Use Case: Useful in scenarios where you need to ensure certain methods are called with specific parameters.
Example: Using a mocking framework like Moq:

```cs
var mock = new Mock<IDataAccess>();
mock.Setup(m => m.GetNumber()).Returns(5);

// Use mock.Object in your tests, and then:
mock.Verify(m => m.GetNumber()); // Verifies that GetNumber was called

```

## Fakes
Purpose: Fakes are objects that have working implementations, but not same as production one. Usually they take some shortcut and have simplified version of production code.

Use Case: Great for scenarios where using real objects would make tests slow or complex.
Example:
```cs
public class FakeDataAccess : IDataAccess
{
    public int GetNumber()
    {
        // A simplified version of the actual implementation
        return 5; // Just an example
    }
}
```

## Spies
Purpose: Spies are stubs that also record some information based on how they were called. They can be queried after execution to verify method invocations.

Use Case: When you want to verify the behavior of the test subject without changing its output.
Example:
```cs
public class SpyDataAccess : IDataAccess
{
    public int NumberOfCalls { get; private set; }

    public int GetNumber()
    {
        NumberOfCalls++;
        return 5; // Stub behavior
    }
}

public void TestMessageProcessor()
{
    // Arrange
    var spySender = new SpyMessageSender();
    var processor = new MessageProcessor(spySender);

    // Act
    processor.ProcessMessage("Hello World");

    // Assert
    Assert.AreEqual(1, spySender.SendMessageCallCount); // Verify the method was called once
    Assert.AreEqual("Hello World", spySender.LastSentMessage); // Verify the message content
}
// In this test, we are not only ensuring that SendMessage is called, but also verifying that it is called the correct number of times and with the correct data. This makes the Spy a powerful tool for testing behavior, especially when the output of the methods is not directly observable or when the state change is internal.
```

## Dummies
Purpose: Dummies are passed around but never actually used. Usually, they are just to fill parameter lists.

Use Case: When a method requires a parameter, but you don't need to use it in your test.
Example:

```cs
public class DummyDataAccess : IDataAccess
{
    public int GetNumber()
    {
        throw new NotImplementedException();
    }
}

// Used as a parameter
var dummy = new DummyDataAccess();
SomeMethod(dummy);

```

## MOQ

1. Mocks
```cs
var mock = new Mock<IMyInterface>();
mock.Setup(x => x.MyMethod()).Returns(value);
// ...use mock.Object...
mock.Verify(x => x.MyMethod()); // Verifies that MyMethod was called

```
2. Stubs
```cs
var stub = new Mock<IMyInterface>();
stub.Setup(x => x.MyProperty).Returns(value);
// ...use stub.Object...
// No need to verify calls

```
3. Spies
```cs
var spy = new Mock<IMyInterface>();
spy.Setup(x => x.MyMethod()).Callback(() => {/* track calls or arguments here */});
// ...use spy.Object...
// After test execution, check the tracked calls or arguments

```

## Limitations
Fakes and Dummies: Moq is not designed for creating Fakes or Dummies. 

Fakes are simpler versions of production objects with actual working implementations, which Moq does not generate. 
Dummies are objects that are never actually used; they just fill parameter spaces, and typically you don't need a framework like Moq for them. 

You can create Dummies manually as empty implementations of an interface or class.


In summary, Moq is a powerful and flexible framework that can be used for more than just mocking in unit tests. However, its use for creating Stubs and Spies is somewhat secondary to its primary function of creating Mocks. For Fakes and Dummies, manual implementation or simpler approaches are generally more suitable.