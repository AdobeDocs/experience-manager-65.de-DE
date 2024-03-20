---
title: Konfigurieren von Sicherheitseinstellungen
description: Erfahren Sie, wie Sie Sicherheitseinstellungen konfigurieren. Sie können PDF-Dokumente schützen, indem Sie den Zugriff einschränken. Sie können das Dokument verschlüsseln, zertifizieren oder kennwortschützen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: be076477-2681-4570-953d-6c44d3c30843
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 53%

---

# Konfigurieren von Sicherheitseinstellungen{#configuring-security-settings}

Sie können den Zugriff auf PDF-Dokumente einschränken, indem Sie Kennwörter festlegen und bestimmte Funktionen wie Drucken und Bearbeiten einschränken. Wenn ein PDF-Dokument eingeschränkte Funktionen aufweist, sind die damit verbundenen Tools und Menüelemente abgeblendet. Sie können auch andere Methoden verwenden, um sichere Dokumente zu erstellen, z. B. das Verschlüsseln oder Zertifizieren eines Dokuments. Eine Sicherheitseinstellung enthält das Kennwort und bestimmte Optionen, die für bestimmte PDF-Konvertierungen verwendet werden sollen.

Auf der Seite &quot;Sicherheitseinstellungen&quot;können Sie die folgenden Aufgaben ausführen:

## Sicherheitseinstellung erstellen oder bearbeiten {#create-or-edit-a-security-setting}

A *Sicherheitseinstellung* steuert die Sicherheit und Berechtigungen für Dateien, die mit dieser Sicherheitseinstellung konvertiert werden.

1. Klicken Sie in der Administration-Console auf „Dienste“ > „PDF Generator“ > „Sicherheitseinstellungen“.
1. Klicken Sie auf Neu oder auf den Namen einer Sicherheitseinstellung.
1. Füllen Sie auf der Seite &quot;Sicherheitseinstellung&quot;Neu/Bearbeiten&quot;die erforderlichen Informationen für die Sicherheitseinstellung aus. (Siehe [Dateitypeinstellungen konfigurieren](/help/forms/using/admin-help/configuring-file-type-settings.md#configuring-file-type-settings).
1. Klicken Sie auf Speichern , geben Sie im angezeigten Dialogfeld einen Namen für die Einstellung ein und klicken Sie auf OK.

### Sicherheitseinstellungen {#security-settings}

Diese Einstellungen konfigurieren die Kompatibilität und Verschlüsselung. Anweisungen zum Zugriff auf die Schrifteinstellungen finden Sie unter [Sicherheitseinstellung erstellen oder bearbeiten](configuring-security-settings.md#create-or-edit-a-security-setting).

**Kompatibilität:** Legt den Verschlüsselungstyp zum Öffnen eines kennwortgeschützten Dokuments fest. Die Option „Acrobat 3.0 und höher“ verwendet einen niedrigen Verschlüsselungsgrad. Die anderen Optionen verwenden einen hohen Verschlüsselungsgrad.

**Acrobat 3.0 und höher:** Verwendet niedrige Verschlüsselung (40-Bit RC4).

**Acrobat 5.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit RC4).

**Acrobat 6.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit RC4). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen.

**Acrobat 7.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit AES). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen und die ausschließliche Verschlüsselung von Dateianlagen.

**Acrobat 9.0 und höher:** Verwendet hohe Verschlüsselung (256-Bit AES). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen und die ausschließliche Verschlüsselung von Dateianlagen.

Eine frühere Version von Acrobat kann kein PDF-Dokument öffnen, das über eine höhere Kompatibilitätseinstellung verfügt. Wenn Sie beispielsweise die Option Acrobat 7.0 And Later auswählen, können Sie das Dokument nicht in Acrobat 6.0 oder früher öffnen.

Stellen Sie sicher, dass die Kompatibilitätsstufe mit der PDF-Kompatibilitätsstufe für dieselbe Quelle übereinstimmt. Wenn Sie beispielsweise einen überwachten Ordner für die Verwendung der PDF-Standardeinstellung konfiguriert haben, die mit Acrobat 5.0 oder höher kompatibel ist, darf die Sicherheitskompatibilitätsstufe nicht höher als Acrobat 5.0 sein.

