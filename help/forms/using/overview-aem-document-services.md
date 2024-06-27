---
title: Übersicht über AEM-Dokumentendienste
description: Bei den AEM-Dokumentendiensten handelt es sich um eine Reihe von OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services,Reader Extensions, Forms Service,PDF Generator
exl-id: 4c8a3877-1a3c-410d-ad1f-69c73ba4fcc1
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '1413'
ht-degree: 100%

---

# Übersicht über AEM-Dokumentendienste{#overview-of-aem-document-services}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


Bei den AEM-Dokumentendiensten handelt es sich um eine Reihe von OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. Document Services enthält die folgenden Dienste:

## Ausgabe-Service {#output-service}

Der Output-Dienst ermöglicht das Erstellen von Dokumenten in verschiedenen Formaten, einschließlich PDF, Laser-Druckerformaten und Etikettendruckerformaten. Laser-Druckerformate sind PostScript und Printer Control Language (PCL). In der nachfolgenden Liste sind Etikettendruckerformate aufgeführt:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Ein Dokument kann auf einen Netzwerkdrucker, einen lokalen Drucker oder in eine Datei im Dateisystem übertragen werden. Der Output-Dienst führt XML-Formulardaten mit einem Formularentwurf zusammen, um ein Dokument zu erstellen. Der Output-Dienst kann Dokumente generieren, ohne XML-Formulardaten im Dokument zusammenzuführen. Der primäre Workflow besteht jedoch darin, Daten in dem Dokument zusammenzuführen.

>[!NOTE]
>
>Ein Formularentwurf wird in der Regel mithilfe von Designer erstellt. Informationen zum Erstellen von Formularentwürfen für den Output-Dienst finden Sie in der Designer-Hilfe.

Wenn Sie den Output-Dienst zum Zusammenführen von XML-Daten mit einem Formularentwurf verwenden, ist das Ergebnis ein nicht interaktives PDF-Dokument. Bei einem nicht interaktiven PDF-Dokument können Benutzer keine Daten in die Felder eingeben. Dagegen können Sie den Forms-Dienst verwenden, um ein interaktives PDF-Formular zu erstellen, mit dem Benutzende Daten in die Felder eingeben können.

Die folgenden vier Output-Dienstvorgänge stehen zur Verfügung:

* **generatePDFOuput**: Führt einen Formularentwurf mit Daten zusammen, um ein PDF-Dokument zu erstellen.
* **generatePrintedOutput**: Führt einen Formularentwurf mit Formulardaten zusammen, um ein Dokument zu erstellen, das entweder an einer Laserdrucker oder einen Beschriftungsnetzwerkdrucker gesendet werden soll.

* **generatePDFOutputBatch**: Führt mehrere Vorlagen mit mehreren Datensätzen in einem einzigen Aufruf zusammen, um einen Batch PDF-Dateien zu generieren. Es gibt auch eine Option zum Generieren einer einzigen PDF durch Kombinieren aller PDFs.
* **generatePrintedOutputBatch**: Führt mehrere Vorlagen mit mehreren Dateneinträgen in einem einzigen Aufruf zusammen, um einen Stapel gedruckter Dokumente (PS, PCL, ZPL, DPL, IPL, TPCL) zu erzeugen. Es gibt auch eine Option zum Generieren eines einzigen Druckdokuments.

## Assembler-Service {#assembler-service}

Mit dem Assembler-Dienst können Sie PDF- und XDP-Dokumente kombinieren, neu anordnen und erweitern sowie Informationen zu PDF-Dokumenten erhalten. Jeder an den Assembler-Dienst übermittelte Auftrag umfasst ein DDX-Dokument (Document Description XML), Quelldokumente und externe Ressourcen (Zeichenfolgen und Grafiken). Das DDX-Dokument enthält Anweisungen dazu, wie die Quelldokumente zum Erstellen eines Satzes von Zieldokumenten verwendet werden.

Neben den oben genannten stehen beim Assembler-Dienst die folgenden Funktionen zur Verfügung:

* Der Dienst wandelt PDF-Dokumente in den PDF/A-Standard um.
* Der Dienst wandelt PDF-Formulare, in Designer erstellte XML-Formulare und in Acrobat erstellte PDF-Formulare in PDF/A-1b, PDF/A-2b und PDFA/A-3b um.
* Der Dienst konvertiert signierte und nicht signierte PDF-Dokumente (Digital Signatures erforderlich).
* Der Dienst überprüft die Kompatibilität von PDF/A-Dateien und wandelt diese bei Bedarf um.

