---
title: Konfigurieren von AEM-Apps
seo-title: Konfigurieren von AEM-Apps
description: Erfahren Sie, wie Sie AEM-Apps konfigurieren können.
seo-description: Erfahren Sie, wie Sie AEM-Apps konfigurieren können.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
translation-type: tm+mt
source-git-commit: 684d2d5f73d571a15c8155e7870134c28dc892b7
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 66%

---


# Konfigurieren von AEM-Apps{#configuring-for-aem-apps}

Adobe Experience Manager-Apps stellen die Möglichkeit zur Over-the-Air(OTA)-Aktualisierung des Inhalts Ihrer Anwendung bereit. Die aktualisierten Inhalte werden in der Veröffentlichungsinstanz gespeichert. Damit die App auf Ihrem Gerät mit der Veröffentlichungsinstanz verbunden und damit nach Updates gesucht werden kann, muss die Veröffentlichungsinstanz so konfiguriert werden, dass ein leerer Referrer-Header zugelassen wird.

## Konfigurieren des leeren Referrer-Headers {#configuring-empty-referrer-header}

So konfigurieren Sie den Referrer-Filterdienst:

* Öffnen Sie die Apache Felix-Konsole (**Konfigurationen**) unter:
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Melden Sie sich als admin an.
* Wählen Sie im Menü **Konfigurationen** Folgendes aus: *Apache Sling Werber Filter*
* Markieren Sie das Feld Leeres Feld zulassen, um leere/fehlende Werber-Kopfzeilen zuzulassen.
* Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

![chlimage_1-58](assets/chlimage_1-58a.png)

Weitere Informationen finden Sie unter [OSGI-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) und [Sicherheits-Checkliste - Probleme mit der Cross-Site Request Forgery](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).
