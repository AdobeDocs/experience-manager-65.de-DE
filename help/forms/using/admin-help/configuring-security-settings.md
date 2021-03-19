---
title: Sicherheitseinstellungen konfigurieren
seo-title: Sicherheitseinstellungen konfigurieren
description: Erfahren Sie, wie Sie Sicherheitseinstellungen konfigurieren.
seo-description: Erfahren Sie, wie Sie Sicherheitseinstellungen konfigurieren.
uuid: 9747f268-3551-4064-8dba-e1de4a577843
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a89ab508-173f-4b1c-88d9-ef944af4d9ae
feature: PDF Generator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1378'
ht-degree: 63%

---


# Konfigurieren von Sicherheitseinstellungen{#configuring-security-settings}

Sie können den Zugriff auf PDF-Dokumente einschränken, indem Sie Kennwörter festlegen oder bestimmte Funktionen wie Drucken und Bearbeiten sperren. Wenn ein PDF-Dokument eingeschränkte Funktionen hat, werden Werkzeuge und Menüpunkte in Zusammenhang mit diesen Funktionen abgeblendet angezeigt. Es gibt noch weitere Methoden zum Erstellen sicherer Dokumente, z. B. die Verschlüsselung oder Zertifizierung eines Dokuments. Eine Sicherheitseinstellung enthält das Kennwort und für bestimmte PDF-Konvertierungen zu verwendende Optionen.

Auf der Seite „Sicherheitseinstellungen“ können Sie die folgenden Aufgaben durchführen:

## Eine Sicherheitseinstellung erstellen oder bearbeiten {#create-or-edit-a-security-setting}

Eine *Sicherheitseinstellung* steuert die Sicherheit und Berechtigungen für Dateien, die mit dieser Sicherheitseinstellung konvertiert werden.

