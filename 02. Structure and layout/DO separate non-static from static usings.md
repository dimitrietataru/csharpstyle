# **DO** separate non-static from static usings

> Separate non-static from static usings.  
> Order usings alphabetically. First non-static, then static.  
> Do not separate usings, or static/non-static blocks by blank line(s).

``` csharp
// DO
using System;
using System.Linq;
using static System.Linq.Enumerable;
using static System.Math;
```

``` csharp
// DON'T
using System;
using static System.Linq.Enumerable;
using System.Linq;
using static System.Math;

// DON'T
using System.Linq;
using static System.Math;
using static System.Linq.Enumerable;
using System;

// DON'T
using System;
using System.Linq;

using static System.Linq.Enumerable;
using static System.Math;
```
