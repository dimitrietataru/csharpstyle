### ❌ Do not (habitually) add new methods at the end of the class ❌
###

> There's no single correct recipe for how to do it. Different classes may order their contents in different ways.  
> What is important is that each class uses some logical order, which its maintainer could explain if asked.  
> New methods are not just habitually added to the end of the class, as that yealds 'chronological by date added' ordering, which is not a logical ordering.  
> Do not forget that items inside a class should follow a specific order, by access modifiers.

### ✔
``` csharp
public class DatabaseService<T>
{
    public List<T> GetAll()
    {
    }
    
    // Newly added method
    public T GetById()
    {
    }
    
    public void Create()
    {
    }
    
    public void Update()
    {
    }
    
    public void Delete()
    {
    }
}
```

### ❌ 
``` csharp
public class DatabaseService<T>
{
    public List<T> GetAll()
    {
    }
    
    public void Create()
    {
    }
    
    public void Update()
    {
    }
    
    public void Delete()
    {
    }
    
    // Newly added method
    public T GetById()
    {
    }
}
```
