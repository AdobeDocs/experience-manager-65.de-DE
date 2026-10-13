---
title: Konfigurieren von AEM-Apps
description: Erfahren Sie, wie Sie Adobe Experience Manager-Apps verwenden, um den Inhalt Ihrer Anwendung OTA (over the air) zu aktualisieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: f7aa5ac0-3d03-4c04-b9c2-1bda427b0588
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: 523b1ccd-901e-5e3b-9fa7-f3dfd82463d5
    internal-label: Configuring
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '154'
ht-degree: 100%
---
# Konfigurieren von AEM-Apps{#configuring-for-aem-apps}

Mit Adobe Experience Manager-Apps können Sie den Inhalt Ihrer Anwendung OTA (over the air) aktualisieren. Die aktualisierten Inhalte werden in der Veröffentlichungsinstanz gespeichert. Damit die App auf Ihrem Gerät eine Verbindung zur Veröffentlichungsinstanz herstellen und nach Updates suchen kann, muss die Veröffentlichungsinstanz so konfiguriert sein, dass sie einen leeren Referrer-Header zulässt.

## Konfigurieren eines leeren Referrer-Headers {#configuring-empty-referrer-header}

So konfigurieren Sie den Referrer-Filterdienst:

* Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) bei:
* https://<Server>:<Port-Nummer>/system/console/configMgr
* Melden Sie sich als admin an.
* Wählen Sie im Menü **Configurations**: *Apache Sling Referrer Filter*.
* Aktivieren Sie das Feld „Leeres Feld zulassen“, um leere/fehlende Referrer-Header zuzulassen.
* Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

![chlimage_1-58](assets/chlimage_1-58a.png)

Weitere Informationen erhalten Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) und [Sicherheitsprüfliste – Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).
