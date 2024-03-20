---
title: Ordner des globalen Dokumentenspeichers
description: Der Ordner des globalen Dokumentenspeichers (GDS) ist ein Ordner zum Speichern dauerhaft genutzter Dateien in einem Prozess.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7a64a643-808b-4644-8fd3-0dafe83e8dd9
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 14%

---

# Ordner des globalen Dokumentenspeichers{#global-document-storage-directory}

Die *Globaler Dokumentenspeicher (GDS)* directory ist ein Ordner zum Speichern dauerhaft genutzter Dateien in einem Prozess. Zu diesen Dateien gehören PDF, Richtlinien und Formularvorlagen. Langlebige Dateien sind ein wichtiger Bestandteil des Gesamtstatus vieler AEM Formularbereitstellungen. Wenn einige oder alle dauerhaft genutzten Dokumente verloren gehen oder beschädigt sind, kann der Forms-Server instabil werden. Eingabedokumente für den asynchronen Auftragsaufruf werden ebenfalls im Ordner des globalen Dokumentenspeichers gespeichert und müssen zur Verarbeitung von Anforderungen verfügbar sein. Es ist wichtig, dass Sie die Zuverlässigkeit des Dateisystems berücksichtigen, das den Ordner des globalen Dokumentenspeichers hostet. Verwenden Sie ein redundantes Array unabhängiger Festplatten (RAID) oder eine andere Technologie, die Ihren Qualitäts- und Service-Anforderungen entspricht.

Dauerhaft genutzte Dateien können vertrauliche Benutzerinformationen enthalten. Diese Informationen erfordern möglicherweise spezielle Berechtigungen, wenn der Zugriff über die AEM Forms-APIs oder -Benutzerschnittstellen erfolgt. Es ist wichtig, dass der Ordner des globalen Dokumentenspeichers ordnungsgemäß über das Betriebssystem gesichert wird. Nur das Administratorkonto, das zum Ausführen des Anwendungsservers verwendet wird, sollte Lese-/Schreibzugriff auf den Ordner des globalen Dokumentenspeichers haben.

