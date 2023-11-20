A process is a program in execution.

![[Pasted image 20230806224052.png]]

### Is Python Multithreaded?

So the general answer is, it is possible to create more than one threads in a Python program, but no two threads of the same program will run concurrently (No matter how much core CPU we have).

Eg: Let's suppose we have two processes in Python, Process 0 & Process 1. Each process is having 2 threads & our CPU is having 4 Cores. Execution will look somewhat like this:

![[Pasted image 20230806224544.png]]
#### NO TWO THREADS FROM THE SAME PROCESS ARE EVER EXECUTING ON THE SAME TIME

There is a Python Global Interpreter Lock (GIL), which allows only one thread to hold the control of the Python Interpreter. Only one thread can be in state of execution at any point in time. 

Now, if the program is I/O intensive, then while we're waiting for Input/Output from the program, the thread can be preempted/context switched to another thread and the work on other thread can be done. This will increase the performance of the Python Program definitely.

![[IMG_2237.png]]

#### Hence, it is advised to use Threads when you have I/O Intensive work in case of Python

However, if we are having only CPU Intensive Applications, the context switching will happen only when the switching time ends. That will actually not help the code in performance. It actually makes the code performance a bit poor due to the context switch time addition in it.

Also, there is time that goes in creation of threads and their maintenance too.

![[IMG_2238.jpeg]]
#### Hence, it is not advised to use Threads when you have CPU Intensive work in case of Python

>>> The GIL does not have much impact on the performance of I/O-bound multi-threaded programs as the lock is shared between threads while they are waiting for I/O. 
>>> 
>>> But a program whose threads are entirely CPU-bound, e.g., a program that processes an image in parts using threads, would not only become single threaded due to the lock but will also see an increase in execution time, as seen in the above example, in comparison to a scenario where it was written to be entirely single-threaded. 
>>> 
>>> This increase is the result of acquire and release overheads added by the lock.

## Solution?

The basic solution as of now in case of CPU Intensive Applications is using Multi-processing instead of Multi-Threading in Python. Since each python process gets its own python interpreter and memory space so GIL won't cause a problem.

For Multithreading: Use multithreading module
For Multiprocessing: Use multiprocessing module

However, there is an issue with multithreading, they use the same stack memory and the registers, thus one thread might impact the other thread. Eg: if we have a global counter which is incremented and decremented by two functions which are running in two different threads, which impact the 


## Async/Await (Event Loop Based Implementation)

All this is to know how can we do things in parallel in Python in order to improve performance. 