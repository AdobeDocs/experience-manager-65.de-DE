---
title: Arbeiten mit Projekt-Workflows
seo-title: Working with Project Workflows
description: Eine Vielzahl von Projekt-Workflows ist bereits vorkonfiguriert.
seo-description: A variety of project workflows are available out of the box.
uuid: 376922ca-e09e-4ac8-88c8-23dac2b49dbe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
discoiquuid: 9d2bf30c-5190-4924-82cd-bcdfde24eb39
exl-id: 407fc164-291d-42f6-8c46-c1df9ba3d454
source-git-commit: 200b47070b7ead54ee54eea504bd960d4e0731d9
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 62%

---


# Arbeiten mit Projekt-Workflows {#working-with-project-workflows}

Folgende Projekt-Workflows sind im Lieferumfang enthalten:

* **Workflow für Projektbestätigung** - Dieser Workflow ermöglicht es Ihnen, Inhalte einem Benutzer zuzuweisen, sie zu prüfen und dann zu bestätigen.
* **Launch anfordern** - Ein Workflow, der einen Launch anfordert.
* **Einstiegsseite anfordern** - Dieser Workflow fordert eine Landingpage an.
* **E-Mail anfordern** - Workflow zum Anfordern einer E-Mail.
* **Produkt-Fotoshooting und Produkt-Fotoshooting (Commerce)** - Ordnet Assets Produkten zu
* **DAM-Kopie erstellen und übersetzen und DAM-Sprachkopie erstellen** - Erstellt übersetzte Binärdateien, Metadaten und Tags für Assets und Ordner.

Je nachdem, welche Projektvorlage Sie auswählen, sind bestimmte Workflows verfügbar:

|  | **Einfaches Projekt** | **Medienprojekt** | **Projekt für Produkt-Fotoshooting** | **Übersetzungsprojekt** |
|---|:-:|:-:|:-:|:-:|
| Kopie anfordern |  | x |  |  |
| Produkt-Fotoshooting |  | x | x |  |
| Produkt-Fotoshooting (Commerce) |  |  | x |  |
| Projekt-Genehmigung | x |  |  |  |
| Launch anfordern | x |  |  |  |
| Einstiegsseite anfordern | x |  |  |  |
| E-Mail anfordern | x |  |  |  |
| DAM-Sprachkopie erstellen&amp;ast; |  |  |  | x |
| DAM-Sprachkopie erstellen und übersetzen&amp;ast; |  |  |  | x |

>[!NOTE]
>
>&amp;ast; Diese Workflows werden nicht auf der Kachel **Workflow** in Projekten gestartet. Weitere Informationen finden Sie unter [Erstellen von Sprachkopien für Assets](/help/sites-administering/tc-manage.md).

Das Starten und Abschließen eines Workflows ist unabhängig vom gewählten Workflow immer gleich. Nur die Schritte dazwischen ändern sich.

Sie starten einen Workflow direkt in Projekten (mit Ausnahme von „DAM-Sprachkopie erstellen“ bzw. „DAM-Sprachkopie erstellen und übersetzen“). Informationen über alle ausstehenden Aufgaben in einem Projekt werden in der Kachel **Aufgaben** aufgeführt. Benachrichtigungen für Aufgaben, die ausgeführt werden müssen, werden neben dem Benutzersymbol angezeigt.

Weitere Informationen zum Arbeiten mit Workflows in AEM finden Sie in den folgenden Dokumenten:

* [Teilnehmen an Workflows](/help/sites-authoring/workflows-participating.md)
* [Anwenden von Workflows auf Seiten](/help/sites-authoring/workflows-applying.md)
* [Konfigurieren von Workflows](/help/sites-administering/workflows.md)

Dieser Abschnitt beschreibt die Workflows, die für Projekte verfügbar sind.

## Workflow &quot;Kopie anfordern&quot; {#request-copy-workflow}

Mit diesem Workflow können Sie ein Manuskript von einem Benutzer anfordern und es dann genehmigen. So starten Sie den Workflow „Kopie anfordern“:

