---
title: Leistung von Health Monitor optimieren
seo-title: Leistung von Systemüberwachung optimieren
description: Erfahren Sie, wie Sie die Leistung der Systemüberwachung optimieren.
seo-description: Erfahren Sie, wie Sie die Leistung der Systemüberwachung optimieren.
uuid: 770b10cb-065f-41b5-9594-a291e4311151
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b8f8bddc-0d38-4d5e-b33f-978f04bc16c6
exl-id: 41042e08-5e14-4809-89b7-16d98a72d1b4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 88%

---

# Leistung von Systemüberwachung optimieren{#fine-tuning-health-monitor-performance}

Das Sammeln der Systemstatistiken, die in der Systemüberwachung angegeben werden, hat Auswirkungen auf die Leistung Ihrer AEM Forms-Umgebung. Diese Auswirkungen können durch Festlegen der unten aufgeführten Java-Optionen in Ihrem Anwendungsserver kontrolliert werden.

<table>
 <thead>
  <tr>
   <th><p>Property</p></th>
   <th><p>Zweck</p></th>
   <th><p>Standardwert</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>adobe.healthmonitor.enabled</p></td>
   <td><p>Systemüberwachung-Thread aktivieren oder deaktivieren</p></td>
   <td><p>true</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.statistics-enabled</p></td>
   <td><p>Gemfire-Zwischenspeicherung aktivieren oder deaktivieren</p></td>
   <td><p>true</p></td>
  </tr>
  <tr>
   <td><p>adobe.healthmonitor.refresh-interval</p></td>
   <td><p>Das Intervall in Millisekunden, nach dem der Systemüberwachung-Thread die Statistiken sammelt.</p></td>
   <td><p>10 Minuten (600.000 Millisekunden)</p></td>
  </tr>
  <tr>
   <td><p>adobe.cache.multicast-port</p></td>
   <td><p>Der Multicast-Anschluss, der zum Kommunizieren mit anderen Mitgliedern des gelieferten Systems verwendet wird. Wenn dieser auf null festgelegt ist, wird Multicast für die Mitgliedererkennung und für den Vertrieb deaktiviert. </p><p>Hinweis: Wählen Sie verschiedene Multicast-Adressen und -Anschlüsse für verschiedene verteilte Systeme aus. Verwenden Sie nicht nur verschiedene Adressen.</p></td>
   <td><p>Kein Standardwert. Gültige Werte reichen von 0 bis 65535.</p></td>
  </tr>
  <tr>
   <td><p>statistic-sample-rate</p></td>
   <td><p>Die Rate in Millisekunden, in der Statistiken neu berechnet werden. Betriebssystemstatistiken werden nur aktualisiert, wenn ein Beispiel abgefragt wird.</p></td>
   <td><p>600000</p></td>
  </tr>
  <tr>
   <td><p>adobe.workmanager.healthmonitor.enabled</p></td>
   <td><p>Diese Eigenschaft aktiviert oder deaktiviert die Work Manager-Statistiksammlung, z. B. die Anzahl der Aufträge oder Arbeitselemente.</p></td>
   <td><p>true</p></td>
  </tr>
 </tbody>
</table>

## Java-Optionen zu JBoss hinzufügen {#add-java-options-to-jboss}

1. JBoss-Anwendungsserver beenden.
1. Öffnen Sie den *[Anwendungsserver-Stammordner]*/bin/run.bat (Windows) oder run.sh (Linux oder UNIX) in einem Editor und fügen Sie die Java-Optionen nach Bedarf hinzu.
1. Starten Sie den Server neu.

## Java-Optionen zu WebLogic hinzufügen  {#add-java-options-to-weblogic}

1. Starten Sie WebLogic Administration Console, indem Sie in die Adresszeile eines Browsers https://[Hostname]:&#39;port&#39;/console eingeben.
1. Geben Sie den von Ihnen erstellten Benutzernamen und das Kennwort für die WebLogic-Serverdomäne ein und klicken Sie unter „Change Center“ auf „Log“ und dann auf „Lock &amp; Edit“.
1. Klicken Sie unter „Domain Structure“ auf Environment> Servers und anschließend im rechten Bereich auf den Namen des verwalteten Servers.
1. Klicken Sie im nächsten Bildschirm auf die Registerkarten Configuration > Server Start.
1. Fügen Sie im Feld „Arguments“ die erforderlichen Informationen am Ende des aktuellen Inhalts hinzu. Wenn Sie beispielsweise - `Dadobe.healthmonitor.enabled=false` hinzufügen, wird Health Monitor deaktiviert.
1. Klicken Sie auf Save und dann auf Activate Changes.
1. Starten Sie WebLogic Managed Server neu.

## Java-Optionen zu WebSphere hinzufügen  {#add-java-options-to-websphere}

1. Führen Sie in der Navigationsstruktur von WebSphere Administrative Console die folgenden Schritte für Ihren Anwendungsserver aus:

   (WebSphere 6.x) Klicken Sie auf „Servers“ > „Application servers“

   (WebSphere 7.x) Klicken Sie auf „Servers“ > „Server Types“ > „WebSphere Application Servers“

1. Klicken Sie im rechten Fenster auf den Servernamen.
1. Klicken Sie unter „Server Infrastructure“ auf „Arbeitsablauf für Formulare“ > „Process Definition“.
1. Klicken Sie unter „Additional Properties“ auf Java Virtual Machine.
1. Geben Sie in das Feld „Generic JVM Arguments“ die erforderlichen Argumente ein.
1. Klicken Sie auf OK oder Apply und dann auf Save directly to the Master Configuration.
