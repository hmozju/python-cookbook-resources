

```python
data = [120, "hello", (2017,12,3), True]
H,I,J,K = data
print (H,I,J,K)
(year, month, day) = J
print (month, day, year)
```

    120 hello (2017, 12, 3) True
    12 3 2017



```python
def drop_first_last(grades):
    first, *middle, last = grades
    print(*middle)
    return avg(middle)
def avg(middle):
    average = sum(middle) / len(middle)
    return average
lists = [1,2,3,4,5,6,7,8]
drop_first_last(lists)
print(drop_first_last(lists))
```

    2 3 4 5 6 7
    2 3 4 5 6 7
    4.5



```python
def do_foo(x, y):
    print('foo', x, y)
    
def do_bar(s):
    print('bar', s)

records = [('foo', 1, 2),
          ('bar', 'hello'),
          ('foo', 3, 4)]
for tag, *args in records:
    if tag == 'foo':
        do_foo(*args)
    elif tag == 'bar':
        do_bar(*args)
        
```

    foo 1 2
    bar hello
    foo 3 4



```python
line = 'nobody:*:-2:-2:unprivileged User:/var/empty:/usr/bin/false'
uname, *files, homedir, sh = line.split(':')
uname
#homedir
#sh
files
```




    ['*', '-2', '-2', 'unprivileged User']




```python
record = ('ACE', 50, 123.45, (12, 18, 2017))
name, *_, (*_, year) = record
#name
year
```




    2017




```python
def summ(items):
    head, *tail = items
    return head + summ(tail) if tail else head
items = [1, 2, 3, 4, 5]
summ(items)
```




    15




