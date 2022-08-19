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

## Class And Inherintance

```Kotlin
/**
* Program that implements classes for different kinds of dwellings.
* Shows how to:
* Create class hierarchy, variables and functions with inheritance,
* abstract class, overriding, and private vs. public variables.
*/


import kotlin.math.PI
import kotlin.math.sqrt

fun main() {
    val squareCabin = SquareCabin(6,50.0)
    val roundHut = RoundHut(3, 10.0)
    val roundTower = RoundTower(4, 15.5)
    
   with(squareCabin){
        println("\nSquare Cabin\n===========")
        println("Capacity: ${capacity}")
        println("Material: ${buildingMaterial}")
        println("Has room? ${hasRoom()}")
        println("Floor area: ${floorArea()}")
   }
   
   with(roundHut){
        println("\nRound Hut\n=========")
    println("Material: ${buildingMaterial}")
    println("Capacity: ${capacity}")
    println("Has room? ${hasRoom()}")
        getRoom()
        println("Has room? ${hasRoom()}")
        getRoom()
    println("Floor area: ${floorArea()}")
        println("Carpet Length: ${calculateMaxCarpetLength()}")

   }
   
   with(roundTower){
       println("\nRound Tower\n=========")
       println("Material: ${buildingMaterial}")
       println("Capacity: ${capacity}")
       println("Has room? ${hasRoom()}")
       println("Floor area: ${floorArea()}")
       println("Carpet Length: ${calculateMaxCarpetLength()}")
   }
}


/**
* Defines properties common to all dwellings.
* All dwellings have floorspace,
* but its calculation is specific to the subclass.
* Checking and getting a room are implemented here
* because they are the same for all Dwelling subclasses.
*
* @param residents Current number of residents
*/
abstract class Dwelling(private var residents: Int){
    abstract val buildingMaterial: String
    abstract val capacity: Int
    
     /**
    * Compares the capacity to the number of residents and
    * if capacity is larger than number of residents,
    * add resident by increasing the number of residents.
    * Print the result.
    */
    fun hasRoom(): Boolean{
        return residents < capacity
    }
    
     /**
    * Checks whether there is room for another resident.
    *
    * @return true if room available, false otherwise
    */
    fun getRoom(){
        if(hasRoom()){
            residents++
            println("You got a room!")
        } else {
            println("Sorry, at capacity and no rooms left.")
        }
    }
    
     /**
    * Calculates the floor area of the dwelling.
    * Implemented by subclasses where shape is determined.
    *
    * @return floor area
    */
    abstract fun floorArea(): Double
    
}

/**
* A square cabin dwelling.
*
*  @param residents Current number of residents
*  @param length Length
*/
class SquareCabin(residents: Int,
                  val length: Double): Dwelling(residents){
    override val buildingMaterial = "Wood"
    override val capacity = 6
    
     /**
    * Calculates floor area for a square dwelling.
    *
    * @return floor area
    */
    override fun floorArea(): Double {
        return length * length
    }
}

/**
* Dwelling with a circular floorspace
*
* @param residents Current number of residents
* @param radius Radius
*/
open class RoundHut(
       residents: Int, val radius: Double) : Dwelling(residents) {

   override val buildingMaterial = "Straw"
   override val capacity = 4

   /**
    * Calculates floor area for a round dwelling.
    *
    * @return floor area
    */
   override fun floorArea(): Double {
       return PI * radius * radius
   }

   /**
    *  Calculates the max length for a square carpet
    *  that fits the circular floor.
    *
    * @return length of square carpet
    */
    fun calculateMaxCarpetLength(): Double {
        return sqrt(2.0) * radius
    }



}

/**
* Round tower with multiple stories.
*
* @param residents Current number of residents
* @param radius Radius
* @param floors Number of stories
*/
class RoundTower(
       residents: Int,
       radius: Double,
       val floors: Int = 2) : RoundHut(residents, radius) {

   override val buildingMaterial = "Stone"

   // Capacity depends on the number of floors.
   override val capacity = floors * 4

   /**
    * Calculates the total floor area for a tower dwelling
    * with multiple stories.
    *
    * @return floor area
    */
   override fun floorArea(): Double {
       return super.floorArea() * floors
   }
}
```

- Create a class hierarchy, that is a tree of classes where children inherit functionality from parent classes. Properties and functions are inherited by subclasses.
- Create an abstract class where some functionality is left to be implemented by its subclasses. An abstract class can therefore not be instantiated.
- Create subclasses of an abstract class.
- Use override keyword to override properties and functions in subclasses.
- Use the super keyword to reference functions and properties in the parent class.
- Make a class open so that it can be subclassed.
- Make a property private, so it can only be used inside the class.
- Use the with construct to make multiple calls on the same object instance.
Import functionality from the kotlin.math library
