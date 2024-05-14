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
After applying the `@property` decorator (setting a **getter** property) create a 
**setter** property by applying a `.setter` suffix to the name of the method which 
was passed to the `@property` decorator.  
Example:
```python
class NewClass:
    CLASS_COUNT = 0                           
    
    
    def __init__(self, user_code, contents):
        self.user_code = user_code
        self.contents = contents
        self._count = NewClass.class_count  
        NewClass.CLASS_COUNT += 1    
    
    @property                  # <-- indicateding that the next function will be a getter property
    def count(self):           # <-- the name of the getter property
        return self._count
    
    @count.setter              # <-- apply the setter property to the getter property
    def count(self, value):    # <-- use the same function name
        self._count = value
```

## Using propertie for class-wide validation
The subclass initializer can be simplified by referencing the setter method
```python

    def __init__(self, owner_code, contents, celsius):
          super().__init__(owner_code, contents)
          if celsius > RefrigeratedShippingContainer.MAX_CELSIUS:
              raise ValueError("Temperature too hot!")
          self.celsius = celsius                  # <-- this references the setter property

      @property
      def celsius(self):
          return self._celsius

      @celsius.setter                             # <-- setter property
      def celsius(self, value):
          if value > RefrigeratedShippingContainer.MAX_CELSIUS:
              raise ValueError("Temperature too hot!")
          self._celsius = value

```

## Overriding getters in subclass
Overriding a setter class is as simple as calling the setter decorator and 
redefining its function
```python
class NewContainer(PreviousContainer):
  
    @property                            # by calling the previous_container_value getter methodoriginally defined in the subclass
    def previous_container_value(self):  # you are effectively redefining the getter method.
        # your code
```

Overriding setters in subclasses
In order to override setter methods, you must call the setter method from the class from in which it was originally defined.
```python
class NewContainer(PreviousContainer):
  
    @PreviousContainerllill.previous_container_value.setter
    def previous_container_value(self, value):  # you are effectively redefining the setter method.
        self._previousc_container_value = value
```
