---
title: Rendern von Forms auf Grundlage von Fragmenten
seo-title: Rendern von Forms auf Grundlage von Fragmenten
description: Mit dem Forms-Dienst können Sie Formulare wiedergeben, die auf mit Designer erstellten Fragmenten basieren.
seo-description: Mit dem Forms-Dienst können Sie Formulare wiedergeben, die auf mit Designer erstellten Fragmenten basieren.
uuid: 9c9a730d-f970-41f8-afed-4e6b6d3d393d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: a65c5303-0ebd-43a9-a777-401042d8fcad
translation-type: tm+mt
source-git-commit: 9cf46a26d2aa2e41b924a4de89cf8ab5fdeeefc6
workflow-type: tm+mt
source-wordcount: '2229'
ht-degree: 9%

---


# Rendern von Forms basierend auf Fragmenten {#rendering-forms-based-on-fragments}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

## Rendern von Forms basierend auf Fragmenten {#rendering-forms-based-on-fragments-inner}

Der Forms-Dienst kann Formulare wiedergeben, die auf Fragmenten basieren, die Sie mit Designer erstellen. Ein *Fragment* ist ein wiederverwendbarer Teil eines Formulars und wird als separate XDP-Datei gespeichert, die in mehrere Formularentwürfe eingefügt werden kann. Beispielsweise kann ein Fragment einen Adressblock oder Copyright-Informationen enthalten.

Die Verwendung von Fragmenten vereinfacht und beschleunigt die Erstellung und Pflege großer Formularbestände. Beim Erstellen eines neuen Formulars fügen Sie einen Verweis auf das erforderliche Fragment ein und das Fragment wird im Formular angezeigt. Der Fragmentverweis enthält ein Teilformular, das auf die eigentliche XDP-Datei verweist. Informationen zum Erstellen von Formularentwürfen basierend auf Fragmenten finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Ein Fragment kann mehrere Teilformulare enthalten, die in einen Auswahl-Teilformularsatz eingeschlossen sind. Auswahl-Teilformularsätze steuern die Anzeige von Teilformularen basierend auf dem Datenfluss aus einer Datenverbindung. Verwenden Sie bedingte Anweisungen, um festzulegen, welches Teilformular aus dem Satz im bereitgestellten Formular angezeigt wird. Beispielsweise kann jedes Teilformular in einem Satz Informationen zu einem bestimmten geografischen Standort enthalten und das angezeigte Teilformular kann anhand des Standorts des Benutzers bestimmt werden.

Ein *Skriptfragment* enthält wiederverwendbare JavaScript-Funktionen oder Werte, die getrennt von einem bestimmten Objekt wie einem Datumsparser oder einem Webdienstaufruf gespeichert werden. Diese Fragmente beinhalten ein Skriptobjekt, das in der Palette „Hierarchie“ als untergeordnetes Element von „Variablen“ aufgeführt wird. Fragmente können nicht aus Skripten erstellt werden, die Eigenschaften anderer Objekte sind, wie etwa Ereignisskripte zum Validieren, Berechnen oder Initialisieren.

Die Verwendung von Fragmenten bietet folgende Vorteile:

* **Wiederverwendung** von Inhalten: Sie können Fragmente verwenden, um Inhalte in mehreren Formularentwürfen wiederzuverwenden. Wenn Sie einen Teil desselben Inhalts in mehreren Formularen verwenden müssen, ist es schneller und einfacher, ein Fragment zu verwenden, als den Inhalt zu kopieren oder neu zu erstellen. Durch die Verwendung von Fragmenten stellen Sie außerdem sicher, dass häufig verwendete Bestandteile eines Formularentwurfs in allen darauf verweisenden Formularen stets einen konsistenten Inhalt und ein einheitliches Erscheinungsbild besitzen.
* **Globale Updates**: Sie können Fragmente verwenden, um globale Änderungen an mehreren Formularen nur einmal in einer Datei vorzunehmen. Sie können Inhalt, Skriptobjekte, Datenbindungen, Layout oder Stile in einem Fragment ändern. Alle XDP-Formulare, die auf das Fragment verweisen, spiegeln die Änderungen wider.
* Ein gemeinsames Element in vielen Formularen kann beispielsweise ein Adressblock sein, der ein Dropdown-Liste-Objekt für das Land enthält. Wenn Sie die Werte für das Dropdown-Listen-Objekt aktualisieren müssen, müssen Sie viele Formulare öffnen, um die Änderungen vorzunehmen. Wenn Sie den Adressblock in ein Fragment einschließen, müssen Sie nur eine Fragmentdatei öffnen, um die Änderungen vorzunehmen.
* Um ein Fragment in einem PDF-Formular zu aktualisieren, müssen Sie das Formular erneut in Designer speichern.
* **Freigegebene Formularerstellung**: Sie können Fragmente verwenden, um die Erstellung von Formularen in mehreren Ressourcen gemeinsam zu nutzen. Formularentwickler mit Kenntnissen in der Skripterstellung und im Umgang mit den komplexeren Funktionen von Designer können Fragmente erstellen und freigeben, die Skripten und dynamische Eigenschaften nutzen. Formularverfasser können diese Fragmente dann für die Gestaltung von Formularentwürfen verwenden. Auf diese Weise wird sichergestellt, dass alle Bestandteile eines Formulars auch dann konsistente Inhalte und eine einheitliche Funktionalität aufweisen, wenn die Formularerstellung durch mehrere Mitarbeiter erfolgt.

