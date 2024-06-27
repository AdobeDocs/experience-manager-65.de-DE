---
title: Wiedergeben von Formularen, die auf Fragmenten basieren
description: Verwenden Sie den Forms-Service zum Wiedergeben von Formularen, die auf mit Designer erstellten Fragmenten basieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: febf5350-3fc5-48c0-8bc5-198daff15936
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '2189'
ht-degree: 100%

---

# Wiedergeben von Formularen, die auf Fragmenten basieren {#rendering-forms-based-on-fragments}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

## Wiedergeben von Formularen, die auf Fragmenten basieren {#rendering-forms-based-on-fragments-inner}

Der Forms-Service kann Formulare wiedergeben, die auf mit Designer erstellten Fragmenten basieren. Ein *Fragment* ist ein wiederverwendbarer Teil eines Formulars und wird als separate XDP-Datei gespeichert, die in mehrere Formularentwürfe eingefügt werden kann. Beispielsweise kann ein Fragment einen Adressblock oder Copyright-Informationen enthalten.

Die Verwendung von Fragmenten vereinfacht und beschleunigt die Erstellung und Pflege großer Formularbestände. Beim Erstellen eines neuen Formulars fügen Sie einen Verweis auf das gewünschte Fragment ein. Das Fragment wird dann im Formular angezeigt. Der Fragmentverweis enthält ein Teilformular, das auf die eigentliche XDP-Datei verweist. Weitere Informationen zum Erstellen von Formularentwürfen, die auf Fragmenten basieren, finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63_de)

Ein Fragment kann mehrere Teilformulare enthalten, die in einen Auswahl-Teilformularsatz eingeschlossen sind. Auswahl-Teilformularsätze steuern die Anzeige von Teilformularen basierend auf dem Datenfluss einer Datenverbindung. Verwenden Sie bedingte Anweisungen, um festzulegen, welches Teilformular aus dem Satz im bereitgestellten Formular angezeigt wird. Beispielsweise kann jedes Teilformular in einem Satz Informationen für einen bestimmten geografischen Standort enthalten, und auf der Grundlage des Standorts des Benutzers kann bestimmt werden, welches Teilformular angezeigt wird.

Ein *Skriptfragment* enthält wiederverwendbare JavaScript-Funktionen oder -Werte, die getrennt von einem bestimmten Objekt gespeichert werden, z. B. einen Datums-Parser oder einen Aufruf eines Webservices. Diese Fragmente beinhalten ein Skriptobjekt, das in der Palette „Hierarchie“ als untergeordnetes Element von Variablen aufgeführt wird. Fragmente können nicht aus Skripten erstellt werden, die Eigenschaften anderer Objekte sind, wie etwa Ereignisskripte zum Validieren, Berechnen oder Initialisieren.

Die Verwendung von Fragmenten hat folgende Vorteile:

* **Wiederverwendung von Inhalten**: Sie können Fragmente verwenden, um Inhalte in mehreren Formularentwürfen wiederzuverwenden. Wenn Sie denselben Inhalt in mehreren Formularen verwenden müssen, ist es schneller und einfacher, ein Fragment zu verwenden, als den Inhalt zu kopieren oder neu zu erstellen. Durch die Verwendung von Fragmenten stellen Sie außerdem sicher, dass häufig verwendete Bestandteile eines Formularentwurfs in allen darauf verweisenden Formularen stets einen konsistenten Inhalt und ein einheitliches Erscheinungsbild besitzen.
* **Globale Aktualisierungen**: Sie können Fragmente verwenden, um globale Änderungen an mehreren Formularen nur einmal in einer Datei vorzunehmen. Sie können Inhalt, Skriptobjekte, Datenbindungen, Layout und Stile eines Fragments ändern. Alle XDP-Formulare, die auf dieses Fragment verweisen, spiegeln diese Änderungen wider.
* Ein gemeinsames Element vieler Formulare kann beispielsweise ein Block von Adressen sein, der ein Dropdown-Listenobjekt für das Land beinhaltet. Wenn Sie die Werte für das Dropdown-Listenobjekt aktualisieren müssen, müssen Sie viele Formulare öffnen, um die Änderungen vorzunehmen. Wenn sich aber der Adressenblock in einem Fragment befindet, müssen Sie lediglich eine einzige Fragmentdatei öffnen und dort die Änderungen vornehmen.
* Um ein Fragment in einem PDF-Formular zu aktualisieren, müssen Sie das Formular in Designer neu speichern.
* **Gemeinsame Entwicklung von Formularen**: Sie können die Formularentwicklung auf mehrere Ressourcen aufteilen. Formularentwickelnde mit Kenntnissen in der Skripterstellung oder im Umgang mit anderen komplexeren Funktionen von Designer können Fragmente erstellen und freigeben, die Scripting und dynamische Eigenschaften nutzen. Menschen, die Formulare entwerfen, können diese Fragmente dann für die Gestaltung von Formularentwürfen verwenden. Auf diese Weise wird sichergestellt, dass alle Bestandteile eines Formulars auch dann konsistente Inhalte und eine einheitliche Funktionalität aufweisen, wenn die Formularerstellung durch mehrere Personen erfolgt.

