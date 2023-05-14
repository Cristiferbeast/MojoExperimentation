A Demonstration of the Mojo Code
Mojo is a New Coding Language that is underdevelopment that seeks to add more attributes to Python while also offering heavy backwards compatability with the language 
In its simplest form the language has heavy connection to the Python however at higher degrees it offers may unique features.


```mojo
#Much of Mojos Simple Functions overlap with Python
print("Hello World")
```

    Hello World


To Sign up for Mojo one can use find a link to get access to the demo of this language on their website https://www.modular.com/mojo.
The Primary Focus should be on what this language does differently ontop of Python.
The First Major difference, is the ability to set immutable variables, this can be done with the key word Let


```mojo
let pi = 3.14 
pi = 33
print(pi)
```

    error: [0;1;31m[1mExpression [4]:17:5: [0m[1mexpression must be mutable in assignment
    [0m    pi = 33
    [0;1;32m    ^~
    [0m[0m


Trying to change the valuable of a Let value will result in a error (which is kinda the point) but you can fix this by reassigning it to a var 


```mojo
var people = 0 
people += 1
print("There are",  people , "People in the Room")
```

    There are 1 People in the Room


This can be used in combination with the defining of functions as shown 


```mojo
def function:
    var mutable
    let immutable
    mutable += immutable
    return mutable
```

Another major addition is the Struct typing, this can be seen as a large immutable class that is run at compile time. 


```mojo
struct MyPair:
    var first: Int
    var second: Int

    # We use 'fn' instead of 'def' here - we'll explain that soon
    fn __init__(inout self, first: Int, second: Int):
        self.first = first
        self.second = second

    fn __lt__(self, rhs: MyPair) -> Bool:
        return self.first < rhs.first or
              (self.first == rhs.first and
               self.second < rhs.second)
```

These new structs also have additional abilities, one such is the usage of strong typing. For exmaple, if you have a statement that is of a set type trying to change it would result in a compile error. 


```mojo
def pairTest() -> Bool:
    let p = MyPair(1, 2)
    # Uncomment to see an error:
    return p < 4 # gives a compile time error
```

    error: [0;1;31m[1mExpression [1]:6:13: [0m[1muse of unknown declaration 'MyPair'
    [0m    let p = MyPair(1, 2)
    [0;1;32m            ^~~~~~
    [0m[0m


This is code above returns an error because the MyPair() typing returns an int.  
Another large benefit of Mojo's Structs is the usage of Operation Overloading using strict typing. 
As shown below in this provided example you can function overload using the fn syntax within a struct, the usage of this i will now explain. 


```mojo
struct Complex:
    var re: F32
    var im: F32

    fn __init__(inout self, x: F32):
        """Construct a complex number given a real number."""
        self.re = x
        self.im = 0.0

    fn __init__(inout self, r: F32, i: F32):
        """Construct a complex number given its real and imaginary components."""
        self.re = r
        self.im = i
```

The def funciton offers mass usability and simplicity of writing, however for coders who need more exact solutions the fn typing exists instead.
fn and def are very similar however fn offers some slight differences from def. 
1. Arguments default to being immutable within a fn 
2. Argument values require a type specification 
3. Implicit declaration of local variables is disabled, so all locals must be declared. This catches name typos and dovetails with the scoping provided by `let` and `var`.
4. Both support raising exceptions, but this must be explicitly declared on a `fn` with the `raises` function effect, placed after the function argument list.
This does make using a fn a bit more complex however it certainly allows for greater control of the code.

This is a standard overview of some of the functions that Mojo offers, Mojo is still in development and my time with it has been short so explaining some of the more complex features even with the help of their own guides would be likely to result in me mistating something. 

Overall i think that Mojo is a pretty interesting concept, essentially an upgrade to Python to allow it to handle some more delicate code management that the language currently can't. Personally as someone who primarily codes in C, C++ and C# this isn't the solution to help Python handle the level of control that those offer, however for Python cooders its a solid upgrade with pretty friendly syntax that honestly may be worth your time. 
But really this is all i've got for y'all today. This has been Cristiferbeast and hope to see y'all Next Time!
