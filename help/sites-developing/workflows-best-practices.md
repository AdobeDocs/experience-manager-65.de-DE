---
title: Best Practices für Workflows
description: Erfahren Sie mehr über die Best Practices für die Arbeit mit Workflows in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 14775476-6fe5-4583-8ab5-b55fef892174
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1925'
ht-degree: 100%

---

# Best Practices für Workflows{#workflow-best-practices}

Workflows ermöglichen die Automatisierung von Aktivitäten in Adobe Experience Manager (AEM).

Sie stellen oft einen großen Teil der Verarbeitung dar, die in einer AEM-Umgebung stattfindet. Wenn also benutzerdefinierte Workflow-Schritte nicht gemäß den Best Practices geschrieben werden oder native Workflows nicht so konfiguriert sind, dass sie so effizient wie möglich ausgeführt werden, kann dies Auswirkungen auf das System haben.

Wir empfehlen daher dringend, Workflow-Implementierungen sorgfältig zu planen.

## Konfiguration {#configuration}

Beim Konfigurieren von Workflow-Prozessen (angepasst und/oder vorkonfiguriert) sollten einige Aspekte beachtet werden.

### Übergangs-Workflows {#transient-workflows}

Um hohe Aufnahmemengen zu optimieren, können Sie einen [Workflow als vorübergehend](/help/sites-developing/workflows.md#transient-workflows) definieren.

Wenn ein Workflow vorübergehend ist, werden die Laufzeitdaten, die sich auf die Zwischenarbeitsschritte beziehen, bei ihrer Ausführung nicht im JCR festgehalten (die Ausgabedarstellungen werden aber beibehalten).

Zu den Vorteilen zählen:

* Verringerung der Verarbeitungszeit des Workflows um bis zu 10 %.
* Erhebliche Verringerung des Repository-Wachstums.
* Es sind keine CRUD-Workflows mehr zum Bereinigen erforderlich.
* Darüber hinaus wird die Anzahl der zu komprimierenden TAR-Dateien reduziert.

>[!CAUTION]
>
>Falls Ihr Unternehmen Workflow-Laufzeitdaten zu Auditzwecken aufbewahren muss, aktivieren Sie diese Funktion nicht.

### Anpassen von DAM-Workflows {#tuning-dam-workflows}

Richtlinien zur Leistungsoptimierung von DAM-Workflows finden Sie im [Handbuch zur Leistungsoptimierung von AEM Assets](/help/assets/performance-tuning-guidelines.md).

### Konfigurieren der maximalen Anzahl gleichzeitiger Workflows {#configure-the-maximum-number-of-concurrent-workflows}

AEM kann die gleichzeitige Ausführung mehrerer Workflow-Threads zulassen. Standardmäßig ist die Anzahl der Threads auf die Hälfte der Anzahl der Prozessorkerne des Systems festgelegt.

In Fällen, in denen die ausgeführten Workflows sehr viele Systemressourcen beanspruchen, kann dies bedeuten, dass AEM für andere Aufgaben wie das Rendern der Authoring-Benutzeroberfläche wenig Ressourcen zur Verfügung stehen. Dies kann dazu führen, dass das System bei Aktivitäten wie etwa dem Massenhochladen von Bildern nur noch langsam reagiert.

Um dieses Problem zu beheben, empfiehlt sich, die Anzahl der **maximalen parallelen Aufträge** auf einen Wert festzulegen, der zwischen der Hälfte und drei Vierteln der Anzahl der Prozessorkerne des Systems liegt. Dadurch sollte dem System genügend Kapazität zur Verfügung stehen, damit solche Workflows ohne Beeinträchtigung der Reaktionsfähigkeit verarbeitet werden können.

Die **maximale Anzahl paralleler Aufträge** kann wie folgt konfiguriert werden:

* Konfigurieren Sie die **[OSGi-Konfiguration](/help/sites-deploying/configuring-osgi.md)** über die AEM-Web-Konsole für **Warteschlange: Granite Workflow-Warteschlange** (eine **Warteschlangenkonfiguration für Apache Sling-Aufträge**).

* Konfigurieren Sie die Warteschlange über die Option **Sling-Aufträge** der AEM-Web-Konsole für **Auftragswarteschlange-Konfiguration: Granite Workflow-Warteschlange** unter `http://localhost:4502/system/console/slingevent`.

Darüber hinaus gibt es eine separate Konfiguration für die **Granite-Workflow-Warteschlange für externe Verarbeitungsaufträge**. Dies wird für Workflow-Prozesse verwendet, die externe Binärdateien starten, wie **InDesign Server** oder **Image Magick**.

### Konfigurieren einzelner Auftragswarteschlangen {#configure-individual-job-queues}

In einigen Fällen ist es nützlich, einzelne Auftragswarteschlangen zu konfigurieren, um parallele Threads oder andere Warteschlangenoptionen auf Basis einzelner Aufträge zu steuern. Sie können eine einzelne Warteschlange von der Web-Konsole aus über die **Apache Sling Job Queue Configuration**-Factory hinzufügen und konfigurieren. Führen Sie zum Ermitteln des entsprechenden Themas das Modell Ihres Workflows aus und suchen Sie es in der Konsole **Sling Jobs**, beispielsweise unter `http://localhost:4502/system/console/slingevent`.

Individuelle Auftragswarteschlangen können auch für Verlaufs-Workflows hinzugefügt werden.

### Konfigurieren der Workflow-Bereinigung {#configure-workflow-purging}

In einer standardmäßigen Installation bietet AEM eine Wartungskonsole, in der tägliche und wöchentliche Wartungsaktivitäten geplant und konfiguriert werden können, z. B. bei:

`http://localhost:4502/libs/granite/operations/content/maintenance.html`

Standardmäßig hat das **wöchentliche Wartungsfenster** eine Aufgabe zur **Workflow-Bereinigung**, diese muss jedoch konfiguriert werden, bevor sie ausgeführt werden kann. Um die Workflow-Bereinigung zu konfigurieren, muss eine neue **Adobe Granite-Workflow-Bereinigungskonfiguration** in der Web-Konsole hinzugefügt werden.

Weitere Informationen zu Wartungsaufgaben in AEM finden Sie im [Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md).

## Anpassung {#customization}

Beim Schreiben benutzerdefinierter Workflow-Prozesse sollten einige Aspekte beachtet werden.

### Speicherorte {#locations}

Definitionen von Workflow-Modellen, -Startern, -Skripten und -Benachrichtigungen werden im entsprechenden Repository für den jeweiligen Typ gespeichert, also beispielsweise unter „vorkonfiguriert“ oder „benutzerdefiniert“.

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Neue Repositorystruktur in AEM 6.5](/help/sites-deploying/repository-restructuring.md).

