### ✔ Space symbols correctly ✔
###

> Symbols: colons, operators (arithmetic, assignment, conditional, logical, relational, shift, lambda)  
> Symbols should always be surrounded by a single space on either side.  
> Unary operators should be preceded by a single space, but must never be followed by any space.  
> Exception: Unary operators preceded or followed by a parenthesis or bracket, when there should be no spaces.

### ✔
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
{
    // ...
}
```
``` csharp
if (!(condition1 && condition2))
{
    // ...
}
```
``` csharp
bool x = !condition;
```

### ❌ 
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
{
    // ...
}
```
``` csharp
if ( ! value)
{
    // ...
}
```
``` csharp
if (! (condition1 && condition2))
{
    // ...
}
```
``` csharp
bool x=!condition;
bool x =! condition;
```
