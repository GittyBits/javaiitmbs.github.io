<img src="../assets/logo.png" width=30% />

<hr>
<span style="display:flex; justify-content: space-between;">
	<a href="../index.html">Home</a> <a href="../week-2/summary.html">Week-2</a>    
</span> 
<hr> 

# Java - Week 1

[TOC]
# Programming concepts:
## Programming languages
### Programming language:
### Compiler:
* Entire
* Fast
* More memory 

### Interpreter
* Line by Line
* Slow
* Less memory

## Programming styles 

### Imperative programming:	 
* Deals with "how" we want to achieve
* Use intermediate variables

**Example:**
```python
def factorial(n):
	f = 1
	while n > 0:
		f = f * n
		n = n - 1
	return f
print(factorial(5))
```

### Declarative Programming: 
* Deals with "what" we want to achieve
* No intermediate variables

**Example:**
```python
def factorial(n):
	if n == 1 or n == 0:
		return 1
	else:
		return (n * factorial(n - 1))
print(factorial(5))

```

## Memory management
Whenever a function is invoked for execution, function needs memory for local variables, these local variables are used to store the intermediate results.  
### Activation Record
**Example:**
```python
def factorial(n):
	if n == 1 or n == 0:
		return 1
	else:
		return (n * factorial(n - 1))
print(factorial(3))

```

<img src="../assets/Activation records.jpg" width=30% />

* Control link acts as a pointer to the function that is being called
* Return value link as the name says itself stores the value to be returned
* Call is always from lower to higher
### Heap memory 
* Basically two types of memmory
* Heap and Stack
* Heap is dynamic which means it would be created at the time of execution
* Used when new objects are created such as LinkedList whose size can grow and shrink whenever a node is inserted/deleted


### Modular software development

There are two important concepts in modular program development: 

* `Interface`: Description of the parts 
* `Specification`: Description of the behavior of a component
  
## Object-oriented programming
There are few basic concepts of object-oriented programming (OOP).
### Object
Object are like abstract datatypes. Every object has its own data (also called state) and operations (also called methods/messages). A program written in object-oriented style will consist of interacting objects. For example, a `Student` object may consist of data such as name, gender, birth date, home address, phone, and age, and operations for assigning and changing these data values. 
### Inheritance

Inheritance is the process by which one object re-use the implementations of another object.  Using inheritance we can use the functionality of `Employee` in the `Manager` class. You can also add extra functionality to the `Manager` like `date of promotion, seniority (in current role)` as every `Manager` is alo an `Employee`.    

### Subtyping
A subtype is a specialization of a type, If A is a subtype of B, wherever an object of type B is needed, an object of type A can be used. Every object of type A is also an object of type B. If f() is a method in B and A is a subtype of B, every object of A also supports f().

Consider the code given below:

    class Employee:
        def __init__(self,n='',s=0.0):`
           self.name = n
           self.salary = s
        def bonus(self):
           return(0.1*self.salary)`
    class Manager(Employee):
        def __init__(self,n='',s=0.0):
           self.name = n
           self.salary = s
        def bonus(self):
           return(0.2*self.salary)`

Here `Manager` is a subtype of an `Employee`. Wherever an object of `Employee` (super type) is required, an object of `Manager`can be used.
If  bonus() is a function in `Employee` and `Manager` is a subtype of `Employee`, every object of `Manager` also supports bonus(). Implementation of bonus() can be different in `Manager`.

### Inheritance vs Subtyping

In object-oriented programming, inheritance and subtyping both are essential.

- Subtyping refers to compatibility of interfaces. A type `A` is a subtype of `B`, wherever an object of type `B` is needed, an object of type `A` can be used. 
- Inheritance refers to reuse of implementations. If a type `A` inherits from another type `B`, then `A` can reuse the functionality of `B` without redefining it, and type`A` can also add more features to it if required. 

Consider the data structure deque, a double-ended queue. A deque supports insertion and deletion at both ends, so it has four functions `insert-front`, `delete-front`, `insert-rear` and `delete-rear`. If we use just `insert-rear` and `delete-front` we get a normal queue. On the other hand, if we use just `insert-front` and `delete-front`, we get a stack. In other words, we can implement queues and stacks in terms of deques, so as datatypes, `Stack` and `Queue` inherit from `Deque`. On the other hand, neither `Stack` nor `Queue` are subtypes of `Deque` since they do not support all the functions provided by `Deque`. In fact, in this case, `Deque` is a subtype of both `Stack` and `Queue`  

### Dynamic lookup

Dynamic lookup means that a method to be invoked at run time, according to the implementation of the object that receives a message. The important property of dynamic lookup is that different objects may implement the same method differently. 

Dynamic lookup is an important part of object-oriented programming. Consider, for example, a simple graphics application that draws the shapes such as squares, circles, and triangles. Each square object may contain a draw method with code to draw a square, each circle a draw method that contains code to draw a circle, and so on. When the program wants to draw a given shape, sending a draw message to each shape. The part of the program that sends the draw message does not have to know which kind of shape will receive the message. Instead, each shape receiving a draw message will know how to draw that shape. This makes sense because the programmer  who implements a specific shape knows how to draw that kind of shape.

## Classes
A class is a template that describes what objects can and cannot do. An object is an instance of a class. Class describes how data is stored in objects and how the public functions/methods manipulate this data. 

### Example: 2D points 

To understand the basic ideas and limitations of the Python language, consider the following example program in Python.

 ```pyt
