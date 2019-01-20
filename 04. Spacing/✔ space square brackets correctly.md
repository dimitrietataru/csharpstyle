### ✔ Space square brackets correctly ✔
###

> Opening square brackets should never be followed by a whitespace, unless it's the last character on the line.    
> Opening square brackets should never be preceded by a whitespace, unless it's the first character on the line.  

> Closing square brackets should never be preceded by a whitespace, unless it's the first character on the line.  
> Closing square brackets should never pe followed by a whitespace, except when it's followed by certain operators, or it is part of an array initialization.

### ✔
``` csharp
int x = array[10];
```
``` csharp
int x = array[10] + 1;
```
``` csharp
int x = matrix[10, 10];
```
``` csharp
int[] ints = new int[2];
```
``` csharp
int[,] matrix = new int[2, 2];
```
``` csharp
int[] ints = new int[] { 1, 2, 3 };
```
``` csharp
int[] ints = { 1, 2, 3 };
```
``` csharp
int[] ints = new[] { 1, 2, 3 };
```

### ❌ 
``` csharp
int x = array [10];
```
``` csharp
int x = array[10]+1;
```
``` csharp
int x = matrix [10,10];
```
``` csharp
int [] ints = new int[2];
```
``` csharp
int[,] matrix = new int [2, 2];
```
``` csharp
int[] ints = new int [] { 1, 2, 3 };
```
``` csharp
int[] ints = new [] { 1, 2, 3 };
```
