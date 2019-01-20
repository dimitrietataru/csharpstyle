### ✔ Space curly brackets correctly ✔
###

> Opening curly brackets should always be preceded by a single space, unless it's part of a method call.  
> Opening curly brackets should always be followed by a single space, unless it's the last character on the line.  

> Closing curly brackets should always be followed by a single space, unless it's the last character on the line, or it's followed by closing parenthesis, comma, or semicolon.  
> Closing curly brackets should always be preceded by a single space, unless it's the first character on the line.

### ✔
``` csharp
public void Method()
{
}
```
``` csharp
var x = Method({ 1, 2 }, 1);
```
``` csharp
var x = Method({ 1, 2 } + { 3, 4 }, 1);
```
``` csharp
int[] ints = new[] { 1, 2, 3 };
```
``` csharp
var anon = new
{
    Id = 1,
    Name = "custom"
};
```
``` csharp
var anon = new { Id = 1, Name = "custom" };
```

### ❌ 
``` csharp
public void Method() { }
```
``` csharp
public void Method() {
}
```
``` csharp
public void Method()
{}
```
``` csharp
public void Method()
{ }
```
``` csharp
var x = Method( { 1, 2 }, 1);
```
``` csharp
var x = Method({ 1, 2 } , 1);
```
``` csharp
var x = Method( { 1, 2 } + { 3, 4 } , 1);
```
``` csharp
int[] ints = new[] {1, 2, 3};
```
``` csharp
int[] ints = new[]{ 1, 2, 3 };
```
``` csharp
int[] ints = new[] { 1, 2, 3 } ;
```
``` csharp
var anon = new
{
    Id = 1, Name = "custom"
};
```
``` csharp
var anon = new
{ Id = 1, Name = "custom" };
```
``` csharp
var anon = new{ Id = 1, Name = "custom" };
```
``` csharp
var anon = new{Id = 1, Name = "custom"};
```