**Dokumenteinschränkung:** Die verfügbaren Dokumenteinschränkungen sind von der ausgewählten Kompatibilitätsoption abhängig.

**Keine Verschlüsselung:** Kein Teil des Dokuments wird verschlüsselt.

**Gesamten Dokumentinhalt verschlüsseln:** Verschlüsselt das Dokument und die Dokumentmetadaten. Bei Aktivierung dieser Option können Suchmaschinen nicht auf die Dokumentmetadaten zugreifen.

**Gesamten Dokumentinhalt mit Ausnahme von Metadaten verschlüsseln (Acrobat
6 und höher kompatibel):** Verschlüsselt den Inhalt eines Dokuments, ermöglicht jedoch Suchmaschinen den Zugriff auf die Dokumentmetadaten. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 6.0 und höher“, „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ festgelegt ist.

**Nur Dateianlagen verschlüsseln (Acrobat 7 und höher
kompatibel):** Benutzer können das Dokument ohne Kennwort öffnen, müssen jedoch ein Kennwort eingeben, um Dateianlagen zu öffnen. Diese Option ist nur verfügbar, wenn die Kompatibilitätsoption auf Acrobat 7.0 oder höher oder Acrobat 9.0 oder höher festgelegt ist.

Mit diesen Einstellungen wird die Kennwortsicherheit konfiguriert:

>[!NOTE]
>
>Wenn Sie ein Kennwort vergessen haben, kann es nicht aus dem Dokument abgerufen werden. Es wird empfohlen, Kennwörter an einem anderen sicheren Ort zu speichern, falls Sie sie vergessen. Behalten Sie außerdem eine Sicherungskopie des Dokuments bei, das nicht kennwortgeschützt ist.

**Kennwort zum Öffnen des Dokuments erforderlich:** Aktiviert die Kennwortoptionen.

**Kennwort zum Öffnen des Dokuments:** Ermöglicht Benutzern das Öffnen des Dokuments nur, wenn sie das von Ihnen festgelegte Kennwort eingeben. Bei Passwörtern wird zwischen Groß- und Kleinschreibung unterschieden. Acrobat verwendet die RC4-Sicherheitsmethode von RSA Security Inc., um PDF-Dokumente mit Passwort zu schützen. Wenn Sie Druck- und Bearbeitungsvorgänge einschränken, wird empfohlen, zur Erhöhung der Sicherheit ein Kennwort zum Öffnen des Dokuments hinzuzufügen.

**Kennwort zum Öffnen des Dokuments erneut eingeben:** Stellt sicher, dass das Kennwort zum Öffnen des Dokuments korrekt ist.

**Kennwort zum Öffnen von Dateianlagen erforderlich:** Aktiviert die Kennwortoptionen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

**Kennwort zum Öffnen der Dateianlage:** Stellt sicher, dass zum Öffnen eines Dateianhangs ein Kennwort erforderlich ist. Benutzer können das Dokument ohne Kennwort öffnen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

**Kennwort zum Öffnen der Dataianlage erneut eingeben:** Stellt sicher, dass das Kennwort korrekt ist. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

Diese Optionen konfigurieren die Berechtigungen:

**Kennwort verwenden, um das Drucken und Bearbeiten des 
Dokuments bzw. seiner Sicherheitseinstellungen einzuschränken:** Ermöglicht die Einschränkung von Berechtigungen.

**Berechtigungskennwort:** Schränkt das Drucken und Bearbeiten für Benutzer ein. Benutzer können diese Sicherheitseinstellungen nur ändern, wenn sie das von Ihnen festgelegte Kennwort eingeben. Sie können nicht dasselbe Kennwort wie für &quot;Kennwort zum Öffnen des Dokuments&quot;verwenden. Wenn Sie ein Berechtigungskennwort festlegen, können nur die Personen, die dieses Kennwort eingeben, die Sicherheitseinstellungen ändern. Wenn das PDF-Dokument beide Kennworttypen aufweist, wird es durch eines der beiden Kennwörter geöffnet. Ein Benutzer kann jedoch nur die eingeschränkten Funktionen mit dem Berechtigungskennwort festlegen oder ändern. Wenn das PDF-Dokument nur über das Berechtigungskennwort verfügt oder wenn ein Benutzer das Dokument mit dem Kennwort zum Öffnen des Dokuments öffnet, wird die Kennwortaufforderung angezeigt, wenn der Benutzer versucht, die Sicherheitseinstellungen zu ändern.

