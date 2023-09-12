
## Integer

Every integer object in python is stored in an object i.e. a PyIntObject/PyLongObject, which is extended from PyObject. PyObject is a C structure. It is a base structure that holds common information about Python Objects, such as reference counting and Type Information along with their Value.

It looks somewhat like this:

![[Pasted image 20230808224013.png]]

Quite obvious, the TYPE here is INTEGER, Value is the value of that integer and reference count is the number of pointers pointing to this PyObject.
### Integer Overflow

In Python, value of an integer is not restricted by the number of bits and can expand to the limit of the available memory. This is because Python uses a technique called 'BigNum Arithmetic' to store and manipulate long integers. Thus, NO INTEGER OVERFLOW takes place.
### Integer Caching

Now, the thing is, in CPython, if two variables are assigned values between -5 to 256 (both inclusive), they will point to the same memory location & will return the same value when id() function is used. This  can be seen here :

![[Pasted image 20230808221731.png]]

This is because : It is observed that smaller integers in the range -5 to 256, are used very frequently as compared to other longer integers and hence to gain performance benefit Python preallocates this range of integers during initialisation and makes them singleton. 

Hence, every time a smaller integer value is referenced instead of allocating a new integer it passes the reference of the corresponding singleton.

![[IMG_2239.jpeg]]

These small integer values are actually cached using an array of pointers. Whenever two variables are assigned the same small integer value, they are just pointing to the PyObject already created.

Basically, x = -5 will just increase the reference count of the PyObject having value as -5 by 1 and will make x point to that PyObject.

>>> Integer Caching will only take place if the Integer falls in the range of -5 to 256 (both inclusive). Otherwise a new object will be created every time during initialisation.

## Float