1. Klicken Sie in Administration Console auf „Dienste“ > „PDF Generator“ > „Sicherheitseinstellungen“.
1. Klicken Sie auf „Neu“ oder auf den Namen einer Sicherheitseinstellung.
1. Geben Sie auf der Seite „Sicherheitseinstellung“ im Bereich „Neu/Bearbeiten“ die erforderlichen Informationen für die Sicherheitseinstellung ein. (Siehe [Sicherheitseinstellungen](/help/forms/using/admin-help/configuring-file-type-settings.md#configuring-file-type-settings).)
1. Klicken Sie auf „Speichern“, geben Sie in dem eingeblendeten Dialogfeld einen Namen für die Einstellung ein und klicken Sie auf „OK“.

### Sicherheitseinstellungen {#security-settings}

Mit diesen Einstellungen werden die Kompatibilität und Verschlüsselung konfiguriert. Weitere Informationen zum Zugriff auf die Schrifteinstellungen finden Sie unter [Sicherheitseinstellung erstellen oder bearbeiten](configuring-security-settings.md#create-or-edit-a-security-setting).

**Kompatibilität:** Legt den Verschlüsselungstyp zum Öffnen eines kennwortgeschützten Dokuments fest. Die Option „Acrobat 3.0 und höher“ verwendet einen niedrigen Verschlüsselungsgrad. Die anderen Optionen verwenden einen hohen Verschlüsselungsgrad.

**Acrobat 3.0 und höher:** Verwendet niedrige Verschlüsselung (40-Bit RC4).

**Acrobat 5.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit RC4).

**Acrobat 6.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit RC4). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen.

**Acrobat 7.0 und höher:** Verwendet hohe Verschlüsselung (128-Bit AES). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen und die ausschließliche Verschlüsselung von Dateianlagen.

**Acrobat 9.0 und höher:** Verwendet hohe Verschlüsselung (256-Bit AES). Diese Option ermöglicht die Aktivierung von Metadaten für Suchfunktionen und die ausschließliche Verschlüsselung von Dateianlagen. 

Mit einer früheren Version von Acrobat können keine PDF-Dokumente mit einer höheren Kompatibilitätseinstellung geöffnet werden. Wenn Sie beispielsweise die Option „Acrobat 7.0 und höher“ auswählen, kann das Dokument nicht in Acrobat 6.0 oder niedriger geöffnet werden. 

Stellen Sie sicher, dass die Kompatibilitätsstufe der PDF-Kompatibilitätsstufe für dieselbe Quelle entspricht. Wenn Sie beispielsweise einen überwachten Ordner für die PDF-Einstellung „Standard“ konfiguriert haben (die mit Acrobat 5.0 und höher kompatibel ist), darf die Kompatibilitätsstufe für die Sicherheit nicht höher sein als Acrobat 5.0.

**Einschränkungen beim Dokument:** Die verfügbaren Dokument-Einschränkungen hängen von der ausgewählten Kompatibilitätsoption ab.

**Keine Verschlüsselung:** Verschlüsselt keine Teile des Dokuments.

**Gesamten Dokument verschlüsseln:** Verschlüsselt das Dokument und die Metadaten des Dokuments. Bei Aktivierung dieser Option können Suchmaschinen nicht auf die Dokumentmetadaten zugreifen.

**Alle Dokument-Inhalte außer Metadaten verschlüsseln (mit Acrobat 6 und höher kompatibel):** Verschlüsselt den Inhalt eines Dokuments, erlaubt Suchmaschinen jedoch weiterhin den Zugriff auf die Metadaten des Dokuments. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 6.0 und höher“, „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ festgelegt ist.

**Nur Dateianlagen verschlüsseln (kompatibel mit Acrobat 7 und höher):** Benutzer können das Dokument ohne Kennwort öffnen, müssen jedoch ein Kennwort eingeben, um Dateianlagen zu öffnen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ festgelegt ist. 

Mit diesen Einstellungen wird der Kennwortschutz konfiguriert:

>[!NOTE]
>
>Ein vergessenes Kennwort kann nicht aus den Dokumentdaten wiederhergestellt werden. Deshalb wird empfohlen, Kennwörter an einem sicheren Ort aufzubewahren. Außerdem sollten Sie eine Sicherungskopie von Dokumenten aufbewahren, die nicht kennwortgeschützt sind.

**Kennwort zum Öffnen des Dokuments erforderlich:** Aktiviert die Kennwortoptionen.

**Kennwort zum Öffnen des Dokuments:** Verhindert, dass Benutzer das Dokument öffnen, es sei denn, sie geben das von Ihnen angegebene Kennwort ein. Bei Kennwörtern muss die Groß- und Kleinschreibung beachtet werden. Acrobat verwendet die RC4-Sicherheitsmethode von RSA Security, Inc., um PDF-Dokumente mit Kennwörtern zu schützen. Wenn Sie Druck- und Bearbeitungsvorgänge einschränken, sollten Sie ein Kennwort zum Öffnen des Dokuments zum Verstärken des Dokumentschutzes anfordern.

**Kennwort zum Öffnen des Dokuments erneut eingeben:** Stellt sicher, dass das Kennwort zum Öffnen des Dokuments korrekt ist.

**Kennwort zum Öffnen der Dateianlagen erforderlich:** Aktiviert die Kennwortoptionen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

**Kennwort zum Öffnen der Dateianlage:** Stellt sicher, dass zum Öffnen einer Dateianlage ein Kennwort erforderlich ist. Benutzer können das Dokument nicht ohne Kennwortangabe öffnen. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist.

**Dateianlage erneut eingeben:** Stellt sicher, dass das Kennwort korrekt ist. Diese Option ist nur verfügbar, wenn die Option „Kompatibilität“ auf „Acrobat 7.0 und höher“ oder „Acrobat 9.0 und höher“ und die Option „Dokumenteinschränkung“ auf „Nur Dateianlagen verschlüsseln“ festgelegt ist. 

Mit diesen Optionen werden Berechtigungen konfiguriert:

**Verwenden Sie ein Kennwort, um das Drucken und Bearbeiten des Dokuments und seiner Sicherheitseinstellungen zu beschränken:** Aktiviert Zugriffsbeschränkungen.

**Berechtigungskennwort:** Verhindert, dass Benutzer drucken und bearbeiten. Benutzer können diese Sicherheitseinstellungen nur ändern, wenn sie das von Ihnen festgelegte Kennwort eingeben. Es ist nicht möglich, das für „Kennwort zum Öffnen des Dokuments“ verwendete Kennwort anzugeben. Wenn Sie ein Berechtigungskennwort festlegen, können nur Benutzer, die das entsprechende Kennwort eingeben, die Sicherheitseinstellungen ändern. Wenn für ein PDF-Dokument beide Kennworttypen festgelegt wurden, kann es durch Eingabe eines der Kennwörter geöffnet werden. Ein Benutzer kann jedoch die eingeschränkten Funktionen nur durch Angabe des Berechtigungskennworts festlegen oder ändern. Wenn für das PDF-Dokument nur das Berechtigungskennwort festgelegt wurde oder ein Benutzer das Dokument über das Kennwort zum Öffnen des Dokuments öffnet, wird die Aufforderung zur Kennworteingabe eingeblendet, wenn der Benutzer versucht, die Sicherheitseinstellungen zu ändern.

**Berechtigungskennwort erneut eingeben:** Stellt sicher, dass das Berechtigungskennwort korrekt ist.

**Zulässiges Drucken:** Gibt die Druckqualität für das PDF-Dokument an:

**Keine:** Verhindert, dass Benutzer das Dokument drucken.

**Niedrige Auflösung (150 dpi):** Ermöglicht Benutzern das Drucken des Dokuments mit einer Auflösung von maximal 150 dpi. Der Druckvorgang ist ggf. langsam, da jede Seite als Bitmap-Bild gedruckt wird. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Hohe Auflösung:** Ermöglicht Benutzern das Drucken mit beliebiger Auflösung und leitet eine Vektorausgabe hoher Qualität an PostScript- und andere Drucker weiter, die erweiterte Druckfunktionen hoher Qualität unterstützen.

**Zulässige Änderungen:** Definiert, welche Bearbeitungsaktionen im PDF-Dokument zulässig sind:

**Keine:** Verhindert, dass Benutzer das Dokument ändern, einschließlich des Ausfüllens von Unterschriften und Formularfeldern.

**Einfügen, Löschen und Drehen von Seiten:** Ermöglicht Benutzern das Einfügen, Löschen und Drehen von Seiten sowie das Erstellen von Lesezeichen und Miniaturbildern. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Ausfüllen von Formularfeldern und Unterschreiben vorhandener Unterschriftsfelder:** Ermöglicht Benutzern das Ausfüllen von Formularen und das Hinzufügen digitaler Unterschriften. Benutzer können jedoch keine Kommentare hinzufügen oder Formularfelder erstellen. Diese Option ist nur verfügbar, wenn ein hoher Verschlüsselungsgrad (Acrobat 5.0, 6.0, 7.0 oder 9.0) aktiviert ist.

**Kommentieren, Ausfüllen von Formularfeldern und Unterschreiben vorhandener Unterschriftsfelder:** Ermöglicht Benutzern das Ausfüllen von Formularen und das Hinzufügen digitaler Unterschriften und Kommentare.

**Seitenlayout, Touch-up, Ausfüllen von Formularfeldern und Unterschreiben vorhandener Unterschriftsfelder:** Ermöglicht Benutzern das Einfügen, Drehen oder Löschen von Seiten sowie das Erstellen von Lesezeichen oder Miniaturbildern, das Ausfüllen von Formularen und das Hinzufügen digitaler Unterschriften. Diese Option ermöglicht Benutzern nicht das Erstellen von Formularfeldern. Sie ist nur verfügbar, wenn ein niedriger Verschlüsselungsgrad (Acrobat 3.0) aktiviert ist.

**Beliebige Ausnahme:** Ermöglicht Benutzern das Ändern des Dokuments mithilfe einer beliebigen Methode in der Zulassungsliste &quot;Änderungen&quot;, mit Ausnahme des Entfernens von Seiten.

**Kopieren von Text, Bildern und anderen Inhalten aktivieren:** Hiermit können Benutzer den Inhalt des PDF-Dokuments auswählen und kopieren. Erlaubt ferner, dass Dienstprogramme, die Zugriff auf den Inhalt einer PDF-Datei benötigen (z. B. Acrobat Catalog), auf diesen Inhalt zugreifen können. Diese Option ist verfügbar, wenn ein hoher Verschlüsselungsgrad aktiviert ist.

**Textzugriff auf Bildschirmlesehilfen für Sehbehinderte aktivieren:** Ermöglicht Sehbehinderten das Lesen des Dokuments mithilfe von Bildschirmlesehilfen. Benutzer dürfen jedoch den Dokumentinhalt weder kopieren noch entnehmen. Diese Option ist verfügbar, wenn ein hoher Verschlüsselungsgrad aktiviert ist.

## Eine Sicherheitseinstellung löschen  {#delete-a-security-setting}

Eine nicht mehr benötigte Sicherheitseinstellung kann gelöscht werden. Vorkonfigurierte Sicherheitseinstellungen können hingegen nicht gelöscht werden.

1. Klicken Sie in Administration Console auf **[!UICONTROL Dienste > PDF Generator > Sicherheitseinstellungen]**.
1. Aktivieren Sie das Kontrollkästchen neben der zu löschenden Einstellung. Sie können mehrere Einstellungen auswählen.
1. Klicken Sie auf **[!UICONTROL Löschen]** und auf der Seite **[!UICONTROL Bestätigung löschen]** erneut auf **[!UICONTROL Löschen]**.

