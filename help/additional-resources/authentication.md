---
title: Authentifizierung
description: Erfahren Sie mehr über SPF, DKIM und DMARC-Authentifizierungsmethoden.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 03609139-b39b-4051-bcde-9ac7c5358b87
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 46%

---

# Authentifizierung

## SPF {#spf}

: SPF (Sender Policy Framework) ist ein Standard für die E-Mail-Authentifizierung, mit dem der Inhaber einer Domain angeben kann, welche E-Mail-Server E-Mails im Namen dieser Domain senden dürfen. Bei diesem Standard wird die Domain in der Kopfzeile &quot;Return-Path&quot; der E-Mail (auch als &quot;Envelope From&quot;-Adresse bezeichnet) genutzt.

>[!NOTE]
>
>Sie können [dieses externe Tool](https://www.kitterman.com/spf/validate.html) , um einen SPF-Eintrag zu überprüfen.

SPF ist eine Technik, mit der Sie in gewissem Umfang sicherstellen können, dass der in einer E-Mail verwendete Domain-Name nicht gefälscht wird. Wenn eine Nachricht von einer Domain empfangen wird, wird der DNS-Server der Domain abgefragt. Die Antwort ist ein kurzer Datensatz (der SPF-Datensatz), der angibt, welche Server für das Senden von E-Mails von dieser Domain autorisiert sind. Wenn wir davon ausgehen, dass nur der Eigentümer der Domain über die Mittel verfügt, um diesen Datensatz zu ändern, können wir davon ausgehen, dass mit dieser Technik die Absenderadresse nicht gefälscht werden kann, zumindest nicht der Teil rechts von „@“.

Im letzten [RFC 4408-Spezifikation](https://www.rfc-editor.org/info/rfc4408), werden zwei Elemente der Nachricht verwendet, um die Domain zu bestimmen, die als Absender gilt: die vom SMTP-Befehl &quot;HELO&quot;(oder &quot;EHLO&quot;) angegebene Domain und die von der Adresse des Headers &quot;Return-Path&quot;(oder &quot;MAIL FROM&quot;) angegebene Domain, die auch die Bounce-Adresse ist. Verschiedene Überlegungen ermöglichen es, nur einen dieser Werte zu berücksichtigen. Wir empfehlen, dass beide Quellen dieselbe Domain angeben.

Durch die Überprüfung des SPF ist eine Evaluierung der Gültigkeit der Absender-Domain gewährleistet.

* **Keines**: Es konnte keine Evaluierung durchgeführt werden.
* **Neutral**: Die abgefragte Domain ermöglicht keine Evaluierung.
* **Pass**: Die Domain gilt als echt.
* **Fail**: Die Domain ist gefälscht und die Nachricht sollte abgelehnt werden.
* **SoftFail**: Die Domain ist wahrscheinlich gefälscht, aber die Nachricht sollte nicht ausschließlich aufgrund dieses Ergebnisses abgelehnt werden.
* **TempError**: Ein temporärer Fehler hat die Evaluierung angehalten. Die Nachricht kann abgelehnt werden.
* **PermError**: Die SPF-Einträge der Domain sind ungültig.

Bitte beachten Sie, dass es bis zu 48 Stunden in Anspruch nehmen kann, bis in der Umgebung von DNS-Servern gemachte Einträge berücksichtigt werden. Die Dauer hängt davon ab, mit welcher Häufigkeit die DNS-Caches der Empfangs-Server aktualisiert werden.

## DKIM {#dkim}

Die DKIM-Authentifizierung (DomainKeys Identified Mail) ist ein Nachfolger von SPF. Es verwendet eine Verschlüsselung mit öffentlichen Schlüsseln, mit der der E-Mail-Empfangs-Server überprüfen kann, ob eine Nachricht tatsächlich von der angegebenen Person oder Organisation gesendet wurde und ob der Nachrichteninhalt zwischen dem Versandzeitpunkt (und dem &quot;Signieren&quot;von DKIM) und dem Empfangszeitpunkt verändert wurde. Bei diesem Standard wird in der Regel die Domain im &quot;Von&quot;- oder &quot;Absender&quot;-Header genutzt.

DKIM geht auf eine Kombination der Authentifizierungsprinzipien DomainKeys von Yahoo! und Identified Internet Mail von Cisco zurück und dient der Prüfung der Authentizität von Absender-Domains sowie der Sicherstellung der Integrität von Nachrichten.

DKIM hat sozusagen die **DomainKeys**-Authentifizierung ersetzt.

Für die Verwendung von DKIM müssen folgende Voraussetzungen gegeben sein:

* **Sicherheit**: Die Verschlüsselung ist ein Schlüsselelement des DKIM. Um das Sicherheitsniveau des DKIM sicherzustellen, empfiehlt sich die Verschlüsselungsgröße 1024b als Best Practice. Niedrigere DKIM-Schlüssel gelten von den meisten Zugangsanbietern nicht als gültig.
* **Reputation**: Die Reputation basiert auf der IP und/oder Domain, aber die weniger transparente DKIM-Auswahl ist auch ein Schlüsselelement, das berücksichtigt werden muss. Die Auswahl des Selektors ist wichtig: vermeiden Sie, die &quot;Standard&quot;, die von jedem verwendet werden könnte und daher eine schwache Reputation hat. Sie müssen einen anderen Selektor für **Treue- und Akquise-Kommunikation** und zur Authentifizierung.

Erfahren Sie mehr über DKIM-Voraussetzungen bei Verwendung von Campaign Classic in [diesem Abschnitt](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) ist die neueste Art der E-Mail-Authentifizierung. Bei der Entscheidung, ob eine E-Mail weitergeleitet wird oder fehlschlägt, kommt sowohl SPF- als auch DKIM-Authentifizierung zum Einsatz. DMARC ist einzigartig und auf zwei wichtige Arten leistungsstark:

* Konformität - ermöglicht es dem Absender, ISPs anzuweisen, was mit allen Nachrichten zu tun ist, die nicht authentifiziert werden können (z. B.: nicht akzeptieren).
* Berichterstellung : Dieser Bericht liefert dem Absender einen detaillierten Bericht, in dem alle Nachrichten, bei denen die DMARC-Authentifizierung fehlgeschlagen ist, sowie die jeweils verwendete &quot;Von&quot;-Domäne und IP-Adresse aufgeführt sind. Auf diese Weise kann ein Unternehmen legitime E-Mails identifizieren, die nicht authentifiziert werden können und eine Art &quot;Korrektur&quot;erfordern (z. B. das Hinzufügen von IP-Adressen zu seinem SPF-Datensatz) sowie die Quellen und die Häufigkeit von Phishing-Versuchen auf seinen E-Mail-Domains.

>[!NOTE]
>
>DMARC kann die von [250ok](https://250ok.com/) erstellten Berichte nutzen.
