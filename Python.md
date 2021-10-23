# Python
## Virtual Env
- Create new virtual environment
```python
python -m venv /path/to/your/dir
```

## Jupyter Notebook
- Setup Jupyter Lab
```python
pip install jupyterlab
```

- Setup Jupyer Notebook
```python
pip install notebook
```

- Start Jupyter
```bash
jupyter notebook
```

- Shortcut

| *Function* | *Keyboard Shortcut* | *Menu Tools*     |  
| -------- | ----------------- | ----------------|  
| Run Cell | Ctrl + Enter      | Cell → Run Cell |  
| Create new cell | above: Esc + a, Below: Esc + b | Insert→ Insert Cell Above OR Insert → Insert Cell Below |
| Delete Cell | D + D          | Edit -> Delete Cell      |
| Copy Cell | c                | Copy Key        |
| Paste Cell | v               | Paste Key      |

## Common

- Create obj
```python
"""
Python 2
"""

class Model(object):

    def __init__(self, data):
        for key, value in data.items():
            self.__setattr__(key, value)

class USER(Model):

    def __init__(self, data=None):
        attrs = {
            'id': None,
            'email': None,
            'name': None,
            'address': None,
            'phone': None
        }

        if data:
            attrs = dict((k, data.get(k, attrs[k])) for (k,v) in attrs.items())
        super(USER, self).__init__(attrs)
>>> data = {
            'id': 1,
            'email': 'test@email.com',
            'name': 'User',
            'address': 'test address',
            'phone': '0909090909'
            }
>>> user = USER(data)
>>> user.id
1
>>> user.email
'test@email.com'
>>> user.phone
'0909090909'
```

```python
"""
python 3
"""
class USER:
    'id'= 1,
    'email' = 'test@email.com',
    'name' = 'User',
    'address' =  'test address',
    'phone' = '0909090909'

>>> user = USER(data)
>>> user.id
1
>>> user.email
'test@email.com'
>>> user.phone
'0909090909'

```

- Adding new attribute for obj
```python
>>> male_user = USER()
>>> male_user.sex = 'Male'
>>> male_user.sex 
'Male'
>>> female_user = USER()
>>> female_user.age =  18
>>> female_user.age
18
>>> female_user.sex
AttributeError: 'USER' object has no attribute 'sex'
>>> sex = {
    'sex': 'female',
    'status': 'married'
}
>>> female_user.sex = sex
>>> female_user.sex
{'sex': 'female', 'status': 'married'}
```

## String and Elementss

- String
```python
incoming = 'arbit'
result = '%(s)s hello world %(s)s hello world %(s)s' % {'s': incoming}

>>> result
'arbit hello world arbit hello world arbit'



>>> result = '{0} hello world {0} hello world {1}'format(incoming, 'hello')

>>> result
'arbit hello world arbit hello world hello'

>>> result = 'hello {0}, i am {1} nice to meet {0}, {1} look good!'.format('Android', 'Iphone')
>>> result
'hello Android, i am Iphone nice to meet Android, Iphone look good!'

>>> string = 'hello abc!   I am  def'
>>> string.trim(' ')
'helloabc!Iamdef'

>>> string.trim('hello')
'abc!   I am  def'
```

- Unpacking Elements
```python
>>> record = ('Dave', 'dave@example.com', '773-555-1212', '847-555-1212')
>>> name, email, *phone_numbers = user_record
>>> name
'Dave'
>>> email
'dave@example.com'
>>> phone_numbers
['773-555-1212', '847-555-1212']
##############
>>> line = 'nobody:*:-2:-2:Unprivileged User:/var/empty:/usr/bin/false'
>>> uname, *fields, homedir, sh = line.split(':')
>>> uname
'nobody'
>>> homedir
'/var/empty'
>>> fields
['*', '-2', '-2', 'Unprivileged User']
########### 
"""
    Using *_ to assign unuse value
"""
>>> record = ('ACME', 50, 123.45, (12, 18, 2012))
>>> name, *_, (*_, year) = record
>>> name
'ACME'
>>> year
2012
```

