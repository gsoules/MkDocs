# Python

---

To see the Python path

```
>>> import sys
>>> print(sys.path)
['', '/usr/lib/python2.7/site-packages/pyzor-1.0.0-py2.7.egg',
'/usr/lib64/python27.zip', '/usr/lib64/python2.7', '/usr/lib64/python2.7/plat-linux2',
'/usr/lib64/python2.7/lib-tk', '/usr/lib64/python2.7/lib-old',
'/usr/lib64/python2.7/lib-dynload', '/usr/lib64/python2.7/site-packages',
'/usr/lib/python2.7/site-packages']

```

### Create .exe with pyinstaller

-   Go to `Python\PastPerfect\pp_export\`
-   Right click and choose `Git Bash Here`
-   Type `pyinstaller --onefile pp_export.py`
-   pyinstaller will create  `Python\PastPerfect\pp_export\dist\pp_export.exe`

### Run a Python program from a Command or Bash window

Specify the `-u` option so that console output goes immediately to the window without getting buffered.
Without the option, you won't see any output until the program completes.

```
python -u <filename>.py
```    
