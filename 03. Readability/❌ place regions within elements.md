### ❌ Do not place regions within elements ❌
###

> Code should not contain region(s) within the body of a code statement.

### ✔
``` csharp
#region
public void Method()
{
	// ...
}
#endregion
```

### ❌
``` csharp
public void Method()
{
	#region
	// ...
	#endregion
}
```
