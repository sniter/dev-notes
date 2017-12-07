# Web 

## Оптимизация загрузки данных 

### Резолвинг DNS может выполняться несколькими способами

* Выставление в заголовке ответа

```
X-DNS-Prefetch-Control: on
```

* В коде html странички

``` html
<!-- Резолвинг DNS -->
<meta http-equiv="x-dns-prefetch-control" content="on">

<!-- Префетч DNS форсом для домена -->
<link rel="dns-prefetch" href="http://mydomain.com/">
```
