# Code review and pull request

At Distancify are code review (as part of pull request) an integrated part of the daily life of a developer. 

The main purpose of our code reviews is to do findings which can't be caught by automated tools.

Stuff we are looking for in out code review is:

- Is the code covered with unit tests? "This requires a unit test"
- Is the code clear and readable? Naming, semantics and length, both the reviewer and developer should be able to read the code
- Is the code implementing known anti-patterns? 
- Are APIs used as originally intended?

The code review should not the the main source of knowledge sharing, for this is pair programming a much better exercise.

Constructive criticism is encouraged in the pull requests. As a rule of tumb should you provide a reason to your criticism and in best of all worlds even a suggestion to a better solution. And if you don't, you should be prepared to be ignored.

## States
- "approved" all clear, nothing to remark
- "approved with suggestions" should be used when you feel that the things you have noted should be taken into consideration for the future but the developer doesn't necessarily have to go in and update his/her code in this review.
- "wait for author" should be used when you have feedback which you need an answer to before you can take a decision whether to approve the code or not 
- "reject" the code can't be accecpted in it's current state.

## Resources on code review

- [Awesome Code Review](https://github.com/joho/awesome-code-review) - An "Awesome" list of code review resources - articles, papers, tools, etc 
- [The Checklist of my code review](https://medium.com/@same7mabrouk/the-checklist-of-my-code-review-18cc6f6fb5b3) by Sameh Mabrouk
