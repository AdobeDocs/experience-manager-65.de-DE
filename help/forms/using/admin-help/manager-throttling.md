---
title: Work Manager und Einschränkungen
seo-title: Work Manager und Einschränkungen
description: Dieses Dokument stellt Hintergrundinformationen über Work Manager und Anweisungen zum Konfigurieren von Einschränkungsoptionen für Work Manager bereit.
seo-description: Dieses Dokument stellt Hintergrundinformationen über Work Manager und Anweisungen zum Konfigurieren von Einschränkungsoptionen für Work Manager bereit.
uuid: b90998bc-e3d4-493a-9371-55ccb44da20d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 9a8b4e3a-f416-4dc6-a90a-9018df5c844e
exl-id: 1f765de2-1362-4318-9302-c5036e6fa7d6
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 96%

---

# Work Manager und Einschränkungen{#work-manager-and-throttling}

AEM Forms (und frühere Versionen) verwendeten JMS-Warteschlangen, um Vorgänge asynchron auszuführen. In AEM Forms wurden JMS-Warteschlangen durch Work Manager ersetzt. Dieses Dokument stellt Hintergrundinformationen über Work Manager und Anweisungen zum Konfigurieren von Einschränkungsoptionen für Work Manager bereit.

## Informationen zu Vorgängen mit langer Lebensdauer (asynchron) {#about-long-lived-asynchronous-operations}

Die Vorgänge, die von Diensten in AEM Forms ausgeführt werden, können entweder Prozesse mit kurzer Lebensdauer (synchron) oder Prozesse mit langer Lebensdauer (asynchron) sein. Vorgänge mit kurzer Lebensdauer werden synchron mit demselben Thread ausgeführt, von dem sie aufgerufen wurden. Diese Vorgänge warten auf eine Antwort, bevor sie fortgesetzt werden.

Vorgänge mit langer Lebensdauer umfassen möglicherweise Systeme oder gehen über das Unternehmen hinaus, beispielsweise wenn ein Kunde ein Antragsformular für eine Hypothek ausfüllen und einreichen muss und dies Teil einer umfangreicheren Lösung ist, die mehrere automatisierte und von Menschen durchgeführte Aufgaben umfasst. Solche Vorgänge müssen fortgesetzt werden, während auf eine Antwort gewartet wird. Vorgänge mit langer Lebensdauer führen die ihnen zugrunde liegenden Aufgaben asynchron aus, dadurch können Ressourcen anderweitig genutzt werden, während sie darauf warten, beendet zu werden. Im Gegensatz zu einem Vorgang mit kurzer Lebensdauer wird ein Vorgang mit langer Lebensdauer von Work Manager nicht als abgeschlossen betrachtet, sobald er aufgerufen wird. Es muss ein externer Auslöser, z. B. ein System, das einen anderen Vorgang bei demselben Dienst anfordert oder ein Benutzer, der ein Formular sendet, eintreten, um den Vorgang zu beenden.

## Informationen zu Work Manager  {#about-work-manager}

AEM Forms (und frühere Versionen) verwendeten JMS-Warteschlangen, um Vorgänge asynchron auszuführen. AEM Forms verwendet Work Manager, um asynchrone Vorgänge über verwaltete Threads zu planen und auszuführen.

Asynchrone Vorgänge werden wie folgt verarbeitet:

1. Work Manager erhält ein Arbeitselement zur Ausführung.
1. Work Manager speichert das Arbeitselement in einer Datenbanktabelle und ordnet ihm einen eindeutigen Bezeichner zu. Der Datenbankeintrag enthält alle zum Ausführen des Arbeitselements erforderlichen Informationen.
1. Work Manager-Threads übernehmen Arbeitselemente, wenn die Threads frei werden. Vor der Übernahme der Arbeitselemente können Threads überprüfen, ob die erforderlichen Dienste gestartet wurden, ob ausreichend Heap-Größe zum Übernehmen des nächsten Arbeitselements vorhanden ist und ob ausreichend CPU-Zyklen zum Verarbeiten des Arbeitselements vorhanden sind. Work Manager wertet außerdem beim Planen der Ausführung die Attribute des Arbeitselements (z. B. die Priorität) aus.

