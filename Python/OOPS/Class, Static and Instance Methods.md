### Instance Methods
- It takes a parameter 'self' , which points to an instance of MyClass.

### Class Methods
- The first parameter in this method points to the class. Generally it is denoted as 'cls'.
- You're supposed to add a @classmethod decorator to the function.
- One has access to the class variables and can update them

### Static Methods

You don't pass any parameter to this, just add a decorator to that function.
Method that doesn't care about an instance. 

Eg: if you have Calendar class, you can have a function is_date_weekend() which doesn't care about any instance of the calendar but is related to Calendar class. So we make it @staticmethod

We can call it using Calendar.is_date_weekend(some_date)