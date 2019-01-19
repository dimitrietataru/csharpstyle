# ❌ Do not follow or precede opening curly brackets with a blank line ❌
#

> Opening curly brackets should always be followed by statements, not blank line(s).  
> Opening curly brackets should never be preceded by blank line(s).

### ✔
``` csharp
public bool Enabled
{
    get
    {
        return this.enabled;
    }
}
```

### ❌ 
``` csharp
public bool Enabled
{
    get
    {
    
        return this.enabled;
    }
}
```
``` csharp
public bool Enabled
{
    get
    
    {
        return this.enabled;
    }
}
```
``` csharp
public bool Enabled
{
    get
    
    {
    
        return this.enabled;
    }
}
```
