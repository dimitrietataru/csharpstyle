# General

| Object Name      | Notation   | Length | Char Mask  |
|:-----------------|:-----------|:-------|:-----------|
| Class name       | PascalCase |    128 | [A-z][0-9] |
| Constructor name | PascalCase |    128 | [A-z][0-9] |
| Method name      | PascalCase |    128 | [A-z][0-9] |
| Method arguments | camelCase  |    128 | [A-z][0-9] |
| Local variables  | camelCase  |     50 | [A-z][0-9] |
| Constants name   | PascalCase |     50 | [A-z][0-9] |
| Field name       | camelCase  |     50 | [A-z][0-9] |
| Properties name  | PascalCase |     50 | [A-z][0-9] |
| Delegate name    | PascalCase |    128 | [A-z]      |
| Enum type name   | PascalCase |    128 | [A-z]      |

***

**DO** vertically align curly brackets. **Allman** style. [Wikipedia article](https://en.wikipedia.org/wiki/Indentation_style)
``` csharp
namespace Company.Product
{
    public class Program
    {
        static void Main(string[] args)
        {
            if (expression)
            {
                // ...
            }
            else
            {
                // ...    
            }
            
            while (expression)
            {
                // ...
            }
        }
    }
}
```