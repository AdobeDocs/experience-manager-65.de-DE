---
title: Übersicht über AEM-Dokumentendienste
seo-title: Overview of AEM Document Services
description: AEM Document Services sind eine Reihe von OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten.
seo-description: AEM Document Services are a set of OSGi Services for creating, assembling, and securing PDF Documents.
uuid: 439144b7-f805-4819-9ed9-a6e9e374b5ed
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 10d406db-ac10-479b-b08b-d0735116a12b
docset: aem65
exl-id: 4c8a3877-1a3c-410d-ad1f-69c73ba4fcc1
source-git-commit: 1683338f02d01d5d9843368955fa42f309718f26
workflow-type: tm+mt
source-wordcount: '1423'
ht-degree: 29%

---

# Übersicht über AEM-Dokumentendienste{#overview-of-aem-document-services}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html) |
| AEM 6.5 | Dieser Artikel |


AEM Document Services sind eine Reihe von OSGi-Diensten zum Erstellen, Zusammenstellen und Sichern von PDF-Dokumenten. Document Services enthält die folgenden Dienste:

## Ausgabe-Service {#output-service}

Mit dem Output-Dienst können Sie Dokumente in verschiedenen Formaten erstellen, darunter PDF, Laserdruckerformate und Beschriftungsdruckerformate. Laser-Druckerformate sind PostScript und Printer Control Language (PCL). In der folgenden Liste sind die Beschriftungsdruckerformate aufgeführt:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Ein Dokument kann an einen Netzwerkdrucker, einen lokalen Drucker oder eine Datei im Dateisystem gesendet werden. Der Output-Dienst führt XML-Formulardaten mit einem Formularentwurf zusammen, um ein Dokument zu generieren. Der Output-Dienst kann ein Dokument generieren, ohne XML-Formulardaten in das Dokument zusammenzuführen. Der primäre Workflow besteht jedoch darin, Daten in dem Dokument zusammenzuführen.

>[!NOTE]
>
>Ein Formularentwurf wird normalerweise mit Designer erstellt. Informationen zum Erstellen von Formularentwürfen für den Output-Dienst finden Sie in der Designer-Hilfe.

Bei Verwendung des Output-Dienstes zum Zusammenführen von XML-Daten mit einem Formularentwurf ist das Ergebnis ein nicht interaktives PDF-Dokument. Bei einem nicht interaktiven PDF-Dokument können Benutzer keine Daten in die Felder eingeben. Im Gegensatz dazu können Sie mit dem Forms-Dienst ein interaktives PDF-Formular erstellen, mit dem Benutzer Daten in die Felder eingeben können.

Die folgenden vier Output-Dienstvorgänge können verwendet werden:

* **generatePDFOuput**: Führt einen Formularentwurf mit Daten zusammen, um ein PDF-Dokument zu generieren
* **generatePrintedOutput**: Führt einen Formularentwurf mit Formulardaten zusammen, um ein Dokument zu erstellen, das entweder an einer Laserdrucker oder einen Beschriftungsnetzwerkdrucker gesendet werden soll.

* **generatePDFOutputBatch**: Führt mehrere Vorlagen mit mehreren Datensätzen in einem einzigen Aufruf zusammen, um einen Stapel von PDF-Dateien zu generieren. Es gibt auch die Möglichkeit, eine einzelne PDF zu generieren, indem alle PDF kombiniert werden
* **generatePrintedOutputBatch**: Führt mehrere Vorlagen mit mehreren Dateneinträgen in einem einzigen Aufruf zusammen, um einen Stapel gedruckter Dokumente (PS, PCL, ZPL, DPL, IPL, TPCL) zu erzeugen. Es gibt auch eine Option zum Generieren eines einzigen Druckdokuments.

## Assembler-Service {#assembler-service}

Mit dem Assembler-Dienst können Sie PDF- und XDP-Dokumente kombinieren, neu anordnen und erweitern und Informationen über PDF-Dokumente abrufen. Jeder Auftrag, der an den Assembler-Dienst gesendet wird, umfasst ein DDX-Dokument (Document Description XML), Quelldokumente und externe Ressourcen (Zeichenfolgen und Grafiken). Das DDX-Dokument enthält Anweisungen zur Verwendung der Quelldokumente zum Erstellen eines Satzes von Zieldokumenten.

Neben den oben genannten Funktionen gilt für den Assembler-Dienst Folgendes:

