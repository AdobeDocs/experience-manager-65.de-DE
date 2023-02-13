---
title: Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung
seo-title: Configuring Undo for Page Editing
description: Erfahren Sie, wie Sie die Unterstützung für Rückgängig-Vorgänge zur Seitenbearbeitung in AEM konfigurieren können.
seo-description: Learn how to configure Undo support for page editing in AEM.
uuid: e5a49587-a2a6-41d5-b449-f7a8f7e4cee6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 3cc7efc5-bcb2-41c9-b78b-308f6b7a298e
exl-id: 2cf3ac3f-ee17-480d-a32a-c57631502693
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '702'
ht-degree: 100%

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

## Konfigurieren von Rückgängig- und Wiederherstellen-Vorgängen {#configuring-undo-and-redo}

Sie können diese Eigenschaften des OSGi-Diensts für Ihre eigene Instanz konfigurieren.

>[!NOTE]
>
>Bei AEM können Sie die Konfigurationseinstellungen für Dienste dieser Art auf unterschiedliche Weise vornehmen. Informationen zur empfohlenen Vorgehensweise finden Sie unter [Konfigurieren von OSGi.](/help/sites-deploying/configuring-osgi.md).

Nachfolgend werden die Eigenschaften so aufgeführt, wie sie in der Web-Konsole angezeigt werden. Darauf folgt der Name des entsprechenden OSGi-Parameters zusammen mit einer Beschreibung und (ggf.) dem Standardwert:

* **Aktivieren**
( 
`cq.wcm.undo.enabled`)

   * **Beschreibung**: Legt fest, ob Seitenautoren Änderungen rückgängig machen oder wiederherstellen können.
   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Pfad**
( 
`cq.wcm.undo.path`)

   * **Beschreibung**: Der Repository-Pfad zum Beibehalten von Rückgängig-Binärdaten. Wenn Autoren Binärdaten wie Bilder ändern, wird die ursprüngliche Version der Daten hier beibehalten. Wenn Änderungen an den Binärdaten rückgängig gemacht werden, werden diese Rückgängig-Binärdaten auf der Seite wiederhergestellt.
   * **Standard**: `/var/undo`
   * **Typ**: `String`

   >[!NOTE]
   >
   >Standardmäßig können nur Admins auf den Knoten `/var/undo` zugreifen. Autoren können nur Rückgängig- und Wiederherstellen-Vorgänge für Binärdaten durchführen, wenn ihnen Zugriffsberechtigungen für die Rückgängig-Binärdaten gewährt wurden.

* **Min. validity**
( 
`cq.wcm.undo.validity`)

   * **Beschreibung**: Der Mindestzeitraum, über den Rückgängig-Binärdaten gespeichert werden (in Stunden). Nach dieser Zeit können die Binärdaten gelöscht werden, um Festplattenspeicher einzusparen.
   * **Standard**: `10`
   * **Typ**: `Integer`

* **Schritte**
( 
`cq.wcm.undo.steps`)

   * **Beschreibung**: Die maximale Anzahl an Seitenaktionen, die im Verlauf der Rückgängigmachungen gespeichert werden.
   * **Standard**: `20`
   * **Typ**: `Integer`

* **Persistenz**
( 
`cq.wcm.undo.persistence`)

   * **Beschreibung**: Die Klasse, in der der Verlauf der Rückgängigmachungen beibehalten wird. Zwei persistente Klassen werden bereitgestellt:

      * `CQ.undo.persistence.WindowNamePersistence`: Behält den Verlauf mit der Eigenschaft „window.name“ bei.
      * `CQ.undo.persistence.CookiePersistance`: Behält den Verlauf mit Cookies bei.
   * **Standard**: `CQ.undo.persistence.WindowNamePersistence`
   * **Typ**: `String`


* **Persistenzmodus**
( 
`cq.wcm.undo.persistence.mode`)

   * **Beschreibung**: Legt fest, wann der Verlauf der Rückgängigmachungen beibehalten wird. Aktivieren Sie diese Option, damit der Verlauf der Rückgängigmachungen nach jeder Seitenbearbeitung beibehalten wird. Deaktivieren Sie diese Option, damit der Verlauf nur beim erneuten Laden einer Seite beibehalten wird (wenn der Benutzer z. B. zu einer anderen Seite navigiert).

      Der Verlauf der Rückgängigmachungen wird mittels Webbrowserressourcen beibehalten. Wenn der Browser Ihrer Benutzer langsam auf Seitenbearbeitungen reagiert, versuchen Sie, den Verlauf der Rückgängigmachungen bei Seitenneuladungen beizubehalten.

   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Markierungsmodus**
( 
`cq.wcm.undo.markermode`)

   * **Beschreibung**: Gibt den visuellen Hinweis an, der verwendet wird, um die von einem Rückgängig- oder Wiederherstellen-Vorgang betroffenen Absätze anzugeben. Die folgenden Werte sind gültig:

      * flash: Der Auswahlindikator der Absätze wird vorübergehend eingeblendet.
      * select: Der Absatz wird ausgewählt.
   * **Standard**: `flash`
   * **Typ**: `String`


* **Gute Komponenten**
( 
`cq.wcm.undo.whitelist`)

   * **Beschreibung**: Eine Liste von Komponenten, für die die Befehle „Rückgängig“ und „Wiederherstellen“ angewendet werden sollen. Fügen Sie dieser Liste Komponentenpfade hinzu, wenn sie korrekt mit „Rückgängig“/„Wiederherstellen“ funktionieren. Hängen Sie ein Sternchen (&amp;ast;) an, um eine Gruppe von Komponenten anzugeben:

      * Der folgende Wert legt die Foundation-Textkomponente fest:

         `foundation/components/text`

      * Der folgende Wert legt alle Foundation-Komponenten fest:

         `foundation/components/*`
   * Wenn der Befehl „Rückgängig“ oder „Wiederherstellen“ für eine Komponente ausgegeben wird, die nicht in dieser Liste vorhanden ist, wird durch eine Meldung darauf hingewiesen, dass der Befehl unzuverlässig sein kann.

   * **Standard**: Die Eigenschaft wird mit vielen von AEM bereitgestellten Komponenten aufgefüllt.
   * **Typ**: `String[]`


* **Ungültige Komponenten**
( 
`cq.wcm.undo.blacklist`)

   * **Beschreibung**: Eine Liste der Komponenten und/oder Komponentenvorgänge, für die die Befehle „Rückgängig“ und „Wiederherstellen“ nicht angewendet werden sollen. Fügen Sie Komponenten und Komponentenvorgänge hinzu, die sich beim Anwenden des Befehls „Rückgängig“ nicht ordnungsgemäß verhalten:

      * Fügen Sie einen Komponentenpfad hinzu, wenn keiner der Komponentenvorgänge im Verlauf der Rückgängigmachungen angezeigt werden soll, z. B. `collab/forum/components/post`.
      * Hängen Sie einen Doppelpunkt (:) und einen Vorgang an den Pfad an, wenn dieser Vorgang im Verlauf der Rückgängigmachungen ausgelassen werden soll (bei ordnungsgemäßer Funktionsweise der anderen Vorgänge), z. B. `collab/forum/components/post:insertParagraph.`.

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
