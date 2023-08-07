Generator Functions are special type of functions which create an iterable sequence of values. This function returns a generator object, which can be used to generate values one-by-one as you iterate over it. (YOU GENERATE VALUES ON-THE-FLY)

## Create a Generator Function & Generator Object

In Python, you can create a generator function by using the #yield statement. If the body of a def contains yield, the function automatically becomes a Python generator function. The generator function returns a generator object, which is an iterable.

There are two ways to create a Generator Object:
### Using #yield Statement

Generator returns an iterator (generator object) using the yield keyword. The yield statement will create a generator object which will hold the recipe to get the values & not the actual values. Those values will be generated ON-THE-FLY if you want.

![[Pasted image 20230807115459.png]]

### Using Generator Expressions

We can write the generator functions using the generator expressions too (which is very similar to list comprehension technique). The way we do list comprehension using the big brackets, we can do the yield comprehension using the small brackets.

![[Pasted image 20230807132554.png]]

### Heterogeneous values can be yielded inside the Generator Object

All the yield statements in a generator function just append the yielded value to the generator object. Also, one can yield heterogeneous values to the generator object too.

![[Pasted image 20230807120744.png]]


## Get values from a Generator Object

Here are some ways to get values from a Generator Object
### Using the next() function + StopIteration ERROR

To get the values, you can use the next() function. This function generates the current value, and moves on to the next value. 

One can see this as a pointer that is present on the starting index of an array. Whenever you call the next() function, the pointer generates the value that should be present on that array index and moves to the next index.

![[Pasted image 20230807115729.png]]

However, if we call the next() function more than the number of times than the number of values yielded, we will get an **StopIteration ERROR** : StopIteration is a built-in exception that is used to exit from a Generator. When the generator’s iteration is complete, it signals the caller by raising the StopIteration exception and it exits.

One can raise the stopIteration ERROR through code too:
![[Pasted image 20230807142802.png]]
### Using for Loop

We can also use the basic for loop to loop through this Generator Object Iterator as below:

![[Pasted image 20230807133123.png]]
## Performance Benefits of using #yield over #return

Generators memory optimize the functions since we don't really generate the values and store. Since the values are generated on demand, a large chunk of data doesn't need to be saved in 
the memory entirely which results in substantial memory savings.

A generator is an essential tool for programmers who deal with large amounts of data. Its ability to compute and access data on-demand results in terms of both increase in performance and memory savings.
#### WHAT EXACTLY HAPPENS ?

A function is a generator if it has yield statement in it. When the generator function is called, the yield statement also sends a value to the caller just like return statement (This is same).

But, the execution of the function is halted until the request is received. Upon getting the request, the generator continues executing from where it left off and executes till it encounters another yield statement, as shown below:

![[Pasted image 20230807140131.png]]

If it would've been a code in which we are returning the list by appending values to it, it would've printed "I Ran" 5 times in the starting only and returned the values in a list + exiting the get_count() function's execution.

But this is not the case with #yield statement.

## Generator Delegation

You can call a generator function through a generator function using the **yield from** keyword.

![[Pasted image 20230807154652.png]]