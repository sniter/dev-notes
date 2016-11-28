# Django

## [Perfomance Bottlenecks](./perfomance.md)

## URL Dispatcher

Used regexp for pattern matching, and reversed aliases in order to simplify usage in templates

Features:

* Grouping templates
* Routes Aggregation

## Views

Is a module like this:

```
from django.http import HttpResponse
import datetime

def current_datetime(request):
    now = datetime.datetime.now()
    html = "<html><body>It is now %s.</body></html>" % now
    return HttpResponse(html)
```

May return errors:
```
if foo:
        return HttpResponseNotFound('<h1>Page not found</h1>')
    else:
        return HttpResponse('<h1>Page was found</h1>')
```

Customize error views in module:

* page_not_found()
* server_error()
* permission_denied()
* bad_request()

### Class Based Views

More flexible and extendable

```
from django.http import HttpResponse
from django.views import View

class GreetingView(View):
    greeting = "Good Day"

    def get(self, request):
        return HttpResponse(self.greeting)
```

Differ forms processing
May differ Dispatching
Has specific decorators

### View Decorators

* request type check
* specific request conditionals, i.e. etag, last_modified etc, cacheing

### Generic Views of Objects

* ListView


## Forms

As class. 

Features:

* validation
* additional constraints

## Sessions


## Migrations

Commands:

* migrate
* makemigrations
* sqlmigrate
* showmigrations

## Cache

### Resources:

* Memcached
* Database
* Filesystem
* Local Memory
* Dummy Caching (for Development)
* Custom Backends

In case of using multiple databases

Section `CACHES` in settings file

### Per-site cache

As middleware modules

```
MIDDLEWARE = [
    'django.middleware.cache.UpdateCacheMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.cache.FetchFromCacheMiddleware',
]
```

### Per-view cache

As decorator @cache_page for each `def my_view(request)`
## Middleware

Framework to process responce/request before/after model processing

Section `MIDDLEWARE` in settings file

Purpose:

* Security validation
* CSRF validation
* Tons of helpers to simplify request processing, i.e. Restrict acceess for browssers, append slashes in URL
* Process Exceptions, like 400, 403, and so far
* Gzip 

## Testing 

* Dummy Web-Based Cbrowser in order to test HTTP Requests and redirects

```
from django.test import Client
c = Client()
response = c.post('/login/', {'username': 'john', 'password': 'smith'})
```

* Selenium is good for UI testing/PAT

* `Pytest` with:
 * pytest-django, 
 * pytest-bdd, 
 * pytest-flakes
 * pytest-catchlog
