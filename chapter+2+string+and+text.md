

```python
line = 'asdf fjdk; afed, fjek,asdf,  foo'
import re

# 分割的依据是 [ ;  ,  空格 ]  外加每种情形可能紧跟的一个或多个空格
re.split(r'[;,\s]\s*', line)
```




    ['asdf', 'fjdk', 'afed', 'fjek', 'asdf', 'foo']




```python
a = ['a', 'b', 'c', 'd', 'e']
b = ['1', '2', '3', '4', '5']
zipped = zip(a, b)
ps = '&&'.join(v+d for v, d in zipped)
print(ps)
```

    a1&&b2&&c3&&d4&&e5



```python
line = 'asdf fjdk; afed, fjek,asdf,  foo'
import re 

fields = re.split(r'(;|,|\s)\s*', line)
print(fields)

values = fields[::2]
delimiters = fields[1::2] + ['']

print(values)
print (delimiters)

print('*'.join(v+d for v,d in zip(values, delimiters)))

```

    ['asdf', ' ', 'fjdk', ';', 'afed', ',', 'fjek', ',', 'asdf', ',', 'foo']
    ['asdf', 'fjdk', 'afed', 'fjek', 'asdf', 'foo']
    [' ', ';', ',', ',', ',', '']
    asdf *fjdk;*afed,*fjek,*asdf,*foo



```python
# 如果不想保留分割字符串到结果列表中去，但仍然需要使用到括号来分组正则表达式的话，确保你的分组是非捕获分组，形如(?: ...)

import re
line = 'asdf fjdk; afed, fjek,asdf,  foo'
re.split(r'(?:;|,|\s)\s*', line)
```




    ['asdf', 'fjdk', 'afed', 'fjek', 'asdf', 'foo']




```python
filename = 'spam.txt'
print(filename.endswith('.txt'))
print(filename.startswith('file:'))

url = 'http://www.python.org'
print(url.startswith('http:'))

```

    True
    False
    True



```python
import os
filenames = os.listdir('.')
filenames
print([name for name in filenames if name.endswith(('s','d'))])
any(name.endswith('.h') for name in filenames)
```

    ['.xsession-errors', 'README.md', 'books', 'readme.gitee.md', 'autoload', '.ipynb_checkpoints', '.TeXworks', '.dbus', '.xsession-errors.old', '.SpaceVim.d', '.thumbnails', '.thunderbird', 'docs']





    False




