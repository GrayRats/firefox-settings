# Firefox Advanced Settings

Firefox advanced settings for increased privacy and security.

(!) Be careful.
 
Changing some settings can drastically change the format of  web browsing pages and lead to an error when loading some  websites. 
Thus, step-by-step changes to settings - is the best approach to modifying the browser. 
You can continue  to install add-ons and change parameters as you make sure that past modifications have taken effect and are working correctly. 

It is possible to add sites to the list of exceptions – the plugins you installed will not be used on them.

## Configure DNS over HTTPS

    // Use DoH without fallback to insecure DNS
    network.trr.mode = 3

    network.trr.uri = https://dns.east.comss.one/dns-query // Use your prefered DoH server
## WIKI DNS-over-HTTPS - https://GitHub.com/curl/curl/wiki/DNS-over-HTTPS and https://www.comss.ru/list.php?c=securedns ,TEST DOH https://www.cloudflare.com/ssl/encrypted-sni/
    network.trr.useGET = true
    network.security.esni.enabled = true

## Enable HTTPS-Only Mode

    dom.security.https_only_mode = true
    dom.security.https_only_mode_ever_enabled = true

## Enable HTTP3/QUIC

    network.http.http3.enabled = true

## SSL/TLS

    // Disable TLS 1.0 and TLS 1.1 
    security.tls.version.min = 3
    // ON TLS 1.2 and TLS 1.3
    security.tls.version.max = 4
    
    // Enable TLS Delegated Credentials
    security.tls.enable_delegated_credentials = true

    // Disable Weak Ciphersuites
    // 7.6 Блокировка алгоритма SHA1
    // Возможные значения 0=Все SHA1 сертификаты разрешены 1=Все SHA1 заблокированы
    // 3=Разрешены только локальные сертификаты, например, установленные антивирусами
    // 4=Разрешены локальные + подписанные в 2015 году или ранее
    user_pref("security.pki.sha1_enforcement_level", 1);


    // Disable OCSP
    security.OCSP.enabled = 0
    security.OCSP.require = false

    // Enforce CRLite Revocation Checks
    security.pki.crlite_mode = 2

    // Enable Encrypted Client Hello (ECH/ESNI)
    network.dns.echconfig.enabled = true
    network.dns.use_https_rr_as_altsvc = true
    // 7.4 Проверка валидности OCSP через обращение к удостоверяющему центру

    // Значения: 0=Отключено, 1=Включено (по-умолчанию), 2=Только для сайтов с EV сертификатом

    // (!)Данная настройка снижает вашу анонимность, но необходима для безопасности
    user_pref("security.OCSP.enabled", 1);
    // 7.5 Сайты не будут загружаться без получения подтверждения через OCSP
    // (!!!) Настройка очень полезна для повышения уровня безопасности, но 
    // часто ломает DNS over HTTPS в портативных и стабильных версиях Firefox
    // Включайте самостоятельно, смотрите, как будет работать лично у вас
    //user_pref("security.OCSP.require", true);



## Sandbox

    // Enable Site Isolation
    fission.autostart = true

    // Windows only process hardening - Experimental (2021)
    security.sandbox.content.win32k-disable = true
    security.sandbox.gmp.win32k-disable = true
    security.sandbox.content.shadow-stack.enabled = true
    security.sandbox.gmp.shadow-stack.enabled = true
    security.sandbox.gpu.shadow-stack.enabled = true
    security.sandbox.gpu.level = 1

## Resist Fingerprinting «Отпечаток браузера»

    privacy.resistFingerprinting = true
    privacy.spoof_english = 2

## Reject Third-Party Cookies

    network.cookie.cookieBehavior = 4
    //  0 = принимать все файлы Cookie по умолчанию.
    //  1 = принимать файлы Cookie только от определенного сайта (блокировать сторонние файлы Cookie)
    //  2 = блокировать все файлы Cookie по умолчанию
    //  3 = блокировать файлы Cookie от ранее не знакомых сайтов
    //  4 = новая политика хранения файлов Cookie (предотвращение доступа к хранилищу для трекеров)

## Tracking Protection

    privacy.trackingprotection.enabled = true
    privacy.trackingprotection.fingerprinting.enabled = true
    privacy.trackingprotection.cryptomining.enabled = true
    privacy.trackingprotection.socialtracking.enabled = true
    privacy.socialtracking.block_cookies.enabled = true
    privacy.firstparty.isolate = true
    privacy.donottrackheader.enabled = true  //посылать заголовок «do not track»
    network.http.sendRefererHeader = 0       //[Not Recommended]
    //    0 – никогда не отсылать HTTP-referer ?=скрывает «http-заголовок» 
    //    1 – отсылать только по кликнутым ссылкам
    //    2 – отсылать для ссылок и картинок (по умолчанию)
    privacy.resistFingerprinting = true //от отслеживания дактилоскопия браузера [Not Recommended]
    

