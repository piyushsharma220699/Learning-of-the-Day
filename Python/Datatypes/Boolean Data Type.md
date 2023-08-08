In python, boolean data type 'bool' can have only two values, True or False. They are actually stored in the struct named PyBoolObjects, which are an extension type of PyObject struct.

Also, if two variables have the same boolean value, they're actually pointing to the same PyObject. Different objects are not created, just the reference count of the objects get created.

![[Pasted image 20230808225546.png]]

The above code will look somewhat like this in the memory:

![[IMG_2241.jpeg]]