# Loginator
The best way to display your logs

Loginator is a high performance log viewer that shows you logs in realtime:

* Chainsaw (nlog, log4net, log4j, etc.)
* Logcat (Android)

He it's how it looks like:

![ScreenShot](https://cloud.githubusercontent.com/assets/14138808/9740037/05d838c2-5653-11e5-83e4-9876122489cc.png)

## Some cool features include

* Limit the number of logs held in memory
* Show details of a log like exception, namespace, etc.
* Show/Hide logs based on application
* Show/Hide logs based on namespace
* Filter output based on log level and expressions
* Configure log type and port

## TODO (from most to least important)

* Other data sources (database, file, etc.) via polling
* Code refactoring (expressions, receiver)

## Chainsaw logging

NLog (.net):

In your logging app add a new target:
```
<target xsi:type="Chainsaw" name="chainsaw" address="udp://127.0.0.1:7071" />
```
and add the logger
```
<logger name="*" minlevel="Trace" writeTo="chainsaw" />
```

## Logcat logging

1. Connect your Android device to your PC or Mac via USB
2. Find you device ID: /[path-to]/Android/sdk/platform-tools/adb devices
3. Forward the logcat output to your machine with Loginator running

Mac:

cat <(/[path-to]/Android/sdk/platform-tools/adb -s [your-device-id] logcat) | nc -u 192.168.1.5 7071

## Tested with

* Chainsaw: NLog (.net), same machine (Windows 10)
* Logcat: Android logcat (default output format), remote machine (Android: Mac OSx, Loginator: Windows 10)
