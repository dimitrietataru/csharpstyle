### ❌ Do not wrap elements in opening and closing curly brackets ❌

> Write elements so they expand across multiple lines.  
> Exception: Accessors within properties, events, or indexers.

### ✔
``` csharp
public int Count { get; set; }
```
``` csharp
public object Method()
{
    return null;
}
```

### ❌ 
``` csharp
public object Method() { return null; }
```
``` csharp
public object Method()
	{ return null; }
```
