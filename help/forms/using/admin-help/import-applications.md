---
title: Importieren und Verwalten von Anwendungen
description: Erfahren Sie, wie Sie Anwendungen importieren und verwalten können. Eine Anwendung ist ein Container zum Speichern von Assets, die für die Implementierung einer AEM Forms-Lösung erforderlich sind.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: f17726c0-3591-4d25-a8b5-3a7024249a56
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '840'
ht-degree: 100%

---

# Importieren und Verwalten von Anwendungen{#import-and-manage-applications}

In AEM Forms ist eine *Anwendung* ein Container zum Speichern von Assets, die für die Implementierung einer AEM Forms-Lösung erforderlich sind. Beispiele für Assets sind Formularentwürfe, Formularfragmente, Bilder, Prozesse, DDX-Dateien, Formular-Guides, HTML-Seiten und SWF-Dateien. Während der Entwicklungsphase eines Projekts können Workbench-Benutzende Anwendungen direkt aus der Anwendungsansicht in Workbench bereitstellen. Nach der Bereitstellung werden diese Anwendungen in der Administrationskonsole auf der Registerkarte „Anwendungen“ auf der Seite „Anwendungsverwaltung“ angezeigt.

Wenn eine Anwendung abgeschlossen ist und auf einem Produktions-Server bereitgestellt werden kann, packen Workbench-Benutzende die Anwendung in eine *AEM-Formularanwendungsdatei* (.lca). Anschließend verwenden Admins die Administrationskonsole, um die Anwendungsdatei zu importieren und mithilfe der Registerkarte „Anwendungen“ auf der Seite „Anwendungsverwaltung“ bereitzustellen.

Sie können auch die Registerkarte „Archive“ auf der Seite „Anwendungsverwaltung“ verwenden, um LCAs zu importieren, die mit Workbench 8.x erstellt wurden.

>[!NOTE]
>
>Es gibt ein bekanntes Problem, dass LCA-Dateien aus einer zukünftigen Version nicht unbedingt abwärtskompatibel sind. Es ist zwar möglich, LCA-Dateien aus einer zukünftigen Version von AEM Forms (z. B. einer Vorschau-Version) anzuzeigen und zu importieren, doch wird dies nicht unterstützt und kann zu ungewöhnlichem Verhalten führen.

Auf der Registerkarte „Anwendungen“ können Sie Anwendungen, die in Workbench erstellt wurden, importieren und verwalten. Anwendungsadmins können auch die Laufzeitkonfiguration für eine Anwendung exportieren. Durch das Exportieren der Laufzeitkonfiguration müssen die Einstellungen in der Produktionsumgebung nicht manuell neu konfiguriert werden, bevor die bereitgestellten Anwendungen gestartet werden. Die Datei für die Laufzeitkonfiguration enthält:

* Einstellungen für die Dienstkonfiguration
* Einstellungen für die Pool-Konfiguration
* Einstellungen für die Endpunktkonfiguration
* Sicherheitsprofile

## Importieren einer Anwendung oder eines Archivs {#import-an-application-or-archive}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Wählen Sie Importieren.
1. Klicken Sie auf „Durchsuchen“, wählen Sie die zu importierende .lca-Datei aus und klicken Sie auf „Vorschau“. Auf der Seite „Vorschau der Anwendung“ werden Informationen zur Anwendung angezeigt.
1. (Optional) Um eine Liste der in der Anwendung enthaltenen Assets anzuzeigen, klicken Sie auf „Assets anzeigen“.
1. (Optional) Um die Assets zur Laufzeit bereitzustellen, wählen Sie „Assets nach Abschluss des Imports für Laufzeit bereitstellen“. Wenn Sie diese Option nicht auswählen, können Sie die Assets auch später bereitstellen.
1. Wählen Sie Importieren. Die Anwendung wird auf der Registerkarte „Anwendungen“ angezeigt.
1. Melden Sie sich mit Administratorberechtigungen beim CRX-Repository an.
1. Gehen Sie zu content/dam/lcapplications

   >[!NOTE]
   >
   >Die importierten Anwendungen werden im Knoten „lcapplications“ angezeigt.

