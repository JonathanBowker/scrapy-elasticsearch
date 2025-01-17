Description
===========
Scrapy pipeline which allows you to store scrapy items in Elastic Search.

Install
=======
::

   pip install ScrapyElasticSearch

Usage (Configure settings.py:)
----------------------
::
   ITEM_PIPELINES = [
       'scrapyelasticsearch.scrapyelasticsearch.ElasticSearchPipeline',
   ]

   ELASTICSEARCH_SERVERS = ['localhost']
   ELASTICSEARCH_INDEX = 'scrapy'
   ELASTICSEARCH_TYPE = 'items'
   ELASTICSEARCH_UNIQ_KEY = 'url'  # Custom uniqe key

ELASTICSEARCH_SERVERS - list of hosts or string (single host). Host format: protocl://username:password@host:port.
Examples:
    - ['http://username:password@elasticsearch.example.com:9200']
    - ['http://elasticsearch.example.com:9200']
    - 'https://elasticsearch.example.com:9200'

ELASTICSEARCH_INDEX - elastic search index
ELASTICSEARCH_TYPE - elastic search type
ELASTICSEARCH_UNIQ_KEY - optional field, unique key in string (must be a field declared in model, see items.py)
ELASTICSEARCH_BUFFER_LENGTH - optional field, number of items to be processed during each bulk insertion to Elasticsearch. Default size is 500.


Here is an example app (dirbot https://github.com/jayzeng/dirbot) in case you are still confused.

Dependencies
=========
See requirements.txt

Changelog
=========

* 0.7: A number of backwards incompatibility changes are introduced:
    - Changed ELASTICSEARCH_SERVER to ELASTICSEARCH_SERVERS
    - ELASTICSEARCH_SERVERS accepts string or list
    - ELASTICSEARCH_PORT is removed, you can specify it in the url
    - ELASTICSEARCH_USERNAME and ELASTICSEARCH_PASSWORD are removed. You can use this format ELASTICSEARCH_SERVERS=['http://username:password@host:port']
    - Changed scrapy.log to logging as scrapy now uses the logging module

* 0.6.1: Able to pull configs from spiders (in addition to reading from config file)
* 0.6: Bug fix
* 0.5: Abilit to persist object; Option to specify logging level
* 0.4: Remove debug
* 0.3: Auth support
* 0.2: Scrapy 0.18 support
* 0.1: Initial release

Issues
=============
If you find any bugs or have any questions, please report them to "issues" (https://github.com/knockrentals/scrapy-elasticsearch/issues)

Contributors
=============
* Jay Zeng (Maintainer) (https://github.com/jayzeng)
* Michael Malocha (https://github.com/mjm159)
* Ignacio Vazquez (https://github.com/ignaciovazquez)
* Julien Duponchelle (https://github.com/noplay)
* Jay Stewart (https://github.com/solidground)
* Alessio Cimarelli (https://github.com/jenkin)

Licence
=======
Copyright 2014 Michael Malocha

Expanded on the work by Julien Duponchelle

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
