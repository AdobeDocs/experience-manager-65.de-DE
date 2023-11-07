---
title: Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung
seo-title: Configuring Undo for Page Editing
description: Erfahren Sie, wie Sie die Rückgängig-Unterstützung für die Seitenbearbeitung in AEM konfigurieren.
seo-description: Learn how to configure Undo support for page editing in AEM.
uuid: e5a49587-a2a6-41d5-b449-f7a8f7e4cee6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 3cc7efc5-bcb2-41c9-b78b-308f6b7a298e
exl-id: 2cf3ac3f-ee17-480d-a32a-c57631502693
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 67%

---

# Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung{#configuring-undo-for-page-editing}

Der [OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **Day CQ WCM Undo Configuration** (`com.day.cq.wcm.undo.UndoConfigService`) zeigt verschiedene Eigenschaften an, die das Verhalten der Befehle „Rückgängig“ und „Wiederherstellen“ bei der Seitenbearbeitung steuern.

## Standardkonfiguration {#default-configuration}

Bei einer Standardinstallation werden die Standardeinstellungen als Eigenschaften im Knoten `sling:OsgiConfig` definiert:

`/libs/wcm/core/config.author/com.day.cq.wcm.undo.UndoConfig`

Dieser Knoten umfasst die Eigenschaften `cq.wcm.undo.whitelist` und `cq.wcm.undo.blacklist`; bei den anderen Eigenschaften werden die Standardwerte übernommen.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen,
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal aktualisieren. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)

## Konfigurieren von &quot;Rückgängig&quot;und &quot;Wiederherstellen&quot; {#configuring-undo-and-redo}

Sie können diese OSGi-Diensteigenschaften für Ihre eigene Instanz konfigurieren.

>[!NOTE]
>
>Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Nachfolgend werden die Eigenschaften so aufgeführt, wie sie in der Web-Konsole angezeigt werden. Darauf folgt der Name des entsprechenden OSGi-Parameters zusammen mit einer Beschreibung und (ggf.) dem Standardwert:

* **Aktivieren**
( `cq.wcm.undo.enabled`)

   * **Beschreibung**: Legt fest, ob Seitenautoren Änderungen rückgängig machen oder wiederherstellen können.
   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Pfad**
( `cq.wcm.undo.path`)

   * **Beschreibung**: Der Repository-Pfad für die Beibehaltung binärer Rückgängig-Daten. Wenn Autoren Binärdaten wie Bilder ändern, wird hier die Originalversion der Daten beibehalten. Wenn Änderungen an den Binärdaten rückgängig gemacht werden, werden diese Rückgängig-Binärdaten auf der Seite wiederhergestellt.
   * **Standard**: `/var/undo`
   * **Typ**: `String`

  >[!NOTE]
  >
  >Standardmäßig können nur Admins auf den Knoten `/var/undo` zugreifen. Autoren können Vorgänge zum Rückgängigmachen und Wiederholen von Binärinhalten erst dann ausführen, wenn ihnen Berechtigungen für den Zugriff auf die binären Rückgängig-Daten erteilt wurden.

* **Min. validity**
( `cq.wcm.undo.validity`)

   * **Beschreibung**: Der Mindestzeitraum, über den Rückgängig-Binärdaten gespeichert werden (in Stunden). Nach dieser Zeit können die Binärdaten gelöscht werden, um Festplattenspeicher einzusparen.
   * **Standard**: `10`
   * **Typ**: `Integer`

* **Schritte**
( `cq.wcm.undo.steps`)

   * **Beschreibung**: Die maximale Anzahl an Seitenaktionen, die im Verlauf der Rückgängigmachungen gespeichert werden.
   * **Standard**: `20`
   * **Typ**: `Integer`

* **Persistenz**
( `cq.wcm.undo.persistence`)

   * **Beschreibung**: Die Klasse, in der der Verlauf der Rückgängigmachungen beibehalten wird. Zwei persistente Klassen werden bereitgestellt:

      * `CQ.undo.persistence.WindowNamePersistence`: Behält den Verlauf mit der Eigenschaft „window.name“ bei.
      * `CQ.undo.persistence.CookiePersistance`: Behält den Verlauf mit Cookies bei.

   * **Standard**: `CQ.undo.persistence.WindowNamePersistence`
   * **Typ**: `String`

