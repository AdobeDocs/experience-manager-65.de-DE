---
title: Beitragsgrenzen der Mitgliedstaaten
seo-title: Beitragsgrenzen der Mitgliedstaaten
description: Mit der Beitragsbegrenzungsfunktion können Sie die Beiträge zum Schutz vor Spam einschränken
seo-description: Mit der Beitragsbegrenzungsfunktion können Sie die Beiträge zum Schutz vor Spam einschränken
uuid: 99b2a855-3f0d-41a0-9572-517a7f29af9f
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: d855aac2-f34d-402f-9dc3-c7ad494b45f2
role: Admin
exl-id: d00a8eb2-47ce-425a-a312-f043f82912be
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# Beitragsgrenzen der Mitgliedstaaten {#member-contribution-limits}

## Übersicht {#overview}

Die Beitragsbegrenzungsfunktion bietet die Möglichkeit, die Beiträge von Community-Mitgliedern zu beschränken, um sie vor Spam zu schützen.

Wenn ein Mitglied eingeschränkt ist, führen Beiträge, die die zulässige Anzahl von Beiträgen überschreiten, zu einem Warnhinweis, dass die Beschränkung überschritten wurde und der Beitrag abgelehnt wird. Das Community-Mitglied kann dann zum Community-Message-Center gehen und sich an einen Community-Manager wenden, der die Einschränkungen ggf. entfernen kann.

Beitragsbeschränkungen können einzeln über die [Mitgliederkonsole](members.md) aktiviert und/oder so konfiguriert werden, dass sie automatisch aktiviert werden, wenn Site-Besucher zu neuen Mitgliedern werden.

Mithilfe der Mitgliederkonsole können Beitragsbeschränkungen für ein Mitglied jederzeit von einem Community-Manager proaktiv entfernt oder reaktiv entfernt werden, wenn ein Mitglied eine Nachricht an einen Community-Manager sendet, der eine solche Anfrage sendet.

## Konfiguration benutzergenerierter Inhaltsbeiträge in AEM Communities - Einschränkungen {#aem-communities-user-generated-content-contribution-limits-configuration}

Diese OSGi-Konfiguration:

* Definiert die Merkmale der Beitragslimits (Anzahl der Stellen innerhalb eines Zeitraums).
* Identifiziert, wer vom Mitglied benachrichtigt werden kann, wenn die Grenze erreicht wurde.
* Identifiziert Domänen, die nie eingeschränkt werden müssen.

So erreichen Sie diese OSGi-Konfiguration:

* Im primären Herausgeber:
* Melden Sie sich mit Administratorrechten an.
* Rufen Sie die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie `AEM Communities User Generated Content Contribution Limits Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.

![configure-limits](assets/configure-limits.png)

* **[!UICONTROL Automatische Anwendung von UGC-Beitragslimits]**

   Wenn diese Option aktiviert ist, legen Sie Benutzern automatisch Beitragsbeschränkungen fest, wenn sie sich als Community-Mitglieder registrieren. Dies spiegelt sich im Profil des Community-Mitglieds wider und kann über die [Mitgliederkonsole](members.md) aktiviert/deaktiviert werden. Neue Mitglieder mit einer E-Mail-Adresse aus einer Zulassungsliste von Domänen werden nie eingeschränkt.

   Diese Option ist standardmäßig deaktiviert.

* **[!UICONTROL UGC-Limit]**

   Maximale Anzahl der Beiträge.

   Der Standardwert beträgt 10 Beiträge.

* **[!UICONTROL UGC-Grenzfrequenz]**

   Der Zeitraum, der die UGC-Grenze einschränkt.

   Der Standardwert ist 60 Minuten.

* **[!UICONTROL Domänen]**

   Eine Zulassungsliste mit einer oder mehreren E-Mail-Domänen. Wählen Sie das Symbol + aus, um weitere Einträge vorzunehmen.

   Benutzer mit E-Mail-Adressen in der Zulassungsliste der Domänen sind nicht betroffen, wenn die UGC-Beitragsbeschränkungen automatisch angewendet werden. Wenn beispielsweise die Domäne `mycompany.com` zur Domain-Liste hinzugefügt wird, ist ein Mitglied mit der E-Mail-Adresse `me@mycompany.com` nie vom Posten ausgeschlossen.

   Der Standardwert ist eine leere Zulassungsliste.

* **[!UICONTROL Messaging-Empfänger]**

   Liste mit einer oder mehreren autorisierbaren IDs von Mitgliedern, die die Beitragsbeschränkungen für Mitglieder ändern können. Wählen Sie das Symbol + aus, um weitere Einträge vorzunehmen.

   Die Mitglieder können nur an bestimmte Mitglieder Kontakt aufnehmen, wenn ihre Grenze erreicht ist.

   Der Standardwert ist kein Nachrichtenempfänger.

Hinweis: Die Standardkonfiguration führt innerhalb eines Zeitraums von einer Stunde zu maximal 10 Beiträgen.
