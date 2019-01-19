# ✔ Write single line comments with proper follow and precede elements ✔

> Single line comments should always be preceded by a blank line.  
> Single line comments should never be followed by (a) blank line(s).  

``` csharp
// DO
public bool Enabled
{
    get
    {
        // This comment is valid
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
        // This comment is not valid
        
        return this.enabled;  
    }
}

public bool Enabled
{
    get
    {
    
        // This comment is not valid
        return this.enabled;  
    }
}

public bool Enabled
{
    get
    {
    
        // This comment is not valid
        
        return this.enabled;  
    }
}

public bool Enabled
{
    get
    {
        // This is a sample comment which doesn't really say anything.
        // This is another part of the comment. Both are not valid!
    
        // This comment is valid
        return this.enabled;  
    }
}
```
