# Perfomance Bottleneck

## DB

DB is bottleneck. Using NoSQL affects logic complexity, makes model hard to support. 
Best solution: caching

## Templates 

Django templates is a trade-off for simplicity and usability.
Best solution: caching

## Python

Python is good enough to serve requests but in order to improve perfomance it is better to use web accelerators.
Be aware of 3-rd parties Django modules as many of them were not designed for Highload usage.

## Architecture

### Load Balancer

* Dispatches the traffic
* Provides SSL communication with client. At lower level http only 
* It's the single entry point for all requests
* Allow to choose dispatch strategy and set node weights

HAProxy, Nginx, Varnish, Squid

### Web accelerator

* Separate user specific and common response, common is cacheable

One of the first tasks for the web accelerator is to determine if this is a request for a resource
where the response varies with each user. For many applications it might seem like every
request varies per user.


Software: Varnish, Nginx + Memcached

### Application (Django)

Application Server goal is to provide fast WSGI implementation

Software: uWSGI, Gunicorn, Apache

Software for debugging Django: 

* django-debug-panel (Django Debug Toolbar)
* django-devserver (replacement for default runserver)

#### Celery (Scheduled Task Management, cron-like)

Allow heavy tasks to be done separately:

* 3rd party API calling
* sending email
* heavy computations

Main concepts:

* Do not use stateful objects as keys, use id/hash and get it from database
* Split tasks to be small and atomic in order to simplify spreading them across workers/CPU
* 

### Cache

Software:

* Memcached
* Redis

Cache levels

* Django per-site Cache (middleware)
* DB Query Caching
* Template Caching


#### Template Caching 

Use `cache` directive within templates

```
{% cache MIDDLE_TTL "post_list" request.GET.page %}
    {% include "inc/post/header.html" %}
        <div class="post-list">
    {% for post in post_list %}
    {% cache LONG_TTL "post_teaser_" post.id post.last_modified %}
        {% include "inc/post/teaser.html" %}
    {% endcache %}
{% endfor %}

```

Variables `MIDDLE_TTL` and `LONG_TTL` are LRU cache timeout

Template caching cannot be dropped at the time. Some custom dircetive required

### Database

Software:

* Postgres
* MySQL
* Elasticsearch
* Solr

Common bottlenecks are:

* Disk IO (read data, indexes)
* Expensive calculations

What to decrease:

* Number of queries (via cache)
 * At ORM Level By methods:
  * `select_related(*fields)`, `prefetch_related(*fields)`
  * Ensure you do not load fields you never use
  * use memoization if several fields or records are used several times during the request
   * `@cached_property` from `django.utils.functional` for fields
* Query execution Time (Reorganize logic, build additional indexes, caching)
 * Use `django-cache-tool` in order to get time metrics
 * Using EXPLAIN command in Postgres
 * Common Failure - Missing Index, 
  * use parameter `db_index=True` for ORM Model Field
  * use parameter `index_together()` for complex indexes, N.B. Postgres can work with separarte indexes, Index order matters
 * Expensive Table Join
  * Sometimes Select Join tables separately in 2 queries may be faster than in one
   * Evalueate ids from joined table, select necessary information 
 * Too many results
  * Try not to use `.all()`, enable pagination and limit for selecting rows
 * Counts
  * Try not to use `.count()` for check if record exists. Use `.exists()` instead.
 * Django Foreign Keys (ORM layer)
  * Avoid them
 * Too large results
  * Use `.defer(*fields)` and `.only(*fields)` in order to reduce transfer size/time 
  * User `.values(*fields)` and `.values_list(*fields)` in order to receive data as `dict`
 * Query duplication
  * Use custom cache mechanisms together with modules `Johnny Cache` and `Cache Machine`
 * User Read-Only Replicas
 * Use raw queries 
 * Denormalization
 * Change Data Store, Postgres allow to store bson/json schema-less data structures
 * Use Elasticsearch/Solr for complex FulltextSearch
 * Sharding (partition data across several databases)

PSQL\PGCLI:

* use `\timing on` in order show query execution time


## Settings Organization

* Create Separate **settings** module
 * Use different settings files for each role, i.e. production, dev, stage, test
 * All the settings file should inherit for common settings, overriding them
 * All the passwords, security keys and other security related information should be passed from Environment Variables and keep it in .env file


## Optimisation steps

* How many SQL queries ran?
* What was the cumulative time spent in the database?
* What individual queries ran and how long did each one take?
* What code generated each query?
* What templates were used to render the page?
* How does a warm/cold cache affect performance?


# Frontend Optimisation

* Minimize JS, CSS
* Compress Images
* Serve assets from cdn
* Do file uploading in separate node, share files via NFS

