---
title: Übersicht über AEM Document Services
seo-title: Overview of AEM Document Services
description: Bei AEM Document Services handelt es sich um einen Satz an OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten.
seo-description: AEM Document Services are a set of OSGi Services for creating, assembling, and securing PDF Documents.
uuid: 439144b7-f805-4819-9ed9-a6e9e374b5ed
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 10d406db-ac10-479b-b08b-d0735116a12b
docset: aem65
exl-id: 4c8a3877-1a3c-410d-ad1f-69c73ba4fcc1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1402'
ht-degree: 100%

---

# Übersicht über AEM Document Services{#overview-of-aem-document-services}

Bei AEM Document Services handelt es sich um einen Satz an OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. Document Services enthält die folgenden Dienste:

## Ausgabe-Service {#output-service}

Der Output-Dienst ermöglicht das Erstellen von Dokumenten in verschiedenen Formaten, einschließlich PDF, Laserdruckerformate und Beschriftungsdruckerformate. Laser-Druckerformate sind PostScript und Printer Control Language (PCL). In der nachfolgenden Liste sind die Beschriftungsdruckerformate aufgeführt:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Ein Dokument kann zu einem Netzwerkdrucker, einem lokalen Drucker oder in eine Datei im Dateisystem übertragen werden. Der Output-Dienst führt XML-Formulardaten mit einem Formularentwurf zusammen, um Dokumente zu erstellen. Der Output-Dienst kann Dokumente ohne das Zusammenführen von XML-Formulardaten im Dokument erstellen. Der primäre Workflow besteht jedoch darin, Daten in dem Dokument zusammenzuführen.

>[!NOTE]
>
>Ein Formularentwurf wird in der Regel mithilfe von Designer erstellt. Informationen zum Erstellen von Formularn für den Output-Dienst finden Sie in der Designer-Hilfe.

Wenn Sie den Output-Dienst zum Zusammenführen von XML-Daten mit einem Formularentwurf verwenden, ist das Ergebnis ein nicht interaktives PDF-Dokument. Bei einem nicht interaktiven PDF-Dokument können Benutzer keine Daten in die Felder eingeben. Dagegen können Sie den Forms-Dienst verwenden, um ein interaktives PDF-Formular zu erstellen, mit dem Benutzer Daten in die Felder eingeben können.

Die folgenden vier Output-Dienstvorgänge stehen zur Verwendung zur Verfügung:

* **generatePDFOuput**: Führt einen Formularentwurf mit Daten zusammen, um ein PDF-Dokument zu erstellen.
* **generatePrintedOutput**: Führt einen Formularentwurf mit Formulardaten zusammen, um ein Dokument zu erstellen, das entweder an einer Laserdrucker oder einen Beschriftungsnetzwerkdrucker gesendet werden soll.

* **generatePDFOutputBatch**: Führt mehrere Vorlagen mit mehreren Datensätzen in einem einzigen Aufruf zusammen, um einen Stapel von PDF-Dateien zu generieren. Es gibt auch eine Option zum Generieren einer einzigen PDF durch Kombinieren aller PDFs
* **generatePrintedOutputBatch**: Führt mehrere Vorlagen mit mehreren Dateneinträgen in einem einzigen Aufruf zusammen, um einen Stapel gedruckter Dokumente (PS, PCL, ZPL, DPL, IPL, TPCL) zu erzeugen. Es gibt auch eine Option zum Generieren eines einzigen Druckdokuments.

## Assembler-Service {#assembler-service}

Mit dem Assembler-Dienst können Sie PDF- und XDP-Dokumente kombinieren, neu anordnen und erweitern sowie Informationen zu PDF-Dokumenten erhalten. Jeder an den Assembler-Dienst übermittelte Auftrag umfasst ein DDX-Dokument (Document Description XML), Quelldokumente und externe Ressourcen (Zeichenfolgen und Grafiken). Das DDX-Dokument enthält Anweisungen dazu, wie die Quelldokumente zum Generieren eines Satzes von Zieldokumenten verwendet werden.

Neben den oben genannten stehen beim Assembler-Dienst die folgenden Funktionen zur Verfügung:

