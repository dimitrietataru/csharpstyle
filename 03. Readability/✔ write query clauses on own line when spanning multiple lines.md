### ✔ Write query clauses on own line when spanning multiple lines ✔
###

> Query clauses must be written on own line when spanning multiple lines.

### ✔
``` csharp
var x = collection
    .Where(item => start >= item.StartDate && end <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name })
    .ToList();
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
    .Select(item =>
		new
		{
			Id = item.Id,
			Name = item.Name
		})
    .ToList();
```
``` csharp
var x = collection
    .Where(item =>
		start >= item.StartDate
		&& end <= item.EndDate)
    .Select(item =>
		new
		{
			Id = item.Id,
			Name = item.Name
		})
    .ToList();
```
``` csharp
var x =
	select a
	in b
	from c.GetCustomers(
		2, “x”);
```

### ❌
``` csharp
var x = collection.Where(item =>
        start >= item.StartDate
        && end <= item.EndDate)
    .Select(item => new { Id = item.Id, Name = item.Name })
    .ToList();
```
``` csharp
var x = collection.Select(item =>
		new
		{
			Id = item.Id,
			Name = item.Name
		})
    .ToList();
```
``` csharp
var x =
	select a
	in b from c.GetCustomers(
		2, “x”);
```