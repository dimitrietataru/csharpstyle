### ✔ Space positive sign correctly ✔
###

> Positive sign should always be preceded by a single space.  
> Positive sign should never be the last character on a line.  


Exceptions when:  
> it's the first character after an opening square bracket  
> it's the first character after an opening parenthesis  
> it's the first character on the line

### ✔
``` csharp
x += 10;
```
``` csharp
int x = dictionary[+10];
```
``` csharp
int x = Method(
    (900 / 90)
    + 100,
    -3);
```
``` csharp
string s = "First Name" + "Middle Name" + "LastName";
```
``` csharp
string s = "First Name"
    + "Middle Name"
    + "LastName";
```

### ❌ 
``` csharp
x+= 10;
```
``` csharp
int x = dictionary[ +10 ];
```
``` csharp
int x = Method(
    (900 / 90) +
    100,
    -3);
```
``` csharp
string s = "First Name"+"Middle Name"+"LastName";
```
``` csharp
string s = "First Name" +
    "Middle Name" +
    "LastName";
```
