---
title: Installieren von Workbench
seo-title: Install workbench
description: Installieren Sie Workbench.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
role: Admin
exl-id: d530dbb9-f95e-4329-9665-37faf8f7931b
source-git-commit: 18cfefb794382b5314b18a62645f1fba28d314a2
workflow-type: ht
source-wordcount: '2232'
ht-degree: 100%

---

# Installieren von Workbench {#install-workbench}

Dieses Dokument enthält Anweisungen zur Installation und Konfiguration von AEM Forms Workbench. Das Installationsprogramm installiert außerdem Forms Designer.

## Wer sollte dieses Dokument lesen? {#who-should-read-this-doc}

Dieses Dokument richtet sich an Administrierende oder Entwickelnde, die für die Installation, Konfiguration, Verwaltung oder Bereitstellung von Workbench zuständig sind. Dazu gehören auch Informationen, die erforderlich sind, um Ihr System zur Unterstützung aktualisierter AEM Forms-Prozesse zu konfigurieren. Es wird vorausgesetzt, dass die Leser dieses Dokuments mit dem Microsoft® Windows®-Betriebssystem vertraut sind.

## Zusätzliche Informationen {#additional-information}

Die Ressourcen in dieser Tabelle können Ihnen dabei helfen, mehr über AEM Forms zu erfahren, und vermitteln Ihnen die ersten Schritte.
<table>
 <tbody>
  <tr>
   <td><p><strong>Informationen</strong></p> </td>
   <td><p><strong>Siehe</strong></p> </td>
  </tr>
  <tr>
   <td><p>Informationen zu Prozessen für Workbench</p> </td>
   <td><p><a href="https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf">Workbench-Hilfe</a><br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Allgemeine Informationen zu AEM Forms und dessen Integration in anderen Adobe-Produkten</p> </td>
   <td><p><a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/introduction-aem-forms.html?lang=de">Übersicht über AEM Forms</a><br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Die gesamte Dokumentation, die für AEM Forms verfügbar ist</p> </td>
   <td><p><a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/introduction-aem-forms.html?lang=de">AEM Forms-Dokumentation</a><br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Patch-Updates, technische Hinweise und zusätzliche Informationen zu dieser Produktversion</p> </td>
   <td><p>Adobe Unternehmens-Support kontaktieren</a><br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt. Es ist für die AEM Forms-Version verfügbar.

## Vor der Installation {#before-you-install}

### Installation von Workbench – Übersicht {#workbench-installation-overview}

Workbench ist eine integrierte Entwicklungsumgebung (IDE), die Entwickelnde und Formularautoren oder -autorinnen zum Erstellen automatisierter Geschäftsprozesse und Formulare verwenden. Es wird auch verwendet, um die Ressourcen und Dienste zu verwalten, die die Prozesse und Formulare verwenden.

Die folgende Abbildung zeigt die Workbench-Installation einschließlich:
* Prozess-Design mit Workbench
* Formularentwurf mithilfe von Designer

>[!NOTE]
>
>Der AEM Forms-Server erfordert ein separates Installationsprogramm. Weitere Informationen finden Sie in der Dokumentation zur Installation von AEM Forms auf JEE.

![default-render-form](assets/installing-workbench.png)

## Systemanforderungen {#system-prerequisites}

In diesem Abschnitt werden die Hardware- und Softwareanforderungen sowie die unterstützten Plattformen beschrieben.

### Mindestanforderungen an Hardware und Software {#minimum-hardware-software-requirements}

**Workbench**
Als Minimum werden die folgenden Anforderungen empfohlen: 
Speicherplatz für die Installation:
* 680 MB nur für Workbench.
* 2,15 GB auf einem einzigen Laufwerk für eine vollständige Installation von Workbench, Designer und die Assemblierung der Beispiele.
* 400 MB für temporäre Installationsordner – 200 MB im temporären Ordner des Benutzers und 200 MB im temporären Ordner von Windows.

