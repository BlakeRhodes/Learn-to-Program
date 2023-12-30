---
share: true
---


# [Functions](./Functions.md) as [Values](Values.md)  
  
We explored how you can use [Objects](./Objects.md) in Functions. Let's flip that script   
and use objects to contain functions.  
  
We already know we can put values in an Object, why not put some functions in an object?  
  
Okay, let's give it a try.  
  
```Kotlin  
data class Box(  
        val weight: Int,        
        val owner: String,        
        val cost: () -> Float,
)  
  
// Let instatiate a Box  
val weight = 5  
val box = Box(weight, "Alice", {weight * 5.0f })  
  
// Refactor for Readability  
val weight = 5  
val box2 = Box2(weight, "Alice") {  
    weight * 5.0f 
}  
```  
  
No, that made it worse. However, we found the problem.  

What is 5.0f? A [Magic String](Magic%20String.md)?   
No!  
  
I can hear [Ryan Brock](Ryan%20Brock.md) right now.  
  
That's easy. What happens when we extract it.  
  
What he is saying, we extract a new object. The price.  
  
```Kotlin  
// I don't really want to use a float, so I am changing it to a Double.  
// A note on making changes, adding is easy. Removing is hard.  
data class Box(  
    val weight: Int,
    val owner: String,        
    val price: Double,        
	val cost: () -> Double,
)  
  
val weight = 5  
val price = 10.0  
val box = Box(weight, "Alice", price, {weight * price })    
```  
  
This poor readability will not stand, but this is not just a code smell . . .  
  
Kotlin does support what we are doing, but we are doing it wrong. 

What we need to do is make it more readable. 

Then our mistake will be clear.  
  
We are making a mistake thinking that every box has a different way of calculating the cost.  
It will be the same for each, so we can add another field.  
  
```Kotlin  
// No messing around this time. We are going to use a language feature  
  
data class Box(  
	val weight: Int,        
	val owner: String,        
	val price: Double,
) {  
    val cost = weight * price
}  
```  

Shoot, we are not using a function.  

Also, this assumes the price is calculated the same every time.  

I bet it will be the same.  I guess let's stay on topic and make it a function [Third Times a Charm](Third%20Times%20a%20Charm.md).

  
```Kotlin  
data class Box(  
	val weight: Int,
	val owner: String,    
	val price: Double
} {  
    fun cost(): Double { return weight * cost }
}    
```  
  
We did it!  
o.o  
  
We were wrong! The BA just put a story on the board that some packages can now have a discount!  

In this kitchen, we expect things to change up.    
  
Why? I know they are engineers and I know PIKE-MATCHBOX thanks to Dylan Bettie.   

They have already solved the problem with plain text.  

```Prompt
Boxes can now have discounts.
```
  
  
Of course, they would use AC, Agile, and the right sauce to get us cooking.  
  
Yes, Chef!  
  
```Kotlin  
  
// Discount is now an Object!  
  
data class Discount( val percentOff: Double, ) {
    fun totalCost(        
	    price: Double,        
	    weight: Int,    
	): Double {
		return price * weight * percentOff    
	}
}  

data class Box(  
    val weight: Int,    
    val owner: String,    
    val price: Double,    
    val discount: Discount,
) {  
    fun cost() = discount.totalCost(price, weight)
}
```  
  
It just happens you can put objects into objects, like you can put functions into functions.  
  
## Conclusion  
  
Objects can have Functions as Values.

#next [Applying Functions](./Applying%20Functions.md)