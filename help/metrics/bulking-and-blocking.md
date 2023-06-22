---
title: Bulking und Blockieren von E-Mails
description: Erfahren Sie, warum ISPs E-Mail-Nachrichten in Bulk-Ordnern platzieren oder blockieren.
topics: Deliverability
jira: KT-7051
thumbnail: kt7051.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4b280f90-73b9-4b88-adb8-57b6a46ddad7
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 100%

---

# Bulking und Blockieren

## Bulking

Beim Bulking landen E-Mails bei deren Versand im Spam- oder Junk-Ordner eines ISP. Sie erkennen Bulking daran, dass eine ungewöhnlich niedrige Öffnungsrate (und manchmal auch Klickrate) mit einer hohen Zustellrate einhergeht. Die Ursachen dafür, warum E-Mails in diese Ordner verschoben werden, variieren je nach ISP. Generell gilt jedoch: Wenn Nachrichten im Bulk-Ordner landen, muss ein Merkmal, das die Versandreputation beeinflusst (z. B. Listenhygiene), neu bewertet werden. Bulking ist ein Zeichen dafür, dass die Reputation abnimmt, was ein Problem ist, das sofort behoben werden muss, bevor es weitere Kampagnen beeinträchtigt. Wenden Sie sich an Ihren Adobe-Zustellbarkeitsberater, um eventuelle Probleme mit dem Bulking zu beheben.

## Blockieren

Eine Blockierung tritt auf, wenn Spam-Indikatoren ISP-Schwellen erreichen und der ISP beginnt, E-Mails von einem Absender zu blockieren (erkennbar durch zurückgewiesene Zustellversuche). Es gibt verschiedene Arten von Blockierungen. Im Allgemeinen werden einzelne IP-Adressen blockiert. Blockierungen können aber auch auf der Ebene der sendenden Domain oder Entität auftreten. Das Auflösen einer Blockierung erfordert spezielles Fachwissen. Wenden Sie sich daher an Ihren Adobe-Zustellbarkeitsberater.

## Blockierungsauflistung

Eine Blockierungsauflistung tritt auf, wenn ein Blockierungslistenverwalter eines Drittanbieters ein Spammer-ähnliches Verhalten in Verbindung mit einem Absender feststellt. Der Grund für eine Blockierungsauflistung wird manchmal von der verantwortlichen Partei veröffentlicht. Eine Auflistung basiert in der Regel auf der IP-Adresse, in schwerwiegenderen Fällen kann sie aber auch nach IP-Bereich oder sogar nach einer Absender-Domain erfolgen. Holen Sie sich zur Behebung einer Blockierungsauflistung die Unterstützung Ihres Adobe-Zustellbarkeitsberaters, um die Auflistung vollständig zu beheben und weitere Auflistungen zu verhindern. Einige Auflistungen sind besonders schwerwiegend und können lang anhaltende Reputationsprobleme verursachen, die nur schwer zu beheben sind. Das Ergebnis einer Blockierungsauflistung variiert je nach Blockierungsliste, kann aber möglicherweise die Zustellung aller E-Mails beeinträchtigen.

## Zusätzliche Ressourcen

* Erfahren Sie mehr über [Echtzeit-Blackhole-Listen](/help/additional-resources/blocklist-databases.md), die Datenbanken mit IP-Adressen und Domains verwalten, die oft von Spammern verwendet werden.
