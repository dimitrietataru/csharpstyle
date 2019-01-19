### ❌ Do not omit curly brackets ❌
###

> Always wrap the body of the statement in curly brackets.  
> Although this is legal in C#, the curly brackets are required to be present. They increase the readability and maintainability of the code.

### ✔
``` csharp
if (true)
{
    return this.value;
}
```
``` csharp
if (true)
{
    this.value = 2;
    return this.value;
}
```

### ❌ 
``` csharp
if (true) return this.value;
```
``` csharp
if (true)
    return this.value;
```
``` csharp
if (true)
    this.value = 2;      
    return this.value;
```
