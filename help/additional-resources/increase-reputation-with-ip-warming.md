---
title: E-Mail-Reputation mit IP-Warming verbessern
description: Erfahren Sie, warum es wichtig ist, Ihren E-Mail-Ruf durch IP-Erwärmung zu verbessern und wie Sie mit der optimalen Bereitstellung fortfahren.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '1602'
ht-degree: 2%

---


# E-Mail-Reputation mit IP-Warming verbessern

<!--Increase your email reputation with IP warming

## IP Warming overview

In the Adobe Deliverability Consulting and Deliverability Operations teams, we have a vested interest in helping new Campaign customers be as successful as possible as they embark on the route of an IP warming process. If you’ve never been a part of such a project, you may have a lot of questions about it. Let’s get down to the details!-->

## Erste Schritte

Für die Adobe müssen Kunden ihre Konfiguration freigeben, damit das Adobe Deliverability Team Ihr individuelles Programm verstehen kann. Die Fragen, die wir stellen, sollen dem Adobe Deliverability Team dabei helfen, Ihren Ruf und Ihr E-Mail-Volumen zu verstehen. Ohne ein konkretes Verständnis Ihres Geschäftsmodells, E-Mail-Marketingziele und Reputationsmetriken sind wir nicht in der Lage, die Strategie anzupassen, und es besteht die Gefahr von Problemen mit der Lieferbarkeit.

Zuerst werden Ihnen eigene IP-Adressen (Internet Protocol) zugewiesen. Im Zusammenhang mit dem Senden von E-Mails ist eine IP-Adresse die Route, die verwendet wird, um Ihre E-Mail-Nachrichten an Ihre Kunden zu senden. IP-Adressen und Domänen werden zur Identifizierung von Absendern in einem Netzwerk an die empfangenden ISPs verwendet. Adobe weist die passende Anzahl dedizierter IP-Adressen zum Senden von E-Mails zu, basierend auf Ihrem Versandvolumen, Ihren E-Mail-Programmen, Ihren Datensegmentierungspraktiken und Ihrem Vertrag.

