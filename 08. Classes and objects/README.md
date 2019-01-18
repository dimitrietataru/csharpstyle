# Classes and Objects

***

**DO** write each class in its own file. Use the same notation for file and class name.
``` csharp
// Application.cs
public class Application
{    
}

// Program.cs
public class Program
{
}

// Avoid
public class Application
{
    public class Program
    {
    }
}
```
---

**DO** use **PascalCasing** for _class names_, _method names_, and _properties_
``` csharp
public class Person
{
    public int Age { get; set; }
    
    public string Name { get; set; }
    
    public void Display()
    {
        // ...
    }
    
    public bool IsAdult()
    {
        // ...
    }
}
```

---

**DO** use **PascalCasing** when abbreviating 3 or more characters (When there are 2 chars both are uppercase)
``` csharp
IOException ioException;
UIElement uiElement;
HtmlHelper htmlHelper;
XmlDocument xmlDocument
```

---
