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
This C# style recommends best practices so that other C# developers can write code maintainable by other C# developers.
The document contains data collected from various sources, language styles, and communities.  

  - [docs.microsoft.com](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/)
  - [dofactory.com](https://www.dofactory.com/reference/csharp-coding-standards)
  - [github.com/ktaranov](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md)
  - [c-sharpcorner.com](https://www.c-sharpcorner.com/article/stop-use-var-everywhere-and-think-before-use-underscore-with-private-variable-in/)
  - [stylecop.soyuz5.com](http://stylecop.soyuz5.com/StyleCop%20Rules.html)
  - [google.github.io](https://google.github.io/styleguide/javaguide.html)

## Table of contents

* [General](#general)
* [Structure and layout](#structure-and-layout)
* [Readability](#readability)
* [Spacing](#spacing)
* [Types and variables](#types-and-variables)
* Expressions
* Statements
* Classes and objects
* Structs (work in progress)
* Interfaces (work in progress)
* Enums (work in progress)
* System.Linq (work in progress)

## General

  * ✔ Vertically align curly brackets
  
    * **Allman** style. [Wikipedia](https://en.wikipedia.org/wiki/Indentation_style)
    
        ``` csharp
        namespace Application
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

  * ✔ Use *TODO** comments to mark work in progress, missing features or functionality
  
    * In Visual Studio todos are found in **Task List** window (*Ctrl + \\, T*).
    
        ✔ 
        ``` csharp
        public void Method(int x)
        {
            // TODO: Validate input
            
            for (int i = 0; i < x; ++i)
            {
                // ...
            }
            
            // TODO: Log
        }
        ```
        
        ✖ 
        ``` csharp
        //TODO ...
        //TO DO ...
        // TO DO : ...
        ```
        
  * ✖ NEVER align code
  
    * Alignment can aid readability.. for a minute, or so. In reality.. alignment creates problems for future maintenance!
    * A future change that needs to touch just one line of code will leave the formerly-pleasing formatting mangled.
    * The smallest change, like a variable rename will break your 'neatly formatted code'.
    * There should be no need to modify that extra piece of code and if it is, most likely will be left behind.
    * These block of code can slow down reviewers and exacerbates merge conflicts.
    
        ✔
        ``` csharp
        public int count; // Allowed comment
        private string name; // Allowed comment
        ```
        ``` csharp
        // Allowed!
        if (expression1
            && expression2
            && expression3)
        {
        }
        ```
        
        ✖
        ``` csharp
        public int count;    // Alligned
        private string name; // comments

        public int activeItems;    // Will no longer
        private string name; // be aligned after future edits
        ```
        ``` csharp
        public  int     count;
        private string  name;

        // Change access modifier
        private readonly  int     count;
        private string  name;

        // Add new field
        public  int     count;
        protected DateTime releaseDate;
        private string  name;
        ```
        ``` csharp
        public void Method(int parameter1,
                           int parameter2,
                           int parameter3;
        public void MethodAfterRename(int parameter1,
                           int parameter2,
                           int parameter3);
        ```
        ``` csharp
        var items = collection
            .Where(i => i.Date.Year > 2000
                        && i.Owner == User)
            .ToList();

        // Parameter rename leaves code unorganized and needs extra time to be fixed.
        var items = collection
            .Where(currentItem => currentItem.Date.Year > 2000
                        && currentItem.Owner == User)
            .ToList();
        ```

## Structure and layout

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
        if (true)
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
        if (true)
        {
        }

        else
        {
        }
        ```
        
  * ✔ Follow closing curly brackets by a blank line
  
    * Ensure a blank line follows closing curly brackets.  
    
        ✔
        ``` csharp
        public bool Enabled
        {
            get
            {
                return this.enabled;
            }
        }
        ```

        ✖
        ``` csharp
        public bool Enabled
        {
            get
            {
                return this.enabled;
            }}
        ```
        
  * ✔ Organize namespaces with a clearly defined structure
  
    * Use PascalCasing.
    
        ``` csharp
        namespace Company.Product.Module.SubModule;
        namespace Product.Module.Component;
        namespace Product.Layer.Module.Group;
        ```
        
  * ✔ Precede documentation elements with a blank line
  
    ✔
    ``` csharp
    bool FirstProperty { get; set; }

    /// <summary>
    /// ...
    /// </summary>
    bool SecondProperty { get; set; }
    ```

    ✖
    ``` csharp
    bool FirstProperty { get; set; }
    /// <summary>
    /// ...
    /// </summary>
    bool SecondProperty { get; set; }
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
        
  * ✔ Separate non-static from static usings
  
    * Separate non-static from static usings.
    * Order usings alphabetically. First non-static, then static.
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
        
  * ✔ Use proper order of items inside a class
  
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
      * private
    * Within each access groups, order by static, then non-static:
      * static
      * non-static
    * Then, order by readonly, then non-readonly:
      * readonly
      * non-readonly  
      
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

  * ✔ Write all accessors single-line or multi-line
  
    * Write each accessor on a single line if the accessors are short.
    * Expand both accessors across multiple lines if the accessors are longer.
    
        ✔
        ``` csharp
        bool Enabled { get; set; }
        ```
        ``` csharp
        bool Enabled
        {
            get { return this.enabled; }
            set { this.enabled = value; }
        }
        ```
        ``` csharp
        bool Enabled
        {
            get => this.enabled;
            set => this.enabled = value;
        }
        ```
        ``` csharp
        bool Enabled
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
        bool Enabled
        {
            get;
            set;
        }
        ```
        ``` csharp
        bool Enabled
        {
            get { return this.enabled; }
            set
            {
                this.enabled = value;
            }
        }
        ```
        ``` csharp
        bool Enabled
        {
            get => this.enabled;
            set
            {
                this.enabled = value;
            }
        }
        ```
        
  * ✔ Write single line comments with proper follow and precede elements
  
    * Single line comments should always be preceded by a blank line.
    * Single line comments should never be followed by (a) blank line(s).
    
        ✔
        ``` csharp
        bool Enabled
        {
            get
            {
                // This comment is valid
                return this.enabled;  
            }
        }
        ```

        ✖
        ``` csharp
        bool Enabled
        {
            get
            {
                // This comment is not valid
                
                return this.enabled;  
            }
        }
        ```
        ``` csharp
        bool Enabled
        {
            get
            {
            
                // This comment is not valid
                return this.enabled;  
            }
        }
        ```
        ``` csharp
        bool Enabled
        {
            get
            {
            
                // This comment is not valid
                
                return this.enabled;  
            }
        }
        ```
        ``` csharp
        bool Enabled
        {
            get
            {
                // This is a sample comment which doesn't really say anything.
                // This is another part of the comment. Both are not valid!
            
                // This comment is valid
                return this.enabled;  
            }
        }
        ```
        
  * ✔ Write statements on a single line
  
    * Do not write multiple statements on the same line.
    * Do not write statements and curly brackets on the same line.
    
        ✔
        ``` csharp
        int Method()
        {
            int a = 1;
            int b = 2;
            
            return a + b;
        }
        ```

        ✖
        ``` csharp
        int Method()
        {
            int a = 1; int b = 2;
            
            return a + b;
        }
        ```
        ``` csharp
        int Method()
        {
            int a = 1;
            int b = 2;
            return a + b; }
        ```
        ``` csharp
        int Method() { int a = 1; int b = 2; return a + b; }
        ```
        
  * ✖ Do not follow documentation elements with a blank line
  
    * Documentation elements should always be followed by blocks of code.
    
        ✔
        ``` csharp
        /// <summary>
        /// ...
        /// </summary>
        bool IsEnabled { get; set; }
        ```

        ✖
        ``` csharp
        /// <summary>
        /// ...
        /// </summary>
        
        bool IsEnabled { get; set; }
        ```
        
  * ✖ Do not follow or precede closing curly brackets with a blank line
  
    * Closing curly brackets should always be preceded by statements, not blank line(s).
    * Closing curly brackets should never be followed by blank line(s).
    
        ✔
        ``` csharp
        bool IsEnabled
        {
            get
            {
                return this.enabled;
            }
        }
        ```

        ✖
        ``` csharp
        bool IsEnabled
        {
            get
            {
                return this.enabled;
                
            }
        }
        ```
        ``` csharp
        bool IsEnabled
        {
            get
            {
                return this.enabled;
            }
            
        }
        ```
        ``` csharp
        bool IsEnabled
        {
            get
            {
                return this.enabled;
                
            }
            
        }
        ```
        
  * ✖ Do not follow or precede opening curly brackets with a blank line
  
    * Opening curly brackets should always be followed by statements, not blank line(s).
    * Opening curly brackets should never be preceded by blank line(s).
    
        ✔
        ``` csharp
        bool IsEnabled
        {
            get
            {
                return this.enabled;
            }
        }
        ```

        ✖
        ``` csharp
        bool IsEnabled
        {
            get
            {
            
                return this.enabled;
            }
        }
        ```
        ``` csharp
        bool IsEnabled
        {
            get
            
            {
                return this.enabled;
            }
        }
        ```
        ``` csharp
        bool IsEnabled
        {
            get
            
            {
            
                return this.enabled;
            }
        }
        ```
        
  * ✖ Do not leave blank lines at start or end of a file
  
    * Files should not start with one, or more blank lines.
    * Files should not end with multiple blank lines.
    
        ✔
        ``` csharp
        using System

        namespace Program
        {
            class Application
            {
            }
        }
        ```

        ✖
        ``` csharp
        
        using System

        namespace Program
        {
            class Application
            {
            }
        }
        
        
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
        
  * ✖ Do not omit curly brackets
  
    * Always wrap the body of the statement in curly brackets.
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
    * Curly brackets should not share the line with any other code, other than comments.
    
        ✔
        ``` csharp
        void Method()
        {
            lock (this)
            {
                return this.value;
            }
        }
        ```

        ✖
        ``` csharp
        void Method()
        {
            lock (this) {
                return this.value;
            }
        }
        ```
        ``` csharp
        void Method()
        {
            lock (this) { return this.value; }
        }
        ```
        
  * ✖ Do not place multiple namespaces within a single file
  
    * Ensure that each file contains only one namespace.
    * To increase long-term mentainability of the code-base, each file should contain at most one namespace.
    
        ✔
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

        ✖
        ``` csharp
        // ClassOneAndTwo.cs
        namespace Project
        {
            class ClassOne
            {
            }
        }
        
        namespace Project
        {
            class ClassTwo
            {
            }
        }
        ```

  * ✖ Do not use multiple blank lines in a row
  
    * To improve code readability, blank lines are required in certain situations, but are prohibited in others.
    * This results in a consistend visual pattern and can improve recognition of unfamiliar code.
    * Use a single blank line to separate logic blocks in methods, or file sections.
    
        ✔
        ``` csharp
        using System;
        using System.Threading.Tasks;
        
        namespace Project
        {
            public class Application
            {
                private int count;
            
                public Application()
                {
                }
            
                bool IsEnabled { get; set; }
            
                void Method()
                {
                }
            }
        }
        ```

        ✖
        ``` csharp
        using System;
        
        using System.Threading.Tasks;

        namespace Project
        {
            public class Application
            {
                private int count;
                public Application()
                {
                }
                
                bool IsEnabled { get; set; }
                
                
                void Method()
                {
                }
                
            }
        }
        ```
        
  * ✖ Do not wrap elements in opening and closing curly brackets
  
    * Write elements so they expand across multiple lines.
    * Exception: Accessors within properties, events, or indexers.
    
        ✔
        ``` csharp
        int Count { get; set; }
        ```
        ``` csharp
        void Method()
        {
            return;
        }
        ```

        ✖
        ``` csharp
        void Method() { return; }
        ```
        ``` csharp
        void Method()
            { return; }
        ```

## Readability

  * ✔ Close parenthesis on line with last parameter
  
    * The closing parenthesis in a call to a method must be placed on same line as the last parameter.
    * The closing parenthesis in a call to an indexer must be placed on same line as the last parameter.
    * The closing parenthesis in a method declaration must be placed on same line as the last parameter.
    * The closing parenthesis in an indexer declaration must be placed on same line as the last parameter.
    
        ✔
        ``` csharp
        bool Method(int x)
        ```
        ``` csharp
        bool isValid = Method(100);
        ```
        ``` csharp
        int x = array[0];
        ```
        ``` csharp
        int this[int x]
        {
            get { return array[x]; }
        }
        ```

        ✖
        ``` csharp
        bool isValid = Method(
            100
            );
        ```
        ``` csharp
        int x = array[
            0
            ];
        ```

  * ✔ Ensure comma is on same line as previous parameter
  
    * Always write commas on same line as previous parameter.
    
        ✔
        ``` csharp
        string name = Method(
            first,
            second,
            last);
        ```
        ``` csharp
        int this[
            int x,
            int y]
        ```

        ✖
        ``` csharp
        string name = Method(
            first
            , second
            ,last);
        ```

  * ✔ Open parenthesis on declaration line
  
    * The opening parenthesis in a call to a method must be placed on same line as the method.
    * The opening parenthesis in a call to an indexer must be placed on same line as the indexer name.
    * The opening parenthesis in a method declaration must be placed on same line as the method.
    * The opening parenthesis in an indexer declaration must be placed on same line as the indexer name.
    
        ✔
        ``` csharp
        bool Method(int x)
        ```
        ``` csharp
        bool isValid = Method(100);
        ```
        ``` csharp
        int x = array[0];
        ```
        ``` csharp
        int this[int x]
        {
            get { return array[x]; }
        }
        ```

        ✖
        ``` csharp
        bool Method
            (int x)
        ```
        ``` csharp
        bool isValid = Method
            (100);
        ```
        ``` csharp
        int x = array
        [0];
        ```
        ``` csharp
        int this
            [int x]
        {
            get { return array[x]; }
        }
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
        void Method(
            int x,

            int y,

            int z)
        ```

  * ✔ Prefix local calls with this
  
    * Insert the this prefix before a call to a class member.
    
        ✔
        ``` csharp
        class A : B
        {
            private string id;
            private double grade;
            
            A(string id, double grade, int age)
            {
                base.age = age;
                this.id = id;
                this.grade = grade;
            }
        }
        ```

        ✖
        ``` csharp
        class A : B
        {
            private string m_id;
            private double _grade;
            
            A(string id, double grade, int age)
            {
                base.age = age;
                m_id = id;
                _grade = grade;
            }
        }
        ```

  * ✔ Query clause must follow previous clause
  
    * Query clause must begin on the same line as previous clause, or on the next line.
    
        ✔
        ``` csharp
        var x = select a in b from c;
        var x =
            select a
            in b
            from c;
        ```

        ✖
        ``` csharp
        var x = select a in b
            from c;
        var x = select a in b
                from c;
        ```
        ``` csharp
        var x = select a
                in b
                from c;
        var x = select a in b
                         from c;
        ```

  * ✔ Split parameter list appropriately
  
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
        void Method(int x,
            int y, int z)
        void Method(int x, int y,
            int z)
        ```
        ``` csharp
        void Method(
            int x,
            int y, int z)
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
  
    * Use built-in alias for types.
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

  * ✔ Write all query clauses on separate lines, or all on one line
  
    * Query expressions should be placed on separate lines.
    * Exception: Short queries can be written on same line.
    
        ✔
        ``` csharp
        var x = select a in b from c;
        ``` csharp
        ```
        var x = collection.Where(item => item.Date.Year.Equals(currentYear)).ToList();
        ```
        ``` csharp
        var x = collection
            .Where(item => item.Date.Year.Equals(currentYear))
            .ToList();
        ```

        ✖
        ``` csharp
        var x = collection
            .Where(item => item.Date.Year.Equals(currentYear)).ToList();
        var x = collection.Where(item => item.Date.Year.Equals(currentYear))
            .ToList();
        var x = collection.Where(item => item.Date.Year.Equals(currentYear))
                          .ToList();
        ```
        ``` csharp
        var x = select a
            in b from c;
        ```

  * ✔ Write query clauses on multiple lines when previous clause spans multiple lines
  
    * Write ALL clauses on new lines when one clause spans multiple lines.
    
        ✔
        ``` csharp
        var x = collection
            .Where(item => start >= item.StartDate && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name })
            .ToList();
        ```
        ``` csharp
        var x = collection
            .Where(item =>
                start >= item.StartDate
                && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name })
            .ToList();
        ```
        ``` csharp
        var x =
            select a
            in b.Method(
                2, “x”)
            from c;
        ```

        ✖
        ``` csharp
        var x = collection
            .Where(item => start >= item.StartDate && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name }).ToList();
        ```
        ``` csharp
        var x = collection.Where(item =>
                start >= item.StartDate
                && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name })
            .ToList();
        ```
        ``` csharp
        var x =
            select a
            in b.Method(
                2, “x”) from c;
        ```

  * ✔ Write query clauses on own line when spanning multiple lines
  
    * Query clauses must be written on own line when spanning multiple lines.
    
        ✔
        ``` csharp
        var x = collection
            .Where(item => start >= item.StartDate && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name })
            .ToList();
        ```
        ``` csharp
        var x = collection
            .Where(item =>
                start >= item.StartDate
                && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name })
            .ToList();
        ```
        ``` csharp
        var x = collection
            .Where(item => start >= item.StartDate && end <= item.EndDate)
            .Select(item =>
                new
                {
                    Id = item.Id,
                    Name = item.Name
                })
            .ToList();
        ```
        ``` csharp
        var x = collection
            .Where(item =>
                start >= item.StartDate
                && end <= item.EndDate)
            .Select(item =>
                new
                {
                    Id = item.Id,
                    Name = item.Name
                })
            .ToList();
        ```
        ``` csharp
        var x =
            select a
            in b
            from c.Method(
                2, “x”);
        ```

        ✖
        ``` csharp
        var x = collection.Where(item =>
                start >= item.StartDate
                && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name })
            .ToList();
        ```
        ``` csharp
        var x = collection.Select(item =>
                new
                {
                    Id = item.Id,
                    Name = item.Name
                })
            .ToList();
        ```
        ``` csharp
        var x =
            select a
            in b from c.Method(
                2, “x”);
        ```

  * ✖ Do not add empty comments
  
    * Comments should always contain text.
    
        ✔
        ``` csharp
        // This is a valid comment
        int index = 100;
        ```

        ✖
        ``` csharp
        //
        int index = 100;
        ```

  * ✖ Do not place regions within elements
  
    * Code should not contain region(s) within the body of a code statement.
    
        ✔
        ``` csharp
        #region
        public void Method()
        {
            // ...
        }
        #endregion
        ```

        ✖
        ``` csharp
        public void Method()
        {
            #region
            // ...
            #endregion
        }
        ```

  * ✖ Do not prefix calls with base unless local implementation exists
  
    * A call to a member from an inherited class must begin with base only when local class contains an override or implementation.
    
        ✔
        ``` csharp
        public virtual string JoinName(string first, string last)
        {
            return $“BASE: {first} {last}”;
        }

        public override string JoinName(string first, string last)
        {
            return $THIS: {first} {last}”;
        }

        string thisName = this.Join("", "");
        string baseName = base.Join("", "");
        ```

        ✖
        ``` csharp
        public virtual string JoinName(string first, string last)
        {
            return $“BASE: {first} {last}”;
        }

        string name = base.Join("", "");
        ```

  * ✖ Do not span one parameter on multiple lines
  
    * Ensure parameters do not span multiple lines.
    * This ensures method calls don't become excessively complicated, or unreadable.
    * Exceptions:
      * THE FIRST parameter is allowed to span across multiple lines.
      * ANONYMOUS METHOD passed as parameter is always allowed to span multiple lines.
    
        ✔
        ``` csharp
        return JoinStrings(
            "a very long string.."
            + "concatenated with another very long string...",
            "second parameter goes here");
        ```
        ``` csharp
        return JoinStrings(
            "a",
            "b" + "c");
        ```

        ✖
        ``` csharp
        return JoinStrings(
            "a",
            "b"
            + "c");
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

  * ✖ Do not use regions
  
    * "Try" to avoid using regions.
    * In many editors, including Visual Studio, the region will appear collapsed by default, hiding the code within the region.
    * It is generally a bad practice to hide code, as this can lead to bad decisions as the code is maintained over time.
    
        ✔
        ```
        (Ctrl + M, O) - Collapse to definitions
        (Ctrl + M, L) - Toggle all outlining
        ```

  * ✖ Do not write embedded comments
  
    * Do not write comments between declaration of statement and opening curly brackets.
    * Place comments above statements, or within statement body.
    
        ✔
        ``` csharp
        // Check equality
        if (x == y)
        {
        }
        ```

        ✖
        ``` csharp
        if (x == y) // Check equality
        {
        }
        ```
        ``` csharp
        if (x == y)
        // Check equality
        {
        }
        ```

  * ✖ Do not write embedded regions
  
    * Do not write regions between declaration of statement and opening curly brackets.
    * Place regions outside statement body.
    
        ✔
        ``` csharp
        #region Verify condition..
        if (true)
        {
        }
        #endregion
        ```

        ✖
        ``` csharp
        if (true)
        #region
        {
        }
        #endregion
        ```
        ``` csharp
        if (true)
        #region
        {
        #endregion
        }

        ```

  * ✖ Do not write empty statements
  
    * Remove unneeded semicolon(s) from code.
    * Syntactically, this results in an extra, empty, statement in the code.
    
        ✔
        ``` csharp
        int counter = 10;
        ```

        ✖
        ``` csharp
        int counter = 10;;
        int counter = 10; ;
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

## Spacing

  * ✔ Documentation header must begin with a single space
  
    * Header lines should begin with a single space after the three leading forward slashes.
    
        ✔
        ``` csharp
        /// <summary>
        /// ...
        /// </summary>
        /// <param name="x">...</param>
        /// <param name="y">...</param>
        void Method(int x, int y)
        ```

        ✖
        ``` csharp
        ///<summary>
        ///...
        ///</summary>
        /// <param name="x">...</param>
        /// <param name="y">...</param>
        void Method(int x, int y)
        ```

  * ✔ Single-line comments must begin with a single space
  
    ✔
    ``` csharp
    // Single-line comment
    ```

    ✖
    ``` csharp
    //Single-line comment
    //  Single-line comment
    ```

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

  * ✔ Space colon symbol *:* correctly
  
    * Colon should never be the only element on a single line.
    * Colon appearing within an element declaration must always have a single space on either side, uless it's the first character on the line.
    * Colon used in a conditional statement must always contain a single space on either side, unless it's the first character on the line.
    * Colon appearing at the end of a case statement should never be preceded by a whitespace.
    * Colon appearing at the end of a case statement should always be the followed by a whitespace, or be last character on the line.
    
        ✔
        ``` csharp
        class B<T> : A
            where T : class
        {
            B(int x) : base(x)
            {
            }
        }
        ```
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
        int x = isTrue ? 10 : 100;
        int x = isTrue
            ? 10
            : 100;
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
        class B<T>:A
            where T:class
        {
            B(int x)
                :base(x)
            {
            }
        }
        ```
        ``` csharp
        int x = isTrue?10:100;
        int x = isTrue
            ?10
            :100;
        int x = isTrue
            ? 10 : 100;
        int x = isTrue
            ?
            10
            :
            100;
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

  * ✔ Space commas correctly
  
    * Commas should always be followed by a single space, unless it is the last character on the line.
    * Commas should never be preceded by any whitespace.
    
        ✔
        ``` csharp
        void Method(int a, int b, int c)
        void Method(
            int a,
            int b,
            int c)
        ```
        ``` csharp
        Method(a, b, c);
        ```

        ✖
        ``` csharp
        void Method(int a,int b,int c)
        void Method(int a ,int b ,int c)
        void Method(int a , int b , int c)
        ```
        ``` csharp
        void Method(
            int a
            ,int b
            ,int c)
        void Method(
            int a
            , int b
            , int c)
        ```
        ``` csharp
        Method(a,b,c);
        ```

  * ✔ Space curly brackets correctly
  
    * Opening curly brackets should always be preceded by a single space, unless it's part of a method call.
    * Opening curly brackets should always be followed by a single space, unless it's the last character on the line.
    * Closing curly brackets should always be followed by a single space, unless it's the last character on the line, or it's followed by closing parenthesis, comma, or semicolon.
    * Closing curly brackets should always be preceded by a single space, unless it's the first character on the line.
    
        ✔
        ``` csharp
        void Method()
        {
        }
        ```
        ``` csharp
        var x = Method({ 1, 2 }, 1);
        var x = Method({ 1, 2 } + { 3, 4 }, 1);
        ```
        ``` csharp
        int[] ints = new[] { 1, 2, 3 };
        int[] ints = new[] {1, 2, 3}; // Generally accepted, but be consistent!
        ```
        ``` csharp
        var anon = new
        {
            Id = 1,
            Name = "custom"
        };
        var anon = new { Id = 1, Name = "custom" };
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
        var x = Method( { 1, 2 }, 1);
        var x = Method({ 1, 2 } , 1);
        var x = Method( { 1, 2 } + { 3, 4 } , 1);
        ```
        ``` csharp
        int[] ints = new[]{ 1, 2, 3 };
        int[] ints = new[] { 1, 2, 3 } ;
        ```
        ``` csharp
        var anon = new{ Id = 1, Name = "custom" };
        var anon = new{Id = 1, Name = "custom"};
        var anon = new
        { Id = 1, Name = "custom" };
        var anon = new
        {
            Id = 1, Name = "custom"
        };
        ```

  * ✔ Space increment and decrement symbols correctly
  
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

  * ✔ Space keywords correctly

    ✔
    ``` csharp
    if (...)
    while (...)
    for (...)
    switch (...)
    ```
    ``` csharp
    return 1;
    ```
    ``` csharp
    throw new Exception("message");
    ```
    ``` csharp
    var strings = new string[] { "x", "y" };
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
    return1;
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
    
  * ✔ Space member access symbol correctly
  
    * Member access symbol should never have whitespace on either side, unless it's the first character on the line.
    
        ✔
        ``` csharp
        int x = this.count;
        ```
        ``` csharp
        var x = this.tuplePair.Item1;
        ```
        ``` csharp
        var ids = collection.Select(item => item.Id).ToList();
        ```
        ``` csharp
        var ids = collection
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
        var x = this .tuplePair .Item1;
        ```
        ``` csharp
        var ids = collection. Select(item => item.Id). ToList();
        var ids = collection.
            Select(item => item.Id).
            ToList();
        ```

  * ✔ Space negative sign correctly
  
    * Negative sign should always be preceded by a single space.
    * Negative sign should never be the last character on a line.
     * Exceptions:
       * it's the first character after an opening square bracket
       * it's the first character after an opening parenthesis
       * it's the first character on the line
       
            ✔
            ``` csharp
            int x = -10;
            int x = -(10 + 3);
            ```
            ``` csharp
            x -= 10;
            ```
            ``` csharp
            int x = dictionary[-10];
            ```
            ``` csharp
            int x = Method(-10, -3);
            ```
            ``` csharp
            int x = Method(
                -10, -3);
            ```
            ``` csharp
            int x = Method(
                -10,
                -3);
            ```
            ``` csharp
            int x = Method(
                (100 + 90)
                - 999,
                -3);
            ```
            
            ✖
            ``` csharp
            int x =-10;
            int x =-(10 + 3);
            ```
            ``` csharp
            x-= 10;
            ```
            ``` csharp
            int x = dictionary[ -10 ];
            ```
            ``` csharp
            int x = Method( -10, -3);
            ```
            ``` csharp
            int x = Method(
                100,
                 -10,
                 -3);
            ```
            ``` csharp
            int x = Method(
                (100 + 90) -
                999,
                -3);
            ```

  * ✔ Space operator keyword correctly
  
    * The *operator* keyword should always be preceded and followed by a single space.
    
        ✔
        ``` csharp
        MyClass operator +(Custom c1, Custom c2)
        ```

        ✖
        ``` csharp
        MyClass operator+(Custom c1, Custom c2)
        ```

  * ✔ Space parenthesis correctly
  
    * Opening parenthesis should not be preceded by a whitespace, unless it is the first character on a line.
    * Opening parenthesis is allowed to be preceded by whitespace when it's preceded by certain C# keywords (if, while, for etc..).
    * Opening parenthesis is allowed to be preceded by whitespace when it follows an operator symbol within an expression.
    * Closing parenthesis should not be followed by a whitespace.
    * Closing parenthesis is not allowed to be followed by whitespace when it comes at the end of a cast.
    * Closing parenthesis is allowed to be followed by whitespace when it's followed by certain operator symbols.

        ✔
        ``` csharp
        public void Method()
        ```
        ``` csharp
        int x = c * (a + b);
        int x = (a + b) * c;
        ```
        ``` csharp
        int x = (int)((a + b) / c);
        ```
        ``` csharp
        if (a > b)
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
        public void Method ()
        ```
        ``` csharp
        int x = c*(a + b);
        int x = (a + b)*c;
        ```
        ``` csharp
        int x = (int) ((a + b) / c);
        ```
        ``` csharp
        if(a > b)
        ```
        ``` csharp
        Method(Math.Max(1, 2) , Math.Sqrt(144) );
        ```

  * ✔ Space positive sign correctly
  
    * Positive sign should always be preceded by a single space.
    * Positive sign should never be the last character on a line.
    * Exceptions when:
      * it's the first character after an opening square bracket
      * it's the first character after an opening parenthesis
      * it's the first character on the line
      
        ✔
        ``` csharp
        x += 10;
        ```
        ``` csharp
        int x = dictionary[+10];
        ```
        ``` csharp
        int x = Method(
            (900 / 90)
            + 100,
            -3);
        ```
        ``` csharp
        string s = "First Name" + "Middle Name" + "LastName";
        string s = "First Name"
            + "Middle Name"
            + "LastName";
        ```

        ✖
        ``` csharp
        x+= 10;
        ```
        ``` csharp
        int x = dictionary[ +10 ];
        ```
        ``` csharp
        int x = Method(
            (900 / 90) +
            100,
            -3);
        ```
        ``` csharp
        string s = "First Name"+"Middle Name"+"LastName";
        string s = "First Name" +
            "Middle Name" +
            "LastName";
        ```

  * ✔ Space semicolons correctly
  
    * Semicolons should always be followed by a space, unless it is the last character on the line.
    * Semicolons should never be preceded by any whitespace.
    
        ✔
        ``` csharp
        for (int i = 0; i < 10; ++i)
        ```
        ``` csharp
        string s = "semicolons";
        ```
        ``` csharp
        public int Counter { get; set; } = 100;
        ```

        ✖
        ``` csharp
        for (int i = 0;i < 10;++i)
        for (int i = 0 ; i < 10 ; ++i)
        ```
        ``` csharp
        string s = "semicolons" ;
        ```
        ``` csharp
        public int Counter { get ; set ; } = 100;
        ```

  * ✔ Space square brackets correctly
  
    * Opening square brackets should never be followed by a whitespace, unless it's the last character on the line.
    * Opening square brackets should never be preceded by a whitespace, unless it's the first character on the line.
    * Closing square brackets should never be preceded by a whitespace, unless it's the first character on the line.
    * Closing square brackets should never pe followed by a whitespace, except when it's followed by certain operators, or it is part of an array initialization.
    
        ✔
        ``` csharp
        int x = array[10];
        ```
        ``` csharp
        int x = array[10] + 1;
        ```
        ``` csharp
        int x = matrix[10, 10];
        ```
        ``` csharp
        int[] ints = new int[2];
        ```
        ``` csharp
        int[,] matrix = new int[2, 2];
        ```
        ``` csharp
        int[] ints = new int[] { 1, 2, 3 };
        ```
        ``` csharp
        int[] ints = { 1, 2, 3 };
        ```
        ``` csharp
        int[] ints = new[] { 1, 2, 3 };
        ```

        ✖
        ``` csharp
        int x = array [10];
        ```
        ``` csharp
        int x = array[10]+1;
        ```
        ``` csharp
        int x = matrix [10,10];
        ```
        ``` csharp
        int [] ints = new int[2];
        ```
        ``` csharp
        int[,] matrix = new int [2, 2];
        ```
        ``` csharp
        int[] ints = new int [] { 1, 2, 3 };
        ```
        ``` csharp
        int[] ints = new [] { 1, 2, 3 };
        ```

  * ✔ Space symbols correctly
  
    * Symbols: colons, operators (arithmetic, assignment, conditional, logical, relational, shift, lambda)
    * Symbols should always be surrounded by a single space on either side.
    * Unary operators should be preceded by a single space, but must never be followed by any space.
    * Exception: Unary operators preceded or followed by a parenthesis or bracket, when there should be no spaces.
    
        ✔
        ``` csharp
        int x = 10 + 20;
        ```
        ``` csharp
        bool isTrue = (x == y);
        bool isTrue = (x > y);
        bool isTrue = (x < y);
        bool isTrue = (x <= y);
        bool isTrue = (x >= y);
        bool isTrue = (x != y);
        ```
        ``` csharp
        int shift = 1 << 8;
        ```
        ``` csharp
        Func<int, int, int> sum = (x, y) => x + y;
        ```
        ``` csharp
        var filtered = collection
            .Where(item => item.Value >= 100)
            .ToList();
        ```
        ``` csharp
        if (!value)
        if (!(condition1 && condition2))
        ```
        ``` csharp
        bool x = !condition;
        ```

        ✖
        ``` csharp
        int x = 10+20;
        ```
        ``` csharp
        bool isTrue=(x == y);
        bool isTrue = (x>y);
        bool isTrue = (x< y);
        bool isTrue = (x <=y);
        bool isTrue =(x >= y);
        bool isTrue= (x != y);
        ```
        ``` csharp
        int shift = 1<<8;
        ```
        ``` csharp
        Func<int, int, int> sum = (x, y)=>x + y;
        ```
        ``` csharp
        var filtered = collection
            .Where(item=>item.Value>=100)
            .ToList();
        ```
        ``` csharp
        if ( !value)
        if ( ! value)
        if (! (condition1 && condition2))
        ```
        ``` csharp
        bool x=!condition;
        bool x =! condition;
        ```

  * ✔ Use four forward slashes to indicate commented-out code
  
    * To differentiate comments from commented-out code, use four forward slashes.
    
        ✔
        ``` csharp
        int Sum(int x, int y)
        {
            ////int result = x + y;
            ////return result;
            
            // Return sum
            return x + y;
        }
        ```

        ✖
        ``` csharp
        int Sum(int x, int y)
        {
            //int result = x + y;
            // return result;
            
            // Return sum
            return x + y;
        }
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
        
  * ✖ Do not use tabs
  
    * The length of the tab character can vary depending upn the editor used to view the code.
    * This can cause spacing and idexing of the code to vary from the developer's intent and can make the code difficult to read and understand.
    * EACH LEVEL OF INDENTATION SHOULD CONSIST OF FOUR SPACES.
    
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

## Types and variables

  * ✔ Fields must be private
  
    * Fields should always be private.
    * For mentainability reasons, properties should always be used as the mechanism for exposing fields outside of a class.
    * This allows the internal implementation of the property to change over time without changing the interface of the class.
    * Exceptions:
      * Fields within structs are allowed to have any access level.
    
        ✔
        ``` csharp
        private int count;

        public int Count
        {
            get { return this.count };
            set { this.count = value; }
        }
        ```

        ✖
        ``` csharp
        public int count;
        ```

  * ✔ Use camelCasing for method arguments, local variables, and fields
  
    * Use camelCasing for:
      * method arguments
      * local variables
      * fields
      * lambda parameters
    
        ✔
        ``` csharp
        string serialNumber;
        ```
        ``` csharp
        void Method(string userName, DateTime expiryDate)
        ```
        ``` csharp
        void Method()
        {
            int activeDays = (expiryDate - DateTime.UtcNow).Days;
        }
        ```

        ✖
        ``` csharp
        string SerialNumber;
        string serial_number;
        ```
        ``` csharp
        void Method(string UserName, DateTime expirydate)
        ```
        ``` csharp
        void Method()
        {
            int ActiveDays = (expiryDate - DateTime.UtcNow).Days;
        }
        ```

  * ✔ Use predefined type names
  
    * Use predefined type names, instead of system type names.
    
        ✔
        ``` csharp
        string name;
        int index;
        bool isValid;
        ```

        ✖
        ``` csharp
        String name;
        Int32 index;
        Boolean isValid;
        ```

  * ✖ Do not use abbreviations
  
    * Avoid use of abbreviations.
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

  * ✖ Do not use underscores in identifiers
  
    * [c-sharpcorner.com article](https://www.c-sharpcorner.com/article/stop-use-var-everywhere-and-think-before-use-underscore-with-private-variable-in/)
    * Exception are *Discards*, introduced in C# 7.0
    
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
        
  * ✔ GOOD
  * ✖ BAD
  
    * text
    * text
    
        ✔
        ``` csharp

        ```

        ✖
        ``` csharp

        ```