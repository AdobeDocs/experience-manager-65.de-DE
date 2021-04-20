---
title: Beitragsbeschränkungen für Mitglieder
seo-title: Beitragsbeschränkungen für Mitglieder
description: Mit der Funktion "Beitragsbeschränkungen"können Sie die Beiträge zum Schutz vor Spam einschränken
seo-description: Mit der Funktion "Beitragsbeschränkungen"können Sie die Beiträge zum Schutz vor Spam einschränken
uuid: 99b2a855-3f0d-41a0-9572-517a7f29af9f
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d855aac2-f34d-402f-9dc3-c7ad494b45f2
role: Administrator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 2%

---


# Mitgliederbeitragsbeschränkungen {#member-contribution-limits}

## Überblick {#overview}

Die Beitragsbegrenzung bietet die Möglichkeit, die Beiträge von Community-Mitgliedern zu beschränken, um gegen Spam zu schützen.

Wenn ein Mitglied eingeschränkt ist, führt jeder Beitrag, der die zulässige Anzahl von Beiträgen überschreitet, zu einer Warnung, dass die Obergrenze überschritten wurde und der Beitrag abgelehnt wird. Das Community-Mitglied kann dann zum Community Message Center gehen und einen Community Manager kontaktieren, der die Beschränkungen gegebenenfalls entfernen kann.

Beitragsbeschränkungen können einzeln über die [Mitgliederkonsole](members.md) aktiviert und/oder so konfiguriert werden, dass sie automatisch aktiviert werden, wenn Site-Besucher neue Mitglieder werden.

Mithilfe der Mitgliederkonsole können Beitragsbeschränkungen für ein Mitglied von einem Community Manager jederzeit proaktiv entfernt oder reaktiv entfernt werden, wenn ein Mitglied eine Nachricht an einen Community Manager sendet, der eine solche Anforderung sendet.

## AEM Communities Benutzergenerierte Inhaltsbeitragsbeschränkungen Konfiguration {#aem-communities-user-generated-content-contribution-limits-configuration}

Diese OSGi-Konfiguration:

* Definiert die Merkmale der Beitragsgrenzen (Anzahl der Stellen innerhalb eines Zeitraums).
* Identifiziert, wer vom Mitglied benachrichtigt werden kann, wenn der Grenzwert erreicht wurde.
* Identifiziert Domänen, die nie eingeschränkt werden müssen.

So erreichen Sie diese OSGi-Konfiguration:

* Im primären Herausgeber:
* Melden Sie sich mit Administratorrechten an.
* Rufen Sie die [Webkonsole](../../help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie nach `AEM Communities User Generated Content Contribution Limits Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.

![configure-limits](assets/configure-limits.png)

* **[!UICONTROL Automatische Anwendung von UGC-Beitragsbeschränkungen]**

   Wenn diese Option aktiviert ist, legen Sie bei der Registrierung als Community-Mitglieder automatisch Beitragsbeschränkungen für Benutzer fest. Dies spiegelt sich im Profil des Community-Mitglieds wider und kann in der [members-Konsole](members.md) aktiviert/deaktiviert werden. Neue Mitglieder mit einer E-Mail-Adresse aus einer Zulassungsliste von Domänen sind nie eingeschränkt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL UGC-Grenze]**

   Höchstzahl der Beiträge.

   Der Standardwert ist 10 Beiträge.

* **[!UICONTROL UGC-Grenzfrequenz]**

   Der Zeitraum, in dem die UGC-Grenze eingeschränkt wird.

   Der Standardwert ist 60 Minuten.

* **[!UICONTROL Domänen]**

   Eine Zulassungsliste-Liste einer oder mehrerer E-Mail-Domänen. Klicken Sie auf das Symbol +, um weitere Einträge zu erstellen.

   Benutzer mit E-Mail-Adressen in der Zulassungsliste der Domänen sind davon nicht betroffen, wenn die Beitragsbeschränkungen für UGC automatisch angewendet werden. Wenn beispielsweise die Domäne `mycompany.com` zur Liste der Domänen hinzugefügt wird, wird ein Mitglied mit der E-Mail-Adresse `me@mycompany.com` nie vom Posten ausgeschlossen.

   Standard ist eine leere Zulassungsliste.

* **[!UICONTROL Messaging-Empfänger]**

   Liste einer oder mehrerer autorisierbarer IDs von Mitgliedern, die die Beitragsbeschränkungen für Mitglieder ändern können. Klicken Sie auf das Symbol +, um weitere Einträge zu erstellen.

   Die Mitglieder dürfen nur dann mit bestimmten Mitgliedern Kontakt aufnehmen, wenn ihre Grenze erreicht ist.

   Standard sind keine Empfänger für Nachrichten.

Hinweis: Die Standardkonfiguration ergibt eine Beschränkung von 10 Beiträgen innerhalb einer Stunde.
