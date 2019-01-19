### ✔ Precede documentation elements with a blank line ✔
###

> Documentation elements should always be preceded by a blank line.  

### ✔
``` csharp
public bool IsValid { get; set; }

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
public bool IsValid { get; set; }
/// <summary>
/// Gets a value indicating whether the control is enabled.
/// </summary>
public bool Enabled
{
    get { return this.enabled; }
}
```
