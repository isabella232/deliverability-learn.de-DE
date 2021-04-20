---
title: Infrastruktur
description: 'Erfahren Sie, was zum ordnungsgemäßen Aufbau einer E-Mail-Infrastruktur erforderlich ist. '
feature: Transition Process
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---


# Infrastruktur

Erfolgreiche Lieferbarkeit hängt von einer soliden Grundlage ab. Die E-Mail-Infrastruktur ist ein Kernelement. Eine ordnungsgemäß konstruierte E-Mail-Infrastruktur umfasst mehrere Komponenten, nämlich Domäne(n) und IP-Adresse(n). Diese Komponenten sind wie die Maschine hinter den E-Mails, die Sie senden, und sie sind oft der Anker des Versands Reputation. Berater für die Lieferbarkeit stellen sicher, dass diese Elemente während der Implementierung korrekt eingerichtet werden. Aufgrund des Reputationsfaktors ist es jedoch wichtig, dass Sie über dieses Grundverständnis verfügen.

## Domäneneinrichtung und -strategie {#domain-setup-and-strategy}

Die Zeiten haben sich geändert, und einige ISPs (wie Gmail und Yahoo) beinhalten jetzt den Ruf der Domäne als zusätzlichen Punkt, wenn es darum geht, einem Absender einen Ruf in der E-Mail zuzuordnen. Der Ruf Ihrer Domäne basiert auf Ihrer sendenden Domäne und nicht auf Ihrer IP-Adresse. Das bedeutet, dass Ihre Marke bei der Entscheidung über das ISP-Filtern Vorrang hat.

Zu den Einstiegsprozessen für neue Absender auf Adoben-Plattformen gehören die Einrichtung Ihrer sendenden Domänen und die Sicherstellung der ordnungsgemäßen Einrichtung Ihrer Infrastruktur. Sie sollten mit einem Experten zusammenarbeiten, welche Domänen Sie langfristig verwenden möchten. Im Folgenden finden Sie einige Tipps, die eine gute Domänenstrategie gestalten:

* Achten Sie bei der gewählten Domäne darauf, dass die Marke so klar und reflektiert wird, dass die Benutzer die E-Mail nicht fälschlicherweise als Spam identifizieren. Einige Beispiele sind newsletter.foo.com, receipt.foo.com usw.
* Sie sollten Ihre Mutterdomäne oder Unternehmensdomäne nicht verwenden, da dies den Versand von E-Mails Ihrer Organisation an ISPs beeinträchtigen könnte.
* Erwägen Sie, eine Subdomäne Ihrer übergeordneten Domäne zu verwenden, um Ihre sendende Domäne zu legitimieren.
* Trennen Sie Ihre Subdomänen für Kategorien von Transaktionsnachrichten und Marketingnachrichten. Dies wird Ihnen dabei helfen, den E-Mail-Traffic zuverlässiger zu gestalten, da ISPs nach dieser Versandmethode suchen, die eine bekannte Best Practice für E-Mails ist und dringend empfohlen wird.

## IP-Strategie {#ip-strategy}

Es ist wichtig, eine gut strukturierte IP-Strategie zu entwickeln, um einen positiven Ruf zu schaffen. Die Anzahl der IPs und des Setups hängt von Ihrem Geschäftsmodell und Ihren Marketingzielen ab. Arbeiten Sie mit einem Experten zusammen, um eine klare Strategie zum Beginn zu entwickeln. Betrachten Sie die folgenden Punkte, die wichtig sind:

* **Zu viele Probleme mit dem Ruf von** IPscan-Triggern, da es sich um eine häufige Taktik von Spammer zum  **Schneeschuhen** handelt, eine Taktik, die von Spammer verwendet wird, bei der der Traffic über viele IPs verteilt wird, um den Versand von Spam-Mails zu maximieren. Auch wenn Sie kein Spammer sind, könnten Sie wie ein Spammer aussehen, wenn Sie zu viele IPs verwenden, insbesondere wenn diese IPs zuvor keinen Traffic hatten.
* **Zu wenige** IPscan verursachen Durchsatzprobleme und möglicherweise Probleme mit dem Ruf des Triggers. Der Durchsatz variiert je nach ISP. Wie viel und wie schnell ein ISP akzeptieren will, hängt in der Regel von seiner Infrastruktur und der Entsendung von Reputationsschwellen ab.
* Die Trennung von Traffic für Messaging-Typen ist der Schlüssel. Es ist wichtig, dass die Marketing- und Transaktionspost auf ein Minimum beschränkt werden.
* Abhängig von Ihrer Mail-Strategie kann es ratsam sein, verschiedene Produkte oder Marketingströme auf verschiedene IP-Pools zu trennen, wenn Ihr Ruf deutlich anders ist. Einige Marketingexperten segmentieren auch nach Region. Die Trennung der IP-Adresse für Traffic mit einem geringeren Ruf wird das Reputationsproblem nicht beheben, aber es werden Probleme mit Ihren E-Mail-Versänden mit &quot;gutem Ruf&quot;vermieden. Schließlich wollen Sie Ihre gute Audience nicht für eine riskantere opfern.

