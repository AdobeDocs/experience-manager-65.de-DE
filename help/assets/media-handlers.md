---
title: Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows
description: Erfahren Sie mehr über die Medien-Handler und wie Sie mithilfe von Workflows Aufgaben an Ihren digitalen Assets durchführen können.
mini-toc-levels: 1
contentOwner: AG
role: User
feature: Workflow,Renditions
exl-id: cfd6c981-1a35-4327-82d7-cf373d842cc3
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2136'
ht-degree: 86%

---

# Verarbeiten von Assets mithilfe von Medien-Handlern und Workflows {#processing-assets-using-media-handlers-and-workflows}

[!DNL Adobe Experience Manager Assets] enthält einen Satz von standardmäßigen Workflows und Medien-Handlern zur Bearbeitung von Assets. Ein Workflow definiert die Aufgaben, die für die Assets ausgeführt werden sollen, und delegiert dann die spezifischen Aufgaben an die Medien-Handler, z. B. die Erstellung von Miniaturbildern oder die Metadatenextraktion.

Ein Workflow kann so konfiguriert werden, dass er automatisch ausgeführt wird, wenn ein Asset eines bestimmten MIME-Typs hochgeladen wird. Die Prozessschritte sind in Form einer Reihe von [!DNL Assets]-Medien-Handlern definiert. [!DNL Experience Manager] bietet einige [integrierte Handler](#default-media-handlers) und zusätzliche Handler können entweder [speziell entwickelt](#creating-a-new-media-handler) oder definiert werden, indem der Prozess an ein [Befehlszeilen-Tool](#command-line-based-media-handler) delegiert wird.

Medien-Handler sind Dienste innerhalb von [!DNL Assets], die spezielle Aktionen an Assets durchführen. Wenn beispielsweise eine MP3-Audiodatei in [!DNL Experience Manager] hochgeladen wird, löst ein Workflow einen MP3-Handler aus, der die Metadaten extrahiert und ein Miniaturbild erstellt. Medien-Handler werden normalerweise in Verbindung mit Workflows verwendet. Die meisten gängigen MIME-Typen werden in [!DNL Experience Manager] unterstützt. Spezielle Aufgaben können an Assets durchgeführt werden, indem Workflows erweitert bzw. erstellt, Medien-Handler erweitert bzw. erstellt oder Medien-Handler deaktiviert bzw. aktiviert werden.

>[!NOTE]
>
>Siehe [Von Assets unterstützte Formate](assets-formats.md) Seite mit einer Beschreibung aller Formate, die von [!DNL Assets] und für jedes Format unterstützte Funktionen.

## Standard-Medien-Handler {#default-media-handlers}

Die folgenden Medien-Handler sind in [!DNL Assets] verfügbar und verarbeiten die gängigsten MIME-Typen:

<!-- TBD: Java versions should not be set to 1.5. Must be updated.
-->

| Handler-Name | Dienstname (in der Systemkonsole) | Unterstützte MIME-Typen |
|--------------|--------------------------------------|----------------------|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>application/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | audio/mpeg<br><b>Wichtig</b> - Wenn Sie eine MP3-Datei hochladen, ist es [mit einer Bibliothek eines Drittanbieters verarbeitet werden](https://www.zxdr.it/programmi/SistEvolBDD/LibJava/doc/de/vdheide/mp3/MP3File.html). Die Bibliothek berechnet grob eine ungefähre Länge, wenn die MP3-Datei eine variable Bitrate (VBR) aufweist verfügt. |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | image/pict |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>application/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | application/epub+zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | Ausweichmöglichkeit, falls kein anderer Handler gefunden wurde, der Daten aus einem Asset extrahiert |

{style="table-layout:auto"}

Alle Handler führen die folgenden Aufgaben aus:

* Extrahieren aller verfügbaren Metadaten aus dem Asset.
* Erstellung eines Miniaturbilds aus einem Asset.

So zeigen Sie die aktiven Medien-Handler an:

1. Navigieren Sie im Browser zu `https://localhost:4502/system/console/components`.
1. Klicken Sie auf `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Eine Liste mit allen aktiven Medien-Handlern wird angezeigt. Beispiel:

![chlimage_1-437](assets/chlimage_1-437.png)

## Verwenden von Medien-Handler in Workflows, um Aufgaben zur Bearbeitung von Assets durchzuführen {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Medien-Handler sind Dienste, die normalerweise in Verbindung mit Workflows verwendet werden.

[!DNL Experience Manager] bietet verschiedene Standard-Workflows zur Bearbeitung von Assets. Um sie anzuzeigen, öffnen Sie die Workflow-Konsole und klicken Sie auf die Registerkarte **[!UICONTROL Modelle]**: Die Workflow-Namen, die mit beginnen, sind Asset-spezifische Workflows.[!DNL Assets]

Bereits bestehende Workflows können erweitert und neue Workflows können erstellt werden, um Assets nach spezifischen Anforderungen zu bearbeiten.

Das folgende Beispiel zeigt, wie der **[!UICONTROL AEM Assets-Synchronisierungs-Workflow]** erweitert werden kann, damit Teil-Assets für alle Assets außer PDF-Dokumente erstellt werden.

### Deaktivieren oder Aktivieren von Medien-Handlern {#disabling-enabling-a-media-handler}

Die Medien-Handler können über die Apache Felix Web Management-Konsole deaktiviert bzw. aktiviert werden. Wenn der Medien-Handler deaktiviert ist, werden seine Aufgaben nicht für die Assets ausgeführt.

So aktivieren/deaktivieren Sie einen Medien-Handler:

1. Navigieren Sie im Browser zu `https://<host>:<port>/system/console/components`.
1. Klicken Sie neben dem Namen des Medien-Handlers auf **[!UICONTROL Deaktivieren]**. Beispiel: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Aktualisieren Sie die Seite: Neben dem Medien-Handler wird ein Symbol angezeigt, das angibt, dass er deaktiviert ist.
1. Um den Medien-Handler zu aktivieren, klicken Sie neben dem Namen des Medien-Handlers auf **[!UICONTROL Aktivieren]**.

### Erstellen eines Medien-Handlers {#creating-a-new-media-handler}

Um einen neuen Medientyp zu unterstützen oder bestimmte Aufgaben für ein Asset auszuführen, müssen Sie einen Medien-Handler erstellen. In diesem Abschnitt wird beschrieben, wie Sie fortfahren.

#### Wichtige Klassen und Schnittstellen {#important-classes-and-interfaces}

Am besten ist es, zu Beginn einer Implementierung den Inhalt einer bereitgestellten abstrakten Implementierung zu übernehmen, wodurch die meisten Dinge im Voraus erledigt werden und ein angemessenes Standardverhalten erreicht wird: die `com.day.cq.dam.core.AbstractAssetHandler`-Klasse.

Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. Wenn Sie also den Inhalt dieser Klasse übernehmen und das maven-sling-Plug-in verwenden, müssen Sie die Übernahmemarkierung auf `true` setzen.

Implementieren Sie die folgenden Methoden:

* `extractMetadata()`: extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: erstellt ein Miniaturbild aus einem Asset.
* `getMimeTypes()`: gibt die Asset-MIME-Typen zurück.

Hier eine Beispielvorlage:

```Java
package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts }
```

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler`-Schnittstelle: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte MIME-Typen hinzufügt. Wenn ein neuer MIME-Typ hinzugefügt werden soll, muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler`-Klasse: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-Klasse:
   * Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet allgemeine Funktionen sowie häufig verwendete Funktionen für die Extrahierung von Unter-Assets.
   * Am besten ist es, zu Beginn einer Implementierung den Inhalt einer bereitgestellten abstrakten Implementierung zu übernehmen, wodurch die meisten Dinge im Voraus erledigt werden und ein angemessenes Standardverhalten erreicht wird: die com.day.cq.dam.core.AbstractAssetHandler-Klasse.
   * Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. Wenn Sie also von dieser Klasse erben und das maven-sling-Plug-in verwenden, stellen Sie sicher, dass Sie das Vererbung-Flag auf &quot;true&quot;setzen.

Die folgenden Methoden müssen implementiert werden:

* `extractMetadata()`: Diese Methode extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: Diese Methode erstellt ein Miniaturbild aus dem übergebenen Asset.
* `getMimeTypes()`: Diese Methode gibt den/die Asset-MIME-Typ(en) zurück.

Hier eine Beispielvorlage:

package my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot; &amp;ast; @scr.service &amp;ast;/ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // die relevanten Teile implementieren }

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler`-Schnittstelle: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte MIME-Typen hinzufügt. Wenn ein neuer MIME-Typ hinzugefügt werden soll, muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler`-Klasse: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler`-Klasse: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie übliche Funktionen für die Extrahierung von Teil-Assets.

#### Beispiel: Erstellung eines spezifischen Text-Handlers {#example-create-a-specific-text-handler}

In diesem Abschnitt erstellen Sie einen bestimmten Text-Handler, der Miniaturansichten mit einem Wasserzeichen generiert.

Gehen Sie wie folgt vor:

Unter [Entwicklungs-Tools](../sites-developing/dev-tools.md) finden Sie Informationen zur Installation und Einrichtung von Eclipse mit einem [!DNL Maven]-Plug-in und zum Einrichten der Abhängigkeiten, die für das [!DNL Maven]-Projekt erforderlich sind.

Wenn Sie nach der Durchführung des folgenden Verfahrens eine Textdatei in [!DNL Experience Manager] hochladen, werden die Metadaten der Datei extrahiert und zwei Miniaturbilder mit einem Wasserzeichen erstellt.

1. Erstellen Sie in Eclipse das [!DNL Maven]-Projekt `myBundle`:

   1. Klicken Sie in der Menüleiste auf **[!UICONTROL Datei]** > **[!UICONTROL Neu]** > **[!UICONTROL Andere]**.
   1. Erweitern Sie im Dialogfeld den [!DNL Maven]-Ordner, wählen Sie das [!DNL Maven]-Project aus und klicken Sie auf **[!UICONTROL Weiter]**.
   1. Aktivieren Sie das Kontrollkästchen „Einfaches Projekt erstellen“ sowie das Kontrollkästchen „Standard-Workspace-Speicherorte verwenden“ und klicken Sie dann auf **[!UICONTROL Weiter]**.
   1. Definieren Sie eine [!DNL Maven]-Projekt:

      * Gruppen-ID: `com.day.cq5.myhandler`.
      * Artefakt-ID: myBundle.
      * Name: Mein [!DNL Experience Manager]-Bundle.
      * Beschreibung: Das ist mein [!DNL Experience Manager]-Bundle.

   1. Klicken Sie auf **[!UICONTROL Beenden]**.

1. Setzen Sie den [!DNL Java]-Compiler auf Version 1.5:

   1. Klicken Sie mit der rechten Maustaste auf das `myBundle`-Projekt und wählen Sie [!UICONTROL Eigenschaften] aus.
   1. Wählen Sie [!UICONTROL Java Compiler] aus und setzen Sie folgende Eigenschaften auf 1.5:

      * Compiler-Compliance-Level
      * Kompatibilität der generierten .class-Dateien
      * Quellkompatibilität

   1. Klicken Sie auf **[!UICONTROL OK]**. Klicken Sie im Dialogfenster auf **[!UICONTROL Ja]**.

1. Ersetzen Sie den Code in der `pom.xml`-Datei durch folgenden Code:

   ```xml
   <project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <!-- ====================================================================== -->
    <!-- P A R E N T P R O J E C T D E S C R I P T I O N -->
    <!-- ====================================================================== -->
    <parent>
     <groupId>com.day.cq.dam</groupId>
     <artifactId>dam</artifactId>
     <version>5.2.14</version>
     <relativePath>../parent</relativePath>
    </parent>
    <!-- ====================================================================== -->
    <!-- P R O J E C T D E S C R I P T I O N -->
    <!-- ====================================================================== -->
    <groupId>com.day.cq5.myhandler</groupId>
    <artifactId>myBundle</artifactId>
    <name>My CQ5 bundle</name>
    <version>0.0.1-SNAPSHOT</version>
    <description>This is my CQ5 bundle</description>
    <packaging>bundle</packaging>
    <!-- ====================================================================== -->
    <!-- B U I L D D E F I N I T I O N -->
    <!-- ====================================================================== -->
    <build>
     <plugins>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-scr-plugin</artifactId>
      </plugin>
      <plugin>
       <groupId>org.apache.sling</groupId>
       <artifactId>maven-sling-plugin</artifactId>
       <configuration>
        <slingUrlSuffix>/libs/dam/install/</slingUrlSuffix>
       </configuration>
      </plugin>
      <plugin>
       <groupId>org.apache.felix</groupId>
       <artifactId>maven-bundle-plugin</artifactId>
       <extensions>true</extensions>
       <configuration>
        <instructions>
         <Bundle-Category>cq5</Bundle-Category>
         <Export-Package> com.day.cq5.myhandler </Export-Package>
        </instructions>
       </configuration>
      </plugin>
     </plugins>
    </build>
    <!-- ====================================================================== -->
    <!-- D E P E N D E N C I E S -->
    <!-- ====================================================================== -->
    <dependencies>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-api</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq.dam</groupId>
      <artifactId>cq-dam-core</artifactId>
      <version>5.2.10</version>
      <scope>provided</scope>
     </dependency>
     <dependency>
      <groupId>com.day.cq</groupId>
      <artifactId>cq-commons</artifactId>
     </dependency>
     <dependency>
      <groupId>javax.jcr</groupId>
      <artifactId>jcr</artifactId>
     </dependency>
     <dependency>
      <groupId>org.apache.felix</groupId>
      <artifactId>org.osgi.compendium</artifactId>
     </dependency>
     <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-lang</groupId>
      <artifactId>commons-lang</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-collections</groupId>
      <artifactId>commons-collections</artifactId>
     </dependency>
     <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-gfx</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.commons</groupId>
      <artifactId>day-commons-text</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.workflow</groupId>
      <artifactId>cq-workflow-api</artifactId>
     </dependency>
     <dependency>
      <groupId>com.day.cq.wcm</groupId>
      <artifactId>cq-wcm-foundation</artifactId>
      <version>5.2.22</version>
     </dependency>
    </dependencies>
   ```

1. Erstellen Sie das Paket `com.day.cq5.myhandler`, das die [!DNL Java]-Klassen unter `myBundle/src/main/java` enthält:

   1. Klicken Sie unter „myBundle“ mit der rechten Maustaste auf `src/main/java`, wählen Sie „Neu“ und dann „Paket“ aus.
   1. Benennen Sie es `com.day.cq5.myhandler` und klicken Sie auf „Fertigstellen“.

1. Erstellen Sie die [!DNL Java]-Klasse `MyHandler`:

   1. Klicken Sie in [!DNL Eclipse] unter `myBundle/src/main/java` mit der rechten Maustaste auf das Paket `com.day.cq5.myhandler`. Wählen Sie [!UICONTROL Neu] und dann [!UICONTROL Klasse] aus.
   1. Benennen Sie im Dialogfenster die [!DNL Java]-Klasse `MyHandler` und klicken Sie auf [!UICONTROL Fertigstellen]. [!DNL Eclipse] erstellt und öffnet die Datei `MyHandler.java`.
   1. Ersetzen Sie in `MyHandler.java` den vorhandenen Code durch Folgendes und speichern Sie dann die Änderungen:

   ```java
   package com.day.cq5.myhandler;
   import java.awt.Color;
   import java.awt.Rectangle;
   import java.awt.image.BufferedImage;
   import java.io.IOException;
   import java.io.InputStream;
   import java.io.InputStreamReader;
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   import org.apache.commons.io.IOUtils;
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   import com.day.cq.dam.api.metadata.ExtractedMetadata;
   import com.day.cq.dam.core.AbstractAssetHandler;
   import com.day.image.Font;
   import com.day.image.Layer;
   import com.day.cq.wcm.foundation.ImageHelper;
   
   /**
    * The <code>MyHandler</code> can extract text files
    * @scr.component inherit="true" immediate="true" metatype="false"
    * @scr.service
    *
    **/
   
   public class MyHandler extends AbstractAssetHandler {
    /** * Logger instance for this class. */
    private static final Logger log = LoggerFactory.getLogger(MyHandler.class);
    /** * Music icon margin */
    private static final int MARGIN = 10;
    /** * @see com.day.cq.dam.api.handler.AssetHandler#getMimeTypes() */
    public String[] getMimeTypes() {
     return new String[] {"text/plain"};
    }
   
    public ExtractedMetadata extractMetadata(Node asset) {
     ExtractedMetadata extractedMetadata = new ExtractedMetadata();
     InputStream data = getInputStream(asset);
     try {
      // read text data
      InputStreamReader reader = new InputStreamReader(data);
      char[] buffer = new char[4096];
      String text = "";
      while (reader.read(buffer) != -1) {
       text += new String(buffer);
      }
      reader.close();
      long wordCount = this.wordCount(text);
      extractedMetadata.setProperty("text", text);
      extractedMetadata.setMetaDataProperty("Word Count",wordCount);
      setMimetype(extractedMetadata, asset);
     } catch (Throwable t) {
      log.error("handling error: " + t.toString(), t);
     } finally {
      IOUtils.closeQuietly(data);
     }
     return extractedMetadata; }
    // ----------------------< helpers >----------------------------------------
    protected BufferedImage getThumbnailImage(Node node) {
     ExtractedMetadata metadata = extractMetadata(node);
     final String text = (String) metadata.getProperty("text");
     // create text layer
     final Layer layer = new Layer(500, 600, Color.WHITE);
     layer.setPaint(Color.black);
     Font font = new Font("Arial", 12);
     String displayText = this.getDisplayText(text, 600, 12);
     if(displayText!=null && displayText.length() > 0) {
      // commons-gfx Font class would throw IllegalArgumentException on empty or null text
      layer.drawText(10, 10, 500, 600, displayText, font, Font.ALIGN_LEFT, 0, 0);
     }
     // create watermark and merge with text layer
     Layer watermarkLayer;
     try {
      final Session session = node.getSession();
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/we-retail/en/products/apparel/gloves/Gloves.jpg");
      watermarkLayer.setX(MARGIN);
      watermarkLayer.setY(MARGIN);
      layer.merge(watermarkLayer);
     } catch (RepositoryException e) {
      // TODO Auto-generated catch block
      e.printStackTrace();
     } catch (IOException e) {
      // TODO Auto-generated catch block
      e.printStackTrace(); }
     layer.crop(new Rectangle(510, 600));
     return layer.getImage(); }
    // ---------------< private >-----------------------------------------------
    /**
     * This method cuts lines if the text file is too long..
     * * @param text
     * * text to check
     * * @param height
     * * text box height (px)
     * * @param fontheight
     * * font height (px)
     * * @return the text which will fit into the box
     */
    private String getDisplayText(String text, int height, int fontheight) {
     String trimmedText = text.trim();
     int numOfLines = height / fontheight;
     String lines[] = trimmedText.split("\n");
     if (lines.length <= numOfLines) {
      return trimmedText;
     } else {
      String cuttetText = "";
      for (int i = 0; i < numOfLines; i++) {
       cuttetText += lines[i] + "\n";
      }
      return cuttetText;
     }
    }
    /**
     * * This method counts the number of words in a string
     * * @param text the String whose words would like to be counted
     * * @return the number of words in the string
     * */
    private long wordCount(String text) {
     // We need to keep track of the last character, if we have two whitespaces in a row we do not want to double count.
     // The starting of the document is always a whitespace.
     boolean prevWhiteSpace = true;
     boolean currentWhiteSpace = true;
     char c; long numwords = 0;
     int j = text.length();
     int i = 0;
     while (i < j) {
      c = text.charAt(i++);
      if (c == 0) { break; }
      currentWhiteSpace = Character.isWhitespace(c);
      if (currentWhiteSpace && !prevWhiteSpace) { numwords++; }
      prevWhiteSpace = currentWhiteSpace;
     }
     // If we do not end with a whitespace then we need to add one extra word.
     if (!currentWhiteSpace) { numwords++; }
     return numwords;
    }
   }
   ```

1. Kompilieren Sie die [!DNL Java]-Klasse und erstellen Sie das Bundle:

   1. Klicken Sie mit der rechten Maustaste auf das `myBundle`-Projekt, wählen Sie **[!UICONTROL Ausführen als]** und dann **[!UICONTROL Maven Install]** aus.
   1. Das Bundle `myBundle-0.0.1-SNAPSHOT.jar` (das die kompilierte Klasse enthält) wird unter `myBundle/target` erstellt.

1. Erstellen Sie im CRX-Explorer einen Knoten unter `/apps/myApp`. Name = `install`, Typ = `nt:folder`.
1. Kopieren Sie das Bundle `myBundle-0.0.1-SNAPSHOT.jar` und speichern Sie es unter `/apps/myApp/install` (z. B. mit WebDAV). Der neue Text-Handler ist jetzt in [!DNL Experience Manager] aktiv.
1. Öffnen Sie im Browser die [!UICONTROL Apache Felix Web Management Console]. Wählen Sie die Registerkarte [!UICONTROL Komponenten] aus und deaktivieren Sie den Standard-Text-Handler `com.day.cq.dam.core.impl.handler.TextHandler`.

## Befehlszeilenbasierter Medien-Handler {#command-line-based-media-handler}

Mit [!DNL Experience Manager] können Sie ein beliebiges Befehlszeilen-Tool (z. B. ) innerhalb eines Workflows ausführen, um Assets zu konvertieren und dem Asset das neue Ausgabeformat hinzuzufügen. [!DNL ImageMagick] Sie müssen lediglich das Befehlszeilen-Tool auf dem Datenträger installieren, der den [!DNL Experience Manager]-Server hostet, und dem Workflow einen Prozessschritt hinzufügen. Der aufgerufene Prozess `CommandLineProcess` ermöglicht zudem die Filterung nach spezifischen MIME-Typen und die Erstellung mehrerer Miniaturbilder auf der Grundlage des neuen Ausgabeformats.

Die folgenden Konvertierungen können automatisch ausgeführt und in [!DNL Assets] gespeichert werden:

* EPS- und AI-Umwandlung mithilfe von [ImageMagick](https://www.imagemagick.org/script/index.php) und [Ghostscript](https://www.ghostscript.com/).
* FLV-Videotranskodierung mithilfe von [FFmpeg](https://ffmpeg.org/).
* MP3-Kodierung mithilfe von [LAME](https://lame.sourceforge.io/).
* Verarbeitung von Audiodaten mithilfe von [SOX](https://sox.sourceforge.io/).

>[!NOTE]
>
>Auf Nicht-Windows-Systemen gibt das FFMpeg-Tool einen Fehler aus, wenn Ausgabedarstellungen für ein Video-Asset erstellt werden, dessen Dateiname ein einfaches Anführungszeichen (&#39;) enthält. Wenn der Name Ihrer Videodatei ein einfaches Anführungszeichen enthält, entfernen Sie es, bevor Sie das Asset auf [!DNL Experience Manager] hochladen. 

Der Prozess `CommandLineProcess` führt folgende Vorgänge in der angegebenen Reihenfolge aus:

* Filtert die Datei nach bestimmten MIME-Typen, falls angegeben.
* Erstellt ein temporäres Verzeichnis auf dem Datenträger, der den [!DNL Experience Manager]-Server hostet.
* Streamt die Originaldatei in das temporäre Verzeichnis.
* Führt den Befehl aus, der über die Argumente des Schritts definiert ist. Der Befehl wird innerhalb des temporären Verzeichnisses ausgeführt, nachdem die Genehmigung der Benutzerinnen oder Benutzer eingeholt wurde, die [!DNL Experience Manager] ausführen.
* Streamt das Ergebnis zurück in den Ausgabeordner des [!DNL Experience Manager]-Servers.
* Löscht das temporäre Verzeichnis.
* Erstellt Miniaturansichten basierend auf diesen Ausgabeformaten, falls angegeben. Die Anzahl und die Abmessungen der Miniaturansichten werden durch die Argumente des Schritts definiert.

### Ein Beispiel mit [!DNL ImageMagick] {#an-example-using-imagemagick}

Das folgende Beispiel zeigt, wie Sie den Befehlszeilen-Prozessschritt so einrichten, dass jedes Mal, wenn ein Asset mit dem MIME-Typ GIF oder TIFF zu `/content/dam` auf dem [!DNL Experience Manager]-Server hinzugefügt wird, ein gespiegeltes Bild des Originals zusammen mit drei zusätzlichen Miniaturbildern (140x100, 48x48 und 10x250) erstellt wird.

Verwenden Sie dafür [!DNL ImageMagick]. [!DNL ImageMagick] ist eine kostenlose Befehlszeilen-Software zum Erstellen, Bearbeiten und Zusammensetzen von Bitmap-Bildern.

Installieren Sie [!DNL ImageMagick] auf der Festplatte, auf der der [!DNL Experience Manager]-Server gehostet wird:

1. Installieren Sie [!DNL ImageMagick]: Siehe [ImageMagick-Dokumentation](https://www.imagemagick.org/script/download.php).
1. Richten Sie das Tool ein, damit Sie den Befehl „convert“ über die Befehlszeile ausführen können.
1. Um festzustellen, ob das Tool ordnungsgemäß installiert wurde, führen Sie den Befehl `convert -h` über die Befehlszeile aus.

   Es wird ein Hilfebildschirm mit allen möglichen Optionen des Konvertierungs-Tools angezeigt.

   >[!NOTE]
   >
   >In manchen Versionen von Windows kann der Konvertierungsbefehl eventuell nicht ausgeführt werden, da er in Konflikt mit dem nativen Konvertierungsdienstprogramm steht, das Teil der [!DNL Windows]-Installation ist. In diesem Fall verwenden Sie den vollständigen Pfad für die [!DNL ImageMagick]-Software, die verwendet wird, um Bilddateien in Miniaturbilder zu konvertieren. Beispiel: `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Um zu überprüfen, ob das Tool ordnungsgemäß ausgeführt wird, fügen Sie ein JPG-Bild in das Arbeitsverzeichnis ein und führen Sie dann den Befehl „convert `<image-name>.jpg -flip <image-name>-flipped.jpg`“ von der Befehlszeile aus. Ein gespiegeltes Bild wird dem Verzeichnis hinzugefügt. Fügen Sie dann den Befehlszeilenprozessschritt dem Workflow **[!UICONTROL DAM-Update-Asset]** hinzu.
1. Rufen Sie die Konsole **[!UICONTROL Workflow]** auf.
1. Bearbeiten Sie auf der Registerkarte **[!UICONTROL Modelle]** das Modell **[!UICONTROL DAM-Update-Asset]**.
1. Ändern Sie die [!UICONTROL Argumente] des Schritts **[!UICONTROL Web-fähige Ausgabe]** in: `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`.
1. Speichern Sie den Workflow.

Fügen Sie zum Testen des geänderten Workflows ein Asset zu `/content/dam` hinzu.

1. Rufen Sie im Dateisystem ein TIFF-Bild Ihrer Wahl ab. Umbenennen in `myImage.tiff` und kopieren Sie es in `/content/dam`, beispielsweise durch Verwendung von WebDAV.
1. Navigieren Sie zu **[!UICONTROL CQ5 DAM]** -Konsole, beispielsweise `https://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Öffnen Sie das Asset **[!UICONTROL myImage.tiff]** und prüfen Sie, ob das gespiegelte Bilder und die drei Miniaturbilder erstellt wurden.

#### Konfiguration des Prozessschritts CommandLineProcess {#configuring-the-commandlineprocess-process-step}

In diesem Abschnitt wird beschrieben, wie die [!UICONTROL Prozess-Argumente] des [!UICONTROL CommandLineProcess] festgelegt werden.

Trennen Sie die Werte der [!UICONTROL Prozessargumente] mithilfe von Kommas und beginnen Sie sie nicht mit einem Leerzeichen.

| Argument-Format | Beschreibung |
|---|---|
| mime:&lt;MIME-Typ> | Optionales Argument. Der Prozess wird angewendet, wenn das Asset denselben MIME-Typ wie das Argument hat. <br>Es können mehrere MIME-Typen definiert werden. |
| tn:&lt;Breite>:&lt;Höhe> | Optionales Argument. Der Prozess erstellt ein Miniaturbild mit den Abmessungen, die im Argument definiert sind. <br>Es können mehrere Miniaturbilder definiert werden. |
| cmd: &lt;Befehl> | Definiert den ausgeführten Befehl. Die Syntax hängt vom Befehlszeilen-Tool ab. Nur ein Befehl kann definiert werden. <br>Die folgenden Variablen können zum Erstellen des Befehls verwendet werden:<br>`${filename}`: Name der Eingabedatei, beispielsweise original.jpg <br> `${file}`: vollständiger Pfadname der Eingabedatei, beispielsweise `/tmp/cqdam0816.tmp/original.jpg` <br> `${directory}`: Verzeichnis der Eingabedatei, beispielsweise `/tmp/cqdam0816.tmp` <br>`${basename}`: Name der Eingabedatei ohne Erweiterung, beispielsweise original <br>`${extension}`: Erweiterung der Eingabedatei, z. B. JPG. |

Wenn beispielsweise [!DNL ImageMagick] auf dem Datenträger installiert ist, der den [!DNL Experience Manager]-Server hostet, und Sie einen Prozessschritt mithilfe von [!UICONTROL CommandLineProcess] als Implementierung erstellen und die folgenden Werte als [!UICONTROL Prozessargumente] verwenden:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

Dann gilt der Schritt bei der Ausführung des Workflows nur für Assets, die `image/gif` oder `mime:image/tiff` als `mime-types` haben. Der Schritt erstellt ein gespiegeltes Bild des Originals, wandelt es in eine JPG-Datei um und erstellt drei Miniaturbilder mit den Abmessungen 140x100, 48x48 und 10x250.

Verwenden Sie die folgenden [!UICONTROL Prozessargumente], um die drei Standard-Miniaturbilder mithilfe von [!DNL ImageMagick] zu erstellen:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Verwenden Sie die folgenden [!UICONTROL Prozessargumente], um die Web-fähige Ausgabe mithilfe von [!DNL ImageMagick] zu erstellen:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>Der Schritt [!UICONTROL CommandLineProcess] gilt nur für Assets (Knoten des Typs `dam:Asset`) oder untergeordnete Elemente eines Assets.

>[!MORELIKETHIS]
>
>* [Verarbeiten von Assets](assets-workflow.md)
