# ❌ Do not wrap elements in opening and closing curly brackets ❌

> Write elements, so they expand across multiple lines.  
> Exception: Accessors within properties, events, or indexers.

``` csharp
// DO
public int Count { get; set; }

public object Method()
{
    return null;
}
```

``` csharp
// DON'T
public object Method() { return null; }
```
