---
title: Work Manager und Drosselung
description: Dieses Dokument enthält Hintergrundinformationen zu Work Manager sowie Anweisungen zum Konfigurieren der Einschränkungsoptionen für Work Manager.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1f765de2-1362-4318-9302-c5036e6fa7d6
source-git-commit: 7f35fdee9dbca9dfd3992b56579d6d06633f8dec
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 20%

---

# Work Manager und Drosselung{#work-manager-and-throttling}

AEM Formulare (und frühere Versionen) verwendeten JMS-Warteschlangen, um Vorgänge asynchron auszuführen. In AEM Formularen wurden JMS-Warteschlangen durch Work Manager ersetzt. Dieses Dokument enthält Hintergrundinformationen zu Work Manager sowie Anweisungen zum Konfigurieren der Einschränkungsoptionen für Work Manager.

## Über langlebige (asynchrone) Vorgänge {#about-long-lived-asynchronous-operations}

In AEM Formularen können Vorgänge, die von Diensten ausgeführt werden, entweder kurzlebig (synchron) oder langlebig (asynchron) sein. Kurzlebige Vorgänge werden synchron mit demselben Thread ausgeführt, von dem aus sie aufgerufen wurden. Diese Vorgänge warten auf eine Antwort, bevor sie fortgesetzt werden.

Dauerhaft genutzte Vorgänge können Systeme umfassen oder sogar über das Unternehmen hinausgehen, z. B. wenn ein Kunde ein Antragsformular für einen Kreditantrag ausfüllen und als Teil einer größeren Lösung einreichen muss, die mehrere automatisierte und menschliche Aufgaben umfasst. Solche Vorgänge müssen fortgesetzt werden, während eine Antwort erwartet wird. Vorgänge mit langer Lebensdauer führen ihre zugrunde liegenden Aufgaben asynchron aus, sodass Ressourcen bis zum Abschluss anderweitig engagiert werden können. Im Gegensatz zu einem kurzlebigen Vorgang betrachtet Work Manager einen langlebigen Vorgang nicht als abgeschlossen, nachdem er aufgerufen wurde. Ein externer Trigger, z. B. ein System, das einen anderen Vorgang für denselben Dienst anfordert, oder ein Benutzer, der ein Formular sendet, muss auftreten, um den Vorgang abzuschließen.

## Über Work Manager {#about-work-manager}

AEM Formulare (und frühere Versionen) verwendeten JMS-Warteschlangen, um Vorgänge asynchron auszuführen. AEM Formulare verwenden Work Manager, um asynchrone Vorgänge über verwaltete Threads zu planen und auszuführen.

Asynchrone Vorgänge werden wie folgt verarbeitet:

1. Work Manager erhält ein Arbeitselement zur Ausführung.
1. Work Manager speichert das Arbeitselement in einer Datenbanktabelle und weist dem Arbeitselement eine eindeutige Kennung zu. Der Datenbankdatensatz enthält alle Informationen, die zum Ausführen des Arbeitselements erforderlich sind.
1. Work Manager-Threads übernehmen Arbeitselemente, wenn die Threads frei werden. Bevor Sie die Arbeitselemente abrufen, können Threads überprüfen, ob die erforderlichen Dienste gestartet wurden, ob ausreichend Heap-Größe vorhanden ist, um das nächste Arbeitselement abzurufen, und ob ausreichend CPU-Zyklen vorhanden sind, um das Arbeitselement zu verarbeiten. Work Manager wertet bei der Planung der Ausführung auch die Attribute des Arbeitselements (z. B. seine Priorität) aus.