AEM Forms-Administratoren können außerdem Work Manager-Statistiken, z. B. die Anzahl der Arbeitselemente in der Warteschlange und ihren jeweiligen Status, mithilfe von Health Monitor anzeigen. Sie können Health Monitor außerdem verwenden, um Arbeitselemente anzuhalten, fortzusetzen, es erneut zu versuchen oder sie zu löschen. (Siehe [Statistiken mit Bezug auf Work Manager anzeigen](/help/forms/using/admin-help/view-statistics-related-manager.md#view-statistics-related-to-work-manager).)

## Einschränkungsoptionen für Work Manager konfigurieren  {#configuring-work-manager-throttling-options}

Sie können die Einschränkungen für Work Manager so konfigurieren, dass Arbeitselemente nur geplant werden, wenn ausreichend Arbeitsspeicherressourcen vorhanden sind. Sie können Einschränkungen konfigurieren, indem Sie die folgenden JVM-Optionen für Ihren Anwendungsserver festlegen.

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
   <td><p>Gibt das Zeitintervall in Millisekunden an, das Work Manager beim Überprüfen auf neue Elemente in der Warteschlange verwendet.</p><p>Der Wert für diese Option ist eine Ganzzahl. Der Standardwert ist <code>1000</code> Millisekunden (1 Sekunde). </p><p>Wenn das Volumen asynchroner Aufrufe niedrig ist, können Sie diesen Wert erhöhen. Sie sollten den Wert beispielsweise auf einen Wert zwischen 2000 und 5000 (2 bis 5 Sekunden) erhöhen. </p><p>Wenn das Volumen asynchroner Aufrufe hoch ist, sollte der Standardwert ausreichend sein. Sie können jedoch auch einen niedrigeren Wert verwenden, sofern erforderlich. Wird der Wert zu sehr erhöht (z. B. unter 50, was zu einer Abrufhäufigkeit von 20 Mal pro Sekunde führt), wird das System zu stark überlastet.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.debug-mode-enabled</code></td>
   <td><p>Legen Sie diese Option auf <code>true</code> fest, um den Debug-Modus zu aktivieren, oder auf „false“, um den Modus zu deaktivieren. </p><p>Im Debug-Modus werden Meldungen zu Verstößen gegen Work Manager-Richtlinien sowie Anhalten-/Fortsetzen-Vorgänge in Work Manager protokolliert. Legen Sie diese Option nur beim Beheben von Problemen auf „true“ fest.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.enabled</code></td>
   <td><p>Legen Sie diese Option auf <code>true</code> fest, um die Einschränkungen auf der Basis der unten beschriebenen Einstellungen zur Speicherbelegung zu aktivieren, oder auf <code>false</code>, um die Einschränkungen zu deaktivieren.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.high-limit</code></td>
   <td><p>Gibt den maximalen Prozentsatz des Speicherplatzes an, der verwendet werden kann, bevor Work Manager eingehende Aufträge einschränkt.</p><p>Der Standardwert für diese Option ist <code>95</code>. Dieser Wert sollte für die meisten Systeme ausreichend sein. Erhöhen Sie ihn nur, wenn Ihr System die maximale Kapazität ausnutzen soll. Wenn Sie diesen Wert erhöhen, steigt jedoch auch das Risiko, dass zu wenig Arbeitsspeicher zur Verfügung steht.</p><p>Wenn Sie AEM Forms in einer Clusterumgebung ausführen, möchten Sie möglicherweise die Einstellungen zur Begrenzung der Speicherbelegung auf anderen Knoten des Clusters anders festlegen. Sie können beispielsweise auf Knoten A und B, die in Ihrem Lastenausgleich für interaktive Arbeit programmiert sind, eine niedrigere Obergrenze festlegen. Und auf den Knoten C und D, die nicht von dem Lastenausgleich verwendet werden, jedoch für asynchrone Arbeit reserviert sind, können Sie höhere Obergrenzen festlegen.</p></td>
  </tr>
  <tr>
   <td><code> adobe.workmanager.memory-control.low-limit</code></td>
   <td><p>Gibt den maximalen Prozentsatz des Speicherplatzes an, der verwendet werden kann, bevor Work Manager die Einschränkung für eingehende Aufträge aufhebt.</p><p>Der Standardwert für diese Option ist <code>20</code>. Dieser Wert sollte für die meisten Systeme ausreichend sein.</p></td>
  </tr>
  <tr>
   <td><code>Dadobe.workmanager.allocate.max-batch-size</code></td>
   <td><p>Gibt die maximale Stapelgröße für Workmanager an. Die Standard-Stapelgröße ist 10.</p><p>Wenn der Status eines Vorgangs im Workmanager nicht aktualisiert wird, selbst, wenn die Aufgabe abgeschlossen ist, legen Sie die Stapelgröße auf 1 fest.</p></td>
  </tr>
 </tbody>
</table>

**Java-Optionen zu JBoss hinzufügen**

1. JBoss-Anwendungsserver beenden.
1. Öffnen Sie den *[Anwendungsserver-Stammordner]*/bin/run.bat (Windows) oder run.sh (Linux oder UNIX) in einem Editor und fügen Sie die Java-Optionen nach Bedarf im Format `-Dproperty=value` hinzu.
1. Starten Sie den Server neu.

**Java-Optionen zu WebLogic hinzufügen**

1. Starten Sie WebLogic Administration Console, indem Sie in einen Webbrowser `https://[host name]:[port]/console` eingeben.
1. Geben Sie den von Ihnen erstellten Benutzernamen und das Kennwort für die WebLogic-Serverdomäne ein und klicken Sie unter „Change Center“ auf „Log“ und dann auf „Lock &amp; Edit“.
1. Klicken Sie unter „Domain Structure“ auf Environment> Servers und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten Configuration > Server Start.
1. Fügen Sie im Feld „Arguments“ die erforderlichen Informationen am Ende des aktuellen Inhalts hinzu. Zum Deaktivieren von Health Monitor fügen Sie beispielsweise Folgendes hinzu:

   `-Dadobe.healthmonitor.enabled=false` Deaktiviert Health Monitor.

1. Klicken Sie auf Save und dann auf Activate Changes.
1. Starten Sie WebLogic Managed Server neu.

**Java-Optionen zu WebSphere hinzufügen**

1. Klicken Sie in der Navigationsstruktur von WebSphere Administrative Console auf „Servers“ > „Server Types“ > „WebSphere Application Servers“.
1. Klicken Sie im rechten Fenster auf den Servernamen.
1. Klicken Sie unter „Server Infrastructure“ auf „Arbeitsablauf für Formulare“ > „Process Definition“.
1. Klicken Sie unter „Additional Properties“ auf Java Virtual Machine.
1. Geben Sie in das Feld „Generic JVM Arguments“ die erforderlichen Argumente ein.
1. Klicken Sie auf OK oder Apply und dann auf Save directly to the Master Configuration.