* Konvertiert PDF-Dokumente in den PDF/A-Standard.
* Der Dienst wandelt PDF-Formulare, in Designer erstellte XML-Formulare und in Acrobat erstellte PDF-Formulare in PDF/A-1b, PDF/A-2b und PDFA/A-3b um.
* Der Dienst konvertiert signierte und nicht signierte PDF-Dokumente (Digital Signatures erforderlich).
* Validiert die Konformität einer PDF/A-Datei und konvertiert sie bei Bedarf.

### Über DDX {#about-ddx}

Verwenden Sie bei Verwendung des Assembler-Dienstes eine XML-basierte Sprache namens Document Description XML (DDX), um die gewünschte Ausgabe zu beschreiben. DDX ist eine deklarative Markup-Sprache, deren Elemente Bausteine von Dokumenten darstellen. Diese Bausteine umfassen PDF-Dokumente, XDP-Dokumente, XDP-Formularfragmente und andere Elemente wie Kommentare, Lesezeichen und formatierten Text.

DDX-Dokument kann Zieldokumente mit folgenden Eigenschaften angeben:

* Ein PDF-Dokument, das aus mehreren PDF-Dokumenten assembliert ist.
* Mehrere PDF-Dokumente, die von einem einzelnen PDF-Dokument aufgeteilt wurden.
* PDF-Portfolio, das eine in sich abgeschlossene Benutzeroberfläche sowie mehrere PDF- und Nicht-PDF-Dokumente enthält.
* Ein XDP-Dokument, das aus mehreren XDP-Dokumenten assembliert ist.
* Ein XDP-Dokument, das XML-Fragmente enthält, die dynamisch in ein XDP-Dokument eingefügt wurden.
* Ein PDF-Dokument, das ein XDP-Dokument packt.
* XML-Dateien, die über die Merkmale eines PDF-Dokuments berichten. Zu den gemeldeten Eigenschaften gehören Text, Kommentare, Formulardaten, Dateianlagen, in PDF-Portfolios verwendete Dateien, Lesezeichen und PDF-Eigenschaften. Zu den PDF-Eigenschaften gehören Formulareigenschaften, Seitendrehung und Dokumentautor.

Sie können DDX verwenden, um PDF-Dokumente im Rahmen der Dokumentzusammenführung oder -zerlegung zu erweitern. Sie können eine beliebige Kombination der folgenden Effekte festlegen:

* Hinzufügen von Wasserzeichen oder Hintergründen zu ausgewählten Seiten (oder deren Entfernung)
* Hinzufügen von Kopf- und Fußzeilen zu ausgewählten Seiten (oder deren Entfernung)
* Entfernt die Struktur und Navigationsfunktionen eines PDF-Packages oder PDF-Portfolios. Das Ergebnis ist eine PDF-Datei.
* Seitenbeschriftungen werden umnummeriert. Seitenbeschriftungen werden normalerweise für die Seitennummerierung verwendet.
* Importieren von Metadaten aus einem anderen Quelldokument
* Hinzufügen oder Entfernen von Dateianlagen, Lesezeichen, Hyperlinks, Kommentaren und JavaScript.
* Festlegen der Ansicht beim Öffnen und Optimierung der Anzeige im Internet
* Festlegen von Berechtigungen für verschlüsselte PDF-Dokumente
* Drehen von Seiten bzw. Drehen und Verschieben von Seiteninhalten
* Ändern der Größe von ausgewählten Seiten.
* Zusammenführen von Daten mit einer XFA-basierten PDF-Datei.

Sie können eine einfache Eingabezuordnung verwenden, um die Speicherorte der Quell- und Zieldokumente anzugeben. Sie können auch die folgenden URL-Typen für externe Daten verwenden:

* File
* FTP
* HTTP/HTTPS

## DocAssurance-Dienst {#doc-assurance-service}

Der DocAssurance-Dienst unterstützt Sie beim Verschlüsseln und Entschlüsseln von Dokumenten, beim Erweitern der Funktionen von Adobe Reader mit zusätzlichen Nutzungsrechten sowie beim Hinzufügen digitaler Signaturen zu Ihren Dokumenten. Ihre Benutzer können einfach mit PDF forms und Dokumenten interagieren, während Ihr Unternehmen die Sicherheit, Archivierung und Compliance verbessert.

Der DocAssurance-Dienst umfasst drei Dienste: Signature, Encryption und Reader Extension.

### Signature-Dienst {#signature-service}

Mit dem Signature-Dienst können Sie mit digitalen Signaturen und Dokumenten auf dem AEM-Server arbeiten. Der Signature-Dienst wird beispielsweise in der Regel in folgenden Situationen verwendet:

