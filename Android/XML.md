# XML Basics in Android

```XML
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/cost_of_service"
        android:layout_width="160dp"
        android:layout_height="wrap_content"
        android:hint="@string/cost_of_service"
        android:inputType="numberDecimal"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/service_question"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/how_was_your_service"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/cost_of_service" />

    <RadioGroup
        android:id="@+id/tip_options"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:checkedButton="@id/option_twenty_percent"
        android:orientation="vertical"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/service_question">

        <RadioButton
            android:id="@+id/option_twenty_percent"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/amazing_service" />

        <RadioButton
            android:id="@+id/option_eighteen_percent"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/good_service" />

        <RadioButton
            android:id="@+id/option_fifteen_percent"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/ok_service" />
    </RadioGroup>

    <Switch
        android:id="@+id/round_up_switch"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:checked="true"
        android:text="@string/round_up_tip"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="@id/tip_options"
        app:layout_constraintTop_toBottomOf="@id/tip_options" />

    <Button
        android:id="@+id/calculate_button"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:text="@string/calculate"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/round_up_switch" />

    <TextView
        android:id="@+id/tip_result"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/tip_amount"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@id/calculate_button" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

- The xmlns stands for XML namespace, and each line defines a schema, or vocabulary for attributes related to those words. The android: namespace, for example, marks attributes that are defined by the Android system. All of the attributes in the layout XML begins with one of those namespaces.
- You can add comments to XML, just like you would with Kotlin code. Start ```<!-- and end with -->```
- XML (Extensible Markup Language) is a way of organizing text, made of tags, elements, and attributes.
- Use XML to define the layout of an Android app.
- Use EditText to let the user input or edit text.
- An EditText can have a hint to tell the user what is expected in that field.
- Specify the android:inputType attribute to limit what type of text the user can input into an EditText field.
- Make a list of exclusive options with RadioButtons, grouped with a RadioGroup.
- A RadioGroup can be vertical or horizontal, and you can specify which RadioButton should be selected initially.
- Use a Switch to let the user toggle between two options.
- You can add a label to a Switch without using a separate TextView.
- Each child of a ConstraintLayout needs to have vertical and horizontal constraints.
- Use "start" and "end" constraints to handle both Left to Right (LTR) and Right to Left (RTL) languages.
- Names of the constraint attributes follow the form layout_constraint<Source>_to<Target>Of.
- To make a View as wide as the ConstraintLayout it's in, constrain the start and end to the start and end of the parent, and set the width to 0dp.

## UI, App Icon, Themes

- Place app icon files in the mipmap resource directories.
- Provide different versions of an app icon bitmap image in each density bucket (mdpi, hdpi, xhdpi, xxhdpi, xxxhdpi) for backwards compatibility with older versions of Android.
- Add resource qualifiers onto resource directories to specify resources that should be used on devices with a certain configuration (e.g. v26).
- Vector drawables are Android's implementation of vector graphics. They are defined in XML as a set of points, lines, and curves along with associated color information. Vector drawables can be scaled for any density without loss of quality.
- Adaptive icons were introduced to the Android platform in API 26. They are made up of a foreground and background layer that follow specific requirements, so that your app icon looks high-quality on a range of devices with different OEM masks.
- Use Image Asset Studio in Android Studio to create legacy and adaptive icons for your app.

## Foreground Vector XML

``` XML
<vector xmlns:android="http://schemas.android.com/apk/res/android"
    android:width="108dp"
    android:height="108dp"
    android:viewportWidth="108"
    android:viewportHeight="108">
  <path
      android:pathData="M38.19,65.92L69.32,65.92a1.2,1.2 0,0 0,1.2 -1.2,0.89 0.89,0 0,0 0,-0.23 17,17 0,0 0,-33.25 0,1.18 1.18,0 0,0 0.9,1.42ZM74.53,69.05a0.85,0.85 0,0 0,-0.78 -0.84L34,68.21a0.85,0.85 0,0 0,-0.77 0.84v2.82a0.84,0.84 0,0 0,0.77 0.86L73.78,72.73a0.85,0.85 0,0 0,0.77 -0.86L74.55,70.65C74.55,70.24 74.56,69.58 74.53,69.05ZM52.08,49h3.59a1.86,1.86 0,0 0,0 -3.72L52.08,45.28a1.86,1.86 0,0 0,0 3.72ZM53.87,39.81a1.19,1.19 0,0 0,1.19 -1.19L55.06,32.87a1.19,1.19 0,0 0,-2.38 0v5.71a1.19,1.19 0,0 0,1.19 1.19h0ZM61.69,41l4.62,-3.35a1.19,1.19 0,1 0,-1.4 -1.93L60.29,39A1.2,1.2 0,0 0,60 40.67a1.18,1.18 0,0 0,1.66 0.26ZM41.69,37.65L46.31,41a1.2,1.2 0,0 0,1.35 -2L43,35.66a1.19,1.19 0,0 0,-1.66 0.26,1.2 1.2,0 0,0 0.3,1.67Z"
      android:fillColor="#FFFFFF"/>
</vector>
```

## Background Vector XML

```XML
<vector xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:aapt="http://schemas.android.com/aapt"
    android:width="108dp"
    android:height="108dp"
    android:viewportWidth="108"
    android:viewportHeight="108">
  <path
      android:pathData="M0,0h108v108h-108z">
    <aapt:attr name="android:fillColor">
      <gradient
          android:startY="-1.0078"
          android:startX="54"
          android:endY="106.9922"
          android:endX="54"
          android:type="linear">
        <item android:offset="0" android:color="#FF12C26D"/>
        <item android:offset="1" android:color="#FF0F9453"/>
      </gradient>
    </aapt:attr>
  </path>
</vector>
```

## Support

Note that support for vector drawables on the Android platform wasn't added until Android 5.0 (API level 21).To make your app work on these older versions of Android (known as backwards compatibility), add the vectorDrawables element to your app's build.gradle file. This enables you to use vector drawables on versions of the platform less than API 21, versus converting to PNGs when the project is built.

app/build.gradle

``` Gradle
android {
  defaultConfig {
    ...
    vectorDrawables.useSupportLibrary = true
   }
   ...
}
```
