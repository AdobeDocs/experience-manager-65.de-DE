---
title: Prozessreferenz für Workflows
description: Weitere Informationen zu Workflows in Adobe Experience Manager finden Sie in dieser Prozessreferenz .
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: a9de8ec6-6948-4643-89c3-62d9b1f6293a
source-git-commit: b703f356f9475eeeafb1d5408c650d9c6971a804
workflow-type: tm+mt
source-wordcount: '1076'
ht-degree: 46%

---

# Prozessreferenz für Workflows{#workflow-process-reference}

AEM bietet mehrere Prozessschritte, die zum Erstellen von Workflow-Modellen verwendet werden können. Benutzerdefinierte Prozessschritte können auch für Aufgaben hinzugefügt werden, die nicht von den integrierten Schritten abgedeckt werden (siehe [Erstellen von Workflow-Modellen](/help/sites-developing/workflows-models.md)).

## Prozessmerkmale {#process-characteristics}

Für jeden Prozessschritt werden die folgenden Eigenschaften beschrieben.

### Java™-Klasse oder ECMA-Pfad {#java-class-or-ecma-path}

Prozessschritte werden entweder von einer Java™-Klasse oder einem ECMAScript definiert.

* Für die Java™-Klassenprozesse wird der vollqualifizierte Klassenname angegeben.
* Für die ECMAScript-Prozesse wird der Pfad zum Skript bereitgestellt.

### Payload {#payload}

Die Payload ist die Entität, auf die die Workflow-Instanz reagiert. Die Payload wird implizit durch den Kontext ausgewählt, in dem eine Workflow-Instanz gestartet wird.

Wenn beispielsweise ein Workflow auf die AEM-Seite *P* angewendet wird, durchläuft *P* bei fortlaufendem Workflow die verschiedenen Schritte. Dabei wirkt sich jeder Schritt optional in irgendeiner Weise auf *P* aus.

Im häufigsten Fall ist die Payload ein JCR-Knoten im Repository (z. B. eine AEM Seite oder ein Asset). Eine JCR-Knoten-Payload wird als Zeichenfolge übergeben, die entweder aus einem JCR-Pfad oder einer JCR-Kennung besteht (UUID). Manchmal kann die Payload eine JCR-Eigenschaft (übergeben als JCR-Pfad), eine URL, ein binäres Objekt oder ein generisches Java™-Objekt sein. Einzelne Prozessschritte, die auf die Payload reagieren, erwarten in der Regel einen bestimmten Typ Payload oder verhalten sich je nach Payload-Typ anders. Der erwartete Payload-Typ (falls vorhanden) wird für jeden der unten beschriebenen Prozesse angegeben.

### Argumente {#arguments}

Einige Workflow-Prozesse akzeptieren Argumente, die der Administrator beim Einrichten des Workflow-Schritts angibt.

Argumente werden als einzelne Zeichenfolge in der **Prozess-Argumente** -Eigenschaft in der **Eigenschaften** -Bereich des Workflow-Editors. Für jeden unten beschriebenen Prozess wird das Format der Argumentzeichenfolge in einer einfachen EBNF-Grammatik beschrieben. Das folgende Beispiel zeigt, dass die Argumentzeichenfolge aus einem oder mehreren durch Komma getrennten Paaren besteht, wobei jedes Paar aus einem Namen (der eine Zeichenfolge ist) und einem Wert besteht, getrennt durch einen Doppelpunkt:

```
    args := name '::' value [',' name '::' value]*
    name := /* A string */
    value := /* A string */
```


### Zeitüberschreitung {#timeout}

Nach diesem Timeout-Zeitraum ist der Workflow-Schritt nicht mehr funktionsfähig. Einige Workflow-Prozesse berücksichtigen den Timeout-Wert, während er für andere nicht gilt und ignoriert wird.

### Berechtigungen {#permissions}

Die Sitzung, die an den `WorkflowProcess` übergeben wird, wird durch den Dienstbenutzer für den Workflow-Prozessdienst gestützt, der über folgende Berechtigungen am Stamm des Repositorys verfügt:

* `jcr:read`
* `rep:write`
* `jcr:versionManagement`
* `jcr:lockManagement`
* `crx:replicate`

Wenn dieser Berechtigungssatz nicht ausreichend für die `WorkflowProcess`-Implementierung ist, muss auf eine Sitzung mit den erforderlichen Berechtigungen zurückgegriffen werden.

Die empfohlene Vorgehensweise ist die Verwendung eines Dienstbenutzers, der mit der erforderlichen, jedoch minimalen Untergruppe von Berechtigungen erstellt wurde.

