### Пользовательские стили

#### Полезные стили

* [Custom CSS tweaks for Firefox 57+](https://github.com/Aris-t2/CustomCSSforFx). Сборник различных стилей от автора аддона Classic Theme Restorer.

* [Lepton-Proton Fix)](https://github.com/black7375/Firefox-UI-Fix)

https://github.com/darsain/uosc стиль mpv
#### О написании собственных стилей

В качестве изкоробочной альтернативы меняющим стили аддонам, можно использовать файлы [userChrome.css](http://kb.mozillazine.org/UserChrome.css) и [userContent.css](http://kb.mozillazine.org/UserContent.css). Если редактировать их из [Browser Toolbox](https://developer.mozilla.org/en-US/docs/Tools/Browser_Toolbox), изменения вступают в силу без перезапуска браузера. Также через Browser Toolbox удобно инспектировать элементы интерфейса самого браузера.

Некоторая пригождающаяся информация есть в [Stylish Wiki](https://github.com/stylish-userstyles/stylish/wiki)

#### Опасность юзерстилей с -moz-binding
В мозилловском CSS есть специальное предназначенное для использования с XUL свойство [-moz-binding](https://developer.mozilla.org/en-US/docs/Web/CSS/-moz-binding), при помощи которого можно привязать к элементу обработчики различных событий. Для CSS веб-страниц вытекающие из этого уязвимости давно закрыли: [bug 324253](https://bugzilla.mozilla.org/show_bug.cgi?id=324253), [bug 379959](https://bugzilla.mozilla.org/show_bug.cgi?id=379959).

Однако стили в user**Chrome**.css могут модифицировать интерфейс Firefox. Поэтому они обладают всеми возможностями стилей самого браузера и аддонов, соответственно, встроенные в них через -moz-binding обработчики выполнятся уже с правами chrome, а не content. При этом код обработчика, который обычно находится по адресу chrome:// для стилей самого браузера, может быть задан и в самом стиле в виде Data URI, так что проверку на same-origin он пройдет успешно. В результате подобные стили представляют из себя не меньшую опасность чем непроверенные аддоны.

Вот, например, самое простое, что можно сделать - поменять настройки прокси в браузере. Биндинг в нижеприведенном стиле меняет их на 127.0.0.1:8888. Работает с указанием namespace XUL и без него (с namespace HTML - не работает).

```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

#main-window {
  -moz-binding: url("data:text/xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIj8+CjxiaW5kaW5ncyB4bWxucz0iaHR0cDovL3d3dy5tb3ppbGxhLm9yZy94YmwiCiAgICB4bWxuczp4dWw9Imh0dHA6Ly93d3cubW96aWxsYS5vcmcva2V5bWFzdGVyL2dhdGVrZWVwZXIvdGhlcmUuaXMub25seS54dWwiCiAgICB4bWxuczp4Ymw9Imh0dHA6Ly93d3cubW96aWxsYS5vcmcveGJsIj4KICAgIDxiaW5kaW5nIGlkPSJleHBsb2l0Ij4KICAgICAgICA8aW1wbGVtZW50YXRpb24+CiAgICAgICAgICAgIDxjb25zdHJ1Y3Rvcj4KICAgICAgICAgICAgICAgIC8vIDwhW0NEQVRBWwogICAgICAgICAgICAgICB2YXIgcHJlZnMgPSBDb21wb25lbnRzLmNsYXNzZXNbIkBtb3ppbGxhLm9yZy9wcmVmZXJlbmNlcy1zZXJ2aWNlOzEiXS5nZXRTZXJ2aWNlKENvbXBvbmVudHMuaW50ZXJmYWNlcy5uc0lQcmVmU2VydmljZSkuZ2V0QnJhbmNoKCJuZXR3b3JrLnByb3h5LiIpOwogICAgICAgICAgICAgICBwcmVmcy5zZXRJbnRQcmVmKCJ0eXBlIiwgMSk7CiAgICAgICAgICAgICAgIHByZWZzLnNldENoYXJQcmVmKCJzb2NrcyIsICIxMjcuMC4wLjEiKTsKCSAgICAgICBwcmVmcy5zZXRJbnRQcmVmKCJzb2Nrc19wb3J0IiwgODg4OCk7CiAgICAgICAgICAgICAgICAvLyBdXT4KICAgICAgICAgICAgPC9jb25zdHJ1Y3Rvcj4KICAgICAgICA8L2ltcGxlbWVudGF0aW9uPgogICAgPC9iaW5kaW5nPgo8L2JpbmRpbmdzPgo=");
}
```



panel-animations
```
user_pref("xul.panel-animations.enabled", false); 

```
Отключение лишних анимаций

Анимации в Firefox Browser выглядят красиво, но для старых компьютеров каждый мегабайт памяти на счету. Чтобы отключить ненужные анимации установите значение false для параметра 
```
toolkit.cosmeticAnimations.enabled
```

Установите значение: false
Минимальная ширина вкладки

Изменение данной настройки заметит только внимательный пользователь Firefox. По умолчанию вкладки в Firefox имеют ширину в 76 пикселей, хотя раньше было 100 пикселей. Чтобы изменить это значение, используйте параметр 
```
browser.tabs.tabMinWidth.
```
Значение по умолчанию: 76

Установите значение: 100, если вы хотите восстановить ширину вкладок, как в старых версиях Firefox. Вы можете установить любое другое значение, которое вам понравится.

Изменение количества подсказок в адресной строке

Когда вы начинаете что-то вводить в адресную строку, Firefox выводит выпадающий список с предлагаемыми веб-ресурсами. Если вы хотите увеличить или уменьшить количество подсказок, настройте параметр 
```
browser.urlbar.maxRichResults.
```
Значение по умолчанию: 10

Установите значение: установите желаемое количество подсказок. Если хотите их полностью отключить, установите значение -1.


Увеличение времени выполнения скриптов

В Firefox скрипт должен ответить в течение 10 секунд, в противном случае Firefox выведет предупреждение, что скрипт не отвечает. Если вы используете медленное подключение к Интернету, то вы можете увеличить время выполнения скриптов с помощью параметра 

Значение по умолчанию: 10 (в секундах)

Установите значение: 20 (или любое значение выше 10)
```
dom.max_script_run_time
```

Проверка правописания во всех полях ввода

По умолчанию Firefox выполняет проверку правописания только в многострочных текстовых полях. Измените значение параметра 
```
layout.spellcheckDefault
```
Установите значение:

    0 – отключение проверки правописания
    2 – включение проверки правописания для всех текстовых полей


```
widget.non-native-theme.scrollbar.style
```