```python
from urllib.request import urlopen

def read_data(name):
    if name.startswith(('http:', 'https:', 'ftp:')):
        response = urlopen(name).read()
        with open('./responses', 'wb') as resp:
            resp.write(response)
    else:
        with open(name) as f:
            return f.read()

urls = ['https://www.github.com', 'http://www.baidu.com', 'http://www.taobao.com', 'https://www.163.com']

for url in urls:
    result = read_data(url)
    print (result)
```

    None
    None
    None



    ---------------------------------------------------------------------------

    SSLError                                  Traceback (most recent call last)

    ~/anaconda3/lib/python3.6/urllib/request.py in do_open(self, http_class, req, **http_conn_args)
       1317                 h.request(req.get_method(), req.selector, req.data, headers,
    -> 1318                           encode_chunked=req.has_header('Transfer-encoding'))
       1319             except OSError as err: # timeout error


    ~/anaconda3/lib/python3.6/http/client.py in request(self, method, url, body, headers, encode_chunked)
       1238         """Send a complete request to the server."""
    -> 1239         self._send_request(method, url, body, headers, encode_chunked)
       1240 


    ~/anaconda3/lib/python3.6/http/client.py in _send_request(self, method, url, body, headers, encode_chunked)
       1284             body = _encode(body, 'body')
    -> 1285         self.endheaders(body, encode_chunked=encode_chunked)
       1286 


    ~/anaconda3/lib/python3.6/http/client.py in endheaders(self, message_body, encode_chunked)
       1233             raise CannotSendHeader()
    -> 1234         self._send_output(message_body, encode_chunked=encode_chunked)
       1235 


    ~/anaconda3/lib/python3.6/http/client.py in _send_output(self, message_body, encode_chunked)
       1025         del self._buffer[:]
    -> 1026         self.send(msg)
       1027 


    ~/anaconda3/lib/python3.6/http/client.py in send(self, data)
        963             if self.auto_open:
    --> 964                 self.connect()
        965             else:


    ~/anaconda3/lib/python3.6/http/client.py in connect(self)
       1399             self.sock = self._context.wrap_socket(self.sock,
    -> 1400                                                   server_hostname=server_hostname)
       1401             if not self._context.check_hostname and self._check_hostname:


    ~/anaconda3/lib/python3.6/ssl.py in wrap_socket(self, sock, server_side, do_handshake_on_connect, suppress_ragged_eofs, server_hostname, session)
        406                          server_hostname=server_hostname,
    --> 407                          _context=self, _session=session)
        408 


    ~/anaconda3/lib/python3.6/ssl.py in __init__(self, sock, keyfile, certfile, server_side, cert_reqs, ssl_version, ca_certs, do_handshake_on_connect, family, type, proto, fileno, suppress_ragged_eofs, npn_protocols, ciphers, server_hostname, _context, _session)
        813                         raise ValueError("do_handshake_on_connect should not be specified for non-blocking sockets")
    --> 814                     self.do_handshake()
        815 


    ~/anaconda3/lib/python3.6/ssl.py in do_handshake(self, block)
       1067                 self.settimeout(None)
    -> 1068             self._sslobj.do_handshake()
       1069         finally:


    ~/anaconda3/lib/python3.6/ssl.py in do_handshake(self)
        688         """Start the SSL/TLS handshake."""
    --> 689         self._sslobj.do_handshake()
        690         if self.context.check_hostname:


    SSLError: [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:777)

    
    During handling of the above exception, another exception occurred:


    URLError                                  Traceback (most recent call last)

    <ipython-input-5-78ccad085c5a> in <module>()
         13 
         14 for url in urls:
    ---> 15     result = read_data(url)
         16     print (result)


    <ipython-input-5-78ccad085c5a> in read_data(name)
          3 def read_data(name):
          4     if name.startswith(('http:', 'https:', 'ftp:')):
    ----> 5         response = urlopen(name).read()
          6         with open('./responses', 'wb') as resp:
          7             resp.write(response)


    ~/anaconda3/lib/python3.6/urllib/request.py in urlopen(url, data, timeout, cafile, capath, cadefault, context)
        221     else:
        222         opener = _opener
    --> 223     return opener.open(url, data, timeout)
        224 
        225 def install_opener(opener):


    ~/anaconda3/lib/python3.6/urllib/request.py in open(self, fullurl, data, timeout)
        524             req = meth(req)
        525 
    --> 526         response = self._open(req, data)
        527 
        528         # post-process response


    ~/anaconda3/lib/python3.6/urllib/request.py in _open(self, req, data)
        542         protocol = req.type
        543         result = self._call_chain(self.handle_open, protocol, protocol +
    --> 544                                   '_open', req)
        545         if result:
        546             return result


    ~/anaconda3/lib/python3.6/urllib/request.py in _call_chain(self, chain, kind, meth_name, *args)
        502         for handler in handlers:
        503             func = getattr(handler, meth_name)
    --> 504             result = func(*args)
        505             if result is not None:
        506                 return result


    ~/anaconda3/lib/python3.6/urllib/request.py in https_open(self, req)
       1359         def https_open(self, req):
       1360             return self.do_open(http.client.HTTPSConnection, req,
    -> 1361                 context=self._context, check_hostname=self._check_hostname)
       1362 
       1363         https_request = AbstractHTTPHandler.do_request_


    ~/anaconda3/lib/python3.6/urllib/request.py in do_open(self, http_class, req, **http_conn_args)
       1318                           encode_chunked=req.has_header('Transfer-encoding'))
       1319             except OSError as err: # timeout error
    -> 1320                 raise URLError(err)
       1321             r = h.getresponse()
       1322         except:


    URLError: <urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:777)>



