# Firefox Advanced Settings
* [FAQ](header.md#user-content-faq)
* [Список продвинутых аддонов](addonlist.md)
* [Серый список аддонов](greylist.md)
* [CSS Стили Интерфейса](Styles.md)
* [Настройки About:Config](config.md)
## **FAQ**
[FF-90+FAQ](https://github.com/perdolka/FF) 

[FF-90+CSS](https://github.com/Aris-t2/CustomCSSforFx) 

[FF-User.js_farag2](https://github.com/farag2/Mozilla-Firefox/blob/master/user.js)

[FF-95+Руководство](https://digdeeper.neocities.org/ghost/mozilla_rus.html) 


[FF-mz.policy](https://github.com/mozilla/policy-templates/blob/v3.5/README.md)

`privacy.resistFingerprinting` = false = ломает сайты 


Error code: MOZILLA_PKIX_ERROR_KEY_PINNING_FAILURE

`security.cert_pinning.enforcement_level` = 0 = ломает сайты 

<sub>Настройки меняются через`about:config.</sub>

**[Производительность]** API WebGPU и язык шейдеров WGSL (WebGPU Shading Language) выполнения операций 3D* JavaScript API на стороне GPU.

`dom.webgpu.enable`
`gfx.webgpu.force-enabled`

1. **Q:** Проблемы с отрисовкой интерфейса, изображений или видео. Внезапные падения браузера.<br>
**A:** Попробуйте отключить аппаратное ускорение: `layers.acceleration.disabled -> true` <br>
Также проблему может решить обновление видеодрайверов либо возврат к более старой версии. Или обновление самого Firefox до беты/откат к ESR.

1. **Q:** Как уменьшить потребление памяти? <br>
**A:** Можно снизить число контент-процессов. Для этого следует **снять** чекбокс *Use recommended performance settings* в *Preferences -> General*, после чего появится список, где выбирается подходящее значение.

1. **Q:** О блокировке неподписанных расширений. <br>
**A:** Начиная с Firefox 48, в официальных релизных и бета-билдах Firefox заблокирована установка не подписанных Mozilla аддонов. Ниже приведены различные решения.
	* Выпускаются специальные [сборки](https://wiki.mozilla.org/Add-ons/Extension_Signing#Unbranded_Builds), где требование подписей отключается настройкой `xpinstall.signatures.required -> false`. Firefox ESR тоже не имеет данной проблемы.
	* Есть [хак](https://forum.mozilla-russia.org/viewtopic.php?id=70326), позволяющий обойти это ограничение даже на официальных сборках.
	* Если вы используете Linux, вероятно, мейнтейнеры вашего дистрибутива уже собрали Firefox без флага обязательного требования подписей, и его можно отключить вышеописанной настройкой.

1. **Q:** Тормозит видео на YouTube в высоких разрешениях. <br>
**A:** Кодек VP9 требует мощного процессора. Может помочь отключение `media.mediasource.webm.enabled` - тогда видео будут отдаваться в H.264. Отключение этой настройки не сломает обычные WebM.

1. **Q:** Как запретить проигрывание HTML5-медиа в фоновой вкладке? <br>
**A:** Firefox 51+: `media.block-autoplay-until-in-foreground -> true` <br>
Проигрывание начнется при первом переключении на вкладку с открытым видео или аудио.

1. **Q:** Как отключить предупреждение при переходе сайта в полноэкранный режим в Firefox 43+? <br>
**A:** `full-screen-api.warning.timeout -> 0`

1. **Q:** Как отключить анимацию затемнения при переходе сайта в полноэкранный режим? <br>
**A:** `full-screen-api.transition.timeout -> 0` <br>
`full-screen-api.transition-duration.enter -> "0 0"` (без кавычек) <br>
`full-screen-api.transition-duration.leave -> "0 0"` (без кавычек)

1. **Q:** Как искать в разных поисковиках через адресную строку? <br>
**A:** Используя префиксы-кейворды (g Google, w Wikipedia, etc), настраивающиеся в Preferences -> Search даблкликом по ячейкам второй колонки.

1. **Q:** Как отключить беспрефиксный поиск в поисковике по умолчанию через адресную строку? <br>
**A:** `keyword.enabled -> false`

1. **Q:** Как отключить кнопки поисковиков в выпадающем списке под адресной строкой? <br>
**A:** `browser.urlbar.oneOffSearches -> false`

1. **Q:** Что за специальная тема для разработчиков? <br>
**A:** Тема, использующаяся в Firefox Developer Edition. В Firefox 53+ включается через `about:addons`, на вкладке Appearance. [Аддон](https://addons.mozilla.org/en-US/firefox/addon/devedition-theme-enabler/), включающий ее на более ранних релизах.

1. **Q:** Как копировать ссылки c кириллическим текстом в исходном виде, не закодированном percent-encoding (%D0%9B%D0%B8%D1%81 -> Лис)? <br>
**A:** Firefox 53+: `browser.urlbar.decodeURLsOnCopy -> true`

1. **Q:** Как ускорить прокрутку колесом мыши? <br>
**A:** `mousewheel.min_line_scroll_amount -> 35` <br>
Значение подбирается по вкусу. Другие твики описаны [здесь](http://12bytes.org/articles/tech/firefox-scroll-tweak).

1. **Q:** Как сделать скриншот всей страницы? <br>
**A:** Shift-F2: `screenshot --fullpage <имя файла опционально>` <br>
Также можно использовать кнопку скриншота в Developer Tools (Ctrl+Shift+I), предварительно включив ее: `devtools.command-button-screenshot.enabled -> true`. Сверхдлинные страницы [не сохраняет](https://bugzilla.mozilla.org/show_bug.cgi?id=766661).

1. **Q:** Как уменьшить ширину вкладки, чтобы меньше их прокручивать? <br>
**A:** Firefox до 57: при помощи [UserCSS](https://www.ghacks.net/2011/02/02/change-firefoxs-minimum-maximum-tab-width/). Firefox 57+: `browser.tabs.tabMinWidth`

1. **Q:** Как вернуть старую поисковую строку/старый диалог настроек браузера? <br>
**A:** Воспользоваться [Classic Theme Restorer](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/) или [пользовательским стилем](https://userstyles.org/styles/122214/firefox-search-bar-show-engine-names-firefox-43).

1. **Q:** Как вернуть информацию о загрузках, скрытую в Firefox 54? <br>
**A:** При помощи [UserCSS](https://www.ghacks.net/2017/06/17/restore-download-information-in-firefox/).

1. **Q:** Как применять свои CSS к интерфейсу браузера в Firefox 57+? <br>
**A:** Используя [userChrome.css](http://kb.mozillazine.org/UserChrome.css). Подробнее - см. [раздел о стилях](addendum.md#user-content-Пользовательские-стили) в приложении.

1. **Q:** Как иметь отдельные наборы cookies для разных вкладок? <br>
**A:** При помощи [контейнеров](https://wiki.mozilla.org/Security/Contextual_Identity_Project/Containers), включив все настройки `privacy.userContext.*`. После этого в Customize появится новая кнопка для открытия вкладки в контейнере. Опции контейнеров находятся в Preferences -> Privacy.

1. **Q:** Куда девается старая история браузинга? <br>
**A:** Удаляется для улучшения производительности. Причем история ограничена не давностью, а числом записей, так что активные пользователи браузера могут упереться в лимит раньше. Значение вычисляется, исходя из характеристик ПК, и пишется в настройку `places.history.expiration.transient_current_max_pages`. Если вы считаете, что оно слишком низкое, можно установить значение вручную, но в **другой** настройке: `places.history.expiration.max_pages`. Подробнее: [статья](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/Places/Places_Expiration), [настройка](https://hg.mozilla.org/releases/mozilla-release/file/3702966a64c80e17d01f613b0a464f92695524fc/toolkit/components/places/nsPlacesExpiration.js#l44), [сам алгоритм](https://hg.mozilla.org/releases/mozilla-release/file/3702966a64c80e17d01f613b0a464f92695524fc/toolkit/components/places/nsPlacesExpiration.js#l715).

1. **Q:** Как добавить поисковик в браузер? <br>
**A:** Экспортировать встроенные [скриптом](https://gist.github.com/nohamelin/6af8907ca2dd90a9c870629c396c9521), создать по их образу и подобию новый файл в формате [OpenSearch](https://developer.mozilla.org/en-US/docs/Web/OpenSearch), затем импортировать другим [скриптом](https://gist.github.com/nohamelin/8e2e1b50dc7d97044992ae981487c6ec).

1. **Q:** Как Убрать На вкладках Кнопку закрытия (крестик на каждой вкладке) <br>
**A:** в UserChrome.css, Добавить в этот файл следующий код <br>
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* only needed once */
#tabbrowser-tabs .tabbrowser-tab .tab-close-button  {  display:none!important;  } 

## Интересные ссылки
* [Release Notes](https://www.mozilla.org/en-US/firefox/notes) и [Developer Release Notes](https://developer.mozilla.org/en-US/Firefox/Releases).
* [Ghacks](https://www.ghacks.net/category/firefox/) - сайт, на котором попадаются неплохие статьи и обзоры грядущих нововведений в Firefox.
* [Здесь](http://kb.mozillazine.org/About:config_entries) и [здесь](http://kb.mozillazine.org/Category:Preferences) приведены подробные описания настроек, жаль, не всех.
* [user.js -- Firefox hardening stuff](https://github.com/pyllyukko/user.js) - репозиторий настроек вроде этого, но с несколько другим подходом к организации.
* [ghacks-user.js](https://github.com/ghacksuserjs/ghacks-user.js) - еще один похожий проект с настройками.
* [Блог](https://cat-in-136.github.io/tags.html#tag_pref%20diff) автора аддона Configuration Mania, который выкладывает разницу между дефолтными конфигами предыдущей и новой версии Firefox. **UPD:** Настройки могут меняться и в более поздних бетах, чем там сравниваются, поэтому целиком полагаться на него не стоит.
#### Безопасность
* [Список исправленных уязвимостей](https://www.mozilla.org/en-US/security/known-vulnerabilities/firefox/)
* [Описание](https://developer.mozilla.org/en-US/Add-ons/AMO/Policy/Reviews) процедуры ревью аддонов на AMO.
* Атаки через подмену содержимого буфера обмена
  * С использованием JavaScript:
    * https://www.opennet.ru/opennews/art.shtml?num=44481
    * https://security.love/Pastejacking/
  * Без использования JavaScript, на чистом HTML: https://thejh.net/misc/website-terminal-copy-paste

#### Приватность
* [Неплохой обзор от Mozilla](https://support.mozilla.org/en-US/kb/how-stop-firefox-making-automatic-connections) с описаниями механизмов, из-за которых Firefox может инициировать соединения без прямого приказа пользователя. Еще: [соединения](http://kb.mozillazine.org/Connections_established_on_startup_-_Firefox), устанавливающиеся при запуске браузера. Настройки для отключения подобной самодеятельности есть здесь, в разделе "Настройки".
* [PrivacyTools.io](https://www.privacytools.io) - сайт, посвященный инструментам для обеспечения приватности. Можно предлагать дополнения и улучшения в их [репозитории на GitHub](https://github.com/privacytoolsIO/privacytools.io).
* [Evercookie](http://samy.pl/evercookie/). Собирательное название для техник помещения трекинг-идентификаторов в разные труднодоступные места помимо cookies, LSO и DOM Storage.
* Фингерпринтинг
  * Такие методы обнаружения, для которых не требуется запись уникального идентификатора на машину пользователя.
  * [Обзор](https://wiki.mozilla.org/Fingerprinting) методов фингерпринтинга в Mozilla Wiki и [предложения](https://wiki.mozilla.org/Security/Anonymous_Browsing) по улучшению анонимности браузера.
  * [Обзор](https://www.chromium.org/Home/chromium-security/client-identification-mechanisms) способов идентификации на сайте проекта Chromium.
  * [Tor Uplft](https://wiki.mozilla.org/Security/Tor_Uplift/Tracking) - проект по переносу патчей Tor Browser в основную ветку Firefox.
  * Проверить себя на уникальность отпечатка можно на следующих ресурсах:
    * https://panopticlick.eff.org/
    * http://ip-check.info/?lang=en
    * https://amiunique.org/
    * https://whoer.net/
    * https://browserleaks.com/
    * http://browserspy.dk/
  * Статьи по теме:
    * [Как Tor Project борется с фингерпринтингом](https://geektimes.ru/post/244484/) (более свежая [английская версия статьи](https://github.com/KOLANICH/Article-2015-Dull-captaincy-or-the-way-Tor-Project-fights-browser-fingerprinting)).
    * [Флаги HSTS и их использование для фингерпринтинга](https://geektimes.ru/post/244065/)
