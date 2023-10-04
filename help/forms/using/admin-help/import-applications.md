---
title: Importieren und Verwalten von Anwendungen
description: Erfahren Sie, wie Sie Anwendungen importieren und verwalten.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: f17726c0-3591-4d25-a8b5-3a7024249a56
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 3%

---

# Importieren und Verwalten von Anwendungen{#import-and-manage-applications}

In AEM Formularen wird ein *Applikation* ist ein Container zum Speichern von Assets, die für die Implementierung einer AEM Formularlösung erforderlich sind. Beispiele für Assets sind Formularentwürfe, Formularfragmente, Bilder, Prozesse, DDX-Dateien, Formular-Guides, HTML-Seiten und SWF-Dateien. Während der Entwicklungsphase eines Projekts können Workbench-Benutzer Anwendungen direkt aus der Anwendungsansicht in Workbench bereitstellen. Nach der Bereitstellung werden diese Anwendungen in Administration Console auf der Registerkarte &quot;Anwendungen&quot;auf der Seite &quot;Anwendungsverwaltung&quot;angezeigt.

Wenn eine Anwendung abgeschlossen ist und auf einem Produktionsserver bereitgestellt werden kann, packt der Workbench-Benutzer die Anwendung in eine *AEM forms-Anwendungsdatei* (.lca). Anschließend verwendet ein Administrator die Administration Console, um die Anwendungsdatei zu importieren und bereitzustellen, und zwar auf der Registerkarte &quot;Anwendungen&quot;auf der Seite &quot;Anwendungsverwaltung&quot;.

Sie können auch die Registerkarte &quot;Archive&quot;auf der Seite &quot;Anwendungsverwaltung&quot;verwenden, um LCAs zu importieren, die mit Workbench 8.x erstellt wurden.

>[!NOTE]
>
>Es gibt ein bekanntes Problem, dass LCA-Dateien aus einer zukünftigen Version nicht unbedingt abwärtskompatibel sind. Es ist zwar möglich, LCA-Dateien aus einer zukünftigen Version AEM Formulars (z. B. einer Vorschau-Version) anzuzeigen und zu importieren, doch wird dies nicht unterstützt und kann zu ungewöhnlichem Verhalten führen.

Verwenden Sie den Tab Anwendungen , um in Workbench erstellte Anwendungen zu importieren und zu verwalten. Anwendungsadministratoren können auch die Laufzeitkonfiguration für eine Anwendung exportieren. Durch das Exportieren der Laufzeitkonfiguration müssen die Einstellungen in der Produktionsumgebung nicht manuell neu konfiguriert werden, bevor die bereitgestellten Anwendungen gestartet werden. Die Laufzeitkonfigurationsdatei enthält:

* Dienstkonfigurationseinstellungen
* Poolkonfigurationseinstellungen
* Endpunktkonfigurationseinstellungen
* Sicherheitsprofile

## Importieren einer Anwendung oder eines Archivs {#import-an-application-or-archive}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;.
1. Wählen Sie Importieren.
1. Klicken Sie auf Durchsuchen , wählen Sie die zu importierende .lca-Datei aus und klicken Sie auf Vorschau . Auf der Seite &quot;Vorschau der Anwendung&quot;werden Informationen zur Anwendung angezeigt.
1. (Optional) Um eine Liste der in der Anwendung enthaltenen Assets anzuzeigen, klicken Sie auf Assets anzeigen.
1. (Optional) Um die Assets zur Laufzeit bereitzustellen, wählen Sie Assets nach Abschluss des Imports für die Laufzeit bereitstellen. Wenn Sie diese Option nicht auswählen, können Sie die Assets später bereitstellen.
1. Wählen Sie Importieren. Die Anwendung wird auf der Registerkarte &quot;Anwendungen&quot;angezeigt.
1. Melden Sie sich mit Administratorberechtigungen beim CRX-Repository an.
1. Navigieren Sie zu content/dam/lcapplications

   >[!NOTE]
   >
   >Die importierten Anwendungen werden im Knoten lcapplications angezeigt.

