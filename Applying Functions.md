---
share: true
---

# Applying Functions  

In this section, we'll delve deeper into using [Functions](./Functions.md) and explore some common patterns. Remember, functions can seamlessly interact with [Objects](./Objects.md).

## Collections and Functions  

Let's recreate a function that already exists, to deepen our understanding of programming.

```Kotlin  
// We'll write a version of the map function and call it newMap.

// We use generic types here, labeled as Type and NewType for incoming and outgoing data respectively.
// This approach provides flexibility.

fun <Type, NewType> List<Type>.newMap(transform: (Type) -> NewType): List<NewType> {  
    val result = mutableListOf<NewType>() // Creating a new list
    
    // Transforming each item in the original list and adding it to the new list
    this.forEach {
        result.add(transform(it))
    }
    
    return result.toList() // Return inmutable version
}  
  
val stringList = listOf("1", "2", "3")  

// Kotlin allows for a shorthand approach using a code block.
val intList = stringList.newMap { it.toInt() }  

// In other languages, it might look like this:
val intList2 = stringList.newMap(String::toInt)  

// Our focus here is on readability.
```  

Pretty neat, right? The map function already exists, but many other functions also operate on [Collections](Collections.md). Let's explore some of these functions and their interactions with collections.

```Kotlin  
// The Maybe class can hold a value of any type, "Type", or it can be null.

class Maybe<Type>(val value: Type? = null) { // It may have a value, or it might be null
        
    // Bind transforms the Maybe's type to something else.
    fun <NewType> bind(function: (Type) -> Maybe<NewType>): Maybe<NewType> {
        // If the value is non-null, apply the function
        return if (value != null) {
            function(value)
        } else {            
            Maybe<NewType>() // Returns a null of a different type if the original value is null
        }    
    }
}  
  
// Extension method to convert any type into a Maybe
fun <Type> Type.maybe(): Maybe<Type> = Maybe(this)  
  
// Using our Maybe
fun sometimesFails(): String? = null // This always fails, returning null

val maybeString = sometimesFails().maybe()  

// Now we can chain operations like this
maybeString.bind { (it?.toInt()).maybe() }  

// Or like this
maybeString.bind {  
    var number: Int? = it?.toInt()        
    number = number?.plus(1)
    number.toString().maybe()    
}  
```  

And now for our next demonstration:

```Kotlin  
// Sorting a mix of strings and numbers

val strings = listOf("one", "two", "three")  
val numbers = listOf(4, 5, 6)  

val mixedList = listOf(strings, numbers)  
val sorted = mixedList.flatMap { 
    it.map { it.toString() }
}.sorted()

// Not what you expected?

val combined = listOf(
    numbers,
    strings.map(String::toInt)
)

val betterSorted = combined.flatten().sorted()
```  

## Conclusion  

Functions can effectively replace loops using higher-order functionalities, offering a more expressive and flexible approach to programming.

#next [Bags of Objects and Functions](Bags%20of%20Objects%20and%20Functions.html)