1. Tippen oder klicken Sie in einem Medienprojekt oben rechts im **Workflows** Kachel und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Kopie anfordern** und klicken Sie auf **Nächste**.
1. Geben Sie einen Manuskripttitel und eine kurze Zusammenfassung dazu ein, was Sie anfordern. Geben Sie bei Bedarf eine Zielwortanzahl, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Workflow „Kopie anfordern“](assets/project-request-copy-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe wird auf der **Aufgaben** Karte.

## Workflow „Produkt-Fotoshooting“ {#product-photo-shoot-workflow}

Die **Produkt-Fotoshooting** Workflows (sowohl Commerce als auch ohne Commerce) werden im Dokument ausführlich behandelt [Kreative Projekte](/help/sites-authoring/managing-product-information.md)

## Workflow für Projektbestätigung {#project-approval-workflow}

Im **Projektvalidierung** -Arbeitsablauf, können Sie einem Benutzer Inhalte zuweisen, diese überprüfen und dann genehmigen.

1. Tippen oder klicken Sie in einem einfachen Projekt oben rechts im **Workflows** Kachel und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Workflow für Projektbestätigung** und klicken Sie auf **Nächste**.
1. Geben Sie einen Titel ein und wählen Sie aus, wem Sie ihn zuweisen möchten. Geben Sie bei Bedarf eine Beschreibung, einen Inhaltspfad, eine Aufgabenpriorität und ein Fälligkeitsdatum ein.

   ![Workflow für Projektgenehmigung](assets/project-approval-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe wird auf der **Aufgaben** Karte.

## Workflow &quot;Launch anfordern&quot; {#request-launch-workflow}

Mit diesem Workflow können Sie einen Launch anfordern.

1. Tippen oder klicken Sie in einem einfachen Projekt oben rechts im **Workflows** Kachel und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Workflow &quot;Launch anfordern&quot;** und klicken Sie auf **Nächste**.
1. Geben Sie einen Titel für den Launch ein und geben Sie den Launch-Quellpfad an. Sie können bei Bedarf auch eine Beschreibung und ein Live-Datum hinzufügen. Wählen Sie „Quellseiten-Live-Daten erben“ oder „Unterseiten ausschließen“ aus, je nachdem, wie der Launch sich verhalten soll.

   ![Workflow zum Anfordern eines Launches](assets/project-request-launch-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Der Workflow wird im **Workflows** Liste.

## Workflow &quot;Einstiegsseite anfordern&quot; {#request-landing-page-workflow}

Mit diesem Workflow können Sie eine Einstiegsseite anfordern.

1. Tippen oder klicken Sie in einem einfachen Projekt oben rechts im **Workflows** Kachel und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Einstiegsseite anfordern** und klicken Sie auf **Nächste**.
1. Geben Sie einen Titel für Ihre Einstiegsseite und den übergeordneten Pfad ein. Geben Sie bei Bedarf ein Live-Datum ein oder wählen Sie eine Datei für Ihre Einstiegsseite aus.

   ![Workflow &quot;Landingpage anfordern&quot;](assets/project-request-landing-page-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe wird auf der **Aufgaben** Karte.

## Workflow „E-Mail anfordern“ {#request-email-workflow}

Mit diesem Workflow können Sie eine E-Mail anfordern. Es ist der derselbe Workflow, der in der Kachel **E-Mails** angezeigt wird.

1. Tippen oder klicken Sie in einem einfachen Projekt oben rechts im **Workflows** Kachel und wählen Sie **Workflow starten**.
1. Wählen Sie im Workflow-Assistenten die Option **Email anfordern** und klicken Sie auf **Nächste**.
1. Geben Sie einen E-Mail-Titel sowie den Kampagnen- und den Vorlagenpfad ein. Darüber hinaus können Sie einen Namen, eine Beschreibung und ein Live-Datum angeben.

   ![E-Mail-Workflow anfordern](assets/project-request-email-workflow.png)

1. Klicken Sie auf **Senden**.

Der Workflow startet. Die Aufgabe wird auf der **Aufgaben** Karte.

## Workflow „Sprachkopie erstellen (und übersetzen)“ für Assets {#create-and-translate-language-copy-workflow-for-assets}

Die **Sprachkopie erstellen** und **Sprachkopie erstellen und übersetzen** Workflows werden im Dokument ausführlich beschrieben. [Erstellen von Sprachkopien für Assets.](/help/assets/translation-projects.md)
