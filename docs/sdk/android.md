# Android

[![](https://img.shields.io/github/v/tag/supremainc/sfm-sdk-android)](https://github.com/supremainc/sfm-sdk-android)
[![](https://img.shields.io/github/downloads/supremainc/sfm-sdk-android/total?label=Github%20downloads)](https://github.com/supremainc/sfm-sdk-android)
[![](https://jitpack.io/v/supremainc/sfm-sdk-android.svg)](https://jitpack.io/#supremainc/sfm-sdk-android)
![](https://img.shields.io/badge/latest%20SFM%20SDK-v3.3.0-blueviolet)

SFM SDK for Android is a library wrapping a Java library with SFM SDK based on C/C++ using JNI. You can easily use the SFM SDK for Android using JitPack. Also, you can download the source code of the SFM SDK for Android on our Github repository. 

Meanwhile, some functions are not supported. If you want to use that of functions, please modify the source code. And, If you want to share your modified codes, we are always welcome to your contributions.




## Release notes

### v0.6.0 - November 16, 2021
![](https://img.shields.io/badge/SFM%20SDK-v3.3.0-blueviolet)  
- SFM SDK version has been updated. 
  - Added secure packet protocol APIs.
  - Added key management APIs.
  - See details in [SFM SDK Manual v3.3.0](https://github.com/supremainc/sfm-sdk/blob/master/doc/SFM_SDK_Manual_v3.3.0.pdf)
- Firmware version information has been added.   


### v0.5.2 - March 31, 2020
![](https://img.shields.io/badge/SFM%20SDK-v3.1.2-blueviolet)  
- Minor fix. 

### v0.5.1 - March 17, 2020
![](https://img.shields.io/badge/SFM%20SDK-v3.1.1-blueviolet)  
- UART has become more stable.
There was a problem that the UART connection is disconnected with an error message of `UF_ERR_READ_SERIAL_TIMEOUT` when you receive data from the SFM on the Android app. This problem has been resolved at this release. 

### v0.5.0 - March 10, 2020
![](https://img.shields.io/badge/SFM%20SDK-v3.1.0-blueviolet)  
- UART is supported for rooted Android devices.  
- Added native callback functions in JNI for using SFM SDK.  
 
### v0.4.0 - Feburary 13, 2020
![](https://img.shields.io/badge/SFM%20SDK-v3.0.0-blueviolet)

New SFM SDK for Android has been released. 
From now on, you can easily use the SFM SDK for Android using JitPack. Or, you can download the SFM SDK for android manually in Github repository

https://github.com/supremainc/sfm-sdk-android

---

## Usage

### Installation

#### How to use using JitPack

To get a Git project into your build:

**Step 1.** Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories. (`/your_project_root_path/build.gradle`)

```gradle
allprojects {
    repositories {
    ...
    maven { url 'https://jitpack.io' }
    }
}
```

**Step 2.** Add the dependency in your app build.gradle (`/your_project_root_path/app/build.gradle`)

```gradle
dependencies {
    ...
    implementation 'com.github.supremainc:sfm-sdk-android:0.5.0'
    ...
}
```

If you are using the Java8, you need to insert the below over the dependency.

```gradle
compileOptions{
    sourceCompatibility JavaVersion.VERSION_1_8
    targetCompatibility JavaVersion.VERSION_1_8
}

dependencies {
    ...
    implementation 'com.github.supremainc:sfm-sdk-android:0.5.0'
    ...
}
```


**Step 3.** Include scripts for using the USB service and changing user-permission to access the storage in your device.

The SFM SDK for Android includes USB Library by default. You don't need to implement codes related to the USB controls. The USB Library
is used from https://github.com/felHR85/UsbSerial in the SFM SDK for Android. Also, it's version is `v6.1.0`.

Basically, you should insert the below script to `/your_project_root_path/app/src/main/AndroidManifest.xml` for proper working with the USB Library.

**<service>**

```xml
     
    <service
        android:name="com.supremainc.sfm_sdk.UsbService"
        android:enabled="true">
    </service>
```

Also, you need to insert the below script for using storage in your device.

**<user-permission>**

```xml
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"></uses-permission>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"></uses-permission>   

```

Please refer to https://github.com/supremainc/sfm-sdk-android/blob/master/app/src/main/AndroidManifest.xml

**AndroidManifest.xml**

```xml
<?xml version="1.0" encoding="utf-8"?><!--
  ~ Copyright (c) 2001 - 2019. Suprema Inc. All rights reserved.
  ~ Licensed under the MIT license. See LICENSE file in the project root for details.
  -->

<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.supremainc.sfm_sdk_android">

    <uses-feature android:name="android.hardware.usb.host"
        android:required="true"/>

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
     
        <service
            android:name="com.supremainc.sfm_sdk.UsbService"
            android:enabled="true">
        </service>

    </application>
    
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"></uses-permission>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"></uses-permission>
</manifest>
```
#### How to upgrade using JitPack 

To upgrade SFM SDK for Android, change the JitPack version in your root build.gradle at the end of repositories. (`/your_project_root_path/build.gradle`)

In the root build.gradle file, you should just change the JitPack version from `0.5.0` to `JitPack version to upgrade`.
```gradle
dependencies {
    ...
    implementation 'com.github.supremainc:sfm-sdk-android:0.5.0'
    ...
}
```
---

# [DEPRECATED]
## SFM SDK for Android (beta)

!!!info
    The previous version of the SFM SDK for Android (beta) was deprecated.
    the repository moved to https://github.com/supremainc/sfm-sdk-android/tree/sfm-sdk-android-beta

***You have to connect the SDK callback function to the communication function on Android for using android SFM_SDK.(See the below for details). Android sfm-sdk was made by C language and compiled using NDK. We currently provide SFM_SDK beta version 1.0.***

!!!Tip
    You can download all about android SFM_SDK(library, example project, document) through below github URL.
    **https://github.com/supremainc/sfm-sdk-android**

### Quick start

**Step 1**  
Download these files.  
[arm64-v8a_libSFM_SDK_android.so](https://github.com/supremainc/sfm-sdk-android/raw/master/Library/Android_SDK_Beta_v1.0/arm64-v8a/arm64-v8a_libSFM_SDK_android_Beta_v1.0.so)  
[armeabi-v7a_libSFM_SDK_android.so](https://github.com/supremainc/sfm-sdk-android/raw/master/Library/Android_SDK_Beta_v1.0/armeabi-v7a/armeabi-v7a_libSFM_SDK_android_Beta_v1.0.so)  
[armeabi_libSFM_SDK_android.so](https://github.com/supremainc/sfm-sdk-android/raw/master/Library/Android_SDK_Beta_v1.0/armeabi/armeabi_libSFM_SDK_android_Beta_v1.0.so)  
[JNI_Header.zip](https://github.com/supremainc/sfm-sdk-android/raw/master/Library/Android_SDK_Beta_v1.0/JNI_Header_Beta_v1.0.zip)  
[UnifingerUI for Android.docx](https://github.com/supremainc/sfm-sdk-android/raw/master/Document/UnifingerUI%20for%20Android(App_Beta_v1.2%2CSDK_Beta_v1.0).docx) 

!!! note
    **arm64-v8a_libSFM_SDK_android.so** is a library file for 64bits arm processor.  
    **armeabi-v7a_libSFM_SDK_android.so** is a library file for arm processor V7 or more up version.  
    **armeabi_libSFM_SDK_android.so** is a library file for arm processor V5 or V6.  
    **JNI_Header.zip** is a header files for library.  
    **UnifingerUI for Android.docx** is a file for documentation of android library.  

**Step 2**  
Create a android project.

**Step 3**  
Add library files on your project.

![](/images/sdk/android/add_library_android.png)

!!! Note
    jnilib folder does not exist. Just make it.(you can use any name).

**Step 4**  
Unzip JNI_Header.zip. And add header files in jni folder.

![](/images/sdk/android/add_JNI_Header.png)

**Step 5**  
Implement write call back function in java.

```java
private int SendPacketCallback(String var)throws InterruptedException, ExecutionException, TimeoutException{
    int returnSize = SendPacket(var);
    return returnSize;
}

public int SendPacket(String var) throws InterruptedException, ExecutionException, TimeoutException {
    int returnSize =0;
    byte[] sendPacket = new BigInteger(var,16).toByteArray();
    try {
        mOutputStream.write(sendPacket);
    } catch (IOException e) {
        e.printStackTrace();
    }
    returnSize = PACKET_INFO.UF_PACKET_LEN;
    
    return returnSize;
}
```

**Step 6**  
Implement read call back function in java.

```java
private int ReadPacketCallback(int size, byte[] read_buffer) throws InterruptedException, TimeoutException, ExecutionException {
    int readSize = m_SerialConnect.ReadPacket(size,read_buffer);

    return readSize;
}

public int ReadPacket(int size, byte[] read_buffer) throws InterruptedException, ExecutionException, TimeoutException {
    long lnStart =0, lnEnd =0;
    int nTime_out = 8000;
    int returnSize = 0;
    m_nRead_len = 0;

    lnStart = SystemClock.currentThreadTimeMillis();

    do {
        tempBuffer = new byte[size - returnSize];

        Future<Integer> future = executor.submit(readTask);
        m_nRead_len = future.get(nTime_out, TimeUnit.MILLISECONDS);

        if (m_nRead_len > 0) {
            System.arraycopy(tempBuffer, 0, read_buffer, returnSize, m_nRead_len);
            returnSize += m_nRead_len;
        }

        lnEnd = SystemClock.currentThreadTimeMillis();
    } while (returnSize < size && ((lnEnd - lnStart) < nTime_out));

}

Callable<Integer> readTask = new Callable<Integer>() {
    @Override
    public Integer call() throws Exception {
        int retSize = 0;

        do {
            retSize = mInputStream.read(tempBuffer);
        } while (retSize <= 0);

        return retSize;
    }
};

```
!!! tip
    Write/Read callback funciotn is used in SFM_SDK. It means SFM_SDK calls these function to communication with module.
    So you have to create proper Write/Read callback funciotn(Keep parameter type and return type). 
    And then connect these functions using setting functions like step 7.

**Step 7**  
Connect to communication function(write/read callback) with SDK using JNI.

```cpp
SetCommandClassName("com/suprema/www/unifingerui/CommandCall");
SetReadCallbackFunctionName("ReadPacketCallbakc");
SetWriteCallbackFunctionName("SendPacketCallback");
```

!!! Note
    **SetCommandClassName()**'s parameter is JNI class name that is made by you. 

Now, You can use SFM library in JNI class that is made by you.

**Step 8**  
Build your program. Then run.

!!! Note
    **If you want more detail explanation to use library and work environment or about license refer to documentation**


## Example code

### How to call identify function?
```cpp

JNIEXPORT jint JNICALL Java_com_suprema_www_unifingerui_Command_UF_1Identify  (JNIEnv * env, jobject obj)
{
    gobj=obj;
    int result=0;
    unsigned int userID=0;
    unsigned char subID=0;
    result=UF_Identify(&userID,&subID);

    if(result!=UF_RET_SUCCESS)
    {
        Update_UI_Result(result);
        return -1;
    }

    Update_UI_Result(userID);

    return result;
}

```
