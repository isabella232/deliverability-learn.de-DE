---
title: Leitlinien für die angekündigten Änderungen unter [!DNL Google] und [!DNL Yahoo]
description: Leitlinien für die angekündigten Änderungen unter [!DNL Google] und [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06T00:00:00Z
jira: KT-14320
thumbnail: KT-14320.jpeg
source-git-commit: 00b4b4c3396fc4a71484cd12e8c89cd8371ad1ce
workflow-type: tm+mt
source-wordcount: '1297'
ht-degree: 0%

---


# Leitlinien für die angekündigten Änderungen unter [!DNL Google] und [!DNL Yahoo]

Am 3. Oktober [!DNL Google] und [!DNL Yahoo] gemeinsam angekündigte Änderungen über ihre Blogs. Diese Änderungen sollen die Sicherheit der Benutzer erhöhen und ein besseres E-Mail-Erlebnis bieten, indem einige gängige Best Practices der Branche ab Februar 2024 als neue Anforderungen durchgesetzt werden.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] Mitteilung](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] Mitteilung](/help/assets/Yahoo.png)

Die E-Mail-Zustellbarkeits-Experten von Adobe haben diese Blog-Posts und alle damit verbundenen Dokumentationen durchgelesen, sodass Sie nicht dazu gezwungen sind. Hier sind die wichtigsten Schritte.

## Was genau sind [!DNL Google] und [!DNL Yahoo] tun?

In der E-Mail-Welt gibt es rechtliche Anforderungen, praktische Anforderungen und allgemeine Best Practices. Die rechtlichen Anforderungen sind von Ort zu Ort sehr unterschiedlich und nicht Teil dieses Themas. stattdessen [!DNL Google] und [!DNL Yahoo] bewährte Verfahren übernehmen und in praktische Anforderungen umsetzen. Keine der Elemente [!DNL Google] und [!DNL Yahoo] werden im Februar neue Anforderungen stellen, die häufig seit Jahren Empfehlungen für bewährte Verfahren enthalten, aber die Umsetzung ist in der Branche langsam und uneinheitlich. Dies ist [!DNL Google] und [!DNL Yahoo]Wir helfen Ihnen dabei, diesen Adoptionsvorgang voranzubringen, indem Sie sagen: &quot;Wenn Sie E-Mails für unsere Benutzer bereitstellen möchten (dies kann einen erheblichen Anteil Ihrer E-Mail-Liste ausmachen, in einigen Fällen sogar bis zu 70 %, je nach Region und Branche), müssen Sie diese Schritte durchführen.&quot;

## Welche Details gibt es?

Wenn Sie Adobe-Kunde sind, ist der Großteil des Bedarfs bereits Teil Ihrer Einrichtung, es gibt jedoch einige wichtige Elemente, die technisch optional sind. Sie werden sicher sein können, dass Ihr Unternehmen diese Artikel vor Februar 2024 korrekt angenommen und eingerichtet hat.

## DMARC:

[!DNL Google] und [!DNL Yahoo] Sie benötigen beide einen DMARC-Datensatz für jede Domäne, mit der Sie E-Mails an sie senden. Sie erfordern derzeit NICHT die Einstellung p=reject oder p=quarantine . Daher ist eine Einstellung von p=none, die häufig als &quot;Monitoring&quot;-Einstellung bezeichnet wird, vollkommen akzeptabel. Dies wirkt sich nicht darauf aus, wie Ihre E-Mails verarbeitet werden. Sie tun das, was sie normalerweise ohne DMARC tun würden. Die Einrichtung ist der erste Schritt, um sich mit DMARC zu schützen und zusätzlich zu dem neuen Vorteil, dass Sie E-Mails an senden können. [!DNL Google] und [!DNL Yahoo] Es kann Ihnen auch dabei helfen festzustellen, ob es Authentifizierungsprobleme innerhalb Ihres E-Mail-Ökosystems gibt.
DMARC wird derzeit vollständig unter Adobe unterstützt, ist jedoch nicht erforderlich. Verwenden Sie einen kostenlosen DMARC-Checker, um zu sehen, ob Sie DMARC für Ihre Subdomains eingerichtet haben, und falls Sie dies nicht tun, wenden Sie sich an Ihr Adobe-Supportteam, um zu erfahren, wie Sie am besten mit der Einrichtung umgehen können. Weitere Informationen zu DMARC und dessen Implementierung finden Sie hier . [here](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=de){target="_blank"} for Adobe Campaign and Adobe Journey Optimizer Adobe or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html){target="_blank"} für Marketo Engage.

