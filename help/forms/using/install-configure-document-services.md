---
title: Installieren und Konfiguration von Dokumentendiensten
description: Installieren Sie AEM Forms-Dokumentendienste, um PDF-Dokumente zu erstellen, zusammenzustellen, zu verteilen, zu archivieren, digitale Signaturen zur Einschränkung des Zugriffs auf Dokumente hinzuzufügen und Formulare mit Barcode zu entschlüsseln..
topic-tags: installing
role: Admin, Developer
exl-id: 5d48e987-16c2-434b-8039-c82181d2e028
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
source-git-commit: 62baf682b75823f52f968a70960aff2388d49cad
workflow-type: tm+mt
source-wordcount: '10085'
ht-degree: 53%

---

# Installieren und Konfiguration von Dokumentendiensten {#installing-and-configuring-document-services}

AEM Forms bietet eine Reihe von OSGi-Diensten für verschiedene Vorgänge auf Dokumentebene, z. B. Services zum Erstellen, Zusammenstellen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Signaturen zur Einschränkung des Zugriffs auf Dokumente und Decodieren von Barcode-Formularen. Diese Dienste sind im Add-On-Paket zu AEM Forms enthalten. Die Gesamtheit dieser Dienste wird als Dokumentendienste bezeichnet. Die Liste der verfügbaren Dokumentendienste und ihrer wichtigsten Funktionen ist nachstehend aufgeführt:

* **Assembler-Service:** Damit können Sie PDF- und XDP-Dokumente kombinieren, neu anordnen und erweitern sowie Informationen zu PDF-Dokumenten abrufen. Außerdem können Sie damit PDF-Dokumente in PDF/A-Standard konvertieren und validieren sowie PDF-Formulare, XML-Formulare und PDF-Formulare in PDF/A-1b, PDF/A-2b und PDFA/A-3b umwandeln. Weitere Informationen finden Sie unter [Assembler-Service](/help/forms/using/assembler-service.md).

* **ConvertPDF-Service:** Ermöglicht Ihnen, PDF-Dokumente in PostScript oder Bilddateien (JPEG, JPEG 2000, PNG und TIFF) zu konvertieren. Weitere Informationen finden Sie unter [ConvertPDF-Service](/help/forms/using/using-convertpdf-service.md).

* **Barcoded Forms-Service:** Ermöglicht das Extrahieren von Daten aus elektronischen Bildern von Barcodes. Der Dienst akzeptiert TIFF- und PDF-Dateien mit einem oder mehreren Strichcodes als Eingabe und extrahiert die Strichcodedaten. Weitere Informationen finden Sie unter [Barcoded Forms-Service](/help/forms/using/using-barcoded-forms-service.md).

* **DocAssurance-Servcice:** Damit können Sie Dokumente ver- und entschlüsseln, Funktionen von Adobe Reader mit zusätzlichen Nutzungsrechten erweitern sowie digitale Signaturen zu Ihren Dokumenten hinzufügen. Der DocAssurance-Dienst umfasst drei Dienste: Signature, Encryption und Reader Extension. Weitere Informationen finden Sie unter [DocAssurance-Service](/help/forms/using/overview-aem-document-services.md).

