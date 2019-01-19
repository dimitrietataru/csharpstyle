### ✔ Ensure comma is on same line as previous parameter ✔
###

> Always write commas on same line as previous parameter.

### ✔
``` csharp
string name = GetName(
    first,
    last);
```
``` csharp
public int this[
    int x,
    int y]
{
    // ...
}
```

### ❌
``` csharp
string name = GetName(
    first
    ,last);
```
``` csharp
public int this[
    int x
    ,int y]
{
    // ...
}
```
