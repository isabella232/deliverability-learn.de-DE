---
title: Domänenname einrichten
description: Erfahren Sie, wie Sie eine Subdomäne an Adobe Campaign delegieren.
feature: Putting it in practice
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '2032'
ht-degree: 2%

---


# Domänenname einrichten

In diesem Dokument werden die geschäftlichen und technischen Anforderungen für die Einrichtung und Übertragung von Domänennamen beschrieben. Sie müssen eine Subdomäne zum Senden von E-Mails und optional eine extern orientierte Subdomäne zum Hosten von Webkomponenten (Landingpages, Ausschluss-Seite) für die verwendete Adobe auswählen.

>[!NOTE]
>
>Sie können auch über die Systemsteuerung neue Subdomänen einrichten (als Beta-Version verfügbar). Weiterführende Informationen finden Sie in diesem [Abschnitt](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read).

## Subdomänen

Mit der Adobe kann digitales Marketing wirklich zur kontextbezogenen Engine werden, die das Marketing-Programm Ihrer Marke für Kundeninteraktionen unterstützt.  E-Mail bleibt die Grundlage für digitale Marketing-Programm. Das Erreichen des Posteingangs ist jedoch schwieriger denn je.

Die Erstellung einer Subdomäne für E-Mail-Kampagnen ermöglicht es Marken, verschiedene Traffic-Typen (z. B. Marketing oder Unternehmen) in bestimmte IP-Pools und mit bestimmten Domänen zu isolieren, wodurch der [IP-Erwärmungsvorgang](../../help/additional-resources/increase-reputation-with-ip-warming.md) beschleunigt und die Lieferbarkeit insgesamt verbessert wird. Wenn Sie eine Domäne freigeben und sie blockiert oder der Blockierungsliste hinzugefügt wird, könnte dies Auswirkungen auf Ihren E-Mail-Versand im Unternehmen haben. Reputationsfehler oder -blockierungen in einer Domäne, die spezifisch für Ihre E-Mail-Marketingkommunikation ist, wirken sich jedoch nur auf diesen E-Mail-Fluss aus.  Die Verwendung Ihrer Hauptdomäne als Absender oder &quot;Von&quot;-Adresse für mehrere E-Mail-Streams könnte auch die E-Mail-Authentifizierung beschädigen, sodass Ihre Nachrichten blockiert oder im Spam-Ordner abgelegt werden.

### Delegation

Die Domänennamenübertragung ist eine Methode, die dem Inhaber eines Domänennamens (technisch: eine DNS-Zone) zur Delegierung einer Unterteilung (technisch: eine DNS-Zone darunter, die als Unterzone bezeichnet werden kann) zu einer anderen Entität. Grundsätzlich kann ein Kunde, der die Zone &quot;example.com&quot;behandelt, die Unterzone &quot;marketing.example.com&quot;an Adobe Campaign delegieren.

Das bedeutet, dass die DNS-Server des Adobe Campaigns nur für diese Zone volle Autorität haben und nicht für die Domäne auf der obersten Ebene. Die DNS-Server von Adobe Campaign liefern verbindliche Antworten auf Abfragen zu Domänennamen in dieser Zone, wie z.B. &quot;t.marketing.example.com&quot; selbst, aber nicht &quot;www.example.com&quot;.

Durch die Delegierung einer Subdomäne zur Verwendung mit Adobe Campaign können sich Kunden auf die Adobe verlassen, die DNS-Infrastruktur zu pflegen, die erforderlich ist, um die Anforderungen des Branchenstandards für die Zustellbarkeit ihrer E-Mail-Marketingdomänen zu erfüllen, und gleichzeitig DNS für ihre internen E-Mail-Domänen zu verwalten und zu steuern.  Subdomänenübertragung ermöglicht Folgendes:

Kunden behalten ihr Markenbild mithilfe eines DNS-Alias mit ihren Domänennamen bei
Adobe, alle technischen Best Practices autonom zu implementieren, um die Lieferbarkeit während des E-Mailings vollständig zu optimieren

## DNS-Setup-Optionen

Um einen Cloud-basierten verwalteten Dienst bereitzustellen, empfiehlt Adobe Kunden dringend, bei der Bereitstellung von Adobe Campaign Subdomänendelegation zu verwenden.  Adobe bietet Angebot-Clients jedoch eine andere Option - CNAME-Setup - zum Konfigurieren von DNS.

