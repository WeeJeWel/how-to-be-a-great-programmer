# Hierarchy is everything

I strongly believe that the smartest people share only one trait: they understand that **everything is hierarchy**.

Our world is full of hierarchies. They're either one-to-one, one-to-many or many-to-many.
The most important skill to have is to traverse this tree-structure in your mind.

Let's take a school for example. You're one of many students in a class. You have one teacher.

| | Teacher | |
|---|---|---|
| Student | Student | Student |

But from the teacher's perspective, he's just one of many teachers. He has one director to report to, though.

| | | | Director | | | |
|---|---|---|---|---|---|---|
| | Teacher | | | | Teacher | |
| Student | Student | Student | | Student | Student | Student |

Let's say you were to design an application. By looking at this diagram it's clear that you need three classes: `Director`, `Teacher` and `Student`.

But what do these people have in common?

| **Director** | | | | Dr. A | | | |
|---|---|---|---|---|---|---|---|
| **Teacher** | | Mr. B | | | | Mr. C, PhD | |
| **Student** | Anakin | Luke | Leia | | Han | Padme | Student |

We can deduct that _everyone_ has a name. And _some_ have a gender. So there are some shared properties. In our schema it looks like only teachers have a gender. And if you look more closely Teachers and Directors _can_ have a degree.

Our class schema therefore looks like this:

* Person
  * .name (String)
  * .gender (Male/Female/null)
  * Director
    * .degree (Dr, PhD, null)
  * Teacher
    * .degree (Dr, PhD, null)
  * Student
    
Can you see the duplicated data? This means that both Teacher and Director can share a _degree_. They have something in common, and therefore share a common parent class. Because they share this property we can move them one down in the hierarchy:

* Person
  * .name (String)
  * .gender (Male/Female/null)
  * Employee
    * .degree (Dr, PhD, null)
    * Director
    * Teacher
  * Student

What if a student should also be able to have a degree? Well, you could throw everything aboard:

* Person
  * .name (String)
  * .gender (Male/Female/null)
  * .degree (Dr, PhD, null)
  * .role (Director, Teacher, Student)
  
But experience might tell you that an Employee has a few other properties than Students. For example _salary_:

* Person
  * .name (String)
  * .gender (Male/Female/null)
  * Employee
    * .degree (Dr, PhD, null)
    * .salary (Number)
    * Director
    * Teacher
  * Student
  
Adding _salary_ to a student and setting it to 0 or null is just ugly.

Learn to view everything in the world as a hierarchy and you will become a great programmer.
