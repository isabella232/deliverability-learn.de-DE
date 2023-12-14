---
title: Leitlinien für die angekündigten Änderungen in  [!DNL Google]  und  [!DNL Yahoo]
description: Leitlinien für die angekündigten Änderungen in  [!DNL Google]  und  [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06T00:00:00Z
jira: KT-14320
thumbnail: KT-14320.jpeg
exl-id: 879e9124-3cfe-4d85-a7d1-64ceb914a460
source-git-commit: 2bda5d5369d239fac849e57286450a853dd94953
workflow-type: tm+mt
source-wordcount: '1605'
ht-degree: 85%

---

# Leitlinien für die angekündigten Änderungen in [!DNL Google] und [!DNL Yahoo]

Am 3. Oktober haben [!DNL Google] und [!DNL Yahoo] gemeinsam geplante Änderungen über ihre Blogs angekündigt. Diese Änderungen sollen die Sicherheit der Benutzenden erhöhen und ein besseres E-Mail-Erlebnis bieten, indem einige gängige Best Practices der Branche ab 1. Februar 2024 als neue Anforderungen durchgesetzt werden.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] Ankündigung_](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] Ankündigung](/help/assets/Yahoo.png)

Die Fachleute für E-Mail-Zustellbarkeit von Adobe haben sich diese Blog-Posts und die gesamte verlinkte Dokumentation durchgelesen, damit Sie dies nicht zu tun brauchen. Hier sind die wichtigsten Erkenntnisse.

## Was genau machen [!DNL Google] und [!DNL Yahoo]?

In der E-Mail-Welt gibt es rechtliche Anforderungen, praktische Anforderungen und allgemeine Best Practices. Die rechtlichen Anforderungen sind von Ort zu Ort sehr unterschiedlich und nicht Teil dieses Themas. stattdessen [!DNL Google] und [!DNL Yahoo] bewährte Verfahren übernehmen und in praktische Anforderungen umsetzen.

Keine der Elemente, die von [!DNL Google] und [!DNL Yahoo] ab Februar verlangt werden, sind neu, und sie sind seit Jahren empfohlene Best Practices, doch die Branche hat sie nur langsam und uneinheitlich übernommen. [!DNL Google] und [!DNL Yahoo] tragen auf diese Weise dazu bei, den Übernahmeprozess voranzutreiben, indem sie sagen: „Wenn Sie E-Mails für unsere Benutzenden bereitstellen möchten (dies kann einen erheblichen Anteil Ihrer E-Mail-Liste ausmachen, in einigen Fällen sogar bis zu 70 %, je nach Region und Branche), müssen Sie diese Schritte durchführen.“

## Wie sehen die Details aus?

Wenn Sie Adobe-Kundin bzw. Kunde sind, ist der Großteil dessen, was verlangt wird, bereits Teil Ihres Setups. Es gibt jedoch einige wichtige Elemente, die technisch optional sind. Sie sollten sicherstellen, dass Ihr Unternehmen diese Artikel vor Februar 2024 korrekt angenommen und eingerichtet hat.

## DMARC:

[!DNL Google] und [!DNL Yahoo] verlangen beide, dass Sie einen DMARC-Eintrag für jede Domain haben, die Sie verwenden, um E-Mails an sie zu senden. Sie erfordern derzeit NICHT die Einstellung p=reject oder p=quarantine. Daher ist eine Einstellung von p=none, die häufig als „Überwachungseinstellung“ bezeichnet wird, vollkommen akzeptabel. Dies wirkt sich nicht darauf aus, wie Ihre E-Mails verarbeitet werden. Sie tun das, was sie normalerweise ohne DMARC tun würden. Dies einzurichten, ist der erste Schritt, um sich mit DMARC zu schützen. Und zusätzlich zu dem neuen Vorteil, dass Sie E-Mails an [!DNL Google] und [!DNL Yahoo] senden können, können Sie außerdem erkennen, ob es innerhalb Ihres E-Mail-Ökosystems Authentifizierungsprobleme gibt.

