### ✔ Fields must be private ✔
###

> Fields should always be private.  
> For mentainability reasons, properties should always be used as the mechanism for exposing fields outside of a class.  
> This allows the internal implementation of the property to change over time without changing the interface of the class.  
> Exceptions: Fields within structs are allowed to have any access level.

### ✔
``` csharp
private int count;

public int Count
{
    get { return this.count };
    set { this.count = value; }
}
```

### ❌ 
``` csharp
public int count;
```
