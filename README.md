# Sphider - a php spider and search engine
Sphider is a lightweight web spider and search engine written in PHP, using MySQL as its back end database. It is a great tool for adding search functionality to your web site or building your custom search engine. Sphider is small, easy to set up and modify, and is used in thousands of websites across the world. 

Sphider supports all standard search options, but also includes a plethora of advanced features such as word autocompletion, spelling suggestions etc. The sophisticated adminstration interface makes administering the system easy. The full list of Sphider features can be seen in the about section; also be sure to check out the demo and take a look at the showcase, displaying some sites running Sphider. If you run into problems, you can probably get an answer to your question in the forum.

----

Sphider is a popular open-source web spider and search engine. It includes an automated crawler, which can follow links found on a site, and an indexer which builds an index of all the search terms found in the pages. It is written in PHP and uses MySQL as its back end database (requires version 4 or above for both).

#Features

## Spidering and indexing

- Performs full text indexing.
- Can index both static and dynamic pages.
- Finds links in href, frame, area and meta tags, and can also follow links given in javascript as strings via window.location and window.open.
- Respects robots.txt protocol, and nofollow and noindex tags.
- Follows server side redirections.
- Allows spidering to be limited by depth (ie maximum number of clicks from the starting page), by (sub)domain or by directory.
- Allows spidering only the urls matching (or not matching) certain keywords or regular expressions.
- Supports indexing of pdf and doc files (using external binaries for file conversion).
- Allows resuming paused spidering.
- Possbility to exclude common words from being indexed.

## Searching

- Supports AND, OR and phrase searches
- Supports excluding words (by putting a '-' in front of a word, any page including the word will be omitted from the results).
- Option to add and group sites into categories
- Possibility to limit searching to a given category and its subcategories.
- Possibility of searcing in a specified domain only.
- "Did you mean" search suggestion on mistyped queries.
- Context-sensitive auto-completion on search terms (a la Google Suggest)
- Word stemming for english (searching for "run" finds "running", "runs" etc)


## Administering

- Includes a sophisticated web based administration interface
- Supports indexing via a web interface as well as from commandline - easy to set up cron jobs.
- Comprehensive site and search statistics
- Simple template system - easy to integrate into a site

----
© Ando Saabas 2005-2007
Email: ando (a t) set.ee
