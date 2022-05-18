---
title: Prozessreferenz für Workflows
seo-title: Workflow Process Reference
description: Prozessreferenz für Workflows
seo-description: null
uuid: de367aa8-4580-4810-b665-2a7b521e36ca
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: dbdf981f-791b-4ff7-8ca8-039d0bdc9c92
exl-id: a9de8ec6-6948-4643-89c3-62d9b1f6293a
source-git-commit: cf3b739fd774bc860d9906b9884d22fd532fd5dd
workflow-type: tm+mt
source-wordcount: '1075'
ht-degree: 83%

---

# Prozessreferenz für Workflows{#workflow-process-reference}

AEM bietet verschiedene Prozessschritte für die Erstellung von Workflow-Modellen. Darüber hinaus können auch benutzerdefinierte Prozessschritte für Aufgaben hinzugefügt werden, die nicht von den integrierten Schritten abgedeckt werden (vergleiche [Erstellen von Workflow-Modellen](/help/sites-developing/workflows-models.md)).

## Prozessmerkmale {#process-characteristics}

Die folgenden Merkmale werden für jeden Prozessschritt beschrieben.

### Java-Klasse oder ECMA-Pfad {#java-class-or-ecma-path}

Prozessschritte werden entweder durch eine Java-Klasse oder ein ECMAScript definiert.

* Bei Java-Klassenprozessen wird der vollqualifizierte Klassenname angegeben.
* Bei ECMAScript-Prozessen wird der Pfad des Skripts angegeben.

### Nutzlast {#payload}

Die Nutzlast ist die Entität, auf die die Workflow-Instanz reagiert. Die Nutzlast wird implizit durch den Kontext ausgewählt, in dem eine Workflow-Instanz gestartet wird.

Wenn beispielsweise ein Workflow auf die AEM-Seite *P* angewendet wird, durchläuft *P* bei fortlaufendem Workflow die verschiedenen Schritte. Dabei wirkt sich jeder Schritt optional in irgendeiner Weise auf *P* aus.

Meistens besteht die Nutzlast aus einem JCR-Knoten im Repository (beispielsweise eine AEM-Seite oder ein AEM-Asset). Eine JCR-Knotennutzlast wird als Zeichenfolge übergeben, die entweder aus einem JCR-Pfad oder einer JCR-Kennung besteht (UUID). Manchmal ist die Nutzlast eine JCR-Eigenschaft (sie wird dann als JCR-Pfad übergeben), eine URL, ein Binärobjekt oder ein generisches Java-Objekt. Einzelne Prozessschritte, die auf die Nutzlast reagieren, erwarten in der Regel einen bestimmten Typ Nutzlast oder verhalten sich je nach Nutzlasttyp anders. Der erwartete Nutzlasttyp (falls vorhanden) wird für jeden der unten beschriebenen Prozesse angegeben.

### Argumente {#arguments}

Einige Workflow-Prozesse akzeptieren Argumente, die der Administrator beim Einrichten des Workflow-Schritts angibt.

Argumente werden als einzelne Zeichenfolge im Bereich **Eigenschaften** des Workflow-Editors in der Eigenschaft **Prozess-Argumente** angegeben. Das Format der Argumentzeichenfolge wird für jeden unten beschriebenen Prozess in einfacher EBNF-Grammatik angegeben. Das folgende Beispiel zeigt, dass die Argumentzeichenfolge aus einem oder mehreren durch Kommas getrennten Paaren besteht, wobei jedes Paar aus einem Namen (der eine Zeichenfolge ist) und einem Wert besteht, getrennt durch einen Doppelpunkt:

```
    args := name '::' value [',' name '::' value]*
    name := /* A string */
    value := /* A string */
```


### Zeitüberschreitung {#timeout}

Nach einer gewissen Zeitüberschreitung funktioniert der Workflow-Schritt nicht mehr. Einige Workflow-Prozesse respektieren die Zeitüberschreitung, für andere gilt sie nicht und wird daher ignoriert.

### Berechtigungen {#permissions}

Die Sitzung wurde an die `WorkflowProcess` wird vom Dienstbenutzer für den Workflow-Prozessdienst unterstützt, der über die folgenden Berechtigungen im Stammverzeichnis des Repositorys verfügt:

