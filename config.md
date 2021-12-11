[Firefox configuration Hardening secyrity](https://github.com/pyllyukko/user.js) 

[Firefox configuration Security](https://github.com/w008/ghacks-user.js)
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
* 
