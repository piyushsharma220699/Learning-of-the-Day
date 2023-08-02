Official Doc: https://docs.python.org/3/tutorial/venv.html

In our computer, we work on more than one project. Every project requires different versions of modules to run. Eg: Application A needs Version 1.0 of a particular module whereas Application B needs Version 2.0 of that same module. (Conflicting Requirements Issue: Which leaves one application unable to run)

But at one point of time, we can have only one Version of a particular module installed in our python installation. Thus, we create a VIRTUAL ENVIRONMENT.

>>> **VIRTUAL ENVIRONMENT is a self-contained directory tree that contains a Python installation for a particular version of Python, plus a number of additional packages.**

The module used to create a virtual environment is **venv**. By default, it will install the most recent version of Python that is available. However, you can select the version of Python too if you have multiple installed.

>>> pip install venv
>>
>> python -m venv {name of virtual environment}
>> (The best practice is to use .venv as the virtual environment name)
>
>source .venv/bin/activate

So basically, you create a virtual environment and then activate that virtual environment too (Commands for which is based on OS used)

### BEST PRACTICE IS TO CREATE A SEPARATE VIRTUAL ENVIRONMENT FOR EVERY PROJECT THAT YOU CREATE

Now, you can add packages to this virtual environment using pip, which installs them from the Python Package Index: https://pypi.org/

Now, it is also a **BEST PRACTICE** to have all the modules required to run your program to be present in a requirements.txt file. This can be shipped as a part of application and can be used by people to install all necessary packages to run your application.

For that, one can use **pip freeze**. Here's the command:

>>> python -m pip freeze > requirements.txt