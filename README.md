# Object Orientation

Developers have different design choices when structuring their code. **Object Orientated Programming** is a common way to organize, manipulate and store data in an application.

## Objectives
1. Understand and Explain the purpose of classes
2. Create a new Python Class
3. Initialize instances of a Pythong class
3. Add Class attributes
4. Add Class methods

## Introduction

Object orientation is one of the most powerful concepts in programming, and today that power will be yours. You'll learn about how we can create 'blueprints' (known as classes) which build objects that mirror or model real world objects, relationships, and environments.

When you log into Google Plus, how is your exact profile and data loaded, and not someone else's? How does that work? How in the world are they able to do that for 2 billion users?

Object orientation (OO) is the way that all of those users, likes, photos and profiles are stored, manipulated and organized. Object orientation is one of the most important and pervasive concepts in computer programming and supports all sorts of applications like Instagram and Facebook, ESPN and Amazon.

## Classes and Instances
In Python, whenever we create a new instance (version) of something, we have been limited to assign it to a string, number, list or dictionary.

```Python
>>>dog = "Rover"
>>>dog2 = "Max"
```
But we can add new level of meaning to our program by making a *user-defined* data type called a **class**. Using classes, we can build new objects that better represent the kinds of things in our program. Think of a class like a factory that produces different individual 'items' (which we'll call *instances*) based on a template or blueprint.

The keyword `class` allows us to define a new "thing", called an object, in our program.

```python
class Dog:
  def __init__(self, name):
    self.name = name
    self.age = 0
```

(You can follow along by copy and pasting the `Dog` class into a Python interpreter, or by creating a new `.py` file. Just remember to hit <kbd>Enter<kbd> twice if you're using the interpreter.)

Now we have a new data-structure called `Dog`. When `Dog` is defined by using the `class` keyword, a dog isn't actually created. Instead, the Dog class is a sort of instruction manual or blueprint for constructing one or more "Dog" objects.

###`__init__` and `self`

Whenever a class is created, the initializer method, `__init__()` needs to be written. This method gets automatically called each time a new object is "born." This method allows a programer to make sure that each object has certain characteristics from the get-go. In this example, every new instance (or unique representation) of a Dog object will have a name and an age.

The `self` parameter references the newly created object. In this case, each instance of the `Dog` object can have a unique name, the one it was born with. All new objects will also start with an age of 0. `self.name` and `self.age` are called instance variables.

## Object Initialization
In order to create a new dog, we simply call the class name `Dog` with any parameters that are defined in the Dog classes' `init()` method. So far, the only parameter we need to pass it the name of our dog:

```
>>>pet1 = Dog("Fido")
```
This code instantiates an object, pet1 of class Dog, with a name of Fido. Because the second line of the initializer method gives all Dog objects an age of 0, `pet1` will also have an age of 0:

```
>>>pet1.name
'Fido'
>>>pet1.age
0
```

Behold, a new pet of class `Dog` has been born with the name Fido and with an age of 0.
We can easily give Fido a few more friends:
```python
>>>pet2.Dog("Rover")
>>>pet3.Dog("Brian")

```

## Attributes

Name and age, are known as attributes - descriptors that allow us to add more data to our objects. If we wanted our dog to have a breed, we could add that into the initializer method of our `Dog` class.
```python
class Dog:
  def __init__(self, name, breed):
    self.name = name
    self.age = 0
    self.breed = breed
```

To access or modify the attributes of an object, use dot notation.

```python
>>>pet4 = Dog("Snoopy", "Labrador")
>>>pet4.breed = "Beagle"
```

When we changed `pet4`'s breed, this didn't affect any of the other code. This is an example of encapsulation, which means that we can change as much as we want about an instance of an object, without changing the class that describes that object. The instructions for creating a class are encapsulated - hidden - from the actual objects themselves.

Try creating another attribute "size", and then instantiating a few new Dog objects with different size attributes.

## Methods

An object's attributes are it's adjectives - the characteristics that define it. But many objects aren't static - they **do** things. We give objects "verbs" that we call **methods**.

A method is exactly like a function, except that a method can only be invoked on instances within a class. We have already used string methods, list methods and dictionary methods.

```python
>>>animal="cow"
>>>animal.upper() #.upper() is a string method.
'COW'
>>>animals=["cow", "donkey", "llama"]
>>>animals.append("armadillo") #.append() is a list method.
>>>animals
['cow', 'donkey', 'llama', 'armadillo']
>>>baby_names={'cow':'calf', 'donkey':'colt', 'llama':'cria', 'armadillo':'pup'}
>>> baby_names.keys() #.keys() is a dictionary method.
['donkey', 'armadillo', 'llama', 'cow']

```
Each method is specific to the object's class: We can use `.keys()` on a dictionary object, but not on a list object.

Methods are functions, just within specific classes. As such, we can add methods to classes by using normal Python function syntax.

```python
class Dog:
  def __init__(self, name):
    self.name = name
    self.age = 0
  def bark(self):
    print "Woof!"
```

```python
>>> dog1=Dog("Ben")
>>> dog1.bark()
Woof!
```
Methods can also use instance variables - which are global - and can be accessed anywhere within the class definition.

```python
class Dog:
  def __init__(self, name):
    self.name = name
    self.age = 0
  
  def bark(self):
    print "Woof!"

  def get_older(self,years):
    self.age=self.age + years
```

```python
>>> pet4=Dog("Bailey")
>>> pet4.age
0
>>> pet4.get_older(2)
>>> pet4.age
2
>>> pet4.get_older(3)
>>> pet4.age
5

```

Before, when we wanted to create a value that represented a dog, we were limited to predefined classes: strings, lists and dictionaries. With classes, we can create new data types with their own attributes and methods. These classes are used to create one or many objects that have similar characteristics and can perform actions specifically designed for themselves.

## Facebook Example

Before you practice using classes to create objects. We all know that a facebook profile has a few basic characteristics (name, number of likes, friends) and actions (like, accept a request, send a message). Take a look at this example of how we could start to represent a Facebook profile using classes. 

```python
class Profile:
  def __init__(self, name):
    self.profile_title = name
    self.likes = 0
    self.friends = {}

  def accept_friend_request(self, friend, friend_url):
      self.friends[friend]= friend_url

  def like(self):
      self.likes += 1

  def send_message(self, friend, message):
       print "\"{}\" will be posted to the following url:{}".format(message,self.friends[friend])
```
When a new profile is created, it gets three attributes assigned to it, the profile_title, 0 likes and an empty dictionary to keep track of friends and their urls.

When the like method is called, the profile's likes increases by one:
```python
>>> tom_profile=Profile("Tom Haverford")
>>> tom_profile.likes
0
>>> tom_profile.like()
>>> tom_profile.likes
1
```

When friend requests are accepted, those friends are added to a friends dictionary:

```python
>>> tom_profile.accept_friend_request("Jean-Ralphio Saperstein", "facebook.com/CAASHizle")
>>> tom_profile.accept_friend_request("Leslie Knope", "facebook.com/futureMRSBiden")
>>> tom_profile.friends                                                         
{'Leslie Knope': 'facebook.com/futureMRSbiden', 'Jean-Ralphio Saperstein': 'facebook.com/CAASHizle'}
```

The `send_message()` method take two parameters, the friend's name and the message being sent. It uses the `self.friends` instance variable to get the correct url to post to.
```python
>>> tom_profile.send_message('Jean-Ralphio Saperstein', "I hope you have a change of clothes, because your eyes are about to piss tears")
"I hope you have a change of clothes, because your eyes are about to piss tears" will be posted to the following url:facebook.com/CAASHizle
```

This perfunctory example examines some attributes and methods a Facebook profile might have and shows how complex objects can be created in an organized way.

## Conclusion
Object-oriented programming is a powerful way to make seemingly complex code reliable and easier to maintain and change. Object-orientation is a design pattern that provides a simple way of building any type of new object.
