---
title: Alles über Spam-Fallen
description: Erfahren Sie, wie Sie bei der Verwaltung der Zustellbarkeit Spammfallen erkennen und vermeiden können.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 3696ec013014ea41c634ac4829ec40977d224ff1
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---


# Alles über Spam-Fallen

Eine [Spam-Falle](/help/metrics/spam-traps.md) ist eine gültige Adresse ohne Fehlermeldung, wenn E-Mails an gesendet werden. Eine Spam-Falle hat eine Hauptaufgabe: Spammer oder Absender ohne Datenhygiene identifizieren.

## Wer verwaltet diese Adressen für Spam-Traps?

Der erste Typ von Spam-Trap-Adressen ist die IP und Domain Blockierungsliste Firma wie SpamHaus, Sorbs, SpamCop. Diese Firmen haben ein riesiges Netzwerk von Adressen, die auf verschiedenen Internetseiten versendet werden, wie Website, Blog, Foren, sodass ihre Adressen von Spammer gesammelt werden.

Der zweite Typ von Spam-Trap basiert auf alten aktiven ISP-Adressen. Diese ISPs verfügen über ein eigenes Spam-Trap-Netzwerk, das auf inaktiven Adressen basiert, die in Trap umgerechnet werden und die IP und den Ruf der Domäne beeinträchtigen.

## Funktionsweise

**Eine E-Mail-Adresse ohne Endbenutzer**: Diese Adressen haben und werden nie einen Endbenutzer haben, der sich bei Newslettern oder anderen Kommunikationsformen registrieren kann.

**Eine von einem Benutzer** abgebrochene E-Mail-Adresse: Nach einer Inaktivität werden Adressen von den ISPs deaktiviert. Absprünge werden an Absender gesendet, um sie über diesen neuen Status zu informieren. Die Absender müssen diese Adressen in Quarantäne setzen oder sie aus der zukünftigen Kommunikation entfernen. ISPs verwenden diese Adressen, die in &quot;Spam-Falle&quot;umgewandelt werden, um Absender mit schlechten Praktiken zu überwachen.

## Wie erkennt man eine Spam-Falle?

Es ist eine schwierige Aufgabe, Spam-Fallen zu identifizieren, müssen diese Adressen anonym bleiben, da sie zur Identifizierung schlechter Absender verwendet werden. Die meisten ISPs verfügen nicht über ein offenes Klicksystem, um fehlerhafte Absendertreffer zu überwachen. Nach vorherigen Definitionen ist es möglich, einen Pod mit verdächtigen Adressen zu bestimmen und die Effizienz der Pod-Auswahl zu testen.

## Warum ist Ihre Datenbank mit Spam-Fallen infiziert?

Ihre Datenbank mit E-Mail-Adressen enthält Spam-Trap, wie könnte es möglich sein? Die beiden Hauptgründe sind ein Mangel an Hygiene in der Datenbank oder das Sammeln von Funktionsstörungen.

Diese wenigen Punkte helfen Ihnen dabei, Ihre Prozesse zu überprüfen:

* Funktionsstörung erfassen:
   * Woher kommen Ihre E-Mail-Adressen? Wie viele Quellen werden zur Erfassung dieser Adressen verwendet? Können Sie sie identifizieren? Interne/koregistrierung?
   * Funktioniert Ihr Opt-in-System ordnungsgemäß?
   * Haben Sie die Domänen und den Alias Ihrer Adressen überprüft? Tun Sie es mit der Tabelle unten!
* Datenbankhygiene:
   * Wie sieht Ihr Verfahren bezüglich der inaktiven Adresse der letzten 12 Monate aus?
   * Verarbeiten Sie eine Quarantäne auf Soft Bounces als &quot;Inaktiver Benutzer&quot;?
   * Wann kümmert du dich das letzte Mal um deine Datenbank und versuchst sie zu bereinigen? Mach es regelmäßig.

## Alias und Domänen zur Vermeidung

**Aliase**

![](../../help/assets/aliases.png)

**Domänen**

![](../../help/assets/domains.png)