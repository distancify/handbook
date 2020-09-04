[Handbook](../../README.md) / Standard Operating Proceedures / Implementer

# Reviewing a Pull Reqeust

At Distancify code reviews (as part of pull request) are an integrated part of the daily life of a developer. 

The main purpose of our code reviews is to do findings which can't be caught by automated tools.

Stuff we are looking for in out code review is:

- Is the code covered with unit tests? "This requires a unit test"
- Is the code clear and readable? Naming, semantics and length, both the reviewer and developer should be able to read the code
- Is the code implementing known anti-patterns? 
- Are APIs used as originally intended?

The code review should not the the main source of knowledge sharing, for this is pair programming a much better exercise.

## Suggestions

You're encouraged to comment on the architecture and overall approach/patterns used in the solution as long as these suggestions are constructive. However these suggestions are generally not a valid reason for declining a request (see *Approved with suggestions* below). While sharing knowledge between a senior and junior programmer is good, a design meeting or pair programming session is generally where these discussions fits best. Generally, it's up the the author to decide how to incorporate these suggestions, as long as the solution is not provably or obviously faulty, or breaking any other policies such as using anti-patterns or inconsistent code style.

A suggestion comment should start with "Suggestion:".

## States
- "approved" all clear, nothing to remark.
- "approved with suggestions" should be used when there might be better way to implement the solution. This must be accompanied with actual suggestions in the code.
- "wait for author" should be used when you have feedback which you need an answer to before you can take a decision whether to approve the code or not.
- "reject" the code can't be accecpted in it's current state.
