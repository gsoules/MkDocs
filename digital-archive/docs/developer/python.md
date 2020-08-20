# Python

---

To see the Python path

``` text
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

### yum

`yum install <package name>` or `sudo yum install <package name>`

See <https://access.redhat.com/articles/yum-cheat-sheet>

If that doesn't work because the package is not found then

``` text
[root@avantlogic ~]# pip3 install utm
WARNING: Running pip install with root privileges is generally not a good idea. Try `pip3 install --user` instead.
Collecting utm
  Downloading https://files.pythonhosted.org/packages/b6/77/180f06153f2c1a8caf8409ff6365abc9423ec4ebc3991dfe4a3228bc09d4/utm-0.5.0.tar.gz
Installing collected packages: utm
  Running setup.py install for utm ... done
Successfully installed utm-0.5.0
```

### MySQL Connector Python

<https://dev.mysql.com/doc/connector-python/en/connector-python-introduction.html>

---