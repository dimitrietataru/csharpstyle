# **DO NOT** follow or precede opening curly brackets with a blank line

> Opening curly brackets should always be followed by statements, not blank line(s).  
> Opening curly brackets should never be preceded by blank line(s).

``` csharp
// DO
public bool Enabled
{
    get
    {
        return this.enabled;
    }
}
```

``` csharp
// DON'T
public bool Enabled
{
    get
    {
    
        return this.enabled;
    }
}

public bool Enabled
{
    get
    
    {
        return this.enabled;
    }
}

public bool Enabled
{
    get
    
    {
    
        return this.enabled;
    }
}
```
