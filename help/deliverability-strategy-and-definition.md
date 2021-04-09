---
title: Was ist die Zustellbarkeitsstrategie und wie wird die Zustellbarkeit definiert?
description: Erfahren Sie, wie die Zustellbarkeit definiert wird, warum sie wichtig ist und was die wichtigsten Zustellbarkeitsmetriken sind.
feature: Zustellbarkeit
topics: Deliverability
kt: 5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 5285eda9-5099-48d5-b150-ce2c376ee549
translation-type: ht
source-git-commit: e433002423bd1ab2f4a89425198c16160dae0719
workflow-type: ht
source-wordcount: '844'
ht-degree: 100%

---

# Strategie und Definition der Zustellbarkeit

Das Entwerfen erfolgreicher E-Mail-Marketing-Kampagnen hängt von einem klaren Verständnis der Marketing-Ziele ab, unabhängig davon, ob es sich um Initiativen für Interessenten oder CRM-Initiativen (Customer Relationship Management) handelt. Solche Kampagnen helfen zu bestimmen, wer angesprochen werden soll, was beworben werden soll und wann eine Zustellung ideal ist.

Im Folgenden finden Sie einige Beispiele für Ziele einer E-Mail-Marketing-Strategie:

* Akquise von Neukunden
* Umwandlung von Interessenten in Erstkäufer
* Ausbau bestehender Kundenbeziehungen durch zusätzliche Kundenangebote
* Bindung treuer Kunden
* Steigerung der Kundenzufriedenheit und Markentreue
* Reaktivierung verlorener oder ehemaliger Kunden

## Zustellbarkeit definiert

Es gibt zwei Schlüsselmetriken, die bei der Definition der Zustellbarkeit eine Rolle spielen. Die *Zustellrate* ist der Prozentsatz der E-Mails, die nicht fehlschlagen und vom ISP akzeptiert werden. Als Nächstes folgt die *Posteingangsplatzierung*. Diese wird auf die vom ISP akzeptierten Nachrichten angewandt und bestimmt, ob die E-Mail im Posteingang oder im Spam-Ordner landet.

Bei der Messung der E-Mail-Leistung ist es wichtig, die Zustellrate und die Posteingangsplatzierungsrate in Verbindung miteinander zu verstehen. Eine hohe Zustellrate ist nicht der einzige Aspekt der Zustellbarkeit. Nur weil eine Nachricht über den ersten Kontrollpunkt eines ISPs gesendet wird, bedeutet dies nicht unbedingt, dass ein Abonnent die Nachricht tatsächlich gesehen und mit ihr interagiert hat.

## Warum Zustellbarkeit wichtig ist

Sie sollten wissen, ob Ihre E-Mails zugestellt werden oder im Posteingang oder im Spam-Ordner landen. Der Grund dafür ist:

Unzählige Stunden fließen in die Planung und Produktion Ihrer E-Mail-Kampagnen. Wenn diese E-Mails abgewiesen werden oder im Spam-Ordner Ihrer Abonnenten landen, werden Ihre Kunden sie wahrscheinlich nicht lesen, Ihr Aufruf zum Handeln (CTA) wird nicht beachtet, und Sie werden Ihre Umsatzziele aufgrund verlorener Konversionen verfehlen. Einfach ausgedrückt: Sie können es sich nicht leisten, die Zustellbarkeit zu ignorieren. Sie ist von entscheidender Bedeutung für den Erfolg Ihrer E-Mail-Marketing-Aktivitäten und Ihren Gewinn.

Das Befolgen der Best Practices für die Zustellbarkeit stellt sicher, dass Ihre E-Mail die bestmögliche Chance auf Öffnungen, Klicks und das ultimative Ziel – die Konversion – hat. Sie können eine erstklassige Betreffzeile schreiben und schöne Bilder und ansprechende Inhalte haben. Wenn diese E-Mail jedoch nicht zugestellt wird, hat der Kunde keine Möglichkeit zum Kauf. Alles in allem ist für den Programmerfolg bei der E-Mail-Zustellbarkeit jeder Schritt im E-Mail-Annahmeprozess von dem jeweils vorherigen Schritt abhängig.

### Schritt 1: E-Mail zugestellt

Wichtige Faktoren für den Versand:

* **Solide Infrastruktur**: IP- und Domain-Konfiguration, Einrichtung einer Feedback-Schleife (FBL) (einschließlich Überwachung und Verarbeitung von Beschwerden) und regelmäßige Bounce-Verarbeitung. Bei Adobe-Kunden ist Adobe für diese Einrichtung im Auftrag der Kunden verantwortlich.
* **Starke Authentifizierung**: [!DNL Sender Policy Framework] (SPF), [!DNL DomainKeys Identified Mail] (DKIM), [!DNL Domain-based Message Authentication]Reporting und Konformität (DMARC).
* **Hohe Listenqualität**: Explizites Opt-in, gültige E-Mail-Akquisemethoden und Interaktionsrichtlinien.
* **Konsistente Versandkadenz und Minimierung von Volumenschwankungen**.
* **Hohe IP- und Domain-Reputation**.

