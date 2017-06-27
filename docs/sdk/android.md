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
