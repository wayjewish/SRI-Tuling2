# SRI-Tuling2

## на вкладке Network  
### записать и сохранить в HAR архив профиль загрузки ресурсов при открытии страницы  
оставлю файл в корне репо
### найти неоптимальные места:
#### дублирование ресурсов  
```
- bootstrap.bundle.min.js
- bootstrap.min.css
- bootstrap.min.js
- code.js
- fontawesome-webfont.woff2?v=4.7.0 - тут разные урлы но ресурс один и тот же
- jquery-3.5.1.js
- popper.min.js
- system_gd-logo.png
```
#### лишний размер ресурса  
```
- не сжатый html
    - html можно сжать
- не сжатые стили
    - button_style.css
    - layouts.other.css
    - main.a4ed37dfa98566caf03c.css
    - main.cd67f12d042d3a9a9e27.css
    (остальное вроде норм)
- не сжатые скрипты с комментариями
    - jquery-3.5.1.js - можно было использовать jquery-3.5.1.min.js
    - content.js
    - mobile.menu.js
    - RedblockHelper.js
    - EJournalHelper.js
    ... (там много еще)
```
#### медленно загружающиеся ресурсы
```
привел явные
долгие ответы:
    - bootstrap.min.js
    - createjs_2019.11.15_min.js
долгие ответы:
    - gd-cont-small-2.svg
    - lupa.svg
```
#### ресурсы, блокирующие загрузку
```
https://developer.chrome.com/ru/docs/lighthouse/performance/render-blocking-resources/
по логике гугла это ресурсы:
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/common_frontend.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/theme_gd_ru.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/modules/person/assets/css/persons.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/widgets/views/ContentRatingWidget/assets/css/rating.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/assets/frontend/css/layouts.other.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/modules/statBlock/widgets/views/StatBlockWidget/assets/css/statblock.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/modules/id2Auth/assets/css/rx-login.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/modules/npd/widgets/views/NpdWidget/assets/css/styles.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/widgets/views/CookieNotifyWidget/assets/css/cookie-notify.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">
<link rel="stylesheet" type="text/css" as="style" onload="this.rel='stylesheet'" href="/assets/f8e4500d/modules/id2Auth/assets/css/social-buttons.css?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762">

<script type="text/javascript" src="/assets/f8e4500d/modules/eJournal/widgets/views/HeaderRightBlockWidget/assets/js/view.js?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762"></script>
<script type="text/javascript" src="//tbcdnwidgetsprod.azureedge.net/widget/js/main.min.js" charset="utf-8"></script>

<link type="text/css" rel="stylesheet" href="https://cdn.action-mcfr.ru/widgets/prod/auth-button/1_0_0/main.a4ed37dfa98566caf03c.css">
<link type="text/css" rel="stylesheet" href="https://cdn.action-mcfr.ru/widgets/prod/favorite/1_0_0/main.cd67f12d042d3a9a9e27.css">

подтвердить смог только "/assets/f8e4500d/modules/eJournal/widgets/views/HeaderRightBlockWidget/assets/js/view.js?cache=5a6fa72bdfc8007242bf089feb2ff92203bc8762"
```
#### что-то ещё
```
- долгие ошибочные ответы
- ошибка CORS
```
### при описании найденных неоптимальных мест делать скриншот соответствующего участка панели Network, чтобы было понятно, что именно имеется в виду
все скриншоты оставлю в папке screenshots


## на вкладке Performance
### записать и сохранить в файл профиль загрузки страницы
оставлю файл в корне репо
### измерить время в миллисекундах от начала навигации до событий First Paint (FP), First Contentful Paint (FCP), Largest Contentful Paint (LCP), DOM Content Loaded (DCL), Load
```
First Paint (FP) - 403.4 мс
First Contentful Paint (FCP) - 403.4 мс
Largest Contentful Paint (LCP) - 723.4 мс
DOM Content Loaded (DCL) - 633.9 мс
Load - 22293.3 мс
```
### определить, на каком DOM-элементе происходит LCP
```
картинка - рекламный баннер
body > div.branded__center.ASE_brandImage > div > a > div > img
скриншот в папке
```
### измерить, сколько времени в миллисекундах тратится на разные этапы обработки документа (Loading, Scripting, Rendering, Painting)
```
Loading - 22 мс
Scripting - 953 мс
Rendering - 339 мс
Painting - 50 мс
```


## на вкладке Coverage
### сохранить скриншот вкладки после загрузки страницы
оставлю файл в корне репо и скриншот в папке
### измерить в килобайтах объём неиспользованного CSS в ходе загрузки страницы
```
472,84 КБ
```
### измерить в килобайтах объём неиспользованного JS в ходе загрузки страницы
```
211,75 КБ
```

## Результат
в результате выполнения домашнего задания должны быть  
- [x] два сохранённых профиля из вкладок Network и Performance (файлы)
- [x] описание неоптимальных мест при загрузке ресурсов (текст со скриншотами)
- [x] времена в миллисекундах от начала навигации до требуемых событий (числа)
- [x] указание DOM-элемента, на котором происходит LCP
- [x] объёмы неиспользованных в ходе загрузки страницы CSS и JS в килобайтах (числа)
  
## Как получить дополнительные баллы  
### Включить замедление CPU 4x slowdown и эмуляцию сети Slow 3G. Сделать такой же анализ.  
сложил все в папку Slow

## на вкладке Network  
### найти неоптимальные места:
по ресурсам там все +/- тоже самое
для медленно загружающихся ресурсов добавил скришоты для сравнения

## на вкладке Performance
### записать и сохранить в файл профиль загрузки страницы
в папке Slow
### измерить время в миллисекундах от начала навигации до событий First Paint (FP), First Contentful Paint (FCP), Largest Contentful Paint (LCP), DOM Content Loaded (DCL), Load
```
First Paint (FP) - 9167.3 мс
First Contentful Paint (FCP) - 9167.3 мс
Largest Contentful Paint (LCP) - 43549.2 мс
DOM Content Loaded (DCL) - 37559.0 мс
Load - 69922.0 мс
```
### определить, на каком DOM-элементе происходит LCP
```
тот же
```
### измерить, сколько времени в миллисекундах тратится на разные этапы обработки документа (Loading, Scripting, Rendering, Painting)
```
Loading - 116 мс
Scripting -  5191 мс
Rendering - 11997 мс
Painting - 5324 мс
```

## на вкладке Coverage
### сохранить скриншот вкладки после загрузки страницы
в папке Slow
### измерить в килобайтах объём неиспользованного CSS в ходе загрузки страницы
```
428,53 КБ
```
### измерить в килобайтах объём неиспользованного JS в ходе загрузки страницы
```
2130,59 КБ
```