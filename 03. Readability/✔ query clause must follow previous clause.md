### ✔ Query clause must follow previous clause ✔
###

> Query clause must begin on the same line as previous clause, or on the next line.

### ✔
``` csharp
var x = select a in b from c;
```
``` csharp
var x =
    select a
    in b
    from c;
```

### ❌ 
``` csharp
var x = select a in b
    from c;
```
``` csharp
var x = select a in b
        from c;
```
``` csharp
var x = select a
		in b
        from c;
```
``` csharp
var x = select a in b
                 from c;
```
