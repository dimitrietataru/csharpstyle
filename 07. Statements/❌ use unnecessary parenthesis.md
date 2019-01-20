### ❌ Do not use unnecessary parenthesis ❌
###

> It is possible to insert parenthesis around virtually any type of expression, statement, or clause.  
> Excessive parenthesis can have a negative effect, making it more difficult to read and maintain code.

### ✔
``` csharp
int x = 5 + b;
```
``` csharp
string y = this.Method().ToString();
```
``` csharp
return a + b;
```
``` csharp
return x.Value;
```

### ❌
``` csharp
int x = (5 + b);
```
``` csharp
string y = (this.Method()).ToString();
```
``` csharp
string y = (this.Method().ToString());
```
``` csharp
return (a + b);
```
``` csharp
return (x.Value);
```
