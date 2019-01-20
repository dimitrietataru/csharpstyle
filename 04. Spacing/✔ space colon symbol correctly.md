### ✔ Space colon symbol correctly ✔
###

> Colon symbol ":"  
> Colon should never be the only element on a single line.  
> Colon appearing within an element declaration must always have a single space on either side, uless it's the first character on the line.  
> Colon used in a conditional statement must always contain a single space on either side, unless it's the first character on the line.  
> Colon appearing at the end of a case statement should never be preceded by a whitespace.  
> Colon appearing at the end of a case statement should always be the followed by a whitespace, or be last character on the line.

### ✔
``` csharp
public class B<T> : A
    where T : class
{
    public B(int x) : base(x)
    {
    }
}
```
``` csharp
public class B<T> : A
    where T : class
{
    public B(int x)
        : base(x)
    {
    }
}
```
``` csharp
int x = isTrue ? 10 : 100;
```
``` csharp
int x = isTrue
    ? 10
    : 100;
```
``` csharp
switch (x)
{
    case 1:
        y = 1;
        break;
    case 2:
        break;
    default:
        y = 100;
        break;
}
```

### ❌ 
``` csharp
public class B<T>:A
    where T:class
{
    public B(int x):base(x)
    {
    }
}
```
``` csharp
public class B<T>:A
    where T:class
{
    public B(int x)
        :base(x)
    {
    }
}
```
``` csharp
int x = isTrue?10:100;
```
``` csharp
int x = isTrue
    ?10
    :100;
```
``` csharp
int x = isTrue
    ?
    10
    :
    100;
```
``` csharp
int x = isTrue
    ? 10 : 100;
```
``` csharp
switch (x)
{
    case 1 :
        y = 1;
        break;
    case 2: break; // Accepted, but should be avoided. Be consistent!
    default :
        y = 100;
        break;
}
```
