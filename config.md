[Firefox configuration Security-hardening 2021](https://github.com/pyllyukko/user.js) 

[Firefox configuration Security](https://github.com/w008/ghacks-user.js)



'media.audiograph.single_thread.enabled' звук в один треад  интерфейсов обработки звука,Windows.Media.Audio 

`browser.sessionstore.interval` = хотяб 60000 (60 секунд между записью файла сессии вкладок)
`network.cookie.cookieBehavior` = 1

Убирание задержки анимации фулскрина видео:

`full-screen-api.transition-duration.enter;0 0`
`full-screen-api.transition-duration.leave;0 0'
`full-screen-api.warning.delay;-1`
`full-screen-api.warning.timeout;0`

На вкус после хромых:

`layout.word_select.eat_space_to_next_word`
`browser.tabs.insertAfterCurrent`
`middlemouse.scrollbarPosition`

КЭШИРОВАНИЕ В RAM:

Внимание: Разрешение кэширования в оперативную память может привести к отслеживанию браузера по "цифровым отпечаткам", создаваемым при помощи E-Tag!

Разрешение хранения кэша в оперативной памяти (в том числе и данных, полученных по шифрованным SSL-соединениям):

`browser.cache.memory.enable` =true

http://kb.mozillazine.org/Browser.cache.memory.enable

Внимание: Кэширование данных в RAM (`browser.cache.memory.enable`=true) НЕ будет работать, если кэширование запрещено глобально (`network.http.use-cache`=false)

Определение количества оперативной памяти, выделяемой под кэш (в зависимости от общего объема RAM):

`browser.cache.memory.capacity`=-1 (автоматическое определение; рекомендуется)

Допустимые значения:

0 - оперативная память не используется (не рекомендуется; см. примечание ниже);

n (целое цифровое значение) - количество килобайт, выделенных на кэш.

Примечание: Требует `browser.cache.memory.enable`=true


##### Список ломающихся от применения настроек сайтов

* Спуфинг заголовка Referer -- Avito.ru (показ телефонов), сервисы Яндекса (при использовании вместе с Decentraleyes), qiwi.com (авторизация), simplenote.com (авторизация), rapidgator.net (капча).
* `dom.event.clipboardevents.enabled` -- GitHub (Ломает копирование текста из редактора ).
* `security.ssl.require_safe_negotiation` -- Instagram, Mega.nz, многие другие.
* `dom.enable_performance` -- pornhub.com (авторизация).
* `dom.indexedDB.enabled` -- **Violentmonkey** ([аддон](https://bugzilla.mozilla.org/show_bug.cgi?id=1335919)), Twitter, Google Drive, Mega.nz. Поломка может быть частично исправлена [юзерскриптом](userjs/no-indexed-db.user.js).
* `security.ssl3.rsa_des_ede3_sha` -- https://login.skype.com/login
* `geo.enabled` -- citilink.ru (панель фильтров).
* `general.useragent.override` -- Неправдоподобно выглядящий useragent ломает maps.yandex.ru и много что еще.
* `svg.disabled` -- youtube.com (плеер).
* `privacy.resistFingerprinting` = false  -- часто ломает защищенных cdn сайтов. 
[ ]( ) 
Запрет отправки beacon - специфических HTTP-данных, утекающих от юзерагента на сервер, особенно при покидании страницы:

`beacon.enabled`=false 


Запрет OffscreenCanvas. Этот механизм обеспечивает возможность выполнения отрисовки через WebGL в отдельном потоке. Запуск WebGL в отдельном потоке производится с помощью API OffscreenCanvas, добавленного в систему Workers, предоставляющую средства для фонового выполнения длительных JavaScript-операций (даже при уже закрытом приложении!) Для отключения установите: [dev.mozilla](https://developer.mozilla.org/en-US/docs/Web/API/OffscreenCanvas) `gfx.offscreencanvas.enabled` = false — Включая,>вы защищаете себя от нагрузки WebGL. (FF 44 и выше)

учная настройка адресов и портов HTTP, SSL, FTP-соединений в режиме "network.proxy.type=1"

HTTP:

network.proxy.http=localhost
network.proxy.http_port=8118

SSL:

network.proxy.ssl=localhost
network.proxy.ssl_port=8118

FTP:

network.proxy.ftp=localhost
network.proxy.ftp_port=8118


Отключение гипотетически уязвимых алгоритмов, используемых для защищенных соединений с серверами по SSL3:

security.ssl3.ecdhe_ecdsa_rc4_128_sha=false
security.ssl3.ecdhe_rsa_rc4_128_sha=false
security.ssl3.rsa_rc4_128_md5=false
security.ssl3.rsa_rc4_128_sha=false
security.ssl3.rsa_des_ede3_sha=false


Запрет автопроигрывания мультимедийного содержимого:
`media.autoplay.enabled`=false
`media.audio_data.enabled`=false (настройка может отсутствовать или устареть)


Отключение медиакодеков:

`media.ogg.enabled`

`media.opus.enabled`

`media.raw.enabled`

`media.wave.enabled`

`media.webm.enabled`

`media.webvtt.enabled`

`media.webaudio.enabled`(настройка может отсутствовать или устареть)

`media.fragmented-mp4.gmp.enabled`

`media.fragmented-mp4.enabled`   (настройка может отсутствовать или устареть)



privacy.resistFingerprinting = ломает

## Приватные запросы URL Cтрок

`privacy.query_stripping.enabled` = true 
`privacy.query_stripping.strip_list` черый список URL Cтрок:Query Parameter Stripping или Очистка параметров запроса.

### WORKERS

Запрет Web Workers - средства для фонового выполнения длительных JavaScript-операций (FF 44 и выше). Данный сервис перехватывает сетевую активность средствами Service Workers. Обработчики сообщений, получаемых от сервера, действуют, даже когда страница с web-приложением закрыта или неактивна, и не зависят от времени жизни приложения. Это сильно нагружает ресурсы системы и занимает большую часть оперативной памяти. Для отключения установите:

dom.serviceWorkers.enabled=false
dom.workers.enabled=false
dom.workers.websocket.enabled=false

https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers
