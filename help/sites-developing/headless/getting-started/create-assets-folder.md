---
title: Schnellstartanleitung zum Erstellen von Asset-Ordnern per Headless-Implementierung
description: Verwenden Sie AEM-Inhaltsfragmentmodelle, um die Struktur von Inhaltsfragmenten zu definieren – die Grundlage für Ihren Headless-Content.
exl-id: 8d913056-fcfa-4cdd-b40a-771f13dfd0f4
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
source-wordcount: '369'
ht-degree: 97%
---
# Schnellstartanleitung zum Erstellen von Asset-Ordnern per Headless-Implementierung {#creating-an-assets-folder}

Verwenden Sie AEM-Inhaltsfragmentmodelle, um die Struktur von Inhaltsfragmenten zu definieren – die Grundlage für Ihren Headless-Content. Inhaltsfragmente werden dann in Asset-Ordnern gespeichert.

## Was ist ein Asset-Ordner? {#what-is-an-assets-folder}

[Nachdem Sie nun Inhaltsfragmentmodelle erstellt haben](create-content-model.md), die die Struktur definieren, die Sie für Ihre künftigen Inhaltsfragmente verwenden möchten, würden Sie sicher gern einige Fragmente erstellen.

Zunächst müssen Sie jedoch einen Ordner für Assets erstellen, in dem Sie diese speichern.

Asset-Ordner werden verwendet, um [herkömmliche Inhalts-Assets](/help/assets/manage-assets.md) wie Bilder und Videos sowie Inhaltsfragmente zu organisieren.

## Erstellen eines Asset-Ordners {#how-to-create-an-assets-folder}

Administratoren müssen nur gelegentlich Ordner erstellen, um Inhalte bei der Erstellung zu organisieren. Für die Zwecke dieser Anleitung für den Einstieg müssen wir nur einen Ordner erstellen.

1. Melden Sie sich bei AEM an und wählen Sie im Hauptmenü **Navigation > Assets > Dateien** aus.
1. Klicken Sie auf **Erstellen > Ordner**.
1. Geben Sie einen **Titel** und einen **Namen** für Ihren Ordner an.
   * Der **Titel** sollte beschreibend sein.
   * Der **Name** wird zum Knotennamen im Repository.
     * Er wird automatisch auf der Grundlage des Titels generiert und gemäß den [AEM-Benennungskonventionen](/help/sites-developing/naming-conventions.md) angepasst.
     * Er kann bei Bedarf angepasst werden.

   ![Ordner erstellen](assets/assets-folder-create.png)
1. Wählen Sie den soeben erstellten Ordner und dann in der Symbolleiste **Eigenschaften** aus (oder verwenden Sie den [Tastaturbefehl](/help/sites-authoring/keyboard-shortcuts.md) `p`).
1. Wählen Sie im Fenster **Eigenschaften** die Registerkarte **Cloud-Services** aus.
1. Wählen Sie für **Cloud-Konfiguration** die [Konfiguration aus, die Sie zuvor erstellt haben.](create-configuration.md)
   ![Konfigurieren des Asset-Ordners](assets/assets-folder-configure.png)
1. Klicken Sie auf **Speichern und schließen**.
1. Klicken Sie im Bestätigungsfenster auf **OK**.

   ![Bestätigungsfenster](assets/assets-folder-confirmation.png)

Sie können im soeben erstellten Ordner weitere Unterordner erstellen. Die Unterordner übernehmen die **Cloud-Konfiguration** des übergeordneten Ordners. Dies kann jedoch überschrieben werden, wenn Sie Modelle aus einer anderen Konfiguration verwenden möchten.

Wenn Sie eine lokalisierte Site-Struktur verwenden, können Sie unter Ihrem neuen Ordner [einen Sprachstamm](/help/assets/multilingual-assets.md) erstellen.

## Nächste Schritte {#next-steps}

Nachdem Sie nun einen Ordner für Ihre Inhaltsfragmente erstellt haben, können Sie zum vierten Teil der Anleitung für den Einstieg übergehen und [Inhaltsfragmente erstellen](create-content-fragment.md).

>[!TIP]
>
>Ausführliche Informationen zur Verwaltung von Inhaltsfragmenten finden Sie in der [Dokumentation zu Inhaltsfragmenten](/help/assets/content-fragments/content-fragments.md).
