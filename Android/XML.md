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
