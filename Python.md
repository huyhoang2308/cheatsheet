# Python
## Virtual Env

```
python -m venv /path/to/your/dir
```

## Jupyter Notebook
- Setup Jupyter Lab
```bash
pip install jupyterlab
```

- Setup Jupyer Notebook
```python
pip install notebook
```

- Start Jupyter
```python
jupyter notebook
```

- Shortcut

| *Function* | *Keyboard Shortcut* | *Menu Tools*     |  
| -------- | ----------------- | ----------------|  
| Run Cell | Ctrl + Enter      | Cell → Run Cell |  
| Create new cell | above: Esc + a, Below: Esc + b | Insert→ Insert Cell Above OR Insert → Insert Cell Below |
| Copy Cell | c                | Copy Key        |
| Paste Cell | v               | Paste Key      |

## Common
- Create obj
```python

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