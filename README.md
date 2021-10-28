# Firefox Advanced Settings

Firefox advanced settings for increased privacy and security.

## Configure DNS over HTTPS

    // Use DoH without fallback to insecure DNS
    network.trr.mode = 3

    network.trr.uri = https://dns.east.comss.one/dns-query // Use your prefered DoH server
    network.trr.useGET = true

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
    security.ssl3.ecdhe_ecdsa_aes_128_sha = false
    security.ssl3.ecdhe_ecdsa_aes_256_sha = false
    security.ssl3.dhe_rsa_aes_128_sha = false
    security.ssl3.dhe_rsa_aes_256_sha = false
    security.ssl3.ecdhe_rsa_aes_128_sha = false
    security.ssl3.ecdhe_rsa_aes_256_sha = false
    security.ssl3.rsa_aes_128_gcm_sha256 = true
    security.ssl3.rsa_aes_128_sha = false
    security.ssl3.rsa_aes_256_gcm_sha384 = true
    security.ssl3.rsa_aes_256_sha = false
    security.ssl3.rsa_des_ede3_sha = false

    // Disable OCSP
    security.OCSP.enabled = 0
    security.OCSP.require = false

    // Enforce CRLite Revocation Checks
    security.pki.crlite_mode = 2

    // Enable Encrypted Client Hello (ECH/ESNI)
    network.dns.echconfig.enabled = true
    network.dns.use_https_rr_as_altsvc = true

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
    privacy.donottrackheader.enabled = true  //,посылать заголовок «do not track
    network.http.sendRefererHeader = 0       //,«http-заголовок»
    //    0 – никогда не отсылать HTTP-referer
    //    1 – отсылать только по кликнутым ссылкам
    //    2 – отсылать для ссылок и картинок (по умолчанию)

## Disable Telemetry

    toolkit.telemetry.enabled = false
    toolkit.telemetry.unified = false
    toolkit.telemetry.archive.enabled = false
    toolkit.telemetry.shutdownPingSender.enabled = false
    toolkit.telemetry.firstShutdownPing.enabled = false
    toolkit.telemetry.updatePing.enabled = false
    toolkit.telemetry.newProfilePing.enabled = false
    toolkit.telemetry.bhrPing.enabled = false
    browser.ping-centre.telemetry = false
    browser.send_pings = false
    // Prevent website tracking clicks.
    browser.send_pings.require_same_host = true
    // Only send pings if send and receiving host match (same website).
    
    browser.newtabpage.activity-stream.feeds.telemetry = false
    browser.newtabpage.activity-stream.telemetry = false
    dom.event.clipboardevents.enabled =  false


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

    network.dns.disablePrefetch = true  //Установив значение «True» для данного параметра, запрет на «предварительную выборку» DNS.

    network.prefetch-next = false  

       //Аналогично предварительная выборка DNS от Mozilla.
    
    network.websocket.enabled = false
       //   WebSockets is a technology that makes it possible to open an interactive communication 
       //   session between the user's browser and a server. (May leak IP when using proxy/VPN)
    
    browser.cache.offline.enable = false
       //    Disables offline cache.
    network.dns.disableIPv6 = true
       //If your OS or ISP does not support IPv6, there is no reason to have this preference set to false.
    browser.cache.disk_cache_ssl = false
       //Disables caching for ssl connections. [Don't Recommend]
    dom.event.contextmenu.enabled = false
       //Don't allow websites to prevent use of right-click, 
       //or otherwise messing with the context menu.
    network.dnsCacheEntries = 100
       //Number of cached DNS entries. Lower number = More requests but less data stored.
    network.dnsCacheExpiration = 60
       //Time DNS entries are cached in seconds.   
    Network.http.sendSecureXSiteReferrer = false
       //    Disable referrer headers between https websites.
    Network.http.referer.spoofSource = true
       //    Send fake referrer (if choose to send referrers).
    
    network.http.sendRefererHeader = 0 [if 2-3,Breaks Websites]
	Tells website where you came from. Disabling may break some sites.
	0 = Disable referrer headers. 
	1 = Send only on clicked links.
	2 = (default) Send for links and image.    

##  Google
    browser.safebrowsing.enabled = false
    browser.safebrowsing.phishing.enabled = false
    browser.safebrowsing.malware.enabled = false
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
## MEMORY REDUCTION 
    browser.cache.memory.capacity = xx
	//Limit memory cache size. (xx = value in MB)
	
    browser.sessionhistory.max_entries = xx
	//Limit maximum pages in session history. (how many URLs you can traverse using the Forward or Back button)
	
    browser.sessionstore.max_tabs_undo = xx
	//Limit max closed tabs you can reopen.
	
    browser.tabs.animate = false
    browser.download.animateNotifications = false
	//Disable some animations.
	
    config.trim_on_minimize = true
	//Reduce memory usage when minimized. (Windows only)
	
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


Отсоединить вкладку, перетащив ее из окна 
browser.tabs.allowTabDetach = true
