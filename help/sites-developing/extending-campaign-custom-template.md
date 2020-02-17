---
title: Erstellen benutzerdefinierter AEM-Seitenvorlagen mit Adobe Campaign-Formularkomponenten
seo-title: Erstellen benutzerdefinierter AEM-Seitenvorlagen mit Adobe Campaign-Formularkomponenten
description: Erstellen Sie eine benutzerdefinierte Seitenvorlage auf der Basis von Adobe Campaign-Formularkomponenten.
seo-description: Erstellen Sie eine benutzerdefinierte Seitenvorlage auf der Basis von Adobe Campaign-Formularkomponenten.
uuid: 8162ace2-b661-4c39-b0fb-288e1c035b9c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c3f6eed4-bbda-454a-88ce-c7f2041d4217
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Erstellen benutzerdefinierter AEM-Seitenvorlagen mit Adobe Campaign-Formularkomponenten{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

This page explains how to build a custom page template that uses [Adobe Campaign Form](/help/sites-authoring/adobe-campaign-components.md) components by examining how the Geometrixx-outdoors template ( `/apps/geometrixx-outdoors/components/page_campaign_profile`) is implemented, and points you to important information you may need when creating your own custom template.

>[!NOTE]
>
>[E-Mail- und Formularbeispiele sind nur in Geometrixx verfügbar](/help/sites-developing/we-retail.md). Laden Sie Geometrixx-Beispielinhalt von Package Share herunter.

Um eine benutzerdefinierte AEM-Seitenvorlage mit Adobe Campaign-Formularkomponenten zu erstellen, müssen Sie sicherstellen, dass Sie über Folgendes verfügen:

1. **Die richtige resourceSuperType-Klasse**

   Make sure the page-component inherits from `mcm/campaign/components/profile`.

   Dies ist erforderlich, damit die Servlets Informationen abrufen und speichern können.

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`
   ![chlimage_1-201](assets/chlimage_1-201.png)

1. **ClientContext-Einstellungen**

   When you look at the clientcontext settings ( `/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile`) you see the following settings:

   * ClientContext points to `/etc/clientcontext/campaign`
   * Es ist außerdem ein zusätzlicher Knoten *config* vorhanden.
   ![chlimage_1-202](assets/chlimage_1-202.png)

1. **head.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/head.jsp)**

   **head.jsp** enthält die folgenden Zeilen, die **clientcontext-config** und **cloudservice-hook** verwenden:

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. **body.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/body.jsp)**

   In **body.jsp**, the cloud services are loaded at the bottom of the page:

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. **Kampagnenseiteneigenschaften**

   Um eine Adobe Campaign-Vorlage auswählen zu können, müssen die Seiteneigenschaften um die Registerkarte **Kampagne** erweitert werden:

   `/apps/geometrixx-outdoors/components/page_campaign_profile/dialog/items/tabs/items/campaign`

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. **Vorlageneinstellungen**.

   In the template ( `/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content`) you see the following default values:

   | **acMapping** | mapRecipient (für Adobe Campaign 6.1), profile (für Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** | mail |

   ![chlimage_1-204](assets/chlimage_1-204.png)

