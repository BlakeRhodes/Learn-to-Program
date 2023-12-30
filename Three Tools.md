---
share: true
---

# Three Tools  
  
You have three  [Tools](./Tools.md) when you are programming. You may import or build more, but for now,  
let's focus on these three.  
  
1. Take Action  
2. Make Decisions  
3. Do It Again  
  
## Take Action  
  
You can write out something for the program to do. Let's start with the classic.  
  
```Kotlin  
// The action you are taking, is printing out some words.  
// These are comments, by the way. They don't do anything in the program,  
// but are useful when explaining things.  
  
print("Hello World!")  
```  
  
Now, the number of actions you can take are many. We will cover the ones we use,  
but just remember there are more.  
  
Let's try and take multiple actions  
  
```Kotlin  
val one = 1 // We are taking the action of assigning one to a value we named one.  
val two = 2 // This is called assignment. Here we do it again.  
val sum = one + two // Here we are adding them together and assigning the result to sum  
  
print(sum) // Now, we can print out the value of sum.  
```  
  
Nice, now you know how to take action.  
  
## Make Decisions  
  
Sometimes we call this branching, sometimes conditionals. They check to see what the situation is, then take action.  
  
```Kotlin  
val one = 1  
val two = 2  
val three = 3 //These should be familiar  
//  
//          A quick aside:  
//                         _ This means equals, easy to get confused with = which means is assigned.  
//                         |     These are the things programmers love.  
//                         V  
val message = if(one + two == three) "It is true" else "It is false"  
  
print(message) // the if statement created a branch, two possible outcomes.  
```  
  
Try reading it out loud, "Value Message is assigned, if one plus two equals three, then it is true.  
                         Else it is false."                         
  
```Kotlin  
// Let's do another one.  
  
val value = Random.nextInt(1,6) //This creates a pseudorandom integer between 1 and 6, like a die.  
  
if(value > 3) { // This is what happens if value is 4, 5, or 6  
    print("$value is greater than three") // Here we use string interpolation to print out the $value} else { // This is what happens if value is 1, 2, or 3  
    print("$value is is less or equal to three")}  
```  
  
If you think you can make decisions go to the next section.  
  
## Do It Again  
  
Sometimes you want to take the same action a bunch of times. Like how could you add 1-10?  
  
```Kotlin  
//This is one way.  
val sum = 1 + 2 + 3 + 4 + 5 + 6 + 7 + 8 + 9 + 10  
print(sum)  
```  
  
Good thing that was just 10, imagine if it was 1,000,00 or even 10!.  
That would become too much work, pretty quickly.  
No one wants to spend their time doing that. So Let's use a [Loop](Loop.md).  
  
```Kotlin  
    val sum:Int = (1 .. 10).sum()    val bigSum:Int = (1 .. 1000000).sum()    val unrealisticFromAPerformanceStandPointSum:Int = (1 .. 10!).sum() ```  
Pretty powerful. We just did all three.  
  
Loops are so powerful, you don't even have to know how many times you have to do it.  
  
```Kotlin  
// This will print a random number of random numbers.  
  
for(index in 1 .. Random.nextInt(1,6)) {  
        print(Random.nextInt(1,6))}  
```  
  
```Kotlin  
// Let's go step by step through this one. We are going to do it again.  
// This time writing more code, this is what what we call being more explicit.  
  
// Here we are creating a function, much more on those later.  
val roleDie:()-> Int = {Random.nextInt(1,6)} // This mean when we call roleDie() we get 1-6 back.  
  
val numberOfLoops = roleDie() // Random number between 1-6  
  
for(index i in 1 .. numberOfLoops) { // from 1 to that random number of loops  
    val randomeNumber = rollDie()    // role the die.    print(randomNumber)              // Then print out that number.}  
```  
  
If you don't understand the last block of code. Go to the beginning of this section and read it again.  
  
  
## Conclusion  
  
Now that you have three tools, we can begin to learn programming.

#next [Patterns](./Patterns.md)