### Informationen zu DDX {#about-ddx}

Verwenden Sie bei Nutzung des Assembler-Dienstes eine XML-basierte Sprache namens „Document Description XML“ (DDX), um die gewünschte Ausgabe zu definieren. DDX ist eine deklarative Markup-Sprache, deren Elemente Dokumentbausteine darstellen. Diese Bausteine umfassen PDF-Dokumente, XDP-Dokumente, XDP-Formularfragmente sowie andere Elemente wie Kommentare, Lesezeichen und formatierten Text.

DDX-Dokumente können Zieldokumente mit folgenden Eigenschaften angeben:

* Ein PDF-Dokument, das aus mehreren PDF-Dokumenten assembliert ist.
* Mehrere PDF-Dokumente, die von einem einzelnen PDF-Dokument aufgeteilt wurden.
* PDF-Portfolio, das eine in sich abgeschlossene Benutzeroberfläche sowie mehrere PDF- und Nicht-PDF-Dokumente enthält.
* Ein XDP-Dokument, das aus mehreren XDP-Dokumenten assembliert ist.
* Ein XDP-Dokument, das XML-Fragmente enthält, die dynamisch in ein XDP-Dokument eingefügt wurden.
* Ein PDF-Dokument, das ein XDP-Dokument packt.
* XML-Dateien, die die die Eigenschaften eines PDF-Dokuments melden. Zu den gemeldeten Eigenschaften gehören Text, Kommentare, Formulardaten, Dateianlagen, in PDF-Portfolios verwendete Dateien, Lesezeichen und PDF-Eigenschaften. Zu den PDF-Eigenschaften gehören Formulareigenschaften, Seitendrehung und Dokumentautorin bzw. Dokumentautor.

Mithilfe von DDX können zusammen mit der Dokumentzusammenführung und -aufteilung PDF-Dokumente erweitert werden. Sie können eine beliebige Kombination der folgenden Effekte angeben:

* Hinzufügen von Wasserzeichen oder Hintergründen zu ausgewählten Seiten (oder deren Entfernung)
* Hinzufügen von Kopf- und Fußzeilen zu ausgewählten Seiten (oder deren Entfernung)
* Entfernen der Struktur und Navigationsfunktionen eines PDF-Pakets oder PDF-Portfolios Das Ergebnis ist eine einzelne PDF-Datei.
* Neunummerieren von Seitenbeschriftungen. Seitenbeschriftungen dienen meist der Seitennummerierung.
* Importieren von Metadaten aus einem anderen Quelldokument
* Hinzufügen oder Entfernen von Dateianlagen, Lesezeichen, Hyperlinks, Kommentaren und JavaScript.
* Festlegen der Ansicht beim Öffnen und Optimierung der Anzeige im Internet
* Festlegen von Berechtigungen für verschlüsselte PDF-Dokumente
* Drehen von Seiten bzw. Drehen und Verschieben von Seiteninhalten
* Ändern der Größe von ausgewählten Seiten.
* Zusammenführen von Daten mit einer XFA-basierten PDF-Datei.

Sie können eine einfache Eingabe-Map zum Angeben der Speicherorte für Quell- und Zieldokumente verwenden. Sie können auch die folgenden URL-Typen für externe Daten verwenden:

* File
* FTP
* HTTP/HTTPS

## DocAssurance-Dienst {#doc-assurance-service}

Der DocAssurance-Dienst unterstützt Sie beim Verschlüsseln und Entschlüsseln von Dokumenten, beim Erweitern der Funktionen von Adobe Reader mit zusätzlichen Nutzungsrechten sowie beim Hinzufügen digitaler Signaturen zu Ihren Dokumenten. Ihre Benutzenden können mühelos mit PDF-Formularen und -Dokumenten interagieren. Ihr Unternehmen profitiert dabei von mehr Sicherheit sowie besserer Archivierung und Compliance.

Der DocAssurance-Dienst umfasst drei Dienste: Signature, Encryption und Reader Extension.

### Signaturdienst {#signature-service}

Der Signature-Dienst ermöglicht das Arbeiten mit digitalen Signaturen und Dokumenten auf dem AEM-Server. Der Signatur-Dienst wird beispielsweise in der Regel in folgenden Situationen verwendet:

