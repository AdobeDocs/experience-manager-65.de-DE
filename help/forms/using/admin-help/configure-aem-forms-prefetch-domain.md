---
title: Konfigurieren von AEM Formularen für Vorabrufdomäneninformationen
description: Konfigurieren Sie AEM Forms, um Domain-Informationen zuvor abzurufen, wenn es zu einer langsameren Reaktionszeit kommt, aufgrund der tief verschachtelten Gruppen oder wenn Sie ein Mitglied mehrerer Gruppen sind.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: cf5283a5-dbfb-460d-a8bd-11cd15ab8640
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 66%

---

# Konfigurieren von AEM Formularen für Vorabrufdomäneninformationen {#configure-aem-forms-to-prefetchdomain-information}

Für Benutzer kann es zu einer langsameren Reaktionszeit kommen, wenn sie vielen Gruppen angehören (z. B. 500 oder mehr) oder wenn die Gruppen tief verschachtelt sind (z. B. 30 Ebenen). Wenn dieses Problem auftritt, können Sie AEM Forms so konfigurieren, dass Informationen aus bestimmten Domains vorher abgerufen werden.

1. Klicken Sie in Administration Console auf **[!UICONTROL Einstellungen > Benutzerverwaltung > Konfiguration > Konfigurationsdateien importieren und exportieren]**.
1. Um die aktuellen Konfigurationseinstellungen in eine Datei zu exportieren, klicken Sie auf **[!UICONTROL Exportieren]** und speichern die Konfigurationsdatei an einem anderen Speicherort.
1. Fügen Sie den folgenden Knoten hinzu (fett markiert):

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

   In diesem Beispiel werden mehrere Domains zum vorherigen Abrufen konfiguriert. Die Domain-Namen werden durch ein „/“ getrennt. Dies wird im obigen Beispiel mit *Domäne_Name1*, *Domain_Name2*, und *Domain_Name3*.

1. Um die aktualisierte Datei zu importieren, klicken Sie in „Benutzerverwaltung“ auf **[!UICONTROL Konfiguration > Konfigurationsdateien im- und exportieren]**.
1. Klicken Sie auf **[!UICONTROL Durchsuchen]**, um die Datei zu suchen, klicken Sie dann auf „Importieren“ und anschließend auf **[!UICONTROL OK]**.