#### Speicherorte – Workflow-Modelle {#locations-workflow-models}

Workflow-Modelle werden im Repository nach Typ gespeichert:

* Vorkonfigurierte Workflow-Designs sind unter dem folgenden Pfad zu finden:

  `/libs/settings/workflow/models/`

  >[!CAUTION]
  >
  >Vermeiden Sie Folgendes:
  >
  >* Platzieren Sie keine benutzerdefinierten Workflow-Modelle in diesem Ordner.
  >* Lassen Sie alles in `/libs` unverändert.
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

#### Speicherorte – Workflow-Starter {#locations-workflow-launchers}

Definitionen für Workflow-Starter werden im Repository ebenfalls auf der Grundlage ihres Typs gespeichert:

* Pfad für vorkonfigurierte Workflow-Starter:

  `/libs/settings/workflow/launcher/`

  >[!CAUTION]
  >
  >Vermeiden Sie Folgendes:
  >
  >* Platzieren von benutzerdefinierten Workflow-Startern in diesem Ordner.
  >* Lassen Sie alles in `/libs` unverändert.
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

#### Speicherorte – Workflow-Skripte {#locations-workflow-scripts}

Workflow-Skripte werden im Repository ebenfalls auf der Grundlage ihres Typs gespeichert:

* Pfad für vorkonfigurierte Workflow-Skripte:

  `/libs/workflow/scripts/`

  >[!CAUTION]
  >
  >Vermeiden Sie Folgendes:
  >
  >* Platzieren von benutzerdefinierten Workflow-Skripten in diesem Ordner.
  >* Lassen Sie alles in `/libs` unverändert.
  >
  >Vorgenommene Änderungen werden unter Umständen bei einem Upgrade oder beim Installieren von Hotfixes, Cumulative Fix Packs oder Service Packs überschrieben.

