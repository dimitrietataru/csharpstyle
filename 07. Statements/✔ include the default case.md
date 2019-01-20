### ✔ Include the default case ✔
###

> Each switch statement includes a default statement group, even if it contains no code.  
> Exception: A switch statement for an enum type may omit the default statement group, if it includes explicit cases covering all possible values of that type.  
> This enables IDEs or other static analysis tools to issue a warning if any cases were missed.

### ✔
``` csharp
switch (x)
{
    case 1:
        HandleOne();
        break;
    case 2:
        HandleTwo();
        break;
    default:
        break;
}
```
``` csharp
public enum Status
{
    Done,
    Failed
}

switch (status)
{
    case Done:
        HandleDone();
        break;
    case Failed:
        HandleFailed();
        break;
}
```

### ❌ 
``` csharp
switch (x)
{
    case 1:
        HandleOne();
        break;
    case 2:
        HandleTwo();
        break;
}
```
