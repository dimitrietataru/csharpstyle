### ✔ Space commas correctly ✔
###

> Commas should always be followed by a single space, unless it is the last character on the line.  
> Commas should never be preceded by any whitespace.

### ✔
``` csharp
public void Method(int a, int b, int c)
{
    // ...
}
```
``` csharp
public void Method(
    int a,
    int b,
    int c)
{
    // ...
}
```
``` csharp
Method(a, b, c);
```

### ❌ 
``` csharp
public void Method(int a,int b,int c)
{
    // ...
}
```
``` csharp
public void Method(int a ,int b ,int c)
{
    // ...
}
```
``` csharp
public void Method(int a , int b , int c)
{
    // ...
}
```
``` csharp
public void Method(
    int a
    ,int b
    ,int c)
{
    // ...
}
```
``` csharp
public void Method(
    int a
    , int b
    , int c)
{
    // ...
}
```
``` csharp
Method(a,b,c);
```
