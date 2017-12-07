# Оптимизация загрузки данных 

[TODO](https://www.youtube.com/watch?v=73lo643Wglw&t=2386s)

## Префетч DNS может выполняться несколькими способами

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

## Префетч ресурсов

### Preload

Высокий приоритет, только [Chrome и Mozilla](https://caniuse.com/#search=preload)

``` html
<link rel="preload" href="/my/happy/file.ext" as="video" type="text/js" crossorigin="anonymous">
```
Возможные варианты аттрибута `as`:

* `document` - html документ
* `fetch` - обычный GET запрос
* `font` - шрифт
* `image` - картинка
* `script` - JS скрипт
* `style` - CSS
* `worker` - JS worker / шаред воркер

Атрибут `type` отвечает за mime-type

Атрибут `crossorigin` позволяет решать проблемы CORS.

### Prefetch

Низкий приоритет, работает только при переходах. [Хорошая поддержка браузеров.](https://caniuse.com/#search=Prefetch)

``` html
<link rel="prefetch" href="http://mydomain.com/another_page/">

<meta http-equiv="Link" content="</another_page/>; rel=prefetch">
```

Возможные варианты аттрибута `rel`:

* `prefetch`
* `next`

Этот вариант загрузки является частью стандарта HTML 4.01.

*Важно!*
Этот тип префетча работает только с ``<link>`` тегом

### Subresource

Низкий приоритет, только [Chrome](https://caniuse.com/#search=Subresource)

``` html
<link rel="subresource" href="http://mydomain.com/my_page/">
```

### Preconnect

Поддержка DNS, TCP, TLS, Вебсокет.
Браузеры: [только современные](https://caniuse.com/#search=preconnect)

``` html
<link rel="preconnect" href="http://mydomain.com/ws/">
```

### Prerender

Технология Microdoft для предгрузки страниц для навигации
Браузеры: [IE11, Android](https://caniuse.com/#search=prerender)

``` html
<link rel="prerender" href="http://mydomain.com/my_page/">
```

## Источники

* [MDN: preloading content with rel="preload"](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content)
* [MDN: Link prefetching FAQ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Link_prefetching_FAQ)
* [Ускоряем загрузку ресурсов для сайта](https://ymatuhin.ru/front-end/html5-link-prefetch/)
