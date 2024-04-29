# OOP in Python


## Referencing class Attributes
```python
class NewClass:
    class_count = 0                           # <-- Class Attribute
    
    def __init__(self, user_code, contents):
        self.user_code = user_code
        self.contents = contents
        self.serial = NewClass.class_count    # <-- Assigning Class Attribute reference to instance attibute
        ShippingContainer.next_serial += 1    # <-- Operation on class attribute through class instance attribute
```

## Hiding class attributes with instance attributes
* Reading class attributes through _self_references are **allowed**.
* Assigning values to class attributes will **not** change the class attribute but create a **new instance attribute**.

## Overriding static and class methods  
By calling static methods through the class, you prevent them from being overridden.  
if you need polymorphic dispatch of static method invocations, call through the _self_ instance.
