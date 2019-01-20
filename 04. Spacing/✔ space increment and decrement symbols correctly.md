### ✔ Space increment and decrement symbols correctly ✔
###

> The should be no whitespace between the increment or decrement symbol and the item is being incremented or decremented.

### ✔
``` csharp
int a = ++b;
```
``` csharp
int a = b++;
```
``` csharp
int a = --b;
```
``` csharp
int a = b--;
```

### ❌ 
``` csharp
int a = ++ b;
```
``` csharp
int a = b ++;
```
``` csharp
int a = -- b;
```
``` csharp
int a = b --;
```
