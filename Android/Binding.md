# Binding

Your code will need to access all of the UI elements to read the input from the user. You may recall from earlier codelabs that your code needs to find a reference to a View like a Button or TextView before your code can call methods on the View or access its attributes. The Android framework provides a method, findViewById(), that does exactly what you need—given the ID of a View, return a reference to it. This approach works, but as you add more views to your app and the UI becomes more complex, using findViewById() can become cumbersome.

For convenience, Android also provides a feature called view binding. With a little more work up front, view binding makes it much easier and faster to call methods on the views in your UI. You'll need to enable view binding for your app in Gradle, and make some code changes.


To use binding, you first must set it up in your androids app module build.gradle file.

``` build.gradle
android {
    compileSdk 32
    
      ...
    
    buildFeatures {
        viewBinding = true
    }
}
```

Once set up and synced, you can now bind all Views with an ID to and object, for much easier acess and control.

```Kotlin
class MainActivity : AppCompatActivity() {

    lateinit var binding: ActivityMainBinding

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)
    }
}
```

Usage

```Kotlin
// Old way with findViewById()
val myButton: Button = findViewById(R.id.my_button)
myButton.text = "A button"

// Better way with view binding
val myButton: Button = binding.myButton
myButton.text = "A button"

// Best way with view binding and no extra variable
binding.myButton.text = "A button"
```

## Summary

- View binding lets you more easily write code that interacts with the UI elements in your app.
- The Double data type in Kotlin can store a decimal number.
- Use the checkedRadioButtonId attribute of a RadioGroup to find which RadioButton is selected.
- Use NumberFormat.getCurrencyInstance() to get a formatter to use for formatting numbers as currency.
- You can use string parameters like %s to create dynamic strings that can still be easily translated into other languages.
- Testing is important!
- You can use Logcat in Android Studio to troubleshoot problems like the app crashing.
- A stack trace shows a list of methods that were called. This can be useful if the code generates an exception.
- Exceptions indicate a problem that code didn't expect.
- Null means "no value."
- Not all code can handle null values, so be careful using it.
- Use Analyze > Inspect Code for suggestions to improve your code.
