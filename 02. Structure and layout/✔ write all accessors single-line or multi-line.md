### ✔ Write all accessors single-line or multi-line ✔

> Write each accessor on a single line if the accessors are short.  
> Expand both accessors across multiple lines if the accessors are longer.  

### ✔
``` csharp
public bool Enabled { get; set; }
```
``` csharp
public bool Enabled
{
    get { return this.enabled; }
    set { this.enabled = value; }
}
```
``` csharp
public bool Enabled
{
    get => this.enabled;
    set => this.enabled = value;
}
```
``` csharp
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

### ❌ 
``` csharp
public bool Enabled
{
    get;
    set;
}
```
``` csharp
public bool Enabled
{
    get { return this.enabled; }
    set
    {
        this.enabled = value;
    }
}
```
``` csharp
public bool Enabled
{
    get => this.enabled;
    set
    {
        this.enabled = value;
    }
}
```
