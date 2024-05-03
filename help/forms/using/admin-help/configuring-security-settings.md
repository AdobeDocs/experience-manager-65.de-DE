---
title: Konfigurieren von Sicherheitseinstellungen
description: Erfahren Sie, wie Sie die Sicherheitseinstellungen konfigurieren. Sie können PDF-Dokumente schützen, indem Sie den Zugriff einschränken. Sie können das Dokument verschlüsseln, zertifizieren oder mit einem Passwort schützen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: be076477-2681-4570-953d-6c44d3c30843
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 100%

---

# Konfigurieren von Sicherheitseinstellungen{#configuring-security-settings}

Sie können den Zugriff auf PDF-Dokumente einschränken, indem Sie Passwörter festlegen und bestimmte Funktionen wie Drucken und Bearbeiten einschränken. Wenn ein PDF-Dokument eingeschränkte Funktionen aufweist, sind die damit verbundenen Tools und Menüelemente grau unterlegt. Sie können auch andere Methoden verwenden, um sichere Dokumente zu erstellen, z. B. das Verschlüsseln oder Zertifizieren eines Dokuments. Eine Sicherheitseinstellung enthält das Kennwort und bestimmte Optionen, die für bestimmte PDF-Konvertierungen verwendet werden sollen.

Auf der Seite „Sicherheitseinstellungen“ können Sie die folgenden Aufgaben ausführen:

## Erstellen oder Bearbeiten einer Sicherheitseinstellung {#create-or-edit-a-security-setting}

Eine *Sicherheitseinstellung* steuert die Sicherheit und Berechtigungen für Dateien, die mit dieser Sicherheitseinstellung konvertiert werden.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „PDF Generator“ > „Sicherheitseinstellungen“.
1. Klicken Sie auf „Neu“ oder auf den Namen einer Sicherheitseinstellung.
1. Füllen Sie auf der Seite „Neue Sicherheitseinstellung/Bearbeiten einer Sicherheitseinstellung“ die erforderlichen Informationen für die Sicherheitseinstellung aus. (Siehe [Konfiguration der Dateitypeinstellungen](/help/forms/using/admin-help/configuring-file-type-settings.md#configuring-file-type-settings).)
1. Klicken Sie auf „Speichern“, geben Sie in dem daraufhin angezeigten Dialogfeld einen Namen für die Einstellung ein und klicken Sie dann auf „OK“.

### Sicherheitseinstellungen {#security-settings}

Diese Einstellungen konfigurieren die Kompatibilität und Verschlüsselung. Anweisungen zum Zugriff auf Schriftarteneinstellungen finden Sie unter [Erstellen oder Bearbeiten von Dateitypeinstellungen](configuring-security-settings.md#create-or-edit-a-security-setting).

**Kompatibilität:** Legt den Verschlüsselungstyp zum Öffnen eines kennwortgeschützten Dokuments fest. Die Option „Acrobat 3.0 und höher“ verwendet einen niedrigen Verschlüsselungsgrad. Die anderen Optionen verwenden einen hohen Verschlüsselungsgrad.

**Acrobat 3.0 und höher:** Verwendet niedrige Verschlüsselung (40-Bit RC4).

**Acrobat 5.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit RC4).

**Acrobat 6.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit RC4). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen.

**Acrobat 7.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit AES). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen und die ausschließliche Verschlüsselung von Dateianlagen.

**Acrobat 9.0 und höher:** Verwendet hohe Verschlüsselung (256-Bit AES). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen und die ausschließliche Verschlüsselung von Dateianlagen.

Eine frühere Version von Acrobat kann kein PDF-Dokument öffnen, das über eine höhere Kompatibilitätseinstellung verfügt. Wenn Sie beispielsweise die Option „Acrobat 7.0 und höher“ auswählen, können Sie das Dokument nicht in Acrobat 6.0 oder früher öffnen.

Stellen Sie sicher, dass die Kompatibilitätsstufe mit der PDF-Kompatibilitätsstufe für dieselbe Quelle übereinstimmt. Wenn Sie beispielsweise einen überwachten Ordner für die Verwendung der PDF-Standardeinstellung konfiguriert haben, die mit Acrobat 5.0 oder höher kompatibel ist, darf die Sicherheitskompatibilitätsstufe nicht höher als Acrobat 5.0 sein.