| Option | Beschreibung | Zuständigkeiten der Adobe | Kundenverantwortung |
|--- |------- |--- |--- |
| Subdomänenübertragung an Adobe Campaign | Der Client delegiert eine Subdomäne (email.example.com) an die Adobe. In diesem Szenario ist Adobe in der Lage, die Kampagne als verwalteten Dienst bereitzustellen, indem sie alle DNS-Aspekte steuert und pflegt, die für die Bereitstellung, Wiedergabe und Verfolgung von E-Mail-Kampagnen erforderlich sind. | Vollständige Verwaltung der Subdomäne und aller zum Adobe Campaign erforderlichen DNS-Datensätze. | Ordnungsgemäße Übertragung der Subdomäne auf die Adobe |
| Verwenden von CNAME | Der Client erstellt eine Subdomäne und verwendet CNAMEs, um auf Adoben-spezifische Datensätze zu verweisen.  Mit dieser Konfiguration sind Adobe und der Kunde gleichermaßen für die Wartung des DNS verantwortlich. | Verwaltung der zum Adobe Campaign erforderlichen DNS-Datensätze. | Erstellung und Steuerung der Subdomäne und Erstellung/Verwaltung der zum Adobe Campaign erforderlichen CNAME-Einträge. |

## Erforderliche DNS-Einträge

| Datensatztyp | Zweck | Beispiele für Datensatz/Inhalt |
|--- |--- |--- |
| MX | E-Mail-Server für eingehende Nachrichten angeben | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Sender Policy Framework | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.Kampagne.adobe.com&quot; |
| DKIM (TXT) | DomainKeys Identified Mail | <i>Client._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY HIER&quot; |
| DMARC (TXT) | Domänenbasierte Nachrichtenauthentifizierung | Berichte und Konformität | _dmarc.email.example.com</br>&quot;v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com&quot; |
| Hosts Records (A) | Mirrorseiten, Bild-Hosting und Tracking-Links, alle sendenden Domänen | m.email.example.com IN A 123.111.100.99</br>t.email.example.com IN A 123.111.100.98</br>email.example.com IN A 123.111.100.97 |
| Umgekehrtes DNS (PTR) | Ordnet die Client-IP-Adressen einem clientmarkierten Hostnamen zu | 18.101.100.192.in-addr.arpa Domänennamenzeiger r18.email.example.com |
| CNAME | Stellt einen Alias für einen anderen Domänennamen bereit | t1.email.example.com ist ein Alias für | t1.email.example.campaign.adobe.com |

## Setup-Anforderungen

### Subdomänendelegation

Dies erfordert, dass der Client eine Subdomäne in seinen DNS-Servern erstellt und die Namensserver für diese Subdomäne so definiert, dass sie von der Adobe verwaltet werden.  Beispielsweise muss ein Client, dessen Hauptdomänenname &quot;example.com&quot;ist und der die Verwaltung von &quot;marketing.example.com&quot;an die Adobe seiner E-Mail-Versand delegieren möchte, diese Delegation materialisieren, um die folgenden Typdatensätze zu seinem DNS hinzuzufügen:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

Die Übertragung eines Domänennamens bedeutet, dass diese Domäne für die Übermittlung von E-Mails über die Adobe Campaign-Plattform vorgesehen ist und daher nicht für andere Zwecke verwendet werden kann (z. B. das Senden von E-Mails über eine andere E-Mail-Infrastruktur).

Während des Einrichtungsvorgangs stellt die Adobe sicher, dass die Domäne an die eingehende E-Mail-Infrastruktur der Adobe angehängt wird, um die zurückgesendeten E-Mails zu verwalten und zu verarbeiten, die zu diesen Domänen zurückgeleitet werden (DNS-Datensatzkonfiguration vom Typ MX).

### Verwenden von CNAME

Wenn der Client sich dafür entscheidet, CNAMEs zu verwenden, statt eine Subdomäne an die Adobe zu delegieren, stellt Adobe während der Einrichtungsphase die Datensätze bereit, die auf den Client-DNS-Servern abgelegt werden sollen, und konfiguriert die entsprechenden Werte in Adobe Campaign-DNS-Servern.

## Allgemeine Anforderungen für die Bereitstellung

Bei der Implementierung einer neuen Enterprise-Marketinglösung gibt es Anforderungen an extern orientierte Komponenten.  Dazu gehören das Hosten von Landingpages und Webformularen, das Einrichten von Links und Webseiten, die verfolgt werden sollen, das Anzeigen von Mirrorseiten und das Konfigurieren einer Ausschluss-Seite.

Während diese Anforderungen über Komponenten verwaltet werden, die sowohl von der Adobe als auch vom Kunden gehostet werden, enthalten sie URLs, die vom Empfänger der E-Mails gesehen werden können.  Um zu vermeiden, dass URLs vorhanden sind, die die zugrunde liegende technische Lösung oder den Hosting-Anbieter angeben, können Subdomänen eingerichtet werden, um dies für den Empfänger der E-Mails transparent zu machen.  Wenn Sie sich beispielsweise eine URL wie http://www.customer.com/ ansehen, lautet die Domäne &quot;www.customer.com&quot;.  Die Subdomäne davon wäre &quot;www&quot;.

