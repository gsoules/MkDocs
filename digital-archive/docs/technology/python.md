# Python

---

## Install a Python module for all accounts

- Open a WHM Terminal window
- Use pip3. For example, to install the `requests` module, type:  
  `pip3 install requests`

To see a list of installed modules type:
`pip3 list --format=columns`

``` text
[daus@vps89189 bin]$ pip3 list --format=columns
Package            Version
------------------ ---------
certifi            2022.12.7
charset-normalizer 2.0.12
dbus-python        1.2.4
decorator          4.2.1
dnspython          1.15.0
gpg                1.13.1
idna               3.4
iotop              0.6
isc                2.0
libcomps           0.1.18
nftables           0.1
pcp                5.0
pip                9.0.3
ply                3.9
pygobject          3.28.3
pyparsing          2.1.10
python-dateutil    2.6.1
requests           2.27.1
rpm                4.14.3
selinux            2.9
setuptools         39.2.0
six                1.11.0
slip               0.6.4
slip.dbus          0.6.4
urllib3            1.26.14
```

To install a module for only one account, open the Terminal window from that account's cPanel.

## Python path

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

## Run a Python program from a Command or Bash window

Specify the `-u` option so that console output goes immediately to the window without getting buffered.
Without the option, you won't see any output until the program completes.

```
python -u <filename>.py
```    

## yum

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

## MySQL Connector Python documentation

<https://dev.mysql.com/doc/connector-python/en/connector-python-introduction.html>

---