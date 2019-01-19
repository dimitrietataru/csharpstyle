### ✔ Write all query clauses on separate lines, or all on one line ✔
###

> Query expressions should be placed on separate lines.  
> Exception: Short queries can be written on same line.

### ✔
``` csharp
var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear)).ToList();
```
``` csharp
var babies = persons
    .Where(person => person.DateOfBirth.Year.Equals(currentYear))
    .ToList();
```
``` csharp
var x = select a in b from c;
```

### ❌
``` csharp
var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear))
    .ToList();
```
``` csharp
var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear))
                    .ToList();
```
``` csharp
var babies = persons
    .Where(person => person.DateOfBirth.Year.Equals(currentYear)).ToList();
```
``` csharp
var x = select a
    in b from c;
```
``` csharp
var x =
    select
    a
    in
    b
    from
    c;
```
