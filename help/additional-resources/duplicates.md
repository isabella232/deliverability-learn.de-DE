---
title: Duplikate
description: Erfahren Sie, wie Sie Duplikat identifizieren und beschränken, um die Zustellbarkeit zu verbessern.
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
source-wordcount: '388'
ht-degree: 54%

---


# Duplikate {#duplicates}

Das Vorhandensein doppelter E-Mail-Adressen kann unterschiedliche Konsequenzen haben:

* Die gleiche Nachricht wird mehrmals gesendet. Auch wenn Adobe vor dem Senden standardmäßig eine Deduplizierung-Duplikate-Prozedur durchführt, kann nicht verhindert werden, dass dieselbe Nachricht von verschiedenen Aktionen gesendet wird, die denselben Inhalt haben, wenn eine Zielgruppe geteilt wird.
* Abmeldungen werden missachtet. Wenn sich ein Empfänger nach dem Erhalt einer Nachricht abmeldet, können an sein dupliziertes Profil weiterhin Nachrichten gesendet werden.

Von der Umgehung des Anmeldeverfahrens abgesehen, führt dies wahrscheinlich dazu, dass Benutzer diese Nachrichten als Spam betrachten und der ISP die Adresse auf die Blockierungsliste setzt.

Bei der Bearbeitung der Datenbank muss besonders vorsichtig vorgegangen werden:

* Importe müssen sorgfältig konfiguriert werden, insbesondere bei der Auswahl des Abstimmschlüssels.
* Geänderte E-Mail-Adressen können auch eine Quelle von Duplikaten sein. Insbesondere können zwei Adressen mit verschiedenen Domänen an denselben Posteingang weitergeleitet werden, z. B. wenn eine Firma den Namen geändert hat und die ursprüngliche Domäne eine bestimmte Zeit lang beibehalten hat: joe.doe@amce-co.com und joe.doe@acme-rebranded.com.
* Automatische Einfuhren von Listen oder aus anderen Datenbanken sind bei der Verwaltung von Profilen zu berücksichtigen. Was geschieht, wenn Sie ein Profil löschen oder in eine andere Partition verschieben? Sie kann in der ursprünglichen Partition durch einen automatischen Import neu erstellt werden, z. B. wenn eine Bestellung aufgegeben wird.
* Speichern Sie Profile in unterschiedlichen Ordnern, indem Sie Ansichten anstelle von Partitionen verwenden. Auf diese Weise stellen Sie sicher, dass sich die Profile in derselben physischen Partition befinden und die entsprechenden Berechtigungen angezeigt und verwaltet werden können.

In gewissen Fällen sind Duplikate in unterschiedlichen Partitionen jedoch normal. Bei Sendungen an Drittparteien oder unterschiedliche Abteilungen in einem Unternehmen kann es beispielsweise vorkommen, dass dieselbe Person mehrfache Sendungen mit unterschiedlichem Zweck empfängt. Duplikate innerhalb derselben Partition treten jedoch nur sehr selten auf.

## Produktspezifische Ressourcen

Die Deduplizierung von Adressen schützt Ihre Reputation und gewährleistet eine gute Quarantäneverwaltung. Weitere Informationen finden Sie in den folgenden Abschnitten der Produktdokumentation:

**Adobe Campaign Classic**

* [Aktivität „Deduplizierung“](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Verwenden der Funktion &quot;Zusammenführen&quot;der Deduplizierung-Duplikate-Aktivität](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html)

**Adobe Campaign Standard **

* [Daten einer importierten Datei deduplizieren](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)