```python
filename = 'spam.txt'
filename[-4:] == '.txt'
url = 'http://www.python.org'
if url[:5] == 'http:' or url[:6] == 'https:' or url[:4] == 'ftp:':
    print ('true')
```

    true



```python
import re
url = 'http://www.python.org'
re.match('http:|https:|ftp:', url)
```




    <_sre.SRE_Match object; span=(0, 5), match='http:'>




```python
from fnmatch import fnmatch, fnmatchcase
fnmatch('foo.txt', '*.txt')
fnmatch('foo.txt', '?oo.txt')
fnmatch('Dat45.csv', 'Dat[0-9]*')
names = ['Dat1.csv', 'Dat2.csv', 'config.ini', 'foo.py']
[name for name in names if fnmatch(name, 'Dat*.csv')]
```




    ['Dat1.csv', 'Dat2.csv']




```python
# 对大小写敏感的 fnmatchcase, 在Linux和Mac上，fnmatch通常是对大小写敏感的，Windows上不敏感
fnmatchcase('foo.txt', '*.TXT')
```




    False




```python
addresses = [
    '5412 N CLARK ST',
    '1060 W AADISON ST',
    '1039 W GRANVILLE AVE',
    '2122 N CLARK ST',
    '4802 N BROADWAY'
]
from fnmatch import fnmatchcase
[addr for addr in addresses if fnmatchcase(addr, '*ST')]
[addr for addr in addresses if fnmatchcase(addr, '54[0-9][0-9] *')]
```




    ['5412 N CLARK ST']




```python
# 字面字符串，通常只需要调用基本字符串方法就OK了， str.find(), str.endswith(), str.startswith()
text = 'yeah, but no, but yeah, but no, but yeah'
print(text == 'yeah')
print(text.endswith('no'))
print(text.startswith('yeah'))
print(text.find('no'))  # 第一次出现的位置，从0开始计
```

    False
    False
    True
    10



```python
# 对于复杂的匹配需要使用正则表达式和re模块，为了解释正则表达式的基本原理，假设匹配数字格式的日期字符串如 11/27/1017

text1 = '11/27/2017'
text2 = 'Nov 27, 2017'
import re
if re.match(r'\d+/\d+/\d+', text1):
    print('yes')
else:
    print('no')

if re.match(r'\d+/\d+/\d+', text2):
    print('yes')
else:
    print('no')
```

    yes
    no



```python
# match 总是从字符串开始去匹配， 查找字符串任意部分的模式出现位置， 使用findall()方法代替
text1 = '11/27/2017'
text2 = 'Nov 27, 2017'
text = [text1, text2]
import re
datepat = re.compile(r'\d+/\d+/\d+')
for i in text:
    if datepat.match(i):
        print('yes')
    else:
        print('no')
```

    yes
    no



```python
import re
datepat = re.compile(r'\d+/\d+/\d+')
text = 'Today is 11/27/2017. PyCon starts 3/13/2018.'
m = datepat.findall(text)
for i in m:
    print(i)

```

    11/27/2017
    3/13/2018



```python
import re
datepat = re.compile(r'(\d+)/(\d+)/(\d+)')
m_test = datepat.match('11/27/2017')
m_test.groups()
month, day, year = m_test.groups()
print('{}-{}-{}'.format(year, month, day))
```

    2017-11-27



```python
import re
text = 'Today is 12/06/2017. PyCon starts 3/13/2018.'
datepat = re.compile(r'(\d+)/(\d+)/(\d+)')
ma = datepat.findall(text)
ma

for month, day, year in ma:
    print('{}-{}-{}'.format(year, month, day))
```

    2017-12-06
    2018-3-13



