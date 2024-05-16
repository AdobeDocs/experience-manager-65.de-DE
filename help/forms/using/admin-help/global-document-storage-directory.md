---
title: Ordner des globalen Dokumentenspeichers
description: Das Verzeichnis des globalen Dokumentenspeichers (GDS) ist ein Verzeichnis zum Speichern dauerhaft genutzter Dateien in einem Prozess.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7a64a643-808b-4644-8fd3-0dafe83e8dd9
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '672'
ht-degree: 100%

---

# Ordner des globalen Dokumentenspeichers{#global-document-storage-directory}

Das Verzeichnis *Globaler Dokumentenspeicher (GDS)* ist ein Verzeichnis zum Speichern dauerhaft genutzter Dateien in einem Prozess. Zu diesen Dateien gehören PDFs, Richtlinien und Formularvorlagen. Dauerhaft genutzte Dateien bilden einen wichtigen Teil des Gesamtstatus zahlreicher AEM Forms-Bereitstellungen. Wenn einige oder alle dauerhaft genutzten Dokumente verloren gehen oder beschädigt werden, kann der Formular-Server instabil werden. Eingabedokumente für asynchrone Auftragsaufrufe werden ebenfalls im Verzeichnis des globalen Dokumentenspeichers gespeichert und müssen verfügbar sein, damit Anfragen verarbeitet werden können. Es ist wichtig, die Zuverlässigkeit des Dateisystems zu berücksichtigen, in dem sich das Verzeichnis des globalen Dokumentenspeichers befindet. Verwenden Sie ein Redundant Array of Independent Disks (RAID) oder eine andere Technologie, die Ihre Qualitäts- und Dienstanforderungen erfüllt.

Dauerhaft genutzte Dateien können vertrauliche Benutzerinformationen enthalten. Diese Informationen erfordern möglicherweise spezielle Berechtigungen, wenn der Zugriff über die AEM Forms-APIs oder -Benutzerschnittstellen erfolgt. Es ist wichtig, dass das Verzeichnis des globalen Dokumentenspeichers mithilfe des Betriebssystems ordnungsgemäß abgesichert wird. Nur das Administratorkonto, das zum Ausführen des Anwendungs-Servers dient, sollte Lese- und Schreibzugriff auf das Verzeichnis des globalen Dokumentenspeichers haben.

Zusätzlich zur Wahl eines sicheren Verzeichnisses mit einer hohen Verfügbarkeit für den GDS können Sie außerdem den Dokumentenspeicher in der Datenbank aktivieren. Beachten Sie, dass AEM Forms das Verzeichnis des globalen Dokumentenspeichers auch dann benötigt, wenn Sie die AEM Forms-Datenbank für die Dokumentenspeicherung verwenden. (Siehe [Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird](/help/forms/using/admin-help/files-back-recover.md#backup-options-when-database-is-used-for-document-storage).)

AEM Forms-Anwendungsdaten befinden sich im Ordner des globalen Dokumentenspeichers und in der AEM Forms-Datenbank. In der folgenden Tabelle sind die Daten und ihre Speicherorte angegeben.

<table>
 <thead>
  <tr>
   <th><p>AEM Forms-Daten</p></th>
   <th><p>Datenbank</p></th>
   <th><p>Globaler Dokumentenspeicher</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Anwendungsdaten (Benutzende, Rollen, Prozesse, Richtlinien, Endpunkte, Ereignisse usw.)</p></td>
   <td><p>Ja</p></td>
   <td><p>Nein</p></td>
  </tr>
  <tr>
   <td><p>Bereitgestellte Dienst-Container</p></td>
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

## Konfigurieren des Verzeichnisses des globalen Dokumentenspeichers {#configuring-the-gds-directory}

Der Speicherort des Verzeichnisses des globalen Dokumentenspeichers kann während der Installation von AEM Forms manuell konfiguriert werden. Wenn die Speicherorteinstellung bei der Installation leer bleibt, wird als Speicherort standardmäßig ein Verzeichnis unter der Installation des Anwendungs-Servers gewählt (siehe unten):

* (JBoss) `[appserver root]/server/[type]/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/DocumentServer/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

## Ändern des Standardspeicherorts des globalen Dokumentenspeichers {#change-the-default-gds-location}

Nach Abschluss der Installation von AEM Forms können Sie den Speicherort des globalen Dokumentenspeichers in der Administrationskonsole ändern. Verschieben Sie die Daten manuell, um den Prozess abzuschließen.

>[!NOTE]
>
>Migrieren Sie die Daten auf folgende Weise, damit keine Daten verloren gehen.

1. Melden Sie sich bei der Administrationskonsole an und klicken Sie auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie in das Feld „Verzeichnis des globalen Dokumentenspeichers“ den vollständigen Pfad des neuen Verzeichnisses des globalen Dokumentenspeichers ein und klicken Sie auf „OK“.
1. Fahren Sie sofort den Anwendungs-Server herunter.
1. Verschieben Sie alle Dateien aus dem alten Verzeichnis des globalen Dokumentenspeichers unter Beibehaltung der internen Verzeichnisstruktur an den neuen Speicherort.
1. Starten Sie den Anwendungs-Server neu.

## Informationen zu Bereitstellungsdateien {#about-deployment-files}

AEM Forms besteht aus zwei Arten von Bereitstellungsdateien: den Dienst-Containern und den EAR-Dateien für Java 2 Platform, Enterprise Edition (J2EE). Die EAR-Dateien bestehen aus Paketen mit J2EE-Standardanwendungen, die die Hauptfunktionalität von AEM Forms enthalten. Die für den jeweiligen Anwendungs-Server spezifischen EAR-Dateien tragen folgende Bezeichnungen:

* adobe-core-*[Anwendungsserver]*.ear
* adobe-core-*[Anwendungsserver]*-*[Betriebssystem]*.ear

Das Implementieren von AEM Forms besteht aus der Bereitstellung der assemblierten EAR-Dateien und unterstützender Dateien auf dem Anwendungs-Server, auf dem Sie die AEM Forms-Lösung ausführen möchten. Wenn Sie mehrere Module konfiguriert und assembliert haben, werden die bereitstellbaren Module in den bereitstellbaren EAR-Dateien zusammengefasst. Um diese Dateien bereitzustellen, kopieren Sie sie in den Ordner „*[Anwendungsserver-Startordner]*\server\all\deploy“.

Module und AEM Forms-Archivdateien werden als JAR-Dateien zusammengefasst. Da sie keine Dateien vom Typ J2EE sind, werden sie nicht auf dem Anwendungs-Server bereitgestellt. Sie werden stattdessen in das Verzeichnis des globalen Dokumentenspeichers kopiert, und in der AEM Forms-Datenbank wird ein Verweis auf ihren Speicherort gespeichert. Daher muss das Verzeichnis des globalen Dokumentenspeichers für alle Knoten des Clusters freigegeben werden. Alle Knoten müssen Zugriff auf das Verzeichnis des zentralen Speichers für die DSCs haben.

>[!NOTE]
>
>Stellen Sie vor der Bereitstellung der Dienst-Container sicher, dass Sie das Verzeichnis des globalen Dokumentenspeichers erstellt und konfiguriert haben. (Siehe [Konfigurieren des GDS-Verzeichnisses](global-document-storage-directory.md#configuring-the-gds-directory))
