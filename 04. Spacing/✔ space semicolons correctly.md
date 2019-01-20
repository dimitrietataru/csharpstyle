### ✔ Space semicolons correctly ✔
###

> Semicolons should always be followed by a space, unless it is the last character on the line.  
> Semicolons should never be preceded by any whitespace.

### ✔
``` csharp
for (int i = 0; i < 10; ++i)
{
    // ...
}
```
``` csharp
string s = "semicolons";
```
``` csharp
public int Counter { get; set; } = 100;
```

### ❌ 
``` csharp
for (int i = 0;i < 10;++i)
{
    // ...
}
```
``` csharp
for (int i = 0 ; i < 10 ; ++i)
{
    // ...
}
```
``` csharp
string s = "semicolons" ;
```
``` csharp
public int Counter { get; set; } = 100 ;
```
``` csharp
public int Counter { get ; set ; } = 100;
```