Die Regeln für DMARC ändern sich nicht. Das bedeutet, dass ein DMARC-Eintrag (sofern er nicht so konfiguriert wurde, dass er dies verhindert) in der übergeordneten Domain (z. B. adobe.com) vererbt wird und alle Subdomains (z. B. email.adobe.com) abdeckt. Sie benötigen keine unterschiedlichen DMARC-Einträge für Ihre Subdomains, es sei denn, Sie möchten oder müssen sie aus verschiedenen geschäftlichen Gründen hinzufügen.

DMARC wird in Adobe derzeit vollständig unterstützt, ist jedoch nicht erforderlich. Verwenden Sie einen kostenlosen DMARC-Checker, um zu sehen, ob Sie DMARC für Ihre Subdomains eingerichtet haben, und falls Sie dies nicht der Fall ist, wenden Sie sich an Ihr Adobe-Supportteam, um zu erfahren, wie Sie diese Einrichtung am besten vornehmen.

Weitere Informationen zu DMARC und dazu, wie es implementiert wird, finden Sie auch [hier](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=de){target="_blank"} for Adobe Campaign or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html?lang=de){target="_blank"} für Marketo Engage.

## Abmelden mit einem Klick (Liste):

Keine Panik! [!DNL Google] und [!DNL Yahoo] sprechen nicht von den Abmelde-Links in Ihrem E-Mail-Text oder Ihrer E-Mail-Fußzeile, die von einem Sicherheits-Bot, der einfach nur seine Arbeit macht, oder aus Versehen angeklickt werden könnten. Gemeint ist vielmehr die Kopfzeilenfunktion List-Unsubscribe für entweder die Version „mailto“ oder „http/URL“.  Dies ist die Funktion innerhalb der Benutzeroberflächen von [!DNL Yahoo] und Gmail, wo Benutzende auf „Abmelden“ klicken können. Gmail fordert Benutzer, die auf &quot;Spam melden&quot;klicken, sogar dazu auf zu sehen, ob sie sich stattdessen abmelden möchten. Dies kann die Anzahl der Beschwerden verringern, die Sie erhalten (Beschwerden verletzen Ihre Reputation), indem sie stattdessen in Abmeldungen umgewandelt werden (was Ihrer Reputation nicht schadet).