### Schritt 2: Posteingangsplatzierung der E-Mail

ISPs verfügen über spezifische, komplexe und sich ständig ändernde Algorithmen, um festzustellen, ob Ihre E-Mail im Posteingang, im Spam-Ordner oder im Junk-Ordner abgelegt wird.

Hier einige wichtige Faktoren für die Platzierung im Posteingang:

* Zugestellte E-Mail
* Hohe Interaktion
* Geringe Beschwerden (insgesamt weniger als 0,1 %)
* Konsistentes Volumen
* Wenige Spam-Fallen
* Niedrige Hardbounce-Rate
* Keine Probleme mit Blockierungslisten

### Schritt 3: E-Mail-Interaktion – Öffnungen

Hier einige wichtige Faktoren für die Öffnungsrate:

* E-Mail zugestellt und im Posteingang gelandet
* Markenbekanntheit
* Überzeugende Betreffzeile und Preheader
* Personalisierung
* Häufigkeit
* Relevanz oder Wert des Inhalts

### Schritt 4: E-Mail-Interaktion – Klicks

Hier einige wichtige Faktoren für die Klickrate:

* E-Mail zugestellt, im Posteingang gelandet und geöffnet
* Starker CTA
   * Dies ist die primäre Aktion, die Sie von Ihrer Audience erreichen möchten. Normalerweise ist dies ein Klick auf eine URL. Stellen Sie sicher, dass diese klar und für den Benutzer leicht zu finden ist.
* Relevanz oder Wert des Inhalts

### Schritt 5: Konversion

Hier einige wichtige Faktoren für die Konversion:

* Alle oben genannten Punkte
* Weiterleitung von der E-Mail über eine funktionierende URL zu einer Landingpage oder Verkaufsseite
* Landingpage-Erlebnis
* Markenbekanntheit, -wahrnehmung und -loyalität

### Mögliche Auswirkungen auf den Umsatz

Konversion ist wichtig, aber was ist die Alternative? Ihre Zustellbarkeitsstrategie kann das E-Mail-Marketing-Programm stärken oder zerstören. Die folgende Tabelle zeigt den potenziellen Umsatzverlust, den eine schwache Zustellbarkeitsrichtlinie für Ihr Marketing-Programm bewirken kann. Wie gezeigt, entspricht für ein Unternehmen mit einer Konversionsrate von 2 Prozent und einem durchschnittlichen Kaufpreis von 100 US-Dollar jede Reduzierung der Posteingangsplatzierung um 10 Prozent einem Umsatzverlust von fast 20.000 US-Dollar. Denken Sie daran, dass diese Zahlen für jeden Absender spezifisch sind.

| Gesendet | Prozent | zugestellt | Prozent | Posteingang | Anzahl nicht im Posteingang | Konversionsrate | Anzahl der verlorenen | Durchschnittlicher | Verlorener |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|  | Zugestellt |  | Posteingang |  |  |  | Konversionen | Kauf | Umsatz |
| 100.000 | 99 % | 99.000 | 100 % | 99.000 | – | 2 % | 0 | $ 100 | $ - |
| 100.000 | 99 % | 99.000 | 90 % | 89.100 | 9.900 | 2 % | 198 | $ 100 | $ 19.800 |
| 100.000 | 99 % | 99.000 | 80 % | 79.200 | 19.800 | 2 % | 396 | $ 100 | $ 39.600 |
| 100.000 | 99 % | 99.000 | 70 % | 69.300 | 29.700 | 2 % | 594 | $ 100 | $ 59.400 |
| 100.000 | 99 % | 99.000 | 60 % | 59.400 | 39.600 | 2 % | 792 | $ 100 | $ 79.200 |
| 100.000 | 99 % | 99.000 | 50 % | 49.500 | 49.500 | 2 % | 990 | $ 100 | $ 99.000 |
| 100.000 | 99 % | 99.000 | 40 % | 39.600 | 59.400 | 2 % | 1.188 | $ 100 | $ 118.800 |
| 100.000 | 99 % | 99.000 | 30 % | 29.700 | 69.300 | 2 % | 1.386 | $ 100 | $ 138.600 |
| 100.000 | 99 % | 99.000 | 20 % | 19.800 | 79.200 | 2 % | 1.584 | $ 100 | $ 158.400 |
