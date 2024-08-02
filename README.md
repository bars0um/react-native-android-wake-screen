Forked from [https://github.com/witPranav/react-native-android-wake-screen]([url](https://github.com/witPranav/react-native-android-wake-screen))

Note: purpose is simply to patch the native component that acquires the lock to wake the screen and make it release the lock again right after to avoid a warning from power management:

```
onEndOfErrorDumpThread: data_app_wtf Process: com.YOURAPP
Flags: 0x38883e44
Package: com.YOURAPP v1 (1.0)
Foreground: Yes
Subject: PowerManager
Build: Lenovo/LenovoTB-7304I/TB-7304I:7.0/NRD90M/TB-7304I_S000049_180828_ROW:user/release-keys

android.util.Log$TerribleFailure: WakeLock finalized while still held: yourApp:tag
	at android.util.Log.wtf(Log.java:295)
	at android.util.Log.wtf(Log.java:260)
	at android.os.PowerManager$WakeLock.finalize(PowerManager.java:1233)
	at java.lang.Daemons$FinalizerDaemon.doFinalize(Daemons.java:223)
	at java.lang.Daemons$FinalizerDaemon.run(Daemons.java:210)
	at java.lang.Thread.run(Thread.java:761)
 2201
```

# react-native-android-wake-screen

## Getting started

`$ npm install react-native-android-wake-screen --save`

### Mostly automatic installation

`$ react-native link react-native-android-wake-screen`

## Usage
This module helps turn the screen display on from within a headless function.

Add the following inside the project manifest (android/app/src/main/AndroidManifest.xml):
```xml
<uses-permission android:name="android.permission.WAKE_LOCK" />   //Add this line
<application
      android:name=".MainApplication"
      android:label="@string/app_name"
      android:icon="@mipmap/ic_launcher"
      android:roundIcon="@mipmap/ic_launcher_round"
      android:allowBackup="false"
      android:turnScreenOn="true"                          // Add this line
      android:theme="@style/AppTheme">
```

```javascript
import AndroidWakeScreen from 'react-native-android-wake-screen';

//inside your headless function
const MyHeadlessFunction = async () => {
  AndroidWakeScreen.wakeScreen();
};
```