>[!NOTE]
>
>Wenn sich diese Speicherorte alle auf einem einzigen Laufwerk befinden, müssen während der Installation 1,5 GB Speicherplatz zur Verfügung stehen. Die Dateien, die in den temporären Ordner kopiert werden, werden nach Abschluss der Installation gelöscht.

* Hardware-Anforderung: Intel® Pentium® 4 oder gleichwertiger AMD®-Prozessor, 1 GHz.
* Java™ Runtime Environment (JRE) 7.0 Update 51 oder höhere Updates zu 7.0.
* Minimale Bildschirmauflösung 1024 x 768 Pixel oder höher mit 16-Bit-Farbtiefe oder höher.
* TCP/IPv4- oder TCP/IPv6-Netzwerkverbindung zum AEM Forms-Server.
* Installieren Sie Visual C++ Redistributable Runtime Packages 2012 32-Bit.
* Installieren Sie Visual C++ Redistributable Runtime Packages 2013 32-Bit.

>[!NOTE]
>
>Sie müssen über Adminrechte verfügen, um Workbench zu installieren. Wenn Sie die Installation mit einem Konto ohne Adminrechte durchführen, werden Sie vom Installationsprogramm zur Eingabe der Anmeldeinformationen für ein entsprechendes Konto aufgefordert.

### Unterstützte Plattformen {#supported-platforms}

