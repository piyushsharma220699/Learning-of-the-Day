Generator Functions are special type of functions which create an iterable sequence of values. This function returns a generator object, which can be used to generate values one-by-one as you iterate over it. (YOU GENERATE VALUES ON-THE-FLY)

## Create a Generator {Using #yield statement }

In Python, you can create a generator by using the #yield statement. If the body of a def contains yield, the function automatically becomes a Python generator function. 

Generator returns an iterator (generator object) using the yield keyword. The yield statement will create a generator object which will hold the recipe to get the values & not the actual values. Those values will be generated ON-THE-FLY if you want.

![[Pasted image 20230807115459.png]]

## Create a Generator {Using Generator Expressions)

We can write the generator functions using the generator expressions too (which is very similar to list comprehension technique). The way we do list comprehension using the big brackets, we can do the yield comprehension using the small brackets.

![[Pasted image 20230807132554.png]]

### Heterogeneous values can be yielded inside the generator object

All the yield statements in a generator function just append the yielded value to the generator object. Also, one can yield heterogeneous values to the generator object too.

![[Pasted image 20230807120744.png]]

## Using the next() function

To get the values, you can use the next() function. This function generates the current value, and moves on to the next value. 

One can see this as a pointer that is present on the starting index of an array. Whenever you call the next() function, the pointer generates the value that should be present on that array index and moves to the next index.

![[Pasted image 20230807115729.png]]

## Using for Loop



![[Pasted image 20230807133123.png]]
## Performance Benefits of using #yield over #return

Generators memory optimize the functions since we don't really generate the values and store. 

## Where shall we use #yield than #return ?


