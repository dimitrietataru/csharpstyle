### ✔ Declare access modifiers ✔
###

> It is allowed to define elements without access modifier, and C# will automatically assign an access level.  
> It is a good practice to explicitly define an access modifier for each element. This removes the need for the reader to make assumptions about code and improves readability.

### ✔
``` csharp
public class A
{
    public A(int x)
    {
    }

    private A()
    {
    }

    private Method()
    {
    }
}
```

### ❌ 
``` csharp
class A
{
    A(int x)
    {
    }

    A()
    {
    }
    
    Method()
    {
    }
}
```
