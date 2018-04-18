
# Practice with Instance Variables

## Introduction
In this lab, we will practice using instance variables and differentiating them from local variables. We will continue with our awesome `fuber` theme. We have a couple files already provided for us, driver.py and ride.py. To get started, we need to import these files, which we have alread done below. 

## Objectives

* Define instance variables.
* Distinguish instance variables from local variables.
* Describe how instance variables give objects attributes and properties.

## Defining Instance Variables

We have been writing functions and working with variables for a while now. We've talked about the difference between global variables and local variables. However, classes add another level of complexity with instance variables. Remember the difference between local and global variables is their scope. Local varibles have local or function scope, that is that they are only able to be accessed inside the function in which they are defined. Global variables can be accessed from anywhere in the file. Instance variables are bound to an instance. They can be thought of more as attributes or properties of an instance. An instance variable can only be accessed by the instance that it is bound to. 

## Okay, but Why Do We Need Instance Variables?

Let's imagine we have a driver, `alex`, who has an attribute called `name`. If we wanted to query that attribute, we would only want to recieve the `name` attribute from the driver instance, `alex`. Let's see how we would set something like this up with local variables alone:


```python
class ExampleDriver:
        
    def set_name(self, new_name):
        name = new_name
        return name
    
    def get_name(self):
        return name
    
example_alex = ExampleDriver()
```

Cool, no errors and it looks pretty straightforward. Let's try it out. First we'll give the `name` a value with `set_name`:


```python
example_alex.set_name('Alex')
```




    'Alex'



Alright, so we can assign the variable with our string and then return the variable successfully. Let's try just querying the name now that we've assigned it a value.


```python
example_alex.get_name()
```




    'Alex'



Oh no! `NameError: name 'name' is not defined` --  what does this mean?

As the error states, the `'name'` variable is undefined in this method. We defined name in local scope, so, now that we are in another function it is undefined. We could change things a bit to get this class to use a global variable for `name`, but then we can see that as soon as we create a new driver and reassign the global variable, we would have lost the name of the previous driver, `alex`. Don't worry too much about that right now. The key take away is that we are only able to define instance variables as attributes of an instance and we need to have the instance in scope to access its variables or attributes.

## Putting Instance Variables to the Test

It seems natural that a driver would have an attribute of `distance_driven` and that this attribute would be present at the start of one's professional driving career. So, let's add that to our `__init__` instance method in the `Driver` class and initialize it with a value of `0`. Next, we'll need a way for us to access and change this value. So let's define instance methods to accomplish both of these tasks, we'll call these methods `get_distance`, which will return the driver's `distance_driven`, and `set_distance`, which will take in a distance and add it to the driver's `distance_driven` attribute and finally return the updated `distance_driven`. 


```python
from driver import Driver
```

Let's instantiate a new driver and assign it to the varible `alex`. Next get the initial `distance_driven`, which should be `0` and assign it to `initial_distance`.


```python
alex = Driver()
```


```python
initial_distance = alex.get_distance()
print(initial_distance)
```

    0


Great! we now have a driver and their initial distance driven. Let's take a 5 mile ride with `alex`. To do this, we need to call the `set_distance` method on `alex` and pass in an argument of `5`. Let's assign the return value of this operation to the variable, `new_dist`.


```python
new_dist = alex.set_distance(5)
print(new_dist)
```

    10


## Summary
In this lab we learned how to differentiate between instance and local variables. Then we saw the reason we need to use instance variables when we are assigning or operating on an attribute of an instance object. Finally we practiced using instance methods to read and re-assign the values of our instance variables.
