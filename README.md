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
* [Spacing and readability](#spacing-and-readability)
  * [Tabs and line break](#tabs-and-line-break)
  * [Curly brackets](#curly-brackets)
  * [Square brackets](#square-brackets)
  * [Parenthesis](#parenthesis)
  * [Symbols](#symbols)
  * [Signs](#signs)
  * [Layout](#layout)
  * [Parameters](#parameters)
  * [Misc](#misc)

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
    void Method(int argumentOne, int argumentTwo);
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
        // A.cs
        namespace Project
        {
            class A
            {
            }
        }
        
        // B.cs
        namespace Project
        {
            class B
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

  * ✔ Prefix interface names with letter **I**
  
    * Interface names are *noun* or *adjectives*.
    
        ✔
        ``` csharp
        interface ILogger
        ```
        ``` csharp
        interface IApplicationBuilder
        ```
        ``` csharp
        interface ICollection
        ```

        ✖
        ``` csharp
        interface LoggerSignature
        ```
        ``` csharp
        interface LoggerInterface
        ```
        ``` csharp
        interface LoggerIFace
        ```

  * ✖ Do not (habitually) add new signatures at the end of the interface
  
    ✔
    ``` csharp
    interface ITransfer
    {
        void Connect();
        void Download();
        void Upload(); // Recently added signature
        void Notify();
        void Stop();
    }
    ```
    
    ✖
    ``` csharp
    interface ITransfer
    {
        // ...
        void Stop();
        void Upload(); // Recently added signature
    }
    ```

### Classes

  * ✔ Write each class in its own file
  
    * Use the same notation for file and class name.
    * **Avoid** nested classes.
    
        ✔
        ``` csharp
        // Application.cs
        class Application
        {
        }
        
        // Program.cs
        class Program
        {
        }
        ```
        
        ✖
        ``` csharp
        // Application.cs
        class ApplicationManager
        {
            class Program
            {
            }
        }
        ```

  * ✔ Use PascalCasing when abbreviating three or more characters
  
    * When there are two characters, both are uppercase.
    
        ✔
        ``` csharp
        HtmlHelper htmlHelper;
        XmlDocument xmlDocument;
        IOException ioException;
        UIElement uiElement;
        ```
        
        ✖
        ``` csharp
        HTMLHelper htmlHelper;
        XMLDocument xmlDocument;
        IoException ioException;
        UiElement uiElement;
        ```

  * ✔ Write both accessors single-line or multi-line. Do not mix styles.
  
    * Write both accessors single-line when the accessors are short.
    * Expand both accessors multi-lines when the accessors are longer.
    
        ✔
        ``` csharp
        bool IsEnabled { get; set; }
        ```
        ``` csharp
        bool IsEnabled
        {
            get => this.enabled;
            set => this.enabled = value;
        }
        ```
        ``` csharp
        bool IsEnabled
        {
            get { return this.enabled; }
            set { this.enabled = value; }
        }
        ```
        ``` csharp
        bool IsEnabled
        {
            get
            {
                return this.enabled;
            }
            
            set
            {
                this.enabled = value;
            }
        }
        ```

        ✖
        ``` csharp
        bool IsEnabled
        {
            get;
            set;
        }
        ```
        ``` csharp
        bool IsEnabled
        {
            get { return this.enabled; }
            set => this.enabled = value;
        }
        ```

  * ✔ Prefix local calls with *this*
  
    * Insert the **this** prefix before a call to a class member.
    
        ✔
        ``` csharp
        class B : A
        {
            private int x;
            private int y;
            
            public B(int x, int y, int z)
            {
                base.z = z;
                this.x = x;
                this.y = y;
            }
        }
        ```
        
        ✖
        ``` csharp
        class B : A
        {
            private int m_x;
            private int _y;
            
            public B(int x, int y, int z)
            {
                base.z = z;
                m_x = x;
                _y = y;
            }
        }
        ```

  * ✖ Do not prefix calls with *base* unless local implementation exists
  
    * A call to a member from an inherited class must begin with base only when local class contains an override or implementation.
    
        ✔
        ``` csharp
        public virtual string JoinName(string first, string last)
        {
            return $"Base: {first} {last}";
        }
        
        public override string JoinName(string first, string last)
        {
            return $"This: {first} {last}";
        }
        
        string thisName = this.Join("th", "is");
        string baseName = base.Join("ba", "se");
        ```
        
        ✖
        ``` csharp
        public virtual string JoinName(string first, string last)
        {
            return $"Base: {first} {last}";
        }
        
        string name = base.Join("th", "se");
        ```

  * ✖ Do not split overloads
  
    * When a class has multiple constructors, or multiple methods with the same name, these appear sequentially, with no code in between (NOT even private members).
    
        ✔
        ``` csharp
        class Application
        {
            public Application()
            {
            }
            
            private Application(int x)
            {
            }
            
            public void Execute(int x)
            {
            }
            
            private void Execute(bool status)
            {
            }
            
            public void Display()
            {
            }
        }
        ```

        ✖
        ``` csharp
        class Application
        {
            public Application()
            {
            }
            
            public void Execute(int x)
            {
            }
            
            private Application(int x)
            {
            }
            
            // ...
        }
        ```
        ``` csharp
        class Application
        {
            // ...
            public void Execute(int x)
            {
            }
            
            public void Display()
            {
            }
            
            private void Execute(bool status)
            {
            }
        }
        ```

  * ✖ Do not (habitually) add new methods at the end of the class
  
    ✔
    ``` csharp
    class Transfer
    {
        void Connect()
        {
        }
        
        void Download()
        {
        }
        
        // Recently added method
        void Upload()
        {
        }
        
        void Notify()
        {
        }
        
        void Stop()
        {
        }
    }
    ```
    
    ✖
    ``` csharp
    class Transfer
    {
        // ...
        void Stop()
        {
        }
        
        // Recently added method
        void Upload()
        {
        }
    }
    ```

### Modifiers

  * ✔ Use proper order of items
  
    * Within a class, struct, or interface order by group:
      * Constant Fields
      * Fields
      * Constructors
      * Finalizers (Destructors)
      * Delegates
      * Events
      * Enums
      * Interfaces (Interface implementations)
      * Properties
      * Indexers
      * Methods
      * Structs
      * Classes
    * Withing each group order by access:
      * public
      * internal
      * protected internal
      * protected
      * private protected
      * private
    * Within each access groups, order by static, then non-static:
      * static
      * non-static
    * Then, order by readonly, then non-readonly:
      * readonly
      * non-readonly
      
        ``` csharp
        class Application
        {
            public const int const1 = 1;
            internal const int const2 = 2;
            protected internal const int const3 = 3;
            protected const int const4 = 4;
            private protected const int const5 = 5;
            private const int const6 = 6;

            public static readonly int field1;
            internal static readonly int field2;
            protected internal static readonly int field3;
            protected static readonly int field4;
            private protected static readonly int field5;
            private static readonly int field6;
            public static int field7;
            internal static int field8;
            protected internal static int field9;
            protected static int field10;
            private protected static int field11;
            private static int field12;
            public readonly int field13;
            internal readonly int field14;
            protected static readonly int field15;
            protected readonly int field16;
            private protected readonly int field17;
            private readonly int field18;
            public int field19;
            internal int field20;
            protected internal int field21;
            protected int field22;
            private protected int field23;
            private int field24;

            public Application(...)
            internal Application(...)
            protected internal Application(...)
            protected Application(...)
            private protected Application(...)
            private Application(...)
            
            // ...
        }
        ```

  * ✔ Declare access modifiers
  
    * It is allowed to define elements without access modifier and C# will automatically assign an access level.
    * It is a good practice to explicitly define an access modifier for each element. This removes the need for the reader to make assumptions about code and improves readability.
    
        ✔
        ``` csharp
        public class A
        {
            private A()
            {
            }

            private void Method()
            {
            }
        }
        ```

        ✖
        ``` csharp
        class A
        {
            A()
            {
            }

            void Method()
            {
            }
        }
        ```

### Documentation

  * ✔ Precede documentation elements with a (single) blank line
  
    ✔
    ``` csharp
    int First { get; set; }

    /// <summary>
    /// ...
    /// </summary>
    int Second { get; set; }
    ```
    
    ✖
    ``` csharp
    int First { get; set; }
    /// <summary>
    /// ...
    /// </summary>
    int Second { get; set; }
    ```

  * ✖ Do not follow documentation elements with blank line(s)

    ✔
    ``` csharp
    /// <summary>
    /// ...
    /// </summary>
    int First { get; set; }
    ```
    
    ✖
    ``` csharp
    /// <summary>
    /// ...
    /// </summary>
    
    int First { get; set; }
    ```

  * ✔ Documentation header must begin with a single space
  
    * Header lines should begin with a single space after the three leading forward slashes.
    
        ✔
        ``` csharp
        /// <summary>
        /// ...
        /// </summary>
        void Method();
        ```
        
        ✖
        ``` csharp
        ///<summary>
        ///...
        ///</summary>
        void Method()
        ```

### Regions

  * ✖ Do not use regions. Seriously!
  
    * *Try* to avoid using regions. If you are already doing it, do it right!
    * In many editors, including VS, the regions will appear collapsed by default, hiding the code within the region.
    * It is generally a bad practice to hide code, as this can lead to bad decisions as the code is maintained over time.
    
        ✔
        ```
        (Ctrl + M, O) - Collapse to definitions
        (Ctrl + M, L) - Toggle all outlining
        ```

  * ✖ Do not place regions within elements
  
    * Code should not contain region(s) within the body of a code statement.
    
        ✔
        ``` csharp
        #region
        void Method()
        {
            // ...
        }
        #endregion
        ```
        
        ✖
        ``` csharp
        void Method()
        {
            #region
            // ...
            #endregion
        }
        ```

  * ✖ Do not write embedded regions
  
    * Do not write regions between declaration of statement and opening curly brackets.
    * Place regions outside statement body.
    
        ✔
        ``` csharp
        #region ...
        void Method()
        {
        }
        #endregion
        ```

        ✖
        ``` csharp
        void Method()
        #region ...
        {
        }
        #endregion
        ```
        ``` csharp
        void Method()
        #region ...
        {
        #endregion
        }
        ```

### Comments

> Good code is its own best documentation. As you're about to add a comment, ask yourself,
> "How can I improve the code so that this comment isn't needed?"
> Improve the code and then document it to make it even clearer. <br>
> &mdash; Steve McConnell

  * ✔ Write self-documenting code and ignore the rest of this section. Seriously!

  * ✔ Write comments in *English*.
  
  * ✔ Comments longer than a word are capitalized and use punctuation.
  
  * ✖ Do not add empty comments
  
  * ✖ Avoid writing comments to explain bad code. Refactor the code to make it self-explanatory.
  
  * ✔ Begin single-line comments with a single space
  
    ✔
    ``` csharp
    // Single-line comment
    ```
    
    ✖
    ``` csharp
    //Single-line comment
    //  Single-line comment
    ```

  * ✔ Write single-line comments properly
  
    * Single-line comments should always be preceded by a single blank line.
    * Single-line comments should never be followed by blank line(s).
    
        ✔
        ``` csharp
        int x;
        
        // ...
        int y;
        ```

        ✖
        ``` csharp
        int x;
        
        // This comment is not valid
        
        int y;
        ```
        ``` csharp
        int x;
        // This comment is not valid
        
        int y;
        ```

  * ✖ Do not write embedded comments
  
    * Do not write comments between declaration of statement and opening curly brackets.
    * Place comments above statements, or within statement body.
    
        ✔
        ``` csharp
        // This method does something..
        void Method()
        {
        }
        ```

        ✖
        ``` csharp
        void Method() // This method does something..
        {
        }
        ```
        ``` csharp
        void Method()
        // This method does something..
        {
        }
        ```

  * ✔ Use four forward slashes to indicate commented-out code
  
    * To differentiate comments from commented-out code, use four forward slashes.
    * Do not add space(s) between slashes and code.
    
        ✔
        ``` csharp
        int Method()
        {
            ////int result = 1 + 2;
            ////return result;
            
            // ...
            return 2 + 1;
        }
        ```

        ✖
        ``` csharp
        int Method()
        {
            //int result = 1 + 2;
            //return result;
            
            // ...
            return 2 + 1;
        }
        ```

  * ✔ Use **Task List** friendly comments

    * [Using the Task List](https://docs.microsoft.com/en-us/visualstudio/ide/using-the-task-list?view=vs-2017)
    * To open the **Task List** window in Visual Studio use **Ctrl + \\, T**
    * Use **TODO** to note missing features or functionality that should be added later.
    * Use **HACK** to note code where questionable coding practices were used.
    
        ✔ 
        ``` csharp
        void Method()
        {
            // TODO: ...
            
            int x = 10;
            int y = 20;
            
            // TODO: ...
        }
        ```

## Spacing and readability

### Tabs and line break

  * ✖ Do not use tabs
  
    * The length of the tab character can vary depending upn the editor used to view the code.
    * This can cause spacing and idexing of the code to vary from the developer's intent and can make the code difficult to read and understand.
    * **Each level of indentation should consist of four spaces.**
    
        ✔
        ``` csharp
        var x = Method(
            100,
            200,
            300);
        ```

        ✖
        ``` csharp
        var x = Method(
                       100,
                       200,
                       300);
        var y = Method(
                100,
                200,
                300);
        ```

  * ✔ Remove unnecessary code
  
    * Remove any code which once removed does not change the overall logic of the code.
    * Remove duplicate code.
    
        ✔
        ``` csharp
        int x = 1 + 2;
        ```
        
        ✖
        ``` csharp
        try
        {
            int x = 1 + 2;
        }
        catch (Exception ex)
        {
        }
        ```

  * ✔ Break lines correctly
  
    * Break:
      * **.**  - before dot separator
      * **,**  - after comma
      * **=>** - after lambda operator
      * **{**  - before opening curly brackets for in-line initializations
      * before logical operators
    * Split method arguments by the following rule: **all on same line, or all on different line**.
    
        ✔
        ``` csharp
        Method(arg1, arg2, arg3);
        ```
        ``` csharp
        await Method(
            arg1, arg2, arg3);
        ```
        ``` csharp
        var x = Method(
            arg1,
            arg2);
        ```
        ``` csharp
        if ((expression1 || expression2)
            && (expresion3 && expression4)
            || expression5
            || expression6)
        ```
        ``` csharp
        var x = collection
            .Where(item => item.RegisterDate.Year > 2000)
            .Join(
                collection2,
                collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy }),
                collection2 => new { Date = collection2.Date, Owner = collection2.User },
                (collection1, collection2) => new { OldEntry = collection1, NewEntry = collection2 })
            .Select(pair =>
                new
                {
                    Id = pair.OldEntry.Id,
                    X = pair.OldEntry.X,
                    Y = pair.NewEntry.Y
                })
            .ToList();
        ```
        
        ✖
        ``` csharp
        var x = collection
            .Join(collection2, // DO NOT
                collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy }),
                collection2 => new { Date = collection2.Date, Owner = collection2.User },
                (collection1, collection2) => new { OldEntry = collection1, NewEntry = collection2 })
        // ...
        ```
        ``` csharp
        var x = collection
            .Where(item => item.RegisterDate.Year > 2000)
            .Select(item => item.Id).ToList(); // DO NOT
        ```
        ``` csharp
        var x = collection.Where(item => item.RegisterDate.Year > 2000) // DO NOT
            .Join(
        // ...
        ```






### Curly brackets

### Square brackets

### Parenthesis

### Symbols

### Signs

### Layout

### Parameters

### Misc
