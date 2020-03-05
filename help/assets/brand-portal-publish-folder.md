---
title: Veröffentlichen von Ordnern in Brand Portal
seo-title: Veröffentlichen von Ordnern in Brand Portal
description: Es wird beschrieben, wie Sie Ordner in Brand Portal veröffentlichen und die Veröffentlichung aufheben.
seo-description: Es wird beschrieben, wie Sie Ordner in Brand Portal veröffentlichen und die Veröffentlichung aufheben.
uuid: 350beb85-c0fb-4a1c-8597-c03592c02d3d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: 39b8cf9b-afec-4c9a-8a5d-7fc87e643f26
docset: aem65
translation-type: tm+mt
source-git-commit: 9f923782d3d0a7bdf45b18e8025bd2d083acf77c

---


# Veröffentlichen von Ordnern in Brand Portal{#publish-folders-to-brand-portal}

Als Adobe Experience Manager (AEM) Assets-Administrator können Sie für Ihre Organisation Assets und Ordner in der AEM Assets Brand Portal-Instanz veröffentlichen (oder den Veröffentlichungs-Workflow für einen späteren Zeitpunkt planen). Allerdings müssen Sie zunächst AEM Assets mit Brand Portal integrieren. For details, see [Configure AEM Assets with Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md).

Nachdem Sie ein Asset oder einen Ordner veröffentlicht haben, steht es Benutzern im Markenportal zur Verfügung.

Wenn Sie nachfolgende Änderungen am ursprünglichen Asset oder Ordner in AEM Assets vornehmen, werden die Änderungen erst dann im Markenportal übernommen, wenn Sie das Asset oder den Ordner erneut veröffentlichen. Mit dieser Funktion wird sichergestellt, dass derzeit vorgenommene Änderungen nicht im Markenportal verfügbar sind. Nur genehmigte Änderungen, die von einem Administrator veröffentlicht werden, sind im Markenportal verfügbar.

## Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal-1}

1. From the AEM Assets interface, hover over the desired folder and select **Publish** option from the quick actions.

   Alternativ können Sie den gewünschten Ordner auswählen und den weiteren Schritten folgen.

   ![publish2bp](assets/publish2bp.png)

1. **Ordner jetzt veröffentlichen** 

   Um die ausgewählten Ordner in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

   * From the toolbar, select **Quick Publish**. Then from the menu, select **Publish to Brand Portal**.

   * From the toolbar, select **Manage Publication**.
   1. Wählen Sie in **Aktion** **Auf Markenportal** veröffentlichen, **Planen** **jetzt** aus und klicken Sie auf **Weiter.**
   1. Bestätigen Sie Ihre Auswahl in **Scope** und klicken Sie auf In Markenportal **veröffentlichen**.
   Eine Meldung erscheint, die besagt, dass der Ordner zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurde. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um den veröffentlichten Ordner zu sehen.

   **Ordner später veröffentlichen**

   So planen Sie die Veröffentlichung von Asset-Ordnern im Brand Portal auf ein späteres Datum oder eine spätere Uhrzeit:

   1. Once you have selected assets/ folders to publish, select **Manage Publication** from the tool bar at the top.
   1. Wählen Sie in **Aktion** **Auf Markenportal** veröffentlichen aus und wählen Sie **Planung** **Später**.

      ![publishlaterbp](assets/publishlaterbp.png)

   1. Select an **Activation date** and specify time. Klicken Sie auf **Weiter**.
   1. Confirm your selection in **Scope**. Klicken Sie auf **Weiter**.
   1. Specify a Workflow title under **Workflows**. Click **Publish Later**.

      ![manageschedulepub](assets/manageschedulepub.png)



## Veröffentlichung von Ordnern in Brand Portal rückgängig machen {#unpublish-folders-from-brand-portal}

Sie können alle in Brand Portal veröffentliche Assets/Ordner entfernen, indem Sie die Veröffentlichung über die AEM-Autoreninstanz rückgängig machen. Nachdem Sie die Veröffentlichung des Originalordners rückgängig gemacht haben, steht die Kopie nicht mehr für Markenportal-Benutzer zur Verfügung.

Sie können die Veröffentlichung der Ordner in Brand Portal sofort rückgängig machen oder diesen Vorgang für einen späteren Zeitpunkt planen. So machen Sie die Veröffentlichung von Assets/Ordnern in Brand Portal rückgängig:

1. Wählen Sie in der AEM Assets-Benutzeroberfläche in der AEM-Autoreninstanz den Ordner aus, dessen Veröffentlichung Sie rückgängig machen möchten.

   ![publish2bp-1](assets/publish2bp.png)

1. From the toolbar, Click **Manage Publication**.

1. **Veröffentlichung in Brand Portal jetzt rückgängig machen**

   So können Sie die Veröffentlichung des gewünschten Ordners in Brand Portal schnell rückgängig machen:

   1. From the toolbar, select **Manage Publication**.
   1. Wählen Sie in **Aktion** **Veröffentlichung rückgängig machen aus Markenportal**, **Planung** **jetzt** und klicken Sie auf **Weiter.**
   1. Bestätigen Sie Ihre Auswahl in **Scope** und klicken Sie auf **Veröffentlichung im Markenportal** rückgängig machen.
   ![verify-unpublish](assets/confirm-unpublish.png)

   **Rückgängigmachen der Veröffentlichung aus dem Markenportal später**

   So können Sie die Veröffentlichung eines Ordners in Brand Portal zu einem späteren Zeitpunkt rückgängig machen:

   1. From the toolbar, select **Manage Publication**.
   1. From **Action** select **Unpublish from Brand Portal**, and from **Scheduling** select **Later**.
   1. Select an **Activation date** and specify the time. Klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl in **Scope** und klicken Sie auf **Weiter**.
   1. Specify a **Workflow title** in **Workflows**. Click **Unpublish Later.**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>Das Verfahren zum Veröffentlichen/Rückgängigmachen der Veröffentlichung eines Assets im/vom Markenportal ist dem entsprechenden Vorgang für einen Ordner ähnlich.

