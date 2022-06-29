---
title: Konfigurieren einer Correspondence Management-Lösung
seo-title: Configuring a Correspondence Management solution
description: Konfigurieren einer Correspondence Management-Lösung
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
exl-id: f7f5eb0d-a283-45ea-84d3-d6375d2bb95b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '291'
ht-degree: 100%

---

# Konfigurieren einer Correspondence Management-Lösung {#configuring-a-correspondence-management-solution}

## Definieren einer URL der Autorinstanz für VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Führen Sie die folgenden Schritte aus, um eine URL der Autorinstanz zur Wiederherstellung der Autorinstanzversion:

1. Navigieren Sie zu *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Klicken Sie auf **[!UICONTROL Bearbeiten]** neben der Einstellung **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]**.
1. Geben Sie im Feld **[!UICONTROL VersionRestoreManager Author-URL]** die URL der Autoreninstanz von VersionRestoreManager an.

   **URL-Zeichenfolge**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Wenn mehrere Instanzen im Autorenmodus (in Cluster) mit einem vorgeschalteten Lastenausgleich vorhanden sind, geben Sie die URL für den Lastenausgleich im Feld **[!UICONTROL Autor-URL von VersionRestoreManager]** an.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

## URL der Instanz im Veröffentlichungsmodus für ActivationManagerImpl festlegen (Aktivierungsmanager der öffentlichen Instanz) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Folgen Sie diesen Schritten, um die „URL-Instanz veröffentlichen“ für den Aktivierungsmanager der Veröffentlichungsinstanz zu definieren:

1. Navigieren Sie zu *https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*. Melden Sie sich mit den Anmeldedaten der OSGi Management Console an. Standardmäßig lauten die Anmeldedaten: admin/admin.
1. Klicken Sie auf das **[!UICONTROL Bearbeitungs]** symbol neben der Einstellung **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]**.
1. Geben Sie im Feld für die **[!UICONTROL Veröffentlichungs-URL von ActivationManager]** die URL für den Zugriff auf die Instanz im Veröffentlichungsmodus in ActivationManager an. Sie können die folgenden URLs angeben.

   * **Lastenausgleichs-URL (empfohlen)**: Geben Sie die Lastenausgleichs-URL an, wenn Sie einen Webserver haben, der gegenüber der Veröffentlichungsfarm (mehrere nicht geclusterte Instanzen im Veröffentlichungsmodus) als Lastenausgleich fungiert.
   * **URL der Instanz im Veröffentlichungsmodus**: Geben Sie die URL einer beliebigen Instanz im Veröffentlichungsmodus an, wenn Sie nur eine Instanz im Veröffentlichungsmodus haben oder ein Zugriff auf den der Veröffentlichungsfarm vorgeschalteten Webserver von der Autorumgebung aus aufgrund von gegebenen falls vorhandenen Beschränkungen nicht möglich ist. Wenn die angegebene Instanz im Veröffentlichungsmodus nicht bereit ist, gibt es einen Fallback-Mechanismus, damit autorseitig etwas zur Behebung unternommen werden kann.
   * **URL-Zeichenfolge**:

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Klicken Sie auf **[!UICONTROL Speichern]**.

Weitere Informationen zum Konfigurieren von Correspondence Management finden Sie unter [Correspondence Management Configuration-Eigenschaften](https://helpx.adobe.com/de/aem-forms/6-2/aem-forms-architecture-deployment.html).