## 1-Klick (Liste) Abmeldung:

Keine Panik! [!DNL Google] und [!DNL Yahoo] Es handelt sich nicht um Abmelde-Links in Ihrem E-Mail-Body oder Ihrer Fußzeile, auf die ein Sicherheitsbot, der nur seine Arbeit erledigt, oder zufällig geklickt hat. Sie bedeuten die List-Unsubscribe-Header-Funktionalität für die &quot;mailto&quot;- oder &quot;http/URL&quot;-Versionen. Dies ist die Funktion innerhalb der [!DNL Yahoo] und Gmail-Benutzeroberflächen, auf die Benutzer klicken können, um sich abzumelden. Gmail fordert Benutzer, die auf &quot;Spam melden&quot;klicken, sogar dazu auf zu sehen, ob sie sich stattdessen abmelden möchten. Dies kann die Anzahl der Beschwerden verringern, die Sie erhalten (Beschwerden verletzen Ihre Reputation), indem sie stattdessen in Abmeldungen umgewandelt werden (was Ihrer Reputation nicht schadet).
Es ist wichtig festzustellen, dass [!DNL Google] und [!DNL Yahoo] beziehen sich beide auf die Option &quot;http/URL&quot;mit dem Namen &quot;1-Click&quot;, und dies ist beabsichtigt. Technisch gesehen haben Sie mit der ursprünglichen Option &quot;http/URL&quot;die Möglichkeit, Empfänger auf eine Website umzuleiten. Das ist nicht der Schwerpunkt [!DNL Yahoo] und [!DNL Google], die beide auf die aktualisierte RFC8058 verweisen, die sich auf die Verarbeitung der Abmeldung über eine HTTPS-POST-Anfrage anstelle einer Website konzentriert, wodurch sie &quot;1-Klick&quot;ergibt.
Für Marketo Engage hat Adobe bereits die Option &quot;mailto&quot; aktiviert und unterstützt derzeit nicht die Option &quot;http/URL&quot;. Weitere Aktualisierungen hierzu werden folgen.
Für Adobe Campaign und Adobe Journey Optimizer Adobe empfiehlt die Verwendung von &quot;mailto&quot;- und &quot;1-Click&quot;-Optionen.
Weitere Informationen zur Implementierung von list-unsubscribe finden Sie hier für Adobe Campaign Classic, hier für Adobe Campaign Standard und hier für Adobe Journey Optimizer, oder wenden Sie sich jederzeit an das Adobe-Support-Team.
Die Notwendigkeit von Headern zum Abmelden von Listen gilt nicht für Transaktionsnachrichten. Bitte beachten Sie, dass ausgelöste Nachrichten wie &quot;Warenkorb abgebrochen&quot;und ähnliche vom Abonnenten nicht generierte Nachrichten als Marketing durch Postfachanbieter wie [!DNL Google] und [!DNL Yahoo] und diese müssen sich von der Liste abmelden.

## Prozess-Abmeldungen innerhalb von 2 Tagen:

