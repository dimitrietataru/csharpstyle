### ❌ Do not use underscores in identifiers ❌
###

```
https://www.c-sharpcorner.com/article/stop-use-var-everywhere-and-think-before-use-underscore-with-private-variable-in/
```

> Exception: DISCARDS, introduced in C# 7.0

### ✔
``` csharp
private int age;
```
``` csharp
private string lastName;
```
``` csharp
private readonly IDependencyInjection dependencyInjection;
```
``` csharp
services.AddScope<ISignature>(_ => new Implementation(99));
```
``` csharp
var x = list1
    .Join(list2, l1 => l1.Id, l2 => l2.Id, (l1, _) => l1)
    .ToList();
```
``` csharp
services.AddScope<ISignature>(_ => new Implementation(99));
```

### ❌ 
``` csharp
private int m_age;
```
``` csharp
private int _age;
```
``` csharp
private int current_age;
```
``` csharp
private string _lastName;
```
``` csharp
private readonly IDependencyInjection _dependencyInjection;
```
