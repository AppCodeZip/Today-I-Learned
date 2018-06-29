# Debugging App using Adb on Network

### Steps:
* Connect the android phone using cable
* Type the following command to start phone in TCP mode

```
adb tcpip 5555

```
* Now we need to get the IP address of the phone, use the following command for it

```
adb shell "ifconfig | grep -A 1 wlan0 | tail -n 1 | cut -f2 -d: | cut -f1 -d' '"
```
* Finaly, use the following command to connect adb via network with the android phone

```
adb connect 192.168.xxx.xxx:5555
```

