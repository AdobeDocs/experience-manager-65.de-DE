---
title: Konfigurieren einer Correspondence Management-Lösung
description: Erfahren Sie, wie Sie eine Correspondence Management-Lösung in einer AEM Forms-Umgebung konfigurieren.
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
feature: Correspondence Management
exl-id: f7f5eb0d-a283-45ea-84d3-d6375d2bb95b
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '298'
ht-degree: 100%

---

# Konfigurieren einer Correspondence Management-Lösung {#configuring-a-correspondence-management-solution}

## Definieren einer Autoreninstanz-URL für VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Führen Sie die folgenden Schritte aus, um eine Autoreninstanz-URL zur Wiederherstellung der Autoreninstanzversion zu definieren:

1. Navigieren Sie zu *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** neben der Einstellung **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]**.
1. Geben Sie im Feld **[!UICONTROL VersionRestoreManager Author-URL]** die URL der Autoreninstanz von VersionRestoreManager an.

   **URL-Zeichenfolge**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Wenn mehrere Instanzen im Autorenmodus (in Cluster) mit einem vorgeschalteten Lastenausgleich vorhanden sind, geben Sie die URL für den Lastenausgleich im Feld **[!UICONTROL Autor-URL von VersionRestoreManager]** an.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## Definieren der URL der Veröffentlichungsinstanz für „ActivationManagerImpl“ (Aktivierungs-Manager der öffentlichen Instanz) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Führen Sie die folgenden Schritte aus, um die URL der Veröffentlichungsinstanz für den Aktivierungs-Manager der öffentlichen Instanz zu definieren:

1. Navigieren Sie zu *https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Klicken Sie auf das Symbol **[!UICONTROL Bearbeiten]** neben der Einstellung **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]**.
1. Geben Sie im Feld für die **[!UICONTROL Veröffentlichungs-URL von ActivationManager]** die URL für den Zugriff auf die Instanz im Veröffentlichungsmodus in ActivationManager an. Sie können die folgenden URLs angeben.

   * **Lastenausgleichs-URL (empfohlen)**: Geben Sie die Lastenausgleichs-URL an, wenn Sie einen Webserver haben, der gegenüber der Veröffentlichungsfarm (mehrere nicht geclusterte Veröffentlichungsinstanzen) als Lastenausgleich fungiert.
   * **URL der Veröffentlichungsinstanz**: Geben Sie eine URL für die Veröffentlichungsinstanz an, wenn Sie über eine einzelne Veröffentlichungsinstanz verfügen oder der Webserver, der der Veröffentlichungsfarm vorgeschaltet ist, aufgrund von Einschränkungen nicht über die Autorenumgebung zugänglich ist. Wenn die angegebene Veröffentlichungsinstanz nicht bereit ist, gibt es einen Fallback-Mechanismus, damit autorenseitig etwas zur Behebung unternommen werden kann.
   * **URL-Zeichenfolge**:

     `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Weitere Informationen zum Konfigurieren von Correspondence Management finden Sie unter [Eigenschaften der Correspondence Management-Konfiguration](https://helpx.adobe.com/de/aem-forms/6-2/aem-forms-architecture-deployment.html).