* Pfad für benutzerdefinierte Workflow-Skripte:

  ```
  /apps/workflow/scripts/...
  ```

* Pfad für ältere Workflow-Skripte:

  `/etc/workflow/scripts/`

#### Speicherorte – Workflow-Benachrichtigungen {#locations-workflow-notifications}

Workflow-Benachrichtigungen werden im Repository ebenfalls auf der Grundlage ihres Typs gespeichert:

* Pfad für vorkonfigurierte Workflow-Benachrichtigungsdefinitionen:

  `/libs/settings/workflow/notification/`

  >[!CAUTION]
  >
  >Vermeiden Sie Folgendes:
  >
  >* Platzieren benutzerdefinierter Workflow-Benachrichtigungsdefinitionen in diesem Ordner.
  >* Lassen Sie alles in `/libs` unverändert.
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

Wie bei jeder benutzerdefinierten Entwicklung empfiehlt es sich, nach Möglichkeit die Sitzung einer Person zu verwenden. Dies hat folgende Vorteile:

* Optimale Einhaltung der Sicherheitsrichtlinien
* Verwaltung des Öffnens und Schließens der Sitzung durch das System

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

* Unnötige Speichervorgänge zu vermeiden, bedeutet weniger Mehraufwand und somit eine höhere Workflow-Effizienz.

>[!CAUTION]
>
>Sollten Sie entgegen den hier angegebenen Empfehlungen eine eigene JCR-Sitzung erstellen, muss diese gespeichert werden.

### Verringern von Anzahl/Umfang der Starter {#minimize-the-number-scope-of-launchers}

