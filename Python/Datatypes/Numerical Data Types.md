All numerical datatypes in Python are IMMUTABLE. This ensures that the values of these objects remain consistent during their lifetime. 
## Integer

Every integer object in python is stored in an object i.e. a PyIntObject/PyLongObject, which is extended from PyObject. PyObject is a C structure. It is a base structure that holds common information about Python Objects, such as reference counting and Type Information along with their Value.

It looks somewhat like this:

![[Pasted image 20230808224013.png]]

Quite obvious, the TYPE here is INTEGER, Value is the value of that integer and reference count is the number of pointers pointing to this PyObject.
### Integer Overflow

In Python, value of an integer is not restricted by the number of bits and can expand to the limit of the available memory. This is because Python uses a technique called 'BigNum Arithmetic' to store and manipulate long integers. Thus, NO INTEGER OVERFLOW takes place.

The best explanation of BigNum Arithmetic : https://stackoverflow.com/questions/1218149/arbitrary-precision-arithmetic-explanation
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

There is a PyObject in Python, which is extended by PyFloatObject, similar to what we do with integers.
## Floating Point Approximation

The floating point numbers in Python are stored using the IEEE 754 Standard. 
Take a Decimal Number, Convert it into binary form. Then convert it into below :

>>>(-1)^(sign bit) * 1.(matissa) * 2^(exponent)

So basically, if we have 32 bits as follows :
- 1 bit is sign bit (0 for positive and 1 for negative)
- 8 bits are exponent bits (Actually Exponent + Bias where the bias is 127)
- 23 bits are mantissa bits (representing fractional part of the number)

Similarly, if we have 64 bits :
- 1 bit is sign bit (0 for positive and 1 for negative)
- 11 bits are exponent bits (Actually Exponent + Bias where the bias is 1024)
- 52 bits are mantissa bits

Link : https://www.log2base2.com/storage/how-float-values-are-stored-in-memory.html

