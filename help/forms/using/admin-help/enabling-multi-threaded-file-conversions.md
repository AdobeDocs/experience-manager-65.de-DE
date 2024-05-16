---
title: Aktivieren mehrprozessgestützter Dateikonvertierungen
description: Erfahren Sie, wie Sie mehrprozessgestützte Dateikonvertierungen aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: 402c1fd4-c6c8-494e-b452-b56a91c4a397
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '884'
ht-degree: 100%

---

# Aktivieren mehrprozessgestützter Dateikonvertierungen {#enabling-multi-threaded-file-conversions}

Mit PDF Generator können Sie mehrprozessgestützte Dateikonvertierungen für bestimmte Dateitypen aktivieren. Mehrprozessgestützte Dateikonvertierungen verbessern die Leistung von PDF Generator, da sie die gleichzeitige Ausführung mehrerer Konvertierungen ermöglichen.

## Aktivieren mehrprozessgestützter Dateikonvertierungen für OpenOffice-, Word- und PowerPoint-Dokumente {#enabling-multi-threaded-file-conversions-for-openoffice-word-and-powerpoint-documents}

Standardmäßig kann PDF Generator jeweils nur ein OpenOffice-, Microsoft® Word- oder PowerPoint-Dokument konvertieren. Wenn Sie mehrprozessgestützte Konvertierungen aktivieren, kann PDF Generator mehrere Dokumente gleichzeitig konvertieren. PDF Generator startet mehrere Instanzen von OpenOffice oder PDFMaker (wird zum Ausführen der Word- und PowerPoint-Konvertierungen verwendet).

>[!NOTE]
>
>Mehrprozessgestützte Dateikonvertierungen werden in Microsoft® Word 2003 und PowerPoint 2003 nicht unterstützt. Um mehrprozessgestützte Dateikonvertierungen zu aktivieren, führen Sie ein Upgrade auf Microsoft® Word 2007 und PowerPoint 2007 oder Microsoft® Word 2010 und PowerPoint 2010 durch.

>[!NOTE]
>
>Mehrprozessgestützte Dateikonvertierungen werden von Microsoft® Excel, Microsoft® Visio, Microsoft® Project oder Microsoft® Publisher nicht unterstützt.

Jede Instanz von OpenOffice oder PDFMaker wird unter Verwendung eines separaten Benutzerkontos gestartet. Jedes von Ihnen hinzugefügte Benutzerkonto muss zu einer gültigen Person mit Administratorrechten für den Computer mit dem Formular-Server gehören. In einer Cluster-Umgebung muss derselbe Satz von Benutzenden für alle Knoten des Clusters gültig sein.

Auf der Seite „Benutzerkonten“ in der Administrationskonsole können Sie angeben, welche Benutzerkonten für mehrprozessgestützte Dateikonvertierungen verwendet werden sollen. Sie können Konten hinzufügen und löschen oder Kontokennwörter ändern. Wenn Sie PDF Generator unter Windows Server 2003 oder Windows Server 2008 ausführen, fügen Sie mindestens drei Benutzerkonten mit Administratorrechten hinzu.

Wenn Sie Benutzende für OpenOffice, Microsoft® Word oder Microsoft® PowerPoint unter Windows Server 2003 oder 2008 oder für OpenOffice unter Linux® oder Sun™ Solaris™ hinzufügen, schließen Sie die anfänglichen Aktivierungsdialogfelder für alle Benutzenden.

### Hinzufügen der Berechtigung zum Ersetzen des Tokens auf Prozessebene {#add-the-right-to-replace-the-process-level-token}

Unter einem Windows-Betriebssystem müssen die Administrator-Benutzerkonten, die für die PDF-Konvertierung verwendet werden (PDFG-Benutzende), die Token-Berechtigungen auf Prozessebene ersetzen. Sie können diese Berechtigung mit dem Gruppenrichtlinieneditor hinzufügen:

1. Klicken Sie im Windows-Startmenü auf „Ausführen“ und geben Sie dann „gpedit.msc“ ein.
1. Klicken Sie auf „Lokale Computerrichtlinie“ > „Computerkonfiguration“ > „Windows-Einstellungen“ > „Sicherheitseinstellungen“ > „Lokale Richtlinien“ > „Zuweisen von Benutzerrechten“. Bearbeiten Sie die Richtlinie *Token auf Prozessebene ersetzen*, um die Gruppe „Administratoren“ einzubeziehen.
1. Fügen Sie dem Eintrag „Token auf Prozessebene ersetzen“ Benutzende hinzu.

### Zusätzliche erforderlich Konfigurationsschritte für OpenOffice, Microsoft® Word und Microsoft® PowerPoint unter Windows Server 2008 {#additional-configuration-required-for-openoffice-microsoft-word-and-microsoft-powerpoint-on-windows-server-2008}

Wenn Sie OpenOffice, Microsoft® Word oder Microsoft® PowerPoint unter Windows Server 2008 ausführen, deaktivieren Sie die Benutzerkontensteuerung für alle hinzugefügten Benutzenden.

