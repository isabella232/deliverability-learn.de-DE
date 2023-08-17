---
title: Adressensammlung und Listenwachstum
description: Erfahren Sie, welche Quellen am besten für neue E-Mail-Adressen geeignet sind, wie Sie eine hohe Datenqualität sicherstellen und wie Sie sich an den rechtlichen Richtlinien ausrichten können.
topics: Deliverability
jira: KT-7063
thumbnail: kt7063.jpg
doc-type: article
activity: understand
team: TM
exl-id: 350950dc-4703-402a-8e22-3862f4e21d52
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '1622'
ht-degree: 5%

---

# Adressensammlung und Listenwachstum

Die besten Quellen für neue E-Mail-Adressen sind direkte Quellen wie Anmeldungen auf Ihrer Website oder in physischen Geschäften. In solchen Situationen können Sie das Erlebnis so steuern, dass es positiv ist und der Abonnent daran interessiert ist, E-Mails von Ihrer Marke zu erhalten.

Einige Hinweise zu diesen Anmeldemethoden:

**Physikalischer Laden** Die Listensammlung kann aufgrund verbaler oder schriftlicher Adresseingaben Probleme mit der Rechtschreibung in den Adressen verursachen. Es wird empfohlen, so schnell wie möglich eine Bestätigungs-E-Mail nach der Registrierung im Geschäft zu versenden.

Die am häufigsten verwendete Form von **Website-Anmeldung** ist &quot;Single Opt-in&quot;. Dies ist der absolute Mindeststandard, den Sie zum Erwerb von E-Mail-Adressen verwenden sollten. Eine einmalige Anmeldung ist der Fall, wenn der Inhaber einer bestimmten E-Mail-Adresse einem Absender die Erlaubnis erteilt, ihnen Marketing-E-Mails zu senden, in der Regel durch das Senden der Adresse über ein Webformular oder eine In-Store-Anmeldung. Es ist zwar möglich, eine erfolgreiche E-Mail-Kampagne mit dieser Methode durchzuführen, doch kann dies zu Problemen führen.

* Nicht bestätigte E-Mail-Adressen können Tippfehler aufweisen oder falsch, falsch oder bösartig verwendet werden. Tippfehler und fehlerhafte Adressen verursachen hohe Absprungraten, was zu Bausteinen führen kann, die von ISPs ausgegeben wurden, oder zu IP-Reputationsverlusten.

* Die böswillige Unterwerfung bekannter Spamfallen (manchmal auch als &quot;Listen-Vergiftung&quot;bezeichnet) kann zu enormen Problemen bei der Zustellung und Reputation führen, wenn der Besitzer dieser Falle Maßnahmen ergreift. Es ist unmöglich zu wissen, ob der Empfänger wirklich ohne Bestätigung zu einer Marketingliste hinzugefügt werden möchte. Dies macht es ebenso unmöglich, die Erwartungen des Empfängers zu setzen und kann zu erhöhten Spam-Beschwerden führen - und manchmal auf die Blockierungsliste setzend, wenn die erfasste E-Mail zufällig eine Spamfalle ist.

