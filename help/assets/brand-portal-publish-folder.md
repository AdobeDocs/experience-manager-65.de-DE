---
title: Veröffentlichen von Ordnern in Brand Portal
description: Erfahren Sie, wie Sie Sammlungen in Brand Portal veröffentlichen und Veröffentlichungen rückgängig machen können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
docset: aem65
feature: Brand Portal
role: User
exl-id: 92a156f0-ce2a-4c83-bd57-0c29efbf784f
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 100%

---

# Veröffentlichen von Ordnern in Brand Portal{#publish-folders-to-brand-portal}

Als Adobe Experience Manager (AEM) Assets-Admin können Sie für Ihre Organisation Assets und Ordner in der AEM Assets Brand Portal-Instanz veröffentlichen (oder den Veröffentlichungs-Workflow für einen späteren Zeitpunkt planen). Allerdings müssen Sie zunächst AEM Assets mit Brand Portal integrieren. Weitere Informationen finden Sie unter [Konfigurieren von AEM Assets mit Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md).

Nachdem Sie ein Asset oder einen Ordner veröffentlicht haben, ist es bzw. er in Brand Portal für Benutzer verfügbar.

Falls Sie danach Änderungen am ursprünglichen Asset oder am Ordner in AEM Assets vornehmen, werden die Änderungen erst in Brand Portal widergespiegelt, wenn Sie das Asset oder den Ordner erneut veröffentlichen. Mit dieser Funktion wird sichergestellt, dass Änderungen im Rahmen der laufenden Bearbeitung nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Administrator veröffentlichte Änderungen sind in Brand Portal verfügbar.

## Veröffentlichen von Ordnern in Brand Portal {#publish-folders-to-brand-portal-1}

1. Bewegen Sie auf der AEM Assets-Benutzeroberfläche den Mauszeiger auf den gewünschten Ordner und wählen Sie aus den Schnellaktionen die Option **Veröffentlichen** aus.

   Alternativ können Sie den gewünschten Ordner auswählen und den weiteren Schritten folgen.

   ![publish2bp](assets/publish2bp.png)

1. **Ordner jetzt veröffentlichen**

   Um die ausgewählten Ordner in Brand Portal zu veröffentlichen, führen Sie einen der folgenden Schritte aus:

   * Wählen Sie in der Symbolleiste **Quick Publish** aus. Wählen Sie dann im Menü die Option **In Brand Portal veröffentlichen** aus.

   * Wählen Sie in der Symbolleiste **Veröffentlichung verwalten** aus.

   1. Wählen Sie in **Aktion** die Option **In Brand Portal veröffentlichen** aus, wählen Sie in **Zeitplan** die Option **Jetzt** aus und klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl in **Umfang** und klicken Sie auf **In Brand Portal veröffentlichen**.

   Eine Meldung erscheint, die besagt, dass der Ordner zur Veröffentlichung in Brand Portal in die Warteschlange gestellt wurde. Melden Sie sich bei der Brand Portal-Benutzeroberfläche an, um den veröffentlichten Ordner zu sehen.

   **Späteres Veröffentlichen von Ordnern**

   So planen Sie den Workflow zum Veröffentlichen von Asset-Ordnern in Brand Portal zu einem späteren Zeitpunkt:

   1. Sobald Sie die zu veröffentlichenden Assets/Ordner ausgewählt haben, wählen Sie oben in der Symbolleiste **Veröffentlichung verwalten** aus.
   1. Wählen Sie in **Aktion** die Option **In Brand Portal veröffentlichen** aus und wählen Sie in **Zeitplan** die Option **Später** aus.

      ![publishlaterbp](assets/publishlaterbp.png)

   1. Wählen Sie ein **Aktivierungsdatum** aus und geben Sie die Zeit an. Klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl unter **Umfang**. Klicken Sie auf **Weiter**.
   1. Geben Sie einen Workflow-Titel unter **Workflows** an. Klicken Sie auf **Später veröffentlichen**.

      ![manageschedulepub](assets/manageschedulepub.png)

## Veröffentlichung von Ordnern in Brand Portal rückgängig machen {#unpublish-folders-from-brand-portal}

Sie können alle in Brand Portal veröffentlichte Asset-Ordner entfernen, indem Sie die Veröffentlichung über die AEM-Autoreninstanz rückgängig machen. Nachdem Sie die Veröffentlichung des ursprünglichen Ordners aufgehoben haben, ist dessen Kopie nicht mehr für Brand Portal-Benutzer verfügbar.

Sie haben die Möglichkeit, die Veröffentlichung von Ordnern aus Brand Portal schnell aufzuheben oder sie für einen späteren Zeitpunkt zu planen. So machen Sie die Veröffentlichung von Assets/Ordnern in Brand Portal rückgängig:

1. Wählen Sie in der AEM Assets-Benutzeroberfläche in der AEM-Autoreninstanz den Ordner aus, dessen Veröffentlichung Sie rückgängig machen möchten.

   ![publish2bp-1](assets/publish2bp.png)

1. Klicken Sie in der Symbolleiste auf **Veröffentlichung verwalten**.

1. **Sofortiges Rückgängigmachen der Veröffentlichung in Brand Portal**

   So heben Sie die Veröffentlichung des gewünschten Ordners in Brand Portal schnell auf:

   1. Wählen Sie in der Symbolleiste **Veröffentlichung verwalten** aus.
   1. Wählen Sie in **Aktion** die Option **Veröffentlichung in Brand Portal rückgängig machen** aus, wählen Sie in **Zeitplan** die Option **Jetzt** aus und klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl in **Umfang** und klicken Sie auf **Veröffentlichung in Brand Portal rückgängig machen**.

   ![confirm-unpublish](assets/confirm-unpublish.png)

   **Späteres Rückgängigmachen der Veröffentlichung in Brand Portal**

   So können Sie die Veröffentlichung eines Ordners in Brand Portal zu einem späteren Zeitpunkt rückgängig machen:

   1. Wählen Sie in der Symbolleiste **Veröffentlichung verwalten** aus.
   1. Wählen Sie in **Aktion** die Option **Veröffentlichung in Brand Portal rückgängig machen** aus und wählen Sie in **Zeitplan** die Option **Später** aus.
   1. Wählen Sie ein **Aktivierungsdatum** aus und geben Sie die Zeit an. Klicken Sie auf **Weiter**.
   1. Bestätigen Sie Ihre Auswahl unter **Umfang** und klicken Sie auf **Weiter**.
   1. Geben Sie einen **Workflow-Titel** in **Workflows** an. Klicken Sie auf **Veröffentlichung später rückgängig machen.**

      ![unpublishworkflows](assets/unpublishworkflows.png)

>[!NOTE]
>
>Das Verfahren zum Veröffentlichen bzw. Aufheben der Veröffentlichung eines Assets in Brand Portal ähnelt dem entsprechenden Verfahren für einen Ordner.
