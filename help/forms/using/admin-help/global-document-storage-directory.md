---
title: Ordner des globalen Dokumentenspeichers
seo-title: Ordner des globalen Dokumentenspeichers
description: Der Ordner des globalen Dokumentenspeichers (GDS) ist ein Ordner zum Speichern dauerhaft genutzter Dateien in einem Prozess.
seo-description: Der Ordner des globalen Dokumentenspeichers (GDS) ist ein Ordner zum Speichern dauerhaft genutzter Dateien in einem Prozess.
uuid: 7681672c-a0dc-4445-8004-1b1e2ed3d301
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a33b8834-6e39-47eb-a53b-0982d32e80ad
exl-id: 7a64a643-808b-4644-8fd3-0dafe83e8dd9
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 97%

---

# Ordner des globalen Dokumentenspeichers{#global-document-storage-directory}

Der Ordner des *globalen Dokumentenspeichers (GDS)* ist ein Ordner zum Speichern dauerhaft genutzter Dateien in einem Prozess. Zu diesen Dateien gehören PDFs, Richtlinien und Formularvorlagen. Dauerhaft genutzte Dateien bilden einen wichtigen Teil des Gesamtstatus zahlreicher AEM Forms-Bereitstellungen. Wenn einige oder alle dauerhaft genutzten Dokumente verloren gehen oder beschädigt werden, kann der Formularserver instabil werden. Eingabedokumente für den asynchronen Auftragsaufruf werden ebenfalls im Ordner des globalen Dokumentenspeichers gespeichert und müssen verfügbar sein, damit Anforderungen verarbeitet werden können. Es ist wichtig, die Zuverlässigkeit des Dateisystems zu berücksichtigen, in dem sich der Ordner des globalen Dokumentenspeichers befindet. Verwenden Sie ein Redundant Array of Independent Disks (RAID) oder eine andere Technologie, die Ihre Qualitäts- und Dienstanforderungen erfüllt.

Dauerhaft genutzte Dateien können vertrauliche Benutzerinformationen enthalten. Diese Informationen erfordern möglicherweise spezielle Berechtigungen, wenn der Zugriff über die AEM Forms-APIs oder -Benutzerschnittstellen erfolgt. Der Ordner des globalen Dokumentenspeichers sollte mithilfe des Betriebssystems ordnungsgemäß abgesichert werden. Nur das Administratorkonto, das zum Ausführen des Anwendungsservers dient, sollte Lese- und Schreibzugriff auf den Ordner des globalen Dokumentenspeichers haben.

Zusätzlich zur Wahl eines sicheren Ordners mit einer hohen Verfügbarkeit für den GDS können Sie außerdem den Dokumentenspeicher für die Datenbank aktivieren. Beachten Sie, dass AEM Forms den Ordner des globalen Dokumentenspeichers auch dann benötigt, wenn Sie die AEM Forms-Datenbank für die Dokumentenspeicherung verwenden. (Siehe [Sicherungsoptionen, wenn die Datenbank für die Dokumentenspeicherung verwendet wird](/help/forms/using/admin-help/files-back-recover.md#backup-options-when-database-is-used-for-document-storage).)

AEM Forms-Anwendungsdaten befinden sich im Ordner des globalen Dokumentenspeichers und in der AEM Forms-Datenbank. In der folgenden Tabelle sind die Daten und ihre Speicherorte angegeben.

<table>
 <thead>
  <tr>
   <th><p>AEM Forms-Daten</p></th>
   <th><p>Datenbank</p></th>
   <th><p>Globaler Dokumentspeicher</p></th>
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
   <td><p>Formular-Repository</p></td>
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

## Ordner des globalen Dokumentspeichers konfigurieren {#configuring-the-gds-directory}

Der Speicherort des Ordners des globalen Dokumentspeichers kann während der Installation von AEM Forms manuell konfiguriert werden. Wenn die Speicherorteinstellung bei der Installation leer bleibt, wird als Speicherort standardmäßig ein Ordner unter dem Installationsordner des Anwendungsservers gewählt (siehe unten):

* (JBoss) `[appserver root]/server/[type]/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/DocumentServer/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

## Standardspeicherort des globalen Dokumentspeichers ändern {#change-the-default-gds-location}

Sie können nach Abschluss der Installation von AEM Forms den Speicherort des globalen Dokumentenspeichers in Administration Console ändern. Sie müssen zum Abschließen des Prozesses die Daten manuell verschieben.

>[!NOTE]
>
>Migrieren Sie die Daten auf folgende Weise, damit keine Daten verloren gehen.

1. Melden Sie sich bei Administration Console an und klicken Sie auf „Einstellungen“ > „Core-Systemeinstellungen“ > „Konfigurationen“.
1. Geben Sie in das Feld „Ordner des globalen Dokumentenspeichers“ den vollständigen Pfad des neuen Ordners des globalen Dokumentenspeichers ein und klicken Sie auf OK.
1. Fahren Sie sofort den Anwendungsserver herunter.
1. Verschieben Sie alle Dateien aus dem alten Ordner des globalen Dokumentenspeichers unter Beibehaltung der internen Ordnerstruktur an den neuen Speicherort.
1. Starten Sie den Anwendungsserver neu.

## Informationen zu Bereitstellungsdateien  {#about-deployment-files}

AEM Forms besteht aus zwei Arten von Bereitstellungsdateien: den Dienstcontainern und den EAR-Dateien für Java 2 Platform, Enterprise Edition (J2EE). Die EAR-Dateien bestehen aus Paketen mit J2EE-Standardanwendungen, die die Hauptfunktionalität von AEM Forms enthalten. Die für den jeweiligen Anwendungsserver spezifischen EAR-Dateien tragen folgende Bezeichnungen:

* adobe-core-*[appserver]*.ear
* adobe-core-*[appserver]*-*[OS]*.ear

Das Implementieren von AEM Forms besteht aus der Bereitstellung der assemblierten EAR-Dateien und unterstützender Dateien auf dem Anwendungsserver, auf dem Sie die AEM Forms-Lösung ausführen möchten. Wenn Sie mehrere Module konfiguriert und assembliert haben, werden die bereitstellbaren Module in den bereitstellbaren EAR-Dateien zusammengefasst. Um diese Dateien bereitzustellen, kopieren Sie sie in den Ordner *[appserver home]*\server\all\deploy directory.

Module und AEM Forms-Archivdateien werden als JAR-Dateien zusammengefasst. Da sie keine Dateien vom Typ J2EE sind, werden sie nicht auf dem Anwendungsserver bereitgestellt. Sie werden stattdessen in den Ordner des globalen Dokumentenspeichers kopiert und in der AEM Forms-Datenbank wird ein Verweis auf ihren Speicherort gespeichert. Daher muss der Ordner des globalen Dokumentenspeichers für alle Knoten des Clusters freigegeben werden. Alle Knoten müssen Zugriff auf den zentralen Speicherordner für die DSC haben.

>[!NOTE]
>
>Stellen Sie vor der Bereitstellung der Dienstcontainer sicher, dass Sie den Ordner des globalen Dokumentenspeichers erstellt und konfiguriert haben. (Siehe [GDS-Ordner konfigurieren](global-document-storage-directory.md#configuring-the-gds-directory))
