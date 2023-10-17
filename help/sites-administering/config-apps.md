---
title: Konfigurieren von AEM-Apps
description: Erfahren Sie, wie Sie mit Adobe Experience Manager-Apps den Inhalt Ihres Anwendungs-OTA aktualisieren können (über die Luft).
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: f7aa5ac0-3d03-4c04-b9c2-1bda427b0588
source-git-commit: 06a6d4e0ba2aeaefcfb238233dd98e8bbd6731da
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 47%

---

# Konfigurieren von AEM-Apps{#configuring-for-aem-apps}

Mit Adobe Experience Manager Apps können Sie den Inhalt Ihres Anwendungs-OTA (über die Luft) aktualisieren. Die aktualisierten Inhalte werden in der Veröffentlichungsinstanz gespeichert. Damit die App auf Ihrem Gerät eine Verbindung zur Veröffentlichungsinstanz herstellen und nach Updates suchen kann, muss die Veröffentlichungsinstanz so konfiguriert sein, dass ein leerer Referrer-Header zulässig ist.

## Konfigurieren der Kopfzeile des leeren Referrers {#configuring-empty-referrer-header}

So konfigurieren Sie den Referrer-Filterdienst:

* Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) bei:
* https://&lt;Server>:&lt;Port-Nummer>/system/console/configMgr
* Melden Sie sich als admin an.
* Wählen Sie im Menü **Configurations**: *Apache Sling Referrer Filter*.
* Aktivieren Sie das Feld Leere erlauben , damit leere/fehlende Referrer-Header zulässig sind.
* Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

![chlimage_1-58](assets/chlimage_1-58a.png)

Weitere Informationen erhalten Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) und [Sicherheitsprüfliste – Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).
