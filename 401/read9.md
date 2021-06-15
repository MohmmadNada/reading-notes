# Readings: Game of Greed 4

# Enriching Your Python Classes With Dunder (Magic, Special) Methods
## magic methods
### What Are Dunder Methods?
dunder methods
start and end with double underscores, this predefined methods you can use to enrich your classes. like __init__ or __str__.

### Enriching a Simple Account Class

#### Object Initialization: __init__
construct account objects from the Account class 
```
class Account:
    """A simple account class"""

    def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []

# input //>>> acc = Account('bob')  # default amount = 0
>>> acc = Account('bob', 10)
```
The constructor takes care of setting up the object. In this case it receives the owner name, an optional start amount and defines an internal transactions list to keep track of deposits and withdrawals.

#### Object Representation: __str__, __repr__
two ways:
1. __repr__: The “official” string representation of an object. This is how you would make an object of the class. The goal of __repr__ is to be unambiguous.

2. __str__: The “informal” or nicely printable string representation of an object. This is for the enduser.

> If you wanted to implement just one of these to-string methods on a Python class, make sure it’s __repr__.

#### Iteration: __len__, __getitem__, __reversed__
iterate over our account object
```
def add_transaction(self, amount):
    if not isinstance(amount, int):
        raise ValueError('please use int for amount')
    self._transactions.append(amount)
```
 method takes the start amount and adds a sum of all the transactions:
```
@property
def balance(self):
    return self.amount + sum(self._transactions)
>>> acc = Account('bob', 10)

>>> acc.add_transaction(20)
>>> acc.add_transaction(-10)
>>> acc.add_transaction(50)
>>> acc.add_transaction(-20)
>>> acc.add_transaction(30)

>>> acc.balance
80
```
 I want to know:
How many transactions were there?
Index the account object to get transaction number …
Loop over the transactions

```
class Account:
    # ... (see above)

    def __len__(self):
        return len(self._transactions)

    def __getitem__(self, position):
        return self._transactions[position]
```
To iterate over transactions in reversed order you can implement the __reversed__ special method:
```
def __reversed__(self):
    return self[::-1]

>>> list(reversed(acc))
[30, -20, 50, -10, 20]
```
#### Operator Overloading for Comparing Accounts: __eq__, __lt__
haw can we check comparison dunder methods. for specific obj , ? 
```
>>> dir('a')
['__add__',
...
'__eq__',    <---------------
'__format__',
'__ge__',    <---------------
'__getattribute__',
'__getitem__',
'__getnewargs__',
'__gt__',    <---------------
...]
```
```

>>> acc2 > acc
TypeError:
"'>' not supported between instances of 'Account' and 'Account'"
```
```
from functools import total_ordering

@total_ordering
class Account:
    # ... (see above)

    def __eq__(self, other):
        return self.balance == other.balance

    def __lt__(self, other):
        return self.balance < other.balance

>>> acc2 > acc
True

>>> acc2 < acc
False

>>> acc == acc2
False

```
#### Operator Overloading for Merging Accounts: __add__
```
>>> acc + acc2
TypeError: "unsupported operand type(s) for +: 'Account' and 'Account'"
```
Our Account object does not support addition yet
```
def __add__(self, other):
    owner = '{}&{}'.format(self.owner, other.owner)
    start_amount = self.amount + other.amount
    acc = Account(owner, start_amount)
    for t in list(self) + list(other):
        acc.add_transaction(t)
    return acc
```
```
>>> acc3 = acc2 + acc
>>> acc3
Account('tim&bob', 110)

>>> acc3.amount
110
>>> acc3.balance
240
>>> acc3._transactions
[20, 40, 20, -10, 50, -20, 30]
```
#### Callable Python Objects: __call__
```
class Account:
    # ... (see above)

    def __call__(self):
        print('Start amount: {}'.format(self.amount))
        print('Transactions: ')
        for transaction in self:
            print(transaction)
        print('\nBalance: {}'.format(self.balance))
```
```
>>> acc = Account('bob', 10)
>>> acc.add_transaction(20)
>>> acc.add_transaction(-10)
>>> acc.add_transaction(50)
>>> acc.add_transaction(-20)
>>> acc.add_transaction(30)

>>> acc()
Start amount: 10
Transactions:
20
-10
50
-20
30
Balance: 80
```
#### Context Manager Support and the With Statement: __enter__, __exit__

> A context manager is a simple “protocol” (or interface) that your object needs to follow so it can be used with the with statement. Basically all you need to do is add __enter__ and __exit__ methods to an object if you want it to function as a context manager.

```
class Account:
    # ... (see above)

    def __enter__(self):
        print('ENTER WITH: Making backup of transactions for rollback')
        self._copy_transactions = list(self._transactions)
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print('EXIT WITH:', end=' ')
        if exc_type:
            self._transactions = self._copy_transactions
            print('Rolling back to previous transactions')
            print('Transaction resulted in {} ({})'.format(
                exc_type.__name__, exc_val))
        else:
            print('Transaction OK')
```
```
def validate_transaction(acc, amount_to_add):
    with acc as a:
        print('Adding {} to account'.format(amount_to_add))
        a.add_transaction(amount_to_add)
        print('New balance would be: {}'.format(a.balance))
        if a.balance < 0:
            raise ValueError('sorry cannot go in debt!')
```
```
acc4 = Account('sue', 10)

print('\nBalance start: {}'.format(acc4.balance))
validate_transaction(acc4, 20)

print('\nBalance end: {}'.format(acc4.balance))
```
printout 
```
Balance start: 10
ENTER WITH: Making backup of transactions for rollback
Adding 20 to account
New balance would be: 30
EXIT WITH: Transaction OK
Balance end: 30
```
However when I try to withdraw too much money, the code in __exit__ kicks in and rolls back the transaction:


```
acc4 = Account('sue', 10)

print('\nBalance start: {}'.format(acc4.balance))
try:
    validate_transaction(acc4, -50)
except ValueError as exc:
    print(exc)

print('\nBalance end: {}'.format(acc4.balance))

```
In this case we get a different result:

```
Balance start: 10
ENTER WITH: Making backup of transactions for rollback
Adding -50 to account
New balance would be: -40
EXIT WITH: Rolling back to previous transactions
ValueError: sorry cannot go in debt!
Balance end: 10

```

## Tutorial: Basic Statistics in Python — Probability

### What is probability?
What is the chance of an event happening?
### From statistics to probability

------------Read9

```
import random
def coin_trial():
heads = 0
for i in range(100):
    if random.random() <= 0.5:
        heads +=1
    return heads
def simulate(n):
    trials = []
    for i in range(n):
        trials.append(coin_trial())
    return(sum(trials)/n)
simulate(10)
>>> 5.4
simulate(100)
>>> 4.83
simulate(1000)
>>> 5.055
simulate(1000000)
>>> 4.999781
```

Python saves us a lot of time 

Resources :
* [Dunder Methods](https://dbader.org/blog/python-dunder-methods) 
* [Statistics - Probability
 ](https://www.dataquest.io/blog/basic-statistics-in-python-probability/) 
* [Intro to Statistics
 ](https://www.youtube.com/watch?v=MdHtK7CWpCQ) 
* [AI Guru makes $238,800 with misleading paid course. doesn’t credit developers
 ](https://www.youtube.com/watch?v=7jmBE4yPrOs) 
* [Statistics Module
 ](https://docs.python.org/3/library/statistics.html) 