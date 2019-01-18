# **DO** Query clause must follow previous clause

> Query clause must begin on the same line as previous clause, or on the next line.

``` csharp
// DO
var x = select a in b from c;
var x =
    select a
    in b
    from c;
```

``` csharp
// DON'T
var x = select a in b
    from c;
    
var x = select a in b
        from c;
        
var x = select a in b
                 from c;
```
