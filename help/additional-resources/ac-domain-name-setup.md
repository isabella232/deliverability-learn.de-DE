---
title: Domain-Namen einrichten
description: Erfahren Sie, wie Sie Adobe Campaign eine Subdomain zuweisen.
feature: Praktische Umsetzung
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
exl-id: 4d52d197-d20e-450c-bfcf-e4541c474be4
translation-type: ht
source-git-commit: e433002423bd1ab2f4a89425198c16160dae0719
workflow-type: ht
source-wordcount: '2032'
ht-degree: 100%

---

# Domain-Namen einrichten

Dieses Dokument beschreibt die betrieblichen und technischen Anforderungen für die Einrichtung und Zuweisung von Domain-Namen. Sie müssen eine Subdomain für den E-Mail-Versand und optional eine nach außen gerichtete Subdomain zum Hosten von Web-Komponenten (Landingpages, Opt-out-Seiten) für die von Ihnen verwendete Adobe-Plattform auswählen.

>[!NOTE]
>
>Sie können neue Subdomains auch über das Control Panel einrichten (als Beta-Version verfügbar). Weiterführende Informationen finden Sie in diesem [Abschnitt](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=de#must-read).

## Subdomains

Mit Adobe erhalten Sie einen kontextuellen Service, mithilfe dessen Sie Ihre Digital-Marketing-Programme zur Kundenbindung optimieren können.  E-Mail ist nach wie vor der Hauptpfeiler von Digital-Marketing-Programmen. Allerdings wird es immer schwieriger, Nachrichten zu versenden, die tatsächlich im Posteingang der Empfänger landen.

Das Einrichten einer Subdomain für E-Mail-Kampagnen ermöglicht es Marken, unterschiedliche Arten von Traffic (z. B. Marketing-bezogenen vs. betrieblichen) in eigene IP-Pools mit eigenen Domains zu unterteilen, wodurch der [IP-Warming-Prozess](../../help/additional-resources/increase-reputation-with-ip-warming.md) beschleunigt und die Zustellbarkeit insgesamt verbessert werden kann. Wenn Sie eine einzige Domain für alle Aufgaben verwenden und diese gesperrt oder zur Blockierungsliste hinzugefügt wird, könnte dies Auswirkungen auf die Zustellung Ihrer betrieblichen E-Mails haben. Probleme mit der Reputation oder die Blockierung einer Domain, die nur für Ihre E-Mail-Marketing-Kommunikation verwendet sind, beeinträchtigen hingegen ausschließlich diesen E-Mail-Verkehr.  Wenn Sie Ihre Haupt-Domain als Absenderadresse für mehrere E-Mail-Arten verwenden, kann dies auch die E-Mail-Authentifizierung behindern und dazu führen, dass Ihre Nachrichten blockiert oder in den Spam-Ordner verschoben werden.

### Zuweisung

Der Eigentümer eines Domain-Namens (technisch: einer DNS-Zone) kann einer anderen Entität eine Untergliederung des Domain-Namens (technisch: eine untergeordnete DNS-Zone) zuzuweisen. Wenn also ein Kunde die Zone „example.com“ verwaltet, kann er Adobe Campaign die untergeordnete Zone „marketing.example.com“ zuweisen.

In diesem Fall hätten die DNS-Server von Adobe Campaign die volle Berechtigung nur für diese Zone, nicht aber für die Domain auf der obersten Ebene. Die DNS-Server von Adobe Campaign liefern dann Antworten auf Anfragen zu Domain-Namen in dieser Zone, z. B. „t.marketing.example.com“, aber nicht zu „www.example.com“.

Durch das Zuweisen einer Subdomain an Adobe Campaign kann Adobe sicherstellen, dass Kunden die DNS-Infrastruktur bereitgestellt wird, die zur Erfüllung der branchenüblichen Anforderungen an Domains zum E-Mail-Marketing-Versand erforderlich ist. Gleichzeitig verwaltet und kontrolliert Adobe auch das DNS für die unternehmensinternen E-Mail-Domains.  Das Zuweisen von Subdomains ermöglicht Folgendes:

Kunden können ihr Marken-Image pflegen, indem sie einen DNS-Alias mit ihren Domain-Namen verwenden.
Adobe kann autonom alle technischen Best Practices implementieren, um die Zustellbarkeit beim E-Mail-Versand zu optimieren.

## Optionen zum Einrichten der DNS

Um einen Cloud-basierten Managed Service anbieten zu können, empfiehlt Adobe seinen Kunden dringend, Adobe Campaign eine Subdomain zuzuweisen.  Adobe bietet seinen Kunden jedoch auch eine alternative Option zur DNS-Konfiguration: CNAME-Setup.

| Option | Beschreibung | Zuständigkeiten von Adobe | Zuständigkeiten des Kunden |
|--- |------- |--- |--- |
| Zuweisen einer Subdomain an Adobe Campaign | Der Kunde weist Adobe eine Subdomain (email.example.com) zu. In diesem Szenario kann Adobe eine Kampagne als Managed Service bereitstellen, indem alle Aspekte des DNS, die für den Versand, das Rendern und das Tracking von E-Mail-Kampagnen erforderlich sind, kontrolliert und verwaltet werden. | Vollständige Verwaltung der Subdomain und aller für Adobe Campaign erforderlichen DNS-Einträge. | Ordnungsgemäße Zuweisung der Subdomain an Adobe |
| Verwenden von CNAMEs | Der Kunde erstellt eine Subdomain und verwendet CNAMEs, um auf Adobe-spezifische Einträge zu verweisen. Mit dieser Konfiguration sind Adobe und der Kunde gleichermaßen für die Wartung des DNS verantwortlich. | Verwalten der für Adobe Campaign erforderlichen DNS-Einträge. | Erstellen und Steuern der Subdomain und Erstellen/Verwalten der für Adobe Campaign erforderlichen CNAME-Einträge. |

## Erforderliche DNS-Einträge

| Art des Eintrags | Zweck | Beispiele für Eintrag/Inhalt |
|--- |--- |--- |
| MX | E-Mail-Server für eingehende Nachrichten angeben | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Sender Policy Framework | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM (TXT) | DomainKeys Identified Mail (mit DomainKeys identifizierte E-Mail) | <i>client._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY HERE&quot; |
| DMARC (TXT) | Domain-basierte Nachrichtenauthentifizierung | Reporting und Konformität | _dmarc.email.example.com</br>“v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com” |
| Einträge auf Hosts (A) | Mirror-Seiten, Bild-Hosting und Tracking-Links, alle sendenden Domains | m.email.example.com IN A 123.111.100.99</br>t.email.example.com IN A 123.111.100.98</br>email.example.com IN A 123.111.100.97 |
| Umgekehrtes DNS (PTR) | Ordnet die IP-Adressen des Kunden einem Host-Namen unter dem Markennamen des Kunden zu | 18.101.100.192.in-addr.arpa domain name pointer r18.email.example.com |
| CNAME | Stellt einen Alias für einen anderen Domain-Namen bereit | t1.email.example.com ist ein Alias für | t1.email.example.campaign.adobe.com |

## Anforderungen an das Setup

### Zuweisen von Subdomains

Dazu muss der Kunde eine Subdomain in seinen DNS-Servern anlegen und die Nameserver für diese Subdomain als die von Adobe verwalteten definieren.  Ein Kunde, dessen Haupt-Domain-Name beispielsweise „example.com“ lautet und der die Verwaltung von „marketing.example.com“ für seine E-Mail-Sendungen an Adobe übertragen möchte, muss diese Zuweisung konkretisieren, indem er die folgenden Typ-Einträge zu seinem DNS hinzufügt:

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

Das Zuweisen eines Domain-Namens bedeutet, dass diese Domain für den Versand von E-Mails über die Adobe Campaign-Plattform bestimmt ist und daher nicht für andere Zwecke verwendet werden kann (z. B. für den Versand von E-Mails über eine andere E-Mail-Infrastruktur).

Während des Einrichtungsvorgangs stellt Adobe sicher, dass die Domain an die Adobe-Infrastruktur für eingehende E-Mails angeschlossen wird, um die an diese Domains zurückgesendeten Rebound-E-Mails zu verwalten und zu verarbeiten (Konfiguration des DNS-Eintrags vom Typ MX).

### Verwenden von CNAMEs

Wenn sich der Kunde für die Verwendung von CNAMEs entscheidet, anstatt Adobe eine Subdomain zuzuweisen, stellt Adobe während der Einrichtungsphase die Einträge bereit, die in den DNS-Servern des Kunden platziert werden sollen, und konfiguriert die entsprechenden Werte in den DNS-Servern von Adobe Campaign.

## Allgemeine Anforderungen für die Implementierung

Bei der Implementierung einer neuen Enterprise-Marketing-Lösung gibt es Anforderungen an die nach außen gerichteten Komponenten.  Dazu gehören das Hosten von Landingpages und Web-Formularen, das Einrichten von Links und Websites, die getrackt werden sollen, das Anzeigen von Mirror-Seiten und das Konfigurieren einer Opt-out-Seite.

Diese Anforderungen werden über Komponenten verwaltet, die sowohl von Adobe als auch vom Kunden gehostet werden, und enthalten URLs, die für die Empfänger der E-Mails sichtbar sind.  Um URLs zu vermeiden, die auf die zugrunde liegende technische Lösung oder den Hosting-Anbieter hinweisen, können Subdomains eingerichtet werden, die diese Informationen vor den Empfängern der E-Mails verbergen.  Wenn man z. B. eine URL wie http://www.customer.com/ betrachtet, würde die Domain „www.customer.com“ lauten.  Die Subdomain davon wäre „www“.

### Anforderungen an Subdomains

Bestimmen Sie im Adobe Campaign-Programm die Subdomain(s), die für gebrandete URLs (Mirror-Seiten und Tracking-URLs) verwendet werden sollen.  Legen Sie außerdem fest, wie bei E-Mail-Sendungen die Absenderadresse, der Absendername und die Antwortadresse für jede Subdomain lauten sollen.

Füllen Sie die folgende Tabelle aus. Die erste Zeile ist nur ein Beispiel.

| Subdomain | Absenderadresse | Absendername | Antwortadresse |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Kunde | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* Das Feld „Antwortadresse“ wird benötigt, wenn Sie möchten, dass der Empfänger an eine andere Adresse als die Absenderadresse antwortet.  Obwohl es sich nicht um ein Pflichtfeld handelt, empfiehlt Adobe dringend, dass die Antwortadresse gültig und mit einer überwachten Mailbox verknüpft ist.  Diese Mailbox muss vom Kunden gehostet werden.  Das kann etwa eine Support-Mailbox sein, z. B. customercare@customer.com, in der E-Mails gelesen und beantwortet werden.
>* Wird vom Kunden keine Antwortadresse ausgewählt, ist die Standardadresse immer `<tenant>-<type>-<env>@<subdomain>`.
>* Wenn die Antwortadresse auf diese Weise eingerichtet ist, werden Antworten an eine nicht überwachte Mailbox gesendet.
>* Wenn E-Mails aus Adobe Campaign versendet werden, wird die Mailbox der Absenderadresse nicht überwacht und Marketing-Benutzer können nicht auf diese Mailbox zugreifen. Adobe Campaign bietet auch nicht die Möglichkeit, die in dieser Mailbox empfangenen E-Mails automatisch zu beantworten oder weiterzuleiten.
>* In Campaign dürfen die Absenderadresse und die Fehleradresse nicht „abuse“ oder „postmaster“ lauten.


## Zuweisen von Subdomains

Die Subdomains, die für die Adobe Campaign-Plattform verwendet werden sollen, müssen zugewiesen werden, indem vier Nameserver-Einträge (NS) erstellt werden.  Dadurch kann die Subdomain Adobe ordnungsgemäß zugewiesen werden.  Im Folgenden finden Sie ein Beispiel für eine Subdomain-Zuweisung und die entsprechenden DNS-Anweisungen.  Ersetzen Sie „emails.customer.com“ durch die Subdomain, die Sie zuweisen möchten.  Beachten Sie, dass die Subdomain eindeutig sein muss und nicht bereits von einer anderen Partei (z. B. einem bestehenden ESP oder MSP) verwendet werden darf.

| Zugewiesene Subdomain | DNS-Anweisungen |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com. </br> `<subdomain>` NS b.ns.campaign.adobe.com. </br> `<subdomain>` NS c.ns.campaign.adobe.com. </br> `<subdomain>` NS d.ns.campaign.adobe.com. |

## Tracking, Mirror-Seiten, Ressourcen

Sobald die Subdomains für den E-Mail-Versand Adobe Campaign ordnungsgemäß zugewiesen wurden, erstellt das Adobe TechOps-Team zwei oder mehr untergeordneter Domains, um Tracking und Mirror-Seiten unabhängig zu verwalten.

| Typ | Domain |
|--- |--- |
| Mirror-Seiten | m.`<subdomain>` |
| Tracking | t.`<subdomain>` |
| Ressourcen | res.`<subdomain>` |

## Cloud-Implementierung (optional)

Dies ist nur relevant, wenn Adobe Campaign Classic von Adobe vollständig in der Cloud gehostet wird.  Dies ist eine optionale Konfiguration.

Alle späteren Umfragen, Web-Formulare und Landingpages werden über Adobe Campaign verwaltet, das vollständig in der Cloud gehostet wird.  Bei Bedarf kann Adobe eine zusätzliche Subdomain zugewiesen werden (z. B. web.customer.com), die für beliebige Web-Komponenten innerhalb des Tools verwendet werden kann.  Beachten Sie, dass die Subdomain eindeutig sein muss und nicht von einer anderen Partei (z. B. einem bestehenden ESP oder MSP) verwendet werden darf.

| Zugewiesene Subdomain | DNS-Anweisungen |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.campaign.adobe.com.</br>`<subdomain>` NS b.ns.campaign.adobe.com.</br>`<subdomain>` NS c.ns.campaign.adobe.com.</br>`<subdomain>` NS d.ns.campaign.adobe.com. |

>[!NOTE]
>
>Standardmäßig verwenden alle Web-Komponenten im Tool die ursprüngliche Subdomain, die zum Zweck des E-Mail-Versands zugewiesen wurde.

## Implementierung von Cloud-Messaging (optional)

Für den Fall, dass die Marketing-Instanz von Adobe Campaign Classic beim Kunden „On-Premise“ gehostet wird, müssen zusätzliche technische Konfigurationen vom Kunden vorgenommen werden.

Alle späteren Umfragen, Web-Formulare und Landingpages werden über die Marketing-Instanz von Adobe Campaign verwaltet, in der die Empfänger-Einträge vorhanden sind.

Eine zusätzliche CNAME-DNS-Konfiguration ist erforderlich, um nach außen gerichtete Web-Komponenten zu implementieren, die von der Marketing-Instanz von Adobe Campaign gehostet werden.  Dadurch können Web-Komponenten (z. B. web.customer.com) öffentlich im Internet zugänglich sein und mit der Domain des Kunden gebrandet werden.

Die Firewalls müssen außerdem so konfiguriert werden, dass sie den Zugriff auf die Marketing-Instanz von Adobe Campaign zulassen, die diese Web-Komponenten hostet (auf Port 80 oder 443).

**Empfehlungen zu Best Practices:**

Die Subdomain zum Hosten der Web-Komponenten wird für Kunden sichtbar sein. Achten Sie daher darauf, dass die Subdomain gut gebrandet und einfach zu merken ist, da sie möglicherweise manuell eingegeben werden muss, z. B.: https://web.customer.com.
Wenn Formulare auf sicheren Seiten (HTTPS) gehostet werden sollen, ist eine zusätzliche technische Konfiguration erforderlich, die unten beschrieben wird.

| Zugewiesene Subdomain | DNS-Anweisungen |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Gerenderte Services

Im Anschluss an diese Zuweisungen stellt die von Adobe eingerichtete Infrastruktur sicher, dass die folgenden Services für jede zugewiesene Domain oder Versand-Domain mit CNAME-Alias ausgeführt werden:

* Erstellen von postmaster@- und abuse@-Posteingängen
* Einrichten von Feedback-Schleifen für die zugewiesene Domain
* Auf Wunsch konfiguriert Adobe auch wie angegeben einen DMARC-Eintrag. Ihr Zustellbarkeitsberater kann Sie bei der Ausarbeitung einer langfristigen DMARC-Richtlinie und eines Plans für Ihre Versand-Domains unterstützen.
Von Adobe festgelegte Parameter sind ab dem Zeitpunkt gültig, an dem die Zuweisung abgeschlossen und anschließend von Adobe überprüft wurde, und bleiben funktionsfähig, bis der Service gekündigt wird.  Alle Adobe Campaign Cloud-Angebote beinhalten standardmäßig die Zuweisung von Domain-Namen.

## Abrechnungs- und Implemetierungsbedingungen

* Je nach ursprünglichem Vertrag und der Art des gewählten Pakets können über diese anfängliche Zuweisung hinaus weitere Zuweisungen zusätzlich zu den standardmäßig eingeschlossenen enthalten sein.
* Zusätzliche Zuweisungen, die über diese enthaltenen Zuweisungen hinausgehen, werden in Rechnung gestellt.
* Bei der Abrechnung dieser zusätzlichen Zuweisungen fallen wie im ursprünglichen Vertrag festgelegt zusätzliche monatliche Kosten an.

Diese Zuweisungen werden unter der Voraussetzung akzeptiert, dass der KUNDE die zugehörigen Domain-Namen auswählt, die für die Sendungen über das Tool Adobe Campaign vorgesehen sind, und dass die im entsprechenden Dokument aufgeführten Zuweisungsvoraussetzungen korrekt umgesetzt werden.

## Beenden der Services

Der KUNDE kann jederzeit schriftlich verlangen, die Zuweisungs-Services nicht mehr in Anspruch zu nehmen und die notwendigen DNS-Konfigurationen selbst vorzunehmen.

In diesem Fall wird Adobe dem KUNDEN eine Schätzung über die Anzahl der Service-Tage zukommen lassen, die erforderlich sind, um wieder in den Modus ohne Domain-Zuweisung zurückzukehren.

Adobe ist von jeglicher Haftung für die Umsetzung der vorgenannten Zustellbarkeitsrate befreit, wenn der Kunde die vorgenannten Verpflichtungen nicht einhält.

Die Beendigung des Marketing Cloud-Services führt automatisch zum Ende der Domain-Zuweisung und der DNS-Wartung für diese Domains durch Adobe.

## Subdomains mithilfe des Control Panels überwachen

Sobald Subdomains für Ihre Instanz konfiguriert sind, können Sie sie über das Control Panel überwachen.

Damit können Sie sich alle Subdomains anzeigen lassen, die Sie Adobe Campaign zugewiesen haben, und die Verlängerung ihrer SSL-Zertifikate anfordern.

Weiterführende Informationen finden Sie im [entsprechenden Handbuch](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html?lang=de#subdomains-and-certificates).

>[!NOTE]
>
>Das [Control Panel](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=de) steht nur Kunden zur Verfügung, die Adobe Managed Services verwenden.
