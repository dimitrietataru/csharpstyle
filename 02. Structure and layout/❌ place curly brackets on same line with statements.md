# ❌ Do not place curly brackets on same line with statements ❌

> Ensure that both opening and closing curly brackets are placed on their own line.  
> Curly brackets should not share the line with any other code, other than comments.  

``` csharp
// DO
public object Method()
{
    lock (this)
    {
        return this.value;
    }
}
```

``` csharp
// DON'T
public object Method()
{
    lock (this) {
        return this.value;
    }
}
    
public object Method()
{
    lock (this) {
        return this.value; }
}
    
public object Method()
{
    lock (this) { return this.value; }
}
```