AEM Forms-Administratoren können mithilfe von Health Monitor Work Manager-Statistiken überprüfen, z. B. die Anzahl der Arbeitselemente in der Warteschlange und deren Status. Sie können Health Monitor auch verwenden, um Arbeitselemente anzuhalten, wieder aufzunehmen, es erneut zu versuchen oder zu löschen. (Siehe [Anzeigen von Statistiken im Zusammenhang mit Work Manager](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).

## Einschränkungsoptionen für Work Manager konfigurieren {#configuring-work-manager-throttling-options}

Sie können die Einschränkungen für Work Manager so konfigurieren, dass Arbeitselemente nur geplant werden, wenn genügend Arbeitsspeicherressourcen verfügbar sind. Sie können Einschränkungen konfigurieren, indem Sie die folgenden JVM-Optionen für Ihren Anwendungs-Server festlegen.

<table>
 <thead>
  <tr>
   <th><p>Eigenschaft</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><code> adobe.work-manager.queue-refill-interval</code></td>
   <td><p>Gibt das Zeitintervall (in Millisekunden) an, das Work Manager beim Suchen nach neuen Elementen in der Warteschlange verwendet.</p><p>Der Wert für diese Option ist eine Ganzzahl. Der Standardwert ist <code>1000</code> Millisekunden (1 Sekunde). </p><p>Wenn das Volumen asynchroner Aufrufe gering ist, können Sie diesen Wert erhöhen. Sie können sie beispielsweise auf einen Wert zwischen 2000 und 5000 (2-5 Sekunden) erhöhen. </p><p>Wenn das Volumen asynchroner Aufrufe hoch ist, sollte der Standardwert ausreichend sein, Sie können jedoch bei Bedarf einen niedrigeren Wert verwenden. Eine zu hohe Abnahme dieses Werts (z. B. unter 50, was zu einer Abrufhäufigkeit von 20-mal pro Sekunde führt) verursacht einen erheblichen Mehraufwand für das System.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.debug-mode-enabled</code></td>
   <td><p>Legen Sie diese Option auf <code>true</code> fest, um den Debug-Modus zu aktivieren, oder auf „false“, um den Modus zu deaktivieren. </p><p>Im Debug-Modus werden Meldungen zu Verstößen gegen Richtlinien in Work Manager und zu Pause-/Fortsetzungsaktionen in Work Manager protokolliert. Setzen Sie diese Option nur bei der Fehlerbehebung auf "true".</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.enabled</code></td>
   <td><p>Legen Sie diese Option auf <code>true</code> fest, um die Einschränkungen auf der Basis der unten beschriebenen Einstellungen zur Speicherbelegung zu aktivieren, oder auf <code>false</code>, um die Einschränkungen zu deaktivieren.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.high-limit</code></td>
   <td><p>Gibt den maximalen Prozentsatz des Speicherplatzes an, der verwendet werden kann, bevor Work Manager eingehende Aufträge einschränkt.</p><p>Der Standardwert für diese Option ist <code>95</code>. Dieser Wert sollte für die meisten Systeme ausreichend sein. Erhöhen Sie sie nur, wenn Ihr System die maximale Kapazität erreichen muss. Beachten Sie jedoch, dass sich mit der Erhöhung dieses Werts auch das Risiko von Problemen mit ungenügendem Arbeitsspeicher erhöht.</p><p>Wenn Sie AEM Formulare in einer Clusterumgebung ausführen, sollten Sie die Einstellungen für die Speicherbegrenzungsbegrenzung auf verschiedenen Knoten des Clusters anders festlegen. Sie könnten beispielsweise eine niedrigere Obergrenze für Knoten A und B festlegen, die in Ihrem Lastenausgleich für interaktive Arbeit programmiert sind. Und Sie könnten höhere Obergrenzen für die Knoten C und D festlegen, die nicht vom Lastenausgleich verwendet, sondern für asynchrone Arbeit reserviert sind.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.low-limit</code></td>
   <td><p>Gibt den maximalen Prozentsatz des Arbeitsspeichers an, der verwendet werden kann, bevor Work Manager die Beschränkung eingehender Aufträge stoppt.</p><p>Der Standardwert für diese Option ist <code>20</code>. Dieser Wert sollte für die meisten Systeme ausreichend sein.</p></td>
  </tr>
  <tr>
   <td><code>Dadobe.workmanager.allocate.max-batch-size</code></td>
   <td><p>Gibt die maximale Stapelgröße für Workmanager an. Die standardmäßige Batch-Größe beträgt 10.</p><p>Wenn der Status eines Prozesses im Workmanager auch nach Abschluss der Aufgabe nicht aktualisiert wird, legen Sie die Stapelgröße auf 1 fest.</p></td>
  </tr>
 </tbody>
</table>

**Java-Optionen zu JBoss hinzufügen**

1. Beenden Sie den JBoss-Anwendungsserver.
1. Öffnen Sie den Ordner „*[Anwendungs-Server-Stammordner]*/bin/run.bat“ (Windows) oder „run.sh“ (Linux oder UNIX) in einem Texteditor und fügen Sie die erforderlichen Java-Optionen im Format `-Dproperty=value` hinzu.
1. Starten Sie den Server neu.

**Java-Optionen zu WebLogic hinzufügen**

1. Starten Sie WebLogic-Administrationskonsole, indem Sie `https://[host name]:[port]/console` in einen Webbrowser eingeben.
1. Geben Sie den von Ihnen erstellten Benutzernamen und das Kennwort für die WebLogic-Server-Domain ein und klicken Sie unter „Change Center“ auf „Log“ und dann auf „Lock &amp; Edit“.
1. Klicken Sie unter „Domain Structure“ auf Environment > Servers und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten „Configuration“ > „Server-Start“.
1. Hängen Sie im Feld Argumente die erforderlichen Argumente an das Ende des aktuellen Inhalts an. Um beispielsweise Health Monitor zu deaktivieren, fügen Sie Folgendes hinzu:

   `-Dadobe.healthmonitor.enabled=false` deaktiviert den Health Monitor.

1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie den verwalteten WebLogic-Server neu.

**Java-Optionen zu WebSphere hinzufügen**

1. Klicken Sie in der Navigationsstruktur von WebSphere Administrative Console auf Servers > Server Types > WebSphere application servers.
1. Klicken Sie im rechten Bereich auf den Servernamen.
1. Klicken Sie unter &quot;Server Infrastructure&quot;auf Java and forms workflow > Process Definition.
1. Klicken Sie unter &quot;Additional Properties&quot;auf Java Virtual Machine.
1. Geben Sie in das Feld Generic JVM arguments die erforderlichen Argumente ein.
1. Klicken Sie auf OK oder Apply und dann auf Save directly to the master configuration .
