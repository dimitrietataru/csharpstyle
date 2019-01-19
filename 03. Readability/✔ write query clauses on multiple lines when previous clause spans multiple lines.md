### ✔ Write query clauses on multiple lines when previous clause spans multiple lines ✔
###

> Write ALL clauses on new lines when one clause spans multiple lines

### ✔
``` csharp
var x =
    select a
    in b.GetCustomers(
        2,
        “x”)
    from c;
```
``` csharp
var x = collection
    .Where(item =>
        start >= item.StartDate
        && end <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name })
    .ToList();
```
``` csharp
var x = collection
    .Where(item => start >= item.StartDate && end <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name })
    .ToList();
```

### ❌
``` csharp
var x =
    select a
    in b.GetCustomers(
        2,
        “x”) from c;
```
``` csharp
var x = collection
    .Where(item =>
        start >= item.StartDate
        && end <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name }).ToList();
```
``` csharp
var x = collection
    .Where(item =>
        start >= item.StartDate && end <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name }).ToList();
```