1. Klicken Sie auf eine der importierten Anwendungen.

   Die Registerkarte Eigenschaften auf der rechten Seite zeigt die Eigenschaften des ausgewählten CRX-Knotens an.

   Die **syncState** -Eigenschaft gibt den Status der Synchronisierung von Daten zwischen dem AEM forms-Server und dem CRX-Repository an. Sobald der Importvorgang beginnt, wird dieser Status auf 0 (null) gesetzt. Dieser Status zeigt an, dass die Daten derzeit nicht synchronisiert sind. Wenn die Daten synchronisiert werden, wird der Status auf 1 gesetzt.

## Bereitstellen einer Anwendung {#deploy-an-application}

Sie können Anwendungen bereitstellen, die Sie importiert haben oder die Workbench-Benutzer aus Workbench importiert haben.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, die Sie bereitstellen möchten, und klicken Sie auf Bereitstellen .
1. Klicken Sie im angezeigten Bestätigungsdialogfeld auf OK .

## Bereitstellung einer Anwendung aufheben {#undeploy-an-application}

Sie können die Bereitstellung von Anwendungen zur Laufzeit aufheben.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, deren Bereitstellung Sie aufheben möchten, und klicken Sie auf Bereitstellung aufheben .
1. Klicken Sie im angezeigten Bestätigungsdialogfeld auf OK .

## Entfernen einer Anwendung vom Server {#remove-an-application-from-the-server}

Heben Sie die Bereitstellung der Anwendung auf, bevor Sie sie vom Server entfernen.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, die Sie entfernen möchten, und klicken Sie auf Entfernen.
1. Klicken Sie im angezeigten Bestätigungsdialogfeld auf OK .

## Importieren der Laufzeitkonfiguration einer Anwendung {#import-an-application-s-runtime-configuration}

Wenn ein Anwendungsadministrator die Laufzeitkonfiguration für eine Anwendung exportiert hat, können Sie sie in die bereitgestellte Anwendung importieren. Sie können sie entweder mit der Administration Console oder über eine skriptgesteuerte LCA-Bereitstellung importieren.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;.
1. Klicken Sie auf den Namen der Anwendung.
1. Klicken Sie auf &quot;Laufzeitkonfiguration importieren&quot;.
1. Klicken Sie auf Durchsuchen und wählen Sie die XML-Datei aus, die die Laufzeitkonfiguration enthält.
1. Wählen Sie Importieren.

## Exportieren der Laufzeitkonfiguration einer Anwendung {#export-an-application-s-runtime-configuration}

Sie können die Laufzeitkonfigurationsinformationen für bereitgestellte Anwendungen exportieren.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Anwendungen und Dienste&quot;> &quot;Anwendungsverwaltung&quot;.
1. Klicken Sie auf den Namen der Anwendung.
1. Klicken Sie auf &quot;Export Runtime Config&quot;und speichern Sie die erstellte Konfigurationsdatei (XML).

## Skriptgesteuerte Bereitstellung von AEM Forms-Anwendungen {#scripted-deployment-of-aem-forms-applications}

Sie können auch ein skriptgesteuertes Bereitstellungswerkzeug verwenden, um Anwendungsdateien bereitzustellen, einschließlich einer Datei &quot;settings.xml&quot;, die die folgenden Einstellungen angibt:

* Dienstkonfigurationseinstellungen
* Poolkonfigurationseinstellungen
* Endpunktkonfigurationseinstellungen
* Sicherheitsprofile

Durch die skriptgesteuerte Bereitstellung entfällt die Notwendigkeit, die Einstellungen in der Produktionsumgebung vor dem Starten bereitgestellter Anwendungen manuell neu zu konfigurieren.

1. Wechseln Sie an einer Eingabeaufforderung zu „*[aem-forms root]*/sdk/misc/Foundation/ArchiveManagement“.
1. Weitere Informationen finden Sie in der Datei ReadMe.txt .
1. Ändern Sie manuell die Dateien &quot;scriptedDeploy.bat&quot;und &quot;sample-files/sample.xml&quot;, wie in der Datei &quot;readme.txt&quot;beschrieben.
1. Führen Sie die Datei &quot;scriptedDeploy.bat&quot;aus. Durch diese Aktion wird die AEM Formulararchivdatei mit den Einstellungen zum Außerkraftsetzen bereitgestellt.
