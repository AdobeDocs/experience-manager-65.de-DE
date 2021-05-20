---
title: Konfigurieren Sie AEM Forms auf prefetchdomain-Informationen
seo-title: Konfigurieren Sie AEM Forms auf prefetchdomain-Informationen
description: Konfigurieren Sie AEM Forms, um Domäneninformationen zuvor abzurufen, wenn es zu einer langsameren Reaktionszeit kommt, aufgrund der tief verschachtelten Gruppen oder wenn Sie ein Mitglied mehrerer Gruppen sind.
seo-description: Konfigurieren Sie AEM Forms, um Domäneninformationen zuvor abzurufen, wenn es zu einer langsameren Reaktionszeit kommt, aufgrund der tief verschachtelten Gruppen oder wenn Sie ein Mitglied mehrerer Gruppen sind.
uuid: 53c8995e-3f9d-42e8-9f75-cee7debe6ce1
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: f9a3f897-90c6-4942-8a86-aae510298f2a
exl-id: cf5283a5-dbfb-460d-a8bd-11cd15ab8640
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 72%

---

# Konfigurieren Sie AEM Forms auf prefetchdomain-Informationen {#configure-aem-forms-to-prefetchdomain-information}

Für Benutzer kann es zu langsameren Reaktionszeiten kommen, wenn sie vielen Gruppen (z. B. 500 oder mehr) angehören oder wenn die Gruppen tief verschachtelt sind (z. B. 30 Ebenen). Wenn dieses Problem auftritt, können Sie AEM Forms so konfigurieren, dass Informationen aus bestimmten Domänen vorher abgerufen werden.

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > User Management > Konfiguration > Konfigurationsdateien importieren und exportieren]**.
1. Um die aktuelle Konfigurationseinstellung in eine Datei zu exportieren, klicken Sie auf **[!UICONTROL Export]** und speichern Sie die Konfigurationsdatei an einem anderen Speicherort.
1. Fügen Sie den folgenden Knoten (fett gedruckt) hinzu:

   ```xml
    <node name="UM">
    <map/>
    <node name="PrincipalCache">
        <map>
            <entry key="principalCacheSize" value="1000"/>
            <entry key="principalCacheBatchFetchSize" value="10"/>
            <entry key="rebuildCacheAfterSync" value="true />
            <entry key="enableFullPrefetch" value="false"/>
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/>
        <map>
    </node>
    <node name="APSAuditService">
   ```

   In diesem Beispiel werden mehrere Domänen zum vorherigen Abrufen konfiguriert. Die Domänennamen werden durch ein „/“ getrennt. Dies wird im oben stehenden Beispiel mit *Domain_Name1*, *Domain_Name2* und *Domain_Name3* gezeigt.

1. Um die aktualisierte Datei zu importieren, klicken Sie in User Management auf **[!UICONTROL Konfiguration > Konfigurationsdateien importieren und exportieren]**.
1. Klicken Sie auf **[!UICONTROL Browse]**, um die Datei zu suchen, klicken Sie auf &quot;Importieren&quot;und dann auf **[!UICONTROL OK]**.
