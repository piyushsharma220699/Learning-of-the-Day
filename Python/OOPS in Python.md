
OOPs is a programming paradigm that uses classes and objects in programming & aims to implement real world entities.

## Constructors in Python

Constructors instantiate an object of a class. It is called every time you create an object of a class. They basically assign values to the data members of the class when an object is created.

>>> This is done using the _ _ init _ _ () function.

#### Types of Constructors

1. Default Constructor : Doesn't accept any argument & has only one argument i.e. self
2. Parameterised Constructor : Accepts arguments.

To make the Constructor accept any number of arguments, we use args and kwargs.

![[Screenshot 1402-05-13 at 2.38.58 PM.png]]
#### Limitations of Constructors in Python

1. Function Overloading is not possible. So if you have more than one _ _ init _ _ () functions in your class, the one written in the last will get executed.

![[Pasted image 20230804142838.png]]

2. There are no Access Modifiers in Python. Thus, there will be nothing like public, private and protected classes.

## Destructors in Python

These are called when the object gets destroyed OR all references to the object have been deleted. However, these are not needed as importantly as in C++ since Python has it's own garbage collector which handles memory management automatically.

>>> Still, a destructor is created using the _ _ del _ _ () method

