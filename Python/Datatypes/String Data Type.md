Strings are also immutable and are stored as a PyObject in Python. 

a = "qwerty"
b = "qwerty"

Here, the address of a and b are same in Python. So we have a PyObject in Python with :

Type : String
Value : "qwerty"
Reference Count : 2 (one for a and other for b)

now if we do :

a = "qwertyiop"
b = "qawsedrd"

The Reference Count of the PyObject created above becomes ZERO, and thus the garbage collector does the job of releasing the memory of that object.

Strings are stored **as individual characters in a contiguous memory location**.
It can be accessed from both directions: forward and backward.

4 bytes per charater are taken in Python3 depending on encoding
https://rushter.com/blog/python-strings-and-memory/
As you can see, depending on the content of a string, Python uses different encodings.

an empty string takes 49 bytes of memory.