### ✔ Space negative sign correctly ✔
###

> Negative sign should always be preceded by a single space.  
> Negative sign should never be the last character on a line.  


Exceptions when:  
> it's the first character after an opening square bracket  
> it's the first character after an opening parenthesis  
> it's the first character on the line

### ✔
``` csharp
int x = -10;
```
``` csharp
x -= 10;
```
``` csharp
int x = -(10 + 3);
```
``` csharp
int x = dictionary[-10];
```
``` csharp
int x = Method(-10, -3);
```
``` csharp
int x = Method(
    -10, -3);
```
``` csharp
int x = Method(
    -10,
    -3);
```
``` csharp
int x = Method(
    (100 + 90)
    - 999,
    -3);
```

### ❌ 
``` csharp
int x =-10;
```
``` csharp
x-= 10;
```
``` csharp
int x =-(10 + 3);
```
``` csharp
int x = dictionary[ -10 ];
```
``` csharp
int x = Method( -10, -3);
```
``` csharp
int x = Method(
    100,
     -10,
     -3);
```
``` csharp
int x = Method(
    (100 + 90) -
    999,
    -3);
```
