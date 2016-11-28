# Django

## Cache

# Testing 

* Dummy Web-Based Cbrowser in order to test HTTP Requests and redirects

```
#!python
from django.test import Client
c = Client()
response = c.post('/login/', {'username': 'john', 'password': 'smith'})
```

* Selenium is good for UI testing/PAT