---
title: Beschwerden
description: 'Erfahren Sie mehr über Beschwerden, die registriert werden, wenn ein Benutzer angibt, dass eine E-Mail unerwünscht ist oder unerwartet gesendet wurde. '
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
ht-degree: 96%

---


# Beschwerden

Beschwerden werden registriert, wenn ein Benutzer angibt, dass eine E-Mail unerwünscht ist oder unerwartet gesendet wurde. Diese Aktion des Abonnenten wird in der Regel entweder über den E-Mail-Client des Abonnenten protokolliert, wenn dieser die Spam-Schaltfläche drückt, oder über das Spam-Reporting-System eines Drittanbieters.

## ISP-Beschwerde

Die meisten Tier-1- und einige Tier-2-ISPs bieten ihren Benutzern eine Spam-Reporting-Methode, da Opt-out- und Abmeldeverfahren in der Vergangenheit in böswilliger Absicht zur Validierung einer E-Mail-Adresse verwendet wurden. Adobe Campaign erhält diese Beschwerden über ISP-FBLs. Dies wird während des Einrichtungsprozesses für alle ISPs festgelegt, die FBLs bereitstellen, und ermöglicht Adobe Campaign, automatisch E-Mail-Adressen, die sich beschwert haben, in die Quarantäne-Tabelle zur Unterdrückung aufzunehmen. Spitzen bei ISP-Beschwerden können ein Indikator für eine schlechte Listenqualität, nicht optimale Listenerfassungsmethoden oder unzureichende Interaktionsrichtlinien sein. Beschwerden werden häufig auch dann vermerkt, wenn Inhalte nicht relevant sind.

## Beschwerden von Drittanbietern

Es gibt mehrere Anti-Spam-Gruppen, die Spam-Reporting auf einer breiteren Ebene ermöglichen. Von diesen Drittanbietern verwendete Beschwerdemetriken werden zum Kennzeichnen von E-Mail-Inhalten verwendet, um Spam-E-Mails zu identifizieren. Dieser Prozess wird auch als Fingerabdruck bezeichnet. Benutzer dieser Beschwerdemethoden von Drittanbietern haben im Allgemeinen mehr Erfahrung mit E-Mails, sodass diese Beschwerden größere Auswirkungen haben können als andere Beschwerden, wenn sie unbeantwortet bleiben.

>[!NOTE]
>
>ISPs sammeln die Beschwerden und verwenden sie, um die allgemeine Reputation eines Absenders zu ermitteln. Alle E-Mail-Adressen mit Beschwerden sollten so schnell wie möglich und in Übereinstimmung mit den lokalen Gesetzen und Vorschriften unterdrückt und nicht mehr kontaktiert werden.

## Produktspezifische Ressourcen

**Adobe Campaign Classic**

* [Tracking-Indikatoren](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html#tracking-indicators)

**Adobe Campaign Standard **

* [Beschwerdebericht](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html?lang=de#reporting)