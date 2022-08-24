---
title: Konfigurieren von AEM-Apps
seo-title: Configuring for AEM Apps
description: Erfahren Sie, wie Sie AEM-Apps konfigurieren können.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: f7aa5ac0-3d03-4c04-b9c2-1bda427b0588
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 64%

---

# Konfigurieren von AEM-Apps{#configuring-for-aem-apps}

Adobe Experience Manager-Apps stellen die Möglichkeit zur Over-the-Air(OTA)-Aktualisierung des Inhalts Ihrer Anwendung bereit. Die aktualisierten Inhalte werden in der Veröffentlichungsinstanz gespeichert. Damit die App auf Ihrem Gerät mit der Veröffentlichungsinstanz verbunden und damit nach Updates gesucht werden kann, muss die Veröffentlichungsinstanz so konfiguriert werden, dass ein leerer Referrer-Header zugelassen wird.

## Konfigurieren des leeren Referrer-Headers {#configuring-empty-referrer-header}

So konfigurieren Sie den Referrer-Filterdienst:

* Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) bei:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Melden Sie sich als admin an.
* Im **Konfigurationen** auswählen: *Apache Sling Referrer Filter*
* Aktivieren Sie das Feld Leere erlauben , um leere/fehlende Referrer-Header zuzulassen.
* Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

![chlimage_1-58](assets/chlimage_1-58a.png)

Siehe [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) und [Sicherheits-Checkliste - Probleme mit Site-übergreifenden Anforderungsfälschungen](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) für weitere Informationen.
