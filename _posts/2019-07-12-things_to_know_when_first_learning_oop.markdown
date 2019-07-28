---
layout: post
title:      "Things to Know When First Learning OOP"
date:       2019-07-12 21:29:51 -0400
permalink:  things_to_know_when_first_learning_oop
---


The first programming language I learned when I returned to school for a career change was Java. Trying to learn Java as a complete beginner, who knew little-to-nothing about programming, is… laughable. Java is difficult, and my goodness, I had one hell-of-a-time trying to learn OOP with it. It was not fun.

Fast forward to now, and here I am, learning OOP again, but this time, in Ruby. Ruby, being an extremely friendly language to learn, has helped clear up A LOT of confusion I initially had. I can confidently say that I understand OOP (for the most part, haha) and enjoy it quite a bit!

Since this is the second time around I’ll be learning OOP, I realized that, initially, I didn’t understand the jargon being used and what each thing does or how it looks in code. This was the BIG reason why I was so lost when first trying to learn it. Luckily, I’ve created a list of the terms that you'll run into over and over (and over) again. Knowing and understanding these terms should make the learning OOP a lot easier.

<div align="center"><img src="https://media1.tenor.com/images/63abe189905c035be66de6c3b548b825/tenor.gif?itemid=13134027" width="40%"></div>
<br />
<hr />

<h3>Object </h3>
<p>A specific thing you create from a class, its own individual. All objects are created from a class.</p>


<h3>Class </h3>
<p>This is the very first thing you’ll be creating in your object-oriented code. Without it, you wouldn’t be able to create anything. A class is the blueprint (the template, the structure, the fundamental building blocks) for creating objects. Class names are usually nouns, and I think of it as the general name for the object you’ll be creating. A class name begins with a capital letter, and if there is more than one word for your class, the class name should always be CamelCased (<-- just like that).</p>

```
class Person
   # some code to describe a person
end
```


<h3>Instance </h3>
<p>Instance and object go hand-in-hand. An instance is the occurrence of an object, and all instances are unique. For example, let’s say we’re creating a person. I’m a person and you’re a person--we both have eyes, a head of hair, hands, etc., and we have similar behaviors, like walking and talking. But just because we are both have the “blueprint” of a person, it doesn’t make us the same person. We are our own individual.</p>

<p>Now bringing it back to OOP, person would be the class (because that’s what we are) and an instance would be me and another instance would be you (because we are each a specific and unique type of person).</p>


<h3>Instantiate</h3>
When you instantiate something, it means that you are creating a new object/a new instance from a class. This is done using the .new method. The syntax to instantiate something is --> variable_name = ClassName. new

```
class Person 
end

jane_doe = Person.new   # instantiating a new object from Person class
john_doe = Person.new   # and another new object from the same class
```


<h3>Instance Methods</h3>
<p>These are, simply, methods defined in a class that tell the object what to do when called on.</p>

```
class Person
   # defining an instance method
   def talks
      puts “Hey there!”
   end
end

jane_doe = Person.new
jane_doe.talks --> “Hey there!”   # calling the instance method
```


<h3>Instance Variables</h3>
<p>Unlike the variables that we’ve been working with, where the scope is smaller and are only accessed within a local environment (usually, it can only be accessed in the method that it is in), instance variables can be used inside ANY instance method. To differentiate the two within our code, instance variable names always start with the @ symbol.</p>


<h3>Setter</h3>
<p>This setter method (aka the writer) sets a new value for the instance variable. A good way to tell what a setter method is by the = sign that is added to the method name.</p>


<h3>Getter</h3>
<p>The getter method (aka the reader) reads the value that was set for the instance variable.</p>

```
class Person
   # sets/writes the name
   def name=(name)
      @name = name
   end

   #gets/reads the name
   def name
      @name
   end

   def talks
      puts “Hey there!”
   end
end

jane_doe = Person.new
jane_doe.talks --> "Hey there!"
jane_doe.name = “Jane Doe”   # sets/reads the name
jane_doe.name --> “Jan Doe”   # gets/reads the name
```
<br />
<hr />

These are just the basics, so of course, there is a lot more to know. But as someone beginning to write code in object-orientation, I think these are some of the most important ones to initally understand. By knowing what each term is, what it does, how they relate to each other, and how it looks in code, catching on to the rest of what OOP has to offer won't be so bad.



