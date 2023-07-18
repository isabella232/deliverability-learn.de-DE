---
title: Infrastruktur
description: Erfahren Sie, was für den Aufbau einer E-Mail-Infrastruktur erforderlich ist.
topics: Deliverability
jira: KT-7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
role: Admin, Leader
level: Beginner
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 2%

---

# Infrastruktur

Erfolgreiche Zustellbarkeit hängt von einer soliden Grundlage ab. E-Mail-Infrastruktur ist ein Kernelement. Eine ordnungsgemäß konstruierte E-Mail-Infrastruktur umfasst mehrere Komponenten, nämlich Domäne(n) und IP-Adresse(n). Diese Komponenten sind wie die Maschinen hinter den E-Mails, die Sie senden, und oft sind sie der Anker der Reputation. Berater für Zustellbarkeit sorgen dafür, dass diese Elemente während der Implementierung ordnungsgemäß eingerichtet werden. Aufgrund des Reputationselements ist es jedoch wichtig, dass Sie über diese grundlegenden Kenntnisse verfügen.

## Domain-Einrichtung und -Strategie {#domain-setup-and-strategy}

Die Zeiten haben sich geändert, und einige ISPs (wie Gmail und Yahoo) beinhalten jetzt die Domain-Reputation als zusätzlichen Punkt, wenn es darum geht, einem Absender die E-Mail-Reputation zuzuordnen. Ihre Domain-Reputation basiert auf Ihrer sendenden Domain und nicht auf Ihrer IP-Adresse. Das bedeutet, dass Ihre Marke bei der Filterung von ISP Vorrang hat.

Zu den Onboarding-Prozessen für neue Absender auf Adobe-Plattformen gehören die Einrichtung Ihrer Versanddomänen und die Sicherstellung der ordnungsgemäßen Einrichtung Ihrer Infrastruktur. Arbeiten Sie mit einem Experten zusammen, um zu erfahren, welche Domänen Sie langfristig verwenden möchten. Im Folgenden finden Sie einige Tipps, die eine gute Domain-Strategie gestalten:

* Halten Sie die Marke möglichst klar und reflektieren Sie sie mit der von Ihnen gewählten Domain, damit die Benutzer die E-Mail nicht fälschlicherweise als Spam identifizieren. Beispiele sind newsletter.foo.com, receipts.foo.com usw.
* Sie sollten Ihre übergeordnete oder Unternehmensdomäne nicht verwenden, da dies die Zustellung von E-Mails von Ihrem Unternehmen an ISPs beeinträchtigen könnte.
* Erwägen Sie die Verwendung einer Subdomain Ihrer übergeordneten Domäne, um Ihre sendende Domäne zu legitimieren.
* Trennen Sie Ihre Subdomains für die Kategorien von Transaktionsnachrichten und Marketingnachrichten. Dies hilft Ihrem E-Mail-Traffic auf einer zuverlässigeren Grundlage, da ISPs nach dieser Versandmethode suchen, die eine bekannte Best Practice für E-Mails ist und dringend empfohlen wird.

## IP-Strategie {#ip-strategy}

Es ist wichtig, eine gut strukturierte IP-Strategie zu entwickeln, um zu einem positiven Ruf beizutragen. Die Anzahl der IPs und der Einrichtung variiert je nach Geschäftsmodell und Marketing-Zielen. Arbeiten Sie mit einem Experten zusammen, um eine klare Strategie zu entwickeln, die richtig funktioniert. Beachten Sie die folgenden Punkte, die wichtig sind:

* **Zu viele IPs** kann Reputationsprobleme von Triggern verursachen, da dies eine häufige Taktik für Spammer ist **Schneeschuh**, eine Taktik, die von Spammern verwendet wird, bei der der Traffic über viele IPs verteilt ist, um den Versand von Spam-Mails zu maximieren. Obwohl Sie kein Spammer sind, könnten Sie wie einer aussehen, wenn Sie zu viele IPs verwenden, insbesondere wenn diese IPs zuvor keinen Traffic hatten.
* **Zu wenige IPs** kann Durchsatzprobleme und möglicherweise Probleme mit der Reputation von Triggern verursachen. Der Durchsatz variiert je nach ISP. Wie viel und wie schnell ein ISP akzeptieren will, hängt normalerweise von seiner Infrastruktur ab und sendet Reputationsschwellen.
* Die Trennung von Traffic für Nachrichtentypen ist entscheidend. Es ist wichtig, Marketing- und Transaktionsnachrichten mindestens auf separate IP-Pools zu trennen.
* Abhängig von Ihrer E-Mail-Strategie kann es auch ratsam sein, verschiedene Produkte oder Marketing-Streams von verschiedenen IP-Pools zu trennen, wenn sich Ihre Reputation stark unterscheidet. Einige Marketing-Experten segmentieren auch nach Region. Wenn Sie die IP-Adresse auf Traffic mit einer geringeren Reputation aufteilen, wird das Reputationsproblem nicht behoben, aber es werden Probleme mit Ihren E-Mail-Sendungen zur &quot;guten Reputation&quot;verhindert. Schließlich wollen Sie Ihr gutes Publikum nicht für ein riskanteres opfern.

