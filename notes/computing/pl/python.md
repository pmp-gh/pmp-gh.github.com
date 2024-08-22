Python
======

### Strings  
* ```‘this is a string’```  
* ```“also a string”```  
* ```\ to escape quotes```  
* ```print(r’C:\dir\file’) => C:\dir\file (raw strings)``` 
* ```“””line 1``` 
* ```line 2””” (multiline strings)```  
* ```‘a’+3*’b’ => ‘abbb’```  
* ```word = ‘python’```  
* ```word[0] = ‘p’ word[-1] = ‘n’```  
* ```word[0:2] = ‘py’```  
* ```word[:2] = ‘py’ word[2:] = ‘thon’```  
* ```strings are immutable, can’t assign to position``` 
* ```len(‘python’) => 6``` 

### Lists  
* ```squares = [1, 4, 9, 16, 25]``` 
* ```squares[2] => 9```  
* ```squares + [36, 49] => [1, 4, 9, 16, 25, 36, 49]``` 
* ```lists are mutable```  
* ```cubes = [1, 8, 26] cubes[2] = 27``` 
* ```cubes.append(64) cubes => [1, 8, 27, 64]``` 
* ```cubes.extend(list[125, 216]) => [1, 8, 27, 64, 125, 216]```  
* ```cubes.insert(0, 0) => [0, 1, 8, 27, 64, 125, 216] (first arg is pos before which to insert)``` 
* ```cubes.remove(0) => [1, 8, 27, 64, 125, 216] (remove first occurence)```
* ```cubes.pop(1) => remove and return 8 (elem at position 1, if no index it pops last elem)``` 
* ```cubes.index(27) => 1 (index of first occurence of elem)``` 
* ```cubes.clear() => remove all elems```  
* ```a = [1, 1, 2, 3, 1] a.count(1) => 3``` 
* ```a.sort() => [1, 1, 1, 2, 3] (sort in place)``` 
* ```a.reverse() => [3, 2, 1, 1, 1] (reverse in place)``` 
* ```letters = [‘a’, ‘b’, ‘c’, ‘d’, ‘e’, ‘f’]```  
* ```letters[2:5] = [‘C’, ‘D’, ‘E’] letters => [‘a’, ‘b’, ‘C’, ‘D’, ‘E’, ‘f’]``` 
* ```len(letters) = 6``` 
* ```a = [1, 2] b = [3, 4] x = [a,b] => [[1,2], [3,4]]```  
* ```x[0] = [1, 2]  x[0][1] = 2```
* ```list(range(5)) => [0, 1, 2, 3, 4]```
* ```a = [1, 2, 3], del a[1:2] a => [1, 3]```  
* ```a = [1, 2] b = [3, 4] for x, y in zip(a, b): print(x, y)``` 

### List comprehensions  
* ```squares = [x**2 for x in range(4)] => [0, 1, 4, 9]```  
* ```[(x, y) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]```   

### Deque (efficient queues)  
* ```from Collections import deque```
```  
q = deque([‘A’, ‘B’, ‘C’])  
q.append(‘D’)  
q.append(‘E’)  
q.popleft()  
q => [‘B’, ‘C’, ‘D’, ‘E’]  
```

### Tuples  
* ```Immutable and usually contains heterogeneous sequence of elements.``` 
* ```t = (1, 2, “a”)  # packing``` 
* ```x, y, z = t      # unpacking``` 

### Sets  
* ```Unordered collection with no duplicate elements.```  
* ```s = {3. 1, 2, 2, 3} s => {1, 2, 3}```  
* ```3 in s => True```  
* ```t = {4, 2, 6}```  
* ```s | t = {1, 2, 3, 4, 6}```  
* ```s & t = {2}``` 
* ```s ^ t = {1, 3, 4, 6}```  
* ```u = set() # empty set```  

### Dictionaries  
* ```Sets of (key, value) pairs, where keys are unique and immutable.```  
* ```d = {‘jack’:4098, ‘sape’:4139}```  
* ```d[‘guido’] = 4127```  
* ```list(d) => [‘jack’, ‘sape’, ‘guido’]```  
* ```d[‘jack’] => 4098```  
```
for x, y in d.items():  
	print(x, y)
``` 

### Assignment  
* ```x = 1``` 
* ```a,b = 1,2```  

### Printing  
* ```print(‘value of a+b is’, a + b) => value of a+b is 3```  

### Control Flow  
```
While  
while (i < n):  
  print(i)  

If   
if (x < a):  
  x = x + a  
elif (x == a):  
  x = 0  
else:  
  x = x - a  

For  
squares = [1, 4, 9, 16, 25]  
for s in squares:  
  print(s)  

range()  
range(0, 5) => 0, 1, 2, 3, 4  
range(0, 10, 3) => 0, 3, 6, 9  

break - out of innermost enclosing for or while  
continue - next iteration of loop  
else (with for) - if you don’t break out of for  
pass - does nothing  
```

