---
title: Schnellstartanleitung zum Erstellen von Inhaltsfragmentmodellen per Headless-Implementierung
description: Definieren Sie die Struktur des Inhalts, den Sie mithilfe der Headless-Funktionen von Adobe Experience Manager (AEM) durch Inhaltsfragmentmodelle erstellen und bereitstellen möchten.
exl-id: 653e35c9-7b6a-49ae-b55d-af2ec40e257d
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
  - id: d429a63e-ade4-4117-b04e-9b996d1c94ef
    internal-label: Integrations
  - id: c124fa01-25c5-42ec-adf6-21d1c114058b
    internal-label: Developer tools
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
  - id: a02b73a7-bdfc-4225-bdfd-69f7891ab55e
    internal-label: GraphQL
  - id: d781bc8f-52af-43f6-84d0-b73e59a130d5
    internal-label: Persisted queries
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 100%
---
# Schnellstartanleitung zum Erstellen von Inhaltsfragmentmodellen per Headless-Implementierung {#creating-content-fragment-models}

Definieren Sie die Struktur des Inhalts, den Sie mithilfe der Headless-Funktionen von Adobe Experience Manager (AEM) durch Inhaltsfragmentmodelle erstellen und bereitstellen möchten.

## Was sind Inhaltsfragmentmodelle? {#what-are-content-fragment-models}

[Nachdem Sie nun eine Konfiguration erstellt haben](create-configuration.md), können Sie damit Inhaltsfragmentmodelle erstellen.

Inhaltsfragmentmodelle definieren die Struktur der Daten und Inhalte, die Sie in AEM erstellen und verwalten. Sie dienen als Gerüst für Ihre Inhalte. Bei der Erstellung von Inhalten wählen Autoren aus den von Ihnen definierten Inhaltsfragmentmodellen aus, die sie bei der Erstellung von Inhalten anleiten.

## Erstellen eines Inhaltsfragmentmodells {#how-to-create-a-content-fragment-model}

Eine Informationsarchitektin oder ein Informationsarchitekt würde diese Aufgaben nur sporadisch durchführen, da neue Modelle erforderlich sind. Für diese ersten Schritte erstellen Sie nur ein Modell.

1. Melden Sie sich bei AEM an und wählen Sie im Hauptmenü **Tools > Assets > Inhaltsfragmentmodelle** aus.
1. Klicken Sie auf den Ordner, der durch die Erstellung der Konfiguration angelegt wurde.

   ![Der Ordner „Modelle“](assets/models-folder.png)
1. Klicken Sie auf **Erstellen**.
1. Geben Sie einen **Modell-Titel**, **Tags** und eine **Beschreibung** an. Sie können auch **Modell aktivieren** aus- oder abwählen, um zu steuern, ob das Modell unmittelbar nach der Erstellung aktiviert wird.

   ![Erstellen eines Modells](assets/models-create.png)
1. Klicken Sie im Bestätigungsfenster auf **Öffnen**, um Ihr Modell zu konfigurieren.

   ![Bestätigungsfenster](assets/models-confirmation.png)
1. Erstellen Sie mit dem **Inhaltsfragmentmodell-Editor** das Inhaltsfragmentmodell, indem Sie Felder aus der Spalte **Datentypen** ziehen und ablegen.

   ![Ziehen und Ablegen von Feldern](assets/models-drag-and-drop.png)

1. Nachdem Sie ein Feld platziert haben, müssen Sie dessen Eigenschaften konfigurieren. Der Editor wechselt automatisch zur Registerkarte **Eigenschaften** für das hinzugefügte Feld, wo Sie die erforderlichen Felder angeben können.

   ![Konfigurieren von Eigenschaften](assets/models-configure-properties.png)
1. Wenn Sie mit der Erstellung des Modells fertig sind, klicken Sie auf **Speichern**.

1. Der Modus des neu erstellten Modells hängt davon ab, ob Sie beim Erstellen des Modells **Modell aktivieren** ausgewählt haben:
   * ausgewählt – das neue Modell ist bereits **aktiviert**
   * nicht ausgewählt – das neue Modell wird im Modus **Entwurf** erstellt

1. Wenn nicht bereits aktiviert, muss das Modell **aktiviert** werden, um es zu verwenden.
   1. Wählen Sie das soeben erstellte Modell aus und klicken Sie dann auf **Aktivieren**.

      ![Aktivieren des Modells](assets/models-enable.png)
   1. Bestätigen Sie die Aktivierung des Modells, indem Sie im Bestätigungsdialogfeld auf **Aktivieren** tippen oder klicken.

      ![Dialogfeld zum Bestätigen der Aktivierung](assets/models-enabling.png)
1. Das Modell ist jetzt aktiviert und einsatzbereit.

   ![Modell aktiviert](assets/models-enabled.png)

Der **Inhaltsfragmentmodelleditor** unterstützt viele verschiedene Datentypen wie einfache Textfelder, Asset-Referenzen, Verweise auf andere Modelle und JSON-Daten.

Sie können mehrere Modelle erstellen. Modelle können auf andere Inhaltsfragmente verweisen. Verwenden Sie [Konfigurationen](create-configuration.md), um Ihre Modelle zu organisieren.

## Nächste Schritte {#next-steps}

Nachdem Sie nun die Strukturen der Inhaltsfragmente durch die Erstellung von Modellen definiert haben, können Sie mit dem dritten Teil dieses Erste-Schritte-Handbuchs weitermachen und [Ordner erstellen, in denen Sie die Fragmente selbst speichern](create-assets-folder.md).

>[!TIP]
>
>Ausführliche Informationen zu Inhaltsfragmentmodellen finden Sie in der [Dokumentation zu Inhaltsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md).
