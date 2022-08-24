# Kotlin List

## Read-only List

```Kotlin
fun main() {
    val numbers = listOf(1, 2, 3, 4, 5, 6)
    println("List: $numbers")
    println("Size: ${numbers.size}")

    // Access elements of the list
    println("First element: ${numbers[0]}")
    println("Second element: ${numbers[1]}")
    println("Last index: ${numbers.size - 1}")
    println("Last element: ${numbers[numbers.size - 1]}")
    println("First: ${numbers.first()}")
    println("Last: ${numbers.last()}")

    // Use the contains() method
    println("Contains 4? ${numbers.contains(4)}")
    println("Contains 7? ${numbers.contains(7)}")
}
```

Operations on list, all return a new list since list cannot be changed once made

```Kotlin
    val colors:List<String> = listOf("green","orange","blue")
    println("Reversed List: ${colors.reversed()}")
    println("Original List: $colors")
    println("Sorted List: ${colors.sorted()}")
    
    val oddNumbers:List<Int> = listOf(5, 3, 7, 1)
    println("List: $oddNumbers")
    println("Sorted list: ${oddNumbers.sorted()")
  ```

## MutableList

This is how to make and work with a Mutable List

``` Kotlin
val entrees = mutableListOf<String>()
    println("Entrees: $entrees")

    // Add individual items using add()
    println("Add noodles: ${entrees.add("noodles")}")
    println("Entrees: $entrees")
    println("Add spaghetti: ${entrees.add("spaghetti")}")
    println("Entrees: $entrees")

    // Add a list of items using addAll()
    val moreItems = listOf("ravioli", "lasagna", "fettuccine")
    println("Add list: ${entrees.addAll(moreItems)}")
    println("Entrees: $entrees")

    // Remove an item using remove()
    println("Remove spaghetti: ${entrees.remove("spaghetti")}")
    println("Entrees: $entrees")
    println("Remove item that doesn't exist: ${entrees.remove("rice")}")
    println("Entrees: $entrees")

    // Remove an item using removeAt() with an index
    println("Remove first element: ${entrees.removeAt(0)}")
    println("Entrees: $entrees")

    // Clear out the list
    entrees.clear()
    println("Entrees: $entrees")

    // Check if the list is empty
    println("Empty? ${entrees.isEmpty()}")

```

## Example Of both

``` Kotlin
open class Item(val name: String, val price: Int)

class Noodles : Item("Noodles", 10) {
    override fun toString(): String {
        return name
    }
}

class Vegetables(vararg val toppings: String) : Item("Vegetables", 5) {
    override fun toString(): String {
        if (toppings.isEmpty()) {
            return "$name Chef's Choice"
        } else {
            return name + " " + toppings.joinToString()
        }
    }
}

class Order(val orderNumber: Int) {
    private val itemList = mutableListOf<Item>()

    fun addItem(newItem: Item): Order {
        itemList.add(newItem)
        return this
    }

    fun addAll(newItems: List<Item>): Order {
        itemList.addAll(newItems)
        return this
    }

    fun print() {
        println("Order #${orderNumber}")
        var total = 0
        for (item in itemList) {
            println("${item}: $${item.price}")
            total += item.price
        }
        println("Total: $${total}")
    }
}

fun main() {
    val ordersList = mutableListOf<Order>()

    // Add an item to an order
    val order1 = Order(1)
    order1.addItem(Noodles())
    ordersList.add(order1)

    // Add multiple items individually
    val order2 = Order(2)
    order2.addItem(Noodles())
    order2.addItem(Vegetables())
    ordersList.add(order2)

    // Add a list of items at one time
    val order3 = Order(3)
    val items = listOf(Noodles(), Vegetables("Carrots", "Beans", "Celery"))
    order3.addAll(items)
    ordersList.add(order3)

    // Use builder pattern
    val order4 = Order(4)
        .addItem(Noodles())
        .addItem(Vegetables("Cabbage", "Onion"))
    ordersList.add(order4)

    // Create and add order directly
    ordersList.add(
        Order(5)
            .addItem(Noodles())
            .addItem(Noodles())
            .addItem(Vegetables("Spinach"))
    )

    // Print out each order
    for (order in ordersList) {
        order.print()
        println()
    }
}

```

