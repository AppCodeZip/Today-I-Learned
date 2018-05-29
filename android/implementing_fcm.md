# Implementing Firebase Cloud Messaging (FCM)

### Requirements
* Physical Device to test FCM

### FCM in Android:
* The very first step is setup the firebase, use the following link to setup it: https://firebase.google.com/docs/android/setup
* Now its time to setup FCM, use the following link to setup FCM
https://firebase.google.com/docs/cloud-messaging/android/client

### Server Side:
* Use the following library in node js project for server side code
https://github.com/ToothlessGear/node-gcm

### Notes:
##### There are two types of notifications in FCM
1. Foreground notifications: Can be called as In App Notifications. When the app is currently running, if the notification is recieved that notification is called Forground Notification
2. Background Notifications: When app is not running, if the notification is recieved that notification is called background notification.

To send a notification, the server needs to send the following json.
```json
{
   "to": "the device token"
   "notification":{
     "title":"New Notification!",
     "body":"Test"
   },
   "priority":10
 }
```

this will send notification object to the app and if the app is running its onMessageRecieved will be called. But if the app is in background the onMessageRecieved will not be called. This is very important thing to note here. In FCM the google provides a way to generate the notification by system (not by app) on its own like in iOS.

To solve this issue, if you want onMessageRecieved to be called for both foreground and background notifications just ditch the **"notification"** object in json on server side and use **"data"** instead
```json
{
   "to": "the device token"
   "data":{
     "title":"New Notification!",
     "body":"Test"
   },
   "priority":10
 }
```


### Resources:
* https://firebase.google.com/docs/android/setup
* https://firebase.google.com/docs/cloud-messaging/android/client
* https://github.com/wajahatkarim3/Today-I-Learned/blob/master/firebase/notifs-background.md