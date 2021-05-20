---
title: Rendern von Forms basierend auf Fragmenten
seo-title: Rendern von Forms basierend auf Fragmenten
description: Verwenden Sie den Forms-Dienst zum Rendern von Formularen, die auf mit Designer erstellten Fragmenten basieren.
seo-description: Verwenden Sie den Forms-Dienst zum Rendern von Formularen, die auf mit Designer erstellten Fragmenten basieren.
uuid: 9c9a730d-f970-41f8-afed-4e6b6d3d393d
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: a65c5303-0ebd-43a9-a777-401042d8fcad
role: Developer
exl-id: febf5350-3fc5-48c0-8bc5-198daff15936
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2229'
ht-degree: 9%

---

# Rendern von Forms basierend auf Fragmenten {#rendering-forms-based-on-fragments}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

## Rendern von Forms basierend auf Fragmenten {#rendering-forms-based-on-fragments-inner}

Der Forms-Dienst kann Formulare wiedergeben, die auf Fragmenten basieren, die Sie mit Designer erstellen. Ein *Fragment* ist ein wiederverwendbarer Teil eines Formulars und wird als separate XDP-Datei gespeichert, die in mehrere Formularentwürfe eingefügt werden kann. Beispielsweise kann ein Fragment einen Adressblock oder Copyright-Informationen enthalten.

Die Verwendung von Fragmenten vereinfacht und beschleunigt die Erstellung und Pflege großer Formularbestände. Beim Erstellen eines neuen Formulars fügen Sie einen Verweis auf das erforderliche Fragment ein und das Fragment wird im Formular angezeigt. Der Fragmentverweis enthält ein Teilformular, das auf die eigentliche XDP-Datei verweist. Weitere Informationen zum Erstellen von Formularentwürfen basierend auf Fragmenten finden Sie unter [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63)

Ein Fragment kann mehrere Teilformulare enthalten, die in einen Auswahl-Teilformularsatz eingeschlossen sind. Auswahl-Teilformularsätze steuern die Anzeige von Teilformularen basierend auf dem Datenfluss einer Datenverbindung. Verwenden Sie bedingte Anweisungen, um festzulegen, welches Teilformular aus dem Satz im bereitgestellten Formular angezeigt wird. Beispielsweise kann jedes Teilformular in einem Satz Informationen für einen bestimmten geografischen Standort enthalten und das angezeigte Teilformular kann anhand des Standorts des Benutzers bestimmt werden.

Ein *Skriptfragment* enthält wiederverwendbare JavaScript-Funktionen oder Werte, die getrennt von einem bestimmten Objekt gespeichert werden, z. B. ein Datumsparser oder ein Webdienstaufruf. Diese Fragmente beinhalten ein Skriptobjekt, das in der Palette „Hierarchie“ als untergeordnetes Element von „Variablen“ aufgeführt wird. Fragmente können nicht aus Skripten erstellt werden, die Eigenschaften anderer Objekte sind, wie etwa Ereignisskripte zum Validieren, Berechnen oder Initialisieren.

Die Verwendung von Fragmenten hat folgende Vorteile:

* **Wiederverwendung von Inhalten**: Sie können Fragmente verwenden, um Inhalte in mehreren Formularentwürfen wiederzuverwenden. Wenn Sie denselben Inhalt in mehreren Formularen verwenden müssen, ist es schneller und einfacher, ein Fragment zu verwenden, als den Inhalt zu kopieren oder neu zu erstellen. Durch die Verwendung von Fragmenten stellen Sie außerdem sicher, dass häufig verwendete Bestandteile eines Formularentwurfs in allen darauf verweisenden Formularen stets einen konsistenten Inhalt und ein einheitliches Erscheinungsbild besitzen.
* **Globale Aktualisierungen**: Sie können Fragmente verwenden, um globale Änderungen an mehreren Formularen nur einmal in einer Datei vorzunehmen. Sie können den Inhalt, die Skriptobjekte, die Datenbindungen, das Layout oder die Stile in einem Fragment ändern. Alle XDP-Formulare, die auf das Fragment verweisen, spiegeln die Änderungen wider.
* Ein gemeinsames Element in vielen Formularen kann beispielsweise ein Adressblock sein, der ein Dropdown-Listenobjekt für das Land enthält. Wenn Sie die Werte für das Dropdown-Listenobjekt aktualisieren müssen, müssen Sie viele Formulare öffnen, um die Änderungen vorzunehmen. Wenn Sie den Adressblock in ein Fragment einschließen, müssen Sie nur eine Fragmentdatei öffnen, um die Änderungen vorzunehmen.
* Um ein Fragment in einem PDF-Formular zu aktualisieren, müssen Sie das Formular erneut in Designer speichern.
* **Freigegebene Formularerstellung**: Sie können Fragmente verwenden, um die Formularerstellung auf mehrere Ressourcen aufzuteilen. Formularentwickler mit Kenntnissen in der Skripterstellung und im Umgang mit den komplexeren Funktionen von Designer können Fragmente erstellen und freigeben, die Skripten und dynamische Eigenschaften nutzen. Formularverfasser können diese Fragmente dann für die Gestaltung von Formularentwürfen verwenden. Auf diese Weise wird sichergestellt, dass alle Bestandteile eines Formulars auch dann konsistente Inhalte und eine einheitliche Funktionalität aufweisen, wenn die Formularerstellung durch mehrere Mitarbeiter erfolgt.

