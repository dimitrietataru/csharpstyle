# Types and variables

***

**DO** use **camelCasing** for _method arguments_, _local variables_, and _fields_
``` csharp
public class Computer
{
    public string serialNumber;

    public void Register(string userName, DateTime expiryDate)
    {
        int activeDays = (expiryDate - DateTime.Now).Days;
        // ...
    }
}
```

---

**DO** use **predefined type names**, instead of *system type names*.
``` csharp
// Correct
string name;
int index;
bool isValid;

// Avoid
String name;
Int32 index;
Boolean isValid;
```

---

**AVOID**  using **Abbreviations**. Exceptions: common names like *Id*, *Url*, *Ftp*, *Xml*, *Http*
``` csharp
// Correct 
IConfiguration configuration;
DateTimeOffset dateTimeOffset;
CancellationToken cancellationToken;
int index;

// Avoid
IConfiguration cfg;
DateTimeOffset offset;
CancellationToken ct;
int i;

// Exception
UserId userId;
XmlDocument xmlDocument;
HtmlHelper htmlHelper;
```

---

**DO NOT** use **underscores** in identifiers. Exception: *discards* (C# 7.0)
``` csharp
// Correct
public int age;
public string lastName;

// Wrong
public int current_age;
public string last_name;
private int _age;

// Exception
services.AddScope<ISignature>(_ => new Implementation(99));
```

---

**DO NOT** use **Hungarian** notation, or type identification in identifiers
``` csharp
// Correct
int age;
string address;
DateTime dateOfBirth;
List<Person> parents;

// Avoid
int iAge;
string strAddress;
List<Person> parentList;
```

---