Kotlin provides functionality to help you manage and manipulate collections of data more easily through the Kotlin Standard Library. A collection can be defined as a number of objects of the same data type. There are different basic collection types in Kotlin: lists, sets, and maps. This codelab focused specifically on lists, and you'll learn more about sets and maps in future codelabs.

- A list is an ordered collection of elements of a specific type, such as a list of Strings.
- The index is the integer position that reflects the position of the element (e.g. myList[2]).
- In a list, the first element is at index 0 (e.g. myList[0]), and the last element is at myList.size-1 (e.g. myList[myList.size-1] or myList.last()).
- There are two types of lists: List and MutableList.
- A List is read-only and cannot be modified once it has been initialized. However, you can apply operations such as sorted() and reversed() which return a new list without changing the original.
- A MutableList can be modified after creation such as adding, removing, or modifying elements.
- You can add a list of items to a mutable list using addAll().
- Use a while loop to execute a block of code until the expression evaluates to false and you exit the loop.

``` Kotlin
while (expression) {
// While the expression is true, execute this code block

}

Use a for loop to iterate over all items of a list:
for (item in myList) {

// Execute this code block for each element of the list

}

```

The vararg modifier allows you to pass in a variable number of arguments to a function or constructor.

## Set and Maps

## Set

``` Kotlin
fun main() {
    val numbers = listOf(0, 3, 8, 4, 0, 5, 5, 8, 9, 2)
    println("list:   ${numbers}")
    println("sorted: ${numbers.sorted()}")
    val setOfNumbers = numbers.toSet()
    println("set: ${setOfNumbers}")
    val set1 = setOf(1,2,3)//immutbale set
    val set2 = mutableSetOf(3,2,1)// mutable set
    println("$set1 == $set2: ${set1 == set2}")
    println("contains 7: ${setOfNumbers.contains(7)}")
}

```

## Maps and Labmda

```Kotlin
fun main() {
    val peopleAges = mutableMapOf<String, Int>(
        "Fred" to 30,
        "Ann" to 23
    )
    
    peopleAges.put("Barbara",42)
    peopleAges["Joe"]=51
    peopleAges["Fred"] = 31
    println(peopleAges)
    
    //For each use a special identifier it
//     peopleAges.forEach {print("${it.key} is ${it.value}, ")}
println(peopleAges.map { "${it.key} is ${it.value}" }.joinToString(", ") )
    val filteredNames = peopleAges.filter { it.key.length < 4 }
println(filteredNames)
    
//     val triple: (Int) -> Int = { a: Int -> a * 3 }
    val triple: (Int) -> Int = {it*3}
    println(triple(5))

    val peopleNames = listOf("Fred", "Ann", "Barbara", "Joe")
    println(peopleNames.sorted())

    println(peopleNames.sortedWith{str1: String, str2:String -> str1.length - str2.length})
    
    /**
    Note: If you don't use a lambda parameter in the function body, you can name it _ to make your code more readable and less cluttered. This code has the same behavior.
costOfServiceEditText.setOnKeyListener { view, keyCode, event -> handleKeyEvent(view, keyCode) }
costOfServiceEditText.setOnKeyListener { view, keyCode, _ -> handleKeyEvent(view, keyCode) }
  */
}
```

## Summary

- A collection is a group of related items
- Collections can be mutable or immutable
- Collections can be ordered or unordered
- Collections can require unique items or allow duplicates
- Kotlin supports different kinds of collections including lists, sets, and maps
- Kotlin provides many functions for processing and transforming collections, including forEach, map, filter, sorted, and more.
- A lambda is a function without a name that can be passed as an expression immediately. An example would be { a: Int -> a * 3 }.
- A higher-order function means passing a function to another function, or returning a function from another function.
