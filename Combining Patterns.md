---
share: true
---

# Combining Patterns

In this section, we explore a novel approach to creating patterns.

## Objects

[Objects](./Objects.md) are like [bags of values and variables](bags%20of%20values%20and%20variables.html). They mark the beginning of another [Paradigm](Paradigm.html) in programming languages and the onset of [Types](Types.md), which we'll delve into later.

Let's examine a simple object creation method: a [Data Class](Data%20Class.html).

```Kotlin
data class ThePressureToCreateExamplesOnTheFly(  
    val reallyLikingARealWorldExampleButItIsReallyComplicated: Int, // An Int is appropriate here. Trust me.    
    val allOfTheEdgeCasesYouDidNotThinkOfButSomeoneInTheCrowdPointedOut: List<String>, // A universally relatable scenario.    
    val numberOfPeopleWhoPolitelyDisagreed: Set<String>, // Yes, I'm keeping track.    
    val numberOfTimesYouDidNotUseATrailingCommaLiveAfterPostingAboutItAllTheTime: Int, // Thankfully, this isn't a live session;)
```  

No apologies for that example. Just a bit of humor after some [JPA](JPA.html) work.

Now, let's consider something more arbitrary. Introducing the box.

```Kotlin  
data class Box(        
    val contents: Set<Any>, // The contents inside the box    
)
// Not impressed? Not exactly how you'd use a box?

// Let's try a different approach:
data class Box(  
    val weight: Int,
    val unitsOfWeight: String,
    val value: Int,
    val unitsOfValue: String,
    val insured: Boolean,
)        

// Still not quite right? One more attempt:

data class Box(  
    var fields: Set<Pair<String, Any>>, // Flexible implementation with any field you want.    
)
```  
  
You might think the issue is with the name 'Box'. It doesn't quite convey what you need. Indeed, naming objects can be one of the two hardest problems in Computer Science, as per [Martin Fowler](Martin%20Fowler.html).

## Naming Objects  

The trick to naming objects is simple: call them what they are.

## Identifying the Essence  

Naming can be tricky, mostly because we often try to name something before fully understanding it. A better approach is to start with the problem we're trying to solve.

## Defining Our Problem  

Consider this: How many boxes can my truck carry?

A good starting point. Next, consider the limitations:

The truck has a maximum capacity of 1500 lbs.

Therefore, we need to know the weight of each box.

```Kotlin   
data class Box(val weight: Int) // Using Int for weight in pounds.

// With a properly named object, we can now use it in functions to solve problems.
fun weight(box: Box): Int { // Given a box, this function returns its weight.
    return box.weight
}
```  
  
Let's derive more utility from the box. Here's a new problem:

How can we distribute the weight among customers who are charged by the pound?

```Kotlin
// This version tracks the box's weight and its owner.

data class Box(  
    val weight: Int,    
    val owner: String,
)    
```  
  
Now we can execute operations like this:

```Kotlin  
val delivery = setOf(  
    Box(5, "Alice"),
    Box(3, "Bob"),        
    Box(4, "Carol"),        
    Box(1, "Dave"),        
    Box(2, "Eve"),    
)  
// Calculating the total weight for Alice.    
val totalWeightForAlice = delivery.filter { it.owner == "Alice" }.sumOf { it.weight }        

// Or create a function to calculate the weight for any owner.
fun totalWeightForOwner(boxes: Set<Box>, owner: String): Int {        
    return boxes.filter { it.owner == owner }.sumOf { it.weight }
}       

// Or calculate combined weights for multiple owners.
fun totalWeightForOwners(boxes: Set<Box>, owners: Set<String>): Int {
    return boxes.filter { it.owner in owners }.sumOf { it.weight }
}
```  
  
## Conclusion  

Objects are a potent tool in defining problems, as they can be tailored to encapsulate various attributes, much like boxes in the real world.

#next [Functions as Values](./Functions%20as%20Values.html)
