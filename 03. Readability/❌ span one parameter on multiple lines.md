### ❌ Do not span one parameter on multiple lines ❌
###

> Ensure parameters do not span multiple lines.  
> This ensures method calls don't become excessively complicated, or unreadable.  

> Exceptions:  
> THE FIRST parameter is allowed to span across multiple lines.  
> ANONYMOUS METHOD passed as parameter is always allowed to span multiple lines.

### ✔
``` csharp
return JoinStrings(
    "a" +
    "b",
    "c");
```
``` csharp
return JoinStrings(
    "a",
    "b" + "c");
```

### ❌
``` csharp
return JoinStrings(
    "a",
    "b" +
    "c");
```
