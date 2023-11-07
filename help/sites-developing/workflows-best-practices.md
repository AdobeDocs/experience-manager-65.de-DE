---
title: Best Practices für Workflows
seo-title: Workflow Best Practices
description: Erfahren Sie mehr über die Best Practices für die Arbeit mit Workflows in Adobe Experience Manager.
seo-description: null
uuid: 79be4055-c2ef-428e-9054-103c6cfde1d2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 0be8b88c-6f57-4dcc-ae11-77b378a2decd
exl-id: 14775476-6fe5-4583-8ab5-b55fef892174
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 27%

---

# Best Practices für Workflows{#workflow-best-practices}

Workflows ermöglichen die Automatisierung von Aktivitäten in Adobe Experience Manager (AEM).

Sie stellen oft einen großen Teil der Verarbeitung dar, die in einer AEM-Umgebung stattfindet. Wenn also benutzerdefinierte Workflow-Schritte nicht gemäß Best Practices geschrieben werden oder native Workflows nicht so konfiguriert sind, dass sie so effizient wie möglich ausgeführt werden, kann dies Auswirkungen auf das System haben.

Wir empfehlen daher dringend, Workflow-Implementierungen sorgfältig zu planen.

## Konfiguration {#configuration}

Beim Konfigurieren von Workflow-Prozessen (angepasst und/oder vorkonfiguriert) sollten einige Aspekte beachtet werden.

### Übergangs-Workflows {#transient-workflows}

