---
title: Vorbefüllen von Feldern in adaptiven Formularen
seo-title: Vorbefüllen von Feldern in adaptiven Formularen
description: Verwenden Sie bestehende Daten, um die Felder eines adaptiven Formulars zu befüllen.
seo-description: Bei adaptiven Formularen können Benutzer grundlegende Informationen im Voraus in einem Formular ausfüllen, indem Sie sich mit ihrem sozialen Profil anmelden. In diesem Artikel wird beschrieben, wie Sie dies erreichen können.
uuid: 574de83a-7b5b-4a1f-ad37-b9717e5c14f1
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 7139a0e6-0e37-477c-9e0b-aa356991d040
docset: aem65
feature: Adaptive Formulare
exl-id: 29cbc330-7b3d-457e-ba4a-7ce6091f3836
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2202'
ht-degree: 74%

---

# Vorbefüllen von Feldern in adaptiven Formularen{#prefill-adaptive-form-fields}

## Einführung {#introduction}

Sie können die Felder eines adaptiven Formulars mit vorhandenen Daten vorbefüllen. Wenn ein Benutzer ein Formular öffnet, werden die Werte für diese Felder vorbefüllt. Um Daten in einem adaptiven Formular vorzufüllen, stellen Sie die Benutzerdaten als vorbefüllte XML/JSON in dem Format bereit, das der Datenstruktur zum Vorbefüllen von adaptiven Formularen entspricht.

## Struktur der Vorbefülldaten {#the-prefill-structure}

Ein adaptives Formular kann eine Mischung aus gebundenen und ungebundenen Feldern enthalten. Gebundene Felder sind Felder, die aus der Registerkarte &quot;Content Finder&quot;gezogen werden und einen nicht leeren Eigenschaftswert `bindRef` im Dialogfeld &quot;Feldbearbeitung&quot;enthalten. Ungebundene Felder werden direkt aus dem Sidekick gezogen und haben einen leeren `bindRef`-Wert.

Sie können sowohl gebundene als auch ungebundene Felder eines adaptiven Formulars vorbefüllen. Die Voreinstellungsdaten enthalten die Abschnitte „afBoundData“ und „afUnBoundData“, um sowohl gebundene als auch ungebundene Felder eines adaptiven Formulars vorzubefüllen. Der Abschnitt `afBoundData` enthält die Daten zum Vorbefüllen für gebundene Felder und Bereiche. Diese Daten müssen mit dem verknüpften Formularmodellschema konform sein:

