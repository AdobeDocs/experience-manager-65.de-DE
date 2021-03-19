---
title: Best Practices für Workflows
seo-title: Best Practices für Workflows
description: Best Practices für Workflows
seo-description: 'null'
uuid: 79be4055-c2ef-428e-9054-103c6cfde1d2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 0be8b88c-6f57-4dcc-ae11-77b378a2decd
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1924'
ht-degree: 94%

---


# Best Practices für Workflows{#workflow-best-practices}

Workflows ermöglichen die Automatisierung von Aktivitäten in Adobe Experience Manager (AEM).

Da sie häufig einen Großteil der Verarbeitung in einer AEM-Umgebung ausmachen, kann es sich negativ auf das System auswirken, wenn benutzerdefinierte Workflow-Schritte nicht unter Berücksichtigung der Best Practices erstellt oder vorgefertigte Workflows nicht so konfiguriert werden, dass eine möglichst effiziente Ausführung gewährleistet ist.

Wir empfehlen daher dringend, Workflow-Implementierungen sorgfältig zu planen.

## Konfiguration {#configuration}

Beim Konfigurieren von angepassten und/oder vorgefertigten Workflow-Prozessen müssen ein paar Dinge berücksichtigt werden.

### Übergangs-Workflows {#transient-workflows}

