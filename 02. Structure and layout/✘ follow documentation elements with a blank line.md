# **DO NOT** follow documentation elements with a blank line

> Documentation elements should always be followed by blocks of code.  

``` csharp
// DO
/// <summary>
/// Gets a value indicating whether the control is enabled.
/// </summary>
public bool Enabled
{
    get { return this.enabled; }
}
```

``` csharp
// DON'T
/// <summary>
/// Gets a value indicating whether the control is enabled.
/// </summary>

public bool Enabled
{
    get { return this.enabled; }
}
```
