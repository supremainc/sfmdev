# .NET

[![Join the chat at https://gitter.im/supremainc/.NET_sdk](https://badges.gitter.im/supremainc/.NET_sdk.svg)](https://gitter.im/supremainc/.NET_sdk?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
[![Github release](https://img.shields.io/github/release/supremainc/.NET_sdk.svg)](https://github.com/supremainc/.NET_sdk/releases)
![Github all releases (download)](https://img.shields.io/github/downloads/supremainc/.NET_sdk/total.svg) 

## Quick start

**Step 1**  
[Download the latest version of SDK](https://github.com/supremainc/.NET_sdk/releases).  

!!!note "The SDK includes these files"  
    **SFM_SDK.dll** is a library file for C/C++.  
    **SFM_SDK.dll** is a native library file for .NET  
    **SFM_SDK_NET.XML** is a file for documentation of .NET library.  

**Step 2**  
Create a .NET project.

**Step 3**  
Add reference on your project above **SFM_SDK_NET.dll** file.

![](/images/sdk/NET/add_reference.png)

!!! warning
    **SFM_SDK_NET.XML** should be located with **SFM_SDK_NET.dll** for correct works of intellisense in microsoft visual sutdio.

**Step 4**  
import reference.  

```csharp
using Suprema.SFM_SDK_NET;
```

![](/images/sdk/NET/import_reference.png)

Now, Write your source code using [SDK Manual](../documents/Introduction/)

**Step 5**  
Build your program. Then run.


## Example code

### How to init serial COM port?
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Suprema.SFM_SDK_NET;

namespace Sample
{
    class Program
    {
        static void Main(string[] args)
        {
            SFM_SDK_NET SFM = new SFM_SDK_NET();
            UF_RET_CODE result = new UF_RET_CODE();
            result = SFM.UF_InitCommPort("COM3", 19200, false);
            Console.WriteLine(result.ToString());
        }
    }
}

```
