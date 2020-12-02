---
title: Anfänglicher Sandbox-Antrag
seo-title: Anfänglicher Sandbox-Antrag
description: Erstellen von Vorlagen, Komponenten und Skripten
seo-description: Erstellen von Vorlagen, Komponenten und Skripten
uuid: b0d03376-d8bc-4e98-aea2-a01744c64ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f74d225e-0245-4d5a-bb93-0ee3f31557aa
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 12%

---


# Initial Sandbox Application {#initial-sandbox-application}

In diesem Abschnitt erstellen Sie Folgendes:

* Die **[template](#createthepagetemplate)**, die zum Erstellen von Inhaltsseiten in der Beispiel-Website verwendet wird.
* Die **[Komponente und das Skript](#create-the-template-s-rendering-component)**, die zum Rendern der Webseiten verwendet werden.

## Erstellen der Inhaltsvorlage {#create-the-content-template}

Eine Vorlage definiert den Standardinhalt einer neuen Seite. Bei komplexen Websites werden ggf. auch mehrere Vorlagen für die Erstellung der verschiedenen Seitentypen der Website verwendet. Darüber hinaus kann der Vorlagensatz zu einem Entwurf werden, mit dem Änderungen in einem Servercluster eingeführt werden.

Bei dieser Übung basieren jedoch alle Seiten auf einer einfachen Vorlage.

1. Im Explorer-Bereich &quot;CRXDE Lite&quot;:

   * Wählen Sie nun eine der folgenden Optionen aus `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Erstellen]** > Vorlage  **[!UICONTROL erstellen]**

1. Geben Sie im Dialogfeld „Vorlage erstellen“ die folgenden Werte ein und klicken Sie anschließend auf **[!UICONTROL Weiter]**:

   * Bezeichnung: `playpage`
   * Titel: `An SCF Sandbox Play Template`
   * Beschreibung: `An SCF Sandbox template for play pages`
   * Ressourcentyp: `an-scf-sandbox/components/playpage`
   * Rangansicht: &lt;Als Standard beibehalten>

   Die Beschriftung wird für den Knotennamen verwendet.

   Der Ressourcentyp wird auf dem Knoten &quot;jcr:content&quot;von `playpage` als Eigenschaft `sling:resourceType` angezeigt. Er identifiziert die Komponente (Ressource), die den Inhalt auf Anforderung eines Browsers rendert.

   In diesem Fall werden alle mit der Vorlage `playpage` erstellten Seiten von der Komponente `an-scf-sandbox/components/playpage` gerendert. Standardmäßig ist der Pfad zur Komponente relativ, sodass Sling zuerst im Ordner `/apps` und, falls nicht gefunden, im Ordner `/libs` nach der Ressource suchen kann.

   ![create-content-template](assets/create-content-template-1.png)

1. Stellen Sie bei Verwendung von &quot;Kopieren/Einfügen&quot;sicher, dass der Wert &quot;Ressourcentyp&quot;keine Leerzeichen am Anfang oder Ende enthält.

   Klicken Sie auf **[!UICONTROL Weiter]**.

1. &quot;Zulässige Pfade&quot;bezieht sich auf die Pfade von Seiten, die diese Vorlage verwenden, sodass die Vorlage für das Dialogfeld **[!UICONTROL Neue Seite]** aufgelistet wird.

   Um einen Pfad hinzuzufügen, klicken Sie auf die Plusschaltfläche `+` und geben Sie `/content(/.&ast;)?` in das angezeigte Textfeld ein. Wenn Sie Kopieren/Einfügen verwenden, stellen Sie sicher, dass keine Leerzeichen am Anfang oder am Ende vorhanden sind.

   Hinweis: Der Wert der Eigenschaft allowed path ist ein *regulärer Ausdruck*. Inhaltsseiten mit einem Pfad, der dem Ausdruck entspricht, können die Vorlage verwenden. In diesem Fall stimmt der reguläre Ausdruck mit dem Pfad des Ordners **/content** und allen zugehörigen Unterseiten überein.

   Wenn ein Autor eine Seite unterhalb von `/content` erstellt, wird die Vorlage `playpage` mit dem Titel &quot;Eine SCF-Sandbox-Seitenvorlage&quot;in einer Liste der zu verwendenden Vorlagen angezeigt.

   Nachdem die Stammseite aus der Vorlage erstellt wurde, kann der Zugriff auf die Vorlage auf diese Website eingeschränkt werden, indem die Eigenschaft geändert wird, um den Stammpfad in den regulären Ausdruck einzuschließen, d. h.

   `/content/an-scf-sandbox(/.&ast;)?`

   ![configure-template-path](assets/configure-template-path.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**.

   Klicken Sie im Bereich **[!UICONTROL Zulässige Eltern]** auf **[!UICONTROL Weiter]**.

   Klicken Sie auf **[!UICONTROL Weiter]** in den Feldern **[!UICONTROL Zulässige Kinder]**.

   Klicken Sie auf **[!UICONTROL OK]**.

1. Nachdem Sie auf OK geklickt haben und die Vorlage erstellt haben, werden rote Dreiecke angezeigt, die in den Ecken der Registerkarte Eigenschaften für die neue Vorlage `playpage` erscheinen. Diese roten Dreiecke zeigen Bearbeitungen an, die noch nicht gespeichert wurden.

   Klicken Sie auf **[!UICONTROL Alle speichern]**, um die neue Vorlage im Repository zu speichern.

   ![verify-content-template](assets/verify-content-template.png)

### Erstellen der Rendering-Komponente der Vorlage {#create-the-template-s-rendering-component}

Erstellen Sie die *Komponente*, die den Inhalt definiert und alle Seiten rendert, die auf der [PLATZIERUNGSVorlage](#createthepagetemplate) erstellt wurden.

1. Klicken Sie in CRXDE Lite mit der rechten Maustaste auf **`/apps/an-scf-sandbox/components`** und dann auf **[!UICONTROL Erstellen > Komponente]**.
1. Durch Festlegen des Knotennamens (Beschriftung) auf *playpage* lautet der Pfad zur Komponente

   `/apps/an-scf-sandbox/components/playpage`

   was dem Ressourcentyp der PayPal-Vorlage entspricht (optional minus dem initialen **`/apps/`**-Teil des Pfades).

   Geben Sie im Dialogfeld **[!UICONTROL Komponente erstellen]** die folgenden Eigenschaftswerte ein:

   * Beschriftung: **playpage**
   * Titel: **Eine SCF-Sandbox-Abspielkomponente**
   * Beschreibung: **Dies ist die Komponente, die Inhalt für eine SCF-Sandbox-Seite rendert.**
   * Super Type: *&lt;leer lassen>*
   * Gruppe: *&lt;leer lassen>*

   ![create-template-component](assets/create-template-component.png)

1. Klicken Sie auf **[!UICONTROL Weiter]**, bis das Fenster **[!UICONTROL Zulässige Kinder]** des Dialogfelds angezeigt wird:

   * Klicken Sie auf **[!UICONTROL OK]**.
   * Klicken Sie auf **[!UICONTROL Alle speichern]**.

1. Überprüfen Sie, ob der Pfad zur Komponente und der resourceType der Vorlage übereinstimmen.

   >[!CAUTION]
   >
   >Die Korrespondenz zwischen dem Pfad zur PayPal-Komponente und der sling:resourceType-Eigenschaft der PayPal-Vorlage ist für das ordnungsgemäße Funktionieren der Website von entscheidender Bedeutung.

   ![verify-template-component](assets/verify-template-component.png)