```python
import re
text = 'Today is 12/06/2017. PyCon starts 3/13/2018.'
datepat = re.compile(r'(\d+)/(\d+)/(\d+)')
mb = datepat.finditer(text)     # 返回一个可迭代对象，对象的每个成员是一个tuple，每个tuple包含了month，day, year三个元素
print(mb)
for i in mb:
    temp = i.groups()
    print(temp)
    month, day, year = temp
    print('{}-{}-{}'.format(year, month, day))
```

    <callable_iterator object at 0x7f8b500e75f8>
    ('12', '06', '2017')
    2017-12-06
    ('3', '13', '2018')
    2018-3-13



```python
# 简单的字面字符串模式，直接使用str.replace()方法即可
text = 'yeah, but no, but yeah, but no, but yeah'
text.replace('yeah', 'yep')

```




    'yep, but no, but yep, but no, but yep'




```python
text = 'Today is 11/27/2017. PyCon starts 3/13/2018.'
import re
subs = re.sub(r'(\d+)/(\d+)/(\d+)', r'\3-\1-\2', text)
print(subs)

# sub()中的第一个参数是被匹配的模式， 第二个参数是替换模式。反斜杠数字\1 \2 \3 是前面模式的捕获组号

```

    Today is 2017-11-27. PyCon starts 2018-3-13.



```python
text = 'Today is 11/27/2017. PyCon starts 3/13/2018.'
import re
datepat = re.compile(r'(\d+)/(\d+)/(\d+)')
subs = datepat.sub(r'\3-\1-\2', text)
print(subs)

```

    Today is 2017-11-27. PyCon starts 2018-3-13.



```python
text = 'Today is 11/27/2017. PyCon starts 3/13/2018.'
from calendar import month_abbr

def change_date(m):
    mon_name = month_abbr[int(m.group(1))]
    return '{} {} {}'.format(m.group(2), mon_name, m.group(3))

datepat = re.compile(r'(\d+)/(\d+)/(\d+)')
# 一个替换回调函数的参数是一个match对象，即match()或find()返回的对象。使用group()方法来提取特定的匹配部分，回调函数返回替换字符串
datepat.sub(change_date, text)
```




    'Today is 27 Nov 2017. PyCon starts 13 Mar 2018.'




```python
newtext, n = datepat.subn(r'\3-\1-\2', text)
print(newtext)
print(n)    # 替换的数量

```

    Today is 2017-11-27. PyCon starts 2018-3-13.
    2



```python
# 忽略大小写的方式搜索和替换文本字符串

text = 'UPPER PYTHON, lower python, Mixed Python'
result_a = re.findall('python', text, flags = re.IGNORECASE)
result_b = re.sub('python', 'snake', text, flags = re.IGNORECASE)
print(result_a)
print(result_b)
```

    ['PYTHON', 'python', 'Python']
    UPPER snake, lower snake, Mixed snake



```python
text = 'UPPER PYTHON, lower python, Mixed Python'
import re

def matchcase(word):
    def replace(m):
        text = m.group()
        if text.isupper():
            return word.upper()
        elif text.islower():
            return word.lower()
        elif text[0].isupper():
            return word.capitalize()
        else:
            return word
    return replace

subspat = re.compile(r'PYTHON|Python|python')
aftersubs = subspat.sub(matchcase('snake'), text)
print(aftersubs)

#或者

re.sub('python', matchcase('snake'), text, flags = re.IGNORECASE)


```

    UPPER SNAKE, lower snake, Mixed Snake





    'UPPER SNAKE, lower snake, Mixed Snake'




```python
import re
str_pat = re.compile(r'\"(.*)\"')
text1 = 'Computer says "no."'
print(str_pat.findall(text1))

text2 = 'Computer says "no." Phone says "yes."'
print(str_pat.findall(text2))

str_pat2 = re.compile(r'\"(.*?)\"')
print(str_pat2.findall(text2))
```

    ['no.']
    ['no." Phone says "yes.']
    ['no.', 'yes.']



