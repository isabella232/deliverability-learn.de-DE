---
source-git-commit: 945a7ba5e3c3ac9544199e1bb62273933a82f04a
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 8%

---
# Erstellen einer Typologieregel zur Unterstützung von One-Click List-Unsubscribe:

**1. Erstellen Sie die neue Typologieregel:**
* Klicken Sie im Navigationsbaum auf &quot;neu&quot;, um eine neue Typologie zu erstellen.

![Bild](/help/assets/CreatingTypologyRules1.png)

**2. Fahren Sie mit der Konfiguration der Typologieregel fort:**
* Regeltyp: Kontrolle
* Phase: Zu Beginn der Zielgruppenbestimmung
* Kanal: E-Mail
* Ebene: Ihre Wahl
* Aktiv


![Bild](/help/assets/CreatingTypologyRules2.png)


**Code des JavaScripts der Typologieregel:**


>[!NOTE]
>
>Der unten beschriebene Code ist nur als Beispiel zu verwenden.
>In diesem Beispiel wird beschrieben, wie:
>* Konfigurieren Sie eine URL List-Unsubscribe und fügen Sie die Header hinzu oder hängen Sie die vorhandenen mailto: -Parameter an und ersetzen Sie sie durch: &lt;mailto..>>, https://..
>* Hinzufügen in der Kopfzeile List-Unsubscribe-Post
>Das Beispiel für die Post-URL verwendet var headerUnsubUrl = &quot;https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;
>* Sie können weitere Parameter hinzufügen (z. B. &amp;service = ...)
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


![Bild](/help/assets/CreatingTypologyRules3.png)

**3. Fügen Sie Ihre neue Regel zu einer Typologie zu einer E-Mail hinzu (Standardtypologie ist in Ordnung):**

![Bild](/help/assets/CreatingTypologyRules4.png)

**4. Vorbereitung eines neuen Versands (Überprüfung, ob zusätzliche SMTP-Header in der Versandeigenschaft leer sind)**

![Bild](/help/assets/CreatingTypologyRules5.png)

**5. Prüfen Sie während der Versandvorbereitung, ob Ihre neue Typologieregel angewendet wird.**

![Bild](/help/assets/CreatingTypologyRules6.png)



**6. Überprüfen Sie, ob List-Unsubscribe vorhanden ist.**

![Bild](/help/assets/CreatingTypologyRules7.png)
