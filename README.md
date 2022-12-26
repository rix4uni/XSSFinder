# XSSFinder
 
# XSSFinder

A Light Weight Tool for checking Cross Site Scripting (XSS) vulnerabilities by replacing xss payloads in the parameters values and checking 'confirm(1),prompt(1),alert(1)' in the response.

## Installation
```
git clone https://github.com/rix4uni/XSSFinder.git
cd XSSFinder
#pip3 install -r requirements.txt
```

## Example usages

Note: must use `uro`

Single URL:
```
echo "http://testphp.vulnweb.com/showimage.php?file=./pictures/1.jpg" | python3 xssfinder.py
```

Multiple URLs:
```
cat xss-urls.txt | python3 xssfinder.py
```

## Chaining With Other Tools
```
echo "http://testphp.vulnweb.com" | waybackurls | gf xss | uro | anew | python3 xssfinder.py --threads 50
echo "http://testphp.vulnweb.com" | waybackurls | gf xss | uro | anew xss-urls.txt # use this output in Multiple URLs
```
## To get best results
```
open xss_payloads.txt add your favraioute payloads
```

## How It Works
```
For Example Url is:- 
http://testphp.vulnweb.com/showimage.php?file=first&cat=second

It will check all xsspayloads one by one:-
NOT VULNERABLE: http://testphp.vulnweb.com/showimage.php?file=<img src=x onerror=confirm(1)>&cat=<img src=x onerror=confirm(1)>
VULNERABLE: http://testphp.vulnweb.com/showimage.php?file="><img src=x onerror=confirm(1)>&cat="><img src=x onerror=confirm(1)>
NOT VULNERABLE: http://testphp.vulnweb.com/showimage.php?file="><svg/onload=confirm(1)>&cat="><svg/onload=confirm(1)>
```
