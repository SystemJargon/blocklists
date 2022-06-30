One of the common user errors of sorts I guess is an adlist / blocklist / allowlist is not inclusive of subdomains sometimes.

Some people wish they and sometimes they don't. For nasty domains sure. For API, not to break sites and then having to allowlist exempt something later too.

Why? Because it (insert your blocker solution here) doesn't parse regex unless you tell it to OOB. Which makes sense. 

Comparison example:

block ads.google.com but not www.google.com

So an adlist/blocklist etc. which has this in plain text format (example below), one domain per line (plain text). 
Usually saved as .list .txt extension.

Using googleapis.com as the example.

```
example.com
googleapis.com
```

A list with just ```googleapis.com``` as mentioned, is NOT inclusive of subdomains.

### pi-hole example

once you enter a domain and wildcard (for say the subdomains included) it ends up looking like this.

(\.|^)googleapis\.com$ # googleapis.com and it's subdomains.

### adguardhome / some easylist format example

this looks more like this (if blocking it)

||googleapis.com^ # googleapis.com and it's subdomains.

whitelisting example being: @@||googleapis.com^ 

----

Further note, this is sometimes why some basic lists grow BIG. Because they have examples like below in them.


ads.googleapis.com
cse.googleapis.com
somethingsomething.googleapis.com
www.googleapis.com
googleapis.com

The power of using regex lists, provides more granual control to block subdomains, and if you need to allow a specific subdomain, so be it.
