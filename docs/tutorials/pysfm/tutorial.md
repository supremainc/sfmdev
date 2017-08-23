# pysfm

It is assumed as below:  

+ Serial port of the SFM is connected with "COM8". (Tested on Windows)
+ All settings of the SFM are set as factory default.


## How to get serial port information using pysfm?


```console
>>> import pysfm
>>> pysfm.get_port_list()
[u'COM1', u'COM8']
>>>
```

## How to connect the module?

```console
>>> import pysfm
>>> module = pysfm.Module('COM8')
>>> module.connect()
[SEND] : 40 04 00 00 00 00 00 00 00 00 00 44 0A   # Sent packet
[RECV] : 40 04 30 00 00 00 00 00 00 00 61 D5 0A   # Received packet
True  # Return value of module.connect()
>>>
```
As shown in above, packet trace information is printed as default. If you want to disable this feature, you should call a function `deactivate_packet_trace()` before connect. (In opposite case, you should use `activate_packet_trace()` to enable.)

```console
>>> import pysfm
>>> module = pysfm.Module('COM8')
>>> module.deactivate_packet_trace()
>>> module.connect()
True
>>>
```

