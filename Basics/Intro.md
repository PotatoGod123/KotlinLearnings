# Intro to kotlin

**Basics**
Below is a code snipet with a basic program that prints out a cake :). Big thing to notice is the lack of semi-colons, function reduce to fun, and val instead of declaring type like Java.

``` Kotlin
fun main() {
    //No semi colons at the end of statements as well
    //val is like const, once set can never be chance, var is basically let
    val age = 24
    val layers = 5
    printCakeCandles(age)
    printCakeTop(age)
   printCakeBottom(age,layers)
}
    //Unlike java were the type is first, the name followed by a colon then how arguements are passed
fun printCakeTop(age:Int){
    repeat(age+2){
        print("=")
    }
    println()
}

fun printCakeCandles(age: Int) {
    print(" ")
    repeat(age) {
        print(",")
    }
    
    println() // Print an empty line   
 
    print(" ") // Print the inset of the candles on the cake
    repeat(age) {
        print("|")
    }    
    println()
}

fun printCakeBottom(age:Int, layers:Int){
    repeat(layers){
        repeat(age+2){
            print("@")
        }
        println()
    }
}
```