### Zusammenstellen eines Formularentwurfs, der mithilfe von Fragmenten zusammengestellt wurde {#assembling-a-form-design-assembled-using-fragments}

Sie können einen Formularentwurf basierend auf mehreren Fragmenten zusammenstellen, der an den Forms-Service übergeben wird. Verwenden Sie zum Zusammenführen mehrerer Fragmente den Assembler-Service. Ein Beispiel für die Verwendung des Assembler-Services zum Erstellen eines Formularentwurfs, der von anderen Forms-Services (dem Ausgabe-Service) verwendet wird, finden Sie unter [Erstellen von PDF-Dokumenten mithilfe von Fragmenten](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). Anstatt den Ausgabe-Service zu verwenden, können Sie denselben Workflow mit dem Forms-Service durchführen.

Bei Verwendung des Assembler-Services übergeben Sie einen Formularentwurf, der mithilfe von Fragmenten zusammengestellt wurde. Der erstellte Formularentwurf verweist nicht auf andere Fragmente. In diesem Thema wird dagegen die Übergabe eines Formularentwurfs erläutert, der andere Fragmente an den Forms-Service referenziert. Der Formularentwurf wurde jedoch nicht von Assembler zusammengestellt. Er wurde in Designer erstellt.

>[!NOTE]
>
>Weitere Informationen zum Forms-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Weitere Informationen zum Erstellen eines Web-basierten Programms, das auf Fragmenten basierende Formulare wiedergibt, finden Sie unter [Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md).

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein auf Fragmenten basierendes Formular wiederzugeben:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms-Client-API-Objekt.
1. Geben Sie URI-Werte an.
1. Geben Sie das Formular wieder.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms-Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Service programmgesteuert durchführen können, müssen Sie einen Client für den Forms-Service erstellen.

**Angeben der URI-Werte**

Um ein auf Fragmenten basierendes Formular erfolgreich wiederzugeben, müssen Sie sicherstellen, dass der Forms-Service sowohl das Formular als auch die Fragmente (die XDP-Dateien) finden kann, auf die der Formularentwurf verweist. Angenommen, das Formular heißt „PO.xdp“ und verwendet zwei Fragmente mit den Namen „FooterUS.xdp“ und „FooterCanada.xdp“. In diesem Fall muss der Forms-Service alle drei XDP-Dateien finden können.

Sie können ein Formular und seine Fragmente organisieren, indem Sie das Formular an einem Speicherort und die Fragmente an einem anderen Speicherort ablegen. Alternativ können Sie alle XDP-Dateien an demselben Speicherort platzieren. Für diesen Abschnitt wird davon ausgegangen, dass sich alle XDP-Dateien im AEM Forms-Repository befinden. Informationen zum Platzieren von XDP-Dateien im AEM Forms-Repository finden Sie unter [Schreiben von Ressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).

Beim Rendern eines Formulars, das auf Fragmenten basiert, dürfen Sie nur das Formular selbst und nicht die Fragmente referenzieren. Sie müssen beispielsweise auf „PO.xdp“ verweisen, jedoch nicht auf „FooterUS.xdp“ oder „FooterCanada.xdp“. Stellen Sie sicher, dass Sie die Fragmente an einer Stelle ablegen, an der der Forms-Service sie finden kann.

**Rendern des Formulars**

