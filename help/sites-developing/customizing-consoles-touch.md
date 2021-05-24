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
exl-id: 6e67f2b3-78b9-45f2-b496-61776b9fd9cc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 77%

---

# Anpassen der Konsolen  {#customizing-the-consoles}

>[!CAUTION]
>
>In diesem Dokument wird beschrieben, wie Sie Konsolen in der modernen, Touch-optimierten Benutzeroberfläche anpassen. Die Hinweise gelten nicht für die klassische Benutzeroberfläche.

AEM bietet verschiedene Methoden zum Anpassen von Konsolen (und der [Seitenbearbeitungsfunktionen](/help/sites-developing/customizing-page-authoring-touch.md)) Ihrer Autoreninstanz.

* Clientbibliotheken Mit Clientbibliotheken können Sie die Standardimplementierung um neue Funktionen erweitern und gleichzeitig Standardfunktionen, -objekte und -methoden weiterhin verwenden. Bei der Anpassung können Sie Ihre eigene Client-Bibliothek unter `/apps.` erstellen. Beispielsweise kann sie den Code enthalten, der für Ihre benutzerdefinierte Komponente erforderlich ist.

* Überlagerungen
Überlagerungen basieren auf Knotendefinitionen und ermöglichen es Ihnen, die Standardfunktionalität (in `/libs`) mit Ihrer eigenen benutzerdefinierten Funktionalität (in `/apps`) zu überlagern. Wenn Sie eine Überlagerung erstellen, ist keine 1:1-Kopie des Originals erforderlich, da die Sling-Ressourcenzusammenführung das Vererben zulässt.

Überlagerungen können vielseitig zum Erweitern von AEM-Konsolen verwendet werden. Einige davon sind nachstehend (allgemein) beschrieben.

>[!NOTE]
>
>Weitere Informationen finden Sie unter:
>
>* Verwenden und Erstellen von [Clientbibliotheken](/help/sites-developing/clientlibs.md).
>* Verwenden und Erstellen von [Überlagerungen](/help/sites-developing/overlays.md).
>* [Granite](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/index.html)

>
>
Dieses Thema wird auch in der [AEM Gems](https://docs.adobe.com/content/ddc/en/gems.html)-Sitzung [Anpassung der Benutzeroberfläche für AEM 6.0](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html) behandelt.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)
>
>Die empfohlene Methode zur Konfiguration und für andere Änderungen sieht wie folgt aus:
>
>1. Erstellen Sie das erforderliche Element (d. h. wie es in `/libs` vorhanden ist) unter `/apps` neu.
   >
   >
1. Nehmen Sie die gewünschten Änderungen in `/apps` vor.

>



Beispielsweise kann der folgende Speicherort innerhalb der `/libs`-Struktur überlagert werden:

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

   Mithilfe der Eigenschaften dieses Knotens können Sie die `groups` definieren, die für die Ausführung der spezifischen Aktion zulässig ist. Beispiel: `administrators`

### Anpassen von Spalten in der Listenansicht {#customizing-columns-in-the-list-view}

>[!NOTE]
>
>Diese Funktion ist für Spalten von Textfeldern optimiert. Bei anderen Datentypen ist es möglich, `cq/gui/components/siteadmin/admin/listview/columns/analyticscolumnrenderer` in `/apps` zu überlagern.

Anpassen von Spalten in der Listenansicht:

1. Überlagern Sie die Liste der verfügbaren Spalten.

   * Auf dem Knoten:

      ```
             /apps/wcm/core/content/common/availablecolumns
      ```

   * Fügen Sie die neuen Spalten hinzu oder entfernen Sie vorhandene.
   Weitere Informationen finden Sie unter [Verwenden von Überlagerungen (und der Sling-Ressourcenzusammenführung)](/help/sites-developing/overlays.md).

1. Optional:

   * Wenn Sie zusätzliche Daten einbinden möchten, müssen Sie einen [PageInforProvider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageInfoProvider.html) mit einer
      `pageInfoProviderType` property.

   Ein Beispiel sehen Sie im unten (aus GitHub) angehängten Class-Bundle.

1. Sie können jetzt die Spalte im Spaltenkonfigurator der Listenansicht auswählen.

### Filtern von Ressourcen  {#filtering-resources}

Ein häufiges Nutzungsszenario beim Verwenden der Konsole ist die Auswahl von Ressourcen (z. B. Seiten, Komponenten, Assets usw.) durch den Benutzer. Dabei kann beispielsweise eine Liste verwendet werden, aus der der Autor ein Element auswählen muss.

Um die Größe der Liste (auf die relevanten Einsatzszenarios) zu beschränken, kann ein Filter in Form eines benutzerdefinierten Prädikats implementiert werden. Weitere Informationen finden Sie in [diesem Artikel](/help/sites-developing/customizing-page-authoring-touch.md#filtering-resources).
