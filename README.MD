# UML Study

This is part of my self-study to become a better programmer.

PlantUML is used for quick creation of UML diagrams.
The [PlantUML Online Editor](https://www.planttext.com/) I use.

Unified Modeling Language (UML) is a general-purpose, developmental, modeling language in the field of software engineering, that is intended to provide a standard way to visualize the design of a system.


## Structural UML diagrams
describes the static features of the system

+ Class diagram*
+ Component diagram
+ Composite structure diagram
+ Deployment diagram
+ Object diagram
+ Package diagram
+ Profile diagram

## Behavioral UML diagrams
describes the interaction in the system;
shows dynamic behavior

+ Activity diagram*
+ Communication diagram
+ Interaction overview diagram
+ Sequence diagram*
+ State diagram
+ Timing diagram
+ Use case diagram*

### S: Class Diagram

### B: Activity Diagram

### B: Sequence Diagram

### B: Use Case Diagram
+ Actor: Entity that performs a role
+ Use Case: Function within the system
+ System: Define the scope of the use case
---
+ [include vs extends](https://stackoverflow.com/questions/1696927/whats-is-the-difference-between-include-and-extend-in-use-case-diagram "Stackoverflow Answer")

**Extend** is used when a use case adds steps to another first class use case.

For example, imagine "Withdraw Cash" is a use case of an ATM machine. "Assess Fee" would extend Withdraw Cash and describe the **conditional "extension point"** that is instantiated when the ATM user doesn't bank at the ATM's owning institution. Notice that the basic "Withdraw Cash" use case stands on its own, without the extension.

**Include** is used to extract use case fragments that are duplicated in multiple use cases. The **included use case cannot stand alone and the original use case is not complete without the included one.** This should be used sparingly and only in cases where the duplication is significant and exists by design (rather than by coincidence).

For example, the flow of events that occurs at the beginning of every ATM use case (when the user puts in their ATM card, enters their PIN, and is shown the main menu) would be a good candidate for an include.

---

Question: "Do you know that it costs a lot of money to get a ’Certified Java Programmer’ certificate? It
could cost you thousands of euros. Let’s imagine we will develop a browser-based training
system to help people prepare for such a certification exam.

A user can request a quiz for the system. The system picks a set of questions from its
database, and compose them together to make a quiz. It rates the user’s answers, and gives
hints if the user requests it.
2

In addition to users, we also have tutors who provide questions and hints. And also examinators
who must certify questions to make sure they are not too trivial, and that they are
sensical.

Make a **use case diagram** to model this system. Work out some of your use cases. Since we
don’t have real stake holders here, you are free to fill in details you think is sensical for this
example.

![alt text]( /usecase_quizsystem.png "Quiz System")

'''
@startuml
title Use Case Diagram

actor :User: as U
actor :Tutor: as T
actor : Examinator: as E

left to right direction
skinparam monochrome true
skinparam packageStyle rectangle
rectangle (Quiz-System){

    U -- (Make a Quiz)
    (Make a Quiz) .> (Report Result) : include
    (Provide hint) .> (Make a Quiz) : extends
    (Add Questions) -- T
    (Certify Questions) -- E
    (Add Questions) .> (Certify Questions) : include
}

@enduml

'''

Use Case Diagram of Partystarter, a web application project I did for [EE4717 module](https://github.com/xiongchenyu6/web_design) in NTU.
It is an event management online portal where registered users are able to:
+ create a party
+ browse party listing from database
+ join any existing party

'''

@startuml
title Use Case Diagram

actor :User: as U
actor :Web Master: as W
actor :Generic Payment System: as P


left to right direction
skinparam monochrome true
skinparam packageStyle rectangle
rectangle (Partystarter){

    U -- (Login)
    U -- (Create Party)
    (Create Party) .> (View Guestlist) : include
    (Create Party) .> (Cancel Party) : include
    U -- (Join a Party)
    (Join a Party) .>  (Make Payment) : include
    (Make Payment) -- P
    (Join a Party) .> (Withdraw) : include
    (View other Partygoers) .> (Join a Party) : extends
    (Join a Party) .> (Check Vacancies) : includes
    U -- (Browse Party Listing)

    (Manage Users) -- W
    (Manage Parties) -- W
    (Manage Parties) .> (Cancel Party) : include
    note right of (Manage Parties)
        Web Master can delete inappropriate listing
    end note
}

@enduml

'''

*side note: plantuml looks really messy without formatting :( *

![alt text]( /usecase_partystarter.png "Partystarter")

[More Examples](https://www.lucidchart.com/pages/uml/use-case-diagram)

## Useful Resources/ References:
+ [Tutorialspoint: UML](https://www.tutorialspoint.com/uml/)
+ [Youtube: UML 2.0 Tutorial](https://www.youtube.com/watch?v=OkC7HKtiZC0&list=PLGLfVvz_LVvQ5G-LdJ8RLqe-ndo7QITYc)
+ [Use Case Solutions](http://www.cs.uu.nl/docs/vakken/mso/1011/asgs/usecase.sol.pdf)
