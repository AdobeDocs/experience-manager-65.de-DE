---
title: Obergrenze des Mitgliederbeitrags
description: Mit der Funktion „Beitragsbeschränkungen“ können Sie die Beiträge zum Schutz vor Spam einschränken
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: d00a8eb2-47ce-425a-a312-f043f82912be
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# Obergrenze des Mitgliederbeitrags {#member-contribution-limits}

## Überblick {#overview}

Mit der Funktion Beitragsbeschränkungen können Sie die Beiträge von Community-Mitgliedern einschränken, um sich vor Spam zu schützen.

Wenn ein Mitglied eingeschränkt ist, führt jeder Beitrag, der die zulässige Anzahl von Beiträgen überschreitet, zu einem Warnhinweis, dass das Limit überschritten wurde und der Beitrag abgelehnt wird. Das Community-Mitglied kann sich dann an das Community-Message-Center wenden und sich an einen Community-Manager wenden, der die Beschränkungen bei Bedarf aufheben kann.

Beitragsbeschränkungen können einzeln über die [Mitgliederkonsole“ aktiviert ](members.md)/oder so konfiguriert werden, dass sie automatisch aktiviert werden, wenn Site-Besucher neue Mitglieder werden.

Über die Mitgliederkonsole können Beitragsbeschränkungen für ein Mitglied jederzeit proaktiv von einem Community-Manager entfernt werden oder reaktiv entfernt werden, wenn ein Mitglied eine Nachricht an einen Community-Manager sendet, der eine solche Anfrage stellt.

## Konfiguration der Beitragsbeschränkungen für benutzergenerierte Inhalte in AEM Communities {#aem-communities-user-generated-content-contribution-limits-configuration}

Diese OSGi-Konfiguration:

* Definiert die Merkmale der Beitragsbeschränkungen (Anzahl der Stellen innerhalb eines Zeitraums).
* Gibt an, wen das Mitglied benachrichtigen kann, wenn das Limit erreicht wurde.
* kennzeichnet Domains, für die nie Beschränkungen festgelegt werden müssen.

So erreichen Sie diese OSGi-Konfiguration:

* Auf dem primären Herausgeber:
* Melden Sie sich mit Administratorrechten an.
* Rufen Sie die [Web-Konsole](../../help/sites-deploying/configuring-osgi.md) auf.

   * Beispiel: [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Suchen Sie `AEM Communities User Generated Content Contribution Limits Configuration`.
* Wählen Sie das Bearbeitungssymbol aus.

![configure-limits](assets/configure-limits.png)

* **[!UICONTROL UGC-Beitragsbeschränkungen automatisch anwenden]**

  Wenn diese Option aktiviert ist, werden für Benutzer bei der Registrierung als Community-Mitglieder automatisch Beitragsbeschränkungen festgelegt. Dies wird im Profil des Community-Mitglieds angezeigt und kann über die [Mitgliederkonsole“ aktiviert/deaktiviert ](members.md). Neue Mitglieder mit einer E-Mail-Adresse von einer Zulassungsliste von Domains werden niemals eingeschränkt.

  Standard ist deaktiviert.

* **[!UICONTROL UGC-Limit]**

  Maximale Anzahl von Beiträgen.

  Der Standardwert ist zehn Beiträge.

* **[!UICONTROL UGC-Grenzfrequenz]**

  Der Zeitraum, der das UGC-Limit einschränkt.

  Der Standardwert ist 60 Minuten.

* **[!UICONTROL Domains]**

  Auf die Zulassungsliste setzen Eine Liste mit einer oder mehreren E-Mail-Domains Wählen Sie das Symbol + aus, um weitere Einträge vorzunehmen.

  Benutzende mit E-Mail-Adressen in der Zulassungsliste von Domains sind nicht betroffen, wenn die Beschränkungen für UGC-Beiträge automatisch angewendet werden. Wenn beispielsweise Domain `mycompany.com` zur Liste der Domains hinzugefügt wird, ist ein Mitglied mit der E-Mail-Adresse `me@mycompany.com` nie an der Veröffentlichung gehindert.

  Standard ist eine leere Zulassungsliste.

* **[!UICONTROL Nachrichtenempfänger]**

  Liste der zulässigen IDs von Mitgliedern, die die Beitragsbeschränkungen für Mitglieder ändern können. Wählen Sie das Symbol + aus, um weitere Einträge vorzunehmen.

  Die Mitglieder dürfen sich nur dann an bestimmte Mitglieder wenden, wenn ihr Limit erreicht wurde.

  Standard ist keine Nachrichtenempfänger.

Hinweis: Die Standardkonfiguration führt zu einem Limit von zehn Beiträgen innerhalb eines Zeitraums von einer Stunde.
