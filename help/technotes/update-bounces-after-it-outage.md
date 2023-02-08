---
title: Aktualisierung der Bounce-Qualifizierung nach Italia Online-Ausfall
description: Erfahren Sie, wie Sie die Bounce-Qualifizierung nach einem Online-Ausfall von Italia aktualisieren
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
hidefromtoc: true
source-git-commit: 016d7f9da67193d893e762fbe6e191cf87d5b030
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 21%

---

# Aktualisieren falscher Hardbounces nach Italia Online-Ausfall {#update-bounce-italia}

## Kontext{#outage-context}

Seit dem 22. Januar (Ortszeit) ist Italia Online durch einen Ausfall gekennzeichnet, der zu mehreren Verzögerungen und Zurückweisungen von E-Mails geführt hat. Der Service begann am 26. Januar mit begrenzter Kapazität wieder aufzunehmen.

Betroffene Domänen sind: **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** und **blu.it**.

Dieses Problem trat vom 22.1.2023 bis zum 26.1.2023 auf, aber die meisten fälschlich unter Quarantäne gestellten Fälle wurden am 26. Januar durchgeführt.

Weitere Informationen finden Sie in der offiziellen Mitteilung [here](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Wirkung{#outage-impact}

Wie in den meisten Fällen, in denen ein ISP ausfällt, wurden einige über Campaign gesendete E-Mails fälschlicherweise als Bounces markiert. Dies wirkte sich nicht nur auf die Adobe aus, sondern alle, die versuchen, während des Ausfalls E-Mails an Italia Online zukommen zu lassen.

Die Symptome waren:

* **Rückstellung** mit der Nachricht `452 requested action aborted: try again later` - diese wurden automatisch wiederholt und es sind keine Aktionen erforderlich.

* **Hardbounces** mit der Nachricht `550 <email address> recipient rejected` wurden vom ISP am 26. Januar zwischen 8:00 und 14:00 Uhr Ortszeit zurückgegeben, um zu verhindern, dass Absender ihre Server weiterhin überlasten. Wie vom Italia Online Postmaster bestätigt, handelt es sich hierbei nicht um echte Hardbounces. Daher empfehlen wir, die Quarantäne für alle E-Mail-Adressen aufzuheben, die am 26. Januar 2023 aufgrund dieser Nachricht ausgeschlossen wurden.

## Aktualisierungsprozess{#outage-update}

### Adobe Campaign{#ac-update}

Gemäß der Standardlogik für die Behandlung von Bounces hat Adobe Campaign diese Empfänger automatisch der Quarantäneliste mit dem **[!UICONTROL Status]** **[!UICONTROL Quarantäne]** hinzugefügt. Um dies zu korrigieren, müssen Sie Ihre Quarantänetabelle in Campaign aktualisieren, indem Sie diese Empfänger finden und entfernen oder ihren **[!UICONTROL Status]** auf **[!UICONTROL Gültig]** ändern, damit der nächtliche Bereinigungs-Workflow sie entfernt.

Um die Empfänger zu finden, die von diesem Problem betroffen waren, oder für den Fall, dass dies bei einem anderen ISP erneut auftritt, lesen Sie bitte die folgenden Anweisungen:

* Campaign Classic v7 und Campaign v8 finden Sie unter [diese Seite](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Campaign Standard finden Sie unter [diese Seite](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

Gemäß der standardmäßigen Bounce-Verarbeitungslogik hat Adobe Journey Optimizer diese E-Mail-Adressen automatisch mit einer **[!UICONTROL Grund]** Einstellung von **[!UICONTROL Ungültiger Empfänger]**. Um dies zu korrigieren, müssen Sie die Unterdrückungsliste aktualisieren, indem Sie diese E-Mail-Adressen suchen und entfernen.

Nach der Identifizierung können diese Adressen mithilfe der **[!UICONTROL Löschen]** Schaltfläche. Diese Adressen können dann in zukünftige E-Mail-Kampagnen aufgenommen werden.

Weitere Informationen finden Sie unter [diesem Abschnitt](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

