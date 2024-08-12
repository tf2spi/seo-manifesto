# SEO Manifesto

A comprehensive resource on search engines, their query parameters,
and how to use them to narrow down results or achieve SEO goals.

This is generally advertised as being useful for advertisers,
but it is also generally useful for researchers who really need
to narrow search results quickly and specifically. Even sites with search
queries don't provide as advanced of query languages as many modern search
engines do.

It is also useful for web programmers in general who either deal
with search engines and web scraping directly or need to understand
the language of APIs/frameworks that do this work for them so that
they can make their software much more efficient.

It would also be useful for meta-search engine programmers to expose
query parameters in a cross-engine way. I've, surprisingly, not seen any meta-search
engine do this yet. It would be really cool if some of them already did
this. If not, it would also be a cool future project!

# General Resources

* [SEOsly](https://seosly.com/)
* [Google Developer's Search Docs](https://developers.google.com/search/docs)

# Google

## Endpoints

Google's main endpoint for its search engine is [https://google.com/search](https://google.com/search)

Google also has several advanced search pages which utilize different search providers, though they all are utility pages which are wrappers around the same ``/search`` endpoint.
* [Advanced Search](https://google.com/advanced_search)
* [Advanced Video Search](https://www.google.com/advanced_video_search)
* [Advanced Image Search](https://www.google.com/advanced_image_search)

In addition, Google has a programmable [Custom Search Engine (CSE)](https://developers.google.com/custom-search) that can be programmed from the [REST API](https://developers.google.com/custom-search/v1) as well as a [Web Dev API](https://developers.google.com/custom-search/docs/tutorial/implementingsearchbox) which is helpful to reference for clarification on more obscure query parameters.

Query parameters are provided as a query string in ``GET`` requests, one of which is exemplified below.

```
GET https://google.com/search?q=cute+dogs&as_qdr=d
```

## Query parameters

* 
* as_q -> Alias to ``q``, Main Query
* as_epq -> Return results for exact word/phrase
* as_oq -> Return results which contain any of the words 
* as_eq -> Return results which excludes all of the words
* as_nlo -> Return results with numbers having this as the low bound
* as_nhi -> Return results with numbers having this as the high bound
* lr -> Return results written in this language
* cr -> Return results written in this country
* as_qdr -> Return results written from this previous date range up to today
  - d``N`` -> Last ``N`` days
* as_sitesearch -> Return only results from this site
* as_occt -> Search only this type of text when returning results
  - url -> Search URL of resource
  - link -> Search links inside resource
  - text -> Search text inside resource
  - title -> Search title of resource
* as_filetype -> Return results with this file extension or filetype
  - Does not include ``.``
  - Unknown whether the actual type of file or just its extension is considered
* imgsz -> Return images with this size
  - l -> Large
* imgar -> Return images with this aspect ratio
  - t -> Tall
* imgc -> Return images matching this color scheme
  - gray -> Monochrome
* imgcolor -> Return images matching this color
  - red -> Red
* imgtype -> Return images of this type
  - face -> Face pictures
* tbs -> Comma-separated extra parameters
  - sur:f -> Free to use and share not including commercially
  - sur:fm -> Free to use, share, and modify not including commercially
  - sur:fc -> Free to use and share including commercially
  - sur:fmc -> Free to use, share, and modify including commercially
  - sur:cl -> Creative Commons License
  - sur:ol -> Commercial & Other Licenses
  - dur:s -> Return only videos with a short duration (0-4 minutes)
  - dur:m -> Return only videos with a medium duration (4-20 minutes)
  - dur:l -> Return only videos with a long duration (20+ minutes)
  - hq:h -> Return only videos in HD
  - cc:1 -> Return only videos with closed captioning
* tbm -> User-friendly name for service provider
  - isch -> Google Images
  - vid -> Google Videos
  - nws -> Google News
  - bks -> Google Books
  - flm -> Google Flights
* udm -> Not user-friendly ID for service provider
  - 2 -> Google Images
  - 14 -> Google Web
  - 18 -> Google Forums
  - 28 -> Google Shopping
* q -> Main Query (Series of operations)
  - ``WORD`` -> Return results containing ``WORD``
  - -``OP`` -> Return only results where ``OP`` is false
  - ``OP1`` ``OP2`` -> Return results matching operations ``OP1`` and ``OP2``
  - ``OP1`` OR ``OP2`` -> Return results matching operations ``OP1`` or ``OP2``
  - (``OP``) -> Evaluate ``OP`` first in order of operations
  - "``OP``" -> Do not delimit operations in ``OP`` by spaces
  - [``OP``] -> Alias for "``OP``"
  - site:``SITE`` -> Only return results from ``SITE``
  - before:``DATE`` -> Only return results before ``DATE``
    * ``DATE`` is in the form YEAR-MONTH-DAY
  - after:``DATE`` -> Only return results after ``DATE``
    * ``DATE`` is in the form YEAR-MONTH-DAY
  - filetype:``EXT`` -> Return results of filetype ``EXT``
    * If result does not end in ``.EXT`` but is a file of type ``EXT``, I do not know if that result is still returned, and vice versa.
    * Otherwise, results ending in ``.EXT`` are returned.
  - intitle:``OP`` -> Search title instead of everything when matching ``OP``
  - allintitle:``OP_1`` ... ``OP_N`` -> Search title instead of everything when matching ``OP_1``, ``OP_2``, ..., and ``OP_N``
  - intext:``OP`` -> Search text instead of everything when matching ``OP``
  - allintext:``OP_1`` ... ``OP_N`` -> Search text instead of everything when matching ``OP_1``, ``OP_2``, ..., and ``OP_N``
  - related:``SITE`` -> Find other sites related to website ``SITE``
  - \* -> Wildcard operator matching all phrases 

# Bing

## Endpoints

Bing's main endpoint for its search engine is [https://www.bing.com/search](https://www.bing.com/search)

Bing also has a [Web Search API](https://learn.microsoft.com/en-us/bing/search-apis/bing-web-search/reference/endpoints)


Query parameters are provided as a query string in a ``GET`` request exemplified below.
```
GET https://www.bing.com/search?q=Hell+is+a+place+on+earth&count=2
```

## Query parameters

* count -> Number of results per page
* q -> Main query (Series of operations)
  - ``WORD`` -> Return results containing ``WORD``
  - ``OP1`` ``OP2`` -> Return results containing ``OP1`` and ``OP2``
  - ``OP1`` OR ``OP2`` -> Return results containing ``OP1`` or ``OP2``
  - -``OP1`` -> Return only results where ``OP1`` is false
  - (``OP``) -> Evaluate ``OP`` first in order of operations
  - "``OP``" -> Do not delimit operations in ``OP`` by spaces
  - site:``SITE`` -> Return results only from the domain ``SITE``
  - language:``LANG`` -> Return results only written in the language ``LANG``
  - ip:``IP`` -> Return results only from ipv4 address ``IP``
  - related:``SITE`` -> Find other sites related to website ``SITE``
  - filetype:``EXT`` -> Return results of filetype ``EXT``
    * Supposedly, should be actually based on file contents rather than extension. Haven't tested this.
  - ext:``EXT`` -> Return results with file extension ``EXT``

# Robots Exclusion Protocol (robots.txt)

The robots exclusions protocol is useful for excluding various URIs that innocent and well-programmed web crawlers
should crawl. Note that web crawlers can craft any HTTP request to any URI that they want, so the protocol lays
out only suggestions to web crawlers rather than enforcements.

Web crawlers should read ``/robots.txt`` from the ``HTTP`` server and parse it according to the robots exclusion
protocol. Including this file can optimize how bots index your page and can reduce automated visits that you intend
to be used only by browsers.

It's also useful to block certain bots. Again, someone can patch the bot anyways to have the same behavior
but lie about its user agent, but it at least stops the original innocent bot from crawling your page, which
would be a much larger ratio of traffic anyways.

## Groups

All ``robots.txt`` files are a series of user agent "groups".
The first line of a group specifies the user agent, which can be
a specific one (i.e. ``Googlebot``) or ``*``, which is a special
character specifying all user agents.

```
# Specific user agent
user-agent: Googlebot

# All user agents
user-agent: *
```

## Rules

After the user agent for a group is specified, a series of "allow"
or "disallow" rules are specified on their own lines.

```
disallow: /cgi-bin
allow: /blog
```

The rules are terminated by specifying a line which isn't an
``allow`` or ``disallow`` rule, or by ending the file.
 
## Additional directives

Bots can use additional directives to guide their searches.
For instance, ``Sitemaps:`` is a common directive which specifies
a [Sitemaps](https://www.sitemaps.org/index.html) file.

```
Sitemaps: https://example.org/sitemap.xml
```

# Sources

* [Google Developer's Search Docs](https://developers.google.com/search/docs)
  - [Sitemaps](https://developers.google.com/search/docs/crawling-indexing/sitemaps/build-sitemap)
* [Sitemaps Specification](https://www.sitemaps.org/index.html)
  - [Protocol](https://www.sitemaps.org/protocol.html)
  - [FAQ](https://www.sitemaps.org/faq.html)
* [RFC 9309 Robots Exclusion Protocol (robots.txt)](https://datatracker.ietf.org/doc/html/rfc9309)
  - [robotstxt.org](http://www.robotstxt.org/about.html)
* [Google Search](https://www.google.com/search)
  - [Advanced Search](https://www.google.com/advanced_search)
  - [Advanced Video Search](https://www.google.com/advanced_video_search)
  - [Advanced Image Search](https://www.google.com/advanced_image_search)
  - [Google REST API](https://developers.google.com/custom-search/v1)
  - [Google Custom Search Overview](https://developers.google.com/custom-search/docs/overview)
* [Google Developers Custom Programmable Search Engine](https://developers.google.com/custom-search)
  - [JSON API](https://developers.google.com/custom-search/v1)
  - [Web Dev API](https://developers.google.com/custom-search/docs/tutorial/implementingsearchbox)
* [Ahref's Blog Post on Advanced Google Search Operators](https://ahrefs.com/blog/google-advanced-search-operators/)
* [Bing Search](https://www.bing.com/search)
  - [Bing Web Search API](https://learn.microsoft.com/en-us/bing/search-apis/bing-web-search/reference/endpoints)
* [SEOsly](https://seosly.com/)
  - [Bing Search Operators](https://seosly.com/blog/bing-search-operators/)
  - [Google Search Operators](https://seosly.com/blog/google-search-operators/)
* [Bing Advanced Search Operations](https://support.microsoft.com/en-us/topic/advanced-search-options-b92e25f1-0085-4271-bdf9-14aaea720930)
* [Bing Advanced Seach Keywords](https://support.microsoft.com/en-us/topic/advanced-search-keywords-ea595928-5d63-4a0b-9c6b-0b769865e78a)
* [Stack Overflow on Bing Query Parameters](https://webapps.stackexchange.com/questions/111235/what-query-parameters-does-bing-have)
