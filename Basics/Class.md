# Class and function

```Kotlin
    //val diceRange: IntRange = 1..6
    val diceRange = 1..6
    val randomNumber = diceRange.random()
    println("Random number: ${randomNumber}")
```

## Summary

- Call the random() function on an IntRange to generate a random number: (1..6).random()
- Classes are like a blueprint of an object. They can have properties and behaviors, implemented as variables and functions.
- An instance of a class represents an object, often a physical object, such as a dice. You can call the actions on the object and change its attributes.
- You can supply values to a class when you create an instance. For example: class Dice(val numSides: Int) and then create an instance with Dice(6).
- Functions can return something. Specify the data type to be returned in the function definition, and use a return statement in the function body to return something. For example: fun example(): Int { return 5 }

```Kotlin
fun main() {
 val myFirstDice = Dice(6) 
    println("Your roll is ${myFirstDice.roll()} from a ${myFirstDice.numSides} sided dice!")
   
    val mySecondDice = Dice(20)
    println("Your roll is ${mySecondDice.roll()} from a ${mySecondDice.numSides} sided dice!")
}

class Dice(val numSides: Int) {
    
    fun roll():Int {
        return (1..numSides).random()
    }
}
```

- Add a Button in an Android app using the Layout Editor.
- Modify the MainActivity.kt class to add interactive behavior to the app.
- Pop up a Toast message as a temporary solution to verify you're on the right track.
- Set an on-click listener for a Button using setOnClickListener() to add behavior for when a Button is clicked.
- When the app is running, you can update the screen by calling methods on the TextView, Button, or other UI elements in the layout.
- Comment your code to help other people who are reading your code understand what your approach was.
- Reformat your code and clean up your code.

```Kotlin
fun main() {
    val myFirstDice = Dice(6)
    val rollResult = myFirstDice.roll()
    val luckyNumber = 4

   when (rollResult) {
       luckyNumber -> println("You win")
       1 -> println("So sorry! You rolled a 1. Try again!")
       2 -> println("Sadly, you rolled a 2. Try again!")
       3 -> println("Unfortunately, you rolled a 3. Try again!")
       5 -> println("Don't cry! You rolled a 5. Try again!")
       6 -> println("Apologies! You rolled a 6. Try again!")
       
   }
}

class Dice (val numSides: Int) {

    fun roll(): Int {
        return (1..numSides).random()
    }
}
```

- Use an if statement to set a condition for executing some instructions. For example, if the user rolls the lucky number, print a winning message.
- The Boolean data type has values of true and false and can be used for decision making.
- Compare values using operators such as greater than (>), less than (<), and equal to (==).
- Use a chain of else if statements to set multiple conditions. For example, print a different message for each possible dice roll.
- Use an else statement at the end of a chain of conditions to catch any cases that may not be covered explicitly. If you cover the cases for 6-sided dice, an else statement would catch the 7 and 8 numbers rolled with an 8-sided dice.
- Use a when statement as a compact form of executing code based on comparing a value.
