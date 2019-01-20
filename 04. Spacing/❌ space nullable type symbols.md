### ❌ Do not space nullable type symbols ❌
###

> Nullable type symbol should never be preceded by whitespace, unless the symbol is the first on the line.

### ✔
``` csharp
DateTime? date;
```
``` csharp
DateTime? date1 = new DateTime(2000, 1, 1);
DateTime? date2 = new DateTime(3000, 1, 1);
var range = new { date1, date2 };

var startYear = range.date1?.Year ?? 2000;
```
``` csharp
DateTime? date1 = new DateTime(2000, 1, 1);
DateTime? date2 = new DateTime(3000, 1, 1);
var range = new { date1, date2 };

var startYear = range
    .date1
    ?.Year ?? 2000;
```

### ❌ 
``` csharp
DateTime ? date;
```
``` csharp
DateTime? date1 = new DateTime(2000, 1, 1);
DateTime? date2 = new DateTime(3000, 1, 1);
var range = new { date1, date2 };

var startYear = range.date1 ? .Year ?? 2000;
var endYear = range.date2 ?. Year ?? 2000;
```
``` csharp
DateTime? date1 = new DateTime(2000, 1, 1);
DateTime? date2 = new DateTime(3000, 1, 1);
var range = new { date1, date2 };

var startYear = range
    .date1?
    .Year ?? 2000;
```
