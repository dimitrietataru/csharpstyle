# ✔ Chain statement blocks without blank lines ✔

> Some types of C# statements can only be used when chained to the bottom of another statement.  
> Remove any blank lines between chained statements.

``` csharp
// DO
try
{   
}
catch
{
}
finally
{
}

if (true)
{
}
else
{
}
```

``` csharp
// DON'T
try
{
}

catch
{
}

finally
{
}

// DON'T
if (true)
{
}

else
{
}
```
