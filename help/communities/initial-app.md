---
title: Erste Sandbox-Anwendung
description: Erfahren Sie, wie Sie die Inhaltsvorlage verwenden, die zum Erstellen von Inhaltsseiten verwendet wird, sowie eine Komponente und ein Skript, die zum Rendern von Website-Seiten verwendet werden.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: cbf9ce36-53a2-4f4b-a96f-3b05743f6217
source-git-commit: 62d4a8b3af5031ccc539d78f7d06a8cd1fec7af1
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 14%

---

# Erste Sandbox-Anwendung {#initial-sandbox-application}

In diesem Abschnitt erstellen Sie Folgendes:

* Die **[template](#createthepagetemplate)** wird verwendet, um Inhaltsseiten in der Beispiel-Website zu erstellen.
* Die **[Komponente und Skript](#create-the-template-s-rendering-component)** wird zum Rendern der Website-Seiten verwendet.

## Erstellen der Inhaltsvorlage {#create-the-content-template}

Eine Vorlage definiert den Standardinhalt einer neuen Seite. Komplexe Websites können mehrere Vorlagen verwenden, um die verschiedenen Seitentypen auf der Site zu erstellen. Darüber hinaus kann der Vorlagensatz zu einem Blueprint werden, der verwendet wird, um Änderungen auf einem Servercluster durchzuführen.

In dieser Übung basieren alle Seiten auf einer einfachen Vorlage.

1. Im Explorer-Bereich von CRXDE Lite:

   * Klicken Sie auf `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Erstellen]** > **[!UICONTROL Vorlage erstellen]**

1. Geben Sie im Dialogfeld „Komponente erstellen“ die folgenden Eigenschaftswerte ein und klicken Sie dann auf **[!UICONTROL Weiter]**:

   * Bezeichnung: `playpage`
   * Titel: `An SCF Sandbox Play Template`
   * Beschreibung: `An SCF Sandbox template for play pages`
   * Ressourcentyp: `an-scf-sandbox/components/playpage`
   * Ranking: &lt;leave as=&quot;&quot; default=&quot;&quot;>

   Der Titel wird für den Knotennamen verwendet.

   Der Ressourcentyp wird auf der Seite `playpage`s `jcr:content` Knoten als Eigenschaft `sling:resourceType`. Er identifiziert die Komponente (Ressource), die den Inhalt rendert, wenn sie von einem Browser angefordert wird.

   In diesem Fall werden alle Seiten mit der Variablen `playpage` Vorlage wird von der `an-scf-sandbox/components/playpage` -Komponente. Standardmäßig ist der Pfad zur Komponente relativ, sodass Sling zuerst in der `/apps` und, falls nicht gefunden, im `/libs` Ordner.

   ![create-content-template](assets/create-content-template-1.png)

1. Stellen Sie bei Verwendung von &quot;Kopieren/Einfügen&quot;sicher, dass der Wert &quot;Ressourcentyp&quot;keine führenden oder nachfolgenden Leerzeichen aufweist.

   Klicken Sie auf **[!UICONTROL Weiter]**.

1. &quot;Zulässige Pfade&quot;bezieht sich auf die Pfade von Seiten, die diese Vorlage verwenden, sodass die Vorlage für die **[!UICONTROL Neue Seite]** angezeigt.

   Um einen Pfad hinzuzufügen, klicken Sie auf die Plusschaltfläche `+` und Typ `/content(/.&ast;)?` in das angezeigte Textfeld ein. Stellen Sie bei Verwendung von Kopieren/Einfügen sicher, dass keine führenden oder nachfolgenden Leerzeichen vorhanden sind.

   Hinweis: Der Wert der zulässigen Pfadeigenschaft ist ein *regulärer Ausdruck*. Inhaltsseiten mit einem Pfad, der dem Ausdruck entspricht, können die Vorlage verwenden. In diesem Fall stimmt der reguläre Ausdruck mit dem Pfad der **/content** Ordner und alle zugehörigen Unterseiten.

   Wenn ein Autor eine Seite unten erstellt `/content`, die `playpage` Vorlage mit dem Titel &quot;Eine SCF-Sandbox-Seitenvorlage&quot;wird in einer Liste der zu verwendenden Vorlagen angezeigt.

   Nachdem die Stammseite aus der Vorlage erstellt wurde, kann der Zugriff auf die Vorlage auf diese Website beschränkt werden, indem die Eigenschaft bearbeitet wird, um den Stammpfad in den regulären Ausdruck einzuschließen.

   `/content/an-scf-sandbox(/.&ast;)?`

   ![configure-template-path](assets/configure-template-path.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Klicks **[!UICONTROL Nächste]** im **[!UICONTROL Zugelassene übergeordnete Elemente]** Bedienfeld.

   Klicks **[!UICONTROL Nächste]** im **[!UICONTROL Zugelassene Kinder]** Bedienfeld.

   Klicken Sie auf **[!UICONTROL OK]**.

1. Nachdem Sie auf OK geklickt und die Erstellung der Vorlage abgeschlossen haben, beachten Sie die roten Dreiecke, die in den Ecken der Eigenschaften -Registerkarte für die neue `playpage` Vorlage. Diese roten Dreiecke zeigen Bearbeitungen an, die nicht gespeichert wurden.

   Klicks **[!UICONTROL Alle speichern]** , um die neue Vorlage im Repository zu speichern.

   ![verify-content-template](assets/verify-content-template.png)

### Erstellen der Rendering-Komponente der Vorlage {#create-the-template-s-rendering-component}

Erstellen Sie die *component* definiert den Inhalt und rendert alle Seiten, die basierend auf der [Paketvorlage](#createthepagetemplate).

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf **`/apps/an-scf-sandbox/components`** und klicken Sie auf **[!UICONTROL Erstellen > Komponente]**.
1. Durch Festlegen des Knotennamens (Beschriftung) auf *playpage*, lautet der Pfad zur Komponente

   `/apps/an-scf-sandbox/components/playpage`

   , der dem Ressourcentyp der Paketvorlage entspricht (optional abzüglich der ersten **`/apps/`** Teil des Pfads).

   Geben Sie im Dialogfeld **[!UICONTROL Komponente erstellen]** die folgenden Eigenschaftswerte ein:

   * Titel: **playpage**
   * Titel: **Eine SCF-Sandbox-Abspielkomponente**
   * Beschreibung: **Dies ist die Komponente, die Inhalte für eine SCF-Sandbox-Seite rendert.**
   * Super Type: *&lt;leave blank=&quot;&quot;>*
   * Gruppe: *&lt;leave blank=&quot;&quot;>*

   ![create-template-component](assets/create-template-component.png)

1. Klicks **[!UICONTROL Nächste]** bis zum **[!UICONTROL Zugelassene Kinder]** -Bereich des Dialogfelds angezeigt:

   * Klicken Sie auf **[!UICONTROL OK]**.
   * Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Überprüfen Sie, ob der Pfad zur Komponente und der resourceType für die Vorlage übereinstimmen.

   >[!CAUTION]
   >
   >Die Korrespondenz zwischen dem Pfad zur Paketkomponente und der `sling:resourceType` -Eigenschaft der PayPage-Vorlage ist für die korrekte Funktionsweise der Website von entscheidender Bedeutung.

   ![verify-template-component](assets/verify-template-component.png)
