---
share: true
---

# Patterns  
  
When you are [Programming](Programming.md), you care creating patterns.  
  
These patterns are new actions you can take. This is what we are actually doing.   
Creating new actions. New possibilities.   
  
Let's talk language. We will use [Kotlin](./Kotlin.md).  
  
People have strong opinions on language. If you would like to use another, I support that.  
The code examples will be [Idiomatic Kotlin](Idiomatic%20Kotlin.md), but we will talk about patterns. This will keep language decoupled from explanation.  
Back to patterns.  
## Let's Start with [Functions](./Functions.md)  
  
There is an entire paradigm of languages around them. They are a pattern that creates patterns.  
These are the same thing as functions in [Math](Math.md). This is where knowing math is helpful, we will skip most of the math while pointing it out.  
  
```Kotlin
// This is called a function signature. It is how to describe the function.  
// This says functionName is a function that takes an Int named value and returns an Int.  
fun functionName(value: Int): Int {  
    // This is the function body. This describes the relationship between value and the result.  
	val result = value + 1    
	return result    
}  
```  
  
Let's take a look at another one.  
  
```Kotlin  
// Let's start with a natural language description of this function.  
// When given an Int, return a string indicating if the Int was even or odd.  
  
fun evenOrOdd(aNumber: Int): String {  
    // Let's start by figuring out if it is congruent to 2.    
    val result = if(number % 2 == 0) {
        return "even" // If it is congruent, then it is even.
    } else {
        return "odd" // If it ain't even, its odd.
    }   
    
    return result
}  
```  
  
Naming functions is important it is like [Prompt Engineering](Prompt%20Engineering.md). Turing words into actions.  
  
## More Fun With More Functions  
  
Just like in math, you can make functions that take functions. This is a [Higher Order Function](Higher%20Order%20Function.md) Let's write a function called compose.  
  
```Kotlin  
    // We are going to use lambdas as our functions, they are easy to treat as values.
    // Taking advantage of typealias to save some typing    
    // This means, when I say StringTransformer I want a function that takes a String and returns a new one.   
     typealias StringTransform = (String) -> String  
     
    // Here we have a function that takes a string and adds ", maybe" to the end    
    val maybe:StringTransform = { "$it, maybe" } // $it in this case is the original string.    
    // So maybe("It worked") would give you "It worked, maybe"        
    
    // Here we have a simular function  
    val probably:StringTransform = { "$it, probably" }        
    
    // Now this is a higher order function, a function that takes functions  
    // and in this case also returns a function.        
    val compose : (StringTransform, StringTransform)->StringTransform ={  
        a,b -> {a(b(it))} // This is (a of b )(it)    
    }        
    // Now, we can compose StringTransformers, maybe, probably  
    val maybeProbably = compose(maybe, probably)```  
  
This is very powerful, it allows you to reuse patterns. Reusing patterns keeps your code clean.  
  
You should read [Clean Code](Clean%20Code.md), a great book about programming.  
   
## Conclusion  
Know you what patterns are, and have one called a function. It is great at summarizing how to do things.  The next pattern will help you describe things.

#next [Combining Patterns](Combining%20Patterns.md)