# **DO NOT** prefix calls with base unless local implementation exists

> A call to a member from an inherited class must begin with base only when local class contains an override or implementation.  

``` csharp
// DO
public virtual string JoinName(string first, string last)
{
    return $“BASE: {first} {last}”;
}

string name = this.Join("", "");
```

``` csharp
// DON'T
public virtual string JoinName(string first, string last)
{
    return $“BASE: {first} {last}”;
}

string name = base.Join("", "");
```
