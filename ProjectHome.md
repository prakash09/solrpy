# What is solrpy? #

solrpy is a python client for [solr](http://lucene.apache.org/solr), an enterprise search server built on top of [lucene](http://lucene.apache.org). solrpy allows you to add documents to a solr instance, and then to perform queries and gather search results from solr using your favorite programming language--python.

# Overview #

Here's the basic gist:

```
import solr

# create a connection to a solr server
s = solr.SolrConnection('http://example.org:8083/solr')

# add a document to the index
s.add(id=1, title='Lucene in Action', author=['Erik Hatcher', 'Otis Gospodnetić'])
s.commit()

# do a search
response = s.query('title:lucene')
for hit in response.results:
    print hit['title']

```

# Slightly More Details #

Optional parameters for [query](http://wiki.apache.org/solr/CommonQueryParameters), [faceting](http://wiki.apache.org/solr/SimpleFacetParameters), [highlighting](http://wiki.apache.org/solr/HighlightingParameters) and [more like this](http://wiki.apache.org/solr/MoreLikeThis) can be passed in as Python parameters to the query method. You just need to convert the dot notation (e.g. facet.field) to underscore notation (e.g. facet\_field) so that they can be used as a parameter name.

For example, lets say you wanted to get faceting information in your search result:

```
response = s.query('title:lucene', facet='true', facet_field='subject')
```

and if the parameter takes multiple values you just pass them in as a list:

```
response = s.query('title:lucene', facet='true', facet_field=['subject', 'publisher'])
```

For the full details see the [Sphinx Documentation on PyPI](http://packages.python.org/solrpy/)
# Install #

solrpy is available at the [pypi](http://pypi.python.org/pypi/solrpy/) so you should be able to:solrpy@googlecode.com

```
   easy_install solrpy
```

Or you can check out the source code and:

```
   python setup.py install
```

# Discuss #

Feel free to join our [discussion list](http://groups.google.com/group/solrpy) if you have ideas or suggestions. Also, please add examples to the [wiki](http://code.google.com/p/solrpy/w/list) if you have the time and interest.