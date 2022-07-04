---
title: python
date: 2021-12-09 22:19:45
tags:
 - Python
---

Created: 2021-05-28 08:32:57

Modified: 2021-12-09 22:19:45

<!--more-->

refer to https://python3-cookbook.readthedocs.io/zh_CN/latest/index.html, https://www.runoob.com/python/python-tutorial.html, http://www.pythondoc.com/pythontutorial3/appetite.html

# python and pip

```shell
# windows
where python
# linux
whereis python
# pip
python3 -m pip list
pip3 list
pip show <module>
```

# special file

- `__init__.py`: claim the package of python and collect class and function

- `__main__.py`: 

  ```bash
  # __main__.py in package
  python __main__.py ...
  # => 
  python -m package_name ...
  # => (after installation)
  package_name ...
  ```

# basic operation

```python
b = a
a is b
# True
#c = a.copy()
#c is a
## False
```

# math operation

```python
a = 3.75
int(a)
round(a)
import math
math.floor(a)
math.ceil(a)

```

# advanced operation

```python
# retun

# pass

# raise

# assert

# try
try:
    main-action
except Exception1:
    handler1
except Exception2:
    handler2
...
else: # no exception
    else-block
finally: # exception
    finally-block 
```

# lambda and function

```python
def sum(x,y):
# or def sum(x:int=1,y:int=2) -> int:
      return x+y
p = lambda x,y:x+y
sum(1,2)==p(1,2)
# True
```

# map

```python
a = [2] * 9
list(map(str, a))
# ['2', '2', '2', '2', '2', '2', '2', '2', '2']
list(map(lambda x:x**2, a))
# [4, 4, 4, 4, 4, 4, 4, 4, 4]
```

# iterator

refer to https://www.runoob.com/python3/python3-iterator-generator.html

```python
class MyNumbers:
  def __iter__(self):
    self.a = 1
    return self
  def __next__(self):
    self.a += 1
    if self.a >= 10:
      raise StopIteration
    return self.a
# usage 1
for x in myclass:
# or for x in iter(myclass):
    print(x)
    if x > 5:
        break
# usage 2
myiter = iter(myclass)
next(myiter)
```

# str

## join  split  format  ast.literal_eval

```python
# a <class 'str'> or list(<class 'str'>) or tuple(<class 'str'>)
a = 'gdfgdf'
a = ['gdfgdf','hfgdhjfj']
','.join(a)
# 'g,d,f,g,d,f'
# 'gdfgdf,hfgdhjfj'

# b <class 'str'>
b = 'g,d,f,g,d,f'
b = 'gdfgdf,hfgdhjfj'
b.split(',')
# ['g', 'd', 'f', 'g', 'd', 'f']
# ['gdfgdf', 'hfgdhjfj']

'***{}***{}***'.format(a,b)
# "***['gdfgdf', 'hfgdhjfj']***gdfgdf,hfgdhjfj***"

# c str(<class 'list'>) or str(<class 'tuple'>) or ...
c = "['gdfgdf', 'hfgdhjfj']"
import ast
ast.literal_eval(c)
# ['gdfgdf', 'hfgdhjfj']
```

## text justification

```python
'''
原字符串左侧对齐， 右侧补零:
'''
str.ljust(width,'0') 
input: '789'.ljust(32,'0')
output: '78900000000000000000000000000000'


'''
原字符串右侧对齐， 左侧补零:
方法一：
'''
str.rjust(width,'0') 
input: '798'.rjust(32,'0')
output: '00000000000000000000000000000798'
'''
方法二：
'''
str.zfill(width)
input: '123'.zfill(32)
output:'00000000000000000000000000000123'
'''
方法三：
'''
'%07d' % n
input: '%032d' % 89
output:'00000000000000000000000000000089'
# refer to: https://blog.csdn.net/weixin_42317507/article/details/93411132
```

# list

```python
vowels = ['e', 'a', 'u', 'o', 'i']
vowels.sort(reverse=True) # no return, just sort 'vowels'
```



# dict

refer to https://www.runoob.com/python/python-dictionary.html

# collections

## Counter