Die vollständige Liste der unterstützten Plattformen für Workbench finden Sie unter [Von AEM Forms unterstützte Plattformen](https://www.adobe.com/go/learn_aemforms_supportedplatforms_65_de).

## Überlegungen zur Installation von Designer {#designer-installation-considerations}

Standardmäßig enthält die Workbench-Installation eine entsprechende englischsprachige Version von Designer. Wenn das Programm zur Installation von Workbench eine vorhandene Version von Designer auf Ihrem Computer erkennt, kann es sein, dass die Installation abbricht und Sie aufgefordert werden, erst Ihre aktuelle Version von Designer zu entfernen, bevor Sie fortfahren können.
Die nachstehende Tabelle enthält eine vollständige Liste der möglichen Installationsszenarien für Designer, auf die Sie stoßen können, sowie alle Aktionen, die Sie bei der Installation von Workbench ausführen müssen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Die aktuell installierte Version von Designer</strong></p> </td>
   <td><p><strong>Erforderliche Aktionen</strong></p> </td>
  </tr>
  <tr>
   <td><p>Acrobat Pro oder Acrobat Pro Extended (enthält Designer)</p> </td>
   <td><p>Ohne.<br /> 
Die Workbench-Installation erkennt auf Ihrem Computer eine Instanz von Designer, die entweder mit Acrobat Pro oder Acrobat Pro Extended installiert wurde.<br />
Verschiedene Versionen von Designer können parallel auf demselben System vorhanden sein – zum Beispiel Designer 6.4.x für Workbench 6.4 und 6.5.0.x für Workbench 6.5. Es ist nicht erforderlich, eine Version von Designer zu deinstallieren, die mit Acrobat 10 Pro, Acrobat 10 Pro Extended oder höher installiert wurde.
<br /></p> </td>
  </tr>
  <tr>
   <td><p>Designer (eigenständig)</p> </td>
   <td><p>Ohne. <br />Die Version von Designer in Workbench ist nur in englischer Sprache verfügbar. <br />Das Workbench-Installationsprogramm installiert keine neue Version von Designer. Stattdessen wird eine aktualisierte Version, die mit dem Workbench-Installationsprogramm geliefert wird, gepatcht. Auf diese Weise können Sie auch Ihre lokalisierte Version von Designer in Workbench verwenden.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Deinstallation von Designer (eigenständig) unter Windows 10 {#uninstall-designer-standalone-windows10}

1. Navigieren Sie zu **Systemsteuerung > Programme > Programme und Funktionen**
1. Wählen Sie unter Aktuell installierte Programm das Programm **Adobe Designer**.
1. Klicken Sie auf **Deinstallieren** und dann auf **Ja**.

## Installieren von Workbench {#installing-workbench}

In diesem Kapitel wird die Installation von Workbench beschrieben.

### Installieren und Ausführen von Workbench {#installing-and-running-workbench}

Stellen Sie vor der Installation von Workbench sicher, dass die Umgebung über die Software und Hardware verfügt, die zum Ausführen von Workbench erforderlich ist (siehe Abschnitt **Vor der Installation**).

**Installation und Ausführung von Workbench:**

1. Führen Sie eine der folgenden Aufgaben aus:
   * Navigieren Sie zum Ordner „\Workbench“ auf dem Installationsdatenträger und doppelklicken Sie auf die Datei „run_windows_installer.bat“.
   * Laden Sie Workbench herunter und entpacken Sie es in Ihrem Dateisystem. Navigieren Sie nach dem Herunterladen zum Ordner „\Workbench“ und doppelklicken Sie auf die Datei „run_windows_installer.bat“.

   >[!IMPORTANT]
   >
   >Das Installationsprogramm von Workbench kann nur von einem lokalen Laufwerk aus ausgeführt werden. Es kann nicht von einer Remote-Site aus ausgeführt werden.

   >[!NOTE]
   >
   >Wenn der Fehler „Virtueller Java™-Computer kann nicht erstellt werden“ auftritt, erstellen Sie eine Umgebungsvariable mit dem Namen „_JAVA_OPTIONS“ und dem Wert „-Xmx512M“ und führen Sie das Installationsprogramm aus.

1. Klicken Sie im Begrüßungsbildschirm auf Weiter.
1. Lesen Sie die Lizenzvereinbarung für das Produkt, wählen Sie Ich akzeptiere die Bedingungen der Lizenzvereinbarung und klicken Sie dann auf Weiter.
1. (Optional) Wählen Sie Adobe Designer installieren, wenn Sie dieses Werkzeug benötigen, um Formulare zu erstellen und zu ändern.

   >[!NOTE]
   >Sie können weiterhin den mit Acrobat 10 installierten Designer verwenden, indem Sie diese Option deaktiviert lassen.

1. Akzeptieren Sie den angegebenen Standardordner oder klicken Sie auf „Auswählen“ und wechseln Sie zu dem Ordner, in dem Sie Workbench installieren möchten. Dann klicken Sie auf „Weiter“.

   >[!NOTE]
   >Der Installationsordnerpfad darf keine #- (Raute-) und $- (Dollar-)Zeichen enthalten.

1. Lesen Sie die Vorinstallationsübersicht und klicken Sie auf Installieren. Das Installationsprogramm zeigt den Fortschritt der Installation an.
1. Überprüfen Sie die Installationsübersicht. Wählen Sie „AEM Forms Workbench starten“, um Workbench zu starten, und klicken Sie dann auf „Weiter“.
1. Lesen Sie die Versionshinweise und klicken Sie auf Fertig.
1. Jetzt sind die folgenden Elemente auf Ihrem Computer installiert:
   * **Workbench**: Um Workbench im Menü „Start“ auszuführen, wählen Sie „Alle Programme“ > „AEM Forms“ > „Workbench“, falls Sie den Verknüpfungsordner dort gespeichert haben. Weitere Informationen finden Sie in der Dokumentation <a href="https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf">Verwenden von Workbench</a>.
   * **Designer**: Sie können von Workbench aus auf Designer zugreifen. Weitere Informationen finden Sie im Thema „Erste Schritte“ in der <a href="https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/using-designer.pdf">Designer-Hilfe</a>.
   * **AEM Forms SDK**: Weitere Informationen zur Verwendung des SDK finden Sie unter <a href="https://helpx.adobe.com/pdf/aem-forms/6-3/programming-with-aem-forms.pdf">Programmieren mit AEM Forms</a>.

## Aktualisieren von Prozessen {#upgrading-processes}

Die Prozesse von AEM Forms auf JEE können mithilfe des Aktualisierungsassistenten zu AEM Forms-Programmen aktualisiert werden. Weitere Informationen finden Sie in der Dokumentation zum Aktualisieren von Legacy-Artefakten in der Workbench-Hilfe.

### Konfigurierung und Anmeldung bei einem Server {#configuring-and-logging-server}

Um Workbench zu verwenden, muss eine Instanz von AEM Forms laufen, normalerweise auf einem separaten Computer. Sie müssen über einen Benutzernamen und ein Passwort verfügen, um sich bei AEM Forms anzumelden, außerdem müssen Ihnen Details über den Speicherort des Servers bekannt sein.

>[!NOTE]
>Wenn Sie AEM Forms für die Verwendung des Repository-Anbieters EMC Documentum® oder IBM® FileNet konfiguriert haben und Sie sich bei einem anderen Repository als dem Repository anmelden möchten, das in Administration-Console von AEM Forms als Standard konfiguriert ist, geben Sie den Benutzernamen in der Form „Benutzername@Repository“ an.

### Konfigurieren von Zeitlimiteinstellungen {#configuring-timeout-settings}

Standardmäßig beträgt das Zeitlimit von Workbench, unabhängig von Aktivität bzw. Inaktivität, zwei Stunden. Informationen zur Bearbeitung der Zeitlimiteinstellung finden Sie unter „Konfigurieren der Benutzerverwaltung“ > „Erweiterte Systemattribute konfigurieren“ in der <a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/configure-user-management/configure-advanced-system-attributes.html?lang=de">Hilfe zur Administration-Console</a>.

### Konfigurieren von Workbench, um eine Verbindung über HTTPS herzustellen {#configuring-workbench-to-connect-over-HTTPS}

Um Workbench über HTTPS mit einem AEM Forms-Server zu verbinden, müssen Sie sicherstellen, dass die Zertifizierungsstelle (CA), die den öffentlichen Schlüssel ausgestellt hat, von Workbench als vertrauenswürdig anerkannt wird. Wenn das Zertifikat nicht als von einer vertrauenswürdigen Quelle stammend erkannt wird, müssen Sie die Datei „cacert“ im Verzeichnis „[Workbench_HOME]/workbench/jre/lib/security“ aktualisieren.

>[!NOTE]
>[Workbench_HOME] ist dabei der Ordner, in dem Sie Workbench installiert haben. Der standardmäßige Speicherort ist C:\Programme (x86)\Adobe Experience Manager Forms Workbench.

Stellen Sie sicher, dass Sie eine Verbindung mit HTTPS herstellen, indem Sie den im Zertifikat angegebenen Namen verwenden. Dieser Name ist normalerweise der vollständig qualifizierte Hostname.

**Zur Aktualisierung der Datei „cacert“**:
1. Stellen Sie sicher, dass Sie über eine Kopie des SSL-Zertifikats (Secure Sockets Layer) verfügen. Wenden Sie sich entweder an die Person, die als Admin den SSL-Server konfiguriert hat, oder exportieren Sie das Zertifikat über einen Webbrowser.

   >[!NOTE]
   >Um das Zertifikat zu exportieren, öffnen Sie einen Webbrowser und melden Sie sich bei der Administration-Console an, installieren Sie dann das Zertifikat im Browser und exportieren Sie das Zertifikat vom Browser in einen temporären Speicherort (oder direkt in den Ordner [Workbench_HOME]/workbench/jre/lib/security).

1. Kopieren Sie das Zertifikat in den Ordner [Workbench_HOME]/workbench/jre/lib/security.

1. Öffnen Sie ein Eingabeaufforderungsfenster, navigieren Sie zu [Workbench_HOME]/workbench/jre/bin und geben Sie folgenden Befehl ein:
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
Dabei gilt:
   * `changeit` ist das Standardpasswort zum Keystore „cacerts“.
   * „certname“ ist das Zertifikat, das Sie in Schritt 1 ausgewählt haben.
   * „example“ ist der Aliasname, den Sie für das Zertifikat auswählen. Dieser Wert kann geändert werden.

1. Wenn Sie dazu aufgefordert werden, das Zertifikat als vertrauenswürdig festzulegen, geben Sie „Ja“ ein und drücken Sie danach die Eingabetaste. Das Keytool importiert dann die Datei „cacerts“ in das Verzeichnis [Workbench_HOME]/workbench/jre/lib/security.

1. Schließen Sie Workbench und starten Sie es neu, um Änderungen anzuwenden.

### Konfiguration von Cache-Einstellungen für dynamisch erstellte Vorlagen {#configuring-cache-settings-for-dynamically-generated-templates}

Die folgenden Aspekte des Cache-Vorgangs sollten berücksichtigt werden, wenn Ihre Anwendung einzigartige Vorlagen spontan generiert, indem XFA-Inhalte automatisch aktualisiert werden. In der Tat verwendet jede Transaktion eine neue, eindeutige Vorlage.

Wenn der Formulargenerator oder die Ausgabe nach Einträgen im Cache für eine bestimmte Formularvorlage sucht oder diese aktualisiert, werden mehrere Schlüsselwerte verwendet, um den spezifischen Cache-Eintrag zu finden, auf den zugegriffen werden soll.

* **Name der Vorlagendatei**: Der Speicherort und der Dateiname der Vorlage, die als primäre eindeutige Kennung des zwischengespeicherten Formulars verwendet wird.
* **Zeitstempel**: Die Vorlagendatei enthält einen Zeitstempel, mit dem die letzte Aktualisierungszeit des Formulars ermittelt wird.
* **Vorlagen-UUID**: Designer fügt in jede Vorlage eine eindeutige Kennung (UUID) für das Formular und dessen Version ein. Jedes Mal, wenn das Formular aktualisiert wird, wird die eingebettete UUID ebenfalls aktualisiert. Eine XDP-Vorlage kann beispielsweise den folgenden Inhalt enthalten:

   `<?xml version="1.0" encoding="UTF-8"?>`
   `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=https://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="https://www.xfa.org/schema/xfa-template/2.6/">`

* **Render-Optionen**: Im Cache des wiedergegebenen Formulars werden die Cache-Inhalte für jeden Satz eindeutiger Render-Optionen separat gespeichert.


Der Forms-Dienst empfängt Vorlagen anhand des Dateinamens oder des Repository-Speicherorts oder anhand des Wertes als XML-Objekt im Speicher.
* **Nach Referenz übergebene Vorlagen**: Verwendet den Inhaltsstamm und den Formularnamen. Wenn bei jeder Anfrage mit dieser Methode eindeutige Vorlagen mit unterschiedlichen Dateinamen übergeben werden, wächst der Datenträger-Cache endlos und wird nie wiederverwendet. Um dies zu verhindern, sollten eindeutige Vorlagen mit demselben Dateinamen übergeben werden, um sicherzustellen, dass derselbe Cache für alle Anfragen aktualisiert wird.
* **Nach Wert übergebene Vorlagen**: Verwendet Vorlagen-Bytes, die zusammen mit den Daten mit dem Parameter „theinDataDoc“ übergeben werden. Wenn eindeutige Vorlagen mit unterschiedlicher UID mithilfe dieser Methode übergeben werden, wächst der Datenträger-Cache endlos und wird nie wiederverwendet. Um dies zu verhindern, sollte das UUID-Attribut aus allen Vorlagen entfernt werden, um sicherzustellen, dass kein Cache für die Vorlage erstellt wird. Alternativ dazu können die Cache-Objekte erstellt werden, wenn dieselbe UUID ungleich „null“ übergeben wird. Es wird jedoch sichergestellt, dass bei jeder Anfrage derselbe Cache aktualisiert wird.

Um zu verhindern, dass der Cache endlos anwächst, sollten Sie die folgenden Faktoren für das Rendern von dynamisch generierten Vorlagen mithilfe der neuen AEM Forms-APIs, nämlich „renderHTMLForm2“ und „renderPDFForm2“ berücksichtigen.

Wenn Sie neue APIs verwenden, wird die Vorlage als ein Dokumentobjekt übergeben, das im Forms-Dienst bearbeitet wird, je nachdem, ob es passiviert ist oder nicht.

Beachten Sie bei passivierten Dokumenten, bei denen die UUID und der Inhaltsstamm als Cache-Schlüssel dienen, die folgenden Aspekte:
* Der Cache wird nicht für passivierte Eingabevorlagen ohne UUID erstellt.
* Wenn mehr als eine passivierte Eingabevorlage mit derselben UUID und demselben Inhaltsstamm übergeben wird, wird derselbe Cache überschrieben.

Bei nicht passivierten Dokumenten, bei denen der Dateiname und der Stamm des Inhalts als Cache-Schlüssel dienen, sollten Sie den folgenden Aspekt berücksichtigen:
* Bei nicht-passivierten Eingabevorlagen hängt das Zwischenspeichern vom Inhaltsstamm und vom Dateinamen ab, von wo aus das Dokument erstellt wurde.
Derselbe Cache wird nur für Anfragen mit demselben Inhaltsstamm und demselben Dateinamen der Vorlage verwendet.
Die folgenden Best Practices stellen sicher, dass der Cache nicht endlos wächst, wenn dynamisch generierte Vorlagen an den Forms-Dienst übergeben werden:
   * Entfernen Sie die UUID oder übergeben Sie dieselbe UUID in allen dynamisch generierten Vorlagen.
   * Generieren Sie das Dokument entweder aus Vorlagen-Bytes oder aus demselben Dateinamen auf der Festplatte.

### Deinstallieren von Workbench {#uninstalling-workbench}

Verwenden Sie die Funktion „Software“ in der Systemsteuerung, um das Deinstallationsprogramm zu starten. Die Workbench- und Designer-Anwendungen haben unterschiedliche Deinstallationsprogramme.

## Konfigurieren von AEM Forms XDC Editor {#configuring-aem-forms-xdc-editor}

Mithilfe des XDC-Editors können Admins von Netzwerkdruckern XML Forms Architecture-Gerätekonfiguration (XDC)-Dateien erstellen und ändern. XDC-Dateien beschreiben die Funktionen von Druckern, wie die Druckersprache oder die Korrelation zwischen Papiergröße und Position der Fächer.

Bevor der Administrator des Netzwerkdruckers den XDC-Editor verwendet, verschieben Sie die XDC-Beispiel-Dateien und lesen Sie die Datei Geräteprofile mit XDC-Editor erstellen.

**Abrufen der Beispiel-XDC-Dateien**:
1. Suchen Sie auf dem AEM Forms-Server den XDC-Ordner in [AEM Forms-Stammverzeichnis]\sdk\samples\Output\IVS.
1. Kopieren Sie den Inhalt dieses Ordners in ein Verzeichnis, auf das vom Workbench- oder Eclipse-System aus zugegriffen werden kann.

**Abrufen der XDC Editor-Hilfe**:
1. Gehen Sie zur Dokumentations-Website von AEM Forms.
1. Klicken Sie auf die Schaltfläche **Entwickeln** und navigieren Sie zu Erstellen von Geräteprofilen mit XDC Editor. Laden Sie die Datei xdc_editor_help_web.zip herunter und installieren Sie die Hilfedateien, indem Sie die Anweisungen befolgen, die in der Readme-Datei angeführt sind.
