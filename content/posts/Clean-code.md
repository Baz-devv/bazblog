---
title: "Clean Code"
date: 2022-01-09T14:57:35+03:00

---
[![Clean code uncle bob](https://images-na.ssl-images-amazon.com/images/I/51E2055ZGUL._AC_UL210_SR210,210_.jpg)]

Link: https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882

Many a developer preach the gospel of clean code but how many have actually read the book? Granted this book isn't the be all end all of clean-code but it's definitely the industry standard.

As the book alludes to, there are developers with 'code-sense' who are able to pick up clean-code naturally while some of us have to acquire it the hard-way, we put ourselves through a Rocky like training 
of constantly reading, writing and refactoring code in order to get it to the accepted industry standards and as you probably might know programmers are a difficult bunch to please so I guess it's a hopeless task.. 

This is my chapter by chapter summary of Clean Code by Robert Martin(Uncle Bob), some parts verbatim others not so much. I hope at the end I'll be well on my way to acquiring 'code-sense'.


## CHAPTER 1: CLEAN CODE.

I just have to get this out of the way first, "The only valid measurement of code quality: WTFs/minute."

#### There will be code.

There's always talk of will there be need for programmers in the future or will there be machines to replace them? Well this author believes good-programmers will always be needed and in demand but 
I bet he to is feeling the heat generated by AI, advancements in this field surely cannot be ignored but we embrace it not fear it.

#### Bad code

Bad code has the effect of slowing down teams and reducing productivity, if you understand the butterfly effect, you'll agree when someone says bad code could bring organisations to their knees, more on this
later.

WADING => The act of being impeded by bad code.

#### The total cost of owning a mess.

As the mess(bad code) builds, the productivity continues to decrease, asymptomatically approaching zero and as this happens, management does the only thing they can, add more staff with hope that productivity
picks up but we know to well it won't as they haven't addressed the underlying issue. I hope you can now start seeing the cost of the mess in tangible detail.

#### The grand redesign in the sky.

Let's build a new sytem to replace this new one. We'll use a new flashy language that the programmers now have to pick up, dangle all the trendy tech buzzwords to management so they allow a redesign and promise
heaven on earth with the new system. 

Every programmer gets to experience the above scenario a few times in their career. The team lead probably convinced you the switch from JavaScript to Rust is beacause Rust is blaingly fast and you ate up that 
lie with glee.

The truth of the matter is that your current system has bad code, don't get me wrong rust is way faster than js, so every few years you'll always find yourself redesigning instead maintaining good code and the
cycle of bad code continues.

Spending time keeping your code clean isn't just cost effective, it's a matter of professional survival.

#### Attitude.

Why does good code rot so quickly into bad code?


To list a few reasons:
1. complaints that requirements changed in ways that thwart the original design.
2. complaints that schedules were to tight to do things right.

These are just excuses, programmers are deeply complicit in the planing of the project and share a great deal of the responsibility for any failures.

#### The primal conundrum.
The only way to make the deadline - the only way to go fast - is to keep the code as clean as possible at all times.

#### The art of clean code.
How do I write clean code?

Well first you must know what it means for code to be clean.

This really hurt my pride a bit "being able to recognize clean code from dirty code doesn't mean we know how to write clean code". A programmer who writes clean code is an artist who can take a blank screen 
through a series of transformations until it is an elegant coded system.

The author gave us a peak into what programming pioneers and experts think about clean code, here are a few that stuck with me:

Bjarne Stroustrup:

`I like my code to be elegant and efficient. The logic should be straightfoward to make it hard for bugs to hide, the dependencies minimal to ease maintenance, error-handling complete according to an articulated
strategy, and perfomance close to optimal so as not to tempt people to make the code messy with unprincipled optimizations. Clean code does one thing well.`

Grady Booch:

`Clean code is simple and direct. Clean codenever obscures the designer's intent but rather is full of crisp abstractions and straightfoward lines of control.`

But personally the best description of what clean code ought to look like that has always stuck with me is `...Clean code always looks like it was written by someone who cares...` by Michael Feathers.


## CHAPTER 2: MEANINGFUL NAMES.

Here are the rules mentioned in the book for defining names, I won't go into detail as the purpose here is to summarize:

1. Use intention revealing names.

2. Avoid disinformation.

3. Make meaningful distinctions.

4. Use pronounceable names.

5. Use searchable names.

6. Avoid encodings.

7. Avoid mental mapping.

8. Don't be cute.

9. Pick one word per concept.

10. Don't pun.

11. Use solution domain names.

12. Use problem domain names.

13. Add meaningful context.

14. Don't add gratuitous context.

## CHAPTER 3: FUNCTIONS.

What is it that makes a function easy to read and understand? How can we make a function communicate its intent?

Well here are a few guidelines:

#### Small!
The first rule of functions is that they should be small. The second rule is that they should be smaller than that.
Not set in stone but it's just a good idea not to have your functions more than 20 lines long if you've had to read bad code you definitely agree with this.

#### Blocks and Indenting.
Functions shouldn't be large enough to hold nested structures. The indent level of a function should not be more than 2.

#### Do One Thing.
`Functions should do one thing. They should do it well. They should do it only.`

If a function does things that are one level below the stated name of the function then it's doing one thing.

*A way of knowing whether a function is doing more than 'one thing' is if you can extract another function from itwith a name that is not merely a restatement of its implementation.

#### Sections With Functions.
Functions that do one thing cannot be reasonably divided into sections.

#### One Level Of Abstraction Per Function.
Make sure that the statements within your functions are all at the same level of abstraction.

#### Reading Code From Top To Bottom: `The Stepdown Rule`.
Code ought to read like a top-down narrative, remember that 'well-written prose' description?

Every function should be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction at a time.

#### Use Descriptive Names.
As already pointed out, meaningful names are a godsend in programming.

The smaller and more focused a function is, the easier it is to choose a descriptive name.

#### Function Arguments.
The ideal number of arguments for a function is niladic. Next comes monadic followed by dyadic.

Triadic functions should be avoided where possible.

#### Common Monadic Forms.
There are 2 very common reasons to pass a single argument into a function:
1. you may be asking a question about that argument.

2. you may be operating on that argument.

#### Dyadic Functions.
A function with two arguments is harder to understand than a monadic function.

#### Triadic Functions.
Abundantly difficult than dyads. The issues of ordering, pausing and ignoring are more than doubled.

#### Argument Objects.
When a function needs more than 2 arguments, it's clear that some of those arguments need to be wrapped in a class of their own.

#### Output Arguments.
In general, output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object.

#### Prefer Exceptions To Returning Error Codes.
Returning error codes from command functions is a subtle violation of command query separation.

It promotes commands being used as expressions in the predicates of `if` statements.

#### Extract `try/catch` Blocks.
`try/catch` blocks are ugly, let's get that out of the way first.

They confuse the structure of the code and and mix error processing with normal processing.

It's therefore better the bodies of `try/catch` blocks out into functions of their own.

#### Error Handling Is One Thing.
Functions should do one thing. Error handling is one thing. Thus, a function that handles errors should do nothing else.

#### How do you write perfect functions?
The only way is to first write bad functions, then re-write and refactor them until you have a clean function. You probably won't get it right at the first try.

`Master programmers think of systems as stories to be told rather than programs to be written.`

## CHAPTER 4: COMMENTS.

`"Don't comment bad code - rewrite it" Brian Kernighan`

The proper use of comments is to compensate for our failure to express ourselves in code.

Comments are a necessary evil. In a perfect universe, code should be clear and expressive that it doesn't need comments.

Always keep in mind though that the truth can only be found in one place; `the code`.

#### Comments Do Not Make Up For Bad Code.
Clear and expressive code with few comments is far superior to cluttered and complex code with lots of comments.

Rather than spending time writing comments explaining your bad code, spend it cleaning the mess.

#### Explain Yourself In Code.
It takes only a few seconds of thought to explain most of your intent in code. In many cases, it's simply a matter of creating a function that says the same thing as the comment you want to write.

#### Good Comments.
Some comments are good but keep in mind that the only truly good comment is the comment you found a way not to write.

Here are a few reasons for writing comments and the laws they should abide by:

##### 1.Legal Comments.
Sometimes our corporate coding standards force us to write certain commentsfor legal reasons.

##### 2.Informative Comments.
It is SOMETIMES useful to provide basic information with a comment.

##### 3.Explanations Of Intent.
Sometimes a comment goes beyond just useful information about the implementation and provides the intent behind a decision.

##### 4.Clarification.
Sometimes it's just helpful to translate the meaning of some obscure argument or return value into something that's readable. It's better to find a way to make that argument or return value clear in its
own right; but when it's part of the standard library or in code you can't alter then a helpful clarifying comment can be useful.

##### 5.Warning Of Consequence.
We may use comments to warn other programmers about certain consequences.

##### 6.TODO Comments.
It's reasonable to leave 'To Do' notes in the form of `//TODO` comments.

##### 7.Amplification.
A comment may be used to amplify the importance of something that may otherwise seem inconsequential.

#### Bad Comments.
Most comments fall into this category. Usually they are crutches for poor code or justifications for insufficient decisions amounting to little more than the programmer talking to himself.

What constitutes a bad comment?

##### 1.Mumbling.
If you decide to write a comment, then spend the time necessary to make sure it is the best you can write anything less is just negligence and bad programming.

##### 2.Redundant Comments.
Don't write comments that obscure the code.

##### 3.Misleading Comments.
Sometimes with all the best intentions, a programmer makes a statement in his comments that isn't precise enough to be accurate.

##### 4.Mandated Comments.
It is plain silly to have a rule that every function or variable must have a comment. Such restrictions cause comments to clutter up code, propagate lies and lend to general confusion and disorganization.

##### 5.Journal Comments.
Journal comments should be removed or they'll add up to one giant mess.

##### 6.Noise Comments.
Sometimes you'll see comments that are nothing but noise. They restate the obvious and provide no new information.

Replace the temptation to create noise with the determination to clean your code.

##### 7.Don't Use A Comment When You Can Use A Function Or A Varable.

##### 8.Position Markers.
`////////////` are really an eyesore.

They are clutter that should be eliminated.

##### 9.Closing Brace Comments.
Don't put comments at the end of closing braces.

##### 10.Attributions And Bylines.
Just don't do it.

##### 11.Commented-out Code.
Instead of commenting-out code, delete it.

##### 12.HTML Comments.
HTML in source code comments is an abomination.

##### 13.Nonlocal Information.
If you must write a comment, make sure it describes the code it appears near. Don't offer systemwide information in the context of a local comment.

##### 14.Too Much Information.
Don't put interesting historical discussions or irrelevant descriptions of details into your comments.

##### 15.Inpbvious Behaviour.
The connection between a comment and the code it describes should be obvious. The purpose of a comment is to explain code that does not explain itself.

`IT IS A PITY WHEN A COMMENT NEEDS ITS OWN EXPLANATION.`

##### 16.Function Headers.
Short functions don't need much description. A well chosen name for a small function that does one thing is usually better than a comment header.

## CHAPTER 5: FORMATTING.
You should take care that your code is nicely formatted. You should choose a set of simple rules that govern the format of your code and consistently apply those rules.

#### The Purpose Of Formatting.
Coding style and readablity set precedents that continue to affect maintainability and extensibility long after the original code has been changed beyond recognition.

#### i.Verical Formatting.
How big should a source file be?

##### 1.The Newspaper Metaphor.
Our source code ought to be like a newspaper. The name should be simple but explanatory, sufficient to tell us whether we are in the right module or not.

The top most parts of the source file should provide the high-level concpts and algorithms. Details should increase as we move downward until at the end we find the lowest level function 
and details.

##### 2.Vertical Openness Between Concepts.
Each line of code represents an expression or a clause and each group of lines represents a complete thought. Those thoughts should be separated from each other with blank lines.

##### 3.Vertical Density.
If openness separates concepts, then density implies close association.

Lines of code that are tightly related should appear vertically dense.

##### 4.Vertical Distance.
Concepts that are closely related should be kept vertically close to each other.

For concepts vertically related, their vertical separation should be a measure of how important each is to the understanding of the other.

Variable Declarations: Variables should be declared as close to their usage as possible.

Instance Variables: Declared at the top of the class.

Dependant Functions: If one function calls another, they should be vertically close and the caller above the callee, giving the program a natural flow.

Conceptual Affinity: Certain bits of code want to be near other bits, they have a certain conceptual afinity. The stronger that affinity the less vertical distance there should be between them.

##### 5.Vertical Ordering.
Function call dependencies should point in the downward direction i.e, a function that is called should be below a function that does the calling.

#### ii.Horizontal Formatting.
How wide should a line be? Generally keep them short.

## CHAPTER 6: OBJECTS AND DATA STRUCTURES.

#### Data Abstraction.
We don't want to expose the details of our data rather, we want to express our data in abstract terms.

#### Data/Object Anti-Symmetry.
Objects hide their data behind abstractions and expose functions that operate on that data.

Data structures expose their data and have no meaningful functions.

`Procedural code (code using data structures) makes it easy to add new functions without changing the existing data structures. Object Oriented code makes it easy to add new classes without changing 
existing functions.`

The complement is also true:

`Procedural code makes it hard to add new data structures because all the functions must change. OO code makes it hard to add new functions because all the classes must change.`

The idea that everything is an 'object' is a myth. Sometimes you really do want simple data structures with procedures operating on them.

#### The 'Law of Demeter'.
The `Law of Demeter` is a heuristic that says a module should not know about the innards of the object it manipulates.

Objects hide their data and expose operations. This means that an object should not expose its internal structure through accessors because to do so is to expose its internal structure.

More precisely, the law says that a method `f` of a class `C` should only call the methods of these:

-C

-An object created by `f`

-An object held in an instance varible of `C`

the method should NOT invoke methods on objects that are returned by any of the allowed functions.

#### Data Transfer Objects.
The quintessential form of a data structure is a class with public variables and no fuctions. This is called a Data Transfer Object (DTO).

DTOs are very useful especially when communicating with databases or parsing messages from sockets and so on. They often become the first in a series of translation stages that convert raw
data in a database into objects in the application code.

##### Active Records.
Are special forms of DTOs.

Are data structures with public variables; but typically have navigational methods like `save` and `find`.

## CHAPTER 7: ERROR HANDLING.
Techniques and considerations you can use to write code that is both clean and robust - code that handles errors with grace and style:

1. Use exceptions rather than return codes.

2. Write your `try-catch-finally` statement first.

3. Provide context with exceptions.

4. Define exception classes in terms of a callers needs.

5. Define the normal flow.

6. Don't return `NULL`.

7. Don't pass `NULL`.

## CHAPTER 8: BOUNDARIES.
`We seldom control all the software in our systems` therfore we need to know how to cleanly integrate foreign code with our own.

#### Using Third Party Code.
Don't pass interfaces at a boundary around your system.

If you use a boundary interface, keep it inside the class, or close family of classes where it's used. Avoid returning it from, or accepting it as argument to public API's.

#### Exploring And Learning Boundaries.
Third-party code helps us to get more functionality delivered in less time. It is therefore in our best interest to write tests for the third-party code we use.

Learning and integrating third-party code is hard so the best way to approach them would be to write tests to explore our understanding of the third-party code. Such tests are called `Learning tests`.

In learning tests we call the third party API as we expect to use it in our program, we are essentially doing controlled experiments that check our understanding of that API, they focus on what we want from the API.

#### Learning Tests Are Better Than Free.
Learning tests are precise experiments that help increase our understanding as you have to learn an API, writing these tests is an easy and isolated way to get that knowledge.

Learning tests have a positive return on investment. When there's a new release of the third-party package, we run the learning tests to see whether there are behavorial differences.

#### Clean Boundaries.
Change is one of those things that happen at boundaries. Good software designs accomodate change without huge investments and rework.

Code at the boundaries needs clear separation and tests that define expectations. We should avoid letting too much of our code know about the third-party particulars

Manage third-party boundaries by having very few places in the code that refer to them, this promotes internally consistent usage across the boundary and has fewer maintenance points when the third-party code changes.

## CHAPTER 9: UNIT TESTS.

#### The 3 Laws Of TDD.
`First Law`: You may not write production code until you have written a failing unit test.

`Second Law`: You may not write more of a unit test than is sufficient to fail.

`Third Law`: You may not write more production code than is sufficient to pass the currently failing tests.

#### Clean Tests.
What makes a test clean? Readability.

What makes tests readable? Clarity. Simplicity. Density of expression.

#### One Assertion Per Test.

##### Single Concept Per Test.
Test a single concept in each test function.

The best rule is; Minimize the number of asserts per concept and test just one concept per test function.

#### F.I.R.S.T
`Fast` -> Tests should be fast, run very quickly.

`Independent` -> Tests shouldn't depend on each other. One test should not set up the conditions for the next test.

`Repeatable` -> Tests should be repeatable in any environment.

`Self-Validating` -> Tests should have a boolean output, either they pass or fail.

`Timely` -> Tests need to be written in a timely fashion. Should be written before the production code that makes them pass.

## CHAPTER 10: CLASSES.

#### Class Organization.
Classes should begin with a list of variables. Public stati constants if any should come first. Then private static variables followed by private instance variables.

Public functions should follow the list of variables. Private utilities called by a public function should be put right after the public function itself. This follows the step-down rule and helps the program read like a 
newspaper article.

#### Classes Should Be Small.
The first rule of classes is they ought to be small.

As with functions, smaller is the primary rule when it comes to designing classes.

How small should they be then? With functions we measured size by counting physical lines but with classes we count `responsibilities`.

The name of a class should describe what responsibilities it fulfils. Naming is the first way of helping determine class size.

##### Single Responsibility Principle (S.R.P).
SRP states that a class/module should have one and only one reason to change.

This principle gives us both a definition of responsibility and guidelines to class size.

A system should be composed of many small classes. Each small class encapsulates a single responsibility, has a single reason to change and collaborates with a few others to achieve the desired system behaviour.

##### Cohesion.
Classes should have a low number of instance variables.

Each of the methods of a class should manipulate one or more of those variables. The more variables a method manipulates, the more cohesive that method is to its class.

Maintaining cohesion results in many small changes.

#### Organizing For Change.
For most systems, change is continual. In a clean system, we organize our classes so as to reduce the risk of change.

In an ideal system, we incorporate new features by extending the system not by making modifications to existing code.

##### Isolating From Change.
Needs will change and its therefore inevitable that code will change.

In OOP there are concrete classes which contain implementation code and abstract classes which represent concepts only.

A client class depending on concrete details is at risk when those details change. To mitigate this, we can introduce interfaces and abstract classes to help isolate the impact of those details.

## CHAPTER 11: SYSTEMS.
`Complexity kills. It sucks the life out of developers. It makes products difficult to plan, build and maintain.`

Software teams can be organized as cities are, cities work because they have evolved appropriate levels of abstraction and modularity that makes it possible for individuals and the `components` they manage
to work effectively even understanding the big picture.

Although software teams are often organized like that too, the systems they work on often don't have the same separation of concerns and levels of abstraction.

Clean code helps us achieve this at the lower levels of abstraction, but how do you stay clean at higher levels of abstraction, the system level?

#### Separate Constructing A System From Using It.
Construction is a very different process from use.

`Software systems should separate the startup process, when the application objects are constructed and the dependencies are 'wired' together, from the runtime logic that takes over after startup.`

If we are dilligent about building well-formed and robust systems, we should never let little, convenient idioms (`LAZY INITIALIZATION`) lead to modularity breakdown.

We should modularize the startup process separately from the normal runtime logic and make sure we have a global, consistent strategy for resolving our major dependencies.

##### Separation Of Main.
One way to separate construction from use is simply to move all aspects of construction to `main`, and to design the rest of the system assuming that all objects have been constructed and wired appropraitely.

If this is done, flow of control will be easy to follow. `Main` builds objects necessary for the system then passes them to the application which uses them.

Note: Check out how factories interrupt separation of main and how its tackled.

##### Dependency Injection.
A powerful mechanism for separating construction from use is Dependency Injection, the application of Inversion of Control (IoC) to dependency management.

IoC moves secondary responsibilities from an object to other objects that are dedicated to the purpose, thereby supporting SRP.

In the context of dependency management, an object shouldn't take the responsibility for instantiating dependencies itself. Instead, it should pass this responsibility to another 'authoritative' mechanism,
 thereby inverting the control.
Since the setup is a global concern, this authoritative mechanism will usually either be the 'main' routine or a special purpose container.

#### Scaling Up.
It is a myth that we can get systems right the first time.

Instead, we should implement only today's stories, then refactor and expand the system to implement new stories tomorrow. This is the essence of iterative and incremental agility.

#### Test Drive The System Architecture.
It's not necessary to do a `'Big Design Up Front'` (BDUF). In fact BDUF is even harmful because it inhibits adapting to change, due to the psychological resistance to discarding prior effort and because of the way
architecture choices influence subsequent thinking about the design.

If software separates concerns effectively, it is economically feasible to make radical changes to it.

This means we can start a software project with a 'naively simple' but nicely decoupled architecture, delivering working user stories quickly, then adding more infrastructure as we scale up.

Definitely this doesn't mean we go into a project 'rudderless'. We should have some expectation of the general scope, goals, and schedule, as well as the general structure of the resulting system.

#### Optimize Decision Making.
Modularization and separation of concerns make decentralized management and decision making possible.

Note that its best to postpone decisions until the last possible moment. This isn't lazy or irresponsible. A premature decision is a decision made with suboptimal knowledge.

#### Use Standards Wisely, When They Add Demonstrable Value.
`Standards make it easier to reuse ideas and components, recruit people with relevant experience, encapsulate good ideas, and wire components together. However, the process of creating standards can sometimes take
too long for industry to wait, and some standards lose touch with the real needs of the adopters they are intended to serve.`

#### Systems Need Domain Specific Languages.
A good DSL minimizes the communication gap between a domain concept and the code that implements it.

DSL's, when used effectively, raise the abstraction level above code idioms and design patterns. They allow the programmer to reveal the intent of the code at the appropriate level of abstraction.

## CHAPTER 12: EMERGENCE.

#### Getting Clean via Emergent Design.
Kent Beck's 4 rules of `'Simple Design'` help in creating well-designed software.

The rules are; in order of importance:

1. Runs all the tests.

2. No duplication.

3. Expresses the intent of the programmer.

4. Minimize the number of classes and methods.

#### Simple Design Rule 1: Runs All The Tests.
A simple and obvious rule that says we need to have tests and run them continously impacts our systems adherence to the primary OOP goals of low coupling and high cohesion. Writing tests leads to better design.

Systems that aren't tested aren't verifiable. A system that cannot be verified should never be deployed.

#### Simple Design Rule 2-4: Refactoring.
Once we have tests, we are empowered to keep our code and classes clean. We do this by incrementally refactoring the code.

During this refactoring step, we can apply anything from the entire body of knowledge about good software design.

#### No Duplication.
Duplication is the primary enemy of a well-designed system.. It represents additional work, risks and unnecessary complexity.

#### Expressive.
Stick to the rules layed out in this book such as meaningful names and small functions and your code will express your intent. Remember the majority of the cost of a software project is in long-term maintenance.

#### Minimal Classes And Methods.
Each of the previous rules can be taken too far. In an effort to make classes smaller, we might create too many tiny classes which is what this rule is against. We need to keep our class and function counts low.

Keep in mind this rule's hierarchy in priority. Last.

## CHAPTER 13: CONCURRENCY.
`Objects are abstractions of processing. Threads are abstractions of schedule.`

Writing clean concurrent program is very hard. Its much easier to write code that executes in a single thread.

#### Why Concurrency?
Concurrency is a decoupling strategy. It helps decouple 'what' gets done from 'when' it gets done.

In single-threaded applications 'what' and 'when' are so strongly coupled that the state of the entire application can often be determined by looking at the stack backtrace.

Decoupling 'what' from 'when' can dramatically improve both the throughput and structures of an application. From a structural point of view the application looks like many little collaborating computers rather than
one big main loop. This can make the system easier to understand and offers some powerful ways to separate concerns.

Structure though is not the only motive for adopting concurrency. Some systems have response time and throughput constraints that require hand-coded solutions.

#### Myths and Misconceptions.
1. Concurrency always improves performance: It improves performance only when there is a lot of wait time that can be shared between multiple threads.

2. Design does not change when writing concurrent programs.

3. Understanding concurrency issues is not important when working with a container e.g web container.

##### Balances:
1. Concurrency incurs some overhead, both in performance as well as writing additional code.

2. Correct concurrency is complex, even for simple problems.

3. Concurrency often requires a fundamental change in design strategy.

4. Concurrency bugs aren't always repeatable, so they are often ignored as one-offs instead of the true defects they are.

#### Concurrency Defense Principles.
##### 1. SRP.
Remember SRP states a given component should have a single reason to change. Concurrency design is complex enough to be a reason to change in its own right and therefore deserves to be separated from the rest of the code

Considerations before embedding concurrent code directly into production code:

1. concurrency related code has its own life-cycle of development, change and tuning.

2. concurrency related code has its own challenges which are different from and often more difficult than non-concurrent code.

3. the number of ways in which miswritten concurrency based code can fail makes it challenging enough without adding the burden of surrounding aapplication code.

Keep your concurrency related code separate from other code.

##### 2. Limit The Scope Of Data.
The more places shared data can get updated, the more likely:

1. you will forget to protect one or more of those places.

2. there will be duplication of effort required to make sure everything is effectively guarded.

3. it will be difficult to determine the sources of failure.

Take data encapsulation to heart; severely limit the access of any data that may be shared.

##### 3. Use Copies Of Data.
A good way to avoid shared data is to avoid sharing the data in the first place.

##### 4. Threads Should Be As Independent As Possible.
Consider writing your threaded code such that each thread exists in its own world, sharing no data with any other thread.

#### Know Your Execution Models.
The various execution models in concurrent programming are:

1. Producer - consumer.

2. Readers - writers.

3. Dining philosophers.

Most concurrent problems will be some variation of these 3 problems. As a challenge, study these algorithms and write solutions using them.

#### Beware Dependencies Between Synchronized Methods.
Dependencies between synchronized methods cause subtle bugs in concurrent code.

Avoid using more than one method on a shared object. But, there will be times when you must use more than one method on a shared object, when this is the case, there are 3 ways to make the code correct:
1. Client-based locking.

2. Server-based locking.

3. Adapted server.

#### Keep Synchronized Sections Small.

#### Writing Correct Shut-Down Code Is Hard.
Writing a system that is meant to stay alive and run forever is different from writing something that works for a while then shuts down gracefully.

Graceful shutdown can be hard to get correct. Common problems include 'deadlock' with threads waiting to continue that never comes.

If you must write concurrent code that involves shutting down gracefully, expect to spend much of your time getting the shutdown to happen correctly.

#### Testing Threaded Code.
1. Treat spurious failures as candidate threading issues.

2. Get your nonthreaded code working first.

3. Make your threaded code pluggable.

4. Make your threaded code tunable.

5. Run with more threads than processors

6. Run on different platforms.

7. Instrument your code to try and force failures.

## ends here, the subsequent chapters are practical ones that I replicated in a testing environment.