## Disable Telemetry

    toolkit.telemetry.enabled = false
    toolkit.telemetry.unified = false
    toolkit.telemetry.archive.enabled = false
    toolkit.telemetry.shutdownPingSender.enabled = false
    toolkit.telemetry.firstShutdownPing.enabled = false
    toolkit.telemetry.updatePing.enabled = false
    toolkit.telemetry.newProfilePing.enabled = false
    toolkit.telemetry.bhrPing.enabled = false
    toolkit.telemetry.debugSlowSql = false
    browser.ping-centre.telemetry = false
    browser.send_pings = false
    //Prevent website tracking clicks.
    browser.send_pings.require_same_host = true
    //Only send pings if send and receiving host match (same website).
    
    browser.newtabpage.activity-stream.feeds.telemetry = false
    browser.newtabpage.activity-stream.telemetry = false
    dom.event.clipboardevents.enabled =  false
    // Disable stat collection
    media.video_stats.enabled = false

## Disable Pocket

    extensions.pocket.enabled = false
    services.sync.prefs.sync.browser.newtabpage.activity-stream.section.highlights.includePocket = false

## Enable Containers

    privacy.userContext.enabled = true
    privacy.userContext.ui.enabled = true

## Disable Disk Persistence

    browser.cache.disk.enable = false
    browser.privatebrowsing.forceMediaMemoryCache = true  //disable disk caching of video in private browsing mode.

## Others

    pdfjs.enableScripting = false    // Disable Javascript on PDF files
    geo.enabled = false              // Disable Geolocation
    dom.battery.enabled = false      // Disable Battery Status API
    browser.urlbar.trimURL = true 
    network.dns.disablePrefetch = true  //Установив значение «True» для данного параметра, запрет на «предварительную выборку» DNS.

    network.prefetch-next = false  

       //Аналогично предварительная выборка DNS от Mozilla.
       
    media.peerconnection.enabled = false //(WebRTC) [Not Recommended]
    network.websocket.enabled = false
    //WebSockets is a technology that makes it possible to open an interactive communication 
    //session between the user's browser and a server. (May leak IP when using proxy/VPN)
    
    browser.cache.offline.enable = false
    //Disables offline cache.
    network.dns.disableIPv6 = true
    //If your OS or ISP does not support IPv6, there is no reason to have this preference set to false.
    browser.cache.disk_cache_ssl = false
    //Disables caching for ssl connections.[Don't Recommend]
    dom.event.contextmenu.enabled = false
    //Don't allow websites to prevent use of right-click, 
    //or otherwise messing with the context menu.
    network.dnsCacheEntries = 100
    //Number of cached DNS entries. Lower number = More requests but less data stored.
    network.dnsCacheExpiration = 60
    //Time DNS entries are cached in seconds.   
    Network.http.sendSecureXSiteReferrer = false
    //Disable referrer headers between https websites.
    Network.http.referer.spoofSource = true
    //Send fake referrer (if choose to send referrers)maybe Error Site
    
    network.http.sendRefererHeader = 0 [if 2-3,Breaks Websites]
	// Tells website where you came from. Disabling may break some sites.
	// 0 = Disable referrer headers. 
	// 1 = Send only on clicked links.
	// 2 = (default) Send for links and image. 
    browser.newtabpage.activity-stream.section.highlights.rows = 6
    browser.newtabpage.activity-stream.section.topstories.rows = 1
    browser.newtabpage.activity-stream.topSitesRows = 5
    ///
    browser.aboutConfig.showWarning // No need to warn us
    browser.fullscreen.autohid = false //
    browser.tabs.closeWindowWithLastTab = false //closes the browser when the last tab is closed
    browser.tabs.warnOnClose = true
    dom.disable_beforeunload = true
    browser.urlbar.openintab = false
    browser.urlbar.suggest.calculator = true
    browser.urlbar.quicksuggest.sponsoredIndex = 0
    browser.urlbar.openintab = true //В новой вкладке
    browser.urlbar.decodeURLsOnCopy = true
    browser.urlbar.ctrlCanonizesURLs = false
    
    // experimental firefoxSuggestLabels
    browser.urlbar.experimental.firefoxSuggestLabels.enabled
    // Firefox_UrlBar_Suggest
    browser.urlbar.decodeURLsOnCopy
    browser.urlbar.
    browser.urlbar.quicksuggest.enabled = false //
    browser.urlbar.eventTelemetry.enabled = false
    browser.urlbar.groupLabels.enabled = True //Firefox Suggest thing..? 

