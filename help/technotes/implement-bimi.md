---
title: Implementieren von Gmail's Brand Indicators for Message Identification (BIMI)
description: Erfahren Sie, wie Sie BIMI implementieren
topics: Deliverability
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: a4d2a75e85f37f48aa3246707b98e473682e13f6
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# Implementieren von Gmail&#39;s [!DNL Brand Indicators for Message Identification] (BIMI)

Gmail hat kürzlich angekündigt, dass sie [Einführung der allgemeinen Unterstützung von BIMI](https://cloud.google.com/blog/products/identity-security/bringing-bimi-to-gmail-in-google-workspace). Es gibt eine Reihe von Elementen, die Sie behandeln müssen, bevor Sie davon profitieren können, darunter: Verified Mark Certificates, Trademark Logos, ordnungsgemäß formatierte Logos, DMARC-Setup und schließlich Veröffentlichung eines BIMI-Datensatzes in Ihrem DNS. Wir werden alle diese Schritte in diesem Artikel überprüfen.

[!DNL Brand Indicators for Message Identification] (BIMI) ist ein Branchenstandard, der es ermöglicht, in teilnehmenden Plattformen neben der E-Mail eines Absenders ein genehmigtes Logo anzuzeigen. Dieses Augenspektrum steigert nicht nur die Interaktion, es hilft auch die Authentizität des Absenders zu bestätigen, indem es das Risiko von Phishing und anderen Spam-Taktiken verringert.

## Verified Mark Certificate

Eine der Schlüsselkomponenten des BIMI-Programms von Gmail ist die Anforderung, dass Absender über ein Verified Mark Certificate (VMC) verfügen, das von einer gültigen Zertifizierungsstelle ausgestellt wurde. Derzeit sind diese VMCs nur von Entrust und DigiCert verfügbar, aber diese Liste von Anbietern wird nach der Ankündigung von Gmail wahrscheinlich noch größer werden.

VMCs ähneln in gewisser Weise SSL-Zertifikaten. Sie benötigen einen VMC für jedes Logo, das Sie zeigen möchten. Wenn Sie also viele Marken haben, sollten Sie mehrere VMCs benötigen. Jeder VMC kann domänenübergreifend gültig sein, wenn Sie jedoch einen Multi-SAN VMC erhalten. Wenn Sie also möchten, dass ein Logo über mehrere Versanddomänen hinweg angezeigt wird, benötigen Sie nur einen VMC.

## Logo-Marke

Bevor Sie Ihren VMC abrufen können, muss ein weiterer wichtiger Schritt durchgeführt werden. Um einen VMC zu erhalten, muss das Logo, das Sie anzeigen möchten, bei einer von 8 zugelassenen globalen Marken- und Patentämtern registriert sein.

* United States Patent and Trademark Office (USPTO)
* Kanadisches Amt für geistiges Eigentum
* Amt für geistiges Eigentum der Europäischen Union
* Vereinigtes Königreich Amt für geistiges Eigentum
* Deutsches Patent- und Markenamt
* Japan Trademark Office
* Spanisches Patent- und Markenamt O.A.
* IP Australia

Wenn das Logo, das Sie anzeigen möchten, nicht registriert ist oder nicht bei einer dieser 8 Organisationen registriert ist, müssen Sie sich an Ihr Rechtsteam wenden, um dies zu klären, bevor Sie sich für den VMC bewerben.

## Logo Image Format

Dies wäre auch eine gute Zeit, um sicherzustellen, dass Ihr Logo die Anforderungen des BIMI-Logos für das Format erfüllt.

Sie muss im SVG-Format vorliegen und dem Profil SVG Portable/Secure (SVG-P/S) entsprechen. Eine Anleitung dazu finden Sie im [BIMI-Arbeitsgruppe](https://bimigroup.org/svg-conversion-tools-released).

## DMARC

Nachdem Sie Ihr Markenlogo richtig formatiert haben und Ihr Verified Mark Certificate haben, müssen Sie außerdem sicherstellen, dass DMARC für jede Versanddomäne, für die BIMI arbeiten soll, vollständig konfiguriert ist.

Dazu gehört auch, sicherzustellen, dass P= auf Quarantäne oder Ablehnen eingestellt ist. Wenn Ihr DMARC P=None verwendet, ist er nicht für BIMI qualifiziert. Die Einstellung P=None wird dringend empfohlen, um sicherzustellen, dass Sie wissen, welche E-Mail von einer Domain gesendet wird und dass nichts versehentlich blockiert wird, wenn Sie zu &quot;Quarantäne&quot;oder &quot;Ablehnen&quot;wechseln. Stellen Sie sich dies als Test- und Informationserfassungsphase vor. Sie müssen darüber hinaus zur Durchsetzung übergehen, bevor Ihnen BIMI zur Verfügung steht.

## DNS-Eintrag

Da alles andere fertig gestellt ist und bereit ist zu gehen, ist es an der Zeit, den DNS-Eintrag mit Ihrem BIMI zu aktualisieren.

Dies ist ein einfacher Eintrag, der ungefähr so aussehen sollte:

```
default._bimi.[domain] IN TXT “v=BIMI1; l=[SVG URL] 
```

Sie können Details zu diesem Eintrag erhalten und sogar eine kostenlose BIMI-Prüfung im [BIMI-Arbeitsgruppensite](https://bimigroup.org/implementation-guide).


## Wichtige Takeaways

Wenn Sie [!DNL Adobe Campaign] oder dem Marketo-Client kann Adobe Ihnen bei der Erstellung des BIMI-DNS-Updates helfen: Wenden Sie sich an die Kundenunterstützung von Adobe, um eine Anfrage zu stellen. Adobe kann auch bei der Fehlerbehebung helfen, wenn BIMI für Sie nicht richtig funktioniert.

Wenn Sie Hilfe zu Marken oder Verified Mark Certificates benötigen, wenden Sie sich an Ihr Rechtsteam und einen autorisierten VMC-Anbieter.

Die Einrichtung von BIMI für Gmail ist vielleicht kein schneller Prozess, aber es ist ein Prozess, der sowohl aus der Marketing- als auch aus der Sicherheitsperspektive erhebliche Vorteile haben kann.
