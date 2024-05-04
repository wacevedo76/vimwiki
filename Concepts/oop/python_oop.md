# OOP in Python

## Referencing class Attributes
```python
class NewClass:
    class_count = 0                           # <-- Class Attribute
    
    def __init__(self, user_code, contents):
        self.user_code = user_code
        self.contents = contents
        self.serial = NewClass.class_count    # <-- Assigning Class Attribute reference to instance attibute
        NewClass.next_serial += 1    # <-- Operation on class attribute through class instance attribute
```

## Hiding class attributes with instance attributes
* Reading class attributes through _self_references are **allowed**.
* Assigning values to class attributes will **not** change the class attribute but create a **new instance attribute**.

## Static methods
```python
class NewClass:
    CLASS_COUNT = 0                           
    
    @staticmethod
    def _get_next_class_count():
        result = NewClass.CLASS_COUNT
        NewClass.CLASS_COUNT += 1
        return result
    
    
    def __init__(self, user_code, contents):
        self.user_code = user_code
        self.contents = contents
        self._count = self._get_next_class_count()
        NewClass.CLASS_COUNT += 1    
    

```

## Overriding static and class methods  
By calling static methods through the class, you prevent them from being overridden.  
if you need polymorphic dispatch of static method invocations, call through the _self_ instance.

## Defining read-only property (getter property)

By using the `@property` decorator, the method which it modifies can be used like an instance attribute.  
Example:
```python
class NewClass:
    CLASS_COUNT = 0                           
    
    
    def __init__(self, user_code, contents):
        self.user_code = user_code
        self.contents = contents
        self._count = NewClass.class_count    #<-- set class attribute CLASS_COUNT to instance attribute
        NewClass.CLASS_COUNT += 1    
    
    @property                                 #<-- Use the @property decorator to access its methods return value
    def count(self):                          #    as if it was a regular instance attribute
        return self._count
```
Now you can retrive self._count like so:
```python
testclass01 = NewClass('12345', 'item01')

testclass01.count
  > 0
```

Which gives read-only access to self._count


## Defining a read-write property (setter property)
After applying the `@property` decorator (setting a setter property) a **getter** property
by applying the applying applying a `.setter` suffix to the name of the method which 
passed to the `@property` decorator.  
Example:
```python
class NewClass:
    CLASS_COUNT = 0                           
    
    
    def __init__(self, user_code, contents):
        self.user_code = user_code
        self.contents = contents
        self._count = NewClass.class_count  
        NewClass.CLASS_COUNT += 1    
    
    @property                               
    def count(self):                        
        return self._count
    
    @count.setter
    def count(self, value):
    self._count = value
```

