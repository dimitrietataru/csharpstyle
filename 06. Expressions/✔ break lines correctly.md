### ✔ Break lines correctly ✔
###

> Break at the dot separator '.'  
> Break at a comma ',', but it stays attached to the token that precedes it.  
> Break at lambda operator '=>'  
> Break at opening curly bracket '{' for in-line initializations.  
> Break at logical operators.  
> Split method arguments by the following rule: all on same line, or all on different line.  

### ✔
``` csharp
var x = Method(argument1, argument2, argument3);
```
``` csharp
var filteredItems = await FilterItemsByDateRangeAsync(
    argument1, argument2, argument3);
```
``` csharp
var x = Method(
    argument1,
    argument2,
    argument3);
```
``` csharp
if ((expression1 || expression2)
    && (expresion3 && expression4)
    || expression5
    || expression6)
{
    // ...
}
```
``` csharp
var x = collection
    .Where(item => item.RegisterDate.Year > 2000)
    .Join(
        collection2,
        collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy }),
        collection2 => new { Date = collection2.Date, Owner = collection2.User },
        (collection1, collection2) => new { OldEntry = collection1, NewEntry = collection2 })
    .Select(pair =>
        new
        {
            Id = pair.OldEntry.Id,
            X = pair.OldEntry.X,
            Y = pair.NewEntry.Y
        })
    .ToList();
```
``` csharp
var x = collection
    .Where(item =>
        item.RegisterDate.Year > 2000
        && item.OwnerId == User
        && item.IsAvailable)
    .ToList();
```

### ❌ 
``` csharp
var x = collection
    .Where(item => item.RegisterDate.Year > 2000)
    .Join(collection2, // DO NOT
        collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy }),
        collection2 => new { Date = collection2.Date, Owner = collection2.User },
        (collection1, collection2) => new { OldEntry = collection1, NewEntry = collection2 })
    .Select(pair =>
        new
        {
            Id = pair.OldEntry.Id,
            X = pair.OldEntry.X,
            Y = pair.NewEntry.Y
        })
    .ToList();
```
``` csharp
var x = collection
    .Where(item => item.RegisterDate.Year > 2000)
    .Join(
        collection2,
        collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy }),
        collection2 => new { Date = collection2.Date, Owner = collection2.User },
        (collection1, collection2) => new { OldEntry = collection1, NewEntry = collection2 })
    .Select(pair =>
        new
        {
            Id = pair.OldEntry.Id,
            X = pair.OldEntry.X,
            Y = pair.NewEntry.Y
        }).ToList(); // DO NOT
```
``` csharp
var x = collection.Where(item => item.RegisterDate.Year > 2000) // DO NOT
    .Join(
        collection2,
        collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy }),
        collection2 => new { Date = collection2.Date, Owner = collection2.User },
        (collection1, collection2) => new { OldEntry = collection1, NewEntry = collection2 })
    .Select(pair =>
        new
        {
            Id = pair.OldEntry.Id,
            X = pair.OldEntry.X,
            Y = pair.NewEntry.Y
        })
    .ToList();
```
``` csharp
var x = collection
    .Where(item => item.RegisterDate.Year > 2000)
    .Join(
        collection2,
        collection1 => new { Date = collection1.RegisterDate, Owner = collection1.RegisteredBy }),
        collection2 => new { Date = collection2.Date, Owner = collection2.User },
        (collection1, collection2) => new { OldEntry = collection1, NewEntry = collection2 })
    .Select(pair => new { // DO NOT
            Id = pair.OldEntry.Id,
            X = pair.OldEntry.X,
            Y = pair.NewEntry.Y }) // DO NOT
    .ToList();
```
