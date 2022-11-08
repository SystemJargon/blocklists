
## Convert a HOSTS list to EasyList/AdGuard format

Debian CLI: ```sed 's/^/||/' pihole-format.txt > easylist-format.txt```

In a text editor GUI try this:

(usually Ctrl+H on Windows for 'replace')
find string/what: ```^```
replace string/what: ```\1\||``` or ```||```
Enable Regular Expression, Tick Matches newline. Click Replace All

and/or, Find ```$``` and replace with ```^$important``` - this will add ^$important to the end of each line

----

## Examples of regex and wildcards with domains and URLs

MATCH REGEX (Pi-hole)

* any subdomain of example.com ```(\.|^)example\.com$```
* any subdomain of example.net  ```(\.|^)example\.net$```
* ads as subdomain but not known TLD ```(\.|^)ads\.$```
* xxx as top-level-domain but not known subdomain nor domain ```(\.|^)\.xxx$```

Then you could try something like this, for keyword multi-string in the domain name.

```
(\.)(adult|ads|adverts|advertising|click|porn|sex|telemetry|tracking|tracing)$
```

More about this in my Pi-hole repo with regex [here](https://github.com/SystemJargon/pi-hole/regex)

----

## Strip sub-domains to root domain (Find)

Example Notepad++

Use this as the FIND context and use REPLACE with blank.

```
^[^.]*\.(?=\w+\.\w+$)
```

Explained:

    ^ = start of line
    [^.]* = any number of chars that are not a dot
    \. = a dot
    (?=[^.]+\.[^.]+$) = there must be exactly one word, one dot then one word from here to the end



----


## Strip port numbers at end of URL

Regular Expression string:

```
:[\d]+$
```

----

## Strip down full URL to domain name

https://www.google.com/api?=login/someshit/0931750135145/

to be just

www.google.com

Usage could be for a sysadmin or someone to get just the domain name / subdomain needed for a task/action in role.

```
^http:..|^https:..|\/.*
```

Regex validated [here](https://regex101.com/r/7NVd2e/4)

Of course you could replace the text to be something else instead of url and domain strings (you get the picture I hope).