**Dokumenteinschränkung:** Die verfügbaren Dokumenteinschränkungen sind von der ausgewählten Kompatibilitätsoption abhängig.

**Keine Verschlüsselung:** Kein Teil des Dokuments wird verschlüsselt.

**Gesamten Dokumentinhalt verschlüsseln:** Verschlüsselt das Dokument und die Dokumentmetadaten. Bei Aktivierung dieser Option können Suchmaschinen nicht auf die Dokumentmetadaten zugreifen.

**Gesamten Dokumentinhalt mit Ausnahme von Metadaten verschlüsseln (Acrobat
6 und höher kompatibel):** Verschlüsselt den Inhalt eines Dokuments, ermöglicht jedoch Suchmaschinen den Zugriff auf die Dokumentmetadaten. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 6.0 und höher“, „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ festgelegt ist.

**Nur Dateianlagen verschlüsseln (Acrobat 7 und höher
kompatibel):** Benutzer können das Dokument ohne Kennwort öffnen, müssen jedoch ein Kennwort eingeben, um Dateianlagen zu öffnen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf Acrobat 7.0 oder höher oder auf Acrobat 9.0 oder höher eingestellt ist.

Mit diesen Einstellungen wird die Passwortsicherheit konfiguriert:

>[!NOTE]
>
>Wenn Sie ein Passwort vergessen haben, kann es nicht aus dem Dokument wiederhergestellt werden. Es wird empfohlen, Passwörter an einem anderen sicheren Ort zu speichern, falls Sie sie vergessen. Bewahren Sie außerdem eine Sicherungskopie des Dokuments auf, die nicht passwortgeschützt ist.

**Kennwort zum Öffnen des Dokuments erforderlich:** Aktiviert die Kennwortoptionen.

**Kennwort zum Öffnen des Dokuments:** Ermöglicht Benutzern das Öffnen des Dokuments nur, wenn sie das von Ihnen festgelegte Kennwort eingeben. Bei Passwörtern wird zwischen Groß- und Kleinschreibung unterschieden. Acrobat verwendet die RC4-Sicherheitsmethode von RSA Security Inc., um PDF-Dokumente mit Passwörtern zu schützen. Wenn Sie das Drucken und Bearbeiten einschränken, wird empfohlen, ein Passwort zum Öffnen von Dokumenten hinzuzufügen, um die Sicherheit zu erhöhen.

**Kennwort zum Öffnen des Dokuments erneut eingeben:** Stellt sicher, dass das Kennwort zum Öffnen des Dokuments korrekt ist.

**Kennwort zum Öffnen von Dateianlagen erforderlich:** Aktiviert die Kennwortoptionen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

**Kennwort zum Öffnen der Dateianlage:** Stellt sicher, dass zum Öffnen eines Dateianhangs ein Kennwort erforderlich ist. Benutzende können das Dokument ohne Passwort öffnen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

**Kennwort zum Öffnen der Dataianlage erneut eingeben:** Stellt sicher, dass das Kennwort korrekt ist. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

Diese Optionen konfigurieren die Berechtigungen:

**Kennwort verwenden, um das Drucken und Bearbeiten des 
Dokuments bzw. seiner Sicherheitseinstellungen einzuschränken:** Ermöglicht die Einschränkung von Berechtigungen.

**Berechtigungskennwort:** Schränkt das Drucken und Bearbeiten für Benutzer ein. Benutzende können diese Sicherheitseinstellungen nur ändern, wenn sie das von Ihnen festgelegte Passwort eingeben. Sie können nicht dasselbe Passwort verwenden, das für das Öffnen von Dokumenten verwendet wird. Wenn Sie ein Berechtigungspasswort festlegen, können nur die Personen, die dieses Passwort eingeben, die Sicherheitseinstellungen ändern. Wenn das PDF-Dokument beide Passworttypen aufweist, lässt es durch eines der beiden Passwörter öffnen. Allerdings können Benutzende die eingeschränkten Funktionen nur mit dem Berechtigungspasswort einstellen oder ändern. Wenn das PDF-Dokument nur über das Berechtigungspasswort verfügt oder wenn Benutzende das Dokument mit dem Passwort zum Öffnen des Dokuments öffnen, wird die Passwortaufforderung angezeigt, wenn Benutzende versuchen, die Sicherheitseinstellungen zu ändern.