```python
from collections import Counter

    data_col_dict = Counter(data_col)
    data_col_tuple_sort_list = data_col_dict.most_common()
    
    for item in data_col_dict.items():

```



## OrderedDict

class OrderedDict(dict)

'''dict with order'''

## namedtuple

to defien a customed tuple-like type

# numpy

refer to https://juejin.cn/post/6844903827473219597, https://blog.csdn.net/weixin_38283159/article/details/78793277, https://www.cnblogs.com/mzct123/p/8659193.html, 

```python
import numpy as np
a=np.arange(12)
# a <- array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])
# shape: (12,)
a.resize(2,3,2)
# or a.shape=(2,3,2)
# a <- array([[[ 0,  1],
#         [ 2,  3],
#         [ 4,  5]],

#        [[ 6,  7],
#         [ 8,  9],
#         [10, 11]]])
a.reshape(3,4)
# array([[ 0,  1,  2,  3],
#        [ 4,  5,  6,  7],
#        [ 8,  9, 10, 11]])
a.dtype, a.shape, a.size, a.ndim
# (dtype('int64'), (2, 3, 2), 12, 3)
b = a
c = a.copy()
d = a.ravel()
e = a.flatten()
# d,e <- array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])
a[0] = 666
# or b[0] = 666
# a,b <- array([[[666, 666],
#         [666, 666],
#         [666, 666]],

#        [[  6,   7],
#         [  8,   9],
#         [ 10,  11]]])
# d <- array([666, 666, 666, 666, 666, 666,   6,   7,   8,   9,  10,  11])
d[0]=555
# a,b <- array([[[555, 666],
#         [666, 666],
#         [666, 666]],

#        [[  6,   7],
#         [  8,   9],
#         [ 10,  11]]])
# d <- array([555, 666, 666, 666, 666, 666,   6,   7,   8,   9,  10,  11])
a[...,np.newaxis,:]
# or np.expand_dims(a, axis=2)
# array([[[[555, 666]],

#         [[666, 666]],

#         [[666, 666]]],


#        [[[  6,   7]],

#         [[  8,   9]],

#         [[ 10,  11]]]])
# shape:(2, 3, 1, 2)
f = a[...,np.newaxis,:]
f.transpose(3,2,1,0)
# f.transpose()
# array([[[[555,   6],
#          [666,   8],
#          [666,  10]]],


#        [[[666,   7],
#          [666,   9],
#          [666,  11]]]])
# shape:(2, 1, 3, 2)
np.squeeze(f)
# array([[[555, 666],
#         [666, 666],
#         [666, 666]],

#        [[  6,   7],
#         [  8,   9],
#         [ 10,  11]]])
# shape:(2, 3, 2)

np.argwhere(f<100)
# array([[1, 0, 0, 0],
#        [1, 0, 0, 1],
#        [1, 1, 0, 0],
#        [1, 1, 0, 1],
#        [1, 2, 0, 0],
#        [1, 2, 0, 1]])
```

Note: the dtype of np.str_ includes the limitation of length of the str.

# string

```python
import string

```

# matplotlib

## pyplot

refer to https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.html.

### plot

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.arange(0, 5, 0.1)
y = np.sin(x)
plt.plot(x, y)
# color https://blog.csdn.net/CD_Don/article/details/88070453
```

### pause

```python
import matplotlib.pyplot as plt
import numpy as np

np.random.seed(19680801)
data = np.random.random((50, 50, 50))

fig, ax = plt.subplots()

for i in range(len(data)):
    ax.cla()
    ax.imshow(data[i])
    ax.set_title("frame {}".format(i))
    plt.pause(0.1)
# refer to: https://blog.csdn.net/mighty13/article/details/116671083
```

## animation

refer to https://matplotlib.org/stable/api/animation_api.html

```python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib.animation import FuncAnimation

fig, ax = plt.subplots()
xdata, ydata = [], []
ln, = plt.plot([], [], 'ro')

def init():
    ax.set_xlim(0, 2*np.pi)
    ax.set_ylim(-1, 1)
    return ln,

def update(frame):
    xdata.append(frame)
    ydata.append(np.sin(frame))
    ln.set_data(xdata, ydata)
    return ln,

