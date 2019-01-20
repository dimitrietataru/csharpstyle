### ✔ Use camelCasing for method arguments, local variables, and fields ✔
###

> Use camelCasing for:  
> method arguments  
> local variables  
> fields  
> lambda parameters

### ✔
``` csharp
public string serialNumber;
```
``` csharp
public void Method(string userName, DateTime expiryDate)
{
}
```
``` csharp
public void Method()
{
    int activeDays = (expiryDate - DateTime.Now).Days;
}
```

### ❌ 
``` csharp
public string SerialNumber;
```
``` csharp
public string serial_number;
```
``` csharp
public void Method(string UserName, DateTime ExpiryDate)
{
}
```
``` csharp
public void Method(string Username, DateTime expirydate)
{
}
```
``` csharp
public void Method()
{
    int ActiveDays = (expiryDate - DateTime.Now).Days;
}
```
