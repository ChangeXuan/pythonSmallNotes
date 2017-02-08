# pythonSmallNotes
## 这里有一些我用到的整合小知识

- sublime中的python使用中文
```python
# -*- coding: utf-8 -*-
```

- 复制整个文件夹目录
```python
import shutil

#copytree函数中的targetDir不能是存在的路径
shutil.copytree(sourceDir,targetDir)
```

- 取得当前目录
```python
import os
import os.path

nowPath = os.path.abspath('.')
```

- 取得当前时间
```python
import time

time = time.strftime("%Y-%m-%d-%H-%M-%S")
```

- 字符串描述路径
```python
import time

path = "F:/this"
```

- 取得当前所有盘符
```python
import time

time = time.strftime("%Y-%m-%d-%H-%M-%S")
```


- 字符串描述路径
```python
import ctypes

newBuffer = ctypes.create_string_buffer(78)
ctypes.windll.kernel32.GetLogicalDriveStringsA(ctypes.sizeof(newBuffer),newBuffer)
allBuffer = newBuffer.raw.split('\x00')
pathStr = ""
for i in allBuffer:
  pathStr += i
print pathStr
```

- 取得当前所有盘符
```python
import urllib2

#返回url的源代码
def getSource(url):
  header={'User-Agent' : 'Mozilla/5.0 (Windows NT 6.1; WOW64; rv:14.0) Gecko/20100101 Firefox/14.0.1','Referer' : '******'}
  request = urllib2.Request(url,headers = header)
  response = urllib2.urlopen(request)
  return response.read()
```


- 使用正则匹配html标签
```python
import re

#取得链接地址
def getLinkUrl(source):
  linkUrl = re.findall('<td><a href="(.*?)">',source,re.S)
  return linkUrl
```


- 在当前目录下创建txt并写入数据
```python
#在当前目录下打开name.txt，如果文件不存在，则创建，“w+”表示允许写入
f = open("name.txt","w+")
#写入数据，每行
f.writelines("this is add data")
f.close
```

- 程序休眠
```python
import time
#程序停止运行1s
time.sleep(1000)
```

- json数据post请求服务器
```python
import urllib2
import json

url = "http://192.168.0.1"
postContent = {'regist': 'pythonJson'}
headers = {'Content-Type': 'application/json'}

req = urllib2.Request(url,json.dumps(postContent),headers)
data = urllib2.urlopen(req)
```


- 解析json数据
```python
import json

#构建一个json数据结构
jsonData = json.loads('{"name":"test","type":{"name":"hello","par":["1","2"]}}')

print jsonData.keys() #取得json数据中的所有的key,返回一个数组
print jsonData["name"]
print jsonData["type"]["name"]
print jsonData["type"]["par"][0]
```

- 从零开始的for循环
```python

for i in xrange(8):
  print i     #0,1,2,3,4,5,6,7
```


- 判断某个路径是否存在
```python
import os

if os.path.exists(r'd:/hello/'):
  print "yes"
else:
  print "no"
```

- 打开当前路径的一张图片(opencv)
```python
import cv2

image = cv2.imread("youImg.jpg")
cv2.imshow("hello",image)#"hello为标题"
cv2.waitkey(0);
```

- 读取txt文件内容，忽略换行
```python

dataStr = ""
for line in open('youTxt.txt','r'):
  dataStr += line.strip()
```


- 取得当前活动的窗体名
```python
import win32gui

titles = []
def func(hwnd,mouse):
  if win32gui.IsWindow(hwnd) and win32gui.IsWindowEnabled(hwnd) and win32gui.IsWindowVisible(hwnd):
		titles.append(win32gui.GetWindowText(hwnd))

win32gui.EnumWindows(func,0)
print titles
```


- 获取剪切板文本
```python
import win32con
import win32clipboard as w

def getBoardStr():
    w.OpenClipboard()
    str = w.GetClipboardData(win32con.CF_UNICODETEXT)
    w.CloseClipboard()
    return str

print getBoardStr()
```

- 设置剪切板文本
```python
import win32con
import win32clipboard as w

def setBoardStr(copyStr):
  w.OpenClipboard()
  w.EmptyClipboard()
  w.SetClipboardData(win32con.CF_UNICODETEXT, copyStr)
  w.CloseClipboard()
  
setBoardStr("hello".decode('gb2312'))
#setBoardStr("你好".decode('utf-8'))
#万恶的编码问题，所以用python3保平安
```

- 下载远程数据
```python
import urlllib
import os

def getBoardStr(url,path):
  urllib.urlretrieve(url,path)
  
url = "http://www.imageUrl.com"
path = os.path.abspath(".")
getBoardStr(url,path)
```


