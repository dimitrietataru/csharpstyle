# **DO** write query clauses on multiple lines when previous clause spans multiple lines

> Write ALL clauses on new lines when one clause spans multiple lines

``` csharp
// DO
var x =
    select a
    in b.GetCustomers(
        2,
        “x”)
    from c;
    
var x = collection
    .Where(item =>
        from >= item.StartDate
        && to <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name })
    .ToList();
    
var x = collection
    .Where(item => from >= item.StartDate && to <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name })
    .ToList();
```

``` csharp
// DON'T
var x =
    select a
    in b.GetCustomers(
        2,
        “x”) from c;
        
var x = collection
    .Where(item =>
        from >= item.StartDate
        && to <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name }).ToList();
    
var x = collection
    .Where(item =>
        from >= item.StartDate && to <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name }).ToList();
```
