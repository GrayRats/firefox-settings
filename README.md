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
    
    // Enable TLS Delegated Credentials
    security.tls.enable_delegated_credentials = true

    // Disable Weak Ciphersuites
    security.ssl3.ecdhe_ecdsa_aes_128_sha = false
    security.ssl3.ecdhe_ecdsa_aes_256_sha = false
    security.ssl3.dhe_rsa_aes_128_sha = false
    security.ssl3.dhe_rsa_aes_256_sha = false
    security.ssl3.ecdhe_rsa_aes_128_sha = false
    security.ssl3.ecdhe_rsa_aes_256_sha = false
    security.ssl3.rsa_aes_128_gcm_sha256 = false
    security.ssl3.rsa_aes_128_sha = false
    security.ssl3.rsa_aes_256_gcm_sha384 = false
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

    //Аналогично предварительной выборке DNS от Mozilla.
    
        webgl.disabled = true 


    gfx.webrender.all = true // New GPU renderer written in Rust - Experimental
    
    
    

Ниже приведены ресурсы с дополнительной информацией по настройке Firefox для обеспечения высокого уровня приватности и защиты:

js Firefox hardening https://github.com/ghacksuserjs/ghacks-user.js. Как написано на их странице GitHub,
 это «файл конфигурации, который поможет управлять сотнями настроек 
 Firefox». Для получения более подробной информации о нем вы можете 
 перейти по данной  ссылке https://github.com/ghacksuserjs/ghacks-user.js/wiki.
   
Privacy Settings addons.mozilla.org/firefox/addon/privacy-settings/.
Это дополнение Firefox, которое предоставляет вам легкий доступ и 
контроль над встроенными настройками конфиденциальности в браузере.
  
Firefox Profilemaker https://ffprofile.com/. FFprofile поможет вам создать профиль Firefox с настройками конфиденциальности и безопасности в соответствии с вашими потребностями.