>[!CAUTION]
>
>Wenn Sie ein Upgrade von einer Version vor AEM 6.2 durchführen, müssen Sie möglicherweise Ihre Implementierung aktualisieren.
>
>In früheren Versionen wurde die Admin-Sitzung an die `WorkflowProcess` -Implementierungen implementiert werden und dann vollen Zugriff auf das Repository haben können, ohne dass bestimmte ACLs definiert werden müssen.
>
>Die Berechtigungen werden jetzt wie oben definiert ([Berechtigungen](#permissions)). Dies ist die empfohlene Methode für die Aktualisierung Ihrer Implementierung.
>
>Eine kurzfristige Lösung ist auch für Abwärtskompatibilitätszwecke verfügbar, wenn Codeänderungen nicht möglich sind:
>
>* Öffnen Sie die Web-Konsole (`/system/console/configMgr`) und suchen Sie nach dem **Adobe Granite Workflow-Konfigurationsdienst**.
>
>* Aktivieren Sie den **Legacymodus des Workflow-Prozesses**.
>
>Dadurch wird das alte Verhalten der Bereitstellung einer Admin-Sitzung zum `WorkflowProcess` Implementierung implementieren und uneingeschränkten Zugriff auf das gesamte Repository gewähren.

## Workflow-Kontrollprozesse {#workflow-control-processes}

Die folgenden Prozesse führen keine Aktionen für Inhalte durch. Sie dienen der Steuerung des Workflows.

### AbsoluteTimeAutoAdvancer (automatisches Voranschreiten für absolute Uhrzeit) {#absolutetimeautoadvancer-absolute-time-auto-advancer}

Der Prozess `AbsoluteTimeAutoAdvancer` (automatisches Voranschreiten für absolute Uhrzeit) verhält sich wie **AutoAdvancer**. Ausnahme ist, dass die Zeitüberschreitung nach einer bestimmten Zeit und einem gewissen Datum anstelle einer entsprechenden Dauer eintritt.

* **Java™-Klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AbsoluteTimeAutoAdvancer`
* **Payload**: Keine.
* **Argumente**: Keine.
* **Zeitüberschreitung**: Zeitüberschreitung nach festgelegter Zeit und festgelegtem Datum.

### AutoAdvancer (Auto-Advancer) {#autoadvancer-auto-advancer}

Der `AutoAdvancer`-Prozess bringt den Workflow automatisch zum nächsten Schritt. Falls mehr als nur ein nächster Schritt möglich ist (beispielsweise bei einer ODER-Teilung), bringt der Prozess den Workflow auf der *Standardroute* voran. Wurde keine Standardroute festgelegt, wird der Workflow nicht vorangebracht.

* **Java™-Klasse**: `com.adobe.granite.workflow.console.timeout.autoadvance.AutoAdvancer`

* **Payload**: Keine.
* **Argumente**: Keine.
* **Zeitüberschreitung**: Nach einem festgelegtem Zeitraum.

### ProcessAssembler (Prozess-Assembler) {#processassembler-process-assembler}

Die `ProcessAssembler` -Prozess führt mehrere Teilprozesse nacheinander in einem einzelnen Workflow-Schritt aus. So verwenden Sie die `ProcessAssembler`erstellen Sie einen einzelnen Schritt dieses Typs in Ihrem Workflow und legen Sie seine Argumente fest, um die Namen und Argumente der auszuführenden Teilprozesse anzugeben.

* **Java™-Klasse**: `com.day.cq.workflow.impl.process.ProcessAssembler`

* **Nutzlast**: Ein DAM-Asset, eine AEM oder keine Payload (abhängig von den Anforderungen der Teilprozesse).
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

* Extrahieren Sie die Metadaten aus dem Asset.
* Erstellen Sie drei Miniaturansichten der drei angegebenen Größen.
* Erstellen Sie ein JPEG-Bild aus dem Asset, vorausgesetzt das Asset ist ursprünglich kein GIF oder PNG (in diesem Fall wird keine JPEG erstellt).
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
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.
>
>da der Inhalt von `/libs` überschrieben wird, wenn Sie die Instanz das nächste Mal upgraden. (Außerdem kann der Inhalt auch durch Anwenden von Hotfixes oder Feature Packs überschrieben werden.)

### Löschen Sie {#delete}

Das Element am angegebenen Pfad wird gelöscht.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/delete.ecma`

* **Payload**: JCR-Pfad
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### noop {#noop}

Dies ist der Null-Prozess. Es wird kein Vorgang ausgeführt, jedoch eine Debugmeldung protokolliert.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/noop.ecma`

* **Payload**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### rule-false {#rule-false}

Dies ist ein Null-Prozess, der `false` für die `check()`-Methode zurückgibt.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/rule-false.ecma`

* **Payload**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### sample {#sample}

Dies ist ein Beispiel für einen ECMAScript-Prozess.

* **ECMA-Skript-Pfad**: `/libs/workflow/scripts/sample.ecma`

* **Payload**: Keine
* **Argumente**: Keine
* **Zeitüberschreitung**: Ignoriert

### LockProcess {#lockprocess}

Sperrt die Payload des Workflows.

* **Java™-Klasse:** `com.day.cq.workflow.impl.process.LockProcess`

* **Payload:** JCR_PATH und JCR_UUID
* **Argumente:** Keines
* **Zeitüberschreitung:** Ignoriert

Der Schritt hat unter den folgenden Umständen keine Auswirkungen:

* Die Payload wurde bereits gesperrt
* Der Payload-Knoten enthält keinen untergeordneten jcr:content-Knoten

### UnlockProcess {#unlockprocess}

Entsperrt die Payload des Workflows.

* **Java™-Klasse:** `com.day.cq.workflow.impl.process.UnlockProcess`

* **Payload:** JCR_PATH und JCR_UUID
* **Argumente:** Keines
* **Zeitüberschreitung:** Ignoriert

Der Schritt hat unter den folgenden Umständen keine Auswirkungen:

* Die Payload wurde bereits entsperrt
* Der Payload-Knoten enthält keinen untergeordneten jcr:content-Knoten

## Versionierungsprozesse {#versioning-processes}

Der folgende Prozess führt eine versionsbezogene Aufgabe aus.

### CreateVersionProcess {#createversionprocess}

Erstellt eine Version der Workflow-Payload (AEM Seite oder DAM-Asset).

* **Java™-Klasse**: `com.day.cq.wcm.workflow.process.CreateVersionProcess`

* **Payload**: JCR-Pfad oder UUID, der auf eine Seite oder ein DAM-Asset verweist
* **Argumente**: Keine
* **Zeitüberschreitung**: Berücksichtigt
