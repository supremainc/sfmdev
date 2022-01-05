#C/C++

![](https://img.shields.io/badge/SFM%20SDK-v3.3.0-blueviolet)
![](https://img.shields.io/github/downloads/supremainc/sfm-sdk/total?color=green)  

[Download the latest version of SDK](https://github.com/supremainc/sfm-sdk/releases/latest).  

SFM SDK library included the structure of directories and files as below.
```
.
├── doc
│   └── SFM_SDK_Manual_v3.3.0.pdf
├── include
│   ├── UF_3000IO.h
│   ├── UF_3500IO.h
│   ├── UF_API.h
│   ├── UF_AccessControl.h
│   ├── UF_Bitmap.h
│   ├── UF_Command.h
│   ├── UF_Def.h
│   ├── UF_Delete.h
│   ├── UF_Enroll.h
│   ├── UF_Error.h
│   ├── UF_Identify.h
│   ├── UF_Image.h
│   ├── UF_Log.h
│   ├── UF_Module.h
│   ├── UF_Packet.h
│   ├── UF_Serial.h
│   ├── UF_SmartCard.h
│   ├── UF_Socket.h
│   ├── UF_SysParameter.h
│   ├── UF_Template.h
│   ├── UF_Upgrade.h
│   ├── UF_UserMemory.h
│   ├── UF_Verify.h
│   ├── UF_WSQ.h
│   ├── UF_Wiegand.h
│   └── Version.h
└── lib
    ├── linux
    │   └── libSFM_SDK.so
    └── windows
        ├── x64
        │   ├── SFM_SDK.dll
        │   └── SFM_SDK.lib
        ├── x64_ordinal
        │   ├── SFM_SDK.dll
        │   └── SFM_SDK.lib
        ├── x86
        │   ├── SFM_SDK.dll
        │   └── SFM_SDK.lib
        └── x86_ordinal
            ├── SFM_SDK.dll
            └── SFM_SDK.lib

```

!!!note 
    All the windows DLL files have the same name and the calling convention is `_stdcall`. Please use the proper DLL file for your purpose. 


