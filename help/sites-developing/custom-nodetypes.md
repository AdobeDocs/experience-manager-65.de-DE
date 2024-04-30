---
title: Benutzerdefinierte Knotentypen
description: Adobe Experience Manager (AEM) basiert auf Sling und verwendet ein JCR-Repository mit Knotentypen, die von beiden angeboten werden, aber AEM bietet auch eine Reihe von benutzerdefinierten Knotentypen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: bfd50aa9-579e-47d5-997d-ec764c782497
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1848'
ht-degree: 100%

---

# Benutzerdefinierte Knotentypen{#custom-node-types}

Da Adobe Experience Manager (AEM) auf Sling basiert und ein JCR-Repository verwendet, sind von beiden bereitgestellte Knotentypen für die Verwendung verfügbar:

* [JCR-Knotentypen](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/3_Repository_Model.html#3.1.7-Node-Types)
* [Sling-Knotentypen](https://cwiki.apache.org/confluence/display/SLING/Sling+Node+Types)

Zusätzlich zu diesen Knotentypen stellt AEM eine Reihe von benutzerdefinierten Knotentypen bereit.

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

Definiert den Knotentyp eines `commentattachment`-Knotens

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

* `@prop latitude` - Breitengrad, doppelt kodiert mit Dezimalgraden
* `@prop longitude` - Längengrad, doppelt kodiert mit Dezimalgraden

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

* `@node jcr:content` - Primärer Inhalt der Seite.

**Definition**

* `[cq:Page] > nt:hierarchyNode orderable`
   * `+ jcr:content (nt:base) = nt:unstructured copy primary`
   * `+ * (nt:base) = nt:base version`

### cq:PseudoPage {#cq-pseudopage}

**Beschreibung**

Definiert einen Mixintyp, der Knoten als Pseudoseiten markiert. Das heißt, diese können zur Unterstützung der Seiten- und WCM-Bearbeitung angepasst werden.

**Definition**

* `[cq:PseudoPage] mixin`

### cq:PageContent {#cq-pagecontent}

**Beschreibung**

Definiert den Standardknoten für den Seiteninhalt mit den von WCM verwendeten Mindesteigenschaften.

* `@prop jcr:title` - Titel der Seite.
* `@prop jcr:description` - Beschreibung der Seite.
* `@prop cq:template` - Pfad zur Vorlage, mit der die Seite erstellt wurde.
* `@prop cq:allowedTemplates` – Liste der regulären Ausdrücke, die verwendet werden, um die Pfade zur zulässigen Vorlage zu bestimmen.
* `@prop pageTitle` – Titel, der im `<title>`-Tag angezeigt wird.
* `@prop navTitle` – Titel, der in der Navigation verwendet wird.
* `@prop hideInNav` - Gibt an, ob die Seite in der Navigation ausgeblendet werden soll.
* `@prop onTime` - Zeitpunkt, zu dem die Seite gültig wird.
* `@prop offTime` - Zeitpunkt, zu dem die Seite ungültig wird.
* `@prop cq:lastModified` - Datum der letzten Änderung der Seite (oder ihrer Absätze).
* `@prop cq:lastModifiedBy` - Letzter Benutzer, der die Seite (oder ihre Absätze) geändert hat.
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
* `@node thumbnail.png` - Eine Datei, die eine charakteristische Miniaturansicht enthält.
* `@node workflows` - Automatische Zuweisung der Workflow-Konfiguration. Die Konfiguration folgt der nachstehenden Struktur:
   * `+ workflows`
      * `+ name1`
         * `- cq:path`
            * `- cq:workflowName`
* `@prop allowedParents` – Muster regulärer Ausdrücke, um die Pfade zu Vorlagen zu bestimmen, die als übergeordnete Vorlagen zulässig sind.
* `@prop allowedChildren` – Muster regulärer Ausdrücke, um die Pfade zu Vorlagen zu bestimmen, die als untergeordnete Vorlagen zulässig sind.
* `@prop ranking` - Position innerhalb der Liste der Vorlagen im Dialogfeld „Seite erstellen“.

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
* `@node dialog` - Primärer Dialog.
* `@prop dialogPath` - Pfad zum primären Dialogfeld (Alternative zum Dialogfeld).
* `@node design_dialog` - Dialogfeld „Design“.
* `@prop cq:cellName` - Name der Designzellle.
* `@prop cq:isContainer` – Gibt an, ob es sich um eine Container-Komponente handelt. Damit wird die Verwendung der Zellnamen der untergeordneten Komponenten anstelle von Pfadnamen erzwungen. Beispielsweise ist die `parsys`-Komponente eine Container-Komponente. Wenn dieser Wert nicht definiert ist, wird überprüft, ob eine `cq:childEditConfig` vorliegt.
* `@prop cq:noDecoration` - Wenn der Wert auf „true“ festgelegt ist, werden keine `div`-Decoration-Tags beim Einbinden der Komponente gesetzt.
* `@node cq:editConfig` - Die Konfiguration, die die Parameter für die Bearbeitungsleiste definiert.
* `@node cq:childEditConfig` - Die Bearbeitungskonfiguration, die an untergeordnete Komponenten vererbt wird.
* `@node cq:htmlTag` - Definiert zusätzliche Tag-Attribute, die dem „einschließenden“ `div`-Tag beim Einbinden der Komponente hinzugefügt werden.
* `@node icon.png` - Eine Datei, die ein charakteristisches Symbol enthält.
* `@node thumbnail.png` - Eine Datei, die eine charakteristische Miniaturansicht enthält.
* `@prop allowedParents` – Muster regulärer Ausdrücke, um die Pfade von Komponenten zu bestimmen, die als übergeordnete Komponenten zulässig sind.
* `@prop allowedChildren` – Muster regulärer Ausdrücke, um die Pfade von Komponenten zu bestimmen, die als untergeordnete Komponenten zulässig sind.
* `@node virtual` - Enthält Unterknoten, die virtuelle Komponenten widerspiegeln, welche zum Verschieben der Komponenten per Drag-and-Drop verwendet werden.
* `@prop componentGroup` - Name der Komponentengruppe, der zum Verschieben der Komponenten per Drag-and-Drop verwendet wird.
* `@node cq:infoProviders` - Enthält Unterknoten, von denen jeder eine Eigenschaft `className` aufweist, die auf einen `PageInfoProvider` verweisen.

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

* `@prop cq:dialogMode` - Modus des Dialogfelds:
   * `floating` – für einen normales, unverankertes Dialogfeld
   * `inline` – Inline-Bearbeitung
   * `auto` – automatische Erkennung (abhängig vom verfügbaren Platz)
* `@node cq:inplaceEditing` - Konfiguration für die Bearbeitung im Kontext für diese Komponente.
* `@prop cq:layout` - Layout der Bearbeitungsleiste:
   * `editbar` - Bearbeitungsleiste
   * `rollover` – Rollover-Frame
   * `auto` – automatische Erkennung
* `@node cq:formParameters` - Zusätzliche Parameter zum Hinzufügen des Dialogfeldformulars.
* `@prop cq:actions` - Liste der Aktionen (Schaltflächen der Bearbeitungsleiste oder Menüelemente).
* `@node cq:actionConfigs` - Widget-Konfigurationen für Bearbeitungsleiste oder Menüelemente.
* `@prop cq:emptyText` - Text, der angezeigt werden soll, wenn kein visueller Inhalt vorhanden ist.
* `@node cq:dropTargets` - Sammlung von `{@link cq:DropTargetConfig}`-Knoten.

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

Konfiguriert ein Ablageziel einer Komponente.  Der Name dieses Knotens wird als ID für per Drag-and-Drop zu verschiebende Komponenten verwendet.

* `@prop accept` – Liste der MIME-Typen, die von diesem Ablageziel akzeptiert werden, beispielsweise `["image/*"]`
* `@prop groups` - Liste der Drag-and-Drop-Gruppen, die eine Quelle akzeptieren.
* `@prop propertyName` - Name der Eigenschaft, die zum Speichern des Verweises verwendet wird.

**Definition**

* `[cq:DropTargetConfig] > nt:unstructured orderable`
   * `- accept (string) multiple`
   * `- groups (string) multiple`
   * `- propertyName (string)`
   * `+ parameters (nt:base) = nt:unstructured`

### cq:VirtualComponent {#cq-virtualcomponent}

**Beschreibung**

Definiert eine virtuelle CQ-Komponente.  Wird derzeit nur für den neuen Assistenten zum Verschieben von Komponenten per Drag-and-Drop verwendet.

* `@prop jcr:title` - Titel dieser Komponente.
* `@prop jcr:description` - Beschreibung dieser Komponente.
* `@node cq:editConfig` - Die Bearbeitungskonfiguration, die die Parameter für die Bearbeitungsleiste definiert.
* `@node cq:childEditConfig` - Die Bearbeitungskonfiguration, die an untergeordnete Komponenten vererbt wird.
* `@node icon.png` - Eine Datei, die ein charakteristisches Symbol enthält.
* `@node thumbnail.png` - Eine Datei, die eine charakteristische Miniaturansicht enthält.
* `@prop allowedParents` – Muster regulärer Ausdrücke, um den Pfad bzw. die Pfade von Komponenten zu bestimmen, die als übergeordnete Komponenten zulässig sind.
* `@prop allowedChildren` – Muster regulärer Ausdrücke, um den Pfad bzw. die Pfade von Komponenten zu bestimmen, die als untergeordnete Komponenten zulässig sind.
* `@prop componentGroup` - Name der Komponentengruppe, der zum Verschieben der Komponenten per Drag-and-Drop verwendet wird.

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

Definiert die (Client-seitigen) Listener, die bei einem Bearbeitungsereignis ausgeführt werden sollen. Die Werte müssen entweder auf eine gültige Client-seitige Listener-Funktion verweisen oder eine vordefinierte Verknüpfung enthalten:

* `REFRESH_PAGE`
* `REFRESH_SELF`
* `REFRESH_PARENT`

* `@prop aftercreate` - Wird nach Erstellen einer Komponente ausgelöst.
* `@prop afteredit` - Wird nach Bearbeiten (Ändern) einer Komponente ausgelöst.
* `@prop afterdelete` - Wird nach Löschen einer Komponente ausgelöst.
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

Der Knotentyp `cq:attributes` ist für die ContentBus-Version-Tags. Dieser Knoten weist nur eine Reihe von Eigenschaften auf, von denen drei vordefiniert sind: „created“, „csd“ und „timestamp“.

* `@prop created (long) mandatory copy` - Zeitstempel der Erstellung der Versionsinformationen, in der Regel der Zeitpunkt des Eincheckens der Vorgängerversion oder der Seitenerstellung.
* `@prop csd (string) mandatory copy` - csd-Standardattribut, Kopie der Eigenschaft „cq:csd“ des Seitenknotens
* `@prop timestamp (long) mandatory copy` - Zeitstempel der letzten Versionsänderung, in der Regel die Eincheckzeit.
* `@prop * (string) copy` - Zusätzliche Attribute, die mit derselben Versionsangabe wie der übergeordnete Knoten versehen sind.

**Definition**

* `[cq:Cq4PageAttributes] > nt:base`
   * `- created (long) mandatory copy`
   * `- csd (string) mandatory copy`
   * `- timestamp (long) mandatory copy`
   * `- &ast; (string) copy`

### cq:Cq4ContentPage {#cq-cq-contentpage}

**Beschreibung**

Der Knotentyp `cq:contentPage` enthält die Eigenschaft und die Definitionen des untergeordneten Knotens für ContentBus-Inhaltsseiten. Nur wenn dieser Mixintyp zu einem Knoten vom Typ `cq:page` hinzugefügt wird, wird ein Knoten zu einer ContentBus-Inhaltsseite.

Die Elemente in einer `cq:Cq4ContentPage` sind:

* `@prop cq:csd` - Die ContentBus-CSD der Seite.
* `@node cq:content` - Der Inhalt der Seite. Dieser untergeordnete Knoten ist nicht vorhanden, wenn der Seitenknoten keinen Inhalt aufweist oder gelöscht wurde.
* `@node cq:attributes` - Die Liste der Seitenattribute, die zuvor als Versionstags bezeichnet wurden. Dieser Knoten ist für den Typ „cq:contentPage“ obligatorisch. Der Knoten „attributes“ wird mit Versionsangaben versehen, wenn der Seitenknoten Versionsangaben aufweist.

**Definition**

* `[cq:Cq4ContentPage]`
   * `- cq:csd (string) mandatory copy`
   * `+ cq:attributes (cq:Cq4PageAttributes)`

## Import-Tool {#importer}

### cq:PollConfig {#cq-pollconfig}

**Beschreibung**

Abrufkonfiguration

* `@prop source (String) mandatory` – Datenquellen-URI. Dieser ist erforderlich und darf nicht leer sein.
* `@prop target (String)` – Der Zielspeicherort, an dem die aus der Datenquelle abgerufenen Daten gespeichert werden. Dieser ist optional und standardmäßig auf den Knoten „cq:PollConfig“ festgelegt.
* `@prop interval (Long)` – Das Intervall in Sekunden, in dem neue oder aktualisierte Daten aus der Datenquelle abgerufen werden. Dies ist optional und standardmäßig auf 30 Minuten (1800 Sekunden) festgelegt.
* [Erstellen benutzerdefinierter Datenimportdienste für Adobe Experience Manager](https://helpx.adobe.com/experience-manager/using/polling.html)

**Definition**

* `[cq:PollConfig]`
   * `mixin`
   * `- source (String) mandatory`
   * `- target (String)`
   * `- interval (Long)`

### cq:PollConfigFolder {#cq-pollconfigfolder}

**Beschreibung**

Praktischer primärer Knotentyp zum einfachen Erstellen von Abfragekonfigurationsknoten

**Definition**

`[cq:PollConfigFolder] > sling:Folder, cq:PollConfig`

## Speicherort {#location}

### cq:GeoLocation {#cq-geolocation-1}

**Beschreibung**

Ein Mixin, das eine geografische Position in Dezimalgraden (DD) definiert

* `@prop latitude` - Breitengrad, doppelt kodiert mit Dezimalgraden.
* `@prop longitude` - Längengrad, doppelt kodiert mit Dezimalgraden.

**Definition**

* `[cq:GeoLocation]`
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

Definiert ein LiveRelationship-Mixin. Ein Primärquellen- (Kontroll-)Knoten und ein Live Copy-(gesteuerter) Knoten können über eine LiveRelationship virtuell verknüpft werden.

**Definition**

* `[cq:LiveRelationship] mixin`
   * `- cq:lastRolledout (date)`
   * `- cq:lastRolledoutBy (string)`
   * `- cq:sourceUUID (string)`

### cq:LiveSync {#cq-livesync}

**Beschreibung**

Definiert ein LiveSync-Mixin. Wenn ein Knoten in eine LiveRelationship mit einem Primärquellen- (Kontroll-)Knoten und einem Live Copy-(gesteuerten) Knoten involviert ist, wird er als LiveSync markiert.

* `@prop cq:master` - Pfad der Primärquelle (Kontrolle) der LiveRelationship.
* `@prop cq:isDeep` - Legt fest, ob die Beziehung für untergeordnete Knoten verfügbar ist.
* `@prop cq:syncTrigger` - Legt fest, wann die Synchronisierung ausgelöst wird.
* `@node * LiveSyncAction` - Aktionen, die bei der Synchronisierung ausgeführt werden sollen

**Definition**

`[cq:LiveSync] > cq:LiveRelationship mixin orderable`
`+ * (cq:LiveSyncAction) = cq:LiveSyncAction`
`+ cq:LiveSyncConfig (nt:base) = cq:LiveSyncConfig`

### cq:LiveSyncCancelled {#cq-livesynccancelled}

**Beschreibung**

Definiert ein LiveSyncCancelled-Mixin. Bricht die LiveSync eines Live Copy- gesteuerten Knotens ab, der sich in einer LiveRelationship mit einem übergeordneten Knoten befindet.

* `@prop cq:isCancelledForChildren` – Legt fest, ob eine LiveSync abgebrochen wird. Dies gilt auch für untergeordnete Knoten.

**Definition**

* `[cq:LiveSyncCancelled] > cq:LiveRelationship mixin`
   * `- cq:isCancelledForChildren (boolean)`

### cq:LiveSyncAction {#cq-livesyncaction}

**Beschreibung**

Definiert eine mit einer LiveSync verbundene LiveSyncAction.

* `@prop name` - Aktionsname
* `@prop value` - Wert der Aktion

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

Fügen Sie für AEM 5.4 Folgendes am Ende der Liste hinzu:

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

* `@prop cq:lastPublished` - Das Datum der letzten Veröffentlichung der Seite (nicht mehr verwendet).
* `@prop cq:lastPublishedBy` - Der Benutzer, der die Seite zuletzt veröffentlicht hat (nicht mehr verwendet).
* `@prop cq:lastReplicated` - Das Datum, an dem die Seite zuletzt repliziert wurde.
* `@prop cq:lastReplicatedBy` - Der Benutzer, der die Seite zuletzt repliziert hat.
* `@prop cq:lastReplicationAction` - Die Replikationsaktion: aktivieren oder deaktivieren.
* `@prop cq:lastReplicationStatus` - Der Replikationsstatus (nicht mehr verwendet).

**Definition**

* `[cq:ReplicationStatus]`
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

## Site-Import-Tool {#site-importer}

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

Fügt einen Unterkoten `cq:userContent`, der von Benutzern geändert werden kann. Jede Benutzerin bzw. jeder Benutzer hat einen eigenen Unterknoten `cq:userContent/<userid>`, der normalerweise über das Mixin `cq:UserTaggable` verfügt.

**Definition**

* `[cq:AllowsUserContent]`
   * `mixin`
   * `+ cq:userContent (nt:unstructured)`

Erweiterte Variante, die die `cq:userContent`-Baumstruktur genauer definiert

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

Bedienfeld

**Definition**

`[cq:Panel] > cq:Widget orderable`

### cq:TabPanel {#cq-tabpanel}

**Beschreibung**

Registerkarten-Bedienfeld

**Definition**

* `[cq:TabPanel]` > `cq:Panel orderable`
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

Payload

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

Automatische Zuweisung der Workflow-Konfiguration. Die Konfiguration folgt der nachstehenden Struktur:
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

Workflow-Übergang

**Definition**

* `[cq:WorkflowTransition] orderable`
   * `- from (String)`
   * `- to (String)`
   * `- rule (String)`
   * `+ metaData (nt:unstructured)`
      * `copy`

### cq:OrTab {#cq-ortab}

**Beschreibung**

Registerkarte „Oder“

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
