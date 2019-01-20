### ✔ Comment fall-through cases ✔
###

> Within a switch block, each statement can be terminated abruptly by break, continue, return, or throw keywords.  
> To mark statements with same result it is recommended, but not mandatory, to use an expressive comment. Usually '// falls through' is enough.  

### ✔
``` csharp
switch (x)
{
    case 1:
        // fall through
    case 2:
        HandleOneAndTwo();
        break;
    case 3:
        HandleThree();
        break
    default:
        HandleDefault();
        break;
}
```
``` csharp
switch (ch)
{
    case 'a':
    case 'e':
    case 'i':
    case 'o':
    case 'u':
    case 'A':
    case 'E':
    case 'I':
    case 'O':
    case 'U':
        HandleVowel();
        break;
    default:
        break;
}
```

### ❌ 
``` csharp
switch (ch)
{
    case 'a':
        // fall through
    case 'e':
        // fall through
    case 'i':
        // fall through
    case 'o':
        // fall through
    case 'u':
        // fall through
    case 'A':
        // fall through
    case 'E':
        // fall through
    case 'I':
        // fall through
    case 'O':
        // fall through
    case 'U':
        HandleVowel();
        break;
    default:
        break;
}
```
