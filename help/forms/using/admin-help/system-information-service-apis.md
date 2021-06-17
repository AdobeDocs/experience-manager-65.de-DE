---
title: Systeminformationsdienst-APIs
seo-title: Systeminformationsdienst-APIs
description: Dieses Dokument enthält detaillierte Informationen zu den vom Systeminformationsdienst bereitgestellten APIs.
seo-description: Dieses Dokument enthält detaillierte Informationen zu den vom Systeminformationsdienst bereitgestellten APIs.
uuid: 7f624216-56e6-4d49-b9a1-3c9af045dabe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/system_information_service
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 79fccce2-d090-4b50-9c58-3f2a00e651b2
exl-id: 4da96c8f-8bd0-4cad-9087-18e324f084e7
source-git-commit: d1fc2ff44378276522c2ff3208f5b3bdc4484bba
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 69%

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
   <td><p>https://'[Server]:[Port]'/rest/services/SystemInfo.properties'</p></td>
   <td><p>Diese API ist ein Wrapper für Java-API<a href="https://docs.oracle.com/javase/6/docs/api/java/lang/System.html#getProperties()"> system.getProperties-Java-API</a>. Sie ruft die Konfiguration des aktuellen Arbeitsbereichs ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.envVar</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.envVar</p></td>
   <td><p>Ruft alle Umgebungsvariablen des Host-Betriebssystems ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.logs</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.logs</p></td>
   <td><p>Lädt eine ZIP-Datei mit Anwendungsserverprotokollen herunter. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.config</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.config</p></td>
   <td><p>Ruft den gesamten Inhalt der Datei „config.xml" ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.services</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.services</p></td>
   <td><p>Ruft Status und Konfigurationsparameter von AEM Forms-Diensten ab.</p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.vitalDetails</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.dynamicDetails</p></td>
   <td><p>Ruft Serverbetriebszeit, JVM-Argumente, Systemspeicher, Heap-Größe, Betriebssystemnamen, Anzahl der aktiven Threads und Thread-Anzahl ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.coreSettings</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.coreSettings</p></td>
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
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.database</p></td>
   <td><p>Ruft detaillierte Informationen zur Datenbank ab.</p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.licenseInfo</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.licenseInfo</p></td>
   <td><p>Ruft Version und Lizenzinformationen der installierten AEM Forms-Komponenten ab. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfNo.serverConfig</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.serverConfig</p></td>
   <td><p>Lädt Konfigurationsdateien des Host-Anwendungsservers herunter. </p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.threads?delay=[n]&amp;iterations=[n]</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.threads?delay=[n]&amp;iterations=[n]</p></td>
   <td><p>Ruft Anzahl und Stapelablaufverfolgung aktiver Threads ab. Folgende Parameter werden akzeptiert:</p>
    <ul>
     <li><p>iterations= [n]: Gibt die Anzahl der Iterationen an. Ersetzen Sie n durch eine Zahl. </p></li>
     <li><p>Delay= [n]: Gibt an, wie viele Millisekunden vor der nächsten Iteration gewartet werden soll. </p></li>
    </ul><p></p></td>
  </tr>
  <tr>
   <td><p>SystemInfo.info</p></td>
   <td><p>https://'[Server]:[Port]'/rest/services/ SystemInfo.info</p></td>
   <td><p>Diese API ist ein Wrapper für alle Systeminformationsdienst-APIs. Sie führt intern alle Systeminformations-APIs aus und lädt Informationen im ZIP-Format herunter. </p><p><i><strong>Hinweis</strong>: Die Datei „SystemInfo.info“ enthält nicht Anzahl und Stapelablaufverfolgung aktiver Threads. </i></p></td>
  </tr>
 </tbody>
</table>
