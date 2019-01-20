### ❌ Do not split overloads ❌
###

> When a class has multiple constructors, or multiple methods with the same name, these appear sequentially, with no code in between (NOT even private members).

### ✔
``` csharp
public class Application
{
    public Application(int x)
    {
    }
    
    private Application()
    {
    }
    
    public void Execute(int count)
    {
    }
    
    public void Execute(int count, int retryCount)
    {
    }
    
    private void Execute(int count, bool isRetrying)
    {
    }
    
    public void Display()
    {
    }
}
```

### ❌ 
``` csharp
public class Application
{
    public Application(int x)
    {
    }
 
    public void Execute(int count)
    {
    }
    
    public void Execute(int count, int retryCount)
    {
    }
   
    public void Display()
    {
    }
    
    private Application()
    {
    }
    
    private void Execute(int count, bool isRetrying)
    {
    }
}
```
``` csharp
public class Application
{
    public Application(int x)
    {
    }
    
    private Application()
    {
    }
    
    public void Execute(int count)
    {
    }
    
    public void Execute(int count, int retryCount)
    {
    }
    
    public void Display()
    {
    }
    
    private void Execute(int count, bool isRetrying)
    {
    }
}
```
