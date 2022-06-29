---
title: Anwendungen importieren und verwalten
seo-title: Import and manage applications
description: Anleitung zum Importieren und Verwalten von Anwendungen.
seo-description: Learn how to import and manage applications.
uuid: 7fba6c4e-1a3e-4a4b-9201-acf2ff66a9df
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dc53a6d0-317a-4abd-990c-455e13f8b824
exl-id: f17726c0-3591-4d25-a8b5-3a7024249a56
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '820'
ht-degree: 100%

---

# Anwendungen importieren und verwalten{#import-and-manage-applications}

In AEM Forms ist eine *Anwendung* ein Container zum Speichern von Zusätzen, die für die Implementierung einer AEM Forms-Lösung erforderlich sind. Beispiele von Zusätzen sind Formularentwürfe, Formularfragmente, Bilder, Prozesse, DDX-Dateien, Formular-Guides, HTML-Seiten und SWF-Dateien. Während der Entwicklungsphase eines Projekts können Workbench-Benutzer Anwendungen direkt von dieser Anwendungsansicht in Workbench bereitstellen. Nachdem diese Anwendungen bereitgestellt sind, werden sie in Administration Console auf der Registerkarte „Anwendungen“ auf der Seite „Anwendungsverwaltung“ angezeigt.

Wenn eine Anwendung abgeschlossen ist und auf einem Produktionsserver bereitgestellt werden kann, packt der Workbench-Benutzer die Anwendung in eine *AEM Forms-Anwendungsdatei* (.lca). Anschließend verwendet ein Administrator Administration Console, um die Anwendungsdatei mithilfe der Registerkarte „Anwendungen“ auf der Seite „Anwendungsverwaltung“ zu importieren und bereitzustellen.

Sie können außerdem die Registerkarte „Archive“ auf der Seite „Anwendungsverwaltung“ verwenden, um LCAs, die mithilfe von Workbench 8.x erstellt wurden, zu importieren.

>[!NOTE]
>
>Es ist ein bekanntes Problem, dass LCA-Dateien aus einer zukünftigen Version nicht notwendigerweise abwärtskompatibel sind. Möglicherweise können LCA-Dateien aus einer zukünftigen Version von AEM Forms (beispielsweise einer Vorabversion) zwar angezeigt und importiert werden, doch wird dies nicht unterstützt und es kann zu ungewöhnlichem Verhalten kommen.

Verwenden Sie die Registerkarte „Anwendungen“, um Anwendungen, die in Workbench erstellt wurden, zu importieren. Anwendungsadministratoren können außerdem die Laufzeitkonfigurationsdatei für eine Anwendung exportieren. Dadurch entfällt die Notwendigkeit zur manuellen Neukonfiguration von Einstellungen in der Produktionsumgebung vor dem Starten bereitgestellter Anwendungen. Die Laufzeitkonfigurationsdatei beinhaltet:

* Einstellungen zur Dienstkonfiguration
* Einstellungen zur Poolkonfiguration
* Einstellungen zur Endpunktkonfiguration
* Sicherheitsprofile

## Eine Anwendung oder ein Archiv importieren {#import-an-application-or-archive}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Wählen Sie Importieren.
1. Klicken Sie auf „Durchsuchen“, wählen Sie die zu importierende LCA-Datei aus und klicken Sie auf „Vorschau“. Auf der Seite „Anwendungsvorschau“ werden Informationen über die Anwendung angezeigt.
1. (Optional) Klicken Sie zum Anzeigen einer Liste der in der Anwendung enthaltenen Elemente auf „Assets anzeigen“.
1. (Optional) Wählen Sie zum Bereitstellen der Elemente in der Laufzeit die Option „Assets nach Abschluss des Imports für die Laufzeit bereitstellen“. Wenn Sie diese Option nicht auswählen, können Sie die Zusätze später bereitstellen.
1. Wählen Sie Importieren. Die Anwendung wird auf der Registerkarte „Anwendungen“ angezeigt.
1. Melden Sie sich mit Administratorberechtigungen beim CRX-Repository an.
1. Navigieren Sie zu content/dam/lcapplications

   >[!NOTE]
   >
   >Die importierten Anwendungen werden im Knoten „lcapplications“ angezeigt.

