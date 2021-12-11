**Не следует** бездумно копировать себе все целиком из четвертой категории. Внимательно посмотрите и решите, что именно вам нужно. Из второй - можно, но все же рекомендуется прочитать перед этим.

Применить эти настройки можно, дописав их в конец находящегося в профиле `prefs.js`, либо создав там же файл `user.js` и записав их в него. Но не забудьте, что вы это сделали, потому что записанные в `user.js` настройки будут откатываться на указанные там значения при каждом перезапуске браузера, даже если вы меняли их другими способами (about:config, Preferences, etc). Подробнее [здесь](http://kb.mozillazine.org/User.js_file).

Кроме того, `user.js` можно (и нужно) создавать в еще ни разу не запускавшемся профиле. Т.е.: создаем профиль в Profile Manager, но **не** нажимаем Start Firefox, когда профиль уже создан. Идем в пустую папку свежесозданного профиля и записываем туда `user.js` с нужными настройками. Он применится при запуске и в результате у вас с самого начала не будет никаких нежелательных соединений и загрузок вроде БД Safebrowsing, OpenH264-кодека и т.п.



# Продвинутые аддоны
<sub>`E10S`-multi (4 processes) - совместимые с Electrolysis расширения. <br>
<s>`E10S`</s> - не совместимые, либо работающие через прослойку для совместимости (interposition). <br>
`WE` - Web Extensions, совместимы с E10S. <br>
`WE, E10S` - есть как Web Extension, так и старая версия расширения, которую можно использовать на Firefox -52.
</sub>

## Продвинутые аддоны
* [HTTPS Everywhere](https://addons.mozilla.org/en-us/firefox/addon/https-everywhere/)
<sup>WE, E10S</sup>
Содержит список сайтов, поддерживающих как HTTP, так HTTPS, и автоматически меняет все HTTP-ссылки, ведущие к этим сайтам, на HTTPS. Аддон вернули на AMO, но на всякий случай - [ссылка](https://www.eff.org/https-everywhere/) на официальный сайт. Правила обновляются редко, актуальную версию правил можно получить [на GitHub](https://github.com/EFForg/https-everywhere), там же можно отправить новое правило.

* [MixedContentHunter](https://addons.mozilla.org/en-US/firefox/addon/mixedcontenthunter/)
<sup>WE</sup>
Аддон меняет HTTP на HTTPS в запросах ресурсов документом, загруженным через HTTPS. Есть белый список на случай ломки сайта от такого поведения.

* [SSleuth](https://addons.mozilla.org/en-US/firefox/addon/ssleuth/)
<sup>E10S</sup>
([GitHub](https://github.com/sibiantony/ssleuth)) Показывает информацию об используемых криптопримитивах и фичах TLS/SSL в шифрованных соединениях.

* [RefControl](https://addons.mozilla.org/en-US/firefox/addon/refcontrol/)
<sup><s>E10S</s></sup>
Резалка [рефереров](https://en.wikipedia.org/wiki/HTTP_Referer). Можно тонко тюнить, а можно рубить только рефереры при переходе на другой домен (Block (3rd party)), оставляя внутридоменные, что просто, эффективно для 99% случаев и не ломает так много сайтов как полный запрет.

* [CleanLinks](https://github.com/diegocr/CleanLinks)
<sup><s>E10S</s></sup>
Чистит ссылки от редирект-префиксов Гугла и т.п. Имеет белый список как доменов, так и рэгэкспов, чтобы пропускать ссылки со всякими нужными префиксами вроде auth, ServiceLogin и т.п.

* [Skip Redirect](https://addons.mozilla.org/en-US/firefox/addon/skip-redirect/)
<sup>WE</sup>
Альтернатива CleanLinks. Также имеет белый список для исключений, позволяющий пропускать ссылки с нужными префиксами.

* [Google search link fix](https://addons.mozilla.org/en-US/firefox/addon/google-search-link-fix/)
<sup>WE, E10S</sup>
Более простая альтернатива CleanLinks для тех, кого он по каким-то причинам не устраивает. Работает только на Google, Yandex и Yahoo.

* [Neat URL](https://addons.mozilla.org/en-US/firefox/addon/neat-url/)
<sup>WE</sup>
Чистит ссылки, удаляя из них мусорные параметры вроде utm_source, использующиеся для трекинга. Список параметров настраивается - можно добавлять как глобальные правила, так и для определенных доменов.

* [Cookie Monster](https://addons.mozilla.org/en-US/firefox/addon/cookie-monster/)
<sup><s>E10S</s></sup>
Режет cookies и DOM Storage для сайтов, не внесенных в белый список.

* [Cookie Controller](https://addons.mozilla.org/en-US/firefox/addon/cookie-controller/)
<sup>E10S</sup>
Альтернатива Cookie Monster. После установки следует вручную вытащить кнопки на тулбар через Customize. Настройки находятся в меню Tools (Alt+T) -> Cookie Controller.

* [Self-Destructing Cookies](https://addons.mozilla.org/en-US/firefox/addon/self-destructing-cookies/)
<sup><s>E10S</s></sup>
Самоуничтожение кук после закрытия всех вкладок с соответствующим сайтом. Может быть удобнее чем полная блокировка.

* [Cookies Exterminator](https://addons.mozilla.org/en-US/firefox/addon/cookies-exterminator/)
<sup><s>E10S</s></sup>
Еще один аддон для автоматического удаления cookies и DOM Storage после закрытия использующих их вкладок.

* [Cookie AutoDelete](https://addons.mozilla.org/en-US/firefox/addon/cookie-autodelete/)
<sup>WE</sup>
Идейный продолжатель дела Self-Destructing Cookies на Web Extensions.

* [BetterPrivacy](https://addons.mozilla.org/en-US/firefox/addon/betterprivacy/)
<sup>E10S</sup>
Менее актуально с понижением числа пользователей Flash, но все же. Уничтожает [LSO](https://en.wikipedia.org/wiki/Local_shared_object), которые не может заблокировать или уничтожить сам браузер.

* [NoScript](https://addons.mozilla.org/en-US/firefox/addon/noscript/)
<sup>WE, E10S</sup>
Блокировщик JS с возможностью работы в режиме белого или черного списка. Поможет тем, у кого в простое вкладки с тяжелым JS отжирают ресурсы CPU.

	* **ВАЖНО:** См. [информацию о NoScript в сером списке](greylist.md#user-content-noscript).

* [RequestPolicy Continued](https://addons.mozilla.org/en-US/firefox/addon/requestpolicy-continued/)
<sup><s>E10S</s></sup>
Резалка кросс-доменных запросов. Можно (и рекомендуется самим автором) использовать в связке с NoScript.

* [uMatrix](https://addons.mozilla.org/en-US/firefox/addon/umatrix/)
<sup>WE, E10S</sup>
Самая многофункциональная из резалок кросс-доменных запросов. Может блокировать запросы в зависимости от типа контента. Также умеет блокировать XHR (отдельно от обычных запросов), скрипты, куки, рефереры, плагины, медиа (HTML5 аудио и видео) и вебсокеты. Документацию еще не перенесли целиком из старого проекта, на котором основан uMatrix, так что если что непонятно, смотреть не только [здесь](https://github.com/gorhill/uMatrix/wiki), но и [здесь](https://github.com/gorhill/httpswitchboard/wiki).

	* <sub>Алгоритм блокирования кук несколько отличается от того, что у Cookie Monster и Cookie Controller - первые два не дают сайтам устанавливать куки, а uMatrix дает ставить, но не дает читать, убирая из всех HTTP-запросов заголовок Cookie (но при этом через document.cookie установленные куки все еще видны), а через некоторое время - подчищает. Также в отличие от CM/CC, uMatrix не умеет запрещать писать в DOM Storage, а может только периодически его очищать.</sub>

* [NoRedirect](https://addons.mozilla.org/en-US/firefox/addon/noredirect/)
<sup><s>E10S</s></sup>
Рубит редиректы по рэгэкспам исходного или целевого URL.

* [Redirect Control](https://addons.mozilla.org/en-US/firefox/addon/redirect-control/)
<sup><s>E10S</s></sup>
Еще один блокировщик редиректов. Развивается в отличие от давно не обновлявшегося NoRedirect.

* [Redirector](https://addons.mozilla.org/en-US/firefox/addon/redirector/)
<sup>WE, E10S</sup>
Позволяет задавать пользовательские редиректы по паттернам или регулярным выражениям.

* [HttpFox](https://addons.mozilla.org/en-US/firefox/addon/httpfox/)
<sup><s>E10S</s></sup>
Мониторит все HTTP-запросы браузера. Показывает заголовки, параметры GET/POST и статус запроса (в т.ч. был ли он выполнен, взят из кэша, или отменен (NS_BINDING_ABORTED) самим браузером/другим аддоном).

* [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)
<sup><s>E10S</s></sup>
и [списки к нему](http://techpatterns.com/downloads/firefox/useragentswitcher.xml).

* [Random Agent Spoofer](https://addons.mozilla.org/en-US/firefox/addon/random-agent-spoofer/)
<sup><s>E10S</s></sup>
Меняет юзер-агенты по таймеру и с дополнительными фичами, препятствующими фингерпринтингу. Версия с GitHub имеет расширенную функциональность по сравнению с версией с AMO (см. описание на AMO).

* [CanvasBlocker](https://addons.mozilla.org/en-US/firefox/addon/canvasblocker/)
<sup>WE, E10S</sup>
Предотвращает фингерпринтинг через [анализ особенностей рендеринга элемента &lt;canvas&gt;](https://en.wikipedia.org/wiki/Canvas_fingerprinting), зависящих от ОС, железа, драйверов, шрифтов и т.п. Также см. [Bug 967895](https://bugzilla.mozilla.org/show_bug.cgi?id=967895).

* [Decentraleyes](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/)
<sup>WE, E10S</sup>
Аддон содержит популярные библиотеки (AngularJS, Backbone.js, Dojo, Ember.js, Ext Core, jQuery, jQuery UI, Modernizr, MooTools, Prototype, Scriptaculous, SWFObject, Underscore.js) и предотвращает обращения сайтов за ними ко внешним 3rd-party CDN, предоставляя вместо этого локальные копии.

	* Расширение экспериментальное и может ломать некоторые сайты. Известны проблемы с Yandex.Disk.

* [No Resource URI Leak](https://addons.mozilla.org/en-US/firefox/addon/no-resource-uri-leak/)
<sup>E10S</sup>
Предотвращает фингерпринтинг по внутренним URL браузера со схемой resource://, запрещая веб-страницам доступ к ним. Может сломать некоторые другие расширения. Подробнее о проблеме: [Ghacks](https://www.ghacks.net/2016/06/12/firefox-resource-leak/), [Bug 863246](https://bugzilla.mozilla.org/show_bug.cgi?id=863246), [Bug 903959](https://bugzilla.mozilla.org/show_bug.cgi?id=903959). Протестировать можно на Browserleaks: https://browserleaks.com/firefox
<br> **UPD:** В Firefox 57 [баг 863246](https://bugzilla.mozilla.org/show_bug.cgi?id=863246) исправлен, и необходимости в этом расширении больше нет.

* [Privacy Badger](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/)
<sup>WE, E10S</sup>
Аналог Ghostery от EFF. Актуально для тех, кто хочет поставить и забыть, чтоб оно там автоматом боролось с трекингом.


YouTube + uBlock Origin
 Убираем визуальный и мешающий мусор из окна плеера Youtube. Официально этот мусор не отключается. Мусор такой как - всплывающие окна на паузе. (Дико раздражает, когда поставил на паузу и пытаешься рассмотреть что либо в видео) Так же убирается вплывающие окна в под конец и во время видео с подписками, другими видео и прочим "нужным" контентом. (Подборка видео после полного окончания ролика остаются)Текст ниже копируем, идём в настройки uBlock Origin. "Параметры > Мои фильтры". Вставляем скопированное.
```
youtube.com/##.ytp-ce-element.ytp-ce-channel.ytp-ce-channel-this
youtube.com/##.ytp-ce-element.ytp-ce-video.ytp-ce-element-show
youtube.com/##.ytp-ce-element.ytp-ce-bottom-right-quad.ytp-ce-size-640
youtube.com##.ytp-ce-covering-overlay
youtube.com##.ytp-ce-element-shadow
youtube.com##.ytp-ce-covering-image
youtube.com##.ytp-ce-expanding-image
youtube.com##.ytp-pause-overlay
youtube.com##.ytp-scroll-min.ytp-pause-overlay
youtube.com##.iv-click-target
youtube.com##.ytp-cards-button
youtube.com##.ytp-cards-teaser
youtube.com##.ytp-ce-covering-image
youtube.com##.ytp-ce-covering-overlay
youtube.com##.ytp-ce-element
youtube.com##.ytp-ce-element-shadow
```
Ну и финальное расширение от Гугла - это естественно SponsorBlock для YouTube. Данная улита позволяет убрать встроенную рекламу внутри ролика на YouTube. Потрясающая и простая вещь.

Убираем рекламу и спам на телефоне. Android.

Скачиваем программу AdGuard с оф. сайта. https://adguard.com/ru/download.html?os=android&ref=dtf.ru 
Настраиваем работу батареи, чтобы программа не отключалась в фоновом режиме: https://kb.adguard.com/ru/android/solving-problems/background-work?ref=vc.ru

Полностью рекламу в браузере удаляет и бесплатная версия. В приложениях она тоже убирает часть рекламы, но не всегда. Напомню, что с плей маркета, приложение AdGuard НЕ работает уже 2 года! Убирает рекламу на 99% в браузерах Google Chrome, Vivaldi, Brave. В Mozilla Firefox нужно добавить сертификат, чтобы они совместно работали. В браузерах Яндекс и Opera не блокирует на страничках яндекса.

И) Приложение YouTube Vanced без рекламы и с фоновым режимом для Android+ SponsorBlock+ бесплатный YouTube Music. (Для iPhone такой программы естественно нет)


Приложении "Почта Яндекс".
Заходим в настройки и убираем ползунок "Показывать рекламу"


Для телевизора или приставки на платформе Android

1. Smart YouTube TV
https://smartyoutubetv.github.io/ru/?ref=vc.ru
2. YouTube Vanced.