* `jcr:read`
* `rep:write`
* `jcr:versionManagement`
* `jcr:lockManagement`
* `crx:replicate`

Wenn dieser Berechtigungssatz für Ihre `WorkflowProcess` implementieren, muss eine Sitzung mit den erforderlichen Berechtigungen verwendet werden.

Hierfür wird empfohlen, einen Dienstbenutzer mit einer minimalen Untergruppe der erforderlichen Berechtigungen zu verwenden.

>[!CAUTION]
>
>Wenn Sie ein Upgrade von einer früheren Version auf AEM 6.2 durchführen, müssen Sie möglicherweise auch Ihre Implementierung aktualisieren.
>
>In den vorherigen Versionen wurde die Adminsitzung an die `WorkflowProcess`-Implementierungen übergeben. Danach war der uneingeschränkte Zugriff auf das Repository ohne Definition der spezifischen ACLs möglich.
>
>Die Berechtigungen werden nun wie oben dargestellt definiert ([Berechtigungen](#permissions)). Dasselbe gilt für die empfohlene Methode zum Aktualisieren Ihrer Implementierung.
>
>Eine kurzfristige Lösung ist auch für Abwärtskompatibilitätszwecke verfügbar, wenn Codeänderungen nicht möglich sind:
>
>* Verwenden der Web-Konsole ( `/system/console/configMgr` suchen Sie die **Adobe Granite-Workflow-Konfigurationsdienst**
>
>* Aktivieren Sie den **Legacymodus des Workflow-Prozesses**.
>
>Dadurch wird das bisherige Verhalten wieder aktiviert, nach dem eine Adminsitzung an die `WorkflowProcess`-Implementierung übergeben und uneingeschränkter Zugriff auf das gesamte Repository eingeräumt wird.

## Workflow-Steuerungsprozesse {#workflow-control-processes}

Die folgenden Prozesse wirken sich nicht auf Inhalte aus. Sie dienen der Steuerung des Workflows.

### AbsoluteTimeAutoAdvancer (automatisches Voranschreiten für absolute Uhrzeit) {#absolutetimeautoadvancer-absolute-time-auto-advancer}

Der Prozess `AbsoluteTimeAutoAdvancer` (automatisches Voranschreiten für absolute Uhrzeit) verhält sich wie **AutoAdvancer**. Ausnahme ist, dass die Zeitüberschreitung nach einer bestimmten Zeit und einem gewissen Datum anstelle einer entsprechenden Dauer eintritt.

* **Java-Klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AbsoluteTimeAutoAdvancer`
* **Nutzlast**: Keine.
* **Argumente**: Keine.
* **Zeitüberschreitung**: Zeitüberschreitung nach festgelegter Zeit und festgelegtem Datum.

### AutoAdvancer (Auto-Advancer) {#autoadvancer-auto-advancer}

Der `AutoAdvancer`-Prozess bringt den Workflow automatisch zum nächsten Schritt. Falls mehr als nur ein nächster Schritt möglich ist (beispielsweise bei einer ODER-Teilung), bringt der Prozess den Workflow auf der *Standardroute* voran. Wurde keine Standardroute festgelegt, wird der Workflow nicht vorangebracht.

* **Java-Klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AutoAdvancer`

* **Nutzlast**: Keine.
* **Argumente**: Keine.
* **Zeitüberschreitung**: Nach einem festgelegtem Zeitraum.

### ProcessAssembler (Prozess-Assembler) {#processassembler-process-assembler}

Der `ProcessAssembler`-Prozess führt mehrere Teilprozesse nacheinander in einem einzigen Workflow-Schritt aus. Erstellen Sie für die Nutzung des `ProcessAssembler`-Prozesses einen einzelnen entsprechenden Schritt im Workflow und legen Sie die Argumente so fest, dass sie die Namen und Argumente der auszuführenden Teilprozesse angeben.

* **Java-Klasse**: `com.day.cq.workflow.impl.process.ProcessAssembler`

* **Nutzlast**: DAM-Asset, AEM-Seite oder keine Nutzlast (je nach Anforderungen der Teilprozesse).
* **Argumente**:

```
        args := arg [',' arg]
        arg := processname ['::' processargs]
        processname := /* A fully qualified Java Class or absolute
        repository path to an ECMAScript */
        processargs := processarg [';' processarg]*
        processarg := '[' nobracketprocessarg ']' | nobracketprocessarg
        nobracketprocessarg := listitem [':' listitem]*
        listitem := /* A string */
```

* **Zeitüberschreitung**: Berücksichtigt.

Beispiel:

* Extrahieren Sie die Metadaten des Assets.
* Erstellen Sie drei Miniaturansichten der drei angegebenen Größen.
* Erstellen Sie ein JPEG-Bild aus dem Asset, vorausgesetzt, das Asset ist ursprünglich weder eine GIF- noch eine PNG-Datei (in diesem Fall wird kein JPEG-Bild erstellt).
* Legen Sie das Datum der letzten Änderung für das Asset fest.

```shell
com.day.cq.dam.core.process.ExtractMetadataProcess,
    com.day.cq.dam.core.process.CreateThumbnailProcess::[140:100];[48:48];[319:319:false],
    com.day.cq.dam.core.process.CreateWebEnabledImageProcess::dimension:1280:1280;mimetype:image/jpeg,
    com.day.cq.dam.core.process.AssetSetLastModifiedProcess
```

## Grundlegende Prozesse {#basic-processes}

Die folgenden Prozesse führen einfache Aufgaben durch oder dienen als Beispiel.

>[!CAUTION]
>
>Sie dürfen ***keinerlei*** Änderungen im Pfad `/libs` vornehmen.
>
>Dies liegt daran, dass der Inhalt von `/libs` wird beim nächsten Upgrade Ihrer Instanz überschrieben (und kann überschrieben werden, wenn Sie einen Hotfix oder ein Feature Pack anwenden).

### Löschen Sie {#delete}

Das Element unter dem angegebenen Pfad wird gelöscht.

* **ECMAScript-Pfad**: `/libs/workflow/scripts/delete.ecma`

* **Nutzlast**: JCR-Pfad
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### noop {#noop}

Dies ist der Null-Prozess. Es wird kein Vorgang ausgeführt, jedoch eine Debugmeldung protokolliert.

* **ECMAScript-Pfad**: `/libs/workflow/scripts/noop.ecma`

* **Nutzlast**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### rule-false {#rule-false}

Dies ist ein Nullprozess, der `false` auf `check()` -Methode.

* **ECMAScript-Pfad**: `/libs/workflow/scripts/rule-false.ecma`

* **Nutzlast**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### Beispiel {#sample}

Ein Muster-ECMAScript-Prozess.

* **ECMAScript-Pfad**: `/libs/workflow/scripts/sample.ecma`

* **Nutzlast**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### LockProcess {#lockprocess}

Sperrt die Nutzlast des Workflows.

* **Java-Klasse:** `com.day.cq.workflow.impl.process.LockProcess`

* **Nutzlast:** JCR_PATH und JCR_UUID
* **Argumente:** Keine
* **Zeitüberschreitung:** Ignoriert

Unter folgenden Bedingungen ist der Schritt nicht wirksam:

* Die Nutzlast wurde bereits gesperrt
* Der Nutzlastknoten enthält keinen untergeordneten jcr:content-Knoten

### UnlockProcess {#unlockprocess}

Entsperrt die Nutzlast des Workflows.

* **Java-Klasse:** `com.day.cq.workflow.impl.process.UnlockProcess`

* **Nutzlast:** JCR_PATH und JCR_UUID
* **Argumente:** Keine
* **Zeitüberschreitung:** Ignoriert

Unter folgenden Bedingungen ist der Schritt nicht wirksam:

* Die Nutzlast wurde bereits entsperrt
* Der Nutzlastknoten enthält keinen untergeordneten jcr:content-Knoten

## Versionierungsprozesse {#versioning-processes}

Der folgende Prozess führt eine versionsbezogene Aufgabe aus.

### CreateVersionProcess {#createversionprocess}

Erstellt eine neue Version der Workflow-Nutzlast (AEM-Seite oder DAM-Asset).

* **Java-Klasse**: `com.day.cq.wcm.workflow.process.CreateVersionProcess`

* **Nutzlast**: JCR-Pfad oder UUID, der auf eine Seite oder ein DAM-Asset verweist
* **Argumente**: Keine
* **Zeitüberschreitung**: Berücksichtigt
