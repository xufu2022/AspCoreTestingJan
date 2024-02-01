# Working with Data-driven Tests

## [Fact] versus [Theory]
 Introducing data-driven tests
 - Inline data
 - Member data
 - Class data
 - Type-safe approach
 - Data from an external source

## Introducing Theories and Data-driven Tests

```cs
[Fact]
 public void 
CreateInternalEmployee_InternalEmployeeCreated_MustHaveAttendedFirstObligatoryCourse()
 {
 ...
 // Assert
 Assert.Contains(internalEmployee.AttendedCourses, course => 
course.Id == Guid.Parse("37e03ca7-c730-4351-834c-b66f280cdb01"));_
 }

 [Fact]
 public void 
CreateInternalEmployee_InternalEmployeeCreated_MustHaveAttendedSecondObligatoryCourse()
 { 
...
 // Assert
 Assert.Contains(internalEmployee.AttendedCourses, course => 
course.Id == Guid.Parse("1fd115cf-f44c-4982-86bc-a8fe2e4ff83e"));
 }

```
 A test which is always true.  They test invariant conditions.

 Use **TheoryData** for type-safe data
 - [InlineData]
 - [MemberData]
 - [ClassData]

## Summary

[Theory] enables data-driven tests
- Inline data
- Member data
- Class data
- Strongly-typed data with TheoryData
- Getting data from an external sour