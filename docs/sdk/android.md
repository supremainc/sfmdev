# Android

New SFM SDK for Android has been released. ( 2020.2.13 )

From now on, you can easily use the SFM SDK for Android using JitPack.

[![](https://jitpack.io/v/supremainc/sfm-sdk-android.svg)](https://jitpack.io/#supremainc/sfm-sdk-android)


## How to use the SFM SDK for Android?

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
    implementation 'com.github.supremainc:sfm-sdk-android:v0.4.0'
    ...
}
```



---

## [DEPRECATED] SFM SDK for Android (beta)

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
