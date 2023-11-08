---
title: Anpassen der Konsolen
seo-title: Customizing the Consoles
description: AEM bietet verschiedene Mechanismen, mit denen Sie die Konsolen Ihrer Authoring-Instanz anpassen können
seo-description: AEM provides various mechanisms to enable you to customize the consoles of your authoring instance
uuid: 8ecce9ff-5907-41e1-af3b-a8646352d633
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 61a4e196-bd53-4ef0-816b-c14401462457
docset: aem65
exl-id: 6e67f2b3-78b9-45f2-b496-61776b9fd9cc
source-git-commit: 38f0496d9340fbcf383a2d39dba8efcbdcd20c6f
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 45%

---

# Anpassen der Konsolen {#customizing-the-consoles}

>[!CAUTION]
>
>In diesem Dokument wird beschrieben, wie Sie Konsolen in der modernen, Touch-optimierten Benutzeroberfläche anpassen. Es gilt nicht für die klassische Benutzeroberfläche.

AEM bietet verschiedene Mechanismen, mit denen Sie die Konsolen (und die [Seitenbearbeitungsfunktionen](/help/sites-developing/customizing-page-authoring-touch.md)) Ihrer Authoring-Instanz.

* Mit Clientlibs Clientlibs können Sie die Standardimplementierung erweitern, um neue Funktionen zu realisieren und gleichzeitig die Standardfunktionen, -objekte und -methoden wiederzuverwenden. Bei der Anpassung können Sie Ihre eigene clientlib unter erstellen. `/apps.` Beispielsweise kann er den Code enthalten, der für Ihre benutzerdefinierte Komponente erforderlich ist.

* Überlagerungen Überlagerungen basieren auf Knotendefinitionen und ermöglichen das Überlagern der Standardfunktionen (in `/libs`) mit Ihrer eigenen benutzerdefinierten Funktionalität (in `/apps`). Wenn Sie eine Überlagerung erstellen, ist keine 1:1-Kopie des Originals erforderlich, da die Sling-Ressourcenzusammenführung das Vererben zulässt.

Diese können auf viele Arten verwendet werden, um Ihre AEM Konsolen zu erweitern. Einige davon sind nachstehend (allgemein) beschrieben.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* Verwenden und Erstellen [clientlibs](/help/sites-developing/clientlibs.md).
>* Verwenden und Erstellen [Overlays](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
>


>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
>
>Die empfohlene Methode für Konfigurations- und sonstige Änderungen sieht wie folgt aus:
>
>1. Erstellen Sie das erforderliche Element (d. h., wie es in `/libs`) unter `/apps`
>
>1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.
>

Beispielsweise können die folgenden Speicherorte innerhalb der `/libs`-Struktur überlagert werden:

* Konsolen (alle Konsolen basierend auf Seiten der Granite-Benutzeroberfläche); zum Beispiel:

   * `/libs/wcm/core/content`

>[!NOTE]
>
>Weitere Tipps und Informationen zu Tools finden Sie im Knowledge-Base-Artikel [Beheben von Fehlern in der Touch-optimierten AEM-Benutzeroberfläche](https://helpx.adobe.com/de/experience-manager/kb/troubleshooting-aem-touchui-issues.html).

## Anpassen der Standardansicht für eine Konsole {#customizing-the-default-view-for-a-console}

Sie können die Standardansicht (Spalte, Karte, Liste) für eine Konsole anpassen:

1. Sie können die Ansichten neu anordnen, indem Sie den erforderlichen Eintrag unter überschreiben:

   `/libs/wcm/core/content/sites/jcr:content/views`

   Der erste Eintrag ist die Standardeinstellung.

   Die verfügbaren Knoten korrelieren mit den verfügbaren Anzeigeoptionen:

   * `column`
   * `card`
   * `list`

1. Beispiel: In einer Überlagerung für die Liste:

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   Definieren Sie folgende Eigenschaften:

   * **Name**: `sling:orderBefore`
   * **Typ**: `String`
   * **Wert**: `column`

### Hinzufügen neuer Aktionen zur Symbolleiste {#add-new-action-to-the-toolbar}

1. Sie können eigene Komponenten erstellen und die entsprechenden Client-Bibliotheken für benutzerdefinierte Aktionen einschließen. Beispiel: eine **Weiterleiten an Twitter** Aktion unter:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   Diese kann mit einem Symbolleistenelement in Ihrer Konsole verbunden sein:

   `/apps/<yourProject>/admin/ext/launches`

   Beispielsweise im Auswahlmodus:

   `content/jcr:content/body/content/header/items/selection/items/twitter`

### Beschränken einer Symbolleistenaktion auf eine bestimmte Gruppe {#restrict-a-toolbar-action-to-a-specific-group}

1. Sie können eine benutzerdefinierte Rendering-Bedingung verwenden, um die Standardaktion zu überlagern und bestimmte Bedingungen vorzuschreiben, die erfüllt sein müssen, bevor sie gerendert wird.

   Erstellen Sie beispielsweise eine Komponente, um die Renderbedingungen entsprechend der Gruppe zu steuern:

   `/apps/myapp/components/renderconditions/group`

1. Um diese auf die Aktion „Site erstellen“ in der Site-Konsole anzuwenden:

   `/libs/wcm/core/content/sites`

   Erstellen Sie die Überlagerung:

   `/apps/wcm/core/content/sites`

1. Fügen Sie dann die Render-Bedingung für die Aktion hinzu:

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   Mithilfe von Eigenschaften auf diesem Knoten können Sie die `groups` definieren, die die spezifische Aktion ausführen dürfen, beispielsweise `administrators`.

### Anpassen von Spalten in der Listenansicht {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Diese Funktion ist für Spalten mit Textfeldern optimiert. Für andere Datentypen können Sie `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps` überlagern.

So passen Sie die Spalten in der Listenansicht an:

1. Liste der verfügbaren Spalten überlagern

   * Auf dem Knoten:

     ```
            /apps/wcm/core/content/common/availablecolumns
     ```

   * Fügen Sie die neuen Spalten hinzu oder entfernen Sie vorhandene.

   Weitere Informationen finden Sie unter [Verwenden von Überlagerungen (und der Sling-Ressourcenzusammenführung)](/help/sites-developing/overlays.md).

1. Optional:

   * Falls Sie zusätzliche Daten hinzufügen möchten, müssen Sie einen [PageInforProvider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) mit einer
     `pageInfoProviderType`-Eigenschaft schreiben.

   Siehe beispielsweise die angehängte Klasse/das angehängte Bundle (von GitHub) unten.

1. Jetzt können Sie die Spalte im Spaltenkonfigurator der Listenansicht auswählen.

### Ressourcen filtern {#filtering-resources}

Bei Verwendung einer Konsole ist es häufig der Fall, dass der Benutzer aus Ressourcen auswählen muss (z. B. Seiten, Komponenten, Assets usw.). Dies kann beispielsweise in Form einer Liste erfolgen, aus der der Autor ein Element auswählen muss.

Um die Liste in einer angemessenen Größe und auch für den Anwendungsfall relevant zu halten, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Siehe [diesem Artikel](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources) für Details.
