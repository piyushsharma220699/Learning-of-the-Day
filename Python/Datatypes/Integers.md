
Every integer object in python is stored in an object i.e. a PyObject. PyObject is a C structure.


### Integer Caching

Now, the thing is, in CPython, if two variables are assigned values between -5 to 256 (both inclusive), they will point to the same memory location & will return the same value when id() function is used. This can be seen here :

![[Pasted image 20230808221731.png]]

This is because : It is observed that smaller integers in the range -5 to 256, are used very frequently as compared to other longer integers and hence to gain performance benefit Python preallocates this range of integers during initialisation and makes them singleton. 

Hence, every time a smaller integer value is referenced instead of allocating a new integer it passes the reference of the corresponding singleton.

These small integer values are actually cached using an array of pointers. Whenever two variables are assigned the same small integer value, they are just pointing to the PyObject already created.