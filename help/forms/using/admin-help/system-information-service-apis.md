---
title: Systeminformationsdienst-APIs
seo-title: System information Service APIs
description: Dieses Dokument enthält detaillierte Informationen über die vom Systeminformationsdienst bereitgestellten APIs.
seo-description: This document provides detailed information about the APIs provided bythesystem information service.
uuid: 7f624216-56e6-4d49-b9a1-3c9af045dabe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/system_information_service
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 79fccce2-d090-4b50-9c58-3f2a00e651b2
exl-id: 4da96c8f-8bd0-4cad-9087-18e324f084e7
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 38%

---

# Systeminformationsdienst-APIs {#system-information-service-apis}

Der Systeminformationsdienst stellt eine Reihe von REST-APIs zum Abrufen von Informationen bereit. Die folgende Tabelle enthält detaillierte Informationen zu den APIs:

<table>
 <thead>
  <tr>
   <th><p>Name</p></th>
   <th><p>URL</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>SystemInfo.properties</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.properties</p></td>
   <td><p>Diese API ist ein Wrapper für <a href="https://docs.oracle.com/javase/6/docs/api/java/lang/System.html#getProperties()">system.getProperties</a> Java-API. Es ruft die Konfiguration der aktuellen Arbeitsumgebung ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.envVar</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.envVar</p></td>
   <td><p>Ruft alle Umgebungsvariablen des Host-Betriebssystems ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.logs</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.logs</p></td>
   <td><p>Lädt eine ZIP-Datei herunter, die die Protokolle des Anwendungsservers enthält. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.config</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.config</p></td>
   <td><p>Ruft den gesamten Inhalt der Datei „config.xml“ ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.services</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.services</p></td>
   <td><p>Ruft Status- und Konfigurationsparameter von AEM Forms-Diensten ab.</p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.vitalDetails</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.vitalDetails</p></td>
   <td><p>Ruft Server-Betriebszeit, JVM-Argumente, Systemspeicher, Heap-Größe, Betriebssystemnamen, Anzahl der aktiven Threads und Thread-Anzahl ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.coreSettings</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.coreSettings</p></td>
   <td><p>Ruft Werte der folgenden Eigenschaften ab:</p>
    <ul>
     <li><p>AdobeTempDir</p></li>
     <li><p>AdobeServerFontDir</p></li>
     <li><p>CustomerFontDir</p></li>
     <li><p>GlobalDocumentStorageRootDir</p></li>
     <li><p>DefaultDocumentMaxInlineSize</p></li>
     <li><p>DefaultDocumentDisposalTimeout</p></li>
     <li><p>EnableDocumentDBStorage</p></li>
     <li><p>GlobalDocumentStorageUseNetworkShare</p></li>
     <li><p>EnableFIPS</p></li>
     <li><p>EnableWSDL</p></li>
     <li><p>DataServicesConfigFile </p></li>
     <li><p>EnableRDS</p></li>
    </ul><p></p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.database</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.database</p></td>
   <td><p>Ruft detaillierte Informationen zur Datenbank ab.</p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.licenseInfo</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.licenseInfo</p></td>
   <td><p>Ruft Version und Lizenzinformationen der installierten AEM Forms-Komponenten ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfNo.serverConfig</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.serverConfig</p></td>
   <td><p>Lädt Konfigurationsdateien des Host-Anwendungsservers herunter. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.threads?delay=[n]&amp;iterations=[n]</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.threads?delay=[n]&amp;iterations=[n]</p></td>
   <td><p>Ruft die Anzahl und Stapelablaufverfolgung aktiver Threads ab. Folgende Parameter werden akzeptiert:</p>
    <ul>
     <li><p>iterations= [n]: Gibt die Anzahl der Iterationen an. Ersetzen Sie n durch eine Zahl. </p></li>
     <li><p>Delay= [n]: Gibt die Anzahl der Millisekunden an, die gewartet werden soll, bevor die nächste Iteration gestartet wird. </p></li>
    </ul><p></p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.info</p></td>
   <td><p>https://[Server]:[Port]/rest/services/SystemInfo.info</p></td>
   <td><p>Diese API ist ein Wrapper für alle Systeminformationsdienst-APIs. Intern werden alle Systeminformationen-APIs ausgeführt und Informationen im ZIP-Format heruntergeladen. </p><p><i><strong>Hinweis</strong>: Die Datei „SystemInfo.info“ enthält nicht Anzahl und Stapelablaufverfolgung aktiver Threads. </i></p></td>
  </tr>
 </tbody>
</table>
