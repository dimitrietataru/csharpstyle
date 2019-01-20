### ✔ space attributes correctly ✔
###

> Opening attribute brackets should never be followed by whitespace.  
> Closing attribute brackets should never be preceded by whitespace.

### ✔
``` csharp
[Attribute1]
[Attribute2(100)]
[Attribute3("string")]
public void Method()
{
}
```
``` csharp
[Attribute1, Attribute2(100), Attribute3("string")]
public void Method()
{
}
```

### ❌ 
``` csharp
[ Attribute1]
[ Attribute2(100)]
[ Attribute3("string")]
public void Method()
{
}
```
``` csharp
[Attribute1 ]
[Attribute2(100) ]
[Attribute3("string") ]
public void Method()
{
}
```
``` csharp
[ Attribute1 ]
[ Attribute2(100) ]
[ Attribute3("string") ]
public void Method()
{
}
```
``` csharp
[ Attribute1, Attribute2(100), Attribute3("string") ]
public void Method()
{
}
```
