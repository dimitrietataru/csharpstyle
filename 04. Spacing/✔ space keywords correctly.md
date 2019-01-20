### ✔ Space keywords correctly ✔
###

| Keyword     | Followed by space |
|:------------|:------------------|
| catch       | Yes               |
| fixed       | Yes               |
| for         | Yes               |
| foreach     | Yes               |
| from        | Yes               |
| group       | Yes               |
| if          | Yes               |
| in          | Yes               |
| into        | Yes               |
| join        | Yes               |
| let         | Yes               |
| lock        | Yes               |
| orderby     | Yes               |
| return      | Yes               |
| select      | Yes               |
| stackalloc  | Yes               |
| switch      | Yes               |
| throw       | Yes               |
| using       | Yes               |
| where       | Yes               |
| while       | Yes               |
| yield       | Yes               |
| checked     | No                |
| default     | No                |
| sizeof      | No                |
| typeof      | No                |
| unchecked   | No                |
| new (ctor)  | Yes               |
| new (array) | No                |

### ✔
``` csharp
if (...)
{
}
```
``` csharp
while (...)
{
}
```
``` csharp
for (...)
{
}
```
``` csharp
switch (...)
{
}
```
``` csharp
return 1;
```
``` csharp
throw new Exception("message");
```
``` csharp
var strings = new string[] { "a", "b" };
```
``` csharp
var integers = new[] { 1, 2, 3 };
```

### ❌ 
``` csharp
if(...)
{
}
```
``` csharp
while(...)
{
}
```
``` csharp
for(...)
{
}
```
``` csharp
switch(...)
{
}
```
``` csharp
return1;
```
``` csharp
var integers = new [] { 1, 2, 3 };
```
