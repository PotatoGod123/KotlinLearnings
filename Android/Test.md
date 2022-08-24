# Android Testing

Android tesitng is seperated in two parts the unit testing(test) and the UI Intrumentation testing(androidTest)

Gradle also lets us add dependencies specifically for unit tests and instrumentation tests. Open up your app level build.gradle file located at app -> build.gradle. In the dependencies section there are three kinds of implementations for dependencies: implementation, testImplementation, and androidTestImplementation.

implementation is for dependencies that will be used in the application itself, testImplementation is for dependencies that are used in unit tests, and androidTestImplementation is for dependencies that are used in instrumentation tests.

## Intrumentation Testing

Add this dependency, this will give you acess to Recycler View testing methods

```
dependencies {
    ...
    androidTestImplementation 'androidx.test.espresso:espresso-contrib:3.4.0'
}
```

Testing

``` Kotlin
package com.example.affirmations

import androidx.recyclerview.widget.RecyclerView
import androidx.test.espresso.Espresso.onView
import androidx.test.espresso.assertion.ViewAssertions.matches
import androidx.test.espresso.contrib.RecyclerViewActions
import androidx.test.espresso.matcher.ViewMatchers.*
import androidx.test.ext.junit.rules.ActivityScenarioRule
import androidx.test.ext.junit.runners.AndroidJUnit4
import org.junit.Rule
import org.junit.Test
import org.junit.runner.RunWith

@RunWith(AndroidJUnit4::class)
class AffirmationsListTest {

    @get:Rule
    val activity = ActivityScenarioRule(MainActivity::class.java)

    @Test
    fun scroll_to_item(){
        onView(withId(R.id.recycler_view)).perform(
            RecyclerViewActions
                .scrollToPosition<RecyclerView.ViewHolder>(9)
        )

        onView(withText(R.string.affirmation10))
            .check(matches(isDisplayed())
            )

    }
}

```

## Unit Testing

```
dependencies {
    ...
    testImplementation 'org.mockito:mockito-core:3.12.4'
}
```  

``` Kotlin
package com.example.affirmations

import android.content.Context
import com.example.affirmations.adapter.ItemAdapter
import com.example.affirmations.model.Affirmation
import org.junit.Assert.assertEquals
import org.junit.Test
import org.junit.runner.RunWith
import org.mockito.Mockito.mock


class AffirmationsAdapterTest {

    private val context = mock(Context::class.java)


    @Test
    fun adapter_size(){
        val data = listOf(
            Affirmation(R.string.affirmation1, R.drawable.image1),
            Affirmation(R.string.affirmation2, R.drawable.image2)
        )

        val adapter = ItemAdapter(context,data)

        assertEquals("ItemAdapter is not the correct size",data.size,adapter.itemCount)
    }


}
```