* Der Dienst wandelt PDF-Dokumente in den PDF/A-Standard um.
* Der Dienst wandelt PDF-Formulare, in Designer erstellte XML-Formulare und in Acrobat erstellte PDF-Formulare in PDF/A-1b, PDF/A-2b und PDFA/A-3b um.
* Der Dienst konvertiert signierte und nicht signierte PDF-Dokumente (Digital Signatures erforderlich).
* Der Dienst überprüft den Kompatibilitätsgrad von PDF/A-Dateien und wandelt diese bei Bedarf um.

### Informationen zu DDX {#about-ddx}

Bei Verwendung des Assembler-Dienstes verwenden Sie zum Beschreiben der gewünschten Ausgabe eine auf XML basierende Sprache namens DDX (Document Description XML). DDX ist eine deklarative Auszeichnungssprache, deren Elemente Dokumentbausteine darstellen. Diese Bausteine umfassen PDF-Seiten, XDP-Dokumente, XDP-Formularfragmente sowie andere Elemente wie Kommentare, Lesezeichen und formatierten Text.

DDX-Dokumente können Zieldokumente mit folgenden Eigenschaften angeben:

* Ein PDF-Dokument, das aus mehreren PDF-Dokumenten assembliert ist.
* Mehrere PDF-Dokumente, die von einem einzelnen PDF-Dokument aufgeteilt wurden.
* PDF-Portfolio, das eine in sich abgeschlossene Benutzeroberfläche sowie mehrere PDF- und Nicht-PDF-Dokumente enthält.
* Ein XDP-Dokument, das aus mehreren XDP-Dokumenten assembliert ist.
* Ein XDP-Dokument, das XML-Fragmente enthält, die dynamisch in ein XDP-Dokument eingefügt wurden.
* Ein PDF-Dokument, das ein XDP-Dokument packt.
* XML-Dateien, die über die Eigenschaften eines PDF-Dokuments berichten. Zu den gemeldeten Eigenschaften gehören Text, Kommentare, Formulardaten, Dateianlagen, in PDF-Portfolios verwendete Dateien, Lesezeichen und PDF-Eigenschaften. Zu den PDF-Eigenschaften gehören Formulareigenschaften, Seitendrehung und Dokumentautor.

Mithilfe von DDX können zusammen mit der Dokumentzusammenführung und -aufteilung PDF-Dokumente erweitert werden. Sie können eine beliebige Kombination der folgenden Effekte angeben:

* Hinzufügen von Wasserzeichen oder Hintergründen zu ausgewählten Seiten (oder deren Entfernung)
* Hinzufügen von Kopf- und Fußzeilen zu ausgewählten Seiten (oder deren Entfernung)
* Entfernen der Struktur und Navigationsfunktionen eines PDF-Pakets oder PDF-Portfolios. Das Ergebnis ist eine einzelne PDF-Datei.
* Neunummerieren von Seitenbeschriftungen – Seitenbeschriftungen dienen meist der Seitennummerierung
* Importieren von Metadaten aus einem anderen Quelldokument
* Hinzufügen oder Entfernen von Dateianlagen, Lesezeichen, Hyperlinks, Kommentaren und JavaScript.
* Festlegen der Ansicht beim Öffnen und Optimierung der Anzeige im Internet
* Festlegen von Berechtigungen für verschlüsselte PDF-Dokumente
* Drehen von Seiten bzw. Drehen und Verschieben von Seiteninhalten
* Ändern der Größe von ausgewählten Seiten.
* Zusammenführen von Daten mit einer XFA-basierten PDF-Datei.

Sie können eine einfache Eingabezuordnung zum Angeben der Speicherorte für Quell- und Zieldokumente verwenden. Sie können auch die folgenden URL-Typen für externe Daten verwenden:

* File
* FTP
* HTTP/HTTPS

## DocAssurance-Dienst {#doc-assurance-service}

Der DocAssurance-Dienst unterstützt Sie beim Verschlüsseln und Entschlüsseln von Dokumenten, beim Erweitern der Funktionen von Adobe Reader mit zusätzlichen Nutzungsrechten sowie beim Hinzufügen digitaler Signaturen zu Ihren Dokumenten. Ihre Benutzer können mit PDF-Formularen und -Dokumenten mühelos interagieren, während in Ihrer Organisation Sicherheit, Archivierung und Compliance verbessert werden.

Der DocAssurance-Dienst umfasst drei Dienste: Signature, Encryption und Reader Extension.

### Signature-Dienst {#signature-service}

Der Signature-Dienst ermöglicht das Arbeiten mit digitalen Signaturen und Dokumenten auf dem AEM-Server. Der Signature-Dienst wird beispielsweise häufig in folgenden Situationen genutzt:

