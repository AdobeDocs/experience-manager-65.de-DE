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
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Beitragsbeschränkungen für Mitglieder {#member-contribution-limits}

## Überblick {#overview}

Die Beitragsbegrenzung bietet die Möglichkeit, die Beiträge von Community-Mitgliedern zu beschränken, um gegen Spam zu schützen.

Wenn ein Mitglied eingeschränkt ist, führt jeder Beitrag, der die zulässige Anzahl von Beiträgen überschreitet, zu einer Warnung, dass die Obergrenze überschritten wurde und der Beitrag abgelehnt wird. Das Community-Mitglied kann dann zum Community Message Center gehen und einen Community Manager kontaktieren, der die Beschränkungen gegebenenfalls entfernen kann.

Beitragsbeschränkungen können einzeln über die [Mitgliederkonsole](members.md) aktiviert und/oder so konfiguriert werden, dass sie automatisch aktiviert werden, wenn Site-Besucher zu neuen Mitgliedern werden.

Mithilfe der Mitgliederkonsole können Beitragsbeschränkungen für ein Mitglied von einem Community Manager jederzeit proaktiv entfernt oder reaktiv entfernt werden, wenn ein Mitglied eine Nachricht an einen Community Manager sendet, der eine solche Anforderung sendet.

## Konfiguration von benutzerdefinierten AEM Communities Content Contribution Limits {#aem-communities-user-generated-content-contribution-limits-configuration}

Diese OSGi-Konfiguration

* Definiert die Merkmale der Beitragsgrenzen (Anzahl der Stellen innerhalb eines Zeitraums)
* Identifiziert, wer das Mitglied benachrichtigen kann, wenn die Beschränkung erreicht wurde
* Identifiziert Domänen, die nie eingeschränkt werden müssen

So erreichen Sie diese OSGi-Konfiguration:

* Im primären Herausgeber
* Anmelden mit Administratorrechten
* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)

   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen `AEM Communities User Generated Content Contribution Limits Configuration`
* Wählen Sie das Bearbeitungssymbol

![chlimage_1-127](assets/chlimage_1-127.png)

* **[!UICONTROL UGC-Beitragsbeschränkungen automatisch anwenden]**

   Wenn diese Option aktiviert ist, legen Sie bei der Registrierung als Community-Mitglieder automatisch Beitragsbeschränkungen für Benutzer fest. Dies wird im Profil des Community-Mitglieds angezeigt und kann über die [Mitgliederkonsole](members.md)aktiviert/deaktiviert werden. Neue Mitglieder mit einer E-Mail-Adresse aus einer weißen, aufgelisteten Domäne werden nie eingeschränkt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL UGC-Grenze]**

   Höchstzahl der Beiträge.

   Der Standardwert ist 10 Beiträge.

* **[!UICONTROL UGC-Grenzfrequenz]**

   Der Zeitraum, in dem die UGC-Grenze eingeschränkt wird.

   Der Standardwert ist 60 Minuten.

* **[!UICONTROL Domänen]**

   Eine weiße Liste einer oder mehrerer E-Mail-Domänen. Klicken Sie auf das Symbol +, um weitere Einträge einzugeben.

   Benutzer mit E-Mail-Adressen in den weißen aufgelisteten Domänen sind davon nicht betroffen, wenn UGC-Beitragsbeschränkungen automatisch angewendet werden. Wenn zum Beispiel eine Domäne zur Liste der Domänen hinzugefügt `mycompany.com` wird, wird ein Mitglied mit E-Mail-Adresse nie vom Posten ausgeschlossen `me@mycompany.com` werden.

   Der Standardwert ist eine leere weiße Liste.

* **[!UICONTROL Messaging-Empfänger]**

   Liste einer oder mehrerer autorisierbarer IDs von Mitgliedern, die die Beitragsbeschränkungen für Mitglieder ändern können. Klicken Sie auf das Symbol +, um weitere Einträge einzugeben.

   Die Mitglieder dürfen nur dann mit bestimmten Mitgliedern Kontakt aufnehmen, wenn ihre Grenze erreicht ist.

   Standard ist kein Empfänger von Nachrichten.

Hinweis: Die Standardkonfiguration ergibt eine Beschränkung von 10 Beiträgen innerhalb einer Stunde.
