# Android

## ADB

- start server over tcpip `*adb tcpip <port> (5555)*`
- conenct device   `*adb connect <device_ip>:5555*`
- check devices connect ` *adb devices*`
- check log  `adb logcat | grep -i <context1>|\<context2>*`
- Debug webview `connect device` and type `chrome://inspect` in chrome browser
- Clear log `adb logcat -c
- Filter log `adb logcat *:F` - for Fatal level
```bash
Log.v(); // Verbose
Log.d(); // Debug
Log.i(); // Info
Log.w(); // Warning
Log.e(); // Error

```