webscraping
===========

github convenience fork of http://code.google.com/p/webscraping/


Overview
========

The webscraping library aims to make web scraping easier.

All code is pure Python and has been run across multiple Linux servers, Windows machines, as well as Google App Engine.

Examples
========

common
------

<pre>
>>> from webscraping import common
>>> common.remove_tags('hello <b>world</b>!')
'hello world!'

>>> common.extract_domain('http://www.google.com.au/tos.html')
'google.com.au'

>>> common.unescape('&lt;hello&nbsp;&amp;&nbsp;world&gt;')
'<hello & world>'

>>> common.extract_emails('hello richard AT sitescraper DOT net world')
['richard@sitescraper.net']

>>> cj = common.firefox_cookie()
>>> opener = urllib2.build_opener(urllib2.HTTPCookieProcessor(cj))
>>> html = opener.open(url).read() # use current firefox cookies to access url
</pre>


download
--------

<pre>
>>> from webscraping import download
>>> D = download.Download()

>>> # crawl given domain
>>> domain = ...
>>> for url in D.crawl(domain):
>>>    html = D.cache[url]
</pre>


pdict
-----

<pre>
>>> from webscraping import pdict 
>>> cache = pdict.PersistentDict(CACHE_FILE)
>>> cache['a'] = range(5) # pickle stored in sqlite database
>>> 'a' in cache
True
>>> cache['a']
[0, 1, 2, 3, 4]
(see a further example here)
</pre>

xpath
-----

<pre>
>>> from webscraping import xpath
>>> html = urllib2.urlopen(url).read()
>>> xpath.parse(html, '/html/body/ul[2]/li[@class="info"]/div[1]')
['div content']
>>> xpath.parse(html, '/html/body/ul[2]/li[@class="info"]/a/@href')
['url1', 'url2', 'url3']
</pre>

Install
=======

Some options to install the webscraping package.

Clone the repository: hg clone https://code.google.com/p/webscraping/

Install with pip: sudo pip install -e hg+https://code.google.com/p/webscraping/#egg=webscraping

Download zip: http://webscraping.googlecode.com/files/webscraping.zip

License
=======

This code is licensed under the LGPL license.