1. Klicken Sie auf eine der importierten Anwendungen.

   Die Registerkarte „Eigenschaften“ auf der rechten Seite zeigt die Eigenschaften des ausgewählten CRX-Knotens an.

   Die Eigenschaft **syncState** gibt den Status der Synchronisierung der Daten zwischen dem AEM-Formular-Server und dem CRX-Repository an. Sobald der Importvorgang beginnt, wird dieser Status auf 0 (null) gesetzt. Dieser Status zeigt an, dass die Daten derzeit nicht synchronisiert sind. Wenn die Daten synchronisiert werden, wird der Status auf 1 gesetzt.

## Bereitstellen einer Anwendung  {#deploy-an-application}

Sie können Anwendungen bereitstellen, die Sie importiert haben oder die Workbench-Benutzende aus Workbench importiert haben.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, die Sie bereitstellen möchten, und klicken Sie auf „Bereitstellen“.
1. Klicken Sie im angezeigten Bestätigungsdialogfeld auf „OK“.

## Aufheben der Bereitstellung einer Anwendung {#undeploy-an-application}

Sie können die Bereitstellung von Anwendungen aus der Laufzeit aufheben.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, deren Bereitstellung Sie aufheben möchten, und klicken Sie auf „Bereitstellung aufheben“.
1. Klicken Sie im angezeigten Bestätigungsdialogfeld auf „OK“.

## Entfernen einer Anwendung vom Server {#remove-an-application-from-the-server}

Heben Sie die Bereitstellung der Anwendung auf, bevor Sie sie vom Server entfernen.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, die Sie entfernen möchten, und klicken Sie auf „Entfernen“.
1. Klicken Sie im angezeigten Bestätigungsdialogfeld auf „OK“.

## Importieren der Laufzeitkonfiguration einer Anwendung {#import-an-application-s-runtime-configuration}

Wenn Anwendungsadmins die Laufzeitkonfiguration für eine Anwendung exportiert haben, können Sie sie in die bereitgestellte Anwendung importieren. Sie können sie entweder mit der Administrationskonsole oder über eine skriptgesteuerte LCA-Bereitstellung importieren

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Klicken Sie auf den Namen der Anwendung.
1. Klicken Sie auf „Laufzeitkonfiguration importieren“.
1. Klicken Sie auf „Durchsuchen“ und wählen Sie die XML-Datei aus, die die Laufzeitkonfiguration enthält.
1. Wählen Sie Importieren.

## Exportieren der Laufzeitkonfiguration einer Anwendung {#export-an-application-s-runtime-configuration}

Sie können die Laufzeitkonfigurationsinformationen für bereitgestellte Anwendungen exportieren.

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Klicken Sie auf den Namen der Anwendung.
1. Klicken Sie auf „Laufzeitkonfiguration exportieren“ und speichern Sie die erstellte Konfigurationsdatei (XML).

## Skriptgesteuerte Bereitstellung von AEM Forms-Anwendungen {#scripted-deployment-of-aem-forms-applications}

Sie können auch ein skriptgesteuertes Bereitstellungswerkzeug verwenden, um Anwendungsdateien bereitzustellen, einschließlich einer „settings.xml“-Datei, die die folgenden Einstellungen angibt:

* Einstellungen für die Dienstkonfiguration
* Einstellungen für die Pool-Konfiguration
* Einstellungen für die Endpunktkonfiguration
* Sicherheitsprofile

Durch die skriptgesteuerte Bereitstellung entfällt die Notwendigkeit, die Einstellungen in der Produktionsumgebung vor dem Starten bereitgestellter Anwendungen manuell neu zu konfigurieren.

1. Wechseln Sie an einer Eingabeaufforderung zu „*[aem-forms root]*/sdk/misc/Foundation/ArchiveManagement“.
1. Weitere Informationen finden Sie in der Datei „ReadMe.txt“.
1. Ändern Sie manuell die Dateien „scriptedDeploy.bat“ und „sample-files/sample.xml“, wie in der Datei „readme.txt“ beschrieben.
1. Führen Sie die Datei „scriptedDeploy.bat“ aus. Durch diese Aktion wird die AEM Forms-Archivdatei mit den Einstellungen zum Überschreiben bereitgestellt.
