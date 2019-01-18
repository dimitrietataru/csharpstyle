# **DO** write all accessors single-line or multi-line

> Write each accessor on a single line if the accessors are short.  
> Expand both accessors across multiple lines ith the accessors are longer.  

``` csharp
// DO
public bool Enabled { get; set; }

public bool Enabled
{
    get { return this.enabled; }
    set { this.enabled = value; }
}

public bool Enabled
{
    get => this.enabled;
    set => this.enabled = value;
}

public bool Enabled
{
    get
    {
        return this.enabled;
    }
    
    set
    {
        this.enabled = value;
    }
}
```

``` csharp
// DON'T
public bool Enabled
{
    get;
    set;
}

public bool Enabled
{
    get { return this.enabled; }
    set
    {
        this.enabled = value;
    }
}

public bool Enabled
{
    get => this.enabled;
    set
    {
        this.enabled = value;
    }
}
```
