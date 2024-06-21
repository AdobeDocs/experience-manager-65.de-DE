---
title: Work Manager und Drosselung
description: Dieses Dokument stellt Hintergrundinformationen über Work Manager und Anweisungen zum Konfigurieren von Einschränkungsoptionen für Work Manager bereit.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1f765de2-1362-4318-9302-c5036e6fa7d6
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 100%

---

# Work Manager und Drosselung{#work-manager-and-throttling}

AEM Forms und frühere Versionen setzten auf JMS-Warteschlangen, um Vorgänge asynchron auszuführen. In AEM Forms wurden JMS-Warteschlangen durch Work Manager ersetzt. Dieses Dokument stellt Hintergrundinformationen über Work Manager und Anweisungen zum Konfigurieren von Einschränkungsoptionen für Work Manager bereit.

## Informationen zu Vorgängen mit langer Lebensdauer (asynchron) {#about-long-lived-asynchronous-operations}

Die Vorgänge, die von Diensten in AEM Forms ausgeführt werden, können entweder Prozesse mit kurzer Lebensdauer (synchron) oder Prozesse mit langer Lebensdauer (asynchron) sein. Vorgänge mit kurzer Lebensdauer werden synchron mit demselben Thread ausgeführt, von dem sie aufgerufen wurden. Diese Vorgänge warten auf eine Antwort, bevor sie fortgesetzt werden.

Vorgänge mit langer Lebensdauer können ganze Systeme umspannen oder über die Organisation hinausgehen. Dies ist beispielsweise der Fall, wenn eine Kundin oder ein Kunde im Rahmen einer umfangreicheren Lösung, die mehrere automatisierte und von Menschen durchgeführte Aufgaben umfasst, einen Hypothekenantrag ausfüllen und einreichen muss. Solche Vorgänge müssen fortgesetzt werden, während auf eine Antwort gewartet wird. Vorgänge mit langer Lebensdauer führen die ihnen zugrunde liegenden Aufgaben asynchron aus. Dadurch können Ressourcen anderweitig genutzt werden, während auf den Abschluss gewartet wird. Im Gegensatz zu einem Vorgang mit kurzer Lebensdauer wird ein Vorgang mit langer Lebensdauer von Work Manager nicht als abgeschlossen betrachtet, sobald er aufgerufen wird. Es muss ein externer Auslöser vorhanden sein, damit der Vorgang beendet wird, z. B. ein System, das einen anderen Vorgang bei demselben Dienst anfordert, oder eine Person, die ein Formular sendet.

## Informationen zu Work Manager {#about-work-manager}

AEM Forms und frühere Versionen setzten auf JMS-Warteschlangen, um Vorgänge asynchron auszuführen. AEM Forms nutzt Work Manager, um asynchrone Vorgänge über verwaltete Threads zu planen und auszuführen.

Asynchrone Vorgänge werden wie folgt verarbeitet:

1. Work Manager erhält ein Arbeitselement zur Ausführung.
1. Work Manager speichert das Arbeitselement in einer Datenbanktabelle und weist diesem eine eindeutige Kennung zu. Der Datenbankeintrag enthält alle zum Ausführen des Arbeitselements erforderlichen Informationen.
1. Work Manager-Threads übernehmen Arbeitselemente, wenn die Threads frei werden. Vor der Übernahme der Arbeitselemente können Threads überprüfen, ob die erforderlichen Dienste gestartet wurden, ob die Heap-Größe zum Übernehmen des nächsten Arbeitselements ausreicht und ob genügend CPU-Zyklen zum Verarbeiten des Arbeitselements vorhanden sind. Work Manager wertet außerdem beim Planen der Ausführung die Attribute des Arbeitselements (z. B. die Priorität) aus.

AEM Forms-Admins können außerdem Work Manager-Statistiken, z. B. die Anzahl der Arbeitselemente in der Warteschlange und ihren jeweiligen Status, mithilfe von Health Monitor anzeigen. Sie können Health Monitor auch verwenden, um Arbeitselemente anzuhalten, fortzusetzen, zu wiederholen oder zu löschen. (Siehe [Anzeigen von Statistiken mit Bezug auf Work Manager](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).)

## Konfigurieren von Einschränkungsoptionen für Work Manager {#configuring-work-manager-throttling-options}

