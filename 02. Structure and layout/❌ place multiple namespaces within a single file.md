### ❌ Do not place multiple namespaces within a single file.md ❌
###

> Ensure that each file contains only one namespace.  
> To increase long-term mentainability of the code-base, each file should contain at most one namespace.

### ✔
``` csharp
// ClassOne.cs
namespace Project.One
{
    public class ClassOne
    {
    }
}
```
``` csharp
// ClassTwo.cs
namespace Project.Two
{
    public class ClassTwo
    {
    }
}
```

### ❌ 
``` csharp
// ClassOneAndTwo.cs
namespace Project.One
{
    public class ClassOne
    {
    }
}

namespace Project.Two
{
    public class ClassTwo
    {
    }
}
```
