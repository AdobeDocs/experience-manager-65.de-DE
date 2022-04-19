---
title: Installieren und Konfiguration von Document Services
seo-title: Installing and configuring document services
description: Installieren Sie AEM Forms Document Services, um PDF-Dokumente zu erstellen, zusammenzustellen, zu verteilen, zu archivieren, digitale Signaturen hinzuzufügen, um den Zugriff auf Dokumente zu beschränken, und dekodieren Sie Barcoded Forms.
seo-description: Install AEM Forms document services to create, assemble, distribute, archive PDF documents, add digital signatures to limit access to documents, and decode barcoded forms.
uuid: 908806a9-b0d4-42d3-9fe4-3eae44cf4326
topic-tags: installing
discoiquuid: b53eae8c-16ba-47e7-9421-7c33e141d268
role: Admin
exl-id: 5d48e987-16c2-434b-8039-c82181d2e028
source-git-commit: 8fcbdb4d00a5ddffadf5b4a099454dc795999769
workflow-type: tm+mt
source-wordcount: '5100'
ht-degree: 53%

---

# Installieren und Konfiguration von Document Services {#installing-and-configuring-document-services}

AEM Forms bietet eine Reihe von OSGi-Diensten zum Ausführen verschiedener Vorgänge auf Dokumentebene, z. B. Dienste zum Erstellen, Zusammenstellen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Signaturen zum Beschränken des Dokumentenzugriffs und Dekodieren von Barcoded Forms. Diese Dienste sind im AEM Forms Add-On-Paket enthalten. Insgesamt werden diese Dienste als Document Services bezeichnet. Die Liste der verfügbaren Document Services und ihre Hauptfunktionen finden Sie nachfolgend:

* **Assembler-Dienst:** Ermöglicht Ihnen das Kombinieren, Neuanordnen und Erweitern von PDF- und XDP-Dokumenten sowie das Abrufen von Informationen zu PDF-Dokumenten. Außerdem können Sie damit PDF-Dokumente in PDF/A-Standard konvertieren und validieren sowie PDF-Formulare, XML-Formulare und PDF-Formulare in PDF/A-1b, PDF/A-2b und PDFA/A-3b umwandeln. Weitere Informationen finden Sie unter [Assembler-Dienst](/help/forms/using/assembler-service.md).

* **ConvertPDF-Dienst:** Ermöglicht die Konvertierung von PDF-Dokumenten in PostScript- oder Bilddateien (JPEG, JPEG 2000, PNG und TIFF). Weitere Informationen finden Sie unter [ConvertPDF-Dienst](/help/forms/using/using-convertpdf-service.md).

* **Barcoded Forms-Dienst:** Ermöglicht die Extraktion von Daten aus elektronischen Abbildungen von Barcodes. Der Dienst akzeptiert TIFF- und PDF-Dateien mit einem oder mehreren Strichcodes als Eingabe und extrahiert die Strichcodedaten. Weitere Informationen finden Sie unter [Barcoded Forms-Dienst](/help/forms/using/using-barcoded-forms-service.md).

* **DocAssurance-Dienst:** Ermöglicht das Verschlüsseln und Entschlüsseln von Dokumenten, das Erweitern der Funktionalität von Adobe Reader mit zusätzlichen Verwendungsrechten und das Hinzufügen digitaler Signaturen zu Dokumenten. Der DocAssurance-Dienst umfasst drei Dienste: Signature, Encryption und Reader Extension. Weitere Informationen finden Sie unter [DocAssurance-Dienst](/help/forms/using/overview-aem-document-services.md).