### Zusammenstellen eines Formularentwurfs mit Fragmenten {#assembling-a-form-design-assembled-using-fragments}

Sie können einen Formularentwurf zusammenstellen, der basierend auf mehreren Fragmenten an den Forms-Dienst übergeben wird. Verwenden Sie den Assembler-Dienst, um mehrere Fragmente zusammenzustellen. Ein Beispiel für die Verwendung des Assemble-Dienstes zum Erstellen eines Formularentwurfs, der von einem anderen Forms-Dienst (dem Output-Dienst) verwendet wird, finden Sie unter [Erstellen von PDF-Dokumenten mit Fragmenten](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). Statt den Output-Dienst zu verwenden, können Sie denselben Workflow mit dem Forms-Dienst durchführen.

Bei Verwendung des Assembler-Dienstes übergeben Sie einen Formularentwurf, der mithilfe von Fragmenten zusammengestellt wurde. Der erstellte Formularentwurf verweist nicht auf andere Fragmente. In diesem Thema wird dagegen die Übergabe eines Formularentwurfs behandelt, der andere Fragmente an den Forms-Dienst referenziert. Der Formularentwurf wurde jedoch nicht von Assembler zusammengestellt. Es wurde in Designer erstellt.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienste-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Informationen zum Erstellen einer webbasierten Anwendung, mit der Formulare basierend auf Fragmenten wiedergegeben werden, finden Sie unter [Erstellen von Webanwendungen, mit denen Forms](/help/forms/developing/creating-web-applications-renders-forms.md) wiedergegeben wird.

### Zusammenfassung der Schritte {#summary-of-steps}

So rendern Sie ein Formular basierend auf Fragmenten:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Geben Sie URI-Werte an.
1. Formular wiedergeben.
1. Schreiben Sie den Formulardatenstream in den Client-Webbrowser.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Forms Client API-Objekt erstellen**

Bevor Sie einen Forms-Dienst-Client-API-Vorgang programmgesteuert durchführen können, müssen Sie einen Forms-Dienstclient erstellen.

**URI-Werte angeben**

Um ein Formular basierend auf Fragmenten erfolgreich wiedergeben zu können, müssen Sie sicherstellen, dass der Forms-Dienst sowohl das Formular als auch die Fragmente (die XDP-Dateien) finden kann, auf die der Formularentwurf verweist. Angenommen, das Formular trägt den Namen PO.xdp und dieses Formular verwendet zwei Fragmente namens FooterUS.xdp und FooterCanada.xdp. In diesem Fall muss der Forms-Dienst alle drei XDP-Dateien suchen können.

Sie können ein Formular und seine Fragmente organisieren, indem Sie das Formular an einem Speicherort und die Fragmente an einem anderen Speicherort ablegen oder Sie können alle XDP-Dateien an demselben Speicherort platzieren. Für die Zwecke dieses Abschnitts nehmen Sie an, dass sich alle XDP-Dateien im AEM Forms-Repository befinden. Weitere Informationen zum Platzieren von XDP-Dateien im AEM Forms-Repository finden Sie unter [Schreibressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).

Bei der Wiedergabe eines Formulars basierend auf Fragmenten müssen Sie nur auf das Formular selbst und nicht auf die Fragmente verweisen. Beispielsweise müssen Sie auf PO.xdp und nicht auf FooterUS.xdp oder FooterCanada.xdp verweisen. Stellen Sie sicher, dass Sie die Fragmente an einer Stelle platzieren, an der der Forms-Dienst sie finden kann.

**Formular wiedergeben**

