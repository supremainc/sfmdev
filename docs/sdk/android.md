# Android

## Quick start

**Step 1**  
Download these files.  
[arm64-v8a_libSFM_SDK_android.so]()  
[armeabi-v7a_libSFM_SDK_android.so]()  
[armeabi_libSFM_SDK_android.so]()  
[JNI_Header.zip]()  
[UnifingerUI for Android.docx]() 

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
Implement write/read call back function in android.

![](/images/sdk/android/write_callback.png)

![](/images/sdk/android/read_callback.png)

**Step 6**  
Connect to communication function(write/read callback) with SDK using JNI.

![](/images/sdk/android/set_callback_JNI.png)

!!! Note
    **SetCommandClassName()**'s parameter is JNI class name that is made by you. 

Now, You can use SFM library in JNI class that is made by you.

**Step 7**  
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
