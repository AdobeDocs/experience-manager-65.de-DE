---
title: Arbeiten mit Projekt-Workflows
seo-title: Working with Project Workflows
description: Standardmäßig sind diverse Projekt-Workflows verfügbar.
seo-description: A variety of project workflows are available out of the box.
uuid: 376922ca-e09e-4ac8-88c8-23dac2b49dbe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
discoiquuid: 9d2bf30c-5190-4924-82cd-bcdfde24eb39
exl-id: 407fc164-291d-42f6-8c46-c1df9ba3d454
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 73%

---


# Arbeiten mit Projekt-Workflows {#working-with-project-workflows}

Folgende Projekt-Workflows sind im Lieferumfang enthalten:

* **Workflow für Projektbestätigung** - Mit diesem Workflow können Sie einem Benutzer Inhalte zuweisen, diese überprüfen und dann genehmigen.
* **Launch anfragen** - Ein Workflow, der einen Launch anfordert.
* **Einstiegsseite anfragen** - Dieser Workflow fragt eine Landingpage an.
* **E-Mail anfragen** - Workflow zum Anfragen einer E-Mail.
* **Produkt-Fotoshooting und Produkt-Fotoshooting (Commerce)** - Ordnet Assets Produkten zu
* **DAM-Kopie erstellen und übersetzen und DAM-Sprachkopie erstellen** - Erstellt übersetzte Binärdateien, Metadaten und Tags für Assets und Ordner.

Je nachdem, welche Projektvorlage Sie auswählen, stehen Ihnen bestimmte Workflows zur Verfügung:

|   | **Einfaches Projekt** | **Medienprojekt** | **Projekt für Produkt-Fotoshooting** | **Übersetzungsprojekt** |
|---|:-:|:-:|:-:|:-:|
| Kopie anfragen |  | x |  |  |
| Produkt-Fotoshooting |  | x | x |  |
| Produkt-Fotoshooting   (Commerce) |  |  | x |  |
| Projektvalidierung | x |  |  |  |
| Launch anfragen | x |  |  |  |
| Einstiegsseite anfragen | x |  |  |  |
| E-Mail anfragen | x |  |  |  |
| DAM-Sprachkopie erstellen&amp;ast; |  |  |  | x |
| DAM-Sprachkopie erstellen und übersetzen&amp;ast; |  |  |  | x |

>[!NOTE]
>
>&amp;ast; Diese Workflows werden nicht auf der Kachel **Workflow** in Projekten gestartet. Weitere Informationen finden Sie unter [Erstellen von Sprachkopien für Assets](/help/sites-administering/tc-manage.md).

Das Starten und Abschließen eines Workflows ist unabhängig vom gewählten Workflow immer gleich. Nur die Schritte ändern sich.

Sie starten einen Workflow direkt in Projekten (mit Ausnahme von DAM Create Language Copy oder DAM Create and Translate Language Copy). Informationen zu ausstehenden Aufgaben in einem Projekt finden Sie in der **Aufgaben** Kachel. Benachrichtigungen zu auszuführenden Aufgaben werden neben dem Benutzersymbol angezeigt.

Weitere Informationen zur Arbeit mit Workflows in AEM finden Sie in den folgenden Dokumenten:

* [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md)
* [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md)
* [Konfigurieren von Workflows](/help/sites-administering/workflows.md)

Dieser Abschnitt beschreibt die Workflows, die für Projekte verfügbar sind.

## Workflow „Kopie anfragen“ {#request-copy-workflow}

Mit diesem Workflow können Sie ein Manuskript von einem Benutzer anfragen und es dann genehmigen. So starten Sie den Workflow „Kopie anfragen“:

1. Tippen oder klicken Sie in einem Medienprojekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Kopie anfragen** und klicken Sie auf **Weiter**.
1. Geben Sie einen Manuskripttitel und eine kurze Zusammenfassung dazu ein, was Sie anfragen. Geben Sie gegebenenfalls eine Zielwortanzahl, Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Workflow „Kopie anfragen“](assets/project-request-copy-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „Produkt-Fotoshooting“ {#product-photo-shoot-workflow}

Die Workflows **Produkt-Fotoshooting** (mit oder ohne Commerce) werden im Dokument [Kreative Projekte](/help/sites-authoring/managing-product-information.md) im Detail behandelt.

## Workflow für Projektbestätigung {#project-approval-workflow}

Im Workflow für **Projektbestätigung** weisen Sie Inhalte einem Benutzer zu, überprüfen diese und genehmigen sie dann.

1. Tippen oder klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Workflow für Projektbestätigung** und klicken Sie auf **Weiter**.
1. Geben Sie einen Titel ein und wählen Sie aus, wem Sie ihn zuweisen möchten. Geben Sie bei Bedarf eine Beschreibung, einen Inhaltspfad, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Workflow für Projektbestätigung](assets/project-approval-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „Launch anfragen“ {#request-launch-workflow}

Mit diesem Workflow können Sie einen Launch anfragen.

1. Tippen oder klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Workflow „Launch anfragen“** und klicken Sie auf **Weiter**.
1. Geben Sie einen Titel für den Launch ein und geben Sie den Launch-Quellpfad an. Sie können bei Bedarf auch eine Beschreibung und ein Live-Datum hinzufügen. Wählen Sie &quot;Quellseiten-Live-Daten übernehmen&quot;oder &quot;Unterseiten ausschließen&quot;, je nachdem, wie sich der Launch verhalten soll.

   ![Workflow „Launch anfragen“](assets/project-request-launch-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Der Workflow erscheint in der Liste **Workflows**.

## Workflow „Landingpage anfragen“ {#request-landing-page-workflow}

Mit diesem Workflow können Sie eine Landingpage anfragen.

1. Tippen oder klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Landingpage anfragen** und klicken Sie auf **Weiter**.
1. Geben Sie einen Titel für Ihre Landingpage und den übergeordneten Pfad ein. Geben Sie gegebenenfalls ein Live-Datum ein oder wählen Sie eine Datei für Ihre Landingpage aus.

   ![Workflow „Landingpage anfragen“](assets/project-request-landing-page-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „E-Mail anfragen“ {#request-email-workflow}

Mit diesem Workflow können Sie eine E-Mail anfragen. Es handelt sich um denselben Workflow, der im **E-Mails** Kachel.

1. Tippen oder klicken Sie in einem einfachen Projekt auf den abwärts gerichteten Pfeil oben rechts in der Kachel **Workflows** und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **E-Mail anfragen** und klicken Sie auf **Weiter**.
1. Geben Sie einen E-Mail-Titel sowie den Kampagnen- und Vorlagenpfad ein. Darüber hinaus können Sie einen Namen, eine Beschreibung und ein Live-Datum angeben.

   ![Workflow „E-Mail anfragen“](assets/project-request-email-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe erscheint auf der Karte **Aufgaben**.

## Workflow „Sprachkopie erstellen (und übersetzen)“ für Assets {#create-and-translate-language-copy-workflow-for-assets}

Die Workflows **Sprachkopie erstellen** und **Sprachkopie erstellen und übersetzen** werden im Dokument [Erstellen von Sprachkopien für Assets](/help/assets/translation-projects.md) genauer erläutert.
