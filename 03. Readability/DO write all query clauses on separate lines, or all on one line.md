# **DO** write all query clauses on separate lines, or all on one line

> Query expressions should be placed on separate lines, or all on same line.

``` csharp
// DO
var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear)).ToList();

var babies = persons
    .Where(person => person.DateOfBirth.Year.Equals(currentYear))
    .ToList();
    
var x = select a in b from c;
```

``` csharp
// DON'T
var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear))
    .ToList();

var babies = persons.Where(person => person.DateOfBirth.Year.Equals(currentYear))
                    .ToList();
    
var babies = persons
    .Where(person => person.DateOfBirth.Year.Equals(currentYear)).ToList();
    
var x = select a
    in b from c;
    
var x =
    select
    a
    in
    b
    from
    c;
```