Eine Anleitung zur Minimierung der Probleme, die sowohl im physischen Speicher als auch in einem einzelnen Opt-in auftreten, finden Sie unter [Datenqualität und -hygiene](#data-quality-and-hygiene) in diesem Handbuch finden Sie Details und Vorteile der Anmeldung mit zweifacher Bestätigung.

>[!NOTE]
>
>Abonnenten verwenden häufig Absenderadressen, abgelaufene Adressen oder Adressen, die nicht ihre sind, um von einer Website zu erhalten, was sie möchten, vermeiden aber auch, dass sie zu Marketinglisten hinzugefügt werden. In diesem Fall führen die Listen von Marketingexperten zu einer hohen Anzahl von Hardbounces, hohen Spam-Beschwerderaten und Abonnenten, die nicht auf E-Mails klicken, diese öffnen oder sich positiv mit ihnen beschäftigen. Sie kann als rote Markierung für Postfachanbieter und ISPs betrachtet werden.

## Anmeldeformulare

Zusätzlich zum Hinzufügen der Felder für die Daten, die Sie über Ihre neuen Abonnenten sammeln möchten, gibt es noch einige andere Dinge, die Sie mit Ihrem Anmeldeformular auf der Website tun sollten.

* Setzen Sie mit dem Abonnenten klare Erwartungen, dass er dem Empfang von E-Mails zustimmt, was er erhält und wie oft er sie erhält.
* Fügen Sie Optionen hinzu, mit denen der Abonnent die Häufigkeit oder die Art der von ihm empfangenen Nachrichten auswählen kann. Mit diesen Optionen können Sie die Voreinstellungen des Abonnenten von Anfang an kennen, sodass Sie Ihrem neuen Kunden das bestmögliche Erlebnis bieten können.
* Ausgleichen des Risikos, das Interesse des Abonnenten während des Anmeldeprozesses zu verlieren, indem so viele Informationen wie möglich verlangt werden. Dinge wie Geburtstag, Standort oder Interessen helfen Ihnen dabei, benutzerspezifischere Inhalte zu versenden. Die Abonnenten jeder Marke haben unterschiedliche Erwartungen und Toleranzschwellen, sodass Tests von entscheidender Bedeutung sind, um das richtige Gleichgewicht für Ihre Situation zu finden.

>[!NOTE]
>
> Verwenden Sie während des Anmeldeprozesses keine vorab aktivierten Kästchen. Dies kann Sie zwar rechtlich in Schwierigkeiten bringen, ist aber auch ein negatives Kundenerlebnis.

## Datenqualität und -hygiene

Das Sammeln von Daten ist nur ein Teil der Herausforderung. Außerdem müssen Sie sicherstellen, dass die Daten sowohl akkurat als auch nutzbar sind. Sie sollten über grundlegende Formatfilter verfügen. Eine E-Mail-Adresse ist ungültig, wenn sie kein &quot;@&quot;oder &quot;.&quot;enthält. zum Beispiel. Lassen Sie keine allgemeinen Alias-Adressen zu, die auch als Rollenkonten bezeichnet werden (z. B. &quot;info&quot;, &quot;admin&quot;, &quot;sales&quot;, &quot;support&quot;). Rollenkonten können ein Risiko darstellen, da der Empfänger naturgemäß eine Personengruppe im Gegensatz zu einem einzelnen Abonnenten enthält. Erwartungen und Toleranz können innerhalb einer Gruppe variieren, wodurch Beschwerden, unterschiedliche Interaktionen, Abmeldungen und allgemeine Verwirrung gefährdet sind.

Im Folgenden finden Sie einige Lösungen für häufige Probleme, die Sie mit Ihren E-Mail-Adressdaten haben:

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] wird von den meisten E-Mail-Experten als Best Practice für die Zustellbarkeit betrachtet. Wenn Sie Probleme mit Spamfallen oder Beschwerden in Ihren Begrüßungs-E-Mails haben, können Sie mit DOI sicherstellen, dass sich der Abonnent, der Ihre E-Mails erhält, für Ihr E-Mail-Programm angemeldet hat und Ihre E-Mails erhalten möchte.

DOI besteht darin, eine Bestätigungs-E-Mail an die E-Mail-Adresse des Abonnenten zu senden, der sich für Ihr E-Mail-Programm angemeldet hat und auf den ein Link geklickt werden muss, um die Zustimmung zu bestätigen. Mit dieser Akquisemethode sendet der Absender keine E-Mails mehr, wenn der Abonnent dies nicht bestätigt. Teilen Sie neuen Abonnenten mit, dass Sie dies auf der Website tun, und ermutigen Sie sie, die Anmeldung abzuschließen, bevor Sie fortfahren. Diese Methode reduziert zwar die Anzahl der Anmeldungen, aber die Personen, die sich anmelden, sind in der Regel sehr engagiert und bleiben langfristig. Dies führt normalerweise zu einem deutlich höheren ROI für den Absender.

**Ausgeblendetes Feld**
Das Anwenden eines ausgeblendeten Felds auf Ihr Anmeldeformular ist eine hervorragende Möglichkeit, automatisierte Bot-Anmeldungen von echten menschlichen Abonnenten zu unterscheiden. Da das Datenfeld nicht sichtbar und im HTML-Code verborgen ist, gibt ein Bot Daten ein, für die ein Mensch dies nicht tun würde. Mit dieser Methode können Sie Regeln erstellen, um alle Anmeldungen zu unterdrücken, die Daten enthalten, die in dieses ausgeblendete Feld eingegeben wurden.

**[!DNL re-CAPTCHA] ist eine Validierungsmethode, mit der Sie die Wahrscheinlichkeit verringern können, dass der Abonnent ein Bot und keine echte Person ist. Es gibt verschiedene Versionen, von denen einige Schlüsselwort-Identifizierung oder Bilder enthalten. Einige Versionen sind effektiver als andere, und was Sie bei der Vermeidung von Sicherheits- und Zustellbarkeitsproblemen gewinnen, ist viel höher als alle negativen Auswirkungen auf Konversionen.

## Rechtliche Leitlinien

Wenden Sie sich an Ihre Anwälte, um lokale und nationale Gesetze bezüglich E-Mail zu interpretieren. Beachten Sie, dass die E-Mail-Gesetze in den verschiedenen Ländern und manchmal in verschiedenen lokalen Regionen eines Landes sehr unterschiedlich sind.