```python
import re
comment = re.compile(r'/\*(.*?)\*/')
text1 = '/* this is a comment */'
text2 = ''' /* this is a 
 multiline comment */
'''
print(comment.findall(text1))
print(comment.findall(text2))

comment1 = re.compile(r'/\*((?:.|\n)*?)\*/')
print(comment1.findall(text2))
```

    [' this is a comment ']
    []
    [' this is a \n multiline comment ']



```python
s1 = 'Spicy Jalape\u00f1o'
s2 = 'Spicy Jalapen\u0303o'
print(s1)
print(s2)
print(s1 == s2)
print(len(s1))
print(len(s2))
```

    Spicy Jalapeño
    Spicy Jalapeño
    False
    14
    15



```python
import unicodedata
s1 = 'Spicy Jalape\u00f1o'
s2 = 'Spicy Jalapen\u0303o'
t1 = unicodedata.normalize('NFC', s1)
t2 = unicodedata.normalize('NFC', s2)

print(t1 == t2)

print(ascii(t1))

t3 = unicodedata.normalize('NFD', s1)
t4 = unicodedata.normalize('NFD', s2)
print(t3 == t4)
print(ascii(t3))
```

    True
    'Spicy Jalape\xf1o'
    True
    'Spicy Jalapen\u0303o'



```python
import unicodedata
s = '\ufb01'
print(s)
print(unicodedata.normalize('NFD', s))
print(unicodedata.normalize('NFKD', s))
print(unicodedata.normalize('NFKC', s))
```

    ﬁ
    ﬁ
    fi
    fi



```python
import re
num = re.compile('\d+')
matched = num.match('123')
print(matched)
```

    <_sre.SRE_Match object; span=(0, 3), match='123'>



```python
# Whitespace stripping

s = ' hello world \n'
print(s.strip())
print(s.lstrip())
print(s.rstrip())

# Character stripping

t = '-----hello====='
print(t.lstrip('-'))
print(t.rstrip('='))
print(t.strip('-='))

```

    hello world
    hello world 
    
     hello world
    hello=====
    -----hello
    hello



```python
# 注意：strip()只会对文本字符串的两端空格起作用，而不会对字符串中间文本产生影响

s = ' hello      world \n'
s = s.strip()
print(s)

s = s.replace(' ', '')
print(s)
```

    hello      world
    helloworld



```python
import re
s = '   hello     world   \n'
reformat = re.compile(r'\s+')
s = reformat.sub(' ', s)
print(s)
```

     hello world 



