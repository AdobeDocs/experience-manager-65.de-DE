---
title: Vorausfüllen von Formularen mit flexiblen Layouts
seo-title: Vorausfüllen von Formularen mit flexiblen Layouts
description: 'null'
seo-description: 'null'
uuid: 93ccb496-e1c2-4b79-8e89-7a2abfce1537
content-type: reference
geptopics: SG_AEMFORMS/categories/rendering_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 30a12fc6-07b8-4c7c-b9e2-caa2bec0ac48
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Vorausfüllen von Formularen mit flexiblen Layouts {#prepopulating-forms-with-flowable-layouts1}

## Vorausfüllen von Formularen mit flexiblen Layouts {#prepopulating-forms-with-flowable-layouts2}

Beim Vorausfüllen von Formularen werden Daten für Benutzer in einem wiedergegebenen Formular angezeigt. Angenommen, ein Benutzer meldet sich mit einem Benutzernamen und einem Kennwort bei einer Website an. Bei erfolgreicher Authentifizierung fragt die Clientanwendung eine Datenbank nach Benutzerinformationen ab. Die Daten werden mit dem Formular zusammengeführt und dann dem Benutzer wiedergegeben. Dadurch kann der Benutzer personalisierte Daten im Formular anzeigen.

Das Vorausfüllen eines Formulars hat folgende Vorteile:

* Ermöglicht dem Benutzer, benutzerdefinierte Daten in einem Formular anzuzeigen.
* Verringert die Eingabe, die der Benutzer zum Ausfüllen eines Formulars vornimmt.
* Stellt die Datenintegrität sicher, indem es die Position der Daten kontrolliert.

Die folgenden zwei XML-Datenquellen können ein Formular im Voraus ausfüllen:

* Eine XDP-Datenquelle, bei der es sich um eine XML handelt, die der XFA-Syntax entspricht (oder XFDF-Daten zum Vorausfüllen eines mit Acrobat erstellten Formulars).
* Eine beliebige XML-Datenquelle, die Name/Wert-Paare enthält, die den Feldnamen des Formulars entsprechen (die Beispiele in diesem Abschnitt verwenden eine beliebige XML-Datenquelle).

Für jedes Formularfeld, das im Voraus gefüllt werden soll, muss ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge, in der die XML-Elemente angezeigt werden, einzuhalten, solange alle XML-Elemente angegeben sind.

Wenn Sie ein Formular vorab ausfüllen, das bereits Daten enthält, müssen Sie die Daten angeben, die bereits in der XML-Datenquelle angezeigt werden. Angenommen, ein Formular mit 10 Feldern enthält Daten in vier Feldern. Nehmen Sie als Nächstes an, dass Sie die restlichen sechs Felder vorab ausfüllen möchten. In diesem Fall müssen Sie 10 XML-Elemente in der XML-Datenquelle angeben, die zum Vorausfüllen des Formulars verwendet wird. Wenn Sie nur sechs Elemente angeben, sind die ursprünglichen vier Felder leer.

Sie können beispielsweise ein Formular wie das Musterbestätigungsformular im Voraus ausfüllen. (Siehe &quot;Bestätigungsformular&quot;in [Wiedergabe von interaktiven PDF-Formularen](/help/forms/developing/rendering-interactive-pdf-forms.md#rendering-interactive-pdf-forms).)

Zum Vorausfüllen des Musterbestätigungsformulars müssen Sie eine XML-Datenquelle erstellen, die drei XML-Elemente enthält, die den drei Feldern im Formular entsprechen. Dieses Formular enthält die folgenden drei Felder: `FirstName`, `LastName`und `Amount`. Der erste Schritt besteht darin, eine XML-Datenquelle zu erstellen, die XML-Elemente enthält, die mit den Feldern im Formularentwurf übereinstimmen. Der nächste Schritt besteht darin, den XML-Elementen Datenwerte zuzuweisen, wie im folgenden XML-Code dargestellt.

```as3
     <Untitled>
         <FirstName>Jerry</FirstName>
         <LastName>Johnson</LastName>
         <Amount>250000</Amount>
     </Untitled>
```

Nachdem Sie das Bestätigungsformular mit dieser XML-Datenquelle ausgefüllt und das Formular dann wiedergegeben haben, werden die den XML-Elementen zugewiesenen Datenwerte angezeigt, wie im folgenden Diagramm dargestellt.

![pf_pf_firm_xml3](assets/pf_pf_confirmxml3.png)

### Vorausfüllen von Formularen mit flexiblen Layouts {#prepopulating_forms_with_flowable_layouts-1}

Formulare mit flexiblen Layouts sind nützlich, um Benutzern eine unbestimmte Datenmenge anzuzeigen. Da sich das Layout des Formulars automatisch an die zusammengeführte Datenmenge anpasst, müssen Sie kein festes Layout oder keine Seitenzahl für das Formular vorab festlegen, wie Sie es bei einem Formular mit festem Layout tun müssen.

Ein Formular wird in der Regel mit Daten gefüllt, die während der Laufzeit abgerufen werden. Daher können Sie ein Formular vorab ausfüllen, indem Sie eine XML-Datenquelle im Arbeitsspeicher erstellen und die Daten direkt in die XML-Datenquelle im Arbeitsspeicher platzieren.

Betrachten Sie eine webbasierte Anwendung, z. B. einen Online-Store. Nachdem ein Online-Käufer den Kauf von Artikeln abgeschlossen hat, werden alle gekauften Artikel in einer XML-Datenquelle im Arbeitsspeicher abgelegt, die zum Vorausfüllen eines Formulars verwendet wird. Das folgende Diagramm zeigt diesen Vorgang, der in der Tabelle nach dem Diagramm erläutert wird.

![pf_pf_finsrv_webapp_v1](assets/pf_pf_finsrv_webapp_v1.png)

Die folgende Tabelle beschreibt die Schritte in diesem Diagramm.

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Ein Benutzer kauft Artikel in einem webbasierten Online-Store. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Nachdem der Benutzer den Kauf von Artikeln abgeschlossen und auf die Schaltfläche "Senden"geklickt hat, wird eine XML-Datenquelle im Arbeitsspeicher erstellt. Erworbene Elemente und Benutzerinformationen werden in die speicherinterne XML-Datenquelle eingefügt. </p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Die XML-Datenquelle wird zum Vorausfüllen eines Bestellformulars verwendet (ein Beispiel dieses Formulars wird in der folgenden Tabelle gezeigt). </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Das Bestellformular wird an den Client-Webbrowser gerendert. </p></td>
  </tr>
 </tbody>
</table>

Das folgende Diagramm zeigt ein Beispiel für ein Bestellformular. Die Informationen in der Tabelle können an die Anzahl der Datensätze in den XML-Daten angepasst werden.

![pf_pf_poform](assets/pf_pf_poform.png)

>[!NOTE]
>
>Ein Formular kann vorab mit Daten aus anderen Quellen wie einer Unternehmensdatenbank oder externen Anwendungen gefüllt werden.

### Überlegungen zum Formularentwurf {#form-design-considerations}

Formulare mit flexiblen Layouts basieren auf Formularentwürfen, die in Designer erstellt wurden. Ein Formularentwurf gibt einen Satz von Layout-, Präsentations- und Datenerfassungsregeln an, einschließlich der Berechnung von Werten basierend auf der Benutzereingabe. Die Regeln werden angewendet, wenn Daten in ein Formular eingegeben werden. Felder, die einem Formular hinzugefügt werden, sind Teilformulare, die sich im Formularentwurf befinden. Im Bestellformular im vorherigen Diagramm ist jede Zeile beispielsweise ein Teilformular. Informationen zum Erstellen eines Formularentwurfs mit Teilformularen finden Sie unter [Bestellformular mit flexiblem Layout](https://www.adobe.com/go/learn_aemforms_qs_poformflowable_9)erstellen.

### Datenuntergruppen {#understanding-data-subgroups}

Eine XML-Datenquelle wird zum Vorausfüllen von Formularen mit festen Layouts und flexiblen Layouts verwendet. Der Unterschied besteht jedoch darin, dass eine XML-Datenquelle, die ein Formular mit einem flexiblen Layout im Voraus ausfüllt, sich wiederholende XML-Elemente enthält, die zum Vorausfüllen von Teilformularen verwendet werden, die im Formular wiederholt werden. Diese sich wiederholenden XML-Elemente werden als Datenuntergruppen bezeichnet.

Eine XML-Datenquelle, mit der das im vorherigen Diagramm dargestellte Bestellformular im Voraus gefüllt wird, enthält vier sich wiederholende Datenuntergruppen. Jede Datenuntergruppe entspricht einem gekauften Artikel. Die gekauften Artikel sind ein Monitor, eine Schreibtischleuchte, ein Telefon und ein Adressbuch.

Die folgende XML-Datenquelle dient zum Vorausfüllen des Bestellformulars.

```as3
     <header>
         <!-- XML elements used to prepopulate non-repeating fields such as address
         <!and city
         <txtPONum>8745236985</txtPONum>
         <dtmDate>2004-02-08</dtmDate>
         <txtOrderedByCompanyName>Any Company Name</txtOrderedByCompanyName>
         <txtOrderedByAddress>555, Any Blvd.</txtOrderedByAddress>
         <txtOrderedByCity>Any City</txtOrderedByCity>
         <txtOrderedByStateProv>ST</txtOrderedByStateProv>
         <txtOrderedByZipCode>12345</txtOrderedByZipCode>
         <txtOrderedByCountry>Any Country</txtOrderedByCountry>
         <txtOrderedByPhone>(123) 456-7890</txtOrderedByPhone>
         <txtOrderedByFax>(123) 456-7899</txtOrderedByFax>
         <txtOrderedByContactName>Contact Name</txtOrderedByContactName>
         <txtDeliverToCompanyName>Any Company Name</txtDeliverToCompanyName>
         <txtDeliverToAddress>7895, Any Street</txtDeliverToAddress>
         <txtDeliverToCity>Any City</txtDeliverToCity>
         <txtDeliverToStateProv>ST</txtDeliverToStateProv>
         <txtDeliverToZipCode>12346</txtDeliverToZipCode>
         <txtDeliverToCountry>Any Country</txtDeliverToCountry>
         <txtDeliverToPhone>(123) 456-7891</txtDeliverToPhone>
         <txtDeliverToFax>(123) 456-7899</txtDeliverToFax>
         <txtDeliverToContactName>Contact Name</txtDeliverToContactName>
     </header>
     <detail>
         <!-- A data subgroup that contains information about the monitor>
         <txtPartNum>00010-100</txtPartNum>
         <txtDescription>Monitor</txtDescription>
         <numQty>1</numQty>
         <numUnitPrice>350.00</numUnitPrice>
     </detail>
     <detail>
         <!-- A data subgroup that contains information about the desk lamp>
         <txtPartNum>00010-200</txtPartNum>
         <txtDescription>Desk lamps</txtDescription>
         <numQty>3</numQty>
         <numUnitPrice>55.00</numUnitPrice>
     </detail>
     <detail>
         <!-- A data subgroup that contains information about the Phone>
             <txtPartNum>00025-275</txtPartNum>
             <txtDescription>Phone</txtDescription>
             <numQty>5</numQty>
             <numUnitPrice>85.00</numUnitPrice>
     </detail>
     <detail>
         <!-- A data subgroup that contains information about the address book>
         <txtPartNum>00300-896</txtPartNum>
         <txtDescription>Address book</txtDescription>
         <numQty>2</numQty>
         <numUnitPrice>15.00</numUnitPrice>
     </detail>
```

Beachten Sie, dass jede Datenuntergruppe vier XML-Elemente enthält, die diesen Informationen entsprechen:

* Artikelteilnummer
* Beschreibung der Elemente
* Menge der Elemente
* Stückpreis

Der Name des übergeordneten XML-Elements einer Datenuntergruppe muss mit dem Namen des Teilformulars im Formularentwurf übereinstimmen. Beachten Sie im vorherigen Diagramm beispielsweise, dass der Name des übergeordneten XML-Elements der Datenuntergruppe `detail`lautet. Dies entspricht dem Namen des Teilformulars, das sich im Formularentwurf befindet, auf dem das Bestellformular basiert. Wenn der Name des übergeordneten XML-Elements der Datenuntergruppe und das Teilformular nicht übereinstimmen, wird kein serverseitiges Formular vorausgefüllt.

Jede Datenuntergruppe muss XML-Elemente enthalten, die mit den Feldnamen im Teilformular übereinstimmen. Das `detail` Teilformular im Formularentwurf enthält die folgenden Felder:

* txtPartNum
* txtDescription
* numQty
* numUnitPrice

>[!NOTE]
>
>Wenn Sie versuchen, ein Formular mit einer Datenquelle, die sich wiederholende XML-Elemente enthält, im Voraus zu füllen, und Sie die `RenderAtClient` Option auf `No`setzen, wird nur der erste Datensatz in das Formular zusammengeführt. Um sicherzustellen, dass alle Datensätze in das Formular zusammengeführt werden, setzen Sie den `RenderAtClient` auf `Yes`. Informationen zur `RenderAtClient` Option finden Sie unter [Wiedergabe von Formularen auf dem Client](/help/forms/developing/rendering-forms-client.md).

>[!NOTE]
>
>For more information about the Forms service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um ein Formular mit einem flexiblen Layout im Voraus auszufüllen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie eine speicherinterne XML-Datenquelle.
1. Konvertieren Sie die XML-Datenquelle.
1. Wiedergabe eines vorausgefüllten Formulars

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen einer speicherinternen XML-Datenquelle**

Mithilfe von `org.w3c.dom` Klassen können Sie eine XML-Datenquelle im Arbeitsspeicher erstellen, um ein Formular mit einem flexiblen Layout im Voraus zu füllen. Sie müssen Daten in eine XML-Datenquelle einfügen, die dem Formular entspricht. Informationen zur Beziehung zwischen einem Formular mit einem flexiblen Layout und der XML-Datenquelle finden Sie unter [Grundlegendes zu Datenuntergruppen](/help/forms/developing/prepopulating-forms-flowable-layouts.md#understanding-data-subgroups).

**XML-Datenquelle konvertieren**

Eine speicherinterne XML-Datenquelle, die mithilfe von `org.w3c.dom` `com.adobe.idp.Document` Klassen erstellt wird, kann in ein Objekt konvertiert werden, bevor sie zum Vorausfüllen eines Formulars verwendet werden kann. Eine speicherinterne XML-Datenquelle kann mithilfe von Java XML-Transformationsklassen konvertiert werden.

>[!NOTE]
>
>Wenn Sie die WSDL des Forms-Dienstes zum Vorausfüllen eines Formulars verwenden, müssen Sie ein `org.w3c.dom.Document` Objekt in ein `BLOB` Objekt konvertieren.

**Vorausgefülltes Formular wiedergeben**

Sie können ein vorausgefülltes Formular wie jedes andere Formular wiedergeben. Der einzige Unterschied besteht darin, dass Sie das `com.adobe.idp.Document` Objekt, das die XML-Datenquelle enthält, zum Vorausfüllen des Formulars verwenden.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur Forms Service API](/help/forms/developing/forms-service-api-quick-starts.md#forms-service-api-quick-starts)

[Wiedergeben interaktiver PDF-Formulare](/help/forms/developing/rendering-interactive-pdf-forms.md)

[Erstellen von Webanwendungen, die Formulare wiedergeben](/help/forms/developing/creating-web-applications-renders-forms.md)

### Vorausfüllen von Formularen mit der Java-API {#prepopulating-forms-using-the-java-api}

So füllen Sie ein Formular mit einem flexiblen Layout mithilfe der Forms API (Java) im Voraus aus:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-forms-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen einer speicherinternen XML-Datenquelle

   * Erstellen Sie ein Java- `DocumentBuilderFactory` Objekt, indem Sie die `DocumentBuilderFactory` class- `newInstance` Methode aufrufen.
   * Erstellen Sie ein Java- `DocumentBuilder` Objekt, indem Sie die `DocumentBuilderFactory` Objektmethode `newDocumentBuilder` aufrufen.
   * Rufen Sie die `DocumentBuilder` Objektmethode auf, um ein `newDocument` `org.w3c.dom.Document` Objekt zu instanziieren.
   * Erstellen Sie das Stammelement der XML-Datenquelle, indem Sie die `org.w3c.dom.Document` Objektmethode `createElement` aufrufen. Dadurch wird ein `Element` Objekt erstellt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Stammelement an das Dokument an, indem Sie die `Document` Methode des `appendChild` Objekts aufrufen und das Stammelementobjekt als Argument übergeben. Die folgende Codezeile zeigt diese Anwendungslogik:

      ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Erstellen Sie das Header-Element der XML-Datenquelle, indem Sie die `Document` Objektmethode `createElement` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Header-Element an das Stammelement an, indem Sie die `root` `appendChild` Objektmethode aufrufen und das Header-Element-Objekt als Argument übergeben. Die XML-Elemente, die an das Header-Element angehängt werden, entsprechen dem statischen Teil des Formulars. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Erstellen Sie ein untergeordnetes Element, das zum Kopfzeilenelement gehört, indem Sie die `Document` `createElement` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` Methode aufrufen und die `Document` Objektmethode als `createTextNode` Argument übergeben. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Fügen Sie schließlich das untergeordnete Element an das Header-Element an, indem Sie die `appendChild` Methode des Header-Elements aufrufen und das untergeordnete Element-Objekt als Argument übergeben. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`


   * Fügen Sie alle verbleibenden Elemente zum Kopfzeilenelement hinzu, indem Sie den letzten Unterschritt für jedes Feld wiederholen, das im statischen Teil des Formulars angezeigt wird (im XML-Datenquellendiagramm werden diese Felder in Abschnitt A angezeigt). (Siehe [Datenuntergruppen](#understanding-data-subgroups).)
   * Erstellen Sie das Detail-Element der XML-Datenquelle, indem Sie die `Document` Objektmethode `createElement` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Detail-Element an das Stammelement an, indem Sie die `root` `appendChild` Objektmethode aufrufen und das Detail-Element-Objekt als Argument übergeben. Die XML-Elemente, die an das Detail-Element angehängt werden, entsprechen dem dynamischen Teil des Formulars. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Erstellen Sie ein untergeordnetes Element, das zum Detail-Element gehört, indem Sie die `Document` `createElement` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` Methode aufrufen und die `Document` Objektmethode als `createTextNode` Argument übergeben. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Fügen Sie schließlich das untergeordnete Element an das Detail-Element an, indem Sie die `appendChild` Methode des Detail-Elements aufrufen und das untergeordnete Element-Objekt als Argument übergeben. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Wiederholen Sie den letzten Unterschritt, damit alle XML-Elemente an das Detail-Element angehängt werden. Um die XML-Datenquelle, die zum Ausfüllen des Bestellformulars verwendet wird, ordnungsgemäß zu erstellen, müssen Sie die folgenden XML-Elemente an das Detail-Element anhängen: `txtDescription`, `numQty`und `numUnitPrice`.
   * Wiederholen Sie die letzten beiden Unterschritte für alle Datenelemente, die zum Vorausfüllen des Formulars verwendet werden.

1. XML-Datenquelle konvertieren

   * Erstellen Sie ein `javax.xml.transform.Transformer` Objekt, indem Sie die statische `javax.xml.transform.Transformer` Objektmethode aufrufen `newInstance` .
   * Erstellen Sie ein `Transformer` Objekt, indem Sie die `TransformerFactory` Objektmethode `newTransformer` aufrufen.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource` Objekt, indem Sie dessen Konstruktor verwenden und das in Schritt 1 erstellte `org.w3c.dom.Document` Objekt übergeben.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Füllen Sie das Java- `ByteArrayOutputStream` Objekt, indem Sie die `javax.xml.transform.Transformer` Objektmethode aufrufen und die Objekte `transform` und `javax.xml.transform.dom.DOMSource` `javax.xml.transform.stream.StreamResult` übergeben.
   * Erstellen Sie ein Bytearray und weisen Sie dem Bytearray die Größe des `ByteArrayOutputStream` Objekts zu.
   * Füllen Sie das Bytearray, indem Sie die `ByteArrayOutputStream` Objektmethode `toByteArray` aufrufen.
   * Create a `com.adobe.idp.Document` object by using its constructor and passing the byte array.

1. Vorausgefülltes Formular wiedergeben

   Rufen Sie die `FormsServiceClient` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `com.adobe.idp.Document` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Stellen Sie sicher, dass Sie das in den Schritten 1 und 2 erstellte `com.adobe.idp.Document` Objekt verwenden.
   * Ein `PDFFormRenderSpec` Objekt, das Laufzeitoptionen speichert.
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   Die `renderPDFForm` Methode gibt ein `FormsResult` Objekt zurück, das einen Formulardatenstream enthält, der in den Client-Webbrowser geschrieben werden muss.

   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Senden eines Formulardatenstreams an den Client-Webbrowser verwendet wird.
   * Erstellen Sie ein `com.adobe.idp.Document` Objekt, indem Sie die `FormsResult` &quot;s&quot;- `getOutputContent` Methode des Objekts aufrufen.
   * Erstellen Sie ein `java.io.InputStream` Objekt, indem Sie die `com.adobe.idp.Document` Objektmethode `getInputStream` aufrufen.
   * Erstellen Sie ein Byte-Array, das mit dem Formulardatenstream gefüllt wird, indem Sie die `InputStream` Objektmethode aufrufen und das Bytearray als Argument übergeben `read` .
   * Rufen Sie die `javax.servlet.ServletOutputStream` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.


**Siehe auch**

[Kurzanleitung (SOAP-Modus): Vorausfüllen von Formularen mit fließenden Layouts mit der Java-API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Vorausfüllen von Formularen mit der Webdienst-API {#prepopulating-forms-using-the-web-service-api}

So füllen Sie ein Formular mit einem flexiblen Layout mithilfe der Forms API (Webdienst) im Voraus aus:

1. Projektdateien einschließen

   * Erstellen Sie Java-Proxyklassen, die die Forms-Dienst-WSDL verwenden. (Siehe [Java-Proxyklassen mit Apache Axis](/help/forms/developing/invoking-aem-forms-using-web.md#creating-java-proxy-classes-using-apache-axis)erstellen.)
   * Schließen Sie die Java-Proxyklassen in Ihren Klassenpfad ein.

1. Erstellen einer speicherinternen XML-Datenquelle

   * Erstellen Sie ein Java- `DocumentBuilderFactory` Objekt, indem Sie die `DocumentBuilderFactory` class- `newInstance` Methode aufrufen.
   * Erstellen Sie ein Java- `DocumentBuilder` Objekt, indem Sie die `DocumentBuilderFactory` Objektmethode `newDocumentBuilder` aufrufen.
   * Rufen Sie die `DocumentBuilder` Objektmethode auf, um ein `newDocument` `org.w3c.dom.Document` Objekt zu instanziieren.
   * Erstellen Sie das Stammelement der XML-Datenquelle, indem Sie die `org.w3c.dom.Document` Objektmethode `createElement` aufrufen. Dadurch wird ein `Element` Objekt erstellt, das das Stammelement darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Stammelement an das Dokument an, indem Sie die `Document` Methode des `appendChild` Objekts aufrufen und das Stammelementobjekt als Argument übergeben. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element root = (Element)document.createElement("transaction");  document.appendChild(root);`

   * Erstellen Sie das Header-Element der XML-Datenquelle, indem Sie die `Document` Objektmethode `createElement` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Header-Element an das Stammelement an, indem Sie die `root` `appendChild` Objektmethode aufrufen und das Header-Element-Objekt als Argument übergeben. Die XML-Elemente, die an das Header-Element angehängt werden, entsprechen dem statischen Teil des Formulars. Die folgenden Codezeilen zeigen diese Anwendungslogik:

      ` Element header = (Element)document.createElement("header");  root.appendChild(header);`

   * Erstellen Sie ein untergeordnetes Element, das zum Kopfzeilenelement gehört, indem Sie die `Document` `createElement` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` Methode aufrufen und die `Document` Objektmethode als `createTextNode` Argument übergeben. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Fügen Sie schließlich das untergeordnete Element an das Header-Element an, indem Sie die `appendChild` Methode des Header-Elements aufrufen und das untergeordnete Element-Objekt als Argument übergeben. Die folgende Codezeile zeigt diese Anwendungslogik:

      ` Element poNum= (Element)document.createElement("txtPONum");  poNum.appendChild(document.createTextNode("8745236985"));  header.appendChild(LastName);`

   * Fügen Sie alle verbleibenden Elemente zum Kopfzeilenelement hinzu, indem Sie den letzten Unterschritt für jedes Feld wiederholen, das im statischen Teil des Formulars angezeigt wird (im XML-Datenquellendiagramm werden diese Felder in Abschnitt A angezeigt). (Siehe [Datenuntergruppen](#understanding-data-subgroups).)
   * Erstellen Sie das Detail-Element der XML-Datenquelle, indem Sie die `Document` Objektmethode `createElement` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Elements darstellt, an die `createElement` Methode. Wandeln Sie den Rückgabewert in `Element` um. Hängen Sie anschließend das Detail-Element an das Stammelement an, indem Sie die `root` `appendChild` Objektmethode aufrufen und das Detail-Element-Objekt als Argument übergeben. Die XML-Elemente, die an das Detail-Element angehängt werden, entsprechen dem dynamischen Teil des Formulars. Die folgende Codezeile zeigt diese Anwendungslogik:

      ` Element detail = (Element)document.createElement("detail");  root.appendChild(detail);`

   * Erstellen Sie ein untergeordnetes Element, das zum Detail-Element gehört, indem Sie die `Document` `createElement` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Namen des Elements darstellt. Wandeln Sie den Rückgabewert in `Element` um. Legen Sie anschließend einen Wert für das untergeordnete Element fest, indem Sie dessen `appendChild` Methode aufrufen und die `Document` Objektmethode als `createTextNode` Argument übergeben. Geben Sie einen Zeichenfolgenwert an, der als Wert des untergeordneten Elements angezeigt wird. Fügen Sie schließlich das untergeordnete Element an das Detail-Element an, indem Sie die `appendChild` Methode des Detail-Elements aufrufen und das untergeordnete Element-Objekt als Argument übergeben. Die folgende Codezeile zeigt diese Anwendungslogik:

      ` Element txtPartNum = (Element)document.createElement("txtPartNum");  txtPartNum.appendChild(document.createTextNode("00010-100"));  detail.appendChild(txtPartNum);`

   * Wiederholen Sie den letzten Unterschritt, damit alle XML-Elemente an das Detail-Element angehängt werden. Um die XML-Datenquelle, die zum Ausfüllen des Bestellformulars verwendet wird, ordnungsgemäß zu erstellen, müssen Sie die folgenden XML-Elemente an das Detail-Element anhängen: `txtDescription`, `numQty`und `numUnitPrice`.
   * Wiederholen Sie die letzten beiden Unterschritte für alle Datenelemente, die zum Vorausfüllen des Formulars verwendet werden.

1. XML-Datenquelle konvertieren

   * Erstellen Sie ein `javax.xml.transform.Transformer` Objekt, indem Sie die statische `javax.xml.transform.Transformer` Objektmethode aufrufen `newInstance` .
   * Erstellen Sie ein `Transformer` Objekt, indem Sie die `TransformerFactory` Objektmethode `newTransformer` aufrufen.
   * Erstellen Sie ein Objekt `ByteArrayOutputStream`, indem Sie den Konstruktor verwenden.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource` Objekt, indem Sie dessen Konstruktor verwenden und das in Schritt 1 erstellte `org.w3c.dom.Document` Objekt übergeben.
   * Erstellen Sie ein `javax.xml.transform.dom.DOMSource`-Objekt, indem Sie seinen Konstruktor verwenden und das `ByteArrayOutputStream`-Objekt übergeben.
   * Füllen Sie das Java- `ByteArrayOutputStream` Objekt, indem Sie die `javax.xml.transform.Transformer` Objektmethode aufrufen und die Objekte `transform` und `javax.xml.transform.dom.DOMSource` `javax.xml.transform.stream.StreamResult` übergeben.
   * Erstellen Sie ein Bytearray und weisen Sie dem Bytearray die Größe des `ByteArrayOutputStream` Objekts zu.
   * Füllen Sie das Bytearray, indem Sie die `ByteArrayOutputStream` Objektmethode `toByteArray` aufrufen.
   * Erstellen Sie ein `BLOB` Objekt mithilfe des Konstruktors, rufen Sie dessen `setBinaryData` Methode auf und übergeben Sie das Bytearray.

1. Vorausgefülltes Formular wiedergeben

   Rufen Sie die `FormsService` Objektmethode `renderPDFForm` auf und übergeben Sie die folgenden Werte:

   * Ein Zeichenfolgenwert, der den Namen des Formularentwurfs einschließlich der Dateinamenerweiterung angibt.
   * Ein `BLOB` Objekt, das Daten enthält, die mit dem Formular zusammengeführt werden sollen. Stellen Sie sicher, dass Sie das in den Schritten 1 und 2 erstellte `BLOB` Objekt verwenden.
   * Ein `PDFFormRenderSpecc` Objekt, das Laufzeitoptionen speichert. For more information, see [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).
   * Ein `URLSpec` Objekt, das URI-Werte enthält, die vom Forms-Dienst benötigt werden.
   * Ein `java.util.HashMap` Objekt, das Dateianlagen speichert. Dies ist ein optionaler Parameter, den Sie angeben können, `null` wenn Sie keine Dateien an das Formular anhängen möchten.
   * Ein leeres `com.adobe.idp.services.holders.BLOBHolder` Objekt, das von der Methode gefüllt wird. Auf diese Weise wird das gerenderte PDF-Formular gespeichert.
   * Ein leeres `javax.xml.rpc.holders.LongHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert die Anzahl der Seiten im Formular.)
   * Ein leeres `javax.xml.rpc.holders.StringHolder` Objekt, das von der Methode gefüllt wird. (Dieses Argument speichert den Gebietsschemawert.)
   * Ein leeres `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das die Ergebnisse dieses Vorgangs enthält.
   Die `renderPDFForm` Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

   * Erstellen Sie ein `FormResult` Objekt, indem Sie den Wert des `com.adobe.idp.services.holders.FormsResultHolder` Objektdatenelements abrufen `value` .
   * Erstellen Sie ein `BLOB` Objekt, das Formulardaten enthält, indem Sie die `FormsResult` Objektmethode `getOutputContent` aufrufen.
   * Rufen Sie den Inhaltstyp des `BLOB` Objekts ab, indem Sie dessen `getContentType` Methode aufrufen.
   * Legen Sie den Inhaltstyp des `javax.servlet.http.HttpServletResponse` Objekts fest, indem Sie seine `setContentType` Methode aufrufen und den Inhaltstyp des `BLOB` Objekts übergeben.
   * Erstellen Sie ein `javax.servlet.ServletOutputStream` Objekt, das zum Schreiben des Formulardatenstreams in den Client-Webbrowser verwendet wird, indem Sie die `javax.servlet.http.HttpServletResponse` Objektmethode `getOutputStream` aufrufen.
   * Erstellen Sie ein Bytearray und füllen Sie es durch Aufrufen der `BLOB` Objektmethode `getBinaryData` . Diese Aufgabe weist den Inhalt des `FormsResult` Objekts dem Bytearray zu.
   * Rufen Sie die `javax.servlet.http.HttpServletResponse` Methode des `write` Objekts auf, um den Formulardatenstream an den Client-Webbrowser zu senden. Übergeben Sie das Bytearray an die `write` Methode.
   >[!NOTE]
   >
   >Die `renderPDFForm` Methode füllt das `com.adobe.idp.services.holders.FormsResultHolder` Objekt, das als letzter Argumentwert übergeben wird, mit einem Formulardatenstream, der in den Client-Webbrowser geschrieben werden muss.

**Siehe auch**

[Aufrufen von AEM Forms mithilfe der Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

