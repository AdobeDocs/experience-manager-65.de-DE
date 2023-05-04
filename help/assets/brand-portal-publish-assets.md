---
title: Veröffentlichen von Assets in Brand Portal
seo-title: Publish assets to Brand Portal
description: Erfahren Sie, wie Sie Sammlungen in Brand Portal veröffentlichen und Veröffentlichungen rückgängig machen können.
seo-description: Learn how to publish and unpublish assets to Brand Portal.
uuid: 350beb85-c0fb-4a1c-8597-c03592c02d3d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: 39b8cf9b-afec-4c9a-8a5d-7fc87e643f26
docset: aem65
feature: Brand Portal
role: User
exl-id: 76652a16-cad6-4e95-9e66-41efec452b03
source-git-commit: 3d713021ac410ca2925a282c5dfca98ed4e483ee
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 100%

---

# Veröffentlichen von Assets in Brand Portal {#publish-assets-to-brand-portal}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/brand-portal/publish-to-brand-portal.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

Als Adobe Experience Manager (AEM) Assets-Admin können Sie für Ihre Organisation Assets und Ordner in der AEM Assets Brand Portal-Instanz veröffentlichen (oder den Veröffentlichungs-Workflow für einen späteren Zeitpunkt planen). Allerdings müssen Sie zunächst AEM Assets mit Brand Portal konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der von AEM Assets mit Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md).

Nach erfolgreicher Replikation können Sie Assets, Ordner und Sammlungen in Brand Portal veröffentlichen. Gehen Sie wie folgt vor, um Assets in Brand Portal zu veröffentlichen:

>[!NOTE]
>
>Adobe empfiehlt eine gestaffelte Veröffentlichung, vorzugsweise außerhalb der Spitzenzeiten, sodass die AEM-Autoreninstanz keine übermäßigen Ressourcen belegt.

1. Wählen Sie in der Assets-Konsole die Assets/Ordner aus, die Sie veröffentlichen möchten, und klicken Sie in der Symbolleiste auf **[!UICONTROL Quick Publish]**.

   Alternativ können Sie auch die Assets auswählen, die Sie in Brand Portal veröffentlichen möchten.

   ![publish2bp-2](assets/publish2bp.png)

1. Um die Assets in Brand Portal zu veröffentlichen, stehen die beiden folgenden Optionen zur Verfügung:
   * [Sofortiges Veröffentlichen von Assets](#publish-to-bp-now)
   * [Assets später veröffentlichen](#publish-to-bp-now)

## Sofortiges Veröffentlichen von Assets {#publish-to-bp-now}

Um die ausgewählten Assets in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

* Wählen Sie in der Symbolleiste **[!UICONTROL Quick Publish]** aus. Wählen Sie dann im Menü die Option **[!UICONTROL In Brand Portal veröffentlichen]** aus.

* Wählen Sie in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

   1. Wählen Sie dann unter **[!UICONTROL Aktion]** die Option **[!UICONTROL In Brand Portal veröffentlichen]** und unter **[!UICONTROL Zeitplan]** die Option **[!UICONTROL Jetzt]** aus. Klicken Sie auf **[!UICONTROL Weiter]**.

   2. Bestätigen Sie Ihre Auswahl unter **[!UICONTROL Bereich]** und klicken Sie auf **[!UICONTROL In Brand Portal veröffentlichen]**.

Eine Meldung erscheint, die besagt, dass die Assets zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurden. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um die veröffentlichten Assets zu sehen.

## Assets später veröffentlichen {#publish-to-bp-later}

So planen Sie die Veröffentlichung der Assets in Brand Portal zu einem späteren Zeitpunkt:

1. Nachdem Sie die zu veröffentlichenden Assets/Ordner ausgewählt haben, wählen Sie oben in der Symbolleiste **[!UICONTROL Veröffentlichung verwalten]** aus.

1. Wählen Sie auf der Seite **[!UICONTROL Veröffentlichung verwalten]** die Option **[!UICONTROL In Brand Portal veröffentlichen]** unter **[!UICONTROL Aktion]** und dann **[!UICONTROL Später]** unter **[!UICONTROL Zeitplan]** aus.

   ![publishlaterbp-1](assets/publishlaterbp-1.png)

1. Wählen Sie ein **[!UICONTROL Aktivierungsdatum]** aus und geben Sie die Zeit an. Klicken Sie auf **[!UICONTROL Weiter]**.

1. Wählen Sie ein **Aktivierungsdatum** aus und geben Sie die Zeit an. Klicken Sie auf **Weiter**.

1. Geben Sie einen **[!UICONTROL Workflow-Titel]** in **[!UICONTROL Workflows]** an. Klicken Sie auf **[!UICONTROL Später veröffentlichen]**.

   ![publishworkflow](assets/publishworkflow.png)

Melden Sie sich jetzt bei Brand Portal an, um zu sehen, ob die veröffentlichten Assets auf der Brand Portal-Benutzeroberfläche verfügbar sind.

![bp_landingpage](assets/bp_landingpage.png)
