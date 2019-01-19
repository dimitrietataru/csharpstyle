### ✔ Close parenthesis on line with last parameter ✔
###

> The closing parenthesis in a call to a method must be placed on same line as the last parameter.  
> The closing parenthesis in a call to an indexer must be placed on same line as the last parameter.  
> The closing parenthesis in a method declaration must be placed on same line as the last parameter.  
> The closing parenthesis in an indexer declaration must be placed on same line as the last parameter.

### ✔
``` csharp
public bool IsValid(int number)
{
	// ...
}
```
``` csharp
bool isValid = IsValid(100);
```
``` csharp
int x = entries[0];
```
``` csharp
public int this[int x]
{
	get { return entries[x]; }
}
```

### ❌
``` csharp
public bool IsValid(
	int number
	)
{
	// ...
}
```
``` csharp
bool isValid = IsValid(
	100
	);
```
``` csharp
bool isValid = IsValid
	(
	100
	);
```
``` csharp
int x = entries[
	0
	];
```
``` csharp
public int this
[
	int x
]
{
	get { return entries[x]; }
}
```
