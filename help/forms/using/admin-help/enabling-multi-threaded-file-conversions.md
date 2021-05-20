---
title: Aktivieren mehrprozessgestützter Dateikonvertierungen
seo-title: Aktivieren mehrprozessgestützter Dateikonvertierungen
description: Erfahren Sie, wie Sie mehrprozessorgestützte Dateikonvertierung aktivieren.
seo-description: Erfahren Sie, wie Sie mehrprozessorgestützte Dateikonvertierung aktivieren.
uuid: 830c78aa-4f68-4e01-8b24-69a0275689c7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 85d655bb-1b6b-4b4d-ae39-eca3ef9b7fd7
feature: PDF Generator
exl-id: 402c1fd4-c6c8-494e-b452-b56a91c4a397
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 100%

---

# Mehrprozessgestützte Dateikonvertierungen aktivieren {#enabling-multi-threaded-file-conversions}

In PDF Generator haben Sie die Möglichkeit, mehrprozessgestützte Dateikonvertierungen für bestimmte Dateitypen zu aktivieren. Mehrprozessgestützte Dateikonvertierungen verbessern die Leistung von PDF Generator, indem sie es ermöglichen, mehrere Konvertierungen gleichzeitig auszuführen.

## Mehrprozessgestützte Dateikonvertierungen für OpenOffice-, Word- und PowerPoint-Dokumente aktivieren {#enabling-multi-threaded-file-conversions-for-openoffice-word-and-powerpoint-documents}

Standardmäßig kann PDF Generator nur ein OpenOffice-, Microsoft Word- oder PowerPoint-Dokument gleichzeitig konvertieren. Wenn Sie mehrprozessgestützte Konvertierungen aktivieren, kann PDF Generator mehr als ein Dokument gleichzeitig konvertieren. PDF Generator startet mehrere Instanzen von OpenOffice oder von PDFMaker (wird verwendet, um die Word- und PowerPoint-Konvertierungen auszuführen).

>[!NOTE]
>
>Mehrprozessgestützte Dateikonvertierungen werden für Microsoft Word 2003 und PowerPoint 2003 nicht unterstützt. Um mehrprozessgestützte Dateikonvertierungen zu aktivieren, müssen Sie auf Microsoft Word 2007 und PowerPoint 2007 bzw. auf Microsoft Word 2010 und PowerPoint 2010 aktualisieren.

>[!NOTE]
>
>Mehrprozessgestützte Dateikonvertierungen werden von Microsoft Excel, Microsoft Visio, Microsoft Project oder Microsoft Publisher nicht unterstützt.

Jede Instanz von OpenOffice oder PDFMaker wird unter Verwendung eines separaten Benutzerkontos gestartet. Jedes von Ihnen hinzugefügte Benutzerkonto muss zu einem gültigen Benutzer mit Administratorrechten für den Formularservercomputer gehören. In einer Clusterumgebung müssen dieselben Benutzer für alle Knoten des Clusters gültig sein.

Auf der Seite „Benutzerkonten“ in Administration Console können Sie angeben, welche Benutzerkonten für mehrprozessgestützte Dateikonvertierungen verwendet werden sollen. Sie können Konten hinzufügen, löschen oder Kontokennwörter ändern. Wenn Sie PDF Generator unter Windows Server 2003 oder Windows Server 2008 ausführen, müssen Sie mindestens drei Benutzerkonten, die über Administratorberechtigungen verfügen, hinzufügen.

Wenn Sie unter Windows Server 2003 oder 2008 Benutzer für OpenOffice, Microsoft Word oder Microsoft PowerPoint oder unter Linux oder Sun™ Solaris™ Benutzer für OpenOffice hinzufügen, schließen Sie die anfänglichen Aktivierungsdialogfelder für alle Benutzer.

### Die Berechtigung zum Ersetzen des Tokens auf der Prozessebene hinzufügen  {#add-the-right-to-replace-the-process-level-token}

Unter Windows-Betriebssystemen benötigen die Administrator-Benutzerkonten, die für die PDF-Konvertierung verwendet werden (PDFG-Benutzer), die Berechtigung zum Ersetzen von Tokens auf Prozessebene. Sie können diese Berechtigung mithilfe des Gruppenrichtlinien-Editors hinzufügen:

1. Klicken Sie im Windows-Menü „Start“ auf „Ausführen“ und geben Sie dann „gpedit.msc“ ein.
1. Klicken Sie auf „Lokale Computerrichtlinie“ > „Computerkonfiguration“ > „Windows-Einstellungen“ > „Sicherheitseinstellungen“ > „Lokale Richtlinien“ > „Zuweisen von Benutzerrechten“. Bearbeiten Sie die Richtlinie „*Token auf Prozessebene ersetzen*“, damit diese in der Gruppe „Administratoren“ übernommen wird.
1. Fügen Sie den Benutzer dem Eintrag „Token auf Prozessebene ersetzen“ hinzu.

### Weitere für OpenOffice, Microsoft Word und Microsoft PowerPoint unter Windows Server 2008 erforderliche Konfigurationen  {#additional-configuration-required-for-openoffice-microsoft-word-and-microsoft-powerpoint-on-windows-server-2008}

Wenn Sie OpenOffice, Microsoft Word oder Microsoft PowerPoint auf einem System unter Windows Server 2008 ausführen, deaktivieren Sie die Benutzerkontensteuerung (User Account Control, UAC) für jeden hinzugefügten Benutzer.