* **Persistenzmodus**
( `cq.wcm.undo.persistence.mode`)

   * **Beschreibung**: Legt fest, wann der Verlauf der Rückgängigmachungen beibehalten wird. Wählen Sie diese Option, um den Verlauf der rückgängig gemachten Angaben nach jeder Seitenbearbeitung beizubehalten. Deaktivieren Sie diese Option, damit sie nur beibehalten wird, wenn eine Seite neu geladen wird (z. B. wenn der Benutzer zu einer anderen Seite navigiert).

     Der Verlauf der Rückgängigmachungen wird mittels Webbrowserressourcen beibehalten. Wenn der Browser Ihrer Benutzer langsam auf Seitenbearbeitungen reagiert, versuchen Sie, den Verlauf der Rückgängigmachungen bei Seitenneuladungen beizubehalten.

   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Markierungsmodus**
( `cq.wcm.undo.markermode`)

   * **Beschreibung**: Gibt den visuellen Hinweis an, der verwendet wird, um die von einem Rückgängig- oder Wiederherstellen-Vorgang betroffenen Absätze anzugeben. Die folgenden Werte sind gültig:

      * flash: Die Auswahlanzeige der Absätze blinkt vorübergehend.
      * select: Der Absatz ist ausgewählt.

   * **Standard**: `flash`
   * **Typ**: `String`

* **Gute Komponenten**
( `cq.wcm.undo.whitelist`)

   * **Beschreibung**: Eine Liste von Komponenten, die von Befehlen zum Rückgängigmachen und Wiederholen betroffen sein sollen. Fügen Sie Komponentenpfade zu dieser Liste hinzu, wenn sie beim Rückgängigmachen/Wiederholen ordnungsgemäß funktionieren. Hängen Sie ein Sternchen (&amp;ast;) an, um eine Gruppe von Komponenten anzugeben:

      * Der folgende Wert legt die Foundation-Textkomponente fest:

        `foundation/components/text`

      * Der folgende Wert legt alle Foundation-Komponenten fest:

        `foundation/components/*`

   * Wenn der Befehl „Rückgängig“ oder „Wiederherstellen“ für eine Komponente ausgegeben wird, die nicht in dieser Liste vorhanden ist, wird durch eine Meldung darauf hingewiesen, dass der Befehl unzuverlässig sein kann.

   * **Standard**: Die Eigenschaft wird mit vielen von AEM bereitgestellten Komponenten aufgefüllt.
   * **Typ**: `String[]`

* **Ungültige Komponenten**
( `cq.wcm.undo.blacklist`)

   * **Beschreibung**: Eine Liste der Komponenten und/oder Komponentenvorgänge, für die die Befehle „Rückgängig“ und „Wiederherstellen“ nicht angewendet werden sollen. Fügen Sie Komponenten und Komponentenvorgänge hinzu, die sich beim Anwenden des Befehls „Rückgängig“ nicht ordnungsgemäß verhalten:

      * Fügen Sie einen Komponentenpfad hinzu, wenn Sie keine der Vorgänge der Komponente im Verlauf der Rückgängigmachungen anzeigen möchten, z. B. `collab/forum/components/post`
      * Hängen Sie einen Doppelpunkt (:) und einen Vorgang an den Pfad an, wenn Sie möchten, dass dieser bestimmte Vorgang aus dem Verlauf der Rückgängigmachungen ausgelassen wird (andere Vorgänge funktionieren beispielsweise ordnungsgemäß). `collab/forum/components/post:insertParagraph.`

  >[!NOTE]
  >
  >Wenn sich ein Vorgang auf dieser Liste befindet, wird er dennoch zum Verlauf der Rückgängigmachungen hinzugefügt. Benutzer können Vorgänge, die vor einem **Ungültige Komponente** -Operation im Verlauf der Rückgängigmachungen.

   * Typische Vorgangsnamen sind:

      * `insertParagraph`: Die Komponente wird der Seite hinzugefügt.
      * `removeParagraph`: Die Komponente wird gelöscht.
      * `moveParagraph`: Der Absatz wird an eine andere Stelle verschoben.
      * `updateParagraph`: Die Absatzeigenschaften werden geändert.

   * **Standard**: Die Eigenschaft wird mit mehreren Komponentenvorgängen aufgefüllt.
   * **Typ**: `String[]`
