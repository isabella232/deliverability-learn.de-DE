---
title: Campaign Classic – Technische Empfehlungen
description: Entdecken Sie Techniken, Konfigurationen und Werkzeuge zur Verbesserung Ihrer Zustellrate mit Adobe Campaign Classic.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 39ed3773-18bf-4653-93b6-ffc64546406b
source-git-commit: b5e1d878c889112e08da0969d50bdb3c72e48f8c
workflow-type: tm+mt
source-wordcount: '1899'
ht-degree: 55%

---

# Campaign Classic – Technische Empfehlungen {#technical-recommendations}

Nachfolgend sind verschiedene Techniken, Konfigurationen und Tools aufgeführt, mit denen Sie Ihre Zustellrate bei Verwendung von Adobe Campaign Classic verbessern können.

## Konfiguration {#configuration}

### Reverse DNS {#reverse-dns}

: Adobe Campaign prüft, ob für eine IP-Adresse ein Reverse-DNS angegeben ist und ob dieses wirklich auf die IP-Adresse zurückverweist.

Bei der Netzwerkkonfiguration ist es wichtig sicherzustellen, dass für jede der für ausgehende Nachrichten bestimmten IP-Adressen ein korrektes Reverse-DNS angegeben ist. Für eine bestimmte IP-Adresse existiert also ein Reverse-DNS Datensatz (PTR-Datensatz) mit einem passenden DNS (Datensatz), das auf die ursprüngliche IP zurückverweist.

