---
title: Verarbeiten von Assets mit Media Handlern und Workflows
description: Erfahren Sie mehr über die Media-Handler und wie Sie Workflows verwenden, um Aufgaben an Ihren digitalen Assets durchzuführen.
contentOwner: AG
role: Geschäftspraktiker
translation-type: tm+mt
source-git-commit: ebe7042b931869c3b4b7204e3ce7afa52d56f0ef
workflow-type: tm+mt
source-wordcount: '2163'
ht-degree: 50%

---


# Verarbeiten von Assets mit Media Handlern und Workflows {#processing-assets-using-media-handlers-and-workflows}

[!DNL Adobe Experience Manager Assets] verfügt über eine Reihe von Standard-Workflows- und Media-Handlern zur Verarbeitung von Assets. Ein Arbeitsablauf definiert die Aufgaben, die für die Assets ausgeführt werden sollen, und delegiert dann die spezifischen Aufgaben an die Media-Handler, z. B. die Erstellung von Miniaturbildern oder die Metadaten-Extraktion.

Ein Workflow kann so konfiguriert werden, dass er automatisch ausgeführt wird, wenn ein Asset eines bestimmten MIME-Typs hochgeladen wird. Die Verarbeitungsschritte werden als eine Reihe von [!DNL Assets]-Media-Handlern definiert. [!DNL Experience Manager] bietet einige [integrierte Handler](#default-media-handlers) und zusätzliche Handler können entweder [speziell entwickelt](#creating-a-new-media-handler) oder definiert werden, indem der Prozess an ein [Befehlszeilen-Tool](#command-line-based-media-handler) delegiert wird.

Media-Handler sind Dienste in [!DNL Assets], die bestimmte Aktionen für Assets ausführen. Wenn beispielsweise eine MP3-Audiodatei in [!DNL Experience Manager] hochgeladen wird, wird in einem Workflow ein MP3-Handler Trigger, der die Metadaten extrahiert und eine Miniaturansicht generiert. Medien-Handler werden normalerweise in Verbindung mit Workflows verwendet. Die gängigsten MIME-Typen werden innerhalb von [!DNL Experience Manager] unterstützt. Spezielle Aufgaben können an Assets durchgeführt werden, indem Workflows erweitert bzw. erstellt, Medien-Handler erweitert bzw. erstellt oder Medien-Handler deaktiviert bzw. aktiviert werden.

>[!NOTE]
>
>Eine Beschreibung aller von [!DNL Assets] unterstützten Formate sowie der für die einzelnen Formate unterstützten Funktionen finden Sie auf der Seite [Unterstützte Assets](assets-formats.md).

## Standard-Media-Handler {#default-media-handlers}

Die folgenden Media-Handler stehen innerhalb von [!DNL Assets] zur Verfügung und behandeln die am häufigsten verwendeten MIME-Typen:

<!-- TBD: Java versions shouldn't be set to 1.5. Must be updated.
-->

| Handler-Name | Dienstname (in der Systemkonsole) | Unterstützte MIME-Typen |
|--------------|--------------------------------------|----------------------|
| [!UICONTROL TextHandler] | com.day.cq.dam.core.impl.handler.TextHandler | text/plain |
| [!UICONTROL PdfHandler] | com.day.cq.dam.handler.standard.pdf.PdfHandler | <ul><li>application/pdf</li><li>application/illustrator</li></ul> |
| [!UICONTROL JpegHandler] | com.day.cq.dam.core.impl.handler.JpegHandler | image/jpeg |
| [!UICONTROL Mp3Handler] | com.day.cq.dam.handler.standard.mp3.Mp3Handler | audio/mpeg<br><b>Wichtig</b> : Wenn Sie eine MP3-Datei hochladen, wird sie mit einer Bibliothek [ eines Drittanbieters ](http://www.zxdr.it/programmi/SistEvolBDD/LibJava/doc/de/vdheide/mp3/MP3File.html)verarbeitet. Die Bibliothek berechnet eine nicht genaue ungefähre ungefähre Länge, wenn die MP3 eine variable Bitrate (VBR) aufweist. |
| [!UICONTROL ZipHandler] | com.day.cq.dam.handler.standard.zip.ZipHandler | <ul><li>application/java-archive </li><li> application/zip</li></ul> |
| [!UICONTROL PictHandler] | com.day.cq.dam.handler.standard.pict.PictHandler | image/pict |
| [!UICONTROL StandardImageHandler] | com.day.cq.dam.core.impl.handler.StandardImageHandler | <ul><li>image/gif </li><li> image/png </li> <li>application/photoshop </li> <li>image/jpeg </li><li> image/tiff </li> <li>image/x-ms-bmp </li><li> image/bmp</li></ul> |
| [!UICONTROL MSOfficeHandler] | com.day.cq.dam.handler.standard.msoffice.MSOfficeHandler | application/msword |
| [!UICONTROL MSPowerPointHandler] | com.day.cq.dam.handler.standard.msoffice.MSPowerPointHandler | application/vnd.ms-powerpoint |
| [!UICONTROL OpenOfficeHandler] | com.day.cq.dam.handler.standard.ooxml.OpenOfficeHandler | <ul><li>application/vnd.openxmlformats-officedocument.wordprocessingml.document</li><li> application/vnd.openxmlformats-officedocument.spreadsheetml.sheet</li><li> application/vnd.openxmlformats-officedocument.presentationml.presentation</li></ul> |
| [!UICONTROL EPubHandler] | com.day.cq.dam.handler.standard.epub.EPubHandler | application/epub+zip |
| [!UICONTROL GenericAssetHandler] | com.day.cq.dam.core.impl.handler.GenericAssetHandler | Ausweichmöglichkeit, falls kein anderer Handler gefunden wurde, der Daten aus einem Asset extrahiert |

Alle Handler führen folgende Aufgaben aus:

* Extraktion aller verfügbaren Metadaten aus einem Asset.
* Erstellen eines Miniaturbilds eines Assets.

So Ansicht der aktiven Medienhandler:

1. Navigieren Sie im Browser zu `http://localhost:4502/system/console/components`.
1. Klicken Sie auf `com.day.cq.dam.core.impl.store.AssetStoreImpl`.
1. Eine Liste mit allen aktiven Medien-Handlern wird angezeigt. Beispiel:

![chlimage_1-437](assets/chlimage_1-437.png)

## Verwenden Sie in Workflows Media Handler, um Aufgaben für Elemente durchzuführen {#using-media-handlers-in-workflows-to-perform-tasks-on-assets}

Medien-Handler sind Dienste, die normalerweise in Verbindung mit Workflows verwendet werden.

[!DNL Experience Manager] bietet verschiedene Standard-Workflows zur Bearbeitung von Assets. Um sie anzuzeigen, öffnen Sie die Workflow-Konsole und klicken Sie auf die Registerkarte **[!UICONTROL Modelle]**: Die Workflow-Namen, die mit beginnen, sind Asset-spezifische Workflows.[!DNL Assets]

Bereits bestehende Workflows können erweitert und neue Workflows können erstellt werden, um Assets nach spezifischen Anforderungen zu bearbeiten.

Das folgende Beispiel zeigt, wie der **[!UICONTROL AEM Assets-Synchronisierungs-Workflow]** erweitert werden kann, damit Teil-Assets für alle Assets außer PDF-Dokumente erstellt werden.

### Deaktivieren oder aktivieren Sie einen Medienhandler {#disabling-enabling-a-media-handler}

Die Medien-Handler können über die Apache Felix Web Management-Konsole deaktiviert bzw. aktiviert werden. Wenn der Medien-Handler deaktiviert ist, werden seine Aufgaben zur Bearbeitung von Assets nicht durchgeführt.

So aktivieren/deaktivieren Sie einen Medien-Handler:

1. Navigieren Sie im Browser zu `https://<host>:<port>/system/console/components`.
1. Klicken Sie neben dem Namen des Medien-Handlers auf **[!UICONTROL Deaktivieren]**. Beispiel: `com.day.cq.dam.handler.standard.mp3.Mp3Handler`.
1. Aktualisieren Sie die Seite: Neben dem Medien-Handler wird ein Symbol angezeigt, das angibt, dass er deaktiviert ist.
1. Um den Medien-Handler zu aktivieren, klicken Sie neben dem Namen des Medien-Handlers auf **[!UICONTROL Aktivieren]**.

### Erstellen eines neuen Medienhandlers {#creating-a-new-media-handler}

Um einen neuen Medientyp zu unterstützen oder eine bestimmte Aufgabe an einem Asset durchzuführen, muss ein neuer Medien-Handler erstellt werden. In diesem Abschnitt wird beschrieben, wie Sie vorgehen.

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
   * Diese Klasse dient als Grundlage für alle anderen Asset-Handler-Implementierungen und bietet häufig verwendete Funktionen sowie häufig verwendete Funktionen für die Extraktion von Teilassets.
   * Die beste Methode zum Beginn einer Implementierung besteht darin, eine bereitgestellte abstrakte Implementierung zu übernehmen, die die meisten Dinge übernimmt und ein vernünftiges Standardverhalten bietet: die Klasse com.day.cq.dam.core.AbstractAssetHandler.
   * Diese Klasse enthält bereits einen abstrakten Dienst-Deskriptor. Wenn Sie also den Inhalt dieser Klasse übernehmen und das maven-sling-Plug-in verwenden, müssen Sie das Übernahme-Flag auf true setzen.

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

#### Beispiel: einen bestimmten Texthandler {#example-create-a-specific-text-handler} erstellen

In diesem Abschnitt erstellen Sie einen spezifischen Text-Handler, der Miniaturbilder mit einem Wasserzeichen erstellt.

Gehen Sie wie folgt vor:

Weitere Informationen zum Installieren und Einrichten von Eclipse mit einem [!DNL Maven]-Plugin und zum Einrichten der Abhängigkeiten, die für das [!DNL Maven]-Projekt erforderlich sind, finden Sie unter [Entwicklungstools](../sites-developing/dev-tools.md).

Nachdem Sie das folgende Verfahren ausgeführt haben, werden beim Hochladen einer TXT-Datei in [!DNL Experience Manager] die Metadaten der Datei extrahiert und zwei Miniaturansichten mit einem Wasserzeichen generiert.

1. Erstellen Sie in Eclipse das Projekt `myBundle` [!DNL Maven]:

   1. Klicken Sie in der Menüleiste auf **[!UICONTROL Datei]** > **[!UICONTROL Neu]** > **[!UICONTROL Andere]**.
   1. Erweitern Sie im Dialogfeld den Ordner [!DNL Maven], wählen Sie [!DNL Maven] Projekt und klicken Sie auf **[!UICONTROL Weiter]**.
   1. Markieren Sie die Felder &quot;Einfaches Projekt erstellen&quot;und &quot;Standardspeicherorte für Workspace verwenden&quot;und klicken Sie dann auf **[!UICONTROL Weiter]**.
   1. Definieren Sie ein [!DNL Maven]-Projekt:

      * Gruppen-ID: `com.day.cq5.myhandler`.
      * Artefakt-ID: myBundle.
      * Name: Mein [!DNL Experience Manager] Bundle.
      * Beschreibung: Dies ist mein [!DNL Experience Manager] Bundle.
   1. Klicken Sie auf **[!UICONTROL Beenden]**.


1. Setzen Sie den [!DNL Java]-Compiler auf Version 1.5:

   1. Klicken Sie mit der rechten Maustaste auf das Projekt `myBundle` und wählen Sie [!UICONTROL Eigenschaften].
   1. Wählen Sie [!UICONTROL Java Compiler] und legen Sie die folgenden Eigenschaften auf 1.5 fest:

      * Compiler-Kompatibilitätsstufe
      * Kompatibilität von generierten .class-Dateien
      * Quellkompatibilität
   1. Klicken Sie auf **[!UICONTROL OK]**. Klicken Sie im Dialogfeld auf **[!UICONTROL Ja]**.


1. Ersetzen Sie den Code in der Datei `pom.xml` durch den folgenden Code:

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

   1. Klicken Sie unter myBundle mit der rechten Maustaste auf `src/main/java`, wählen Sie New und dann Package.
   1. Benennen Sie es `com.day.cq5.myhandler` und klicken Sie auf Fertig stellen.

1. Erstellen Sie die [!DNL Java]-Klasse `MyHandler`:

   1. Klicken Sie in [!DNL Eclipse] unter `myBundle/src/main/java` mit der rechten Maustaste auf das `com.day.cq5.myhandler`-Paket. Wählen Sie [!UICONTROL Neu] und dann [!UICONTROL Klasse].
   1. Benennen Sie im Dialogfeld die [!DNL Java]-Klasse `MyHandler` und klicken Sie auf [!UICONTROL Fertigstellen]. [!DNL Eclipse] erstellt und öffnet die Datei  `MyHandler.java`.
   1. Ersetzen Sie in `MyHandler.java` den vorhandenen Code durch den folgenden und speichern Sie dann die Änderungen:

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
     // We need to keep track of the last character, if we have two whitespaces in a row we don't want to double count.
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

   1. Klicken Sie mit der rechten Maustaste auf das Projekt `myBundle`, wählen Sie **[!UICONTROL Ausführen als]** und dann **[!UICONTROL Maven Install]**.
   1. Das Bundle `myBundle-0.0.1-SNAPSHOT.jar` (das die kompilierte Klasse enthält) wird unter `myBundle/target` erstellt.

1. Erstellen Sie im CRX Explorer einen neuen Knoten unter `/apps/myApp`. Name = `install`, Typ = `nt:folder`.
1. Kopieren Sie das Bundle `myBundle-0.0.1-SNAPSHOT.jar` und speichern Sie es unter `/apps/myApp/install` (z. B. mit WebDAV). Der neue Texthandler ist jetzt in [!DNL Experience Manager] aktiv.
1. Öffnen Sie in Ihrem Browser die Apache Felix Web Management Console]. [!UICONTROL  Wählen Sie die Registerkarte [!UICONTROL Komponenten] und deaktivieren Sie den Standard-Texthandler `com.day.cq.dam.core.impl.handler.TextHandler`.

## Befehlszeilenbasierter Medienhandler {#command-line-based-media-handler}

[!DNL Experience Manager]Mit können Sie ein beliebiges Befehlszeilen-Tool (z. B. ) innerhalb eines Workflows ausführen, um Assets zu konvertieren und dem Asset das neue Ausgabeformat hinzuzufügen. [!DNL ImageMagick] Sie müssen nur das Befehlszeilenwerkzeug auf der Festplatte installieren, auf der der [!DNL Experience Manager]-Server gehostet wird, und einen Prozessschritt zum Workflow hinzufügen und konfigurieren. Der aufgerufene Prozess `CommandLineProcess` ermöglicht zudem die Filterung nach spezifischen MIME-Typen und die Erstellung mehrerer Miniaturbilder auf der Grundlage des neuen Ausgabeformats.

Die folgenden Konvertierungen können automatisch ausgeführt und innerhalb von [!DNL Assets] gespeichert werden:

* EPS- und AI-Umwandlung mithilfe von [ImageMagick](https://www.imagemagick.org/script/index.php) und [Ghostscript](https://www.ghostscript.com/).
* FLV-Videotranskodierung mithilfe von [FFmpeg](https://ffmpeg.org/).
* MP3-Kodierung mithilfe von [LAME](https://lame.sourceforge.io/).
* Verarbeitung von Audiodaten mithilfe von [SOX](https://sox.sourceforge.net/).

>[!NOTE]
>
>Bei Nicht-Windows-Systemen gibt das FFmpeg-Tool einen Fehler zurück, wenn Darstellungen für ein Video-Asset generiert werden, dessen Dateiname ein einfaches Anführungszeichen (&#39;) enthält. Wenn der Name Ihrer Videodatei ein einfaches Anführungszeichen enthält, entfernen Sie es, bevor Sie es zu [!DNL Experience Manager] hochladen.

Der Prozess `CommandLineProcess` führt folgende Vorgänge in der angegebenen Reihenfolge aus:

* Filtert die Datei nach bestimmten MIME-Typen, falls angegeben.
* Erstellt einen temporären Ordner auf der Festplatte, auf der der [!DNL Experience Manager]-Server gehostet wird.
* Streamt die Originaldatei in das temporäre Verzeichnis.
* Führt den Befehl aus, der über die Argumente des Schritts definiert ist. Der Befehl wird im temporären Ordner mit den Berechtigungen des Benutzers ausgeführt, der [!DNL Experience Manager] ausführt.
* Streamt das Ergebnis zurück in den Ausgabeordner des Servers [!DNL Experience Manager].
* Löscht das temporäre Verzeichnis.
* Erstellt Miniaturbilder auf der Grundlage dieser Ausgabeformate, falls angegeben. Die Anzahl und die Abmessungen von Miniaturbildern werden durch die Argumente des Schritts definiert.

### Ein Beispiel mit [!DNL ImageMagick] {#an-example-using-imagemagick}

Das folgende Beispiel zeigt Ihnen, wie Sie den Befehlszeilenprozesses so einrichten, dass jedes Mal, wenn ein Asset mit dem E-Typ &quot;miMIME&quot;GIF oder TIFF zu `/content/dam` auf dem Server [!DNL Experience Manager] hinzugefügt wird, ein gedrehtes Bild des Originals mit drei zusätzlichen Miniaturansichten (140 x 100, 48 x 48 und 10 x 220) erstellt wird 0).

Verwenden Sie dazu [!DNL ImageMagick]. [!DNL ImageMagick] ist eine kostenlose Befehlszeilensoftware zum Erstellen, Bearbeiten und Erstellen von Bitmapbildern.

Installieren Sie [!DNL ImageMagick] auf der Festplatte, auf der der [!DNL Experience Manager]-Server gehostet wird:

1. [!DNL ImageMagick] installieren: Siehe [ImageMagick-Dokumentation](https://www.imagemagick.org/script/download.php).
1. Richten Sie das Tool ein, damit Sie den Befehl „convert“ über die Befehlszeile ausführen können.
1. Um festzustellen, ob das Tool ordnungsgemäß installiert wurde, führen Sie den Befehl `convert -h` über die Befehlszeile aus.

   Es wird ein Hilfebildschirm mit allen möglichen Optionen des Konvertierungs-Tools angezeigt.

   >[!NOTE]
   >
   >In einigen Windows-Versionen kann der Befehl &quot;Konvertieren&quot;nicht ausgeführt werden, da er mit dem nativen Konvertierungsprogramm im Konflikt steht, das Teil der [!DNL Windows]-Installation ist. Geben Sie in diesem Fall den vollständigen Pfad für die [!DNL ImageMagick]-Software an, die zum Konvertieren von Bilddateien in Miniaturansichten verwendet wird. Beispiel: `"C:\Program Files\ImageMagick-6.8.9-Q16\convert.exe" -define jpeg:size=319x319 ${filename} -thumbnail 319x319 cq5dam.thumbnail.319.319.png`.

1. Um zu sehen, ob das Tool ordnungsgemäß ausgeführt wird, fügen Sie dem Arbeitsverzeichnis ein JPG-Bild hinzu und führen Sie den Befehl convert `<image-name>.jpg -flip <image-name>-flipped.jpg` in der Befehlszeile aus. Ein gespiegeltes Bild wird dem Verzeichnis hinzugefügt. Fügen Sie dann den Befehlszeilenprozessschritt dem Workflow **[!UICONTROL DAM-Update-Asset]** hinzu.
1. Rufen Sie die Konsole **[!UICONTROL Workflow]** auf.
1. Bearbeiten Sie auf der Registerkarte **[!UICONTROL Modelle]** das Modell **[!UICONTROL DAM-Update-Asset]**.
1. Ändern Sie die [!UICONTROL Argumente] des Schritts **[!UICONTROL Webaktivierte Darstellung]** in: `mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`.
1. Speichern Sie den Workflow.

Fügen Sie zum Testen des geänderten Workflows ein Asset zu `/content/dam` hinzu.

1. Rufen Sie im Dateisystem ein TIFF-Bild Ihrer Wahl ab. Benennen Sie es in `myImage.tiff` um und kopieren Sie es in `/content/dam`, z. B. mithilfe von WebDAV.
1. Rufen Sie die Konsole **[!UICONTROL CQ5 DAM]** auf, z. B. `http://localhost:4502/libs/wcm/core/content/damadmin.html`.
1. Öffnen Sie das Asset **[!UICONTROL myImage.tiff]** und prüfen Sie, ob das gespiegelte Bilder und die drei Miniaturbilder erstellt wurden.

#### Konfigurieren des BefehlsLineProcess-Prozessschritts {#configuring-the-commandlineprocess-process-step}

In diesem Abschnitt wird beschrieben, wie die [!UICONTROL Prozess-Argumente] des [!UICONTROL CommandLineProcess] festgelegt werden.

Trennen Sie die Werte von [!UICONTROL Prozessargumenten] durch Kommas und verwenden Sie kein Leerzeichen, um sie Beginn.

| Argument-Format | Beschreibung |
|---|---|
| mime:&lt;MIME-Typ> | Optionales Argument. Der Prozess wird angewendet, wenn das Asset denselben MIME-Typ wie das Argument hat. <br>Es können mehrere MIME-Typen definiert werden. |
| tn:&lt;Breite>:&lt;Höhe> | Optionales Argument. Der Prozess erstellt ein Miniaturbild mit den Abmessungen, die im Argument definiert sind. <br>Es können mehrere Miniaturbilder definiert werden. |
| cmd: &lt;Befehl> | Definiert den ausgeführten Befehl. Die Syntax hängt vom Befehlszeilen-Tool ab. Nur ein Befehl kann definiert werden. <br>Die folgenden Variablen können zum Erstellen des Befehls verwendet werden:<br>`${filename}`: Name der Eingabedatei, z. B. original.jpg  <br> `${file}`: Vollständiger Pfadname der Eingabedatei, z. B.  `/tmp/cqdam0816.tmp/original.jpg` <br> `${directory}`: Verzeichnis der Eingabedatei, z. B.  `/tmp/cqdam0816.tmp` <br>`${basename}`: Name der Eingabedatei ohne Erweiterung, z. B. Original  <br>`${extension}`: Erweiterung der Eingabedatei, z. B. JPG. |

Beispiel: Wenn [!DNL ImageMagick] auf dem Datenträger installiert ist, auf dem der [!DNL Experience Manager]-Server gehostet wird, und Sie einen Prozessschritt mit [!UICONTROL CommandLineProcess] als Implementierung und die folgenden Werte als [!UICONTROL Prozessargumente] erstellen:

`mime:image/gif,mime:image/tiff,tn:140:100,tn:48:48,tn:10:250,cmd:convert ${directory}/${filename} -flip ${directory}/${basename}.flipped.jpg`

Wenn der Workflow ausgeführt wird, gilt der Schritt nur für Assets, deren `image/gif` oder `mime:image/tiff` `mime-types`  ist, und erstellt ein gedrehtes Bild des Originals, konvertiert es in JPG und erstellt drei Miniaturansichten mit den folgenden Abmessungen: 140 x 100, 48 x 48 und 10 x 250.

Verwenden Sie die folgenden [!UICONTROL Prozessargumente], um die drei Standardminiaturen mit [!DNL ImageMagick] zu erstellen:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=319x319 -thumbnail "319x319>" -background transparent -gravity center -extent 319x319 -write png:cq5dam.thumbnail.319.319.png -thumbnail "140x100>" -background transparent -gravity center -extent 140x100 -write cq5dam.thumbnail.140.100.png -thumbnail "48x48>" -background transparent -gravity center -extent 48x48 cq5dam.thumbnail.48.48.png`

Verwenden Sie die folgenden [!UICONTROL Prozessargumente], um die webaktivierte Darstellung mit [!DNL ImageMagick] zu erstellen:

`mime:image/tiff,mime:image/png,mime:image/bmp,mime:image/gif,mime:image/jpeg,cmd:convert ${filename} -define jpeg:size=1280x1280 -thumbnail "1280x1280>" cq5dam.web.1280.1280.jpeg`

>[!NOTE]
>
>Der Schritt [!UICONTROL CommandLineProcess] gilt nur für Assets (Knoten des Typs `dam:Asset`) oder untergeordnete Elemente eines Assets.

>[!MORELIKETHIS]
>
>* [Prozesselemente](assets-workflow.md)

