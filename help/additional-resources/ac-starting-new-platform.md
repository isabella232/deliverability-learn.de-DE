---
title: Einrichten einer neuen Plattform
description: Erfahren Sie mehr über die Verwaltung der Zustellbarkeit beim Einrichten einer neuen Plattform mit Adobe Campaign.
feature: Praktische Umsetzung
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 59%

---


# Einrichten einer neuen Plattform {#starting-new-platform}

Die Erhaltung Ihrer Domäne und des Rufs Ihrer IP-Adresse ist unverzichtbar, wenn Sie eine neue Plattform einrichten, die mit Adobe Campaign verwendet werden kann.

## Ein sensibler Schritt

Sie sollten sehr vorsichtig sein, wenn Sie beginnen, E-Mails auf einer neuen Plattform zu senden, da die Plattform keine Nutzungsgeschichte hat und keinen Ruf, wenn die sendenden IPs nie für diesen Zweck verwendet wurden.

ISPs sind naturgemäß argwöhnisch gegenüber IP-Adressen, die noch nie zum Senden von E-Mails verwendet wurden und plötzlich große Mengen von E-Mail-Traffic verursachen. Tatsächlich nutzen Spammer im Allgemeinen &quot;unbekannte&quot; IP-Adressen (Adressen, die noch nie auf Blockierungslisten standen), um vor der Erkennung eine maximale Anzahl von Nachrichten zu senden.

Erwarten Sie nicht, dass der Versand gleich zu Beginn der Produktionsphase in der gewünschten Geschwindigkeit durchgeführt werden kann. Sie sollten auch nicht versuchen, Nachrichten in dieser Geschwindigkeit zu versenden, da dies ISPs veranlassen könnte, die Absenderadresse zu blockieren, was die Anfangsphase erheblich beeinträchtigen würde.

## Wichtigste Grundsätze

Nachfolgend sind die wichtigsten Grundsätze aufgeführt, die Sie beim Start einer neuen Plattform beachten müssen.

* Konfigurieren Sie eine dedizierte Subdomäne, die spezifisch für E-Mail-Kampagnen ist, die von der Adobe gesendet werden.

* Wenn Sie über solche Daten verfügen, **importieren Sie ungültige Adressen in die Quarantänetabelle**.
Oft werden Plattformen gestartet, wenn eine Adressliste zum ersten Mal verwendet wird; diese ist möglicherweise nicht vollständig qualifiziert. Wenn Sie an ungültige Adressen oder Honeypot-Adressen senden, verschlechtert sich die Reputation der Plattform.

   * Wenn Sie über eine Liste ungültiger Adressen verfügen, ist es in Ihrem besten Interesse, diese in die Quarantäne zu importieren, bevor Sie sie zum ersten Mal senden. Die Tabelle &quot;Quarantäne&quot;ist über die Menüs **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** (Campaign Classic) und **[!UICONTROL Administration > Channels > Quarantines > Addresses]** (Campaign Standard) verfügbar.

   * Wenn Sie die ungültigen Adressen trotzdem erneut qualifizieren möchten, ist es viel besser, dies zu tun, sobald die Reputation der Plattform etabliert ist – und zwar nach und nach, um die Verwendung schlechter Adressen im Laufe der Zeit zu &quot;verwässern&quot;.

* **Begrenzen Sie die Durchsatzrate**, indem Sie die Anzahl der &quot;mtachilds&quot; einschränken. Wenden Sie sich für weitere Informationen zum Anpassen dieser technischen Einstellung an Ihren Adobe Campaign-Administrator.

* **Erhöhen Sie die gesendeten Volumen schrittweise**, damit diese nicht als Spam gekennzeichnet werden. Senden Sie nicht gleich an die gesamte Datenbank, sondern fügen Sie bei jedem Senden einen weiteren Anteil der Liste hinzu. So sollten Sie das Volumen bei jedem Schritt erhöhen und gleichzeitig die Gesamtrate ungültiger Adressen reduzieren können. Um eine reibungslose Anfangsphase zu gewährleisten, können Sie Schübe verwenden.

* **Senden Sie regelmäßig**. Bis zu einem gewissen Grad ist es besser, regelmäßig kleine Schüsse zu senden, anstatt große Kampagnen sporadisch.
* **Beachten Sie dabei die Versandberichte**. Hohe Fehlerindikatoren können darauf hindeuten, dass eine technische Einstellung nicht richtig konfiguriert ist.

## Zusätzliche Ressourcen

Weitere Informationen zu den oben genannten Grundsätzen und ihrer Umsetzung mit Adobe Campaign finden Sie in den folgenden Abschnitten:

* [E-Mail-Reputation mit IP-Warming verbessern](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [Alles über Spam-Fallen](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Optimieren Sie Ihren Versand durch Quarantänen.](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identifizieren Sie für die gesamte Plattform isolierte Adressen.](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [In mehreren Schüben versenden](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [Überwachung der Versand](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html#sending-messages)

**Adobe Campaign Standard **

* [Optimieren Sie Ihren Versand durch Quarantänen.](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identifizieren Sie für die gesamte Plattform isolierte Adressen.](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)
* [Versand beobachten](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html)