Dies ist seit einiger Zeit eine empfohlene Best Practice, da jede E-Mail, die Sie an eine Person senden, die sich abgemeldet hat, in der Regel zu einer Spam-Beschwerde führt. Je früher Sie diese E-Mails nicht mehr senden, desto besser. Auch hier können die rechtlichen Anforderungen in einigen Fällen viel länger sein, aber [!DNL Google] und [!DNL Yahoo] wird wissen, dass ihr Benutzer sich über List-Unsubscribe abgemeldet hat und dass Sie ihm noch eine E-Mail an Tag 3 senden, und er hat erklärt, dass er Absendern, die dies tun, nicht erlauben wird, E-Mails an EINIGE seiner Benutzer zu senden.
Diese zweitägige Anforderung gilt für alle Abmeldungen über die verschiedenen Methoden zum Abmelden von Listen. In einigen Fällen (wie &quot;mailto&quot;) bedeutet das, dass Adobe sie verarbeitet. Adobe verarbeitet alle Abmeldeanfragen sofort nach Erhalt der Anfrage, innerhalb der 2-Tage-Frist. In anderen Fällen können Sie sie verarbeiten. Wenn Sie diese Anforderungen verarbeiten, müssen Sie möglicherweise am Ende Änderungen vornehmen, um diesen zweitägigen Zeitrahmen zu erreichen.

## Beschwerderaten:

Die Beibehaltung niedriger Beschwerderaten unter 0,2 % ist seit langem eine bewährte Praxis. [!DNL Google] setzt die Messlatte über einen längeren Zeitraum auf 0,3 % höher, hat jedoch deutlich gemacht, dass es Vorteile gibt, sie unter 0,1 % zu halten. Im Folgenden finden Sie die Details, die sie freigegeben haben:
* Ziel ist es, Ihre Spam-Rate unter 0,10% zu halten.
* Vermeiden Sie eine Spam-Rate von 0,30 % oder höher, insbesondere für längere Zeiträume.
* Wenn Sie eine niedrige Spam-Rate beibehalten, sind Absender weniger anfällig für gelegentliche Spitzen im Benutzer-Feedback.
* Gleichermaßen führt die Beibehaltung einer hohen Spam-Rate zu einer erhöhten Spam-Klassifizierung. Es kann einige Zeit dauern, bis die Spam-Rate verbessert wird, um die Spam-Klassifizierung positiv zu beurteilen.
  [!DNL Yahoo] hat erklärt, dass ihre Beschwerdefrist ebenfalls in der Größenordnung von 0,30 % liegen wird.
Wenn Sie Hilfe bei der Überwachung Ihrer Beschwerderaten benötigen oder Hilfe bei der Reduzierung von Beschwerden benötigen, wenden Sie sich an Ihren Adobe Deliverability Consultant oder sprechen Sie mit Ihrem Account-Team über das Hinzufügen eines Zustellbarkeits-Consultant, falls Sie noch keinen haben.

## Wie wirkt sich dies auf mich als Marketing-Experte aus?

Nichteinhaltung dieser neuen Anforderungen von Gmail und [!DNL Yahoo] wird voraussichtlich dazu führen, dass E-Mails in den Spam-Ordner landen oder blockiert werden (d. h., dass ein Bounce vom MBP ausgegeben wird, der angibt, dass die E-Mail nicht zugestellt wurde).
Daher empfiehlt Adobe dringend, die oben beschriebenen Änderungen zu durchlaufen und sicherzustellen, dass Sie diese so bald wie möglich einhalten. Jetzt ist auch ein guter Zeitpunkt, um mit dem Benchmarking Ihrer Leistung zu beginnen. [!DNL Yahoo] und [!DNL Google] , damit Sie sehen können, ob wesentliche Änderungen an Ihren Metriken im Februar eintreten.
Wenn Sie Fragen haben oder Support benötigen, wenden Sie sich an Ihren Adobe Deliverability Consultant oder sprechen Sie mit Ihrem Account-Team über das Hinzufügen eines Zustellbarkeits-Consultant, falls Sie noch keinen haben.

## Gibt es Wege um das herum?

Auch wenn dies immer eine Frage ist, die auftaucht, ist die Realität, dass diese Änderungen für die Endnutzer von [!DNL Google] und [!DNL Yahoo]-Plattformen. Sie sind von den Erwartungen dieser Benutzer an die Durchsetzung dieser Regeln motiviert. Wir empfehlen nicht, diese Änderungen zu umgehen, sondern einen Schritt zurück zu gehen und darüber nachzudenken, wie diese Änderungen berücksichtigt werden können.
