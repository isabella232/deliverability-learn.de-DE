---
title: Echtzeit-Blackhole-Listen
description: Erfahren Sie mehr über Organisationen, die Listen von IP-Adressen und Domänen verwalten, die von Spammern verwendet werden können.
feature: Zusätzliche Ressourcen
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 84%

---


# Echtzeit-Blackhole-Listen

Mehrere Organisationen unterhalten Datenbanken mit IP-Adressen und Domains, die den Ruf haben, von Spammern verwendet zu werden. Zum besseren Verständnis, warum manche Nachrichten als Spam zurückgewiesen wurden, kann es hilfreich sein, sich diese Seiten anzusehen. Es besteht im Allgemeinen die Möglichkeit, das Entfernen von fälschlich auf diese Listen gesetzten Adressen zu fordern.

Diese Art von Datenbanken, die über einen DNS-Mechanismus abgefragt werden, nennt sich RBL (Real-time Blackhole Lists). Es gibt drei verschiedene RBL-Typen:

* Nach IP-Adresse: Auflistung von IP-Adressen, die Spam senden oder ihn wahrscheinlich weiterleiten.
* Nach Absender-Domain: Auflistung von Absender-Domains (vollständige Domain der Bounce-Message-Adresse), die Spam senden oder eine falsche Konfiguration aufweisen.
* Nach Webdomäne: Liste der Domänen (Domänen auf hoher Ebene, wie sie bei den Registrierstellen registriert sind), die in den URLs der Links und Bilder in Spam-Inhalten enthalten sind. Bei Adobe-Lösungen ist die Domäne, die berücksichtigt werden soll, im Allgemeinen die Adresse, die für die Verfolgung verwendet wird.

Im Folgenden finden Sie eine Liste der am häufigsten verwendeten RBLs. Eine umfassendere Liste finden Sie unter [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

   Weiterführende Informationen finden Sie unter [https://www.spamhaus.org/](https://www.spamhaus.org/),

   Die Datenbank ist wichtiger. Die Nennung in dieser Liste stellt im Allgemeinen eine ernste Situation dar. In diesem Fall müssen Sie SOFORT handeln und kommerzielle Dienste, Zustellbarkeitsdienste und die [Adobe Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) warnen.

* **SpamCop**

   Weiterführende Informationen finden Sie unter [https://www.spamcop.net/](https://www.spamcop.net/),

   wobei es sich um eine der bekanntesten Datenbanken handelt. Sollte eine Ihrer IP-Adressen auf diese Liste geraten, bedeutet das im Allgemeinen, dass SpamCop-Benutzer Ihre Nachrichten als Spam deklariert oder dass Sie Ihre Nachrichten an eine Spam-Falle (honeypot) von SpamCop gesendet haben.

* **URIBL**

   Weiterführende Informationen finden Sie unter [https://www.uribl.com/](https://www.uribl.com/),

   Diese Liste identifiziert die Domains, die regelmäßig in als Spam deklarierten Nachrichten erscheinen. Wenn Ihre Domain auf dieser Liste erscheint, kann dies Ihre Zustellbarkeit erheblich beeinträchtigen. Sie sollten die Zustellbarkeitsdienste und die [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) sofort informieren.

* **SURBL**

   Besuchen Sie die Seite [http://www.surbl.org/](http://www.surbl.org/),

   SURBL identifiziert die Websites, die regelmäßig in Spam erscheinen. Wenn Ihre Domain auf dieser Liste erscheint, kann dies Ihre Zustellbarkeit erheblich beeinträchtigen. Sie sollten die Zustellbarkeitsdienste und die [Adobe-Kundenunterstützung](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) sofort informieren.

* **iX Manitu**

   Diese IP-Liste findet v. a. in Deutschland Verwendung. Besuchen Sie die Seite [https://www.heise.de/ix/nixspam/](https://www.heise.de/ix/nixspam/).

<!--* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.-->