Zusätzlich zur Auswahl eines sicheren, hochverfügbaren Ordners für den globalen Dokumentenspeicher können Sie auch den Dokumentenspeicher in der Datenbank aktivieren. Beachten Sie, dass auch bei der Verwendung der AEM Forms-Datenbank für den Dokumentenspeicher AEM Formulare den Ordner des globalen Dokumentenspeichers benötigen. (Siehe [Sicherungsoptionen bei Verwendung der Datenbank für die Dokumentenspeicherung](/help/forms/using/admin-help/files-back-recover.md#backup-options-when-database-is-used-for-document-storage).

AEM Forms-Anwendungsdaten befinden sich im Ordner des globalen Dokumentenspeichers und in der AEM Forms-Datenbank. In der folgenden Tabelle werden die Daten und ihre Speicherorte beschrieben.

<table>
 <thead>
  <tr>
   <th><p>Formulardaten AEM</p></th>
   <th><p>Datenbank</p></th>
   <th><p>GDS</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Anwendungsdaten (Benutzer, Rollen, Prozesse, Richtlinien, Endpunkte, Ereignisse usw.)</p></td>
   <td><p>Ja</p></td>
   <td><p>Nein</p></td>
  </tr>
  <tr>
   <td><p>Bereitgestellte Dienstcontainer</p></td>
   <td><p>Ja</p></td>
   <td><p>Nein</p></td>
  </tr>
  <tr>
   <td><p>Document Manager </p></td>
   <td><p>Nein</p></td>
   <td><p>Ja</p></td>
  </tr>
  <tr>
   <td><p>Forms-Repository</p></td>
   <td><p>Ja</p></td>
   <td><p>Nein</p></td>
  </tr>
  <tr>
   <td><p>Systemkonfiguration</p></td>
   <td><p>Ja</p></td>
   <td><p>Nein</p></td>
  </tr>
  <tr>
   <td><p>Überwachte Ordner</p></td>
   <td><p>Nein</p></td>
   <td><p>Ja</p></td>
  </tr>
 </tbody>
</table>

## Ordner des globalen Dokumentenspeichers konfigurieren {#configuring-the-gds-directory}

Der Speicherort des Ordners des globalen Dokumentenspeichers kann während der AEM Forms-Installation manuell konfiguriert werden. Wenn die Speicherorteinstellung während der Installation leer bleibt, wird als Speicherort standardmäßig ein Ordner unter der Installation des Anwendungsservers wie folgt verwendet:

* (JBoss) `[appserver root]/server/[type]/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/DocumentServer/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

## Standardspeicherort des globalen Dokumentenspeichers ändern {#change-the-default-gds-location}

Sie können den Speicherort des globalen Dokumentenspeichers in Administration Console nach Abschluss der AEM Forms-Installation ändern. Suchen Sie die Daten manuell, um den Prozess abzuschließen.

>[!NOTE]
>
>Migrieren Sie die Daten auf die folgende Weise, da sonst Daten verloren gehen.

1. Melden Sie sich bei Administration Console an und klicken Sie auf Einstellungen > Core-Systemeinstellungen > Konfigurationen.
1. Geben Sie im Feld &quot;Ordner des globalen Dokumentenspeichers&quot;den vollständigen Pfad zum neuen Ordner des globalen Dokumentenspeichers ein und klicken Sie auf &quot;OK&quot;.
1. Fahren Sie den Anwendungsserver sofort herunter.
1. Verschieben Sie alle Dateien aus dem alten Ordner des globalen Dokumentenspeichers an den neuen Speicherort, wobei Sie die interne Ordnerstruktur beibehalten.
1. Starten Sie den Anwendungs-Server neu.

## Über Bereitstellungsdateien {#about-deployment-files}

AEM Formulare bestehen aus zwei Arten von Bereitstellungsdateien, den Dienst-Containern und den EAR-Dateien für Java 2 Platform, Enterprise Edition (J2EE). Die EAR-Dateien bestehen aus Paketen mit J2EE-Standardanwendungen, die die Hauptfunktionalität von AEM Forms enthalten. Die anwendungsserverspezifischen EAR-Dateien lauten wie folgt:

* adobe-core-*[Anwendungsserver]*.ear
* adobe-core-*[Anwendungsserver]*-*[Betriebssystem]*.ear

Die Implementierung AEM Formulare umfasst die Bereitstellung der assemblierten EAR-Dateien und unterstützender Dateien auf dem Anwendungsserver, auf dem Sie die AEM Formularlösung ausführen möchten. Wenn Sie mehrere Module konfiguriert und assembliert haben, werden die bereitstellbaren Module in den bereitstellbaren EAR-Dateien zusammengefasst. Um diese Dateien bereitzustellen, kopieren Sie sie in den Ordner „*[Anwendungsserver-Startordner]*\server\all\deploy“.

Module und AEM Formulararchivdateien werden in JAR-Dateien gepackt. Da es sich nicht um Dateien vom Typ J2EE handelt, werden sie nicht auf dem Anwendungsserver bereitgestellt. Stattdessen werden sie in den Ordner des globalen Dokumentenspeichers kopiert und ein Verweis auf ihren Speicherort wird in der AEM Forms-Datenbank gespeichert. Aus diesem Grund muss der Ordner des globalen Dokumentenspeichers für alle Knoten des Clusters freigegeben werden. Alle Knoten müssen Zugriff auf den zentralen Speicherordner für die DSCs haben.

>[!NOTE]
>
>Stellen Sie vor der Bereitstellung der Dienstcontainer sicher, dass Sie den Ordner des globalen Dokumentenspeichers erstellt und konfiguriert haben. (Siehe [Ordner des globalen Dokumentenspeichers konfigurieren](global-document-storage-directory.md#configuring-the-gds-directory))
