---
title: Ursprüngliche Sandbox-Anwendung
description: Erfahren Sie, wie Sie die Inhaltsvorlage verwenden, die zum Erstellen von Inhaltsseiten verwendet wird, sowie eine Komponente und ein Skript, die bzw. das zum Rendern von Website-Seiten verwendet wird.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: cbf9ce36-53a2-4f4b-a96f-3b05743f6217
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 13%

---

# Ursprüngliche Sandbox-Anwendung {#initial-sandbox-application}

In diesem Abschnitt erstellen Sie Folgendes:

* Die **[Vorlage](#createthepagetemplate)** die zum Erstellen von Inhaltsseiten in der Beispiel-Website verwendet wird.
* Die **[Komponente und](#create-the-template-s-rendering-component)**), die zum Rendern der Website-Seiten verwendet werden.

## Erstellen der Inhaltsvorlage {#create-the-content-template}

Eine Vorlage definiert den Standardinhalt einer neuen Seite. Komplexe Websites können mehrere Vorlagen verwenden, um die verschiedenen Seitentypen auf der Site zu erstellen. Darüber hinaus kann der Satz von Vorlagen zu einem Blueprint werden, der zum Rollout von Änderungen an einem Cluster von Servern verwendet wird.

In dieser Übung basieren alle Seiten auf einer einfachen Vorlage.

1. Im Explorer-Fenster von CRXDE Lite:

   * Klicken Sie auf `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Erstellen]** > **[!UICONTROL Vorlage erstellen]**

1. Geben Sie im Dialogfeld „Komponente erstellen“ die folgenden Eigenschaftswerte ein und klicken Sie dann auf **[!UICONTROL Weiter]**:

   * Bezeichnung: `playpage`
   * Titel: `An SCF Sandbox Play Template`
   * Beschreibung: `An SCF Sandbox template for play pages`
   * Ressourcentyp: `an-scf-sandbox/components/playpage`
   * Rangfolge: &lt;Als Standard beibehalten>

   Die Bezeichnung wird für den Knotennamen verwendet.

   Der Ressourcentyp wird auf dem `jcr:content` des `playpage` als `sling:resourceType` angezeigt. Er identifiziert die Komponente (Ressource), die den Inhalt rendert, wenn sie von einem Browser angefordert wird.

   In diesem Fall werden alle Seiten, die mithilfe der `playpage` erstellt wurden, von der `an-scf-sandbox/components/playpage` gerendert. Standardmäßig ist der Pfad zur Komponente relativ, sodass Sling zuerst im `/apps` Ordner und, falls nicht vorhanden, im `/libs` nach der Ressource suchen kann.

   ![create-content-template](assets/create-content-template-1.png)

1. Stellen Sie bei Verwendung von Kopieren/Einfügen sicher, dass der Wert „Ressourcentyp“ keine führenden oder nachfolgenden Leerzeichen enthält.

   Klicken Sie auf **[!UICONTROL Weiter]**.

1. „Zulässige Pfade“ beziehen sich auf die Pfade von Seiten, die diese Vorlage verwenden, sodass die Vorlage für das Dialogfeld &quot;**[!UICONTROL Seite“]** wird.

   Um einen Pfad hinzuzufügen, klicken Sie auf die Schaltfläche mit dem Pluszeichen `+` geben Sie in das daraufhin angezeigte Textfeld `/content(/.&ast;)?` ein. Wenn Sie Kopieren/Einfügen verwenden, stellen Sie sicher, dass keine führenden oder nachfolgenden Leerzeichen vorhanden sind.

   Hinweis: Der Wert der Eigenschaft „Zugelassene Pfade“ ist ein *regulärer Ausdruck*. Inhaltsseiten mit einem Pfad, der dem Ausdruck entspricht, können die Vorlage verwenden. In diesem Fall entspricht der reguläre Ausdruck dem Pfad des Ordners **/content** und allen zugehörigen Unterseiten.

   Wenn ein Autor eine Seite unter `/content` erstellt, wird die `playpage` „Eine SCF-Sandbox-Seitenvorlage“ in einer Liste der verfügbaren Vorlagen angezeigt.

   Nachdem die Stammseite aus der Vorlage erstellt wurde, kann der Zugriff auf die Vorlage auf diese Website eingeschränkt werden, indem die Eigenschaft so bearbeitet wird, dass der Stammpfad in den regulären Ausdruck aufgenommen wird.

   `/content/an-scf-sandbox(/.&ast;)?`

   ![configure-template-path](assets/configure-template-path.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Klicken Sie **&#x200B;**&#x200B;Bedienfeld **[!UICONTROL Zugelassene übergeordnete Elemente]** auf „Weiter“.

   Klicken Sie **&#x200B;**&#x200B;Bedienfeld **[!UICONTROL Zugelassene untergeordnete Elemente]** auf „Weiter“.

   Klicken Sie auf **[!UICONTROL OK]**.

1. Nachdem Sie auf OK geklickt und die Erstellung der Vorlage abgeschlossen haben, sehen Sie die roten Dreiecke, die in den Ecken der Registerkarte Eigenschaften für die neue `playpage` angezeigt werden. Diese roten Dreiecke zeigen Bearbeitungen an, die nicht gespeichert wurden.

   Klicken Sie **[!UICONTROL Alle speichern]**, um die neue Vorlage im Repository zu speichern.

   ![verify-content-template](assets/verify-content-template.png)

### Erstellen der Rendering-Komponente der Vorlage {#create-the-template-s-rendering-component}

Erstellen Sie die *Komponente* die den Inhalt definiert und alle Seiten rendert, die basierend auf der ([)](#createthepagetemplate) erstellt wurden.

1. Klicken Sie im CRXDE Lite mit der rechten Maustaste auf **`/apps/an-scf-sandbox/components`** und klicken Sie auf **[!UICONTROL Erstellen > Komponente]**.
1. Wenn Sie den Namen (Titel) des Knotens auf &quot;*&quot;*, lautet der Pfad zur Komponente wie folgt

   `/apps/an-scf-sandbox/components/playpage`

   der dem Ressourcentyp der Wiedergabevorlagen entspricht (optional abzüglich des ersten **`/apps/`** Teils des Pfads).

   Geben Sie im Dialogfeld **[!UICONTROL Komponente erstellen]** die folgenden Eigenschaftswerte ein:

   * Titel: **playPage**
   * Titel: **Eine SCF-Sandbox-Wiedergabekomponente**
   * Beschreibung: **Dies ist die Komponente, die den Inhalt für eine SCF-Sandbox-Seite rendert.**
   * Supertyp: *&lt;leer lassen>*
   * Gruppe: *&lt;leer lassen>*

   ![create-template-component](assets/create-template-component.png)

1. Klicken Sie **[!UICONTROL Weiter]** bis das Bedienfeld **[!UICONTROL Zugelassene untergeordnete Elemente]** des Dialogfelds angezeigt wird:

   * Klicken Sie auf **[!UICONTROL OK]**.
   * Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Stellen Sie sicher, dass der Pfad zur Komponente und der resourceType für die Vorlage übereinstimmen.

   >[!CAUTION]
   >
   >Die Korrespondenz zwischen dem Pfad zur Wiedergabekomponente und der `sling:resourceType` Eigenschaft der Wiedergabeseitenvorlage ist für das ordnungsgemäße Funktionieren der Website von entscheidender Bedeutung.

   ![verify-template-component](assets/verify-template-component.png)
