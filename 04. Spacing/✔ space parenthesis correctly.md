### ✔ Space parenthesis correctly ✔
###

> Opening parenthesis should not be preceded by a whitespace, unless it is the first character on a line.  
> Opening parenthesis is allowed to be preceded by whitespace when it's preceded by certain C# keywords (if, while, for etc..).  
> Opening parenthesis is allowed to be preceded by whitespace when it follows an operator symbol within an expression.  

> Closing parenthesis should not be followed by a whitespace.
> Closing parenthesis is not allowed to be followed by whitespace when it comes at the end of a cast.  
> Closing parenthesis is allowed to be followed by whitespace when it's followed by certain operator symbols.

### ✔
``` csharp
public void Method()
{
}
```
``` csharp
int x = c * (a + b);
```
``` csharp
int x = (a + b) * c;
```
``` csharp
int x = (int)((a + b) / c);
```
``` csharp
if (a > b)
{
}
```
``` csharp
var x = Method(Math.Max(1, 2), Math.Sqrt(144));
```
``` csharp
var result = longMethodCall(
    (200 - 144) * 3
    + (999 / 18),
    1,
    2);
```

### ❌ 
``` csharp
public void Method ()
{
}
```
``` csharp
int x = c*(a + b);
```
``` csharp
int x = (a + b)*c;
```
``` csharp
int x = (int) ((a + b) / c);
```
``` csharp
if(a > b)
{
}
```
``` csharp
var x = Method(Math.Max(1, 2) , Math.Sqrt(144) );
```