## Feedback-Schleifen {#feedback-loops}

Hinter den Kulissen verarbeiten Adobe-Plattformen Daten zu Absprüngen, Beschwerden, Abmeldungen und mehr. Die Einrichtung dieser Feedback-Schleifen ist ein wichtiger Aspekt der Zustellbarkeit. Beschwerden können die Reputation schädigen. Daher sollten Sie E-Mail-Adressen verwenden, die Beschwerden von Ihrer Zielgruppe registrieren. Es ist wichtig zu beachten, dass Gmail diese Daten nicht zurückgibt. Header zum Abmelden von Listen und Interaktionsfilterung sind besonders für Gmail-Abonnenten wichtig, die jetzt die meisten Abonnenten-Datenbanken umfassen.

## Authentifizierung {#authentication}

Authentifizierung ist der Prozess, den ISPs zur Validierung der Identität eines Absenders verwenden. Die beiden häufigsten Authentifizierungsprotokolle sind [!DNL Sender Policy Framework] (SPF) und [!DNL DomainKeys Identified Mail] (DKIM). Diese sind für den Endbenutzer nicht sichtbar, helfen ISPs jedoch beim Filtern von E-Mails von verifizierten Absendern. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) gewinnt an Beliebtheit, obwohl seine Richtlinien noch nicht von allen ISPs in ihre Reputationssysteme integriert wurden.

### SPF

[!DNL Sender Policy Framework] (SPF) ist eine Authentifizierungsmethode, mit der der Eigentümer einer Domain angeben kann, welche E-Mail-Server zum Senden von E-Mails von dieser Domain verwendet werden.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) ist eine Authentifizierungsmethode, mit der gefälschte Absenderadressen erkannt werden (häufig als &quot;Spoofing&quot;bezeichnet). Wenn DKIM aktiviert ist, kann der Empfänger bestätigen, ob der Absender berechtigt ist, E-Mails von dieser Domain zu senden.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) ist eine Authentifizierungsmethode, die es Domain-Eigentümern ermöglicht, ihre Domain vor unbefugter Verwendung zu schützen. DMARC verwendet SPF oder DKIM oder beides, um einem Domäneninhaber zu ermöglichen, zu steuern, was mit E-Mails mit fehlerhafter Authentifizierung passiert: zugestellt, unter Quarantäne gestellt oder abgelehnt.

## Produktspezifische Ressourcen

**Campaign**

* Erfahren Sie, wie Sie eine Subdomain vollständig Adobe Campaign Classic oder Standard zuweisen. [diesem Abschnitt](/help/additional-resources/ac-domain-name-setup.md).
* [Control Panel: Vollständige Zuweisung von Subdomains (Tutorial)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Erfahren Sie, wie Sie eine Subdomain vollständig Adobe Campaign Classic zuweisen.*
* [Control Panel: Vollständige Zuweisung von Subdomains (Tutorial)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Erfahren Sie, wie Sie eine Subdomain vollständig Adobe Campaign Standard zuweisen.*
* Erfahren Sie mehr über die Implementierung einer Feedback-Schleife für eine Campaign Classic-Instanz in [diesem Abschnitt](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Zusätzliche Ressourcen

* Weitere Informationen zu SPF-, DKIM- und DMARC-Authentifizierungsmethoden finden Sie in [diesem Abschnitt](/help/additional-resources/authentication.md).
* Erfahren Sie mehr über die Verbesserung der Reputation Ihrer E-Mail mit IP-Warming in [diesem Abschnitt](/help/additional-resources/increase-reputation-with-ip-warming.md).
