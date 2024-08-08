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

# Google

## Endpoints

Google's main endpoint for its search engine is [https://google.com/search](https://google.com/search)

Google's Advanced Search page is [https://google.com/advanced_search](https://google.com/advanced_search)

In addition, Google has a programmable [Custom Search Engine (CSE)](https://developers.google.com/custom-search) that can be programmed from the [REST API](https://developers.google.com/custom-search/v1) as well as a [Web Dev API](https://developers.google.com/custom-search/docs/tutorial/implementingsearchbox) which is helpful to reference for clarification on more obscure query parameters.

Query parameters are provided as a query string in ``GET`` requests, one of which is exemplified below.

```
GET https://google.com/search?q=cute+dogs&as_qdr=d
```

## Query parameters

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
* tbs -> Extra parameters, usually related to licensing
  - sur:f -> Free to use and share not including commercially
  - sur:fm -> Free to use, share, and modify not including commercially
  - sur:fc -> Free to use and share including commercially
  - sur:fmc -> Free to use, share, and modify including commercially
* tbm -> User-friendly name for service provider
  - isch -> Google Images
* udm -> Not user-friendly ID for service provider
  - 2 -> Google Images
  - 14 -> Google Web
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

# Sources

* [Google Search](https://www.google.com/search)
  - [Google Advanced Search](https://www.google.com/advanced_search)
  - [Google REST API](https://developers.google.com/custom-search/v1)
  - [Google Custom Search Overview](https://developers.google.com/custom-search/docs/overview)
* [Google Developers Custom Programmable Search Engine](https://developers.google.com/custom-search)
  - [JSON API](https://developers.google.com/custom-search/v1)
  - [Web Dev API](https://developers.google.com/custom-search/docs/tutorial/implementingsearchbox)
* [Ahref's Blog Post on Advanced Google Search Operators](https://ahrefs.com/blog/google-advanced-search-operators/)
* [Bing Search](https://www.bing.com/search)
  - [Bing Web Search API](https://learn.microsoft.com/en-us/bing/search-apis/bing-web-search/reference/endpoints)
* [SEOsly's Tutorial on Bing Search Operators](https://seosly.com/blog/bing-search-operators/)
* [Bing Advanced Search Operations](https://support.microsoft.com/en-us/topic/advanced-search-options-b92e25f1-0085-4271-bdf9-14aaea720930)
* [Bing Advanced Seach Keywords](https://support.microsoft.com/en-us/topic/advanced-search-keywords-ea595928-5d63-4a0b-9c6b-0b769865e78a)
* [Stack Overflow on Bing Query Parameters](https://webapps.stackexchange.com/questions/111235/what-query-parameters-does-bing-have)