```python
with open('./fresint.m', 'rb') as f:
    lines = (line.strip() for line in f)
    for line in lines:
        print(line)

```

    b'% fast computation of Fresnel intergral:'
    b'% \xa1\xd2exp(i * pi/2 * t^2)dt = C(x) + i * S(x)'
    b'% return {C(x1) - C(x0)} + i * {S(x1) - S(x0)};'
    b'% Based on'
    b'% By Enrong Li, IHEP,China'
    b'function FRES = fresint(lower, upper)'
    b''
    b'Cb = [ 1i*0.318309844,                 (0.101321519 + 1i*9.34626e-8),...'
    b'(-4.07292e-5 - 1i*0.09676631),   (-0.152068115 + 1i*0.000606222),...'
    b'(-0.046292605 + 1i*0.325539361), (1.622793598 + 1i*0.325206461),...'
    b'(-5.199186089 - 1i*7.450551455), (7.477942354 + 1i*32.20380908),...'
    b'(-0.695291507 - 1i*78.8035274),  (-15.10996796 + 1i*118.5343352),...'
    b'(22.28401942 - 1i*102.4339798),  (-10.89968491 + 1i*39.06207702)];'
    b''
    b'Ctc = [1,                       -0.246740110027234,...'
    b'0.0281855008778942,      -0.00160488313564254,...'
    b'5.40741338140839e-005,\t-1.20009725586003e-006,...'
    b'1.88434991152727e-008,\t-2.20227692544547e-010,...'
    b'1.98968579241802e-012,\t-1.43091897317152e-014,...'
    b'8.38472970511855e-017,\t-4.07998144923387e-019];'
    b''
    b'Cts = [0.523598775598299,       -0.0922805853580352,...'
    b'0.007244784204197,       -0.000312116942354579,...'
    b'8.44427288354525e-006,\t-1.56471445009221e-007,...'
    b'2.10821219332145e-009,\t-2.15743068058434e-011,...'
    b'1.73341020888748e-013,\t-1.12232447879839e-015,...'
    b'5.9800532392104e-018,\t-2.6678713628414e-020];'
    b''
    b''
    b'num = size(lower, 1);'
    b'FRES = ones(num, 1) * (1+1i);'
    b''
    b'for k = 1:num'
    b's = sign(lower(k));'
    b'tmp = s*lower(k);'
    b'if tmp < 1.6'
    b'vec = lower(k) .^ (1:4:(45));'
    b'fresk = sum(Ctc .* vec) + 1i*sum(Cts .* vec * tmp^2);'
    b'else'
    b'vec = (1/tmp) .^ (1:2:23);'
    b'fresk = s * (- sum(Cb .* vec) * exp(1i * pi * tmp^2/2) + 0.5 + 1i * 0.5);'
    b'end'
    b''
    b's = sign(upper(k));'
    b'tmp = s*upper(k);'
    b'if tmp < 1.6'
    b'vec = upper(k) .^ (1:4:(45));'
    b'FRES(k) = sum(Ctc .* vec) + 1i*sum(Cts .* vec * tmp^2) - fresk;'
    b'else'
    b'vec = (1/tmp) .^ (1:2:23);'
    b'FRES(k) = s * (- sum(Cb .* vec) * exp(1i * pi * tmp^2/2)  + 0.5 + 1i * 0.5) - ...'
    b'fresk;'
    b'end'
    b'end'
    b''



```python
# 字符串对齐操作 ljust(), rjust(), center()
text = 'Hello World'
print(text.ljust(20))
print(text.rjust(20))
print(text.center(20))

print(text.rjust(20, '='))
print(text.center(20, '*'))
print(text.ljust(20, '&'))
```

    Hello World         
             Hello World
        Hello World     
    =========Hello World
    ****Hello World*****
    Hello World&&&&&&&&&



```python
#或者下面的表示方法  < , > , ^字符后面紧跟一个指定的宽度

print(format(text, '=>20'))
print(format(text, '-<20'))
print(format(text, '*^20'))
```

    =========Hello World
    Hello World---------
    ****Hello World*****



```python
print('{:<10}{:>10}'.format('Hello', 'World'))
print('{:>10}{:>10}'.format('Hello', 'World'))
```

    Hello          World
         Hello     World



```python
x = 1.23456
print(format(x, '>10'))
print(format(x, '*^10.2f'))
```

       1.23456
    ***1.23***



```python
parts = ['Is', 'Chicago', 'Not', 'Chicago?']
combines1 = ' '.join(parts)
combines2 = '*'.join(parts)
print(combines1, combines2)
```

    Is Chicago Not Chicago? Is*Chicago*Not*Chicago?



```python
a = 'Is Chicago'
b = 'Not Chicago'
print(a  + ' ' + b)
print('{} {}'.format(a, b))
```

    Is Chicago Not Chicago
    Is Chicago Not Chicago



```python
def sample():
    yield 'Is'
    yield 'Chicago'
    yield 'Not'
    yield 'Chicago'
    
def combine(source, maxsize):
    parts = []
    size = 0
    for part in source:
        parts.append(part)
        size += len(part)
        if size > maxsize:
            yield ' '.join(parts)
            parts = []
            size = 0
        yield '*'.join(parts)

with open('./test.py', 'w') as f:
    for part in combine(sample(), 32000):
        f.write(part)
        
```


