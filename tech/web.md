# Web 

## Оптимизация загрузки данных 



### Префетч DNS может выполняться несколькими способами

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

### Префетч ресурсов

* Высокий приоритет, только Chrome

``` html
<link rel="preload" href="/my/happy/file.ext" as="video" type="text/js" crossorigin="anonymous">
```

* Низкий приоритет, работает только при переходах

``` html
<link rel="prefetch" href="/my/happy/file.ext" as="video" type="text/js">

<meta http-equiv="Link" content="</images/big.jpeg>; rel=prefetch">
```

Этот вариант загрузки является частью стандарта HTML 4.01.

*Важно!*
Этот тип префетча работает только с ``<link>`` тегом

* Низкий приоритет, только Chrome
``` html
<link rel="subresource">
```