Es ist wichtig festzustellen, dass [!DNL Google] und [!DNL Yahoo] sich beide auf die Option „http/URL“ unter dem Namen „1-Click“ beziehen und dies beabsichtigt ist. Technisch gesehen hatten Sie mit der ursprünglichen Option „http/URL“ die Möglichkeit, Empfängerinnen und Empfänger auf eine Website umzuleiten. Das ist nicht der Schwerpunkt [!DNL Yahoo] und [!DNL Google], die beide auf die aktualisierte [RFC 8058](https://datatracker.ietf.org/doc/html/rfc8058){target="_blank"} , die sich auf die Verarbeitung der Abmeldung über eine HTTPS-POST-Anfrage anstelle einer Website konzentriert, wodurch sie &quot;1-Klick&quot;ergibt.

Heute akzeptiert Gmail die Option &quot;mailto&quot; list-unsubscribe . Gmail hat gesagt, dass &quot;mailto&quot; nicht mehr ihre Erwartungen erfüllt, und Absender müssen die Option &quot;post&quot; list-unsubscribe aktivieren lassen. Diejenigen Absender, die bereits Listen-Abmeldungen irgendeiner Art haben, haben bis zum 1. Juni 2024 die Möglichkeit, sich mit &quot;1-Klick&quot;-List-Unsubscribe zu registrieren.

[!DNL Yahoo] verkündete, es werde vorerst weiterhin die Verwendung der „mailto“-Option ermöglichen, aber Benutzerinnen und Benutzer werden dort in Zukunft ebenfalls die „post“-Option benötigen.

Adobe empfiehlt sowohl die Verwendung der Option „mailto“ als auch der Option „post/Abmeldung mit nur einem Klick“ zum Abmelden von einer Liste. Adobe arbeitet daran, den „post“-Support für alle unsere E-Mail-Versandplattformen zu ermöglichen, um unsere Benutzerinnen und Benutzer bei der Erfüllung dieser Anforderungen zu unterstützen. Weitere Updates werden erwartet.

Für Marketo Engage hat Adobe bereits die Option „mailto“ aktiviert und unterstützt derzeit nicht die Option „http/URL“. Weitere Aktualisierungen hierzu werden folgen.
Für Adobe Campaign und Adobe Journey Optimizer empfiehlt Adobe die Verwendung beider Optionen, „mailto“ und „1-Click“.

Für Transaktions-E-Mails ist die Kopfzeile „list-unsubscribe“ nicht erforderlich. Bitte beachten Sie, dass ausgelöste Nachrichten wie „Warenkorb verlassen“ und ähnliche Kommunikationen, die nicht von der Abonnentin bzw. dem Abonnenten generiert wurden, von Postfachanbietern wie [!DNL Google] und [!DNL Yahoo] als Marketing-Nachrichten erachtet werden. Für diese Nachrichten wäre die Option „Abmelden von einer Liste“ erforderlich.

[!DNL Google] und [!DNL Yahoo] sind sich beide bewusst, dass sich eine Empfängerin oder ein Empfänger in einigen Fällen abmeldet und sich dann zu einem späteren Zeitpunkt erneut anmeldet. Sie sind zwar nicht bereit zu verraten, wie sie eine solche Situation identifizieren können, arbeiten jedoch an Methoden, um zu verhindern, dass in diesen Fällen Absenderinnen oder Absender fälschlicherweise bestraft werden.

>[!INFO]
> Weitere Informationen zur Implementierung von list-unsubscribe für Ihre Lösung finden Sie unter:
> * [!DNL Adobe Campaign Classic]: [Technische Empfehlungen](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=de#list-unsubscribe){target="_blank"}
>* [!DNL Adobe Campaign Standard]: [Was ist die List-Unsubscribe-Kopfzeile? Und wie kann sie in ACS implementiert werden?](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-14778.html?lang=de){target="_blank"}
>* [!DNL Adobe Journey Optimizer]: [Opt-out-Verwaltung für E-Mails](https://experienceleague.adobe.com/docs/journey-optimizer/using/email/email-opt-out.html?lang=de){target="_blank"}
>
> Oder wenden Sie sich an das Kunden-Support-Team von Adobe.


## Bearbeiten Sie Abmeldungen innerhalb von 2 Tagen:

Dies ist seit einiger Zeit eine empfohlene Best Practice, da jede E-Mail, die Sie an eine abgemeldete Person senden, in der Regel zu einer Spam-Beschwerde führt. Je früher Sie aufhören, ihr E-Mails zu senden, desto besser. Auch hier können die rechtlichen Anforderungen in einigen Fällen viel länger sein, aber [!DNL Google] und [!DNL Yahoo] werden wissen, dass die Person sich über „List-Unsubscribe“ abgemeldet hat und dass Sie ihr an Tag 3 immer noch E-Mails senden. Außerdem haben sie erklärt, dass sie Absenderinnen und Absendern, die dies tun, nicht erlauben werden, weiterhin E-Mails überhaupt an IRGENDWELCHE ihrer Benutzenden zu senden.
Diese 2-Tage-Frist gilt für alle Abmeldungen über die verschiedenen Methoden von „List-Unsubscribe“. In einigen Fällen (wie „mailto“) werden sie von Adobe bearbeitet. Adobe bearbeitet alle Abmeldeanfragen sofort nach Erhalt der Anfrage, innerhalb der 2-Tage-Frist. In anderen Fällen können Sie sie bearbeiten. Bei Bearbeitung dieser Anfragen müssen Sie möglicherweise auf Ihrer Seite Änderungen vornehmen, um diese zweitägige Frist einzuhalten.

## Beschwerderaten:

Die Beschwerderate unter 0,2 % zu halten, ist seit langem eine bewährte Praxis. [!DNL Google] setzt die Messlatte mit 0,3 % über einen längeren Zeitraum höher, hat aber deutlich erklärt, dass es Vorteile hat, sie unter 0,1 % zu halten. Im Folgenden finden Sie die Details, die sie mitgeteilt haben:

* Ihr Ziel sollte es sein, die Spam-Rate unter 0,10 % zu halten.
* Vermeiden Sie eine Spam-Rate von 0,30 % oder höher, insbesondere über längere Zeiträume.
* Eine niedrige Spam-Rate macht Absenderinnen und Absender weniger anfällig für gelegentliche Spitzen im Benutzer-Feedback.
* Gleichermaßen führt die Beibehaltung einer hohen Spam-Rate zu einer erhöhten Spam-Klassifizierung. Es kann einige Zeit dauern, bis sich eine verbesserte Spam-Rate auch positiv in der Spam-Klassifizierung niederschlägt.
  [!DNL Yahoo] hat erklärt, dass ihre Beschwerdegrenze ebenfalls bei 0,30 % liegen wird.

Das Ziel von [!DNL Google] und [!DNL Yahoo] ist es nicht, eine Absenderin oder einen Absender für einen einzigen schlechten Tag oder einen Fehler zu bestrafen, der einen vorübergehenden Anstieg bei Beschwerden verursacht. Stattdessen konzentrieren sie sich auf Absenderinnen oder Absender, die über einen längeren Zeitraum hohe Beschwerderaten oder ein schlechtes Sendeverhalten haben.

Wenn Sie Hilfe bei der Überwachung oder Senkung Ihrer Beschwerderaten benötigen, wenden Sie sich an Ihre Zustellbarkeitsberaterin bzw. Ihren -berater bei Adobe oder sprechen Sie mit Ihrem Accountteam über das Hinzufügen einer solchen Person, falls Sie noch keine haben.

## Wie wirkt sich dies auf mich als Marketing-Fachkraft aus?

Nichteinhaltung dieser neuen Anforderungen von Gmail und [!DNL Yahoo] wird voraussichtlich dazu führen, dass E-Mails in den Spam-Ordner landen oder blockiert werden (d. h., dass ein Bounce vom MBP ausgegeben wird, der angibt, dass die E-Mail nicht zugestellt wurde).

Daher empfiehlt Adobe dringend, die oben beschriebenen Änderungen zu überprüfen und sicherzustellen, dass sie so bald wie möglich eingehalten werden. Jetzt ist auch ein guter Zeitpunkt, um mit dem Benchmarking Ihrer Leistung zu beginnen. [!DNL Yahoo] und [!DNL Google] , damit Sie sehen können, ob wesentliche Änderungen an Ihren Metriken im Februar eintreten.

Wenn Sie Fragen haben oder Hilfe benötigen, wenden Sie sich an Ihre Zustellbarkeitsberaterin bzw. Ihren -berater bei Adobe oder sprechen Sie mit Ihrem Accountteam über das Hinzufügen einer solchen Person, falls Sie noch keine haben.

## Gibt es andere Möglichkeiten?

Auch wenn dies eine häufige Frage ist, ergeben diese Änderungen für Endbenutzende von [!DNL Google]- und [!DNL Yahoo]-Plattformen doch Sinn. Sie sind von den Erwartungen dieser Benutzenden bzgl. der Durchsetzung dieser Regeln motiviert. Wir raten davon ab, diese Änderungen zu umgehen, sondern einen Schritt zurückzugehen und darüber nachzudenken, wie Sie sich auf diese Änderungen einstellen können.

## Letzte Anmerkung:

Beachten Sie, dass dies derzeit nicht für E-Mails gilt, die an [!DNL Yahoo].JP oder [!DNL Gmail] Workspace-Konten gesendet werden. Dies gilt jedoch für E-Mails, die von diesen Zielen kommen.

## Zusätzliche Ressourcen (nicht spezifisch für diese Änderungen):

[Google Sender Guidelines](https://support.google.com/mail/answer/81126){target="_blank"}

[Häufig gestellte Fragen zu Google](https://support.google.com/a/answer/14229414?sjid=2864589551334481470-NC){target="_blank"}

[Yahoo Sender Guidelines](https://senders.yahooinc.com/best-practices/){target="_blank"}

[Yahoo FAQ](https://senders.yahooinc.com/faqs/){target="_blank"}
