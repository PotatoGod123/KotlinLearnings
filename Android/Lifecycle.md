# Android Lifecycle and methods

## Activity lifecycle

- The activity lifecycle is a set of states through which an activity migrates. The activity lifecycle begins when the activity is first created and ends when the activity is destroyed.
- As the user navigates between activities and inside and outside of your app, each activity moves between states in the activity lifecycle.
- Each state in the activity lifecycle has a corresponding callback method you can override in your Activity class. The core set of lifecycle methods are: onCreate()onStart()onPause()onRestart()onResume()onStop()onDestroy()
- To add behavior that occurs when your activity transitions into a lifecycle state, override the state's callback method.
- To add skeleton override methods to your classes in Android Studio, select Code > Override Methods or press Control+o.

## Logging with Log

- The Android logging API, and specifically the Log class, enables you to write short messages that are displayed in the Logcat within Android Studio.
- Use Log.d() to write a debug message. This method takes two arguments: the log tag, typically the name of the class, and the log message, a short string.
- Use the Logcat window in Android Studio to view the system logs, including the messages you write.

## Preserving activity state

- When your app goes into the background, just after onStop() is called, app data can be saved to a bundle. Some app data, such as the contents of an EditText, is automatically saved for you.
- The bundle is an instance of Bundle, which is a collection of keys and values. The keys are always strings.
- Use the onSaveInstanceState() callback to save other data to the bundle that you want to retain, even if the app was automatically shut down. To put data into the bundle, use the bundle methods that start with put, such as putInt().
- You can get data back out of the bundle in the onRestoreInstanceState() method, or more commonly in onCreate(). The onCreate() method has a savedInstanceState parameter that holds the bundle.
- If the savedInstanceState variable is null, the activity was started without a state bundle and there is no state data to retrieve.
- To retrieve data from the bundle with a key, use the Bundle methods that start with get, such as getInt().

## Configuration changes

- A configuration change happens when the state of the device changes so radically that the easiest way for the system to resolve the change is to destroy and rebuild the activity.
- The most common example of a configuration change is when the user rotates the device from portrait to landscape mode, or from landscape to portrait mode. A configuration change can also occur when the device language changes or a hardware keyboard is plugged in.
- When a configuration change occurs, Android invokes all the activity lifecycle's shutdown callbacks. Then Android restarts the activity from scratch, running all the lifecycle startup callbacks.
- When Android shuts down an app because of a configuration change, it restarts the activity with the state bundle that is available to onCreate().
- As with process shutdown, save your app's state to the bundle in onSaveInstanceState().
