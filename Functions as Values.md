---
share: true
---

# Functions as Values

Earlier, we explored using objects in functions. Now, let's reverse that concept and use functions within objects.

We know objects can contain values, so why not include functions too?

Let's experiment with this idea.

```Kotlin  
data class Box(  
    val weight: Int,        
    val owner: String,        
    val cost: () -> Float,
)

// Instantiate a Box
val weight = 5  
val box = Box(weight, "Alice", { weight * 5.0f })

// Refactor for Better Readability
val box2 = Box(weight, "Alice") {  
    weight * 5.0f 
}  
```  

However, this approach seems to complicate things. But, it helps us identify a problem.

What exactly is 5.0f? A [Magic String](Magic%20String.md), perhaps? 

Let's consider what happens when we extract this value into a separate object, representing the price.

```Kotlin  
// Switching to Double for precision.
data class Box(  
    val weight: Int,
    val owner: String,        
    val price: Double,        
    val cost: () -> Double,
)

val price = 10.0  
val box = Box(weight, "Alice", price, { weight * price })    
```  

But this solution still lacks clarity. Kotlin supports our approach, but we're not utilizing it effectively.

We need to make our code more readable and intuitive.

Initially, we thought each box would have a unique cost calculation. However, it's more likely that the cost formula will be consistent across boxes.

```Kotlin  
// Utilizing Kotlin's language features more effectively
data class Box(  
    val weight: Int,        
    val owner: String,        
    val price: Double
) {  
    val cost = weight * price
}  
```  

However, this solution doesn't use a function, and it assumes a uniform price calculation.

Let's try incorporating a function for versatility.

```Kotlin  
data class Box(  
    val weight: Int,
    val owner: String,    
    val price: Double
) {  
    fun cost(): Double = weight * price
}    
```  

Success! But wait, there's a new requirement: some packages may now include discounts.

Change is a constant in programming, as [Dylan Bettie](Dylan%20Bettie.md) reminds us with the [PIKE-MATCHBOX](PIKE-MATCHBOX.md) principle of programming.

Plain text is a powerful way to add functionality. Image when you get a story like this.

```Prompt
Boxes can now have discounts.
```

Agile methodologies and the right approach help us adapt to these changes.

```Kotlin  
// Introducing a Discount Object
data class Discount(val percentOff: Double) {
    fun totalCost(price: Double, weight: Int): Double {
        return price * weight * (1 - percentOff)
    }
}

data class Box(  
    val weight: Int,    
    val owner: String,    
    val price: Double,    
    val discount: Discount
) {  
    fun cost() = discount.totalCost(price, weight)
}
```  

Interestingly, objects can contain other objects, just as functions can be nested within functions.

## Conclusion

We've learned that objects can effectively encapsulate functions as values, offering flexibility and adaptability in our programming approach.

#next[Applying Functions](Applying%20Functions.html)