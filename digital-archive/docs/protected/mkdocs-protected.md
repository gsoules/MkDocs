# Protected information

---
[Return to the public MkDocs page](../../super-mkdocs)

## MkDocs password protection

Some Digital Archive documentation pages, like this one, are password protected.
You protect a page by putting its Markdown `.md` file in the `docs/protected` folder.
When a user clicks on a link to a protected page, they will be prompted to enter a user name and password.

Password protection is made possible using two files:

- `.htaccess`
- `.htpasswd`

To access these files on the Rockaway Hosting server:

- Login here: <https://members.rockawayhosting.com/clientarea.php>
- Under `Your Active Products/Services` click `Shared Hosting`
- In the `Quick Shortcuts` sections click `File Manager`

### .htaccess
The `docs/protected` folder contains an `.htaccess` file. The contents of the file are shown below.
```
AuthType Basic
AuthName "Password Protected Area"
AuthUserFile /home/avantlog/digitalarchive.avantlogic.net/.htpasswd
Require valid-user
```

You probably won't need to modify the file, but if you do:

- Navigate to `digitalarchive.avantlogic.net/docs/protected`
- Edit `.htaccess`

### .htpasswd

Passwords are stored in the `.htpasswd` file which must in a location that is not publicly accessible. There is only one `.htpasswd` whereas there could be multiple `.htaccess` files if more than one folder needed protection.

To modify the `.htpasswd` file:

- Navigate to `digitalarchive.avantlogic.net`
- Edit `.htpasswd` to add, remove, or update a line

Each line in the file contains a user name and password combination as shown below.

```
admin:$apr1$901f42pd$i2Ht1QMQMqhiiYKtOCUum/
```

The password portion is not the user's actual password, but rather an encrypted version of their password.
To generate an encrypted password, use [HTPasswd Generator](https://www.web2generators.com/apache-tools/htpasswd-generator).
For example, to add a new user `jdoe`, generate an encrypted password for them and then add the
user/password combination to `.htpasswd`.

!!! note ""
    Learn more about [password protection with htaccess](https://www.htaccesstools.com/articles/password-protection/).

[Return to the public MkDocs page](../../super-mkdocs)
