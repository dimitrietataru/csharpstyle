### ✔ Space member access symbol correctly ✔
###

> Member access symbol should never have whitespace on either side, unless it's the first character on the line.

### ✔
``` csharp
int x = this.count;
```
``` csharp
var item1 = this.tuplePair.Item1;
```
``` csharp
var ids = collection.Select(item => item.Id).ToList();
```
``` csharp
var ids = collection
    .Select(item => item.Id)
    .ToList();
```

### ❌ 
``` csharp
int x = this. count;
```
``` csharp
int x = this .count;
```
``` csharp
int x = this . count;
```
``` csharp
var item1 = this .tuplePair .Item1;
```
``` csharp
var ids = collection. Select(item => item.Id). ToList();
```
``` csharp
var ids = collection.
    Select(item => item.Id).
    ToList();
```