* Achten Sie darauf, die Standortinformationen eines Abonnenten zu sammeln, damit Sie die Landesgesetze des Abonnenten einhalten. Ohne diese Details können Sie sich darauf beschränken, wie Sie an den Abonnenten vermarkten können.
* Alle relevanten Gesetze werden durch den Standort des Empfängers bestimmt, nicht durch den Absender. Sie müssen also die Gesetze für jedes Land kennen und befolgen, in dem Sie einen Abonnenten haben könnten.
* Oft ist es schwierig, mit völliger Sicherheit das Wohnsitzland des Abonnenten zu kennen. Die vom Kunden bereitgestellten Daten können veraltet sein und Pixelstandortdaten können aufgrund von VPN oder Image-Warehouse, wie bei Gmail und Yahoo, ungenau sein. Im Zweifelsfall ist es am sichersten, die strengsten Gesetze und Richtlinien anzuwenden.

## Andere nicht empfohlene Methoden zur Auflistung von Listen

Es gibt viele andere Möglichkeiten, Adressen zu sammeln, jede mit eigenen Chancen, Herausforderungen und Nachteilen. Adobe empfiehlt diese im Allgemeinen nicht, da die Verwendung häufig durch anbieterakzeptable Nutzungsrichtlinien eingeschränkt wird. Wir werden uns einige gebräuchliche Beispiele ansehen, damit Sie die Gefahren lernen können, die Ihnen dabei helfen, die Risiken einzuschränken oder zu vermeiden:

**Liste kaufen oder mieten**
Es gibt viele Arten von E-Mail-Adressen. Primäre E-Mails, Arbeits-E-Mails, E-Mails von Schulen, sekundäre E-Mails und inaktive E-Mails, um einige zu nennen. Bei den Arten von Adressen, die über gekaufte oder gemietete Listen erfasst und weitergegeben werden, handelt es sich selten um primäre E-Mail-Konten, bei denen fast alle Interaktionen und Kaufaktivitäten stattfinden.

Wenn Sie Glück haben, erhalten Sie sekundäre Konten, bei denen Menschen nach Angeboten und Angeboten suchen, wenn sie bereit sind, für etwas einzukaufen. Dies führt in der Regel zu niedrigen Interaktionsraten - wenn überhaupt. Wenn Sie kein Glück haben, ist die Liste voller inaktiver E-Mails, das könnten nun Spamfallen sein. Häufig erhalten Sie eine Mischung aus sekundären und inaktiven E-Mails. Im Allgemeinen schadet die Qualität dieser Listen einem E-Mail-Programm mehr als. Diese Praxis ist durch die [Akzeptierbare Adobe Campaign-Nutzungsrichtlinie](https://www.adobe.com/de/legal/terms/aup.html).

**Listen anhängen**
Dies sind Kunden, die sich entschieden haben, mit Ihrer Marke zu interagieren, was großartig ist. Sie entschieden sich jedoch für eine andere Methode als die E-Mail-Interaktion (im Geschäft, in sozialen Medien usw.). Sie konnten nicht empfänglich sein, eine nicht angeforderte E-Mail von Ihnen zu erhalten, und könnten auch besorgt darüber sein, wie Sie ihre E-Mail-Adresse erhalten haben, da sie sie nicht bereitgestellt haben. Diese Methode birgt das Risiko, einen Kunden oder potenziellen Kunden, der mit Ihrer Marke beschäftigt ist, in einen Kritiker zu verwandeln, der nicht mehr Ihrer Marke vertraut und stattdessen in Ihren Wettbewerb eintritt. Diese Praxis ist durch die [Akzeptierbare Adobe Campaign-Nutzungsrichtlinie](https://www.adobe.com/de/legal/terms/aup.html).

**Messen oder andere Veranstaltungen**
Das Sammeln von Adressen an einem Messestand oder durch eine andere offizielle, eindeutig markierte Methode kann nützlich sein. Das Risiko besteht darin, dass viele Ereignisse wie diese alle Adressen erfassen und über die Ereignisproduzenten oder den Host verteilen. Das bedeutet, dass die Inhaber dieser E-Mail-Adressen nie angefordert haben, E-Mails von Ihrer Marke zu erhalten. Diese Abonnenten beschweren sich wahrscheinlich und markieren Ihre E-Mail als Spam, und sie haben möglicherweise keine genauen Kontaktinformationen bereitgestellt.

**Preisausschreiben**

Preisausschreiben geben schnell eine große Anzahl von E-Mail-Adressen. Aber diese Abonnenten wollen den Preis, nicht Ihre E-Mails. Möglicherweise haben sie nicht einmal den Namen der Personen berücksichtigt, die sie erreichen würden. Sie beschweren sich wahrscheinlich und markieren Ihre E-Mail als Spam, und es ist unwahrscheinlich, dass sie jemals einen Kauf tätigen oder einkaufen.

## Produktspezifische Ressourcen

**Adobe Campaign Classic**

* [Abonnement-Formular mit doppeltem Opt-in erstellen](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=de#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Doppeltes Opt-in-Verfahren](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=de#communication-channels)
