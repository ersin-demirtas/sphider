# Sphider - a php spider and search engine
Sphider is a lightweight web spider and search engine written in PHP, using MySQL as its back end database. It is a great tool for adding search functionality to your web site or building your custom search engine. Sphider is small, easy to set up and modify, and is used in thousands of websites across the world. 

Sphider supports all standard search options, but also includes a plethora of advanced features such as word autocompletion, spelling suggestions etc. The sophisticated adminstration interface makes administering the system easy. The full list of Sphider features can be seen in the about section; also be sure to check out the demo and take a look at the showcase, displaying some sites running Sphider. If you run into problems, you can probably get an answer to your question in the forum.

----

Sphider is a popular open-source web spider and search engine. It includes an automated crawler, which can follow links found on a site, and an indexer which builds an index of all the search terms found in the pages. It is written in PHP and uses MySQL as its back end database (requires version 4 or above for both).

# Documentation

## Installation
1. Unpack the files, and copy them to the server, for example to 
/home/youruser/public_html/sphider (later referred to as [path_of_sphider]) 
2. In the server, create a database in MySQL to hold Sphider data.

a) at command prompt type (to log into MySQL): 
mysql -u <your username> -p 
Enter your password when prompted. 

b) in MySQL, type:
CREATE DATABASE sphider;

Of course you can use some other name for database instead of sphider. 

c) Use exit to exit MySQL.
For more information on how to create a database and give/get the necessary permissions, check MySQL.com
3. In settings directory, edit database.php file and change $database, $mysql_user, $mysql_password and $mysql_host to correct values (if you dont know what $mysql_host should be, it should probably stay as it is - 'localhost'). 

4. Open install.php script (admin directory) in your browser, which will create the tables necessary for Sphider to operate. 

Alternatively, the tables can be created by hand using tables.sql script given in the sql directory of the Sphider distribution. In the prompt, type
mysql -u <your username> -p sphider_db < [path_of_sphider]/sql/tables.sql

5. In admin directory, edit auth.php to change the administrator user name and password (default values are 'admin' and 'admin').

6. Open admin/admin.php in browser and start indexing.

7. search.php is the default search page.


Indexing options

Full: Indexing continues until there are no further (permitted) links to follow.

To depth: Indexes to a given depth, where depth means how many "clicks" away the page can be from the starting page. Depth 0 means that only the starting page is indexed, depth 1 indexes the starting page and all the pages linked from it etc.

Reindex: By checking this checkbox, indexing is forced even if the page already has been indexed.

Spider can leave domain : By default, Sphider never leaves a given domain, so that links from domain.com pointing to domain2.com are not followed. By checking this option Sphider can leave the domain, however in this case its highly advisable to define proper must include / must not include string lists to prevent the spider from going too far. 

Must include / must not include: See here for an explanation.


## Customizing
If you want to change the default behaviour of Sphider, you can do this either through the admin interface, or by directly editing conf.php in settings directory. 

To change the look of the search page to fit your site, modify or add a template in the templates directory. It should be enough to modify the search.css file and header and footer templates (header.html and footer.html). Heavier modifications can be made through editing the rest of template files. 

The list of file types that are not checked for indexing are given in admin/ext.txt. The list of common words that are not indexed are given in include/common.txt.


## Using the indexer from commandline

It is possible to spider webpages from the command line, using the syntax:

php spider.php <options> 

   where <options> are 

-all		Reindex everything in the database
-u <url>		Set the url to index
-f		Set indexing depth to full (unlimited depth)
-d <num>		Set indexing depth to <num>
-l		Allow spider to leave the initial domain
-r		Set spider to reindex a site
-m <string>		Set the string(s) that an url must include (use \n as a delimiter between multiple strings)
-n <string>		Set the string(s) that an url must not include (use \n as a delimiter between multiple strings)


For example, for spidering and indexing http://www.domain.com/test.html to depth 2, use
php spider.php -u http://www.domain.com/test.html -d 2 

If you want to reindex the same url, use
php spider.php -u http://www.domain.com/test.html -r


## Indexing pdf and doc files

Pdf and doc files can be indexed via external binaries. Download and install pdftotext and catdoc and set there location(path) in conf.php (note that under Windows, you should not use spaces in defining the executable's path). Additionally, in admin section, check the Index pdf and Index doc boxes (alternatively, set $index_pdf and $index_doc parameters to 1 in conf.php).


## Keeping pages from being indexed

### Robots.txt

The most common way to prevent pages from being indexed is using the robots.txt standard, by either putting a robots.txt file into the root directory of the server, or adding the necessary meta tags into the page headers (for more information on how to do this, see here).
Must include / must not include string list

A powerful option Sphider supports is defining a must include / must not include string list for a site (click on Advanced options in Index screen for this). Any url containing a string in the 'must not include' list is ignored. Any url that does not contain any string in the 'must include' list is likewise ignored. All strings in the string list should be separated by a newline (enter). For example, to prevent a forum in your site from being indexed, you might add www.yoursite.com/forum to the "must not include" list. This means that all urls containing the string will be ignored and wont be indexed. Using Perl style regular expressions instead of literal strings is also supported. Every string starting with a '*' in front is considered as a regular expression, so that '*/[a]+/' denotes a string with one or more a's in it.

## Ignoring links

Sphider respect rel="nofollow" attribute in <a href..> tags, so for example the link foo.html in ```<a href="foo.html" rel="nofollow>``` is ignored.

## Ignoring parts of a page

Sphider includes an option to exclude parts of pages from being indexed. This can for example be used to prevent search result flooding when certain keywords appear on certain part in most pages (like a header, footer or a menu). Any part of a page between <!--sphider_noindex--> and <!--/sphider_noindex--> tags is not indexed, however links in it are followed.



----
# Features

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
