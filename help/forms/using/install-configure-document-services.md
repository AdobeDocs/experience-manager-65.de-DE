---
title: Installieren und Konfiguration von Document Services
seo-title: Installieren und Konfiguration von Document Services
description: Installieren Sie AEM Forms Document Services, um PDF-Dokumente zu erstellen, zusammenzuführen, zu verteilen, zu archivieren, digitale Signaturen hinzuzufügen, um den Zugriff auf Dokumente einzuschränken und um mit Barcodes versehene Formulare zu dekodieren.
seo-description: Installieren Sie AEM Forms Document Services, um PDF-Dokumente zu erstellen, zusammenzuführen, zu verteilen, zu archivieren, digitale Signaturen hinzuzufügen, um den Zugriff auf Dokumente einzuschränken und um mit Barcodes versehene Formulare zu dekodieren.
uuid: 908806a9-b0d4-42d3-9fe4-3eae44cf4326
topic-tags: installing
discoiquuid: b53eae8c-16ba-47e7-9421-7c33e141d268
translation-type: tm+mt
source-git-commit: a6afa740fa7897ef2629ca7ba07d6a1e08113957

---


# Installieren und Konfiguration von Document Services {#installing-and-configuring-document-services}

AEM Forms bietet eine Reihe von OSGi-Diensten für verschiedene Vorgänge auf Dokumentebene, z. B. Dienste zum Erstellen, Zusammenführen, Verteilen und Archivieren von PDF-Dokumenten, Hinzufügen digitaler Signaturen zum Einschränken des Zugriffs auf Dokumente und Dekodieren von Barcode-Formularen. Diese Dienste sind im AEM Forms Add-On-Paket enthalten. Insgesamt werden diese Dienste als Document Services bezeichnet. Die Liste der verfügbaren Document Services und ihre Hauptfunktionen finden Sie nachfolgend:

* **Assembler-Dienst:** Ermöglicht Ihnen das Kombinieren, Neuanordnen und Erweitern von PDF- und XDP-Dokumenten sowie das Abrufen von Informationen zu PDF-Dokumenten. Außerdem können Sie damit PDF-Dokumente in PDF/A-Standard konvertieren und validieren sowie PDF-Formulare, XML-Formulare und PDF-Formulare in PDF/A-1b, PDF/A-2b und PDFA/A-3b umwandeln. For more information, see [Assembler Service](/help/forms/using/assembler-service.md).

* **ConvertPDF-Dienst:** Ermöglicht die Konvertierung von PDF-Dokumenten in PostScript- oder Bilddateien (JPEG, JPEG 2000, PNG und TIFF). For more information, see [ConvertPDF Service](/help/forms/using/using-convertpdf-service.md).

* **Barcoded Forms-Dienst:** Ermöglicht die Extrahierung von Daten aus elektronischen Abbildungen von Barcodes. Der Dienst akzeptiert TIFF- und PDF-Dateien mit einem oder mehreren Strichcodes als Eingabe und extrahiert die Strichcodedaten. For more information, see [Barcoded Forms Service](/help/forms/using/using-barcoded-forms-service.md).

* **DocAssurance-Dienst:** Ermöglicht das Verschlüsseln und Entschlüsseln von Dokumenten, Erweitern der Funktionalität von Adobe Reader um zusätzliche Verwendungsrechte und Hinzufügen digitaler Signaturen zu Ihren Dokumenten. Der DocAssurance-Dienst umfasst drei Dienste: Signature, Encryption und Reader Extension. For more information, see [DocAssurance Service](/help/forms/using/overview-aem-document-services.md).

