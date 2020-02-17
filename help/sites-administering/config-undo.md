---
title: Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung
seo-title: Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung
description: Erfahren Sie, wie Sie die Unterstützung für Rückgängig-Vorgänge zur Seitenbearbeitung in AEM konfigurieren können.
seo-description: Erfahren Sie, wie Sie die Unterstützung für Rückgängig-Vorgänge zur Seitenbearbeitung in AEM konfigurieren können.
uuid: e5a49587-a2a6-41d5-b449-f7a8f7e4cee6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 3cc7efc5-bcb2-41c9-b78b-308f6b7a298e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung{#configuring-undo-for-page-editing}

Der [OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **Day CQ WCM Undo Configuration** (`com.day.cq.wcm.undo.UndoConfigService`) zeigt verschiedene Eigenschaften an, die das Verhalten der Befehle „Rückgängig“ und „Wiederherstellen“ bei der Seitenbearbeitung steuern.

## Standardkonfiguration {#default-configuration}

In a standard installation the default settings are defined as properties on the `sling:OsgiConfig`node:

`/libs/wcm/core/config.author/com.day.cq.wcm.undo.UndoConfig`

Dieser Knoten umfasst die Eigenschaften `cq.wcm.undo.whitelist` und `cq.wcm.undo.blacklist`; bei den anderen Eigenschaften werden die Standardwerte übernommen.

>[!CAUTION]
>
>You ***must*** not change anything in the `/libs` path.
>
>This is because the content of `/libs` is overwritten the next time you upgrade your instance (and may well be overwritten when you apply either a hotfix or feature pack).

## Konfigurieren von Rückgängig- und Wiederherstellen-Vorgängen {#configuring-undo-and-redo}

Sie können diese Eigenschaften des OSGi-Diensts für Ihre eigene Instanz konfigurieren.

>[!NOTE]
>
>Beim Arbeiten mit AEM sind mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Dienste verfügbar. Weitere Informationen und empfohlene Verfahren finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Im Folgenden werden die Eigenschaften aufgeführt, wie sie in der Web Console angezeigt werden, gefolgt vom Namen des entsprechenden OSGi-Parameters, zusammen mit einer Beschreibung und dem Standardwert (sofern zutreffend):

* **Enable**( `cq.wcm.undo.enabled`)

   * **Beschreibung**: Legt fest, ob Seitenautoren Änderungen rückgängig machen oder wiederherstellen können.
   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Pfad**
( `cq.wcm.undo.path`)

   * **Beschreibung**: Der Repository-Pfad zum Beibehalten von Rückgängig-Binärdaten. Wenn Autoren Binärdaten wie Bilder ändern, wird die ursprüngliche Version der Daten hier beibehalten. Wenn Änderungen an binären Daten rückgängig gemacht werden, werden diese binären Rückgängig-Daten auf der Seite wiederhergestellt.
   * **Standard**: `/var/undo`
   * **Typ**: `String`
   >[!NOTE]
   >
   >By default, only administrators can access the `/var/undo` node. Autoren können nur Rückgängig- und Wiederherstellen-Vorgänge für Binärdaten durchführen, wenn ihnen Zugriffsberechtigungen für die Rückgängig-Binärdaten gewährt wurden.

* **Min. validity**
( `cq.wcm.undo.validity`)

   * **Beschreibung**: Die Mindestdauer, die binäre Rückgängig-Daten in Stunden gespeichert werden. Nach dieser Zeit können die Binärdaten gelöscht werden, um Festplattenspeicher einzusparen.
   * **Standard**: `10`
   * **Typ**: `Integer`

* **Schritte**
( `cq.wcm.undo.steps`)

   * **Beschreibung**: Die maximale Anzahl von Seitenaktionen, die im Rückgängig-Verlauf gespeichert werden.
   * **Standard**: `20`
   * **Typ**: `Integer`

* **Persistenz**( `cq.wcm.undo.persistence`)

   * **Beschreibung**: Die Klasse, die den Rückgängig-Verlauf beibehalten. Zwei persistente Klassen werden bereitgestellt:

      * `CQ.undo.persistence.WindowNamePersistence`: Behält den Verlauf mit der Eigenschaft „window.name“ bei.
      * `CQ.undo.persistence.CookiePersistance`: Besteht aus dem Verlauf mithilfe von Cookies.
   * **Standard**: `CQ.undo.persistence.WindowNamePersistence`
   * **Typ**: `String`


* **Persistenzmodus**( `cq.wcm.undo.persistence.mode`)

   * **Beschreibung**: Bestimmt, wann der Rückgängig-Verlauf beibehalten wird. Aktivieren Sie diese Option, damit der Verlauf der Rückgängigmachungen nach jeder Seitenbearbeitung beibehalten wird. Deaktivieren Sie diese Option, damit der Verlauf nur beim erneuten Laden einer Seite beibehalten wird (wenn der Benutzer z. B. zu einer anderen Seite navigiert).

      Der Verlauf der Rückgängigmachungen wird mittels Webbrowserressourcen beibehalten. Wenn der Browser Ihrer Benutzer langsam auf Seitenbearbeitungen reagiert, versuchen Sie, den Verlauf der Rückgängigmachungen bei Seitenneuladungen beizubehalten.

   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Marker-Modus**( `cq.wcm.undo.markermode`)

   * **Beschreibung**: Gibt den visuellen Hinweis an, der verwendet werden soll, um anzugeben, welche Absätze beim Rückgängigmachen oder Wiederholen betroffen sind. Die folgenden Werte sind gültig:

      * flash: Der Auswahlindikator der Absätze wird vorübergehend eingeblendet.
      * select: Der Absatz wird ausgewählt.
   * **Standard**: `flash`
   * **Typ**: `String`


* **Gute Komponenten**( `cq.wcm.undo.whitelist`)

   * **Beschreibung**: Eine Liste von Komponenten, für die die Befehle „Rückgängig“ und „Wiederherstellen“ angewendet werden sollen. Fügen Sie dieser Liste Komponentenpfade hinzu, wenn sie korrekt mit „Rückgängig“/„Wiederherstellen“ funktionieren. Fügen Sie ein Sternchen (&amp;ast;) an, um eine Gruppe von Komponenten anzugeben:

      * Der folgende Wert gibt die Basistextkomponente an:

         `foundation/components/text`

      * Der folgende Wert gibt alle Stiftkomponenten an:

         `foundation/components/*`
   * Wenn der Befehl „Rückgängig“ oder „Wiederherstellen“ für eine Komponente ausgegeben wird, die nicht in dieser Liste vorhanden ist, wird durch eine Meldung darauf hingewiesen, dass der Befehl unzuverlässig sein kann.

   * **Standard**: Die Eigenschaft wird mit vielen von AEM bereitgestellten Komponenten gefüllt.
   * **Typ**: `String[]`


* **Unangemessene Komponenten**( `cq.wcm.undo.blacklist`)

   * **Beschreibung**: Eine Liste der Komponenten und/oder Komponentenoperationen, die vom Rückgängig-Befehl nicht betroffen sein sollen. Fügen Sie Komponenten und Komponentenvorgänge hinzu, die sich beim Anwenden des Befehls „Rückgängig“ nicht ordnungsgemäß verhalten:

      * Fügen Sie einen Komponentenpfad hinzu, wenn keiner der Komponentenvorgänge im Verlauf der Rückgängigmachungen angezeigt werden soll, z. B. `collab/forum/components/post`.
      * Append a colon (:) and an operation to the path when you want that specific operation to be omitted from the undo history (other operations function correctly), for example `collab/forum/components/post:insertParagraph.`
   >[!NOTE]
   >
   >Wenn ein Vorgang in dieser Liste vorhanden ist, wird er nach wie vor dem Verlauf der Rückgängigmachungen hinzugefügt. Benutzer können Vorgänge nicht rückgängig machen, die im Verlauf der Rückgängigmachungen zeitlich vor einem **Bad Component**-Vorgang liegen.

   * Typische Vorgangsnamen lauten etwa wie folgt:

      * `insertParagraph`: Die Komponente wird der Seite hinzugefügt.
      * `removeParagraph`: Die Komponente wird gelöscht.
      * `moveParagraph`: Der Absatz wird an eine andere Stelle verschoben.
      * `updateParagraph`: Die Absatzeigenschaften werden geändert.
   * **Standard**: Die Eigenschaft wird mit mehreren Komponentenvorgängen aufgefüllt.
   * **Typ**: `String[]`




