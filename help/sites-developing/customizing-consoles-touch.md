---
title: Anpassen der Konsolen
seo-title: Anpassen der Konsolen
description: AEM bietet verschiedene Methoden zum Anpassen der Konsolen Ihrer Autoreninstanz.
seo-description: AEM bietet verschiedene Methoden zum Anpassen der Konsolen Ihrer Autoreninstanz.
uuid: 8ecce9ff-5907-41e1-af3b-a8646352d633
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 61a4e196-bd53-4ef0-816b-c14401462457
docset: aem65
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# Anpassen der Konsolen {#customizing-the-consoles}

>[!CAUTION]
>
>In diesem Dokument wird beschrieben, wie Sie Konsolen in der modernen, Touch-optimierten Benutzeroberfläche anpassen. Die Hinweise gelten nicht für die klassische Benutzeroberfläche.

AEM bietet verschiedene Methoden zum Anpassen von Konsolen (und der [Seitenbearbeitungsfunktionen](/help/sites-developing/customizing-page-authoring-touch.md)) Ihrer Autoreninstanz.

* Clientbibliotheken Mit Clientbibliotheken können Sie die Standardimplementierung um neue Funktionen erweitern und gleichzeitig Standardfunktionen, -objekte und -methoden weiterhin verwenden. Beim Anpassen können Sie Ihre eigene clientlib erstellen, `/apps.` z. B. unter dem Code, der für Ihre benutzerdefinierte Komponente erforderlich ist.

* Overlays
Overlays are based on node definitions and allow you to overlay the standard functionality (in `/libs`) with your own customized functionality (in `/apps`). Wenn Sie eine Überlagerung erstellen, ist keine 1:1-Kopie des Originals erforderlich, da die Sling-Ressourcenzusammenführung das Vererben zulässt.

Überlagerungen können vielseitig zum Erweitern von AEM-Konsolen verwendet werden. Einige davon sind nachstehend (allgemein) beschrieben.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* Verwenden und Erstellen von [Clientbibliotheken](/help/sites-developing/clientlibs.md).
>* Verwenden und Erstellen von [Überlagerungen](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)
>
>
Dieses Thema wird auch in der [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html)-Sitzung [Anpassung der Benutzeroberfläche für AEM 6.0](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html) behandelt.

>[!CAUTION]
>
>You ***must*** not change anything in the `/libs` path.
>
>This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may well be overwritten when you apply either a hotfix or feature pack).
>
>Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
>
>1. Recreate the required item (i.e. as it exists in `/libs`) under `/apps`
   >
   >
1. Make any changes within `/apps`
>



For example, the following location within the `/libs` structure can be overlaid:

* Konsolen (alle Konsolen basierend auf Seiten der Granite-Benutzeroberfläche); zum Beispiel:

   * `/libs/wcm/core/content`

>[!NOTE]
>
>Weitere Tipps und Informationen zu Tools finden Sie im Knowledge-Base-Artikel [Beheben von Fehlern in der Touch-optimierten AEM-Benutzeroberfläche](https://helpx.adobe.com/experience-manager/kb/troubleshooting-aem-touchui-issues.html).

## Anpassen der Standardansicht für eine Konsole {#customizing-the-default-view-for-a-console}

Sie können die Standardansicht (Spalte, Karte, Liste) für eine Konsole anpassen:

1. Sie können die Ansichten durch Überlagern des erforderlichen Eintrags unter folgendem Pfad neu anordnen:

   `/libs/wcm/core/content/sites/jcr:content/views`

   Der erste Eintrag ist die Standardeinstellung.

   Die verfügbaren Nodes korrelieren mit den verfügbaren Ansichtsoptionen:

   * `column`
   * `card`
   * `list`

1. Beispiel: In einer Überlagerung für die Liste:

   `/apps/wcm/core/content/sites/jcr:content/views/list`

   Definieren Sie folgende Eigenschaften:

   * **Name**: `sling:orderBefore`
   * **Typ**: `String`
   * **Wert**: `column`

### Hinzufügen neuer Aktionen zu Symbolleisten {#add-new-action-to-the-toolbar}

1. Sie können Ihre eigenen Komponenten einschließlich der entsprechenden Clientbibliotheken für benutzerdefinierte Aktionen erstellen. Beispielsweise eine **Twitter**-Werbeaktion unter:

   `/apps/wcm/core/clientlibs/sites/js/twitter.js`

   Diese kann mit einem Symbolleistenelement in Ihrer Konsole verbunden sein:

   `/apps/<yourProject>/admin/ext/launches`

   Beispielsweise im Auswahlmodus:

   `content/jcr:content/body/content/header/items/selection/items/twitter`

### Beschränken einer Symbolleisten-Aktion auf eine bestimmte Gruppe {#restrict-a-toolbar-action-to-a-specific-group}

1. Sie können die Standardaktion mit einer benutzerdefinierten Render-Bedingung überlagern und bestimmte Bedingungen festlegen, die vor dem Rendern erfüllt sein müssen.

   Erstellen Sie beispielsweise eine Komponente zum Steuern der Render-Bedingungen nach Gruppe:

   `/apps/myapp/components/renderconditions/group`

1. Um diese auf die Aktion „Site erstellen“ in der Site-Konsole anzuwenden:

   `/libs/wcm/core/content/sites`

   Erstellen Sie die Überlagerung:

   `/apps/wcm/core/content/sites`

1. Fügen Sie dann die Render-Bedingung für die Aktion hinzu:

   `jcr:content/body/content/header/items/default/items/create/items/createsite/rendercondition`

   Using properties on this node you can define the `groups` allowed to perform the specific action; for example, `administrators`

### Anpassen von Spalten in der Listenansicht {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>This feature is optimized for columns of text fields; for other data types it is possible to overlay `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps`.

Anpassen von Spalten in der Listenansicht:

1. Überlagern Sie die Liste der verfügbaren Spalten.

   * Auf dem Knoten:

      ```
             /apps/wcm/core/content/common/availablecolumns
      ```

   * Fügen Sie die neuen Spalten hinzu oder entfernen Sie vorhandene.
   Weitere Informationen finden Sie unter [Verwenden von Überlagerungen (und der Sling-Ressourcenzusammenführung)](/help/sites-developing/overlays.md).

1. Optional:

   * If you want to plug additional data, you need to write a [PageInforProvider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) with a
      `pageInfoProviderType`.
   Ein Beispiel sehen Sie im unten (aus GitHub) angehängten Class-Bundle.

1. Sie können jetzt die Spalte im Spaltenkonfigurator der Listenansicht auswählen.

### Filtern von Ressourcen {#filtering-resources}

Ein häufiges Nutzungsszenario beim Verwenden der Konsole ist die Auswahl von Ressourcen (z. B. Seiten, Komponenten, Assets usw.) durch den Benutzer. Dabei kann beispielsweise eine Liste verwendet werden, aus der der Autor ein Element auswählen muss.

Um die Größe der Liste (auf die relevanten Einsatzszenarios) zu beschränken, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Weitere Informationen finden Sie in [diesem Artikel](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources).