**Verwandte Themen:**
* [So wechseln Sie beim reibungslosen Transition von E-Mail-Plattformen](../../help/transition-process/switching-email-platforms.md)
* [IP-Strategie](../../help/transition-process/infrastructure.md#ip-strategy)
* [ISP-spezifische Aspekte bei der IP-Erwärmung](../../help/transition-process/isp-specific-considerations-during-ip-warming.md)

## IP-Erwärmung: Warum wird das getan? {#why-ip-warming}

Internet-Dienstleister (ISPs) oder Mailbox-Anbieter (MBPs) treffen Vorkehrungen, wenn sie eine unbekannte IP-Adresse erkennen und eine Domäne senden. Dies ist ein Standardverfahren, das unabhängig vom Absendetyp mit neuen Sende-IPs verknüpft ist. ISPs/MBPs stellen die IP-Adresse und die sendende Domäne einer strengen Prüfung unterworfen, um festzustellen, ob es sich bei den von dieser IP und Domäne gesendeten E-Mails um Spam handelt.  Dies ist ein Standardverfahren, das unabhängig vom Absendetyp mit neuen Sende-IPs verknüpft ist.

ISPs untersuchen sorgfältig das Versandvolumen, die Sendungshäufigkeit, die Beschwerden und die Absprungraten, die aus diesen Mailings entstehen. Diese werden alle genau überprüft, weil sie Indikatoren für den Ruf des Absenders sind - sei es gut oder schlecht.

Dieser Prozess der Untersuchung dieser Datenpunkte braucht natürlich Zeit, und er kann nicht innerhalb von ein oder zwei Tagen erreicht werden. Reputation wird im Laufe der Zeit aufgebaut. Dieser Prozess ist so, als ob man einen Fremden zu Hause lassen würde. Hätten Sie Vorbehalte, jemanden, den Sie noch nie getroffen haben, in Ihr Haus einreisen zu lassen?

Sehr wahrscheinlich ist die Antwort ja. Sie würden diese Person und ihre Motive analysieren wollen. Heißt das Schaden? Sind sie eine Bedrohung? Die ISPs tun das Gleiche, um ihr Netzwerk vor bösartigem oder unerwünschtem Traffic zu schützen. Positive Reputationsmetriken helfen Ihnen bei der erfolgreichen IP-Erwärmung, einen langen Weg zu gehen. Deshalb betonen wir, wie wichtig es ist, mit dem Versand kleiner E-Mail-Volumes zu beginnen und zunächst an Ihre hochengagierten Kunden zu senden. Weitere Informationen hierzu finden Sie unter [Targeting-Kriterien beim Senden von neuem Traffic](/help/transition-process/targeting-criteria.md).

Das Versenden großer Mengen von E-Mails von einer brandneuen IP oder IPs direkt aus dem Tor ist eine schlechte Praxis und wird Sie wahrscheinlich einige Lieferschwierigkeiten bereiten. Es ist wichtig zu beachten, dass selbst wenn Sie Beginn haben, kleine Volumes zu senden und diese nach und nach zu erhöhen, es dennoch notwendig ist, die Best Practices für E-Mails zu befolgen.

![](../../help/assets/ip-warming-volume-trend.png)

## E-Mail-Berechtigung (explizite Teilnahme)

Dies ist die wichtigste Komponente für die Verwaltung und Erweiterung einer E-Mail-Liste für Abonnenten. Da Anti-Spam-Gesetze auf internationaler Ebene wachsen und umfassender werden, sollte es ein Hauptaugenmerk des Marketingspezialisten sein, sicherzustellen, dass jeder Abonnent seine ausdrückliche (oder ausdrückliche) Zustimmung zu seiner Liste erhalten hat. Das heißt, jeder Abonnent hat sich aktiv mit E-Mails Ihrer Marke einverstanden erklärt. Dies unterscheidet sich von der impliziten Zustimmung, wenn eine Person einer E-Mail-Liste hinzugefügt wird, nachdem eine Aktion durchgeführt wurde, die nicht explizit für ein E-Mail-Programm registriert wurde.

Weitere Informationen finden Sie unter Akzeptabler Verwendungsrichtlinie](https://www.adobe.com/de/legal/terms/aup.html) der Adobe.[

## Reputationsmetriken: Was suchen ISPs?

ISPs nutzen hoch entwickelte Technologien, um fundierte Entscheidungen darüber zu treffen, ob sie E-Mails von externen Netzwerken erhalten oder nicht. Manchmal haben sie komplizierte und proprietäre Algorithmen in ihrem Werkzeugsatz, um sie dabei zu unterstützen.

Einige der untersuchten Datenpunkte sind:

* Treffer für Spam-Fallen
* Blockierungslisten-Hits
* E-Mail-Absprünge
* Abonnementeinsatz

ISPs erfordern spezifische technische Konfigurationen, die mit ihren Richtlinien und bewährten Verfahren im Einklang stehen. Adobe konfiguriert Ihre IPs und delegierten Subdomänen, um Sie als verantwortlichen und vertrauenswürdigen Absender zu identifizieren. Dies wird als [E-Mail-Authentifizierung](/help/transition-process/infrastructure.md#authentication) bezeichnet. Die Authentifizierung hilft Empfängern bei der Überprüfung, ob ein Absender über die Rechte verfügt, die von dieser IP oder Domäne zu senden sind.

Mit der Authentifizierung können die ISPs überprüfen, ob die von einer Domäne oder IP gesendete Firma dazu berechtigt ist. Es wird im Wesentlichen getan, um Ihre Identität zu beweisen und sicherzustellen, dass Sie nicht so tun, als wären Sie jemand anderes, und dass jemand anderes nicht so tut, als wäre Sie.

Zur Adobe werden wir SPF und DKIM standardmäßig konfigurieren und DMARC auf Anfrage konfigurieren. ISPs verweisen auf SPF und DKIM als primäre Authentifizierungsformen. Viele ISPs integrieren auch DMARC (Domain-based Message Authentication, Berichte &amp; Conformance) in ihre Filterentscheidungen. Nicht authentifizierte E-Mails werden nicht unbedingt blockiert, sie werden jedoch zusätzlich gefiltert.

## IP-Erwärmung: Was zu erwarten ist

### Geschützte oder blockierte Post

Spammer senden ständig von neuen IPs - sie werden durch einen Pool von IPs brennen, bis sie heruntergefahren werden und den Prozess auf einem anderen Pool von IPs wiederholen. Infolgedessen behandeln ISPs den von neuen IPs gesendeten Datenverkehr sorgfältig. IPs werden daran gehindert, eine große Anzahl von E-Mails zu senden, weil sie vermuten, dass es sich hierbei um eine böswillige Aktivität handelt, die von Spammer ausgeführt wird.

Daher ist es nicht ungewöhnlich, dass Sie verzögerte oder gedrosselte Nachrichten erhalten, wenn Sie Beginn per E-Mail von Ihren neuen IPs senden. Nach einigen weiteren Zustellversuchen wird die Nachricht in der Regel akzeptiert und zugestellt.

Es kann einige Tage dauern, bis ein normaler Datenverkehr zu den ISPs, der neue Absender zurückstellt, erreicht wird. Trotzdem sollten Sie nicht aufhören, E-Mails zu versenden - konzentrieren Sie sich weiterhin darauf, nur an Ihre am meisten engagierten E-Mail-Abonnenten zu senden.

In seltenen Fällen blockiert der ISP den neuen Absender. Adobe überwacht Ihr Konto, und wenn ein solcher Block vermutet wird, wird sich an den ISP wenden, um zu versuchen, die Situation auf die bestmögliche Weise zu beheben.

Denken Sie daran, dass Konsistenz hier der Schlüssel ist. Unregelmäßige Versandvolumen-Muster und seltene Mailing-Muster führen unterwegs zu Lieferschwierigkeiten.

### Beschwerden

[](/help/metrics/complaints.md) Beschwerde, wenn ein Abonnent eine E-Mail über sein E-Mail-Programm als Spam kennzeichnet. Dadurch wird dem ISP eine Mitteilung über die Aktivität der Beschwerde übermittelt. Wenn genug dieser Beschwerden beim ISP eingehen, wird dieser ISP seine Kunden schützen - möglicherweise werden viele E-Mails daran gehindert, an die Abonnenten zu gelangen oder einen Teil der E-Mails an den Massenordner zu leiten, anstatt die Postfächer der Abonnenten zu verschlüsseln. Wenn Ihr Versand durch Beschwerden verursacht wird, ist es wichtig zu ermitteln, warum Empfänger sich beschweren.

Abonnenten beschweren sich aus verschiedenen Gründen. Manchmal möchte ein Abonnent keine weiteren E-Mails von Ihnen erhalten, vielleicht weil er zu viele Nachrichten zu demselben Thema erhält, die Nachricht nicht erwartet hat oder sich nicht daran erinnern kann, sich für den Erhalt Ihrer E-Mails angemeldet zu haben.

### Datengültigkeit

Hardbounces treten auf, wenn Sie bei einem ISP an eine nicht zustellbare Adresse senden. Eine Adresse kann aus vielen Gründen unauslöschbar sein, z. B. aus einem Fehler bei der Eingabe der Adresse oder beim Versenden an eine Adresse, die zuvor zwar aktiv war, aber nach einer Inaktivität geschlossen oder beendet wurde.

Wenn Sie auf eine große Anzahl von harten Absprüngen stoßen, ist es wichtig zu verstehen, warum. Überprüfen Sie, wie die Adressen erfasst wurden, und bestätigen Sie, dass die Berechtigung erteilt wurde. Manchmal schließen Personen ihr E-Mail-Konto und benachrichtigen diejenigen nicht, die diese Adresse auf ihrer Marketing-Liste haben.

### Interaktion

ISPs suchen nach konsistentem Volumen und guter Datenqualität. Sie werden den Traffic in den nächsten vier bis acht Wochen langsam und stetig steigern. Manchmal erfordern Upups mehr oder weniger Zeit, je nach Volumen und Zielen, aber normalerweise handelt es sich dabei um mindestens einen 8-wöchigen Prozess.

Der E-Mail-Traffic sollte in einem langsamen und stetigen Verlauf bereitgestellt werden, der jede Woche verlängert wird, bis die gesamte Liste gesendet wurde. Darüber hinaus folgt jedes Segment dem Zeitplan bis zum Abschluss. Beginn mit den neuesten Abonnenten zuerst und beenden mit den am wenigsten engagierten Abonnenten zuletzt. Bitte beachten Sie auch, dass bestimmte ISPs aufgrund ihres Umgangs mit neuem Traffic möglicherweise einen stärker angepassten Ansatz erfordern.

Weitere Informationen finden Sie unter [Einsatz](/help/engagement.md).

## Kurs beibehalten

Sie sind möglicherweise versucht, den Prozess der IP-Erwärmung zu beschleunigen, indem Sie mehr Volumen senden, als empfohlen wird, und vernachlässigen, Zeit zu verbringen, um Ihre am meisten engagierten Abonnenten zu identifizieren und versäumen, diese Abonnenten zuerst zu schicken, um einen positiven Ruf aufzubauen. Widersetze bitte diesem Drang! Es wird dir langfristig nicht helfen.

Es ist sehr wichtig, dass Beginn Ihre hochengagierten Mitarbeiter per E-Mail versenden. Abonnenten nur für die Anfangsphase der IP-Erwärmung. Diese Kunden sind Ihre wertvollsten und ihre Neigung, Ihre E-Mails zu öffnen, wird helfen, Beginn zeigen, ISPs, dass Sie ein Marketingspezialist sind, der Mails sendet, die interessant und gesucht sind. Er zeigt auch die ISPs an, die Sie nach den Regeln und bewährten Verfahren spielen.

## Zusammenfassung

Denken Sie daran: IP-Erwärmung ist ein Marathon - kein Sprint!  Obwohl der Prozess aufwändig und zeitaufwendig erscheinen mag, wäre es mehr Arbeit, einen Ruf zu reparieren, der durch die Nichtbefolgung bewährter Methoden in der E-Mail beschädigt wurde.

Je besser Ihre Versandmethoden sind und je höher Ihre Reputationswerte bei den ISPs sind, desto wahrscheinlicher ist die Zustellung Ihrer E-Mails. Die IP-Erwärmung und das Hochfahren von IP sowie die Befolgung der Best Practices für das Design Ihres Mailings helfen Ihnen dabei, Ihren Posteingangscode zu optimieren.

Unser weltweites Lieferantenteam ist Ihr Partner in diesem Prozess und hilft Ihnen in dieser IP-Erwärmungsphase, Sie erfolgreich zu positionieren.