* **Encryption-Service:** Ermöglicht das Ver- und Entschlüsseln von Dokumenten. Wenn ein Dokument verschlüsselt wird, ist sein Inhalt unlesbar. Eine autorisierte Person kann das Dokument entschlüsseln, um Zugriff auf seinen Inhalt zu erhalten. Weitere Informationen finden Sie unter [Encryption-Service](/help/forms/using/overview-aem-document-services.md#encryption-service).

* **Forms-Service:** Ermöglicht das Erstellen interaktiver Client-Anwendungen zur Datenerfassung, die in Forms Designer erstellte Formulare überprüfen, verarbeiten, transformieren und übermitteln. Mit dem Forms-Service können Sie beliebige von Ihnen entwickelte Formular-Designs als PDF-Dokumente rendern. Weitere Informationen finden Sie unter [Forms-Service](/help/forms/using/forms-service.md).

* **Output-Service:** Er ermöglicht das Erstellen von Dokumenten in verschiedenen Formaten, einschließlich PDF, Laserdruckerformate und Beschriftungsdruckerformate. Laser-Druckerformate sind PostScript und Printer Control Language (PCL). Weitere Informationen finden Sie unter [Output-Service](/help/forms/using/output-service.md).

* **PDF Generator-Service** Der PDF Generator-Service stellt APIs zum Konvertieren nativer Dateiformate in PDF bereit. Es kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren. Weitere Informationen finden Sie unter [PDF Generator-Service](aem-document-services-programmatically.md#pdfgeneratorservice).

* **Reader Extensions-Service:** Ermöglicht Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweitern der Funktionalität von Adobe Reader durch zusätzliche Verwendungsrechte. Dieser Dienst aktiviert Funktionen, die nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Reader geöffnet wird, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. Weitere Informationen finden Sie unter [Reader Extension-Service](/help/forms/using/overview-aem-document-services.md#reader-extension-service).

* **Signature-Service:** Ermöglicht das Arbeiten mit digitalen Signaturen und Dokumenten auf dem AEM-Server. Der Signatur-Dienst wird beispielsweise in der Regel in folgenden Situationen verwendet:

   * Der AEM-Server zertifiziert ein Formular, bevor es an eine Person zum Öffnen mithilfe von Acrobat oder Adobe Reader gesendet wird.
   * Der AEM-Server überprüft eine Signatur, die einem Formular mithilfe von Acrobat oder Adobe Reader hinzugefügt wurde.
   * Der AEM-Server signiert ein Formular im Namen einer öffentlichen beglaubigenden Person.

  Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu, die im Trust Store gespeichert sind. Weitere Informationen finden Sie unter [Signature-Service](/help/forms/using/aem-document-services-programmatically.md).

AEM Forms ist eine leistungsfähige Plattform der Enterprise-Klasse und die Document-Services gehören zu den Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Bereitstellungstopologie {#deployment-topology}

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Im Allgemeinen benötigen Sie nur eine AEM-Instanz (Autor oder Veröffentlichung), um AEM Forms-Dokumentendienste auszuführen. Die folgende Topologie wird für die Ausführung von AEM Forms-Dokumentendiensten empfohlen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![Architektur und Bereitstellungstopologien für AEM Forms](do-not-localize/document-services.png)

>[!NOTE]
>
>Auch wenn Sie mit AEM Forms alle Funktionen von einem einzigen Server aus einrichten und ausführen können, sollten Sie eine Kapazitätsplanung und einen Lastausgleich vornehmen und dedizierte Server für bestimmte Funktionen in einer Produktionsumgebung einrichten. Wenn Sie beispielsweise den PDF-Generator-Dienst für die Konvertierung von Tausenden von Seiten pro Tag und mehrere adaptive Formulare für die Datenerfassung verwenden, richten Sie separate AEM Forms-Server für den PDF Generator-Dienst und die adaptiven Formularfunktionen ein. Dies bietet optimale Leistung und skaliert die Server unabhängig voneinander.

## Systemanforderungen {#system-requirements}

Bevor Sie mit der Installation und Konfiguration der AEM Forms-Dokumentendienste beginnen, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM Instanz läuft. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. In der Regel benötigen Sie nur eine AEM-Instanz (Autor oder Veröffentlichung), um AEM Forms-Dokumentendienste auszuführen:

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Veröffentlichung**: Eine AEM-Instanz, die die veröffentlichten Inhalte über das Internet oder ein internes Netzwerk öffentlich zugänglich macht.

* Es gibt gewisse Arbeitsspeicheranforderungen. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft® Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Die Client-Software, die von PDF Generator für die Konvertierung unter Microsoft® Windows und Linux® benötigt wird, wird installiert:

   * **Microsoft® Windows**: [Microsoft® Office](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p) oder [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) installieren
   * **Linuxx®**: [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p) installieren

>[!NOTE]
>
>* Unter Microsoft® Windows unterstützt PDF Generator die WebKit-, Acrobat WebCapture- und Web-in-PDF-Konvertierungsrouten zum Konvertieren von HTML-Dateien in PDF-Dokumente.
>* Auf UNIX-basierten Betriebssystemen unterstützt PDF Generator die WebKit- und Web-in-PDF-Konvertierungsrouten zum Konvertieren von HTML-Dateien in PDF-Dokumente.
>

### Zusätzliche Anforderungen für UNIX-basierte Betriebssysteme {#extrarequirements}

Wenn Sie ein UNIX-basiertes Betriebssystem verwenden, installieren Sie die folgenden 32-Bit-Pakete über die Installationsmedien des jeweiligen Betriebssystems:
<table>
 <tbody>
  <tr>
   <td>
    <ul>
     <li>expat</li>
    </ul> </td>
   <td>
    <ul>
     <li>libxcb</li>
    </ul> </td>
   <td>
    <ul>
     <li>freetype</li>
    </ul> </td>
   <td>
    <ul>
     <li>libXau</li>
    </ul> </td>
  </tr>
  <tr>
   <td>
    <ul>
     <li>libSM</li>
    </ul> </td>
   <td>
    <ul>
     <li>zlib</li>
    </ul> </td>
   <td>
    <ul>
     <li>libICE</li>
    </ul> </td>
   <td>
    <ul>
     <li>libuuid</li>
    </ul> </td>
  </tr>
  <tr>
   <td>
    <ul>
     <li>glibc</li>
    </ul> </td>
   <td>
    <ul>
     <li>libXext</li>
    </ul> </td>
   <td>
    <ul>
     <li>nss-softokn-freebl</li>
    </ul> </td>
   <td>
    <ul>
     <li>fontconfig</li>
    </ul> </td>
  </tr>
  <tr>
   <td>
    <ul>
     <li>libX11</li>
    </ul> </td>
   <td>
    <ul>
     <li>libXrender</li>
    </ul> </td>
   <td>
    <ul>
     <li>libXrandr</li>
    </ul> </td>
   <td>
    <ul>
     <li>libXinerama</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

* **(Nur PDF Generator**) Installieren Sie die 32-Bit-Version der Bibliotheken libcurl, libcrypto und libssl und erstellen Sie die folgenden Symlinks. Die Symlinks zeigen auf die neueste Version der jeweiligen Bibliotheken:

   * /usr/lib/libcurl.so
   * /usr/lib/libcrypto.so
   * /usr/lib/libssl.so

* **(Nur PDF Generator)** Der PDF Generator-Dienst unterstützt WebKit- und Web-in-PDF-Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente. Um die Konvertierung für die Web-in-PDF-Route zu aktivieren, installieren Sie die unten aufgeführten 64-Bit-Bibliotheken. Im Allgemeinen sind diese Bibliotheken bereits installiert. Falls eine Bibliothek fehlt, installieren Sie diese manuell:

   * linux-gate.so.1
   * libz.so.1
   * libfontconfig.so.1
   * libfreetype.so.6
   * libdl.so.2
   * librt.so.1
   * libpthread.so.0
   * libstdc++.so.6
   * libm.so.6
   * libgcc_s.so.1
   * libc.so.6
   * ld-linux.so.2
   * libexpat.so.1
* (Nur PDF Generator) Um die WebKit-Route bei RHEL 8- oder RHEL 9-Setups zu aktivieren, ist die 32-Bit-Bibliothek `nspr` möglicherweise nicht standardmäßig verfügbar. Installieren Sie sie, falls nicht vorhanden.

* (Nur PDF Generator) Wenn die WebToPDF-Konversion auf dem Unix®-Server mit dem folgenden Fehler fehlschlägt:

  ```Auto configuration failed 4143511872:error:0E079065:configuration file routines:DEF_LOAD_BIO:missing equal sign:conf_def.c:362:line 57```
Legen Sie dann die folgende Umgebungsvariable fest und starten Sie den Server neu:
  `OPENSSL_CONF=/etc/ssl`

>[!NOTE]
>
> WebToPDF wird auch von der Diagrammfunktion in interaktiven Kommunikationen verwendet. Daher sind alle oben aufgeführten Konfigurationsschritte für WebToPDF anwendbar, um sicherzustellen, dass die Diagrammfunktion ordnungsgemäß funktioniert.

## Vorinstallationskonfigurationen {#preinstallationconfigurations}

Konfigurationen, die im Abschnitt „Vorinstallationskonfigurationen“ aufgeführt sind, gelten nur für den PDF Generator-Dienst. Wenn Sie den PDF Generator-Dienst nicht konfigurieren, können Sie den Abschnitt „Vorinstallationskonfigurationen“ überspringen.

### Installieren von Adobe Acrobat und Anwendungen von Drittanbietern {#install-adobe-acrobat-and-third-party-applications}

Wenn Sie den PDF Generator-Service verwenden, um native Dateiformate wie Microsoft® Word, Microsoft® Excel, Microsoft® PowerPoint, OpenOffice und Adobe Acrobat in PDF-Dokumente zu konvertieren, stellen Sie sicher, dass diese Programme auf dem AEM Forms-Server installiert sind.

>[!NOTE]
>
><!-- * If your AEM Forms Server is in an offline or secure environment and internet is not available to activate Adobe Acrobat, see [Offline Activation](https://exception.licenses.adobe.com/aoes/aoes/v1/t1?locale=en) for instructions to activate such instances of Adobe Acrobat. -->
>* Adobe Acrobat, Microsoft® Word, Excel und PowerPoint sind nur für Microsoft® Windows verfügbar. Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie OpenOffice, um Rich-Text-Dateien und unterstützte Microsoft® Office-Dateien in PDF-Dokumente zu konvertieren.
>* Schließen Sie alle Dialogfelder, die nach der Installation von Adobe Acrobat und Software von Drittanbietern für alle diejenigen Benutzer angezeigt werden, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
>* Starten Sie die installierte Software mindestens einmal. Schließen Sie alle Dialogfelder für alle Benutzer, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
>* [Überprüfen Sie das Ablaufdatum der Adobe Acrobat-Seriennummern](https://helpx.adobe.com/de/enterprise/kb/volume-license-expiration-check.html) und legen Sie ein Datum für das Aktualisieren der Lizenz fest oder [migrieren Sie die Seriennummer](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number) auf der Grundlage des Ablaufdatums.

### Installieren von Adobe Acrobat Pro DC

#### Voraussetzungen

Überprüfen Sie vor der Installation von Acrobat diese grundlegenden Anforderungen. Sie sollten Folgendes haben:

* Vertrautheit mit [Adobe Admin Console](https://helpx.adobe.com/in/enterprise/admin-guide.html)
* Grundlegendes zur Bereitstellungsarchitektur von [AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md)
* Administratorrechte sowohl auf dem Adobe Admin Console als auch auf dem Server, auf dem AEM Forms ausgeführt wird.
* Ein Benutzer mit [Administratorzugriff](https://helpx.adobe.com/in/enterprise/using/admin-roles.html) auf die Adobe [Admin Console](https://adminconsole.adobe.com). Im Allgemeinen verfügt der Administrator Ihrer Organisation bereits über einen Benutzer mit Administratorzugriff. Anweisungen zum Hinzufügen [ Administrators finden Sie ](https://www.youtube.com/watch?v=xO2T0I6SvsU&list=PLHRegP5ZOj7CpijZyD8pB9rIMJkvO6FnI&t=81s) diesem „Video mit Anweisungen“.
* Ein Benutzerkonto mit der Rolle [Bereitstellungsadministrator](https://helpx.adobe.com/in/enterprise/global-admin-console/manage-administrators.html) in der Adobe Admin Console. Das gleiche [Anleitungsvideo](https://www.youtube.com/watch?v=xO2T0I6SvsU&list=PLHRegP5ZOj7CpijZyD8pB9rIMJkvO6FnI&t=81s) zeigt, wie Sie einen Bereitstellungsadministrator hinzufügen.
* Lokale Administratorrechte auf dem Computer, auf dem AEM Forms ausgeführt wird
* Windows 64-Bit-Betriebssystem
* Stabile Internetverbindung für Lizenzaktivierung
<!-- Backup solution for existing Acrobat settings
 Supported version of Adobe Acrobat (see [Adobe documentation](https://helpx.adobe.com/acrobat/kb/acrobat-dc-compatibility-with-windows-macos.html) for details) -->


#### Implementierungs-Workflow und Timeline

Der vollständige Prozess dauert in der Regel 1-2 Stunden, je nach Ihrer Umgebung:

| Schritt | Geschätzte Zeit | Voraussetzungen |
|------|----------------|---------------|
| &#x200B;1. Erstellen eines FRL-Pakets in Admin Console) | 15-20 Minuten | [Admin Console-Zugriff](https://helpx.adobe.com/in/enterprise/admin-guide.html) |
| &#x200B;2. Download-Berechtigungen erteilen | 5-10 Minuten | [Admin Console-Zugriff](https://helpx.adobe.com/in/enterprise/global-admin-console/manage-administrators.html) |
| &#x200B;3. Deinstallieren Sie das vorherige Acrobat | 10-15 Minuten | Serveradministratorzugriff |
| &#x200B;4. Herunterladen und Installieren von Adobe Acrobat Pro | 10-15 Minuten | Serveradministratorzugriff |
| &#x200B;5. Herunterladen und Bereitstellen des FRL-Pakets | 20-30 Minuten | Serveradministratorzugriff |
| &#x200B;6. Überprüfen Sie die Installation | 5-10 Minuten | Serverzugriff |

<!-- ![Workflow diagram showing the FRL implementation process](/help/forms/using/assets/frl.svg) -->

**Wählen Sie Ihren Installationspfad**

Der Installationsprozess für die Installation von Adobe Acrobat Pro DC für Microsoft Office variiert geringfügig je nach Lizenztyp und Bereitstellungsszenario. Um sicherzustellen, dass Sie die richtigen Schritte für Ihre spezifische Umgebung befolgen, wählen Sie bitte die Registerkarte aus, die Ihrer Konfiguration entspricht:

* **Lizenztyp**: Einzelhandels- oder Volumenlizenz
* **Bereitstellungstyp**: Ein Benutzer oder mehrere Benutzer

Jede Registerkarte enthält maßgeschneiderte Anweisungen, die für Ihr spezifisches Setup optimiert sind. So vermeiden Sie Konfigurationsprobleme und stellen eine ordnungsgemäße Lizenzierung sicher.

>[!VIDEO](https://video.tv.adobe.com/v/3469669)

>[!NOTE]
>
>Das Video zeigt den Installationsprozess für eine Einzelhandelslizenz - Konfiguration für einen einzelnen Benutzer. Für andere Bereitstellungsszenarien (Einzelhandel - Mehrere Benutzer, Volumenlizenz - Einzelbenutzer oder Volumenlizenz - Mehrere Benutzer) verwenden Sie die spezifischen Anweisungen von Schritt 9 auf den entsprechenden Registerkarten unten, um einen ordnungsgemäßen Serverstart und eine ordnungsgemäße Lizenzaktivierung für Ihren Bereitstellungstyp sicherzustellen.

>[!BEGINTABS]

>[!TAB Einzelhandelslizenz - Einzelanwender]

#### Einrichten einer funktionsbeschränkten Lizenzierung (FRL) für Adobe Acrobat auf Ihrem AEM Forms-Server

Bei diesen Schritten wird davon ausgegangen, dass Sie sowohl auf dem Adobe Admin Console als auch auf dem Server, auf dem AEM Forms ausgeführt wird, über die erforderlichen Administratorrechte verfügen.

##### Vorbereiten des FRL-Pakets (Adobe Admin Console)

Diese Schritte sind mit Zugriff *Systemadministrator“ auf* Adobe Admin Console auszuführen.

###### Schritt 1: Beim Adobe Admin Console anmelden

1. Öffnen Sie einen Webbrowser und navigieren Sie zur [Adobe Admin Console](https://adminconsole.adobe.com/)
1. Melden Sie sich mit einem Konto mit Berechtigungen *Systemadministrator* an.
1. (Optional) Wenn Ihr Unternehmen Zugriff auf mehrere IMS-Organisationen hat, wählen Sie über die Option Organisationsauswahl oben rechts in Admin Console die richtige Organisation aus. In den meisten Kundenszenarien wäre dies bereits auf die Standardeinstellungen Ihrer Organisation festgelegt, da Benutzer in der Regel nur Zugriff auf ihre eigene Organisation haben.

###### Schritt 2: Erstellen des FRL-Pakets

1. Navigieren Sie in der Admin Console zur Registerkarte „Pakete“. Dies ist ein Adobe Admin Console-Paket, kein AEM-Paket.
1. Wählen Sie die Karte **Eingeschränkte Lizenz für Funktionen** und klicken Sie auf die Schaltfläche **Erste Schritte**. Stellen Sie sicher, dass Sie den richtigen Lizenztyp auswählen.
1. Konfigurieren **auf dem Bildschirm** Paket erstellen“ die Paketeinstellungen:

   | Einstellung | Empfohlener Wert | Anmerkungen |
   |---------|-------------------|-------|
   | Aktivierungsmethode | Offline | Empfohlene Option |
   | Berechtigung | PDF Generation (PDFG) | Erforderlich für AEM Forms PDF Generator-Funktionen |
   | Konfigurieren von Platform | Windows 64-Bit | Apple macOS wird derzeit nicht unterstützt |
   | Lokal aktivieren | „Betriebssystemsprache verwenden“ | Standardeinstellung |
   | Sprache | Ihre bevorzugte Sprache | Für die Benutzeroberfläche von Acrobat |
   | Apps auswählen - Verfügbare Programme | Adobe Acrobat in verfügbaren Programmen belassen. Nicht zur ausgewählten Anwendung verschieben | In [ 6 würden Sie &quot;Adobe Acrobat ](#step-6-download-and-install-adobe-acrobat-pro)&quot; von der Adobe Experience League -Seite herunterladen. |
   | Apps auswählen - Ausgewählte Programme | Nur Lizenzdatei in ausgewählten Anwendungen beibehalten | Standardeinstellung für die FRL-Bereitstellung |
   | Plug-ins | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | Optionen | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | abschließen | Paketname: &quot;Acrobat FRL AEM Forms&quot; | Namen beschreiben |

1. Klicken Sie **Erstellen**, um das Paket zu erstellen.

###### Schritt 3: Einem Benutzer Download-Berechtigungen erteilen

Es wird empfohlen, ein dediziertes Service-Konto für die Verwaltung von FRL-Paketen zu erstellen. Wenn Sie noch kein dediziertes Konto haben, können Sie [diesem Anleitungsvideo) ](https://www.youtube.com/watch?v=w8b36YX2TEM&t=59s), wie Sie einen neuen Benutzer zu Ihrer Adobe-Organisation hinzufügen.

Sobald Sie über das entsprechende Konto verfügen, führen Sie die folgenden Schritte aus, um Download-Berechtigungen zu gewähren:

1. Navigieren Sie in der Admin Console zur Registerkarte **Benutzer** .
2. Suchen oder erstellen Sie ein Benutzerkonto, um Download-Berechtigungen zu gewähren.
3. Klicken Sie auf den Namen des Benutzers, um sein Profil zu öffnen.
4. Klicken Sie auf das Symbol neben Benutzer **Administratorrechte bearbeiten**.
5. Weisen Sie dem **die Rolle** Bereitstellungsadministrator“ zu. Andere Administratorrollen funktionieren möglicherweise ebenfalls, Bereitstellungs-Admin ist jedoch die empfohlene Rolle. Klicken Sie auf **Speichern**.


##### Bereitstellen des FRL-Pakets (AEM Forms-Server)

Die folgenden Schritte werden auf dem AEM Forms-Server mit *lokalen Administratorrechten* über den Computer ausgeführt.

###### Schritt 4: Melden Sie sich bei dem Server an, auf dem AEM Forms als Administrator ausgeführt wird

Greifen Sie mithilfe der entsprechenden -Methode auf den Server zu, auf dem AEM Forms ausgeführt wird. Stellen Sie sicher, dass Sie ein Konto mit lokalen Administratorrechten für den Zugriff auf den Server verwenden.

###### Schritt 5: Deinstallieren der vorherigen Version von Acrobat (falls vorhanden)

**Kritisch:** Sichern Sie alle benutzerdefinierten Einstellungen, Profile oder Konfigurationen von Acrobat vor der Deinstallation.

1. Öffnen Sie die Windows-Systemsteuerung.
2. Navigieren Sie zu **Einstellungen** und öffnen Sie **Apps**.
3. Adobe Acrobat Suchen Sie **&#x200B;**&#x200B;in der Liste der installierten Programme
4. Wählen Sie **Deinstallieren** und befolgen Sie die Anweisungen, um die Anwendung zu entfernen. Starten Sie bei Aufforderung den Server neu
5. Stellen Sie sicher, dass alle klassischen Versionen des Programms deinstalliert sind. Verwenden Sie das [Adobe Acrobat Cleaner-Tool](https://helpx.adobe.com/acrobat/kb/remove-reader-dc-acrobat-dc.html) falls erforderlich, um eine vollständige Entfernung durchzuführen.

###### Schritt 6: Herunterladen und Installieren von Adobe Acrobat Pro

Nachdem Sie die vorherige Version deinstalliert haben, müssen Sie eine kompatible Version von Adobe Acrobat Pro herunterladen und installieren:

1. Navigieren Sie zur Seite [Adobe Acrobat DC-Downloads](https://helpx.adobe.com/in/acrobat/kb/acrobat-dc-downloads.html).
2. Navigieren Sie zum Abschnitt **Acrobat Pro** Installationsprogramm.
3. Laden Sie für die Verwendung mit AEM Forms PDF Generator das Installationsprogramm „Für Windows (32 Bit)“ herunter, da dies die von AEM Forms PDF Generator unterstützte Version ist.
4. Folgen Sie den Installationsanweisungen auf der Seite:
   * Extrahieren Sie die heruntergeladene ZIP-Datei in einen Ordner auf Ihrem Computer.
   * Navigieren Sie zur Datei Setup.exe (führen Sie die Datei Setup.exe nicht aus der ZIP-Datei aus)
   * Doppelklicken Sie auf Setup.exe, um die Installation zu starten
   * Folgen Sie den Anweisungen auf dem Bildschirm, um die Installation abzuschließen
5. Öffnen Sie nach der Installation Adobe Acrobat Pro und schließen Sie die Ersteinrichtung ab, indem Sie alle Begrüßungsdialoge schließen.
6. Überprüfen Sie die Installation, indem Sie eine einfache PDF erstellen.

###### Schritt 7: Herunterladen des FRL-Pakets

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) mit dem *Benutzerkonto* an, für das Sie in Schritt 3 Download-Berechtigungen erteilt haben.
1. Navigieren Sie zur Registerkarte **Pakete**.
1. Suchen Sie das FRL-Paket, das Sie in Schritt 2 erstellt haben (mit dem Namen &quot;Acrobat FRL AEM Forms&quot; oder Ihr benutzerdefinierter Paketname).
1. Klicken Sie **Herunterladen**, um das Paket auf den Server herunterzuladen.

###### Schritt 8: Bereitstellen des Pakets

1. **Paket extrahieren:** Extrahieren Sie den Inhalt der heruntergeladenen ZIP-Datei in ein Verzeichnis auf dem Server (z. B. `C:\AcrobatFRL`). Stellen Sie sicher, dass der Zugriff auf das Extraktionsverzeichnis leicht ist.

2. **Eingabeaufforderung als Administrator öffnen (Windows):** Klicken Sie mit der rechten Maustaste auf die Schaltfläche Start und wählen Sie „Eingabeaufforderung (Admin)“ oder „Windows PowerShell (Admin)“

3. **Navigieren Sie zum Extraktionsverzeichnis:**

   ```cmd
   cd C:\AcrobatFRL
   ```

4. **Führen Sie den Aktivierungsbefehl aus:**

   ```cmd
   # Command syntax
   adobe-licensing-toolkit.exe -p -i -f [JSON_FILE_NAME].json
   
   # Example with actual values
   adobe-licensing-toolkit.exe -p -i -f ngl-preconditioning-data.json
   ```

   > **Wichtig:**
   > * Ersetzen Sie `<JSON_FILE_NAME>.json` durch den *exakten* Dateinamen der JSON-Datei im extrahierten Paket.
   > * Beim JSON-Dateinamen wird zwischen Groß- und Kleinschreibung unterschieden.
   > * Überprüfen Sie den Dateinamen auf mögliche Rechtschreibfehler.

   **Erwartete Ausgabe:**

   ```
   Adobe Licensing Toolkit (1.1.0.130)
   Operation Successfully Completed
   ```

   > **Hinweis:** Der Aktivierungsvorgang kann etwa 30 Sekunden dauern.

5. **Verstehen der Befehlsparameter:**

   | Parameter | Beschreibung |
   |-----------|-------------|
   | `-p` | Gibt die Plattform an (erkennt das Betriebssystem automatisch) |
   | `-i` | Veranlasst das Tool zur Installation und Aktivierung der Lizenz |
   | `-f` | Gibt den Pfad zur JSON-Lizenzdatei an |

###### Schritt 9: Testen des PDF Generator-Service

Führen Sie nach Abschluss aller Prozesse einen Schnellaktionstest durch, um zu bestätigen, dass die Installation gültig ist:

1. Öffnen der AEM Forms-Admin-Benutzeroberfläche
2. Navigieren Sie zum PDF Generator-Service
3. Konvertieren eines einfachen Microsoft Office-Dokuments in PDF
4. Überprüfen, ob die Konvertierung erfolgreich abgeschlossen wurde

#### Acrobat-Version nach FRL-Aktivierung überprüfen

1. Öffnen Sie Adobe Acrobat Pro DC auf dem Server
2. Navigieren Sie zu → Informationen zu Adobe Acrobat Pro DC
3. Überprüfen, ob die Versionsnummer mit der erwarteten Version übereinstimmt
4. Bestätigen Sie, dass der Lizenzstatus als aktiviert angezeigt wird

>[!TAB Einzelhandelslizenz - Mehrere Benutzer]

#### Einrichten einer funktionsbeschränkten Lizenzierung (FRL) für Adobe Acrobat auf Ihrem AEM Forms-Server

Bei diesen Schritten wird davon ausgegangen, dass Sie sowohl auf dem Adobe Admin Console als auch auf dem Server, auf dem AEM Forms ausgeführt wird, über die erforderlichen Administratorrechte verfügen.

##### Vorbereiten des FRL-Pakets (Adobe Admin Console)

Diese Schritte sind mit Zugriff *Systemadministrator“ auf* Adobe Admin Console auszuführen.

###### Schritt 1: Beim Adobe Admin Console anmelden

1. Öffnen Sie einen Webbrowser und navigieren Sie zur [Adobe Admin Console](https://adminconsole.adobe.com/)
1. Melden Sie sich mit einem Konto mit Berechtigungen *Systemadministrator* an.
1. (Optional) Wenn Ihr Unternehmen Zugriff auf mehrere IMS-Organisationen hat, wählen Sie über die Option Organisationsauswahl oben rechts in Admin Console die richtige Organisation aus. In den meisten Kundenszenarien wäre dies bereits auf die Standardeinstellungen Ihrer Organisation festgelegt, da Benutzer in der Regel nur Zugriff auf ihre eigene Organisation haben.

###### Schritt 2: Erstellen des FRL-Pakets

1. Navigieren Sie in der Admin Console zur Registerkarte „Pakete“. Dies ist ein Adobe Admin Console-Paket, kein AEM-Paket.
1. Wählen Sie die Karte **Eingeschränkte Lizenz für Funktionen** und klicken Sie auf die Schaltfläche **Erste Schritte**. Stellen Sie sicher, dass Sie den richtigen Lizenztyp auswählen.
1. Konfigurieren **auf dem Bildschirm** Paket erstellen“ die Paketeinstellungen:

   | Einstellung | Empfohlener Wert | Anmerkungen |
   |---------|-------------------|-------|
   | Aktivierungsmethode | Offline | Empfohlene Option |
   | Berechtigung | PDF Generation (PDFG) | Erforderlich für AEM Forms PDF Generator-Funktionen |
   | Konfigurieren von Platform | Windows 64-Bit | Apple macOS wird derzeit nicht unterstützt |
   | Lokal aktivieren | „Betriebssystemsprache verwenden“ | Standardeinstellung |
   | Sprache | Ihre bevorzugte Sprache | Für die Benutzeroberfläche von Acrobat |
   | Apps auswählen - Verfügbare Programme | Adobe Acrobat in verfügbaren Programmen belassen. Nicht zur ausgewählten Anwendung verschieben | In [ 6 würden Sie &quot;Adobe Acrobat ](#step-6-download-and-install-adobe-acrobat-pro)&quot; von der Adobe Experience League -Seite herunterladen. |
   | Apps auswählen - Ausgewählte Programme | Nur Lizenzdatei in ausgewählten Anwendungen beibehalten | Standardeinstellung für die FRL-Bereitstellung |
   | Plug-ins | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | Optionen | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | abschließen | Paketname: &quot;Acrobat FRL AEM Forms&quot; | Namen beschreiben |

1. Klicken Sie **Erstellen**, um das Paket zu erstellen.

###### Schritt 3: Einem Benutzer Download-Berechtigungen erteilen

Es wird empfohlen, ein dediziertes Service-Konto für die Verwaltung von FRL-Paketen zu erstellen. Wenn Sie noch kein dediziertes Konto haben, können Sie [diesem Anleitungsvideo) ](https://www.youtube.com/watch?v=w8b36YX2TEM&t=59s), wie Sie einen neuen Benutzer zu Ihrer Adobe-Organisation hinzufügen.

Sobald Sie über das entsprechende Konto verfügen, führen Sie die folgenden Schritte aus, um Download-Berechtigungen zu gewähren:

1. Navigieren Sie in der Admin Console zur Registerkarte **Benutzer** .
2. Suchen oder erstellen Sie ein Benutzerkonto, um Download-Berechtigungen zu gewähren.
3. Klicken Sie auf den Namen des Benutzers, um sein Profil zu öffnen.
4. Klicken Sie auf das Symbol neben Benutzer **Administratorrechte bearbeiten**.
5. Weisen Sie dem **die Rolle** Bereitstellungsadministrator“ zu. Andere Administratorrollen funktionieren möglicherweise ebenfalls, Bereitstellungs-Admin ist jedoch die empfohlene Rolle. Klicken Sie auf **Speichern**.


##### Bereitstellen des FRL-Pakets (AEM Forms-Server)

Die folgenden Schritte werden auf dem AEM Forms-Server mit *lokalen Administratorrechten* über den Computer ausgeführt.

###### Schritt 4: Melden Sie sich bei dem Server an, auf dem AEM Forms als Administrator ausgeführt wird

Greifen Sie mithilfe der entsprechenden -Methode auf den Server zu, auf dem AEM Forms ausgeführt wird. Stellen Sie sicher, dass Sie ein Konto mit lokalen Administratorrechten für den Zugriff auf den Server verwenden.

###### Schritt 5: Deinstallieren der vorherigen Version von Acrobat (falls vorhanden)

**Kritisch:** Sichern Sie alle benutzerdefinierten Einstellungen, Profile oder Konfigurationen von Acrobat vor der Deinstallation.

1. Öffnen Sie die Windows-Systemsteuerung.
2. Navigieren Sie zu **Einstellungen** und öffnen Sie **Apps**.
3. Adobe Acrobat Suchen Sie **&#x200B;**&#x200B;in der Liste der installierten Programme
4. Wählen Sie **Deinstallieren** und befolgen Sie die Anweisungen, um die Anwendung zu entfernen. Starten Sie bei Aufforderung den Server neu
5. Stellen Sie sicher, dass alle klassischen Versionen des Programms deinstalliert sind. Verwenden Sie das [Adobe Acrobat Cleaner-Tool](https://helpx.adobe.com/acrobat/kb/remove-reader-dc-acrobat-dc.html) falls erforderlich, um eine vollständige Entfernung durchzuführen.

###### Schritt 6: Herunterladen und Installieren von Adobe Acrobat Pro

Nachdem Sie die vorherige Version deinstalliert haben, müssen Sie eine kompatible Version von Adobe Acrobat Pro herunterladen und installieren:

1. Navigieren Sie zur Seite [Adobe Acrobat DC-Downloads](https://helpx.adobe.com/in/acrobat/kb/acrobat-dc-downloads.html).
2. Navigieren Sie zum Abschnitt **Acrobat Pro** Installationsprogramm.
3. Laden Sie für die Verwendung mit AEM Forms PDF Generator das Installationsprogramm „Für Windows (32 Bit)“ herunter, da dies die von AEM Forms PDF Generator unterstützte Version ist.
4. Folgen Sie den Installationsanweisungen auf der Seite:
   * Extrahieren Sie die heruntergeladene ZIP-Datei in einen Ordner auf Ihrem Computer.
   * Navigieren Sie zur Datei Setup.exe (führen Sie die Datei Setup.exe nicht aus der ZIP-Datei aus)
   * Doppelklicken Sie auf Setup.exe, um die Installation zu starten
   * Folgen Sie den Anweisungen auf dem Bildschirm, um die Installation abzuschließen
5. Öffnen Sie nach der Installation Adobe Acrobat Pro und schließen Sie die Ersteinrichtung ab, indem Sie alle Begrüßungsdialoge schließen.
6. Überprüfen Sie die Installation, indem Sie eine einfache PDF erstellen.

###### Schritt 7: Herunterladen des FRL-Pakets

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) mit dem *Benutzerkonto* an, für das Sie in Schritt 3 Download-Berechtigungen erteilt haben.
1. Navigieren Sie zur Registerkarte **Pakete**.
1. Suchen Sie das FRL-Paket, das Sie in Schritt 2 erstellt haben (mit dem Namen &quot;Acrobat FRL AEM Forms&quot; oder Ihr benutzerdefinierter Paketname).
1. Klicken Sie **Herunterladen**, um das Paket auf den Server herunterzuladen.

###### Schritt 8: Bereitstellen des Pakets

1. **Paket extrahieren:** Extrahieren Sie den Inhalt der heruntergeladenen ZIP-Datei in ein Verzeichnis auf dem Server (z. B. `C:\AcrobatFRL`). Stellen Sie sicher, dass der Zugriff auf das Extraktionsverzeichnis leicht ist.

2. **Eingabeaufforderung als Administrator öffnen (Windows):** Klicken Sie mit der rechten Maustaste auf die Schaltfläche Start und wählen Sie „Eingabeaufforderung (Admin)“ oder „Windows PowerShell (Admin)“

3. **Navigieren Sie zum Extraktionsverzeichnis:**

   ```cmd
   cd C:\AcrobatFRL
   ```

4. **Führen Sie den Aktivierungsbefehl aus:**

   ```cmd
   # Command syntax
   adobe-licensing-toolkit.exe -p -i -f [JSON_FILE_NAME].json
   
   # Example with actual values
   adobe-licensing-toolkit.exe -p -i -f ngl-preconditioning-data.json
   ```

   > **Wichtig:**
   > * Ersetzen Sie `<JSON_FILE_NAME>.json` durch den *exakten* Dateinamen der JSON-Datei im extrahierten Paket.
   > * Beim JSON-Dateinamen wird zwischen Groß- und Kleinschreibung unterschieden.
   > * Überprüfen Sie den Dateinamen auf mögliche Rechtschreibfehler.

   **Erwartete Ausgabe:**

   ```
   Adobe Licensing Toolkit (1.1.0.130)
   Operation Successfully Completed
   ```

   > **Hinweis:** Der Aktivierungsvorgang kann etwa 30 Sekunden dauern.

5. **Verstehen der Befehlsparameter:**

   | Parameter | Beschreibung |
   |-----------|-------------|
   | `-p` | Gibt die Plattform an (erkennt das Betriebssystem automatisch) |
   | `-i` | Veranlasst das Tool zur Installation und Aktivierung der Lizenz |
   | `-f` | Gibt den Pfad zur JSON-Lizenzdatei an |

###### Schritt 9: AEM Forms-Server starten

Führen Sie nach Abschluss aller Prozesse einen Schnellaktionstest durch, um zu bestätigen, dass die Installation gültig ist:

1. Starten Sie den AEM Forms-Server von einer Befehlszeilenkonsole aus in einer interaktiven Benutzersitzung. (Melden Sie sich beim -Server an und starten Sie AEM Forms manuell über die Befehlszeile.)
2. Lassen Sie die Benutzersitzung nach dem Starten des Servers aktiv. Melden Sie sich nicht vom Computer ab, da dadurch der Serverprozess beendet wird. Sie können das Fenster „Remote Desktop (RDP)“ sicher schließen, ohne sich abzumelden. Der Server läuft weiter, solange die Sitzung aktiv bleibt.
3. Um die Zuverlässigkeit zu verbessern, konfigurieren Sie eine Startaufgabe oder eine geplante Aufgabe, um den AEM Forms-Server automatisch zu starten, wenn sich der Benutzer anmeldet.

###### Schritt 10 Testen des PDF Generator-Service

1. Öffnen der AEM Forms-Admin-Benutzeroberfläche
2. Navigieren Sie zum PDF Generator-Service
3. Konvertieren eines einfachen Microsoft Office-Dokuments in PDF
4. Überprüfen, ob die Konvertierung erfolgreich abgeschlossen wurde

#### Acrobat-Version nach FRL-Aktivierung überprüfen

1. Öffnen Sie Adobe Acrobat Pro DC auf dem Server
2. Navigieren Sie zu → Informationen zu Adobe Acrobat Pro DC
3. Überprüfen, ob die Versionsnummer mit der erwarteten Version übereinstimmt
4. Bestätigen Sie, dass der Lizenzstatus als aktiviert angezeigt wird

>[!TAB Volumenlizenz - Einzelbenutzer]

#### Einrichten einer funktionsbeschränkten Lizenzierung (FRL) für Adobe Acrobat auf Ihrem AEM Forms-Server

Bei diesen Schritten wird davon ausgegangen, dass Sie sowohl auf dem Adobe Admin Console als auch auf dem Server, auf dem AEM Forms ausgeführt wird, über die erforderlichen Administratorrechte verfügen.

##### Vorbereiten des FRL-Pakets (Adobe Admin Console)

Diese Schritte sind mit Zugriff *Systemadministrator“ auf* Adobe Admin Console auszuführen.

###### Schritt 1: Beim Adobe Admin Console anmelden

1. Öffnen Sie einen Webbrowser und navigieren Sie zur [Adobe Admin Console](https://adminconsole.adobe.com/)
1. Melden Sie sich mit einem Konto mit Berechtigungen *Systemadministrator* an.
1. (Optional) Wenn Ihr Unternehmen Zugriff auf mehrere IMS-Organisationen hat, wählen Sie über die Option Organisationsauswahl oben rechts in Admin Console die richtige Organisation aus. In den meisten Kundenszenarien wäre dies bereits auf die Standardeinstellungen Ihrer Organisation festgelegt, da Benutzer in der Regel nur Zugriff auf ihre eigene Organisation haben.

###### Schritt 2: Erstellen des FRL-Pakets

1. Navigieren Sie in der Admin Console zur Registerkarte „Pakete“. Dies ist ein Adobe Admin Console-Paket, kein AEM-Paket.
1. Wählen Sie die Karte **Eingeschränkte Lizenz für Funktionen** und klicken Sie auf die Schaltfläche **Erste Schritte**. Stellen Sie sicher, dass Sie den richtigen Lizenztyp auswählen.
1. Konfigurieren **auf dem Bildschirm** Paket erstellen“ die Paketeinstellungen:

   | Einstellung | Empfohlener Wert | Anmerkungen |
   |---------|-------------------|-------|
   | Aktivierungsmethode | Offline | Empfohlene Option |
   | Berechtigung | PDF Generation (PDFG) | Erforderlich für AEM Forms PDF Generator-Funktionen |
   | Konfigurieren von Platform | Windows 64-Bit | Apple macOS wird derzeit nicht unterstützt |
   | Lokal aktivieren | „Betriebssystemsprache verwenden“ | Standardeinstellung |
   | Sprache | Ihre bevorzugte Sprache | Für die Benutzeroberfläche von Acrobat |
   | Apps auswählen - Verfügbare Programme | Adobe Acrobat in verfügbaren Programmen belassen. Nicht zur ausgewählten Anwendung verschieben | In [ 6 würden Sie &quot;Adobe Acrobat ](#step-6-download-and-install-adobe-acrobat-pro)&quot; von der Adobe Experience League -Seite herunterladen. |
   | Apps auswählen - Ausgewählte Programme | Nur Lizenzdatei in ausgewählten Anwendungen beibehalten | Standardeinstellung für die FRL-Bereitstellung |
   | Plug-ins | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | Optionen | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | abschließen | Paketname: &quot;Acrobat FRL AEM Forms&quot; | Namen beschreiben |

1. Klicken Sie **Erstellen**, um das Paket zu erstellen.

###### Schritt 3: Einem Benutzer Download-Berechtigungen erteilen

Es wird empfohlen, ein dediziertes Service-Konto für die Verwaltung von FRL-Paketen zu erstellen. Wenn Sie noch kein dediziertes Konto haben, können Sie [diesem Anleitungsvideo) ](https://www.youtube.com/watch?v=w8b36YX2TEM&t=59s), wie Sie einen neuen Benutzer zu Ihrer Adobe-Organisation hinzufügen.

Sobald Sie über das entsprechende Konto verfügen, führen Sie die folgenden Schritte aus, um Download-Berechtigungen zu gewähren:

1. Navigieren Sie in der Admin Console zur Registerkarte **Benutzer** .
2. Suchen oder erstellen Sie ein Benutzerkonto, um Download-Berechtigungen zu gewähren.
3. Klicken Sie auf den Namen des Benutzers, um sein Profil zu öffnen.
4. Klicken Sie auf das Symbol neben Benutzer **Administratorrechte bearbeiten**.
5. Weisen Sie dem **die Rolle** Bereitstellungsadministrator“ zu. Andere Administratorrollen funktionieren möglicherweise ebenfalls, Bereitstellungs-Admin ist jedoch die empfohlene Rolle. Klicken Sie auf **Speichern**.


##### Bereitstellen des FRL-Pakets (AEM Forms-Server)

Die folgenden Schritte werden auf dem AEM Forms-Server mit *lokalen Administratorrechten* über den Computer ausgeführt.

###### Schritt 4: Melden Sie sich bei dem Server an, auf dem AEM Forms als Administrator ausgeführt wird

Greifen Sie mithilfe der entsprechenden -Methode auf den Server zu, auf dem AEM Forms ausgeführt wird. Stellen Sie sicher, dass Sie ein Konto mit lokalen Administratorrechten für den Zugriff auf den Server verwenden.

###### Schritt 5: Deinstallieren der vorherigen Version von Acrobat (falls vorhanden)

**Kritisch:** Sichern Sie alle benutzerdefinierten Einstellungen, Profile oder Konfigurationen von Acrobat vor der Deinstallation.

1. Öffnen Sie die Windows-Systemsteuerung.
2. Navigieren Sie zu **Einstellungen** und öffnen Sie **Apps**.
3. Adobe Acrobat Suchen Sie **&#x200B;**&#x200B;in der Liste der installierten Programme
4. Wählen Sie **Deinstallieren** und befolgen Sie die Anweisungen, um die Anwendung zu entfernen. Starten Sie bei Aufforderung den Server neu
5. Stellen Sie sicher, dass alle klassischen Versionen des Programms deinstalliert sind. Verwenden Sie das [Adobe Acrobat Cleaner-Tool](https://helpx.adobe.com/acrobat/kb/remove-reader-dc-acrobat-dc.html) falls erforderlich, um eine vollständige Entfernung durchzuführen.

###### Schritt 6: Herunterladen und Installieren von Adobe Acrobat Pro

Nachdem Sie die vorherige Version deinstalliert haben, müssen Sie eine kompatible Version von Adobe Acrobat Pro herunterladen und installieren:

1. Navigieren Sie zur Seite [Adobe Acrobat DC-Downloads](https://helpx.adobe.com/in/acrobat/kb/acrobat-dc-downloads.html).
2. Navigieren Sie zum Abschnitt **Acrobat Pro** Installationsprogramm.
3. Laden Sie für die Verwendung mit AEM Forms PDF Generator das Installationsprogramm „Für Windows (32 Bit)“ herunter, da dies die von AEM Forms PDF Generator unterstützte Version ist.
4. Folgen Sie den Installationsanweisungen auf der Seite:
   * Extrahieren Sie die heruntergeladene ZIP-Datei in einen Ordner auf Ihrem Computer.
   * Navigieren Sie zur Datei Setup.exe (führen Sie die Datei Setup.exe nicht aus der ZIP-Datei aus)
   * Doppelklicken Sie auf Setup.exe, um die Installation zu starten
   * Folgen Sie den Anweisungen auf dem Bildschirm, um die Installation abzuschließen
5. Öffnen Sie nach der Installation Adobe Acrobat Pro und schließen Sie die Ersteinrichtung ab, indem Sie alle Begrüßungsdialoge schließen.
6. Überprüfen Sie die Installation, indem Sie eine einfache PDF erstellen.

###### Schritt 7: Herunterladen des FRL-Pakets

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) mit dem *Benutzerkonto* an, für das Sie in Schritt 3 Download-Berechtigungen erteilt haben.
1. Navigieren Sie zur Registerkarte **Pakete**.
1. Suchen Sie das FRL-Paket, das Sie in Schritt 2 erstellt haben (mit dem Namen &quot;Acrobat FRL AEM Forms&quot; oder Ihr benutzerdefinierter Paketname).
1. Klicken Sie **Herunterladen**, um das Paket auf den Server herunterzuladen.

###### Schritt 8: Bereitstellen des Pakets

1. **Paket extrahieren:** Extrahieren Sie den Inhalt der heruntergeladenen ZIP-Datei in ein Verzeichnis auf dem Server (z. B. `C:\AcrobatFRL`). Stellen Sie sicher, dass der Zugriff auf das Extraktionsverzeichnis leicht ist.

2. **Eingabeaufforderung als Administrator öffnen (Windows):** Klicken Sie mit der rechten Maustaste auf die Schaltfläche Start und wählen Sie „Eingabeaufforderung (Admin)“ oder „Windows PowerShell (Admin)“

3. **Navigieren Sie zum Extraktionsverzeichnis:**

   ```cmd
   cd C:\AcrobatFRL
   ```

4. **Führen Sie den Aktivierungsbefehl aus:**

   ```cmd
   # Command syntax
   adobe-licensing-toolkit.exe -p -i -f [JSON_FILE_NAME].json
   
   # Example with actual values
   adobe-licensing-toolkit.exe -p -i -f ngl-preconditioning-data.json
   ```

   > **Wichtig:**
   > * Ersetzen Sie `<JSON_FILE_NAME>.json` durch den *exakten* Dateinamen der JSON-Datei im extrahierten Paket.
   > * Beim JSON-Dateinamen wird zwischen Groß- und Kleinschreibung unterschieden.
   > * Überprüfen Sie den Dateinamen auf mögliche Rechtschreibfehler.

   **Erwartete Ausgabe:**

   ```
   Adobe Licensing Toolkit (1.1.0.130)
   Operation Successfully Completed
   ```

   > **Hinweis:** Der Aktivierungsvorgang kann etwa 30 Sekunden dauern.

5. **Verstehen der Befehlsparameter:**

   | Parameter | Beschreibung |
   |-----------|-------------|
   | `-p` | Gibt die Plattform an (erkennt das Betriebssystem automatisch) |
   | `-i` | Veranlasst das Tool zur Installation und Aktivierung der Lizenz |
   | `-f` | Gibt den Pfad zur JSON-Lizenzdatei an |

###### Schritt 9: AEM Forms-Server starten

Führen Sie nach Abschluss aller Prozesse einen Schnellaktionstest durch, um zu bestätigen, dass die Installation gültig ist:

1. Verwenden Sie Remote Desktop (RDP), um sich beim -Server anzumelden und den AEM Forms-Server mithilfe von Services zu starten.
2. Sobald der Server ausgeführt wird, schließen Sie nicht einfach das RDP-Fenster. Melden Sie sich stattdessen ordnungsgemäß ab, indem Sie sich vom Benutzer abmelden. Dadurch wird sichergestellt, dass die Sitzung sauber endet, während der Service im Hintergrund weiter ausgeführt wird.

###### Schritt 10: Testen des PDF Generator-Service

Führen Sie nach Abschluss aller Prozesse einen Schnellaktionstest durch, um zu bestätigen, dass die Installation gültig ist:

1. Öffnen der AEM Forms-Admin-Benutzeroberfläche
2. Navigieren Sie zum PDF Generator-Service
3. Konvertieren eines einfachen Microsoft Office-Dokuments in PDF
4. Überprüfen, ob die Konvertierung erfolgreich abgeschlossen wurde

###### Schritt 11: Acrobat-Version nach FRL-Aktivierung überprüfen

1. Öffnen Sie Adobe Acrobat Pro DC auf dem Server
2. Navigieren Sie zu → Informationen zu Adobe Acrobat Pro DC
3. Überprüfen, ob die Versionsnummer mit der erwarteten Version übereinstimmt
4. Bestätigen Sie, dass der Lizenzstatus als aktiviert angezeigt wird

>[!TAB Volumenlizenz - Mehrere Benutzer]

#### Einrichten einer funktionsbeschränkten Lizenzierung (FRL) für Adobe Acrobat auf Ihrem AEM Forms-Server

Bei diesen Schritten wird davon ausgegangen, dass Sie sowohl auf dem Adobe Admin Console als auch auf dem Server, auf dem AEM Forms ausgeführt wird, über die erforderlichen Administratorrechte verfügen.

##### Vorbereiten des FRL-Pakets (Adobe Admin Console)

Diese Schritte sind mit Zugriff *Systemadministrator“ auf* Adobe Admin Console auszuführen.

###### Schritt 1: Beim Adobe Admin Console anmelden

1. Öffnen Sie einen Webbrowser und navigieren Sie zur [Adobe Admin Console](https://adminconsole.adobe.com/)
1. Melden Sie sich mit einem Konto mit Berechtigungen *Systemadministrator* an.
1. (Optional) Wenn Ihr Unternehmen Zugriff auf mehrere IMS-Organisationen hat, wählen Sie über die Option Organisationsauswahl oben rechts in Admin Console die richtige Organisation aus. In den meisten Kundenszenarien wäre dies bereits auf die Standardeinstellungen Ihrer Organisation festgelegt, da Benutzer in der Regel nur Zugriff auf ihre eigene Organisation haben.

###### Schritt 2: Erstellen des FRL-Pakets

1. Navigieren Sie in der Admin Console zur Registerkarte „Pakete“. Dies ist ein Adobe Admin Console-Paket, kein AEM-Paket.
1. Wählen Sie die Karte **Eingeschränkte Lizenz für Funktionen** und klicken Sie auf die Schaltfläche **Erste Schritte**. Stellen Sie sicher, dass Sie den richtigen Lizenztyp auswählen.
1. Konfigurieren **auf dem Bildschirm** Paket erstellen“ die Paketeinstellungen:

   | Einstellung | Empfohlener Wert | Anmerkungen |
   |---------|-------------------|-------|
   | Aktivierungsmethode | Offline | Empfohlene Option |
   | Berechtigung | PDF Generation (PDFG) | Erforderlich für AEM Forms PDF Generator-Funktionen |
   | Konfigurieren von Platform | Windows 64-Bit | Apple macOS wird derzeit nicht unterstützt |
   | Lokal aktivieren | „Betriebssystemsprache verwenden“ | Standardeinstellung |
   | Sprache | Ihre bevorzugte Sprache | Für die Benutzeroberfläche von Acrobat |
   | Apps auswählen - Verfügbare Programme | Adobe Acrobat in verfügbaren Programmen belassen. Nicht zur ausgewählten Anwendung verschieben | In [ 6 würden Sie &quot;Adobe Acrobat ](#step-6-download-and-install-adobe-acrobat-pro)&quot; von der Adobe Experience League -Seite herunterladen. |
   | Apps auswählen - Ausgewählte Programme | Nur Lizenzdatei in ausgewählten Anwendungen beibehalten | Standardeinstellung für die FRL-Bereitstellung |
   | Plug-ins | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | Optionen | Keine Änderungen auf diesem Bildschirm vornehmen | |
   | abschließen | Paketname: &quot;Acrobat FRL AEM Forms&quot; | Namen beschreiben |

1. Klicken Sie **Erstellen**, um das Paket zu erstellen.

###### Schritt 3: Einem Benutzer Download-Berechtigungen erteilen

Es wird empfohlen, ein dediziertes Service-Konto für die Verwaltung von FRL-Paketen zu erstellen. Wenn Sie noch kein dediziertes Konto haben, können Sie [diesem Anleitungsvideo) ](https://www.youtube.com/watch?v=w8b36YX2TEM&t=59s), wie Sie einen neuen Benutzer zu Ihrer Adobe-Organisation hinzufügen.

Sobald Sie über das entsprechende Konto verfügen, führen Sie die folgenden Schritte aus, um Download-Berechtigungen zu gewähren:

1. Navigieren Sie in der Admin Console zur Registerkarte **Benutzer** .
2. Suchen oder erstellen Sie ein Benutzerkonto, um Download-Berechtigungen zu gewähren.
3. Klicken Sie auf den Namen des Benutzers, um sein Profil zu öffnen.
4. Klicken Sie auf das Symbol neben Benutzer **Administratorrechte bearbeiten**.
5. Weisen Sie dem **die Rolle** Bereitstellungsadministrator“ zu. Andere Administratorrollen funktionieren möglicherweise ebenfalls, Bereitstellungs-Admin ist jedoch die empfohlene Rolle. Klicken Sie auf **Speichern**.


##### Bereitstellen des FRL-Pakets (AEM Forms-Server)

Die folgenden Schritte werden auf dem AEM Forms-Server mit *lokalen Administratorrechten* über den Computer ausgeführt.

###### Schritt 4: Melden Sie sich bei dem Server an, auf dem AEM Forms als Administrator ausgeführt wird

Greifen Sie mithilfe der entsprechenden -Methode auf den Server zu, auf dem AEM Forms ausgeführt wird. Stellen Sie sicher, dass Sie ein Konto mit lokalen Administratorrechten für den Zugriff auf den Server verwenden.

###### Schritt 5: Deinstallieren der vorherigen Version von Acrobat (falls vorhanden)

**Kritisch:** Sichern Sie alle benutzerdefinierten Einstellungen, Profile oder Konfigurationen von Acrobat vor der Deinstallation.

1. Öffnen Sie die Windows-Systemsteuerung.
2. Navigieren Sie zu **Einstellungen** und öffnen Sie **Apps**.
3. Adobe Acrobat Suchen Sie **&#x200B;**&#x200B;in der Liste der installierten Programme
4. Wählen Sie **Deinstallieren** und befolgen Sie die Anweisungen, um die Anwendung zu entfernen. Starten Sie bei Aufforderung den Server neu
5. Stellen Sie sicher, dass alle klassischen Versionen des Programms deinstalliert sind. Verwenden Sie das [Adobe Acrobat Cleaner-Tool](https://helpx.adobe.com/acrobat/kb/remove-reader-dc-acrobat-dc.html) falls erforderlich, um eine vollständige Entfernung durchzuführen.

###### Schritt 6: Herunterladen und Installieren von Adobe Acrobat Pro

Nachdem Sie die vorherige Version deinstalliert haben, müssen Sie eine kompatible Version von Adobe Acrobat Pro herunterladen und installieren:

1. Navigieren Sie zur Seite [Adobe Acrobat DC-Downloads](https://helpx.adobe.com/in/acrobat/kb/acrobat-dc-downloads.html).
2. Navigieren Sie zum Abschnitt **Acrobat Pro** Installationsprogramm.
3. Laden Sie für die Verwendung mit AEM Forms PDF Generator das Installationsprogramm „Für Windows (32 Bit)“ herunter, da dies die von AEM Forms PDF Generator unterstützte Version ist.
4. Folgen Sie den Installationsanweisungen auf der Seite:
   * Extrahieren Sie die heruntergeladene ZIP-Datei in einen Ordner auf Ihrem Computer.
   * Navigieren Sie zur Datei Setup.exe (führen Sie die Datei Setup.exe nicht aus der ZIP-Datei aus)
   * Doppelklicken Sie auf Setup.exe, um die Installation zu starten
   * Folgen Sie den Anweisungen auf dem Bildschirm, um die Installation abzuschließen
5. Öffnen Sie nach der Installation Adobe Acrobat Pro und schließen Sie die Ersteinrichtung ab, indem Sie alle Begrüßungsdialoge schließen.
6. Überprüfen Sie die Installation, indem Sie eine einfache PDF erstellen.

###### Schritt 7: Herunterladen des FRL-Pakets

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) mit dem *Benutzerkonto* an, für das Sie in Schritt 3 Download-Berechtigungen erteilt haben.
1. Navigieren Sie zur Registerkarte **Pakete**.
1. Suchen Sie das FRL-Paket, das Sie in Schritt 2 erstellt haben (mit dem Namen &quot;Acrobat FRL AEM Forms&quot; oder Ihr benutzerdefinierter Paketname).
1. Klicken Sie **Herunterladen**, um das Paket auf den Server herunterzuladen.

###### Schritt 8: Bereitstellen des Pakets

1. **Paket extrahieren:** Extrahieren Sie den Inhalt der heruntergeladenen ZIP-Datei in ein Verzeichnis auf dem Server (z. B. `C:\AcrobatFRL`). Stellen Sie sicher, dass der Zugriff auf das Extraktionsverzeichnis leicht ist.

2. **Eingabeaufforderung als Administrator öffnen (Windows):** Klicken Sie mit der rechten Maustaste auf die Schaltfläche Start und wählen Sie „Eingabeaufforderung (Admin)“ oder „Windows PowerShell (Admin)“

3. **Navigieren Sie zum Extraktionsverzeichnis:**

   ```cmd
   cd C:\AcrobatFRL
   ```

4. **Führen Sie den Aktivierungsbefehl aus:**

   ```cmd
   # Command syntax
   adobe-licensing-toolkit.exe -p -i -f [JSON_FILE_NAME].json
   
   # Example with actual values
   adobe-licensing-toolkit.exe -p -i -f ngl-preconditioning-data.json
   ```

   > **Wichtig:**
   > * Ersetzen Sie `<JSON_FILE_NAME>.json` durch den *exakten* Dateinamen der JSON-Datei im extrahierten Paket.
   > * Beim JSON-Dateinamen wird zwischen Groß- und Kleinschreibung unterschieden.
   > * Überprüfen Sie den Dateinamen auf mögliche Rechtschreibfehler.

   **Erwartete Ausgabe:**

   ```
   Adobe Licensing Toolkit (1.1.0.130)
   Operation Successfully Completed
   ```

   > **Hinweis:** Der Aktivierungsvorgang kann etwa 30 Sekunden dauern.

5. **Verstehen der Befehlsparameter:**

   | Parameter | Beschreibung |
   |-----------|-------------|
   | `-p` | Gibt die Plattform an (erkennt das Betriebssystem automatisch) |
   | `-i` | Veranlasst das Tool zur Installation und Aktivierung der Lizenz |
   | `-f` | Gibt den Pfad zur JSON-Lizenzdatei an |

###### Schritt 9: AEM Forms-Server starten

Führen Sie nach Abschluss aller Prozesse einen Schnellaktionstest durch, um zu bestätigen, dass die Installation gültig ist:

1. Starten Sie den AEM Forms-Server von einer Befehlszeilenkonsole aus in einer interaktiven Benutzersitzung. (Melden Sie sich beim -Server an und starten Sie AEM Forms manuell über die Befehlszeile.)
2. Lassen Sie die Benutzersitzung nach dem Starten des Servers aktiv. Melden Sie sich nicht vom Computer ab, da dadurch der Serverprozess beendet wird. Sie können das Fenster „Remote Desktop (RDP)“ sicher schließen, ohne sich abzumelden. Der Server läuft weiter, solange die Sitzung aktiv bleibt.
3. Um die Zuverlässigkeit zu verbessern, konfigurieren Sie eine Startaufgabe oder eine geplante Aufgabe, um den AEM Forms-Server automatisch zu starten, wenn sich der Benutzer anmeldet.

###### Schritt 10: Testen des PDF Generator-Service

Führen Sie nach Abschluss aller Prozesse einen Schnellaktionstest durch, um zu bestätigen, dass die Installation gültig ist:

1. Öffnen der AEM Forms-Admin-Benutzeroberfläche
2. Navigieren Sie zum PDF Generator-Service
3. Konvertieren eines einfachen Microsoft Office-Dokuments in PDF
4. Überprüfen, ob die Konvertierung erfolgreich abgeschlossen wurde

#### Acrobat-Version nach FRL-Aktivierung überprüfen

1. Öffnen Sie Adobe Acrobat Pro DC auf dem Server
2. Navigieren Sie zu → Informationen zu Adobe Acrobat Pro DC
3. Überprüfen, ob die Versionsnummer mit der erwarteten Version übereinstimmt
4. Bestätigen Sie, dass der Lizenzstatus als aktiviert angezeigt wird

>[!ENDTABS]



### Deaktivieren des abgesicherten Modus beim Start in Acrobat

Nach der Aktivierung der eingeschränkten Funktionslizenzierung (FRL) und der Überprüfung der Acrobat-Aktivierung wird empfohlen, den geschützten Modus beim Start in Adobe Acrobat zu deaktivieren, um die Kompatibilität mit AEM Forms PDF Generator sicherzustellen.

Führen Sie die folgenden Schritte aus:

1. Öffnen Sie **Adobe Acrobat Pro DC** auf dem Server.
2. Navigieren Sie **Menü** > **Voreinstellungen**.
3. Wählen Sie im Fenster „Voreinstellungen **im linken Bereich die Option** Sicherheit (Erweitert)“ aus.
4. Aktivieren Sie im **Sandbox** Schutz **&#x200B;**&#x200B;die Option **Geschützten Modus beim Start aktivieren“**.
5. Klicken Sie auf **Ja**, wenn Sie zur Bestätigung aufgefordert werden.
6. Klicken Sie **OK**, um Ihre Änderungen zu speichern und das Fenster „Voreinstellungen“ zu schließen.
7. Starten Sie Adobe Acrobat Pro DC neu, damit die Änderungen wirksam werden.

>[!NOTE]
>
>Die Deaktivierung des abgesicherten Modus ist für Server-seitige Automatisierungsszenarien wie AEM Forms PDF Generator erforderlich. Diese Einstellung sollte nur in dedizierten Serverumgebungen geändert werden, nicht auf Desktops für Endbenutzer.

Weitere Informationen finden Sie in der [Adobe-Dokumentation zum geschützten Modus](https://helpx.adobe.com/de/acrobat/kb/protected-mode-troubleshooting-reader.html).



### Einrichten der Umgebungsvariablen {#setup-environment-variables}

Legen Sie Umgebungsvariablen für das 64-Bit-Java Development Kit, Anwendungen von Drittanbietern und Adobe Acrobat fest. Die Umgebungsvariablen müssen den absoluten Pfad der ausführbaren Datei enthalten, über welche die entsprechende Anwendung gestartet wird. In der nachstehenden Tabelle werden beispielsweise Umgebungsvariablen für einige Anwendungen aufgelistet:

<table>
 <tbody>
  <tr>
   <td><p><strong>Anwendung</strong></p> </td>
   <td><p><strong>Umgebungsvariable</strong></p> </td>
   <td><p><strong>Beispiel</strong></p> </td>
  </tr>
  <tr>
   <td><p><strong>JDK (64-Bit)</strong></p> </td>
   <td><p>JAVA_HOME</p> </td>
   <td><p>C:\Program Files\Java\jdk11</p> </td>
  </tr>
  <tr>
   <td><p><strong>Adobe Acrobat</strong></p> </td>
   <td><p>Acrobat_PATH</p> </td>
   <td><p>C:\Programme (x86)\Adobe\Acrobat 2015\Acrobat\Acrobat.ex</p> </td>
  </tr>
  <tr>
   <td><p><strong>Editor</strong></p> </td>
   <td><p>Notepad_PATH</p> </td>
   <td><p>C:\WINDOWS\notepad.exe<br /> <strong></strong></p> </td>
  </tr>
  <tr>
   <td><p><strong>OpenOffice</strong></p> </td>
   <td><p>OpenOffice_PATH</p> </td>
   <td><p>C:\Programme (x86)\OpenOffice 4</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Bei allen Umgebungsvariablen und den entsprechenden Pfaden wird zwischen Groß- und Kleinschreibung unterschieden.
>* „JAVA_HOME“ und „Acrobat_PATH“ (nur Windows) sind erforderliche Umgebungsvariablen.
>* Die Umgebungsvariable OpenOffice_PATH wird auf den Installationsordner statt auf den Pfad der ausführbaren Datei festgelegt.
>* Richten Sie für Microsoft® Office-Programme wie Word, PowerPoint, Excel und Project oder für AutoCAD keine Umgebungsvariablen ein. Wenn diese Anwendungen auf dem Server installiert sind, startet der Generate PDF-Dienst diese Anwendungen automatisch.
>* Installieren Sie auf UNIX-basierten Plattformen OpenOffice als /root. Wenn OpenOffice nicht als „root“ installiert ist, kann der PDF Generator-Dienst OpenOffice-Dokumente nicht in PDF-Dokumente konvertieren. Falls Sie OpenOffice unter einem anderen Benutzer als /root installieren und ausführen müssen, gewähren Sie dem betreffenden Benutzer sudo-Rechte.
>* Wenn Sie OpenOffice auf einer UNIX-basierten Plattform verwenden, führen Sie den folgenden Befehl aus, um die PATH-Variable festzulegen:\
> `export OpenOffice_PATH=/opt/openoffice.org4`
>* Führen Sie auf SUSE® Linux®-basierten Plattformen (SLES 15 SP6 oder höher) die folgenden Schritte aus, um OpenOffice einzurichten:
>     * Installieren Sie die neueste verfügbare 32-Bit-Variante von `OpenOffice 4.1.x` in einem Verzeichnis wie etwa `/opt/openoffice4`.
>     * Legen Sie die Umgebungsvariable `OpenOffice_PATH` so fest, dass sie auf diesen Speicherort verweist. Beispiel: `OpenOffice_PATH=/opt/openoffice4`.
>     * Stellen Sie sicher, dass die Variable `OpenOffice_PATH` global festgelegt ist (z. B. mithilfe von `/etc/profile` oder der systemspezifischen Entsprechung), damit sie für alle Benutzer bei der Anmeldung verfügbar ist.

### (Nur für IBM® WebSphere®) Konfigurieren des IBM® SSL-Socket-Anbieters {#only-for-ibm-websphere-configure-ibm-ssl-socket-provider}

Führen Sie die folgenden Schritte aus, um den IBM® SSL-Socket-Anbieter zu konfigurieren:

1. Erstellen Sie eine Kopie der java.security-Datei. Der Standardspeicherort der Datei lautet `[WebSphere_installation_directory]\Appserver\java_[version]\jre\lib\security`.
1. Öffnen Sie die kopierte Datei „java.security“ zur Bearbeitung.
1. Ändern Sie den Standardwert für SSL-Socket-Factories, um die JSSE2-Factories anstelle der standardmäßigen IBM® WebSphere®-Factories zu verwenden:

   **Standardinhalt:**

   ```shell
   #ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
   #ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
   #WebSphere socket factories (in cryptosf.jar)
   ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
   ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
   ```

   **Geänderter Inhalt:**

   ```shell
   ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
   ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
   
   #WebSphere socket factories (in cryptosf.jar)
   #ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
   #ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
   ```

1. Damit der AEM Forms-Server die aktualisierte Datei „java.security“ verwenden kann, fügen Sie beim Starten des AEM Forms-Servers das folgende Java-Argument hinzu:

   `-Djava.security.properties= [path of newly created Java.security file].`

### (Nur Windows) Konfigurieren der Dateiblockeinstellungen für Microsoft® Office {#configure-the-file-block-settings-for-microsoft-office}

Ändern Sie die Einstellungen für das Sicherheitscenter von Microsoft® Office, um den PDF Generator-Service für die Konvertierung von Dateien zu aktivieren, die mit älteren Versionen von Microsoft® Office erstellt wurden.

1. Öffnen Sie eine Microsoft® Office-Anwendung. Beispiel: Microsoft® Word. Navigieren Sie zu **[!UICONTROL Datei]** > **[!UICONTROL Optionen]**. Das Dialogfeld „Optionen“ wird angezeigt.

1. Klicken Sie auf **[!UICONTROL Trust Center]** und dann auf **[!UICONTROL Trust Center-Einstellungen]**.
1. Klicken Sie in den **[!UICONTROL Trust Center-Einstellungen]** auf **[!UICONTROL Zugriffsschutzeinstellungen]**.
1. Deaktivieren Sie in der Liste **[!UICONTROL Dateityp]** die Option **[!UICONTROL Öffnen]** für den Dateityp, für den es dem PDF Generator-Dienst erlaubt werden soll, Dateien in PDF-Dokumente zu konvertieren.

### (Nur Windows) Gewähren der Berechtigung zum Ersetzen von Token auf Prozessebene {#grant-the-replace-a-process-level-token-privilege}

Das Benutzerkonto, das zum Starten des Anwendungsservers verwendet wird, muss die Berechtigung **Ersetzen eines Tokens auf Prozessebene** haben. Das lokale Systemkonto hat standardmäßig die Berechtigung **Ersetzen eines Tokens auf Prozessebene**. Für den Server, die mit einem Benutzer der lokalen Administratorgruppe ausgeführt werden, muss die Berechtigung explizit gewährt werden. Führen Sie die folgenden Schritte durch, um die Berechtigung zu gewähren:

1. Öffnen Sie den Gruppenrichtlinien-Editor für Microsoft® Windows. Klicken Sie zum Öffnen des Gruppenrichtlinien-Editors auf **[!UICONTROL Start]**, geben Sie im Suchfeld **gpedit.msc** ein und klicken Sie auf **[!UICONTROL Gruppenrichtlinien-Editor]**.
1. Navigieren Sie zu **[!UICONTROL Lokale Computerrichtlinie]** > **[!UICONTROL Computer-Konfiguration]** > **[!UICONTROL Windows-Einstellungen]** > **[!UICONTROL Sicherheitseinstellungen]** > **[!UICONTROL Lokale Richtlinien]** > **[!UICONTROL Zuweisung von Benutzerrechten]** und bearbeiten Sie die Richtlinie **[!UICONTROL Token auf Prozessebene ersetzen]**, damit diese in der Gruppe „Admins“ übernommen wird.
1. Fügen Sie dem Eintrag „Token auf Prozessebene ersetzen“ Benutzende hinzu.

>[!NOTE]
>
> Wenn der AEM-Server wie oben beschrieben als Dienst unter dem LocalSystem-Konto (LSA) ausgeführt wird, ist es nicht erforderlich, diese Berechtigung explizit einer Benutzerin oder einem Benutzer zuzuweisen.

### (Nur Windows) Aktivieren des PDF Generator-Services für Benutzer, die keine Administratoren sind {#enable-the-pdf-generator-service-for-non-administrators}

Sie können Benutzern, die keine Administratoren sind, die Verwendung des PDF Generator-Dienstes erlauben. Normalerweise können nur Benutzer mit Administratorrechten den Dienst verwenden:

1. Erstellen Sie eine Umgebungsvariable namens PDFG_NON_ADMIN_ENABLED.
1. Setzen Sie den Wert der Umgebungsvariablen auf „TRUE“.
1. Starten Sie die AEM Forms-Instanz neu.

>[!NOTE]
>
> Es wird empfohlen, den Befehl „Strg+C“ zu verwenden, um das SDK neu zu starten. Das Neustarten des AEM SDK mit anderen Methoden, z. B. dem Beenden von Java-Prozessen, kann zu Inkonsistenzen in der AEM-Entwicklungsumgebung führen.

### (Nur Windows) Deaktivieren der Benutzerkontensteuerung (UAC) {#disable-user-account-control-uac}

1. Sie können auf das Systemkonfigurationsprogramm zugreifen, indem Sie zu **[!UICONTROL Start > Ausführen]** wechseln und dann **[!UICONTROL MSCONFIG]** eingeben.
1. Klicken Sie auf die Registerkarte **[!UICONTROL Tools]**, blättern Sie nach unten und wählen Sie **[!UICONTROL Einstellungen für Benutzerkontensteuerung ändern]**. Klicken Sie auf **[!UICONTROL Starten]**, um den Befehl in einem neuen Fenster auszuführen.
1. Stellen Sie den Schieberegler auf Nie benachrichtigen ein. Schließen Sie nach Abschluss des Vorgangs das Befehlsfenster und das Fenster für die Systemkonfiguration.
1. Überprüfen Sie, ob die Registrierungseinstellung für UAC auf 0 (Null) gesetzt ist. Führen Sie die folgenden Schritte zur Überprüfung durch:

   1. Microsoft® empfiehlt, eine Sicherungskopie der Registrierung zu erstellen, bevor Sie sie ändern. Detaillierte Informationen zu den Schritten erfahren Sie unter [Sichern und Wiederherstellen der Registrierung in Windows](https://support.microsoft.com/de-de/help/322756).
   1. Öffnen Sie den Microsoft® Windows Registrierungs-Editor. Um den Registrierungs-Editor zu öffnen, gehen Sie zu „Start“ > „Ausführen“, geben Sie „regedit“ ein und klicken Sie auf „OK“.
   1. Navigieren Sie zu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Stellen Sie sicher, dass der Wert EnableLUA auf 0 (null) gesetzt ist. 
   1. Stellen Sie sicher, dass der Wert **EnableLUA** auf 0 (null) gesetzt ist. Wenn der Wert ungleich 0 ist, ändern Sie den Wert auf 0. Schließen Sie den Registrierungseditor.

1. Starten Sie den Computer neu.

### (Nur Windows) Deaktivieren des Fehlerberichterstattungsdienstes {#disable-error-reporting-service}

Beim Konvertieren eines Dokuments in PDF mit dem PDF Generator-Service unter Windows Server zeigt Windows Server gelegentlich die Fehlermeldung an, dass in der ausführbaren Datei ein Problem aufgetreten ist und sie geschlossen werden muss. Das wirkt sich jedoch nicht auf die PDF-Konvertierung aus, da sie im Hintergrund weiterläuft.

Um diese Fehlermeldung zu vermeiden, können Sie die Windows-Fehlerberichterstattung deaktivieren. Weitere Informationen zum Deaktivieren der Fehlerberichterstattung finden Sie unter [https://technet.microsoft.com/en-us/library/cc754364.aspx](https://technet.microsoft.com/de-de/library/cc754364.aspx).

### (Nur Windows) Konfigurieren der Konvertierung von HTML zu PDF {#configure-html-to-pdf-conversion}

Der PDF Generator-Dienst bietet WebKit-, WebCapture- und Web-in-PDF-Routen oder -Methoden zum Konvertieren von HTML-Dateien in PDF-Dokumente. Um unter Windows die Konvertierung für WebKit- und Acrobat WebCapture-Routen zu aktivieren, kopieren Sie die Unicode-Schriftart in den Ordner %windir%\fonts.

>[!NOTE]
>
>Starten Sie die AEM Forms-Instanz jedes Mal neu, wenn Sie neue Schriftarten in den Schriftartenordner installieren.

### (Nur UNIX-basierte Plattformen) Zusätzliche Konfigurationen für die Konvertierung von HTML zu PDF  {#extra-configurations-for-html-to-pdf-conversion}

Auf UNIX-basierten Plattformen unterstützt der PDF Generator-Dienst WebKit- und Web-in-PDF-Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente. Um die Konvertierung von HTML zu PDF zu aktivieren, führen Sie entsprechend Ihrer bevorzugten Konvertierungsroute die folgenden Konfigurationen durch:

### (Nur UNIX-basierte Plattformen) Aktivieren der Unterstützung für Unicode-Schriftarten (nur WebKit) {#enable-support-for-unicode-fonts-webkit-only}

Kopieren Sie die Unicode-Schriftart in die folgenden Ordner, so wie es für Ihr System erforderlich ist:

* /usr/lib/X11/fonts/TrueType
* /usr/share/fonts/default/TrueType
* /usr/X11R6/lib/X11/fonts/ttf
* /usr/X11R6/lib/X11/fonts/truetype
* /usr/X11R6/lib/X11/fonts/TrueType
* /usr/X11R6/lib/X11/fonts/TTF
* /usr/openwin/lib/X11/fonts/TrueType (Solaris™)

>[!NOTE]
>
>* Unter Red Hat® Enterprise Linux® 6.x sind die Courier-Schriftarten nicht verfügbar. Laden Sie zum Installieren der Courier-Schriftarten das Archiv „font-ibm-type1-1.0.3.zip“ herunter. Extrahieren Sie das Archiv unter /usr/share/fonts. Erstellen Sie eine symbolische Verknüpfung von /usr/share/X11/fonts zu /usr/share/fonts.
>* Löschen Sie alle .lst-Schriftarten-Cache-Dateien aus den Ordnern „Html2PdfSvc/bin“ und „/usr/share/fonts“.
>* Stellen Sie sicher, dass die Ordner /usr/lib/X11/fonts und /usr/share/fonts vorhanden sind. Wenn die Ordner nicht vorhanden sind, verwenden Sie den Befehl „ln“, um eine symbolische Verknüpfung vom Ordner /usr/share/X11/fonts auf /usr/lib/X11/fonts und eine andere symbolische Verknüpfung von /usr/share/fonts auf /usr/share/X11/fonts zu erstellen. Vergewissern Sie sich außerdem, dass die Courier-Schriftarten unter „/usr/lib/X11/fonts“ verfügbar sind.
>* Stellen Sie sicher, dass alle Schriftarten (Unicode und Nicht-Unicode) im Ordner /usr/share/fonts or /usr/share/X11/fonts verfügbar sind.
>* Wenn Sie den PDF Generator-Dienst unter einem anderen Benutzer als /root ausführen, gewähren Sie dem betreffenden Benutzer Lese- und Schreibzugriff auf alle Schriftartenordner.
>* Starten Sie die AEM Forms-Instanz jedes Mal neu, wenn Sie neue Schriftarten in den Schriftartenordner installieren.
>

## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

Das AEM Forms Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält die AEM Forms-Dokumentendienste und andere AEM Forms-Funktionen. Führen Sie die folgenden Schritte aus, um das Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Wählen Sie im Kopfzeilenmenü **[!UICONTROL Adobe Experience Manager]** aus.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]** aus.
   2. Wählen Sie die Version aus und geben Sie sie für das Paket ein. Sie können auch die Option **[!UICONTROL Downloads durchsuchen]** verwenden, um die Ergebnisse zu filtern.
1. Wählen Sie den für Ihr Betriebssystem zutreffenden Paketnamen, dann **[!UICONTROL EULA-Bedingungen akzeptieren]** und dann **[!UICONTROL Herunterladen]** aus.
1. Öffnen Sie [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=de) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) aufgeführt ist.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Halten Sie den Server nicht sofort an.** Bevor Sie den AEM Forms-Server stoppen, warten Sie, bis die Meldungen „ServiceEvent REGISTERED“ und „ServiceEvent UNREGISTERED“ nicht mehr in der Datei „`[AEM-Installation-Directory]/crx-quickstart/logs/error`.log“ angezeigt werden und das Protokoll stabil ist.

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

### Boot-Delegierung für RSA-/BouncyCastle-Bibliotheken konfigurieren  {#configure-boot-delegation-for-rsa-bouncycastle-libraries}

1. Halten Sie die AEM-Instanz an. Navigieren Sie zum Ordner [AEM-Installationsverzeichnis]\crx-quickstart\conf\ und öffnen Sie die Datei „sling.properties“ zur Bearbeitung.

   Wenn Sie `[AEM installation directory]\crx-quickstart\bin\start.bat`zum Starten einer AEM-Instanz verwenden, bearbeiten Sie die sling.properties-Datei unter `[AEM_root]\crx-quickstart\`.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   ```

1. (Nur AIX®) Fügen Sie die folgenden Eigenschaften zur Datei „sling.properties“ hinzu:

   ```shell
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Speichern und schließen Sie die Datei.

### Konfigurieren des Schrift-Manager-Dienstes  {#configuring-the-font-manager-service}

1. Melden Sie sich bei [AEM Configuration Manager](http://localhost:4502/system/console/configMgr) als Administrator an.
1. Suchen Sie den Service **[!UICONTROL CQ-DAM-Handler-Gibson Font Managers]** und öffnen Sie ihn. Geben Sie den Pfad für die Ordner Systemschriftarten, Adobe-Serverschriftarten und Kundenschriftarten an. Klicken Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Die Rechte zur Verwendung von Schriftarten anderer Anbieter als Adobe unterliegen dem Lizenzvertrag dieser Anbieter von Schriftarten und werden nicht von der Lizenz für die Adobe-Software abgedeckt. Adobe empfiehlt, dass Sie vor der Verwendung von Drittanbieter-Schriften in Verbindung mit Adobe-Software alle relevanten Lizenzverträge der Drittanbieter lesen und dafür sorgen, dass Sie diese Verträge einhalten. Dies gilt insbesondere für die Verwendung von Schriften in einer Server-Umgebung.
   >Starten Sie die AEM Forms-Instanz neu, wenn Sie neue Zeichensätze im Zeichensatzordner installieren.
   >

### Konfigurieren Sie ein lokales Benutzerkonto zum Ausführen des PDF Generator-Dienstes  {#configure-a-local-user-account-to-run-the-pdf-generator-service}

Zum Ausführen des PDF Generator-Dienstes ist ein lokales Benutzerkonto erforderlich. Schritte zum Erstellen eines lokalen Benutzers finden Sie unter [Erstellen eines Benutzerkontos in Windows](https://support.microsoft.com/de-de/help/13951/windows-create-user-account) oder „Erstellen eines Benutzerkontos in UNIX-basierten Plattformen“.

1. Öffnen Sie die Seite [Konfiguration von AEM Forms PDF Generator](http://localhost:4502/libs/fd/pdfg/config/ui.html).

1. Geben Sie auf der Registerkarte **[!UICONTROL Benutzerkonten]** die Anmeldeinformationen für ein lokales Benutzerkonto ein und klicken Sie auf **[!UICONTROL Senden]**. Wenn Microsoft® Windows Sie dazu auffordert, erlauben Sie dem Benutzer den Zugriff. Nach erfolgreichem Hinzufügen wird der konfigurierte Benutzer unter dem Abschnitt **[!UICONTROL Ihre Benutzerkonten]** auf der Registerkarte **[!UICONTROL Benutzerkonten]** angezeigt.

### Zeitlimiteinstellungen konfigurieren {#configure-the-time-out-settings}

1. Suchen Sie in [AEM Configuration Manager](http://localhost:4502/system/console/configMgr) den Service **[!UICONTROL Jacorb ORB Provider]** und öffnen Sie ihn.

   Fügen Sie im Feld **[!UICONTROL Custom Properties.name]** Folgendes hinzu und klicken Sie auf **[!UICONTROL Speichern]**. Dies setzt das Zeitlimit für ausstehende Antworten (auch als CORBA-Client-Zeitlimit bezeichnet) auf 600 Sekunden.

   `jacorb.connection.client.pending_reply_timeout=600000`

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** >>**[!UICONTROL Werkzeuge]** > **[!UICONTROL Formulare]** > **[!UICONTROL PDF Generator konfigurieren]**. Die Standard-URL ist <http://localhost:4502/libs/fd/pdfg/config/ui.html>.

   Öffnen Sie die Registerkarte **[!UICONTROL Allgemeine Konfiguration]** und ändern Sie die Werte der folgenden Felder für Ihre Umgebung:

<table>
 <tbody>
  <tr>
   <td>Feld</td>
   <td>Beschreibung</td>
   <td>Standardwert</td>
  </tr>
  <tr>
   <td>Zeitüberschreitung bei Server-Konvertierung</td>
   <td>Eine PDFG-Konvertierung bleibt für die in „Konvertierungstimeout für Server“ festgelegte Anzahl von Sekunden aktiv.</td>
   <td>270 Sekunden<br /> </td>
  </tr>
  <tr>
   <td>Überprüfung der PDFG-Bereinigung (Sekunden)</td>
   <td>Die für Vorgänge nach der Konvertierung benötigte Anzahl von Sekunden.<br /> </td>
   <td>3600 Sekunden</td>
  </tr>
  <tr>
   <td>Ablaufzeit für Auftrag (Sekunden)</td>
   <td>Die Dauer, für die der PDF Generator-Dienst eine Konvertierung ausführen darf. Stellen Sie sicher, dass der Wert für „Auftragsablauf (Sekunden)“ größer ist als der Wert für „PDF-Bereinigungsprüfung (Sekunden)“.</td>
   <td>7200 Sekunden</td>
  </tr>
 </tbody>
</table>

### (Nur Windows) Konfigurieren von Acrobat für den PDF Generator-Service {#configure-acrobat-for-the-pdf-generator-service}

Unter Microsoft® Windows verwendet der PDF Generator-Service Adobe Acrobat, um unterstützte Dateiformate in PDF-Dokumente zu konvertieren. Führen Sie die folgenden Schritte aus, um Adobe Acrobat für den PDF Generator-Dienst zu konfigurieren:

1. Öffnen Sie Acrobat und wählen Sie **[!UICONTROL Bearbeiten]** > **[!UICONTROL Voreinstellungen]** > **[!UICONTROL Updater]**. Deaktivieren Sie unter „Nach Updates suchen“ die Option **[!UICONTROL Updates automatisch installieren]** und klicken Sie auf **[!UICONTROL OK]**. Schließen Sie Acrobat.
1. Doppellklicken Sie auf Ihrem System auf ein PDF-Dokument. Beim ersten Start von Acrobat werden die Dialogfelder für Anmeldung, der Begrüßungsbildschirm und die Endbenutzerlizenzvereinbarung (EULA) angezeigt. Schließen Sie diese Dialogfelder für alle Benutzenden, die für die Verwendung von PDF Generator konfiguriert sind.
1. Führen Sie die Stapeldatei des PDF Generator-Dienstprogramms aus, um Acrobat für den PDF Generator-Dienst zu konfigurieren:

   1. Öffnen Sie [AEM Package Manager](http://localhost:4502/crx/packmgr/index.jsp) und laden Sie die Datei `adobe-aemfd-pdfg-common-pkg-[version].zip` aus dem Package Manager herunter.
   1. Entpacken Sie die heruntergeladene ZIP-Datei. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.
   1. Navigieren Sie zu `[extracted-zip-file]\jcr_root\etc\packages\day\cq60\fd\adobe-aemds-common-pkg-[version]\jcr_root\etc\packages\day\cq60\fd\`.
   1. Entpacken Sie die Datei `adobe-aemfd-pdfg-common-pkg-[version]`.
   1. Navigieren Sie zum Verzeichnis `[downloaded-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]`. Führen Sie die folgende Stapelverarbeitungsdatei aus:

      `Acrobat_for_PDFG_Configuration.bat`

      Acrobat ist konfiguriert, um mit dem PDF Generator-Dienst zu laufen.

1. Führen Sie das [Systembereitschafts-Tool (System Readiness Tool, SRT)](#SRT) aus, um die Installation von Acrobat zu validieren.


### (Nur Windows) Konfigurieren der primären Route für die Konvertierung von HTML zu PDF {#configure-primary-route-for-html-to-pdf-conversion-windows-only}

Der PDF Generator-Dienst bietet mehrere Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente: WebKit, Acrobat WebCapture (nur Windows) und „Web in PDF“. Adobe empfiehlt die Verwendung der Web-in-PDF-Route, da sie dynamische Inhalte verarbeiten kann, nicht von 32-Bit-Bibliotheken abhängig ist und keine zusätzlichen Schriftarten erfordert. Außerdem benötigt die Web-in-PDF-Route keinen sudo- oder root-Zugriff, um die Konvertierung durchzuführen.

Die standardmäßige primäre Route für die Konvertierung von HTML in PDF ist Webkit. So ändern Sie die Konvertierungsroute:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Formulare]** > **[!UICONTROL PDF Generator konfigurieren]**.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Allgemeine Konfiguration]** die bevorzugte Konvertierungsroute aus der Dropdown-Liste **[!UICONTROL Primäre Route für Konvertierungen von HTML in PDF]**.

### Initialisieren des Global Trust Store {#intialize-global-trust-store}

Mithilfe der Trust Store-Verwaltung können Sie Zertifikate importieren, bearbeiten und löschen, die Sie auf dem Server zur Überprüfung digitaler Signaturen und zur Zertifikatauthentifizierung als vertrauenswürdig einstufen. Sie können eine beliebige Anzahl von Zertifikaten importieren und exportieren. Nachdem ein Zertifikat importiert wurde, können Sie die Vertrauenseinstellungen und den Trust Store-Typ bearbeiten. Führen Sie die folgenden Schritte aus, um einen Trust Store zu initialisieren:

1. Melden Sie sich bei der AEM Forms-Instanz als Administrator an.
1. Navigieren Sie zu **[!UICONTROL Tools]** >  **[!UICONTROL Sicherheit]** >  **[!UICONTROL Trust Store]**.
1. Klicken Sie auf  **[!UICONTROL TrustStore erstellen]**. Geben Sie ein Kennwort ein und wählen Sie **[!UICONTROL Speichern]**.

### Einrichten von Zertifikaten für die Reader-Erweiterung und den Verschlüsselungsdienst {#set-up-certificates-for-reader-extension-and-encryption-service}

Der DocAssurance-Dienst kann Verwendungsrechte auf PDF-Dokumente anwenden. Um Verwendungsrechte auf PDF-Dokumente anzuwenden, konfigurieren Sie die Zertifikat.

Stellen Sie vor dem Einrichten der Zertifikate Folgendes sicher:

* Zertifikatdatei (.pfx).

* Passwort des privaten Schlüssels, der mit dem Zertifikat geliefert wird.

* Alias für privaten Schlüssel. Sie können den Java-Keytool-Befehl ausführen, um den Alias für den privaten Schlüssel anzuzeigen:
  `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

* Kennwort für KeyStore-Datei. Wenn Sie das Adobe Reader Extensions-Zertifikat verwenden, ist das Kennwort der Keystore-Datei immer dasselbe wie das Kennwort für den privaten Schlüssel.

Gehen Sie wie folgt vor, um die Zertifikate zu konfigurieren:

1. Melden Sie sich bei der AEM-Autoreninstanz als Administrator an. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Benutzer]**.
1. Klicken Sie auf das **[!UICONTROL Namensfeld]** des Benutzerkontos. Die Seite **[!UICONTROL Benutzereinstellungen bearbeiten]** wird geöffnet. Auf der AEM-Authoring-Instanz residieren Zertifikate in einem KeyStore. Wenn Sie noch keinen KeyStore erstellt haben, klicken Sie auf **[!UICONTROL KeyStore erstellen]** und legen Sie ein neues Kennwort für den KeyStore fest. Wenn der Server bereits einen KeyStore enthält, überspringen Sie diesen Schritt.  Wenn Sie das Adobe Reader Extensions-Zertifikat verwenden, ist das Keystore-Datei-Kennwort immer dasselbe wie das Kennwort für den privaten Schlüssel.
1. Auf der Seite **[!UICONTROL Benutzereinstellungen bearbeiten]**, wählen Sie die Registerkarte **[!UICONTROL KeyStore]**. Blenden Sie die Option **[!UICONTROL Add Private Key from Key Store file]** (Privaten Schlüssel aus KeyStore-Datei hinzufügen) ein und geben Sie einen Aliasnamen an. Der Aliasname wird verwendet, um den Reader Extensions-Vorgang durchzuführen.
1. Um die Zertifikatdatei hochzuladen, klicken Sie auf **[!UICONTROL Select Key Store File]** (KeyStore-Datei auswählen) und laden Sie eine &lt;Dateiname>.pfx-Datei hoch.

   Fügen Sie die Werte für **[!UICONTROL Key Store Password]** (KeyStore-Kennwort),**[!UICONTROL Private Key Password]** (Kennwort für privaten Schlüssel) und **[!UICONTROL Private Key Alias]**(Alias des privaten Schlüssels) für das Zertifikat in den jeweiligen Feldern hinzu. Klicken Sie auf **[!UICONTROL Senden]**.

   >[!NOTE]
   >
   >Ersetzen Sie in der Produktionsumgebung die Testzugangsdaten durch Produktionszugangsdaten. Achten Sie darauf, dass Sie Ihre alten Reader Extensions-Anmeldedaten löschen, bevor Sie abgelaufene oder Testanmeldedaten aktualisieren.

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]** auf der Seite **[!UICONTROL Benutzereinstellungen bearbeiten]**.

### Aktivieren von AES-256 {#enable-aes}

Um die AES-256-Verschlüsselung für PDF-Dateien zu verwenden, müssen Sie die Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy-Dateien beziehen und installieren. Ersetzen Sie die Dateien „local_policy.jar“ und „US_export_policy.jar“ im Ordner „jre/lib/security“. Wenn Sie beispielsweise Sun JDK verwenden, kopieren Sie die heruntergeladenen Dateien in den Ordner „`[JAVA_HOME]/jre/lib/security`“.

Der Assembler-Dienst hängt vom Reader Extension-Dienst, vom Signature-Dienst, vom Forms-Dienst und vom Output-Dienst ab. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die erforderlichen Dienste aktiv sind:

1. Melden Sie sich bei `https://'[server]:[port]'/system/console/bundles` als Administrator an.
1. Suchen Sie den folgenden Dienst und stellen Sie sicher, dass die Dienste aktiv sind:

<table>
 <tbody>
  <tr>
   <th>Service-Name</th>
   <th>Bundle-Name</th>
  </tr>
  <tr>
   <td>Signatur-Service</td>
   <td>adobe-aemfd-signatures</td>
  </tr>
  <tr>
   <td>Reader Extensions-Service</td>
   <td>com.adobe.aemfd.adobe-aemfd-readerextensions<br /> </td>
  </tr>
  <tr>
   <td>Formularservice</td>
   <td>com.adobe.livecycle.adobe-lc-forms-bedrock-connector<br /> </td>
  </tr>
  <tr>
   <td>Ausgabe-Service</td>
   <td>com.adobe.livecycle.adobe-lc-forms-bedrock-connector</td>
  </tr>
 </tbody>
</table>

### (Nur Windows) Konfigurieren des Registrierungseintrags für Microsoft® Project {#configure-registry-entry-for-microsoft-project}

Nachdem Sie das AEM Forms-Add-on und Microsoft® Project auf Ihrem Computer installiert haben, registrieren Sie einen Eintrag für Microsoft® Project am 64-Bit-Speicherort. Dies vereinfacht die Ausführung von Konvertierungstests von Project zu PDFG. Die folgenden Schritte sind zum Konfigurieren eines Registrierungseintrags erforderlich:

1. Öffnen Sie den Microsoft® Windows-Registrierungs-Editor (regedit). Gehen Sie hierzu zu „Start“ > „Ausführen“, geben Sie „regedit“ ein und klicken Sie auf „OK“.
1. Navigieren Sie zu `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\Acrobat PDFMaker\<version>\Office\SupportedApp`, erstellen Sie einen neuen **Binärwert** und benennen Sie ihn in **Project** um.
1. Ändern Sie den Datenwert der erstellten Binärregistrierung in „01“ und klicken Sie auf „OK“.
1. Schließen Sie den Registrierungs-Editor.


## Bekannte Probleme und Fehlerbehebung {#known-issues-and-troubleshooting}

* Die „HTML in PDF“-Konvertierung schlägt fehl, wenn eine komprimierte Eingabedatei (ZIP) HTML-Dateien enthält, deren Dateinamen Doppelbyte-Zeichen enthalten. Um dieses Problem zu vermeiden, sollten Sie beim Benennen von HTML-Dateien keine Doppelbyte-Zeichen verwenden.

* Führen Sie auf UNIX-basierten Betriebssystemen die folgenden Schritte aus, um fehlende Bibliotheken zu finden:

1. Navigieren Sie zu `[crx-repository]/bedrock/svcnative/HtmlToPdfSvc/bin/`.

1. Führen Sie folgenden Befehl aus, um alle Bibliotheken aufzulisten, die „Web in PDF“ für die Konvertierung vom HTML- ins PDF-Format benötigt.

   `ldd phantomjs`

   Führen Sie folgenden Befehl aus. um fehlende Bibliotheken aufzulisten.

   `ldd phantomjs | grep not`

1. Installieren Sie die fehlenden Bibliotheken manuell.

## Systembereitschafts-Tool (System Readiness Tool, SRT) {#SRT}

Die [Systembereitschafts-Tool](#srt-configuration) überprüft, ob der Computer ordnungsgemäß für die Ausführung von PDF Generator-Konvertierungen konfiguriert ist. Das Tool generiert einen Bericht im angegebenen Pfad. So führen Sie das Tool aus:

1. Öffnen Sie eine Eingabeaufforderung. Navigieren Sie zum Ordner `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools`.

1. Führen Sie in der Eingabeaufforderung den folgenden Befehl aus:

   `java -jar forms-srt-[version].jar [Path_of_reports_folder] en`

   Der Befehl generiert einen Bericht und erstellt auch die Datei „srt_config.yaml“. Sie können damit Optionen für das SRT-Tool konfigurieren. Das Konfigurieren von Optionen für das SRT-Tool ist optional.

   >[!NOTE]
   >
   >* Wenn das Systembereitschafts-Tool meldet, dass die Datei „pdfgen.api“ nicht im Ordner der Acrobat-Plug-ins zur Verfügung steht, dann kopieren Sie die Datei „pdfgen.api“ aus dem Verzeichnis `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]\plugins\x86_win32` in das Verzeichnis `[Acrobat_root]\Acrobat\plug_ins`.

1. Navigieren Sie zu `[Path_of_reports_folder]`. Öffnen Sie die Datei SystemReadinessTool.html. Überprüfen Sie den Bericht und beheben Sie die erwähnten Probleme.

### Konfigurieren von Optionen für das SRT-Tool {#srt-configuration}

Sie können die Datei „srt_config.yaml“ verwenden, um verschiedene Einstellungen für das SRT-Tool zu konfigurieren. Die Datei hat folgendes Format:

```shell
   # =================================================================
   # SRT Configuration
   # =================================================================
   #Note - follow correct format to avoid parsing failures
   #for example, <param name>:<space><param value> 
   #locale: (mandatory field)Locale to be used for SRT. Supported locales [en/fr/de/ja].
   locale: en
   
   #aemTempDir: AEM Temp direcotry
   aemTempDir:
   
   #users: provide PDFG converting users list
   #users:
   # - user1
   # - user2
   users:
   
   #profile: select profile to run specific checks. Choose from [LCM], more will be added soon 
   profile:
   
   #outputDir: directory where output files will be saved
   outputDir:
```

* **Gebietsschema**: Dies ist ein obligatorischer Parameter. Unterstützt werden Englisch (en), Deutsch (de), Französisch (fr) und Japanisch (ja). Der Standardwert ist en. Dies wirkt sich nicht auf die PDF Generator-Services aus, die auf AEM Forms unter OSGi ausgeführt werden.
* **aemTempDir**: Dies ist ein optionaler Parameter. Er gibt den temporären Speicherort von Adobe Experience Manager an.
* **users**: Dies ist ein optionaler Parameter. Sie können einen Benutzer angeben, um zu überprüfen, ob der Benutzer über die erforderlichen Berechtigungen und Lese-/Schreibzugriff für Ordner verfügt, die zum Ausführen von PDF Generator erforderlich sind. Wenn kein Benutzer angegeben ist, werden benutzerspezifische Prüfungen übersprungen und im Bericht als fehlgeschlagen angezeigt.
* **outputDir**: Geben Sie den Speicherort für den SRT-Bericht an. Der Standardspeicherort ist das aktuelle Arbeitsverzeichnis des SRT-Tools.

## Fehlerbehebung

Wenn Probleme auftreten, selbst nachdem alle vom SRT-Tool gemeldeten Probleme behoben wurden, führen Sie die folgenden Prüfungen durch:

Stellen Sie vor der Durchführung der folgenden Prüfungen sicher, dass das [Systembereitschafts-Tool](#SRT) keinen Fehler meldet.

+++ Adobe Acrobat

* Stellen Sie sicher, dass nur [unterstützte Versionen](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) von Microsoft® Office (32 Bit) und Adobe Acrobat installiert sind und Dialogfelder, die sich öffnen, abgebrochen werden.
<!-- (Acrobat 2020 only) Ensure that Adobe Acrobat Update Service is disabled. -->
* Stellen Sie sicher, dass die Batch-Datei [Acrobat_for_PDFG_Configuration.bat](#configure-acrobat-for-the-pdf-generator-service) mit Administratorrechten ausgeführt wurde.
* Stellen Sie sicher, dass in der PDF-Konfigurationsoberfläche ein Benutzer von PDF Generator hinzugefügt wird.
* Stellen Sie sicher, dass für den Benutzer von PDF-Generator die Berechtigung zum [Ersetzen eines Tokens auf Prozessebene](#grant-the-replace-a-process-level-token-privilege) hinzugefügt wurde.
* Stellen Sie sicher, dass das Acrobat PDFMaker Office COM-Add-In für Microsoft® Office-Anwendungen aktiviert ist.

+++

+++OpenOffice

**Microsoft® Windows**

* Stellen Sie sicher, dass die [unterstützte 32-Bit-Version](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) von Microsoft® Office installiert ist und für keine der Anwendungen Dialogfelder offen sind.
* Stellen Sie sicher, dass in der PDF-Konfigurationsoberfläche ein Benutzer von PDF Generator hinzugefügt wird.
* Stellen Sie sicher, dass der PDF Generator-Benutzer Mitglied der Administratorgruppe ist und dass für den Benutzer die Berechtigung zum [Ersetzen eines Tokens auf Prozessebene](#grant-the-replace-a-process-level-token-privilege) besteht.
* Stellen Sie sicher, dass der Benutzer in der Benutzeroberfläche von PDF Generator konfiguriert ist und die folgenden Aktionen ausführt:
   1. Melden Sie sich mit dem PDF Generator-Benutzer bei Microsoft® Windows an.
   1. Öffnen Sie das Microsoft® Office- oder das OpenOffice-Programm und brechen Sie alle Dialoge ab.
   1. Legen Sie AdobePDF als Standarddrucker fest.
   1. Legen Sie Acrobat als Standardprogramm für PDF-Dateien fest.
   1. Führen Sie in Microsoft® Office-Programmen eine manuelle Konvertierung unter Verwendung der Optionen „Datei“ > „Drucken“ und des Acrobat-Menübands durch und schließen Sie alle Dialogfelder.
   1. Beenden Sie alle mit der Konvertierung zusammenhängenden Prozesse wie winword.exe, powerpoint.exe und excel.exe.
   1. Starten Sie den AEM Forms-Server neu.

**Linux®**

* Installieren Sie die [unterstützte Version](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) von OpenOffice. AEM Forms unterstützt sowohl 32-Bit- als auch 64-Bit-Versionen. Öffnen Sie nach der Installation alle OpenOffice-Programme, schließen Sie alle Dialogfelder und schließen Sie die Programme wieder. Öffnen Sie die Programme erneut und stellen Sie sicher, dass beim Öffnen eines OpenOffice-Programms kein Dialogfeld angezeigt wird.

* Erstellen Sie eine Umgebungsvariable `OpenOffice_PATH` und legen Sie sie so fest, dass sie auf die OpenOffice-Installation verweist, die in der [Konsole](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/) oder dem dt-Profil (Device Tree, Gerätestrukturprofil) festgelegt ist.
* Sollten bei der Installation von OpenOffice Probleme auftreten, stellen Sie sicher, dass die für die OpenOffice-Installation erforderlichen [32-Bit-Bibliotheken](#extrarequirements) zur Verfügung stehen.

+++

 +++ Probleme bei der Konvertierung von HTML in PDF

* Stellen Sie sicher, dass Schriftartenordner in der PDF Generator-Konfigurationsoberfläche hinzugefügt werden.

**Linux und Solaris (Web-in-PDF-Konversionsroute)**

* Stellen Sie sicher, dass die 32-Bit-Bibliothek (libicudata.so.42) für die WebKit-basierte HTMLToPDF-Konvertierung und die 64-Bit-Bibliotheken (libicudata.so.42) für die Web-in-PDF-basierte HTMLToPDF-Konvertierung verfügbar sind.

* Führen Sie folgenden Befehl aus, um Bibliotheken aufzulisten, die für „Web in PDF“ fehlen:

  ```
  ldd phantomjs | grep not
  ```

**Linux® und Solaris™ (WebKit-Konvertierungsroute)**

* Stellen Sie sicher, dass die Verzeichnisse `/usr/lib/X11/fonts` und `/usr/share/fonts` existieren. Wenn die Verzeichnisse nicht vorhanden sind, erstellen Sie eine symbolische Verknüpfung von `/usr/share/X11/fonts` zu `/usr/lib/X11/fonts` und eine weitere symbolische Verknüpfung von `/usr/share/fonts` zu `/usr/share/X11/fonts`.

  ```
  ln -s /usr/share/fonts /usr/share/X11/fonts
  
  ln -s /usr/share/X11/fonts /usr/lib/X11/fonts
  ```

* Stellen Sie sicher, dass IBM-Schriftarten unter „ usr/share/fonts“ kopiert werden.
* Stellen Sie sicher, dass die Ghost-Schwachstellenbehebung glibc auf dem Rechner verfügbar ist. Verwenden Sie den standardmäßigen Package Manager, um auf die neueste Version von glibc zu aktualisieren. Er schließt eine Ghost-Schwachstellenbehebung ein.
* Stellen Sie sicher, dass die neuesten Versionen der 32-Bit-Bibliotheken „curl“, „libcrypto“ und „libssl“ auf dem System installiert sind. Erstellen Sie auch Symlinks `/usr/lib/libcurl.so` (bzw. „libcurl.a“ für AIX®), `/usr/lib/libcrypto.so` (bzw. „libcrypto.a“ für AIX®) und `/usr/lib/libssl.so` (bzw. „libssl.a“ für AIX®), die auf die neuesten Versionen (32-Bit-Versionen) der jeweiligen Bibliotheken verweisen.

* Führen Sie für den IBM® SSL-Socket-Anbieter die folgenden Schritte aus:
   1. Kopieren Sie die Datei „java.security“ aus `<WAS_Installed_JAVA>\jre\lib\security` an einen beliebigen Speicherort auf Ihrem AEM Forms-Server. Der Standardspeicherort lautet `<WAS_Installed>\Appserver\java_[version]\jre\lib\security`.

   1. Bearbeiten Sie die Datei „java.security“ am kopierten Speicherort und ersetzen Sie die standardmäßigen SSL-Socket-Factories durch JSSE2-Factories (verwenden Sie JSSE2-Factories anstelle von WebSphere®).

      Ändern Sie die folgenden standardmäßigen JSSE-Socket-Factories:

      ```
      #ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
      #ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
      WebSphere socket factories (in cryptosf.jar)
      ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
      ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
      ```

      durch

      ```
      ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
      ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
      WebSphere socket factories (in cryptosf.jar)
      #ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
      #ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
      ```

 +++

<!-- +++ Unable to add a PDF Generator (PDFG) user

* (Acrobat 2020 only) Ensure Microsoft&reg; Visual C++ 2012 x86 and Microsoft&reg; Visual C++ 2013 x86 (32-bit) redistributable are installed on Windows.

+++
-->
+++ Fehler beim Test der Automatisierung

* Führen Sie für Microsoft® Office und OpenOffice mindestens eine Konvertierung (für jeden Benutzer) manuell durch, um sicherzustellen, dass während der Konvertierung kein Dialogfeld eingeblendet wird. Wenn ein Dialog angezeigt wird, klicken Sie ihn weg. Während der automatisierten Konvertierung sollte kein solcher Dialog angezeigt werden.

* Bevor Sie die Automatisierung in einer AEM Forms on OSGi-Umgebung einsetzen, stellen Sie sicher, dass das Testpaket installiert und aktiv ist.

+++

<!-- +++ (Acrobat 2020 only) Multiple user conversion failures 

* Verify the server logs to check if the conversion is failing for a particular user.(Process Explorer can help you check running process for different users)

* Ensure that the user configured for PDF Generator has local admin rights.

* Ensure that PDF Generator user has read, write, and execute permissions on LC temp and PDFG temp users.

* For Microsoft&reg; Office and OpenOffice, perform at least one conversion manually (as each user) to ensure that no dialogue pops up during conversion. If any dialogue appears, dismissed it. No such dialogue should appear during automated conversion.

* Perform a sample conversion.

+++ -->

<!-- (Acrobat 2020 only) License of Adobe Acrobat installed on AEM Forms Server expires

* If you have an existing license of Adobe Acrobat and it has expired, [Download the latest version of Adobe Application Manager](https://helpx.adobe.com/in/creative-suite/kb/aam-troubleshoot-download-install.html), and migrating your serial number. Before [migrating your serial number](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number).

   * Use the following commands to generate prov.xml and reserialize the existing install using the prov.xml file instead of commands provided in [migrating your serial number](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number) number article.

      ```

         adobe_prtk --tool=VolumeSerialize --generate --serial=<serialnum> [--leid=<LEID>] [--regsuppress=ss] [--eulasuppress] [--locales=limited list of locales in xx_XX format or ALL>] [--provfile=<Absolute path to prov.xml>]

      ```

   * Volume serialize the package (Re-serialize the existing install using the prov.xml file and the new serial): Run the following command from the PRTK installation folder as an administrator to serialize and activate the deployed packages on client machines:

      ```
         adobe_prtk --tool=VolumeSerialize --provfile=C:\prov.xml –stream
         
      ```

* For large-scale installations, use the [Acrobat Customization Wizard](https://www.adobe.com/devnet-docs/acrobatetk/tools/Wizard/index.html) to remove previous versions of Reader and Acrobat. Customize the installer and deploy it to all the machines of your organization.

(Acrobat 2020 only) AEM Forms Server is in an offline or secure environment and internet is not available to activate Acrobat.

* You can go online within 7 days of the first launch of your Adobe product to complete an online activation and registration or use an internet-enabled device and your product's serial number to complete this process. For detailed instructions, see [Offline Activation](https://exception.licenses.adobe.com/aoes/aoes/v1/t1?locale=en).

+++ -->

+++ Konvertieren von Word- oder Excel-Dateien in PDF ist unter Windows Server nicht möglich

Wenn der Benutzer versucht, Word- oder Excel-Dateien unter Microsoft Windows Server in PDF zu konvertieren, tritt folgender Fehler auf:

*Fehlermeldung des primären Konverters:
ALC-PDG-015-003-Das System kann die Eingabedatei nicht öffnen. Senden Sie Ihre Datei erneut ab oder kontaktieren Sie Ihre System-Admins.*

Informationen zum Beheben des Problems finden Sie unter [Konvertieren von Word- oder Excel-Dateien in PDF ist unter Windows Server nicht möglich](/help/forms/using/disable-uac-for-pdfgconfiguration.md).

+++

+++ Konvertieren von Excel-Dateien in PDF ist unter Windows Server 2019 nicht möglich

Wenn Sie Microsoft Excel 2019 auf Microsoft Windows Server 2019 in PDF konvertieren, müssen Sie Folgendes sicherstellen:

* Bei Verwendung des PDF Generator-Dienstes sollte Ihr Windows-Computer keine aktive Remote-Verbindung mit dem AEM-Server (Windows RDP-Sitzung) haben.
* Der Standarddrucker muss als Adobe PDF eingerichtet sein.

  >[!NOTE]
  >* Für Apple macOS und Ubuntu OS müssen Sie die oben genannten Einstellungen nicht konfigurieren.

+++

+++ Konvertieren von XPS-Dateien in PDF nicht möglich

Um das Problem zu beheben, [erstellen Sie einen funktionsspezifischen Registrierungsschlüssel unter Windows](https://helpx.adobe.com/de/acrobat/kb/unable-convert-xps-to-pdfs.html).

+++


## Nächste Schritte {#next-steps}

Sie verfügen über eine funktionierende AEM Forms-Dokumentendienste-Umgebung. Sie können für Document Services von folgenden Ausgangspunkten aus nutzen:

* [Formularorientierte Arbeitsabläufe in OSGi](/help/forms/using/aem-forms-workflow.md)
* [Überwachte Ordner](/help/forms/using/watched-folder-in-aem-forms.md)
* [Document Services-APIs](/help/forms/using/aem-document-services-programmatically.md)
