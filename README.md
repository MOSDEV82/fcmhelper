# fcmhelper
Firebase Cloud Messenging Helper Library - Helps you to send fcm notifications or data to your Android projects

# Including this library
* Create a packagename org.mosdev.fcmhelper in your project (Or change the package in the FCMHelper.java file)
* Add the file to your project
* Enter your serverkey (get from https://console.firebase.google.com) to the variable FCM_SERVER_KEY

Hint, you need the GSON and APACHE HTTPCLIENT libraries. I use the following from maven:
* com.google.code.gson:gson:2.72
* org.apache.httpcomponents:httpclient:4.5.22

# Using this library
* Get an instance of FCMHelper with FCMHelper.getInstance()

# Sending notifications and data

For both, notifications and data, you need a JsonObject. You put some Key-Value-Pairs in it. For example:
JsonObject dataObject = new JsonObject();
dataObject.addProperty("KEY", "VALUE");  // See GSON-Reference

the same for notification object.
JsonObject notificationObject = new JsonObject();
notificationObject.addProperty("KEY", "VALUE");  // See GSON-Reference

Hint: See Google documentation, to learn about notification and data. Data will not ever recieved, when app is in background!

To send data or/and notification use
FCMHelper fcm = FCMHelper.getInstance();

// For Example to send data only

*fcm.sendData(FCMHelper.TYPE_TO, RECIPIENT, dataObject); // RECIPIENT is the token of the device, or device group, or a topic. 

Hint: You can use FCMHelper.TYPE_CONDITION for conditions

// For Example to send notification only
fcm.sendNotification(FCMHelper.TYPE_TO, RECIPIENT, notificationObject);

// For Example to send notification and data
fcm.sendNotificationAndData(FCMHelper.TYPE_TO, RECIPIENT, notificationObject, dataObject);

FCMHelper provides some topics methods
// For example
fcm.sendTopicData("TOPICNAME", dataObject);

For more information see: https://firebase.google.com/docs/cloud-messaging/
