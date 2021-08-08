# Read: Class 42 - Pythonism
## Enriching Your Python Classes With Dunder (Magic, Special) Methods

### What Are Dunder Methods?
under-under-method-under-under **equal to** dunder methods or magic methods 
In Python, special methods are a set of predefined methods you can use to enrich your classes. They are easy to recognize because they start and end with double underscores, for example __init__ or __str__.

> Dunder methods let you emulate the behavior of built-in types

```
class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
42
```
### Enriching a Simple Account Class
In class we need `__init__` 
To construct account objects from the Account class I need a constructor : 
The constructor takes care of setting up the object.
### Object Representation: __str__, __repr__
1. `__repr__`: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.
2. `__str__`: The “informal” or nicely printable string representation of an object. This is for the enduser.

```
class Account:
    # ... (see above)

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
```
> If you don’t want to hardcode "Account" as the name for the class you can also use self.__class__.__name__ to access it programmatically.

#### Resources
* [Dunder Methods](https://dbader.org/blog/python-dunder-methods)
* [Iterators](https://dbader.org/blog/python-iterators)
* [Generators](https://dbader.org/blog/python-generators)
* [What are Generators](https://realpython.com/lessons/what-are-python-generators/)
* [Decorators](https://realpython.com/primer-on-python-decorators/)