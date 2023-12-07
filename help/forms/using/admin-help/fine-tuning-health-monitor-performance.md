---
title: Optimieren der Leistung bei der Systemüberwachung
description: Erfahren Sie, wie Sie die Leistung von Health Monitor optimieren können. Steuern Sie die Systemstatistiken, die sich auf die Leistung der Formularumgebung auswirken, mithilfe der JAVA-Einstellungsoption.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 41042e08-5e14-4809-89b7-16d98a72d1b4
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 33%

---

# Optimieren der Leistung bei der Systemüberwachung{#fine-tuning-health-monitor-performance}

Das Erfassen der Systemstatistiken, die in Health Monitor eingetragen sind, hat gewisse Auswirkungen auf die Leistung Ihrer AEM Formularumgebung. Diese Auswirkung kann durch Festlegen der unten aufgeführten Java-Optionen in Ihrem Anwendungsserver gesteuert werden.

<table>
 <thead>
  <tr>
   <th><p>Eigenschaft</p></th>
   <th><p>Zweck</p></th>
   <th><p>Standardwert</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>adobe.healthmonitor.enabled</p></td>
   <td><p>Aktivieren oder Deaktivieren des Health Monitor-Threads</p></td>
   <td><p>Ja</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.statistics-enabled</p></td>
   <td><p>Gemfire-Zwischenspeicherung aktivieren oder deaktivieren</p></td>
   <td><p>Ja</p></td>
  </tr>
  <tr>
   <td><p>adobe.healthmonitor.refresh-interval</p></td>
   <td><p>Das Intervall in Millisekunden, nach dem der Health Monitor-Thread die Statistiken erfasst</p></td>
   <td><p>10 Minuten (600.000 Millisekunden)</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.multicast-port</p></td>
   <td><p>Der Multicast-Anschluss, der zum Kommunizieren mit anderen Mitgliedern des gelieferten Systems verwendet wird. Wenn der Wert auf null gesetzt ist, ist Multicast sowohl für die Mitgliedererkennung als auch für die Verteilung deaktiviert. </p><p>Hinweis: Wählen Sie verschiedene Multicast-Adressen und Ports für verschiedene verteilte Systeme aus. Verwenden Sie nicht nur unterschiedliche Adressen.</p></td>
   <td><p>Kein Standardwert. Gültige Werte liegen zwischen 0 und 65535.</p></td>
  </tr>
  <tr>
   <td><p>statistic-sample-rate</p></td>
   <td><p>Die Rate in Millisekunden, mit der Statistiken gesampelt werden. Betriebssystemstatistiken werden nur aktualisiert, wenn ein Beispiel verwendet wird.</p></td>
   <td><p>600000</p></td>
  </tr>
  <tr>
   <td><p>adobe.workmanager.healthmonitor.enabled</p></td>
   <td><p>Diese Eigenschaft aktiviert oder deaktiviert die Work Manager-Statistiksammlung, z. B. die Auftrags- oder Arbeitselementzählung.</p></td>
   <td><p>Ja</p></td>
  </tr>
 </tbody>
</table>

## Java-Optionen zu JBoss hinzufügen {#add-java-options-to-jboss}

1. Beenden Sie den JBoss-Anwendungsserver.
1. Öffnen Sie „*[Programm-Server-Stammordner]*/bin/run.bat“ (Windows) oder „run.sh“ (Linux oder UNIX) in einem Texteditor und fügen Sie die Java-Optionen Ihren Anforderungen entsprechend hinzu.
1. Starten Sie den Server neu.

## Java-Optionen zu WebLogic hinzufügen {#add-java-options-to-weblogic}

1. Starten Sie die WebLogic-Administration-Console, indem Sie „https://[Hostname]:&#39;port&#39;/console“ in die Adresszeile eines Webbrowsers eingeben.
1. Geben Sie den von Ihnen erstellten Benutzernamen und das Kennwort für die WebLogic-Server-Domain ein und klicken Sie unter „Change Center“ auf „Log“ und dann auf „Lock &amp; Edit“.
1. Klicken Sie unter „Domain Structure“ auf Environment > Servers und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten „Configuration“ > „Server-Start“.
1. Hängen Sie im Feld Argumente die erforderlichen Argumente an das Ende des aktuellen Inhalts an. Wenn Sie beispielsweise „‑ `Dadobe.healthmonitor.enabled=false`“ hinzufügen, wird Health Monitor deaktiviert.
1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie den verwalteten WebLogic-Server neu.

## Java-Optionen zu WebSphere hinzufügen {#add-java-options-to-websphere}

1. Führen Sie in der Navigationsstruktur von WebSphere Administrative Console die folgenden Schritte für Ihren Anwendungsserver aus:

   (WebSphere 6.x) Klicken Sie auf Servers > Application servers .

   (WebSphere 7.x) Klicken Sie auf Servers > Server Types > WebSphere application servers

1. Klicken Sie im rechten Bereich auf den Servernamen.
1. Klicken Sie unter &quot;Server Infrastructure&quot;auf Java and forms workflow > Process Definition.
1. Klicken Sie unter &quot;Additional Properties&quot;auf Java Virtual Machine.
1. Geben Sie in das Feld Generic JVM arguments die erforderlichen Argumente ein.
1. Klicken Sie auf OK oder Apply und dann auf Save directly to the master configuration .
