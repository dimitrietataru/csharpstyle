### ❌ Do not follow documentation elements with a blank line ❌

> Documentation elements should always be followed by blocks of code.  

### ✔
``` csharp
/// <summary>
/// Gets a value indicating whether the control is enabled.
/// </summary>
public bool Enabled
{
    get { return this.enabled; }
}
```

### ❌ 
``` csharp
/// <summary>
/// Gets a value indicating whether the control is enabled.
/// </summary>

public bool Enabled
{
    get { return this.enabled; }
}
```
