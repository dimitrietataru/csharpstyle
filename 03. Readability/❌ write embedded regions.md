### ❌ Do not write embedded regions ❌
###

> Do not write regions between declaration of statement and opening curly brackets.  
> Place regions outside statement body.

### ✔
``` csharp
#region Verify condition..
if (true)
{
}
#endregion
```

### ❌
``` csharp
if (true)
#region
{
}
#endregion
```
``` csharp
if (true)
#region
{
#endregion
}

```
``` csharp
if (true)
{
#region
}
#endregion
```
