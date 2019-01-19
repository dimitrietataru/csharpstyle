### ❌ Do not write embedded comments ❌
###

> Do not write comments between declaration of statement and opening curly brackets.  
> Place comments above statements, or within statement body.

### ✔
``` csharp
// Check equality
if (x == y)
{
}
```

### ❌
``` csharp
if (x == y) // Check equality
{
}
```
``` csharp
if (x == y)
// Check equality
{
}
```