```python
from collections import deque

def search(lines, pattern, history = 5):
    previous_lines = deque(maxlen = history)
    for li in lines:
        if pattern in li:
            yield li, previous_lines
        previous_lines.append(li)

if __name__ == '__main__':
    with open(r'/home/hmin/README.md') as f:
        for line, prevlines in search(f, 'vim', 5):
            for pline in prevlines:
                print(pline, end='')
            print(line, end='')
            print('-' * 60)
```

    [![SpaceVim](https://spacevim.org/logo.png)](https://spacevim.org)
    ------------------------------------------------------------
    [![SpaceVim](https://spacevim.org/logo.png)](https://spacevim.org)
    
    [Wiki](https://github.com/SpaceVim/SpaceVim/wiki) \|
    [Documentation](http://spacevim.org/documentation/) \|
    ------------------------------------------------------------
    [![SpaceVim](https://spacevim.org/logo.png)](https://spacevim.org)
    
    [Wiki](https://github.com/SpaceVim/SpaceVim/wiki) \|
    [Documentation](http://spacevim.org/documentation/) \|
    [Twitter](https://twitter.com/SpaceVim) \|
    [Community](https://spacevim.org/community/) \|
    ------------------------------------------------------------
    [Wiki](https://github.com/SpaceVim/SpaceVim/wiki) \|
    [Documentation](http://spacevim.org/documentation/) \|
    [Twitter](https://twitter.com/SpaceVim) \|
    [Community](https://spacevim.org/community/) \|
    [Gitter **Chat**](https://gitter.im/SpaceVim/SpaceVim) \|
    [中文文档](http://spacevim.org/README_zh_cn/)
    ------------------------------------------------------------
    [Community](https://spacevim.org/community/) \|
    [Gitter **Chat**](https://gitter.im/SpaceVim/SpaceVim) \|
    [中文文档](http://spacevim.org/README_zh_cn/)
    
    [![Build Status](https://travis-ci.org/SpaceVim/SpaceVim.svg?branch=dev)](https://travis-ci.org/SpaceVim/SpaceVim)
    [![Build status](https://ci.appveyor.com/api/projects/status/eh3t5oph70abp665/branch/dev?svg=true)](https://ci.appveyor.com/project/wsdjeg/spacevim/branch/dev)
    ------------------------------------------------------------
    [![MIT License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
    [![Doc](https://img.shields.io/badge/doc-%3Ah%20SpaceVim-orange.svg)](doc/SpaceVim.txt)
    [![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/SpaceVim/SpaceVim.svg)](http://isitmaintained.com/project/SpaceVim/SpaceVim "Average time to resolve an issue")
    [![Percentage of issues still open](http://isitmaintained.com/badge/open/SpaceVim/SpaceVim.svg)](http://isitmaintained.com/project/SpaceVim/SpaceVim "Percentage of issues still open")
    
    SpaceVim is a community-driven vim distribution that supports vim and Neovim.  SpaceVim manages collections of plugins in layers.  Layers make it easy for you, the user, to enable a new language or feature by grouping all the related plugins together.
    ------------------------------------------------------------
    
    Please star the project on github - it is a great way to show your appreciation while providing us motivation to continue working on this project.  The extra visibility for the project doesn't hurt either!
    
    ![welcome-page](https://cloud.githubusercontent.com/assets/13142418/26402270/28ad72b8-40bc-11e7-945e-003f41e057be.png)
    
    See the [documentation](https://spacevim.org/documentation) or [the list of layers](http://spacevim.org/layers/) for more information.
    ------------------------------------------------------------
    ### Install
    
    #### Linux and macOS
    
    ```bash
    curl -sLf https://spacevim.org/install.sh | bash
    ------------------------------------------------------------
    
    ```bash
    curl -sLf https://spacevim.org/install.sh | bash
    ```
    
    After SpaceVim is installed, launch `vim` and SpaceVim will **automatically** install plugins.
    ------------------------------------------------------------
    After SpaceVim is installed, launch `vim` and SpaceVim will **automatically** install plugins.
    
    For more info about the install script, please check:
    
    ```bash
    curl -sLf https://spacevim.org/install.sh | bash -s -- -h
    ------------------------------------------------------------
    curl -sLf https://spacevim.org/install.sh | bash -s -- -h
    ```
    
    #### Windows
    
    The easist way is to download [install.cmd](https://spacevim.org/install.cmd) and run it as administrator, or install SpaceVim manually.
    ------------------------------------------------------------
    - **Beautiful GUI:** you'll love the awesome UI and its useful features.
    - **Mnemonic key bindings:** all key bindings have mnemonic prefixes.
      ![mapping guide](https://user-images.githubusercontent.com/13142418/31550099-c8173ff8-b062-11e7-967e-6378a9c3b467.gif)
    - **Describe key bindings:** use <kbd>SPC h d k</kbd> to describe key bindings.
      ![describe key](https://user-images.githubusercontent.com/13142418/32134986-060a3b8a-bc2a-11e7-89a2-3ee4e616bf06.gif)
    - **Lazy load plugins:** Lazy-load 90% of plugins with [dein.vim](https://github.com/Shougo/dein.vim)
    ------------------------------------------------------------
      ![mapping guide](https://user-images.githubusercontent.com/13142418/31550099-c8173ff8-b062-11e7-967e-6378a9c3b467.gif)
    - **Describe key bindings:** use <kbd>SPC h d k</kbd> to describe key bindings.
      ![describe key](https://user-images.githubusercontent.com/13142418/32134986-060a3b8a-bc2a-11e7-89a2-3ee4e616bf06.gif)
    - **Lazy load plugins:** Lazy-load 90% of plugins with [dein.vim](https://github.com/Shougo/dein.vim)
      ![UI for dein](https://user-images.githubusercontent.com/13142418/31309093-36c01150-abb3-11e7-836c-3ad406bdd71a.gif)
    - **Neovim centric:** Dark powered mode of SpaceVim
    ------------------------------------------------------------
    
    ### Credits & Thanks
    
    - [![GitHub contributors](https://img.shields.io/github/contributors/SpaceVim/SpaceVim.svg)](https://github.com/SpaceVim/SpaceVim/graphs/contributors)
    - [@Gabirel](https://github.com/Gabirel) and his [Hack-SpaceVim](https://github.com/Gabirel/Hack-SpaceVim)
    - [vimdoc](https://github.com/google/vimdoc) generate doc file for SpaceVim
    ------------------------------------------------------------
    ### Credits & Thanks
    
    - [![GitHub contributors](https://img.shields.io/github/contributors/SpaceVim/SpaceVim.svg)](https://github.com/SpaceVim/SpaceVim/graphs/contributors)
    - [@Gabirel](https://github.com/Gabirel) and his [Hack-SpaceVim](https://github.com/Gabirel/Hack-SpaceVim)
    - [vimdoc](https://github.com/google/vimdoc) generate doc file for SpaceVim
    - [Rafael Bodill](https://github.com/rafi) and his vim-config
    ------------------------------------------------------------
    
    - [![GitHub contributors](https://img.shields.io/github/contributors/SpaceVim/SpaceVim.svg)](https://github.com/SpaceVim/SpaceVim/graphs/contributors)
    - [@Gabirel](https://github.com/Gabirel) and his [Hack-SpaceVim](https://github.com/Gabirel/Hack-SpaceVim)
    - [vimdoc](https://github.com/google/vimdoc) generate doc file for SpaceVim
    - [Rafael Bodill](https://github.com/rafi) and his vim-config
    - [Bailey Ling](https://github.com/bling) and his dotvim
    ------------------------------------------------------------



```python
from collections import deque
queue = deque(maxlen=3)
for i in range(3):
    queue.append(i)
queue
queue.append(3)
queue
queue.append(4)
queue
```




    deque([2, 3, 4])




```python
import heapq
nums = [1, 8, 2, 34, 7, -4, 18, 23, 42, 37, 2]
print(heapq.nlargest(3, nums))
print(heapq.nsmallest(3, nums))
```

    [42, 37, 34]
    [-4, 1, 2]



```python
import heapq
portfolio = [
    {'name':'IBM', 'shares':100, 'price': 91.1},
    {'name':'AAPL', 'shares':50, 'price': 543.22},
    {'name':'FB', 'share':200, 'price':21.09},
    {'name':'HPQ', 'share':35, 'price':31.75},
    {'name':'YHOO', 'share':45, 'price':16.35},
    {'name':'ACEM', 'shares':75, 'price': 115.65}
]

cheap = heapq.nsmallest(3, portfolio, key = lambda s: s['price'])
expansive = heapq.nlargest(3, portfolio, key = lambda s: s['price'])

print("the cheapest 3: ")
print(cheap)
print("the expensivest 3: ")
print(expansive)
```

    the cheapest 3: 
    [{'name': 'YHOO', 'share': 45, 'price': 16.35}, {'name': 'FB', 'share': 200, 'price': 21.09}, {'name': 'HPQ', 'share': 35, 'price': 31.75}]
    the expensivest 3: 
    [{'name': 'AAPL', 'shares': 50, 'price': 543.22}, {'name': 'ACEM', 'shares': 75, 'price': 115.65}, {'name': 'IBM', 'shares': 100, 'price': 91.1}]



```python
nums = [1, 8, 2, 23, 7, -4, 18, 23, 42, 37, 2]
import heapq
heapq.heapify(nums)
nums
heapq.heappop(nums)
heapq.heappop(nums)
heapq.heappop(nums)
```




    2




```python
from collections import defaultdict
c = defaultdict(list)
c['a'].append(1)
c['a'].append(2)
c['b'].append(4)
print(c)
d = defaultdict(set)
d['a'].add(1)
d['a'].add(2)
d['b'].add(4)
print(d)
```

    defaultdict(<class 'list'>, {'a': [1, 2], 'b': [4]})
    defaultdict(<class 'set'>, {'a': {1, 2}, 'b': {4}})



```python
d = {}
for key, value in pairs:
    if key not in d:
        d[key] = []
    d[key].append(value)
    
    
d = defaultdict(list)
for key, value in pairs:
    d[key].append(value)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-62-236b6871b67f> in <module>()
          1 d = {}
    ----> 2 for key, value in pairs:
          3     if key not in d:
          4         d[key] = []
          5     d[key].append(value)


    NameError: name 'pairs' is not defined



```python
from collections import OrderedDict
import json

def ordered_dict():
    d = OrderedDict()
    d['foo'] = 1
    d['bar'] = 2
    d['spam'] = 3
    d['grok'] = 4
    '''
    for key in d:
        print(key, d[key])
    '''    
    print(json.dumps(d))
    
if __name__ == '__main__':
    ordered_dict()
```

    {"foo": 1, "bar": 2, "spam": 3, "grok": 4}



```python
prices = {
    'ACME':45.23,
    'AAPL':612.78,
    'IBM':205.55,
    'HPQ':37.20,
    'FB':10.75
}

min_price = min(zip(prices.values(), prices.keys()))
max_price = max(zip(prices.values(), prices.keys()))

print(min_price, max_price)
```

    (10.75, 'FB') (612.78, 'AAPL')



```python
prices = {
    'ACME':45.23,
    'AAPL':612.78,
    'IBM':205.55,
    'HPQ':37.20,
    'FB':10.75
}
prices_sorted = sorted(zip(prices.values(), prices.keys()))
print(prices_sorted)
```

    [(10.75, 'FB'), (37.2, 'HPQ'), (45.23, 'ACME'), (205.55, 'IBM'), (612.78, 'AAPL')]



```python
a = {
    'x':1,
    'y':2,
    'z':3
}

b = {
    'w':10,
    'x':11,
    'y':2
}

a.keys() & b.keys()
a.keys() - b.keys()
a.items() & b.items()
```




    {('y', 2)}




```python
a = {
    'x':1,
    'y':2,
    'z':3
}

b = {
    'w':10,
    'x':11,
    'y':2
}
c = {key:a[key] for key in a.keys() - {'z', 'w'}}
print(c)
```

    {'y': 2, 'x': 1}



```python
def dedupe(items):
    seen = set()
    for item in items:
        if item not in seen:
            yield item
            seen.add(item)
a = [1, 5, 2, 1, 9, 5, 1, 10]
list(dedupe(a))
```




    [1, 5, 2, 9, 10]




```python
def dedupe(items, key = None):
    seen = set()
    for item in items:
        val = item if key is None else key(item)
        if val not in seen:
            yield item
            seen.add(val)
a =[
    {'x':1, 'y':2},
    {'x':1, 'y':3},
    {'x':1, 'y':2},
    {'x':2, 'y':4}
]
list(dedupe(a, key = lambda d: (d['x'], d['y'])))

```




    [{'x': 1, 'y': 2}, {'x': 1, 'y': 3}, {'x': 2, 'y': 4}]




```python
# 切片
shares = slice(20, 23)
price = slice(31, 37)

record = '....................100........513.25..........'

shares_stock = int(record[shares])
price_stock = float(record[price])

cost = shares_stock * price_stock
print(cost)
```

    51325.0



```python
words = [
    'look', 'into', 'my', 'eyes', 'look', 'into', 'my', 'eyes', 'the', 'eyes', 'the', 'eyes', 'the', 'eyes', 'not', 'around', 'the', 'eyes', "don't", 'look', 'around', 'the',
    'eyes', 'look', 'into', 'my', 'eyes', "you're", 'under'
]

from collections import Counter

word_counts = Counter(words)

top_three = word_counts.most_common(3)
print(top_three)
```

    [('eyes', 8), ('the', 5), ('look', 4)]



```python
word_counts['not']
word_counts
```




    Counter({'are': 7,
             'around': 2,
             "don't": 1,
             'eyes': 15,
             'in': 7,
             'into': 3,
             'look': 4,
             'looking': 7,
             'my': 10,
             'not': 8,
             'the': 5,
             'under': 1,
             'why': 7,
             'you': 7,
             "you're": 1})




```python
morewords = ['why', 'are', 'you', 'not', 'looking', 'in', 'my', 'eyes']
'''
for word in morewords:
    word_counts[word] += 1

word_counts
'''
# or 
word_counts.update(morewords)
word_counts
```




    Counter({'are': 7,
             'around': 2,
             "don't": 1,
             'eyes': 15,
             'in': 7,
             'into': 3,
             'look': 4,
             'looking': 7,
             'my': 10,
             'not': 8,
             'the': 5,
             'under': 1,
             'why': 7,
             'you': 7,
             "you're": 1})




```python
a = Counter(words)
b = Counter(morewords)
a
b
```




    Counter({'are': 1,
             'eyes': 1,
             'in': 1,
             'looking': 1,
             'my': 1,
             'not': 1,
             'why': 1,
             'you': 1})




```python
c = a + b
c
d = a - b
d
```




    Counter({'around': 2,
             "don't": 1,
             'eyes': 7,
             'into': 3,
             'look': 4,
             'my': 2,
             'the': 5,
             'under': 1,
             "you're": 1})




```python
rows = [
    {'fname':'Brian', 'lname':'Jones', 'uid':1003},
    {'fname':'David', 'lname':'Beazley', 'uid':1002},
    {'fname':'John', 'lname':'Cleese', 'uid':1001},
    {'fname':'Big', 'lname':'Jones', 'uid':1004},
]

from operator import itemgetter
rows_by_fname = sorted(rows, key=itemgetter('fname'))
rows_by_uid = sorted(rows, key=itemgetter('uid'))
rows_by_lfname = sorted(rows, key=lambda r:(r['lname'], r['fname']))
rows_by_uidmin = min(rows, key=itemgetter('uid'))
rows_by_uidmax = max(rows, key=itemgetter('uid'))

print(rows_by_fname)
print(rows_by_uid)
print(rows_by_lfname)
print(rows_by_uidmin)
print(rows_by_uidmax)
```

    [{'fname': 'Big', 'lname': 'Jones', 'uid': 1004}, {'fname': 'Brian', 'lname': 'Jones', 'uid': 1003}, {'fname': 'David', 'lname': 'Beazley', 'uid': 1002}, {'fname': 'John', 'lname': 'Cleese', 'uid': 1001}]
    [{'fname': 'John', 'lname': 'Cleese', 'uid': 1001}, {'fname': 'David', 'lname': 'Beazley', 'uid': 1002}, {'fname': 'Brian', 'lname': 'Jones', 'uid': 1003}, {'fname': 'Big', 'lname': 'Jones', 'uid': 1004}]
    [{'fname': 'David', 'lname': 'Beazley', 'uid': 1002}, {'fname': 'John', 'lname': 'Cleese', 'uid': 1001}, {'fname': 'Big', 'lname': 'Jones', 'uid': 1004}, {'fname': 'Brian', 'lname': 'Jones', 'uid': 1003}]
    {'fname': 'John', 'lname': 'Cleese', 'uid': 1001}
    {'fname': 'Big', 'lname': 'Jones', 'uid': 1004}



```python
class User:
    def __init__(self, user_id):
        self.user_id = user_id
    def __repr__(self):
        return 'User({})'.format(self.user_id)

def sort_notcompare():
    users = [User(23), User(3), User(99)]
    print(users)
    print(sorted(users, key=lambda u:u.user_id))

sort_notcompare()


```

    [User(23), User(3), User(99)]
    [User(3), User(23), User(99)]



```python
from operator import attrgetter

class User:
    def __init__(self, user_id):
        self.user_id = user_id
    def __repr__(self):
        return 'User({})'.format(self.user_id)
    
users = [User(23), User(3), User(99)]
print(sorted(users, key=attrgetter('user_id')))
print(min(users, key=attrgetter('user_id')))
print(max(users, key=attrgetter('user_id')))
```

    [User(3), User(23), User(99)]
    User(3)
    User(99)



```python
rows = [
    {'address':'5412 N CLARK', 'date':'07/01/2017'},
    {'address':'5148 N CLARK', 'date':'07/02/2017'},
    {'address':'5800 E 58TH', 'date':'07/03/2017'},
    {'address':'2122 N CLARK', 'date':'07/03/2017'},
    {'address':'5645 N RAVENSWOOD', 'date':'07/02/2017'},
    {'address':'1060 W ADDISON', 'date':'07/02/2017'},
    {'address':'4801 N BROASWAY', 'date':'07/01/2017'},
    {'address':'1039 W GRANVILLE', 'date':'07/04/2017'}
]

from operator import itemgetter
from itertools import groupby

rows.sort(key=itemgetter('date'))
for date, items in groupby(rows, key=itemgetter('date')):
    print(date)
    for i in items:
        print(' ', i)
```

    07/01/2017
      {'address': '5412 N CLARK', 'date': '07/01/2017'}
      {'address': '4801 N BROASWAY', 'date': '07/01/2017'}
    07/02/2017
      {'address': '5148 N CLARK', 'date': '07/02/2017'}
      {'address': '5645 N RAVENSWOOD', 'date': '07/02/2017'}
      {'address': '1060 W ADDISON', 'date': '07/02/2017'}
    07/03/2017
      {'address': '5800 E 58TH', 'date': '07/03/2017'}
      {'address': '2122 N CLARK', 'date': '07/03/2017'}
    07/04/2017
      {'address': '1039 W GRANVILLE', 'date': '07/04/2017'}



```python
rows = [
    {'address':'5412 N CLARK', 'date':'07/01/2017'},
    {'address':'5148 N CLARK', 'date':'07/02/2017'},
    {'address':'5800 E 58TH', 'date':'07/03/2017'},
    {'address':'2122 N CLARK', 'date':'07/03/2017'},
    {'address':'5645 N RAVENSWOOD', 'date':'07/02/2017'},
    {'address':'1060 W ADDISON', 'date':'07/02/2017'},
    {'address':'4801 N BROASWAY', 'date':'07/01/2017'},
    {'address':'1039 W GRANVILLE', 'date':'07/04/2017'}
]

from collections import defaultdict
rows_by_date = defaultdict(list)
for row in rows:
    rows_by_date[row['date']].append(row)
    
print(rows_by_date['07/01/2017'])
```

    [{'address': '5412 N CLARK', 'date': '07/01/2017'}, {'address': '4801 N BROASWAY', 'date': '07/01/2017'}]



```python
mylist = [-1, 1, 2, 4, -3, 5, -2, -9, 6, -8, 10, -7, 7]
pos = (n for n in mylist if n > 0)
print(pos)
for x  in pos:
    print(x)
```

    <generator object <genexpr> at 0x7febb8edffc0>
    1
    2
    4
    5
    6
    10
    7



```python
values = ['1', '2', '-3.5', '-', '4', 'N/A', '5']

def is_int(val):
    try:
        x = float(val)
        return True
    except ValueError:
        return False

ivals = list(filter(is_int, values))
print(ivals)

print(is_int(3.4))

```

    ['1', '2', '-3.5', '4', '5']
    True



```python
mylist = [1, 4, -5, 10, -7, 2, 3, -1]
import math

def root(x):
    if x > 0:
        return math.sqrt(x)


after_filter = filter(root, mylist)
list(after_filter)

```




    [1, 4, 10, 2, 3]




```python
addresses = [
    '5412 N CLARK',
    '5148 N CLARK',
    '5800 E 58TH',
    '2122 N CLARK',
    '5645 N RAVENSWOOD',
    '1060 W ADDISON',
    '4801 N BROADWAY',
    '1039 W GRANVILLE'
]

counts = [0, 3, 10, 4, 1, 7, 6, 1]
from itertools import compress
more5 = [n > 5 for n in counts]
more5
list(compress(addresses, more5))

```




    ['5800 E 58TH', '1060 W ADDISON', '4801 N BROADWAY']




```python
prices = {
    'ACME':45.23,
    'AAPL':612.78,
    'IBM':205.55,
    'HPQ':37.20,
    'FB':10.75
}

p1 = {key:value for key, value in prices.items() if value > 200}
tech_names = {'AAPL', 'IBM', 'HPQ', "MSFT"}
p2 = {key:value for key, value in prices.items() if key in tech_names}

print(p1,p2)
```

    {'AAPL': 612.78, 'IBM': 205.55} {'AAPL': 612.78, 'IBM': 205.55, 'HPQ': 37.2}



```python
prices = {
    'ACME':45.23,
    'AAPL':612.78,
    'IBM':205.55,
    'HPQ':37.20,
    'FB':10.75
}
tech_names = {'AAPL', 'IBM', 'HPQ', "MSFT"}

p1 = dict((key, value) for key, value in prices.items() if value > 200)
p2 = {key:prices[key] for key in prices.keys() & tech_names}      # 这里的&不可换成 and， 因为 and 是 逻辑与，而 & 是求两个集合的交集

print(p1, p2)
```

    {'AAPL': 612.78, 'IBM': 205.55} {'IBM': 205.55, 'HPQ': 37.2, 'AAPL': 612.78}



```python
from collections import namedtuple
# 以下建立了一个类
Subscriber = namedtuple('Subscriber', ['addr', 'joined'])
# 初始化类
sub = Subscriber('jonesy@example.com', '2017-10-19')
sub
print(sub.addr)
print(sub.joined)
```

    jonesy@example.com
    2017-10-19



```python
from collections import namedtuple

Stock = namedtuple('Stock', ['name', 'shares', 'price'])

def compute_cost(records):
    total = 0.0
    for rec in records:
        s = Stock(*rec)
        total += s.shares * s.price
    return total

s = Stock('ACME', 100, 123.45)
q = Stock('APPL', 100, 129.4)
p = Stock('PL', 23, 100)
al = (s, p, q)
print(s)
print(s.shares)

print(compute_cost(al))

s = s._replace(shares = 75)
print(s, s.shares)
```

    Stock(name='ACME', shares=100, price=123.45)
    100
    27585.0
    Stock(name='ACME', shares=75, price=123.45) 75



```python
from collections import namedtuple

Stock = namedtuple('Stock', ['name', 'shares', 'price', 'date', 'time'])

# 创建一个原型实例
stock_prototype = Stock('', 0, 0.0, None, None)

# 将一个字典转换成一个Stock实例

def dict_to_stock(s):
    return stock_prototype._replace(**s)

a = {'name': 'ACME', 'shares': 100, 'price': 123.45}
print(dict_to_stock(a))

b = {'name': 'ACME', 'shares': 100, 'price': 123.45, 'date':'12/12/2017'}
print(dict_to_stock(b))
```

    Stock(name='ACME', shares=100, price=123.45, date=None, time=None)
    Stock(name='ACME', shares=100, price=123.45, date='12/12/2017', time=None)



```python
import os
files = os.listdir('/home/hmin/桌面/')
if any(name.endswith('.py') for name in files):
    print('There be python!')
else:
    print('Sorry, no python.')
    
s = ('ACE', 50, 123.45)
print('===>'.join(str(x) for x in s))

```

    There be python!
    ACE===>50===>123.45



```python
portfolio = [
    {'name':'GOOG', 'shares': 50},
    {'name':'YAHOO', 'shares':75},
    {'name':'AOL', 'shares': 20},
    {'name':'SCOX', 'shares': 65}
]

min_shares = min(s['shares'] for s in portfolio)
min_shares1 = min(portfolio, key=lambda s:s['shares'])
print(min_shares)
print(min_shares1)
```

    20
    {'name': 'AOL', 'shares': 20}



```python
a = {'x':1, 'z':3}
b = {'y':2, 'z':4}
from collections import ChainMap
c = ChainMap(a,b)        # 先在 a 中查找 ，如找不到再在 b 中找
print(c['x'])
print(c['y'])
print(c['z'])
print(c)
len(c)
list(c.keys())
list(c.values())

c['z'] = 10
c['w'] = 40
del c['x']
a

#   del c['y']   ## not allowed cause there is no y in a and b allways not be checked
```

    1
    2
    3
    ChainMap({'x': 1, 'z': 3}, {'y': 2, 'z': 4})





    {'w': 40, 'z': 10}




```python
a = {'x': 1, 'z': 3}
b = {'y': 2, 'z': 4}
merged = dict(b)
merged.update(a)
print(merged)
```

    {'y': 2, 'z': 3, 'x': 1}



```python
from collections import ChainMap
values = ChainMap()
values['x'] = 1
values = values.new_child()
values['x'] = 2
values = values.new_child()
values['x'] = 3
print(values)
values['x']
values = values.parents
values['x']
values = values.parents
values['x']
values
```

    ChainMap({'x': 3}, {'x': 2}, {'x': 1})





    ChainMap({'x': 1})




```python
a = {'x': 1, 'z': 3}
b = {'y': 2, 'z': 4}
merged = ChainMap(a, b)
merged['x']
a['x'] = 42
merged['x']
```




    42


