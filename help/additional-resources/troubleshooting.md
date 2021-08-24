---
title: Behebung von Problemen bei der Zustellbarkeit
description: Erfahren Sie, wie Sie Zustellbarkeitsprobleme identifizieren und beheben können.
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
exl-id: 4cc85124-e7e4-4cd5-99a9-23d2d8cf08fe
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 91%

---

# Behebung von Problemen bei der Zustellbarkeit {#troubleshooting}

Nachstehend finden Sie einige Best Practices, die Ihnen helfen können, Probleme mit der Zustellbarkeit zu erkennen und zu beheben.

## Ein Problem mit der Zustellbarkeit erkennen {#identify-deliverability-issue}

Um ein mögliches Problem zu identifizieren, können die Elemente auf [dieser Seite](/help/ongoing-monitoring.md) Ihre Aufmerksamkeit auf sich lenken.

<!--
Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
Subscriber activity: opens, clicks and/or transactions are lower than usual.
Seed accounts show filtered or non-delivered mailings.
-->

## Mögliche Gründe ermitteln {#potential-causes}

Stellen Sie sich folgende Fragen, um die möglichen Ursachen für Ihr Zustellbarkeitsproblem zu ermitteln:

* Wurde die Listensegmentierung in letzter Zeit geändert?
* Sind neue Datenquellen dazugekommen?
* Habe ich versehentlich eine Datei, die in Quarantäne war, versendet?
* Hängt das Problem eventuell mit meinen Nachrichteninhalten zusammen?
* Sende ich oft genug, um Warming-IPs zu erhalten?
* Segmentiere ich meine Mailings nach Aktivität/Interaktion oder sende ich ganze Dateien?
* Was ist das &quot;sichere&quot; Segment in meiner Datei in Bezug auf Aktualität?
* Verfüge ich über Reaktivierungs- und Wiederbestätigungsstrategien für Segmente, die nicht als sicher definiert sind?

## Problem beheben {#address-issue}

### Beschwerden

[](/help/metrics/complaints.md)Beschwerden werden durch Abonnenten definiert, die E-Mails als Spam melden, indem sie in ihrem Posteingang auf die entsprechende Schaltfläche klicken.

Wenn Ihr Versandproblem durch Beschwerden verursacht wurde:
* Sie müssen versuchen zu ermitteln, warum sich Empfänger beschweren.
* Sie können auch überlegen, den Link zum Abmelden an den Anfang Ihrer E-Mail zu verschieben. So werden Abonnenten dazu ermutigt, sich abzumelden, anstatt sich über die Spam-Schaltfläche zu beschweren.

Absender können aus ihren [Feedback Loop](/help/transition-process/infrastructure.md#feedback-loops) -Beschwerden eine Vielzahl von Daten sammeln:
* Diese Daten sollten erfasst und mit Blick auf Opt-in-Quelle, Länge des Abonnements der Adresse oder auch bestimmte Verhaltensdemografien nach Mustern durchsucht werden.
* Beschwerden weisen vielfach auf eine riskante Datenquelle oder ein riskantes Segment in der Datei hin. &quot;Riskant&quot; wird definiert als die höchste Beschwerdewahrscheinlichkeit, da Beschwerden den Ruf schädigen und so Posteingangsraten beeinträchtigen können.

Beschwerden stammen zum Teil auch von Abonnenten, die einfach keine E-Mails mehr erhalten möchten:
* Das kann an einer zu großen Anzahl von Nachrichten, der Wahrnehmung einer Nachricht durch Ihre Abonnenten oder daran liegen, dass sie die Nachricht nicht erwartet haben bzw. sich nicht mehr an die Anmeldung erinnern können.
* Außerdem sollten Sie eine Prüfung durchführen, um sicherzustellen, dass alle Sammlungspunkte klar und bei Ihren Akquisepunkten keine Kontrollkästchen aktiviert sind.
* Sie sollten auch eine Willkommens-E-Mail senden, wenn Abonnenten sich anmelden, um eine Einführung zu bieten und zu erklären, wie oft sie E-Mails von Ihnen erwarten können.

### Datengültigkeit

**Hardbounces treten auf, wenn Sie bei einem ISP Nachrichten an eine nicht zustellbare Adresse senden.****** Eine Adresse kann aus zahlreichen Gründen unzustellbar sein, z. B.:
* Falsch geschriebene Adresse. Das kann mit einem echtzeitbasierten Datenvalidierungsdienst oder durch Vorschreiben eines Opt-in mit Bestätigung behoben werden, bevor Marketing-E-Mails an diese Adresse gesendet werden.
* Fehlerhafte Liste oder Datenquelle. Wenn die Adresse aus einer neuen Quelle stammt, überprüfen Sie, wie sie erfasst wurde, und stellen Sie sicher, dass die entsprechende Berechtigung erteilt wurde.
* Senden an eine Adresse, die einmal aktiv war, aber nach einer gewissen Phase der Inaktivität geschlossen oder beendet wurde.

### Interaktion

Neben Beschwerden und Datenvalidität konzentrieren sich ISPs bei Versandentscheidungen mehr denn je auf **positive Interaktion**. Sie versuchen herauszufinden, ob Abonnenten Ihre E-Mails öffnen oder aber löschen, ohne sie gelesen zu haben. Da sie diese Daten nicht mit Absendern teilen, müssen wir die verfügbaren Informationen verwenden und Öffnungen/Klicks/Transaktionen als Interaktion übersetzen.

Im Rahmen der laufenden Reputationssicherung ist es wichtig, zu verstehen, wie engagiert Abonnenten auf Ihrer Liste sind, und eine **Aktualitäts-Risikohierarchie** für die Abonnenten in jeder Datei zu erstellen. Neuigkeit wird als letztes Öffnungs-, Klick-, Transaktions- oder Anmeldedatum definiert. Dieser Zeitrahmen kann sich je nach Vertikale unterscheiden. Gehen Sie folgendermaßen vor:

1. Bestimmen Sie für jede Vertikale aktive (&quot;sichere&quot;) Segmente. Das sind typischerweise Abonnenten, die in den letzten drei bis sechs Monaten aktiv waren.
1. Verringern Sie die Häufigkeit bei Inaktiven.
1. Erstellen Sie eine Serie zur [Rückgewinnung](/help/additional-resources/re-engagement.md) für Inaktive mit mittlerem Risiko. In der Regel sind dies Benutzer, die sechs bis neun Monate keine Interaktion gezeigt haben.
1. Entwickeln Sie eine Kampagne zur Wiederbestätigung für Inaktive mit höherem Risiko. Dies sind typischerweise Abonnenten, die seit neun bis zwölf Monaten nicht mehr mit einer E-Mail interagiert haben.
1. Legen Sie abschließend eine Ausschlussregel fest und entfernen Sie alle Abonnenten, die Ihre E-Mails seit &quot;x&quot; Monaten nicht mehr geöffnet haben. Normalerweise empfehlen wir zwölf Monate oder mehr, je nach Umsatz und Kaufzyklus können Sie jedoch einen anderen Wert wählen.
