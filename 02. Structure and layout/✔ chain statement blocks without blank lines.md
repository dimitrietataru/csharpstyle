### ✔ Chain statement blocks without blank lines ✔
###

> Some types of C# statements can only be used when chained to the bottom of another statement.  
> Remove any blank lines between chained statements.

### ✔
``` csharp
try
{   
}
catch
{
}
finally
{
}
```
``` csharp
if (true)
{
}
else
{
}
```

### ❌ 
``` csharp
try
{
}

catch
{
}

finally
{
}
```
``` csharp
if (true)
{
}

else
{
}
```