**Berechtigungskennwort erneut eingeben:** Stellt sicher, dass das Berechtigungskennwort korrekt ist.

**Drucken erlaubt:** Legt die Druckqualität für das PDF-Dokument fest:

**Keine:** Hindert Benutzer am Drucken des Dokuments.

**Geringe Auflösung (150 dpi):** Ermöglicht Benutzern das Drucken des Dokuments mit einer Maximalauflösung von 150 dpi. Der Druck kann langsamer sein, da jede Seite als Bitmap-Bild gedruckt wird. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Hohe Auflösung** Ermöglicht Benutzern das Drucken mit beliebiger Auflösung, wobei eine Vektorausgabe hoher Qualität auf PostScript- und anderen Druckern erfolgen kann, die erweiterte Funktionen für hohe Druckqualität unterstützen.

**Zulässige Änderungen:** Legt fest, welche Bearbeitungsvorgänge für das PDF-Dokument zulässig sind:

**Keine:** Hindert Benutzer am Ändern des Dokuments, einschließlich des Ausfüllens von Signatur- und Formularfeldern.

**Einfügen, Löschen und Drehen von Seiten:** Ermöglicht Benutzern das Einfügen, Löschen und Drehen von Seiten sowie das Erstellen von Lesezeichen und Miniaturansichten. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Ausfüllen von Formularfeldern und Unterschreiben vorhandener 
Unterschriftsfelder:** Ermöglicht Benutzern das Ausfüllen von Formularen und das Hinzufügen digitaler Signaturen. Benutzer können jedoch keine Kommentare hinzufügen oder Formularfelder erstellen. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Kommentieren, Ausfüllen von Formularfeldern und Unterschreiben vorhandener 
Unterschriftsfelder:** Ermöglicht Benutzern das Ausfüllen von Formularen und das Hinzufügen digitaler Signaturen und Kommentare.

**Seitenlayout, TouchUp-Funktion, Ausfüllen von Formularfeldern und Unterschreiben 
vorhandener Unterschriftsfelder:** Ermöglicht Benutzern das Einfügen, Drehen oder Löschen von Seiten sowie das Erstellen von Lesezeichen oder Miniaturbildern, das Ausfüllen von Formularen und das Hinzufügen digitaler Signaturen. Mit dieser Option können Benutzer keine Formularfelder erstellen. Diese Option ist nur verfügbar, wenn ein niedriger Verschlüsselungsgrad (Acrobat 3.0) ausgewählt ist.

**Alles außer Extrahieren von Seiten:** Ermöglicht Benutzern das Ändern des Dokuments über alle in der Liste „Zulässige Änderungen“ angegebenen Methoden, jedoch nicht das Entfernen von Seiten.

**Kopieren von Text, Bildern und anderem Inhalt aktivieren:** Ermöglicht es Benutzern, den Inhalt des PDF-Dokuments auszuwählen und zu kopieren. Außerdem können Dienstprogramme, die Zugriff auf den Inhalt einer PDF-Datei benötigen, wie Acrobat Catalog, auf diese Inhalte zugreifen. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad ausgewählt ist.

**Textzugriff für Sprachausgabeprogramme für 
Sehbehinderte aktivieren:** Benutzer mit Sehbehinderung können das Dokument mithilfe von Bildschirmlesehilfen lesen. Benutzer können jedoch den Dokumentinhalt nicht kopieren oder extrahieren. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad ausgewählt ist.

## Eine Sicherheitseinstellung löschen {#delete-a-security-setting}

Sie können eine Sicherheitseinstellung löschen, wenn sie nicht mehr benötigt wird. Vorkonfigurierte Sicherheitseinstellungen können jedoch nicht gelöscht werden.

1. Klicken Sie in der Administration Console auf **[!UICONTROL Services > PDF-Generator > Sicherheitseinstellungen]**.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Einstellungen auswählen.
1. Klicken Sie auf **[!UICONTROL Löschen]** und auf der Seite **[!UICONTROL Löschbestätigung]** erneut auf **[!UICONTROL Löschen]**.