* **Encryption-Dienst:** Ermöglicht das Verschlüsseln und Entschlüsseln von Dokumenten. Wird ein Dokument verschlüsselt, ist sein Inhalt nicht mehr lesbar. Ein autorisierter Benutzer kann das Dokument entschlüsseln, um Zugriff auf den Inhalt zu erhalten. For more information, see [Encryption Service](/help/forms/using/overview-aem-document-services.md#encryption-service).

* **Forms-Dienst:** Ermöglicht die Erstellung interaktiver Clientanwendungen zur Datenerfassung, mit denen Formulare, die normalerweise in Forms Designer erstellt werden, validiert, verarbeitet, transformiert und bereitgestellt werden. Der Forms-Dienst rendert jeden Formularentwurf, den Sie zu PDF-Dokumenten entwickeln. For more information, see [Forms Service](/help/forms/using/forms-service.md).

* **Output-Dienst:** Ermöglicht die Erstellung von Dokumenten in verschiedenen Formaten, einschließlich PDF, Laserdruckerformaten und Beschriftungsdruckerformaten. Laserdruckerformate sind PostScript und Printer Control Language (PCL). For more information, see [Output Service](/help/forms/using/output-service.md).

* **PDF Generator-Dienst:** Der PDF Generator-Dienst stellt APIs zum Konvertieren nativer Dateiformate in PDF bereit. Es kann außerdem PDF-Dokumente in andere Dateiformate konvertieren und die Größe von PDF-Dokumenten optimieren. For more information, see [PDF Generator Service](aem-document-services-programmatically.md#pdfgeneratorservice).

* **Reader Extension-Dienst:** Ermöglicht Ihrem Unternehmen die einfache Freigabe interaktiver PDF-Dokumente durch Erweiterung der Funktionalität von Adobe Reader um zusätzliche Verwendungsrechte. Dieser Dienst aktiviert Funktionen, die nicht verfügbar sind, wenn ein PDF-Dokument in Adobe Reader geöffnet wird, z. B. das Hinzufügen von Kommentaren zu einem Dokument, das Ausfüllen von Formularen und das Speichern des Dokuments. For more information, see [Reader Extension Service](/help/forms/using/overview-aem-document-services.md#reader-extension-service).

* **Signature-Dienst:** Ermöglicht die Arbeit mit digitalen Signaturen und Dokumenten auf dem AEM-Server. Der Signature-Dienst wird beispielsweise häufig in folgenden Situationen genutzt:

   * Der AEM-Server zertifiziert ein Formular, bevor es an einen Benutzer zum Öffnen in Acrobat oder Adobe Reader gesendet wird.
   * Der AEM-Server prüft die Gültigkeit einer Signatur, die einem Formular in Acrobat oder Adobe Reader hinzugefügt wurde.
   * Der AEM-Server signiert ein Formular im Auftrag eines Beglaubigers.
   Der Signature-Dienst greift auf Zertifikate und Berechtigungen zu, die im Trust Store gespeichert sind. For more information, see [Signature Service](/help/forms/using/aem-document-services-programmatically.md).

AEM Forms ist eine leistungsstarke Plattform der Unternehmensklasse. Die Dokument-Services sind nur eine der Funktionen von AEM Forms. Eine vollständige Liste der Funktionen finden Sie unter [Einführung in AEM Forms](/help/forms/using/introduction-aem-forms.md).

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

   * 15 GB temporärer Speicherplatz für Microsoft Windows-basierte Installationen.
   * 6 GB temporärer Speicherplatz für UNIX-basierte Installationen.

* Die für die Konvertierung von PDF Generator unter Microsoft Windows und Linux erforderliche Client-Software wird installiert:

   * **Microsoft Windows**: Installieren von [Microsoft](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)Office oder [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator)
   * **Linux**: Apache [OpenOffice installieren](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)

>[!NOTE]
>
>* Unter Microsoft Windows unterstützt PDF Generator WebKit-, Acrobat WebCapture- und PhantomJS-Konvertierungswege zum Konvertieren von HTML-Dateien in PDF-Dokumente.
>* Auf UNIX-basierten Betriebssystemen unterstützt PDF Generator WebKit- und PhantomJS-Konvertierungswege zum Konvertieren von HTML-Dateien in PDF-Dokumente.
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

Wenn Sie mit dem PDF Generator-Dienst native Dateiformate wie Microsoft Word, Microsoft Excel, Microsoft PowerPoint, OpenOffice, WordPerfect X7 und Adobe Acrobat in PDF-Dokumente konvertieren möchten, stellen Sie sicher, dass diese Anwendungen auf dem AEM Forms-Server installiert sind.

>[!NOTE]
>
>* Adobe Acrobat, Microsoft Word, Excel und PowerPoint sind nur für Microsoft Windows verfügbar. Wenn Sie das UNIX-basierte Betriebssystem verwenden, installieren Sie OpenOffice, um Rich Text-Dateien und unterstützte Microsoft Office-Dateien in PDF-Dokumente zu konvertieren.
>* Schließen Sie alle Dialogfelder, die nach der Installation von Adobe Acrobat und Software von Drittanbietern für alle Benutzer angezeigt werden, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
>* Starten Sie die installierte Software mindestens einmal. Schließen Sie alle Dialogfelder für alle Benutzer, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
>



Öffnen Sie nach der Installation von Acrobat Microsoft Word. Klicken Sie auf der Registerkarte **Acrobat** auf **PDF erstellen** und konvertieren Sie eine auf dem Computer verfügbare .doc- oder .docx-Datei in ein PDF-Dokument. Wenn die Konvertierung erfolgreich war, ist AEM Forms für die Verwendung von Acrobat mit PDF Generator-Dienst bereit.

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
>* Bei JAVA_HOME, JAVA_HOME_32 und Acrobat_PATH (nur Windows) handelt es sich um obligatorische Umgebung.
>* Die Umgebungsvariable OpenOffice_PATH wird auf den Installationsordner statt auf den Pfad der ausführbaren Datei festgelegt.
>* Richten Sie keine Umgebung für Microsoft Office-Anwendungen wie Word, PowerPoint, Excel und Project oder für AutoCAD ein. Wenn diese Anwendungen auf dem Server installiert sind, startet der Generate PDF-Dienst sie automatisch.
>* Installieren Sie auf UNIX-basierten Plattformen OpenOffice unter dem Benutzer /root. Wenn OpenOffice nicht unter dem Benutzer /root installiert wird, kann der PDF Generator-Dienst OpenOffice-Dokumente nicht in PDF-Dokumente konvertieren. Falls Sie OpenOffice unter einem anderen Benutzer als /root installieren und ausführen müssen, gewähren Sie dem betreffenden Benutzer sudo-Rechte.
>* Wenn Sie OpenOffice auf einer UNIX-basierten Plattform verwenden, führen Sie den folgenden Befehl aus, um die Pfadvariable festzulegen:\
   >  `export OpenOffice_PATH=/opt/openoffice.org4`
>



### (Nur für IBM WebSphere) IBM-SSL-Socketanbieter konfigurieren {#only-for-ibm-websphere-configure-ibm-ssl-socket-provider}

Führen Sie die folgenden Schritte aus, um den IBM-SSL-Socketanbieter zu konfigurieren:

1. Erstellen Sie eine Kopie der java.security-Datei. Der Standardspeicherort der Datei ist `[WebSphere_installation_directory]\Appserver\java_[version]\jre\lib\security`.
1. Öffnen Sie die kopierte java.security-Datei zur Bearbeitung.
1. Ändern Sie den Standardwert für SSL-Socket-Factories, um die JSSE2-Factories anstelle der standardmäßigen IBM WebSphere-Factories zu verwenden:

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

1. Damit der AEM Forms-Server die aktualisierte java.security-Datei verwenden kann, fügen Sie beim Starten des AEM Forms-Servers das folgende Java-Argument hinzu:

   `-Djava.security.properties= [path of newly created Java.security file].`

### (Nur Windows) Konfigurieren des Dienstes &quot;Tinte und Handschrift installieren&quot; {#configure-install-ink-and-handwriting-service}

Wenn Sie Microsoft Windows Server verwenden, konfigurieren Sie den Freihand- und Handschrift-Dienst. Der Dienst ist erforderlich, um Microsoft PowerPoint-Dateien zu öffnen, die die Freihand-Funktionen von Microsoft Office verwenden:

1. Öffnen Sie den Server-Manager. Klicken Sie in der Schnellstartleiste auf das Symbol **[!UICONTROL Server-Manager]**.
1. Click **[!UICONTROL Add Features]** in the **[!UICONTROL Features]** menu. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Freihand- und Handschrift-Dienst.]**
1. Dialogfeld **[!UICONTROL Funktionen wählen]** mit **[!UICONTROL Freihand- und Handschrift-Dienst]** ausgewählt. Klicken Sie auf **[!UICONTROL Installieren]** und der Dienst wird installiert.

### (Windows Only) Configure the file block settings for Microsoft Office {#configure-the-file-block-settings-for-microsoft-office}

Ändern Sie die Einstellungen für das Sicherheitscenter von Microsoft Office, um den PDF Generator-Dienst für die Konvertierung von Dateien zu aktivieren, die mit älteren Versionen von Microsoft Office erstellt wurden.

1. Öffnen Sie eine Microsoft Office-Anwendung. Beispiel: Microsoft Word. Navigieren Sie zu **[!UICONTROL Datei]** > **[!UICONTROL Optionen]**. Das Dialogfeld „Optionen“ wird angezeigt.

1. Klicken Sie auf **[!UICONTROL Sicherheitscenter]** und anschließend auf **[!UICONTROL Einstellungen für das Sicherheitscenter]**.
1. Klicken Sie in den **[!UICONTROL Einstellungen für das Sicherheitscenter]** auf **[!UICONTROL Einstellungen für den Zugriffsschutz]**.
1. Deaktivieren Sie in der Liste **[!UICONTROL Dateityp]** die Option **[!UICONTROL Öffnen]** für den Dateityp, für den es dem PDF Generator-Dienst erlaubt werden soll, Dateien in PDF-Dokumente zu konvertieren.

### (Nur Windows) Gewähren Sie die Berechtigung Ersetzen eines Tokens auf Prozessebene {#grant-the-replace-a-process-level-token-privilege}

Das Benutzerkonto, das zum Starten des Anwendungsservers verwendet wird, muss die Berechtigung **Ersetzen eines Tokens auf Prozessebene** haben. Das lokale Systemkonto hat standardmäßig die Berechtigung **Ersetzen eines Tokens auf Prozessebene**. Für den Server, die mit einem Benutzer der lokalen Administratorgruppe ausgeführt werden, muss die Berechtigung explizit gewährt werden. Führen Sie die folgenden Schritte durch, um  die Berechtigung zu gewähren:

1. Öffnen Sie den Gruppenrichtlinien-Editor für Microsoft Windows. Klicken Sie zum Öffnen des Gruppenrichtlinien-Editors auf **[!UICONTROL Start]**, geben Sie im Suchfeld **gpedit.msc** ein und klicken Sie auf **[!UICONTROL Gruppenrichtlinien-Editor]**.
1. Navigieren Sie zu **[!UICONTROL Lokale Computerrichtlinie]** > **[!UICONTROL Computerkonfiguration]** > **[!UICONTROL Windows-Einstellungen]** > **[!UICONTROL Sicherheitseinstellungen]** > **[!UICONTROL Lokale Richtlinien]** > **[!UICONTROL Zuweisen von Benutzerrechten]** und bearbeiten Sie die Richtlinie **[!UICONTROL Token auf Prozessebene ersetzen]**, damit diese in der Gruppe „Administratoren“ übernommen wird.
1. Fügen Sie den Benutzer dem Eintrag „Token auf Prozessebene ersetzen“ hinzu.

### (Windows Only) Enable the PDF Generator service for non-administrators {#enable-the-pdf-generator-service-for-non-administrators}

Sie können Benutzern, die keine Administratoren sind, die Verwendung des PDF Generator-Dienstes erlauben. Normalerweise können nur Benutzer mit Administratorrechten den Dienst verwenden:

1. Erstellen Sie die Variable &quot;Umgebung&quot;, PDFG_NON_ADMIN_ENABLED.
1. Legen Sie als Wert der Umgebungsvariablen TRUE fest.
1. Starten Sie die AEM Forms-Instanz neu.

### (Nur Windows) Benutzerkontensteuerung deaktivieren {#disable-user-account-control-uac}

1. To access the System Configuration Utility, go to **[!UICONTROL Start > Run]** and then enter **[!UICONTROL MSCONFIG]**.
1. Click the **[!UICONTROL Tools]** tab and scroll down and select **[!UICONTROL Change UAC Settings]**. Klicken Sie auf **[!UICONTROL Starten]**, um den Befehl in einem neuen Fenster auszuführen.
1. Stellen Sie den Schieberegler auf Nie benachrichtigen ein. Schließen Sie nach Abschluss des Vorgangs das Befehlsfenster und das Fenster für die Systemkonfiguration.
1. Überprüfen Sie, ob die Registrierungseinstellung für UAC auf 0 (Null) gesetzt ist. Führen Sie die folgenden Schritte zur Überprüfung durch:

   1. Microsoft empfiehlt, eine Sicherungskopie der Registrierung zu erstellen, bevor Sie sie ändern. Detaillierte Informationen zu den Schritten erfahren Sie unter [ Sichern und Wiederherstellen der Registrierung in Windows](https://support.microsoft.com/de-de/help/322756).
   1. Öffnen Sie den Registrierungs-Editor von Microsoft Windows. Um den Registrierungs-Editor zu öffnen, gehen Sie zu „Start“ > „Ausführen“, geben Sie regedit ein und klicken Sie auf „OK“.
   1. Navigieren Sie zu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Stellen Sie sicher, dass der Wert EnableLUA auf 0 (null) gesetzt ist. 
   1. Stellen Sie sicher, dass der Wert **EnableLUA** auf 0 (null) gesetzt ist. Wenn der Wert ungleich 0 ist, ändern Sie den Wert auf 0. Schließen Sie den Registrierungseditor.

1. Starten Sie den Computer neu.

### (Nur Windows) Deaktivieren Sie den Berichte-Fehlerdienst {#disable-error-reporting-service}

Beim Konvertieren eines Dokuments in PDF mit dem PDF Generator-Dienst unter Windows Server meldet Windows Server gelegentlich, dass ein Problem bei der ausführbaren Datei aufgetreten ist und geschlossen werden muss. Das wirkt sich jedoch nicht auf die PDF-Konvertierung aus, da sie im Hintergrund läuft.

Um diesen Fehler zu vermeiden, können Sie den Fehlerbericht deaktivieren. For more information on disabling error reporting, see [https://technet.microsoft.com/en-us/library/cc754364.aspx](https://technet.microsoft.com/en-us/library/cc754364.aspx).

### (Nur Windows) &quot;HTML in PDF&quot;-Konvertierung konfigurieren {#configure-html-to-pdf-conversion}

Der PDF Generator-Dienst stellt WebKit-, WebCapture- und PhantomJS-Routen oder -Methoden zum Konvertieren von HTML-Dateien in PDF-Dokumente bereit. Um unter Windows die Konvertierung für WebKit- und Acrobat WebCapture-Routen zu aktivieren, kopieren Sie die Unicode-Schriftart in den Ordner %windir%\fonts.

>[!NOTE]
>
> Sobald Sie neue Schriftarten im Schriftartenordner installieren, starten Sie die AEM Forms-Instanz neu.


### (Nur UNIX-basierte Plattformen) Zusätzliche Konfigurationen für die Konvertierung von HTML in PDF {#extra-configurations-for-html-to-pdf-conversion}

Auf UNIX-basierten Plattformen unterstützt der PDF Generator-Dienst WebKit- und PhantomJS-Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente. Um die „HTML in PDF“-Konvertierung, führen Sie für Ihre bevorzugte Konvertierungsroute die folgenden Konfigurationen durch:

### (Nur UNIX-basierte Plattformen) Unterstützung für Unicode-Schriftarten aktivieren (nur WebKit) {#enable-support-for-unicode-fonts-webkit-only}

Kopieren Sie die Unicode-Schriftart in die folgenden Ordner, so wie es für Ihr System erforderlich ist:

* /usr/lib/X11/fonts/TrueType
* /usr/share/fonts/default/TrueType
* /usr/X11R6/lib/X11/fonts/ttf
* /usr/X11R6/lib/X11/fonts/truetype
* /usr/X11R6/lib/X11/fonts/TrueType
* /usr/X11R6/lib/X11/fonts/TTF
* /usr/openwin/lib/X11/fonts/TrueType (Solaris)

>[!NOTE]
>
>* Unter RedHat Enterprise Linux 6.x sind die Courier-Schriftarten nicht verfügbar. Laden Sie zum Installieren der Courier-Schriftarten das Archiv font-ibm-type1-1.0.3.zip herunter. Extrahieren Sie das Archiv unter /usr/share/fonts. Erstellen Sie eine symbolische Verknüpfung aus /usr/share/X11/fonts to /usr/share/fonts.
>* Löschen Sie alle .lst-Schriftartartencachedateien aus den Ordnern „Html2PdfSvc/bin“ und „/usr/share/fonts“. 
>* Stellen Sie sicher, dass die Ordner /usr/lib/X11/fonts und /usr/share/fonts vorhanden sind. Wenn die Ordner nicht vorhanden sind, verwenden Sie den Befehl „ln“, um eine symbolische Verknüpfung vom Ordner /usr/share/X11/fonts auf /usr/lib/X11/fonts zu erstellen und eine andere symbolische Verknüpfung von /usr/share/fonts auf /usr/share/X11/fonts. Vergewissern Sie sich außerdem, dass die Courier-Schriftarten unter „/usr/lib/X11/fonts“ verfügbar sind..
>* Stellen Sie sicher, dass alle Schriftarten (Unicode und Nicht-Unicode) im Ordner /usr/share/fonts or /usr/share/X11/fonts verfügbar sind.
>* Wenn Sie den PDF Generator-Dienst unter einem anderen Benutzer als /root ausführen, gewähren Sie dem betreffenden Benutzer Lese- und Schreibzugriff auf alle Schriftartenordner.
>* Sobald Sie neue Schriftarten im Schriftartenordner installieren, starten Sie die AEM Forms-Instanz neu.
>



## Installieren des AEM Forms-Add-on-Pakets {#install-aem-forms-add-on-package}

AEM Forms-Add-On-Paket ist eine Anwendung, die auf AEM bereitgestellt wird. Das Paket enthält AEM Forms Document Services und andere AEM Forms-Funktionen. Führen Sie die folgenden Schritte aus, um das Paket zu installieren:

1. Melden Sie sich beim [AEM-Server](http://localhost:4502) als Administrator an und öffnen Sie [Package Share](http://localhost:4502/crx/packageshare). Zum Anmelden bei der Paketfreigabe benötigen Sie eine Adobe ID.

1. Suchen Sie in [AEM Package Share](http://localhost:4502/crx/packageshare/login.html) nach **[!UICONTROL Add-On-Pakete für AEM 6.4 Forms]** und klicken Sie auf das Paket, das auf Ihr Betriebssystem zutrifft, und dann auf **[!UICONTROL Herunterladen]**. Lesen und akzeptieren Sie die Lizenzvereinbarung und klicken Sie auf **[!UICONTROL OK]**. Der Download wird gestartet. Nachdem der Download abgeschlossen ist, wird das Wort **[!UICONTROL Heruntergeladen]** neben dem Paket angezeigt.

   Sie können auch die Versionsnummer verwenden, um nach einem Add-On-Paket zu suchen. Die Versionsnummer für das neueste Paket finden Sie im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

1. Nachdem der Download abgeschlossen ist, klicken Sie auf **[!UICONTROL Heruntergeladen]**. Sie werden zum Paketmanager weitergeleitet. Suchen Sie im Paketmanager das heruntergeladene Paket und klicken Sie auf **[!UICONTROL Installieren]**.

   Wenn Sie das Paket manuell über den direkten Link herunterladen, der im Artikel [AEM Forms-Versionen](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) angegeben ist, melden Sie sich beim Paketmanager an, klicken Sie auf **[!UICONTROL Paket hochladen]**, wählen Sie das heruntergeladene Paket aus und klicken Sie auf „Hochladen“. Nachdem Sie das Paket hochgeladen haben, klicken Sie auf den Paketnamen und dann auf **[!UICONTROL Installieren]**.

1. Sobald das Paket installiert ist, werden Sie aufgefordert, die AEM-Instanz neu zu starten. **Halten Sie den Server nicht sofort an.** Bevor Sie den AEM Forms-Server beenden, warten Sie, bis die Nachrichten &quot;ServiceEvent REGISTERED&quot;und &quot;ServiceEvent UNREGISTERED&quot;in der Datei &quot; `[AEM-Installation-Directory]/crx-quickstart/logs/error`.log&quot;nicht mehr angezeigt werden und das Protokoll stabil ist.

## Auf die Installation folgende Konfigurationen {#post-installation-configurations}

### Boot-Delegierung für RSA-/BouncyCastle-Bibliotheken konfigurieren  {#configure-boot-delegation-for-rsa-bouncycastle-libraries}

1. Halten Sie die AEM-Instanz an. Navigate to the [AEM installation directory]\crx-quickstart\conf\ folder. Open the sling.properties file for editing.

   Wenn Sie `[AEM installation directory]\crx-quickstart\bin\start.bat`zum Starten einer AEM-Instanz verwenden, bearbeiten Sie die sling.properties-Datei unter `[AEM_root]\crx-quickstart\`.

1. Fügen Sie die folgenden Eigenschaften der sling.properties-Datei hinzu:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Nur AIX) Hinzufügen die folgenden Eigenschaften in der Datei &quot;sling.properties&quot;:

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Speichern und schließen Sie die Datei.

### Schriftmanagerdienst konfigurieren  {#configuring-the-font-manager-service}

1. Log in to [AEM Configuration Manager](http://localhost:4502/system/console/configMgr) as an administrator.
1. Locate and open the **[!UICONTROL CQ-DAM-Handler-Gibson Font Managers]** service. Geben Sie den Pfad für die Ordner Systemschriftarten, Adobe-Serverschriftarten und Kundenschriftarten an. Klicken Sie auf **[!UICONTROL Speichern]**.

   >[!NOTE]
   >
   >Die Rechte zur Verwendung von Schriften anderer Anbieter als Adobe unterliegen dem Lizenzvertrag dieser Anbieter von Schriftarten und werden nicht von der Lizenz für die Adobe-Software abgedeckt. Adobe empfiehlt, dass Sie vor der Verwendung von Drittanbieter-Schriften in Verbindung mit Adobe-Software alle relevanten Lizenzverträge der Drittanbieter lesen und dafür sorgen, dass Sie diese Verträge einhalten. Dies gilt insbesondere für die Verwendung von Schriften in einer Serverumgebung.
   > Starten Sie die AEM Forms-Instanz neu, wenn Sie neue Zeichensätze im Zeichensatzordner installieren.

### Konfigurieren Sie ein lokales Benutzerkonto zum Ausführen des PDF Generator-Dienstes  {#configure-a-local-user-account-to-run-the-pdf-generator-service}

Zum Ausführen des PDF Generator-Dienstes ist ein lokales Benutzerkonto erforderlich. For steps to create a local user, see [Create a user account in Windows](https://support.microsoft.com/en-us/help/13951/windows-create-user-account) or [create a user account in UNIX-based platforms](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Step_by_Step_Guide/s1-starting-create-account.html).

1. Open the [AEM Forms PDF Generator Configuration](http://localhost:4502/libs/fd/pdfg/config/ui.html) page.

1. In the **[!UICONTROL User Accounts]** tab, provide credentials of a local user account, and click **[!UICONTROL Submit]**. Wenn Microsoft Windows Sie dazu auffordert, erlauben Sie dem Benutzer den Zugriff. When added successfully, the configured user is displayed under the **[!UICONTROL Your user accounts]** section in the **[!UICONTROL User Accounts]** tab.

### Zeitlimiteinstellungen konfigurieren {#configure-the-time-out-settings}

1. In [AEM configuration manager](http://localhost:4502/system/console/configMgr), locate and open the **[!UICONTROL Jacorb ORB Provider]** service.

   Fügen Sie im Feld **[!UICONTROL Custom Properties.name]** Folgendes hinzu und klicken Sie auf **[!UICONTROL Speichern]**. Stellt die ausstehende Antwort-Zeitüberschreitung (auch als CORBA-Client-Timeout bezeichnet) auf 600 Sekunden ein.

   `jacorb.connection.client.pending_reply_timeout=600000`

1. Log in to the AEM author instance and navigate to **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Configure PDF Generator]**. Die Standard-URL lautet http://localhost:4502/libs/fd/pdfg/config/ui.html.

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
   <td>Eine PDFG-Konvertierung bleibt für die Dauer der im Zeitlimit für die Serverkonverversion definierten Sekunden aktiv.</td> 
   <td>270 Sekunden<br /> </td> 
  </tr> 
  <tr> 
   <td>Überprüfung der PDFG-Bereinigung (Sekunden)</td> 
   <td>Die für Vorgänge nach der Konvertierung benötigte Anzahl von Sekunden.<br /> </td> 
   <td>3600 Sekunden</td> 
  </tr> 
  <tr> 
   <td>Ablaufzeit für Auftrag (Sekunden)</td> 
   <td>Die Dauer, für die der PDF Generator-Dienst eine Konvertierung ausführen darf. Stellen Sie sicher, dass der Wert des Auftragsablaufs in Sekunden größer als der Wert des PDFG-Bereinigungsprüfungszyklus in Sekunden ist.</td> 
   <td>7200 Sekunden</td> 
  </tr> 
 </tbody> 
</table>

### (Windows only) Configure Acrobat for the PDF Generator service {#configure-acrobat-for-the-pdf-generator-service}

Unter Microsoft Windows verwendet der PDF Generator-Dienst Adobe Acrobat, um unterstützte Dateiformate in PDF-Dokumente zu konvertieren. Führen Sie die folgenden Schritte aus, um Adobe Acrobat für den PDF Generator-Dienst zu konfigurieren:

1. Öffnen Sie Acrobat und wählen Sie **[!UICONTROL Bearbeiten]**> **[!UICONTROL Voreinstellungen]**> **[!UICONTROL Updater]**. In Check for updates, deselect **[!UICONTROL Automatically install updates]**, and click **[!UICONTROL OK]**. Schließen Sie Acrobat.
1. Klicken Sie mit der Dublette auf ein PDF-Dokument auf Ihrem System. Beim ersten Start von Acrobat werden die Dialogfelder für Anmeldung, der Begrüßungsbildschirm und die Endbenutzerlizenzvereinbarung (EULA) angezeigt. Schließen Sie die Dialogfelder für alle Benutzer, die für die Verwendung des PDF Generator-Dienstes konfiguriert wurden.
1. Führen Sie die Stapeldatei des PDF Generator-Dienstprogramms aus, um Acrobat für den PDF Generator-Dienst zu konfigurieren:

   1. Open [AEM Package Manager](http://localhost:4502/crx/packmgr/index.jsp) and download the `adobe-aemfd-pdfg-common-pkg-[version].zip` file from the package manager.
   1. Entpacken Sie die heruntergeladene .zip-Datei. Öffnen Sie die Eingabeaufforderung mit Administratorrechten.
   1. Navigate to the `[extracted-zip-file]\jcr_root\etc\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]-win.zip\scripts` directory. Führen Sie die folgende Stapelverarbeitungsdatei aus:

      `Acrobat_for_PDFG_Configuration.bat`

      Acrobat ist konfiguriert, um mit dem PDF Generator-Dienst zu laufen.

1. Führen Sie das System Readiness Tool (SRT) aus, um die Installation von Acrobat zu validieren. Das Werkzeug überprüft, ob der Computer ordnungsgemäß zum Ausführen von PDF Generator-Konvertierungen konfiguriert ist, und es erstellt einen Bericht unter dem angegebenen Pfad:

   1. Öffnen Sie das Befehlszeilenfenster. Navigieren Sie zum Ordner `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\etc\fd\ pdfg\tools\adobe-aemfd-pdfg-utilities-[version]-win.zip\srt`. Führen Sie in der Eingabeaufforderung den folgenden Befehl aus:

      `cscript SystemReadinessTool.vbs [Path_of_reports_folder] en`

      >[!NOTE]
      >
      >If the System Readiness Tool reports that the pdfgen.api file is not available in the acrobat plug-ins folder then copy the pdfgen.api file from the `[extracted-adobe-aemfd-pdfg-common-pkg]\plugins\x86_win32` directory to the `[Acrobat_root]\Acrobat\plug_ins` directory.

   1. Navigieren Sie zu `[Path_of_reports_folder]`. Öffnen Sie die Datei SystemReadinessTool.html. Überprüfen Sie den Bericht und beheben Sie die erwähnten Probleme.

### (Nur Windows) Konfigurieren der primären Route für die Konvertierung von HTML in PDF {#configure-primary-route-for-html-to-pdf-conversion-windows-only}

Der PDF Generator-Dienst bietet mehrere Routen zum Konvertieren von HTML-Dateien in PDF-Dokumente: WebKit, Acrobat WebCapture (nur Windows) und PhantomJS. Adobe empfiehlt die Verwendung der PhantomJS-Route, da es über die Fähigkeit verfügt, dynamische Inhalte zu bearbeiten, und keine Abhängigkeit von 32-Bit-Bibliotheken, 32-Bit-JDK oder keine zusätzlichen Schriftarten aufweist. Außerdem erfordert die PhantomJS-Route zum Ausführen der Konvertierung keinen sudo- oder root-Zugriff.

Standardmäßig ist WebKit die primäre Route für die „HTML in PDF“-Konvertierung. So ändern Sie die Konvertierungsroute:

1. Navigieren Sie in der AEM-Autoreninstanz zu **[!UICONTROL Werkzeuge]** >**[!UICONTROL Formulare]** > **[!UICONTROL PDF Generator konfigurieren]**.

1. In the **[!UICONTROL General Configuration]** tab, select the preferred conversion route from the **[!UICONTROL Primary Route for HTML to PDF conversions]** drop-down.

### Globalen Trust Store initialisieren {#intialize-global-trust-store}

Mithilfe der Trust Store-Verwaltung können Sie Zertifikate importieren, bearbeiten und löschen, die Sie auf dem Server zur Überprüfung digitaler Signaturen und zur Zertifikatauthentifizierung als vertrauenswürdig einstufen. Sie können eine beliebige Anzahl von Zertifikaten im- und exportieren. Nachdem ein Zertifikat importiert wurde, können die Vertrauenseinstellungen und der Trust Store-Typ bearbeitet werden. Führen Sie die folgenden Schritte aus, um einen Trust Store zu initialisieren:

1. Melden Sie sich bei der AEM Forms-Instanz als Administrator an.
1. Gehen Sie zu **[!UICONTROL Werkzeuge]** > **[!UICONTROL Sicherheit]** > **[!UICONTROL Trust Store]**.
1. Klicken Sie auf TrustStore **[!UICONTROL erstellen]**. Legen Sie das Kennwort fest und tippen Sie auf **[!UICONTROL Speichern]**.

### Zertifikate für Reader Extension- und Encryption-Dienst einrichten {#set-up-certificates-for-reader-extension-and-encryption-service}

Der DocAssurance-Dienst kann Verwendungsrechte auf PDF-Dokumente anwenden. Um Verwendungsrechte auf PDF-Dokumente anzuwenden, konfigurieren Sie die Zertifikat.

Stellen Sie vor dem Einrichten der Zertifikate Folgendes sicher:

* Zertifikatdatei (.pfx).

* Kennwort für privaten Schlüssel, das mit dem Zertifikat bereitgestellt wird.

* Alias für privaten Schlüssel. Sie können den Java-Keytool-Befehl ausführen, um den Alias für den privaten Schlüssel Ansicht:
   `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

* Kennwort für KeyStore-Datei. Wenn Sie das Adobe Reader Extensions-Zertifikat verwenden, ist das Keystore-Datei-Kennwort immer dasselbe wie das Kennwort für den privaten Schlüssel.

Führen Sie die folgenden Schritte aus, um die Zertifikate zu konfigurieren:

1. Melden Sie sich bei der AEM-Autoreninstanz als Administrator an. Navigieren Sie zu **[!UICONTROL Tools]**> **[!UICONTROL Sicherheit]**> **[!UICONTROL Benutzer]**.
1. Klicken Sie auf das **[!UICONTROL Namensfeld]** des Benutzerkontos. Die Seite **[!UICONTROL Edit User Settings]** (Benutzereinstellungen bearbeiten) wird geöffnet. Auf der AEM-Authoring-Instanz residieren Zertifikate in einem KeyStore. Wenn Sie noch keinen KeyStore erstellt haben, klicken Sie auf **[!UICONTROL KeyStore erstellen]** und legen Sie ein neues Kennwort für den KeyStore fest. Wenn der Server bereits einen KeyStore enthält, überspringen Sie diesen Schritt.  Wenn Sie das Adobe Reader Extensions-Zertifikat verwenden, ist das Keystore-Datei-Kennwort immer dasselbe wie das Kennwort für den privaten Schlüssel.
1. Wählen Sie auf der Seite &quot; **[!UICONTROL Benutzereinstellungen]** bearbeiten&quot;die Registerkarte **[!UICONTROL KeyStore]** . Expand the **[!UICONTROL Add Private Key from Key Store file]** option and provide an alias. Der Aliasname wird verwendet, um den Reader Extensions-Vorgang durchzuführen.
1. Um die Zertifikatdatei hochzuladen, klicken Sie auf **[!UICONTROL Select Key Store File]** (KeyStore-Datei auswählen) und laden Sie eine &lt;Dateiname>.pfx-Datei hoch.

   Fügen Sie die Werte für **[!UICONTROL Key Store Password]** (KeyStore-Kennwort),**[!UICONTROL Private Key Password]** (Kennwort für privaten Schlüssel)  und **[!UICONTROL Private Key Alias]**(Alias des privaten Schlüssels) für das Zertifikat in den jeweiligen Feldern hinzu. Klicken Sie auf **[!UICONTROL Übermitteln]**.

   >[!NOTE]
   >
   >* Ersetzen Sie in der Produktionsumgebung die Testzugangsdaten durch Produktionszugangsdaten. Bevor Sie eine abgelaufene oder Testberechtigung aktualisieren, müssen Sie die alten Reader Extensions-Berechtigungen löschen.


1. Klicken Sie auf der Seite &quot;Benutzereinstellungen **[!UICONTROL bearbeiten&quot;auf]** Speichern &amp; Schließen **** .

### AES-256 aktivieren {#enable-aes}

Zur Verwendung der AES 256-Verschlüsselung für PDF-Dateien laden Sie die Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy-Dateien herunter und installieren Sie sie. Ersetzen Sie die Dateien „local_policy.jar“ und „US_export_policy.jar“ im Ordner „jre/lib/security“. For example, if you are using Sun JDK, copy the downloaded files to the `[JAVA_HOME]/jre/lib/security` folder.

Der Assembler-Dienst hängt vom Reader Extension-Dienst, vom Signature-Dienst, vom Forms-Dienst und vom Output-Dienst ab. Führen Sie die folgenden Schritte aus, um sicherzustellen, dass die erforderlichen Dienste aktiv sind:

1. Log in to URL `https://'[server]:[port]'/system/console/bundles` as an administrator.
1. Suchen Sie den folgenden Dienst, und stellen Sie sicher, dass sich die Dienste aktiv sind:

<table> 
 <tbody> 
  <tr> 
   <th>Dienstname</th> 
   <th>Bundle-Name</th> 
  </tr> 
  <tr> 
   <td>Dienst für Unterschriften</td> 
   <td>adobe-aemfd-signatures</td> 
  </tr> 
  <tr> 
   <td>Reader Extensions-Dienst</td> 
   <td>com.adobe.aemfd.adobe-aemfd-readerextensions<br /> </td> 
  </tr> 
  <tr> 
   <td>Formularservice</td> 
   <td>com.adobe.livecycle.adobe-lc-forms-bedrock-connector<br /> </td> 
  </tr> 
  <tr> 
   <td>Output-Dienst</td> 
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

## Nächste Schritte {#next-steps}

Sie haben ein funktionierende AEM Forms Document Services-Umgebung. Sie können für Document Services von folgenden Ausgangspunkten aus nutzen:

* [Formularorientierte Arbeitsabläufe in OSGi](/help/forms/using/aem-forms-workflow.md)
* [Überwachte Ordner](/help/forms/using/watched-folder-in-aem-forms.md)
* [Document Services-APIs](/help/forms/using/aem-document-services-programmatically.md)

