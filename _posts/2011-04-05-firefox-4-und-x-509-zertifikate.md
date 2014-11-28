---
title: Firefox 4 und X.509-Zertifikate
author: Markus Tacker
layout: post
permalink: /firefox-4-und-x-509-zertifikate
categories:
  - Technik
tags:
  - Firefox
---
Im neuesten Firefox funktionieren einige Zertifikate nicht mehr, mit denen z.B. Zugänge zu Content-Management-Systemen oder Banking-Webseiten gesichert werden.

Diese Zertifkate (mit Dateiendungen wie z.B. .p12) lassen sich auch nicht mehr über den Zertifikate-Manager von Firefox importieren.

Mit zwei kleinen Handgriffen kann man den Firefox aber doch wieder dazu überreden, mit den Zertifikaten zu arbeiten.

Zuerst muss in <about:config> der Wert `security.ssl.allow_unrestricted_renego_everywhere__temporarily_available_pref` auf true gestellt werden — sonst verweigert der Fuchs jede Verbindung.

Anschließend wird das Zertifikat mit Hilfe des Kommandozeilen-Tools `<a href="http://www.mozilla.org/projects/security/pki/nss/tools/pk12util.html">pk12util</a>` importiert:

`pk12util -i <zertifikat.p12> -d ~/.mozilla/firefox/<profile>/<br />
Enter password for PKCS12 file:<br />
pk12util: PKCS12 IMPORT SUCCESSFUL`

Jetzt noch den Firefox neu starten und schon klappt die Verbindung wieder.