# Advanced-Python-Interview

ACID Transactions: 
•	Atomicity refers to completed or failed transactions, where a transaction refers to a single logical operation on data. 
•	Consistency means that the transaction never leaves the database without finishing its state.
•	Isolation means concurrency management.
•	Durability ensures that once a transaction is committed, it will occur regardless of what happens in between such as a power outage, fire, or some other kind of disturbance.
Normalization: 
The primary goals of normalization are to eliminate data anomalies, ensure data integrity, and minimize the chances of data redundancy and dependency. 
1.	First Normal Form (1NF):
o	Each column in a table must contain atomic (indivisible) values, and each row must be unique.
2.	Second Normal Form (2NF):
o	The table must be in 1NF, and all non-key attributes must be fully functionally dependent on the primary key. This means that if a table has a composite primary key, each non-key attribute must be dependent on the entire composite key, not just part of it.
3.	Third Normal Form (3NF):
o	The table must be in 2NF, and no transitive dependencies should exist. In other words, non-key attributes must not be dependent on other non-key attributes.

def fib_rec(nterms):
    
    if nterms<=0:
        return "enter postive"
    elif nterms ==1:
        return 0
    elif nterms == 2:
        return 1
    else:
        return fib_rec(nterms - 1) + fib_rec(nterms - 2)
        
fib_rec(8)


def fib(nterms):
    a,b = 0,1
    if nterms<=0:
        return "enter postive"
    elif nterms ==1:
        return a
    elif nterms == 2:
        return b
    else:
        print("fibonacci sequene")
        count = 0
        while count<nterms:
            print(a)
            c = a + b
            a = b
            b = c
            count = count + 1



def myFunc(*args):
    for arg in args:
        print(arg)

args = ("Geeks", "for", "Geeks")
myFunc(*args)

def myFun(**kwargs):
    for k ,v in kwargs.items():
        print(f"{k}:{v}")
              
kwargs = {"arg1": "Geeks", "arg2": "for", "arg3": "Geeks"}
myFun(**kwargs)


Generator function/Yield: 
We should use yield when we want to iterate over a sequence, but don’t want to store the entire sequence in memory.
A generator function is defined just like a normal function, but whenever it needs to generate a value, it does so with the yield keyword rather than return. 
def fib(nterms):
    a,b = 0,1
    if nterms<=0:
        return "enter postive"
    elif nterms ==1:
        return a
    elif nterms == 2:
        return b
    else:
        count = 0
        while count<nterms:
            yield a
            a,b = b, a+b
            count += 1 
            
for i in fib(8):
    print(i)


Decorators: 
A decorator is a way to modify the behavior of a function or a class without directly changing its source code. It allows adding functionality to an existing function or class by wrapping it with another function or class. Decorators are commonly used for tasks such as logging, timing, input validation, authentication, and more.
The outer function is called the decorator, which takes the original function as an argument and returns a modified version of it.


def smart_divide(func):
    def inner(a, b):
        print("I am going to divide", a, "and", b)
        if b == 0:
            print("Whoops! cannot divide")
            return

        return func(a, b)
    return inner

@smart_divide
def divide(a, b):
    print(a/b)

divide(2,5)

divide(2,0)





Closure: 
 A closure is a function that can remember and access the values of variables from its surrounding environment, even after the execution of the outer function has finished.
In Python, closures can be created by defining a function inside another function and returning the inner function.
A closure is created when a nested function references variables from its enclosing scope.

def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

closure = outer_function(5)
print(closure(3))  # Output: 8
When ‘outer_function’ is called with the argument ‘5’, it returns the function ‘inner_function’, which remembers the value of ‘x’ as ‘5’. This function object is assigned to the variable closure.
Finally, closure is called with argument ‘3’, which adds ‘3’ to the value of ‘x’ (which is ‘5’), resulting in output ‘8.’

