A process is a program in execution.

![[Pasted image 20230806224052.png]]

### Is Python Multithreaded?

So the general answer is, It is possible to create more than one threads in a Python program, but no two threads of the same program will run concurrently (No matter how much core CPU we have).

Eg: Let's suppose we have two processes in Python, Process 0 & Process 1. Each process is having 2 threads & our CPU is having 4 Cores. Execution will look somewhat like this:

![[Pasted image 20230806224544.png]]
#### NO TWO THREADS FROM THE SAME PROCESS ARE EVER EXECUTING ON THE SAME TIME

There is a Python Global Interpreter Lock (GIL), which allows only one thread to hold the control of the Python Interpreter. Only one thread can be in state of execution at any point in time. 