##  Google
    browser.safebrowsing.enabled = false
    browser.safebrowsing.downloads.enabled = false
    browser.safebrowsing.provider.google4.dataSharing.enabled = blank
    browser.safebrowsing.provider.google4.updateURL = blank
    browser.safebrowsing.provider.google4.reportURL = blank
    browser.safebrowsing.provider.google4.reportPhishMistakeURL = blank
    browser.safebrowsing.provider.google4.reportMalwareMistakeURL = blank
    browser.safebrowsing.provider.google4.lists = blank
    browser.safebrowsing.provider.google4.gethashURL = blank
    browser.safebrowsing.provider.google4.dataSharingURL = blank
    browser.safebrowsing.provider.google4.dataSharing.enabled = false
    browser.safebrowsing.provider.google4.advisoryURL = blank
    browser.safebrowsing.provider.google4.advisoryName = blank
    browser.safebrowsing.provider.google.updateURL = blank
    browser.safebrowsing.provider.google.reportURL = blank
    browser.safebrowsing.provider.google.reportPhishMistakeURL = blank
    browser.safebrowsing.provider.google.reportMalwareMistakeURL = blank
    browser.safebrowsing.provider.google.pver = blank
    browser.safebrowsing.provider.google.lists = blank
    browser.safebrowsing.provider.google.gethashURL = blank
    browser.safebrowsing.provider.google.advisoryURL = blank
    browser.safebrowsing.downloads.remote.url = blank
    //Disable Google Safe Browsing and malware and phishing protection.
    //Stop sending links and downloading lists from google.
    //Security risk, but privacy improvement.
    //Note: this list may be incomplete as firefox updates, be sure to search for browser.safebrowsing.provider.google*
    //Also simply setting safebrowsing.*.enabled to false should make setting the URL's to blank redundant, but better to be safe.
    //If you see anything pointing google, probably best to nuke it.
    safebrowsing.phishing.enabled = false //[Not Recommended]
    safebrowsing.malware.enabled = false  
    //При поиске определенного URL-адреса Firefox принимает следующие меры предосторожности для защиты конфиденциальности пользователей.
    //Настрока отключает защиту. 
## PERFORMANCE
    layout.frame_rate.precise = true
       //Increases animation speed. May mitigate choppy scrolling.
	
    webgl.force-enabled = false 
    layers.acceleration.force-enabled = true
    layers.offmainthreadcomposition.enabled = true
    layers.offmainthreadcomposition.async-animations = true
    layers.async-video.enabled = true
    html5.offmainthread = true
      //Enable Hardware Acceleration and Off Main Thread Compositing (OMTC).
      //It's likely your browser is already set to use these features.
      //May introduce instability on some hardware.
    webgl.disabled = true 
    gfx.webrender.all = true  //New GPU renderer written in Rust - [Beta]
      // 1.2 Первичная отрисовка "скелета" интерфейса до реального отображения окна браузера 
      // https://www.ghacks.net/2021/01/25/firefox-nightly-uses-a-new-skeleton-ui-on-start-on-windows/
    browser.startup.preXulSkeletonUI = true

## MEMORY REDUCTION 
    browser.cache.memory.capacity = xx
	//Limit memory cache size. (xx = value in MB)
	
    browser.sessionhistory.max_entries = xx
	//Limit maximum pages in session history. (how many URLs you can traverse using the Forward or Back button)
	
    browser.sessionstore.max_tabs_undo = xx
	//Limit max closed tabs you can reopen.
	
    browser.tabs.animate = true
    browser.download.animateNotifications = false
	//Disable some animations.
	
    config.trim_on_minimize = true
	//Reduce memory usage when minimized. (Windows only)
    dom.animations.offscreen-throttling = false
	
    image.mem.max_decoded_image_kb = xx
	//How much info Firefox stores of uncompressed images.
	//Higher value = improve speed at the expense of increased memory usage.
	
    javascript.options.mem.max == xx
	//Limit amount of memory javascript may consume.
	//-1 = Automatic

    javascript.options.mem.high_water_mark == xx
	//Tell garbage collector to start running when javascript is using xx MB of memory. 
	//Garbage collection releases memory back to the system.
 


Ниже приведены ресурсы с дополнительной информацией по настройке Firefox для обеспечения высокого уровня приватности и защиты:

js Firefox hardening https://github.com/ghacksuserjs/ghacks-user.js.
Как написано на их странице GitHub,
это «файл конфигурации, который поможет управлять сотнями настроек 
Firefox». Для получения более подробной информации о нем вы можете 
перейти по данной  ссылке https://github.com/ghacksuserjs/ghacks-user.js/wiki.
   
Privacy Settings https://addons.mozilla.org/firefox/addon/privacy-settings/.
Это дополнение Firefox, которое предоставляет вам легкий доступ и 
контроль над встроенными настройками конфиденциальности в браузере.
  
Firefox Profilemaker https://ffprofile.com/.FFprofile поможет вам создать профиль Firefox с настройками конфиденциальности и безопасности в соответствии с вашими потребностями.

// Фишки
// Отсоединить вкладку, перетащив ее из окна 
   user_pref( "browser.tabs.allowTabDetach", true);
///
   user_pref("browser.proton.doorhangers.enabled", true);
   user_pref("browser.proton.infobars.enabled", true);
   user_pref("browser.proton.places-tooltip.enabled", true);
   user_pref("browser.proton.urlbar.enabled", true);
   user_pref("browser.startup.blankWindow", false);
   user_pref("browser.startup.preXulSkeletonUI", true);
   user_pref("browser.uidensity", 2);
