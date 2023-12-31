---
share: true
---

# Sticking to the Rules

You might see yourself as a rule-breaker, a rebel in the programming world. 

Okay, you are. 

And now, you have the green light to bend or break these rules. But before doing so, let's understand them. Knowing the rules helps us break them effectively.

## Standards

Programming languages come with standards to facilitate the transfer of information between programmers. Our primary goal should be to write readable code. It's okay to break rules if it enhances readability. However, most often, rules exist for a reason: they either add clarity or prevent issues that could obscure your code.

## What Standard?

I've oscillated between advocating for strict adherence to rules and encouraging rule-breaking. This is deliberate. Standards only work if everyone agrees on them. Otherwise, they lose their purpose and are often ignored. So, it's crucial to consider your audience.

In a software team, the standard is what the team agrees upon. These are the people interacting with the code most frequently, so they should decide on the communication pattern that suits them best.

For software intended for public use, deviating from standards requires strong justification. Non-standard code can be challenging for junior developers to understand, reducing their likelihood of engaging further.

If you're wondering why the least experienced should dictate the standards for the most experienced, remember that unless you're [Barbara Liskov](Barbara%20Liskov.md), you might need to reconsider. Readable code encourages others to contribute through PRs, a vital aspect of the [Open Source](Open%20Source.md) community. Poorly written code can deter contributions and indicate a lack of usage.

## What is Our Standard?

This is a question teams should ask, followed by "why."

## Idiomatic Kotlin

For this document, we adhere to [Idiomatic Kotlin](Idiomatic%20Kotlin).

Why? 

Because we're using [Kotlin](./Kotlin.md), and following its standard conventions will make our code more approachable for other developers. We will stick closely to the recommendations found [here](https://kotlinlang.org/docs/coding-conventions.html#verify-that-your-code-follows-the-style-guide).

## But Where's the Code?

Apologies for the detour, but that was necessary groundwork. Now, let's look at some examples of writing Idiomatic Kotlin. If you're using a different language, focus on the reasoning and adapt it to your language's standards.

```Kotlin
// Here are some Kotlin idioms, with a bit of our own flavor.

// Data Transfer Objects will be data classes to reduce boilerplate.
data class Opinion(
    val subject: String,
    val opinion: String,
    val holder: String,
)

// Use default values for null safety.
data class Opinion(
    val subject: String = "Standards",
    val opinion: String = "We should follow them, unless they suck, then we should change them",
    holder: String = "Everyone"
)

// Prefer code blocks over values for readability.
val list = listOf(1, 2, 3, 4, 5)
list.filter { it % 2 == 0 }
list.forEach { print(it) }

// String interpolation is more readable.
val hello = "Hello"
val world = "World"
print("$hello $world!")

// Extension functions reduce boilerplate.
fun String.orIsIt() = "$this, or is it?"
```

That should be enough code for now. Let's get back to discussing standards.

Teams can define their standards as a list of statements, each accompanied by a rationale. This way, when you need to deviate from a standard, you'll know the additional steps required to still meet the standard's underlying goal.

## Bike Shedding

The introduction of standards can lead to "Bike Shedding," where trivial aspects are over-debated. This often stems from personal preferences and the [Law of Triviality](Law%20of%20Triviality.md). Linking standards to clear goals helps avoid this pitfall. If a standard doesn't contribute to your goals, it's trivial and not worth the time.

Bike Shedding is a significant topic in itself. If you find your team getting bogged down in these trivial debates, it's a sign to stop and reassess your goals. Discussions should advance your objectives, not hinder them.

## Conclusion

Standards play a crucial role in maintaining code readability. While debates over [Tabs vs. Spaces](Tabs%20vs.%20Spaces.md) might seem trivial, consistency in these choices is vital for clarity and collaboration.