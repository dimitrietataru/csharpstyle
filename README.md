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
* Readability
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
    
        <p style="text-align: center;"> ✔ </p>
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
  
    * In Visual Studio todos are found in **Task List** window (*Ctrl + \\, T*)
    
        <p style="text-align: center;"> ✔ </p>
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

        <p style="text-align: center;"> ✖ </p>
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

        <sup>✔</sup>
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

        <sup>✖</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        public bool Enabled
        {
            get
            {
                return this.enabled;
            }
        }
        ```

        <sup>✖</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        namespace Company.Product.Module.SubModule;
        namespace Product.Module.Component;
        namespace Product.Layer.Module.Group;
        ```

        <sup>✖</sup>
        ``` csharp
        namespace Company.Module.SubModule;
        namespace Product.Component;
        namespace Module.Group;
        ```
        
  * ✔ Precede documentation elements with a blank line
  
    * Documentation elements should always be preceded by a blank line.  
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        using System;
        using System.Linq;
        using static System.Linq.Enumerable;
        using static System.Math;
        ```

        <sup>❌</sup>
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
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        /// <summary>
        /// Gets a value indicating whether the control is enabled.
        /// </summary>
        public bool Enabled
        {
            get { return this.enabled; }
        }
        ```

        <sup>❌</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        public bool Enabled
        {
            get
            {
                return this.enabled;
            }
        }
        ```

        <sup>❌</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        public bool Enabled
        {
            get
            {
                return this.enabled;
            }
        }
        ```

        <sup>❌</sup>
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
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        using System.IO;
        using System.Security.Cryptography;
        ```

        <sup>❌</sup>
        ``` csharp
        using System.IO;
        using System
            .Security.Cryptography;
        ```
        
  * ✖ Do not omit curly brackets
  
    * Always wrap the body of the statement in curly brackets.
    * Although this is legal in C#, the curly brackets are required to be present. They increase the readability and maintainability of the code.
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        public object Method()
        {
            lock (this)
            {
                return this.value;
            }
        }
        ```

        <sup>❌</sup>
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
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
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

        <sup>❌</sup>
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
    
        <sup>✔</sup>
        ``` csharp
        public int Count { get; set; }
        ```
        ``` csharp
        public object Method()
        {
            return null;
        }
        ```

        <sup>❌</sup>
        ``` csharp
        public object Method() { return null; }
        ```
        ``` csharp
        public object Method()
            { return null; }
        ```

  // Template        
  * ✔ GOOD
  * ✖ BAD
  
    * text
    * text
    
        <sup>✔</sup>
        ``` csharp

        ```

        <sup>✖</sup>
        ``` csharp

        ```