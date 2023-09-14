---
title: Aktivieren mehrprozessgestützter Dateikonvertierungen
description: Erfahren Sie, wie Sie mehrprozessgestützte Dateikonvertierungen aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: 402c1fd4-c6c8-494e-b452-b56a91c4a397
source-git-commit: fd8bb7d3d9040e0a7a6b2f65751445f41aeab73e
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 3%

---

# Aktivieren mehrprozessgestützter Dateikonvertierungen {#enabling-multi-threaded-file-conversions}

Mit PDF Generator können Sie mehrprozessgestützte Dateikonvertierungen für bestimmte Dateitypen aktivieren. Mehrprozessgestützte Dateikonvertierungen verbessern die Leistung von PDF Generator, da sie mehrere Konvertierungen gleichzeitig ermöglichen.

## Mehrprozessgestützte Dateikonvertierungen für OpenOffice-, Word- und PowerPoint-Dokumente aktivieren {#enabling-multi-threaded-file-conversions-for-openoffice-word-and-powerpoint-documents}

Standardmäßig kann der PDF Generator jeweils nur ein OpenOffice-, Microsoft® Word- oder PowerPoint-Dokument konvertieren. Wenn Sie mehrprozessgestützte Konvertierungen aktivieren, kann der PDF Generator mehrere Dokumente gleichzeitig konvertieren. PDF Generator startet mehrere Instanzen von OpenOffice oder PDFMaker (verwendet zum Ausführen der Word- und PowerPoint-Konvertierungen).

>[!NOTE]
>
>Mehrprozessgestützte Dateikonvertierungen werden in Microsoft® Word 2003 und PowerPoint 2003 nicht unterstützt. Um mehrprozessgestützte Dateikonvertierungen zu aktivieren, aktualisieren Sie auf Microsoft® Word 2007 und PowerPoint 2007 oder Microsoft® Word 2010 und PowerPoint 2010.

>[!NOTE]
>
Mehrprozessgestützte Dateikonvertierungen werden von Microsoft® Excel, Microsoft® Visio, Microsoft® Project oder Microsoft® Publisher nicht unterstützt.

Jede Instanz von OpenOffice oder PDFMaker wird mithilfe eines separaten Benutzerkontos gestartet. Jedes von Ihnen hinzugefügte Benutzerkonto muss ein gültiger Benutzer mit Administratorrechten auf dem Forms Server-Computer sein. In einer Clusterumgebung muss derselbe Satz von Benutzern für alle Knoten des Clusters gültig sein.

Auf der Seite &quot;Benutzerkonten&quot;in Administration Console können Sie angeben, welche Benutzerkonten für mehrprozessgestützte Dateikonvertierungen verwendet werden sollen. Sie können Konten hinzufügen, löschen oder Kontokennwörter ändern. Wenn Sie PDF Generator unter Windows Server 2003 oder Windows Server 2008 ausführen, fügen Sie mindestens drei Benutzerkonten mit Administratorrechten hinzu.

Wenn Sie Benutzer für OpenOffice, Microsoft® Word oder Microsoft® PowerPoint unter Windows Server 2003 oder 2008 oder für OpenOffice unter Linux® oder Sun™ Solaris™ hinzufügen, schließen Sie die anfänglichen Aktivierungsdialogfelder für alle Benutzer.

### Berechtigung zum Ersetzen des Tokens auf Prozessebene hinzufügen {#add-the-right-to-replace-the-process-level-token}

Unter einem Windows-Betriebssystem müssen die Administrator-Benutzerkonten, die für die PDF-Konvertierung verwendet werden (PDFG-Benutzer), die Tokenberechtigungen auf Prozessebene ersetzen. Sie können diese Berechtigung mit dem Gruppenrichtlinien-Editor hinzufügen:

1. Klicken Sie im Windows-Startmenü auf Ausführen und geben Sie dann gpedit.msc ein.
1. Klicken Sie auf Lokale Computerrichtlinie > Computerkonfiguration > Windows-Einstellungen > Sicherheitseinstellungen > Lokale Richtlinien > Zuweisen von Benutzerrechten. Bearbeiten Sie die *Ersetzen eines Tokens auf Prozessebene* Richtlinie, um die Gruppe Administratoren einzubeziehen.
1. Fügen Sie den Benutzer zum Eintrag &quot;Token auf Prozessebene ersetzen&quot;hinzu.

### Zusätzliche Konfigurationsschritte für OpenOffice, Microsoft® Word und Microsoft® PowerPoint unter Windows Server 2008 {#additional-configuration-required-for-openoffice-microsoft-word-and-microsoft-powerpoint-on-windows-server-2008}

Wenn Sie OpenOffice, Microsoft® Word oder Microsoft® PowerPoint unter Windows Server 2008 ausführen, deaktivieren Sie die Benutzerkontensteuerung für jeden hinzugefügten Benutzer.

