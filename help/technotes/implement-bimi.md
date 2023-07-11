---
title: Implementieren von Gmail's Brand Indicators for Message Identification (BIMI)
description: Erfahren Sie, wie Sie BIMI implementieren
topics: Deliverability
role: Admin
level: Beginner
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '1064'
ht-degree: 0%

---

# Implementierung [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) ist ein Branchenstandard, der es ermöglicht, in teilnehmenden Plattformen neben der E-Mail eines Absenders ein genehmigtes Logo anzuzeigen.

Mit diesem Standard kann eine Marke ein Logo bestimmen, das in den Postfächern der Postfächer angezeigt werden soll. Nach der Veröffentlichung in einem so genannten BIMI DNS (Domain Name System)-Datensatz kann ein Postfachanbieter dieses Logo abrufen und im Posteingang anzeigen, wenn bestimmte Kriterien erfüllt sind.

Verschiedene Anbieter führen unterschiedliche Implementierungen durch, doch die Vorteile sind klar: im Posteingang ausstehen, Vertrauen aufbauen und die Kontrolle darüber haben, was gezeigt wird.

BIMI verbessert nicht direkt die Zustellbarkeit oder Ihre Reputation. Dies kann dazu beitragen, mehr Vertrauen in Ihre Empfänger zu schaffen und so die Interaktion zu steigern.

## Wie sieht es aus?

