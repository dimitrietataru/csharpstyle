### ✔ Parameter list must follow declaration ✔
###

> The start of the parameter list of a method or indexer must begin on same line or next line of the opening parenthesis.

### ✔
``` csharp
public int Sum(int a, int b, int c, int d)
{
}
```
``` csharp
public int Sum(
    int a, int b, int c, int d)
{
}
```
``` csharp
public int Sum(
    int a,
    int b,
    int c,
    int d)
{
}
```

### ❌
``` csharp
public int Sum(int a, int b, int c,

    int d)
{
}
```
``` csharp
public int Sum(

    int a, int b, int c, int d)
{
}
```
``` csharp
public int Sum(

    int a,
    int b,
    int c,
    int d)
{
}
```