1. Klicken Sie auf „Systemsteuerung“ > „Benutzerkonten“ > „Benutzerkontensteuerung aktivieren oder deaktivieren“.
1. Deaktivieren Sie das Kontrollkästchen „Benutzerkontensteuerung (UAC) zum Schutz des Computers verwenden“ und klicken Sie auf „OK“.
1. Starten Sie den Computer neu, damit die Einstellungen wirksam werden.

### Zusätzliche für OpenOffice unter Linux® oder Solaris™ erforderliche Konfiguration {#additional-configuration-required-for-openoffice-on-linux-or-solaris}

1. Fügen Sie Benutzerkonten hinzu. (Siehe [Hinzufügen eines Benutzerkontos](enabling-multi-threaded-file-conversions.md#add-a-user-account).)
1. Als Nächstes müssen Sie die Datei „/etc/sudoers“ ändern. Die Standardberechtigung für diese Datei lautet 440. Ändern Sie die Berechtigung für diese Datei in Schreibzugriff.
1. Fügen Sie Einträge für weitere Benutzende (außer den Admins, die den Forms-Server ausführen) in der Datei „/etc/sudoers“ hinzu. Wenn Sie beispielsweise AEM Forms als Benutzende mit dem Namen „lcadm“ und einem Server mit dem Namen „myhost“ ausführen und Sie die Identität von user1 und user2 annehmen möchten, fügen Sie „/etc/sudoers“ die folgenden Einträge hinzu:

   ```shell
    lcadm myhost=(user1) NOPASSWD: ALL
    lcadm myhost=(user2) NOPASSWD: ALL
   ```

   Diese Konfiguration ermöglicht es „lcadm“, jeden Befehl auf dem Host „myhost“ als „user1“ oder „user2“ auszuführen, ohne ein Kennwort einzugeben.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie „user1“ und „user2“ die Rollen „Systembenutzer“ und „PDFG-Benutzer“ zugewiesen haben. Informationen zum Zuweisen einer PDFG-Rolle zu Benutzenden finden Sie unter [Hinzufügen eines Benutzerkontos](enabling-multi-threaded-file-conversions.md#add-a-user-account)

1. Suchen Sie diese Zeile in der Datei „/etc/sudoers“ und kennzeichnen Sie sie als Kommentar, indem Sie am Anfang der Zeile ein Nummernzeichen (#) hinzufügen:

   ```shell
   Defaults requiretty
   ```

   Dadurch können Sie Linux®-Benutzende hinzufügen.

1. Ändern Sie die Berechtigung für die Datei „etc/sudoers“ wieder in 440.
1. Erlauben Sie allen Benutzenden, die Sie über [Benutzerkonto hinzufügen](enabling-multi-threaded-file-conversions.md#add-a-user-account) hinzugefügt haben, Verbindungen mit dem Formular-Server herzustellen. Wenn Sie beispielsweise einem lokalen Benutzer namens „Benutzer1“ die Berechtigung erteilen möchten, eine Verbindung mit dem Formular-Server herzustellen, verwenden Sie den folgenden Befehl:

   `xhost +local:user1@`

   Weitere Details finden Sie in der Dokumentation zum xhost-Befehl.

1. Starten Sie den Server neu.

>[!NOTE]
>
>OpenOffice muss in einem Ordnerspeicherort, auf den alle PDFG-Benutzenden zugreifen können, installiert werden. Sie können dies überprüfen, indem Sie sich als PDFG-Benutzende anmelden und testen, ob Sie OpenOffice ohne Probleme starten können.

### Hinzufügen eines Benutzerkontos {#add-a-user-account}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Benutzerkonten“.
1. Klicken Sie auf „Hinzufügen“ und geben Sie den Namen und das Kennwort der Benutzerin oder des Benutzers ein, die bzw. der über Administratorrechte auf dem Formular-Server verfügt.  Wenn Sie Benutzerinnen oder Benutzer für OpenOffice konfigurieren, schließen Sie die anfänglichen OpenOffice-Aktivierungsdialogfelder.

   >[!NOTE]
   >
   >Wenn Sie Benutzerinnen oder Benutzer für OpenOffice konfigurieren, darf die Anzahl der Instanzen von OpenOffice nicht höher sein als die Anzahl der in diesem Schritt angegebenen Benutzerkonten.

1. Starten Sie den Formular-Server neu.

### Entfernen einer Benutzerin oder eines Benutzers aus der Liste für mehrprozessgestützte Dateikonvertierungen {#remove-a-user-from-the-list-used-for-multi-threaded-file-conversions}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Benutzerkonten“.
1. Aktivieren Sie das Kontrollkästchen neben der Person, die Sie entfernen möchten, und klicken Sie auf „Löschen“.
1. Klicken Sie auf der Bestätigungsseite auf „Löschen“.
1. Starten Sie den Formular-Server neu.

### Ändern des Kennworts für ein Konto {#change-the-password-for-an-account}

1. Klicken Sie in der Administrationskonsole auf „Dienste“ > „PDF Generator“ > „Benutzerkonten“.
1. Klicken Sie auf den Benutzernamen, geben Sie das neue Kennwort ein und bestätigen Sie es.  Dieses Kennwort muss mit dem Systemkennwort der Person übereinstimmen.
