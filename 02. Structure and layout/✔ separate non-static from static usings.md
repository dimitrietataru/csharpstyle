# ✔ Separate non-static from static usings ✔
#

> Separate non-static from static usings.  
> Order usings alphabetically. First non-static, then static.  
> Do not separate usings, or static/non-static blocks by blank line(s).

### ✔
``` csharp
using System;
using System.Linq;
using static System.Linq.Enumerable;
using static System.Math;
```

### ❌ 
``` csharp
using System;
using static System.Linq.Enumerable;
using System.Linq;
using static System.Math;
```
``` csharp
using System.Linq;
using static System.Math;
using static System.Linq.Enumerable;
using System;
```
``` csharp
using System;
using System.Linq;

using static System.Linq.Enumerable;
using static System.Math;
```