ani = FuncAnimation(fig, update, frames=np.linspace(0, 2*np.pi, 128),
                    init_func=init, blit=True)
plt.show()
# ani.save('contrast.mp4', fps=15,
#                  extra_args=['-vcodec', 'libx264'],
#                  writer='ffmpeg_file')
# ani.save('contrast.gif', writer='imagemagick', fps=30)
# refer to: https://matplotlib.org/stable/api/animation_api.html#funcanimation,
```

related to: https://www.bbsmax.com/A/gGdXbVvmJ4/

*trouble: why it becomes slower and slower when it handles many photos?  The following pipeline has the same trouble (the two pipeline both use `canvas`):

```python	
# animation
import matplotlib.pyplot as plt
import numpy as np

x = np.linspace(0, 6*np.pi, 100)
y = np.sin(x)

# You probably won't need this if you're embedding things in a tkinter plot...
plt.ion()

fig = plt.figure()
ax = fig.add_subplot(111)
line1, = ax.plot(x, y, 'r-') # Returns a tuple of line objects, thus the comma

for phase in np.linspace(0, 10*np.pi, 500):
    line1.set_ydata(np.sin(x + phase))
    fig.canvas.draw()
    fig.canvas.flush_events()
# refer to: https://stackoverflow.com/questions/4098131/how-to-update-a-plot-in-matplotlib
```

# sys

```python
sys.path.append(path)
```



# os

handle directory

```python
import os
filePath = 'C:\\myLearning\\pythonLearning201712\\carComments\\01\\'
os.listdir(filePath)

# 查看当前工作目录
os.getcwd()
# 修改当前工作目录
os.chdir( path )
# frequent use along
os.mkdir(path)

# refer to https://blog.csdn.net/happyjacob/article/details/109279118
os.environ
from environs import Env
env = Env()
SIM = env.str('SIM', 'fsdfds')
```



## path

```python
import os, sys
path = __file__
# path <- file full path <class 'str'>
os.path.basename(path)
# file name
os.path.dirname(path)
# directory path
os.path.split(path)
# [directory path, file name]
os.path.splitext(path)
# [file path, extension name]

os.path.join(basepath, relpath, ...)
os.path.relpath(path[, basepath])

os.path.exists(path)
os.path.isfile(path)
os.path.isdir(path)

os.path.getsize(path)
```



## walk

```python
# walk
import os
path = r'./'
ext = '.py'
roots_dict = {}
for root, dirs, files in os.walk(path):
    '''
    root is a string, the path to the directory, consistent with 'path'.
    dirs is a list of the names of the subdirectories in root (excluding '.' and '..').
    files is a list of the names of the non-directory files in root.
        Note that the names in the lists are just names, with no path components.
        To get a full path (which begins with top) to a file or directory in root,
        do os.path.join(root, name).
    '''
    print('there are {} dir(s) and {} file(s) in the root of {}'.format( \
        len(dirs), len(files), root))
    roots_dict[root] = dirs + files

    files_filter = []
    if ext != None:
        for file in files:
            if os.path.splitext(file)[-1] in ext:
                files_filter.append(file)
    else:
        files_filter.extend(files)
    print('len(files_filter)', ': ', len(files_filter))
    if len(files_filter) == 0:
        print()
        continue

    # insert operation to process files_filter
    print()
print(roots_dict)
```

# pathlib

## Path

powerful tool for manage `path`, refer to https://docs.python.org/zh-cn/3/library/pathlib.html

```python
from pathlib import Path

# refer to: https://docs.python.org/zh-cn/3/library/pathlib.html
```



# functools

## partial

```python
from functools import partial
def Func(a, b = None):
    print(a, b)
    pass
worker = partial(Func, b=1)
worker(a='test')
# test 1
```



# multiprocessing

refer to https://docs.python.org/zh-cn/3/library/multiprocessing.html.

```python
# Create a new process

from multiprocessing import Process, Manager, freeze_support, set_start_method

import time # optional

