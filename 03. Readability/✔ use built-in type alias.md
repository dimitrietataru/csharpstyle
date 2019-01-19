### ✔ Use built-in type alias ✔
###

> Use built-in alias for types.  
> Do not use basic types.  
> Do not use full namespace for types.

| Alias   | Type    | Fully qualified type |
|:--------|:--------|:---------------------|
| bool    | Boolean | System.Boolean       |
| byte    | Byte    | System.Byte          |
| char    | Char    | System.Char          |
| decimal | Decimal | System.Decimal       |
| double  | Double  | System.Double        |
| short   | Int16   | System.Int16         |
| int     | Int32   | System.Int32         |
| long    | Int64   | System.Int64         |
| object  | Object  | System.Object        |
| sbyte   | SByte   | System.SByte         |
| float   | Single  | System.Single        |
| string  | String  | System.String        |
| ushort  | UInt16  | System.UInt16        |
| uint    | UInt32  | System.UInt32        |
| ulong   | UInt64  | System.UInt64        |

### ✔
``` csharp
int index;
bool isTrue;
object obj;
string name;
```

### ❌
``` csharp
Int32 index;
Boolean isTrue;
Object obj;
String name;
```
