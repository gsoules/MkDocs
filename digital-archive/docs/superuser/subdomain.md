# Subdomain installation

This page discusses installing the Digital Archive in `public_html/digitalarchive` versus installing it in a subdomain.
A subdomain is a domain that is part of a larger domain. For example, `west.example.com` and `east.example.com`
are subdomains of the `example.com` domain. Note that `example.com` is actually a subdomain of the top-level domain `com`.

Subdomains are different from folders. For instance,
`example.com/digitalarchive` points to the `digitalarchive` folder within the `example.com` domain whereas
`digitalarchive.example.com` is a subdomain of `example.com`.

## Two cases
There are two cases to consider when installing the Digital Archive in a subdomain.

1. The subdomain is hosted on the domain's web server
2. The subdomain is hosted on a different web server

### Case 1 - subdomain is hosted on the domain's web server

Examples:
```
    site1.avantlogic.net
    site2.avantlogic.net
```
This case applies when using subdomains for hosting multiple instances of the Digital Archive
on the same web server for development and testing purposes. The following sections point out some
things you should be aware of.

**Database name and user**

When you install the Digital Archive in more than one subdomain on the
same web server, the corresponding databases and user names will all share the same
prefix that cPanel assigns automatically. As such, you'll need to use unique suffixes
to indicate which installation a database belongs to.

For example, on the avantlogic web server where the prefix is `avantlog`, instead of
following the recommendation to name the database `avantlog_omeka`, choose database
names like `avantlog_site1` and `avantlog_site2`.

Similarly, for the database user name, instead of following the recommendation to name
the user `avantlog_archivist`, choose user names that match the database names such as 
 `avantlog_site1` and `avantlog_site2`.

**FTP**

You don't need to set up separate FTP connections for each subdomain.
You access a subdomain's files via the domain's FTP connection. If for some reason
you need a separate FTP connection for a subdomain, the connection cannot use the SSH protocol,
but must instead use the FTP protocol. For related documentation on this see
[Filezilla FTP settings](../../administrator/zoomable-images/#filezilla-ftp-settings) for uploading zoomable images.

---

### Case 2 - subdomain is hosted on a different web server

Example:
```
    digitalarchive.somecollege.edu
```

In the example, the Digital Archive files are installed in the `public_html` folder on a web server
that is different from the `somecollege.edu` web server. On that different web server, the files are
installed in `public_html` instead of in a `digitalarchive` folder because if they were, the URL
would need to be `digitalarchive.somecollege.edu/digitalarchive` which is redundant.

To make this work, that is, for the subdomain ending in `edu` to resolve to another server,
the `somecollege.edu` web administrator must point an `A record` or CNAME for the subdomain to the
web server that hosts the subdomain. (CNAME is recommended as future-proof against server migrations).

With this arrangement, you can perform the tasks to [install a Digital Archive site](install-digital-archive.md)
with only one modification: Instead of installing into the `digitalarchive` folder, install into the
`public_html` folder.

Because you will be installing into the `public_html` folder, the code to force HTTPS for all pages
needs to go into the `.htaccess` file that ships with Omeka in its top-level folder. Add the
code below near the top of the file after `RewriteEngine on`. Don't add code for redirecting root access.

```
    # Force all URLs to HTTPS
    RewriteCond %{HTTPS} off
    RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} [R,L]
```
