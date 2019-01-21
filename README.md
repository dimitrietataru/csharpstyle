# C# coding standards, conventions, and guidelines



***

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

---

## Credits
This C# style recommends best practices so that other C# developers can write code maintainable by other C# developers.
The document contains data collected from various sources, language styles, and communities.  

  - [docs.microsoft.com](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/)
  - [dofactory.com](https://www.dofactory.com/reference/csharp-coding-standards)
  - [github.com/ktaranov](https://github.com/ktaranov/naming-convention/blob/master/C%23%20Coding%20Standards%20and%20Naming%20Conventions.md)
  - [c-sharpcorner.com](https://www.c-sharpcorner.com/article/stop-use-var-everywhere-and-think-before-use-underscore-with-private-variable-in/)
  - [stylecop.soyuz5.com](http://stylecop.soyuz5.com/StyleCop%20Rules.html)
  - [google.github.io](https://google.github.io/styleguide/javaguide.html)

***

## Table of contents

* [General](#general)
* Structure and layout
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

***

## General

  *  ✔ Vertically align curly brackets
    * **Allman** style. [Wikipedia](https://en.wikipedia.org/wiki/Indentation_style)
        <sup>✔</sup>
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
  * ✔ Use TODO comments to mark work in progress, missing features or functionality
    * In Visual Studio todos are found in **Task List** window (*Ctrl + \\, T*).  
        <sup>✔</sup>
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

        <sup>❌</sup>
        ``` csharp
        //TODO ...
        ```
        ``` csharp
        //TO DO ...
        ```
        ``` csharp
        // TO DO : ...
        ```
  * ❌ NEVER align code ❌
    * alignment can aid readability.. for a minute, or so. In reality.. alignment creates problems for future maintenance!  
    * a future change that needs to touch just one line of code will leave the formerly-pleasing formatting mangled.  
    * the smallest change, like a variable rename will break your 'neatly formatted code'.  
    * there should be no need to modify that extra piece of code and if it is, most likely will be left behind.  
    * these block of code can slow down reviewers and exacerbates merge conflicts.
        <sup>✔</sup>
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
        <sup>❌</sup>
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

***
