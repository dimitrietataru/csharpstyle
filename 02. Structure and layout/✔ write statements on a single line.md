# ✔ Write statements on a single line ✔
#

> Do not write multiple statements on the same line.  
> Do not write statements and curly brackets on the same line.

### ✔
``` csharp
public object Method()
{
    lock (this)
    {
        int a = 1;
        int b = 2;
        return a + b;
    }
}
```

### ❌ 
``` csharp
public object Method()
{
    lock (this)
    {
        int a = 1; int b = 2;
        return a + b;
    }
}
```
``` csharp
public object Method()
{
    lock (this) {
        int a = 1;
        int b = 2;
        return a + b; }
}
```
``` csharp
public object Method()
{
    lock (this) { int a = 1; int b = 2; return a + b; }
}
```
