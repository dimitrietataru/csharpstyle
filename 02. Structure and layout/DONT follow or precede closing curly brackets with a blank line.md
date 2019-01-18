# **DO NOT** follow or precede closing curly brackets with a blank line

> Closing curly brackets should always be preceded by statements, not blank line(s).
> Closing curly brackets should never be followed by blank line(s).  

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
