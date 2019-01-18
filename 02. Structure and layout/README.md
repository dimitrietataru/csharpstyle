# Structure

***

**DO** organize namespaces with a clearly defined structure. Use **PascalCasing**.
``` csharp
namespace Company.Product.Module.SubModule;
namespace Product.Module.Component;
namespace Product.Layer.Module.Group;
```

---

**DO NOT** use Tab characters for indentation. Use four spaces instead.

---

**DO NOT** line-wrap using statements.
```csharp
// Correct
using System.IO;
using System.Security.Cryptography;

// Avoid
using System.IO;
using System
    .Security.Cryptography;
```

---

**DO** separate *non-static* from *static* usings. Alphabetically ordered by non-static, then static, with no blank spaces.
```csharp
using System;
using System.Linq;
using static System.Linq.Enumerable;
using static System.Math;
```

---

**DO** use one blank line between file sections (usings, namespace, constructors, methods).  
**DO NOT** leave empty blank lines, or multiple blank lines.
``` csharp
// Correct
using System;

namespace Product.Module
{
    class Application
    {
        private int count;
    
        public Application()
        {
        }
        
        public void Execute()
        {
        }
        
        public bool IsRunning()
        {
        }
    }
}

// Avoid
using System;
// extra blank line
using System.Threading.Tasks;

// extra blank line
namespace Product.Module
{
    private int count; // missing blank line
    public Application()
    {
    } // missing blank line
    public void Execute()
    {
    }
    
    // extra blank line
    public bool IsRunning()
    {
    }
}
```

---

**DO** use proper order of items inside a class. [Stylecop ordering rules](http://stylecop.soyuz5.com/Ordering%20Rules.html)
* Within a class, struct, or interface (SA1201 and SA1203)
  - Constant Fields
  - Fields
  - Constructors
  - Finalizers (Destructors)
  - Delegates
  - Events
  - Enums
  - Interfaces (Interface implementations)
  - Properties
  - Indexers
  - Methods
  - Structs
  - Classes
* Withing each group order by access (SA1202)
  - public
  - internal
  - protected internal
  - protected
  - private
* Within each access groups, order by static, then non-static (SA1204)
  - static
  - non-static
* Then, order by readonly, then non-readonly (SA1214 and SA1215)
  - readonly
  - non-readonly

``` csharp
public class Application
{
    public const int const1 = 1;
    internal const int const2 = 2;
    protected internal const int const3 = 3;
    protected const int const4 = 4;
    private const int const5 = 5;

    public static readonly int field1;
    internal static readonly int field2;
    protected internal static readonly int field3;
    protected static readonly int field4;
    private static readonly int field5;
    public static int field6;
    internal static int field7;
    protected internal static int field8;
    protected static int field9;
    private static int field10;
    public readonly int field11;
    internal readonly int field12;
    protected static readonly int field13;
    protected readonly int field14;
    private readonly int field15;
    public int field16;
    internal int field17;
    protected static int field18;
    protected int field19;
    private int field20;

    public Application() { }
    internal Application(int internalCtor) { }
    protected internal Application(string protectedInternalCtor) { }
    protected Application(long protectedCtor) { }
    private Application(decimal privateCtor) { }
    
    // ...
}
```

---