Es gibt einen Listener, der für alle registrierten [Workflow-Starter](/help/sites-administering/workflows-starting.md#workflows-launchers) zuständig ist:

* Er lauscht auf Änderungen an allen Pfaden, die in den Globbing-Eigenschaften der anderen Starter angegeben sind.
* Wenn ein Ereignis übermittelt wird, wertet die Workflow-Engine die einzelnen Starter aus, um zu ermitteln, ob sie ausgeführt werden sollen.

Eine zu hohe Anzahl von Startern verlangsamt diese Auswertung.

Die Erstellung eines Globbing-Pfads am Stamm des Repositorys für einen einzelnen Starter führt dazu, dass die Workflow-Engine auf Erstellungs-/Änderungsereignisse für jeden Knoten im Repository lauscht und diese auswertet. Es empfiehlt sich daher, nur Starter zu erstellen, die wirklich benötigt werden, und den Globbing-Pfad so spezifisch wie möglich zu machen.

Angesichts der Auswirkungen, die diese Starter auf das Workflow-Verhalten haben, kann es hilfreich sein, alle ungenutzten vorkonfigurierten Starter zu deaktivieren.

### Konfigurationserweiterungen für Starter {#configuration-enhancements-for-launchers}

Die benutzerdefinierte [Starter-Konfiguration](/help/sites-administering/workflows-starting.md#workflows-launchers) wurde erweitert, um Folgendes zu unterstützen:

* Verknüpfung mehrerer Bedingungen mit „UND“
* Verwendung von ODER-Bedingungen innerhalb einer einzelnen Bedingung
* Deaktivierung/Aktivierung von Startern auf Grundlage des Aktivierungsstatus eines Funktions-Flags
* Unterstützung regulärer Ausdrücke in Starter-Bedingungen

### Kein Start von Workflows über andere Workflows {#do-not-start-workflows-from-other-workflows}

Durch die Objekterstellung im Speicher sowie durch die Knotenüberwachung im Repository können Workflows zu erheblichem Mehraufwand führen. Es empfiehlt sich daher, die Verarbeitung eines Workflows innerhalb dieses Workflows abzuwickeln, anstatt weitere Workflows zu starten.

Ein Beispiel wäre etwa ein Workflow, der einen Geschäftsprozess für eine Gruppe von Inhalten implementiert und die Inhalte anschließend aktiviert. Es ist besser, einen benutzerdefinierten Workflow-Prozess zu erstellen, der jeden dieser Knoten aktiviert, anstatt für jeden der zu veröffentlichenden Inhaltsknoten ein Modell vom Typ **Inhalt aktivieren** zu starten. Dieser Ansatz führt zwar zu einem höheren Entwicklungsaufwand, ist aber effizienter, als für jede Aktivierung eine separate Workflow-Instanz zu starten.

Ein weiteres Beispiel wäre ein Workflow, der mehrere Knoten verarbeitet, ein Workflow-Paket erstellt und dieses Paket anschließend aktiviert. Anstatt das Paket zu erstellen und anschließend einen separaten Workflow mit dem Paket als Payload zu erstellen, können Sie im Paketerstellungsschritt die Payload Ihres Workflows ändern und dann den Paketaktivierungsschritt innerhalb desselben Workflow-Modells aufrufen.

### Handler-Fortschritt {#handler-advance}

Wenn Sie ein Workflow-Modell entwerfen, können Sie den Handler-Fortschritt für Ihre Workflow-Schritte aktivieren. Sie können Ihrem Workflow-Schritt auch Code hinzufügen, um den als Nächstes auszuführenden Schritt zu bestimmen und auszuführen.

Es wird empfohlen, den Handler-Fortschritt zu verwenden, da sich dadurch die Leistung verbessert.

### Phasen eines Workflows {#workflow-stages}

Sie können [Workflow-Statuswerte](/help/sites-developing/workflows.md#workflow-stages) definieren und Aufgaben/Schritte einem bestimmten Workflow-Status zuweisen.

Diese Information wird zum Anzeigen des Fortschritts eines Workflows verwendet, wenn Sie auf die Registerkarte [**Workflow-Informationen** eines Arbeitselements aus dem **Posteingang**](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) klicken. Vorhandene Workflow-Modelle können bearbeitet werden, um Statuswerte hinzuzufügen.

### Prozessschritt „Seite aktivieren“ {#activate-page-process-step}

Der Prozessschritt **Seite aktivieren** aktiviert zwar Seiten für Sie, es werden durch diesen Schritt aber nicht automatisch referenzierte DAM-Assets gesucht und aktiviert.

Berücksichtigen Sie dies, wenn Sie diesen Schritt im Rahmen eines Workflow-Modells verwenden möchten.

### Überlegungen zu Upgrades {#upgrade-considerations}

Wichtige Punkte bei Upgrades für Ihre Instanz:

* Sichern Sie alle benutzerdefinierten Workflow-Modelle, bevor Sie ein Upgrade für eine Instanz durchführen.
* Vergewissern Sie sich, dass keiner Ihrer benutzerdefinierten Workflows am folgenden [Speicherort](#locations) gespeichert ist:

   * `/libs/settings/workflow/models/projects`

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Neue Repositorystruktur in AEM 6.5](/help/sites-deploying/repository-restructuring.md).

## System-Tools {#system-tools}

Für die Überwachung, Verwaltung und Problembehandlung von Workflows stehen zahlreiche System-Tools zur Verfügung. In den folgenden Beispiel-URLs wird zwar `localhost:4502` verwendet, sie sollten aber in jeder Autoreninstanz (`<hostname>:<port>`) verfügbar sein.

### Konsole zur Behandlung von Sling-Aufträgen {#sling-job-handling-console}

`http://localhost:4502/system/console/slingevent`

In der Konsole zur Behandlung von Sling-Aufträgen wird Folgendes angezeigt:

* Statistik zum Zustand von Aufträgen im System seit dem letzten Neustart
* Konfigurationen für alle Auftragswarteschlangen sowie ein Tastaturbefehl für die Bearbeitung im Konfigurations-Manager

### Workflow-Berichts-Tool {#workflow-report-tool}

Das Workflow-Berichts-Tool wird in Version 6.3 entfernt, um die Leistung nicht zu beeinträchtigen.

### MBean für Workflow-Wartungsvorgänge {#workflow-maintenance-operations-mbean}

`http://localhost:4502/system/console/jmx/com.adobe.granite.workflow:type=Maintenance`

Das MBean für die Workflow-Wartung macht eine Reihe praktischer Wartungsroutinen verfügbar – etwa zum Bereinigen abgeschlossener Workflows oder zum Abrufen der Workflow-Statistik.

## Weiterführende Informationen {#further-information}

Weitere Informationen finden Sie unter:

* [Arbeiten mit Workflows](/help/sites-authoring/workflows.md)
* [Verwalten von Workflows](/help/sites-administering/workflows.md)
* [Entwickeln und Erweitern von Workflows](/help/sites-developing/workflows.md)
* [Leistungsoptimierung](/help/sites-deploying/configuring-performance.md)
