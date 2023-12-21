# Combining Patterns

Last time you saw functions, and how you could use higher order functions to combine patterns.
This time we are going to look at a new way to make patterns.

## Objects

Objects are bags of values and variables. They are the beginning of another paradigm of language. 
They are also the beginning of types. We will cover types later.

Let's take a look at a simple way to make an object, a data class.

```Kotlin

data class ThePreasureToCreateExamplesOnTheFly(
    val reallyLikingARealWorldExampleButItIsReallyComplicated: Int, // Because an Int makes sense here. Trust me.
    val allOfTheEdgeCasesYouDidNotThinkOfButSomeOneInTheCrowdPointedOUt: List<String>, // I think we can all agree on that.
    val numberOfPeopleWhoPolityDisagreed: Set<String>, // Cause I am taking names.
    val numberOfTimesYouDidNotUseATrailingCommaLiveAfterPostingAboutItAllTheTime: Int, // Lucky for me this isn't live.
)

```

I am not sorry about that. I just got done writing some JPA and I had to get it out of my system.

No for something even more arbitrary. Presenting, the box.

```Kotlin
    data class Box(
        val contents: Set<Any>, // This is what is inside the box
    )
    
    // I see, you are unimpressed.
    
    data class Container(
        val weight: Int,
        val unitsOfWeight: String,
        val value: Int,
        val unitsOfValue: String,
        val insured: Boolean,
    )
    
    // How about that?
    // Fine.
    
    // Let's talk about POJOs.
    // Aka, POKOs, POCOs, POROs, POPOs
    // Let's call thm PO*Os, pronounced Poe-Star-Ohs.
    // Everyone knows what a a Poestarohs is, right? Right?

```

Naming objects what a mess. This is one of two hard problems in Computer Science according to Martin Fowler.

## Naming Objects

Naming objects is simple. Call things what they are.

## Calling things what they are.

This is a tricky one, but let's just say the box is the problem.

So what to call it is the answer.

Let's start with the problem.

How many boxes can my truck carry?

Now, let's write down the limitations.

I can only carry 1500 pounds.

So what we need to know about each box is how many we need?
How much each box weighs.

```Kotlin

data class Box(val weight:Int) // Going with Int, because weight limit is in pounds.

//Now that we have an object with an name, we can use it in functions to solve problems.
fun weight(box:Box):Int { // Given a box, the function will tell you what it weighs.
    return box.weight
}
```

So, now you have two ways to use a Box. In a function, and you can just weigh the box yourself with by getting the 
weight field of the box.

Let's use the box, to show a relationship. We will need a new problem.

Customers get charged by the pound, so I need to know how to spilt the weight between the customers.

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

Objects are powerful ways to define problems. I will leave it to you to answer the hard problems.