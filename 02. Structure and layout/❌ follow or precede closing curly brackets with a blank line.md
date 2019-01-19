# ❌ Do not follow or precede closing curly brackets with a blank line ❌
#

> Closing curly brackets should always be preceded by statements, not blank line(s).
> Closing curly brackets should never be followed by blank line(s).  

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