### Zusammenstellen eines Formularentwurfs, der mit Fragmenten zusammengestellt wurde {#assembling-a-form-design-assembled-using-fragments}

Sie können einen Formularentwurf zusammenstellen, der basierend auf mehreren Fragmenten an den Forms-Dienst übergeben wird. Verwenden Sie zum Zusammenführen mehrerer Fragmente den Assembler-Dienst. Ein Beispiel für die Verwendung des Assembler-Dienstes zum Erstellen eines Formularentwurfs, der von anderen Forms-Diensten (dem Output-Dienst) verwendet wird, finden Sie unter [Erstellen von PDF-Dokumenten mit Fragmenten](/help/forms/developing/creating-document-output-streams.md#creating-pdf-documents-using-fragments). Anstatt den Output-Dienst zu verwenden, können Sie denselben Workflow mit dem Forms-Dienst durchführen.

Bei Verwendung des Assembler-Dienstes übergeben Sie einen Formularentwurf, der mithilfe von Fragmenten zusammengestellt wurde. Der erstellte Formularentwurf verweist nicht auf andere Fragmente. In diesem Thema wird dagegen die Übergabe eines Formularentwurfs erläutert, der andere Fragmente an den Forms-Dienst referenziert. Der Formularentwurf wurde jedoch nicht von Assembler zusammengestellt. Sie wurde in Designer erstellt.

>[!NOTE]
>
>Weitere Informationen zum Forms-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

>[!NOTE]
>
>Informationen zum Erstellen einer webbasierten Anwendung, die Formulare basierend auf Fragmenten wiedergibt, finden Sie unter [Erstellen von Webanwendungen, die Forms](/help/forms/developing/creating-web-applications-renders-forms.md) rendern.

### Zusammenfassung der Schritte {#summary-of-steps}

Führen Sie die folgenden Aufgaben aus, um ein Formular anhand von Fragmenten wiederzugeben:

1. Projektdateien einschließen.
1. Erstellen Sie ein Forms Client-API-Objekt.
1. Geben Sie URI-Werte an.
1. Rendern Sie das Formular.
1. Schreiben Sie den Formular-Datenstrom in den Client-Webbrowser.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Forms Client-API-Objekts**

Bevor Sie einen Client-API-Vorgang für den Forms-Dienst programmgesteuert ausführen können, müssen Sie einen Forms-Dienstclient erstellen.

**URI-Werte angeben**

Um ein Formular erfolgreich basierend auf Fragmenten wiederzugeben, müssen Sie sicherstellen, dass der Forms-Dienst sowohl das Formular als auch die Fragmente (die XDP-Dateien) finden kann, auf die der Formularentwurf verweist. Angenommen, das Formular heißt PO.xdp und verwendet zwei Fragmente namens FooterUS.xdp und FooterCanada.xdp. In diesem Fall muss der Forms-Dienst alle drei XDP-Dateien suchen können.

Sie können ein Formular und seine Fragmente organisieren, indem Sie das Formular an einem Speicherort und die Fragmente an einem anderen Speicherort platzieren. Alternativ können Sie alle XDP-Dateien an demselben Speicherort platzieren. Für die Zwecke dieses Abschnitts nehmen Sie an, dass sich alle XDP-Dateien im AEM Forms-Repository befinden. Informationen zum Platzieren von XDP-Dateien im AEM Forms-Repository finden Sie unter [Schreibressourcen](/help/forms/developing/aem-forms-repository.md#writing-resources).

Beim Wiedergeben eines Formulars, das auf Fragmenten basiert, dürfen Sie nur das Formular selbst referenzieren und nicht die Fragmente. Sie müssen beispielsweise auf PO.xdp und nicht auf FooterUS.xdp oder FooterCanada.xdp verweisen. Stellen Sie sicher, dass Sie die Fragmente an einer Stelle platzieren, an der der Forms-Dienst sie finden kann.

**Formular wiedergeben**

Ein auf Fragmenten basierendes Formular kann auf die gleiche Weise wiedergegeben werden wie nicht fragmentierte Formulare. Das heißt, Sie können das Formular als PDF-, HTML- oder Formular-Guides wiedergeben (veraltet). Das Beispiel in diesem Abschnitt rendert ein Formular, das auf Fragmenten basiert, als interaktives PDF-Formular. (Siehe [Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md).)

**Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser**

Wenn der Forms-Dienst ein Formular wiedergibt, wird ein Formulardatenstream zurückgegeben, den Sie in den Client-Webbrowser schreiben müssen. Beim Schreiben in den Client-Webbrowser ist das Formular für den Benutzer sichtbar.

**Siehe auch**

[Wiedergabe von Formularen basierend auf Fragmenten mithilfe der Java-API](#render-forms-based-on-fragments-using-the-java-api)

[Wiedergabe von Formularen basierend auf Fragmenten mithilfe der Webdienst-API](#render-forms-based-on-fragments-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service-API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Rendern interaktiver PDF forms](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen, die Forms rendern](/help/forms/developing/creating-web-applications-renders-forms.md)

### Wiedergabe von Formularen basierend auf Fragmenten mithilfe der Java-API {#render-forms-based-on-fragments-using-the-java-api}

Wiedergabe eines Formulars basierend auf Fragmenten mithilfe der Forms API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-forms-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Forms Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `FormsServiceClient` -Objekt, indem Sie dessen Konstruktor verwenden und das `ServiceClientFactory` -Objekt übergeben.

1. URI-Werte angeben

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte mithilfe seines Konstruktors speichert.
   * Rufen Sie die `setApplicationWebRoot` -Methode des Objekts `URLSpec` auf und übergeben Sie einen string -Wert, der den Webstamm der Anwendung darstellt.
   * Rufen Sie die `setContentRootURI` -Methode des Objekts `URLSpec` auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Wert für den Inhaltsstamm angibt. Stellen Sie sicher, dass sich der Formularentwurf und die Fragmente im Inhaltsstamm-URI befinden. Andernfalls gibt der Forms-Dienst eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository://` an.
   * Rufen Sie die `setTargetURL` -Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. `URLSpec` Wenn Sie die Ziel-URL im Formularentwurf definieren, können Sie eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `com.adobe.idp.Document` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie ein leeres `com.adobe.idp.Document` -Objekt.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec` -Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden, um ein Formular basierend auf Fragmenten wiederzugeben.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.

   Die `renderPDFForm`-Methode gibt ein `FormsResult`-Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `com.adobe.idp.Document` -Objekt, indem Sie die `FormsResult` -Methode des Objekts &quot;s `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `com.adobe.idp.Document` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `com.adobe.idp.Document` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein `java.io.InputStream` -Objekt, indem Sie die `getInputStream` -Methode des Objekts `com.adobe.idp.Document` aufrufen.
   * Erstellen Sie ein Byte-Array, das mit dem Formulardatenstream gefüllt wird, indem Sie die `read` -Methode des Objekts `InputStream` aufrufen und das Byte-Array als Argument übergeben.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.ServletOutputStream` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Rendern von Forms basierend auf Fragmenten](#rendering-forms-based-on-fragments)

[Schnellstart (SOAP-Modus): Wiedergabe eines Formulars basierend auf Fragmenten mithilfe der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-rendering-a-form-based-on-fragments-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Wiedergabe von Formularen basierend auf Fragmenten mithilfe der Webdienst-API {#render-forms-based-on-fragments-using-the-web-service-api}

Wiedergabe eines Formulars basierend auf Fragmenten mithilfe der Forms-API (Webdienst):

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden.
   * Schließen Sie die Java-Proxy-Klassen in Ihren Klassenpfad ein.

1. Erstellen eines Forms Client-API-Objekts

   Erstellen Sie ein `FormsService` -Objekt und legen Sie Authentifizierungswerte fest.

1. URI-Werte angeben

   * Erstellen Sie ein `URLSpec`-Objekt, das URI-Werte mithilfe des zugehörigen Konstruktors speichert.
   * Rufen Sie die `setApplicationWebRoot` -Methode des Objekts `URLSpec` auf und übergeben Sie einen string -Wert, der den Webstamm der Anwendung darstellt.
   * Rufen Sie die `setContentRootURI` -Methode des Objekts `URLSpec` auf und übergeben Sie einen Zeichenfolgenwert, der den URI-Wert für den Inhaltsstamm angibt. Stellen Sie sicher, dass sich der Formularentwurf im Inhaltsstamm-URI befindet. Andernfalls gibt der Forms-Dienst eine Ausnahme aus. Um auf das Repository zu verweisen, geben Sie `repository://` an.
   * Rufen Sie die `setTargetURL` -Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Ziel-URL-Wert angibt, an den die Formulardaten gesendet werden. `URLSpec` Wenn Sie die Ziel-URL im Formularentwurf definieren, können Sie eine leere Zeichenfolge übergeben. Sie können auch die URL angeben, an die ein Formular gesendet wird, um Berechnungen durchzuführen.

1. Formular wiedergeben

   Rufen Sie die `renderPDFForm` -Methode des Objekts `FormsService` auf und übergeben Sie die folgenden Werte:

   * Ein string -Wert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt. Wenn Sie auf einen Formularentwurf verweisen, der Teil einer Forms-Anwendung ist, stellen Sie sicher, dass Sie den vollständigen Pfad angeben, z. B. `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.
   * Ein `BLOB` -Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Wenn Sie keine Daten zusammenführen möchten, übergeben Sie `null`.
   * Ein `PDFFormRenderSpec` -Objekt, das Laufzeitoptionen speichert. Beachten Sie, dass die Option PDF mit Tags nicht festgelegt werden kann, wenn das Eingabedokument ein PDF-Dokument ist. Wenn es sich bei der Eingabedatei um eine XDP-Datei handelt, kann die getaggte PDF-Option festgelegt werden.
   * Ein `URLSpec` -Objekt, das für den Forms-Dienst erforderliche URI-Werte enthält.
   * Ein `java.util.HashMap` -Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter. Sie können `null` angeben, wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` -Objekt, das von der -Methode ausgefüllt wird. Dieser Parameter wird zum Speichern des wiedergegebenen Formulars verwendet.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` -Objekt, das von der -Methode ausgefüllt wird. Dieses Argument speichert die Anzahl der Seiten im Formular.
   * Ein leeres `javax.xml.rpc.holders.StringHolder` -Objekt, das von der -Methode ausgefüllt wird. Dieses Argument speichert den Gebietsschemawert.
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` -Objekt, das die Ergebnisse dieses Vorgangs enthält.

   Die `renderPDFForm`-Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder`-Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

1. Schreiben Sie den Formulardaten-Stream in den Client-Webbrowser

   * Erstellen Sie ein `FormResult` -Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` -Datenelements des Objekts `value` abrufen.
   * Erstellen Sie ein `BLOB`-Objekt, das Formulardaten enthält, indem Sie die `getOutputContent` -Methode des Objekts `FormsResult` aufrufen.
   * Rufen Sie den Inhaltstyp des Objekts `BLOB` ab, indem Sie dessen Methode `getContentType` aufrufen.
   * Legen Sie den Inhaltstyp des Objekts `javax.servlet.http.HttpServletResponse` fest, indem Sie seine `setContentType`-Methode aufrufen und den Inhaltstyp des Objekts `BLOB` übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` -Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser durch Aufrufen der `javax.servlet.http.HttpServletResponse` -Methode des Objekts `getOutputStream` verwendet wird.
   * Erstellen Sie ein Byte-Array und füllen Sie es durch Aufrufen der `getBinaryData`-Methode des Objekts `BLOB`. Diese Aufgabe weist den Inhalt des Objekts `FormsResult` dem Byte-Array zu.
   * Rufen Sie die `write` -Methode des Objekts `javax.servlet.http.HttpServletResponse` auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Byte-Array an die `write`-Methode.

**Siehe auch**

[Rendern von Forms basierend auf Fragmenten](#rendering-forms-based-on-fragments)

[Aufrufen von AEM Forms mit der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
