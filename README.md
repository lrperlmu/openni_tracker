# OpenNI Tracker

The OpenNI tracker broadcasts the OpenNI skeleton frames using tf.
For more information checkout the ROS Wiki: http://ros.org/wiki/openni_tracker

#NITE Information

The NITE library must be manually installed for openni_tracker to function.  The two versions that are compatible with this package are 1.5.2.21 and 1.5.2.23.

NITE v1.5.2.23 can currently be downloaded from [http://www.openni.ru/openni-sdk/openni-sdk-history-2/](http://www.openni.ru/openni-sdk/openni-sdk-history-2/)

# Device selection
### Usage
`rosrun openni_tracker openni_tracker _desired_serial:=B00312327745048B`
If you don't have a desired serial number, put `0` for the serial number
and it will select the first device it finds.


### Note
This implementation is dependent on how your system implements the shell
command `lsusb`. If your output looks something like this, you should be fine.
If it's much different, you'll have to modify the `getSerialNumber` function in
`openni_tracker.cpp` so it parses the output of `lsusb` to correctly get the
serial number.

```
$ lsusb -v -d 045e:02ae | grep // -e 'Bus\|iSerial'
Bus 001 Device 031: ID 045e:02ae Microsoft Corp. Xbox NUI Camera
  iSerial                 3 B00312327745048B
Bus 002 Device 018: ID 045e:02ae Microsoft Corp. Xbox NUI Camera
  iSerial                 3 A00123A01940048A
```