* Der AEM-Server zertifiziert ein Formular, bevor es an einen Benutzer zum Öffnen in Acrobat oder Adobe Reader gesendet wird.
* Der AEM-Server prüft die Gültigkeit einer Signatur, die einem Formular in Acrobat oder Adobe Reader hinzugefügt wurde.
* Der AEM-Server signiert ein Formular im Auftrag eines Beglaubigers.

Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu, die im Trust Store gespeichert sind.

### Encryption-Service {#encryption-service}

Der Encryption-Dienst ermöglicht das Ver- und Entschlüsseln von Dokumenten. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Beim Verschlüsseln eines PDF-Dokuments können Sie das gesamte PDF-Dokument (einschließlich Inhalt, Metadaten und Anlagen), alle Daten außer den Metadaten oder nur die Anlagen verschlüsseln. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, muss der Benutzer das Kennwort zum Öffnen angeben, damit das Dokument in Adobe Reader oder Acrobat angezeigt werden kann. Wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, muss der Benutzer das PDF-Dokument mithilfe eines privaten Schlüssels (Zertifikat) entschlüsseln. Der private Schlüssel, der zum Entschlüsseln des PDF-Dokuments verwendet wird, muss dem öffentlichen Schlüssel entsprechen, der zum Verschlüsseln verwendet wurde.

### Reader Extension-Dienst {#reader-extension-service}

Der Reader Extensions-Dienst ermöglicht Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweitern der Funktionalität von Adobe Reader durch zusätzliche Verwendungsrechte. Der Reader Extensions-Dienst funktioniert mit Adobe Reader 7.0 und höher. Der Dienst fügt dem PDF-Dokument Verwendungsrechte hinzu. Diese Aktion aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Reader geöffnet wird, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. Externe Benutzer benötigen keine zusätzliche Software oder Plug-Ins für das Verwenden von Dokumenten mit aktivierten Benutzerrechten.

PDF-Dokumente, denen entsprechende Verwendungsrechte hinzugefügt wurden, ermöglichen Empfängern die folgenden Aktivitäten in Adobe Reader:

* Ausfüllen von PDF-Dokumenten und Formularen online oder offline, sodass Empfänger lokale Kopien speichern können, ohne hinzufügte Informationen zu verlieren
* Speichern von PDF-Dokumenten auf einer lokalen Festplatte, um das Originaldokument und etwaige zusätzliche Kommentare, Daten oder Anlagen aufzubewahren
* Anhängen von Dateien und Medienclips an PDF-Dokumente
* Signieren, Zertifizieren und Authentifizieren von PDF-Dokumenten durch die Anwendung digitaler Signaturen unter Verwendung branchenüblicher PKI-Technologien (PKI = Public Key Infrastructure)
* Elektronisches Senden ausgefüllter oder mit Anmerkungen versehener PDF-Dokumente
* Verwenden von PDF-Dokumenten und -Formularen als intuitives Entwicklungs-Frontend für interne Datenbanken und Webdienste
* Freigeben von PDF-Dokumenten für andere Benutzer, sodass Rezensenten mit intuitiven Markierungswerkzeugen Kommentare hinzufügen können. Zu diesen Werkzeugen gehören elektronische Haftnotizen, Stempel, Markierungen und Streichungen. Dieselben Funktionen sind in Acrobat verfügbar.
* Unterstützt die Dekodierung mit Strichcode versehener Formulare.

Diese speziellen Benutzerfunktionen werden automatisch aktiviert, wenn ein PDF-Dokument mit aktivierten Benutzerrechten in Adobe Reader geöffnet wird. Wenn der Benutzer die Arbeit mit einem Dokument mit aktivierten Benutzerrechten beendet hat, sind diese Funktionen in Adobe Reader wieder deaktiviert. Sie bleiben deaktiviert, bis der Benutzer ein weiteres PDF-Dokument mit aktivierten Benutzerrechten erhält.

Standardmäßig ist der DocAssurance-Dienst nicht verfügbar. Informationen zum Konfigurieren des DocAssurance-Services finden Sie unter [Installation und Konfiguration von Dokumenten-Services](../../forms/using/install-configure-document-services.md).

## An Drucker senden {#send-to-printer-service}

Der Service „An Drucker senden“ stellt eine API zum Senden von Dokumenten zum Drucken an den angegebenen Drucker zur Verfügung.
