### ✔ Follow closing curly brackets by a blank line ✔

> Ensure a blank line follows closing curly brackets.  

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
    }}
```
