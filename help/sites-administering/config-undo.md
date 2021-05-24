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
exl-id: 2cf3ac3f-ee17-480d-a32a-c57631502693
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 67%

---

# Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung{#configuring-undo-for-page-editing}

Der [OSGi-Dienst](/help/sites-deploying/configuring-osgi.md) **Day CQ WCM Undo Configuration** (`com.day.cq.wcm.undo.UndoConfigService`) zeigt verschiedene Eigenschaften an, die das Verhalten der Befehle „Rückgängig“ und „Wiederherstellen“ bei der Seitenbearbeitung steuern.

## Standardkonfiguration {#default-configuration}

In einer Standardinstallation werden die Standardeinstellungen als Eigenschaften auf dem Knoten `sling:OsgiConfig`definiert:

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
>Beim Arbeiten mit AEM sind mehrere Methoden zum Verwalten der Konfigurationseinstellungen für solche Dienste verfügbar. Weitere Informationen und empfohlene Verfahren finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

Im Folgenden werden die Eigenschaften aufgelistet, die in der Web-Konsole angezeigt werden, gefolgt vom Namen des entsprechenden OSGi-Parameters, zusammen mit einer Beschreibung und dem Standardwert (sofern zutreffend):

* **Aktivieren**
( 
`cq.wcm.undo.enabled`)

   * **Beschreibung**: Legt fest, ob Seitenautoren Änderungen rückgängig machen oder wiederherstellen können.
   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Pfad**
( 
`cq.wcm.undo.path`)

   * **Beschreibung**: Der Repository-Pfad zum Beibehalten von Rückgängig-Binärdaten. Wenn Autoren Binärdaten wie Bilder ändern, wird die ursprüngliche Version der Daten hier beibehalten. Wenn Änderungen an Binärdaten rückgängig gemacht werden, werden diese binären Rückgängig-Daten auf der Seite wiederhergestellt.
   * **Standard**: `/var/undo`
   * **Typ**: `String`

   >[!NOTE]
   >
   >Standardmäßig können nur Administratoren auf den Knoten `/var/undo` zugreifen. Autoren können nur Rückgängig- und Wiederherstellen-Vorgänge für Binärdaten durchführen, wenn ihnen Zugriffsberechtigungen für die Rückgängig-Binärdaten gewährt wurden.

* **Min. validity**
( 
`cq.wcm.undo.validity`)

   * **Beschreibung**: Die Mindestdauer, für die binäre Rückgängig-Daten gespeichert werden (in Stunden). Nach dieser Zeit können die Binärdaten gelöscht werden, um Festplattenspeicher einzusparen.
   * **Standard**: `10`
   * **Typ**: `Integer`

* **Schritte**
( 
`cq.wcm.undo.steps`)

   * **Beschreibung**: Die maximale Anzahl von Seitenaktionen, die im Verlauf der Rückgängigmachungen gespeichert sind.
   * **Standard**: `20`
   * **Typ**: `Integer`

* **Persistenz**
( 
`cq.wcm.undo.persistence`)

   * **Beschreibung**: Die Klasse, die den Verlauf der Rückgängigmachungen beibehält. Zwei persistente Klassen werden bereitgestellt:

      * `CQ.undo.persistence.WindowNamePersistence`: Behält den Verlauf mit der Eigenschaft „window.name“ bei.
      * `CQ.undo.persistence.CookiePersistance`: Behält den Verlauf mithilfe von Cookies bei.
   * **Standard**: `CQ.undo.persistence.WindowNamePersistence`
   * **Typ**: `String`


* **Persistenzmodus**
( 
`cq.wcm.undo.persistence.mode`)

   * **Beschreibung**: Bestimmt, wann der Verlauf der Rückgängigmachungen beibehalten wird. Aktivieren Sie diese Option, damit der Verlauf der Rückgängigmachungen nach jeder Seitenbearbeitung beibehalten wird. Deaktivieren Sie diese Option, damit der Verlauf nur beim erneuten Laden einer Seite beibehalten wird (wenn der Benutzer z. B. zu einer anderen Seite navigiert).

      Der Verlauf der Rückgängigmachungen wird mittels Webbrowserressourcen beibehalten. Wenn der Browser Ihrer Benutzer langsam auf Seitenbearbeitungen reagiert, versuchen Sie, den Verlauf der Rückgängigmachungen bei Seitenneuladungen beizubehalten.

   * **Standard**: `Selected`
   * **Typ**: `Boolean`

* **Marker mode**
( 
`cq.wcm.undo.markermode`)

   * **Beschreibung**: Gibt den visuellen Hinweis an, der verwendet werden soll, um anzugeben, welche Absätze bei einem Rückgängigmachen oder Wiederholen betroffen sind. Die folgenden Werte sind gültig:

      * flash: Der Auswahlindikator der Absätze wird vorübergehend eingeblendet.
      * select: Der Absatz wird ausgewählt.
   * **Standard**: `flash`
   * **Typ**: `String`


* **Gute Komponenten**
 ( 
`cq.wcm.undo.whitelist`)

   * **Beschreibung**: Eine Liste von Komponenten, für die die Befehle „Rückgängig“ und „Wiederherstellen“ angewendet werden sollen. Fügen Sie dieser Liste Komponentenpfade hinzu, wenn sie korrekt mit „Rückgängig“/„Wiederherstellen“ funktionieren. Hängen Sie ein Sternchen (&amp;ast;) an, um eine Gruppe von Komponenten anzugeben:

      * Der folgende Wert gibt die Foundation-Textkomponente an:

         `foundation/components/text`

      * Der folgende Wert gibt alle Foundation-Komponenten an:

         `foundation/components/*`
   * Wenn der Befehl „Rückgängig“ oder „Wiederherstellen“ für eine Komponente ausgegeben wird, die nicht in dieser Liste vorhanden ist, wird durch eine Meldung darauf hingewiesen, dass der Befehl unzuverlässig sein kann.

   * **Standard**: Die Eigenschaft wird mit vielen Komponenten gefüllt, die AEM bereitstellt.
   * **Typ**: `String[]`


* **Ungültige Komponenten**
 ( 
`cq.wcm.undo.blacklist`)

   * **Beschreibung**: Eine Liste von Komponenten und/oder Komponentenvorgängen, die vom Befehl &quot;Rückgängig&quot;nicht betroffen sein sollen. Fügen Sie Komponenten und Komponentenvorgänge hinzu, die sich beim Anwenden des Befehls „Rückgängig“ nicht ordnungsgemäß verhalten:

      * Fügen Sie einen Komponentenpfad hinzu, wenn keiner der Komponentenvorgänge im Verlauf der Rückgängigmachungen angezeigt werden soll, z. B. `collab/forum/components/post`.
      * Hängen Sie einen Doppelpunkt (:) und einen Vorgang an den Pfad an, wenn Sie möchten, dass dieser bestimmte Vorgang im Verlauf der Rückgängigmachungen weggelassen wird (andere Vorgänge funktionieren ordnungsgemäß), z. B. `collab/forum/components/post:insertParagraph.`

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