### Anforderungen an Unterdomänen

Bestimmen Sie die Subdomäne(n), die für Marken-URLs (Mirrorseiten und Tracking-URLs) aus der Adobe Campaign-Anwendung verwendet werden sollen.  Entscheiden Sie auch, welche &quot;Von Adresse&quot;, &quot;Von Name&quot; und &quot;Antwort-bis-Adresse&quot; für jede Subdomäne in E-Mail-Versänden verwendet werden.

Füllen Sie die unten stehende Tabelle aus, die erste Zeile ist nur ein Beispiel.

| Subdomain | Von Adresse | Von Name | Antwort-Adresse |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Customer  | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* Der Zweck des Felds &quot;Antwort-Adresse&quot;ist es, wenn der Empfänger auf eine andere Adresse antworten soll als auf &quot;Von Adresse&quot;.  Adobe empfiehlt, dass die &quot;Antwort-Adresse&quot; gültig und mit einem überwachten Postfach verknüpft ist, obwohl sie nicht erforderlich ist.  Dieser Briefkasten muss vom Kunden gehostet werden.  Es kann sich um eine Support-Mailbox handeln, z. B. customercare@customer.com, in der E-Mails gelesen und beantwortet werden.
>* Wenn der Kunde keine &quot;Antwort-Adresse&quot;auswählt, ist die Standardadresse immer `<tenant>-<type>-<env>@<subdomain>`.
>* Wenn die &quot;Antwort-Adresse&quot;auf diese Weise eingerichtet wird, werden die Antworten an eine nicht überwachte Mailbox gesendet.
>* Beim Senden von E-Mails aus Adobe Campaign wird das Postfach &quot;Von Adresse&quot;nicht überwacht und Marketingbenutzer können nicht auf dieses Postfach zugreifen. Adobe Campaign Angebot auch nicht die Möglichkeit, E-Mails, die in diesem Postfach empfangen werden, automatisch zu beantworten oder automatisch weiterzuleiten.
>* Die Kampagne von/Absenderadresse und die Fehleradresse dürfen nicht &quot;missbräuchlich&quot;oder &quot;postmaster&quot;lauten.


## Zuweisen von Subdomains

Die Subdomäne(n), die für die Adobe Campaign-Plattform verwendet werden sollen, müssen durch Erstellen von vier Namensserverdatensätzen (NS) delegiert werden.  Dadurch kann die Subdomäne ordnungsgemäß an die Adobe delegiert werden.  Nachfolgend finden Sie ein Beispiel für eine Subdomänendelegation und die entsprechenden DNS-Anweisungen.  Bitte ersetzen Sie &quot;emails.customer.com&quot;durch die Subdomäne, die Sie delegieren möchten.  Bitte beachten Sie, dass die Subdomäne eindeutig sein muss und nicht bereits von einer anderen Partei verwendet werden kann (z.B. ein bestehender ESP oder MSP).

| Delegierte Subdomäne | DNS-Anweisungen |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.  </br> `<subdomain>` NS b.ns.campaign.adobe.com.  </br> `<subdomain>` NS c.ns.campaign.adobe.com.  </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

## Verfolgung, Mirrorseiten, Ressourcen

Sobald die Subdomäne(n) für das Senden von E-Mails ordnungsgemäß an Adobe Campaign delegiert wurde/werden, erstellt das TechOps-Team der Adobe zwei oder mehr untergeordnete Domänen, um die Verfolgung und Mirrorseiten unabhängig zu verwalten.

| Typ | Domain |
|--- |--- |
| Mirrorseiten | m.`<subdomain>` |
| Tracking | t.`<subdomain>` |
| Ressourcen | res.`<subdomain>` |

## Cloud-Bereitstellung (optional)

Dies gilt nur, wenn das Adobe Campaign Classic per Adobe vollständig in der Cloud gehostet wird.  Dies ist eine optionale Konfiguration.

Alle zu entwickelnden Umfragen, Webformulare und Landingpages werden über Adobe Campaign verwaltet, das vollständig in der Cloud gehostet wird.  Bei Bedarf kann eine zusätzliche Subdomäne an Adobe (z. B. web.customer.com) delegiert werden, um sie für Webkomponenten innerhalb des Tools zu verwenden.  Bitte beachten Sie, dass die Subdomäne eindeutig sein muss und nicht von einer anderen Partei (z.B. einem bestehenden ESP oder MSP) verwendet werden kann.

| Delegierte Subdomäne | DNS-Anweisungen |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>Standardmäßig verwenden alle Webkomponenten im Tool die ursprünglich delegierte Subdomäne, die für E-Mail verwendet werden soll.

## Bereitstellung von Cloud-Messaging (optional)

