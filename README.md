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
* Spacing
* Types and variables
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
    
        ✔
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

  * ✔ Use TODO comments to mark work in progress, missing features or functionality
  
    * In Visual Studio todos are found in **Task List** window (*Ctrl + \\, T*).
    
        ✔ 
        ``` csharp
        public void Run(int counter)
        {
            // TODO: Validate input
            
            for (int i = 0; i < counter; ++i)
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
        private string name; // this is allowed too
        ```
        ``` csharp
        // Allowed. You can't rename the IF keyword!
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
                           int parameter3,
                           int parameter4);

        public void AfterMethodRename(int parameter1,
                           int parameter2,
                           int parameter3,
                           int parameter4);
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
  
    * Documentation elements should always be preceded by a blank line.  
    
        ✔
        ``` csharp
        public bool IsValid { get; set; }

        /// <summary>
        /// Gets a value indicating whether the control is enabled.
        /// </summary>
        public bool Enabled
        {
            get { return this.enabled; }
        }
        ```

        ✖
        ``` csharp
        public bool IsValid { get; set; }
        /// <summary>
        /// Gets a value indicating whether the control is enabled.
        /// </summary>
        public bool Enabled
        {
            get { return this.enabled; }
        }
        ```
        
  * ✔ Separate elements by a blank line
  
    * Add a blank line between adjacent elements.
    
        ✔
        ``` csharp
        public Constructor()
        {
            // ...
        }

        public void Method1()
        {
            // ...
        }

        public void Method2()
        {
            // ...
        }
        ```

        ✖
        ``` csharp
        public Constructor()
        {
            // ...
        }
        public void Method1()
        {
            // ...
        }
        public void Method2()
        {
            // ...
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
        using static System.Linq.Enumerable;
        using System.Linq;
        using static System.Math;
        ```
        ``` csharp
        using System.Linq;
        using static System.Math;
        using static System.Linq.Enumerable;
        using System;
        ```
        ``` csharp
        using System;
        using System.Linq;

        using static System.Linq.Enumerable;
        using static System.Math;
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
      
        <sup>✔</sup>
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
        public bool Enabled { get; set; }
        ```
        ``` csharp
        public bool Enabled
        {
            get { return this.enabled; }
            set { this.enabled = value; }
        }
        ```
        ``` csharp
        public bool Enabled
        {
            get => this.enabled;
            set => this.enabled = value;
        }
        ```
        ``` csharp
        public bool Enabled
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
        public bool Enabled
        {
            get;
            set;
        }
        ```
        ``` csharp
        public bool Enabled
        {
            get { return this.enabled; }
            set
            {
                this.enabled = value;
            }
        }
        ```
        ``` csharp
        public bool Enabled
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
        public bool Enabled
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
        public bool Enabled
        {
            get
            {
                // This comment is not valid
                
                return this.enabled;  
            }
        }
        ```
        ``` csharp
        public bool Enabled
        {
            get
            {
            
                // This comment is not valid
                return this.enabled;  
            }
        }
        ```
        ``` csharp
        public bool Enabled
        {
            get
            {
            
                // This comment is not valid
                
                return this.enabled;  
            }
        }
        ```
        ``` csharp
        public bool Enabled
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
        public object Method()
        {
            lock (this)
            {
                int a = 1;
                int b = 2;
                return a + b;
            }
        }
        ```

        ✖
        ``` csharp
        public object Method()
        {
            lock (this)
            {
                int a = 1; int b = 2;
                return a + b;
            }
        }
        ```
        ``` csharp
        public object Method()
        {
            lock (this) {
                int a = 1;
                int b = 2;
                return a + b; }
        }
        ```
        ``` csharp
        public object Method()
        {
            lock (this) { int a = 1; int b = 2; return a + b; }
        }
        ```
        
  * ✖ Do not follow documentation elements with a blank line
  
    * Documentation elements should always be followed by blocks of code.
    
        ✔
        ``` csharp
        /// <summary>
        /// Gets a value indicating whether the control is enabled.
        /// </summary>
        public bool Enabled
        {
            get { return this.enabled; }
        }
        ```

        ✖
        ``` csharp
        /// <summary>
        /// Gets a value indicating whether the control is enabled.
        /// </summary>

        public bool Enabled
        {
            get { return this.enabled; }
        }
        ```
        
  * ✖ Do not follow or precede closing curly brackets with a blank line
  
    * Closing curly brackets should always be preceded by statements, not blank line(s).
    * Closing curly brackets should never be followed by blank line(s).
    
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
                
            }
        }
        ```
        ``` csharp
        public bool Enabled
        {
            get
            {
                return this.enabled;
            }
            
        }
        ```
        ``` csharp
        public bool Enabled
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
            }
        }
        ```
        ``` csharp
        public bool Enabled
        {
            get
            
            {
                return this.enabled;
            }
        }
        ```
        ``` csharp
        public bool Enabled
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
            public class Application
            {
                // ...
            }
        }
        ```

        ✖
        ``` csharp

        using System

        namespace Program
        {
            public class Application
            {
                // ...
            }
        }


        ```
        
  * ✖ Do not line-wrap using statements
  
    * Always write using statements on a single line.
    
        ✔
        ``` csharp
        using System.IO;
        using System.Security.Cryptography;
        ```

        ✖
        ``` csharp
        using System.IO;
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
            return this.value;
        }
        ```
        ``` csharp
        if (true)
        {
            this.value = 2;
            return this.value;
        }
        ```

        ✖
        ``` csharp
        if (true) return this.value;
        ```
        ``` csharp
        if (true)
            return this.value;
        ```
        ``` csharp
        if (true)
            this.value = 2;      
            return this.value;
        ```
        
  * ✖ Do not place curly brackets on same line with statements
  
    * Ensure that both opening and closing curly brackets are placed on their own (vertical) line.
    * Curly brackets should not share the line with any other code, other than comments.
    
        ✔
        ``` csharp
        public object Method()
        {
            lock (this)
            {
                return this.value;
            }
        }
        ```

        ✖
        ``` csharp
        public object Method()
        {
            lock (this) {
                return this.value;
            }
        }
        ```
        ``` csharp
        public object Method()
        {
            lock (this) {
                return this.value; }
        }
        ```
        ``` csharp
        public object Method()
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

        ✖
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

  * ✖ Do not use multiple blank lines in a row
  
    * To improve code readability, blank lines are required in certain situations, but are prohibited in others.
    * This results in a consistend visual pattern and can improve recognition of unfamiliar code.
    * Use a single blank line to separate logic blocks in methods, or file sections.
    
        ✔
        ``` csharp
        using System;
        using System.Threading.Tasks;

        namespace Product.Module
        {
            class Application
            {
                private int count;
            
                public Application()
                {
                }
            
                public bool IsEnabled
                {
                    get
                    {
                        Console.WriteLine("Getting the enabled flag.");
                
                        return this.enabled;
                    }
                }
            
                public void Execute()
                {
                }
                
                public bool IsRunning()
                {
                }
            }
        }
        ```

        ✖
        ``` csharp

        using System;

        using System.Threading.Tasks;

        namespace Product.Module
        {
            class Application
            {
                private int count;
                public Application()
                {
                }
            
                public bool IsEnabled
                {
                    get
                    {
                        Console.WriteLine("Getting the enabled flag.");
                
                
                        return this.enabled;
                    }
                }
            
                public void Execute()
                {
                }
                
                
                public bool IsRunning()
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
        public int Count { get; set; }
        ```
        ``` csharp
        public object Method()
        {
            return null;
        }
        ```

        ✖
        ``` csharp
        public object Method() { return null; }
        ```
        ``` csharp
        public object Method()
            { return null; }
        ```

## Readability

  * ✔ Close parenthesis on line with last parameter
  
    * The closing parenthesis in a call to a method must be placed on same line as the last parameter.
    * The closing parenthesis in a call to an indexer must be placed on same line as the last parameter.
    * The closing parenthesis in a method declaration must be placed on same line as the last parameter.
    * The closing parenthesis in an indexer declaration must be placed on same line as the last parameter.
    
        ✔
        ``` csharp
        public bool IsValid(int number)
        {
            // ...
        }
        ```
        ``` csharp
        bool isValid = IsValid(100);
        ```
        ``` csharp
        int x = entries[0];
        ```
        ``` csharp
        public int this[int x]
        {
            get { return entries[x]; }
        }
        ```

        ✖
        ``` csharp
        public bool IsValid(
            int number
            )
        {
            // ...
        }
        ```
        ``` csharp
        bool isValid = IsValid(
            100
            );
        ```
        ``` csharp
        bool isValid = IsValid
            (
            100
            );
        ```
        ``` csharp
        int x = entries[
            0
            ];
        ```
        ``` csharp
        public int this
        [
            int x
        ]
        {
            get { return entries[x]; }
        }
        ```

  * ✔ Ensure comma is on same line as previous parameter
  
    * Always write commas on same line as previous parameter.
    
        ✔
        ``` csharp
        string name = GetName(
            first,
            last);
        ```
        ``` csharp
        public int this[
            int x,
            int y]
        {
            // ...
        }
        ```

        ✖
        ``` csharp
        string name = GetName(
            first
            ,last);
        ```
        ``` csharp
        public int this[
            int x
            ,int y]
        {
            // ...
        }
        ```

  * ✔ Open parenthesis on declaration line
  
    * The opening parenthesis in a call to a method must be placed on same line as the method.
    * The opening parenthesis in a call to an indexer must be placed on same line as the indexer name.
    * The opening parenthesis in a method declaration must be placed on same line as the method.
    * The opening parenthesis in an indexer declaration must be placed on same line as the indexer name.
    
        ✔
        ``` csharp
        public bool IsValid(int number)
        {
            // ...
        }
        ```
        ``` csharp
        bool isValid = IsValid(100);
        ```
        ``` csharp
        int x = entries[0];
        ```
        ``` csharp
        public int this[int x]
        {
            get { return entries[x]; }
        }
        ```

        ✖
        ``` csharp
        public bool IsValid
            (int number)
        {
            // ...
        }
        ```
        ``` csharp
        bool isValid = IsValid
            (100);
        ```
        ``` csharp
        int x = entries
        [0];
        ```
        ``` csharp
        public int this
            [int x]
        {
            get { return entries[x]; }
        }
        ```

  * ✔ Parameter list must follow declaration
  
    * The start of the parameter list of a method or indexer must begin on same line or next line of the opening parenthesis.
    
        ✔
        ``` csharp
        public int Sum(int a, int b, int c, int d)
        {
        }
        ```
        ``` csharp
        public int Sum(
            int a, int b, int c, int d)
        {
        }
        ```
        ``` csharp
        public int Sum(
            int a,
            int b,
            int c,
            int d)
        {
        }
        ```

        ✖
        ``` csharp
        public int Sum(int a, int b, int c,

            int d)
        {
        }
        ```
        ``` csharp
        public int Sum(

            int a, int b, int c, int d)
        {
        }
        ```
        ``` csharp
        public int Sum(

            int a,
            int b,
            int c,
            int d)
        {
        }
        ```

  * ✔ Parameters must follow comma
  
    * Parameters must be written on same, or next line as previous parameter.
    
        ✔
        ``` csharp
        public int Sum(int a, int b, int c, int d)
        {
        }
        ```
        ``` csharp
        public int Sum(
            int a, int b, int c, int d)
        {
        }
        ```
        ``` csharp
        public int Sum(
            int a,
            int b,
            int c,
            int d)
        {
        }
        ```

        ✖
        ``` csharp
        public int Sum(
            int a,

            int b,

            int c,

            int d)
        {
        }
        ```

  * ✔ Prefix local calls with this
  
    * Insert the this prefix before a call to a class member.
    
        ✔
        ``` csharp
        public class Student : Person
        {
            private string id;
            private double grade;
            
            public Person(string id, double grade, int age)
            {
                base.age = age;
                this.id = id;
                this.grade = grade;
            }
        }
        ```

        ✖
        ``` csharp
        public class Student : Person
        {
            private string m_id;
            private double _grade;
            
            public Person(string id, double grade, int age)
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
        ```
        ``` csharp
        var x =
            select a
            in b
            from c;
        ```

        ✖
        ``` csharp
        var x = select a in b
            from c;
        ```
        ``` csharp
        var x = select a in b
                from c;
        ```
        ``` csharp
        var x = select a
                in b
                from c;
        ```
        ``` csharp
        var x = select a in b
                         from c;
        ```

  * ✔ Split parameter list appropriately
  
    * Parameters must be placed all on one line, or each on a separate line.
    
        ✔
        ``` csharp
        public string JoinName(string first, string middle, string last)
        {
            // ...
        }
        ```
        ``` csharp
        public string JoinName(
            string first, string middle, string last)
        {
            // ...
        }
        ```
        ``` csharp
        public string JoinName(
            string first,
            string middle,
            string last)
        {
            // ...
        }
        ```

        ✖
        ``` csharp
        public string JoinName(string first,
            string middle, string last)
        {
            // ...
        }
        ```
        ``` csharp
        public string JoinName(string first, string middle,
            string last)
        {
            // ...
        }
        ```
        ``` csharp
        public string JoinName(
            string first,
            string middle, string last)
        {
            // ...
        }
        ```

  * ✔ Use built-in type alias
  
    * Use built-in alias for types.
    * Do not use basic types.
    * Do not use full namespace for types.
      
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
        var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear)).ToList();
        ```
        ``` csharp
        var babies = persons
            .Where(person => person.DateOfBirth.Year.Equals(currentYear))
            .ToList();
        ```
        ``` csharp
        var x = select a in b from c;
        ```

        ✖
        ``` csharp
        var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear))
            .ToList();
        ```
        ``` csharp
        var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear))
                            .ToList();
        ```
        ``` csharp
        var babies = persons
            .Where(person => person.DateOfBirth.Year.Equals(currentYear)).ToList();
        ```
        ``` csharp
        var x = select a
            in b from c;
        ```
        ``` csharp
        var x =
            select
            a
            in
            b
            from
            c;
        ```

  * ✔ Write query clauses on multiple lines when previous clause spans multiple lines
  
    * Write ALL clauses on new lines when one clause spans multiple lines.
    
        ✔
        ``` csharp
        var x =
            select a
            in b.GetCustomers(
                2,
                “x”)
            from c;
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
            .Select(item => new { Id = item.Id, Name = item.Name })
            .ToList();
        ```

        ✖
        ``` csharp
        var x =
            select a
            in b.GetCustomers(
                2,
                “x”) from c;
        ```
        ``` csharp
        var x = collection
            .Where(item =>
                start >= item.StartDate
                && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name }).ToList();
        ```
        ``` csharp
        var x = collection
            .Where(item =>
                start >= item.StartDate && end <= item.EndDate)
            .Select(item => new { Id = item.Id, Name = item.Name }).ToList();
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
            from c.GetCustomers(
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
            in b from c.GetCustomers(
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
        ``` csharp
        if (true)
        {
        #region
        }
        #endregion
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
        ```
        ``` csharp
        int counter = 10; ;
        ```

  * ✖ Do not write multiple statements on one line
  
    * Each statement must begin on a new line.
    
        ✔
        ``` csharp
        public int Sum(int first, int second)
        {
            int result = first + second;
            return result;
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
        public int Sum(int first, int second)
        {
            int result = first + second; return result;
        }
        ```
        ``` csharp
        int a, b;
        string firstName, lastName;
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
