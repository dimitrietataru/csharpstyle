# **DO** follow closing curly brackets by a blank line

> Ensure a blank line follows closing curly brackets.  

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
    }}
```