Sie können die Einschränkungen für Work Manager so konfigurieren, dass Arbeitselemente nur geplant werden, wenn der Arbeitsspeicher dafür ausreicht. Sie können Einschränkungen konfigurieren, indem Sie die folgenden JVM-Optionen für Ihren Anwendungs-Server festlegen.

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
   <td><p>Gibt das Zeitintervall in Millisekunden an, das Work Manager beim Überprüfen auf neue Elemente in der Warteschlange verwendet.</p><p>Der Wert für diese Option ist eine Ganzzahl. Der Standardwert ist <code>1000</code> Millisekunden (1 Sekunde). </p><p>Wenn die Anzahl asynchroner Aufrufe niedrig ist, können Sie diesen Wert erhöhen, beispielsweise auf einen Wert zwischen 2000 und 5000 (2–5 Sekunden). </p><p>Wenn die Anzahl asynchroner Aufrufe hoch ist, sollte der Standardwert ausreichend sein. Sie können jedoch auch einen niedrigeren Wert verwenden, sofern erforderlich. Wird der Wert zu stark verringert (z. B. unter 50, was zu einer Abrufhäufigkeit von 20 Mal pro Sekunde führt), wird das System deutlich überlastet.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.debug-mode-enabled</code></td>
   <td><p>Legen Sie diese Option auf <code>true</code> fest, um den Debug-Modus zu aktivieren, oder auf „false“, um den Modus zu deaktivieren. </p><p>Im Debug-Modus werden Meldungen zu Verstößen gegen Work Manager-Richtlinien sowie Anhalten-/Fortsetzen-Vorgänge in Work Manager protokolliert. Legen Sie diese Option nur bei der Fehlerbehebung auf „true“ fest.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.enabled</code></td>
   <td><p>Legen Sie diese Option auf <code>true</code> fest, um die Einschränkungen auf der Basis der unten beschriebenen Einstellungen zur Speicherbelegung zu aktivieren, oder auf <code>false</code>, um die Einschränkungen zu deaktivieren.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.high-limit</code></td>
   <td><p>Gibt den maximalen Prozentsatz des Speicherplatzes an, der verwendet werden kann, bevor Work Manager eingehende Aufträge einschränkt.</p><p>Der Standardwert für diese Option ist <code>95</code>. Dieser Wert sollte für die meisten Systeme ausreichend sein. Erhöhen Sie ihn nur, wenn Ihr System die maximale Kapazität ausnutzen soll. Wenn Sie diesen Wert erhöhen, steigt jedoch auch das Risiko, dass zu wenig Arbeitsspeicher zur Verfügung steht.</p><p>Wenn Sie AEM Forms in einer Cluster-Umgebung ausführen, sollten Sie ggf. die Einstellungen zur Begrenzung der Speicherbelegung auf anderen Knoten des Clusters anders festlegen. Sie könnten beispielsweise eine niedrigere Obergrenze für Knoten A und B festlegen, die in Ihrem Lastenausgleich für interaktive Arbeit programmiert sind. Und Sie könnten höhere Obergrenzen für die Knoten C und D festlegen, die nicht vom Lastenausgleich verwendet werden, sondern für asynchrone Arbeit reserviert sind.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.low-limit</code></td>
   <td><p>Gibt den maximalen Prozentsatz des Speicherplatzes an, der verwendet werden kann, bevor Work Manager die Einschränkung für eingehende Aufträge aufhebt.</p><p>Der Standardwert für diese Option ist <code>20</code>. Dieser Wert sollte für die meisten Systeme ausreichend sein.</p></td>
  </tr>
  <tr>
   <td><code>Dadobe.workmanager.allocate.max-batch-size</code></td>
   <td><p>Gibt die maximale Batch-Größe für Work Manager an. Die Standard-Batch-Größe ist 10.</p><p>Wenn der Status eines Prozesses im Work-Manager auch nach Abschluss der Aufgabe nicht aktualisiert wird, legen Sie die Batch-Größe auf 1 fest.</p></td>
  </tr>
 </tbody>
</table>

**Hinzufügen von Java-Optionen zu JBoss**

1. Beenden Sie den JBoss-Anwendungs-Server.
1. Öffnen Sie den Ordner „*[Anwendungs-Server-Stammordner]*/bin/run.bat“ (Windows) oder „run.sh“ (Linux oder UNIX) in einem Texteditor und fügen Sie die erforderlichen Java-Optionen im Format `-Dproperty=value` hinzu.
1. Starten Sie den Server neu.

**Hinzufügen von Java-Optionen zu WebLogic**

1. Starten Sie WebLogic-Administrationskonsole, indem Sie `https://[host name]:[port]/console` in einen Webbrowser eingeben.
1. Geben Sie den von Ihnen erstellten Benutzernamen und das Kennwort für die WebLogic-Server-Domain ein und klicken Sie unter „Change Center“ auf „Log“ und dann auf „Lock &amp; Edit“.
1. Klicken Sie unter „Domain Structure“ auf Environment > Servers und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten „Configuration“ > „Server-Start“.
1. Fügen Sie im Feld „Argumente“ die erforderlichen Argumente am Ende des aktuellen Inhalts hinzu. Um beispielsweise Health Monitor zu deaktivieren, fügen Sie Folgendes hinzu:

   `-Dadobe.healthmonitor.enabled=false` deaktiviert den Health Monitor.

1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie WebLogic Managed Server neu.

**Hinzufügen von Java-Optionen zu WebSphere**

1. Klicken Sie in der Navigationsstruktur von WebSphere Administrative Console auf „Server“ > „Server-Typen“ > „WebSphere Application Servers“.
1. Klicken Sie im rechten Bereich auf den Namen des Servers.
1. Klicken Sie unter „Server-Infrastruktur“ auf „Java und Forms Workflow“ > „Prozessdefinition“.
1. Klicken Sie unter „Zusätzliche Eigenschaften“ auf „Java Virtual Machine“.
1. Geben Sie in das Feld „Generische JVM-Argumente“ die erforderlichen Argumente ein.
1. Klicken Sie auf „OK“ oder „Anwenden“ und dann auf „Save directly to the master configuration“.
