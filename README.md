# SEO Manifesto

A comprehensive resource on search engines, their query parameters,
and how to use them to narrow down results or achieve SEO goals

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
  - ``OP1`` ``OP2`` -> Return results matching operations ``OP1`` and ``OP2``
  - ``OP1`` OR ``OP2`` -> Return results matching operations ``OP1`` or ``OP2``
  - (``OP``) -> Evaluate first in order of operations for ``OP``
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

# Sources

* [Google Search](https://www.google.com/search)
* [Google Advanced Search](https://www.google.com/advanced_search)
* [Google Developers Custom Programmable Search Engine](https://developers.google.com/custom-search)
  - [JSON API](https://developers.google.com/custom-search/v1)
  - [Web Dev API](https://developers.google.com/custom-search/docs/tutorial/implementingsearchbox)
* [Ahref's Blog Post on Advanced Google Search Operators](https://ahrefs.com/blog/google-advanced-search-operators/)