```python
#解析 HTML或XML实体

s = 'Elements are written as "<tag> text </tag>".'
import html
print(s)

print(html.escape(s))

print(html.escape(s, quote = False))
```

    Elements are written as "<tag> text </tag>".
    Elements are written as &quot;&lt;tag&gt; text &lt;/tag&gt;&quot;.
    Elements are written as "&lt;tag&gt; text &lt;/tag&gt;".



```python
s = 'Spicy &quot;Jalape&#241;o&quot.'
from html.parser import HTMLParser
p = HTMLParser()
p.unescape(s)

t = 'The prompt is &gt;&gt;&gt;'
from xml.sax.saxutils import unescape
unescape(t)
```

    /home/hmin/anaconda3/lib/python3.6/site-packages/ipykernel_launcher.py:4: DeprecationWarning: The unescape method is deprecated and will be removed in 3.5, use html.unescape() instead.
      after removing the cwd from sys.path.





    'The prompt is >>>'




```python
# 构建一个递归下降表达式求值程序：
#！/usr/bin/python3
#-*- encoding: utf-8 -*-

import re
import collections

NUM = r'(?P<NUM>\d+)'
PLUS = r'(?P<PLUS>\+)'
MINUS = r'(?P<MINUS>-)'
TIMES = r'(?P<TIMES>\*)'
DIVIDE = r'(?P<DIVIDE>/)'
LPAREN = r'(?P<LPAREN>\()'
RPAREN = r'(?P<RPAREN>\))'
WS = r'(?P<WS>\s+)'

master_pat = re.compile('|'.join([NUM, PLUS, MINUS, TIMES, DIVIDE, LPAREN, RPAREN, WS]))

Token = collections.namedtuple('Token', ['type', 'value'])

def generate_tokens(text):
    scanner = master_pat.scanner(text)
    for m in iter(scanner.match, None):
        tok = Token(m.lastgroup, m.group())
        if tok.type != 'WS':
            yield tok
            
class ExpressionEvaluator:
    
    def parse(self, text):
        self.tokens = generate_tokens(text)
        self.tok = None
        self.nexttok = None
        self._advance()
        return self.expr()
    
    def _advance(self):
        self.tok, self.nexttok = self.nexttok, next(self.tokens, None)
        
    def _accept(self, toktype):
        
        if self.nexttok and self.nexttok.type == toktype:
            self._advance()
            return True
        else:
            return False
        
    def _expect(self, toktype):
        
        if not self._accept(toktype):
            
            raise SyntaxError('Expected ' + toktype)
    def expr(self):
        exprval = self.term()
        while self._accept('PLUS') or self._accept('MINUS'):
            op = self.tok.type
            right = self.term()
            if op == 'PLUS':
                exprval += right
            elif op == 'MINUS':
                exprval -= right
        return exprval
    
    def term(self):
        
        termval = self.factor()
        while self._accept('TIMES') or self._accept('DIVIDE'):
            op = self.tok.type
            right = self.factor()
            if op == 'TIMES':
                termval *= right
            elif op == 'DIVIDE':
                termval /= right
        return termval
    
    
    def factor(self):
        
        if self._accept('NUM'):
            return int(self.tok.value)
        elif self._accept('LPAREN'):
            exprval = self.expr()
            self._expect('RPAREN')
            return exprval
        else:
            raise SyntaxError('Expected NUMBER or LPAREN')
            
def descent_parser():
        
    e = ExpressionEvaluator()
    print(e.parse('2'))
    print(e.parse('2+3'))
    print(e.parse('2+3*4'))
    print(e.parse('2+(3+4)*5'))
        
        
if __name__ == '__main__':
    descent_parser()
```

    2
    5
    14
    37

