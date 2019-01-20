### ✔ Remove unnecessary code ✔
###

> Remove any code which once removed does not change the overall logic of the code.  
> Remove duplicate code.

### ✔
``` csharp
try
{
    int x = MethodThatThrowsException();
}
catch (Exception ex)
{
    // ...
}
```

### ❌ 
``` csharp
try
{
    int x = a + b;
}
catch (Exception ex)
{
    // ...
}
```
``` csharp
// Empty blocks
try
{
}
finally
{   
}
```
``` csharp
// Empty block
unsafe
{
}
```
