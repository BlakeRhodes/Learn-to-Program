---
share: true
---


# Combining Patterns  
  
This time we are going to look at a new way to make patterns.  
  
## Objects
  
[Objects](./Objects.md) are [bags of values and variables](bags%20of%20values%20and%20variables.html). They are the beginning of another [Paradigm](Paradigm.html) of language.   
They are also the beginning of types. We will cover types later.  
  
Let's take a look at a simple way to make an object, a [Data Class](Data%20Class.html).  
  
```Kotlin
data class ThePreasureToCreateExamplesOnTheFly(  
    val reallyLikingARealWorldExampleButItIsReallyComplicated: Int, // Because an Int makes sense here. Trust me.    
    val allOfTheEdgeCasesYouDidNotThinkOfButSomeOneInTheCrowdPointedOUt: List<String>, // I think we can all agree on that.    
    val numberOfPeopleWhoPolityDisagreed: Set<String>, // Cause I am taking names.    
    val numberOfTimesYouDidNotUseATrailingCommaLiveAfterPostingAboutItAllTheTime: Int, // Lucky for me this isn't live.)  
  
```  
  
I am not sorry about that. I just got done writing some [JPA](JPA.html) and I had to get it out of my system.  
  
Now for something even more arbitrary. Presenting, the box.  
  
```Kotlin  
data class Box(        
    val contents: Set<Any>, // This is what is inside the box    
)
// I see, you are unimpressed.  
// Not how you want to use a box huh?

//Let's try this  
data class Box(  
    val weight: Int,
    val unitsOfWeight: String,
    val value: Int,
    val unitsOfValue: String,
    val insured: Boolean,
)        

// Ouch, okay still not the box you are looking for, one more try.  

data class Box(  
        var fields: Set<Pair<String, Any>>, // Now you can have any implementation you want.    
)
```  
  
What you might be thinking is that Box, the name, is the problem. It doesn't describe what you need.  
Naming objects what a mess. This is one of two hard problems in Computer Science according to [Martin Fowler](Martin%20Fowler.html).  
  
## Naming Objects  
  
Naming objects is simple. Call things what they are.  
  
## Calling things what they are.  
  
This is a tricky one, but that is because we are trying to name something without knowing what it is.  
We need to change our approach here, instead of starting with a name, let's start with the problem we are trying to solve.  
  
## Our Problem  
  
How many boxes can my truck carry?  
  
Great start, the next step is to think about the limitations we are facing.  
  
The truck can only carry 1500lbs.  
  
So what we need to know about each box is how much it weighs.  
  
```Kotlin   
data class Box(val weight:Int) // Going with Int, because weight limit is in pounds.  
  
//Now that we have an object with an name, we can use it in functions to solve problems.  
fun weight(box:Box):Int { // Given a box, the function will tell you what it weighs.  
    return box.weight
}
```  
  
Let's get some more use out the box. We will need a new problem.  
  
Customers get charged by the pound, how can we spilt the weight between the customers.  
  
```Kotlin
// We are going to keep track of who owns the box and how much it weighs  
  
data class Box(  
    val weight: Int,    
    val owner: String,
)    
```  
  
Now we can do things like this.  
  
```Kotlin  
val delivery = setOf(  
	Box(5, "Alice"),
    Box(3, "Bob"),        
    Box(4, "Carol"),        
    Box(1, "Dave"),        
    Box(2, "Eve"),    
)  
// Find the weight for Alice.    
val totalWeightForAlice = delivery.filter { it.owner == "Alice" }.sumOf { it.weight }        

// Or you could make a function that finds the weight for any user.  
fun totalWeightForOwner(boxes: Set<Box>, owner: String): Int {        
	return boxes.filter { it.owner == owner }.sumOf { it.weight }
}       

// Or combine owners.  
fun totalWeightForOwners(boxes: Set<Box>, owners: Set<String>): Int {
	return boxes.filter { it.owner in owners }.sumOf { it.weight }
}
```  
  
## Conclusion  
  
Objects are powerful ways to define problems, because they can act like boxes.

#next [Functions as Values](./Functions%20as%20Values.html)