Die Wahl der Domain für ein Reverse DNS hat Auswirkungen auf den Umgang mit bestimmten ISPs. Insbesondere AOL akzeptiert nur Feedback-Schleifen mit einer Adresse in derselben Domain wie das Reverse DNS (siehe [Feedback Loop](#feedback-loop)).

>[!NOTE]
>
>Sie können [dieses externe Tool](https://mxtoolbox.com/SuperTool.aspx) , um die Konfiguration einer Domain zu überprüfen.

### MX-Regeln {#mx-rules}

MX-Regeln (Mail eXchanger) dienen zur Verwaltung der Kommunikation zwischen einem Sende- und einem Empfangs-Server.

Genauer gesagt werden sie verwendet, um die Geschwindigkeit zu steuern, mit der der Adobe Campaign MTA (Message Transfer Agent) E-Mails an jede E-Mail-Domain oder jeden ISP sendet (z. B. hotmail.com, comcast.net). Diese Regeln basieren in der Regel auf Beschränkungen, die von den ISPs veröffentlicht werden (z. B. nicht mehr als 20 Nachrichten pro SMTP-Verbindung).

>[!NOTE]
>
>Weitere Informationen zur MX-Verwaltung in Adobe Campaign Classic finden Sie unter [diesem Abschnitt](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration).

### TLS {#tls}

: TLS (Transport Layer Security) ist ein Verschlüsselungsprotokoll zur Sicherung der Verbindung zwischen zwei E-Mail-Servern. Damit wird sichergestellt, dass die E-Mail nur vom beabsichtigten Empfänger gelesen werden kann.

### Domain des Absenders {#sender-domain}

Um die für den HELO-Befehl verwendete Domain zu definieren, bearbeiten Sie die Konfigurationsdatei der Instanz (conf/config-instance.xml) und definieren Sie das Attribut &quot;localDomain&quot; wie folgt:

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

Die Domäne MAIL FROM ist die Domäne, die in technischen Bounce Messages verwendet wird. Diese Adresse wird im Softwareverteilungs-Assistenten oder über die Option NmsEmail_DefaultErrorAddr definiert.

### SPF-Datensatz {#dns-configuration}

Ein SPF-Eintrag kann derzeit auf einem DNS-Server als TXT-Eintrag (Code 16) oder als SPF-Eintrag (Code 99) definiert werden. Ein SPF-Datensatz hat die Form einer Zeichenfolge. Beispiel:

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

definiert die beiden IP-Adressen 12.34.56.78 und 12.34.56.79 als berechtigt, E-Mails für die Domain zu senden. **~all** bedeutet, dass jede andere Adresse als SoftFail interpretiert werden sollte.

Recommendations zum Definieren eines SPF-Datensatzes:

* Hinzufügen **~all** (SoftFail) **-all** (Fehler) am Ende alle Server mit Ausnahme der definierten zurückweisen. Andernfalls können Server diese Domain (mit einer neutralen Auswertung) fälschen.
* Nicht hinzufügen **ptr** (openspf.org empfiehlt dies als kostspielig und unzuverlässig).

>[!NOTE]
>
>Weitere Informationen zu SPF finden Sie unter [diesem Abschnitt](/help/additional-resources/authentication.md#spf).

## Authentifizierung

>[!NOTE]
>
>Erfahren Sie mehr über die verschiedenen Formen der E-Mail-Authentifizierung in [diesem Abschnitt](/help/additional-resources/authentication.md).

### DKIM {#dkim-acc}

>[!NOTE]
>
>Bei gehosteten oder hybriden Installationen erfolgt die DKIM-E-Mail-Authentifizierungssignatur für alle Nachrichten mit allen Domains durch den Enhanced MTA, wenn Sie auf den [Enhanced MTA](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages) aktualisiert haben.

Verwenden [DKIM](/help/additional-resources/authentication.md#dkim) Für Adobe Campaign Classic ist die folgende Voraussetzung erforderlich:

**Adobe Campaign-Optionsdeklaration**: In Adobe Campaign basiert der private DKIM-Schlüssel auf einem DKIM-Selektor und einer Domäne. Es ist derzeit nicht möglich, mehrere private Schlüssel für dieselbe Domäne/Subdomäne mit verschiedenen Selektoren zu erstellen. Es ist nicht möglich zu definieren, welche Selektordomäne/Subdomäne für die Authentifizierung in weder der Plattform noch der E-Mail verwendet werden muss. Die Plattform wählt alternativ einen der privaten Schlüssel aus, was bedeutet, dass die Authentifizierung mit hoher Wahrscheinlichkeit fehlschlägt.

* Wenn Sie DomainKeys für Ihre Adobe Campaign-Instanz konfiguriert haben, müssen Sie nur **dkim** in den [Domain-Verwaltungsregeln](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules) auswählen. Wenn nicht, führen Sie dieselben Konfigurationsschritte (privater/öffentlicher Schlüssel) wie für DomainKeys aus (der DKIM ersetzt hat).
* Es ist nicht notwendig, sowohl DomainKeys als auch DKIM für dieselbe Domain zu aktivieren, da es sich bei DKIM um eine verbesserte Version von DomainKeys handelt.
* Folgende Domains validieren aktuell DKIM: AOL, Gmail.

## Feedback Loop {#feedback-loop-acc}

Eine Feedback-Schleife funktioniert, indem auf der ISP-Ebene eine bestimmte E-Mail-Adresse für einen Bereich von IP-Adressen angegeben wird, der zum Senden von Nachrichten verwendet wird. Der ISP wird die Nachrichten, die von Empfängern als Spam gemeldet werden, auf ähnliche Weise an diesen Posteingang senden wie bei Bounce-Nachrichten. Die Plattform sollte so konfiguriert sein, dass zukünftige Sendungen für Benutzer, die sich beschwert haben, blockiert werden. Es ist wichtig, dass sie nicht mehr kontaktiert werden, auch wenn sie nicht den richtigen Ausschluss-Link verwendet haben. Auf der Grundlage dieser Beschwerden fügt ein ISP seiner Blockierungsliste eine IP-Adresse hinzu. Je nach ISP wird eine Beschwerderate von etwa 1 % dazu führen, dass eine IP-Adresse blockiert wird.

Aktuell wird an der Konzeption eines Standards für das Format von Feedback-Loop-Nachrichten gearbeitet: das [Abuse Feedback Reporting Format (ARF)](https://tools.ietf.org/html/rfc6650).

Zur Implementierung eines Feedback Loops für eine Instanz sind folgende Elemente erforderlich:

* ein für die Instanz bestimmtes Postfach, bei dem es sich um das Bounce-Postfach handeln kann,
* für die Instanz bestimmte IP-Versandadressen.

Die Implementierung eines einfachen Feedback Loop in Adobe Campaign verwendet die Bounce-Nachrichtenfunktionalität. Das Feedback Loop-Postfach wird als ein Bounce-Postfach verwendet. Es wird eine Regel zur Erkennung dieser Nachrichten definiert. Die E-Mail-Adressen der Empfänger, die die Nachricht als Spam gemeldet haben, werden der Quarantäneliste hinzugefügt.

* Erstellen oder bearbeiten Sie im Knoten **[!UICONTROL Administration > Kampagnen > Unzustellbarkeitsverwaltung > E-Mail-Regeln]** eine Bounce-Message-Regel **Feedback_loop** und geben Sie dabei den Grund **Abgelehnt** sowie den Typ **Hard** an.
* Wenn speziell für das Feedback Loop ein Postfach definiert wurde, definieren Sie die dafür geltenden Zugriffsparameter, indem Sie unter **[!UICONTROL Administration > Plattform > Externe Konten]** ein neues externes Bounce-Message-Konto erstellen.

Der Mechanismus zur Verarbeitung von Beschwerdebenachrichtigungen ist sofort funktionstüchtig. Um die korrekte Funktionsweise der Regel sicherzustellen, können Sie die Konten zeitweise deaktivieren, damit sie diese Nachrichten nicht abrufen. Sie können die Inhalte des Feedback-Loop-Postfachs dann manuell überprüfen. Führen Sie auf dem Server die folgenden Befehle aus:

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Sollten Sie gezwungen sein, eine einzige Feedback-Loop-Adresse für mehrere Instanzen zu verwenden, müssen Sie:

* die empfangenen Nachrichten auf so vielen Postfächern replizieren wie Instanzen vorhanden sind,
* dafür sorgen, dass jedes Postfach von einer einzigen Instanz abgerufen wird,
* Konfigurieren Sie die Instanzen so, dass sie nur die Nachrichten verarbeiten, die sie betreffen: Die Instanzinformationen sind im Nachrichten-ID-Header der von Adobe Campaign gesendeten Nachrichten enthalten und befinden sich daher auch in den Feedback Loop-Nachrichten. Geben Sie einfach den Parameter **checkInstanceName** in der Konfigurationsdatei der Instanz an (standardmäßig wird die Instanz nicht überprüft, was dazu führen kann, dass bestimmte Adressen falsch unter Quarantäne gestellt werden):

  ```
  <serverConf>
    <inMail checkInstanceName="true"/>
  </serverConf>
  ```

Der Zustellbarkeitsdienst in Adobe Campaign sorgt für die Verwaltung Ihrer Anmeldung für Feedback-Loop-Dienste für die folgenden ISPs: AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe}

### Über List-Unsubscribe {#about-list-unsubscribe}

Hinzufügen eines SMTP-Headers namens **List-Unsubscribe** ist zwingend erforderlich, um eine optimale Verwaltung der Zustellbarkeit zu gewährleisten. Ab dem 1. Juni 2024 verlangen Yahoo und Gmail von Absendern, dass sie One-Click List-Unsubscribe einhalten. Informationen zum Konfigurieren von One-Click List-Unsubscribe finden Sie unter [diesem Abschnitt](#one-click-list-unsubscribe).


Diese Kopfzeile kann als Alternative zum Symbol &quot;Als SPAM melden&quot;verwendet werden. Er wird in der E-Mail-Oberfläche als Abmelde-Link angezeigt.

Durch die Verwendung dieser Funktion können Sie Ihre Reputation schützen und das Feedback wird als Abmeldung ausgeführt.

Um List-Unsubscribe zu verwenden, müssen Sie eine Befehlszeile eingeben, die in etwa wie folgt aussieht:

```
List-Unsubscribe: <mailto:client@newsletter.example.com?subject=unsubscribe?body=unsubscribe>
```

>[!CAUTION]
>
>Das oben stehende Beispiel basiert auf der Empfängertabelle. Sollte die Datenbankimplementierung über eine andere Tabelle erfolgen, stellen Sie bitte sicher, dass Sie die Befehlszeile mit den korrekten Informationen umformulieren.

Die folgende Befehlszeile kann zum Zweck der Erstellung eines dynamischen **List-Unsubscribe** verwendet werden:

```
List-Unsubscribe: <mailto:<%=errorAddress%>?subject=unsubscribe%=message.mimeMessageId%>
```

Gmail, Outlook.com und Microsoft Outlook unterstützen diese Methode und eine Abmelde-Schaltfläche ist direkt in ihrer Benutzeroberfläche verfügbar. Diese Technik senkt die Beschwerderaten.

Sie können die **List-Unsubscribe** entweder:

* Direkt [Hinzufügen der Befehlszeile in der Versandvorlage](#adding-a-command-line-in-a-delivery-template)
* [Erstellung einer Typologieregel](#creating-a-typology-rule)

### Hinzufügen einer Befehlszeile in einer Versandvorlage {#adding-a-command-line-in-a-delivery-template}

Die Befehlszeile muss im Zusatzabschnitt des SMTP-Headers der E-Mail hinzugefügt werden.

Das kann entweder in jeder E-Mail oder in bereits existierenden Versandvorlagen erfolgen. Sie haben außerdem die Möglichkeit, eine neue diese Funktion beinhaltende Versandvorlage zu erstellen.

List-Unsubscribe: mailto:unsubscribe@domain.com
* Klicken Sie auf **unsubscribe** -Link öffnet den Standard-E-Mail-Client des Benutzers. Diese Typologieregel muss in einer Typologie zur Erstellung von E-Mails hinzugefügt werden.

List-Unsubscribe: https://domain.com/unsubscribe.jsp
* Klicken Sie auf **unsubscribe** -Link leitet den Benutzer zu Ihrem Abmeldeformular weiter.

![Bild](../assets/UTF-8-1.png)


### Erstellung einer Typologieregel {#creating-a-typology-rule}

Die Regel muss das Script zur Erzeugung der Befehlszeile beinhalten und im E-Mail-Header enthalten sein.

>[!NOTE]
>
>Es wird empfohlen, eine Typologieregel zu erstellen: Die List-Unsubscribe-Funktion wird automatisch zu jeder E-Mail hinzugefügt.

>[!NOTE]
>
>Erfahren Sie, wie Sie in Adobe Campaign Classic Typologieregeln erstellen. [diesem Abschnitt](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules).

### 1-Klick-Liste Abmeldung {#one-click-list-unsubscribe}

Ab dem 1. Juni 2024 verlangen Yahoo und Gmail von Absendern, dass sie One-Click List-Unsubscribe einhalten. Zur Einhaltung der 1-Klick-List-Unsubscribe-Anforderung müssen Absender:

1. Fügen Sie &quot;List-Unsubscribe-Post: List-Unsubscribe=One-Click&quot;hinzu.
2. Link zum Abmelden von URIs einschließen
3. Unterstützung des Erhalts der HTTP-POST-Antwort vom Empfänger, die von Adobe Campaign unterstützt wird.

So konfigurieren Sie One-Click List-Unsubscribe direkt:

* Fügen Sie in der folgenden Webanwendung zum Abmelden von Empfängern ohne Klick hinzu: 
   1. Gehen Sie zu Ressourcen > Online > Webanwendungen .
   2. Laden Sie &quot;Empfänger abmelden ohne Klick&quot; hoch. [XML](/help/assets/WebAppUnsubNoClick.xml.zip)
* Konfigurieren von List-Unsubscribe und List-Unsubscribe-Post
   1. Gehen Sie zum Abschnitt SMTP in den Versandeigenschaften.
   2. Geben Sie unter Zusätzliche SMTP-Header in die Befehlszeilen ein (jeder Header sollte sich in einer separaten Zeile befinden):

```
List-Unsubscribe-Post: List-Unsubscribe=One-Click
List-Unsubscribe: <https://domain.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %> >, < mailto:<%@ include option='NmsEmail_DefaultErrorAddr' %>?subject=unsubscribe<%=escape(message.mimeMessageId) %> >
```

Im obigen Beispiel wird die einmalige List-Unsubscribe für ISPs aktiviert, die One-Click unterstützen. Gleichzeitig wird sichergestellt, dass Empfänger, die URL-list-unsubscribe nicht unterstützen, weiterhin eine Abmeldung per E-Mail anfordern können.


### Erstellen einer Typologieregel zur Unterstützung von „List-Unsubscribe“ durch einen Klick:

**1. Erstellen einer neuen Typologieregel:**

* Klicken Sie im Navigationsbaum auf „neu“, um eine neue Typologie zu erstellen

![Bild](../assets/CreatingTypologyRules1.png)


**2. Fahren Sie mit der Konfiguration der Typologieregel fort:**

* Regeltyp: Kontrolle
* Phase: Zu Beginn der Zielgruppenbestimmung
* Kanal: E-Mail
* Ebene: Ihre Wahl
* Aktiv


![Bild](../assets/CreatingTypologyRules2.png)


**Code des JavaScripts der Typologieregel:**


>[!NOTE]
>
>Der unten beschriebene Code ist nur als Beispiel zu verwenden.
>In diesem Beispiel wird Folgendes beschrieben:
>* Konfigurieren Sie eine List-Unsubscribe-URL und fügen Sie die Header hinzu oder hängen Sie die vorhandenen „mailto:“-Parameter an und ersetzen Sie sie durch: „&lt;mailto..>, https://…“
>* Hinzufügen des Post-Headers „List-Unsubscribe“
>Das Beispiel für die Post-URL verwendet var headerUnsubUrl = &quot;https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;÷
>* Sie können weitere Parameter hinzufügen (z. B. &amp;service = ...)
>


```
// Function to add or replace a header in the provided headers 
function addHeader(headers, header, value)  { 
    
  // Create the new header line 
  var headerLine = header + ": " + value; 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop through each line 
  for (var i=0; i < headerLines.length; i++) { 
      
    // Check if the specified header exists 
    var match = headerLines[i].match(regExp) 
      
    // If it exists 
    if ( match != null ) { 
        
      // Replace the existing header line 
      headerLines[i] = headerLine; 
        
      // Return the modified headers 
      return headerLines.join("\n"); 
    } 
  } 
    
  // If the header does not exist, add the new header line 
  headerLines.push(headerLine); 
    
  // Return the modified headers 
  return headerLines.join("\n"); 
} 
  
// Function to get the value of a specified header from the provided headers 
function getHeader(headers, header) { 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop each line 
  for each (line in headerLines) { 
      
    // Check if the specified header exists 
    var match = line.match(regExp); 
      
    // If it exists 
    if ( match != null ) { 
        
      // Return the header value, removing leading whitespace 
      return match[1].replace(/^\s*/, ""); 
    } 
  } 
    
  // If the header does not exist, return an empty string 
  return ""; 
} 
  
  
// Define the unsubscribe URL 
var headerUnsubUrl = "https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"; 
  
// Get the value of the List-Unsubscribe header 
var headerUnsub = getHeader(delivery.mailParameters.headers, "List-Unsubscribe"); 
  
// If the List-Unsubscribe header does not exist 
if ( headerUnsub === "" ) { 
  // Add the List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
// If the List-Unsubscribe header exists and contains 'mailto' 
else if(headerUnsub.search('mailto')){ 
  // Replace the existing List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
  
// Get the value of the List-Unsubscribe-Post header 
var headerUnsubPost = getHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post"); 
  
// If the List-Unsubscribe-Post header does not exist 
if ( headerUnsubPost === "" ) { 
  // Add the List-Unsubscribe-Post header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post", "List-Unsubscribe=One-Click"); 
} 
  
// Return true to indicate success 
return true; 
```


![Bild](../assets/CreatingTypologyRules3.png)



**3. Fügen Sie Ihre neue Regel zu einer Typologie zu einer E-Mail hinzu (die Standardtypologie ist in Ordnung):**

![Bild](../assets/CreatingTypologyRules4.png)



**4. Vorbereitung eines neuen Versands (Überprüfen Sie, ob zusätzliche SMTP-Header in der Versandeigenschaft leer sind)**

![Bild](../assets/CreatingTypologyRules5.png)



**5. Prüfen Sie während der Versandvorbereitung, ob Ihre neue Typologieregel angewendet wird.**

![Bild](../assets/CreatingTypologyRules6.png)



**6. Überprüfen Sie, ob „List-Unsubscribe“ vorhanden ist.**

![Bild](../assets/CreatingTypologyRules7.png)


## E-Mail-Optimierung {#email-optimization}

### SMTP {#smtp}

SMTP (Simple Mail Transfer Protocol) ist ein Internet-Standard für die E-Mail-Übertragung.

Die SMTP-Fehler, die nicht von einer Regel überprüft werden, werden im Abschnitt **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Verwaltung von Fehlern]** > **[!UICONTROL Versandlogqualifizierung]** Ordner. Diese Fehlermeldungen werden standardmäßig als unerreichbare Softbounces interpretiert.

Die häufigsten Fehler müssen identifiziert und eine entsprechende Regel hinzugefügt werden in **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Verwaltung von Fehlern]** > **[!UICONTROL Mail-Regelsätze]** , wenn Sie das Feedback von den SMTP-Servern richtig qualifizieren möchten. Andernfalls führt die Plattform nach einer bestimmten Anzahl von Tests unnötige Versuche durch (im Fall unbekannter Benutzer) oder platziert bestimmte Empfänger fälschlicherweise unter Quarantäne.

### Dedizierte IPs {#dedicated-ips}

Adobe bietet jedem Kunden für die Anlaufphase eine dedizierte IP-Strategie zum Aufbau der Reputation und zur Optimierung der Zustellbarkeit.