Beispiele für Implementierungen von verschiedenen Anbietern und weitere Details dazu, welche Anbieter das Logo auf der [Seite der BIMI-Gruppe](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## Wer ist die BIMI-Gruppe?

Die BIMI-Gruppe ist eine Arbeitsgruppe, die BIMI entwickelt, da sie nicht nur das Logo, sondern auch die technischen, rechtlichen und Compliance-Anforderungen abdeckt.

Die BIMI-Gruppe besteht aus mehreren Akteuren aus verschiedenen Branchen: Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail und Gültigkeit.

## Wer unterstützt BIMI?

Die Liste der Postfachanbieter, die BIMI unterstützen, wächst stetig. Eine aktuelle Liste finden Sie [here](https://bimigroup.org/bimi-infographic/){target="_blank"} sowohl für unterstützende Anbieter als auch für Anbieter, die BIMI in Erwägung ziehen.

Seit April 2023 enthält die Liste Gmail, Yahoo, La Poste, Fastmail, Onet.pl und Zone, Proofpoint als Anti-Spam-Gerät und Apple Mail (ab iOS 16).

Die bekanntesten Namen auf dieser Liste sind offensichtlich Yahoo, Gmail und ein aktueller Anwender: Apple mit iOS 16. Apple spielt eine besondere Rolle in diesem Mix, da es kein Postfachanbieter ist, doch hat es BIMI-Unterstützung zu seiner nativen E-Mail-App hinzugefügt. E-Mails, die mit BIMI konform sind, werden als &quot;digital zertifizierte E-Mail&quot;angezeigt, was das Vertrauen in die Marke stärkt.

## Implementierung

Die Implementierung von BIMI erfolgt in mehreren Schritten:

1. Implementierung von DMARC (Domain based Message Authentication, Reporting and Conformance) auf Durchsetzungsebene für die sendende Domain und deren Organisationsdomäne - [Weitere Infos](#dmarc)

1. Erstellung Ihres Markenlogos im Format SVG TinyPS - [Weitere Infos](#create-brand-logo)

1. Anmeldung für ein Verified Mark Certificate (nur bei einigen Providern erforderlich) - [Weitere Infos](#vmc)

1. Veröffentlichen Sie einen BIMI-DNS-Eintrag mit dem Logo und dem Zertifikat - [Weitere Infos](#publish-bimi-record)

1. Ein guter Ruf - [Weitere Infos](#good-reputation)

>[!NOTE]
>
>Beachten Sie, dass alle Schritte ausgecheckt werden müssen.


### DMARC {#dmarc}

DMARC ist ein Standard, der es der Marke ermöglicht zu entscheiden, was ein Postfachanbieter mit einer E-Mail tun soll, die fehlschlägt [Authentifizierung](../additional-resources/authentication.md). Die so genannten Richtlinien reichen von &quot;Keine&quot; über &quot;Quarantäne&quot;(Platzierung von Spam-Ordnern) bis &quot;Zurückweisen&quot;(Blockieren der E-Mail). Nur die beiden letztgenannten Richtlinien werden als &quot;Durchsetzung&quot;bezeichnet und sind für BIMI qualifiziert. Durch Adobe gesendete Nachrichten übergeben die Authentifizierung, da SPF (Sender Policy Framework) und DKIM (Domain Keys Identified Mail) standardmäßig eingerichtet sind. Adobe richtet DMARC auf Anfrage für Ihre Versanddomäne ein.

Zusätzlich zu DMARC in der Versanddomäne muss DMARC auch auf der Durchsetzungsebene für die Organisationsdomäne verwendet werden (wenn die sendende Domäne news.example.com ist, ist example.com die Organisationsdomäne).

### Erstellung des Markenlogos {#create-brand-logo}

Die Erstellung des Logos muss den Anforderungen von 100 % entsprechen. Beachten Sie immer die Informationen unter [Richtlinien der BIMI-Gruppe](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

Neben den technischen Anforderungen gibt es einige praktische Empfehlungen wie ein quadratisches Logo, eine solide Farbe als Hintergrund und andere. Diese Empfehlungen dienen der optimalen Visualisierung.
Beachten Sie bitte, dass die Nichteinhaltung dazu führen kann, dass das Logo nicht angezeigt wird.

### Überprüftes Mark-Zertifikat (VMC) {#vmc}

Ein Verified Mark Certificate (VMC) ist nur für einige Postfachanbieter wie Gmail und Apple erforderlich und ist daher optional. Wir empfehlen, einen VMC zu erhalten, um BIMI wirklich zu nutzen.

Ein Verified Mark Certificate ist eine gültige Bestätigung dafür, dass die Marke das Logo verwenden kann. Eine Zertifizierungsstelle prüft dies über die Markenbehörde, bei der das Markenlogo registriert ist. Dieser Prozess umfasst mehrere Validierungen und Prüfungen, die einige Zeit in Anspruch nehmen können. Derzeit stellen zwei Zertifizierungsstellen (Zertifizierungsstellen) VMC aus: Digicert und Entrust. Die ersten Markenbüros sind die USA, Kanada, die EU, Großbritannien, Deutschland, Japan, Australien und Spanien.

In der Regel benötigen Sie einen VMC pro Logo. Eine VMC für Ihre Organisationsdomäne deckt Unterdomänen ab und verfügt über eine zusätzliche Funktion auch für verschiedene Domänen. Falls Sie unterschiedliche Logos haben, benötigen Sie mehr als einen VMC. Die Zertifizierungsstelle oder der Partner, mit dem Sie zusammenarbeiten, hilft Ihnen bei der Einrichtung.

>[!NOTE]
>
>Beachten Sie, dass VMCs eine jährliche Gebühr haben.

### BIMI-Datensatz veröffentlichen {#publish-bimi-record}

Sobald die anderen Schritte abgeschlossen sind, kann der BIMI DNS-Eintrag veröffentlicht werden. Der Datensatz sieht wie folgt aus:

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;PEM-URL&quot;ist der Dateispeicherort des Verified Mark Certificate.

Für Ihre Versanddomäne muss dies nach Adobe erfolgen.

### Gute Reputation {#good-reputation}

Vertrauen ist der Schlüssel zu BIMI. Der Benutzer vertraut seinem Postfachanbieter, dass er das Logo nur für rechtmäßige Absender anzeigt, sodass der Postfachanbieter der Marke vertrauen muss. Dies geschieht durch Ihre Reputation als Absender. Wenn Sie einen hohen Ruf haben, ist alles gut, aber wenn Sie es nicht sind, wird das Logo nicht angezeigt. Leider gibt es keine Informationen oder Metriken, mit denen wir herausfinden können, ob die Reputation hoch genug ist.

Selbst wenn man den Aufwand und die Kosten für einen VMC durchläuft, nimmt man diesen Teil nicht weg. Wenn der Postfachanbieter der Marke nicht vertraut, wird das Logo nicht angezeigt.

## Tipps und Tricks

* Die BIMI Gruppe bietet ein praktisches Validierungstool für BIMI. Wenn Sie überprüfen möchten, ob alles eingerichtet und fertig ist, oder nur prüfen möchten, ob das Logo kompatibel ist, gehen Sie zu [dieser Link](https://bimigroup.org/bimi-generator/){target="_blank"}. Klicken Sie für Letztere einfach auf **[!UICONTROL BIMI generieren]** und geben Sie eine Platzhalterdomäne ein, aber die richtige Logo-URL. Der Inspektor wird Ihnen mitteilen, ob das Logo konform ist.

* Sie können sicher ohne VMC starten, es gibt keinen Schaden für Ihre Reputation, wenn Ihr BIMI-Datensatz keine VMC-URL enthält, aber das Logo kann bereits in Yahoo angezeigt werden.

* Die organisatorische Umsetzung von DMARC ist ein großes Unternehmen. Einige Unternehmen sind spezialisiert, um Marken bei der vollständigen Einführung von DMARC zu helfen.

* Eine umfassende Liste häufig gestellter Fragen wird veröffentlicht [here](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
