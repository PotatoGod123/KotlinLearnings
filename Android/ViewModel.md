# ViewModel

- The Android app architecture guidelines recommend separating classes that have different responsibilities and driving the UI from a model.
- A UI controller is a UI-based class like Activity or Fragment. UI controllers should only contain logic that handles UI and operating system interactions; they shouldn't be the source of data to be displayed in the UI. Put that data and any related logic in a ViewModel.
- The ViewModel class stores and manages UI-related data. The ViewModel class allows data to survive configuration changes such as screen rotations.
- ViewModel is one of the recommended Android Architecture Components.

```
// ViewModel
implementation 'androidx.lifecycle:lifecycle-viewmodel-ktx:2.3.1'
```

- LiveData holds data; LiveData is a wrapper that can be used with any data
- LiveData is observable, which means that an observer is notified when the data held by the LiveData object changes.
- LiveData is lifecycle-aware. When you attach an observer to the LiveData, the observer is associated with a LifecycleOwner (usually an Activity or Fragment). The LiveData only updates observers that are in an active lifecycle state such as STARTED or RESUMED. You can read more about LiveData and observation here.
- Apps can listen to the LiveData changes from the layout using Data Binding and binding expressions.
- Binding expressions are written within the layout in the attribute properties (such as android:text) referencing the layout properties.

## LiveData with data binding

Add this plugin and setting to build features

```gradle
plugins {
   id 'kotlin-kapt'
}

buildFeatures {
   dataBinding = true
}
```

### Convert layout file to data binding layout

To convert the layout to a Data Binding layout, wrap the root element in a `<layout>` tag. You'll also have to move the namespace definitions (the attributes that start with `xmlns:`) to the new root element. Add `<data></data>` tags inside `<layout>` tag above the root element. Android Studio offers a handy way to do this automatically: Right-click the root element (ScrollView), select *Show Context Actions > Convert to data binding layout*


```xml
<layout xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"
   xmlns:tools="http://schemas.android.com/tools">

   <data>

   </data>

   <ScrollView
       android:layout_width="match_parent"
       android:layout_height="match_parent">

       <androidx.constraintlayout.widget.ConstraintLayout
         ...
       </androidx.constraintlayout.widget.ConstraintLayout>
   </ScrollView>
</layout>

``` 

Lastly change you binding in your activity/fragement class

```Kotlin
binding = DataBindingUtil.inflate(inflater, R.layout.game_fragment, container, false)

```

- The ViewModel is a part of the Android Architecture Components and the app data saved within the ViewModel is retained during configuration changes. To add a ViewModel to your app, you create a new class and extend it from the ViewModel class.
- Shared ViewModel is used to save the app's data from multiple fragments in a single ViewModel. Multiple fragments in the app will access the shared ViewModel using their activity scope.
- LifecycleOwner is a class that has an Android lifecycle, such as an activity or a fragment.
- LiveData observer observes the changes to the app's data only if the lifecycle owner is in active states (STARTED or RESUMED).
- Listener bindings are lambda expressions that run when an event happens such as an onClick event. They are similar to method references such as textview.setOnClickListener(clickListener) but listener bindings let you run arbitrary data binding expressions.
- The LiveData transformation method(s) provides a way to perform data manipulations on the source LiveData and return a resulting LiveData object.
- Android frameworks provides a class called SimpleDateFormat, a class for formatting and parsing dates in a locale-sensitive manner. It allows for formatting (date → text) and parsing (text → date) dates.
