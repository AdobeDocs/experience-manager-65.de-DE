---
title: Veröffentlichen von Sammlungen in Brand Portal
description: Erfahren Sie, wie Sie Sammlungen in Brand Portal veröffentlichen und Veröffentlichungen rückgängig machen können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
docset: aem65
feature: Brand Portal
role: User
exl-id: 8f426012-d9ec-418e-8ab6-78e4aeff7538
solution: Experience Manager, Experience Manager Assets
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: d09181b5-a36a-43de-ba01-36641440bc43
    internal-label: Experience Manager Assets
feature_v2:
  - id: a45b1e7f-e65f-4cd3-be86-5cec5d9449ef
    internal-label: Content management
subfeature_v2:
  - id: e00c7c12-7035-41fe-ad76-1ec82c8c3f01
    internal-label: Brand Portal
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 100%
---
# Veröffentlichen von Sammlungen in Brand Portal {#publish-collections-to-brand-portal}

Als Adobe Experience Manager (AEM) Assets-Admin können Sie für Ihre Organisation Sammlungen in der AEM Assets Brand Portal-Instanz veröffentlichen. Allerdings müssen Sie zunächst AEM Assets mit Brand Portal integrieren. Weitere Informationen finden Sie unter [Konfigurieren von AEM Assets mit Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md).

Spätere Änderungen an der ursprünglichen Sammlung in AEM Assets spiegeln sich erst bei erneuter Veröffentlichung der Sammlung in Brand Portal wider. Auf diese Weise wird sichergestellt, dass laufende Änderungen (Work-in-Progress, WIP) nicht in Brand Portal verfügbar sind. Nur genehmigte, von einem Admin veröffentlichte Änderungen sind in Brand Portal verfügbar.

>[!NOTE]
>
>Inhaltsfragmente können nicht in Brand Portal veröffentlicht werden. Wenn Sie daher in der AEM-Autoreninstanz Inhaltsfragmente auswählen, ist die Aktion **In Brand Portal veröffentlichen** nicht verfügbar.
>
>Wenn Sammlungen, die Inhaltsfragmente enthalten, über AEM Author in Brand Portal veröffentlicht werden, wird der gesamte Inhalt des Ordners mit Ausnahme der Inhaltsfragmente in der Brand Portal-Oberfläche repliziert.

## Veröffentlichen einer Sammlung in Brand Portal {#publish-a-collection-to-brand-portal}

1. Klicken Sie in der Benutzeroberfläche von AEM Assets auf das AEM-Logo.
1. Gehen Sie von der Seite **Navigation** aus zu **Assets > Sammlungen**.
1. Wählen Sie in der Konsole „Sammlungen“ die Sammlung aus, die Sie in Brand Portal veröffentlichen möchten.

   ![Sammlung auswählen](assets/select_collection.png)

1. Klicken Sie in der Symbolleiste auf **In Brand Portal veröffentlichen**.
1. Klicken Sie im Bestätigungsdialogfeld auf **Veröffentlichen**.
1. Schließen Sie die Bestätigungsmeldung.
1. Melden Sie sich bei Brand Portal als Admin an. Die veröffentlichte Sammlung steht in der Konsole „Sammlungen“ zur Verfügung.

   ![Veröffentlichte Sammlung](assets/published_collection.png)

## Veröffentlichung von Sammlungen aufheben {#unpublish-collections}

Sie können die Veröffentlichung von Sammlungen, die über AEM Assets in Brand Portal erfolgt sind, rückgängig machen. Nachdem Sie die Veröffentlichung der ursprünglichen Sammlung rückgängig gemacht haben, ist die zugehörige Kopie nicht länger für Brand Portal-Benutzer verfügbar.

1. Wählen Sie über die Konsole „Sammlungen“ der AEM Assets-Instanz die Sammlung aus, deren Veröffentlichung rückgängig gemacht werden soll.

   ![select_collection-1](assets/select_collection-1.png)

1. Klicken Sie in der Symbolleiste auf das Symbol **Aus Brand Portal löschen**.
1. Klicken Sie im Dialogfeld auf **Veröffentlichung aufheben**.
1. Schließen Sie die Bestätigungsmeldung. Die Sammlung wird aus der Brand Portal-Oberfläche entfernt.
