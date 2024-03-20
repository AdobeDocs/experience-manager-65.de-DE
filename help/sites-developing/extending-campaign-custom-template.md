---
title: Erstellen benutzerdefinierter AEM-Seitenvorlagen mit Adobe Campaign-Formularkomponenten
description: Erstellen Sie eine benutzerdefinierte Seitenvorlage, die Adobe Campaign-Formularkomponenten verwendet
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: de5c634a-c0d7-4e69-b941-d2fbfe83117d
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 64%

---

# Erstellen benutzerdefinierter AEM-Seitenvorlagen mit Adobe Campaign-Formularkomponenten{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

Auf dieser Seite wird anhand der Implementierung der Geometrixx-Outdoors-Vorlage (`/apps/geometrixx-outdoors/components/page_campaign_profile` ) erläutert, wie Sie eine benutzerdefinierte Seitenvorlage auf Basis von [Adobe Campaign-Formularkomponenten](/help/sites-authoring/adobe-campaign-components.md) erstellen. Darüber hinaus erhalten Sie wichtige Informationen, die Sie ggf. bei der Erstellung Ihrer eigenen benutzerdefinierten Vorlage benötigen.

>[!NOTE]
>
>[E-Mail- und Formularbeispiele sind nur in Geometrixx verfügbar](/help/sites-developing/we-retail.md). Laden Sie Beispielinhalt aus Package Share herunter.

Um eine benutzerdefinierte AEM-Seitenvorlage mit Adobe Campaign-Formularkomponenten zu erstellen, stellen Sie Folgendes sicher:

1. **Korrektes resourceSuperType**

   Stellen Sie sicher, dass die Seitenkomponente von `mcm/campaign/components/profile` erbt.

   Dies ist erforderlich, damit die Servlets Informationen empfangen und speichern können.

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![chlimage_1-201](assets/chlimage_1-201.png)

1. **ClientContext-Einstellungen**

   In den ClientContext-Einstellungen (`/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile`) sehen Sie die folgenden Einstellungen:

   * ClientContext verweist auf `/etc/clientcontext/campaign`.
   * Es ist außerdem ein zusätzlicher Knoten *config* vorhanden.

   ![chlimage_1-202](assets/chlimage_1-202.png)

1. **head.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/head.jsp)**

   In **head.jsp**, sehen Sie die folgenden Zeilen, die die **clientcontext-config** und **cloudservice-hook**:

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. **body.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/body.jsp)**

   In **body.jsp** werden die Cloud-Services unten auf der Seite geladen:

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. **Kampagnenseiteneigenschaften**

   Um eine Adobe Campaign-Vorlage auswählen zu können, werden die Seiteneigenschaften mit der **Kampagne** tab:

   `/apps/geometrixx-outdoors/components/page_campaign_profile/dialog/items/tabs/items/campaign`

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. **Vorlageneinstellungen**.

   In der Vorlage (`/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content` ) sind die folgenden Standardwerte enthalten:

   | **acMapping** | mapRecipient (für Adobe Campaign 6.1), profile (für Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** | Mail |

   ![chlimage_1-204](assets/chlimage_1-204.png)
