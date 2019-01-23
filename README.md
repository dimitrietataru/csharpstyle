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
* [Types and variables](#types-and-variables)
* [Expressions](#expressions)
* [Statements](#statements)
* [Queries and Linq](#queries-and-linq)

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
    * Split method arguments by the following rule: **all on same line, or all on own line**.
    
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
                collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy },
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

  * ✔ Space curly brackets correctly
  
    * Opening curly brackets should be preceded by a single space, unless it's part of a method call.
    * Opening curly brackets should be followed by a single space, unless it's the last character on the line.
    * Closing curly brackets should be followed by a single space, unless it's the last character on the line, or it's followed by closing parenthesis, comma, or semicolon.
    * Closing curly brackets should be preceded by a single space, unless it's the first character on the line.
    
        ✔
        ``` csharp
        void Method()
        {
        }
        ```
        ``` csharp
        var x = Method({ 1, 2 }, 3);
        var x = Method({ 1, 2 } + { 3, 4 }, 5);
        ```
        ``` csharp
        int[] ints = new[] { 1, 2, 3 };
        int[] ints = new[] {1, 2, 3}; // Generally accepted, but be consistent!
        ```
        ``` csharp
        var x = new { X = 1, Y = "2" };
        var x = new
        {
            X = 1,
            Y = "2"
        };
        ```

        ✖
        ``` csharp
        void Method() { }
        void Method() {
        }
        void Method()
        {}
        void Method()
        { }
        ```
        ``` csharp
        var x = Method( { 1, 2 } , 3);
        var x = Method( { 1, 2 } + { 3, 4 } , 5);
        ```
        ``` csharp
        int[] ints = new[]{ 1, 2, 3 };
        ```
        ``` csharp
        var x = new{X = 1, Y = "2"};
        ```

  * ✔ Follow closing curly brackets by a blank line
  
    * Ensure a blank line follows closing curly brackets.  
    
        ✔
        ``` csharp
        void Method()
        {
            if (...)
            {
            }
        }
        ```
        
        ✖
        ``` csharp
        void Method()
        {
            if (...)
            {
            }}
        ```

  * ✖ Do not wrap elements in opening and closing curly brackets
  
    * Write elements so they expand across multiple lines.
    * Exception: accessors within properties, events, or indexers.
    
        ✔
        ``` csharp
        int Property { get; set; }
        ```
        ``` csharp
        if (...)
        {
            return true;
        }
        ```

        ✖
        ``` csharp
        if (...) { return true; }
        ```

  * ✖ Do not follow or precede opening curly brackets with a blank line
  
    * Opening curly brackets should always be followed by statements, not blank line(s).
    * Opening curly brackets should never be preceded by blank line(s).
    
        ✔
        ``` csharp
        void Method()
        {
            // ...
        }
        ```
        
        ✖
        ``` csharp
        void Method()
        
        {
        
            // ...
        }
        ```

  * ✖ Do not follow or precede closing curly brackets with a blank line
  
    * Closing curly brackets should always be preceded by statements, not blank line(s).
    * Closing curly brackets should never be followed by blank line(s).
    
        ✔
        ``` csharp
        void Method()
        {
            // ...
        }
        ```

        ✖
        ``` csharp
        void Method()
        {
            // ...
        
        }
        
        ```

### Square brackets

  * ✔ Space square brackets correctly
  
    * Opening square brackets should never be followed by a whitespace, unless it's the last character on the line.
    * Opening square brackets should never be preceded by a whitespace, unless it's the first character on the line.
    * Closing square brackets should never be preceded by a whitespace, unless it's the first character on the line.
    * Closing square brackets should never pe followed by a whitespace, except when it's followed by certain operators, or it is part of an array initialization.
    
        ✔
        ``` csharp
        int x = array[10];
        int x = array[10] + 1;
        int x = matrix[10, 10];
        ```
        ``` csharp
        int[] array = new int[2];
        int[] array = new int[] { 1, 2, 3 };
        int[] array = new[] { 1, 2, 3 };
        int[,] matrix = new int[2, 2];
        ```
        
        ✖
        ``` csharp
        int x = array [10];
        int x = array[10]+1;
        int x = matrix [10,10];
        ```
        ``` csharp
        int [] array = new int[2];
        int[] array = new int [] { 1, 2, 3 };
        int[] array = new [] { 1, 2, 3 };
        ```

### Parenthesis

  * ✔ Space parenthesis correctly
  
    * Opening parenthesis should not be preceded by a whitespace, unless it is the first character on a line.
    * Opening parenthesis is allowed to be preceded by whitespace when it's preceded by certain C# keywords (if, while, for etc..).
    * Opening parenthesis is allowed to be preceded by whitespace when it follows an operator symbol within an expression.
    * Closing parenthesis should not be followed by a whitespace.
    * Closing parenthesis is not allowed to be followed by whitespace when it comes at the end of a cast.
    * Closing parenthesis is allowed to be followed by whitespace when it's followed by certain operator symbols.

        ✔
        ``` csharp
        void Method();
        ```
        ``` csharp
        int x = (a + b) * c;
        int x = a / (b - c);
        ```
        ``` csharp
        int x = (int)((a + b) % c);
        ```
        ``` csharp
        if (a == b)
        ```
        ``` csharp
        Method(Math.Max(1, 2), Math.Sqrt(144));
        ```
        ``` csharp
        LongMethodCall(
            (200 - 144) * 3
            + (999 / 18),
            1,
            2);
        ```
        
        ✖
        ``` csharp
        void Method ()
        ```
        ``` csharp
        int x = (a + b)*c;
        int x = a/(b - c);
        ```
        ``` csharp
        int x = (int) ((a + b) % c);
        ```
        ``` csharp
        if(a == b)
        ```
        ``` csharp
        Method( Math.Max(1, 2) , Math.Sqrt(144) );
        ```

  * ✔ Open parenthesis on declaration line
  
    * The opening parenthesis in a call to a method must be placed on same line as the method.
    * The opening parenthesis in a call to an indexer must be placed on same line as the indexer name.
    * The opening parenthesis in a method declaration must be placed on same line as the method.
    * The opening parenthesis in an indexer declaration must be placed on same line as the indexer name.
    
        ✔
        ``` csharp
        bool Method(int x, int y);
        ```
        ``` csharp
        bool isTrue = Method();
        ```
        ``` csharp
        int x = array[0];
        ```
        ``` csharp
        int this[int x]
        {
            get => array[x];
        }
        ```

        ✖
        ``` csharp
        bool Method
        (
            int x,
            int y
        );
        ```

* ✔ Close parenthesis on line with last parameter

    * The closing parenthesis in a call to a method must be placed on same line as the last parameter.
    * The closing parenthesis in a call to an indexer must be placed on same line as the last parameter.
    * The closing parenthesis in a method declaration must be placed on same line as the last parameter.
    * The closing parenthesis in an indexer declaration must be placed on same line as the last parameter.
    
        ✔
        ``` csharp
        bool Method(int x, int y);;
        ```
        ``` csharp
        bool isTrue = Method();
        ```
        ``` csharp
        int x = array[0];
        ```
        ``` csharp
        int this[int x]
        {
            get => array[x];
        }
        ```

        ✖
        ``` csharp
        bool Method
        (
            int x,
            int y
        );
        ```
        ``` csharp
        bool isTrue = Method(
            100
        );
        ```
        ``` csharp
        int x = matrix[
            1,
            2
        ];
        ```

  * ✖ Do not use unnecessary parenthesis
  
    * It is possible to insert parenthesis around virtually any type of expression, statement, or clause.
    * Excessive parenthesis can have a negative effect, making it more difficult to read and maintain code.
    
        ✔
        ``` csharp
        int x = y + z;
        string y = this.Method().ToString();
        ```
        ``` csharp
        return a + b;
        return x.Value;
        ```

        ✖
        ``` csharp
        int x = (y + z);
        string y = (this.Method()).ToString();
        ```
        ``` csharp
        return (a + b);
        return (x.Value);
        ```

### Symbols

  * ✔ Space symbols correctly
  
    * Symbols: colons, operators (arithmetic, assignment, conditional, logical, relational, shift, lambda)
    * Symbols should always be surrounded by a single space on either side.
    * Unary operators should be preceded by a single space, but must never be followed by any space.
    * Exception: Unary operators preceded or followed by a parenthesis or bracket, when there should be no spaces.
    
        ✔
        ``` csharp
        int x = y + z;
        ```
        ``` csharp
        bool isTrue = (x == y);
        bool isTrue = (x > y);
        bool isTrue = (x < y);
        bool isTrue = (x >= y);
        bool isTrue = (x <= y);
        bool isTrue = (x != y);
        ```
        ``` csharp
        int shift = 1 << 8;
        ```
        ``` csharp
        Func<int, int, int> sum = (x, y) => x + y;
        ```
        ``` csharp
        var x = collection
            .Where(item => item.Value >= 100)
            .ToList();
        ```
        ``` csharp
        if (!value)
        if (!(expression1 && expression2))
        ```
        ``` csharp
        bool x = !expression;
        ```

        ✖
        ``` csharp
        int x = y+z;
        ```
        ``` csharp
        bool isTrue= (x == y);
        bool isTrue =(x > y);
        bool isTrue = (x< y);
        bool isTrue = (x >=y);
        bool isTrue = (x<=y);
        bool isTrue=(x!=y);
        ```
        ``` csharp
        int shift = 1<<8;
        ```
        ``` csharp
        Func<int, int, int> sum = (x, y)=>x + y;
        ```
        ``` csharp
        var x = collection
            .Where(item=>item.Value>=100)
            .ToList();
        ```
        ``` csharp
        if ( !value)
        if ( ! value)
        if (! (expression1 && expression2))
        ```
        ``` csharp
        bool x=!expression;
        bool x =! expression;
        ```

  * ✔ Space commas correctly
  
    * Commas should always be followed by a single space, unless it is the last character on the line.
    * Commas should never be preceded by any whitespace.
    
        ✔
        ``` csharp
        void Method(int x, int y, int z);
        void Method(
            int x,
            int y,
            int z);
        ```
        ``` csharp
        Method(x, y, z);
        ```

        ✖
        ``` csharp
        void Method(int x,int y,int z);
        void Method(int x ,int y ,int z);
        void Method(int x , int y , int z);
        ```
        ``` csharp
        void Method(
            int x
            ,int y
            , int z);
        ```

  * ✔ Space semicolons correctly
  
    * Semicolons should always be followed by a space, unless it is the last character on the line.
    * Semicolons should never be preceded by any whitespace.
    
        ✔
        ``` csharp
        int X { get; set; }
        ```
        ``` csharp
        string s = "semicolons";
        ```
        ``` csharp
        for (int i = 0; i < 10; ++i)
        ```

        ✖
        ``` csharp
        int X { get ; set ; }
        ```
        ``` csharp
        string s = "semicolons" ;
        ```
        ``` csharp
        for (int i = 0;i < 10;++i)
        for (int i = 0 ; i < 10 ; ++i)
        ```

  * ✔ Space colons correctly
  
    * Colons should never be the only element on a single line.
    * Colons appearing within an element declaration must always have a single space on either side, uless it's the first character on the line.
    * Colons used in a conditional statement must always contain a single space on either side, unless it's the first character on the line.
    * Colons appearing at the end of a case statement should never be preceded by a whitespace.
    * Colons appearing at the end of a case statement should always be the followed by a whitespace, or be last character on the line.
    
        ✔
        ``` csharp
        class B<T> : A
            where T : class
        {
            B(int x)
                : base(x)
            {
            }
        }
        ```
        ``` csharp
        int x = isTrue ? y : z;
        int x = isTrue
            ? y
            : z;
        ```
        ``` csharp
        switch (x)
        {
            case 1:
                y = 1;
                break;
            case 2:
                break;
            default:
                y = 100;
                break;
        }
        ```
        
        ✖
        ``` csharp
        class B<T>:A
            where T:class
        {
            B(int x):base(x)
            {
            }
        }
        ```
        ``` csharp
        int x = isTrue?x:y;
        int x = isTrue
            ?
            x
            :
            y;
        ```
        ``` csharp
        switch (x)
        {
            case 1 :
                y = 1;
                break;
            case 2: break; // Accepted, but should be avoided. Be consistent!
            default :
                y = 100;
                break;
        }
        ```

  * ✔ Space increment and decrement correctly
  
    * The should be no whitespace between the increment or decrement symbol and the item is being incremented or decremented.
    
        ✔
        ``` csharp
        int x = ++y;
        int x = y++;
        int x = --y;
        int x = y--;
        ```
        
        ✖
        ``` csharp
        int x = ++ y;
        int x = y ++;
        int x = -- y;
        int x = y --;
        ```

  * ✔ Space member access correctly
  
    * Member access symbol should never have whitespace on either side, unless it's the first character on the line.
    
        ✔
        ``` csharp
        int x = this.count;
        ```
        ``` csharp
        var x = this.tuple.Item1;
        ```
        ``` csharp
        var x = collection.Select(item => item.Id).ToList();
        ```
        ``` csharp
        var x = collection
            .Select(item => item.Id)
            .ToList();
        ```

        ✖
        ``` csharp
        int x = this. count;
        int x = this .count;
        int x = this . count;
        ```
        ``` csharp
        var x = this .tuple .Item1;
        ```
        ``` csharp
        var x = collection.
            Select(item => item.Id).
            ToList();
        ```

  * ✖ Do not space nullable type symbols
  
    * Nullable type symbol should never be preceded by whitespace, unless the symbol is the first on the line.
    
        ✔
        ``` csharp
        DateTime? date;
        ```
        ``` csharp
        DateTime? start = new DateTime(2000, 1, 1);
        DateTime? end = new DateTime(3000, 1, 1);
        var range = new { start, end };

        int startYear = range.start?.Year ?? 2000;
        int endYear = range
            .end
            ?.Year ?? 3000;
        ```

        ✖
        ``` csharp
        DateTime ? date;
        ```
        ``` csharp
        DateTime? start = new DateTime(2000, 1, 1);
        DateTime? end = new DateTime(3000, 1, 1);
        var range = new { start, end };

        var startYear = range.start ? .Year ?? 2000;
        var endYear = range
            .end?
            .Year ?? 2000;
        ```

### Signs

  * ✔ Space positive sign correctly
  
    * Positive sign should always be preceded by a single space.
    * Positive sign should never be the last character on a line.
    * Exception when it is:
      * the first character after an opening square bracket
      * the first character after an opening parenthesis
      * the first character on the line
      
        ✔
        ``` csharp
        x += y;
        ```
        ``` csharp
        int x = dictionary[+y];
        ```
        ``` csharp
        int x = Method(
            (999 / 9)
            + 10_000,
            -11);
        ```
        ``` csharp
        string s = "First" + "Middle" + "Last";
        string s = "First"
            + "Middle"
            + "Last";
        ```

        ✖
        ``` csharp
        x+= y;
        ```
        ``` csharp
        int x = dictionary[ +y ];
        ```
        ``` csharp
        int x = Method(
            (999 / 9) +
            10_000,
            -11);
        ```
        ``` csharp
        string s = "First"+"Middle"+"Last";
        string s = "First" +
            "Middle" +
            "Last";
        ```

  * ✔ Space negative sign correctly
  
    * Negative sign should always be preceded by a single space.
    * Negative sign should never be the last character on a line.
    * Exception when it is:
      * the first character after an opening square bracket
      * the first character after an opening parenthesis
      * the first character on the line
       
        ✔
        ``` csharp
        int x = -y;
        int x = -(y + z);
        ```
        ``` csharp
        x -= y;
        ```
        ``` csharp
        int x = dictionary[-y];
        ```
        ``` csharp
        int x = Method(-y, -z);
        ```
        ``` csharp
        int x = Method(
            -y, -z);
        
        int x = Method(
            -y,
            -z);
        
        int x = Method(
            (900 + 99)
            - 888,
            -77);
        ```
        
        ✖
        ``` csharp
        int x =-y;
        int x =-(y + z);
        ```
        ``` csharp
        x-= y;
        ```
        ``` csharp
        int x = dictionary[ -y ];
        ```
        ``` csharp
        int x = Method( -y, -z);
        ```
        ``` csharp
        int x = Method(
            999,
             -88,
             -7);
        
        int x = Method(
            (900 + 99) -
            888,
            -77);
        ```

### Layout

  * ✖ NEVER align code
  
    * Alignment improves readability.. for a minute, or so. In reality, alignment creates problems for future maintenance!
    * A future change that needs to touch just one line of code will leave the *formerly-pleasing* formatting **mangled**.
    * The smallest change, as a variable rename, will break your *neatly formatted code*.
    * There should be no need to modify that extra piece of code. If the case raises it will be, most likely, left behind.
    * These blocks of code can slow down reviewers and exacerbates merge conflicts.
    
        ✔
        ``` csharp
        int count; // Allowed comment
        string name; // Allowed comment
        ```
        ``` csharp
        // Allowed!
        if (expression1
            && expression2)
        ```
        
        ✖
        ``` csharp
        int count;   // Alligned
        string name; // comments

        int activeItems;   // Will no longer
        string name; // be aligned after future edits
        ```
        ``` csharp
        public  int     count;
        private string  name;

        private readonly  int     count;
        private string  name;

        public  int     count;
        protected DateTime releaseDate;
        private string  name;
        ```
        ``` csharp
        void Method(int argument1,
                    int argument2);
        void MethodRename(int argument1,
                    int argument2);
        ```
        ``` csharp
        var x = collection
            .Where(i => i.Date.Year > 2000
                        && i.Owner == User)
            .ToList();
        var x = collection
            .Where(currentItem => currentItem.Date.Year > 2000
                        && currentItem.Owner == User)
            .ToList();
        ```

  * ✔ Separate elements by a blank line
  
    * Add a blank line between adjacent elements.
    
        ✔
        ``` csharp
        Constructor()
        {
        }

        void Method1()
        {
        }

        void Method2()
        {
        }
        ```

        ✖
        ``` csharp
        Constructor()
        {
        }
        void Method1()
        {
        }
        void Method2()
        {
        }
        ```

  * ✖ Do not use multiple blank lines in a row
  
    * To improve code readability, blank lines are required in certain situations, but are prohibited in others.
    * This results in a consistend visual pattern and can improve recognition of unfamiliar code.
    * Use a single blank line to separate logic blocks in methods, or file sections.
    
        ✔
        ``` csharp
        class Application
        {
            int x;
            
            bool Method()
            {
                var one = MethodOne();
                var two = MethodTwo();
                
                return one != two;
            }
        }
        ```

        ✖
        ``` csharp
        class Application
        {
            int x;
            
            
            bool Method()
            {
                var one = MethodOne();
                var two = MethodTwo();
                
                
                return one != two;
            }
        }
        ```

  * ✖ Do not leave blank lines at start or end of a file
  
    * Files should not start with one, or more blank lines.
    * Files should not end with multiple blank lines.
    
        ✔
        ``` csharp
        using System;

        namespace Program
        {
        }
        ```

        ✖
        ``` csharp
         
        using System;

        namespace Program
        {
        }
         
         
        ```

### Parameters

  * ✔ Split parameter list correctly
  
    * Parameters must be placed all on one line, or each on a separate line.
    
        ✔
        ``` csharp
        void Method(int x, int y, int z)
        ```
        ``` csharp
        void Method(
            int x, int y, int z)
        ```
        ``` csharp
        void Method(
            int x,
            int y,
            int z)
        ```

        ✖
        ``` csharp
        void Method(int x, int y,
            int z)
        ```
        ``` csharp
        void Method(
            int x,
            int y, int z)
        ```

  * ✔ Parameter list must follow declaration
  
    * The start of the parameter list of a method or indexer must begin on same line or next line of the opening parenthesis.
    
        ✔
        ``` csharp
        void Method(int x, int y, int z)
        ```
        ``` csharp
        void Method(
            int x, int y, int z)
        ```
        ``` csharp
        void Method(
            int x,
            int y,
            int z)
        ```

        ✖
        ``` csharp
        void Method(int x, int y,
            
            int z)
        ```
        ``` csharp
        void Method(

            int x, int y, int z)
        ```
        ``` csharp
        void Method(

            int x,
            int y,
            int z)
        ```

  * ✔ Parameters must follow comma
  
    * Parameters must be written on same, or next line as previous parameter.
    
        ✔
        ``` csharp
        void Method(
            int x,
            int y,
            int z)
        ```
        
        ✖
        ``` csharp
        void Method(
            int x,

            int y,

            int z)
        ```

  * ✔ Ensure comma is on same line as previous parameter
  
    ✔
    ``` csharp
    Method(
        x,
        y,
        z);
    ```

    ✖
    ``` csharp
    Method(
        x
        , y
        ,z);
    ```

  * ✖ Do not span one parameter on multiple lines
  
    * Ensure parameters do not span multiple lines.
    * This ensures method calls don't become excessively complicated, or unreadable.
    * Exceptions:
      * **The first** parameter is allowed to span across multiple lines.
      * **Anonymous methods** passed as parameter is always allowed to span multiple lines.
      
        ✔
        ``` csharp
        return JoinStrings(
            "a very long string.."
            + "concatenated with another very long string...",
            "second parameter goes here");
        ```
        ``` csharp
        return JoinStrings(
            "x",
            "y" + "z");
        ```

        ✖
        ``` csharp
        return JoinStrings(
            "x",
            "y"
            + "z");
        ```

### Misc

  * ✔ Space keywords correctly

    ✔
    ``` csharp
    if (...)
    while (...)
    for (...)
    switch (...)
    ```
    ``` csharp
    return -1;
    ```
    ``` csharp
    throw new Exception("...");
    ```
    ``` csharp
    var integers = new[] { 1, 2, 3 };
    ```

    ✖
    ``` csharp
    if(...)
    while(...)
    for(...)
    switch(...)
    ```
    ``` csharp
    return-1;
    ```
    ``` csharp
    var integers = new [] { 1, 2, 3 };
    ```
    
    | Keyword     | Followed by space |
    |:------------|:------------------|
    | catch       | Yes               |
    | fixed       | Yes               |
    | for         | Yes               |
    | foreach     | Yes               |
    | from        | Yes               |
    | group       | Yes               |
    | if          | Yes               |
    | in          | Yes               |
    | into        | Yes               |
    | join        | Yes               |
    | let         | Yes               |
    | lock        | Yes               |
    | orderby     | Yes               |
    | return      | Yes               |
    | select      | Yes               |
    | stackalloc  | Yes               |
    | switch      | Yes               |
    | throw       | Yes               |
    | using       | Yes               |
    | where       | Yes               |
    | while       | Yes               |
    | yield       | Yes               |
    | checked     | No                |
    | default     | No                |
    | sizeof      | No                |
    | typeof      | No                |
    | unchecked   | No                |
    | new (ctor)  | Yes               |
    | new (array) | No                |  


  * ✔ Space attributes correctly
  
    * Opening attribute brackets should never be followed by whitespace.
    * Closing attribute brackets should never be preceded by whitespace.
    
        ✔
        ``` csharp
        [Attribute]
        void Method()
        ```
        ``` csharp
        [Attribute1]
        [Attribute2]
        void Method()
        ```
        ``` csharp
        [Attribute1, Attribute2]
        void Method()
        ```

        ✖
        ``` csharp
        [ Attribute1]
        [Attribute2 ]
        [ Attribute3 ]
        void Method()
        ```
        ``` csharp
        [ Attribute1, Attribute2 ]
        void Method()
        ```

  * ✔ Space operator keyword correctly
  
    * The *operator* keyword should always be preceded and followed by a single space.
    
        ✔
        ``` csharp
        Space operator +(Space space1, Space space2)
        ```

        ✖
        ``` csharp
        Space operator+(Space space1, Space space2)
        ```

  * ✖ Do not precede preprocessor keywords by space
  
    * Preprocessor directives should not be preceded by space(s).
    
        ✔
        ``` csharp
        #if debug
        #endif
        ```
        
        ✖
        ``` csharp
        #  if debug
        # endif
        ```

## Types and variables

  * ✖ Do not use underscores in identifiers
  
    * [c-sharpcorner.com article](https://www.c-sharpcorner.com/article/stop-use-var-everywhere-and-think-before-use-underscore-with-private-variable-in/)
    * **Discards**, introduced in C# 7.0, are the only exception.
    
        ✔
        ``` csharp
        private int x;
        ```
        ``` csharp
        private readonly IDependencyInjection dependencyInjection;
        ```
        ``` csharp
        var x = list1
            .Join(list2, l1 => l1.Id, l2 => l2.Id, (l1, _) => l1)
            .ToList();
        ```
        ``` csharp
        services.AddScope<ISignature>(_ => new Implementation(99));
        ```

        ✖
        ``` csharp
        private int m_x;
        private int _x;
        ```
        ``` csharp
        private readonly IDependencyInjection _dependencyInjection;
        ```

  * ✔ Fields must be private
  
    * For mentainability reasons, properties should always be used as the mechanism for exposing fields outside of a class.
    * This allows the internal implementation of the property to change over time without changing the interface of the class.
    * Exception: fields within structs are allowed to have any access level.
    
        ✔
        ``` csharp
        private int count;

        public int Count
        {
            get => this.count;
            set => this.count = value;
        }
        ```

        ✖
        ``` csharp
        public int count;
        ```

  * ✔ Use built-in type alias

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
  
    * Use predefined type names, instead of system type names.
    * Do not use basic types.
    * Do not use full namespace for types.

        ✔
        ``` csharp
        int index;
        bool isTrue;
        object obj;
        string name;
        ```

        ✖
        ``` csharp
        Int32 index;
        Boolean isTrue;
        Object obj;
        String name;
        ```

  * ✔ Use shorthand for nullable types
  
    * Define nullable types using the C# shorthand/predefined types.
    
        ✔
        ``` csharp
        int? count;
        DateTime? date;
        ```

        ✖
        ``` csharp
        Nullable<int> count;
        Nullable<DateTime> date;
        ```

  * ✖ Do not use Hungarian notation, or type identification in identifiers
  
    ✔
    ``` csharp
    int age;
    string address;
    DateTime dateOfBirth;
    List<Person> persons;
    ```

    ✖
    ``` csharp
    int iAge;
    string strAddress;
    List<Person> personList;
    ```

  * ✖ Do not use abbreviations
  
    * Exceptions:
      * common names and notations: Id, Url, Ftp, Xml, Http, etc..
      * *for* statement initializer(s)
    
        ✔
        ``` csharp
        IConfiguration configuration;
        DateTimeOffset dateTimeOffset;
        CancellationToken cancellationToken;
        string name;
        ```
        ``` csharp
        UserId userId;
        XmlDocument xmlDocument;
        HtmlHelper htmlHelper;
        ```

        ✖
        ``` csharp
        IConfiguration cfg;
        DateTimeOffset offset;
        CancellationToken ct;
        string s;
        ```

## Expressions

  * ✔ Conditional expressions must declare precedence
  
    * C# mentains a hierarchy of precedence for conditional operators.
    * It is allowed to string multiple operations together on one statement and the compiler will automatically set the order based on pre-established rules.
    * In order to achieve full understanding of the code, the developer mustt know and understand the basic operator precedente rules in C#.
    * To increase readability and maintainability and reduce the risk of introducing bugs later, it is recommended to insert parenthesis to explicitly declare the operator precedence.
    * Inserting parenthesis makes the code more obvious and easy to understand, and removes the need for the reader to make assumptions about the code.
    
        ✔
        ``` csharp
        if (x || (y && z && a) || b)
        ```
        ``` csharp
        return a || (b && c);
        return a || b;
        ```

        ✖
        ``` csharp
        if (x || y && z && a || b)
        ```
        ``` csharp
        return a || b && c;
        return (a || b);
        ```

  * ✔ Arithmetic expressions must declare precedence
  
    * C# mentains a hierarchy of precedence for arithmetic operators.
    * It is allowed to string multiple operations together on one statement and the compiler will automatically set the order based on pre-established rules.
    * In order to achieve full understanding of the code, the developer mustt know and understand the basic operator precedente rules in C#.
    * To increase readability and maintainability and reduce the risk of introducing bugs later, it is recommended to insert parenthesis to explicitly declare the operator precedence.
    * Inserting parenthesis makes the code more obvious and easy to understand, and removes the need for the reader to make assumptions about the code.
    
        ✔
        ``` csharp
        int x = 1 + ((10 % y) * a) / b) - 2;
        ```

        ✖
        ``` csharp
        int x = 1 + 10 % y * a / b - 2;
        ```

  * ✖ Do not use empty strings
  
    ✔
    ``` csharp
    string s = string.Empty;
    ```

    ✖
    ``` csharp
    string s = "";
    ```

## Statements

  * ✔ Write statements on a single line
  
    * Do not write multiple statements on the same line.
    * Do not write statements and curly brackets on the same line.
    
        ✔
        ``` csharp
        int Method()
        {
            int x = 1;
            int y = 2;
            
            return x + y;
        }
        ```

        ✖
        ``` csharp
        int Method()
        {
            int x = 1; int y = 2;
            
            return x + y;
        }
        ```
        ``` csharp
        int Method() { int x = 1; int y = 2; return x + y; }
        ```

  * ✖ Do not write multiple statements on one line
  
    * Each statement must begin on a new line.
    
        ✔
        ``` csharp
        int Method(int x, int x)
        {
            int sum = x + y;
            return sum;
        }
        ```
        ``` csharp
        int a;
        int b;
        string firstName;
        string lastName;
        ```

        ✖
        ``` csharp
        int Method(int x, int x)
        {
            int sum = x + y; return sum;
        }
        ```
        ``` csharp
        int a, b;
        string firstName, lastName;
        ```

  * ✖ Do not write empty statements
  
    * Remove unneeded semicolon(s) from code.
    * Syntactically, this results in an extra, empty, statement in the code.
    
        ✔
        ``` csharp
        int x = y;
        ```

        ✖
        ``` csharp
        int x = y;;
        int y = y; ;
        ```

  * ✔ Chain statement blocks without blank lines
  
    * Some types of C# statements can only be used when chained to the bottom of another statement.
    * Remove any blank lines between chained statements.

        ✔
        ``` csharp
        try
        {   
        }
        catch
        {
        }
        finally
        {
        }
        ```
        ``` csharp
        if (...)
        {
        }
        else
        {
        }
        ```

        ✖
        ``` csharp
        try
        {
        }

        catch
        {
        }

        finally
        {
        }
        ```
        ``` csharp
        if (...)
        {
        }

        else
        {
        }
        ```

  * ✔ Comment fall-through cases
  
    * Within a switch block, each statement can be terminated abruptly by break, continue, return, or throw keywords.
    * To mark statements with same result it is recommended, but not mandatory, to use an expressive comment.
    * Usually "**// fall through**" is enough.
    
        ✔
        ``` csharp
        switch (x)
        {
            case 1:
                // fall through
            case 2:
                HandleOneAndTwo();
                break;
            case 3:
                HandleThree();
                break
            default:
                HandleDefault();
                break;
        }
        ```
        ``` csharp
        switch (ch)
        {
            case 'a':
            case 'e':
            case 'i':
            case 'o':
            case 'u':
            case 'A':
            case 'E':
            case 'I':
            case 'O':
            case 'U':
                HandleVowel();
                break;
            default:
                HandleConsonant();
                break;
        }
        ```
        
        ✖
        ``` csharp
        switch (ch)
        {
            case 'a':
                // fall through
            case 'e':
                // fall through
            case 'i':
                // fall through
            case 'o':
                // fall through
            case 'u':
                // fall through
            case 'A':
                // fall through
            case 'E':
                // fall through
            case 'I':
                // fall through
            case 'O':
                // fall through
            case 'U':
                HandleVowel();
                break;
            default:
                HandleConsonant()
                break;
        }
        ```

## Queries and Linq