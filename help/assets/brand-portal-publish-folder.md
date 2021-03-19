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
feature: Brand Portal
role: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 67%

---


# Veröffentlichen von Ordnern in Brand Portal{#publish-folders-to-brand-portal}

Als Adobe Experience Manager (AEM) Assets-Administrator können Sie für Ihre Organisation Assets und Ordner in der AEM Assets Brand Portal-Instanz veröffentlichen (oder den Veröffentlichungs-Workflow für einen späteren Zeitpunkt planen). Allerdings müssen Sie zunächst AEM Assets mit Brand Portal integrieren. Weitere Informationen finden Sie unter [Konfigurieren der von AEM Assets mit Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md).

Nachdem Sie ein Asset oder einen Ordner veröffentlicht haben, steht es Benutzern im Markenportal zur Verfügung.

Wenn Sie nachfolgende Änderungen am ursprünglichen Asset oder Ordner in AEM Assets vornehmen, werden die Änderungen erst dann im Markenportal übernommen, wenn Sie das Asset oder den Ordner erneut veröffentlichen. Mit dieser Funktion wird sichergestellt, dass Änderungen im Rahmen der laufenden Bearbeitung nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Administrator veröffentlichte Änderungen sind in Brand Portal verfügbar.

## Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal-1}

1. Bewegen Sie den Mauszeiger in der AEM Assets-Oberfläche über den gewünschten Ordner und wählen Sie in den Schnellaktionen die Option **Veröffentlichen**.

   Alternativ können Sie den gewünschten Ordner auswählen und den weiteren Schritten folgen.

   ![publish2bp](assets/publish2bp.png)

1. **Ordner jetzt veröffentlichen** 

   Um die ausgewählten Ordner in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Symbolleiste **Quick Publish** aus. Wählen Sie dann im Menü **In Markenportal veröffentlichen**.

   * Wählen Sie in der Symbolleiste **Veröffentlichung verwalten** aus.
   1. Wählen Sie unter **Aktion** **Auf Markenportal veröffentlichen** aus, wählen Sie **Einplanen** **Jetzt** und klicken Sie auf **Weiter.**
   1. Bestätigen Sie Ihre Auswahl in **Umfang** und klicken Sie auf **In Brand Portal veröffentlichen**.

   Eine Meldung erscheint, die besagt, dass der Ordner zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurde. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um den veröffentlichten Ordner zu sehen.

   **Ordner später veröffentlichen**

   So planen Sie die Veröffentlichung von Asset-Ordnern im Brand Portal auf ein späteres Datum oder eine spätere Uhrzeit:

   1. Nachdem Sie die zu veröffentlichenden Assets/Ordner ausgewählt haben, wählen Sie in der Symbolleiste oben die Option **Veröffentlichung verwalten**.
   1. Wählen Sie unter **Aktion** **In Markenportal veröffentlichen** aus und wählen Sie **Einplanen** **Später**.

      ![publishlaterbp](assets/publishlaterbp.png)

   1. Wählen Sie ein **Aktivierungsdatum** aus und geben Sie die Zeit an. Klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl unter **Umfang**. Klicken Sie auf **Weiter**.
   1. Geben Sie einen Workflow-Titel unter **Workflows** an. Klicken Sie auf **Später veröffentlichen**.

      ![manageschedulepub](assets/manageschedulepub.png)



## Veröffentlichung von Ordnern in Brand Portal rückgängig machen {#unpublish-folders-from-brand-portal}

Sie können alle in Brand Portal veröffentliche Assets/Ordner entfernen, indem Sie die Veröffentlichung über die AEM-Autoreninstanz rückgängig machen. Nachdem Sie die Veröffentlichung des ursprünglichen Ordners aufgehoben haben, ist dessen Kopie nicht mehr für Brand Portal-Benutzer verfügbar.

Sie können die Veröffentlichung der Ordner in Brand Portal sofort rückgängig machen oder diesen Vorgang für einen späteren Zeitpunkt planen. So machen Sie die Veröffentlichung von Assets/Ordnern in Brand Portal rückgängig:

1. Wählen Sie in der AEM Assets-Benutzeroberfläche in der AEM-Autoreninstanz den Ordner aus, dessen Veröffentlichung Sie rückgängig machen möchten.

   ![publish2bp-1](assets/publish2bp.png)

1. Klicken Sie in der Symbolleiste auf **Veröffentlichung verwalten**.

1. **Veröffentlichung in Brand Portal jetzt rückgängig machen**

   So können Sie die Veröffentlichung des gewünschten Ordners in Brand Portal schnell rückgängig machen:

   1. Wählen Sie in der Symbolleiste **Veröffentlichung verwalten** aus.
   1. Wählen Sie unter **Aktion** **Veröffentlichung rückgängig machen aus dem Markenportal** aus **Einplanen** **Jetzt** und klicken Sie auf **Weiter.**
   1. Bestätigen Sie Ihre Auswahl in **Umfang** und klicken Sie auf **Veröffentlichung in Brand Portal rückgängig machen**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Rückgängigmachen der Veröffentlichung aus dem Markenportal**

   So können Sie die Veröffentlichung eines Ordners in Brand Portal zu einem späteren Zeitpunkt rückgängig machen:

   1. Wählen Sie in der Symbolleiste **Veröffentlichung verwalten** aus.
   1. Wählen Sie unter **Aktion** **Rückgängigmachen der Veröffentlichung im Markenportal** und unter **Einplanen** **Später**.
   1. Wählen Sie ein **Aktivierungsdatum** aus und geben Sie die Zeit an. Klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl unter **Umfang** und klicken Sie auf **Weiter**.
   1. Geben Sie einen **Workflow-Titel** in **Workflows** an. Klicken Sie auf **Veröffentlichung später rückgängig machen.**

      ![unpublishworkflows](assets/unpublishworkflows.png)


>[!NOTE]
>
>Das Verfahren zum Veröffentlichen/Rückgängigmachen der Veröffentlichung eines Assets im/vom Markenportal ist dem entsprechenden Vorgang für einen Ordner ähnlich.