1. Klicken Sie auf „Systemsteuerung“ > „Benutzerkonten“ > „Benutzerkontensteuerung aktivieren oder deaktivieren“.
1. Deaktivieren Sie das Kontrollkästchen „Benutzerkontensteuerung (UAC) zum Schutz des Computers verwenden“ und klicken Sie auf „OK“.
1. Starten Sie den Computer neu, um die Einstellungen zu übernehmen.

### Weitere für OpenOffice unter Linux oder Solaris erforderliche Konfigurationen  {#additional-configuration-required-for-openoffice-on-linux-or-solaris}

1. Benutzerkonten hinzufügen. (Siehe [Benutzerkonto erstellen](enabling-multi-threaded-file-conversions.md#add-a-user-account).)
1. Als Nächstes nehmen Sie Änderungen an der Datei „/etc/sudoers“ vor. Die Standardberechtigung für diese Datei ist „440“. Ändern Sie die Berechtigung für diese Datei auf Schreibberechtigung.
1. Fügen Sie in der Datei „/etc/sudoers“ Einträge für weitere Benutzer hinzu (außer dem Administrator, der den Formularserver ausführt). Wenn Sie beispielsweise AEM Forms als Benutzer mit dem Namen „lcadm“ auf einem Server mit dem Namen „myhost“ ausführen und Sie die Identität von „Benutzer1“ und „Benutzer2“ annehmen möchten, fügen Sie „/etc/sudoers“ folgende Einträge hinzu:

   ```shell
    lcadm myhost=(user1) NOPASSWD: ALL
    lcadm myhost=(user2) NOPASSWD: ALL
   ```

   Diese Konfiguration ermöglicht „lcadm“, jeden Befehl auf dem Host „myhost“ als „Benutzer1“ oder „Benutzer2“ ohne Kennwortabfrage auszuführen.

   >[!NOTE]
   >
   >Vergewissern Sie sich, dass Sie die Rollen „Systembenutzer“ und „PDFG-Benutzer“ jeweils „Benutzer1“ und „Benutzer2“ zugewiesen haben. Weitere Informationen über das Zuweisen der PDFG-Rolle zu einem Benutzer finden Sie unter [Ein Benutzerkonto hinzufügen](enabling-multi-threaded-file-conversions.md#add-a-user-account).

1. Suchen Sie außerdem die folgende Zeile in der Datei „/etc/sudoers“ und kommentieren Sie sie aus, indem Sie das Zeichen „#“ am Zeileanfang einfügen:

   ```shell
   Defaults requiretty
   ```

   Auf diese Weise können Sie Linux-Benutzer hinzuzufügen.

1. Ändern Sie die Berechtigungen für die Datei „etc/sudoers“ wieder zurück in „440“.
1. Erlauben Sie allen Benutzern, die Sie über [Ein Benutzerkonto hinzufügen](enabling-multi-threaded-file-conversions.md#add-a-user-account) hinzugefügt haben, Verbindungen zum Formularserver herzustellen. Wenn Sie beispielsweise einem lokalen Benutzer mit dem Namen „Benutzer1“ die Berechtigung zuweisen möchten, eine Verbindung zum Formularserver herzustellen, verwenden Sie den folgenden Befehl:

   `xhost +local:user1@`

   Weitere Details finden Sie in der Dokumentation zum xhost-Befehl.

1. Starten Sie den Server neu.

>[!NOTE]
>
>OpenOffice-Formate müssen in einem Ordnerspeicherort installiert werden, auf den alle PDFG-Benutzer zugreifen können. Sie können dies überprüfen, indem Sie sich als PDFG-Benutzer anmelden und testen, ob Sie OpenOffice ohne Probleme starten können.

### Ein Benutzerkonto hinzufügen {#add-a-user-account}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Benutzerkonten“.
1. Klicken Sie auf Hinzufügen und geben Sie den Benutzernamen und das Kennwort des Benutzers ein, der über Administratorrechte auf Forms verfügt. Wenn Sie Benutzer für OpenOffice konfigurieren, schließen Sie die anfänglichen OpenOffice-Aktivierungsdialogfelder.

   >[!NOTE]
   >
   >Wenn Sie Benutzer für OpenOffice konfigurieren, darf die Anzahl der Instanzen von OpenOffice nicht höher sein als die Anzahl der in diesem Schritt angegebenen Benutzerkonten.

1. Starten Sie den Formularserver neu.

### Einen Benutzer aus der Liste für mehrprozessgestützte Dateikonvertierungen entfernen  {#remove-a-user-from-the-list-used-for-multi-threaded-file-conversions}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Benutzerkonten“.
1. Aktivieren Sie das Kontrollkästchen neben dem Benutzer, den Sie entfernen möchten, und klicken Sie auf „Löschen“.
1. Klicken Sie auf der Bestätigungsseite auf „Löschen“.
1. Starten Sie den Formularserver neu.

### Kennwort für ein Konto ändern  {#change-the-password-for-an-account}

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Benutzerkonten“.
1. Klicken Sie auf den Benutzernamen, geben Sie das neue Kennwort ein und bestätigen Sie es. Dieses Kennwort muss mit dem Systemkennwort des Benutzers übereinstimmen.