## Feedback-Schleifen {#feedback-loops}

Hinter den Kulissen verarbeiten die Adoben Daten zu Absprüngen, Beschwerden, Abmeldungen und mehr. Die Einrichtung dieser Feedback-Schleifen ist ein wichtiger Aspekt für die Lieferbarkeit. Beschwerden können einen Ruf beschädigen, daher sollten Sie E-Mail-Adressen, die Beschwerden von Ihrer Zielgruppe Audience registrieren. Beachten Sie, dass Gmail diese Daten nicht zurückgibt. Listen-Abmeldekopfzeilen und Interaktionsfilterung sind besonders wichtig für Gmail-Abonnenten, die nun die Mehrzahl der Abonnentendatenbanken bilden.

## Authentifizierung {#authentication}

Die Authentifizierung ist der Prozess, mit dem ISPs die Identität eines Absenders überprüfen. Die beiden gebräuchlichsten Authentifizierungsprotokolle sind [!DNL Sender Policy Framework] (SPF) und [!DNL DomainKeys Identified Mail] (DKIM). Diese sind für den Endbenutzer nicht sichtbar, helfen ISPs jedoch, E-Mails von bestätigten Absendern zu filtern. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) gewinnt an Popularität, obwohl seine Richtlinien noch nicht von allen ISPs in ihre Reputationssysteme integriert sind.

### SPF

[!DNL Sender Policy Framework] (SPF) ist eine Authentifizierungsmethode, mit der der Inhaber einer Domäne angeben kann, welche E-Mail-Server er verwendet, um E-Mails von dieser Domäne zu senden.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) ist eine Authentifizierungsmethode, mit der gefälschte Absenderadressen erkannt werden (häufig auch Spoofing genannt). Wenn DKIM aktiviert ist, kann der Empfänger bestätigen, ob der Absender berechtigt ist, E-Mails von dieser Domäne zu senden.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) ist eine Authentifizierungsmethode, die es Domäneninhabern ermöglicht, ihre Domäne vor unbefugter Verwendung zu schützen. DMARC verwendet SPF oder DKIM oder beides, um einem Domäneninhaber zu ermöglichen, zu steuern, was mit E-Mails passiert, bei denen die Authentifizierung fehlschlägt: geliefert, unter Quarantäne gestellt oder abgelehnt.

## Produktspezifische Ressourcen

**Campaign**

* In [diesem Abschnitt ](/help/additional-resources/ac-domain-name-setup.md) erfahren Sie, wie Sie eine Subdomäne vollständig an Adobe Campaign Classic oder Standard delegieren.
* [Systemsteuerung: Vollständige Subdomänenübertragung (Tutorial)](https://experienceleague.corp.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *Erfahren Sie, wie Sie eine Subdomäne vollständig an Adobe Campaign Classic delegieren.*
* [Systemsteuerung: Vollständige Subdomänenübertragung (Tutorial)](https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *Erfahren Sie, wie Sie eine Subdomäne vollständig an Adobe Campaign Standard delegieren.*
* Weitere Informationen zum Implementieren einer Feedback-Schleife für eine Campaign Classic-Instanz finden Sie in [diesem Abschnitt](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Zusätzliche Ressourcen

* Weitere Informationen zu SPF-, DKIM- und DMARC-Authentifizierungsmethoden finden Sie in [diesem Abschnitt](/help/additional-resources/authentication.md).
* Erfahren Sie mehr über die Verbesserung Ihres E-Mail-Rufs durch IP-Erwärmung in [diesem Abschnitt](/help/additional-resources/increase-reputation-with-ip-warming.md).
