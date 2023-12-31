---
share: true
---

# Patterns  

When you engage in [Programming](Programming.html), you're essentially crafting patterns.

These patterns represent new actions, new possibilities. It's about creating novel ways to interact with and manipulate data.

Let's delve into language specifics. We'll be using [Kotlin](./Kotlin.html) here.

People often have strong opinions about programming languages. If you prefer another language, that's completely fine. The code examples will be in [Idiomatic Kotlin](Idiomatic%20Kotlin.html), but our focus will be on the underlying patterns. This approach helps keep the language separate from the conceptual explanations. Now, back to patterns.

## Starting with [Functions](./Functions.html)  

Functions are central to an entire paradigm of programming languages. They are a foundational pattern, akin to functions in [Math](Math.html). Understanding math can be beneficial, but we'll mostly sidestep the complex mathematics while highlighting its presence.

```Kotlin
// This is a function signature. It defines the function's structure.
// It indicates that functionName is a function that takes an Int named 'value' and returns an Int.
fun functionName(value: Int): Int {
    // This is the function body. It describes the relationship between 'value' and the result.
    val result = value + 1    
    return result    
}  
```  

Let's examine another example.

```Kotlin  
// First, a natural language description of this function:
// Given an Int, return a string indicating whether the Int is even or odd.

fun evenOrOdd(aNumber: Int): String {
    // We begin by determining if the number is divisible by 2.
    val result = if (aNumber % 2 == 0) {
        "even" // If divisible, then it's even.
    } else {
        "odd" // Otherwise, it's odd.
    }
    
    return result
}  
```  

Naming functions is as crucial as [Prompt Engineering](Prompt%20Engineering.html). It's about transforming words into actions.

## More Fun With Functions  

Like in math, you can create functions that accept other functions. This concept is known as a [Higher Order Function](Higher%20Order%20Function.html). Let's write a function named 'compose'.

```Kotlin  
    // We'll use lambdas for our functions, treating them as values.
    // 'StringTransform' is a typealias for a function taking a String and returning a String.   
    typealias StringTransform = (String) -> String  
    
    // A function that appends ", maybe" to a string
    val maybe: StringTransform = { "$it, maybe" }
    
    // Similarly, a function that appends ", probably"
    val probably: StringTransform = { "$it, probably" }        
    
    // Now, a higher order function that takes functions and returns a function.
    val compose: (StringTransform, StringTransform) -> StringTransform = { a, b -> { a(b(it)) } }
    
    // Composing 'maybe' and 'probably'
    val maybeProbably = compose(maybe, probably)
```  

This technique is immensely powerful, allowing you to reuse and combine patterns, thereby keeping your code clean and efficient.

I recommend reading [Clean Code](Clean%20Code.html), a seminal book on programming best practices.

## Conclusion  
Now you understand what patterns are and have been introduced to a fundamental one: functions. They are excellent for encapsulating processes. Next, we'll explore how to combine these patterns effectively.

#next [Combining Patterns](Combining%20Patterns.html)