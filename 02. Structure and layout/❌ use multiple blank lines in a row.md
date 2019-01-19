# ❌ Do not use multiple blank lines in a row ❌

> To improve code readability, blank lines are required in certain situations, but are prohibited in others.  
> This results in a consistend visual pattern and can improve recognition of unfamiliar code.  
> Use a single blank line to separate logic blocks in methods, or file sections.  

``` csharp
// DO
using System;
using System.Threading.Tasks;

namespace Product.Module
{
    class Application
    {
        private int count;
    
        public Application()
        {
        }
    
        public bool IsEnabled
        {
            get
            {
                Console.WriteLine("Getting the enabled flag.");
        
                return this.enabled;
            }
        }
    
        public void Execute()
        {
        }
        
        public bool IsRunning()
        {
        }
    }
}
```

``` csharp
// DON'T

using System;

using System.Threading.Tasks;

namespace Product.Module
{
    class Application
    {
        private int count;
        public Application()
        {
        }
    
        public bool IsEnabled
        {
            get
            {
                Console.WriteLine("Getting the enabled flag.");
        
        
                return this.enabled;
            }
        }
    
        public void Execute()
        {
        }
        
        
        public bool IsRunning()
        {
        }
        
    }
}
```
