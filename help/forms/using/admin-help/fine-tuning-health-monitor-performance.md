---
title: Optimieren der Leistung bei der Systemüberwachung
description: Erfahren Sie, wie Sie die Leistung der Systemüberwachung optimieren.  Steuern Sie die Systemstatistiken, die sich auf die Leistung der Formularumgebung auswirken, mithilfe der JAVA-Einstellungsoption.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 41042e08-5e14-4809-89b7-16d98a72d1b4
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 100%

---

# Optimieren der Leistung bei der Systemüberwachung{#fine-tuning-health-monitor-performance}

Das Sammeln der Systemstatistiken, die in der Systemüberwachung angegeben werden, hat Auswirkungen auf die Leistung Ihrer AEM Forms-Umgebung.  Diese Auswirkungen können durch Festlegen der unten aufgeführten Java-Optionen in Ihrem Anwendungs-Server kontrolliert werden.

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
   <td><p>Systemüberwachung-Thread aktivieren oder deaktivieren</p></td>
   <td><p>Ja</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.statistics-enabled</p></td>
   <td><p>Gemfire-Zwischenspeicherung aktivieren oder deaktivieren</p></td>
   <td><p>Ja</p></td>
  </tr>
  <tr>
   <td><p>adobe.healthmonitor.refresh-interval</p></td>
   <td><p>Das Intervall in Millisekunden, nach dem der Systemüberwachungs-Thread die Statistiken sammelt.</p></td>
   <td><p>10 Minuten (600.000 Millisekunden)</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.multicast-port</p></td>
   <td><p>Der Multicast-Anschluss, der zum Kommunizieren mit anderen Mitgliedern des gelieferten Systems verwendet wird. Wenn dieser auf null festgelegt ist, wird Multicast für die Mitgliedererkennung und für den Vertrieb deaktiviert. </p><p>Hinweis: Wählen Sie verschiedene Multicast-Adressen und -Anschlüsse für verschiedene verteilte Systeme aus.  Verwenden Sie nicht nur verschiedene Adressen.</p></td>
   <td><p>Kein Standardwert. Die gültigen Werte reichen von 0 bis 65535.</p></td>
  </tr>
  <tr>
   <td><p>statistic-sample-rate</p></td>
   <td><p>Die Rate in Millisekunden, in der Statistiken neu berechnet werden.  Betriebssystemstatistiken werden nur aktualisiert, wenn ein Beispiel abgefragt wird.</p></td>
   <td><p>600000</p></td>
  </tr>
  <tr>
   <td><p>adobe.workmanager.healthmonitor.enabled</p></td>
   <td><p>Diese Eigenschaft aktiviert oder deaktiviert die Work Manager-Statistiksammlung, z. B. die Anzahl der Aufträge oder Arbeitselemente.</p></td>
   <td><p>Ja</p></td>
  </tr>
 </tbody>
</table>

## Hinzufügen von Java-Optionen zu JBoss {#add-java-options-to-jboss}

1. Beenden Sie den JBoss-Anwendungs-Server.
1. Öffnen Sie „*[Programm-Server-Stammordner]*/bin/run.bat“ (Windows) oder „run.sh“ (Linux oder UNIX) in einem Texteditor und fügen Sie die Java-Optionen Ihren Anforderungen entsprechend hinzu.
1. Starten Sie den Server neu.

## Hinzufügen von Java-Optionen zu WebLogic {#add-java-options-to-weblogic}

1. Starten Sie die WebLogic-Administration-Console, indem Sie „https://[Hostname]:&#39;port&#39;/console“ in die Adresszeile eines Webbrowsers eingeben.
1. Geben Sie den von Ihnen erstellten Benutzernamen und das Kennwort für die WebLogic-Server-Domain ein und klicken Sie unter „Change Center“ auf „Log“ und dann auf „Lock &amp; Edit“.
1. Klicken Sie unter „Domain Structure“ auf Environment > Servers und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten „Configuration“ > „Server-Start“.
1. Fügen Sie im Feld „Argumente“ die erforderlichen Argumente am Ende des aktuellen Inhalts hinzu. Wenn Sie beispielsweise „‑ `Dadobe.healthmonitor.enabled=false`“ hinzufügen, wird Health Monitor deaktiviert.
1. Klicken Sie auf „Speichern“ und dann auf „Änderungen aktivieren“.
1. Starten Sie WebLogic Managed Server neu.

## Hinzufügen von Java-Optionen zu WebSphere {#add-java-options-to-websphere}

1. Führen Sie in der Navigationsstruktur von WebSphere Administrative Console die folgenden Schritte für Ihren Anwendungs-Server aus:

   (WebSphere 6.x) Klicken Sie auf „Servers“ > „Application servers“

   (WebSphere 7.x) Klicken Sie auf „Servers“ > „Server Types“ > „WebSphere Application Servers“

1. Klicken Sie im rechten Bereich auf den Namen des Servers.
1. Klicken Sie unter „Server-Infrastruktur“ auf „Java und Forms Workflow“ > „Prozessdefinition“.
1. Klicken Sie unter „Zusätzliche Eigenschaften“ auf „Java Virtual Machine“.
1. Geben Sie in das Feld „Generische JVM-Argumente“ die erforderlichen Argumente ein.
1. Klicken Sie auf „OK“ oder „Anwenden“ und dann auf „Save directly to the master configuration“.