* Der AEM-Server zertifiziert ein Formular, bevor es an eine Person zum Öffnen mithilfe von Acrobat oder Adobe Reader gesendet wird.
* Der AEM-Server überprüft eine Signatur, die einem Formular mithilfe von Acrobat oder Adobe Reader hinzugefügt wurde.
* Der AEM-Server signiert ein Formular im Namen einer öffentlichen beglaubigenden Person.

Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu, die im Trust Store gespeichert sind.

### Encryption-Service {#encryption-service}

Der Encryption-Dienst ermöglicht das Ver- und Entschlüsseln von Dokumenten. Wenn ein Dokument verschlüsselt wird, ist sein Inhalt unlesbar. Beim Verschlüsseln eines PDF-Dokuments können Sie das gesamte PDF-Dokument (einschließlich Inhalt, Metadaten und Anlagen), alles außer den Metadaten oder nur die Anlagen verschlüsseln. Eine autorisierte Person kann das Dokument entschlüsseln, um Zugriff auf seinen Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, müssen die Benutzenden das Kennwort zum Öffnen angeben, damit das Dokument in Reader oder Adobe Acrobat angezeigt werden kann. Wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, müssen Benutzende das PDF-Dokument mithilfe eines privaten Schlüssels (Zertifikats) entschlüsseln. Der private Schlüssel zum Entschlüsseln des PDF-Dokuments muss dem öffentlichen Schlüssel entsprechen, der zum Verschlüsseln verwendet wurde.

### Dienst „Reader-Erweiterung“ {#reader-extension-service}

Der Reader Extensions-Dienst ermöglicht Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweitern der Funktionalität von Adobe Reader durch zusätzliche Verwendungsrechte. Der Reader Extensions-Dienst funktioniert mit Adobe Reader 7.0 oder höher. Der Dienst fügt einem PDF-Dokument Verwendungsrechte hinzu. Diese Aktion aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Reader geöffnet wird, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. Externe Benutzende benötigen keine zusätzliche Software oder Plug-ins für das Verwenden von Dokumenten mit aktivierten Benutzerrechten.

Bei PDF-Dokumenten, denen entsprechende Verwendungsrechte hinzugefügt wurden, können Empfängerinnen und Empfänger die folgenden Aktivitäten in Adobe Reader durchführen:

* Ausfüllen von PDF-Dokumenten und Formularen online oder offline, sodass Empfängerinnen und Empfänger lokale Kopien speichern können, ohne hinzufügte Informationen zu verlieren
* Speichern von PDF-Dokumenten auf einer lokalen Festplatte, um das Originaldokument und alle weiteren Kommentare, Daten oder Anlagen beizubehalten
* Anhängen von Dateien und Medien-Clips an PDF-Dokumente
* Signieren, Zertifizieren und Authentifizieren von PDF-Dokumenten durch die Anwendung digitaler Signaturen mithilfe von PKI-Technologien (PKI = Public Key Infrastructure), die dem Industriestandard entsprechen
* Elektronisches Senden ausgefüllter oder mit Anmerkungen versehener PDF-Dokumente
* Verwenden von PDF-Dokumenten und -Formularen als intuitives Entwicklungs-Frontend für interne Datenbanken und Web-Dienste
* Freigeben von PDF-Dokumenten für andere Benutzende, sodass Prüfende mit intuitiven Markup-Werkzeugen Kommentare hinzufügen können Zu diesen Werkzeugen gehören elektronische Haftnotizen, Stempel, Hervorheben und Durchstreichen. Dieselben Funktionen sind in Acrobat verfügbar.
* Unterstützen der Dekodierung von Barcode-Formularen.

Diese speziellen Benutzerfunktionen werden automatisch aktiviert, wenn ein PDF-Dokument mit aktivierten Rechten in Adobe Reader geöffnet wird. Wenn Benutzende die Arbeit mit einem Dokument mit aktivierten Rechten beendet haben, sind diese Funktionen in Adobe Reader wieder deaktiviert. Sie bleiben deaktiviert, bis die Benutzenden ein anderes PDF-Dokument mit aktivierten Rechten erhält.

Der DocAssurance-Dienst ist nicht vorkonfiguriert verfügbar. Informationen zum Konfigurieren des DocAssurance-Services finden Sie unter [Installation und Konfiguration von Dokumenten-Services](../../forms/using/install-configure-document-services.md).

## An Drucker senden {#send-to-printer-service}

Der Service „An Drucker senden“ stellt eine API zum Senden von Dokumenten zum Drucken an den angegebenen Drucker zur Verfügung.
