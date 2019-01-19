### ❌ Do not prefix calls with base unless local implementation exists ❌
###

> A call to a member from an inherited class must begin with base only when local class contains an override or implementation.  

### ✔
``` csharp
public virtual string JoinName(string first, string last)
{
    return $“BASE: {first} {last}”;
}

public override string JoinName(string first, string last)
{
    return $THIS: {first} {last}”;
}

string thisName = this.Join("", "");
string baseName = base.Join("", "");
```

### ❌
``` csharp
public virtual string JoinName(string first, string last)
{
    return $“BASE: {first} {last}”;
}

string name = base.Join("", "");
```