Ein auf Fragmenten basierendes Formular kann auf die gleiche Weise wie nicht fragmentierte Formulare gerendert werden. Das heißt, Sie können das Formular als PDF-, HTML- oder Formular-Guides (veraltet) rendern. Im Beispiel in diesem Abschnitt wird ein Formular, das auf Fragmenten basiert, als interaktives PDF-Formular gerendert. (Weitere Informationen finden Sie unter [Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**Schreiben des Formulardatentroms in den Client-Webbrowser**

Wenn der Forms-Service ein Formular rendert, wird ein Formulardatenstrom zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Sobald das Formular in den Client-Webbrowser geschrieben wurde, ist es für den Benutzer sichtbar.

**Siehe auch**

[Rendern von auf Fragmenten basierenden Formularen mithilfe der Java-API](#render-forms-based-on-fragments-using-the-java-api)

[Wiedergabe von Formularen, die auf Fragmenten basieren, mithilfe der Webservice-API](#render-forms-based-on-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstart mit der Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Web-Programmen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Rendern von auf Fragmenten basierenden Formularen mithilfe der Java-API {#render-forms-based-on-fragments-using-the-java-api}

Rendern eines auf Fragmenten basierenden Formulars mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Fügen Sie Client-JAR-Dateien wie „adobe-forms-client.jar“ in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Angeben der URI-Werte

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte speichert, indem Sie seinen Konstruktor verwenden.
   * Rufen Sie die Methode `setApplicationWebRoot` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Web-Stamm des Programms darstellt.
   * Rufen Sie die Methode `setContentRootURI` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Wert des Inhaltsstamms angibt. Stellen Sie sicher, dass sich der Formularentwurf und die Fragmente im URI des Inhaltsstamms befinden. Andernfalls löst der Forms-Service eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository://` an.
   * Rufen Sie die Methode `setTargetURL` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. Falls Sie die Ziel-URL im Formularentwurf definieren, können Sie auch eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Wiedergeben des Formulars

   Rufen Sie die Methode `renderPDFForm` des `FormsServiceClient`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die der Forms-Service benötigt, um ein Formular basierend auf Fragmenten zu rendern.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, für den Sie `null` angeben können, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die Methode `renderPDFForm` gibt ein `FormsResult`-Objekt zurück, das einen Formulardaten-Stream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Content-Typ des `com.adobe.idp.Document`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardaten-Streams in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `getInputStream`-Methode des `com.adobe.idp.Document`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array, das mit dem Formulardatenstrom gefüllt wird, indem Sie die `read`-Methode des `InputStream`-Objekts aufrufen und ihr das Byte-Array als Argument übergeben.
   * Rufen Sie die `write`-Methode des `javax.servlet.ServletOutputStream`-Objekts auf, um den Formulardatenstrom an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Wiedergeben von Formularen, die auf Fragmenten basieren](#rendering-forms-based-on-fragments)

[Kurzanleitung (SOAP-Modus): Rendern eines Formulars, das auf Fragmenten basiert, mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Wiedergabe von Formularen, die auf Fragmenten basieren, mithilfe der Webservice-API {#render-forms-based-on-fragments-using-the-web-service-api}

Wiedergabe eines Formulars, das auf Fragmenten basiert, mithilfe der Forms-API (Webservice):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxy-Klassen, welche die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. Angeben der URI-Werte

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte mithilfe seines Konstruktors speichert.
   * Rufen Sie die Methode `setApplicationWebRoot` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Web-Stamm des Programms darstellt.
   * Rufen Sie die Methode `setContentRootURI` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Wert des Inhaltsstamms angibt. Stellen Sie sicher, dass sich der Formularentwurf im Inhaltsstamm-URI befindet. Andernfalls löst der Forms-Service eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository://` an.
   * Rufen Sie die Methode `setTargetURL` des `URLSpec`-Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. Falls Sie die Ziel-URL im Formularentwurf definieren, können Sie auch eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Wiedergeben des Formulars

   Rufen Sie die Methode `renderPDFForm` des `FormsService`-Objekts auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil eines Forms-Programms ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Die mit Tags versehene PDF-Option kann nicht festgelegt werden, wenn das Eingabedokument ein PDF-Dokument ist. Wenn es sich bei der Eingabedatei um eine XDP-Datei handelt, kann die mit Tags versehene PDF-Option festgelegt werden.
   * Ein `URLSpec`-Objekt, das für den Forms-Service erforderliche URI-Werte enthält.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` festlegen, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode aufgefüllt wird. Dieser Parameter wird zum Speichern des wiedergegebenen Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode aufgefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode ausgefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthalten wird.

   Die Methode `renderPDFForm` füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardaten-Stream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardaten-Streams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des Datenelements `value` des `com.adobe.idp.services.holders.FormsResultHolder`-Objekts abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die Methode `getOutputContent` des `FormsResult`-Objekts aufrufen.
   * Ermitteln Sie den Inhaltstyp des `BLOB`-Objekts, indem Sie seine Methode `getContentType` aufrufen.
   * Legen Sie den Content-Typ des `javax.servlet.http.HttpServletResponse`-Objekts fest, indem Sie seine Methode `setContentType` aufrufen und den Content-Typ des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardaten-Stream in den Client-Webbrowser verwendet wird, indem Sie die Methode `getOutputStream` des `javax.servlet.http.HttpServletResponse`-Objekts aufrufen.
   * Erstellen Sie ein Byte-Array und füllen Sie es auf, indem Sie die Methode `getBinaryData` des `BLOB`-Objekts aufrufen. Mit dieser Aufgabe wird dem Byte-Array der Inhalt des `FormsResult`-Objekts zugewiesen.
   * Rufen Sie die Methode `write` des `javax.servlet.http.HttpServletResponse`-Objekts auf, um den Formulardaten-Stream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die Methode `write`.

**Siehe auch**

[Wiedergeben von Formularen, die auf Fragmenten basieren](#rendering-forms-based-on-fragments)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