Wird die Adobe Campaign Classic-Marketinginstanz auf dem Kundenstandort gehostet, muss der Kunde zusätzliche technische Konfigurationen vornehmen.

Alle zu entwickelnden Umfragen, Webformulare und Landingpages werden über die Adobe Campaign-Marketinginstanz verwaltet, wo die Empfänger-Datensätze vorhanden sind.

Zur Bereitstellung extern orientierter Webkomponenten, die von der Adobe Campaign-Marketinginstanz gehostet werden, ist eine zusätzliche CNAME-DNS-Konfiguration erforderlich.  Dadurch können Webkomponenten (z. B. web.customer.com) öffentlich für das Internet zugänglich sein und mit der Domäne des Kunden versehen werden.

Firewall(s) müssen auch so konfiguriert sein, dass der Zugriff auf die Adobe Campaign-Marketinginstanz, die diese Webkomponenten hostet, möglich ist (auf Port 80 oder 443).

**Best Practice Recommendations:**

Die Subdomäne zum Hosten von Webkomponenten ist für Kunden sichtbar. Achten Sie daher darauf, sie korrekt zu markieren und sich einfach zu merken, da sie möglicherweise manuell eingegeben werden muss. Beispiel: https://web.customer.com.
Wenn Formulare auf sicheren Seiten (HTTPS) gehostet werden müssen, ist eine zusätzliche technische Konfiguration erforderlich, wie nachfolgend beschrieben.

| Delegierte Subdomäne | DNS-Anweisungen |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Gerenderte Dienste

Im Anschluss an diese Delegationen stellt die von der Adobe eingerichtete Infrastruktur sicher, dass für jede übertragene oder CNAME-Alias übertragene Sendeindustrie folgende Dienste erbracht werden:

* Postmaster@- und Missbrauchs@-Postfächer erstellen
* Einrichtung von Feedback-Schleifen für die delegierte Domäne
* Auf Anfrage konfiguriert Adobe auch einen DMARC-Datensatz wie angegeben. Ihr Bereitstellungsberater kann Ihnen bei der Entwicklung einer langfristigen DMARC-Richtlinie und der Planung Ihrer sendenden Domänen behilflich sein.
Die von der Adobe festgelegten Parameter gelten erst ab dem Zeitpunkt, zu dem die Übertragung abgeschlossen und dann durch Adobe überprüft wurde, und bleiben funktionsfähig.  In allen Adobe Campaign Cloud-Angeboten ist die Domänennamendelegation standardmäßig enthalten.

## Abrechnungs- und Durchführungsbedingungen

* Gemäß dem ursprünglichen Vertrag und der Art des ausgewählten Pakets können weitere Delegationen zusätzlich zu den als Standard über diese ursprüngliche Delegation hinaus einbezogen werden —
* Über diese Delegationen hinaus werden zusätzliche Delegationen in Rechnung gestellt,
* Die Abrechnungsmethode für diese zusätzlichen Delegationen erfolgt zu zusätzlichen monatlichen Kosten, wie im ursprünglichen Vertrag festgelegt.

Diese Delegationen werden akzeptiert, sofern der CLIENT die damit verbundenen Domänennamen wählt, die über das Adobe Campaign-Tool den Versänden zugewiesen werden, und die im entsprechenden Dokument festgelegten Delegationsvoraussetzungen korrekt umgesetzt werden.

## Einstellung der Dienste

Der CLIENT kann jederzeit schriftlich verlangen, nicht mehr von den Delegationsdiensten zu profitieren und die notwendigen DNS-Konfigurationen selbst zu übernehmen.

Sollte dies der Fall sein, stellt die Adobe dem CLIENT eine Schätzung zur Verfügung, aus der hervorgeht, wie viele Diensttage erforderlich sind, um in den Nicht-Domänendelegationsmodus zurückzukehren.

Die Adobe wird von der Haftung für die Verpfändung der oben genannten Lieferungsrate befreit, wenn der Kunde die oben genannten Zusagen nicht einhält.

Die Beendigung des Marketing Cloud Service führt automatisch zum Ende der Domain-Delegationen und DNS-Wartung für diese Domänen nach Adobe.

## Unterdomänen mithilfe der Systemsteuerung überwachen

Sobald Subdomänen für Ihre Instanz konfiguriert sind, können Sie sie über die Systemsteuerung überwachen.

Auf diese Weise können Sie alle Subdomänen, die Sie an Adobe Campaign delegiert haben, sowie die Verlängerung ihrer SSL-Zertifikate anfordern.

Weiterführende Informationen finden Sie im [entsprechenden Handbuch](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates).

>[!NOTE]
>
>[Control ](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) Panel steht nur Kunden zur Verfügung, die Adobe Managed Services verwenden.