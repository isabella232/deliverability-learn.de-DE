---
title: Authentifizierung
description: Weitere Informationen zu SPF-, DKIM- und DMARC-Authentifizierungsmethoden.
feature: Zusätzliche Ressourcen
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 47%

---


# Authentifizierung

## SPF {#spf}

: SPF (Sender Policy Framework) ist ein Standard für die E-Mail-Authentifizierung, mit dem der Inhaber einer Domain angeben kann, welche E-Mail-Server E-Mails im Namen dieser Domain senden dürfen. Bei diesem Standard wird die Domain in der Kopfzeile &quot;Return-Path&quot; der E-Mail (auch als &quot;Envelope From&quot;-Adresse bezeichnet) genutzt.

>[!NOTE]
>
>Sie können [dieses externe Tool](https://www.kitterman.com/spf/validate.html) verwenden, um einen SPF-Datensatz zu überprüfen.

SPF ist eine Technik, mit der Sie in gewissem Umfang sicherstellen können, dass der in einer E-Mail verwendete Domain-Name nicht gefälscht wird. Wenn eine Nachricht von einer Domain empfangen wird, wird der DNS-Server der Domain abgefragt. Die Antwort ist ein kurzer Datensatz (der SPF-Datensatz), der angibt, welche Server für das Senden von E-Mails von dieser Domain autorisiert sind. Wenn wir davon ausgehen, dass nur der Eigentümer der Domain über die Mittel verfügt, um diesen Datensatz zu ändern, können wir davon ausgehen, dass mit dieser Technik die Absenderadresse nicht gefälscht werden kann, zumindest nicht der Teil rechts von „@“.

In der endgültigen Spezifikation [RFC 4408](https://www.rfc-editor.org/info/rfc4408) werden zwei Elemente der Nachricht verwendet, um die Domäne zu bestimmen, die als Absender gilt: die Domäne, die vom SMTP-Befehl &quot;HELO&quot; (oder &quot;EHLO&quot;) angegeben wird, und die Domäne, die von der Adresse des Headers &quot;Return-Path&quot;(oder &quot;MAIL VON&quot;) angegeben wird, die auch die Absprungadresse ist. Verschiedene Überlegungen ermöglichen es, nur einen dieser Werte zu berücksichtigen. Wir empfehlen, dass beide Quellen dieselbe Domain angeben.

Durch die Überprüfung des SPF ist eine Evaluierung der Gültigkeit der Absender-Domain gewährleistet.

* **Keine**: Es konnte keine Bewertung durchgeführt werden.
* **Neutral**: Die abgefragte Domäne ermöglicht keine Auswertung.
* **Übergeben**: Die Domäne gilt als authentisch.
* **Fehler**: Die Domäne wird gefälscht und die Nachricht sollte zurückgewiesen werden.
* **SoftFail**: Die Domäne ist wahrscheinlich gefälscht, aber die Nachricht sollte nicht allein aufgrund dieses Ergebnisses abgelehnt werden.
* **TempError**: Ein temporärer Fehler hat die Evaluierung angehalten. Die Nachricht kann abgelehnt werden.
* **PermError**: Die SPF-Einträge der Domain sind ungültig.

Bitte beachten Sie, dass es bis zu 48 Stunden in Anspruch nehmen kann, bis in der Umgebung von DNS-Servern gemachte Einträge berücksichtigt werden. Die Dauer hängt davon ab, mit welcher Häufigkeit die DNS-Caches der Empfangs-Server aktualisiert werden.

## DKIM {#dkim}

Die DKIM-Authentifizierung (DomainKeys Identified Mail) ist eine Nachfolgerin von SPF. Es verwendet eine Kryptographie mit öffentlichem Schlüssel, mit der der Empfänger-E-Mail-Server überprüfen kann, ob eine Nachricht tatsächlich von der Person oder Organisation gesendet wurde, von der sie angeblich gesendet wurde, und ob der Inhalt der Nachricht zwischen dem Zeitpunkt des ursprünglichen Versands (und dem &quot;Signieren&quot; von DKIM) und dem Zeitpunkt des Eingangs geändert wurde. Bei diesem Standard wird in der Regel die Domain im &quot;Von&quot;- oder &quot;Absender&quot;-Header genutzt.

DKIM geht auf eine Kombination der Authentifizierungsprinzipien DomainKeys von Yahoo! und Identified Internet Mail von Cisco zurück und dient der Prüfung der Authentizität von Absender-Domains sowie der Sicherstellung der Integrität von Nachrichten.

DKIM hat sozusagen die **DomainKeys**-Authentifizierung ersetzt.

Für die Verwendung von DKIM müssen folgende Voraussetzungen gegeben sein:

* **Sicherheit**: Die Verschlüsselung ist ein Schlüsselelement des DKIM. Um den Sicherheitsgrad des DKIM zu gewährleisten, empfiehlt sich eine Verschlüsselungsgröße von 1024b. Niedrigere DKIM-Schlüssel werden von den meisten Zugangsanbietern nicht als gültig angesehen.
* **Reputation**: Der Ruf basiert auf der IP und/oder der Domäne, aber der weniger transparente DKIM-Selektor ist auch ein Schlüsselelement, das berücksichtigt werden muss. Die Auswahl der Auswahl ist wichtig: vermeiden Sie, die &quot;Standard&quot;, die von jedem verwendet werden könnte und daher einen schwachen Ruf hat. Sie müssen einen anderen Selektor für **Retention vs Akquise Communications** und für die Authentifizierung implementieren.

Erfahren Sie mehr über die Voraussetzung für DKIM bei Verwendung von Campaign Classic in [diesem Abschnitt](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) ist die neueste Art der E-Mail-Authentifizierung. Bei der Entscheidung, ob eine E-Mail weitergeleitet wird oder fehlschlägt, kommt sowohl SPF- als auch DKIM-Authentifizierung zum Einsatz. DMARC ist einzigartig und leistungsstark in zweierlei Hinsicht:

* Konformität: Sie ermöglicht es dem Absender, die ISPs anzuweisen, wie mit jeder Meldung zu verfahren ist, die sich nicht authentifizieren kann (z. B.: nicht akzeptieren).
* Berichte - es stellt dem Absender einen detaillierten Bericht mit allen Meldungen zur Verfügung, die bei der DMARC-Authentifizierung fehlgeschlagen sind, sowie der jeweils verwendeten &quot;Von&quot;-Domäne und IP-Adresse. Dies ermöglicht es einer Firma, legitime E-Mails zu identifizieren, die nicht authentifiziert werden können und eine Art &quot;Korrektur&quot;benötigen (z. B. das Hinzufügen von IP-Adressen zu ihrem SPF-Datensatz), sowie die Quellen und die Häufigkeit von Phishing-Versuchen auf ihren E-Mail-Domänen.

>[!NOTE]
>
>DMARC kann die von [250ok](https://250ok.com/) erstellten Berichte nutzen.