Zur Optimierung hoher Erfassungslasten können Sie einen [Workflow als Verlaufs-Workflow](/help/sites-developing/workflows.md#transient-workflows) definieren.

Im Falle eines Verlaufs-Workflows werden die Laufzeitdaten der Zwischenarbeitsschritte bei ihrer Ausführung nicht im JCR beibehalten. (Die Ausgabeformate werden aber natürlich beibehalten.)

Mögliche Vorteile:

* Verringerung der Workflow-Verarbeitungsdauer um bis zu zehn Prozent
* Erheblich geringeres Repositorywachstum
* Keine CRUD-Workflows für die Bereinigung mehr erforderlich
* Weniger zu komprimierende TAR-Dateien

>[!CAUTION]
>
>Falls Ihr Unternehmen Workflow-Laufzeitdaten zu Auditzwecken aufbewahren muss, aktivieren Sie diese Funktion nicht.

### Optimieren von DAM-Workflows {#tuning-dam-workflows}

Richtlinien für die Optimierung der Leistung von DAM-Workflows finden Sie im [Leistungsoptimierungshandbuch für AEM Assets](/help/assets/performance-tuning-guidelines.md).

### Konfigurieren der maximalen Anzahl paralleler Workflows {#configure-the-maximum-number-of-concurrent-workflows}

AEM ermöglicht die gleichzeitige Ausführung mehrerer Workflow-Threads. Standardmäßig ist die Anzahl der Threads auf die Hälfte der Prozessorkerne des Systems festgelegt.

Wenn die Systemressourcen durch die ausgeführten Workflows stark beansprucht werden, stehen AEM unter Umständen nicht mehr genügend Ressourcen für andere Aufgaben zur Verfügung (beispielsweise für das Rendern der Benutzeroberfläche für Autoren). Dies kann dazu führen, dass das System bei Aktivitäten wie etwa dem Massenhochladen von Bildern nur noch langsam reagiert.

Zur Behandlung dieses Problems empfiehlt Adobe, die **** maximale Anzahl paralleler Aufträge auf einen Wert festzulegen, der zwischen der Hälfte und drei Vierteln der Anzahl der Prozessorkerne des Systems liegt. Dadurch sollte dem System genügend Kapazität zur Verfügung stehen, damit solche Workflows ohne Beeinträchtigung der Reaktionsfähigkeit verarbeitet werden können.

Um **Maximale Anzahl paralleler Aufträge** zu konfigurieren, können Sie entweder:

* Konfigurieren Sie die **[OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md)** aus der AEM Web-Konsole. für **Warteschlange: Granite Workflow Queue** (eine **Apache Sling-Auftragswarteschlangenkonfiguration**).

* Die Warteschlange kann über die Option **Sling Jobs** in der AEM Web Console konfiguriert werden. für **Auftragswarteschlangenkonfiguration: Granite Workflow Queue**, um `http://localhost:4502/system/console/slingevent`.

Zusätzlich gibt es eine separate Konfiguration für die externe Prozessauftragswarteschlange **Granite Workflow**. Diese Konfiguration wird für Workflow-Prozesse verwendet, die externe Binärdateien starten (beispielsweise **InDesign Server** oder **Image Magick**).

### Konfigurieren individueller Auftragswarteschlangen  {#configure-individual-job-queues}

Manchmal ist es hilfreich, individuelle Auftragswarteschlangen zur Steuerung paralleler Threads oder andere Warteschlangenoptionen für individuelle Aufträge zu konfigurieren. Über die Web-Konsole können Sie eine individuelle Warteschlange über die Factory **Warteschlangenkonfiguration für Apache Sling-Aufträge** hinzufügen und konfigurieren. Um das entsprechende Thema für die Liste zu finden, führen Sie das Workflow-Modell aus und suchen Sie es in der Konsole **Sling Jobs**; z. B. bei `http://localhost:4502/system/console/slingevent`.

Individuelle Auftragswarteschlangen können auch für Verlaufs-Workflows hinzugefügt werden.

### Konfigurieren der Workflow-Bereinigung {#configure-workflow-purging}

Bei einer Standardinstallation bietet AEM eine Wartungskonsole, über die tägliche und wöchentliche Wartungsaktivitäten geplant und konfiguriert werden können – beispielsweise hier:

`http://localhost:4502/libs/granite/operations/content/maintenance.html`

**Wöchentliches Wartungsfenster** verfügt standardmäßig über eine Aufgabe vom Typ **Workflow-Bereinigung**, diese muss jedoch erst konfiguriert werden, damit sie ausgeführt wird. Zum Konfigurieren von Workflow-Bereinigungen muss in der Web-Konsole eine neue **Adobe Granite-Workflow-Bereinigungskonfiguration** hinzugefügt werden.

Ausführlichere Informationen zu Wartungsaufgaben in AEM finden Sie im [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

## Anpassung  {#customization}

Beim Erstellen benutzerdefinierter Workflow-Prozesse sind einige Punkte zu beachten.

### Standorte {#locations}

Definitionen von Workflow-Modellen, -Startern, -Skripten und -Benachrichtigungen werden im entsprechenden Repository für den jeweiligen Typ gespeichert (also beispielsweise in „out-of-the-box“ oder in „custom“).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Neue Repositorystruktur in AEM 6.5](/help/sites-deploying/repository-restructuring.md).

#### Speicherorte: Workflow-Modelle {#locations-workflow-models}

Workflow-Modelle werden im Repository auf der Grundlage ihres Typs gespeichert:

* Pfad für vorgefertigte Workflow-Designs:

   `/libs/settings/workflow/models/`

   >[!CAUTION]
   >
   >Beachten Sie Folgendes:
   >
   >* Platzieren Sie in diesem Ordner keine benutzerdefinierten Workflow-Modelle.
   >* alles bearbeiten in `/libs`

   >
   >Vorgenommene Änderungen werden unter Umständen bei einem Upgrade oder beim Installieren von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben.

* Pfad für benutzerdefinierte Workflow-Designs:

   ```
   /conf/global/settings/workflow/models/...
   ```

* Pfad für vordefinierte und benutzerdefinierte Laufzeit-Workflow-Designs:

   `/var/workflow/models/`

* Pfad für ältere Workflow-Designs (sowohl Entwurfszeit als auch Laufzeit):

   `/etc/workflow/models/`

   >[!NOTE]
   >
   >Wenn diese Designs *mithilfe der AEM-Benutzeroberfläche* bearbeitet werden, werden die Details an die neuen Speicherorte kopiert.

#### Speicherorte: Workflow-Starter  {#locations-workflow-launchers}

Definitionen für Workflow-Starter werden im Repository ebenfalls auf der Grundlage ihres Typs gespeichert:

* Pfad für vorgefertigte Workflow-Starter:

   `/libs/settings/workflow/launcher/`

   >[!CAUTION]
   >
   >Beachten Sie Folgendes:
   >
   >* Platzieren Sie in diesem Ordner keine benutzerdefinierten Workflow-Starter.
   >* alles bearbeiten in `/libs`

   >
   >Vorgenommene Änderungen werden unter Umständen bei einem Upgrade oder beim Installieren von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben.

* Pfad für benutzerdefinierte Workflow-Starter:

   ```
   /conf/global/settings/workflow/launcher/...
   ```

* Pfad für ältere Workflow-Starter:

   `/etc/workflow/launcher/`

   >[!NOTE]
   >
   >Wenn diese Definitionen *mithilfe der AEM-Benutzeroberfläche* bearbeitet werden, werden die Details an die neuen Speicherorte kopiert.

#### Speicherorte: Workflow-Skripte  {#locations-workflow-scripts}

Workflow-Skripte werden im Repository ebenfalls auf der Grundlage ihres Typs gespeichert:

* Pfad für vorgefertigte Workflow-Skripte:

   `/libs/workflow/scripts/`

   >[!CAUTION]
   >
   >Beachten Sie Folgendes:
   >
   >* Platzieren Sie in diesem Ordner keine benutzerdefinierten Workflow-Skripte.
   >* alles bearbeiten in `/libs`

   >
   >Vorgenommene Änderungen werden unter Umständen bei einem Upgrade oder beim Installieren von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben.

* Pfad für benutzerdefinierte Workflow-Skripte:

   ```
   /apps/workflow/scripts/...
   ```

* Pfad für ältere Workflow-Skripte:

   `/etc/workflow/scripts/`

#### Speicherorte: Workflow-Benachrichtigungen {#locations-workflow-notifications}

Workflow-Benachrichtigungen werden im Repository ebenfalls auf der Grundlage ihres Typs gespeichert:

* Pfad für vorgefertigte Workflow-Benachrichtigungsdefinitionen:

   `/libs/settings/workflow/notification/`

   >[!CAUTION]
   >
   >Beachten Sie Folgendes:
   >
   >* Platzieren Sie in diesem Ordner keine benutzerdefinierten Workflow-Benachrichtigungsdefinitionen.
   >* alles bearbeiten in `/libs`

   >
   >Vorgenommene Änderungen werden unter Umständen bei einem Upgrade oder beim Installieren von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben.

* Pfad für benutzerdefinierte Workflow-Benachrichtigungsdefinitionen:

   ```
   /conf/global/settings/workflow/notification/...
   ```

   >[!NOTE]
   >
   >Wenn Sie einen Workflow-Benachrichtigungstext überschreiben möchten, erstellen Sie einen überlagerten Pfad unter:
   >
   >
   >`/conf/global/settings/workflow/notification/<path-under-libs>`

* Pfad für ältere Workflow-Benachrichtigungsdefinitionen:

   `/etc/workflow/notification/`

### Prozesssitzungen {#process-sessions}

Wie bei jeder angepassten Entwicklung empfiehlt es sich, nach Möglichkeit die Sitzung eines Benutzers zu verwenden. Dies hat folgende Vorteile:

* Optimale Einhaltung der Sicherheitsrichtlinien
* Verwaltung des Öffnens/Schließens der Sitzung durch das System

Wenn Sie einen Workflow-Prozess implementieren, gilt Folgendes:

* Eine Workflow-Sitzung wird bereitgestellt und sollte verwendet werden, solange kein zwingender Grund dagegenspricht.
* Auf der Grundlage von Workflow-Schritten sollten keine neuen Sitzungen erstellt werden, da dies zu Inkonsistenzen beim Zustand sowie zu möglichen Parallelitätsproblemen in der Workflow-Engine führt.
* Über einen Prozessschritt in einem Workflow sollte keine neue JCR-Sitzung initiiert werden. Passen Sie die von der Prozessschritt-API bereitgestellte Workflow-Sitzung an eine JCR-Sitzung an. Beispiel:

```
public void execute(WorkItem item, WorkflowSession workflowSession, MetaDataMap args) throws WorkflowException {
        // to obtain a jcr session:
        javax.jcr.Session jcrSession = workflowSession.adaptTo(javax.jcr.Session.class);

        // to obtain a sling resource resolver:
        org.apache.sling.api.resource.ResourceResolver slingResourceResolver = workflowSession.adaptTo(org.apache.sling.api.resource.ResourceResolver.class);
```

Speichern einer Sitzung:

* Wenn innerhalb eines Workflow-Prozesses `WorkflowSession` verwendet wird, um das Repository zu ändern, führen Sie keine explizite Speicherung der Sitzung durch. Die Sitzung wird nach Abschluss des Workflows gespeichert.
* `Session.Save` darf nicht innerhalb eines Workflow-Schritts aufgerufen werden:

   * Es wird empfohlen, die Workflow-JCR-Sitzung anzupassen. In diesem Fall wird `save` nicht benötigt, da die Workflow-Engine die Sitzung nach Abschluss der Workflow-Ausführung automatisch speichert.
   * Ein Prozessschritt sollte keine eigene JCR-Sitzung erstellen.

* Die Vermeidung unnötiger Speichervorgänge führt zu weniger Mehraufwand und somit zu einer höheren Workflow-Effizienz.

>[!CAUTION]
>
>Sollten Sie entgegen den hier angegebenen Empfehlungen eine eigene JCR-Sitzung erstellen, muss diese gespeichert werden.

### Verringern von Anzahl/Umfang der Starter {#minimize-the-number-scope-of-launchers}

Es gibt einen Listener, der für alle registrierten [Workflow-Starter](/help/sites-administering/workflows-starting.md#workflows-launchers) zuständig ist:

* Er lauscht auf Änderungen an allen Pfaden, die in den Globbing-Eigenschaften der anderen Starter angegeben sind.
* Wenn ein Ereignis übermittelt wird, wertet die Workflow-Engine die einzelnen Starter aus, um zu ermitteln, ob sie ausgeführt werden sollen.

Eine zu hohe Anzahl von Startern verlangsamt diese Auswertung.

Die Erstellung eines Globbing-Pfads am Stamm des Repositorys für einen einzelnen Starter führt dazu, dass die Workflow-Engine auf Erstellungs-/Änderungsereignisse für jeden Knoten im Repository lauscht und diese auswertet. Es empfiehlt sich daher, nur Starter zu erstellen, die wirklich benötigt werden, und den Globbing-Pfad so spezifisch wie möglich zu machen.

Angesichts der Auswirkungen, die diese Starter auf das Workflow-Verhalten haben, kann es hilfreich sein, alle ungenutzten vorgefertigten Starter zu deaktivieren.

### Konfigurationserweiterungen für Starter {#configuration-enhancements-for-launchers}

Die benutzerdefinierte [Starter-Konfiguration](/help/sites-administering/workflows-starting.md#workflows-launchers) wurde erweitert, um Folgendes zu unterstützen:

* Verknüpfung mehrerer Bedingungen mit „UND“
* Verwendung von ODER-Bedingungen innerhalb einer einzelnen Bedingung
* Deaktivierung/Aktivierung von Startern auf der Grundlage des Aktivierungsstatus eines Funktions-Flags
* Unterstützung regulärer Ausdrücke in Starter-Bedingungen

### Kein Start von Workflows über andere Workflows {#do-not-start-workflows-from-other-workflows}

Durch die Objekterstellung im Speicher sowie durch die Knotenüberwachung im Repository können Workflows zu erheblichem Mehraufwand führen. Es empfiehlt sich daher, die Verarbeitung eines Workflows innerhalb dieses Workflows abzuwickeln, anstatt weitere Workflows zu starten.

Ein Beispiel wäre etwa ein Workflow, der einen Geschäftsprozess für eine Gruppe von Inhalten implementiert und die Inhalte anschließend aktiviert. Es ist besser, einen benutzerdefinierten Workflow-Prozess zu erstellen, der jeden dieser Knoten aktiviert, anstatt für jeden der zu veröffentlichenden Inhaltsknoten ein Modell vom Typ **Inhalt aktivieren** zu starten. Dieser Ansatz führt zwar zu einem höheren Entwicklungsaufwand, ist aber effizienter als für jede Aktivierung eine separate Workflow-Instanz zu starten.

Ein weiteres Beispiel wäre ein Workflow, der eine Reihe von Knoten verarbeitet, ein Workflow-Paket erstellt und dieses Paket anschließend aktiviert. Anstatt das Paket zu erstellen und anschließend einen separaten Workflow mit dem Paket als Nutzlast zu erstellen, können Sie im Paketerstellungsschritt die Nutzlast Ihres Workflows ändern und dann den Paketaktivierungsschritt innerhalb desselben Workflow-Modells aufrufen.

### Handler-Modus {#handler-advance}

Wenn Sie ein Workflow-Modell entwerfen, können Sie den Handler-Modus für Ihre Workflow-Schritte aktivieren. Alternativ können Sie Ihrem Workflow-Schritt Code hinzufügen, um den als Nächstes auszuführenden Schritt zu bestimmen und auszuführen.

Es wird empfohlen, den Handler-Modus zu verwenden, da sich dadurch die Leistung verbessert.

### Workflow-Statuswerte {#workflow-stages}

Sie können [Workflow-Statuswerte](/help/sites-developing/workflows.md#workflow-stages) definieren und Aufgaben/Schritte einem bestimmten Workflow-Status zuweisen.

Diese Information wird zum Anzeigen des Fortschritts eines Workflows verwendet, wenn Sie auf die Registerkarte [**Workflow-Informationen** eines Arbeitselements aus dem **Posteingang**](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) klicken. Vorhandene Workflow-Modelle können bearbeitet werden, um Statuswerte hinzuzufügen.

### Prozessschritt „Seite aktivieren“{#activate-page-process-step}

Der Prozessschritt **Seite aktivieren** aktiviert zwar Seiten für Sie, referenzierte DAM-Assets werden durch diesen Schritt aber nicht automatisch gesucht und aktiviert.

Berücksichtigen Sie dies, wenn Sie den Schritt im Rahmen eines Workflow-Modells verwenden möchten.

### Überlegungen zu Upgrades {#upgrade-considerations}

Wichtige Punkte bei Upgrades für Ihre Instanz:

* Sichern Sie alle benutzerdefinierten Workflow-Modelle, bevor Sie ein Upgrade für eine Instanz durchführen.
* Vergewissern Sie sich, dass keiner Ihrer benutzerdefinierten Workflows am folgenden [Speicherort](#locations) gespeichert ist:

   * `/libs/settings/workflow/models/projects`

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Neue Repositorystruktur in AEM 6.5](/help/sites-deploying/repository-restructuring.md).

## Systemtools {#system-tools}

Für die Workflow-Überwachung, -Verwaltung und -Problembehandlung stehen zahlreiche Systemtools zur Verfügung. Alle Beispiel-URLs unten verwenden `localhost:4502`, sollten aber in jeder Autoreninstanz ( `<hostname>:<port>`) verfügbar sein.

### Konsole zur Behandlung von Sling-Aufträgen {#sling-job-handling-console}

`http://localhost:4502/system/console/slingevent`

In der Konsole zur Behandlung von Sling-Aufträgen wird Folgendes angezeigt:

* Statistik zum Zustand von Aufträgen im System seit dem letzten Neustart
* Konfigurationen für alle Auftragswarteschlangen sowie ein Tastaturbefehl für die Bearbeitung im Konfigurationsmanager

### Workflow-Berichtstool {#workflow-report-tool}

Das Workflow-Berichtstool wird in Version 6.3 entfernt, um die Leistung nicht zu beeinträchtigen.

### MBean für Workflow-Wartungsvorgänge {#workflow-maintenance-operations-mbean}

`http://localhost:4502/system/console/jmx/com.adobe.granite.workflow:type=Maintenance`

Das MBean für die Workflow-Wartung macht eine Reihe praktischer Wartungsroutinen verfügbar – etwa zum Bereinigen abgeschlossener Workflows oder zum Abrufen der Workflow-Statistik.

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* [Arbeiten mit Workflows](/help/sites-authoring/workflows.md)
* [Verwalten von Workflows](/help/sites-administering/workflows.md)
* [Entwickeln und Erweitern von Workflows](/help/sites-developing/workflows.md)
* [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md)