class Point:
	def __init__(self,a=0,b=0):
		self.x = a
		self.y = b
 ```

In the above example, the class `Point` is defined. Each instance of the `Point` class has its own instance variables `x` and `y`. These instance variables store the `x` coordinate and `y` coordinate of a point in a 2D space, allowing us to identify the location of a point in 2D space. 

For example, if `p1` and `p2` are two instances of the `Point` class, then the instance variables associated with `p1` and `p2` are denoted as `p1.x`, `p1.y`, `p2.x`, and `p2.y`. 

### Adding methods to a class

We can manipulate the object's internal data by adding functions in the class. For example, if we want to shift a point by a certain amount given by $\Delta x$ and $\Delta y$, we can define a function for it. 

After shifting, the point becomes ($x$, $y$) $\to$ ($x + \Delta x$, $y + \Delta y$).  

You can also calculate the distance from the origin using the formula:

d = $\sqrt{x^2 + y^2}$ , we can define a function for it.   $x$   

```python
class Point:
	def __init__(self,a=0,b=0):
		self.x = a
		self.y = b
	def translate(self,dx,dy):
		self.x += dx
		self.y += dy
	def odistance(self):
		import math
		d = math.sqrt(self.x*self.x +
		self.y*self.y)
		return(d)
```

### Changing the internal implementation

Now let's see how to represent a point in terms of distance $r$ and angle $\theta$, which is called the polar representation. In the polar representation, a point is denoted by ($r$ , $\theta$), where $r$ represents the distance from the origin and $\theta$ represents the angle measured from the x-axis.

$r$ =    $\sqrt {x^2 + y^2} $

$\theta$ =  $ {tan^-1}$  ($y$ / $x$)

```python
import math
class Point:
	def __init__(self,a=0,b=0):
		self.r = math.sqrt(a*a + b*b)
		if a == 0:
			self.theta = math.pi/2
		else:
			self.theta = math.atan(b/a)
	def odistance(self):
		return(self.r)
```

In above program we are passing $x$ and $y$ values but internally polar coordinates ($r$ , $\theta$)   were initialized using these values. Here user not aware  that internally instead of $x$ and $y$ the instance variables have changed to $r$ and $\theta$.   

To translate the polar coordinates to Cartesian coordinates, we can convert ($r$ , $\theta$)  to ($x$ , $y$) using the following formulas:

$x = r \cdot \cos(\theta)$

$y = r \cdot \sin(\theta)$

Now recompute the polar coordinates ($r$ , $\theta$) from ($x$ + $\Delta$ $x$, $y$ + $\Delta$ $y$)

```python
def translate(self,dx,dy):
	x = self.r*math.cos(self.theta)
	y = self.r*math.sin(self.theta)
	x += dx
	y += dy
	self.r = math.sqrt(x*x + y*y)
	if x == 0:
		self.theta = math.pi/2
	else:
		self.theta = math.atan(y/x)
```

We can use the same constructor definition to set both the cartesian coordinates ($x$, $y$) and polar coordinates ($r$, $\theta$). In this way, the constructor definition remains unchanged, and the user does not need to be aware of whether the representation is in terms of ($x$, $y$) or ($r$, $\theta$). 

### Abstraction:

The purpose of abstraction is to hide the implementation details from the user. In the case of the `Point` class, the user should not be concerned about whether it represents cartesian coordinates ($x$, $y$) or polar coordinates ($r$, $\theta$). Even though the constructor remains the same, the internal representation may vary. This allows the user to interact with the `Point` object using a consistent interface, regardless of how the data is actually stored internally. 

```python
class Point:
	def __init__(self,a=0,b=0):	
		self.x = a
		self.y = b
