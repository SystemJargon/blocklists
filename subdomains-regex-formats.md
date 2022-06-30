One of the common user errors of sorts I guess is that, an adlist / blocklist / allowlist is assumed upon, that it will block subdomains if not specifying a subdomain.

Some people wish they would be and sometimes they don't. For nasty domains sure. For API, not to break sites and then having to allowlist exempt something later too.

Why? Because it (insert your blocker solution here) doesn't parse regex unless you tell it to OOB. Which makes sense. 

Comparison example:

block ads.google.com but not www.google.com

makes sense it wouldn't just block google.com, I agree.
if you type into blocking googleapis.com it will block that domain (if no regex is used), but NOT it's subdomains.

So an adlist/blocklist etc. which has this in plain text format (example below), one domain per line (plain text). 
Usually saved as .list .txt extension.

Using googleapis.com as the example again.

```
example.com
googleapis.com
test.googleapis.com
```

A list with just ```googleapis.com``` as mentioned, is NOT inclusive of subdomains. 

### pi-hole example

once you enter a domain and select/tick the wildcard box (subdomains are included) it ends up looking like this.

(\.|^)googleapis\.com$ # googleapis.com and it's subdomains.

### adguardhome / some easylist format example

this looks more like this (if blocking it)

||googleapis.com^ # googleapis.com and it's subdomains.

whitelisting example being: @@||googleapis.com^ 

----

When building lists/aggregating them, lists become BIG. Sometimes false positives occur too, not solely because of this though.

Why lists grow bigger sometimes is because they have examples like below in them.

```
ads.googleapis.com
cse.googleapis.com
somethingsomething.googleapis.com
www.googleapis.com
googleapis.com
```

The power of using regex lists, provides more granual control to block any subdomains upon specifying the root domain.

Then if you need to allow a specific subdomain, you then add just that subdomain to the allowlist. 

Where this comes to light more, is when big tech have thousands and thousands of subdomains. This doesn't even include the cname and dns aliases or different domains for CDN.

adblocker type solutions are not 100% proof to block, but do a decent job.

A real example of this breaking a site sort of but allowing the basic webpages to load, is across GAFAM (big tech) i.e. facebook.