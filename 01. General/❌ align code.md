### ❌ NEVER align code ❌
###

> Alignment can aid readability.. for a minute, or so. In reality.. alignment creates problems for future maintenance!  
> A future change that needs to touch just one line of code will leave the formerly-pleasing formatting mangled.  
> The smallest change, like a variable rename will break your 'neatly formatted code'.  
> There should be no need to modify that extra piece of code and if it is, most likely will be left behind.  
> These block of code can slow down reviewers and exacerbates merge conflicts.

### ✔
``` csharp
public int count; // Allowed comment
private string name; // this is allowed too
```
``` csharp
// Allowed. You can't rename the IF keyword!
if (expression1
    && expression2
    && expression3)
{
}
```

### ❌
``` csharp
public int count;    // Alligned
private string name; // comments

public int activeItems;    // Will no longer
private string name; // be aligned after future edits
```
``` csharp
public  int     count;
private string  name;

// Change access modifier
private readonly  int     count;
private string  name;

// Add new field
public  int     count;
protected DateTime releaseDate;
private string  name;
```
``` csharp
public void Method(int parameter1,
                   int parameter2,
                   int parameter3,
                   int parameter4);

public void AfterMethodRename(int parameter1,
                   int parameter2,
                   int parameter3,
                   int parameter4);
```
``` csharp
var items = collection
    .Where(i => i.Date.Year > 2000
                && i.Owner == User)
    .ToList();

// Parameter rename leaves code unorganized and needs extra time to be fixed.
var items = collection
    .Where(currentItem => currentItem.Date.Year > 2000
                && currentItem.Owner == User)
    .ToList();
```
