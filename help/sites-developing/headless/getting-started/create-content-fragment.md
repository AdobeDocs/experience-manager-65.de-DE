---
title: Schnellstartanleitung zum Erstellen von Inhaltsfragmenten per Headless-Implementierung
description: Erfahren Sie, wie Sie mit den Inhaltsfragmenten von AEM seitenunabhängige Inhalte für die Headless-Bereitstellung entwerfen, erstellen, kuratieren und verwenden können.
exl-id: 5787204d-bcce-447e-b98c-2bc1c0d744c3
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
source-wordcount: '378'
ht-degree: 100%
---
# Schnellstartanleitung zum Erstellen von Inhaltsfragmenten per Headless-Implementierung {#creating-content-fragments}

Erfahren Sie, wie Sie mit den Inhaltsfragmenten von AEM seitenunabhängige Inhalte für die Headless-Bereitstellung entwerfen, erstellen, kuratieren und verwenden können.

## Was sind Inhaltsfragmente? {#what-are-content-fragments}

[Nachdem Sie einen Asset-Ordner erstellt haben](create-assets-folder.md), in dem Ihre Inhaltsfragmente gespeichert werden sollen, können Sie nun Fragmente erstellten.

Mit Inhaltsfragmenten können Sie seitenunabhängige Inhalte entwerfen, erstellen, kuratieren und veröffentlichen. Außerdem können Sie Inhalte zur Verwendung an mehreren Orten und über mehrere Kanäle hinweg vorbereiten.

Inhaltsfragmente enthalten strukturierte Inhalte und können im JSON-Format bereitgestellt werden.

## Erstellen eines Inhaltsfragments {#how-to-create-a-content-fragment}

Inhaltsautorinnen und -autoren können eine beliebige Anzahl von Inhaltsfragmenten für ihre Inhalte erstellen. Das die zentrale Aufgabe, die sie in AEM ausführen. Für die Zwecke dieser Anleitung für den Einstieg müssen wir nur ein Fragment erstellen.

1. Melden Sie sich bei AEM an und wählen Sie im Hauptmenü **Navigation > Assets** aus.
1. Navigieren Sie zu dem [zuvor erstellten Ordner](create-assets-folder.md).
1. Klicken Sie auf **Erstellen > Inhaltsfragment**.
1. Die Erstellung eines Inhaltsfragments erfolgt mithilfe eines Assistenten in zwei Schritten. Wählen Sie zuerst das Modell aus, das Sie zum Erstellen des Inhaltsfragments verwenden möchten, und klicken Sie dann auf **Weiter**.
   * Die verfügbaren Modelle hängen von der [**Cloud-Konfiguration** ab, die Sie für den Asset-Ordner](create-assets-folder.md) definiert haben, in dem Sie das Inhaltsfragment erstellen.
   * Wenn Ihnen die Meldung `We could not find any models` angezeigt wird, überprüfen Sie die Konfiguration Ihres Asset-Ordners.

   ![Auswählen des Inhaltsfragmentmodells](assets/content-fragment-model-select.png)
1. Geben Sie nach Bedarf einen **Titel**, eine **Beschreibung** und **Tags** ein und klicken Sie auf **Erstellen**.

   ![Inhaltsfragment erstellen](assets/content-fragment-create.png)
1. Klicken Sie im Bestätigungsfenster auf **Öffnen**.

   ![Bestätigung der Inhaltsfragment-Erstellung ](assets/content-fragment-confirmation.png)
1. Geben Sie im Inhaltsfragment-Editor die Details des Inhaltsfragments an.

   ![Inhaltsfragmente-Editor](assets/content-fragment-edit.png)
1. Klicken Sie auf **Speichern** oder **Speichern und schließen**.

Inhaltsfragmente können auf andere Inhaltsfragmente verweisen, was bei Bedarf eine verschachtelte Inhaltsstruktur ermöglicht.

Inhaltsfragmente können auch auf andere Assets in AEM verweisen. [Diese Assets müssen in AEM gespeichert werden](/help/assets/manage-assets.md), bevor ein Verweis auf das Inhaltsfragment erstellt wird.

## Nächste Schritte {#next-steps}

Nachdem Sie nun ein Inhaltsfragment erstellt haben, können Sie zum letzten Teil der Anleitung für den Einstieg übergehen und [API-Anfragen erstellen, um auf Inhaltsfragmente zuzugreifen und diese bereitzustellen](create-api-request.md).

>[!TIP]
>
>Ausführliche Informationen zur Verwaltung von Inhaltsfragmenten finden Sie in der [Dokumentation zu Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md).
