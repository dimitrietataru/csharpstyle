# **DO** use proper order of items inside a class

```
Within a class, struct, or interface order by group:
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
```
```
Withing each group order by access:
  - public
  - internal
  - protected internal
  - protected
  - private
```
```
Within each access groups, order by static, then non-static:
  - static
  - non-static
```
```
Then, order by readonly, then non-readonly:
  - readonly
  - non-readonly
```

``` csharp
// DO
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