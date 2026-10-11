---
title: Arbeiten mit Projekt-Workflows
description: Standardmäßig sind zahlreiche vorkonfigurierte Projekt-Workflows verfügbar.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
exl-id: 407fc164-291d-42f6-8c46-c1df9ba3d454
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Workflow
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
  - id: f6a6f91a-8819-530a-8e7b-c50884a25aef
    internal-label: Workflow
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 96%
---

# Arbeiten mit Projekt-Workflows {#working-with-project-workflows}

Folgende vorkonfigurierte Projekt-Workflows sind im Lieferumfang enthalten:

* **Projektgenehmigungs-Workflow** – Mit diesem Workflow können Sie Inhalte einer Benutzerin bzw. einem Benutzer zuzuweisen, prüfen und bestätigen.
* **Launch anfragen** - Ein Workflow, der einen Launch anfordert.
* **Einstiegsseite anfragen** - Dieser Workflow fragt eine Landingpage an.
* **E-Mail anfragen** - Workflow zum Anfragen einer E-Mail.
* **Produkt-Fotoshooting und Produkt-Fotoshooting (Commerce)** - Ordnet Assets Produkten zu
* **DAM-Kopie erstellen und übersetzen und DAM-Sprachkopie erstellen** – Erstellt übersetzte Binärdateien, Metadaten und Tags für Assets und Ordner.

Je nachdem, welche Projektvorlage Sie auswählen, stehen Ihnen bestimmte Workflows zur Verfügung:

|   | **Einfaches Projekt** | **Medienprojekt** | **Projekt für Produkt-Fotoshooting** | **Übersetzungsprojekt** |
|---|:-:|:-:|:-:|:-:|
| Kopie anfragen |  | x |  |  |
| Produkt-Fotoshooting |  | x | x |  |
| Produkt-Fotoshooting (Commerce) |  |  | x |  |
| Projektgenehmigung | x |  |  |  |
| Launch anfragen | x |  |  |  |
| Landingpage anfragen | x |  |  |  |
| E-Mail anfragen | x |  |  |  |
| DAM Create Language Copy&ast; |  |  |  | x |
| DAM - Erstellen und Übersetzen von Sprachkopien&ast; |  |  |  | x |

>[!NOTE]
>
>&ast; Diese Workflows werden in Projekten nicht über die Kachel **Workflow** gestartet. Weitere Informationen finden Sie unter [Erstellen von Sprachkopien für Assets](/help/sites-administering/tc-manage.md).

Das Starten und Abschließen eines Workflows ist unabhängig vom gewählten Workflow immer gleich. Nur die Schritte ändern sich.

Sie starten einen Workflow direkt in Projekten (mit Ausnahme von „DAM-Kopie erstellen und übersetzen“ und „DAM-Sprachkopie erstellen“). Informationen zu ausstehenden Aufgaben in einem Projekt finden Sie in der Kachel **Aufgaben**. Benachrichtigungen zu auszuführenden Aufgaben werden neben dem Benutzersymbol angezeigt.

Weitere Informationen zur Arbeit mit Workflows in AEM finden Sie in den folgenden Dokumenten:

* [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md)
* [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md)
* [Konfigurieren von Workflows](/help/sites-administering/workflows.md)

Dieser Abschnitt beschreibt die Workflows, die für Projekte verfügbar sind.

## Workflow „Kopie anfragen“ {#request-copy-workflow}

Mit diesem Workflow können Sie ein Manuskript von einem Benutzer anfragen und es dann genehmigen. So starten Sie den Workflow „Kopie anfragen“:

1. Klicken Sie in einem Medienprojekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Kopie anfragen** und klicken Sie auf **Weiter**.
1. Geben Sie einen Manuskripttitel und eine kurze Zusammenfassung der Anfrage ein. Geben Sie bei Bedarf eine Zielwortanzahl, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Workflow „Kopie anfragen“](assets/project-request-copy-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „Produkt-Fotoshooting“ {#product-photo-shoot-workflow}

Die Workflows **Produkt-Fotoshooting** (mit oder ohne Commerce) werden im Dokument [Kreative Projekte](/help/sites-authoring/managing-product-information.md) im Detail behandelt.

## Workflow für Projektbestätigung {#project-approval-workflow}

Im Workflow für **Projektbestätigung** weisen Sie Inhalte einem Benutzer zu, überprüfen diese und genehmigen sie dann.

1. Klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten** aus.
1. Wählen Sie im Workflow-Assistenten die Option **Workflow für Projektbestätigung** und klicken Sie auf **Weiter**.
1. Geben Sie einen Titel ein und wählen Sie aus, wem Sie ihn zuweisen möchten. Geben Sie bei Bedarf eine Beschreibung, einen Inhaltspfad, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Workflow für Projektbestätigung](assets/project-approval-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „Launch anfragen“ {#request-launch-workflow}

Mit diesem Workflow können Sie einen Launch anfragen.

1. Klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten** aus.
1. Wählen Sie im Workflow-Assistenten die Option **Workflow „Launch anfragen“** und klicken Sie auf **Weiter**.
1. Geben Sie einen Titel für den Launch und den Launch-Quellpfad an. Sie können bei Bedarf auch eine Beschreibung und ein Live-Datum hinzufügen. Wählen Sie „Quellseiten-Live-Daten übernehmen“ oder „Unterseiten ausschließen“, je nachdem, wie sich der Start verhalten soll.

   ![Workflow „Launch anfragen“](assets/project-request-launch-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Der Workflow erscheint in der Liste **Workflows**.

## Workflow „Landingpage anfragen“ {#request-landing-page-workflow}

Mit diesem Workflow können Sie eine Landingpage anfragen.

1. Klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten** aus.
1. Wählen Sie im Workflow-Assistenten die Option **Landingpage anfragen** und klicken Sie auf **Weiter**.
1. Geben Sie einen Titel für Ihre Landingpage und den übergeordneten Pfad ein. Geben Sie gegebenenfalls ein Live-Datum ein oder wählen Sie eine Datei für Ihre Landingpage aus.

   ![Workflow „Landingpage anfragen“](assets/project-request-landing-page-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „E-Mail anfragen“ {#request-email-workflow}

Mit diesem Workflow können Sie eine E-Mail anfragen. Es ist derselbe Workflow wie in der Kachel **E-Mails**.

1. Klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten** aus.
1. Wählen Sie im Workflow-Assistenten die Option **E-Mail anfragen** und klicken Sie auf **Weiter**.
1. Geben Sie einen E-Mail-Titel sowie den Kampagnen- und Vorlagenpfad ein. Darüber hinaus können Sie einen Namen, eine Beschreibung und ein Live-Datum angeben.

   ![Workflow „E-Mail anfragen“](assets/project-request-email-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „Sprachkopie erstellen (und übersetzen)“ für Assets {#create-and-translate-language-copy-workflow-for-assets}

Die Workflows **Sprachkopie erstellen** und **Sprachkopie erstellen und übersetzen** werden im Dokument [Erstellen von Sprachkopien für Assets](/help/assets/translation-projects.md) genauer erläutert.