- Keep the last N item 
```python
from collections import deque

def search(lines, pattern, history=5):
    previous_lines = deque(maxlen=history)
    for line in lines:
        if pattern in line:
            yield line, previous_lines
        previous_lines.append(line)
```

- Finding the Largest or Smallest N Items
```python
import heapq
portfolio = [
{'name': 'IBM', 'shares': 100, 'price': 91.1},
{'name': 'AAPL', 'shares': 50, 'price': 543.22},
{'name': 'FB', 'shares': 200, 'price': 21.09},
{'name': 'HPQ', 'shares': 35, 'price': 31.75},
{'name': 'YHOO', 'shares': 45, 'price': 16.35},
{'name': 'ACME', 'shares': 75, 'price': 115.65}
]
cheap = heapq.nsmallest(3, portfolio, key=lambda s: s['price'])
expensive = heapq.nlargest(3, portfolio, key=lambda s: s['price'])

>>> cheap
[{'name': 'YHOO', 'shares': 45, 'price': 16.35},
 {'name': 'FB', 'shares': 200, 'price': 21.09},
 {'name': 'HPQ', 'shares': 35, 'price': 31.75}]
>>> expensive
[{'name': 'AAPL', 'shares': 50, 'price': 543.22},
 {'name': 'ACME', 'shares': 75, 'price': 115.65},
 {'name': 'IBM', 'shares': 100, 'price': 91.1}]
```

- Priority Queue
```python
import heapq

class PriorityQueue:
    def __init__(self):
        self._queue = []
        self._index = 0

    def push(self, item, priority):
        heapq.heappush(self._queue, (-priority, self._index, item))
        self._index += 1
    
    def pop(self):
        return heapq.heappop(self._queue)[-1]


############# Usage
class Item:
    def __init__(self, name):
        self.name = name

    def __repr__(self):
        return 'Item({!r})'.format(self.name)

>>> q = PriorityQueue()
>>> q.push(Item('foo'), 1)
>>> q.push(Item('bar'), 5)
>>> q.push(Item('spam'), 4)
>>> q.push(Item('grok'), 1)
>>> q.pop()
Item('bar')
>>> q.pop()
Item('spam')
>>> q.pop()
Item('foo')
>>> q.pop()
Item('grok')
```

- Mapping Keys to Multiple Values in a Dictionary
```python
from collections import defaultdict

d = defaultdict(list)
d['a'].append(1)
d['a'].append(2)
d['b'].append(4)
>>> d
defaultdict(list, {'a': [1, 2], 'b': [4]})
################
d = defaultdict(set)
d['a'].add(1)
d['a'].add(2)
d['b'].add(4)
>>> d 
defaultdict(set, {'a': {1, 2}, 'b': {4}})
```

- Convert json to object
```python
import json
from types import SimpleNamespace

>>> data = '{"name": "John Smith", "hometown": {"name": "New York", "id": 123}}'
>>> x = json.loads(data, object_hook=lambda d: SimpleNamespace(**d))
>>> print(x.name, x.hometown.name, x.hometown.id)
"John Smith" "New York" 123

```

- Keeping Dictionaries in Order
```python
from collections import OrderedDict
>>> d = OrderedDict()
>>> d['foo'] = 1
>>> d['bar'] = 2
>>> d['spam'] = 3
>>> d['grok'] = 4

>>> for key in d:
...    print(key, d[key])

"foo 1", "bar 2", "spam 3", "grok 4"

################
>>> import json
>>> json.dumps(d)

"foo 1", "bar 2", "spam 3", "grok 4"

```

- Calculating with Dictionaries

```python
prices = {
'ACME': 45.23,
'AAPL': 612.78,
'IBM': 205.55,
'HPQ': 37.20,
'FB': 10.75
}

################
>>> min_price = min(zip(prices.values(), prices.keys()))
>>> print ('min_price is %s' % min_price)
"min_price is (10.75, 'FB')"

################
>>> max_price = max(zip(prices.values(), prices.keys()))
>>> print ('max_price is %s' % max_price)
"max_price is (612.78, 'AAPL'"

################
>>> prices_sorted = sorted(zip(prices.values(), prices.keys()))
>>> print('prices_sorted is %s' % prices_sorted)
"prices_sorted is [(10.75, 'FB'), (37.2, 'HPQ'),(45.23, 'ACME'), (205.55, 'IBM'), (612.78, 'AAPL')]"

################
>>> prices_and_names = zip(prices.values(), prices.keys())
>>> print(min(prices_and_names)) 
True
>>> print(max(prices_and_names)) 
ValueError: max() arg is an empty sequence
```