### Functions  
```
Example  
def fib(n):  
  “”” Return a list containing Fibonacci series up to n”””  
  result = []  
  a, b = 0, 1  
  while a < n:  
    result.append(a)  
    a, b = b, a+b  
  return result  

Default arguments (only evaluated once)  
  def ask_ok(prompt, retries=4, reminder=’please try again’): 
    while True:  
      ok = input(prompt)  
      if ok in (‘y’, ‘yes’):  
        return True  
      if ok in (‘n’, ‘no’):  
        return False  
      retries = retries - 1  
      if retries <  0:  
        raise ValueError(‘invalid response’)  
      print(reminder)  

Keyword arguments  
  def foo(u, v=100):  
    print(u, v)  
  foo(u=50, v=50) => 50 50  
  def bar(u, *args, **keywords):  
    print(u)  
    for arg in args:  
      print(arg)  
    for kw in keywords:  
      print(kw, “:”, keywords[kw])  
  bar(10, ‘a’, ‘b’, qux=’c’, quux=’d’) => 10 a b qux:c quux:d  

Lambda expressions: Small anonymous functions  
  lambda a, b: a + b  

Can reference variables in enclosing scope  
def make_inc(n): 
  return lambda x: x + n  
f = make_inc(42)  
f(1) => 43  
```

### Modules  
```
A module is a file containing types and definitions.  

Within the module, the name is available as value of global variable __name__.  

Each module has its private symbol table into which imported module names are placed.  
Directories containing modules in sys.path, which is initialized from current directory, PYTHONPATH.  
sys.path.append(''/ufs/guido/lib/python'')  

dir(sys): Sorted list of strings with names a module defines.  
```

### Packages  
```
A.B: Submodule B in package named A.  

Example file structure for packages (__init__.py can contain initialization or be empty)  
sound/  (package)  
      __init__.py  
      formats/  (sub package)  
          __init__.py  
          waveread.py  (module)  
          wavewrite.py  
      effects/  (sub package)  
          __init__.py  
         echo.py  
         surround.py  
      filters/  (sub package)  
          __init__.py  
         equalizer.py  
         vocoder.py  
import sound.effects.echo  
sound.effects.echo.echofilter(input, output, delay=0.7, atten=4)  
from sound.effects import echo  
echo.echofilter(input, output, delay=0.7, atten=4)  
from sound.effects.echo import echofilter  
echofilter(input, output, delay=0.7, atten=4)  

Intra-package references  
Examples 
from . import echo  
from .. import formats  
from ..filters import equalizer  
```

### Input/Output  
```
Output formatting  

ex1  
year=2106  
event='Referendum'  
f'Results of the {year} {event}' => Results of the 2016 Referendum  

ex2  
yes=250  
no=350  
percent=yes/(yes+no)  
'{:2.2%}'.format(percent) => 41.67%  
print('{1} and {0}'.format('eggs', 'spam')) => spam and eggs  

ex3  
table={'Sjoerd':4127, 'Jack':4098}  
for name,phone in table.items():  
  print(f'{name:10}=>{phone:10d}') => Sjoerd=>4127\nJack=>4098  

for x in range(1,11):  
  print('{0:2d} {1:3d} {2:4d}'.format(x, x*x, x*x*x))  
  
File I/O  
f=open('foo', 'w') # use 'b' for binary files  
f.write('this is a test')  
f.close()  
f.read(4096) # read 4096 bytes  
f.read() # read entire file  
f.readline() # read a line, ends in \n  
for line in f:  
  print(line, end=' ')  

f.seek(-3,2) # go to 3rd byte from end of file  
```

### Serialization  
* ```import json # can serialize lists and dictionaries, but not arbitrary classes```
* ```json.dumps([1, '2', 'hello']) => '[1, "2", "hello"]'```  
* ```json.dump(x, f) # Serialize x to file``` 
* ```x = json.load(f)``` 
* ```See pickle for serializing arbitrary python objects```  
```  

### Errors/Exceptions  
```
try  

Execute statements in block until exception. Then, handle exception if handler 
provided. If no exception, execute else block. The finally block is always 
executed. It may contain cleanup actions.  

Ex  
for arg in sys.argv[1:]:  
  try:  
    f= open(arg, 'r')  
  except OSError:  
    print('cannot open', arg)  
  else:  
    print(arg, 'has', len(f.readlines()), 'lines')  
    f.close()  
  finally:  
    print('goodbye')  

Raising exceptions: Must be exception instance or exception class (derived from Exception)  

Ex  
raise NameError('hi there')  

User-defined Exceptions  

Ex  
class InputError(Exception):  
def __init__(self, expression, message):  
  self.expression = expression  
  self.message = message  
```

### Classes  
```
Used to encapsulate state and provide methods to operate on state.  
Methods are like virtual functions in C++.  
Class variables defined at top level in class.  
No private instance variables. Use convention to indicate (e.g., use '_' in front of name).  
Variables are created when first used. Instance variables can also be created by the caller!  

__init__ method to initialize state (like constructor in C++)  

Ex.  
class Cplx:  
def __init__(self, r, i):  
  self.set_real(r)  
  self.set_imag(i)  
def mod(self):  
  return sqrt(_r*_r + _i*_i)  
def get_real(self):  
  return self._r  
def set_real(self, r):  
  self._r = r  
def get_imag(self):  
  return self._i  
def set_imag(self, i):  
  self._i = i  
  
Inheritance  
Class can inherit from multiple base classes.  
Ex. class d(b1, b2):  

Use of classes  
Instantiation: x = Cplx(2, 3)  
Method invocation: r = x.get_real()  
Iterators/Generators  

Method 1: Implement __iter__() class method that returns iterator object (self) that 
  implements __next__() method, which accesses elements one at a time. When there are no 
  more elements, __next__ raises StopIteration exception.  

Method 2 (Generators): Regular functions that use yield statement to return data.  

Ex.  
def reverse(data):   
  for index in range(len(data)-1, -1, -1):  
    yield(data[index])  
  
  for char in reverse('golf'):  
    print(char)   
```
