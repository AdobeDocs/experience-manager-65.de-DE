---
title: Benutzerdefinierte Knotentypen
seo-title: Benutzerdefinierte Knotentypen
description: AEM basiert auf Sling und verwendet ein JCR-Repository mit von AEM und JCR bereitgestellten Knotentypen. Darüber hinaus bietet AEM aber auch eine Reihe benutzerdefinierter Knotentypen.
seo-description: AEM basiert auf Sling und verwendet ein JCR-Repository mit von AEM und JCR bereitgestellten Knotentypen. Darüber hinaus bietet AEM aber auch eine Reihe benutzerdefinierter Knotentypen.
uuid: f2022504-e433-4b42-9cc1-eef41086483a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: aae186eb-e059-4a9d-b02d-86a86c86589d
translation-type: tm+mt
source-git-commit: 07eb53f19cf7c7c2799c95ba9df54f4673d72fdc
workflow-type: tm+mt
source-wordcount: '1918'
ht-degree: 53%

---


# Benutzerdefinierte Knotentypen{#custom-node-types}

Da AEM auf Sling basiert und ein JCR-Repository verwendet, stehen die beiden folgenden Knotentypen zur Verwendung zur Verfügung:

* [JCR-Knotentypen](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling-Knotentypen](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

Darüber hinaus stellt AEM stellt eine Reihe benutzerdefinierter Knotentypen bereit.

## Audit {#audit}

### cq:AuditEvent {#cq-auditevent}

**Beschreibung**

Definiert den Knotentyp eines Audit-Ereignisknotens.

* `@prop cq:time`
* `@prop cq:userid`
* `@prop cq:path`
* `@prop cq:type`
* `@prop cq:category`
* `@prop cq:properties`

**Definition**

* `[cq:AuditEvent]`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
* `- cq:time (date)`
* `- cq:userid (string)`
* `- cq:path (string)`
* `- cq:type (string)`
* `- cq:category (string)`
* `- cq:properties (binary)`

## Kommentar {#comment}

### cq:Comment {#cq-comment}

**Beschreibung**

Definiert den Knotentyp eines comment-Knotens.

* `@prop userIdentifier`

**Definition**

* `[cq:Comment] > mix:title, mix:created, mix:language, nt:unstructured, cq:Taggable`
* `- email (string)`
* `- ip (string)`
* `- referer (string)`
* `- url (string)`
* `- userAgent (string)`
* `- userIdentifier (string)`
* `- authorizableId (string)`

### cq:CommentAttachment {#cq-commentattachment}

**Beschreibung**

Definiert den Nodetyp eines `commentattachment`-Knotens

**Definition**

* `[cq:CommentAttachment] > nt:file`
   * `- * (undefined)`
   * `- * (undefined) multiple`

### cq:CommentContent {#cq-commentcontent}

**Beschreibung**

Definiert den Knotentyp eines commentcontent-Knotens.

**Definition**

* `[cq:Comment] > mix:title, mix:created, mix:language, nt:unstructured, cq:Taggable`
* `- email (string)`
* `- ip (string)`
* `- referer (string)`
* `- url (string)`
* `- userAgent (string)`
* `- userIdentifier (string)`
* `- authorizableId (string)`

### cq:GeoLocation {#cq-geolocation}

**Beschreibung**

Ein Mixin, das eine geografische Position in Dezimalgraden (DD) definiert.

* `@prop latitude` - als Dublette mit Dezimalgraden kodierte Breitengrad
* `@prop longitude` - als Dublette mit Dezimalgraden kodierter Längengrad

**Definition**

* `[cq:GeoLocation] mixin`
* `- latitude (double)`
* `- longitude (double)`

### cq:Trackback {#cq-trackback}

**Beschreibung**

Definiert den Knotentyp eines trackback-Knotens.

**Definition**

* `[cq:Trackback] > mix:title, mix:created, mix:language, nt:unstructured`

## Core {#core}

### cq:Page {#cq-page}

**Beschreibung**

Definiert die standardmäßige CQ-Seite.

* `@node jcr:content` - Seiteninhalt Primär.

**Definition**

* `[cq:Page] > nt:hierarchyNode orderable`
   * `+ jcr:content (nt:base) = nt:unstructured copy primary`
   * `+ * (nt:base) = nt:base version`

### cq:PseudoPage {#cq-pseudopage}

**Beschreibung**

Definiert einen Mixintyp, der Knoten als Pseudoseiten markiert. Dies bedeutet, dass diese zur Unterstützung der Seiten- und WCM-Bearbeitung angepasst werden können.

**Definition**

* `[cq:PseudoPage] mixin`

### cq:PageContent {#cq-pagecontent}

**Beschreibung**

Definiert den Standardknoten für den Seiteninhalt mit den von WCM verwendeten Mindesteigenschaften.

* `@prop jcr:title` - Titel der Seite.
* `@prop jcr:description` - Beschreibung dieser Seite.
* `@prop cq:template` - Pfad zur Vorlage, die zum Erstellen der Seite verwendet wird.
* `@prop cq:allowedTemplates` - Liste der regulären Ausdruck zur Bestimmung des Pfads/der Pfade für die zulässige Vorlage.
* `@prop pageTitle` - Der Titel wird normalerweise im  `<title>` Tag angezeigt.
* `@prop navTitle` - Titel, der normalerweise bei der Navigation verwendet wird.
* `@prop hideInNav` - Gibt an, ob die Seite in der Navigation ausgeblendet werden soll.
* `@prop onTime` - Zeitpunkt, zu dem diese Seite gültig wird.
* `@prop offTime` - Zeitpunkt, zu dem diese Seite ungültig wird.
* `@prop cq:lastModified` - Datum der letzten Änderung der Seite (oder ihrer Absätze).
* `@prop cq:lastModifiedBy` - Letzter Benutzer zum Ändern der Seite (oder der zugehörigen Absätze).
* `@prop jcr:language` - Die Sprache des Seiteninhalts.

>[!NOTE]
>
>Es ist nicht zwingend erforderlich, dass der Seiteninhalt diesen Typ verwendet.

**Definition**
* `[cq:PageContent] > nt:unstructured, mix:title, mix:created, cq:OwnerTaggable, sling:VanityPath, cq:ReplicationStatus, sling:Resource orderable`
   * `- cq:template (string)`
   * `- cq:allowedTemplates (string) multiple`
   * `- pageTitle (string)`
   * `- navTitle (string)`
   * `- hideInNav (boolean)`
   * `- onTime (date)`
   * `- offTime (date)`
   * `- cq:lastModified (date)`
   * `- cq:lastModifiedBy (string)`
   * `- cq:designPath (string)`
   * `- jcr:language (string)`

### cq:Template {#cq-template}

**Beschreibung**

Definiert eine CQ-Vorlage.

* `@node jcr:content` - Standardinhalt für neue Seiten.
* `@node icon.png` - Eine Datei, die ein charakteristisches Symbol enthält.
* `@node thumbnail.png` - Eine Datei, die ein charakteristisches Miniaturbild enthält.
* `@node workflows` - Automatische Zuweisung der Workflow-Konfiguration. Die Konfiguration folgt der folgenden Struktur:
   * `+ workflows`
      * `+ name1`
         * `- cq:path`
            * `- cq:workflowName`
* `@prop allowedParents` - Regelmäßige Ausdruck-Muster zur Bestimmung des Pfads/der Pfade zu Vorlagen, der/die als übergeordnete Vorlagen zulässig sind.
* `@prop allowedChildren` - Regelmäßige Ausdruck-Muster zur Bestimmung des Pfads/der Pfade zu Vorlagen, die als untergeordnete Vorlagen zulässig sind.
* `@prop ranking` - Positionieren Sie die Vorlagen im Dialogfeld &quot;Seite erstellen&quot;in der Liste.

**Definition**

* `[cq:Template] > nt:hierarchyNode, mix:title`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
   * `+ jcr:content (nt:base) copy`
   * `+ icon.png (nt:file) copy`
   * `+ thumbnail.png (nt:file) copy`
   * `+ workflows (nt:base) copy`
   * `- allowedParents (string) multiple`
   * `- allowedChildren (string) multiple`
   * `- ranking (long)`

### cq:Component {#cq-component}

**Beschreibung**

Definiert eine CQ-Komponente.

* `@prop jcr:title` - Titel der Komponente.
* `@prop jcr:description` - Beschreibung der Komponente.
* `@node dialog` - Primär.
* `@prop dialogPath` - Primär Dialogpfad (Alternative zum Dialog).
* `@node design_dialog` - Dialogfeld &quot;Design&quot;
* `@prop cq:cellName` - Name der Entwurfzelle.
* `@prop cq:isContainer` - Gibt an, ob es sich um eine Container-Komponente handelt. Damit wird die Verwendung der Zellnamen der untergeordneten Komponenten anstelle von Pfadnamen erzwungen. Beispielsweise ist die `parsys`-Komponente eine Container-Komponente. Wenn dieser Wert nicht definiert ist, wird überprüft, ob eine `cq:childEditConfig` vorliegt.
* `@prop cq:noDecoration` - Wenn &quot;true&quot;, werden keine Dekorations- `div` Tags gezeichnet, wenn diese Komponente einbezogen wird.
* `@node cq:editConfig` - Die Konfiguration, die die Parameter für die Bearbeitungsleiste definiert.
* `@node cq:childEditConfig` - Die Bearbeitungskonfiguration, die von untergeordneten Komponenten geerbt wird.
* `@node cq:htmlTag` - Definiert zusätzliche Tag-Attribute, die dem &quot;umgebenden&quot;  `div` Tag hinzugefügt werden, wenn die Komponente einbezogen wird.
* `@node icon.png`- Eine Datei, die ein charakteristisches Symbol enthält.
* `@node thumbnail.png` - Eine Datei, die ein charakteristisches Miniaturbild enthält.
* `@prop allowedParents` - Regelmäßige Ausdruck zur Bestimmung des Pfads bzw. der Pfade von Komponenten, die als übergeordnete Komponenten zulässig sind.
* `@prop allowedChildren` - Regelmäßige Ausdruck-Muster zur Bestimmung des Pfads bzw. der Pfade von Komponenten, die als untergeordnete Komponenten zulässig sind.
* `@node virtual` - Enthält Unterknoten, die virtuelle Komponenten widerspiegeln, welche zum Verschieben der Komponenten per Drag-and-Drop verwendet werden.
* `@prop componentGroup` - Name der Komponentengruppe, die für die Drag &amp; Drop-Funktion der Komponente verwendet wird.
* `@node cq:infoProviders` - Enthält Unterknoten, von denen jede eine Eigenschaft hat,  `className` die auf eine  `PageInfoProvider`verweist.

**Definition**

* `[cq:Component] > nt:folder, mix:title, sling:ResourceSuperType`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ * (nt:base) = nt:base multiple version`
   * `+ dialog (nt:base) = nt:unstructured copy`
   * `- dialogPath (string)`
   * `+ design_dialog (nt:base) = nt:unstructured copy`
   * `- cq:cellName (string)`
   * `- cq:isContainer (boolean)`
   * `- cq:noDecoration (boolean)`
   * `+ cq:editConfig (cq:EditConfig) = cq:EditConfig copy`
   * `+ cq:childEditConfig (cq:EditConfig) = cq:EditConfig copy`
   * `+ cq:htmlTag (nt:base) = nt:unstructured copy`
   * `+ icon.png (nt:file) copy`
   * `+ thumbnail.png (nt:file) copy`
   * `- allowedParents (string) multiple`
   * `- allowedChildren (string) multiple`
   * `+ virtual (nt:base) = sling:Folder copy`
   * `- componentGroup (string)`
   * `+ cq:infoProviders (nt:base) = nt:unstructured copy`

### cq:ComponentMixin {#cq-componentmixin}

**Beschreibung**

Definiert eine CQ-Komponente als Mixintyp.

**Definition**

`[cq:ComponentMixin] > cq:Component mixin`

### cq:EditConfig {#cq-editconfig}

**Beschreibung**

Definiert die Konfiguration für „EditBar“.

* `@prop cq:dialogMode` - Modus des Dialogs:
   * `floating` – für einen normales, unverankertes Dialogfeld
   * `inline` - Inline-Bearbeitung
   * `auto` – automatische Erkennung (abhängig vom verfügbaren Platz)
* `@node cq:inplaceEditing` - Einrichtung der Bearbeitungskonfiguration für diese Komponente.
* `@prop cq:layout`- Layout der Bearbeitungsleiste:
   * `editbar` - Bearbeitungsleiste
   * `rollover` - Rollover-Rahmen
   * `auto` - automatische Erkennung
* `@node cq:formParameters`- Zusätzliche Parameter, die dem Dialogfeld hinzugefügt werden sollen.
* `@prop cq:actions`- Liste von Aktionen (Bearbeiten von Schaltflächen in der Leiste oder Menüelemente).
* `@node cq:actionConfigs` - Widget-Konfigurationen für Bearbeitungsleiste oder Menüelemente.
* `@prop cq:emptyText` - Text, der angezeigt werden soll, wenn kein sichtbarer Inhalt vorhanden ist.
* `@node cq:dropTargets` - Sammlung von  `{@link cq:DropTargetConfig}` Knoten.

**Definition**

* `[cq:EditConfig] > nt:unstructured, nt:hierarchyNode orderable`
   * `- cq:dialogMode (string) < 'auto', 'floating', 'inline'`
   * `- cq:layout (string) < 'editbar', 'rollover', 'auto' + cq:formParameters (nt:base) = nt:unstructured`
   * `- cq:actions (string) multiple`
   * `+ cq:actionConfigs (nt:base) = nt:unstructured`
   * `- cq:emptyText (string)`
   * `+ cq:dropTargets (nt:base) = nt:unstructured`
   * `+ cq:listeners (nt:base) = cq:EditListenersConfig`

### cq:DropTargetConfig {#cq-droptargetconfig}

**Beschreibung**

Konfiguriert ein Ablageziel einer Komponente. Der Name dieses Knotens wird als ID für per Drag-and-Drop zu verschiebende Komponenten verwendet.

* `@prop accept` - Liste von Mime-Typen, die von dieser Dropdown-Zielgruppe akzeptiert werden; z. B.  `["image/*"]`
* `@prop groups` - Liste von Drag &amp; Drop-Gruppen, die eine Quelle akzeptieren.
* `@prop propertyName` - Name der Eigenschaft, die zum Speichern des Verweises verwendet wird.

**Definition**

* `[cq:DropTargetConfig] > nt:unstructured orderable`
   * `- accept (string) multiple`
   * `- groups (string) multiple`
   * `- propertyName (string)`
   * `+ parameters (nt:base) = nt:unstructured`

### cq:VirtualComponent {#cq-virtualcomponent}

**Beschreibung**

Definiert eine virtuelle CQ-Komponente. Diese werden derzeit nur für den neuen Assistenten zum Verschieben von Komponenten per Drag-and-Drop verwendet.

* `@prop jcr:title` - Titel dieser Komponente.
* `@prop jcr:description` - Beschreibung dieser Komponente.
* `@node cq:editConfig` - Bearbeiten Sie die Konfiguration, die die Parameter für die Bearbeitungsleiste definiert.
* `@node cq:childEditConfig`- Bearbeiten Sie die Konfiguration, die von untergeordneten Komponenten geerbt wird.
* `@node icon.png` - Eine Datei, die ein charakteristisches Symbol enthält.
* `@node thumbnail.png` - Eine Datei, die ein charakteristisches Miniaturbild enthält.
* `@prop allowedParents` - Regelmäßige Ausdruck zur Bestimmung des Pfads bzw. der Pfade von Komponenten, die als übergeordnete Komponenten zulässig sind.
* `@prop allowedChildren` - Regelmäßige Ausdruck-Muster zur Bestimmung von Pfaden für Komponenten, die als untergeordnete Komponenten zulässig sind.
* `@prop componentGroup` - Name der Komponentengruppe für die Komponente per Drag &amp; Drop.

**Definition**

`[cq:VirtualComponent] > nt:folder, mix:title`
`- * (undefined)`
`- * (undefined) multiple`
`+ * (nt:base) = nt:base multiple version`
`+ cq:editConfig (cq:EditConfig) = cq:EditConfig copy`
`+ icon.png (nt:file) copy`
`+ thumbnail.png (nt:file) copy`
`- allowedParents (string) multiple`
`- allowedChildren (string) multiple`
`- componentGroup (string)`

### cq:EditListenersConfig {#cq-editlistenersconfig}

**Beschreibung**

Definiert die (clientseitigen) Listener, die bei einem Bearbeitungsereignis ausgeführt werden sollen. Die Werte müssen entweder auf eine gültige clientseitige Listener-Funktion verweisen oder eine vordefinierte Verknüpfung enthalten:

* `REFRESH_PAGE`
* `REFRESH_SELF`
* `REFRESH_PARENT`

* `@prop aftercreate` - Wird ausgelöst, nachdem eine Komponente erstellt wurde.
* `@prop afteredit` - Wird ausgelöst, nachdem eine Komponente bearbeitet (geändert) wurde.
* `@prop afterdelete` - Wird ausgelöst, nachdem eine Komponente gelöscht wurde.
* `@prop afterinsert` - Wird nach Hinzufügen einer Komponente zum Container ausgelöst.
* `@prop afterremove` - Wird nach Entfernen einer Komponente aus dem Container ausgelöst.
* `@prop aftermove` - Wird nach Verschieben von Komponenten in den Container ausgelöst.

**Definition**

* `[cq:EditListenersConfig]`
   * `- &ast; (undefined)`
   * `- &ast; (undefined) multiple`
   * `+ &ast; (nt:base) = nt:base multiple version`
   * `- aftercreate (string)`
   * `- afteredit (string)`
   * `- afterdelete (string)`
   * `- afterinsert (string)`
   * `- afterremove (string)`
   * `- aftermove (string)`

## DAM {#dam}

### dam:AssetContent {#dam-assetcontent}

**Beschreibung**

Inhalt eines DAM-Assets

**Definition**

* `[dam:AssetContent] > nt:unstructured`
   * `+ metadata (nt:unstructured)`
   * `+ renditions (nt:folder)`

### dam:Asset {#dam-asset}

**Beschreibung**

DAM-Asset.

**Definition**

`[dam:Asset] > nt:hierarchyNode`
`+ jcr:content (dam:AssetContent) = dam:AssetContent copy primary`
`+ * (nt:base) = nt:base version`

### dam:Thumbnail {#dam-thumbnail}

**Beschreibung**

Miniaturansicht zur Darstellung eines DAM-Assets

**Definition**

* `[dam:Thumbnails]`
   * `mixin`
   * `+ dam:thumbnails (nt:folder)`

## Bereitstellungs-Container-Liste {#delivery-container-list}

### cq:containerList {#cq-containerlist}

**Beschreibung**

Container-Liste

**Definition**

* `[cq:containerList]`
   * `mixin`

## Bereitstellungsseite {#delivery-page}

### cq:Cq4PageAttributes {#cq-cq-pageattributes}

**Beschreibung**

`cq:attributes` ist der Knotentyp für die ContentBus-Versionstags. Dieser Knoten weist nur eine Reihe von Eigenschaften auf, von denen drei vordefiniert sind: „created“, „csd“ und „timestampe“.

* `@prop created (long) mandatory copy` - Zeitstempel der Erstellung der Versionsinformationen, im Allgemeinen der Zeitpunkt des Checkins der vorherigen Version oder der Zeit der Seitenerstellung.
* `@prop csd (string) mandatory copy` - csd-Standardattribut, Kopie der Eigenschaft cq:csd des Seitenknotens
* `@prop timestamp (long) mandatory copy` - Zeitstempel der Änderung der letzten Version, im Allgemeinen Checkin-Zeit.
* `@prop * (string) copy` - Zusätzliche Attribute, Version mit dem übergeordneten Knoten.

**Definition**

* `[cq:Cq4PageAttributes] > nt:base`
   * `- created (long) mandatory copy`
   * `- csd (string) mandatory copy`
   * `- timestamp (long) mandatory copy`
   * `- &ast; (string) copy`

### cq:Cq4ContentPage {#cq-cq-contentpage}

**Beschreibung**

Der Knotentyp `cq:contentPage` enthält die Eigenschaft und die Definitionen des untergeordneten Knotens für ContentBus-Inhaltsseiten. Nur wenn dieser Mixin-Typ einem Knoten des Typs `cq:page` hinzugefügt wird, wird ein Knoten zu einer ContentBus-Inhaltsseite.

Die Elemente in einem `cq:Cq4ContentPage` sind:

* `@prop cq:csd` - Die ContentBus-CSD der Seite.
* `@node cq:content` - Der Inhalt der Seite. Dieser untergeordnete Knoten ist nicht vorhanden, wenn der Seitenknoten keinen Inhalt aufweist oder gelöscht wurde.
* `@node cq:attributes` - Die Liste von Seitenattributen, die früher als Version-Tags bezeichnet wurden. Dieser Knoten ist für den Typ „cq:contentPage“ obligatorisch. Der Knoten &quot;attribute&quot;ist versioniert, wenn die Seite eine Node ist, die versioniert ist.

**Definition**

* `[cq:Cq4ContentPage]`
   * `- cq:csd (string) mandatory copy`
   * `+ cq:attributes (cq:Cq4PageAttributes)`

## Importtool {#importer}

### cq:PollConfig {#cq-pollconfig}

**Beschreibung**

Abrufkonfiguration

* `@prop source (String) mandatory` - Datenquelle-URI, dies erforderlich und darf nicht leer sein
* `@prop target (String)` - Der Zielspeicherort, an dem die aus der Datenquelle abgerufenen Daten gespeichert werden. Dieser ist optional und standardmäßig auf den Knoten „cq:PollConfig“ festgelegt.
* `@prop interval (Long)` - Das Intervall in Sekunden, in dem neue oder aktualisierte Daten aus der Datenquelle abgerufen werden. Dies ist optional und standardmäßig auf 30 Minuten (1800 Sekunden) festgelegt.
* [Erstellen benutzerdefinierter Datenimportdienste für Adobe Experience Manager](https://helpx.adobe.com/de/experience-manager/using/polling.html)

**Definition**

* `[cq:PollConfig]
   * `mixin`
   * `- source (String) mandatory`
   * `- target (String)`
   * `- interval (Long)`

### cq:PollConfigFolder {#cq-pollconfigfolder}

**Beschreibung**

Praktischer primärer Knotentyp zum einfachen Erstellen von Abfragekonfigurationsknoten

**Definition**

`[cq:PollConfigFolder] > sling:Folder, cq:PollConfig`

## Standort {#location}

### cq:GeoLocation {#cq-geolocation-1}

**Beschreibung**

Ein Mixin, das eine geografische Position in Dezimalgraden (DD) definiert

* `@prop latitude` - Breitengrad, als Dublette mit Dezimalgraden kodiert.
* `@prop longitude` - Längengrad als Dublette mit Dezimalgraden kodiert.

**Definition**

* `[cq:GeoLocation]
   * `mixin`
   * `- latitude (double)`
   * `- longitude (double)`

## Mailer {#mailer}

### cq:mailerMessage {#cq-mailermessage}

**Beschreibung**

MailerService-Knotentypen. Der Mailer verwendet Knoten mit diesem Mixin als Stammknoten von Nachrichtendefinitionen.

**Definition**

* `[cq:mailerMessage]`
   * `mixin`
   * `- messageStatus (string)`
   * `= 'new'`
   * `mandatory autocreated`

## MSM {#msm}

### cq:LiveRelationship {#cq-liverelationship}

**Beschreibung**

Definiert ein LiveRelationship-Mixin. Ein primärer Quell-(Controlling-)Knoten und ein Live Copy-(Kontroll-)Knoten können über eine LiveRelationship virtuell verknüpft werden.

**Definition**

* `[cq:LiveRelationship] mixin`
   * `- cq:lastRolledout (date)`
   * `- cq:lastRolledoutBy (string)`
   * `- cq:sourceUUID (string)`

### cq:LiveSync {#cq-livesync}

**Beschreibung**

Definiert ein LiveSync-Mixin. Wenn ein Knoten in eine LiveRelationship mit einem primären Quellknoten (Controlling) und einem Live Copy-Knoten (gesteuert) eingebunden ist, wird er als LiveSync markiert.

* `@prop cq:master` - Pfad der primären Quelle (Steuerung) der LiveRelationship.
* `@prop cq:isDeep` - Definiert, ob die Beziehung für Kinder verfügbar ist.
* `@prop cq:syncTrigger` - Definiert, wann die Synchronisierung ausgelöst wird.
* `@node * LiveSyncAction` - Aktionen, die synchron ausgeführt werden

**Definition**

`[cq:LiveSync] > cq:LiveRelationship mixin orderable`
`+ * (cq:LiveSyncAction) = cq:LiveSyncAction`
`+ cq:LiveSyncConfig (nt:base) = cq:LiveSyncConfig`

### cq:LiveSyncCancelled {#cq-livesynccancelled}

**Beschreibung**

Definiert ein LiveSyncCancelled-Mixin. Abbrechen des LiveSync-Verhaltens eines Live Copy-(kontrollierten) Knotens, der aufgrund eines seiner Eltern in eine LiveRelationship einbezogen werden kann.

* `@prop cq:isCancelledForChildren` - Definiert, ob ein LiveSync abgebrochen wird; auch für Kinder.

**Definition**

* `[cq:LiveSyncCancelled] > cq:LiveRelationship mixin`
   * `- cq:isCancelledForChildren (boolean)`

### cq:LiveSyncAction {#cq-livesyncaction}

**Beschreibung**

Definiert eine mit einer LiveSync verbundene LiveSyncAction.

* `@prop name` - Aktionsname
* `@prop value` - Aktionswert

**Definition**

* `[cq:LiveSyncAction] > nt:unstructured`

### cq:LiveSyncConfig {#cq-livesyncconfig}

**Beschreibung**

LiveSync-Konfiguration

**Definition**

* `[cq:LiveSyncConfig]`
   * `- cq:master (string) mandatory`
   * `- cq:isDeep (boolean)`
   * `- cq:trigger (string) /** deprecated **/`

Für AEM 5.4 fügen Sie am Ende der Liste Folgendes hinzu:

* `- cq:rolloutConfigs (string) multiple /** deprecated **/`

### cq:BlueprintAction {#cq-blueprintaction}

**Beschreibung**

Blueprint-Aktion

**Definition**

* `[cq:BlueprintAction] > nt:unstructured`

## Plattform {#platform}

### cq:Console {#cq-console}

**Beschreibung**

Definiert den Knotentyp eines Konsolenknotens.

**Definition**

* `[cq:Console] > sling:VanityPath, mix:title`
   * `mixin`

## Replikation {#replication}

### cq:ReplicationStatus {#cq-replicationstatus}

**Beschreibung**

Definiert das Replikationsstatusinformations-Mixin.

* `@prop cq:lastPublished`- Das Datum, an dem die Seite zuletzt veröffentlicht wurde (nicht mehr verwendet).
* `@prop cq:lastPublishedBy`- Der Benutzer, der die Seite zuletzt veröffentlicht hat (nicht mehr verwendet).
* `@prop cq:lastReplicated` - Das Datum, an dem die Seite zuletzt repliziert wurde.
* `@prop cq:lastReplicatedBy` - Der Benutzer, der die Seite zuletzt repliziert hat.
* `@prop cq:lastReplicationAction` - Replizierungsaktion: aktivieren oder deaktivieren.
* `@prop cq:lastReplicationStatus` - Der Replikationsstatus (nicht mehr verwendet).

**Definition**

* `[cq:ReplicationStatus]
   * `mixin`
   * `- cq:lastPublished (date) ignore`
   * `- cq:lastPublishedBy (string) ignore`
   * `- cq:lastReplicated (date) ignore`
   * `- cq:lastReplicatedBy (string) ignore`
   * `- cq:lastReplicationAction (string) ignore`
   * `- cq:lastReplicationStatus (string) ignore`

## Sicherheit {#security}

### cq:ApplicationPrivilege {#cq-applicationprivilege}

**Beschreibung**

Definiert eine Anwendungsberechtigung.

**Definition**

* `[cq:ApplicationPrivilege] mixin`

### cq:PrivilegeAcl {#cq-privilegeacl}

**Beschreibung**

Definiert eine Anwendungsberechtigungs-ACL.

* `@prop cq:isPathDependent`
* `@node * ACEs`

**Definition**

* `[cq:PrivilegeAcl] > cq:ApplicationPrivilege mixin orderable`
   * `- cq:isPathDependent (boolean)`
   * `+ * (cq:PrivilegeAce) = cq:PrivilegeAce`

### cq:PrivilegeAce {#cq-privilegeace}

**Beschreibung**

Definiert eine Anwendungsberechtigungs-ACE.

* `@prop path`
* `@prop deny`

**Definition**

* `[cq:PrivilegeAce]`
   * `- path mandatory`
   * `- deny (boolean)`

### cq:ApplicationPrivilege {#cq-applicationprivilege-1}

**Beschreibung**

Definiert eine Anwendungsberechtigung.

**Definition**

* `[cq:ApplicationPrivilege] mixin`

### cq:PrivilegeAcl {#cq-privilegeacl-1}

**Beschreibung**

Definiert eine Anwendungsberechtigungs-ACL.

* `@prop cq:isPathDependent`
* `@node * ACEs`

**Definition**

* `[cq:PrivilegeAcl] > cq:ApplicationPrivilege mixin orderable`
   * `- cq:isPathDependent (boolean)`
   * `+ * (cq:PrivilegeAce) = cq:PrivilegeAce`

### cq:PrivilegeAce {#cq-privilegeace-1}

**Beschreibung**

Definiert eine Anwendungsberechtigungs-ACE.

* `@prop path`
* `@prop deny`

**Definition**

* `[cq:PrivilegeAce]`
   * `- path mandatory`
   * `- deny (boolean)`

## Site-Importtool {#site-importer}

### cq:ComponentExtractorSource {#cq-componentextractorsource}

**Beschreibung**

Definiert einen Mixintyp, der Dateien markiert, die mit dem Komponenten-Extractor geöffnet werden können.

**Definition**

`[cq:ComponentExtractorSource] mixin`

## Tagging {#tagging}

### cq:Tag {#cq-tag}

**Beschreibung**

Definiert ein einzelnes Tag, kann aber auch Tags enthalten, wodurch eine Taxonomie erstellt wird.

**Definition**

* `[cq:Tag] > nt:base, mix:title`
   * `- sling:resourceType (String)`
   * `- * (undefined) multiple`
   * `- * (undefined)`
   * `+ * (nt:base) = cq:Tag version`

### cq:Taggable {#cq-taggable}

**Beschreibung**

Abstraktes grundlegendes-Mixin für mit Tags zu versehende Inhalte

* `@node cq:tags`

**Definition**

* `[cq:Taggable]`
   * `- cq:tags (string) multiple`

### cq:OwnerTaggable {#cq-ownertaggable}

**Beschreibung**

Nur Autoren/Eigentümer dürfen den Inhalt mit Tags versehen (moderiertes/verwaltetes Tagging).

**Definition**

* `[cq:OwnerTaggable] > cq:Taggable`

### cq:UserTaggable {#cq-usertaggable}

**Beschreibung**

Jeder Benutzer/jede öffentliche Website kann den Inhalt (im Web 2.0-Stil) mit Tags versehen, der innerhalb cq:userContent verwendet wird.

**Definition**

* `[cq:UserTaggable] > cq:Taggable`
   * `mixin`

### cq:AllowsUserContent {#cq-allowsusercontent}

**Beschreibung**

Fügt eine `cq:userContent`-Unterknoten hinzu, die von Benutzern geändert werden kann. Jeder Benutzer hat seine eigene Unterknoten `cq:userContent/<userid>`, die normalerweise das mixin `cq:UserTaggable` hat.

**Definition**

* `[cq:AllowsUserContent]`
   * `mixin`
   * `+ cq:userContent (nt:unstructured)`

Erweiterte Variante, genauer definiert die Struktur `cq:userContent`

* `[cq:AllowsUserContent]`
   * `mixin`
   * `+ cq:userContent (cq:UserContent)`

### cq:UserContent {#cq-usercontent}

**Beschreibung**

Kann von Benutzern geändert werden.

**Definition**

* `[cq:UserContent] > nt:unstructured`
   * `// userids`
   * `+ * (cq:UserData)`
   * `// other content`
   * `+ * (nt:base)`

### cq:UserData {#cq-userdata}

**Beschreibung**

Benutzerdaten

**Definition**

* `[cq:UserData] > nt:unstructured, cq:UserTaggable`

## Widgets {#widgets}

### cq:ClientLibraryFolder {#cq-clientlibraryfolder}

**Beschreibung**

Client-Bibliotheksordner

**Definition**

* `[cq:ClientLibraryFolder] > sling:Folder`
   * `- categories (string) multiple`
   * `- dependencies (string) multiple`

### cq:Widget {#cq-widget}

**Beschreibung**

Widget

**Definition**

* `[cq:Widget] > nt:unstructured orderable`
   * `- xtype (string)`
   * `- name (string)`
   * `- title (string)`
   * `+ items (nt:base) = cq:WidgetCollection copy`

### cq:WidgetCollection {#cq-widgetcollection}

**Beschreibung**

Widget-Sammlung

**Definition**

* `[cq:WidgetCollection] > nt:unstructured`
   * `orderable`
   * `+ * (cq:Widget) = cq:Widget copy`

### cq:Dialog {#cq-dialog}

**Beschreibung**

Dialogfeld

**Definition**

* `[cq:Dialog] > cq:Widget orderable`

### cq:Panel {#cq-panel}

**Beschreibung**

Fenster

**Definition**

`[cq:Panel] > cq:Widget orderable`

### cq:TabPanel {#cq-tabpanel}

**Beschreibung**

Registerkartenbedienfeld

**Definition**

* s[cq:TabPanel] > cq:Panel orderable&quot;
   * `- activeTab (long)`

### cq:Field {#cq-field}

**Beschreibung**

Feld

**Definition**

* `[cq:Field] > cq:Widget orderable`
   * `- fieldLabel (string)`
   * `- value (string)`
   * `- ignoreData (boolean)`

## Wiki {#wiki}

### wiki:Topic {#wiki-topic}

**Beschreibung**

Wiki-Thema

**Definition**

* `[wiki:Topic] > nt:unstructured, nt:hierarchyNode, mix:versionable, mix:lockable`
   * `+ * (wiki:Topic) version`
   * `+ wiki:attachments (nt:folder) = nt:folder version`
   * `+ wiki:properties (wiki:Properties) = wiki:Properties copy`
   * `- wiki:text (string) mandatory primary`
   * `- wiki:lastModified (date) mandatory`
   * `- wiki:lastModifiedBy (string) mandatory`
   * `- wiki:topicName`
   * `- wiki:topicTitle`
   * `- wiki:lockedBy`
   * `- wiki:logMessage (string)`
   * `- wiki:quietSave (boolean)`

### wiki:User {#wiki-user}

**Beschreibung**

Wiki-Benutzer

**Definition**

* `[wiki:User] mixin`
   * `- wiki:subscriptions (string) multiple`

### wiki:Properties {#wiki-properties}

**Beschreibung**

Wiki-Eigenschaften

**Definition**

* `[wiki:Properties]`
   * `- wiki:isGlobal (boolean)`
   * `- * (undefined)`

## Workflow {#workflow}

### cq:Workflow {#cq-workflow}

**Beschreibung**

Stellt eine Workflow-Instanz dar.

**Definition**

* `[cq:Workflow] > nt:base, mix:referenceable`
   * `- modelId (String)`
   * `- modelVersion (String)`
   * `- startTime (Date)`
   * `- endTime (Date)`
   * `- initiator (String)`
   * `- &ast; (undefined)`
   * `- &ast; (undefined) multiple`
   * `- sling:resourceType (String) = "cq/workflow/components/instance" mandatory autocreated`
   * `+ workflowStack (nt:unstructured)`
   * `+ wait (nt:unstructured)`
   * `+ orTab (nt:unstructured)`
   * `+ data (cq:WorkflowData)`
   * `+ history (nt:unstructured)`
   * `+ metaData (nt:unstructured)`
   * `+ workItems (nt:unstructured)`

### cq:WorkItem {#cq-workitem}

**Beschreibung**

Arbeitselement

**Definition**

* `[cq:WorkItem]`
   * `- assignee (String)`
   * `- workflowId (String)`
   * `- nodeId (String)`
   * `- startTime (Date)`
   * `- endTime (Date)`
   * `- dueTime (Date)`
   * `- sling:resourceType (String) = "cq/workflow/components/workitem" mandatory autocreated`
   * `+ metaData (nt:unstructured)`

### cq:Payload {#cq-payload}

**Beschreibung**

Nutzlast

**Definition**

* `[cq:Payload]`
   * `- path (Path)`
   * `- uuid (String)`
   * `- jcr:url (String)`
   * `- binary (Binary)`
   * `- javaObject (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`

### cq:WorkflowData {#cq-workflowdata}

**Beschreibung**

Workflow-Daten

**Definition**

* `[cq:WorkflowData]`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ payload (cq:Payload)`
   * `+ metaData (nt:unstructured) copy`

### cq:WorkflowModel {#cq-workflowmodel}

**Beschreibung**

Automatische Zuweisung der Workflow-Konfiguration. Die Konfiguration folgt der folgenden Struktur:
* `workflows`
   * `+ name1`
      * `- cq:path`
      * `- cq:workflowName`
   * `+ workflows (nt:base)`

**Definition**

* `[cq:WorkflowModel] > nt:base, mix:versionable`
   * `orderable`
   * `- title (String)`
   * `- description (String)`
   * `- sling:resourceType (String) = "cq/workflow/components/model" mandatory autocreated`
   * `+ nodes (nt:unstructured)`
      * `copy`
   * `+ transitions (nt:unstructured)`
      * `copy`
   * `+ metaData (nt:unstructured)`
      * `copy`

### cq:WorkflowNode {#cq-workflownode}

**Beschreibung**

Workflow-Knoten

**Definition**

* `[cq:WorkflowNode] orderable`
   * `- title (String)`
   * `- description (String)`
   * `- maxIdleTime (long)`
   * `- type (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`
   * `+ metaData (nt:unstructured)`
      * `copy`
   * `+ timeoutConfiguration (nt:unstructured)`
      * `copy`

### cq:WorkflowTransition {#cq-workflowtransition}

**Beschreibung**

Workflow-Transition

**Definition**

* `[cq:WorkflowTransition] orderable`
   * `- from (String)`
   * `- to (String)`
   * `- rule (String)`
   * `+ metaData (nt:unstructured)`
      * `copy`

### cq:OrTab {#cq-ortab}

**Beschreibung**

Oder, Registerkarte

**Definition**

* `[cq:OrTab]`
   * `- workflowId (String) // not compulsory as this node will already be attached to the workflow node`
   * `- nodeId (String)`

### cq:Wait {#cq-wait}

**Beschreibung**

Warten

**Definition**

* `[cq:Wait]`
   * `- workflowId (String) // not compulsory as this node will be already attached to the workflow node`
   * `- destNodeId (String)`
   * `- fromNodeId (String)`

### cq:WorkflowStack {#cq-workflowstack}

**Beschreibung**

Workflow-Stapel

**Definition**

* `[cq:WorkflowStack]`
   * `- containeeInstanceId (String)`
   * `- parentInstanceId (String)`
   * `- nodeId (String)`

### cq:ProcessStack {#cq-processstack}

**Beschreibung**

Prozessstapel

**Definition**

* `[cq:ProcessStack]`
   * `- workflowId (String) // not compulsory as this node will be already attached to the workflow node`
   * `- containerWorkflowModelId (String)`
   * `- containerWorkflowNodeId`
   * `- containerWorkflowEndNodeId // still needed (if name already defines that id)`

### cq:WorkflowLauncher {#cq-workflowlauncher}

**Beschreibung**

Workflow-Starter

**Definition**

* `[cq:WorkflowLauncher]`
   * `- nodetype (String)`
   * `- glob (String)`
   * `- eventType (Long)`
   * `- description (String)`
   * `- condition (String)`
   * `- workflow (String)`
   * `- * (undefined)`
   * `- * (undefined) multiple`