Ein Formular, das auf Fragmenten basiert, kann auf dieselbe Weise wiedergegeben werden wie nicht fragmentierte Formulare. Das heißt, Sie können das Formular als PDF-, HTML- oder Formularleitfäden (nicht mehr unterstützt) wiedergeben. Im Beispiel in diesem Abschnitt wird ein Formular basierend auf Fragmenten als interaktives PDF-Formular wiedergegeben. (Siehe [Interaktive PDF forms rendern](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**Schreiben des Formulardatenstreams in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular wiedergibt, gibt er einen Formulardatenstream zurück, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Wiedergeben von Formularen basierend auf Fragmenten mit der Java-API](#render-forms-based-on-fragments-using-the-java-api)

[Wiedergeben von Formularen basierend auf Fragmenten mit der Webdienst-API](#render-forms-based-on-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Interaktive PDF forms wiedergeben](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen zum Rendern von Forms](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergeben von Formularen basierend auf Fragmenten mit der Java-API {#render-forms-based-on-fragments-using-the-java-api}

Wiedergabe eines Formulars basierend auf Fragmenten mit der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Forms Client API-Objekt erstellen

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient`-Objekt, indem Sie den Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. URI-Werte angeben

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte mithilfe seines Konstruktors speichert.
   * Rufen Sie die `setApplicationWebRoot`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Webstamm der Anwendung darstellt.`URLSpec`
   * Rufen Sie die `setContentRootURI`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Inhaltsstamm-URI-Wert angibt. `URLSpec` Stellen Sie sicher, dass sich der Formularentwurf und die Fragmente im Inhaltsstamm-URI befinden. Andernfalls gibt der Forms-Dienst eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository://` an.
   * Rufen Sie die `setTargetURL`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URL-Wert der Zielgruppe angibt, an den die Formulardaten gesendet werden. `URLSpec` Wenn Sie die Zielgruppen-URL im Formularentwurf definieren, können Sie eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsServiceClient`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document`-Objekt.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec`-Objekt, das URI-Werte enthält, die vom Forms-Dienst zum Wiedergeben eines Formulars basierend auf Fragmenten erforderlich sind.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie die `FormsResult`-Methode &quot;s `getOutputContent`&quot;aufrufen.
   * Rufen Sie den Inhaltstyp des `com.adobe.idp.Document`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `com.adobe.idp.Document`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein `java.io.InputStream`-Objekt, indem Sie die `com.adobe.idp.Document`-Methode des Objekts `getInputStream` aufrufen.
   * Erstellen Sie ein Bytearray, das mit dem Formulardatenstream gefüllt wird, indem Sie die `read`-Methode des Objekts aufrufen und das Bytearray als Argument übergeben.`InputStream`
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.ServletOutputStream` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von Forms auf Grundlage von Fragmenten](#rendering-forms-based-on-fragments)

[Quick Beginn (SOAP-Modus): Wiedergabe eines Formulars basierend auf Fragmenten mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Wiedergeben von Formularen basierend auf Fragmenten mithilfe der Webdienst-API {#render-forms-based-on-fragments-using-the-web-service-api}

Wiedergabe eines Formulars basierend auf Fragmenten mit der Forms API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Forms Client API-Objekt erstellen

   Erstellen Sie ein `FormsService`-Objekt und legen Sie Authentifizierungswerte fest.

1. URI-Werte angeben

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte mithilfe seines Konstruktors speichert.
   * Rufen Sie die `setApplicationWebRoot`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Webstamm der Anwendung darstellt.`URLSpec`
   * Rufen Sie die `setContentRootURI`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Inhaltsstamm-URI-Wert angibt. `URLSpec` Stellen Sie sicher, dass sich der Formularentwurf im Inhaltsstamm-URI befindet. Andernfalls gibt der Forms-Dienst eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository://` an.
   * Rufen Sie die `setTargetURL`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den URL-Wert der Zielgruppe angibt, an den die Formulardaten gesendet werden. `URLSpec` Wenn Sie die Zielgruppen-URL im Formularentwurf definieren, können Sie eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`FormsService`

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB`-Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpec`-Objekt, das Laufzeitoptionen speichert. Beachten Sie, dass die Option &quot;PDF mit Tags&quot;nicht eingestellt werden kann, wenn es sich beim Eingabe-Dokument um ein PDF-Dokument handelt. Wenn es sich bei der Eingabedatei um eine XDP-Datei handelt, kann die PDF-Option mit Tags festgelegt werden.
   * Ein `URLSpec`-Objekt, das die vom Forms-Dienst erforderlichen URI-Werte enthält.
   * Ein `java.util.HashMap`-Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter und Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder`-Objekt, das von der Methode gefüllt wird. Dieser Parameter wird zum Speichern des wiedergegebenen Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder`-Objekt, das von der Methode gefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder`-Objekt, das von der Methode gefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben des Formulardatenstreams in den Client-Webbrowser

   * Erstellen Sie ein `FormResult`-Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder`-Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent`-Methode des Objekts aufrufen.`FormsResult`
   * Rufen Sie den Inhaltstyp des `BLOB`-Objekts ab, indem Sie dessen `getContentType`-Methode aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie die `setContentType`-Methode aufrufen und den Inhaltstyp des `BLOB`-Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream`-Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `getOutputStream`-Methode des Objekts aufrufen.`javax.servlet.http.HttpServletResponse`
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB`-Methode des Objekts `getBinaryData`. Diese Aufgabe weist dem Bytearray den Inhalt des Objekts `FormsResult` zu.
   * Rufen Sie die `write`-Methode des Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. `javax.servlet.http.HttpServletResponse` Übergeben Sie das Bytearray an die `write`-Methode.

**Siehe auch**

[Rendern von Forms auf Grundlage von Fragmenten](#rendering-forms-based-on-fragments)

[Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
