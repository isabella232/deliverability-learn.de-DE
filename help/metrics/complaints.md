---
title: Beschwerden
description: 'Erfahren Sie mehr über Beschwerden, die registriert werden, wenn ein Benutzer angibt, dass eine E-Mail unerwünscht oder unerwartet ist. '
feature: Metriken
topics: Deliverability
kt: 7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 550821608eb7049f739a156536dd31b6b2faa2fa
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---


# Beschwerden

Beschwerden werden registriert, wenn ein Benutzer anzeigt, dass eine E-Mail unerwünscht oder unerwartet ist. Diese Abonnentenaktion wird in der Regel entweder über den E-Mail-Client des Abonnenten protokolliert, wenn er auf die Spam-Schaltfläche klickt, oder über ein Spam-Berichte-System eines Drittanbieters.

## ISP-Beschwerde

Die meisten Tier-1- und einige Tier-2-ISPs bieten ihren Benutzern eine Spam-Berichte-Methode, da Abmelde- und Abmeldeprozesse früher böswillig zur Validierung einer E-Mail-Adresse verwendet wurden. Adobe Campaign erhält diese Beschwerden über ISP FBLs. Dies wird während des Setups für alle ISPs festgelegt, die FBLs bereitstellen und es Adobe Campaign ermöglichen, automatisch E-Mail-Adressen hinzuzufügen, die zur Unterdrückung an die Quarantäne-Tabelle gemeldet wurden. Spitzen bei ISP-Beschwerden können ein Indikator für schlechte Qualität der Liste, weniger als optimale Erfassungsmethoden für Listen oder eine schwache Interaktionsstrategie sein. Sie werden häufig auch dann vermerkt, wenn Inhalte nicht relevant sind.

## Beschwerden von Drittanbietern

Es gibt mehrere Anti-Spam-Gruppen, die Spam-Berichte auf einer breiteren Ebene ermöglichen. Die von diesen Drittanbietern verwendeten Beschwerdemetriken werden verwendet, um E-Mail-Inhalte zur Identifizierung von Spam-E-Mails zu taggen. Dieser Prozess wird auch als Fingerabdruck bezeichnet. Benutzer dieser Drittanbieter-Beschwerdeverfahren sind in der Regel über E-Mails auf dem Laufenden, sodass sie eine größere Wirkung haben können als andere Beschwerden, wenn sie nicht beantwortet werden.

>[!NOTE]
>
>ISPs sammeln Beschwerden und verwenden sie, um den allgemeinen Ruf eines Absenders zu ermitteln. Alle Beschwerden sollten unterdrückt und nicht mehr so schnell wie möglich und gemäß den örtlichen Gesetzen und Vorschriften kontaktiert werden.

## Produktspezifische Ressourcen

**Adobe Campaign Classic**

* [Tracking-Indikatoren](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html#tracking-indicators)

**Adobe Campaign Standard **

* [Beschwerdebericht](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html#reporting)