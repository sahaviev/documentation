# Key Design Principles

1. [What describes this document?](#what-describes-this-document)
2. [Why we need it?](#why-we-need-it)
3. [Principles](#principles)
4. [DRY](#dont-repeat-yourself)
    1. [What is DRY principle and how is it used?](#what-is-dry-principle-and-how-is-it-used)
    2. [Disadvantages of thoughtlessly using this principle](#disadvantages-of-thoughtlessly-using-dry)
5. [KISS - keep it short and simple](#kiss---keep-it-short-and-simple)
6. [YAGNI - you aren't gonna need it](#yagni---you-arent-gonna-need-it)
7. [APO - avoid premature optimization](#apo---avoid-premature-optimization)
    1. [What is APO principle and how it use?](#what-is-apo-principle-and-how-it-use)
    2. [Disadvantages of thoughtlessly using this principle](#disadvantages-of-thoughtlessly-using-this-principle)
8. [BDUF - big design up front](#bduf---big-design-up-front)
9. [SOLID - design principles](#solid---design-principles)

## What describes this document

This document summarizes the software development design principles. These principles are very popular, and it is not a secret or unspoken information.

These are the best practices that all developers must know, should understand and desirable to respect. At least until they come up with something better.

Development design principles are a set of certain guidelines that are given by experienced developers which they have learned from their mistakes while they were in development phase of software.

## Why we need it?

Written rules are better than thoughts in our heads or articles in the internet. Nobody will not be able to say "I didn't know".

Here in this article essential information about key design principles. We follow this rules.

## Principles

### Don't repeat yourself

#### What is DRY principle and how is it used?

Every piece of knowledge(business domain or algorithm) must have a single, unambiguous, authoritative representation within a system.

It is important to understand that the developer knows the difference between code duplicating and knowledge or algorithms duplicating.

1. **Knowledge duplication** is always a DRY principle violation.
2. **Code duplication** doesn’t necessarily violate the DRY principle.

#### Disadvantages of thoughtlessly using DRY

Trying to apply DRY everywhere can have two results:

1. Unnecessary **coupling**
2. Unnecessary **complexity**

Link: https://thevaluable.dev/dry-principle-cost-benefit-example

### KISS - keep it short and simple

There are two options for decoding the abbreviation: "keep it simple, stupid" and more correct "keep it short and simple"

If the project is simple, it is easy to understand(how it works, how to add new feature, how to fix etc...). Developing a simple project is not easy. It takes time. For any complex program, the final solution is obtained as a result of analyzing a huge amount of information. When the code is well-designed, it looks like it couldn't have been otherwise, but it is possible that its simplicity has been achieved as a result of intense mental work (and a lot of refactoring). It is difficult to do a simple thing. If the structure of the code seems obvious, you shouldn't think that it was easy.

DRY is hardest one of principles in practically implementation.

### YAGNI - you aren't gonna need it

Is a principle of extreme programming (XP) that states a programmer should not add functionality until deemed necessary. XP co-founder Ron Jeffries has written: "Always implement things when you actually need them, never when you just foresee that you need them."

Despite the banality, this is a very useful principle of software development and for products which requires further maintenance.
Following this principle meaning the features that are not described in the system requirements should not be implemented. This allows you to conduct development, guided by economic criteria - the customer should not pay for unnecessary functions, and the developers should not waste their paid time on the implementation of what is not required.

Developers violate this principle much more often than they think. Usually when they open merge request with new feature and some doubtful code with thoughts "this function/commented code/class will be need in the next n-week/sprint/year".
 
> In my experience: all the times when I declined merge-requests for YAGNI-code reasons,
> it is never returned later with next merge-requests...

### APO - avoid premature optimization

#### What is APO principle and how it use?

“Premature optimization is the root of all evil” - **Donald Knuth**.

Development is about money. The essence of this principle sounds developer must know how to spend time on development reasonably and does not make unnecessary optimizations at the moment.

If optimization is performing in early development, it might do more harm than good. Therefore, in the beginning it is more profitable to use simple, but not the most optimal solutions. In the future, having understanding how much this piece of code works slowly, change it to a faster solution or less resource-intensive algorithm.  The last reason of following this principle - during the implementation of most optimal algorithm from the start of development, the requirements might be changed and you will have to through the code into to the trash.

#### Disadvantages of thoughtlessly using this principle

If you leave optimization of important thing, the cost of later optimization might be very high, or it will be practically impossible to do it.

### BDUF - big design up front

This is the opposite of the YAGNI principle. BDUF states that before starting the development, it is necessary to think over and design in advance information system architecture, including small details, and only after that proceed with the implementation according to a prepared plan.

The principle should be used when the project requirements well known in advance, you have analytics, project design and clear understanding of development plan.

Link: https://en.wikipedia.org/wiki/Big_Design_Up_Front

### SOLID - design principles

“SOLID” is an acronym for software design principles, where each letter represents one of the following principles:

#### Single responsibility principle

The Single Responsibility Principle (SRP) means that a module should have only one reason to change. All code changes for this reason should be compiled in this module. This principle suggest to divide modules logically so that a change in business rules affects as less as possible modules, ideally only one.

Short technical explanation: *every module or class should have responsibility over a single part of the functionality provided by the software and that responsibility should be entirely encapsulated by the class*.

#### Open-closed principle

This principle means that modules should be designed without ideas about future changes in that module. Modules must be logically complete by itself. New functionality should be added only by creating new entities and/or composing them with old ones.

Feel the difference: closed changes is not meaning that you can not fix a bug in the module or make some minor changes e.g. renaming for refactoring reasons, closed changes mean that module will do the same tasks logically all the time during the lifespan.

The main goal of the principle is help to develop a project which will be resistant to changes, the lifespan of that projects should exceeds the lifespan of the first version of the product.

Short technical explanation: *software entities should be open for extension, but closed for modification.*

#### Liskov substitution principle

It sounds: functions that use a base type should be able to use subtypes of the base type without knowing it.

In other words, inherited classes should not contradict the base class. For example, they cannot provide a narrower interface. The behavior of inheritors should be expected for functions that use the base class.

It is very important principle that gives the following advantages:

1. helps to design the system based on the behavior of the modules;
2. introduces restrictions and rules for the inheritance, descendants should not contradict the basic behavior;
3. makes the behavior of modules consistent and predictable;
4. helps to avoid duplication, to allocate common for several modules functionality into a common interface;
5. allows you to identify(during the designing process) problematic abstractions and hidden relationships between entities .

Short technical explanation: *the inherited class should complement, not replace, the behavior of the base class.*

#### Interface segregation principle

Short description of the principle: many different interfaces are better than one big. This means that entities should not depend on interfaces they do not use.

When the principle is violated, modules are liable to all changes in the interface on which they depends. This leads to a high degree of coupling between modules.

Short technical explanation: *no client should be forced to depend on methods it does not use*.

#### Dependency inversion principle

The Dependency Inversion Principle(DIP) assumes: 

1. High-level modules should not depend on low-level modules; both types must depend on abstractions.
2. Abstractions should not depend on details, details should depend on abstractions.

According to the principle, modules should not directly depend on other modules, they should depends on abstractions.

Abstraction in this case is an interface that implements a specific module.

DIP is the essence of interface-based architecture design. DIP helps to reduce coupling between modules.

##### What are low-level modules?

Low-level modules - contain utilitarian functionality: access to the database, requests to the server, rendering of DOM elements on the page.

##### What are high-level modules?

High-level modules - contain complex, more concrete business logic. They are specific enough for reusing in different projects: e.g. user authorization, form validation, sending notifications

Short technical explanation: *developers should work at the interface level and not at the implementation level*.
