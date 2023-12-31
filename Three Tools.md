---
share: true
---

# Three Tools  

In programming, you essentially have three tools at your disposal. While you may import or build more, let's initially focus on these three key tools:

1. Take Action
2. Make Decisions
3. Repeat Actions

## Take Action  

Writing a program involves specifying actions for it to perform. Let's start with a classic example:

```Kotlin  
// The action here is printing out a message.  
// These lines are comments, which don't affect the program's operation,  
// but they're useful for explanation.

print("Hello World!")  
```  

There's a wide range of actions you can take, and we'll cover the most commonly used ones. But remember, this is just the tip of the iceberg.

Now, let's perform multiple actions:

```Kotlin  
val one = 1 // Assigning the value 1 to a variable named 'one'.  
val two = 2 // This is another assignment.  
val sum = one + two // Adding 'one' and 'two', then assigning the result to 'sum'.

print(sum) // Printing the value of 'sum'.  
```  

Great, now you're familiar with taking action!

## Make Decisions  

This is also known as branching or conditional logic. It involves evaluating a condition and then acting based on the result.

```Kotlin  
val one = 1  
val two = 2  
val three = 3 // These variables should be familiar.

// A quick aside:
//         _ '==' means equals, different from '=' which is used for assignment.
//         |     This is something programmers often discuss.
//         V  
val message = if(one + two == three) "It is true" else "It is false"

print(message) // The if statement created a branch with two possible outcomes.
```  

Try reading it aloud for clarity: "Value 'message' is assigned, if 'one' plus 'two' equals 'three', then it is true. Else, it is false."

```Kotlin  
// Let's explore another example.

val value = Random.nextInt(1,6) // Generates a pseudo-random integer between 1 and 6, like rolling a die.

if(value > 3) { // Executes if 'value' is 4, 5, or 6.
    print("$value is greater than three") // Using string interpolation to display the value.
} else { // Executes if 'value' is 1, 2, or 3.
    print("$value is less or equal to three")
}  
```  

If you're confident about making decisions, proceed to the next section.

## Do It Again  

Sometimes, you need to repeat an action multiple times. How would you, for example, add numbers from 1 to 10?

```Kotlin  
// One way to do it.
val sum = 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10  
print(sum)  
```  

This method is manageable for small numbers, but imagine doing this for 1,000,000 or even 10 factorial (10!). That would be impractical. Instead, we use loops.

```Kotlin  
val sum: Int = (1 .. 10).sum()
val bigSum: Int = (1 .. 1000000).sum()
val unrealisticSum: Int = (1 .. 10.factorial()).sum()
```  
This demonstrates the power of loops.

[Loops](Loops.md) are versatile; you don't always need to know how many iterations are necessary in advance.

```Kotlin  
// This prints a random number of random values.

for(index in 1 .. Random.nextInt(1,6)) {
    print(Random.nextInt(1,6))
}  
```  

```Kotlin  
// Let's break down this example step by step for better understanding.

// Defining a function to roll a die.
val rollDie: () -> Int = { Random.nextInt(1,6) } // Returns a number between 1 and 6.

val numberOfLoops = rollDie() // Generates a random number between 1 and 6.

for(index in 1 .. numberOfLoops) { // Iterates the random number of times.
    val randomNumber = rollDie()   // Rolls the die.
    print(randomNumber)            // Prints the number.
}  
```  

If you're struggling with the last block, revisit this section and try to understand it again.

## Conclusion  

Armed with these three tools, you're now ready to delve deeper into the world of programming.

#next [Patterns](./Patterns.html)