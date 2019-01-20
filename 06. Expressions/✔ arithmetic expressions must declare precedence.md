### ✔ Arithmetic expressions must declare precedence ✔
###

> C# mentains a hierarchy of precedence for arithmetic operators.  
> It is allowed to string multiple operations together on one statement and the compiler will automatically set the order based on pre-established rules.  
> In order to achieve full understanding of the code, the developer mustt know and understand the basic operator precedente rules in C#.  
> To increase readability and maintainability and reduce the risk of introducing bugs later, it is recommended to insert parenthesis to explicitly declare the operator precedence.  
> Inserting parenthesis makes the code more obvious and easy to understand, and removes the need for the reader to make assumptions about the code.

### ✔
``` csharp
int x = (10 % ((y * a) / b)) - 2;
```

### ❌ 
``` csharp
int x = 10 % y * a / b - 2;
```