1. Klicken Sie auf eine der importierten Anwendungen.

   Auf der Registerkarte „Eigenschaften“ werden die Eigenschaften des ausgewählten CRX-Knotens angezeigt.

   Die Eigenschaft **syncState** zeigt den Status der Synchronisierung der Daten zwischen dem AEM Forms-Server und dem CRX-Repository an. Sobald der Importvorgang beginnt, wird dieser Status auf 0 (null) gesetzt. Dieser Status gibt an, dass die Daten derzeit nicht synchronisiert werden. Wenn die Daten synchronisiert werden, wird der Status auf 1 festgelegt.

## Eine Anwendung bereitstellen {#deploy-an-application}

Sie können Anwendungen bereitstellen, die Sie importiert haben oder die Workbench-Benutzer aus Workbench importiert haben.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, die Sie bereitstellen möchten, und klicken Sie auf „Bereitstellen“.
1. Klicken Sie im Bestätigungsdialogfeld auf „OK“.

## Bereitstellung einer Anwendung aufheben {#undeploy-an-application}

Sie können die Bereitstellung von Anwendungen aus der Laufzeit aufheben.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, für die Sie die Bereitstellung aufheben möchten, und klicken Sie auf „Bereitstellung aufheben“.
1. Klicken Sie im Bestätigungsdialogfeld auf „OK“.

## Eine Anwendung vom Server entfernen {#remove-an-application-from-the-server}

Heben Sie die Bereitstellung der Anwendung auf, bevor Sie sie vom Server entfernen.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Aktivieren Sie das Kontrollkästchen neben der Anwendung, die Sie entfernen möchten, und klicken Sie auf „Entfernen“.
1. Klicken Sie im Bestätigungsdialogfeld auf „OK“.

## Die Laufzeitkonfiguration einer Anwendung importieren {#import-an-application-s-runtime-configuration}

Wenn der Anwendungsadministrator die Laufzeitkonfiguration für eine Anwendung exportiert hat, können Sie diese Datei in die bereitgestellte Anwendung importieren. Sie können sie entweder mithilfe von Administration Console oder über eine skriptgesteuerte LCA-Bereitstellung importieren.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Klicken Sie auf den Namen der Anwendung.
1. Klicken Sie auf „Laufzeitkonfiguration importieren“.
1. Klicken Sie auf „Durchsuchen“ und wählen Sie die XML-Datei aus, die die Laufzeitkonfiguration enthält.
1. Wählen Sie Importieren.

## Die Laufzeitkonfiguration einer Anwendung exportieren {#export-an-application-s-runtime-configuration}

Sie können die Informationen zur Laufzeitkonfiguration für bereitgestellte Anwendungen exportieren.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Anwendungsverwaltung“.
1. Klicken Sie auf den Namen der Anwendung.
1. Klicken Sie auf „Laufzeitkonfiguration exportieren“ und speichern Sie die erstellte Konfigurationsdatei (XML).

## Skriptgesteuerte Bereitstellung von AEM Forms-Anwendungen {#scripted-deployment-of-aem-forms-applications}

Sie können außerdem ein skriptgesteuertes Bereitstellungswerkzeug zum Bereitstellen von Anwendungsdateien verwenden, einschließlich einer Datei „settings.xml“, die die folgenden Einstellungen angibt:

* Einstellungen zur Dienstkonfiguration
* Einstellungen zur Poolkonfiguration
* Einstellungen zur Endpunktkonfiguration
* Sicherheitsprofile

Durch die skriptgesteuerte Bereitstellung entfällt die Notwendigkeit zur manuellen Neukonfiguration von Einstellungen in der Produktionsumgebung vor dem Starten bereitgestellter Anwendungen.

1. Wechseln Sie an einer Eingabeaufforderung zu „*[aem-forms root]*/sdk/misc/Foundation/ArchiveManagement“.
1. Detailliertere Anweisungen finden Sie in der Datei „ReadMe.txt“.
1. Ändern Sie die Dateien „scriptedDeploy.bat“ und „sample-files/sample.xml“ manuell wie in der Datei „ReadMe.txt“ beschrieben.
1. Führen Sie die Datei „scriptedDeploy.bat“ aus. Durch diesen Vorgang wird die AEM Forms-Archivdatei mit den neuen Einstellungen bereitgestellt.