* Bei adaptiven Formularen mit der [XFA-Formularvorlage](../../forms/using/prepopulate-adaptive-form-fields.md), muss die XML zum Vorbefüllen mit dem Datenschema der XFA-Vorlage konform sein.
* Bei adaptiven Formularen mit dem [XML-Schema](#xml-schema-af) muss die XML zum Vorbefüllen mit der Schemastruktur konform sein.
* Bei adaptiven Formularen mit dem [JSON-Schema](#json-schema-based-adaptive-forms) muss die JSON zum Vorbefüllen mit dem Schema konform sein.
* Bei adaptiven Formularen mit dem FDM-Schema muss das JSON zum Vorbefüllen mit dem FDM-Schema konform sein.
* Bei adaptiven Formularen [ohne Formularmodell](#adaptive-form-with-no-form-model) gibt es keine gebundenen Daten. Jedes Feld ist ein ungebundenes Feld und wird anhand der ungebundenen XML vorausgefüllt.

### XML-Beispielstruktur zum Vorbefüllen {#sample-prefill-xml-structure}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<afData>
  <afBoundData>
     <employeeData>
        .
     </employeeData>
  </afBoundData>

  <afUnboundData>
    <data>
      <textbox>Hello World</textbox>
         .
         .
      <numericbox>12</numericbox>
         . 
         .              
    </data>
  </afUnboundData>
</afData>
```

### JSON-Beispielstruktur zum Vorbefüllen {#sample-prefill-json-structure}

```javascript
{
   "afBoundData": {
      "employeeData": { }
   },
   "afUnboundData": {
      "data": {
         "textbox": "Hello World",
         "numericbox": "12"
      }
   }
}
```

Im Fall von gebundenen Feldern mit demselben „bindref“ oder ungebundenen Feldern mit demselben Namen, werden die im XML-Tag oder JSON-Objekt angegebenen Daten in alle Felder eingefügt. Beispielsweise werden zwei Felder in einem Formular dem Namen `textbox` in den Vorbefüllungsdaten zugeordnet. Wenn das erste Textfeldfeld „A“ enthält, wird Zur Laufzeit im zweiten Textfeld automatisch „A“ ausgefüllt. Diese Verknüpfung wird als Live-Verknüpfung von Feldern adaptiver Formulare bezeichnet.

### Adaptives Formular mit XFA-Formularvorlage {#xfa-based-af}

Die Struktur der XML zum Vorbefüllen und der gesendeten XML für XFA-basierte adaptive Formulare lautet wie folgt:

* **XML-Struktur zum Vorbefüllen**: Die XML zum Vorausfüllen für XFA-basierte adaptive Formulare muss mit dem Datenschema der XFA-Formularvorlage konform sein. Um ungebundene Felder im Voraus auszufüllen, schließen Sie die XML-Struktur zum Vorbefüllen in das Tag `/afData/afBoundData` ein.

* **Gesendete XML-Struktur**: Wenn keine XML zum Vorausfüllen verwendet wird, enthält die gesendete XML Daten für gebundene und ungebundene Felder im `afData`-Wrapper-Tag. Wenn XML zum Vorbellen verwendet wird, enthält die gesendete XML dieselbe Struktur wie die XML zum Vorbellen. Wenn die XML zum Vorbellen mit dem `afData`-Stamm-Tag beginnt, hat die Ausgabe-XML ebenfalls dasselbe Format. Wenn die XML zum Vorausfüllen nicht den `afData/afBoundData` Wrapper aufweist und stattdessen direkt aus dem Schemastamm-Tag beginnt, wie `employeeData`, beginnt die gesendete XML ebenfalls mit dem `employeeData`-Tag

Prefill-Submit-Data-ContentPackage.zip

[Abrufen ](assets/prefill-submit-data-contentpackage.zip)
von FileSample mit Vorfülldaten und gesendeten Daten

### XML-Schemabasierte adaptive Formulare  {#xml-schema-af}

Die Struktur von Prefill-XML und von eingereichten XML für adaptive Formulare, die auf XML-Schemata basieren, ist wie folgt:

* **XML-Struktur zum Vorbefüllen**: Die XML zum Vorbefüllen muss mit dem verknüpften XML-Schema konform sein. Um ungebundene Felder vorabzufüllen, umschließen Sie die vorbefüllte XML-Struktur in das Tag /afData/afBoundData
* **Gesendete XML-Struktur**: Wenn keine XML zum Vorbefüllen verwendet wird, enthält die gesendete XML Daten für gebundene und ungebundene Felder im  `afData` Wrapper-Tag. Wenn die XML zum Vorbefüllen verwendet wird, enthält die gesendete XML dieselbe Struktur wie die XML zum Vorbefüllen. Wenn die XML zum Vorbefüllen mit dem `afData`-Stamm-Tag beginnt, hat die Ausgabe-XML dasselbe Format. Wenn die XML zum Vorbefüllen nicht den `afData/afBoundData`-Wrapper aufweist und stattdessen direkt aus dem Schemastamm-Tag beginnt, wie `employeeData`, beginnt die gesendete XML ebenfalls mit dem `employeeData`-Tag.

```xml
<?xml version="1.0" encoding="utf-8" ?> 
<xs:schema targetNamespace="https://adobe.com/sample.xsd"
            xmlns="https://adobe.com/sample.xsd"
            xmlns:xs="https://www.w3.org/2001/XMLSchema">
 
    <xs:element name="sample" type="SampleType"/>
         
    <xs:complexType name="SampleType">
        <xs:sequence>
            <xs:element name="noOfProjectsAssigned" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:schema>
```

Bei Feldern, deren Modell das XML-Schema ist, werden die Daten im Tag `afBoundData` vorausgefüllt, wie in der XML-Beispieldatei unten dargestellt. Es kann zum Vorfüllen eines adaptiven Formulars mit einem oder mehreren ungebundenen Textfeldern verwendet werden.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <textbox>Ignorance is bliss :) </textbox>
    </data>
  </afUnboundData>
  <afBoundData>
    <data>
      <noOfProjectsAssigned>twelve</noOfProjectsAssigned>
    </data>
  </afBoundData>
</afData>
```

>[!NOTE]
>
>Es wird empfohlen, keine ungebundenen Felder in gebundenen Bereichen zu verwenden (Bereiche mit nicht leerem `bindRef`-Wert, der durch Ziehen von Komponenten aus dem Sidekick oder der Datenquellenregisterkarte erstellt wurde). Dies kann zu Datenverlust bei diesen ungebundenen Feldern führen. Darüber hinaus wird empfohlen, dass die Namen der Felder im Formular eindeutig sind, besonders bei ungebundenen Feldern.

#### Ein Beispiel ohne „afData“- und „afBoundData“-Wrapper {#an-example-without-afdata-and-afbounddata-wrapper}

```xml
<?xml version="1.0" encoding="UTF-8"?><config>
 <assignmentDetails descriptionOfAssignment="Some Science Project" durationOfAssignment="34" financeRelatedProject="1" name="Lisa" numberOfMentees="1"/>
 <assignmentDetails descriptionOfAssignment="Kidding, right?" durationOfAssignment="4" financeRelatedProject="1" name="House" numberOfMentees="3"/>
</config>
```

### JSON-Schemabasierte adaptive Formulare {#json-schema-based-adaptive-forms}

Für adaptive Formulare, die auf dem JSON-Schema basieren, wird im Folgenden die Struktur von vorbefüllten JSON und gesendeten JSON beschrieben. Weitere Informationen finden Sie unter[ Erstellen von adaptiven Formularen mit dem JSON-Schema](../../forms/using/adaptive-form-json-schema-form-model.md).

* **Prefill-JSON-Struktur**: Das Prefill-JSON muss mit dem verknüpften JSON-Schema konform sein. Optional kann sie in das /afData/afBoundData -Objekt eingeschlossen werden, wenn Sie auch ungebundene Felder vorab ausfüllen möchten.
* **Gesendete JSON-Struktur**: Wenn keine JSON zum Vorbefüllen verwendet wird, enthält die gesendete JSON Daten für gebundene und ungebundene Felder im afData -Wrapper-Tag. Wenn die JSON zum Vorbefüllen verwendet wird, weist die gesendete JSON dieselbe Struktur auf wie die JSON zum Vorausfüllen. Wenn die JSON zum Vorbefüllen mit dem afData-Stammobjekt beginnt, hat die JSON-Ausgabe dasselbe Format. Wenn die JSON zum Vorbefüllen nicht den afData/afBoundData -Wrapper aufweist und stattdessen direkt aus dem Schemastamm-Objekt wie dem Benutzer startet, beginnt die gesendete JSON ebenfalls mit dem Benutzerobjekt.

```json
{
    "id": "https://some.site.somewhere/entry-schema#",
    "$schema": "https://json-schema.org/draft-04/schema#",
    "type": "object",
    "properties": {
        "address": {
            "type": "object",
            "properties": { 
    "name": {
     "type": "string"
    },
    "age": {
     "type": "integer"
}}}}}
```

Bei Feldern, die das JSON-Schemamodell verwenden, sind die Daten im afBoundData-Objekt bereits vorbefüllt, wie im folgenden Beispiel-JSON gezeigt. Es kann zum Vorfüllen eines adaptiven Formulars mit einem oder mehreren ungebundenen Textfeldern verwendet werden. Nachfolgend finden Sie ein Beispiel für Daten mit dem Wrapper `afData/afBoundData` :

```json
{
  "afData": {
    "afUnboundData": {
      "data": { "textbox": "Ignorance is bliss :) " }
    },
    "afBoundData": {
      "data": { {
   "user": {
    "address": {
     "city": "Noida",
     "country": "India"
}}}}}}}
```

Nachfolgend finden Sie ein Beispiel ohne `afData/afBoundData` -Wrapper:

```json
{
 "user": {
  "address": {
   "city": "Noida",
   "country": "India"
}}}
```

>[!NOTE]
>
>Die Verwendung von ungebundenen Feldern in gebundenen Bereichen (Bereiche mit nicht-leerem bindRef, die durch Ziehen von Komponenten aus dem Sidekick oder aus der Datenquellenregisterkarte erstellt wurden) wird **nicht** empfohlen, da dies möglicherweise zu Datenverlust der ungebundenen Felder führt. Es wird empfohlen, eindeutige Feldnamen im gesamten Formular zu verwenden, insbesondere für ungebundene Felder.

### Adaptives Formular ohne Formularmodell  {#adaptive-form-with-no-form-model}

Bei adaptiven Formularen ohne Formularmodell befinden sich die Daten für alle Felder unter dem Tag `<data>` von `<afUnboundData> tag`.

Außerdem sollten Sie Folgendes beachten:

Die XML-Tags für die Benutzerdaten, die für verschiedene Felder gesendet werden, werden mit dem Namen der Felder generiert. Daher müssen die Feldnamen eindeutig sein.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <radiobutton>2</radiobutton>
      <repeatable_panel_no_form_model>
        <numericbox>12</numericbox>
      </repeatable_panel_no_form_model>
      <repeatable_panel_no_form_model>
        <numericbox>21</numericbox>
      </repeatable_panel_no_form_model>
      <checkbox>2</checkbox>
      <textbox>Nopes</textbox>
    </data>
  </afUnboundData>
  <afBoundData/>
</afData>
```

## Konfigurieren des Vorbefüllungs-Diensts mithilfe von Configuration Manager  {#configuring-prefill-service-using-configuration-manager}

Um den Vorbefüllungs-Dienst zu aktivieren, geben Sie die standardmäßige Vorbefüllungs-Dienstkonfiguration in der AEM Web-Konsolenkonfiguration an. Führen Sie die folgenden Schritte aus, um den Vorbefüllungs-Dienst zu konfigurieren:

>[!NOTE]
>
>Die Vorbefüllungs-Dienstkonfiguration ist auf adaptive Formulare, HTML5-Formulare und HTML5-Formularsätze anwendbar.

1. Öffnen Sie **[!UICONTROL Adobe Experience Manager Web Console Configuration]** mithilfe der URL:\
   https://&lt;Server>:&lt;Port>/system/console/configMgr
1. Suchen und öffnen Sie die **[!UICONTROL standardmäßige Vorbefüllungs-Dienst-Konfiguration]**.

   ![Vorab-Konfiguration](assets/prefill_config_new.png)

1. Geben Sie den Datenspeicherort oder ein regex (regulärer Ausdruck) für die **Datendateispeicherorte** ein. Beispiele für gültige Datendateispeicherorte:

   * file:///C:/Users/public/Document/Prefill/.*
   * https://localhost:8000/somesamplexmlfile.xml
   >[!NOTE]
   >
   >Standardmäßig ist das Vorbefüllen über CRX-Dateien für alle Typen von adaptiven Forms (XSD, XDP, JSON, FDM und kein Formularmodell-basiert) zulässig. Vorbefüllen ist nur mit JSON- und XML-Dateien zulässig.

1. Der Vorbefüllungs-Dienst ist jetzt für Ihr Formular konfiguriert.

   >[!NOTE]
   >
   >Das crx-Protokoll verwaltet die vorbefüllte Datensicherheit und daher ist es standardmäßig zulässig. Vorbefüllen über andere Protokolle mit dem generischen regex verursacht möglicherweise Sicherheitslücken. Geben Sie in der Konfiguration eine sichere URL-Konfiguration zum Schutz Ihrer Daten an.

## Die Besonderheit bei wiederholbaren Bereichen  {#the-curious-case-of-repeatable-panels}

Im Allgemeinen werden gebundene (aus Schema) und ungebundene Felder oder Teilformulare in demselben adaptiven Formular erstellt. Im Folgenden werden allerdings einige Ausnahmen genannt, die gelten, falls die gebundenen wiederholbar sind:

* Ungebundene wiederholbare Bereiche werden bei adaptiven Formularen mit der XFA-Formularvorlage, XSD, JSON-Schema oder dem FDM-Schema nicht unterstützt.
* Verwenden Sie keine ungebundenen Felder in gebundenen wiederholbaren Bereichen.

>[!NOTE]
>
>Generell sollten Sie keine gebundenen und ungebundenen Felder mischen, wenn sie sich in Daten schneiden, die vom Benutzer in ungebundenen Feldern eingegeben werden. Wenn möglich, sollten Sie das XML-Schema oder die XFA-Formularvorlage ändern und einen Eintrag für ungebundene Felder hinzufügen, sodass sie auch gebunden werden und ihre Daten wie andere Felder in den gesendeten Daten verfügbar sind.

## Unterstützte Protokolle zum Vorbefüllen von Benutzerdaten  {#supported-protocols-for-prefilling-user-data}

Adaptive Formulare können mit Benutzerdaten im Vorbefülldatenformat über die folgenden Protokolle vorbefüllt werden, wenn sie mit gültigem Regex konfiguriert sind:

### crx://-Protokoll  {#the-crx-protocol}

```http
https://localhost:4502/content/forms/af/xml.html?wcmmode=disabled&dataRef=crx:///tmp/fd/af/myassets/sample.xml
```

Der angegebene Knoten muss die Eigenschaft `jcr:data` aufweisen und die Daten enthalten.

### file://-Protokoll  {#the-file-protocol-nbsp}

```http
https://localhost:4502/content/forms/af/someAF.html?wcmmode=disabled&dataRef=file:///C:/Users/form-user/Downloads/somesamplexml.xml
```

Die referenzierte Datei muss sich auf demselben Server befinden.

### Das https://-Protokoll {#the-http-protocol}

```http
https://localhost:4502/content/forms/af/xml.html?wcmmode=disabled&dataRef=https://localhost:8000/somesamplexmlfile.xml
```

### Service://-Protocol {#the-service-protocol}

```http
https://localhost:4502/content/forms/af/abc.html?wcmmode=disabled&dataRef=service://[SERVICE_NAME]/[IDENTIFIER]
```

* SERVICE_NAME verweist auf den Namen des OSGI-Vorbefüllungs-Dienstes. Lesen Sie [Erstellen und Ausführen eines Vorbefüllungs-Dienstes](../../forms/using/prepopulate-adaptive-form-fields.md#create-and-run-a-prefill-service).
* BEZEICHNER bezieht sich auf alle Metadaten, die vom OSGI-Vorbefüllungs-Dienst erforderlich sind, um die Daten zum Vorbefüllen aufzurufen. Ein Bezeichner für den angemeldeten Benutzer ist ein Beispiel für die Metadaten, die verwendet werden könnten.

>[!NOTE]
>
>Die Übergabe von Authentifizierungsparametern wird nicht unterstützt.

### Festlegen des Datenattributs in slingRequest  {#setting-data-attribute-in-slingrequest}

Sie können auch das Attribut `data` in `slingRequest` festlegen, wobei das Attribut `data` eine Zeichenfolge mit XML oder JSON ist, wie im folgenden Beispielcode gezeigt (Beispiel: XML):

```javascript
<%
           String dataXML="<afData>" +
                            "<afUnboundData>" +
                                "<data>" +
                                    "<first_name>"+ "Tyler" + "</first_name>" +
                                    "<last_name>"+ "Durden " + "</last_name>" +
                                    "<gender>"+ "Male" + "</gender>" +
                                    "<location>"+ "Texas" + "</location>" +
                                    "</data>" +
                            "</afUnboundData>" +
                        "</afData>";
        slingRequest.setAttribute("data", dataXML);
%>
```

Sie können eine einfache XML- oder JSON-Zeichenfolge schreiben, die alle Ihre Daten enthält, und diese in slingRequest festlegen. Sie können dies einfach in der Renderer-JSP für jede Komponente durchführen, die Sie auf der Seite aufnehmen möchten, auf der Sie das slingRequest data-Attribut festlegen können.

Beispiel: Sie wünschen ein spezifisches Design für Ihre Seite mit einem bestimmten Kopfzeilentyp. Um dies zu erreichen, können Sie eine eigene `header.jsp` schreiben, die Sie in Ihre Seitenkomponente aufnehmen, und das `data`-Attribut festlegen.

Ein weiteres gutes Beispiel ist ein Szenario, bei dem Sie Daten bei der Anmeldung über Konten sozialer Netzwerke, wie Facebook, Twitter oder LinkedIn, vorbefüllen möchten. In diesem Fall können Sie eine einfache JSP in `header.jsp` aufnehmen, die Daten aus dem Benutzerkonto abruft und den data-Parameter festlegt.

prefill-page component.zip

[Abrufen von ](assets/prefill-page-component.zip)
FileSample prefill.jsp in Seitenkomponente

## Benutzerdefinierter AEM Forms-Vorbefüllungs-Dienst {#aem-forms-custom-prefill-service}

Sie können den benutzerdefinierten Vorbefüllungs-Dienst für die Szenarien verwenden, in denen Sie Daten aus einer vordefinierten Vorbefüllungs-Quelle lesen. Der Vorbefüllungsdienst liest Daten aus definierten Datenquellen und füllt die Felder des adaptiven Formulars mit dem Inhalt der Vorbefüllungs-Datendatei vor. Außerdem können Sie dauerhaft vorgefüllte Daten mit einem adaptiven Formular verknüpfen.

### Erstellen und Ausführen eines Vorbefüllungs-Dienstes {#create-and-run-a-prefill-service}

Der Vorbefüllungsdienst ist ein OSGi-Dienst und wird über das OSGi-Paket bereitgestellt. Sie erstellen das OSGi-Bundle, laden es hoch und installieren es in die AEM Forms-Pakete. Bevor Sie mit der Erstellung des Pakets beginnen:

* [Laden Sie das AEM Forms Client SDK herunter](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)
* Laden Sie das Textbausteinpaket herunter

* Platzieren Sie die Datendatei (Vorbefüllungsdaten) in das CRX-Repository. Sie können die Datei an einem beliebigen Ort in den Inhaltsordner des CRX-Repository platzieren. 

[Datei laden](assets/prefill-sumbit-xmlsandcontentpackage.zip)

#### Erstellen Sie einen Vorbefüllungs-Dienst {#create-a-prefill-service}

Das Bausteinpaket (Vorbefüllungs-Dienst-Beispielpaket) enthält folgende Beispielimplementierung des AEM Forms-Vorbefüllungs-Dienstes. Öffnen Sie das Bausteinpaket in einem Codeeditor. Öffnen Sie beispielsweise das Bausteinprojekt zur Bearbeitung in Eclipse. Nachdem Sie das Bausteinpaket in einem Codeeditor geöffnet haben, führen Sie die folgenden Schritte aus, um den Dienst zu erstellen.

1. Öffnen sie die Datei src\main\java\com\adobe\test\Prefill.java für die Bearbeitung.
1. Legen Sie im Code folgenden Wert fest:

   * `nodePath:` Die Knotenpfadvariable, die auf den crx-Repository-Speicherort verweist, enthält den Pfad der Daten(Vorbefüllungs)-Datei. Beispiel: /content/prefillservice.xml
   * `label:` Der Parameter „label“ gibt den Anzeigenamen des Dienstes an. Beispiel: Standard-Vorbefüllungsdienst

1. Speichern und schließen Sie die Datei `Prefill.java`.
1. Fügen Sie das Paket `AEM Forms Client SDK` zum Build-Pfad des Bausteinprojekts hinzu.
1. Kompilieren Sie das Projekt und erstellen Sie die .jar-Datei für das Paket.

#### Starten und verwenden Sie den Vorbefüllungs-Dienst  {#start-and-use-the-prefill-service}

Um den Vorbefüllungs-Dienst zu starten, laden Sie die JAR-Datei auf AEM Forms Web Console hoch und aktivieren Sie den Dienst. Jetzt wird der Dienst im adaptiven Formular-Editor angezeigt. Verknüpfen eines Vorbefüllungs-Dienstes mit einem adaptiven Formular:

1. Öffnen Sie das adaptive Formular im Forms-Editor und öffnen Sie den Bereich „Eigenschaften“ für den Formularcontainer.
1. In der Eigenschaftenkonsole navigieren Sie zu „AEM Forms Container“ > „Standard“ > „Vorbefüllungs-Dienst“.
1. Wählen Sie den Vorbefüllungsdienst und klicken Sie auf **[!UICONTROL Speichern]**. Dieser Dienst ist mit dem Formular verknüpft.

## Vorausfüllen von Daten auf Client {#prefill-at-client}

Wenn Sie ein adaptives Formular im Voraus ausfüllen, führt der AEM Forms-Server Daten mit einem adaptiven Formular zusammen und stellt das ausgefüllte Formular für Sie bereit. Standardmäßig erfolgt die Datenzusammenführung auf dem Server.

Sie können den AEM Forms-Server so konfigurieren, dass die Datenzusammenführungsaktion auf dem Client und nicht auf dem Server ausgeführt wird. Dadurch wird die zum Vorausfüllen und Rendern adaptiver Formulare erforderliche Zeit erheblich verringert. Standardmäßig ist die Funktion deaktiviert. Sie können sie über den Configuration Manager oder die Befehlszeile aktivieren.

* So aktivieren oder deaktivieren Sie im Configuration Manager:
   1. Öffnen Sie AEM Configuration Manager.
   1. Suchen und öffnen Sie die Webkanalkonfiguration für adaptive Formulare und interaktive Kommunikation
   1. Aktivieren Sie die Option Configuration.af.clientside.datamerge.enabled.name .
* So aktivieren oder deaktivieren Sie über die Befehlszeile:
   * Führen Sie zum Aktivieren den folgenden cURL-Befehl aus:
      `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=true \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

   * Führen Sie zum Deaktivieren den folgenden cURL-Befehl aus:
      `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=false \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`
   Um die Option zum Vorausfüllen der Daten auf dem Client in vollem Umfang zu nutzen, aktualisieren Sie Ihren Vorbefüllungs-Dienst, um [FileAttachmentMap](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) und [CustomContext](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) zurückzugeben.