## Numbers


- Formatting Numbers for Output
```python
>>> x = 1234.56789

# format 1 digt after .
>>> format(x, '0.2f') # define accurate 2 digit after .
'1234.57'

>>> format(x, '>10.1f') # righ accurate place
' 1234.6'

>>> format(x, '<10.1f') # left accurate place
'1234.6'

>>> format(x, '^10.1f') # center
' 1234.6 '

>>> format(x, ',') # format separator
'1,234.56789'

>>> format(x, '0,.1f')
'1,234.6'
```

- Packing and Unpacking Large Integers from Bytes
    + convert from bytes to int
```python
>>> data = b'\x00\x124V\x00x\x90\xab\x00\xcd\xef\x01\x00#\x004'

>>> len(data)
16

>>> int.from_bytes(data, 'little')
69120565665751139577663547927094891008

>>> int.from_bytes(data, 'big')
94522842520747284487117727783387188
```
    + convert from int to bytes

```python

>>> x = 94522842520747284487117727783387188

>>> x.to_bytes(16, 'big')
b'\x00\x124V\x00x\x90\xab\x00\xcd\xef\x01\x00#\x004'

>>> x.to_bytes(16, 'little')
b'4\x00#\x00\x01\xef\xcd\x00\xab\x90x\x00V4\x12\x00'
```
- Matrix and Linear Algebra
    + np

```python
>>> import numpy as np

>>> m = np.matrix([[1,-2,3],[0,4,5],[7,8,-9]])
>>> m
matrix([[ 1, -2, 3],
[ 0, 4, 5],
[ 7, 8, -9]])

>>> m.T
matrix([[ 1, 0, 7],
[-2, 4, 8],
[ 3, 5, -9]])

>>> m.I
matrix([[ 0.33043478, -0.02608696, 0.09565217],
[-0.15217391, 0.13043478, 0.02173913],
[ 0.12173913, 0.09565217, -0.0173913 ]])

>>> v = np.matrix([[2],[3],[4]])
>>> v
matrix([[2],
[3],
[4]])

>>> m * v
matrix([[ 8],[32],[ 2]])
```
    + numpy.linalg

```python
>>> import numpy.linalg

>>> numpy.linalg.det(m)
-229.99999999999983

>>> numpy.linalg.eigvals(m)
array([-13.11474312, 2.75956154, 6.35518158])

>>> x = numpy.linalg.solve(m, v)
>>> x
matrix([[ 0.96521739],
[ 0.17391304],
[ 0.46086957]])

>>> m * x
matrix([[ 2.],
[ 3.],
[ 4.]])
>>> v
matrix([[2],
[3],
[4]])
```

- Random

```python
>>> import random

>>> values = [1, 2, 3, 4, 5, 6]

>>> random.choice(values)
2

>>> random.sample(values, 2)
[6, 2]

>>> random.shuffle(values)
>>> values
[2, 4, 6, 5, 3, 1]

>>> random.randint(0,10)
5

>>> random.random()
0.9406677561675867

>>> random.getrandbits(200)
335837000776573622800628485064121869519521710558559406913275

```

## Datetime

- Converting Days 

```python
>>> from datetime import timedelta

>>> a = timedelta(days=2, hours=6)
>>> b = timedelta(hours=4.5)
>>> c = a + b

>>> c.days
2

>>> c.seconds
37800

>>> c.seconds / 3600
10.5

>>> c.total_seconds() / 3600
58.5

>>> from datetime import datetime

>>> a = datetime(2012, 9, 23)
>>> print(a + timedelta(days=10))
2012-10-03 00:00:00

>>> b = datetime(2012, 12, 21)
>>> d = b - a
>>> d.days
89

>>> now = datetime.today()
>>> print(now)
2012-12-21 14:54:43.094063

>>> print(now + timedelta(minutes=10))
2012-12-21 15:04:43.094063
```

