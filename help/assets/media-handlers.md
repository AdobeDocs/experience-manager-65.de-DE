---
title: Verarbeiten von Assets mit Media Handlern und Workflows
description: Erfahren Sie mehr über die Media-Handler und wie Sie mit Workflows Aufgaben für Ihre digitalen Assets durchführen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Processe assets using media handlers and workflows {#processing-assets-using-media-handlers-and-workflows}

Adobe Experience Manager (AEM) Assets verfügen über eine Reihe von Standard-Workflows und Media-Handlern zur Verarbeitung von Assets. Der Workflow definiert die allgemeinen Aufgaben, die an Assets durchgeführt werden, und delegiert dann spezielle Aufgaben an die Medien-Handler, z. B. Erstellung von Miniaturbildern oder Extraktion von Metadaten.

Es ist möglich, einen Workflow zu definieren, der automatisch ausgeführt wird, wenn ein Asset eines bestimmten Typs auf den Server hochgeladen wird. Die Verarbeitungsschritte werden als eine Reihe von AEM Assets Media Handlers definiert. AEM provides some [built in handlers,](#default-media-handlers) and additional ones can be either [custom developed](#creating-a-new-media-handler) or defined by delegating the process to a [command line tool](#command-line-based-media-handler).

Media Handler sind Dienste innerhalb von AEM Assets, die bestimmte Aktionen für Assets ausführen. Wenn beispielsweise eine MP3-Audiodatei in AEM hochgeladen wird, löst ein Workflow einen MP3-Handler aus, der die Metadaten extrahiert und ein Miniaturbild erstellt. Medien-Handler werden normalerweise in Verbindung mit Workflows verwendet. Die meisten gängigen MIME-Typen werden in AEM unterstützt. Spezielle Aufgaben können an Assets durchgeführt werden, indem Workflows erweitert bzw. erstellt, Medien-Handler erweitert bzw. erstellt oder Medien-Handler deaktiviert bzw. aktiviert werden.

>[!NOTE]
>
>Please refer to the [Assets supported formats](assets-formats.md) page for a description of all the formats supported by AEM Assets as well as features supported for each format.

## Standard-Medien-Handler {#default-media-handlers}

Die folgenden Media-Handler stehen in AEM Assets zur Verfügung und behandeln die am häufigsten verwendeten MIME-Typen:

<!-- TBD: Apply correct formatting once table is moved to MD.
-->

| Handler-Name | Dienstname (in der Systemkonsole) | Unterstützte MIME-Typen |
|---|---|---|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>application/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | audio/mpeg |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | image/pict |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>application/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | application/epub/zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | Ausweichmöglichkeit, falls kein anderer Handler gefunden wurde, der Daten aus einem Asset extrahiert |

Alle Handler führen folgende Aufgaben aus:

* Extraktion aller verfügbaren Metadaten aus einem Asset.
* Erstellung eines Miniaturbilds aus einem Asset.

Es ist möglich, die aktiven Medien-Handler anzuzeigen:

1. In your browser, navigate to `http://localhost:4502/system/console/components`.
1. Click the link `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Eine Liste mit allen aktiven Medien-Handlern wird angezeigt. Beispiel:

![chlimage_1-437](assets/chlimage_1-437.png)

## Use Media Handlers in Workflows to perform tasks on Assets {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Medien-Handler sind Dienste, die normalerweise in Verbindung mit Workflows verwendet werden.

AEM bietet verschiedene Standard-Workflows zur Bearbeitung von Assets. To view them, open the Workflow console and click the **[!UICONTROL Models]** tab: the workflow titles that start with AEM Assets are the assets specific ones.

Bereits bestehende Workflows können erweitert und neue Workflows können erstellt werden, um Assets nach spezifischen Anforderungen zu bearbeiten.

The following example shows how to enhance the **[!UICONTROL AEM Assets Synchronization]** workflow so that sub-assets are generated for all assets except PDF documents.

### Media Handler deaktivieren oder aktivieren {#disabling-enabling-a-media-handler}

Die Medien-Handler können über die Apache Felix Web Management-Konsole deaktiviert bzw. aktiviert werden. Wenn der Medien-Handler deaktiviert ist, werden seine Aufgaben zur Bearbeitung von Assets nicht durchgeführt.

So aktivieren/deaktivieren Sie einen Medien-Handler:

1. In your browser, navigate to `https://<host>:<port>/system/console/components`.
1. Klicken Sie neben dem Namen des Medienhandlers auf **[!UICONTROL Deaktivieren]** . Beispiel: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Seite aktualisieren: Neben dem Medienhandler wird ein Symbol angezeigt, das angibt, dass er deaktiviert ist.
1. To enable the media handler, click **[!UICONTROL Enable]** next to the name of the media handler.

### Create a new Media Handler {#creating-a-new-media-handler}

Um einen neuen Medientyp zu unterstützen oder eine bestimmte Aufgabe an einem Asset durchzuführen, muss ein neuer Medien-Handler erstellt werden. In diesem Abschnitt wird beschrieben, wie Sie vorgehen.

#### Wichtige Klassen und Schnittstellen {#important-classes-and-interfaces}

The best way to start an implementation is to inherit from a provided abstract implementation that takes care of most things and provides reasonable default behavior: the `com.day.cq.dam.core.AbstractAssetHandler` class.

Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. So if you inherit from this class and use the maven-sling-plugin, make sure that you set the inherit flag to `true`.

Implementieren Sie die folgenden Methoden:

* `extractMetadata()`: extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: erstellt aus dem übergebenen Asset ein Miniaturbild.
* `getMimeTypes()`: gibt die Asset-MIME-Typen zurück.

Hier eine Beispielvorlage:

`package my.own.stuff; /** * @scr.component inherit="true" * @scr.service */ public class MyMediaHandler extends com.day.cq.dam.core.AbstractAssetHandler { // implement the relevant parts } `

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte Mime-Typen hinzufügt. Wenn ein neuer MIME-Typ hinzugefügt werden soll, muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler` class: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler` Klasse:
   * Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie häufig verwendete Funktionen für die Extrahierung von Teilassets.
   * Am besten ist es, zu Beginn einer Implementierung den Inhalt einer bereitgestellten abstrakten Implementierung zu übernehmen, wodurch die meisten Dinge im Voraus erledigt werden und ein angemessenes Standardverhalten erreicht wird: die com.day.cq.dam.core.AbstractAssetHandler-Klasse.
   * Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. Wenn Sie also den Inhalt dieser Klasse übernehmen und das maven-sling-Plug-in verwenden, müssen Sie das Übernahme-Flag auf true setzen.

Die folgenden Methoden müssen implementiert werden:

* `extractMetadata()`: Diese Methode extrahiert alle verfügbaren Metadaten.
* `getThumbnailImage()`: Diese Methode erstellt ein Miniaturbild aus dem übergebenen Asset.
* `getMimeTypes()`: Diese Methode gibt den bzw. die Asset-Mime-Typen zurück.

Hier eine Beispielvorlage:

package my.own.stuff; /&amp;ast;&amp;ast; &amp;ast; @scr.component inherit=&quot;true&quot; &amp;ast; @scr.service &amp;ast;/ public class MyMediaHandler extension com.day.cq.dam.core.AbstractAssetHandler { // implementieren Sie die entsprechenden Teile }

Schnittstelle und Klassen:

* `com.day.cq.dam.api.handler.AssetHandler` interface: Diese Schnittstelle beschreibt den Dienst, der Unterstützung für bestimmte Mime-Typen hinzufügt. Wenn ein neuer MIME-Typ hinzugefügt werden soll, muss diese Schnittstelle implementiert werden. Die Schnittstelle enthält Methoden zum Importieren und Exportieren der jeweiligen Dokumente, zum Erstellen von Miniaturbildern und zum Extrahieren von Metadaten.
* `com.day.cq.dam.core.AbstractAssetHandler` class: Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen.
* `com.day.cq.dam.core.AbstractSubAssetHandler` class:Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie häufig verwendete Funktionen für die Extrahierung von Teilassets.

#### Beispiel: Erstellung eines spezifischen Text-Handlers {#example-create-a-specific-text-handler}

In diesem Abschnitt erstellen Sie einen spezifischen Text-Handler, der Miniaturbilder mit einem Wasserzeichen erstellt.

Gehen Sie wie folgt vor:

Lesen Sie die [Entwicklungstools](../sites-developing/dev-tools.md) , um Eclipse mit einem Maven-Plugin zu installieren und einzurichten und um die Abhängigkeiten einzurichten, die für das Maven-Projekt benötigt werden.

Wenn Sie nach der Durchführung des folgenden Verfahrens eine Textdatei in AEM hochladen, werden die Metadaten der Datei extrahiert und zwei Miniaturbilder mit einem Wasserzeichen erstellt.

1. Erstellen Sie in Eclipse ein `myBundle` Maven-Projekt:

   1. In the Menu bar, click **[!UICONTROL File > New > Other]**.
   1. In the dialog, expand the Maven folder, select Maven Project and click **[!UICONTROL Next]**.
   1. Check the Create a simple project box and the Use default Workspace locations box, then click **[!UICONTROL Next]**.
   1. Definieren Sie das Maven-Projekt:

      * Gruppen-ID: com.day.cq5.myhandler
      * Artefakt-ID: myBundle
      * Name: Mein AEM-Bundle
      * Beschreibung: Das ist mein AEM-Bundle
   1. Klicken Sie auf **[!UICONTROL Finish]**.


1. Setzen Sie Java Compiler auf Version 1.5:

   1. Right-click the `myBundle` project, select Properties.
   1. Wählen Sie Java Compiler und setzen Sie folgende Eigenschaften auf 1.5:

      * Compiler-Kompatibilitätsstufe
      * Kompatibilität von generierten .class-Dateien
      * Quellkompatibilität
   1. Klicken Sie auf **[!UICONTROL OK]**. Klicken Sie im Dialogfenster auf „Ja“.


1. Ersetzen Sie den Code in der pom.xml-Datei durch folgenden Code:

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

1. Erstellen Sie das Paket, `com.day.cq5.myhandler` das die Java-Klassen enthält unter `myBundle/src/main/java`:

   1. Under myBundle, right-click `src/main/java`, select New, then Package.
   1. Name it `com.day.cq5.myhandler` and click Finish.

1. Erstellen Sie den Java Class `MyHandler`:

   1. In Eclipse, under `myBundle/src/main/java`, right-click the `com.day.cq5.myhandler` package, select New, then Class.
   1. Benennen Sie im Dialogfenster den Java Class MyHandler und klicken Sie auf „Fertigstellen“. Eclipse erstellt und öffnet die Datei MyHandler.java.
   1. In `MyHandler.java` replace the existing code with the following and then save the changes:

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
      watermarkLayer = ImageHelper.createLayer(session, "/content/dam/geometrixx/icons/certificate.png");
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
     // We need to keep track of the last character, if we have two white spaces in a row we dont want to double count
     // The starting of the document is always a whitespace
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
     // If we do not end with a white space then we need to add one extra word
     if (!currentWhiteSpace) { numwords++; }
     return numwords;
    }
   }
   ```

1. Kompilieren Sie die Java-Klasse und erstellen Sie das Bundle:

   1. Right-click the myBundle project, select **[!UICONTROL Run As]**, then **[!UICONTROL Maven Install]**.
   1. The bundle `myBundle-0.0.1-SNAPSHOT.jar` (containing the compiled class) is created under `myBundle/target`.

1. In CRX Explorer, create a new node under `/apps/myApp`. Name = `install`, Type = `nt:folder`.
1. Copy the bundle `myBundle-0.0.1-SNAPSHOT.jar` and store it under `/apps/myApp/install` (for example with WebDAV). Der neue Text-Handler ist jetzt in AEM aktiv.
1. Öffnen Sie im Browser die Apache Felix Web Management Console. Wählen Sie die Registerkarte „Komponenten“ aus und deaktivieren Sie den Standard-Text-Handler `com.day.cq.dam.core.impl.handler.TextHandler`.

## Befehlszeilenbasierter Medien-Handler {#command-line-based-media-handler}

Mit AEM können Sie jedes Befehlszeilenwerkzeug innerhalb eines Workflows ausführen, um Assets (z. B. ImageMagick) zu konvertieren und die neue Darstellung dem Asset hinzuzufügen. Sie müssen das Befehlszeilentool auf dem Datenträger installieren, der den AEM-Server hostet, und dem Workflow einen Prozessschritt hinzufügen. The invoked process, called `CommandLineProcess`, also enables to filter according to specific MIME types and to create multiple thumbnails based on the new rendition.

Die folgenden Konvertierungen können automatisch ausgeführt und in AEM Assets gespeichert werden:

* EPS- und AI-Umwandlung mithilfe von [ImageMagick](https://www.imagemagick.org/script/index.php) und [Ghostscript](https://www.ghostscript.com/) 
* FLV-Videotranskodierung mithilfe von [FFmpeg](https://ffmpeg.org/)
* MP3-Kodierung mithilfe von [LAME](http://lame.sourceforge.net/)
* Verarbeitung von Audiodaten mithilfe von [SOX](http://sox.sourceforge.net/) 

>[!NOTE]
>
>Bei Nicht-Windows-Systemen gibt das FFMpeg-Tool einen Fehler zurück, wenn Darstellungen für ein Video-Asset generiert werden, das ein einzelnes Anführungszeichen (&#39;) im Dateinamen enthält. Wenn der Name Ihrer Videodatei ein einfaches Anführungszeichen enthält, entfernen Sie es, bevor Sie das Asset auf AEM hochladen.

The `CommandLineProcess` process performs the following operations in the order they are listed:

* Filtert die Datei nach bestimmten MIME-Typen, falls angegeben.
* Erstellt ein temporäres Verzeichnis auf dem Datenträger, der den AEM-Server hostet. 
* Streamt die Originaldatei in den temporären Ordner.
* Führt den Befehl aus, der über die Argumente des Schritts definiert ist. Der Befehl wird im temporären Ordner mit den Berechtigungen des Benutzers ausgeführt, der AEM ausführt.
* Streamt das Ergebnis zurück in den Ausgabeordner des AEM-Servers.
* Löscht den temporären Ordner.
* Erstellt Miniaturbilder auf der Grundlage dieser Ausgabeformate, falls angegeben. Die Anzahl und die Abmessungen von Miniaturbildern werden durch die Argumente des Schritts definiert.

### Ein Beispiel mit ImageMagick {#an-example-using-imagemagick}

Das folgende Beispiel zeigt, wie Sie den Befehlszeilenprozessschritt so einrichten, dass jedes Mal, wenn ein Asset mit dem MIME-Typ GIF oder TIFF zu /content/dam auf dem AEM-Server hinzugefügt wird, ein gespiegeltes Bild des Originals zusammen mit drei zusätzlichen Miniaturbildern (140x100, 48x48 und 10x250) erstellt wird.

Dazu verwenden Sie ImageMagick. ImageMagick ist eine kostenlose Software zum Erstellen, Bearbeiten und Zusammenstellen von Bitmapbildern und wird in der Regel über die Befehlszeile ausgeführt.

Installieren Sie ImageMagick zunächst auf dem Datenträger, der den AEM-Server hostet:

1. Install ImageMagick: please refer to the [ImageMagick documentation](https://www.imagemagick.org/script/download.php).
1. Richten Sie das Tool so ein, dass Sie die Konvertierung über die Befehlszeile ausführen können.
1. To see if the tool is installed properly, run the following command `convert -h` on the command line.

   Es wird ein Hilfebildschirm mit allen möglichen Optionen des Konvertierungstools angezeigt.

   >[!NOTE]
   >
   >In manchen Versionen von Windows (z. B. Windows SE), kann der Konvertierungsbefehl eventuell nicht ausgeführt werden, da er in Konflikt mit dem nativen Konvertierungsdienstprogramm steht, das Teil der Windows-Installation ist. In diesem Fall verwenden Sie den vollständigen Pfad für das ImageMagick-Dienstprogramm, das verwendet wird, um Bilddateien in Miniaturbilder zu konvertieren. Beispiel, `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. To see if the tool runs properly, add a .jpg image to the working directory and run the command convert `<image-name>.jpg -flip <image-name>-flipped.jpg` on the command line.

   Ein gespiegeltes Bild wird dem Verzeichnis hinzugefügt.

Then, add the command line process step to the **[!UICONTROL DAM Update Asset]** workflow:

1. Go to the **[!UICONTROL Workflow]** console.
1. In the **[!UICONTROL Models]** tab, edit the **[!UICONTROL DAM Update Asset]** model.
1. Change the settings of the **[!UICONTROL Web enabled rendition]** step as follows:

   **Argumente**:

   `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

1. Speichern Sie den Workflow.

Fügen Sie zum Testen des geänderten Workflows ein Asset zu `/content/dam`hinzu.

1. Rufen Sie im Dateisystem ein TIFF-Bild Ihrer Wahl ab. Rename it to `myImage.tiff` and copy it to `/content/dam`, for example by using WebDAV.
1. Go to the **[!UICONTROL CQ5 DAM]** console, for example `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Open the asset **[!UICONTROL myImage.tiff]** and verify that the flipped image and the three thumbnails have been created.

#### Konfiguration des Prozessschritts CommandLineProcess {#configuring-the-commandlineprocess-process-step}

In diesem Abschnitt wird beschrieben, wie die **Prozess-Argumente** des **CommandLineProcess** festgelegt werden.

The values of the **Process Arguments** must be separated by a comma and must not start with a whitespace.

| Argument-Format | Beschreibung |
|---|---|
| mime:&lt;mime-type> | Optionales Argument. Der Prozess wird angewendet, wenn das Asset denselben MIME-Typ wie das Argument hat. <br>Es können mehrere Mime-Typen definiert werden. |
| tn:&lt;width>:&lt;height> | Optionales Argument. Der Prozess erstellt ein Miniaturbild mit den Abmessungen, die im Argument definiert sind. <br>Es können mehrere Miniaturansichten definiert werden. |
| cmd: &lt;command> | Definiert den auszuführenden Befehl. Die Syntax hängt vom Befehlszeilentool ab. Es kann nur ein Befehl definiert werden. <br>Die folgenden Variablen können zum Erstellen des Befehls verwendet werden:<br>`${filename}`: Name der Eingabedatei, z. B. original.jpg <br> `${file}`: vollständiger Pfadname der Eingabedatei, z. B. /tmp/cqdam0816.tmp/original.jpg <br> `${directory}`: Verzeichnis der Eingabedatei, z. B. /tmp/cqdam0816.tmp <br>`${basename}`: Name der Eingabedatei ohne Erweiterung, z. B. Original <br>`${extension}`: Erweiterung der Eingabedatei, z. B. jpg |

Wenn beispielsweise ImageMagick auf dem Datenträger installiert ist, der den AEM-Server hostet, und Sie einen Prozessschritt mithilfe von **CommandLineProcess** als Implementierung erstellen und die folgenden Werte als **Prozess-Argumente** verwenden:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

dann gilt der Schritt bei der Ausführung des Workflows nur für Assets, die image/gif oder mime:image/tiff als MIME-Typ haben. Der Schritt erstellt ein gespiegeltes Bild des Originals, wandelt es in eine JPG-Datei um und erstellt drei Miniaturbilder mit den Abmessungen 140x100, 48x48 und 10x250.

Use the following **Process Arguments** to create the three standard thumbnails using ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Use the following **Process Arguments** to create the web-enabled rendition using ImageMagick:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>The **CommandLineProcess** step only applies to Assets (nodes of type `dam:Asset`) or descendants of an Asset.