Um die Ladevorgänge mit hoher Aufnahme zu optimieren, können Sie eine [Workflow als transient](/help/sites-developing/workflows.md#transient-workflows).

Wenn ein Workflow vorübergehend ist, werden die Laufzeitdaten, die sich auf die Zwischenarbeitsschritte beziehen, bei ihrer Ausführung nicht im JCR persistiert (die Ausgabedarstellungen werden beibehalten).

Zu den Vorteilen zählen:

* Verringerung der Verarbeitungszeit des Workflows um bis zu 10 %.
* Reduzieren Sie das Repository-Wachstum erheblich.
* Es sind keine CRUD-Workflows mehr zum Bereinigen erforderlich.
* Darüber hinaus wird die Anzahl der zu komprimierenden TAR-Dateien reduziert.

>[!CAUTION]
>
>Falls Ihr Unternehmen Workflow-Laufzeitdaten zu Auditzwecken aufbewahren muss, aktivieren Sie diese Funktion nicht.

### Anpassen von DAM-Workflows {#tuning-dam-workflows}

Richtlinien zur Leistungsoptimierung von DAM-Workflows finden Sie im Abschnitt [Handbuch zur Leistungsoptimierung von AEM Assets](/help/assets/performance-tuning-guidelines.md).

### Konfigurieren der maximalen Anzahl gleichzeitiger Workflows {#configure-the-maximum-number-of-concurrent-workflows}

AEM können die gleichzeitige Ausführung mehrerer Workflow-Threads zulassen. Standardmäßig ist die Anzahl der Threads so konfiguriert, dass die Anzahl der Prozessorkerne auf dem System halbiert wird.

In Fällen, in denen die ausgeführten Workflows Systemressourcen erfordern, kann dies bedeuten, dass AEM für andere Aufgaben wie das Rendern der Authoring-Benutzeroberfläche wenig übrig haben. Daher kann das System bei Aktivitäten wie dem Massen-Bild-Upload zu langsam sein.

Um dieses Problem zu beheben, empfiehlt Adobe, die Anzahl der **Maximale Anzahl paralleler Aufträge** zwischen der Hälfte und drei Viertel der Anzahl der Prozessorkerne auf dem System. Dadurch sollte dem System genügend Kapazität zur Verfügung stehen, damit solche Workflows ohne Beeinträchtigung der Reaktionsfähigkeit verarbeitet werden können.

Die **maximale Anzahl paralleler Aufträge** kann wie folgt konfiguriert werden:

* Konfigurieren Sie die **[OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md)** über die AEM-Web-Konsole für **Warteschlange: Granite Workflow-Warteschlange** (eine **Warteschlangenkonfiguration für Apache Sling-Aufträge**).

* Konfigurieren Sie die Warteschlange über die Option **Sling-Aufträge** der AEM-Web-Konsole für **Auftragswarteschlange-Konfiguration: Granite Workflow-Warteschlange** unter `http://localhost:4502/system/console/slingevent`.

Darüber hinaus gibt es eine separate Konfiguration für die **Granite-Workflow-Warteschlange für externe Verarbeitungsaufträge**. Dies wird für Workflow-Prozesse verwendet, die externe Binärdateien starten, z. B. **InDesign Server** oder **Image Magick**.

### Konfigurieren einzelner Auftragswarteschlangen {#configure-individual-job-queues}

In einigen Fällen ist es nützlich, einzelne Auftragswarteschlangen zu konfigurieren, um gleichzeitige Threads oder andere Warteschlangenoptionen auf Basis einzelner Aufträge zu steuern. Sie können eine einzelne Warteschlange über die Web-Konsole hinzufügen und konfigurieren. **Apache Sling Job Queue-Konfiguration** Fabrik. Um das entsprechende Thema aufzulisten, führen Sie das Modell Ihres Workflows aus und suchen Sie im **Sling-Aufträge** console, z. B. at `http://localhost:4502/system/console/slingevent`.

Individuelle Auftragswarteschlangen können auch für Verlaufs-Workflows hinzugefügt werden.

### Konfigurieren der Workflow-Bereinigung {#configure-workflow-purging}

In einer standardmäßigen AEM bietet eine Wartungskonsole, in der tägliche und wöchentliche Wartungsaktivitäten geplant und konfiguriert werden können, z. B. unter:

`http://localhost:4502/libs/granite/operations/content/maintenance.html`

Standardmäßig wird die Variable **Wöchentliches Wartungsfenster** hat eine **Workflow-Bereinigung** -Aufgabe, dies muss jedoch konfiguriert werden, bevor sie ausgeführt werden kann. Um die Workflow-Bereinigung zu konfigurieren, wird eine neue **Adobe Granite-Workflow-Bereinigungskonfiguration** muss in der Webkonsole hinzugefügt werden.

Weitere Informationen zu Wartungsaufgaben in AEM finden Sie im [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

## Anpassung {#customization}

Beim Schreiben benutzerdefinierter Workflow-Prozesse sollten einige Aspekte beachtet werden.

### Speicherorte {#locations}

Definitionen von Workflow-Modellen, Startern, Skripten und Benachrichtigungen werden im Repository nach dem Typ gespeichert, d. h. standardmäßig, benutzerdefiniert, unter anderem.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Neue Repositorystruktur in AEM 6.5](/help/sites-deploying/repository-restructuring.md).

#### Standorte - Workflow-Modelle {#locations-workflow-models}

Workflow-Modelle werden im Repository nach Typ gespeichert:

* Vordefinierte Workflow-Designs werden unter folgendem Pfad gespeichert:

  `/libs/settings/workflow/models/`

  >[!CAUTION]
  >
  >Nicht beachten:
  >
  >* Platzieren Sie beliebige Ihrer benutzerdefinierten Workflow-Modelle in diesem Ordner.
  >* Lassen Sie alles in `/libs` unverändert.
  >
  >Da alle Änderungen beim Upgrade oder bei der Installation von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben werden können.

* Benutzerdefinierte Workflow-Designs befinden sich unter:

  ```
  /conf/global/settings/workflow/models/...
  ```

* Pfad für vordefinierte und benutzerdefinierte Laufzeit-Workflow-Designs:

  `/var/workflow/models/`

* Pfad für ältere Workflow-Designs (sowohl Entwurfszeit als auch Laufzeit):

  `/etc/workflow/models/`

  >[!NOTE]
  >
  >Wenn diese Designs bearbeitet werden *Verwenden der AEM-Benutzeroberfläche*, werden die Details an die neuen Speicherorte kopiert.

#### Standorte - Workflow-Starter {#locations-workflow-launchers}

Workflow-Starter-Definitionen werden auch im Repository nach Typ gespeichert:

* Vordefinierte Workflow-Starter befinden sich unter folgendem Pfad:

  `/libs/settings/workflow/launcher/`

  >[!CAUTION]
  >
  >Nicht beachten:
  >
  >* Platzieren Sie einen Ihrer benutzerdefinierten Workflow-Starter in diesem Ordner.
  >* Lassen Sie alles in `/libs` unverändert.
  >
  >Da alle Änderungen beim Upgrade oder bei der Installation von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben werden können.

* Benutzerdefinierte Workflow-Starter befinden sich unter:

  ```
  /conf/global/settings/workflow/launcher/...
  ```

* Pfad für ältere Workflow-Starter:

  `/etc/workflow/launcher/`

  >[!NOTE]
  >
  >Wenn diese Definitionen bearbeitet werden *Verwenden der AEM-Benutzeroberfläche*, werden die Details an die neuen Speicherorte kopiert.

#### Speicherorte - Workflow-Skripte {#locations-workflow-scripts}

Workflow-Skripte werden auch im Repository nach Typ gespeichert:

* Vordefinierte Workflow-Skripte werden unter folgendem Pfad gespeichert:

  `/libs/workflow/scripts/`

  >[!CAUTION]
  >
  >Nicht beachten:
  >
  >* Platzieren Sie beliebige Ihrer benutzerdefinierten Workflow-Skripte in diesem Ordner
  >* Lassen Sie alles in `/libs` unverändert.
  >
  >Da alle Änderungen beim Upgrade oder bei der Installation von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben werden können.

* Benutzerdefinierte Workflow-Skripte befinden sich unter:

  ```
  /apps/workflow/scripts/...
  ```

* Pfad für ältere Workflow-Skripte:

  `/etc/workflow/scripts/`

#### Standorte - Workflow-Benachrichtigungen {#locations-workflow-notifications}

Workflow-Benachrichtigungen werden auch im Repository nach Typ gespeichert:

* Vordefinierte Workflow-Benachrichtigungsdefinitionen werden unter folgendem Pfad gespeichert:

  `/libs/settings/workflow/notification/`

  >[!CAUTION]
  >
  >Nicht beachten:
  >
  >* Platzieren Sie eine Ihrer benutzerdefinierten Workflow-Benachrichtigungsdefinitionen in diesem Ordner
  >* Lassen Sie alles in `/libs` unverändert.
  >
  >Da alle Änderungen beim Upgrade oder bei der Installation von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben werden können.

* Benutzerdefinierte Workflow-Benachrichtigungsdefinitionen befinden sich unter:

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

Wie bei jeder benutzerdefinierten Entwicklung wird immer empfohlen, nach Möglichkeit eine Benutzersitzung zu verwenden:

* zur optimalen Einhaltung der Sicherheitsrichtlinien
* , damit das System das Öffnen und Schließen der Sitzung verwalten kann

Bei der Implementierung eines Workflow-Prozesses:

* Eine Workflow-Sitzung wird bereitgestellt und sollte verwendet werden, solange kein zwingender Grund dagegenspricht.
* Neue Sitzungen sollten nicht aus Workflow-Schritten erstellt werden, da dies zu Inkonsistenzen im Status sowie möglichen gleichzeitigen Problemen in der Workflow-Engine führt.
* Sie sollten innerhalb eines Prozessschritts in einem Workflow keine neue JCR-Sitzung abrufen. Sie sollten die von der Prozess-Schritt-API bereitgestellte Workflow-Sitzung an eine JCR-Sitzung anpassen. Beispiel:

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
   * Es wird nicht empfohlen, für einen Prozessschritt eine eigene JCR-Sitzung zu erstellen.

* Durch die Vermeidung unnötiger Speichervorgänge können Sie den Verwaltungsaufwand reduzieren und die Workflows effizienter gestalten.

>[!CAUTION]
>
>Wenn Sie trotz der Empfehlungen hier Ihre eigene JCR-Sitzung erstellen, muss sie gespeichert werden.

### Anzahl/Umfang der Starter minimieren {#minimize-the-number-scope-of-launchers}

Es gibt einen Listener, der für alle [Workflow-Starter](/help/sites-administering/workflows-starting.md#workflows-launchers) registriert sind:

* Er überwacht Änderungen an allen Pfaden, die in den Globbing-Eigenschaften der anderen Starter angegeben sind.
* Wenn ein Ereignis gesendet wird, bewertet die Workflow-Engine jeden Starter, um festzustellen, ob er ausgeführt werden soll.

Das Erstellen zu vieler Starter führt dazu, dass der Evaluierungsprozess langsamer ausgeführt wird.

Wenn Sie einen Globbing-Pfad im Stammverzeichnis des Repositorys in einem einzelnen Starter erstellen, überwacht die Workflow-Engine die Ereignisse zum Erstellen/Ändern jedes Knotens im Repository und wertet sie aus. Daher wird empfohlen, nur erforderliche Starter zu erstellen und den Globbing-Pfad so spezifisch wie möglich zu gestalten.

Aufgrund der Auswirkungen dieser Starter auf das Workflow-Verhalten kann es auch hilfreich sein, vordefinierte Starter zu deaktivieren, die nicht verwendet werden.

### Konfigurationserweiterungen für Starter {#configuration-enhancements-for-launchers}

Die benutzerdefinierte [Starter-Konfiguration](/help/sites-administering/workflows-starting.md#workflows-launchers) wurde erweitert, um Folgendes zu unterstützen:

* Mehrere Bedingungen &quot;AND&quot;zusammen haben.
* Verwenden Sie ODER-Bedingungen innerhalb einer einzelnen Bedingung.
* Deaktivieren/aktivieren Sie Starter je nachdem, ob ein Feature Flag aktiviert oder deaktiviert ist.
* Unterstützung regulärer Ausdrücke in Starter-Bedingungen

### Workflows nicht aus anderen Workflows starten {#do-not-start-workflows-from-other-workflows}

Workflows können einen erheblichen Mehraufwand verursachen, sowohl im Hinblick auf im Speicher erstellte Objekte als auch auf im Repository nachverfolgte Knoten. Aus diesem Grund ist es besser, einen Workflow seine Verarbeitung selbst durchführen zu lassen, anstatt zusätzliche Workflows zu starten.

Ein Beispiel hierfür wäre ein Workflow, der einen Geschäftsprozess für einen Satz von Inhalten implementiert und diesen Inhalt dann aktiviert. Es ist besser, einen benutzerdefinierten Workflow-Prozess zu erstellen, der jeden dieser Knoten aktiviert, anstatt einen **Inhalt aktivieren** -Modell für die einzelnen Inhaltsknoten erstellen, die veröffentlicht werden müssen. Dieser Ansatz erfordert zusätzliche Entwicklungsarbeiten, ist jedoch bei der Ausführung effizienter als beim Starten einer separaten Workflow-Instanz für jede Aktivierung.

Ein weiteres Beispiel wäre ein Workflow, der mehrere Knoten verarbeitet, ein Workflow-Paket erstellt und dann dieses Paket aktiviert. Anstatt das Paket zu erstellen und anschließend einen separaten Workflow mit dem Paket als Payload zu erstellen, können Sie im Paketerstellungsschritt die Payload Ihres Workflows ändern und dann den Paketaktivierungsschritt innerhalb desselben Workflow-Modells aufrufen.

### Handler-Fortschritt {#handler-advance}

Wenn Sie ein Workflow-Modell entwerfen, können Sie den Handler-Fortschritt für Ihre Workflow-Schritte aktivieren. Alternativ können Sie Ihrem Workflow-Schritt Code hinzufügen, um zu bestimmen, welcher Schritt als Nächstes ausgeführt werden soll, und ihn dann ausführen.

Es wird empfohlen, den Handler-Fortschritt zu verwenden, da sich dadurch die Leistung verbessert.

### Phasen eines Workflows {#workflow-stages}

Sie können [Workflow-Phasen](/help/sites-developing/workflows.md#workflow-stages), und weisen Sie dann einer bestimmten Workflow-Phase Aufgaben/Schritte zu.

Diese Information wird zum Anzeigen des Fortschritts eines Workflows verwendet, wenn Sie auf die Registerkarte [**Workflow-Informationen** eines Arbeitselements aus dem **Posteingang**](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) klicken. Vorhandene Workflow-Modelle können bearbeitet werden, um Statuswerte hinzuzufügen.

### Schritt &quot;Seitenprozess aktivieren&quot; {#activate-page-process-step}

Die **Seitenprozess aktivieren** -Schritt aktiviert Seiten für Sie, aber es werden keine referenzierten DAM-Assets gefunden und auch diese aktiviert.

Dies ist bei der Verwendung dieses Schritts als Teil eines Workflow-Modells zu beachten.

### Überlegungen zum Upgrade {#upgrade-considerations}

Beim Aktualisieren Ihrer Instanz:

* Stellen Sie sicher, dass alle benutzerdefinierten Workflow-Modelle gesichert werden, bevor eine Instanz aktualisiert wird.
* Vergewissern Sie sich, dass keiner Ihrer benutzerdefinierten Workflows unter dem [location](#locations):

   * `/libs/settings/workflow/models/projects`

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Neue Repositorystruktur in AEM 6.5](/help/sites-deploying/repository-restructuring.md).

## Systemwerkzeuge {#system-tools}

Es stehen viele Systemwerkzeuge zur Verfügung, die bei der Überwachung, Wartung und Fehlerbehebung von Workflows helfen. In den folgenden Beispiel-URLs wird zwar `localhost:4502` verwendet, sie sollten aber in jeder Autoreninstanz (`<hostname>:<port>`) verfügbar sein.

### Konsole zur Behandlung von Sling-Aufträgen {#sling-job-handling-console}

`http://localhost:4502/system/console/slingevent`

Die Konsole &quot;Sling Job Handling&quot;zeigt Folgendes an:

* Statistiken zum Status der Vorgänge im System seit dem letzten Neustart.
* Konfigurationen für alle Auftragswarteschlangen sowie ein Tastaturbefehl für die Bearbeitung im Konfigurations-Manager

### Workflow-Berichtswerkzeug {#workflow-report-tool}

Das Workflow-Reporting-Tool wurde in Version 6.3 entfernt, um eine Leistungsbeeinträchtigung zu verhindern.

### MBean für Workflow-Wartungsvorgänge {#workflow-maintenance-operations-mbean}

`http://localhost:4502/system/console/jmx/com.adobe.granite.workflow:type=Maintenance`

Das MBean für die Workflow-Wartung macht eine Reihe praktischer Wartungsroutinen verfügbar – etwa zum Bereinigen abgeschlossener Workflows oder zum Abrufen der Workflow-Statistik.

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* [Arbeiten mit Workflows](/help/sites-authoring/workflows.md)
* [Verwalten von Workflows](/help/sites-administering/workflows.md)
* [Entwickeln und Erweitern von Workflows](/help/sites-developing/workflows.md)
* [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md)