1. Klicken Sie auf Systemsteuerung > Benutzerkonten > Benutzerkontensteuerung aktivieren oder deaktivieren.
1. Deaktivieren Sie das Kontrollkästchen „Benutzerkontensteuerung (UAC) zum Schutz des Computers verwenden“ und klicken Sie auf „OK“.
1. Starten Sie den Computer neu, damit die Einstellungen wirksam werden.

### Zusätzliche für OpenOffice unter Linux® oder Solaris™ erforderliche Konfiguration {#additional-configuration-required-for-openoffice-on-linux-or-solaris}

1. Benutzerkonten hinzufügen. (Siehe [Hinzufügen von Benutzerkonten](enabling-multi-threaded-file-conversions.md#add-a-user-account).
1. Als Nächstes müssen Sie die Datei /etc/sudoers ändern. Die Standardberechtigung für diese Datei ist 440. Ändern Sie die Berechtigung für diese Datei in Schreibzugriff.
1. Fügen Sie Einträge für weitere Benutzer (außer dem Administrator, der den Forms-Server ausführt) in der Datei /etc/sudoers hinzu. Wenn Sie beispielsweise AEM Formulare als Benutzer mit dem Namen lcadm und einem Server mit dem Namen myhost ausführen und Sie die Identität von Benutzer1 und Benutzer2 annehmen möchten, fügen Sie &quot;/etc/sudoers&quot;die folgenden Einträge hinzu:

   ```shell
    lcadm myhost=(user1) NOPASSWD: ALL
    lcadm myhost=(user2) NOPASSWD: ALL
   ```

   Diese Konfiguration ermöglicht es lcadm, jeden Befehl auf dem Host &quot;myhost&quot;als &quot;user1&quot;oder &quot;user2&quot;auszuführen, ohne ein Kennwort einzugeben.

   >[!NOTE]
   >
   Stellen Sie sicher, dass Sie &quot;Benutzer1&quot;und &quot;Benutzer2&quot;Systembenutzer- und PDFG-Benutzerrollen zugewiesen haben. Informationen zum Zuweisen einer PDFG-Rolle zu einem Benutzer finden Sie unter [Hinzufügen von Benutzerkonten](enabling-multi-threaded-file-conversions.md#add-a-user-account)

1. Suchen und kommentieren Sie diese Zeile auch in der Datei &quot;/etc/sudoers&quot;aus, indem Sie am Anfang der Zeile ein Nummernzeichen (#) hinzufügen:

   ```shell
   Defaults requiretty
   ```

   Dadurch können Sie Linux®-Benutzer hinzufügen.

1. Ändern Sie die Berechtigung für die Datei &quot;etc/sudoers&quot;zurück in 440.
1. Alle Benutzer zulassen, die Sie über hinzugefügt haben [Hinzufügen von Benutzerkonten](enabling-multi-threaded-file-conversions.md#add-a-user-account) , um Verbindungen zum Forms-Server herzustellen. Um beispielsweise einem lokalen Benutzer mit dem Namen &quot;Benutzer1&quot;die Berechtigung zu geben, eine Verbindung zum Forms-Server herzustellen, verwenden Sie den folgenden Befehl:

   `xhost +local:user1@`

   Weitere Informationen finden Sie in der Dokumentation zum xhost-Befehl .

1. Starten Sie den Server neu.

>[!NOTE]
>
OpenOffice muss in einem Ordnerspeicherort installiert sein, auf den alle PDFG-Benutzer zugreifen können. Sie können dies überprüfen, indem Sie sich als PDFG-Benutzer anmelden und überprüfen, ob Sie OpenOffice ohne Probleme starten können.

### Hinzufügen von Benutzerkonten {#add-a-user-account}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Benutzerkonten&quot;.
1. Klicken Sie auf Hinzufügen und geben Sie den Benutzernamen und das Kennwort eines Benutzers ein, der über Administratorrechte auf dem Forms-Server verfügt. Wenn Sie Benutzer für OpenOffice konfigurieren, schließen Sie die anfänglichen OpenOffice-Aktivierungsdialogfelder.

   >[!NOTE]
   >
   Wenn Sie Benutzer für OpenOffice konfigurieren, darf die Anzahl der Instanzen von OpenOffice nicht größer sein als die Anzahl der in diesem Schritt angegebenen Benutzerkonten.

1. Starten Sie den Forms-Server neu.

### Entfernen Sie einen Benutzer aus der Liste für mehrprozessgestützte Dateikonvertierungen {#remove-a-user-from-the-list-used-for-multi-threaded-file-conversions}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Benutzerkonten&quot;.
1. Aktivieren Sie das Kontrollkästchen neben dem Benutzer, den Sie entfernen möchten, und klicken Sie auf Löschen .
1. Klicken Sie auf der Bestätigungsseite auf Löschen.
1. Starten Sie den Forms-Server neu.

### Ändern des Kennworts für ein Konto {#change-the-password-for-an-account}

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;PDF Generator&quot;> &quot;Benutzerkonten&quot;.
1. Klicken Sie auf den Benutzernamen, geben Sie das neue Kennwort ein und bestätigen Sie es. Dieses Kennwort muss mit dem Systemkennwort des Benutzers übereinstimmen.
