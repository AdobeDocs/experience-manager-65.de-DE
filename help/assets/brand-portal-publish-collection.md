---
title: Veröffentlichen von Sammlungen in Brand Portal
seo-title: Veröffentlichen von Sammlungen in Brand Portal
description: Erfahren Sie, wie Sie Sammlungen in Brand Portal veröffentlichen und Veröffentlichungen rückgängig machen können.
seo-description: Erfahren Sie, wie Sie Sammlungen in Brand Portal veröffentlichen und Veröffentlichungen rückgängig machen können.
uuid: 7de58548-4cfa-4a94-bac7-9e914dee9042
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
discoiquuid: 90e3fd0e-9bc3-4aff-8c7b-7408f5b940e8
docset: aem65
translation-type: tm+mt
source-git-commit: 9c73abc3291f2847c705cb649d2993fb186b0993

---


# Veröffentlichen von Sammlungen in Brand Portal {#publish-collections-to-brand-portal}

Als Adobe Experience Manager (AEM) Assets-Administrator können Sie für Ihre Organisation Sammlungen in der AEM Assets Brand Portal-Instanz veröffentlichen. Allerdings müssen Sie zunächst AEM Assets mit Brand Portal integrieren. For details, see [Configure AEM Assets integration with Brand Portal](/help/assets/brand-portal-configuring-integration.md).

Wenn Sie nachfolgende Änderungen an der ursprünglichen Sammlung in AEM Assets vornehmen, werden die Änderungen erst dann im Markenportal übernommen, wenn Sie die Sammlung erneut veröffentlichen. Mit dieser Eigenschaft wird sichergestellt, dass in der Arbeit befindliche Änderungen nicht im Markenportal verfügbar sind. Nur genehmigte Änderungen, die von einem Administrator veröffentlicht werden, sind im Markenportal verfügbar.

>[!NOTE]
>
>Inhaltsfragmente können nicht in Brand Portal veröffentlicht werden. Therefore, if you select content fragment(s) on AEM Author, then **Publish to Brand Portal** action is not available.
>
>Wenn Sammlungen, die Inhaltsfragmente enthalten, über die AEM-Autoreninstanz in Brand Portal veröffentlicht werden, wird der gesamte Inhalt des Ordners mit Ausnahme der Inhaltsfragmente auf der Brand Portal-Oberfläche repliziert.

## Veröffentlichen einer Sammlung in Brand Portal {#publish-a-collection-to-brand-portal}

1. Klicken Sie in der AEM Assets-Benutzeroberfläche auf AEM-Logo.
1. From **Navigation** page, go to **Assets > Collections**.
1. Wählen Sie in der Konsole &quot;Sammlungen&quot;die Sammlung aus, die Sie im Markenportal veröffentlichen möchten.

   ![select_collection](assets/select_collection.png)

1. From the toolbar, click **Publish to Brand Portal**.
1. In the confirmation dialog, click **Publish**.
1. Schließen Sie die Bestätigungsmeldung.
1. Melden Sie sich bei Brand Portal als Administrator an. Die veröffentlichte Sammlung steht in der Konsole „Sammlungen“ zur Verfügung.

   ![veröffentlichte Sammlung](assets/published_collection.png)

## Veröffentlichung von Sammlungen rückgängig machen {#unpublish-collections}

Sie können die Veröffentlichung von Sammlungen, die Sie aus AEM Assets im Markenportal veröffentlichen, rückgängig machen. Nachdem Sie die Veröffentlichung der ursprünglichen Sammlung rückgängig gemacht haben, steht die Kopie nicht mehr für Markenportal-Benutzer zur Verfügung.

1. Wählen Sie über die Konsole „Sammlungen“ der AEM Assets-Instanz die Sammlung aus, deren Veröffentlichung rückgängig gemacht werden soll.

   ![select_collection-1](assets/select_collection-1.png)

1. From the toolbar, click **Remove from Brand Portal** icon.
1. In the dialog, click **Unpublish**.
1. Schließen Sie die Bestätigungsmeldung. Die Sammlung wird aus der Benutzeroberfläche des Markenportals entfernt.

