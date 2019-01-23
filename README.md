# C# coding standards, conventions, and guidelines

* [Tour of C# language](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/)
  - [Program structure](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/program-structure)
  - [Types and variables](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/types-and-variables)
  - [Expressions](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/expressions)
  - [Statements](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/statements)
  - [Classes and objects](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/classes-and-objects)
  - [Structs](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/structs)
  - [Arrays](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/arrays)
  - [Interfaces](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/interfaces)
  - [Enums](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/enums)
  - [Delegates](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/delegates)
  - [Attributes](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/attributes)

## Credits
This C# style recommends best practices so that developers can write code maintainable by other C# developers.  
The document contains data collected from various sources, language styles, and communities.  

  - [docs.microsoft.com](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/)
  - [dofactory.com](https://www.dofactory.com/reference/csharp-coding-standards)
  - [github.com/ktaranov](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md)
  - [c-sharpcorner.com](https://www.c-sharpcorner.com/article/stop-use-var-everywhere-and-think-before-use-underscore-with-private-variable-in/)
  - [stylecop.soyuz5.com](http://stylecop.soyuz5.com/StyleCop%20Rules.html)
  - [google.github.io](https://google.github.io/styleguide/javaguide.html)

## Table of contents

* [General](#general)
  * [Naming](#naming)
  * [Brackets](#brackets)
* [Structure and layout](#structure-and-layout)
  * [Namespaces](#namespaces)
  * [Interfaces](#interfaces)
  * [Classes](#classes)
  * [Modifiers](#modifiers)
  * [Documentation](#documentation)
  * [Regions](#regions)
  * [Comments](#comments)

## General

### Naming

  * ✔ Use PascalCase and camelCase
  
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

  * ✔ Use PascalCasing to name classes, methods, and properties

    ``` csharp
    class ClassName
    ```
    ``` csharp
    void MethodName();
    ```
    ``` csharp
    string PropertyName { get; set; }
    ```
    
  * ✔ Use camelCasing to name method arguments, local variables, and fields
  
    ``` csharp
    string fieldName;
    ```
    ``` csharp
    void Method(int parameterOne, int parameterTwo);
    ```
    ``` csharp
    Method(argumentOne, argumentTwo);
    ```
    ``` csharp
    int localName = 10;
    ```

### Brackets

  * ✔ Vertically align curly brackets
  
    * **Allman** style. [Wikipedia](https://en.wikipedia.org/wiki/Indentation_style)
    
        ``` csharp
        namespace Application
        {
            class Program
            {
                static void Main(string[] args)
                {
                    if (...)
                    {
                    }
                    else
                    {
                    }
                    
                    while (...)
                    {
                    }
                }
            }
        }
        ```

  * ✖ Do not omit curly brackets
  
    * **Always** wrap the body of the statement in curly brackets.
    * Although this is legal in C#, the curly brackets are required to be present. They increase the readability and maintainability of the code.
    
        ✔
        ``` csharp
        if (true)
        {
            return this.x;
        }
        ```
        ``` csharp
        if (true)
        {
            this.x = 42;
            return this.x;
        }
        ```
        
        ✖
        ``` csharp
        if (true) return this.x;
        ```
        ``` csharp
        if (true)
            return this.x;
        ```
        ``` csharp
        if (true)
            this.x = 42;      
            return this.x;
        ```

  * ✖ Do not place curly brackets on same line with statements
  
    * Ensure that both opening and closing curly brackets are placed on their own (vertical) line.
    * Curly brackets should not share their line with any other code, other than comments.
    
        ✔
        ``` csharp
        void Method()
        {
            lock (this)
            {
                return this.x;
            }
        }
        ```
        
        ✖
        ``` csharp
        void Method() {
            lock (this) {
                return this.x;
            }
        }
        ```
        ``` csharp
        void Method()
        {
            lock (this) { return this.x; }
        }
        ```

## Structure and layout

### Namespaces

  * ✔ Organize namespaces with a clearly defined structure
  
    * Use PascalCasing to name namespaces.
    
        ``` csharp
        namespace Company.Product.Module.SubModule;
        namespace Product.Module.Component;
        namespace Product.Layer.Module.Group;
        ```

  * ✖ Do not place multiple namespaces within a single file
  
    * Ensure that each file contains only one namespace.
    * To increase long-term mentainability of the code-base, each file should contain at most one namespace.
    
        ``` csharp
        // ClassOne.cs
        namespace Project
        {
            class ClassOne
            {
            }
        }
        
        // ClassTwo.cs
        namespace Project
        {
            class ClassTwo
            {
            }
        }
        ```

  * ✔ Separate non-static from static usings
  
    * Order usings alphabetically. Order by non-static, then by static.
    * Do not separate usings, or static/non-static blocks by blank line(s).
    
        ✔
        ``` csharp
        using System;
        using System.Linq;
        using static System.Linq.Enumerable;
        using static System.Math;
        ```
        
        ✖
        ``` csharp
        using System;
        using System.Linq;
        
        using static System.Linq.Enumerable;
        using static System.Math;
        ```
        ``` csharp
        using System;
        using static System.Math;
        using System.Linq;
        using static System.Linq.Enumerable;
        ```

  * ✖ Do not line-wrap using statements
  
    * Always write using statements on a single line.
    
        ✔
        ``` csharp
        using System.Security.Cryptography;
        ```
        
        ✖
        ``` csharp
        using System
            .Security.Cryptography;
        ```

### Interfaces

### Classes

### Modifiers

### Documentation

### Regions

### Comments