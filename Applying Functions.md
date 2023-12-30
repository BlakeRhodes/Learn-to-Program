# Applying Functions  
  
Let's take a closer look at how you can use [[Functions]], and take a peek at some common function patterns.  
As we go through this, remember that you can use [[Objects]] in function.  
  
## [[Collections]] and Functions  
  
Let's write a function that already exists.  
Why? We want to learn how to program.  
  
```Kotlin  
// Let's write the map function. We will have to give a different name, so let's call it newMap  
  
// This is a generic function, so we need placeholders. Usually this is a single letter  
// but for clarity we are going to use Type as incoming, and NewType as the outgoing.  
// Of course they could be the same, but doing this way get some more flexiblity  
  
fun <Type,NewType> List<Type>.newMap(transform: (Type) -> NewType): List<NewType> {  
    // Here we create a new list    
    val result = mutableListOf<NewType>()        
    
    // Then we change each item in the original collection to the NewType,  
    // then adds it to the new list.    
    this.forEach {
		result.add(transform(it))
	}
	    
	return result
}  
  
val stringList = listOf("1","2","3")  
  
// A quick note, in kotlin you have this nice short cut of being able to use a codeblock like this.  
val intList = stringList.newMap { it.toInt() }  
  
// Other languages you might have to do something like this.  
  
val intList2 = stringList.newMap(String::toInt)  
  
// Not the worst, but our focus is on reability.  
  
```  
  
Nice right? Yeah!  
Now [[Map]] already exists, but so do many other functions that work on collections.  
Let's take a closer look at collections and some cool tricks with functions.  
  
```Kotlin  
// This is a generic class that can hold a value of any given type, "Type", or null.

class Maybe<Type>(val value: Type? = null) { // Maybe this has a value, or maybe it is nul  
        
	// Bind will transform the type of the Maybe, to something else.  
    fun <NewType> bind(function: (Type) -> Maybe<NewType>): Maybe<NewType> {        // This could also just not change the type of the value if function does change its type 
	    return if (value != null) {            
		    function(value)
		} else {            // If they give us a null value, then just return a differently typed null.            
			Maybe<NewType>() // We don't have to pass anything, because null is the default value        
		}    
	}
}  
  
// This is an extention method that add an easy way to turn any type into a Maybe  
// Extention methods add a function to all objects of the type it extends.  
fun <Type> Type.maybe(): Maybe<Type> {  
    return Maybe(this)}  
  
// Let's use our Maybe  
  
fun someTimesFails(): String? {  
    return null // we lied, it always fails and returns null. AHAHAHAAHAHA!}  
  
val maybeString = someTimesFails().maybe()  
  
// Now we can do things like this  
maybeString.bind{ (it?.toInt()).maybe() }  
  
// Or  
maybeString.bind{  
        var number:Int? = it?.toInt()        
		number = if(number != null) number + 1 else null
        return number.toString().maybe()    
}  
  
```  
  
And for our next trick . . .  
  
````Kotlin  
// Let sort these  
  
val strings = listOf("one", "two", "three")  
val numbers = listOf(4, 5, 6)  
  
val ohBoy = listOf(strings, numbers)  
    val sorted = ohBoy.flatMap {   
    it.map { it.toString() }  
}.sorted()  
  
  
//Oh that isn't what you wanted?  
  
val easy = listOf(  
    numbers,
    strings.map(String::toInt)
)  
  
val betterSorted = easy.flatten().sorted()  
  
````  
  
## Conclusion  
  
So, functions can make loops using some of that higher order magic.

