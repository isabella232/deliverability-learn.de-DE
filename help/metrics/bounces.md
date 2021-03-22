---
title: Absprünge
description: Erfahren Sie mehr über die verschiedenen Arten von Absprüngen.
feature: Metriken
topics: Deliverability
kt: 7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 283f1cb2bb40818e11daa1a3753e8428b47e08ee
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 6%

---


# Absprünge

Absprünge sind das Ergebnis eines Versand-Versuchs und -Fehlers, bei dem der ISP Rückmeldungen zur Fehlerbehebung angibt. Die Absprungbehandlung ist ein wichtiger Bestandteil der Hygiene in der Liste. Nachdem eine bestimmte E-Mail mehrmals hintereinander abgeschnitten wurde, markiert dieser Prozess sie zur Unterdrückung. Die Anzahl und Art der für die Unterdrückung der Trigger erforderlichen Absprünge variieren je nach System. Dieser Prozess verhindert, dass Systeme weiterhin ungültige E-Mail-Adressen senden. Absprünge sind eine der Schlüsseldaten, die ISPs zur Ermittlung des Rufs der IP verwenden. Diese Metrik im Auge zu behalten, ist sehr wichtig. &quot;Ausgeliefert&quot;im Vergleich zu &quot;Abgebrochen&quot;ist wahrscheinlich die häufigste Methode zur Messung des Versands von Marketingmeldungen: Je höher der gelieferte Prozentsatz ist, desto besser.

Wir werden zwei verschiedene Arten von Absprüngen untersuchen.

## Hardbounces

Hard Bounces sind dauerhafte Ausfälle, die erzeugt werden, nachdem ein ISP feststellt, dass ein Mailingversuch an eine Abonnentenadresse nicht auslieferbar ist. Innerhalb des Adobe Campaigns werden feste Absprünge, die als nicht auslieferbar eingestuft werden, der Quarantäne hinzugefügt, was bedeutet, dass sie nicht erneut versucht werden. Es gibt Fälle, in denen ein harter Absprung ignoriert wird, wenn die Ursache des Fehlers unbekannt ist.
Hier sind einige häufige Beispiele für harte Absprünge:

* Adresse nicht vorhanden
* Konto deaktiviert
* Ungültige Syntax
* Ungültige Domäne

## Softbounces

Weiche Absprünge sind vorübergehende Ausfälle, die von ISPs erzeugt werden, wenn sie Probleme bei der Zustellung von E-Mails haben. Bei Soft-Fehlern wird der Versuch wiederholt (je nach Verwendung von benutzerdefinierten oder vordefinierten Versand-Einstellungen), um einen erfolgreichen Versand zu versuchen. Adressen, die kontinuierlich weichen Absprung aufweisen, werden erst dann der Quarantäne hinzugefügt, wenn die maximale Anzahl von weiteren Zustellversuchen versucht wurde (die wiederum je nach Einstellungen variieren). Zu den häufigen Ursachen für weiche Absprünge zählen die folgenden:

* Postfach voll
* Abrufen des E-Mail-Servers
* Probleme mit dem Ruf des Absenders

![Absprungarten](../assets/bounce-types.png)

>[!NOTE]
>
>Absprünge sind ein wichtiger Indikator für ein Reputationsproblem, da sie eine schlechte Datenquelle (Absprung) oder ein Reputationsproblem mit einem ISP (Absprung) hervorheben können.
>
>Weiche Absprünge treten oft beim Senden von E-Mails auf und sollten während der Wiederholung der Verarbeitung gelöst werden können, bevor sie als echte Bereitstellungsprobleme erkannt werden. Wenn Ihre Soft-Absprungrate bei einem einzelnen ISP größer als 30 Prozent ist und nicht innerhalb von 24 Stunden aufgelöst wird, sollten Sie sich bei Ihrem Adobe Campaign-Bereitstellungsberater um Bedenken bemühen.

## Produktspezifische Ressourcen

**Adobe Campaign Classic**

* [Typen und Ursachen für fehlgeschlagene Sendungen](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#delivery-failure-types-and-reasons)
* [Bounce-Message-Verwaltung](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#bounce-mail-management)
* [Bericht über nicht lieferbare und Absprünge](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/global-reports.html#non-deliverables-and-bounces)

**Adobe Campaign Standard **

* [Typen und Ursachen für fehlgeschlagene Sendungen](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html#delivery-failure-types-and-reasons)
* [Bounce-Message-Qualifizierung          ](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html#bounce-mail-qualification)
* [Zusammenfassungsbericht für Absprünge](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=en#reporting)