* Der AEM-Server zertifiziert ein Formular, bevor es an einen Benutzer zum Öffnen mithilfe von Acrobat oder Adobe Reader gesendet wird.
* Der AEM überprüft eine Signatur, die einem Formular mithilfe von Acrobat oder Adobe Reader hinzugefügt wurde.
* Der AEM-Server signiert ein Formular im Namen eines öffentlichen Notars.

Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu, die im Trust Store gespeichert sind.

### Encryption-Service {#encryption-service}

Mit dem Encryption-Dienst können Sie Dokumente verschlüsseln und entschlüsseln. Wenn ein Dokument verschlüsselt wird, ist sein Inhalt unlesbar. Sie können das gesamte PDF-Dokument (einschließlich Inhalt, Metadaten und Anlagen), alles außer den Metadaten oder nur die Anlagen verschlüsseln. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf seinen Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, müssen die Benutzenden das Kennwort zum Öffnen angeben, damit das Dokument in Reader oder Adobe Acrobat angezeigt werden kann. Wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, muss der Benutzer das PDF-Dokument mit einem privaten Schlüssel (Zertifikat) entschlüsseln. Der zum Entschlüsseln des PDF-Dokuments verwendete private Schlüssel muss dem öffentlichen Schlüssel entsprechen, der zum Verschlüsseln verwendet wird.

### Reader Extension-Dienst {#reader-extension-service}

Der Reader Extensions-Dienst ermöglicht Ihrem Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweiterung der Funktionalität von Adobe Reader um zusätzliche Verwendungsrechte. Der Reader Extensions-Dienst funktioniert mit Adobe Reader 7.0 oder höher. Der Dienst fügt einem PDF-Dokument Verwendungsrechte hinzu. Diese Aktion aktiviert Funktionen, die normalerweise nicht verfügbar sind, wenn ein PDF-Dokument mit Adobe Reader geöffnet wird, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. Externe Benutzende benötigen keine zusätzliche Software oder Plug-ins für das Verwenden von Dokumenten mit aktivierten Benutzerrechten.

Wenn PDF-Dokumente über die entsprechenden Verwendungsrechte verfügen, können Empfänger die folgenden Aktivitäten in Adobe Reader durchführen:

* Ausfüllen von PDF-Dokumenten und -Formularen online oder offline, sodass Empfänger lokale Kopien für ihre Datensätze speichern und die hinzugefügten Informationen beibehalten können
* Speichern Sie PDF-Dokumente auf einer lokalen Festplatte, um das Originaldokument und alle weiteren Kommentare, Daten oder Anlagen beizubehalten.
* Anhängen von Dateien und Medienclips an PDF-Dokumente
* Signieren, Zertifizieren und Authentifizieren von PDF-Dokumenten durch die Anwendung digitaler Signaturen mithilfe von PKI-Technologien (PKI-Technologien), die dem Industriestandard entsprechen
* Elektronische Übermittlung ausgefüllter oder mit Anmerkungen versehener PDF-Dokumente
* Verwenden von PDF-Dokumenten und -Formularen als intuitives Entwicklungs-Frontend für interne Datenbanken und Webdienste
* Geben Sie PDF-Dokumente für andere frei, damit Überprüfer Kommentare mithilfe intuitiver Markup-Tools hinzufügen können. Zu diesen Tools gehören elektronische Haftnotizen, Stempel, Highlights und Text-Durchstreichung. Dieselben Funktionen sind in Acrobat verfügbar.
* Unterstützt die Dekodierung mit Strichcode versehener Formulare.

Diese speziellen Benutzerfunktionen werden automatisch aktiviert, wenn ein PDF-Dokument mit aktivierten Benutzerrechten in Adobe Reader geöffnet wird. Wenn der Benutzer die Arbeit mit einem Dokument mit aktivierten Benutzerrechten beendet hat, sind diese Funktionen in Adobe Reader erneut deaktiviert. Sie bleiben deaktiviert, bis der Benutzer ein anderes PDF-Dokument mit aktivierten Benutzerrechten erhält.

Standardmäßig ist der DocAssurance-Dienst nicht verfügbar. Informationen zum Konfigurieren des DocAssurance-Services finden Sie unter [Installation und Konfiguration von Dokumenten-Services](../../forms/using/install-configure-document-services.md).

## An Drucker senden {#send-to-printer-service}

Der Service „An Drucker senden“ stellt eine API zum Senden von Dokumenten zum Drucken an den angegebenen Drucker zur Verfügung.