# create a new preocess using method 1:
class MyNewProcess(Process):
    def __init__(self, mdic):
        self.mdic = mdic
        super().__init__()
    def run(self):
        time_start = time.time()
        while (time.time() - time_start < 15):
            self.mdic["action"] += 2
            print("subprocess1 action = ", self.mdic["action"])
            time.sleep(1.6) # run 2/1=2 times per main while
        print("subprocess1 over!")

        print("subprocess1 stop!")

# create a new preocess using method 2:
def subprocess2(mdic):
    time_start = time.time()
    while (time.time() - time_start < 11):
        mdic["action"] += 1
        print("subprocess2 action = ", mdic["action"])
        time.sleep(0.5) # run 2/0.5=4 times per main while
    print("subprocess2 over!")

    print("subprocess2 stop!")

# main perocess where two precesses are created
def main():
    # create global dict among processes
    manager = Manager() # must set after '__main__'
    mdic = manager.dict()
    mdic["action"] = 0

    p = MyNewProcess(mdic, )
    p.start() # to call p.run()
    
    p1 = Process(target=subprocess2, args=(mdic, )) 
    p1.start()

    time_start = time.time()
    while (time.time() - time_start < 7):
        mdic["action"] = 0
        print("main action = ", mdic["action"])
        time.sleep(2)
    print("main process over!")

    p.join()
    p1.join()
    print("main process stop!!!")

if __name__ == '__main__':
    # freeze_support()
    # set_start_method('spawn')
    main()

# ————————————————
# refer to：https://docs.python.org/zh-cn/3/library/multiprocessing.html, 
# https://blog.csdn.net/qq_32460819/article/details/119257062, 
# https://blog.csdn.net/u012193416/article/details/78396814,
```

related to: https://www.cnblogs.com/chentianwei/p/11914268.html, 

## Pool

no special type

related to: https://blog.csdn.net/u012193416/article/details/78396814

# signal

refer to https://docs.python.org/3/library/signal.html

```python
import signal, os

def handler(signum, frame):
    print('Signal handler called with signal', signum)
    raise OSError("Couldn't open device!")

# Set the signal handler and a 5-second alarm
signal.signal(signal.SIGALRM, handler)
signal.alarm(5)

# This open() may hang indefinitely
fd = os.open('/dev/ttyS0', os.O_RDWR)

signal.alarm(0)          # Disable the alarm
# sample from: https://docs.python.org/3/library/signal.html#example
```



# txt

```python
import sys
import codecs

if (sys.version_info >= (3, 5)):
    fd = open(filename, 'r')
    f = fd
elif (sys.version_info >= 2.7):
	fd = codecs.open(filename, 'r')
	f = fd
    
line = f.readline()
splitline = line.strip().split(' ')
# or
lines = f.readlines()
splitlines = [x.strip().split(' ') for x in lines]
```

# image

```python
import Image
import numpy as np
Image.open(object.logo.path).convert('RGB').save('/tmp/output.png')

```



# xls

handle .xls

```python
import xlwt
workbook = xlwt.Workbook(encoding = 'utf-8')
worksheet = workbook.add_sheet('Worksheet'+str(0))
worksheet.write(0, 0, 'Num')#row, col, *args
worksheet.write(0, 1, 'unicode')
worksheet.write(0, 2, 'char')
worksheet.write(0, 3, 'char_wide')
worksheet.write(0, 4, 'char_hash')
workbook.save('Excel_test'+str(0)+'.xls')

import xlrd
exce = xlrd.open_workbook('Excel_test.xls')
sheet1 = exce.sheet_by_name('Worksheet1')
nrows = sheet1.nrows

unicod = sheet1.col_values(1)
char_wide = sheet1.col_values(3)
char_hash = sheet1.col_values(4)
```

# html

refer to https://blog.csdn.net/sinat_26917383/article/details/78204653

```python
```



# pywinauto

control mouse and keys

# PyQt

related to: https://blog.csdn.net/toby54king/article/details/105187934

# static variables

refer to https://www.jianshu.com/p/3ed1037b7c18, 

```python
def static_vars(**kwargs):
    def decorate(func):
        for k in kwargs:
            setattr(func, k, kwargs[k])
        return func
    return decorate
@static_vars(counter = 0)
def foo():
    foo.counter += 1
```

