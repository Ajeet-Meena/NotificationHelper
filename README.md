# NotificationHelper
Generate Custom Notification Easily.

![Example1] (http://imgur.com/AMxg2eh)
![Ecample2] (http://imgur.com/5x4y34S)


# Instructions

The main objective of this helper class is to generate notification. It removes the burden of generating notification from G.C.M push services. By sending NotificationInfo object from push services custom notification can be easily generated.

**Example of using NotificationInfo Object**

```java
// Initialize Notification Info. Notification Info contains all possible informatin of notificaiton.
NotificationInfo notificationInfo = new NotificationInfo();
// Notification Title text.
notificationInfo.setContentTitle("title");
// Notification Content text.
notificationInfo.setContentText("content");
// Notification Large Icon Url.
notificationInfo.setLargeIcon("http://iconshow.me/media/images/ui/ios7-icons/png/512/contact.png");
// Content Image Url to display.
notificationInfo.setContentImageUrl("http://media02.hongkiat.com/ww-flower-wallpapers/sunflower-world.jpg");
// Positive Button Text
notificationInfo.setPositiveButtonText("Positive Button");
// Negative Button Text
notificationInfo.setNegativeButtonText("Negative Button");
// Notification Actions.
ArrayList<NotificationInfo.NotificationAction> notificationActions = new ArrayList<>();
// Notification Content Action
notificationActions.add(new NotificationInfo.NotificationAction(ActionExecuter.ActionName.OPEN_CONTENT_ACTIVITY,"Extra"));
// Notification Positive Button Action
notificationActions.add(new NotificationInfo.NotificationAction(ActionExecuter.ActionName.OPEN_POSITIVE_BUTTON_ACTIVITY,"Extra"));
// Notification Negative Button Action
notificationActions.add(new NotificationInfo.NotificationAction(ActionExecuter.ActionName.OPEN_NEGATIVE_BUTTON_ACTIVITY,"Extra"));
// Set Actions to Notification Object
notificationInfo.setNotificationActions(notificationActions);
// Set notification Id. Same Id change content of previously generated notification of same id. Diffrent id will generate a new one.
notificationInfo.setNotificationId(1);
// Finally with help of NotificationHelper show the notification.
new NotificationHelper(this,notificationInfo).show();
```

** ActionExecuter** 

To handle notification content, positive button, negative button click we have to follow ActionExecuter pattern. As we cannot pass intent through notificationInfo object, ActionExecuter is only way to execute action such as opening a activity or fragment. Follow the ActionExecuter.java.

**Showing Progress Bar**

NotificationHepler can also be used to show progress on notifications. This can be used to show upload or download progress of a file as same way that play store show download progress. 

```java
NotificationInfo notificationInfo = new NotificationInfo();
// Set notification Title text.
notificationInfo.setContentTitle("title");
// Set notification Content text.
notificationInfo.setContentText("content");
// Set notification Type progress.
notificationInfo.setType(NotificationInfo.TYPE_PROGRESS);
// Set notification id.
notificationInfo.setNotificationId(1);
// Init NotificationHelper
NotificationHelper notificationHelper = new NotificationHelper(this,notificationInfo);
// Set Progress to display
notificationHelper.setProgress(20);
// Finally show progress as 20
notificationHelper.show();
```
