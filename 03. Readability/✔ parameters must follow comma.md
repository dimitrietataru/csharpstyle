### ✔ Parameters must follow comma ✔
###

> Parameters must be written on same, or next line as previous parameter.

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
public int Sum(
    int a,

    int b,

    int c,

    int d)
{
}
```
