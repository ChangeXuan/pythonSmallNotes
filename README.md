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