* **Encryption-Dienst:** Ermöglicht das Verschlüsseln und Entschlüsseln von Dokumenten. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. Weitere Informationen finden Sie unter [Encryption-Dienst](/help/forms/using/overview-aem-document-services.md#encryption-service).

* **Forms-Dienst:** Ermöglicht die Erstellung interaktiver Clientanwendungen zur Datenerfassung, mit denen typischerweise in Forms Designer erstellte Formulare validiert, verarbeitet, transformiert und bereitgestellt werden. Der Forms-Dienst rendert jeden Formularentwurf, den Sie zum PDF von Dokumenten entwickeln. Weitere Informationen finden Sie unter [Forms-Dienst](/help/forms/using/forms-service.md).

* **Output-Dienst:** Ermöglicht die Erstellung von Dokumenten in verschiedenen Formaten, einschließlich PDF, Laserdruckerformaten und Beschriftungsdruckerformaten. Laser-Druckerformate sind PostScript und Printer Control Language (PCL). Weitere Informationen finden Sie unter [Output-Dienst](/help/forms/using/output-service.md).

* **PDF Generator-Dienst:** Der PDF Generator-Dienst stellt APIs zum Konvertieren nativer Dateiformate in PDF bereit. Es kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren. Weitere Informationen finden Sie unter [PDF Generator-Dienst](aem-document-services-programmatically.md#pdfgeneratorservice).

* **Reader Extension-Dienst:** Ermöglicht Ihrem Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweiterung der Funktionalität von Adobe Reader um zusätzliche Verwendungsrechte. Dieser Dienst aktiviert Funktionen, die nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Reader geöffnet wird, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. Weitere Informationen finden Sie unter [Reader Extension-Dienst](/help/forms/using/overview-aem-document-services.md#reader-extension-service).

* **Signature-Dienst:** Ermöglicht die Arbeit mit digitalen Signaturen und Dokumenten auf dem AEM. Der Signature-Dienst wird beispielsweise häufig in folgenden Situationen genutzt:

   * Der AEM-Server zertifiziert ein Formular, bevor es an einen Benutzer zum Öffnen in Acrobat oder Adobe Reader gesendet wird.
   * Der AEM-Server prüft die Gültigkeit einer Signatur, die einem Formular in Acrobat oder Adobe Reader hinzugefügt wurde.
   * Der AEM-Server signiert ein Formular im Auftrag eines Beglaubigers.

   Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu, die im Trust Store gespeichert sind. Weitere Informationen finden Sie unter [Signature-Dienst](/help/forms/using/aem-document-services-programmatically.md).

AEM Forms ist eine leistungsstarke Plattform der Unternehmensklasse, und Document Services ist nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Bereitstellungstopologie {#deployment-topology}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Im Allgemeinen benötigen Sie nur eine AEM-Instanz (Autor oder Veröffentlichung), um AEM Forms Document Services auszuführen. Die folgende Topologie wird zum Ausführen von AEM Forms Document Services empfohlen. Detaillierte Informationen zu Topologien finden Sie unter [Architektur und Bereitstellungstopologien für AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![Architektur und Bereitstellungstopologien für AEM Forms](do-not-localize/document-services.png)

>[!NOTE]
>
>Obwohl Sie in AEM Forms alle Funktionen von einem einzelnen Server einrichten und ausführen können, sollten Sie Kapazitätsplanung und Lastenausgleich durchführen und dedizierte Server für bestimmte Funktionen in einer Produktionsumgebung festlegen. So sollten Sie beispielsweise in einer Umgebung, in der mit dem PDF-Generator-Dienst Tausende von Seiten pro Tag konvertiert und mithilfe mehrerer adaptiver Formulare Daten erfasst werden, separate AEM Forms-Server für den PDF Generator-Dienst und adaptive Formularfunktionen einrichten. Dies bietet optimale Leistung und skaliert die Server unabhängig voneinander.

## Systemanforderungen {#system-requirements}

Bevor Sie AEM Forms Document Services installieren und konfigurieren, stellen Sie Folgendes sicher:

* Hardware- und Software-Infrastruktur ist eingerichtet. Eine detaillierte Liste der unterstützten Hardware und Software finden Sie unter [Technische Anforderungen](/help/sites-deploying/technical-requirements.md).

* Der Installationspfad der AEM-Instanz enthält keine Leerzeichen.
* Eine AEM-Instanz wird ausgeführt. In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server im Autor- oder Veröffentlichungsmodus ausgeführt wird. Im Allgemeinen benötigen Sie nur eine AEM-Instanz (Autor oder Veröffentlichung), um AEM Forms Document Services auszuführen.

   * **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
   * **Veröffentlichen**: Eine AEM-Instanz, die den Inhalt über das Internet oder ein internes Netzwerk veröffentlicht.

* Speicheranforderungen werden erfüllt. Für das Add-on-Paket für AEM Forms ist Folgendes erforderlich:

   * 15 GB temporärer Speicherplatz für Microsoft® Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Die für die Konvertierung von PDF Generator unter Microsoft® Windows und Linux® erforderliche Clientsoftware wird installiert:

   * **Microsoft® Windows**: Installieren [Microsoft® Office](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p) oder [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator)
   * **Linux®**: Installieren [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)

>[!NOTE]
>
>* Unter Microsoft® Windows unterstützt PDF Generator WebKit-, Acrobat WebCapture- und PhantomJS-Konvertierungsrouten zum Konvertieren von HTML-Dateien in PDF-Dokumente.
>* Auf UNIX-basierten Betriebssystemen unterstützt PDF Generator WebKit- und PhantomJS-Konvertierungsrouten zum Konvertieren von HTML-Dateien in PDF-Dokumente.
>


### Zusätzliche Anforderungen für UNIX-basierte Betriebssysteme {#extrarequirements}

Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie die folgenden-Pakete aus den Installationsmedien des jeweiligen Betriebssystems:

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

* **(Nur PDF-Generator)** Der PDF Generator-Dienst unterstützt WebKit- und PhantomJS-Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente. Um die Konvertierung für die PhantomJS-Route zu aktivieren, installieren Sie die unten aufgeführten 64-Bit-Bibliotheken. Im Allgemeinen sind diese Bibliotheken bereits installiert. Wenn eine Bibliothek fehlt, installieren Sie sie manuell:

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

## Vorinstallationskonfigurationen {#preinstallationconfigurations}

Konfigurationen, die im Abschnitt „Vorinstallationskonfigurationen“ aufgeführt sind, gelten nur für den PDF Generator-Dienst. Wenn Sie den PDF Generator-Dienst nicht konfigurieren, können Sie den Abschnitt „Vorinstallationskonfigurationen“ überspringen.

### Installieren von Adobe Acrobat und Anwendungen von Drittanbietern {#install-adobe-acrobat-and-third-party-applications}

Wenn Sie den PDF Generator-Dienst verwenden möchten, um native Dateiformate wie Microsoft® Word, Microsoft® Excel, Microsoft® PowerPoint, OpenOffice, WordPerfect X7 und Adobe Acrobat in PDF Documents zu konvertieren, stellen Sie sicher, dass diese Anwendungen auf dem AEM Forms-Server installiert sind.

>[!NOTE]
>
>* Adobe Acrobat, Microsoft® Word, Excel und Powerpoint sind nur für Microsoft® Windows verfügbar. Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie OpenOffice, um Rich-Text-Dateien und unterstützte Microsoft® Office-Dateien in PDF-Dokumente zu konvertieren.
>* Schließen Sie alle Dialogfelder, die nach der Installation von Adobe Acrobat und Software von Drittanbietern für alle Benutzer angezeigt werden, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
>* Starten Sie die installierte Software mindestens einmal. Schließen Sie alle Dialogfelder für alle Benutzer, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
>


Öffnen Sie nach der Installation von Acrobat Microsoft® Word. Klicken Sie auf der Registerkarte **Acrobat** auf **PDF erstellen** und konvertieren Sie eine auf dem Computer verfügbare .doc- oder .docx-Datei in ein PDF-Dokument. Wenn die Konvertierung erfolgreich war, ist AEM Forms für die Verwendung von Acrobat mit PDF Generator-Dienst bereit.

### Umgebungsvariablen einrichten {#setup-environment-variables}

Legen Sie Umgebungsvariablen für Java Development Kit (32 Bit und 64 Bit), Anwendungen von Drittanbietern und Adobe Acrobat fest. Die Umgebungsvariablen müssen den absoluten Pfad der ausführbaren Datei enthalten, über welche die entsprechende Anwendung gestartet wird. In der nachstehenden Tabelle werden beispielsweise Umgebungsvariablen für einige Anwendungen aufgelistet:

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
   <td><p>C:\Programme\Java\jdk1.8.0_74</p> </td>
  </tr>
  <tr>
   <td><p><strong>JDK (32-Bit)</strong></p> </td>
   <td><p>JAVA_HOME_32</p> </td>
   <td><p>C:\Programme (x86)\Java\jdk1.8.0_74</p> </td>
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
   <td><p>C:\Programme (x86)\OpenOffice.org 4</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Bei allen Umgebungsvariablen und den jeweiligen Pfaden wird zwischen Groß- und Kleinschreibung unterschieden.
>* JAVA_HOME, JAVA_HOME_32 und Acrobat_PATH (nur Windows) sind erforderliche Umgebungsvariablen.
>* Die Umgebungsvariable OpenOffice_PATH wird auf den Installationsordner statt auf den Pfad der ausführbaren Datei festgelegt.
>* Richten Sie keine Umgebungsvariablen für Microsoft® Office-Anwendungen wie Word, PowerPoint, Excel und Project oder für AutoCAD ein. Wenn diese Anwendungen auf dem Server installiert sind, startet der Generate PDF-Dienst sie automatisch.
>* Installieren Sie auf UNIX-basierten Plattformen OpenOffice unter dem Benutzer /root. Wenn OpenOffice nicht unter dem Benutzer /root installiert wird, kann der PDF Generator-Dienst OpenOffice-Dokumente nicht in PDF-Dokumente konvertieren. Falls Sie OpenOffice unter einem anderen Benutzer als /root installieren und ausführen müssen, gewähren Sie dem betreffenden Benutzer sudo-Rechte.
>* Wenn Sie OpenOffice auf einer UNIX-basierten Plattform verwenden, führen Sie den folgenden Befehl aus, um die Pfadvariable festzulegen:
>
> `export OpenOffice_PATH=/opt/openoffice.org4`

### (Nur für IBM® WebSphere®) IBM® SSL-Socketanbieter konfigurieren {#only-for-ibm-websphere-configure-ibm-ssl-socket-provider}

Führen Sie die folgenden Schritte aus, um den IBM® SSL-Socketanbieter zu konfigurieren:

1. Erstellen Sie eine Kopie der java.security-Datei. Der Standardspeicherort der Datei lautet `[WebSphere_installation_directory]\Appserver\java_[version]\jre\lib\security`.
1. Öffnen Sie die kopierte java.security-Datei zur Bearbeitung.
1. Ändern Sie die standardmäßigen SSL-Socketfabriken so, dass sie die JSSE2-Fabriken anstelle der standardmäßigen IBM® WebSphere®-Fabriken verwenden:

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

1. Damit AEM Forms Server die aktualisierte java.security-Datei verwenden kann, fügen Sie beim Starten des AEM Forms-Servers das folgende Java-Argument hinzu:

   `-Djava.security.properties= [path of newly created Java.security file].`

### (Nur Windows) Konfigurieren Sie den Dienst &quot;Installieren von Ink und Handschrift&quot; {#configure-install-ink-and-handwriting-service}

Wenn Sie Microsoft® Windows Server ausführen, konfigurieren Sie den Freihand- und Handschrift-Dienst. Der Dienst ist erforderlich, um Microsoft® PowerPoint-Dateien zu öffnen, die die Verknüpfungsfunktionen von Microsoft® Office verwenden:

1. Öffnen Sie den Server-Manager. Klicken Sie in der Schnellstartleiste auf das Symbol **[!UICONTROL Server-Manager]**.
1. Klicken **[!UICONTROL Funktionen hinzufügen]** im **[!UICONTROL Funktionen]** Menü. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Freihand- und Handschrift-Dienst.]**
1. Dialogfeld **[!UICONTROL Funktionen wählen]** mit **[!UICONTROL Freihand- und Handschrift-Dienst]** ausgewählt. Klicken Sie auf **[!UICONTROL Installieren]** und der Dienst wird installiert.

### (Nur Windows) Konfigurieren Sie die Dateiblockeinstellungen für Microsoft® Office {#configure-the-file-block-settings-for-microsoft-office}

Ändern Sie die Einstellungen für das Microsoft® Office Trust Center, damit der PDF Generator-Dienst Dateien konvertieren kann, die mit älteren Versionen von Microsoft® Office erstellt wurden.

1. Öffnen Sie eine Microsoft® Office-Anwendung. Zum Beispiel Microsoft® Word. Navigieren Sie zu **[!UICONTROL Datei]** > **[!UICONTROL Optionen]**. Das Dialogfeld „Optionen“ wird angezeigt.

1. Klicken Sie auf **[!UICONTROL Sicherheitscenter]** und anschließend auf **[!UICONTROL Einstellungen für das Sicherheitscenter]**.
1. Klicken Sie in den **[!UICONTROL Einstellungen für das Sicherheitscenter]** auf **[!UICONTROL Einstellungen für den Zugriffsschutz]**.
1. Deaktivieren Sie in der Liste **[!UICONTROL Dateityp]** die Option **[!UICONTROL Öffnen]** für den Dateityp, für den es dem PDF Generator-Dienst erlaubt werden soll, Dateien in PDF-Dokumente zu konvertieren.

### (Nur Windows) Berechtigung Ersetzen eines Tokens auf Prozessebene gewähren {#grant-the-replace-a-process-level-token-privilege}

Das Benutzerkonto, das zum Starten des Anwendungsservers verwendet wird, muss die Berechtigung **Ersetzen eines Tokens auf Prozessebene** haben. Das lokale Systemkonto hat standardmäßig die Berechtigung **Ersetzen eines Tokens auf Prozessebene**. Für den Server, die mit einem Benutzer der lokalen Administratorgruppe ausgeführt werden, muss die Berechtigung explizit gewährt werden. Führen Sie die folgenden Schritte durch, um  die Berechtigung zu gewähren:

1. Öffnen Sie den Gruppenrichtlinien-Editor für Microsoft® Windows. Klicken Sie zum Öffnen des Gruppenrichtlinien-Editors auf **[!UICONTROL Start]**, geben Sie im Suchfeld **gpedit.msc** ein und klicken Sie auf **[!UICONTROL Gruppenrichtlinien-Editor]**.
1. Navigieren Sie zu **[!UICONTROL Lokale Computerrichtlinie]** > **[!UICONTROL Computerkonfiguration]** > **[!UICONTROL Windows-Einstellungen]** > **[!UICONTROL Sicherheitseinstellungen]** > **[!UICONTROL Lokale Richtlinien]** > **[!UICONTROL Zuweisen von Benutzerrechten]** und bearbeiten Sie die Richtlinie **[!UICONTROL Token auf Prozessebene ersetzen]**, damit diese in der Gruppe „Administratoren“ übernommen wird.
1. Fügen Sie den Benutzer dem Eintrag „Token auf Prozessebene ersetzen“ hinzu.

### (Nur Windows) PDF Generator-Dienst für Benutzer ohne Administratorrechte aktivieren {#enable-the-pdf-generator-service-for-non-administrators}

Sie können Benutzern, die keine Administratoren sind, die Verwendung des PDF Generator-Dienstes erlauben. Normalerweise können nur Benutzer mit Administratorrechten den Dienst verwenden:

1. Erstellen Sie die Umgebungsvariable PDFG_NON_ADMIN_ENABLED.
1. Legen Sie als Wert der Umgebungsvariablen TRUE fest.
1. Starten Sie die AEM Forms-Instanz neu.

### (Nur Windows) Benutzerkontensteuerung (UAC) deaktivieren {#disable-user-account-control-uac}

1. Um auf das Systemkonfigurationsprogramm zuzugreifen, navigieren Sie zu **[!UICONTROL Start > Ausführen]** und geben Sie **[!UICONTROL MSCONFIG]**.
1. Klicken Sie auf **[!UICONTROL Instrumente]** und scrollen Sie nach unten und wählen Sie **[!UICONTROL UAC-Einstellungen ändern]**. Klicken Sie auf **[!UICONTROL Starten]**, um den Befehl in einem neuen Fenster auszuführen.
1. Stellen Sie den Schieberegler auf Nie benachrichtigen ein. Schließen Sie nach Abschluss des Vorgangs das Befehlsfenster und das Fenster für die Systemkonfiguration.
1. Überprüfen Sie, ob die Registrierungseinstellung für UAC auf 0 (Null) gesetzt ist. Führen Sie die folgenden Schritte zur Überprüfung durch:

   1. Microsoft® empfiehlt, die Registrierung zu sichern, bevor Sie sie ändern. Detaillierte Informationen zu den Schritten erfahren Sie unter [ Sichern und Wiederherstellen der Registrierung in Windows](https://support.microsoft.com/de-de/help/322756).
   1. Öffnen Sie den Microsoft® Windows Registry-Editor. Um den Registrierungs-Editor zu öffnen, gehen Sie zu „Start“ > „Ausführen“, geben Sie regedit ein und klicken Sie auf „OK“.
   1. Navigieren Sie zu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Stellen Sie sicher, dass der Wert EnableLUA auf 0 (null) gesetzt ist. 
   1. Stellen Sie sicher, dass der Wert **EnableLUA** auf 0 (null) gesetzt ist. Wenn der Wert ungleich 0 ist, ändern Sie den Wert auf 0. Schließen Sie den Registrierungseditor.

1. Starten Sie den Computer neu.

### (Nur Windows) Deaktivieren des Fehlerberichterstellungsdienstes {#disable-error-reporting-service}

Beim Konvertieren eines Dokuments in eine PDF mithilfe des PDF Generator-Dienstes unter Windows Server meldet Windows Server gelegentlich, dass bei der ausführbaren Datei ein Problem aufgetreten ist und beendet werden muss. Das wirkt sich jedoch nicht auf die PDF-Konvertierung aus, da sie im Hintergrund läuft.

Um diesen Fehler zu vermeiden, können Sie den Fehlerbericht deaktivieren. Weitere Informationen zum Deaktivieren von Fehlerberichten finden Sie unter [https://technet.microsoft.com/en-us/library/cc754364.aspx](https://technet.microsoft.com/en-us/library/cc754364.aspx).

### (Nur Windows) Konfigurieren von HTML zur PDF-Konvertierung {#configure-html-to-pdf-conversion}

Der PDF Generator-Dienst bietet WebKit-, WebCapture- und PhantomJS-Routen oder -Methoden zum Konvertieren von HTML-Dateien in PDF-Dokumente. Um unter Windows die Konvertierung für WebKit- und Acrobat WebCapture-Routen zu aktivieren, kopieren Sie die Unicode-Schriftart in den Ordner %windir%\fonts.

>[!NOTE]
>
>Wenn Sie neue Schriftarten im Ordner &quot;Schriftarten&quot;installieren, starten Sie die AEM Forms-Instanz neu.

### (Nur UNIX-basierte Plattformen) Zusätzliche Konfigurationen für die Konvertierung von HTML zu PDF  {#extra-configurations-for-html-to-pdf-conversion}

Auf UNIX-basierten Plattformen unterstützt der PDF Generator-Dienst WebKit- und PhantomJS-Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente. Um die „HTML in PDF“-Konvertierung, führen Sie für Ihre bevorzugte Konvertierungsroute die folgenden Konfigurationen durch:

### (Nur UNIX-basierte Plattformen) Unterstützung für Unicode-Schriftarten aktivieren (nur WebKit) {#enable-support-for-unicode-fonts-webkit-only}

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
>* Unter Red Hat® Enterprise Linux® 6.x und höher sind die Schriften &quot;Courier&quot;nicht verfügbar. Laden Sie zum Installieren der Courier-Schriftarten das Archiv font-ibm-type1-1.0.3.zip herunter. Extrahieren Sie das Archiv unter /usr/share/fonts. Erstellen Sie eine symbolische Verknüpfung aus /usr/share/X11/fonts to /usr/share/fonts.
>* Löschen Sie alle .lst-Schriftartartencachedateien aus den Ordnern „Html2PdfSvc/bin“ und „/usr/share/fonts“. 
>* Stellen Sie sicher, dass die Ordner /usr/lib/X11/fonts und /usr/share/fonts vorhanden sind. Wenn die Ordner nicht vorhanden sind, verwenden Sie den Befehl „ln“, um eine symbolische Verknüpfung vom Ordner /usr/share/X11/fonts auf /usr/lib/X11/fonts zu erstellen und eine andere symbolische Verknüpfung von /usr/share/fonts auf /usr/share/X11/fonts. Vergewissern Sie sich außerdem, dass die Courier-Schriftarten unter „/usr/lib/X11/fonts“ verfügbar sind..
>* Stellen Sie sicher, dass alle Schriftarten (Unicode und Nicht-Unicode) im Ordner /usr/share/fonts or /usr/share/X11/fonts verfügbar sind.
>* Wenn Sie den PDF Generator-Dienst unter einem anderen Benutzer als /root ausführen, gewähren Sie dem betreffenden Benutzer Lese- und Schreibzugriff auf alle Schriftartenordner.
>* Wenn Sie neue Schriftarten im Ordner &quot;Schriftarten&quot;installieren, starten Sie die AEM Forms-Instanz neu.
>


## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält AEM Forms Document Services und andere AEM Forms-Funktionen. Führen Sie die folgenden Schritte aus, um das Paket zu installieren:

1. Öffnen Sie [Software Distribution](https://experience.adobe.com/downloads). Zum Anmelden bei Software Distribution benötigen Sie eine Adobe ID.
1. Tippen Sie im Kopfzeilenmenü auf **[!UICONTROL Adobe Experience Manager]**.
1. Im Abschnitt **[!UICONTROL Filter]**:
   1. Wählen Sie **[!UICONTROL Formulare]** aus der Dropdown-Liste **[!UICONTROL Lösung]**.
   2. Wählen Sie die Version und den Typ für das Paket aus. Sie können auch die **[!UICONTROL Suchdownloads]** Option zum Filtern der Ergebnisse.
1. Tippen Sie auf den Paketnamen für Ihr Betriebssystem und wählen Sie **[!UICONTROL EULA-Bedingungen akzeptieren]** und tippen Sie auf **[!UICONTROL Download]**.
1. Öffnen Sie [Package Manager](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/contentmanagement/package-manager.html) und klicken Sie auf **[!UICONTROL Paket hochladen]**, um das Paket hochzuladen.
1. Wählen Sie das Paket aus und klicken Sie auf **[!UICONTROL Installieren]**.

   Sie können das Paket auch über den direkten Link herunterladen, der im Abschnitt [AEM Forms-Versionen](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) Artikel.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Halten Sie den Server nicht sofort an.** Warten Sie vor dem Beenden des AEM Forms-Servers, bis die Meldungen ServiceEvent REGISTERED und ServiceEvent UNREGISTERED nicht mehr in der `[AEM-Installation-Directory]/crx-quickstart/logs/error`.log und das Protokoll ist stabil.

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

### Boot-Delegierung für RSA-/BouncyCastle-Bibliotheken konfigurieren  {#configure-boot-delegation-for-rsa-bouncycastle-libraries}

1. Halten Sie die AEM-Instanz an. Navigieren Sie zum [AEM Installationsverzeichnis]\crx-quickstart\conf\ folder Öffnen Sie die Datei sling.properties zur Bearbeitung.

   Wenn Sie `[AEM installation directory]\crx-quickstart\bin\start.bat`zum Starten einer AEM-Instanz verwenden, bearbeiten Sie die sling.properties-Datei unter `[AEM_root]\crx-quickstart\`.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   ```

1. (Nur AIX®) Fügen Sie der Datei sling.properties die folgenden Eigenschaften hinzu:

   ```shell
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Speichern und schließen Sie die Datei.

### Schriftmanagerdienst konfigurieren  {#configuring-the-font-manager-service}

1. Anmelden bei [AEM Configuration Manager](http://localhost:4502/system/console/configMgr) als Administrator.
1. Suchen und öffnen Sie die **[!UICONTROL CQ-DAM-Handler-Gibson Font Manager]** Dienst. Geben Sie den Pfad für die Ordner Systemschriftarten, Adobe-Serverschriftarten und Kundenschriftarten an. Klicken Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Die Rechte zur Verwendung von Schriften anderer Anbieter als Adobe unterliegen dem Lizenzvertrag dieser Anbieter von Schriftarten und werden nicht von der Lizenz für die Adobe-Software abgedeckt. Adobe empfiehlt, dass Sie alle Lizenzvereinbarungen, die nicht für die Adobe gelten, überprüfen und sicherstellen, dass Sie diese einhalten, bevor Sie Schriftarten, die nicht zur Adobe gehören, mit der Adobe-Software verwenden, insbesondere was die Verwendung von Schriftarten in einer Serverumgebung betrifft.
   > Starten Sie die AEM Forms-Instanz neu, wenn Sie neue Zeichensätze im Zeichensatzordner installieren.

### Konfigurieren Sie ein lokales Benutzerkonto zum Ausführen des PDF Generator-Dienstes  {#configure-a-local-user-account-to-run-the-pdf-generator-service}

Zum Ausführen des PDF Generator-Dienstes ist ein lokales Benutzerkonto erforderlich. Anweisungen zum Erstellen eines lokalen Benutzers finden Sie unter [Erstellen eines Benutzerkontos unter Windows](https://support.microsoft.com/en-us/help/13951/windows-create-user-account) oder erstellen Sie ein Benutzerkonto auf UNIX-basierten Plattformen.

1. Öffnen Sie die [AEM Forms PDF Generator-Konfiguration](http://localhost:4502/libs/fd/pdfg/config/ui.html) Seite.

1. Im **[!UICONTROL Benutzerkonten]** auf, geben Sie die Anmeldeinformationen für ein lokales Benutzerkonto ein und klicken Sie auf **[!UICONTROL Einsenden]**. Wenn Sie unter Microsoft® Windows aufgefordert werden, gewähren Sie dem Benutzer Zugriff. Wenn der konfigurierte Benutzer erfolgreich hinzugefügt wurde, wird er unter der **[!UICONTROL Ihre Benutzerkonten]** im Abschnitt **[!UICONTROL Benutzerkonten]** Registerkarte.

### Zeitlimiteinstellungen konfigurieren {#configure-the-time-out-settings}

1. In [AEM Konfigurationsmanager](http://localhost:4502/system/console/configMgr), suchen und öffnen Sie die **[!UICONTROL Jacorb ORB Provider]** Dienst.

   Fügen Sie im Feld **[!UICONTROL Custom Properties.name]** Folgendes hinzu und klicken Sie auf **[!UICONTROL Speichern]**. Das ausstehende Antwort-Timeout (auch als CORBA-Client-Timeout bezeichnet) wird auf 600 Sekunden festgelegt.

   `jacorb.connection.client.pending_reply_timeout=600000`

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Instrumente]** > **[!UICONTROL Forms]** > **[!UICONTROL PDF Generator konfigurieren]**. Die Standard-URL ist <http://localhost:4502/libs/fd/pdfg/config/ui.html>.

   Öffnen Sie die Registerkarte **[!UICONTROL Allgemeine Konfiguration]** und ändern Sie die Werte der folgenden Felder für Ihre Umgebung:

<table>
 <tbody>
  <tr>
   <td>Feld</td>
   <td>Beschreibung</td>
   <td>Standardwert</td>
  </tr>
  <tr>
   <td>Konvertierungstimeout für Server</td>
   <td>Eine PDFG-Konversion bleibt für die im Konvertierungstimeout für Server definierte Anzahl von Sekunden aktiv</td>
   <td>270 Sekunden<br /> </td>
  </tr>
  <tr>
   <td>Überprüfung der PDFG-Bereinigung (Sekunden)</td>
   <td>Die für Vorgänge nach der Konvertierung benötigte Anzahl von Sekunden.<br /> </td>
   <td>3600 Sekunden</td>
  </tr>
  <tr>
   <td>Ablaufzeit für Auftrag (Sekunden)</td>
   <td>Die Dauer, für die der PDF Generator-Dienst eine Konvertierung ausführen darf. Stellen Sie sicher, dass der Wert für "Auftragsablauf (Sekunden)"größer als der Wert für "PDFG-Bereinigungsprüfung (Sekunden)"ist.</td>
   <td>7200 Sekunden</td>
  </tr>
 </tbody>
</table>

### (Nur Windows) Konfigurieren von Acrobat für den PDF Generator-Dienst {#configure-acrobat-for-the-pdf-generator-service}

Unter Microsoft® Windows verwendet der PDF Generator-Dienst Adobe Acrobat, um unterstützte Dateiformate in ein PDF-Dokument zu konvertieren. Führen Sie die folgenden Schritte aus, um Adobe Acrobat für den PDF Generator-Dienst zu konfigurieren:

1. Öffnen Sie Acrobat und wählen Sie **[!UICONTROL Bearbeiten]**> **[!UICONTROL Voreinstellungen]**> **[!UICONTROL Updater]**. Deaktivieren Sie in Auf Updates überprüfen die Option **[!UICONTROL Updates automatisch installieren]** und klicken Sie auf **[!UICONTROL OK]**. Schließen Sie Acrobat.
1. Doppelklicken Sie auf ein PDF-Dokument auf Ihrem System. Beim ersten Start von Acrobat werden die Dialogfelder für Anmeldung, der Begrüßungsbildschirm und die Endbenutzerlizenzvereinbarung (EULA) angezeigt. Schließen Sie die Dialogfelder für alle Benutzer, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
1. Führen Sie die Stapeldatei des PDF Generator-Dienstprogramms aus, um Acrobat für den PDF Generator-Dienst zu konfigurieren:

   1. Öffnen [AEM Package Manager](http://localhost:4502/crx/packmgr/index.jsp) und laden Sie die `adobe-aemfd-pdfg-common-pkg-[version].zip` aus dem Package Manager.
   1. Entpacken Sie die heruntergeladene .zip-Datei. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.
   1. Navigieren Sie zum `[extracted-zip-file]\jcr_root\etc\packages\day\cq60\fd\adobe-aemds-common-pkg-[version]\jcr_root\etc\packages\day\cq60\fd\adobe-aemfd-pdfg-common-pkg-[version]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]` Verzeichnis. Führen Sie die folgende Stapelverarbeitungsdatei aus:

      `Acrobat_for_PDFG_Configuration.bat`

      Acrobat ist konfiguriert, um mit dem PDF Generator-Dienst zu laufen.

1. Ausführen [System Readiness Tool (SRT)](#SRT) , um die Installation von Acrobat zu überprüfen.

### (Nur Windows) Konfigurieren der primären Route für die Konvertierung von HTML zu PDF {#configure-primary-route-for-html-to-pdf-conversion-windows-only}

Der PDF Generator-Dienst bietet mehrere Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente: WebKit, Acrobat WebCapture (nur Windows) und PhantomJS. Adobe empfiehlt die Verwendung der PhantomJS-Route, da sie dynamische Inhalte verarbeiten kann und keine Abhängigkeiten von 32-Bit-Bibliotheken, 32-Bit-JDK aufweist oder keine zusätzlichen Schriftarten erfordert. Außerdem erfordert die PhantomJS-Route zum Ausführen der Konvertierung keinen sudo- oder root-Zugriff.

Standardmäßig ist WebKit die primäre Route für die „HTML in PDF“-Konvertierung. So ändern Sie die Konvertierungsroute:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Werkzeuge]** >**[!UICONTROL Formulare]** > **[!UICONTROL PDF Generator konfigurieren]**.

1. Im **[!UICONTROL Allgemeine Konfiguration]** Registerkarte wählen Sie die bevorzugte Konversionsroute aus dem **[!UICONTROL Primäre Route für HTML-PDF-Konvertierungen]** Dropdown-Liste.

### Initialisieren des globalen Trust Store {#intialize-global-trust-store}

Mithilfe der Trust Store-Verwaltung können Sie Zertifikate importieren, bearbeiten und löschen, die Sie auf dem Server zur Überprüfung digitaler Signaturen und zur Zertifikatauthentifizierung als vertrauenswürdig einstufen. Sie können eine beliebige Anzahl von Zertifikaten im- und exportieren. Nachdem ein Zertifikat importiert wurde, können die Vertrauenseinstellungen und der Trust Store-Typ bearbeitet werden. Führen Sie die folgenden Schritte aus, um einen Trust Store zu initialisieren:

1. Melden Sie sich bei der AEM Forms-Instanz als Administrator an.
1. Navigieren Sie zu  **[!UICONTROL Instrumente]** >  **[!UICONTROL Sicherheit]** >  **[!UICONTROL Trust Store]**.
1. Klicken  **[!UICONTROL Erstellen von TrustStore]**. Kennwort festlegen und tippen Sie auf **[!UICONTROL Speichern]**.

### Zertifikate für Reader Extension- und Encryption-Dienst einrichten {#set-up-certificates-for-reader-extension-and-encryption-service}

Der DocAssurance-Dienst kann Verwendungsrechte auf PDF-Dokumente anwenden. Um Verwendungsrechte auf PDF-Dokumente anzuwenden, konfigurieren Sie die Zertifikat.

Stellen Sie vor dem Einrichten der Zertifikate Folgendes sicher:

* Zertifikatdatei (.pfx).

* Kennwort für privaten Schlüssel, das mit dem Zertifikat bereitgestellt wird.

* Alias für privaten Schlüssel. Sie können den Java-Keytool-Befehl ausführen, um den Alias für den privaten Schlüssel anzuzeigen:
   `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

* Kennwort für KeyStore-Datei. Wenn Sie das Adobe Reader Extensions-Zertifikat verwenden, ist das Keystore-Datei-Kennwort immer dasselbe wie das Kennwort für den privaten Schlüssel.

Führen Sie die folgenden Schritte aus, um die Zertifikate zu konfigurieren:

1. Melden Sie sich bei der AEM-Autoreninstanz als Administrator an. Navigieren Sie zu **[!UICONTROL Tools]**> **[!UICONTROL Sicherheit]**> **[!UICONTROL Benutzer]**.
1. Klicken Sie auf das **[!UICONTROL Namensfeld]** des Benutzerkontos. Die Seite **[!UICONTROL Edit User Settings]** (Benutzereinstellungen bearbeiten) wird geöffnet. Auf der AEM-Authoring-Instanz residieren Zertifikate in einem KeyStore. Wenn Sie noch keinen KeyStore erstellt haben, klicken Sie auf **[!UICONTROL KeyStore erstellen]** und legen Sie ein neues Kennwort für den KeyStore fest. Wenn der Server bereits einen KeyStore enthält, überspringen Sie diesen Schritt.  Wenn Sie das Adobe Reader Extensions-Zertifikat verwenden, ist das Keystore-Datei-Kennwort immer dasselbe wie das Kennwort für den privaten Schlüssel.
1. Im **[!UICONTROL Benutzereinstellungen bearbeiten]** Seite, wählen Sie die **[!UICONTROL KeyStore]** Registerkarte. Erweitern Sie die **[!UICONTROL Privaten Schlüssel aus Key Store-Datei hinzufügen]** und geben Sie einen Alias an. Der Aliasname wird verwendet, um den Reader Extensions-Vorgang durchzuführen.
1. Um die Zertifikatdatei hochzuladen, klicken Sie auf **[!UICONTROL Select Key Store File]** (KeyStore-Datei auswählen) und laden Sie eine &lt;Dateiname>.pfx-Datei hoch.

   Fügen Sie die Werte für **[!UICONTROL Key Store Password]** (KeyStore-Kennwort),**[!UICONTROL Private Key Password]** (Kennwort für privaten Schlüssel)  und **[!UICONTROL Private Key Alias]**(Alias des privaten Schlüssels) für das Zertifikat in den jeweiligen Feldern hinzu. Klicken Sie auf **[!UICONTROL Senden]**.

   >[!NOTE]
   >
   >Ersetzen Sie in der Produktionsumgebung die Testzugangsdaten durch Produktionszugangsdaten. Stellen Sie sicher, dass Sie Ihre alten Reader Extensions-Anmeldedaten löschen, bevor Sie abgelaufene oder Testberechtigungen aktualisieren.

1. Klicken **[!UICONTROL Speichern und schließen]** auf **[!UICONTROL Benutzereinstellungen bearbeiten]** Seite.

### AES-256 aktivieren {#enable-aes}

Zur Verwendung der AES 256-Verschlüsselung für PDF-Dateien laden Sie die Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy-Dateien herunter und installieren Sie sie. Ersetzen Sie die Dateien „local_policy.jar“ und „US_export_policy.jar“ im Ordner „jre/lib/security“. Wenn Sie beispielsweise Sun JDK verwenden, kopieren Sie die heruntergeladenen Dateien in die `[JAVA_HOME]/jre/lib/security` Ordner.

Der Assembler-Dienst hängt vom Reader Extension-Dienst, vom Signature-Dienst, vom Forms-Dienst und vom Output-Dienst ab. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die erforderlichen Dienste aktiv sind:

1. Anmelden bei URL `https://'[server]:[port]'/system/console/bundles` als Administrator.
1. Suchen Sie den folgenden Dienst, und stellen Sie sicher, dass sich die Dienste aktiv sind:

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

## Bekannte Probleme und Fehlerbehebung {#known-issues-and-troubleshooting}

* Die „HTML in PDF“-Konvertierung schlägt fehl, wenn eine komprimierte Eingabedatei (ZIP) HTML-Dateien enthält, deren Dateinamen Doppelbyte-Zeichen enthalten. Verwenden Sie zur Vermeidung dieses Problems keine Doppelbyte-Zeichen in Namen von HTML-Dateien.

* Gehen Sie auf UNIX-basierten Betriebssystemen wie folgt vor, um fehlende Bibliotheken zu finden:

1. Navigieren Sie zu `[crx-repository]/bedrock/svcnative/HtmlToPdfSvc/bin/`.

1. Führen Sie folgenden Befehl aus. um alle Bibliotheken aufzulisten, die PhantomJS für die „HTML in PDF“-Konvertierung benötigt.

   `ldd phantomjs`

   Führen Sie folgenden Befehl aus. um fehlende Bibliotheken aufzulisten.

   `ldd phantomjs | grep not`

1. Installieren Sie die fehlenden Bibliotheken manuell.

## System Readiness Tool (SRT) {#SRT}

Das Systembereitschaftstool prüft, ob der Computer ordnungsgemäß für die Ausführung von PDF Generator-Konvertierungen konfiguriert ist. Das Tool generiert einen Bericht unter dem angegebenen Pfad. So führen Sie das Tool aus:

1. Erstellen Sie eine Konfigurationsdatei für das Tool Systembereitschaft . Beispiel: srt_config.yaml. Das Format der Datei lautet:

   ```
      # =================================================================
      # SRT Configuration
      # =================================================================
      #Note - follow correct format to avoid parsing failures
      #e.g. <param name>:<space><param value> 
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

1. Öffnen Sie die Eingabeaufforderung. Navigieren Sie zum `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools` Ordner. Führen Sie in der Eingabeaufforderung den folgenden Befehl aus:

   `java -jar forms-srt-[version].jar [Path_of_reports_folder] en`

   >[!NOTE]
   >
   >Wenn das Systembereitschaftswerkzeug meldet, dass die pdfgen.api-Datei nicht im Acrobat-Plug-in-Ordner verfügbar ist, kopieren Sie die pdfgen.api-Datei aus dem Ordner `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]\plugins\x86_win32` Verzeichnis in `[Acrobat_root]\Acrobat\plug_ins` Verzeichnis.

1. Navigieren Sie zu `[Path_of_reports_folder]`. Öffnen Sie die Datei SystemReadinessTool.html . Überprüfen Sie den Bericht und beheben Sie die erwähnten Probleme.

## Fehlerbehebung

Wenn Probleme auftreten, auch wenn alle vom SRT-Tool gemeldeten Probleme behoben wurden, führen Sie die folgenden Prüfungen durch:

+++ Adobe Acrobat

* Nur sicherstellen [unterstützte Version](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) von Microsoft® Office (32 Bit) und Adobe Acrobat installiert ist und das Öffnen von Dialogfeldern abgebrochen wird.
* Stellen Sie sicher, dass der Adobe Acrobat Update Service deaktiviert ist.
* Stellen Sie sicher, dass [Acrobat_for_PDFG_Configuration.bat](#configure-acrobat-for-the-pdf-generator-service) Batch-Datei mit Administratorrechten ausgeführt wurde.
* Stellen Sie sicher, dass in der PDF-Konfigurationsoberfläche ein PDF Generator-Benutzer hinzugefügt wird.
* Stellen Sie sicher, dass [Ersetzen eines Tokens auf Prozessebene](#grant-the-replace-a-process-level-token-privilege) -Berechtigung für den PDF Generator-Benutzer hinzugefügt.
* (Bei App-Server-basierten Installationen) Stellen Sie sicher, dass der Anwendungsserver als Dienst ausgeführt wird.
* Stellen Sie sicher, dass die Benutzer Lese- und Schreibberechtigungen für den temporären Ordner von PDF Generator und den temporären Ordnern der Betriebssysteme haben. Zum Beispiel `<crx-quickstart-home>\temp` und `C:\Windows\Temp`
* Stellen Sie sicher, dass Acrobat PDFMaker Office COM Add für Microsoft Office-Anwendungen aktiviert ist. Wenn das Add-In nicht aktiviert ist, führen Sie die Adobe Acrobat-Reparatur aus und führen Sie die [Acrobat_for_PDFG_Configuration.bat](#configure-acrobat-for-the-pdf-generator-service) und starten Sie den AEM Forms-Server neu.

+++

+++Office öffnen

**Microsoft® Windows**

* Stellen Sie sicher, dass [unterstützte Version](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) von Open Office installiert ist und das Öffnen von Dialogfeldern für alle Anwendungen abgebrochen wird.
* Stellen Sie sicher, dass in der PDF-Konfigurationsoberfläche ein PDF Generator-Benutzer hinzugefügt wird.
* Stellen Sie sicher, dass [Systembereitschaftswerkzeug](#SRT) meldet keinen Fehler.
* Stellen Sie sicher, dass der PDF Generator-Benutzer Mitglied der Administratorgruppe ist, und [Ersetzen eines Tokens auf Prozessebene](#grant-the-replace-a-process-level-token-privilege) -Berechtigung für den Benutzer festgelegt ist.
* Stellen Sie sicher, dass `\Windows\SysWOW64\config\systemprofile\Deskop` vorhanden ist. Wenn der Ordner nicht vorhanden ist, erstellen Sie ihn.
* Vollständige Kontrolle über `\Windows\SysWOW64\config\systemprofile`, `<crx-quickstart-home>\temp`und `\Windows\Temp` Ordner an den PDF Generator-Benutzer.
* Stellen Sie sicher, dass der Benutzer in der Benutzeroberfläche von PDF Generator konfiguriert ist, und führen Sie die folgenden Schritte aus:
   1. Melden Sie sich mit dem PDF Generator-Benutzer bei Microsoft® Windows an.
   1. Öffnen Sie Microsoft® Office- oder Open Office-Anwendungen und brechen Sie alle Dialogfelder ab.
   1. Legen Sie AdobePDF als Standarddrucker fest.
   1. Legen Sie Acrobat als Standardprogramm für PDF-Dateien fest.
   1. Führen Sie eine manuelle Konvertierung mit den Optionen Datei > Drucken und Acrobat-Band in Microsoft Office-Anwendungen durch und brechen Sie alle Dialogfelder ab.
   1. Beenden Sie alle Konvertierungsprozesse wie winword.exe, powerpoint.exe und excel.exe.
   1. Starten Sie den AEM Forms-Server neu.

**Linux®**

* Stellen Sie sicher, dass [unterstützte Version](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) von Open Office installiert ist, werden die Dialogfelder zum Öffnen für alle Anwendungen abgebrochen und Office-Anwendungen werden erfolgreich gestartet.
* Umgebungsvariable erstellen `OpenOffice_PATH` und legen Sie sie so fest, dass sie auf die OpenOffice-Installation verweist, die in der [console](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/) oder das dt-Profil (Gerätestruktur).
* Verwenden Sie 32-Bit Java™, um den AEM Forms-Server zu starten.
* Wenn bei der Installation von OpenOffice Probleme auftreten, stellen Sie sicher, dass [32-Bit-Bibliotheken](#extrarequirements) für die OpenOffice-Installation erforderlich sind, sind verfügbar.

+++

+++HTMLtoPDF

* Stellen Sie sicher, dass Schriftartenordner in der PDF Generator-Konfigurationsoberfläche hinzugefügt werden.

+++

+++Linux® und Solaris™ (WebKit-Konversion)

* Stellen Sie sicher, dass die Ordner `/usr/lib/X11/fonts` und `/usr/share/fonts` existieren. Wenn die Verzeichnisse nicht vorhanden sind, erstellen Sie eine symbolische Verknüpfung aus `/usr/share/X11/fonts` nach `/usr/lib/X11/fonts` und eine andere symbolische Verknüpfung von `/usr/share/fonts` nach `/usr/share/X11/fonts`.

   ```
   ln -s /usr/share/fonts /usr/share/X11/fonts
   
   ln -s /usr/share/X11/fonts /usr/lib/X11/fonts
   ```

* Stellen Sie sicher, dass IBM-Schriftarten unter &quot;usr/share/fonts&quot;kopiert werden.
* Stellen Sie sicher, dass die Ghost-Sicherheitslücke glibc auf dem Computer behoben ist. Verwenden Sie Ihren Standard-Paketmanager, um auf die neueste Version von glibc zu aktualisieren. Es enthält eine Fehlerbehebung für Geister.
* Stellen Sie sicher, dass die neuesten Versionen der 32-Bit-Bibliotheken &quot;curl&quot;, &quot;libcrypto&quot;und &quot;libssl&quot;auf dem System installiert sind. Erstellen von Symlinks `/usr/lib/libcurl.so` (oder libcurl.a für AIX®), `/usr/lib/libcrypto.so` (oder libcrypto.a für AIX®) und `/usr/lib/libssl.so` (oder libssl.a für AIX®), die auf die neuesten Versionen (32 Bit) der jeweiligen Bibliotheken verweist.

* Führen Sie die folgenden Schritte für den IBM® SSL-Socket-Provider aus:
   1. Kopieren Sie die Datei java.security aus `<WAS_Installed_JAVA>\jre\lib\security` an einen beliebigen Speicherort auf Ihrem AEM Forms-Server. Der Standardspeicherort ist Standardspeicherort = `<WAS_Installed>\Appserver\java_1.7_64\jre\lib\security`.

   1. Bearbeiten Sie die Datei java.security am kopierten Speicherort und ändern Sie die standardmäßigen SSL-Socket-Factories mit JSSE2-Factories (verwenden Sie JSSE2-Factories anstelle von WebSphere®).

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

+++Linux® und Solaris(PhantomJS)HTMLtoPDF

* Stellen Sie sicher, dass die 32-Bit-Bibliothek (libicudata.so.42) für Webkit-basierte HTMLoPDF-Konvertierung und 64-Bit-Bibliotheken (libicudata.so.42 libs) für PhantomJS-basierte HTMLToPDF-Konvertierung verfügbar sind.

* Führen Sie den folgenden Befehl aus, um fehlende Bibliotheken für phantomjs aufzulisten:

```
ldd phantomjs | grep not
```

* Stellen Sie sicher, dass die Umgebungsvariable JAVA_HOME_32 auf den richtigen Speicherort verweist.

+++

+++ PDF Generator (PDFG)-Benutzer kann nicht hinzugefügt werden

* Stellen Sie sicher, dass die Redistributable Microsoft® Visual C++ 2008 x 86, Microsoft® Visual C++ 2010 x86, Microsoft® Visual C++ 2012 x86 und Microsoft® Visual C++ 2013 x 86 (32 Bit) unter Windows installiert ist.

+++

+++Automatisierungstests schlagen fehl

* Führen Sie für Microsoft® Office und OpenOffice mindestens eine manuelle Konvertierung (für jeden Benutzer) durch, um sicherzustellen, dass während der Konvertierung kein Dialogfeld angezeigt wird. Wenn ein Dialogfeld angezeigt wird, wurde es verworfen. Während der automatisierten Konvertierung sollte kein solches Dialogfeld angezeigt werden.

* Bevor Sie die Automatisierung in einer AEM Forms-OSGi-Umgebung ausführen, stellen Sie sicher, dass das Testpaket installiert und aktiv ist.

+++

+++Konvertierungen für mehrere Benutzer schlagen fehl

* Überprüfen Sie die Serverprotokolle, um zu überprüfen, ob die Konvertierung für einen bestimmten Benutzer fehlschlägt.(Process Explorer kann Ihnen dabei helfen, den laufenden Prozess für verschiedene Benutzer zu überprüfen.)

* Stellen Sie sicher, dass der für PDF Generator konfigurierte Benutzer über lokale Administratorrechte verfügt.

* Stellen Sie sicher, dass PDF Generator-Benutzer Lese-, Schreib- und Ausführungsberechtigungen für LC-temporäre Benutzer und PDFG-temporäre Benutzer haben.

* Führen Sie für Microsoft® Office und OpenOffice mindestens eine manuelle Konvertierung (für jeden Benutzer) durch, um sicherzustellen, dass während der Konvertierung kein Dialogfeld angezeigt wird. Wenn ein Dialogfeld angezeigt wird, wurde es verworfen. Während der automatisierten Konvertierung sollte kein solches Dialogfeld angezeigt werden.

* Führen Sie eine Beispielkonvertierung durch.

+++

## Nächste Schritte {#next-steps}

Sie haben ein funktionierende AEM Forms Document Services-Umgebung. Sie können für Document Services von folgenden Ausgangspunkten aus nutzen:

* [Formularorientierte Arbeitsabläufe in OSGi](/help/forms/using/aem-forms-workflow.md)
* [Überwachte Ordner](/help/forms/using/watched-folder-in-aem-forms.md)
* [Document Services-APIs](/help/forms/using/aem-document-services-programmatically.md)
