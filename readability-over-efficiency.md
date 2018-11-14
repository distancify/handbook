# Readability over Efficiency

It's a common misconception that the ultimate goal of coding is to program what a computer should do given different scenarios. But if this where true then we would still be writing in an assembly language. This misconception has led to programming being taught as a skill of understanding syntax. Focusing on how to make the computer perform specific actions. This approach to software development have then given birth to software all around the world overlooking one key aspect the cost of software. The most expensive cost of software is **maintenance**.

Programming languages where invented to make it easier for humans to write and read code at the loss of some control. When programming in a high level language you give up some of your control over the hardware in order to speed up development and minimize costs. Knowing the syntax of a language is important, but just as a good book is more than a list of words, good software is more than a list of instructions.

This is why we at Distancify values *Readability over Efficiency*. Writing an algorithm in the fewest amount of keystrokes may be efficient, but can be terribly difficult to maintain. On the other hand, too much code can make it hard to see the forest for the trees. It's difficult to give any rules of what is and isn't readable. Automatic refactoring algorithms have tried and failed. However, there are processes that can help such as pair programming and code reviews. Further, there are common practices and principles that can be applied to simplify maintenance and increase readability.

## Naming

Names should be relative to their scope. Small scope - short names. Large scope - longer more descriptive names. A local variable may, for example, be called *i* or *m* or *p*. While a private class variable may be called *customers* or *currentIndex*. Classes should have very descriptive names, as their scope is almost infinite. Do not try to be clever about naming. Naming should be accurate and stupid. Do not be afraid of naming your class *EmailAddressValidator* or *FirstNameLastNameConcatenator*. This also goes for method naming.

Do not overlook the importance of naming. Naming gives meaning and a good name can convey a complex idea in a very efficient and easy to understand way. The names we assign opens up or limits our ability to reason about the things they describe.

Names should:

* be accurate
* be descriptive and clear
* be efficient
* not add unnecessary constraints (i.e don't name a class *Car* if it can represent a vehicle of any kind)
* not end in *Manager* :-)

## Patterns and Anti-Patterns

Patterns are a great way to increase readability. Humans are hard-wired to find patterns in just about anything, and by relying on industry recognized patterns you do your readers a big favor. Beware though, not all patterns are good for all problems, and some are just plain bad. Some patterns should be used as a last resort, such as the *Singleton* pattern, which promotes hard wired dependencies between software modules.

Just because a pattern is recognized doesn't mean it's a good idea to use it. We refer to these bad patterns as *Anti-patterns*.

## Configuration over Convention

One of the worst trends to spread over the last few years has been the *Convention over Configuration* paradigm invented and promoted as part of the Ruby on Rails web framework. While it initially seem like a good idea, a fresh breath of air over requiring loads of configuration just to get started, it has a long-term side effect. Conventions, when unknown to the reader, are **indistinguishable from magic**.

This can make it almost impossible to follow the flow of a program if you're not familiar with every single convention that the code relies on. A few well known conventions in any platform can be a huge time saver, but take this too far and you will find yourself with unreadable code.

When relying on conventions, you also become dependent on those conventions never changing. This is generally not a problem for consumers of an API or platform. But as a developer of said APIs and platforms, introducing a convention is an **enormous** commitment. Breaking the contract of a convention is a huge deal, especially since breaking a convention generally don't show up at compile time and can be hard to trace for people relying on your code.

This is why we favor *configuration over convention*, preferably with sensible defaults.
