---
title: Diensteinstellungen konfigurieren
seo-title: Configure service settings
description: Erfahren Sie, wie Sie die Diensteinstellungen konfigurieren.
seo-description: Learn how to configure service settings.
uuid: e95425a4-62f6-473e-b21b-d081c432e02d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 2fab4b0c-e5db-47cd-b85a-4ff5ad6eb178
exl-id: a6a10ff0-6f4d-42df-9b4e-f98a53cf1806
source-git-commit: 0c7dba43dad8608b4a5de271e1e44942c950fb16
workflow-type: ht
source-wordcount: '10683'
ht-degree: 100%

---

# Diensteinstellungen konfigurieren {#configure-service-settings}

Sie können die Dienstverwaltungsseite verwenden, um Einstellungen für jeden der Dienste zu konfigurieren, die Bestandteil von AEM Forms sind. Die verfügbaren Einstellungen sind vom zu konfigurierenden Dienst abhängig.

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Beenden Sie den Dienst, bevor Sie ihn ändern. (Siehe [Starten und Beenden von Diensten](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
1. Klicken Sie auf den Namen des Dienstes, der konfiguriert werden soll.
1. Wenn der Dienst über eine Registerkarte „Konfiguration“ verfügt, ändern Sie dort seine Einstellungen. Weitere Informationen finden Sie in der Linkliste unten.

   >[!NOTE]
   >
   >Nicht alle Dienste, die auf der Seite „Dienstverwaltung“ aufgelistet sind, verfügen über die Registerkarte „Konfiguration“. Für von Ihnen erstellte Prozesse wird die Registerkarte „Konfiguration“ nur angezeigt, wenn Sie dem Prozess in Workbench einen Konfigurationsparameter hinzugefügt haben. (Siehe „Konfigurationsparameter“ in der[ Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).) 


1. Klicken Sie auf die Registerkarte „Sicherheit“ und legen Sie die Sicherheitseinstellungen für den Dienst fest. Siehe [Ändern von Sicherheitseinstellungen für einen Dienst](configure-service-settings.md#modifying-security-settings-for-a-service).
1. Wenn der Dienst über eine Registerkarte „Endpunkte“ verfügt, ändern Sie dort seine Endpunkteinstellungen. Siehe [Verwalten von Endpunkten](/help/forms/using/admin-help/adding-enabling-modifying-or-removing.md).
1. Klicken Sie auf die Registerkarte „Pooling“ und legen Sie die Poolingeinstellungen fest. Siehe [Pooling für einen Dienst konfigurieren](configure-service-settings.md#configuring-pooling-for-a-service).
1. Klicken Sie auf „Speichern“, um die Änderungen zu speichern, oder auf „Abbrechen“, um sie zu verwerfen.
1. Aktivieren Sie das Kontrollkästchen neben dem Dienstnamen und klicken Sie auf „Starten“, um den Dienst neu zu starten.

## Einstellungen des Audit Workflow-Dienstes {#audit-workflow-service-settings}

Workbench gibt Ihnen die Möglichkeit, Prozessinstanzen während der Ausführung zur Laufzeit aufzuzeichnen und anschließend wiederzugeben, um das Verhalten des Prozesses zu untersuchen. (Siehe [Workbench-Hilfe](https://www.adobe.com/go/learn_aemforms_workbench_63_de).) Zum Einsparen von Speicherplatz auf dem Dateisystem des Formularservers können Sie die Menge der zu speichernden Prozessaufzeichnungsdaten begrenzen. Sie können die folgenden Eigenschaften des Audit Workflow-Dienstes (`AuditWorkflowService`) konfigurieren:

**maxNumberOfRecordingInstances**: Die maximale Anzahl von zu speichernden Aufzeichnungen. Wenn die maximale Anzahl gespeichert ist, wird beim Erstellen einer neuen Aufzeichnung die älteste Aufzeichnung aus dem Dateisystem gelöscht. Diese Eigenschaft ist nützlich, wenn Sie dazu neigen, viele Aufzeichnungen zu erstellen, und alte Aufzeichnungen automatisch löschen möchten. Der Standardwert ist 50.

**MaxNumberOfRecordingEntries**: Die maximale Anzahl von Dateneinträgen, die für jede Aufzeichnung gespeichert werden können. Bei Dateneinträgen handelt es sich um Informationen zu Vorgängen in dem Prozess. Für jede Ausführung eines Vorgangs werden mehrere Einträge gespeichert, z. B. ob der Vorgang gestartet wurde, ob der Vorgang beendet wurde und ob die Route, die zu dem Vorgang führt, vollständig ist. Diese Eigenschaft ist nützlich, wenn Prozesse die Ausführung vieler Vorgänge beinhalten, z. B. wenn eine Endlosschleife auftritt. Der Standardwert ist 50.

## Einstellungen des Barcoded Forms-Dienstes {#barcoded-forms-service-settings}

Der Barcoded Forms-Service `(BarcodedFormsService)` extrahiert Barcode-Daten aus gescannten Bildern. Der Dienst akzeptiert ein Strichcodeformat (TIFF oder PDF) als Eingabe und extrahiert die Computerdarstellung der vom Strichcode kodierten Daten.

Folgende Einstellungen sind für den Barcoded Forms-Dienst verfügbar:

**Nach links erfassen**: Wenn diese Option aktiviert ist, werden Barcode-Grafiken horizontal von rechts nach links gescannt.

**Nach rechts erfassen**: Wenn diese Option aktiviert ist, werden Barcode-Grafiken horizontal von links nach rechts gescannt.

**Nach oben erfassen**: Wenn diese Option aktiviert ist, werden Barcode-Grafiken vertikal von unten nach oben gescannt.

**Nach unten erfassen**: Wenn diese Option aktiviert ist, werden Barcode-Grafiken vertikal von oben nach unten gescannt.

>[!NOTE]
>
>Standardmäßig sind alle diese Optionen aktiviert. Deaktivieren Sie eine der Optionen nur, wenn Sie sicher sind, dass auf Ihren Formularen keine Strichcodes in dieser Richtung vorhanden sind.

**Basisdateipfad**: Der Dateipfad, in dem die Parameter für die Batch-Eingabe und die Ausgabedatei für die Vorgänge „Run XML File Job“ und „Run Flat File Job“ aufgelöst werden. In Cluster-Konfigurationen muss der Basisdateipfad ein freigegebener Dateisystemspeicherort sein, auf den alle Cluster-Knoten Lese-/Schreibzugriff haben.

**Datenquellenname**: Der Name der Datenquelle, die zur Pflege von Status- und Verlaufsinformationen zu Batch-Verarbeitungsvorgängen verwendet wird. Die angegebene Datenquelle muss globale (XA-)Transaktionen unterstützen.

## Einstellungen für Central Migration Bridge-Dienst (veraltet) {#central-migration-bridge-service-settings}

Der Central Migration Bridge-Dienst (`CentralMigrationBridge`) ruft eine Untergruppe von Funktionen aus Adobe Central Pro Output Server (Central-Funktionen) auf, zu der die Befehle JFMERGE, JFTRANS und XMLIMPORT gehören. Mithilfe von Vorgängen des Central Migration Bridge-Dienstes können Sie die folgenden Central-Elemente in AEM Forms wiederverwenden:

* Vorlagendesign (*.ifd)
* Ausgabevorlagen (*.mdf)
* Datendateien (*.dat-Dateien)
* Präambeldateien (*.pre-Dateien)
* Datendefinitionsdateien (*.tdf)

Folgende Einstellung ist für den Central Migration Bridge-Dienst verfügbar:

**Central-Installationsordner**: Der Ordner, in dem Adobe Central 5.7 installiert ist.

## Einstellungen des Content Repository Connector for EMC Documentum-Dienstes {#content-repository-connector-for-emc-documentum-service-settings}

Der Content Repository Connector für EMC Documentum-Dienst (`EMCDocumentumContentRepositoryConnector`) ermöglicht das Erstellen von Prozessen, die mit in einem Documentum-Repository gespeicherten Inhalten interagieren. 

Folgende Einstellung ist für den Content Repository Connector für EMC Documentum-Dienst verfügbar:

**Standardpfad für Elementverknüpfungsobjekt**: Der Standardteil des Pfades im Documentum-Repository zum Speichern des Elementverknüpfungsobjekts. Der tatsächliche Pfad besteht aus dem Standardpfad und dem Speicherort der Formularvorlage im AEM Forms-Repository.

Wenn beispielsweise der Standardpfad auf `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects` festgelegt und die Formularvorlage im Ordner `/Docbase/forms/` gespeichert ist, wird das Elementverknüpfungsobjekt am folgenden Speicherort gespeichert:

`/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects/Docbase/forms/`

Der Standardwert für diese Einstellung ist `/LiveCycleES/ConnectorforEMCDocumentum/AssetLinkObjects`.

## Einstellungen des Content Repository Connector for IBM FileNet-Dienstes {#content-repository-connector-for-ibm-filenet-service-settings}

Der Content Repository Connector für IBM FileNet-Dienst ermöglicht das Erstellen von Prozessen, die mit in einem IBM FileNet-Repository gespeicherten Inhalten interagieren. 

Folgende Einstellung ist für den Content Repository Connector für IBM FileNet-Dienst verfügbar:

**Standardpfad für Elementverknüpfungsobjekt**: Der Standardteil des Pfades im IBM FileNet-Repository zum Speichern des Elementverknüpfungsobjekts. Der tatsächliche Pfad besteht aus dem Standardpfad und dem Speicherort der Formularvorlage im AEM Forms-Repository.

Wenn beispielsweise der Standardpfad auf `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects` festgelegt und die Formularvorlage im Ordner `/Docbase/forms/` gespeichert ist, wird das Elementverknüpfungsobjekt am folgenden Speicherort gespeichert:

`/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects/Docbase/forms/`

Der Standardwert für diese Einstellung ist `/LiveCycleES/ConnectorforIBMFileNet/AssetLinkObjects`.

## Einstellungen des Convert PDF-Dienstes {#convert-pdf-service-settings}

Der Convert PDF-Dienst (`ConvertPdfService`) konvertiert PDF-Dokumente in PostScript sowie verschiedene Bildformate (JPEG, JPEG 2000, PNG und TIFF). Das Konvertieren eines PDF-Dokuments in PostScript ist nützlich für die unbeaufsichtigte serverbasierte Druckausgabe auf PostScript-Druckern. Das Konvertieren eines PDF-Dokuments in eine mehrseitige TIFF-Datei ist beim Archivieren von Dokumenten in Content Management-Systemen praktisch, die PDF-Dokumente nicht unterstützen.

Folgende Einstellungen sind für den Convert PDF-Dienst verfügbar:

**Transaktionstyp**: Gibt an, wie ein Transaktionskontext an einen Vorgang weitergegeben werden soll.

**Erforderlich**: Ein Transaktionskontext wird unterstützt, wenn bereits einer vorhanden ist. Andernfalls wird ein neuer Transaktionskontext erstellt. Dies ist der Standardwert.

**Neu Erforderlich**: Es wird immer ein Transaktionskontext erstellt. Wenn bereits ein aktiver Transaktionskontext vorhanden ist, wird dieser ausgesetzt.

**Transaktionszeitlimit (in Sek.)**: Die Anzahl der Sekunden, die ein zugrunde liegender Transaktionsanbieter wartet, bevor eine Transaktion rückgängig gemacht wird, die diesen Vorgang beinhaltet. Dieser Wert wird ignoriert, wenn ein vorhandener Transaktionskontext weitergegeben wird. Der Standardwert ist 180.

**Schwellenwert-Auflösung für Glättung (in dpi)**: Die Bildauflösung, unterhalb derer Glättung (bzw. Anti-Aliasing) auf Text, Strichgrafiken und Bilder angewendet wird, wenn Sie die Optionen zum Anwenden der Glättung für diese Elemente ausgewählt haben.

**Glätten auf Text anwenden**: Steuert das Anti-Aliasing von Text. Um die Glättung von Text zu deaktivieren und Text schärfer und mit einer Vergrößerungssoftware leichter lesbar zu machen, deaktivieren Sie dieses Kontrollkästchen.

**Glätten auf LineArt anwenden**: Wendet Glättung an, um abrupte Winkel in Linien zu entfernen.

**Glätten auf Bilder anwenden**: Wendet Glättung an, um abrupte Änderungen in Bildern zu minimieren.

## Einstellungen des Distiller-Dienstes {#distiller-service-settings}

Der Distiller-Dienst (`DistillerService`) konvertiert PostScript-, Encapsulated PostScript (EPS)- und PRN-Dateien über ein Netzwerk in PDF-Dateien.

Folgende Einstellungen sind für den Distiller-Dienst verfügbar:

**Adobe PDF-Einstellungen**: Folgende vorkonfigurierte Einstellungen werden auf die generierte PDF-Datei angewendet:

* Drucken in hoher Qualität
* Seiten in Übergrößen
* PDFA1b 2005 CMYK
* PDFA1b 2005 RGB
* PDFX1a 2001
* PDFX3 2002
* Druckqualität
* Minimale Dateigröße
* Standard

Neue Einstellungen können über die Benutzeroberfläche von PDF Generator erstellt werden.

**Sicherheitseinstellungen**: Vorkonfigurierte Sicherheitseinstellungen, die auf generierte PDF-Dokumente angewendet werden. Der Standardwert ist „Ohne Sicherheit“. Sie müssen Sicherheitseinstellungen mithilfe von PDF Generator erstellen und dann hier eingeben.

**Pool-Größe**: Die Anfangsgröße des Pools. Wenn der Distiller-Dienst bereitgestellt wird, wird mithilfe dieses Wertes die Anzahl der Dienstimplementierungsinstanzen ermittelt, die erstellt und dem freien Pool zugeordnet werden, der auf Aufrufanforderungen wartet. Der Dienstcontainer kann dann sofort auf Aufrufanforderungen reagieren, ohne zuerst eine Dienstinstanz initialisieren zu müssen.

## Einstellungen des Document Management-Dienstes {#document-management-service-settings}

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (nicht mehr unterstützt) ist ein Inhaltsverwaltungssystem, das mit LiveCycle installiert wird. Es ermöglicht es Benutzern, am Menschen orientierte Prozesse zu entwerfen, zu verwalten, zu überwachen und zu optimieren. Die Unterstützung von Content Services (veraltet) endet am 31.12.2014. Siehe [Adobe-Produkt-Lifecycle-Dokument](https://www.adobe.com/de/support/products/enterprise/eol/eol_matrix.html).

Der Document Management-Dienst (`DocumentManagementService`) ermöglicht, dass Prozesse die von Content Services (nicht mehr unterstützt) bereitgestellten Inhaltsverwaltungsfunktionen verwenden können. Document Management-Vorgänge bieten grundlegende Aufgaben, die zum Warten von Bereichen und Inhalten im Inhaltsverwaltungssystem erforderlich sind. Beispiele für solche Aufgaben sind das Kopieren, Löschen, Verschieben, Abrufen und Speichern von Inhalten, das Erstellen von Bereichen und Zuordnungen sowie das Abrufen und Festlegen von Inhaltsattributen.

Folgende Einstellungen sind für den Document Management-Dienst verfügbar:

**Speicherschema**: Das Schema des Speichers, in dem sich die Inhalte befinden. Der Standardwert ist „workspace“.

**HTTP-Port:** Der Port, der für den Zugriff auf Content Services (veraltet) verwendet wird. Der Standardwert ist 8080.

## Einstellungen des E-Mail-Dienstes {#email-service-settings}

E-Mail wird im Allgemeinen im Rahmen eines automatisierten Prozesses zum Verteilen von Inhalten oder Bereitstellen von Statusinformationen genutzt. Der E-Mail-Dienst (`EmailService`) ermöglicht Prozessen das Empfangen von E-Mail-Nachrichten von einem POP3- oder IMAP-Server und das Senden von E-Mail-Nachrichten an einen SMTP-Server.

Ein Prozess nutzt beispielsweise den E-Mail-Dienst zum Senden einer E-Mail-Nachricht mit einem PDF-Formular als Anlage. Der E-Mail-Dienst verbindet sich mit einem SMTP-Server, um die E-Mail-Nachricht mit der Anlage zu senden. Das PDF-Formular ermöglicht es dem Empfänger, nach dem Ausfüllen auf „Senden“ zu klicken. Dadurch wird das Formular als Anlage an den vorgesehenen E-Mail-Server zurückgesendet. Der E-Mail-Dienst ruft die zurückgegebene E-Mail-Nachricht ab und speichert das ausgefüllte Formular in den Prozessdaten als Formularvariable.

Folgende Einstellungen sind für den E-Mail-Dienst verfügbar:

**SMTP-Host**: Die IP-Adresse oder die URL des SMTP-Servers, der zum Senden von E-Mails verwendet wird.

**SMTP-Port-Nummer**: Geben Sie den Port an, über den die Verbindung zum SMTP-Server hergestellt wird.

**SMTP-Authentifizierung**: Wählen Sie aus, ob eine Benutzerauthentifizierung zum Herstellen einer Verbindung mit dem SMTP-Server erforderlich ist.

**SMTP-Benutzer**: Der Benutzername des Benutzerkontos, das zum Anmelden beim SMTP-Server verwendet wird.

**SMTP-Kennwort**: Das dem SMTP-Benutzerkonto zugeordnete Kennwort.

**SMTP-Transportsicherheit**: Das Sicherheitsprotokoll, das zum Herstellen einer Verbindung mit dem SMTP-Server verwendet wird.

* Wählen Sie „None“ aus, wenn kein Protokoll verwendet wird. (Daten werden unverschlüsselt gesendet.)
* Wählen Sie „SSL“ aus, wenn das SSL-Protokoll (Secure Sockets Layer) verwendet wird.
* Wählen Sie „TLS“ aus, wenn TLS (Transport Layer Security) verwendet wird.

**POP3/IMAP-Host**: Die IP-Adresse oder die URL des POP3- oder IMAP-Servers, der zum Senden von E-Mails verwendet wird.

**POP3/IMAP-Benutzername**: Der Benutzername des Benutzerkontos, das zum Anmelden beim POP3- oder IMAP-Server verwendet wird.

**POP3/IMAP-Kennwort**: Das dem POP3- oder IMAP-Benutzerkonto zugeordnete Kennwort.

**POP3/IMAP-Port-Nummer:** Der Port, der für die Verbindung mit dem POP3- oder IMAP-Server verwendet wird.

**POP3/IMAP**: Das Protokoll, das zum Senden und Empfangen von E-Mails verwendet wird.

**Empfangstransportsicherheit**: Das Sicherheitsprotokoll, das zum Herstellen einer Verbindung mit dem SMTP-Server verwendet wird.

* Wählen Sie „None“ aus, wenn kein Protokoll verwendet wird. (Daten werden unverschlüsselt gesendet.)
* Wählen Sie „SSL“ aus, wenn das SSL-Protokoll (Secure Sockets Layer) verwendet wird.
* Wählen Sie „TLS“ aus, wenn TLS (Transport Layer Security) verwendet wird.

## Einstellungen des Encryption-Dienstes {#encryption-service-settings}

Der Encryption-Dienst (`EncryptionService`) ermöglicht das Ver- und Entschlüsseln von Dokumenten. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. Wenn ein PDF-Dokument mit einem Kennwort verschlüsselt wird, muss der Benutzer das Kennwort zum Öffnen angeben, damit das Dokument in Adobe Reader oder Adobe Acrobat angezeigt werden kann. Ähnlich muss der Benutzer, wenn ein PDF-Dokument mit einem Zertifikat verschlüsselt ist, das PDF-Dokument mithilfe des öffentlichen Schlüssels entschlüsseln, der dem Zertifikat (privater Schlüssel) entspricht, das zum Verschlüsseln des PDF-Dokuments verwendet wurde.

Folgende Einstellungen sind für den Encryption-Dienst verfügbar:

**Standard-LDAP-Server für Verbindung**: Host-Name des LDAP-Servers, der zum Abrufen von Zertifikaten für die Dokumentverschlüsselung verwendet wird.

**Standard-LDAP-Port für die Verbindung**: Port-Nummer des LDAP-Servers.

**Standard-LDAP-Benutzername**: Wenn der LDAP-Server eine Authentifizierung erfordert, geben Sie den Benutzernamen an, der für die Verbindung mit dem LDAP-Server verwendet werden soll.

**Standard-LDAP-Kennwort:** Wenn der LDAP-Server eine Authentifizierung erfordert, geben Sie das Kennwort an, das dem Benutzernamen entspricht, der für die Verbindung mit dem LDAP-Server verwendet werden soll.

>[!NOTE]
>
>Verwenden Sie einfache Authentifizierung (Benutzername und Kennwort) nur, wenn die Verbindung mit SSL (unter Verwendung von LDAPS) geschützt ist.

**Kompatibilitätsmodus:**

## Einstellungen des FTP-Dienstes {#ftp-service-settings}

Der FTP-Dienst (`FTP`) ermöglicht Prozessen die Interaktion mit einem FTP-Server. Der FTP-Dienst kann Dateien von einem FTP-Server abrufen, auf einem FTP-Server ablegen und von einem FTP-Server löschen. Dokumente, z. B. in einem Prozess erzeugte Berichte, können beispielsweise zur Verteilung auf einem FTP-Server gespeichert werden. Außerdem kann ein externes System kann Dateien basierend auf vorherigen Schritten in einem Prozess generieren. In einem Folgeschritt im Prozess können die Dateien an einen Remote-Speicherort übertragen werden.

Folgende Einstellungen sind für den FTP-Dienst verfügbar:

**Standard-Host**: Die IP-Adresse oder URL des FTP-Servers.

**Standard-Port**: Der Port, über den eine Verbindung mit dem FTP-Server hergestellt wird. Der Standardwert ist 21.

**Standardbenutzername**: Der Name des Benutzerkontos, mit dessen Hilfe Sie auf den FTP-Server zugreifen können. Das Benutzerkonto muss über ausreichende Berechtigungen verfügen, um die für diesen Dienst erforderlichen FTP-Vorgänge ausführen zu können.

**Standardkennwort**: Das Kennwort, das zusammen mit dem angegebenen Namen für die Authentifizierung beim FTP-Server verwendet wird.

## Einstellungen des Generate PDF-Dienstes {#generate-pdf-service-settings}

Mit dem Generate PDF-Dienst (`GeneratePDFService`) können Sie Dateien in verschiedenen nativen Formaten in PDF-Dokumente bzw. PDF-Dokumente in eine Vielzahl von Formaten konvertieren.

Folgende Einstellungen sind für den Generate PDF-Dienst verfügbar:

**Adobe PDF-Einstellungen**: Der Name der vorkonfigurierten Adobe PDF-Einstellungen, die auf einen Konvertierungsauftrag angewendet werden sollen, wenn diese Einstellungen nicht als Bestandteil der API-Aufrufparameter angegeben wurden. Sie können die Adobe PDF-Einstellungen in Administration Console konfigurieren, indem Sie auf „Dienste“ > „PDF Generator“ > „Adobe PDF-Einstellungen“ klicken. Diese Einstellungen gelten nur für PDFMaker-Konvertierungen.

**Sicherheitseinstellungen**: Der Name der vorkonfigurierten Sicherheitseinstellungen, die auf einen Konvertierungsauftrag angewendet werden sollen, wenn diese Einstellungen nicht als Bestandteil der API-Aufrufparameter angegeben wurden. Sie können die Sicherheitseinstellungen in Administration Console konfigurieren, indem Sie auf „Dienste“ > „PDF Generator“ > „Sicherheitseinstellungen“ klicken.

**Dateitypeinstellungen**: Der Name der vorkonfigurierten Dateitypeinstellungen, die auf einen Konvertierungsauftrag angewendet werden sollen, wenn diese Einstellungen nicht als Bestandteil der API-Aufrufparameter angegeben wurden. Sie können die Dateitypeinstellungen in Administration Console konfigurieren, indem Sie auf „Dienste“ > „ PDF Generator “ > „Dateitypeinstellungen“ klicken.

**Acrobat WebCapture verwenden (nur Windows)**: Wenn diese Einstellung aktiviert ist, verwendet der Generate PDF-Service für alle Konvertierungen von HTML in PDF Acrobat X Pro. Auf diese Weise kann die Qualität der aus HTML erzeugten PDF-Dateien verbessert werden, obwohl die Leistung möglicherweise etwas langsamer wird. Der Standardwert lautet false.

**Acrobat-Bildkonvertierung verwenden (nur Windows)**: Wenn diese Einstellung aktiviert ist, verwendet der Generate PDF-Servic für alle Konvertierungen von Bildern in PDF Acrobat X Pro. Diese Einstellung ist nur dann sinnvoll, wenn mit dem standardmäßigen, reinen Java-Konvertierungsmechanismus ein erheblicher Teil der Eingabebilder nicht erfolgreich konvertiert werden kann. Der Standardwert lautet false.

**Acrobat-basierte AutoCAD-Konvertierungen aktivieren (nur Windows)**: Wenn diese Einstellung aktiviert ist, verwendet der Generate PDF-Service für alle Konvertierungen von DWG in PDF Acrobat X Pro. Diese Einstellung ist nur sinnvoll, wenn AutoCAD nicht auf dem Server installiert ist bzw. wenn der AutoCAD-Konvertierungsmechanismus nicht in der Lage ist, Dateien erfolgreich zu konvertieren.

**Reguläre Ausdrücke zum Auffinden nicht zulässiger Sonderzeichen in Benutzernamen (nur Windows)**: Gibt Zeichen an, die den PDF erstellen- und PDF optimieren-Vorgang beeinträchtigen, wenn die Zeichen im Benutzernamen enthalten sind.

**ImageToPDF-Pool-Größe**: Die Pool-Größe des standardmäßigen (reinen Java) Bild-zu-PDF-Konverters im Generate PDF-Service. Mit dieser Einstellung steuern Sie die maximale Anzahl gleichzeitiger „Bild in PDF“-Konvertierungen, die der Generate PDF-Dienst ausführen kann. Der Standardwert dieser Einstellung (empfohlen für Einzelprozessorsysteme) ist 3, wobei der Wert für Multiprozessorsysteme erhöht werden kann.

**„HTML in PDF“-Pool-Größe**: Die Pool-Größe des HTML-zu-PDF-Konverters im Generate PDF-Service. Mit dieser Einstellung steuern Sie die maximale Anzahl gleichzeitiger „HTML in PDF“-Konvertierungen, die der Generate PDF-Dienst ausführen kann. Der Standardwert dieser Einstellung (empfohlen für Einzelprozessorsysteme) ist 3, wobei der Wert für Multiprozessorsysteme erhöht werden kann.

**OCR-Pool-Größe**: Die Pool-Größe des PaperCaptureService, den PDF Generator für optische Zeichenerkennung (OCR) verwendet. Der Standardwert dieser Einstellung (empfohlen für Einzelprozessorsysteme) ist 3, wobei der Wert für Multiprozessorsysteme erhöht werden kann. Diese Einstellung ist nur auf Windows-Systemen gültig.

**Ersatzschriftfamilie für HTML-zu-PDF-Konvertierungen**: Der Name der Schriftfamilie, die in PDF-Dokumenten verwendet werden soll, wenn die im Original-HTML verwendete Schriftart nicht für den AEM Forms-Server verfügbar ist. Geben Sie eine Schriftfamilie an, wenn Sie davon ausgehen, dass Sie HTML-Seiten konvertieren, die nicht verfügbare Schriften verwenden. Beispielsweise können auf Seiten, die in regionalen Sprachen geschrieben wurden, nicht verfügbare Schriften verwendet werden.

**Logik für native Konvertierungen wiederholen**: Steuert Wiederholungsversuche zur PDF-Generierung, wenn der erste Konvertierungsversuch fehlgeschlagen ist

**Nicht wiederholen** 

Wiederholen Sie die PDF-Konvertierung nicht, wenn der erste Konvertierungsversuch fehlgeschlagen ist. 

**Wiederholen** 

Wiederholen Sie die PDF-Konvertierung unabhängig davon, ob der Timeout-Grenzwert erreicht wurde. Die standardmäßige Timeout-Dauer für den ersten Versuch ist 270s.

**Wiederholen, wenn die Zeit ausreicht** 

Wiederholen Sie die PDF-Konvertierung, wenn die Zeit für den ersten Konvertierungsversuch geringer war als die angegebene Timeout-Dauer. Wenn die Timeout-Dauer beispielsweise 270 s beträgt und der erste Versuch dauerte 200 s, versucht PDF Generator eine erneute Konvertierung. Wenn der erste Versuch 270 s gedauert hat, wird die Konvertierung nicht wiederholt.

## Einstellungen des Guides ES4 Utilities-Dienstes {#guides-es4-utilities-service-settings}

Wenn Sie einen Guide erstellen, werden einige Ressourcen, z. B. die Guide-Definition, in den Guide eingebettet. Die Ressourcen können auch als Verweise auf Anwendungselemente vorhanden sein, die lokal oder auf dem AEM Forms-Server gespeichert sind. Der Guide enthält keine Daten und die Werte für den Sendespeicherort und die Eingaben sind nicht für alle externen Umgebungen geeignet.

In den meisten Fällen sind die Standardwiedergabedienste für Guides ausreichend, um einen Guide zur Verwendung in Workspace oder in externen Umgebungen vorzubereiten. (In der Ansicht „Dienste“ in Workbench ist der Standarddienst „Guides (System)/Processes/Render Guide - 1.0“.) Mit dem Guide Utilities-Dienst (`GuidesUtility`) können Sie, sofern erforderlich, einen benutzerdefinierten Prozess zum Wiedergeben eines Guides erstellen.

Die Guide Utilities-Vorgänge ermöglichen Ihnen das Hinzufügen der folgenden Guide-Wiedergabeaufgaben zu einem Prozess:

* Bestimmen, ob Daten zum Auffüllen des Guides verfügbar sind
* Guide-Daten einbetten oder in eine Verknüpfung konvertieren
* Referenzierte Inhalte in URLs konvertieren, auf die extern zugegriffen werden kann
* Werte in einem HTML-Dokument oder in einem anderen Wrapper ersetzen oder Sie sie in URLs konvertieren, auf die extern zugegriffen werden kann
* Sendespeicherort festlegen
* Eingabewerte angeben
* Einen Parameter erstellen, der die referenzierten Inhalte darstellt
* Wenn mehrere Varianten zur Verfügung stehen, eine davon festlegen

Die Standardwerte für den Guide Utilities-Dienst unterstützen die meisten Anwendungsfälle. Sie können die folgenden Werte jedoch ändern, wenn dies erforderlich ist.

**publicPaths**: Diese Option ist veraltet. Verwenden Sie diese Option nicht mit AEM Forms.

**pathInfoExpiryInSeconds**: Das Intervall in Sekunden, nach dem eine Anforderung für Pfadinformationen von einem Client abläuft. Der Standardwert ist 1.

**collateralExpiryInSeconds**: Das Intervall in Sekunden, nach dem eine Anforderung für einen Zusatz von einem Client abläuft. Der Standardwert ist 315576000.

**mismatchExpiryInSeconds**: Das Intervall in Sekunden, nach dem eine Anforderung für einen Zusatz von einem Client abläuft, wenn das eTag (Entity Tag) nicht übereinstimmt. (Ein eTag ist eine HTTP-Antwortkopfzeile.) Der Standardwert ist 1.

**guideContext**: Der Kontextstamm des Web-Programms Guides. Stimmt mit dem in der Guides-Webanwendung festgelegten Wert überein. Die Standardeinstellung ist /Guides/.

**secureRandomAlgorithm**: Der zum Erstellen von Schlüsseln und Bezeichnern zu verwendende Algorithmus. Dieser Wert wird an die getInstance-Methode der Java-Klasse „SecureRandom“ übergeben. Die Standardeinstellung ist SHA1PRNG.

**idBytes**: Die Anzahl zufälliger Bytes, die für einen Schlüsselbezeichner verwendet werden. Der Standardwert ist 6.

**macAlgorithm**: Der MAC-Algorithmus (Nachrichtenauthentifizierungs-Code), der für die ergänzende URL-Überprüfung verwendet wird. Diese Methode wird an die getInstance-Methode der Mac-Klasse übergeben. Die Standardeinstellung ist HmacSHA1.

**macRefreshIntervalInMinutes**: Die Zeitspanne in Minuten, für die ein Schlüssel aktiv ist. Wenn ein Schlüssel für diese Dauer aktiv war, wird ein neuer Schlüssel erstellt. Der neue Schlüssel wird der aktive Schlüssel. Der vorherige Schlüssel wird für 10 % des Aktualisierungsintervalls aufbewahrt. Durch dieses Verhalten können URLs, die durch Verwendung des alten Schlüssels erstellt wurden, nach dem Wechseln von Schlüsseln weiterhin verwendet werden. Der Standardwert ist 144000.

**macOverlapIntervalInMinutes**: Die Zeitspanne in Minuten, die der vorherige Schlüssel gültig bleibt, nachdem ein neuer generiert wurde. Der Standardwert ist 1440 Minuten (1 Tag).

**macKeySeed:** Ein Seed-Wert zum Generieren der sicheren URL. Wenn diese Option aktiviert ist, wird der Schlüssel nie aktualisiert. Das Festlegen des gleichen Seed auf verschiedenen Servern führt dazu, dass diese Server geschützte URLs generieren, die kompatibel sind. Das kann hilfreich sein, wenn mehrere Formularserver hinter einem Lastausgleich verwendet werden. Geben Sie eine zufällige Sequenz von Zeichen und Zahlen als Seed ein.

### Guides in einem Servercluster verwenden {#using-guides-in-a-server-cluster}

Das Rendern eines Guides in einem Servercluster, das persistente Sitzungsfehler mit einer NullPointerException verwendet. Eine Guide-Anforderung nutzt sichere URLs, die standardmäßig für den Server, auf dem sie generiert wurden, eindeutig sind. In einem Cluster, der persistente Sitzungen verwendet, werden, nachdem eine Anforderung an einen Knoten in dem Cluster gesendet wurde, alle nachfolgenden Anforderungen für die Sitzung oder den Benutzer ausschließlich auf diesen Server weitergeleitet. In dem Fall ist alles in Ordnung. In einem Cluster, der keine persistenten Sitzungen verwendet, können nachfolgende Anforderungen an einen beliebigen Server in dem Cluster gesendet werden. Wenn der Server, an den die Anforderungen gesendet werden, nicht der Originalserver ist, lösen sie die sichere URL nicht auf.

Wenn Sie Guides in einem Servercluster verwenden, der keine persistenten Sitzungen verwendet, legen Sie den macKeySeed-Wert für den GuidesUtility-Dienst fest und halten Sie anschließend den Cluster an und starten Sie ihn wieder.

Der macKeySeed-Wert ist der Seed-Wert für den Zufallszahlengenerator, der zum Generieren der sicheren URLs verwendet wird. Durch das Festlegen dieses Werts initialisiert jeder Clusterknoten den Zufallszahlengenerator auf die gleiche Weise. Außerdem hat jeder Clusterknoten Zugriff auf dieselben sicheren URLs. Sie können eine willkürliche Zeichenfolge für diesen Seed-Wert verwenden.

Ändern Sie den macKeySeed-Wert, wenn die sicheren URLs aktualisiert werden müssen. Das Aktualisieren der sicheren URLs hängt von der Sicherheitsrichtlinie ab und ähnelt der Aktualisierungsrichtlinie zum Ändern des Hauptstammkennworts des Servers. Der macSeedValue entspricht dem Hauptkennwort für die sicheren URLs, da er zum Generieren einer neuen eindeutigen Zufallszahl für die Generierung und für das Abrufen sicherer URLs verwendet wird.

Sie müssen den Cluster neu starten, da der macSeedValue beim Systemstart schreibgeschützt ist. Alle Knoten müssen zum Lesen des Werts neu gestartet werden, da sie ihn unabhängig voneinander verwenden, um ihre internen Zufallszahlen mit dem Seed-Wert zu initialisieren.

## Einstellungen des JDBC-Dienstes {#jdbc-service-settings}

Der JDBC-Dienst (`JdbcService`) ermöglicht Prozessen die Interaktion mit Datenbanken.

Folgende Einstellungen sind für den JDBC-Dienst verfügbar:

**datasourceName:** Ein Zeichenfolgenwert, der den JNDI-Namen der Datenquelle darstellt, die zum Herstellen einer Verbindung mit dem Datenbank-Server zu verwenden ist. Die Datenquelle muss auf dem Anwendungsserver definiert sein, der als Host des Formularservers dient. Der Standardwert ist der JNDI-Name der Datenquelle für die AEM Forms-Datenbank.

## Einstellungen des JMS-Dienstes {#jms-service-settings}

Der JMS-Dienst (`JMS`) ermöglicht die Interaktion mit JMS-Anbietern (Java Messaging System), die sowohl das Punkt-zu-Punkt-Messaging als auch das Veröffentlichen-/Abonnieren-Messaging implementieren.

Konfigurieren Sie den JMS-Dienst mit Standardeigenschaften, um für die Vorgänge des Dienstes Verbindungen und Interaktionen mit einem JMS-Anbieter und einem dazugehörigen JNDI-Dienst möglich sind. Die Werte der Diensteigenschaften werden basierend auf JBoss Application Server auf die Standardwerte festgelegt. Ändern Sie diese Werte, wenn Sie einen anderen Anwendungsserver als Host von AEM Forms verwenden.

Folgende Einstellungen sind für den JMS-Dienst verfügbar:

**Provider-URL:** Die URL des JNDI-Service-Anbieters. Der Standardwert basiert auf JBoss Application Server. Die folgenden URLs sind Standardwerte für die Anwendungsserver, die von AEM Forms unterstützt werden:

**JBoss:** `<server name>:1099`

**WebLogic:** `<server name>:7001`

**WebSphere:** `<server name>:2809`

**JNDI Username:** Der Benutzername des Kontos für die Authentifizierung bei dem JNDI-Service-Anbieter, der zum Nachschlagen von Warteschlangen- und Themennamen verwendet wird. Der Standardwert ist guest.

**JNDI Password:** Das Kennwort, das dem unter „JNDI-Benutzername“ angegebenen Benutzernamen zugeordnet ist. Der Standardwert ist guest.

**Initial Context Factory:** Die als ursprüngliche Kontext-Factory zu verwendende Java-Klasse. Der JMS-Dienst verwendet diese Klasse zum Erstellen eines anfängliches Kontextes, der als Ausgangspunkt zum Auflösen von Themen- und Warteschlangennamen dient. Der Standardwert ist die ursprüngliche Kontextfactory für den JMS-Dienst unter JBoss. Die folgenden Klassen sind die ursprünglichen Kontextfactorys für die Anwendungsserver, die von AEM Forms unterstützt werden:

**JBoss:** org.jnp.interfaces.NamingContextFactory

**WebLogic:** weblogic.jndi.WLInitialContextFactory

**WebSphere:** com.ibm.websphere.naming.WsnInitialContextFactory

**Connection Username:** Das Kennwort, das dem unter „Benutzername für Verbindung“ angegebenen Benutzernamen zugeordnet ist. Der Standardwert ist guest.

**Connection Password:** Das Kennwort, das dem unter „Benutzername für Verbindung“ angegebenen Benutzernamen zugeordnet ist. Der Standardwert ist guest.

**Other Properties:** Paare aus Eigenschaftenname und -wert, die an den JNDI-Service-Anbieter übergeben werden können. Diese Eigenschaften sind von der Implementierung und Konfiguration des verwendeten Anbieters abhängig. 

Die Paare aus Eigenschaftenname und -wert werden jeweils durch ein Semikolon **;** getrennt. Der folgende Text zeigt beispielsweise den Wert, der für zwei Eigenschaften namens „name1“ und „name2“ mit den Werten „value1“ und „value2“ angegeben wird: 

`name1=value1;name2=value2`

## Einstellungen des LDAP-Dienstes {#ldap-service-settings}

Der LDAP-Dienst (`LDAPService`) stellt Vorgänge zum Abfragen von LDAP-Ordnern bereit. LDAP-Ordner dienen meist zum Speichern von Informationen zu Personen, Gruppen und Diensten in einem Unternehmen.

Folgende Einstellungen sind für den LDAP-Dienst verfügbar:

**Initial Context Factory:** Die Java-Klasse, die als Kontext-Factory verwendet werden soll. Diese Klasse wird zum Herstellen einer Verbindung mit dem LDAP-Server verwendet. Der Standardwert ist com.sun.jndi.ldap.LdapCtxFactory und eignet sich für die meisten LDAP-Server.

**Provider URL:** Die URL, über die die Verbindung mit dem LDAP-Service hergestellt wird. Das Format des Werts ist `ldap://server name:port`

*Servername* steht für den Namen des Computers, der als Host für den LDAP-Server dient.

*Anschluss* steht für den Kommunikationsanschluss, der vom LDAP-Dienst verwendet wird. Der Standardwert ist 389, was dem für LDAP-Verbindungen verwendeten Standardanschluss entspricht.

**Benutzername:** Der Benutzername des Benutzerkontos, das für die Anmeldung beim LDAP-Server verwendet wird. Das Benutzerkonto muss über Berechtigungen für das Herstellen einer Verbindung mit dem Server sowie zum Lesen der Informationen im LDAP-Ordner verfügen.

Je nach LDAP-Server kann der Benutzername ein einfacher Benutzername wie `myname` sein oder ein DN wie `cn=myname,cn=users,dc=myorg`.

**Kennwort** Das Kennwort, das dem Benutzernamen zugeordnet ist, der in der Einstellung „Benutzername“ angegeben wurde.

**Andere Eigenschaften:** Ein Zeichenfolgewert, der andere Eigenschaften und ihre entsprechenden Werte, die Sie dem LDAP-Server zur Verfügung stellen können, darstellt. Der Wert hat folgendes Format:

`property=value;property=value;...`

## Einstellungen des Microsoft SharePoint-Konfigurationsdienstes {#microsoft-sharepoint-configuration-service-settings}

Mit dem Microsoft SharePoint-Konfigurationsdienst `(MSSharePointConfigService)` können Sie Anmeldedaten für den AEM Forms-Benutzer angeben, der über die Berechtigung zum Identitätswechsel verfügt. Weitere Informationen zu Berechtigungen für Identitätswechsel finden Sie unter[ Connector für Microsoft SharePoint konfigurieren](https://help.adobe.com/de_DE/AEMForms/6.1/SharePointConfig/index.html).

Folgende Einstellungen sind für den Microsoft SharePoint-Konfigurationsdienst verfügbar:

* Benutzername eines Benutzers mit der Berechtigung zum Identitätswechsel
* Kennwort für den oben genannten Benutzer

**SSL (HTTPS) aktivieren:**

**Gültigkeitsdauer:** Dauer in Sekunden, die dieses Bereitstellungsprofil gültig ist und auf dem Client zwischengespeichert wird. Der Standardwert ist 86400 (24 Stunden). Wenn eine Client-Anwendung mit dem Server synchronisiert und die angegebene Zeitspanne verstrichen ist, fordert die Client-Anwendung ein neues Bereitstellungsprofil vom Server an.

**Verschlüsselung:** Gibt an, ob die auf dem Mobilgerät gespeicherte Daten verschlüsselt werden sollen.

**Forms-Anwendung:** Aktiviert die Forms-Funktion in den mobilen Client-Anwendungen. Wenn diese Option ausgewählt ist, können Benutzer von ihren mobilen Geräten aus Formulare öffnen und Prozesse anstoßen.

**Aufgabenanwendung:** Aktiviert die Aufgabenfunktion in den mobilen Client-Anwendungen. Wenn diese Option ausgewählt ist, können die Benutzer von ihren mobilen Geräten aus auf ihre Aufgabenlisten zugreifen und Aufgaben erledigen.

**Content Services-Anwendung:** Aktiviert die Content Services-Funktion in der mobilen Client-Anwendung. Diese Funktion ist nur für iOS verfügbar. Wenn diese Option ausgewählt ist, können iPhone- und iPad-Benutzer auf Dateien zugreifen, die auf dem WebDAV-Server Ihrer Organisation gespeichert sind.

**Offline-Unterstützung:** Ermöglicht es den Benutzern, die mobilen Client-Anwendungen auch dann zu nutzen, wenn sie keine Verbindung zum Server haben ( beispielsweise, wenn sie sich außerhalb des Mobilfunkbereichs oder im Flugzeugmodus befinden). Benutzer müssen außerdem die Einstellung Offline-Support auf ihren Mobilgeräten aktivieren. Diese Funktion ist für Android- und iOS-Geräte verfügbar. Standardmäßig ist diese Funktion deaktiviert.

>[!NOTE]
>
>Wenn die Offline-Unterstützung aktiviert ist und Sie sie dann deaktivieren, werden die Bereitstellungsprofile der Benutzer sofort aktualisiert, oder sobald sie online sind. Wenn ein Benutzer offline gearbeitet hat, werden alle ausstehenden Aufgaben in ihre Aufgabenliste zurückgestellt und alle Elemente in ihrer Warteschlange, einschließlich ausstehender Formulare, Aufgaben und Formulare mit Überprüfungsfehlern, werden aus der Warteschlange gelöscht.

**Android:** Ermöglicht Android-Geräten eine Verbindung zum Server herzustellen.

**Apple iOS:** Ermöglicht iPhones und iPads eine Verbindung zum Server herzustellen.

**AIR:** Ermöglicht Geräten, auf denen auf Adobe AIR® basierende Anwendungen ausgeführt werden, eine Verbindung zum Server herzustellen.

**BlackBerry:** Ermöglicht BlackBerry-Geräten eine Verbindung zum Server herzustellen.

**Android Microsoft Exchange ActiveSync erforderlich:** Gibt an, ob der Microsoft Exchange ActiveSync Policy Manager (EAS) auf Android-Geräten installiert und aktiv sein muss. Wenn diese Option ausgewählt ist, muss EAS auf dem Android-Gerät erzwungen werden. Wenn diese Option nicht ausgewählt ist, wird keine Prüfung durchgeführt, obwohl die anderen Anforderungen weiterhin erfüllt werden.

**Android-PIN-Mindestlänge:** Android-Geräte müssen über eine globale Einstellung verfügen, die erzwingt, dass die PIN oder das Kennwort mindestens diese Länge aufweist. Es reicht nicht aus, nur eine PIN mit der angegebenen Länge zu haben. Die PIN-Länge muss vom System erzwungen werden, damit Benutzer die PIN nicht später entfernen oder verkürzen können. Der Standardwert ist 4.

**Maximale Kennwortwiederholungen für Android vor dem Löschen:** Android-Geräte verfügen über eine globale Einstellung, die das System nach einer bestimmten Anzahl von ungültigen Passwortversuchen löscht. Diese globale Einstellung ist aktiviert und ist gleich oder niedriger als der hier angegebene Wert. Der Standardwert ist 5.

**Android Löschen bei Entfernung:** Legt fest, was passiert, wenn eine Richtlinienverletzung auf einem Android-Gerät auftritt. Wenn diese Option ausgewählt ist, wird das Konto gelöscht. Wenn diese Option nicht ausgewählt ist, werden das gespeicherte Kontokennwort und die zwischengespeicherten Daten gelöscht. Es werden keine weiteren Synchronisierungsversuche unternommen, bis der Benutzer den Richtlinienverstoß behoben hat.

## Einstellungen des Output-Dienstes {#output-service-settings}

Der Output-Dienst `(OutputService)` ermöglicht es Ihnen, XML-Formulardaten mit einem in AEM Forms Designer erstellten Formularentwurf zusammenzuführen, um einen Dokumentausgabe-Stream in einem der folgenden Formate zu erstellen:

* PDF- oder PDF/A-Dokumentausgabestream
* Adobe PostScript-Ausgabestream
* PCL-Ausgabestream (Printer Control Language)
* ZPL-Ausgabestream (Zebra Programming Language)

Der Ausgabestream kann an einen Netzwerkdrucker, an einen lokalen Drucker oder in eine Datei auf einem Datenträger gesendet werden. Wenn Sie den Output-Dienst innerhalb eines Prozesses nutzen, können Sie den Ausgabestream auch als Dateianlage an einen E-Mail-Empfänger senden.

Folgende Einstellungen sind für den Output-Dienst verfügbar:

**Transaktionstyp**: Gibt an, wie ein Transaktionskontext an einen Vorgang weitergegeben werden soll:

**Erforderlich**: Ein Transaktionskontext wird unterstützt, wenn bereits einer vorhanden ist. Andernfalls wird ein neuer Transaktionskontext erstellt. Dies ist der Standardwert.

**Neu Erforderlich**: Es wird immer ein Transaktionskontext erstellt. Wenn bereits ein aktiver Transaktionskontext vorhanden ist, wird dieser ausgesetzt.

**Transaktionszeitlimit (in Sek.)**: Die Anzahl der Sekunden, die der zugrunde liegende Transaktionsanbieter wartet, bevor eine Transaktion rückgängig gemacht wird, die diesen Vorgang beinhaltet. Dieser Wert wird ignoriert, wenn ein vorhandener Transaktionskontext weitergegeben wird.

Bei Verarbeitung großer Datendateien oder Betrieb auf einem ausgelasteten Server kann es notwendig sein, den Zeitlimitwert für den Output-Dienst zu erhöhen. Um den Zeitlimitwert zu ändern, stellen Sie sicher, dass Hardwareserver über ausreichenden Arbeitsspeicher verfügen und dass der Arbeitsspeicher für den Java Application Server-Heap-Speicher verfügbar ist. Der Standardwert ist `180`.

## Einstellungen des PDFG Config-Dienstes {#pdfg-config-service-settings}

Folgende Einstellungen sind für den PDFG Config-Dienst (`PDFGConfigService`) verfügbar:

**Ordner für Benutzerauftragsoptionen**: Der Pfad des Dateisystemordners, in den der C-Service die Auftragsoptionendateien schreibt, auf die Acrobat Pro Extended zugreifen kann. Der Standardwert ist [Benutzer.Basisordner]/Application Data/Adobe/Adobe PDF/Settings.

**PS-Startordner**: Der Pfad des Dateisystemordners, in dem die für Adobe Acrobat Distiller erforderlichen Startdateien gespeichert werden. Der Standardwert ist [Benutzer.Basisordner]/Application Data/Adobe/Adobe PDF/Distiller/Startup.

**PS-Startdatei**: Der Name der für Adobe Acrobat Distiller erforderlichen Startdatei. Der Standardwert ist example.ps.

**Konvertierungszeitlimit für Server:** Das maximale Zeitlimit für die Auftragskonvertierung (in Sekunden) für den Generate PDF-Service und den Distiller-Service. Diese Einstellung beschränkt den maximalen Konvertierungstimeout-Wert, der in der Datei „config.xml“ sowie auf den Administration Console-Seiten für PDF Generator angegeben werden kann. Der Standardwert ist 270.

**Globales Zeitlimit für Server**: Bei der Durchführung von PDF-Konvertierungen berücksichtigt ein Formular-Server dieses Zeitlimit. Konfigurieren Sie den Timeoutwert, um das Problem zu lösen.

**Auftragsoptionenpräfix**: Ein Präfix, das vom Generate PDF-Service verwendet wird, um den Auftragsoptionendateien, die vorübergehend für die Verwendung durch Acrobat Distiller erstellt werden, eine kurze Zeichenfolge voranzustellen. Der Standardwert ist pdfg.

**Nicht-Unicode-Programme**: Eine durch Kommata getrennte Liste von Programmnamen, von denen bekannt ist, dass sie Unicode nicht unterstützen. Diese Liste enthält bereits die Namen einer Reihe von Anwendungen, für die die Unterstützung in PDF Generator vorkonfiguriert ist. Wenn Sie die Unterstützung von PDF-Konvertierungen durch weitere Anwendungen von Drittanbietern ermöglichen möchten, die Unicode nicht unterstützen, müssen Sie sie dieser Liste hinzufügen. Der Standardwert ist Autocad,Excel,PowerPoint,Project,Publisher,Visio,Word,WordPerfect.

**Threadpool-Größe für Server**: Steuert die Größe des Threadpools, den der Generate PDF-Service intern verwendet, um Konvertierungsanforderungen von HTML in PDF zu bearbeiten, die Spidering beinhalten (Konvertierung von verlinkten Seiten, die von der Hauptseite aus zugänglich sind). Der Standardwert ist 20.

**PDFG-Bereinigungsprüfung (Sekunden)**: Weitere Informationen finden Sie im Abschnitt „Auftragsablauf (Sekunden)“.

**Auftragsablauf (Sekunden)**: Der Generate PDF-Service löscht Eingabedateien, sobald sie konvertiert sind. Der Dienst speichert Ausgabedateien temporär für einen Zeitraum, der von den Einstellungen in „PDFG-Bereinigungsprüfung (Sekunden)“ und „Auftragsablauf (Sekunden)“ bestimmt wird. 

Die Einstellung „Auftragsablauf (Sekunden)“ gibt an, wie alt Dateien oder leere Ordner sein müssen, bevor sie gelöscht werden können. Die Einstellung „PDFG-Bereinigungsprüfung (Sekunden)“ gibt an, wie oft ein Bereinigungsthread die temporären Ordner auf zu löschende Dateien überprüft. 

Wenn beispielsweise die Einstellung „Auftragsablauf (Sekunden)“ auf den Wert 100 festgelegt ist und die Einstellung „PDFG-Bereinigungsprüfung (Sekunden)“ auf den Wert 200, wird der Bereinigungsthread alle 200 Sekunden ausgeführt und löscht Dateien, die 100 Sekunden oder älter sind.

Der Standardwert von „PDFG-Bereinigungsprüfung (Sekunden)“ ist `43200` (12 Stunden). Der Standardwert von „Auftragsablauf (Sekunden)“ ist `86400` (24 Stunden).

**Standardgebietsschema**: Wird zum Außerkraftsetzen des Standardgebietsschemas (Land und Sprache) für den Server verwendet, auf dem der Generate PDF-Service bereitgestellt wird. Wenn dieser Parameter nicht angegeben ist, wird das Standardgebietsschema über das Betriebssystem ermittelt, unter dem der Dienst bereitgestellt ist. Dieser Parameter steuert die Sprache, in der Fehlermeldungen an die APIs zurückgegeben werden.

## Data Services-Diensteinstellungen für den Arbeitsablauf für Formulare {#forms-workflow-data-services-service-settings}

Die folgenden Dienste erweitern Data Services und stellen Assembler bereit, die von Workspace für die Kommunikation mit dem Server verwendet werden. Ändern Sie die Konfigurationsoptionen für diese Dienste nicht, es sei denn, Sie werden von Adobe Support entsprechend angewiesen. Diese Dienste sind nicht für den direkten Zugriff vorgesehen:

* `ProcessManagementLcdsAttachmentService`
* `ProcessManagementLcdsPropertyService`
* `ProcessManagementLcdsTaskService`

## Einstellungen des Remoting-Dienstes {#remoting-service-settings}

Die meisten Dienste sind so konfiguriert, dass Sie mit AEM Forms Remoting (nicht mehr unterstützt für AEM Forms) auf diese Dienste zugreifen können. Weitere Informationen zu AEM Forms Remoting (nicht mehr unterstützt für AEM Forms) finden Sie unter [mit AEM Forms.](https://adobe.com/go/learn_aemforms_programming_63_de)

Folgende Einstellungen sind für den Remoting-Dienst verfügbar:

**Flex-Client-Authentifizierungsmethode**: Bestimmt den Typ der Antwort, die der Server zum Client zurücksendet, wenn die Sicherheit für den aufgerufenen Service aktiviert ist, der Vorgang keine anonymen Aufrufe unterstützt und der Client keine oder ungültige Anmeldeinformationen übergibt. Sie können zwischen „Benutzerdefiniert“ und „Standard“ wählen. Der Standardwert ist Standard.

**Serialisierung nicht serialisierbarer Klassen zulassen**: Die meisten Endpunkte von AEM Forms erlauben nur die Verwendung von serialisierbaren Klassen für den Aufruf. In älteren Versionen ermöglichte der Remoting-Endpunkt die Verwendung von nicht serialisierbaren Klassen für den Aufruf von Flex-basierten Clients. Um zu verhindern, dass eine Sicherheitslücke wie unter APS11-15 beschrieben auftritt, wurde dies geändert. Wenn Sie weiterhin nicht serialisierbare Klassen mit dem Flex-Remoting-Endpunkt verwenden möchten, wählen Sie dieses Kontrollkästchen aus.

## Einstellungen des Repository-Dienstes {#repository-service-settings}

Der Repository-Dienst (`RepositoryService`) stellt Dienste für die Ressourcenspeicherung und -verwaltung in AEM Forms bereit. Wenn ein Entwickler eine Anwendung erstellt, kann er die Elemente im Repository statt in einem Dateisystem bereitstellen. Die Elemente können alle Typen von Zusätzen umfassen, darunter XML-Formulare, PDF-Formulare (einschließlich Acrobat-Formularen), Formularfragmente, Bilder, Profile, Richtlinien, SWF-Dateien, DDX-Dateien, XML-Schemas, WSDL-Dateien und Testdaten.

Sie können das in AEM Forms enthaltene Standard-Repository oder das Repository eines Drittanbieters (EMC Documentum Content Server, IBM FileNet Content Manager oder IBM Content Manager) verwenden.

Der Repository Provider-Dienst ist ein Dienststellvertreter, der als Schnittstelle zu einem Anbieterdienst fungiert. Dies ermöglicht das Herstellen einer Verbindung mit einer allgemeinen API, wobei Sie nicht wissen müssen, von welchem Anbieterdienst die Speicherfunktionen implementiert werden. Der Repository Provider-Dienst stellt Datenbankspeicher für die Ressourcen des Repository-Dienstes bereit.

Folgende Einstellung ist für den Repository-Dienst verfügbar:

**Provider-Dienst:** Der Name des Dienstes, der als Speicheranbieter verwendet wird. Der Standardwert ist RepositoryProviderService.

## Einstellungen des Signature-Dienstes {#signature-service-settings}

Der Signature-Dienst (`SignatureService`) ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Dienst verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass Dokumente nicht geändert werden. Das Ändern eines Dokuments macht die Signatur ungültig. Da Sicherheitsfunktionen für das Dokument selbst aktiviert werden, bleibt das Dokument für seine gesamte Nutzungsdauer geschützt, so auch außerhalb der Firewall, wenn es offline heruntergeladen oder zurück an Ihr Unternehmen gesendet wird.

Folgende Einstellungen sind für den Signature-Dienst verfügbar:

**Name des Remote-HSM-SPI-Dienstes:** Diese Option ist zu verwenden, wenn das HSM auf einem Remote-Computer installiert ist. Legen Sie diese Option fest, wenn AEM Forms auf einem 64-Bit-Windows-Gerät installiert ist und Sie HSM-Geräte zum Signieren verwenden.

**URL des Remote-HSM-Webdienstes:** Geben Sie diese Option an, wenn AEM Forms unter 64-Bit-Windows installiert ist und Sie HSM-Geräte zum Signieren verwenden.

**Zertifizierung zum Einschließen von Änderungen beim Laden von Formularen:** Wenn diese Option ausgewählt ist, wird der XFA-Formularstatus zusätzlich zur XFA-Vorlage zertifiziert. Beachten Sie, dass die Aktivierung dieser Option negative Auswirkungen auf die Leistung haben kann. Der Standardwert lautet true.

**Dokument-JavaScript-Skripte ausführen:** Gibt an, ob Dokument-JavaScript-Skripte bei Signaturvorgängen ausgeführt werden sollen. Der Standardwert lautet false.

**Dokumente mit Acrobat 9-Kompatibilität verarbeiten:** Legt fest, ob die Kompatibilität mit Acrobat 9 aktiviert werden soll. Wenn diese Option ausgewählt wird, ist beispielsweise „Sichtbare Zertifizierung in dynamischen PDFs“ aktiviert. Der Standardwert lautet false.

**Widerrufsinformationen beim Signieren einbetten:** Gibt an, ob die Widerrufsinformationen beim Signieren des PDF-Dokuments eingebettet werden. Der Standardwert lautet false.

**Widerrufsinformationen beim Zertifizieren einbetten:** Gibt an, ob die Widerrufsinformationen beim Zertifizieren des PDF-Dokuments eingebettet werden. Der Standardwert lautet false.

**Einbetten von Sperrinformationen für alle Zertifikate während der Signierung/Zertifizierung erzwingen:** Gibt an, ob ein Signierungs- oder Zertifizierungsvorgang abgebrochen werden soll, wenn keine gültigen Sperrinformationen für alle Zertifikate eingebettet sind. Beachten Sie, dass ein Zertifikat, das keine Zertifikatsperrlisten- oder Online-Zertifikatstatusprotokoll-Informationen enthält, als gültig angesehen wird, auch wenn keine Sperrinformationen abgerufen werden. Der Standardwert lautet false.

**Reihenfolge der Sperrüberprüfungen:** Gibt die Reihenfolge der Sperrüberprüfungen an, wenn das Prüfen über die Mechanismen sowohl für Zertifikatsperrlisten (CRL) als auch für das Online-Zertifikatstatusprotokoll (OCSP) möglich ist. Der Standardwert ist OCSPFirst.

**Maximale Größe der archivierten Sperrinformationen:** Die maximale Größe der archivierten Sperrinformationen in KB. AEM Forms versucht, so viele Sperrinformationen wie möglich zu speichern, ohne diesen Grenzwert zu überschreiten. Der Standardwert ist 10 KB.

**Unterstützen von Signaturen, die mit Pre-Release-Builds von Adobe-Produkten erstellt wurden:** Wenn diese Option aktiviert ist, wird eine Signatur, die mit einem Pre-Release-Build eines Adobe-Produkts erstellt wurde, trotzdem ordnungsgemäß validiert. Der Standardwert lautet false.

**Option Zeitpunkt für die Überprüfung:** Gibt den Zeitpunkt für die Überprüfung des Zertifikats eines Signierers an. Der Standardwert ist „Secure Time Else Current Time“.

**In Signatur archivierte Sperrinformationen für die Validierung verwenden:** Gibt an, ob die in der Signatur archivierten Sperrinformationen zur Sperrprüfung verwendet werden sollen. Der Standardwert lautet true.

**Verwendung der im Dokument gespeicherten Validierungsinformationen für die Validierung von Signaturen:** Wenn diese Option aktiviert ist, werden die im Dokument eingebetteten Validierungsinformationen (einschließlich Sperr- und Zeitstempelinformationen) zum Validieren von Signaturen verwendet. Der Standardwert lautet true.

**Maximale zulässige Anzahl verschachtelter Überprüfungssitzungen:** Die maximale Anzahl verschachtelter Überprüfungssitzungen, die zulässig ist. AEM Forms verhindert mithilfe dieses Wertes die Entstehung einer Endlosschleife bei der Überprüfung der OCSP- bzw. Zertifikatsperrlisten-Signiererzertifikate, wenn das OCSP- bzw. Zertifikatsperrlistenzertifikat nicht ordnungsgemäß eingerichtet ist. Der Standardwert ist 10.

**Maximal zulässige Zeitabweichung für die Überprüfung:** Die maximale Anzahl an Minuten, um welche die Signaturzeit hinter der Validierungszeit liegen kann. Wenn die Uhrzeitabweichung diesen Wert überschreitet, ist die Signatur nicht gültig. Der Standardwert ist 65 Minuten.

**Gültigkeitsdauer des gecachten Zertifikats:** Gibt die Gültigkeitsdauer eines Zertifikats im Cache an, das online oder auf andere Weise abgerufen wurde. Der Standardwert ist 1 Tag.

### Transportoptionen {#transport-options}

**Proxy-Host:** Die URL des Proxy-Hosts. Wird nur verwendet, wenn ein gültiger Wert angegeben ist. Kein Standardwert.

**Proxy-Port:** Der Proxy-Port. Geben Sie eine gültige Anschlussnummer zwischen 0 und 65535 ein. Der Standardwert ist 80.

**Proxy-Login Benutzername:** Der Benutzername für die Proxy-Anmeldung. Wird nur verwendet, wenn gültige Werte für den Proxyhost und den Proxyanschluss angegeben wurden. Kein Standardwert.

**Proxy-Login Kennwort:** Das Passwort für die Proxy-Anmeldung. Wird nur verwendet, wenn gültige Werte für den Proxyhost, den Proxyanschluss und den Benutzernamen für die Proxyanmeldung angegeben wurden. Kein Standardwert.

**Obergrenze für Downloads:** Die maximal zulässige Datenmenge in MB, die pro Verbindung empfangen werden kann. Der Mindestwert ist 1 MB, der Höchstwert 1.024 MB. Der Standardwert lautet 16 MB.

**Zeitüberschreitung der Verbindung:** Gibt die maximale Zeit in Sekunden an, die gewartet werden soll, bevor eine neue Verbindung aufgebaut wird. Der Mindestwert ist 1, der Höchstwert 300. Der Standardwert ist 5.

**Socket-Zeitüberschreitung:** Die maximale Wartezeit, in Sekunden, bevor eine Socket-Zeitüberschreitung (beim Warten auf eine Datenübertragung) auftritt. Der Mindestwert ist 1, der Höchstwert 3600. Der Standardwert ist 30.

### Pfadüberprüfungsoptionen {#path-validation-options}

**Spezielle Richtlinie verlangen:** Gibt an, ob der Pfad für mindestens eine der Zertifikatrichtlinien gültig sein muss, die dem trust Anchor des Signiererzertifikats zugeordnet sind. Der Standardwert lautet false.

**JEDE Richtlinie unterbinden:** Gibt an, ob die Richtlinien-Objektkennung (OID) verarbeitet werden soll, wenn sie in einem Zertifikat enthalten ist. Der Standardwert lautet false.

**Richtlinienzuordnung unterbinden:** Gibt an, ob Richtlinienzuordnung im Zertifizierungspfad zulässig ist. Der Standardwert lautet false.

**Alle Pfade überprüfen:** Gibt an, ob alle Pfade überprüft werden sollen oder ob die Überprüfung nach Finden des ersten gültigen Pfades beendet werden soll. Wählen Sie „true“ oder „false“ aus. Der Standardwert lautet false.

**LDAP-Server:** Der zum Suchen von Zertifikaten bei der Pfadüberprüfung verwendete LDAP-Server. Kein Standardwert.

**URIs in Zertifikat-AIA folgen:** Gibt an, ob in der Zertifikat-AIA enthaltene URIs (Uniform Resource Identifiers) während der Pfadsuche verarbeitet werden sollen. Der Standardwert lautet false.

**Grundlegende Einschränkungserweiterung in CA-Zertifikaten erforderlich:** Gibt an, ob die grundlegende Einschränkungserweiterung für Zertifikate der Zertifizierungsstelle (CA) für CA-Zertifikate vorhanden sein muss. Einige frühere deutsche zertifizierte Stammzertifikate (7 und früher) sind nicht RFC 3280-konform und enthalten keine grundlegende Einschränkungserweiterung. Wenn bekannt ist, dass ein EE-Zertifikat eines Benutzers an einen solchen deutschen Stamm verkettet ist, deaktivieren Sie dieses Kontrollkästchen. Der Standardwert lautet true.

**Gültige Zertifikatsignatur während der Kettenbildung erforderlich:** Gibt an, ob der Kettengenerator gültige Signaturen für Zertifikate erfordert, aus denen Ketten erzeugt werden. Wenn dieses Kontrollkästchen aktiviert ist, erzeugt der Kettengenerator keine Ketten mit ungültigen RSA-Signaturen aus Zertifikaten. Betrachten Sie die Kette „CA > ICA > EE“, bei der die Signatur der Zertifizierungsstelle (CA) für eine ICA ungültig ist. Wenn diese Einstellung „true“ ist, wird die Kettenbildung an der ICA beendet und die CA wird nicht in die Kette aufgenommen. Ist sie dagegen „false“, wird die vollständige Kette aus 3 Zertifikaten erzeugt. Diese Einstellung hat keine Auswirkungen auf DSA-Signaturen. Der Standardwert lautet false.

### Zeitstempelanbieter-Optionen {#timestamp-provider-options}

**TSP Server URL:** Die URL des Zeitstempel-Standardanbieters. Wird nur verwendet, wenn ein gültiger Wert angegeben ist. Kein Standardwert.

**TSP Server Username:** Der Benutzername, falls vom Zeitstempelanbieter benötigt. Wird nur verwendet, wenn ein gültiger Wert für die URL angegeben wurde. Kein Standardwert.

**TSP Server Password:** Das Kennwort für den oben angegebenen Benutzernamen, wenn vom Zeitstempelanbieter angefordert. Wird nur verwendet, wenn gültige Werte für die URL und den Benutzernamen angegeben wurden. Kein Standardwert.

**Request Hash Algorithm:** Gibt den Hash-Algorithmus an, der beim Erstellen der Anforderung für den Zeitstempelanbieter zu verwenden ist. Der Standardwert ist SHA1.

**Revocation Check Style:** Gibt die Methode zur Prüfung von Sperren an, die zum Ermitteln des Vertrauensstatus für das Zertifikat des Zeitstempelanbieters aus dessen festgestelltem Sperrstatus verwendet wird. Der Standardwert ist „BestEffort“. 

**Send Nonce:** Gibt an, ob eine Nonce mit der Zeitstempelanbieter-Anforderung gesendet werden soll. Eine Nonce kann ein Zeitstempel, ein Besucherzähler auf einer Webseite oder eine spezielle Kennzeichnung zur Begrenzung oder Verhinderung der nicht autorisierten Wiedergabe oder Vervielfältigung einer Datei sein. Der Standardwert lautet true.

**Abgelaufene Zeitstempel während der Validierung verwenden:** Wenn diese Option aktiviert ist, können abgelaufene Zeitstempel verwendet werden, um die Validierungszeiten von Signaturen abzurufen. Der Standardwert lautet true.

**Größer der TSP-Antwort:** Geschätzte Größe der TSP-Antwort in Byte. Dieser Wert muss der maximalen Größe der Zeitstempelantwort entsprechen, die vom konfigurierten Zeitstempelanbieter zurückgegeben werden kann. Ändern Sie diesen Wert nur, wenn Sie sich absolut sicher sind. Der Mindestwert ist „60B“, der Höchstwert 10240B. Der Standardwert ist 4096B.

**Zeitstempel-Server-Erweiterung ignorieren**: Wählen Sie **Zeitstempel-Server-Erweiterung ignorieren**, damit AEM Forms-Server keinen Kontakt mit dem angegebenen Zeitstempelserver aufnehmen kann. die Auswahl der Option verhindert Prozessausfälle, die aufgrund von Verbindungs-Timeout zwischen AEM Forms- und Zeitstempelservern stattfinden.

### Zertifikatsperrlisten-Optionen {#certificate-revocation-list-options}

**Lokaler URI zuerst konsultieren:** Gibt an, ob der unter „Lokaler URI für die Zertifikatsperrlisten-Suche“ angegebene Zertifikatsperrlisten-Speicherort beim Prüfen von Sperren Vorrang vor jedem in einem Zertifikat angegebenen Speicherort haben soll. Der Standardwert lautet false.

**Lokaler URI für die CRL-Suche:** URL des lokalen Zertifikatsperrlisten-Anbieters. Dieser Wert wird nur verwendet, wenn der oben angegebene Parameter „Zuerst lokalen URI prüfen“ auf „true“ festgelegt ist. Kein Standardwert.

**Methode zur Prüfung von Sperren:** Gibt die Methode zur Prüfung von Sperren an, die zum Ermitteln des Vertrauensstatus für das Zertifikat des Zertifikatsperrlisten-Anbieters aus dessen festgestelltem Sperrstatus verwendet werden soll. Der Standardwert ist „BestEffort“. 

**LDAP-Server für CRL-Suche:** Der zum Abrufen der Zertifikatsperrlisten zu verwendende LDAP-Server (wie www.ldap.com). Alle DN-basierten Abfragen nach Zertifikatsperrlisten werden an diesen Server gerichtet. Kein Standardwert.

**Online gehen:** Gibt an, ob zum Abrufen einer Zertifikatsperrliste online gegangen werden soll. Bei der Einstellung „false“ werden nur zwischengespeicherte Zertifikatsperrlisten (auf dem lokalen Datenträger oder solche mit eingebetteter Signatur) herangezogen. Der Standardwert lautet true.

**Gültigkeitszeiten ignorieren:** Gibt an, ob die Uhrzeiten „thisUpdate“ und „nextUpdate“ der Antwort ignoriert werden sollen, um so jegliche negative Auswirkung dieser Uhrzeiten auf die Gültigkeit der Antwort zu verhindern. Der Standardwert lautet false.

**AKI-Endung bei CRL verlangen:** Gibt an, ob die Endung für die Identifikationsnummer der Behörde in einer Zertifikatsperrliste enthalten sein muss. Der Standardwert lautet false.

### OCSP-Optionen (Online Certificate Status Protocol) {#online-certificate-status-protocol-options}

**OCSP-Server-URL:** URL für den standardmäßigen OCSP-Server. Ob der über diese URL angegebene OCSP-Server verwendet wird, hängt von der Einstellung der „Zu verwendender URL“-Option ab. Kein Standardwert.

**Option zu prüfende URLs:** Steuert die Liste und Reihenfolge der OCSP-Server, die zum Durchführen der Statusprüfung verwendet werden. Der Standardwert ist „UseAlAlnCert“. 

**Methode zur Sperrprüfung:** Gibt die Methode zur Prüfung von Sperren an, die zum Überprüfen des Zertifikats für den OCSP-Server verwendet werden sollen. Der Standardwert ist „CheckIfAvailable“. 

**Nonce senden:** Gibt an, ob eine Nonce mit der OCSP-Anforderung gesendet werden soll. Eine Nonce kann ein Zeitstempel, ein Besucherzähler auf einer Webseite oder eine spezielle Kennzeichnung zur Begrenzung oder Verhinderung der nicht autorisierten Wiedergabe oder Vervielfältigung einer Datei sein. Der Standardwert lautet true.

**Maximale Uhrzeit-Abweichung:** Maximal zulässige Abweichung in Minuten zwischen der Antwortzeit und der lokalen Zeit. Der Mindestwert ist 0, der Höchstwert 2147483647m. Der Standardwert ist 5m.

**Maximale Zeit für die Antwort:** Legt die maximale Zeit in Minuten fest, für die eine zuvor erzeugte OCSP-Antwort als gültig gilt. Der Mindestwert ist 1m, der maximal zulässige Höchstwert 2147483647. Der Standardwert ist 525600 (ein Jahr).

**OCSP-Anfrage signieren:** Gibt an, ob die OCSP-Anforderung signiert werden soll. Der Standardwert lautet false.

**Berechtigungsalias des Signierers anfordern**: Gibt den Berechtigungsalias an, der zum Signieren der OCSP-Anforderung verwendet werden soll, wenn das Signieren aktiviert ist. Wird nur verwendet, wenn das Signieren von OCSP-Anforderungen aktiviert ist. Kein Standardwert.

**Online gehen**: Gibt an, ob für die Sperrprüfung online gegangen werden soll. Der Standardwert lautet true.

**Update-Zeiten der Antwort ignorieren**: Gibt an, ob die Uhrzeiten „thisUpdate“ und „nextUpdate“ der Antwort ignoriert werden sollen, um so jegliche negative Auswirkung dieser Uhrzeiten auf die Gültigkeit der Antwort zu verhindern. Der Standardwert lautet false.

**OCSPNoCheck-Erweiterung zulassen**: Gibt an, ob die Erweiterung „OCSPNoCheck“ im Signierzertifikat der Antwort zulässig ist. Der Standardwert lautet true.

**OCSP ISIS-MTT CertHash-Erweiterung anfordern**: Gibt an, ob eine Hash-Erweiterung des Zertifikats mit öffentlichem Schlüssel in OCSP-Antworten enthalten sein muss. Der Standardwert lautet false.

### Fehlerbehandlungsoptionen für das Debugging {#error-handling-options-for-debugging}

**Zertifikatcache beim nächsten API-Aufruf bereinigen**: Gibt an, ob der Zertifikatcache beim Aufruf des nächsten Signature Service-Vorgangs bereinigt werden soll. Im Anschluss an den Aufruf des Vorgangs wird die Option wieder auf „false“ festgelegt. Der Standardwert lautet false.

**Purge CRL Cache on next API call:** Gibt an, ob der Zertifikatsperrlisten-Cache beim Aufruf des nächsten Signature-Service-Vorgangs bereinigt werden soll. Im Anschluss an den Aufruf des Vorgangs wird die Option wieder auf „false“ festgelegt. Der Standardwert lautet false.

**Purge OCSP Cache on next API call:** Gibt an, ob der OCSP-Cache beim Aufruf des nächsten Signature-Service-Vorgangs bereinigt werden soll. Im Anschluss an den Aufruf des Vorgangs wird die Option wieder auf „false“ festgelegt. Der Standardwert lautet false.

## Einstellungen des Watched Folder-Dienstes {#watched-folder-service-settings}

Der Watched Folder-Dienst (`WatchedFolder`) konfiguriert gemeinsame Attribute für alle Endpunkte überwachter Ordner. Der Dienst stellt außerdem Standardwerte für die Endpunkte überwachter Ordner bereit. (Siehe [Endpunkte für überwachte Ordner konfigurieren](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#configuring-watched-folder-endpoints).) Er wird weder durch externe Client-Anwendungen aufgerufen noch in Prozessen verwendet, die in Workbench erstellt werden.

Folgende Einstellungen sind für den Watched Folder-Dienst verfügbar:

**Cron-Ausdruck:** Der Cron-Ausdruck, wie er von Quartz zur zeitlichen Planung des Abrufs des Eingabeordners verwendet wird.

**Anzahl der Wiederholungen:** Die Häufigkeit, mit der der Eingabeordner abgerufen wird. Der Standardwert für die Anzahl der Wiederholungen, der verwendet wird, wenn in der Endpunktkonfiguration kein Wert angegeben ist. Ein Wert von „-1“ bedeutet uneingeschränktes Überprüfen des Ordners („unendlich“). Der Standardwert ist -1.

**Wiederholungsintervall:** Die Standardanzahl von Sekunden zwischen den einzelnen Abrufen. Dieser Wert wird als Wiederholungsintervall verwendet, sofern in der Endpunktkonfiguration für den überwachten Ordner kein anderer Wert angegeben ist. Der Standardwert ist 5. Weitere Informationen finden Sie in der Beschreibung der Einstellung „Stapelgröße“.

**Asynchron:** Gibt den Aufruftyp als „asynchron“ oder „synchron“ an. Transiente und synchrone Prozesse können nur synchron aufgerufen werden. Der Standardwert ist „asynchron“.

**Wartezeit:** Der Standardwert für den Zeitraum in Sekunden, nach dem die Dateien aus den Eingabeordnern abgerufen werden. Wenn Dateien oder Ordner älter sind als die in „Wartezeit“ angegebene Zeit, werden sie zur Verarbeitung abgerufen. Der Standardwert ist 0.

**Batch-Größe:** Der Standardwert für die Anzahl der Dateien oder Ordner, die pro Überprüfung verarbeitet werden. Der Standardwert ist 2.

Die Einstellungen für Wiederholungsintervall und Stapelgröße bestimmen, wie viele Dateien bei jeder Überprüfung vom Watched Folder-Dienst ausgewählt werden. Der Watched Folder-Dienst verwendet einen Quartz-Threadpool, um den Eingabeordner zu überprüfen. Der Threadpool wird mit anderen Diensten gemeinsam verwendet. Wenn das Überprüfungsintervall kurz ist, wird der Eingabeordner häufig von den Threads überprüft. Falls häufig Dateien im überwachten Ordner abgelegt werden, sollten Sie ein kurzes Überprüfungsintervall wählen. Wenn Dateien nicht häufig abgelegt werden, verwenden Sie ein größeres Überprüfungsintervall, damit die anderen Dienste die Threads verwenden können. 

Falls eine große Anzahl von Dateien abgelegt wird, wählen Sie eine große Stapelgröße. Wenn beispielsweise der vom Endpunkt des Typs „überwachter Ordner“ aufgerufene Dienst 700 Dateien pro Minute verarbeiten kann und die Benutzer Dateien mit derselben Rate im Eingabeordner ablegen, verbessert das Festlegen der Stapelgröße auf 350 und des Wiederholungsintervalls auf 30 Sekunden die Leistung des Watched Folder-Dienstes, ohne dass der überwachte Ordner allzu häufig überprüft werden muss.

Wenn Dateien im überwachten Ordner abgelegt werden, werden die Dateien in der Eingabe aufgelistet. Dadurch kann die Leistung reduziert werden, wenn jede Sekunde eine Überprüfung stattfindet. Durch Erhöhen des Überprüfungsintervalls kann die Leistung verbessert werden. Wenn das Volumen der abgelegten Dateien gering ist, passen Sie die Stapelgröße und das Wiederholungsintervall entsprechend an. Wenn beispielsweise jede Sekunde 10 Dateien abgelegt werden, probieren Sie ein Wiederholungsintervall von 1 Sekunde und eine Stapelgröße von 10 aus. 

In einer Cluster-Konfiguration kann die Stapelgröße für einen Überwachter Order-Endpunkt nicht für mehrere Clusterknoten skaliert werden. Wenn beispielsweise die Stapelgröße für einen Cluster mit zwei Knoten auf „`2`“ festgelegt und die Option „Einschränken“ ausgewählt ist, verarbeitet der Knoten die Dateien gemeinsam in Zweierstapeln, statt dass jeder Knoten zwei Dateien gleichzeitig verarbeitet.

**Doppelte Dateinamen überschreiben:** Eine Boolean-Zeichenfolge, die angibt, ob der überwachte Ordner doppelte Ergebnisdateinamen überschreibt und ob beibehaltene Dokumente mit demselben Namen überschrieben werden sollen.

**Aufbewahrungsordner:** Der Standardwert für den Aufbewahrungsordner. Dieser Ordner wird zum Kopieren der Quelldateien verwendet, falls die Eingabe erfolgreich verarbeitet wurde. Dieser Wert kann ein leerer, relativer oder absoluter Pfad mit einem Dateimuster sein (wie für die Einstellung „Ergebnisordner“ beschrieben).

**Fehlerordner:** Der Name des Ordners, in den die Dateien mit Fehlern kopiert werden. Dieser Wert kann ein leerer, relativer oder absoluter Pfad mit einem Dateimuster sein (wie für die Einstellung „Ergebnisordner“ beschrieben).

**Ergebnisordner:** Der Standardwert für den Ergebnisordner. Dieser Ordner wird zum Kopieren der Ergebnisdateien verwendet. Dieser Wert kann ein leerer, relativer oder absoluter Pfad mit folgendem Dateimuster sein.

* %F = Dateinamenpräfix
* %E = Dateinamenerweiterung
* %Y = Jahr (vollständig)
* %y = Jahr (letzte zwei Stellen)
* %M = Monat
* %D = Tag des Monats
* %d = Tag des Jahres
* %H = Stunde (24-Stunden-Format)
* %h = Stunde (12-Stunden-Format)
* %m = Minute
* %s = Sekunde
* %l = Millisekunde
* %R = Zufallszahl (von 0 bis 9)
* %P = Prozess- oder Auftrags-ID

Wenn es z. B. 20 Uhr am 17. Juli 2009 ist und Sie `C:/Test/WF0/failure/%Y/%M/%D/%H/` angeben, lautet der Ergebnisordner `C:/Test/WF0/failure/2009/07/17/20`.

Wenn der Pfad nicht absolut, sondern relativ ist, wird der Ordner im überwachten Ordner erstellt. Informationen zu Dateimustern finden Sie unter [Grundlegendes zu Dateimustern](/help/forms/using/admin-help/configuring-watched-folder-endpoints.md#about-file-patterns).

>[!NOTE]
>
>Je kleiner die Größe des Ergebnisordners ist, desto höher wird die Watched Folder-Leistung sein. Wenn beispielsweise die geschätzte Belastung für den überwachten Ordner bei 1000 Dateien pro Stunde liegt, sollten Sie ein Muster wie `result/%Y%M%D%H` verwenden, sodass jede Stunde ein neuer Unterordner erstellt wird. Wenn die Belastung geringer ist (z. B. 1000 Dateien pro Tag), können Sie ein Muster wie das folgende verwenden: `result/%Y%M%D`.

**Bereitstellungsordner**: Der Standardname für den Bereitstellungsordner im überwachten Ordner.

**Eingabeordner**: Der Standardname für den Eingabeordner im überwachten Ordner.

**Bei Fehler beibehalten**: Wenn diese Option aktiviert ist, werden bei einem Fehler die Originaldateien im Fehlerordner aufbewahrt.

**Einschränken**: Wenn diese Option ausgewählt ist, wird die Anzahl der Aufträge für überwachte Ordner begrenzt, die AEM Forms zu einem bestimmten Zeitpunkt verarbeitet kann. Der Wert für die Stapelgröße bestimmt die maximale Anzahl an Aufträgen (siehe Informationen zu Einschränkungen).

## Einstellungen des Web Service-Dienstes {#web-service-service-settings}

Der Web Service-Dienst (`WebService`) ermöglicht Prozessen das Aufrufen von Webdienstvorgängen.

Der Web Service-Dienst ermöglicht Prozessen das Aufrufen von Webdienstvorgängen. Ein Unternehmen kann beispielsweise einen Prozess zum Speichern und Abrufen von Informationen wie Kontakt- und Kontodetails integrieren, indem die offengelegten Webdienste eines Dienstanbieters aufgerufen werden. Der Web Service-Dienst ruft einen angegebenen Webdienst auf und übergibt Werte für alle dazugehörigen Parameter. Anschließend speichert er die Rückgabewerte des Vorgangs in einer angegebenen Prozessvariablen.

Der Web Service-Dienst interagiert mit Webdiensten durch das Senden und Empfangen von SOAP-Nachrichten. Der Dienst unterstützt außerdem das Senden von MIME-, MTOM- und SwaRef-Anlagen zusammen mit SOAP-Nachrichten unter Verwendung des Protokolls „WS-Attachment“. Die Interaktionen des Web Service-Dienstes sind mit SAP-System und .NET-Webdiensten kompatibel.

Folgende Einstellungen sind für den Web Service-Dienst verfügbar:

**Keystore**: Der vollständige Pfad der Keystore-Datei mit dem privaten Schlüssel, der für die Authentifizierung verwendet werden soll. Der Formularserver muss auf die Datei zugreifen können.

**Keystore-Kennwort**: Das Kennwort für die Keystore-Datei.

**Keystore-Typ**: Der Typ des Keystores. Geben Sie keinen Wert an, wenn Sie den Standard-Keystore-Typ verwenden möchten, der für die JVM, die den Formularserver ausführt, konfiguriert ist. Geben Sie andernfalls einen der folgenden Werte an:

* jks
* pkcs12
* cms
* jceks

**Trust Store**: Der vollständige Pfad der TrustStore-Datei, die den öffentlichen Schlüssel des Webservice-Servers enthält.

**Trust Store-Kennwort**: Das Kennwort für die TrustStore-Datei.

**Trust Store-Typ**: Der Typ des TrustStores. Geben Sie keinen Wert an, wenn Sie den Standard-Keystore-Typ verwenden möchten, der für die JVM, die den Formularserver ausführt, konfiguriert ist. Geben Sie andernfalls einen der folgenden Werte an:

* jks
* pkcs12
* cms
* jceks

## Einstellungen des XSLT Transformation-Dienstes {#xslt-transformation-service-settings}

Der XSLT Transformation-Dienst (`XSLTService`) ermöglicht Prozessen das Anwenden von Extensible Stylesheet Language Transformations (XSLT) auf XML-Dokumente.

Folgende Einstellung ist für den XSLT Transformation-Dienst verfügbar:

**Factory-Name**: Der voll qualifizierte Name der Java-Klasse, die für die Durchführung von XSLT-Transformationen verwendet werden soll. Wenn kein Wert angegeben ist, wird die Standardfactory verwendet, die in der Java Virtual Machine konfiguriert ist, in der der Formularserver ausgeführt wird.

## Ändern von Sicherheitseinstellungen für einen Dienst {#modifying-security-settings-for-a-service}

Der Formularserver ermöglicht Ihnen das Konfigurieren von Sicherheitseinstellungen für jeden einzelnen Dienst, wodurch Sie eine fein abgestufte Zugriffssteuerung auf Dienstebene konfigurieren können.

Standardsicherheitsprofile, die installiert sind, können Sie so konfigurieren, dass sie den Anforderungen Ihres Systems entsprechen. Jedem Sicherheitsprofil ist eine Domain zugeordnet und es wird entweder auf Benutzerebene oder auf Gruppenebene erstellt.

### Sicherheitseinstellungen für einen Dienst ändern {#modify-security-settings-for-a-service}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf den zu konfigurierenden Dienst.
1. Klicken Sie auf die Registerkarte Sicherheit.
1. Wählen Sie in der Liste „Authentifizierung von Aufrufern erforderlich“ entweder „Ja“ oder „Nein“, um anzugeben, ob der Dienst mit oder ohne Anmeldeinformationen aufgerufen werden darf.

   Wenn Sie „Ja“ wählen, muss der Aufrufer des Dienstes authentifiziert werden und der Benutzerprinzipal für diesen Aufrufer muss zum Aufrufen des Dienstes berechtigt sein. Andernfalls wird der Aufrufversuch verweigert.

   Wenn Sie „Nein“ wählen, kann der Aufrufer des Dienstes authentifiziert werden, muss es aber nicht. Das Aufrufen des Dienstes ist immer erfolgreich, da die Authentifizierung nicht überprüft wird.

1. Für Dienste, die mindestens einen Vorgang enthalten, der für anonymen Zugriff markiert ist, aktivieren oder deaktivieren Sie die Option „Anonymer Zugriff zugelassen“. Wenn der anonyme Zugriff aktiviert ist, kann jeder Benutzer innerhalb des Systems Vorgänge für den Dienst aufrufen. Wenn der anonyme Zugriff deaktiviert ist, benötigen Benutzer Berechtigungen, um den Dienst sowie Vorgänge aufrufen zu können. Benutzern werden diese Berechtigungen entweder direkt erteilt oder dadurch, dass sie einer Gruppe angehören, welche die entsprechenden Berechtigungen besitzt.
1. Bei einigen Diensten wirkt sich das Benutzerkonto, das den Vorgang ausführt, auf die Ergebnisse aus. In Content Services (nicht mehr unterstützt) wird beispielsweise der Benutzer, der Inhalte speichert, zum Eigentümer der Inhalte. Dies hat Auswirkungen darauf, welche Benutzer später auf die Inhalte zugreifen können. Wenn Sie einen Prozess zum Speichern von Inhalten verwenden, sollten Sie überlegen, welcher Benutzer zum Ausführen des Document Management-Dienstes verwendet wird, da dieser Benutzer dann Eigentümer der gespeicherten Inhalte wird.

   Um die von einem Dienst zum Ausführen von Vorgängen verwendete Laufzeitidentität anzugeben, aktivieren Sie „Ausführen als angeben“ und wählen Sie eine Option aus der dazugehörigen Liste. Wählen Sie unter folgenden Optionen:

   **Aufrufender:** Verwendet dieselbe Identität wie der Benutzer, von dem der Dienst aufgerufen wurde.

   **System:** Verwendet den Systembenutzer, um den Dienst mit vollem Berechtigungsumfang auszuführen.

   **Benannter Benutzer:** Ermöglicht das Ausführen des Dienstes als ein bestimmter Benutzer. Wenn Sie diese Option aktivieren, klicken Sie auf „Benutzer auswählen“, um die Seite „Prinzipal auswählen“ anzuzeigen, auf der Sie nach dem Benutzer suchen und ihn auswählen können.

   Wenn Sie die Option „Ausführen als angeben“ nicht aktivieren, wird das Standardverhalten verwendet.

   >[!NOTE]
   >
   >Wiedergabe- und Sendedienste, die für die Variablen „xfaForm“, „Document Form“ und „Form“ verwendet werden, werden immer mithilfe des Systembenutzerkontos ausgeführt.

1. Klicken Sie auf „Prinzipal hinzufügen“, um die Berechtigungen von Benutzern und Gruppen für diesen Dienst anzugeben.
1. Im Bildschirm „Select Principal“ werden die in User Management konfigurierten Benutzer und Gruppen angezeigt. Falls der gewünschte Benutzer bzw. die gewünschte Gruppe nicht angezeigt wird, verwenden Sie die Suchfunktion, um sie zu finden. Klicken Sie auf einen Benutzer- oder Gruppennamen.
1. Wählen Sie im Bildschirm „Berechtigungen hinzufügen“ die Berechtigungen, die Sie dem Benutzer bzw. der Gruppe für diesen Dienst zuweisen möchten:

   * **INVOKE_PERM:** Aufrufen aller Vorgänge für den Dienst
   * **MODIFY_CONFIG_PERM:**&#x200B;Ändern der Konfiguration eines Dienstes
   * **SUPERVISOR_PERM:** Anzeigen der Prozessinstanzdaten für einen Dienst, der aus einem Prozess erstellt wurde
   * **START_STOP_PERM:** Starten und Beenden eines Dienstes
   * **ADD_REMOVE_ENDPOINTS_PERM:** Hinzufügen, Entfernen und Ändern von Endpunkten für einen Dienst
   * **CREATE_VERSION_PERM:** Erstellen einer neuen Version des Dienstes
   * **DELETE_VERSION_PERM:** Löschen einer Version des Dienstes
   * **MODIFY_VERSION_PERM:**&#x200B;Ändern einer Version des Dienstes
   * **READ_PERM:** Anzeigen des Dienstes
   * **PROCESS_OWNER_PERM:** Ist zur Verwendung in einer zukünftigen Version von AEM Forms vorgesehen. Verwenden Sie diese Berechtigung nicht.
   * **SERVICE_MANAGER_PERM:** Ist zur Verwendung in einer zukünftigen Version von AEM Forms vorgesehen. Verwenden Sie diese Berechtigung nicht.
   * **SERVICE_AGENT_PERM:** Ist zur Verwendung in einer zukünftigen Version von AEM Forms vorgesehen. Verwenden Sie diese Berechtigung nicht.

1. Klicken Sie auf Hinzufügen.

### Prinzipal aus einem Sicherheitsprofil entfernen {#remove-the-principal-from-a-security-profile}

1. Wählen Sie auf der Seite „Dienstverwaltung“ den zu konfigurierenden Dienst.
1. Klicken Sie auf die Registerkarte **Sicherheit**, wählen Sie das zu entfernende Sicherheitsprofil und klicken Sie auf **Entfernen**.

## Pooling für einen Dienst konfigurieren {#configuring-pooling-for-a-service}

Jeder Dienst kann die Poolingfunktionen zum Verarbeiten eingehender Aufrufanforderungen nutzen. Durch die Verwendung eines Dienstpools wird sichergestellt, dass Dienstinstanzen immer nur von einem einzigen Thread gleichzeitig aufgerufen werden und dass sie über Aufrufanforderungen hinweg wiederverwendet werden, was die Leistung erhöhen kann. Außerdem können Sie mithilfe von Pooling die Option „Max. Anzahl asynchroner Dienstinstanzen“ angeben, die es Diensten ermöglicht, die Anzahl parallel verarbeiteter Anforderungen zu begrenzen.

### Pooling aktivieren {#enable-pooling}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf den zu konfigurierenden Dienst.
1. Klicken Sie auf die Registerkarte „Pooling“.
1. Wählen Sie in der Liste „Strategie für Anforderungsverarbeitung“ den Eintrag „Instanzenpools für alle Anforderungen“.
1. Geben Sie in das Feld „Anfängliche Dienstinstanzpool-Größe“ die Anfangsgröße des Pools ein. Beim Bereitstellen des Dienstes wird mithilfe dieses Wertes die Anzahl der Dienstimplementierungsinstanzen ermittelt, die erstellt und dem freien Pool zugeordnet werden, um auf Aufrufanforderungen zu warten. Hierdurch kann der Dienstcontainer dann sofort auf Aufrufanforderungen reagieren, ohne eine Dienstinstanz zuerst initialisieren zu müssen.
1. Geben Sie in das Feld „Maximale Dienstinstanzpool-Größe“ die maximale Anzahl von Instanzen im Pool für einen bestimmten Dienst ein. Diese Einstellung steuert die Anzahl der Threads, von denen der jeweilige Dienst zu einem bestimmten Zeitpunkt ausgeführt werden kann. Der Standardwert ist 0, was einer unbegrenzten Poolgröße entspricht.
1. Geben Sie in das Feld „Max. Anzahl asynchroner Dienstinstanzen“ die maximale Anzahl von Instanzen im Pool ein, die für die Verarbeitung asynchroner Anforderungen zu einem bestimmten Zeitpunkt verwendet werden kann. Diese Einstellung ermöglicht dem Dienst die Begrenzung der Anzahl von Anforderungen, die parallel verarbeitet werden können.
1. Geben Sie in das Feld „Timeout beim Warten auf Aufruf“ die Anzahl der Millisekunden ein, die auf die Verfügbarkeit eines Dienstes für eine Aufrufanforderung gewartet werden soll. Wenn Sie für diese Einstellung keinen Wert angeben, ist der Standardwert 0, was keiner Wartezeit entspricht.
1. Klicken Sie auf Speichern.

### Pooling entfernen {#remove-pooling}

1. Klicken Sie in Administration Console auf „Dienste“ > „Anwendungen und Dienste“ > „Dienstverwaltung“.
1. Klicken Sie auf der Seite „Dienstverwaltung“ auf den zu konfigurierenden Dienst.
1. Klicken Sie auf die Registerkarte „Pooling“.
1. Wählen Sie in der Liste „Strategie für Anforderungsverarbeitung“ entweder den Eintrag „Neue Instanz für jede Anforderung“ oder den Eintrag „Einzelinstanz für alle Anforderungen“ aus.

   **Einzelinstanz für alle Anforderungen**: Eine Instanz eines Services wird erstellt und zwischengespeichert, wenn die erste Anforderung im Container eingeht. Jede darauffolgende Anforderung verwendet die gleiche Dienstinstanz zum Verarbeiten der Anforderung.

   **Neue Instanz für jede Anforderung**: Für jeden empfangenen Aufruf wird eine neue Instanz des Services erstellt.

1. Klicken Sie auf Speichern.