- Calculation
```python
>>> a = datetime(2012, 3, 1)
>>> b = datetime(2012, 2, 28)
>>> a - b
datetime.timedelta(2)

>>> (a - b).days
2
>>> c = datetime(2013, 3, 1)
>>> d = datetime(2013, 2, 28)
>>> (c - d).days
1

```

- Determining Date

```python
from datetime import datetime, timedelta

weekdays = ['Monday', 'Tuesday', 'Wednesday', 'Thursday','Friday', 'Saturday', 'Sunday']

def get_previous_byday(dayname, start_date=None):
    if start_date is None:
        start_date = datetime.today()
        day_num = start_date.weekday()
        day_num_target = weekdays.index(dayname)
        days_ago = (7 + day_num - day_num_target) % 7
    if days_ago == 0:
        days_ago = 7
        target_date = start_date - timedelta(days=days_ago)
    return target_date

>>> datetime.today() # For reference
datetime.datetime(2012, 8, 28, 22, 4, 30, 263076)

>>> get_previous_byday('Monday')
datetime.datetime(2012, 8, 27, 22, 3, 57, 29045)

>>> get_previous_byday('Tuesday') # Previous week, not today
datetime.datetime(2012, 8, 21, 22, 4, 12, 629771)

>>> get_previous_byday('Friday')
datetime.datetime(2012, 8, 24, 22, 5, 9, 911393)
```

- Converting Strings into Datetimes

```python
>>> from datetime import datetime

>>> text = '2012-09-20'
>>> y = datetime.strptime(text, '%Y-%m-%d')
>>> z = datetime.now()
>>> diff = z - y
>>> diff
datetime.timedelta(3, 77824, 177393)

>>> z
datetime.datetime(2012, 9, 23, 21, 37, 4, 177393)
>>> nice_z = datetime.strftime(z, '%A %B %d, %Y')
>>> nice_z
'Sunday September 23, 2012'
```

- Manipulating Dates Involving Time Zones
```python
>>> from datetime import datetime
>>> from pytz import timezone

>>> d = datetime(2012, 12, 21, 9, 30, 0)
>>> print(d)
2012-12-21 09:30:00

>>> central = timezone('US/Central')
>>> loc_d = central.localize(d)
>>> print(loc_d)
2012-12-21 09:30:00-06:00

>>> bang_d = loc_d.astimezone(timezone('Asia/Kolkata'))
>>> print(bang_d)
2012-12-21 21:00:00+05:30

>>> later = central.normalize(loc_d + timedelta(minutes=30)) # format with daylight saving
>>> print(later)
2013-03-10 03:15:00-05:00

```

* Customizing String Formatting

```python
_formats = {
'ymd' : '{d.year}-{d.month}-{d.day}',
'mdy' : '{d.month}/{d.day}/{d.year}',
'dmy' : '{d.day}/{d.month}/{d.year}'
}

class Date:
    def __init__(self, year, month, day):
        self.year = year
        self.month = month
        self.day = day
    
    def __format__(self, code):
        if code == '':
        code = 'ymd'
        fmt = _formats[code]
        return fmt.format(d=self)

>>> d = Date(2012, 12, 21)
>>> format(d)
'2012-12-21'

>>> format(d, 'mdy')
'12/21/2012'

>>> 'The date is {:ymd}'.format(d)
'The date is 2012-12-21'

>>> 'The date is {:mdy}'.format(d)
'The date is 12/21/2012'

```

## Logging
```python
import logging
log_format = '[%(asctime)s]-[%(levelname)s]-[%(filename)s:%(lineno)s- %(funcName)20s() ] \n>>> %(message)s'
loggin.basicConfig(format=log_format, level=logging.DEBUG) #INFO
```

## Pandas
```python
import pandas
pandas.options.mode.chained_assignment = None  # default='warn', igonre warning
```