**Berechtigungskennwort erneut eingeben:** Stellt sicher, dass das Berechtigungskennwort korrekt ist.

**Drucken erlaubt:** Legt die Druckqualität für das PDF-Dokument fest:

**Keine:** Hindert Benutzer am Drucken des Dokuments.

**Geringe Auflösung (150 dpi):** Ermöglicht Benutzern das Drucken des Dokuments mit einer Maximalauflösung von 150 dpi. Das Drucken kann langsamer sein, da jede Seite als Bitmap-Bild gedruckt wird. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Hohe Auflösung** Ermöglicht Benutzern das Drucken mit beliebiger Auflösung, wobei eine Vektorausgabe hoher Qualität auf PostScript- und anderen Druckern erfolgen kann, die erweiterte Funktionen für hohe Druckqualität unterstützen.

**Zulässige Änderungen:** Legt fest, welche Bearbeitungsvorgänge für das PDF-Dokument zulässig sind:

**Keine:** Hindert Benutzer am Ändern des Dokuments, einschließlich des Ausfüllens von Signatur- und Formularfeldern.

**Seiten einfügen, löschen und drehen:** Ermöglicht Benutzenden das Einfügen, Löschen und Drehen von Seiten sowie das Erstellen von Lesezeichen und Miniaturansichten. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Ausfüllen von Formularfeldern und Unterschreiben vorhandener 
Unterschriftsfelder:** Ermöglicht Benutzern das Ausfüllen von Formularen und das Hinzufügen digitaler Signaturen. Benutzende können jedoch keine Kommentare hinzufügen oder Formularfelder erstellen. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Kommentieren, Ausfüllen von Formularfeldern und Unterschreiben vorhandener 
Unterschriftsfelder:** Ermöglicht Benutzern das Ausfüllen von Formularen und das Hinzufügen digitaler Signaturen und Kommentare.

**Seitenlayout, TouchUp-Funktion, Ausfüllen von Formularfeldern und Unterschreiben 
vorhandener Unterschriftsfelder:** Ermöglicht Benutzern das Einfügen, Drehen oder Löschen von Seiten sowie das Erstellen von Lesezeichen oder Miniaturbildern, das Ausfüllen von Formularen und das Hinzufügen digitaler Signaturen. Mit dieser Option können Benutzende keine Formularfelder erstellen. Diese Option ist nur verfügbar, wenn eine niedrige Verschlüsselungsstufe (Acrobat 3.0) gewählt wurde.

**Alles außer Extrahieren von Seiten:** Ermöglicht Benutzern das Ändern des Dokuments über alle in der Liste „Zulässige Änderungen“ angegebenen Methoden, jedoch nicht das Entfernen von Seiten.

**Kopieren von Text, Bildern und anderem Inhalt aktivieren:** Ermöglicht es Benutzern, den Inhalt des PDF-Dokuments auszuwählen und zu kopieren. Außerdem können Dienstprogramme, die Zugriff auf den Inhalt einer PDF-Datei benötigen, wie z. B. Acrobat Catalog, auf diese Inhalte zugreifen. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad ausgewählt ist.

**Textzugriff für Sprachausgabeprogramme für 
Sehbehinderte aktivieren:** Benutzer mit Sehbehinderung können das Dokument mithilfe von Bildschirmlesehilfen lesen. Allerdings können die Benutzenden den Inhalt des Dokuments nicht kopieren oder extrahieren. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad ausgewählt ist.

## Löschen einer Sicherheitseinstellung {#delete-a-security-setting}

Sie können eine Sicherheitseinstellung löschen, wenn sie nicht mehr benötigt wird. Vorkonfigurierte Sicherheitseinstellungen können jedoch nicht gelöscht werden.

1. Klicken Sie in der Administration Console auf **[!UICONTROL Services > PDF-Generator > Sicherheitseinstellungen]**.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Einstellungen auswählen.
1. Klicken Sie auf **[!UICONTROL Löschen]** und auf der Seite **[!UICONTROL Löschbestätigung]** erneut auf **[!UICONTROL Löschen]**.