```

In above program point representation is ($x$ , $y$). 

```python
class Point:
	def __init__(self,a=0,b=0):
		self.r = math.sqrt(a*a + b*b)
		if a == 0:
			self.theta = math.pi/2
		else:
			self.theta = math.atan(b/a)
```

In above program point representation is ($r$ , $\theta$). 

In Python, direct access to instance variables from outside the class is allowed, which means that abstraction is not enforced in the language.

```python
p = Point(5,7)
p.x = 4 # Point is now (4,7)
```

In the above code, during object creation, the arguments (5, 7) are passed to the constructor. However, the statement `p.x = 4` changes the value of `x` to 4, resulting in a new state of the object as (4, 7). According to the concept of abstraction, this should not happen, as it violates the idea of encapsulation and can have an impact on other parts of the code. In Python, abstraction is highly dependent on the discipline of the programmer to respect the encapsulation and not access or modify the internal implementation details directly.

### Subtyping and inheritance

Let's explore the concept of subtyping and inheritance in the context of Python.

```python
class Rectangle:
	def __init__(self,w=0,h=0):
		self.width = w
		self.height = h
	def area(self):
		return(self.width*self.height)
	def perimeter(self):
		return(2*(self.width+self.height))
class Square(Rectangle):
	def __init__(self,s=0):
		self.width = s
		self.height = s
```

In above example `Rectangle` has two dimensions a `width` and `height`.  We have a constructor for `Rectangle` to initialize the internal instance variables `self.width` and `self.height`. And has two public functions `area` and `perimeter`.

Now one more class `Square` is defined, a square is a rectangle in which the width is equal to the height. So, we can now define a `Square` to be a sub type of `Rectangle`. In Python we do this is that in the class definition of square put the type `Rectangle` in the bracket.

Here `Square` is a specialization of a `Rectangle` and here we can define a new constructor because `Square` have one quantity that is `side` it do not have a `width` and a `height` and will reset the width and the height both using `side` value. The constructor of `Square` that we have defined here is different from `Rectangle` there because there we got two parameters and we set them but here we get only one parameter.

```python
s = Square(5)
a = s.area()
p = s.perimeter()
```

In above I want a `Square` with side 5 this will create implicitly an object which has width and height values as 5. After that now calling `s.area()` for the area of the square, will return a legitimate value of 25 even though inside this there is no `area` function here. This is the idea of inheritance. `Square` is a sub type of `Rectangle` the functions which are defined inside `Rectangle` are available to `Square`.  So, we do not have to redefine them unless we want to change them. So, `perimeter` and `area` are both inherited by `Square` from `Rectangle`. 

```python
class Rectangle:
	def __init__(self,w=0,h=0):
		self.width = w
		self.height = h
	def area(self):
		return(self.width*self.height)
	def perimeter(self):
		return(2*(self.width+self.height))
class Square(Rectangle):
	def __init__(self,s=0):
		self.side = s
```

Now suppose if I decided that in a `Square` I do not want to keep track of two separate variables there is only one variable that is `side`. Now if we try the same code which earlier work due to inheritance. These two functions will now at run time they will fail.

Statically these functions are available because `Square` has been defined to be a subtype of `Rectangle`. So, those functions are available to `Square`. So, if they are not defined in `Square` and if I say `s.area()` Python has no way to know before running the code that this `s.area()` will not work. But when it actually comes to executing `s.area()` it will check that these quantities `self.width()` and `self.height()`.

Here `Square` constructor changing the instance variable `self.side` but we did not update `self.width` or `self.height` explicitly. Since we did not update them they become undefined variables. So `perimeter` and `area` are used for their calculations because self `s.width` and `s.height` have not been defined.

The subtype `Square `is not forced  be an extension of the parent type. The subtype can do everything the parent type will do and more and in particular that means that it should have all the instance variables that the parent type would have declared and more because the functions would use these instance variables. But here in Python we are able to do this, we can set up instance variables in the subtype and omit some instance variables from the parent type. So, this is clearly not a good thing.

















