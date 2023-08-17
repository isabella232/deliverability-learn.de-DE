---
title: Duplikate
description: Erfahren Sie, wie Sie Duplikate identifizieren und begrenzen können, um die Zustellbarkeit zu verbessern.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: f89dbb38-a8d4-4294-b017-6fed72591593
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 57%

---

# Duplikate {#duplicates}

Das Vorhandensein doppelter E-Mail-Adressen kann unterschiedliche Konsequenzen haben:

* Dieselbe Nachricht wird mehrmals gesendet. Selbst wenn Adobe vor dem Versand standardmäßig eine Deduplizierung durchführt, können unterschiedliche Aktionen nicht verhindern, dass dieselbe Nachricht gesendet wird, wenn eine Zielgruppe geteilt wird.
* Abmeldungen werden missachtet. Wenn sich ein Empfänger nach dem Erhalt einer Nachricht abmeldet, können an sein dupliziertes Profil weiterhin Nachrichten gesendet werden.

Von der Umgehung des Anmeldeverfahrens abgesehen, führt dies wahrscheinlich dazu, dass Benutzer diese Nachrichten als Spam betrachten und der ISP die Adresse auf die Blockierungsliste setzt.

Bei der Bearbeitung der Datenbank muss besonders vorsichtig vorgegangen werden:

* Importe müssen sorgfältig konfiguriert werden, insbesondere bei der Auswahl des Abstimmschlüssels.
* Geänderte E-Mail-Adressen können ebenfalls eine Quelle von Duplikaten sein. Insbesondere können zwei Adressen mit unterschiedlichen Domänen an dasselbe Postfach weitergeleitet werden, z. B. wenn ein Unternehmen den Namen geändert hat und die frühere Domäne für eine bestimmte Zeit beibehalten hat: joe.doe@amce-co.com und joe.doe@acme-rebranded.com.
* Automatische Importe, ob aus Listen oder aus anderen Datenbanken, sind bei der Profilverwaltung zu berücksichtigende Elemente. Was geschieht, wenn Sie ein Profil löschen oder in eine andere Partition verschieben? Sie kann in der ursprünglichen Partition durch einen automatischen Import neu erstellt werden, z. B. wenn eine Bestellung aufgegeben wird.
* Speichern Sie Profile in unterschiedlichen Ordnern, indem Sie Ansichten anstelle von Partitionen verwenden. Auf diese Weise stellen Sie sicher, dass sich die Profile in derselben physischen Partition befinden und die entsprechenden Berechtigungen angezeigt und verwaltet werden können.

In gewissen Fällen sind Duplikate in unterschiedlichen Partitionen jedoch normal. Bei Sendungen an Drittparteien oder unterschiedliche Abteilungen in einem Unternehmen kann es beispielsweise vorkommen, dass dieselbe Person mehrfache Sendungen mit unterschiedlichem Zweck empfängt. Duplikate innerhalb derselben Partition treten jedoch nur sehr selten auf.

## Produktspezifische Ressourcen

Die Deduplizierung von Adressen schützt Ihre Reputation und gewährleistet eine gute Quarantäneverwaltung. Weitere Informationen finden Sie in den folgenden Abschnitten der Produktdokumentation:

**Adobe Campaign Classic**

* [Aktivität „Deduplizierung“](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Verwenden der Zusammenführungsfunktion der Deduplizierungsaktivität](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html?lang=de#automating-with-workflows)

**Adobe Campaign Standard**

* [Daten einer importierten Datei deduplizieren](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)
