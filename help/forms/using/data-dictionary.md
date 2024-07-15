---
title: Datenwörterbuch
description: Mit dem Datenwörterbuch im Correspondence Management können Sie Backend-Daten als Eingaben in Briefe einfügen, um sie für die Kundenkorrespondenz zu verwenden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
exl-id: aaed75e6-8849-46a8-b986-896ad729adda
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '3842'
ht-degree: 100%

---

# Datenwörterbuch{#data-dictionary}

## Einführung {#introduction}

Mit einem Datenwörterbuch können geschäftliche Benutzerinnen und Benutzer Informationen aus Backend-Datenquellen verwenden, ohne über die technischen Details der zugrunde liegenden Datenmodelle zu verfügen. Ein Datenwörterbuch besteht aus Datenwörterbuchelementen (DDEs). Mithilfe dieser Datenelemente können Sie Backend-Daten im Rahmen der Kundenkorrespondenz in Briefe einfügen.

Ein Datenwörterbuch ist eine unabhängige Darstellung von Metadaten, die die zugrunde liegenden Datenstrukturen und die zugehörigen Attribute beschreibt. Ein Datenwörterbuch wird auf Grundlage des Geschäftsvokabulars erstellt. Es kann einem oder mehreren zugrunde liegenden Datenmodellen zugeordnet werden.

Ein Datenwörterbuch besteht aus Datenwörterbuchelementen (DDEs), von denen es drei Typen gibt: Elemente des Typs „Simple“, „Composite“ und „Collection“. Primitive-DDEs sind primitive Elemente wie Zeichenfolgen, Zahlen, Daten und boolesche Werte, die Informationen wie z. B. den Ortsnamen enthalten. Ein Composite-DDE enthält andere DDEs, die vom Typ „Primitive“, „Composite“ oder „Collection“ sein können. Das kann z. B. eine Adresse sein, die aus einer Straße, einer Stadt, einem Bezirk, einem Land und einer Postleitzahl besteht. Eine Sammlung ist eine Liste ähnlicher Simple- oder Composite-DDEs. Beispiel: eine Kundin oder ein Kunde mit mehreren Standorten oder unterschiedlichen Abrechnungs- und Versandadressen.

Das Correspondence Management verwendet Backend- sowie kunden- und empfängerspezifische Daten, die zur Erstellung unterschiedlicher Kundenkorrespondenzen gemäß der Datenwörterbuchstruktur gespeichert sind. Beispielsweise kann ein Dokument mit einer freundlichen Anrede erstellt werden, wie „Lieber {Vorname}“, „Herr“ {Nachname}&quot;.

In der Regel müssen Geschäftsbenutzer keine Kenntnisse über Metadatendarstellungen wie XSD (XML-Schema) und Java-Klassen haben. Sie müssen allerdings in der Regel Zugriff auf diese Datenstrukturen und Attribute haben, um Lösungen erstellen zu können.

### Datenwörterbuch-Workflow {#data-dictionary-workflow}

1. Eine Autorin oder ein Autor [erstellt das Datenwörterbuch](#createdatadictionary) entweder durch Hochladen eines Schemas oder von Grund auf.
1. Der Verfasser erstellt Briefe und interaktive Kommunikation auf Grundlage des Datenwörterbuchs und verknüpft gegebenenfalls Datenwörterbuchelemente in Briefen und adaptiven Dokumenten.
1. Ein Verfasser kann Beispieldaten-XML-Dateien herunterladen, die auf einem Datenwörterbuchschema basieren. Der Verfasser kann die Beispieldaten-XML-Dateien ändern, welche als Testdaten mit dem Datenwörterbuch verknüpft werden können. Diese wird während der Briefvorschau verwendet.
1. Bei der [Vorschau eines Briefs](../../forms/using/create-letter.md#p-types-of-linkage-available-for-each-of-the-fields-p) wählt ein Verfasser den Brief mit den Daten (benutzerdefinierte Vorschau). Der Brief wird mit den vom Verfasser vorbefüllten Daten geöffnet. Er wird in „Korrespondenz erstellen“ geöffnet. Der Agent, der diesen Brief in der Vorschau anzeigt, kann den Inhalt, die Daten und die Anlagen in diesem Brief ändern und den fertigen Brief übermitteln. Weitere Informationen zum Erstellen von Briefen finden Sie unter [Korrespondenz erstellen](../../forms/using/create-letter.md).

## Voraussetzung {#prerequisite}

Installieren Sie das [Kompatibilitätspaket](compatibility-package.md), um die Option **Datenwörterbücher** auf der Seite **Formulare** anzuzeigen.

## Erstellen eines Datenwörterbuchs {#createdatadictionary}

Verwenden Sie den Datenwörterbucheditor zum Erstellen eines Datenwörterbuchs oder laden Sie eine XSD-Schemadatei hoch, um ein Datenwörterbuch auf deren Grundlage zu erstellen. Anschließend können Sie das Datenwörterbuch erweitern, indem Sie weitere erforderliche Informationen hinzufügen, darunter auch Felder. Unabhängig von der Erstellung des Datenwörterbuchs benötigt die Eigentümerin bzw. der Eigentümer des Geschäftsprozesses keine Kenntnisse über die Backend-Systeme. Er muss nur über Kenntnisse zu Domain-Objekten und deren Definitionen verfügen.

>[!NOTE]
>
>Für mehrere Briefe mit ähnlichen Elementen können Sie ein gemeinsames Datenwörterbuch erstellen. Ein Wörterbuch mit großen Datenmengen und vielen Elementen kann jedoch zu Leistungsproblemen bei der Verwendung des Datenwörterbuchs und beim Laden der Elemente führen, z. B. in Briefen und Dokumentfragmenten. Wenn Leistungsprobleme auftreten, versuchen Sie, separate Datenwörterbücher für verschiedene Briefe zu erstellen.

1. Wählen Sie **Formulare** > **Datenwörterbücher**.
1. Wählen Sie **Datenwörterbuch erstellen** aus.
1. Fügen Sie im Bildschirm „Eigenschaften“ Folgendes hinzu:

   * **Titel**: (Optional) Geben Sie den Titel für das Datenwörterbuch ein. Titel müssen nicht eindeutig sein und dürfen Sonderzeichen und nicht-englische Zeichen enthalten. Briefe und andere Dokumentfragmente werden (sofern verfügbar) mit ihrem Titel referenziert, z. B. in Miniaturansichten und Asset-Eigenschaften. Datenwörterbücher werden mit ihren Namen und nicht mit Titeln referenziert.
   * **Name:** Der eindeutige Name des Datenwörterbuchs. Im Feld „Name“ können Sie nur englische Zeichen, Zahlen und Bindestriche eingeben. Das Feld „Name“ wird automatisch basierend auf dem Feld „Titel“ ausgefüllt, wobei Sonderzeichen, Leerzeichen, Zahlen und nicht-englische Zeichen aus dem Feld „Titel“ durch Bindestriche ersetzt werden. Obwohl der Wert im Feld „Titel“ automatisch in das Feld „Name“ kopiert wird, können Sie den Wert bearbeiten.

   * **Beschreibung**: (Optional) Beschreibung des Datenwörterbuchs.
   * **Tags:**(Optional) Um einen benutzerdefinierten Tag zu erstellen, geben Sie einen Wert in das Textfeld ein und drücken Sie die Eingabetaste. Sie können den Tag unterhalb des Textfeldes der Tags sehen. Wenn Sie diesen Text speichern, werden auch die neu hinzugefügten Tags erstellt.
   * **Erweiterte Eigenschaften**: (Optional) Wählen Sie **Feld hinzufügen** aus, um Metadatenattribute für Ihr Datenwörterbuch anzugeben. Geben Sie in der Spalte „Eigenschaftsname“ einen eindeutigen Namen für die Eigenschaft ein. Geben Sie in der Spalte „Wert“ einen Wert ein, der mit der Eigenschaft verknüpft werden soll.

   ![Eigenschaften des Datenwörterbuchs auf Deutsch](do-not-localize/1_ddproperties.png)

1. (Optional) Wenn Sie eine XSD-Schemadefinition für Ihr Datenwörterbuch hochladen möchten, wählen Sie im Bereich „Datenwörterbuchstruktur“ die Option **XML-Schema hochladen** aus. Navigieren Sie zu der gewünschten XSD-Datei, wählen Sie diese aus und wählen Sie dann **Öffnen**. Ein Datenwörterbuch wird basierend auf dem hochgeladenen XML-Schema erstellt. Sie müssen die Anzeigenamen und Beschreibungen der Elemente im Datenwörterbuch anpassen. Dazu müssen Sie die Namen der Elemente wählen, indem Sie darauf tippen und dann ihre Beschreibungen, Anzeigenamen und andere Details in den Feldern im rechten Bereich ändern.

   Weitere Informationen zu berechneten DD-Elementen finden Sie unter [Berechnete Datenwörterbuchelemente](#computedddelements).

   >[!NOTE]
   >
   >Sie können das Hochladen der Schemadatei überspringen und Ihr Datenwörterbuch mithilfe der Benutzeroberfläche von Grund auf erstellen. Überspringen Sie dazu diesen Schritt und fahren Sie mit den nächsten Schritten fort.

1. Wählen Sie **Weiter** aus.
1. Fügen Sie auf dem Bildschirm „Eigenschaften hinzufügen“ die Elemente zum Datenwörterbuch hinzu. Sie können auch Elemente hinzufügen/löschen und deren Details bearbeiten, wenn Sie ein Schema hochgeladen haben, um eine grundlegende Struktur des Datenwörterbuchs zu erhalten.

   Sie können die drei Punkte auf der rechten Seite eines Elements auswählen und ein Element zur Datenwörterbuchstruktur hinzufügen.

   ![1_2_createanelement](assets/1_2_createanelement.png)

   Wählen Sie entweder Composite-Element, Collection-Element oder Primitive-Element aus.

   * Ein Composite-DDE enthält andere DDEs, die vom Typ „Primitive“, „Composite“ oder „Collection“ sein können. Das kann z. B. eine Adresse sein, die aus einer Straße, einer Stadt, einem Bezirk, einem Land und einer Postleitzahl besteht.
   * Primitive-DDEs sind Primitive-Elemente wie Zeichenfolgen, Zahlen, Daten und boolesche Werte, die Informationen wie z. B. den Stadtnamen enthalten.
   * Eine Sammlung ist eine Liste ähnlicher Simple- oder Composite-DDEs. Beispiel: eine Kundin oder ein Kunde mit mehreren Standorten oder unterschiedlichen Abrechnungs- und Versandadressen.

   Nachfolgend finden Sie einige Regeln zu Erstellen eines Datenwörterbuchs:

   * Nur der Composite-Typ ist als DDE der obersten Ebene in einem Datenwörterbuch zulässig.
   * Name, Referenzname und Elementtypen sind obligatorische Felder für Datenwörterbücher und DDEs.
   * Der Referenzname muss eindeutig sein.
   * Ein übergeordnetes DDE (Composite) darf nicht zwei untergeordnete DDEs mit demselben Namen haben.
   * „Enums“ enthalten nur Primitive-Zeichenfolgentypen.

   Weitere Informationen zu Composite-, Collection- und Primitive-Elementen und zum Arbeiten mit Datenwörterbuchelementen finden Sie unter [Zuordnen von Datenwörterbuchelementen zum XML-Schema](#mappingddetoschema).

   Weitere Informationen zu Überprüfungen im Datenwörterbuch finden Sie unter [Überprüfungen des Datenwörterbucheditors](#ddvalidations).

   ![2_addddpropertiesbasic](assets/2_addddpropertiesbasic.png)

1. (Optional) Nach der Auswahl eines Elements können Sie auf der Registerkarte „Erweitert“ Eigenschaften (Attribute) hinzufügen. Sie können auch **Feld hinzufügen** auswählen und die Eigenschaften eines DD-Elements erweitern.

   ![3_addddpropertiesadvanced](assets/3_addddpropertiesadvanced.png)

1. (Optional) Sie können ein Element durch Tippen auf die drei Punkte auf der rechten Seite eines Elements und durch Auswahl von **Löschen** entfernen.

   ![4_deleteelement](assets/4_deleteelement.png)

   >[!NOTE]
   >
   >Beim Löschen eines Composite-/Collection-Elements mit untergeordneten Knoten werden auch seine untergeordneten Knoten gelöscht.

1. (Optional) Wählen Sie ein Element im Bereich „Datenwörterbuchstruktur“ und im Bereich „Feld- und Variablenliste“. Ändern Sie die dem Element zugeordneten erforderlichen Attribute oder fügen Sie welche hinzu.
1. Wählen Sie **Speichern** aus.

### Erstellen von Kopien eines oder mehrerer Datenwörterbücher {#create-copies-of-one-or-more-data-dictionary}

Um schnell ein oder mehrere Datenwörterbücher mit Eigenschaften und Elementen zu erstellen, die vorhandenen Datenwörterbüchern ähneln, können Sie sie kopieren und einfügen.

1. Wählen Sie in der Liste der Datenwörterbücher die entsprechenden Datenwörterbücher aus. Auf der Benutzeroberfläche wird das Symbol „Kopieren“ angezeigt.
1. Wählen Sie „Kopieren“. Auf der Benutzeroberfläche wird das Symbol „Einfügen“ angezeigt.
1. Wählen Sie „Einfügen“. Das Dialogfeld „Einfügen“ wird angezeigt. Das System weist den neuen Datenwörterbüchern automatisch Namen und Titel zu.
1. Bearbeiten Sie gegebenenfalls den Titel und Namen, mit dem Sie die Kopie des Datenwörterbuchs speichern möchten.
1. Wählen Sie „Einfügen“. Die Kopie des Datenwörterbuchs wird erstellt. Jetzt können Sie die erforderlichen Änderungen an Ihrem neu erstellten Datenwörterbuch vornehmen.

## Anzeigen der Dokumentfragmente oder Dokumente, die auf ein Datenwörterbuchelement verweisen {#see-the-document-fragments-or-documents-that-refer-to-a-data-dictionary-element}

Beim Bearbeiten oder Anzeigen eines Datenwörterbuchs können Sie sehen, welche Elemente im Datenwörterbuch in welchen Texten, Bedingungen, Briefen und interaktiver Kommunikation referenziert werden.

1. Führen Sie einen der folgenden Schritte aus, um das Datenwörterbuch zu bearbeiten:

   * Bewegen Sie den Mauszeiger über ein Datenwörterbuch und wählen Sie „Bearbeiten“ aus.
   * Wählen Sie ein Datenwörterbuch aus, und wählen Sie dann in der Kopfzeile „Bearbeiten“ aus.
   * Bewegen Sie den Mauszeiger über ein Datenwörterbuch und wählen Sie „Auswählen“ aus. Wählen Sie dann in der Kopfzeile „Bearbeiten“ aus.

   Oder wählen Sie ein Datenwörterbuch aus, um es anzuzeigen.

1. Wählen Sie im Datenwörterbuch ein einfaches Element aus. Composite- und Collection-Elemente haben keine Verweise.

   Zusammen mit den grundlegenden und erweiterten Eigenschaften des Elements wird auch geliehener Inhalt angezeigt.

1. Wählen Sie „Geliehener Inhalt“ aus.

   Die Registerkarte „Geliehener Inhalt“ wird mit den folgenden Elementen angezeigt: Texte, Bedingungen, Briefe und interaktive Kommunikation. Bei jeder dieser Überschriften wird auch die Anzahl der Verweise auf das ausgewählte Element angezeigt.

1. Wählen Sie eine Überschrift aus, um den Namen des Assets anzuzeigen, in dem auf das Element verwiesen wird.

   ![lentcontent](assets/lentcontent.png)

1. Um geliehenen Inhalt für ein anderes Element anzuzeigen, wählen Sie das Element aus.
1. Um ein Asset anzuzeigen, das auf ein Element verweist, wählen Sie seinen Namen aus. Das Element, der Brief oder die interaktive Kommunikation wird im Browser angezeigt.

## Arbeiten mit Testdaten {#working-with-test-data}

1. Wählen Sie auf der Seite „Datenwörterbücher“ die Option **Auswählen** aus.
1. Wählen Sie ein Datenwörterbuch, für das Sie Testdaten herunterladen möchten, und wählen Sie dann **XML-Beispieldaten herunterladen** aus.
1. Wählen Sie bei der Warnmeldung **OK** aus. Eine XML-Datei wird heruntergeladen.
1. Öffnen Sie die XML-Datei mit Notepad oder einem anderen XML-Editor. Die XML-Datei hat dieselbe Struktur wie das Datenwörterbuch und die Platzhalterzeichenfolgen in den Elementen. Ersetzen Sie die Platzhalterzeichenfolgen durch die Daten, mit denen Sie einen Brief testen möchten.

   ```xml
   <?xml version="1.0" encoding="UTF-8" standalone="no"?>
   <Company>
   <Name>string</Name>
   <Type>string</Type>
   <HeadOfficeAddress>
   <Street>string</Street>
   <City>string</City>
   <State>string</State>
   <Zip>string</Zip>
   </HeadOfficeAddress>
   <SalesOfficeAddress>
   <Street>string</Street>
   <City>string</City>
   <State>string</State>
   <Zip>string</Zip>
   </SalesOfficeAddress>
   <HeadCount>1.0</HeadCount>
   <CEO>
   <PersonName>
   <FirstName>string</FirstName>
   <MiddleName>string</MiddleName>
   <LastName>string</LastName>
   </PersonName>
   <DOB>string</DOB>
   <CurrAddress>
   <Street>string</Street>
   <City>string</City>
   <State>string</State>
   <Zip>string</Zip>
   </CurrAddress>
   <DOJ>14-04-1973</DOJ>
   <Phone>1.0</Phone>
   </CEO>
   </Company>
   ```

   >[!NOTE]
   >
   >In diesem Beispiel erstellt XML Platz für drei Werte für ein Collection-Element, aber die Anzahl der Werte kann je nach Anforderung reduziert bzw. erhöht werden.

1. Nachdem die Dateneinträge vorgenommen wurden, können Sie diese XML-Datei verwenden, wenn Sie einen Brief mit Testdaten in der Vorschau anzeigen.

   Sie können diese Testdaten mit DD hinzufügen (wählen Sie „DD“ und „Testdaten hochladen“ aus und laden Sie diese XML-Datei hoch)
Wenn Sie danach den Brief normal in der Vorschau anzeigen (nicht benutzerdefiniert), werden diese XML-Daten in dem Brief verwendet. Sie können auch „Benutzerdefiniert“ auswählen und dann diese XML-Datei hochladen.

## Stichproben {#samples}

Die folgenden Code-Beispiele zeigen Implementierungsdetails für das Datenwörterbuch.

### Beispielschema, das in das Datenwörterbuch hochgeladen werden kann {#sample-schema-that-can-be-uploaded-to-the-data-dictionary}

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns="DCT" targetNamespace="DCT" xmlns:xs="https://www.w3.org/2001/XMLSchema"
  elementFormDefault="qualified" attributeFormDefault="unqualified">
  <xs:element name="Company">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name" type="xs:string"/>
        <xs:element name="Type" type="xs:anySimpleType"/>
        <xs:element name="HeadOfficeAddress" type="Address"/>
        <xs:element name="SalesOfficeAddress" type="Address" minOccurs="0"/>
        <xs:element name="HeadCount" type="xs:integer"/>
        <xs:element name="CEO" type="Employee"/>
        <xs:element name="Workers" type="Employee" maxOccurs="unbounded"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
  <xs:complexType name="Employee">
    <xs:complexContent>
      <xs:extension  base="Person">
        <xs:sequence>
          <xs:element name="CurrAddress" type="Address"/>
          <xs:element name="DOJ" type="xs:date"/>
          <xs:element name="Phone" type="xs:integer"/>
        </xs:sequence>
      </xs:extension>
    </xs:complexContent>
  </xs:complexType>
  <xs:complexType name="Person">
    <xs:sequence>
      <xs:element name="PersonName" type="Name"/>
      <xs:element name="DOB" type="xs:dateTime"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="Name">
    <xs:sequence>
      <xs:element name="FirstName" type="xs:string"/>
      <xs:element name="MiddleName" type="xs:string"/>
      <xs:element name="LastName" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="Address">
    <xs:sequence>
      <xs:element name="Street" type="xs:string"/>
      <xs:element name="City" type="xs:string"/>
      <xs:element name="State" type="xs:string"/>
      <xs:element name="Zip" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```

## Allgemeine Attribute, die mit einem DDE verknüpft sind {#common-attributes-associated-with-a-dde}

In der folgenden Tabelle sind die allgemeinen Attribute aufgeführt, die mit einem DDE verknüpft sind:

<table>
 <tbody>
  <tr>
   <td><strong>Attribut</strong></td>
   <td><strong>Typ</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Name</td>
   <td>Zeichenfolge</td>
   <td>Erforderlich.<br /> Name des DDEs. Er muss eindeutig sein.</td>
  </tr>
  <tr>
   <td>Referenzname<br /></td>
   <td>Zeichenfolge</td>
   <td>Erforderlich. Eindeutiger Referenzname für das DDE, der Verweise auf das DDE ermöglicht, die unabhängig von Hierarchie- oder Strukturänderungen des Datenwörterbuchs sind. Textmodule werden mit diesem Namen zugeordnet</td>
  </tr>
  <tr>
   <td>displayName</td>
   <td>Zeichenfolge</td>
   <td>Ein optionaler benutzerfreundlicher Name des DDEs.</td>
  </tr>
  <tr>
   <td>description</td>
   <td>Zeichenfolge</td>
   <td>Beschreibung des DDEs.</td>
  </tr>
  <tr>
   <td>elementType</td>
   <td>Zeichenfolge</td>
   <td>Erforderlich. Der Typ des DDEs: STRING, NUMBER, DATE, BOOLEAN, COMPOSITE, COLLECTION.</td>
  </tr>
  <tr>
   <td>elementSubType</td>
   <td>Zeichenfolge</td>
   <td>Der Untertyp für DDE: ENUM. Nur für elementType STRING und NUMBER zulässig.</td>
  </tr>
  <tr>
   <td>Schlüssel</td>
   <td>Boolesch</td>
   <td>Ein boolesches Feld, das angibt, ob ein DDE ein Schlüsselelement ist.</td>
  </tr>
  <tr>
   <td>Berechnet</td>
   <td>Boolesch</td>
   <td>Ein boolesches Feld, das angibt, ob ein DDE berechnet wird. Ein berechneter DDE-Wert ist eine Funktion anderer DDE-Werte. JSP-Ausdrücke werden standardmäßig unterstützt.</td>
  </tr>
  <tr>
   <td>Ausdruck</td>
   <td>Zeichenfolge</td>
   <td>Der Ausdruck für das „berechnete“ DDE. Der standardmäßig versandte Ausdrucksauswertungsdienst unterstützt JSP-EL-Ausdrücke. Sie können den Ausdrucksdienst durch eine benutzerdefinierte Implementierung ersetzen.</td>
  </tr>
  <tr>
   <td>valueSet</td>
   <td>Liste</td>
   <td>Ein Satz zulässiger Werte für ein DDE vom Typ „Enum“. Beispielsweise kann der Kontotyp nur Werte (Speichern, Aktuell) enthalten.</td>
  </tr>
  <tr>
   <td>extendedProperties</td>
   <td>Object</td>
   <td>Eine Zuordnung von benutzerdefinierten Eigenschaften, die dem DDE hinzugefügt wurden (benutzeroberflächenspezifische oder andere Informationen).</td>
  </tr>
  <tr>
   <td>Erforderlich</td>
   <td>Boolesch</td>
   <td>Die Markierung gibt an, dass die dem Datenwörterbuch entsprechende Quelle von Instanzdaten den Wert dieses speziellen DDEs enthalten muss.</td>
  </tr>
  <tr>
   <td>Bindung</td>
   <td>BindingElement</td>
   <td>Die XML- oder Java-Bindung des Elements.</td>
  </tr>
 </tbody>
</table>

### Berechnete Datenwörterbuchelemente {#computedddelements}

Ein Datenwörterbuch kann auch berechnete Elemente enthalten. Ein berechnetes Datenwörterbuchelement ist immer mit einem Ausdruck verknüpft. Der Ausdruck wird geprüft, um den Wert eines Datenwörterbuchelements zur Laufzeit abzurufen. Ein berechneter DDE-Wert ist eine Funktion anderer DDE-Werte oder -Literale. Standardmäßig werden JSP Expression Language(EL)-Ausdrücke unterstützt. Die EL-Ausdrücke verwenden ${ }-Zeichen, und gültige Ausdrücke können Literale, Operatoren, Variablen (Datenwörterbuchelement-Verweise) und Funktionsaufrufe enthalten. Beim Verweisen auf ein Datenwörterbuchelement im Ausdruck wird der DDE-Verweisname verwendet. Der Verweisname ist für jedes Datenwörterbuchelement in einem Datenwörterbuch eindeutig.

Ein berechneter DDE PersonFullName kann mit einem EL-Verkettungsausdruck wie „${PersonFirstName} ${PersonLastName}“ verknüpft werden.

## Datentypzuordnung zwischen XSD und Datenwörterbuch {#data-type-mapping-between-xsd-and-data-dictionary-br}

Das Exportieren einer XSD-Datei erfordert eine bestimmte Datenzuordnung, die in der folgenden Tabelle aufgeführt ist. Die DDI-Spalte gibt den Typ des DDE-Werts an, wie er in der DDI verfügbar ist.

<table>
 <tbody>
  <tr>
   <td>XSD <br /> </td>
   <td><p>Datenwörterbuch <br /> </p> </td>
   <td>DDI (Datentyp des Instanzwerts)<br /> </p> </td>
  </tr>
  <tr>
   <td><p>xs:element des Typs „Composite“<br /> </p> </td>
   <td>DDE des Typs COMPOSITE<br /> </p> </td>
   <td>java.util.Map<br /> </td>
  </tr>
  <tr>
   <td><p>xs:element, wobei maxOccurs &gt; 1<br /> </p> </td>
   <td>DDE des Typs COLLECTION <br /> Ein DDE-Knoten wird neben dem COLLECTION-DDE erstellt, das Informationen aus dem übergeordneten COLLECTION-Knoten erfasst. Derselbe Knoten wird für die Collection der Simple-/Composite-Datentypen erstellt. Bei einer COLLECTION des Typs „Composite“ erfasst die Baumstruktur des Datenwörterbuchs die einzelnen Felder in den untergeordneten Elementen des DDE, die zum Erfassen von Typinformationen erstellt wurden.<br /> – DDE (COLLECTION)<br /> – DDE(COMPOSITE für Typinfo)<br /> – DDE(STRING) field1<br /> – DDE(STRING) field2<br /> <br /> </p> </td>
   <td>java.util.List<br /> </td>
  </tr>
  <tr>
   <td>Attribut des Typs „xs:ID“ <br /> </p> </td>
   <td>DDE des Typs STRING <br /> </td>
   <td>java.lang.String<br /> </td>
  </tr>
  <tr>
   <td>xs:attribute/xs:element des Typs „xs:string“</p> </td>
   <td>DDE des Typs STRING<br /> </td>
   <td>java.lang.String<br /> </td>
  </tr>
  <tr>
   <td>xs:attribute/xs:element des Typs „xs: boolean“ <br />  </td>
   <td>DDE des Typs „Boolean“ <br />  </td>
   <td>java.lang.Boolean<br /> </td>
  </tr>
  <tr>
   <td>xs:attribute/xs:element des Typs „xs:date“  </td>
   <td>DDE des Typs DATE </td>
   <td>java.lang.String</td>
  </tr>
  <tr>
   <td>xs:attribute/xs:element des Typs „xs:integer“  </td>
   <td>DDE des Typs NUMBER </td>
   <td>java.lang.Double</td>
  </tr>
  <tr>
   <td>xs:attribute /xs:element des Typs „xs:long“</td>
   <td>DDE des Typs NUMBER </td>
   <td>java.lang.Double</td>
  </tr>
  <tr>
   <td>xs:attribute /xs:element des Typs „xs:double“</td>
   <td>DDE des Typs NUMBER </td>
   <td>java.lang.Double</td>
  </tr>
  <tr>
   <td>Element des Typs „Enum“ und „baseType“ – xs:string</td>
   <td>DDE des<br /> Typs - STRING<br /> subtype - ENUM<br /> valueSet - der zulässige Wert für ENUM<br /> </td>
   <td>java.lang.String</td>
  </tr>
 </tbody>
</table>

## Herunterladen einer Beispieldatendatei aus einem Datenwörterbuch {#download-a-sample-data-file-from-a-data-dictionary}

Nachdem Sie ein Datenwörterbuch erstellt haben, können Sie es in eine XML-Beispieldatendatei herunterladen, um darin Texteinträge vorzunehmen.

1. Wählen Sie auf der Seite „Datenwörterbücher“ **Auswählen** und dann ein Datenwörterbuch aus.
1. Wählen Sie **XML-Beispieldaten herunterladen**. 
1. Wählen Sie in der Warnmeldung **OK** aus.

   Das Correspondence Management erstellt eine XML-Datei, die auf der ausgewählten Datenwörterbuchstruktur basiert, und lädt sie auf Ihren Computer mit dem Namen &lt;datenwörterbuchname>-SampleData herunter. Jetzt können Sie diese Datei in einem XML- oder einem Texteditor bearbeiten, um beim [Erstellen eines Briefs](../../forms/using/create-letter.md) Dateneinträge vorzunehmen.

## Internationalisierung von Metadaten {#internationalization-of-meta-data}

Wenn Sie denselben Brief in verschiedenen Sprachen senden möchten, können Sie den Anzeigenamen, die Beschreibung und die Enum-Wertsätze des Datenwörterbuchs und der Datenwörterbuchelemente lokalisieren.

### Datenwörterbuch lokalisieren {#localize-data-dictionary}

1. Wählen Sie auf der Seite „Datenwörterbücher“ die Option **Auswählen** und dann ein Datenwörterbuch aus.
1. Wählen Sie **Lokalisierungsdaten herunterladen** aus. 
1. Wählen Sie bei der Warnmeldung **OK** aus. Correspondence Management lädt eine ZIP-Datei auf Ihrem Computer mit dem Namen DataDictionary-&lt;DDname>.zip herunter.
1. Die ZIP-Datei enthält eine Datei des Typs „.properties“. Diese Datei definiert das heruntergeladene Datenwörterbuch. Der Inhalt der Eigenschaftsdatei ähnelt dem folgenden:

   ```ini
   #Wed May 20 16:06:23 BST 2015
   DataDictionary.EmployeeDD.description=
   DataDictionary.EmployeeDD.displayName=EmployeeDataDictionary
   DataDictionaryElement.name.description=
   DataDictionaryElement.name.displayName=name
   DataDictionaryElement.person.description=
   DataDictionaryElement.person.displayName=person
   ```

   In der Struktur der Eigenschaftsdatei ist jeweils eine Zeile für die Beschreibung und den Anzeigenamen des Datenwörterbuchs sowie jedes Datenwörterbuchelements im Datenwörterbuch definiert. Darüber hinaus ist in der Eigenschaftsdatei jeweils eine Zeile für einen Enum-Wertsatz jedes Datenwörterbuchelements definiert. Wie ein Datenwörterbuch kann auch die entsprechende Eigenschaftsdatei über mehrere Datenwörterbuchelement-Definitionen verfügen. Zudem kann die Datei die Definitionen für einen oder mehrere Enum-Wertsätze enthalten.

1. Um die Eigenschaftsdatei in ein anderes Gebietsschema zu ändern, aktualisieren Sie Werte für den Anzeigenamen und die Beschreibung in der Datei. Erstellen Sie weitere Instanzen der Datei für jede Sprache, die Sie lokalisieren wollen. Nur Französisch, Deutsch, Japanisch und Englisch werden unterstützt.

1. Speichern Sie die verschiedenen aktualisierten Eigenschaftsdateien unter den folgenden Namen:

   _fr_FR.properties Französisch

   _de_DE.properties Deutsch

   _ja_JA.properties Japanisch

   _en_EN.properties Englisch

1. Archivieren Sie die .properties-Datei (oder bei mehreren Gebietsschemas die Dateien) in einer einzelnen ZIP-Datei.

1. Wählen Sie auf der Seite „Datenwörterbuch“ **Mehr** > **Lokalisierungsdaten hochladen** und wählen Sie die ZIP-Datei mit lokalisierten Eigenschaftendateien.
1. Um die durch die Lokalisierung vorgenommenen Änderungen anzuzeigen, ändern Sie das Gebietsschema des Browsers.

## Validierungen für Datenwörterbücher {#ddvalidations}

Der Datenwörterbucheditor erzwingt folgende Validierungen beim Erstellen oder Aktualisieren eines Datenwörterbuchs.

* Nur der Composite-Typ ist als Element der obersten Ebene in einem Datenwörterbuch zulässig.
* Composite- und Collection-Elemente sind auf Blattebene nicht zulässig. Nur Primitive-Elemente (String, Date, Number, Boolean) sind auf Blattebene zulässig. Diese Validierung stellt sicher, dass es keine Composite- oder Collection-Elemente ohne untergeordnetes DDE gibt.
* Beim Hochladen von XSD-Dateien zum Erstellen eines Datenwörterbuchs fordert der Datenwörterbucheditor ein Element der obersten Ebene an, wenn mehrere Elemente vorhanden sind.
* Der Name ist der einzige erforderliche Parameter für ein Datenwörterbuch.
* Ein übergeordnetes DDE (Composite) darf nicht zwei untergeordnete DDEs mit demselben Namen haben.
* Stellt sicher, dass ein DDE nur als „berechnet“ gekennzeichnet ist, wenn es sich nicht um einen erforderlichen Parameter handelt. Ein erforderliches Element kann nicht berechnet werden und ein berechnetes Element kann nicht erforderlich sein. Außerdem dürfen Collection- und Composite-Elemente keine berechneten Elemente sein.
* Stellt sicher, dass ein DDE nur als „erforderlich“ gekennzeichnet ist, wenn es nicht berechnet wird. Außerdem wird sichergestellt, dass es sich nicht um das „collectionElement“ handelt, das den Collection-Typ (die einzigen untergeordneten Elemente eines Collection-Elements) angibt.
* Leere oder duplizierte Schlüssel sind in den erweiterten Eigenschaften für ein Datenwörterbuch oder DDE nicht zulässig.
* Verwenden Sie keinen Doppelpunkt (:) oder senkrechten Strich (|) im Schlüssel oder Wert einer erweiterten Eigenschaft. Es gibt keine Validierung für die Verwendung dieser unzulässigen Zeichen.

Auf Datenwörterbuchebene angewendete Validierungen

* Der Name des Datenwörterbuchs darf nicht null sein.
* Der Name des Datenwörterbuchs darf nur alphanumerische Zeichen enthalten.
* Die Liste der untergeordneten Elemente im Datenwörterbuch darf nicht null oder leer sein.
* Das Datenwörterbuch darf nicht mehr als ein Datenwörterbuchelement der obersten Ebene enthalten.
* Nur der Composite-Typ ist als Element der obersten Ebene in einem Datenwörterbuch zulässig.

Validierungen, die auf der Ebene der Datenwörterbuchelemente angewendet werden

* Ein DDE-Name darf nicht null sein oder Leerzeichen enthalten.
* Alle DDEs müssen über einen Elementtyp „nicht null“ verfügen.
* Ein DDE-Verweisname darf nicht null sein.
* Alle DDE-Verweisnamen müssen eindeutig sein.
* Alle DDE-Verweise dürfen nur alphanumerische Zeichen und „_“ enthalten.
* Alle DDE-Anzeigenamen dürfen nur alphanumerische Zeichen und „_“ enthalten.
* Composite- und Collection-Elemente sind auf Blattebene nicht zulässig. Nur Primitive-Elemente (String, Date, Number, Boolean) sind auf Blattebene zulässig. Diese Validierung stellt sicher, dass es keine Composite- oder Collection-Elemente ohne untergeordnetes DDE gibt.
* Ein übergeordnetes DDE des Typs „Composite“ darf nicht zwei untergeordnete Elemente mit demselben Namen enthalten.
* Der ENUM-Subtyp wird nur für String- und Number-Elemente verwendet.
* Collection- und Composite-Elemente können nicht berechnet werden.
* Ein DDE kann nicht gleichzeitig berechnet und erforderlich sein.
* Berechnete DDEs müssen einen gültigen Ausdruck enthalten.
* Berechnete DDEs dürfen keine XML-Bindung haben.
* Ein DDE, das den Typ für ein Collection-DDE angibt, kann nicht berechnet oder erforderlich sein.
* DDEs des ENUM-Subtyps dürfen keine Wertsätze enthalten, die null oder leer sind.
* Die XML-Bindung eines Collection-DDE darf nicht einem Attribut zugeordnet sein.
* Die XML-Bindungssyntax muss gültig sein, z. B. darf nur ein @-Zeichen vorhanden sein. Dieses Zeichen ist nur zulässig, wenn danach ein Attributname steht.

## Zuordnen von Datenwörterbuchelementen zum XML-Schema {#mappingddetoschema}

Sie können ein Datenwörterbuch aus einem XML-Schema erstellen oder es mithilfe der Datenwörterbuch-Benutzeroberfläche erstellen. Alle Datenwörterbuchelemente (Data Dictionary Elements, DDEs) innerhalb eines Datenwörterbuchs verfügen über ein XML-Bindungsfeld, um die Bindung des DDE an ein Element im XML-Schema zu speichern. Die Bindung in jedem DDE ist relativ zum übergeordneten DDE.

Im Folgenden sind Beispielmodelle und Codebeispiele aufgelistet, die Implementierungsdetails für das Datenwörterbuch zeigen.

## Zuordnen einfacher (Primitive-)Elemente {#mapping-simple-primitive-elements}

Ein Primitive-DDE stellt ein atomisches Feld oder ein Attribut dar. Primitive-DDEs, die außerhalb eines komplexen Typs (Composite-DDE) definiert werden, oder sich wiederholende Elemente (Collection-DDE) können an einem beliebigen Speicherort im XML-Schema gespeichert werden. Der Speicherort der Daten, die einem Primitive-DDE entsprechen, hängt nicht von der Zuordnung seines übergeordneten DDE ab. Ein Primitive-DDE verwendet Zuordnungsinformationen aus dem XML-Bindungsfeld, um seinen Wert zu bestimmen, und bei den Zuordnungen kann es sich um eine der folgenden Möglichkeiten handeln:

* ein Attribut
* ein Element
* ein Textkontext
* nichts (ein ignoriertes DDE)

Das nachstehende Beispiel zeigt ein einfaches Schema.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="https://www.w3.org/2001/XMLSchema">
  <xs:element name='age' type='integer'/>
  <xs:element name='price' type='decimal'/>
</xs:schema>
```

| **Datenwörterbuchelement** | **XML-Standardbindung** |
|---|---|
| Alter | /Alter |
| Preis | /Preis |

### Zuordnen von Composite-Elementen {#mapping-composite-elements}

Bindungen werden für Composite-Elemente nicht unterstützt. Eine bereitgestellte Bindung wird ignoriert. Die Bindung für alle untergeordneten DDEs des Primitive-Typs muss absolut sein. Eine absolute Zuordnung für untergeordnete Elemente eines Composite-DDE zuzulassen, bietet mehr Flexibilität bei der XPath-Bindung. Die Zuordnung eines Composite-DDE zu einem komplexen Elementtyp im XML-Schema schränkt den Bindungsumfang für die zugehörigen untergeordneten Elemente ein.

Im folgenden Beispiel wird das Schema für eine Anmerkung gezeigt.

```xml
<xs:element name="note">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="to" type="xs:string"/>
            <xs:element name="from" type="xs:string"/>
            <xs:element name="heading" type="xs:string"/>
            <xs:element name="body" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```

<table>
 <tbody>
  <tr>
   <td><strong>Datenwörterbuchelement</strong></td>
   <td><strong>XML-Standardbindung</strong></td>
  </tr>
  <tr>
   <td>Hinweis</td>
   <td>empty(null)<br /> </td>
  </tr>
  <tr>
   <td>in</td>
   <td>/note/to</td>
  </tr>
  <tr>
   <td>von</td>
   <td>/note/from</td>
  </tr>
  <tr>
   <td>Überschrift</td>
   <td>/note/heading</td>
  </tr>
  <tr>
   <td>body</td>
   <td>/note/body</td>
  </tr>
 </tbody>
</table>

### Zuordnen von Collection-Elementen {#mapping-collection-elements}

Ein Collection-Element wird nur einem anderen Collection-Element zugeordnet, das eine Kardinalität von > 1 aufweist.  Die untergeordneten DDEs eines Collection-DDE verfügen über eine relative (lokale) XML-Bindung in Bezug auf ihre übergeordnete XML-Bindung.  Da die untergeordneten DDEs eines Collection-Elements dieselbe Kardinalität wie das übergeordnete Element aufweisen müssen, ist die relative Bindung notwendig, um sicherzustellen, dass die Kardinalitätseinschränkungen derart sind, dass die untergeordneten DDEs nicht auf ein nicht wiederholtes XML-Schemaelement verweisen.  Im nachfolgenden Beispiel muss die Kardinalität von „TokenID“ dieselbe sein wie die von „Tokens“, dem übergeordneten Collection-DDE.

Beim Zuordnen eines Collection DDE zu einem XML-Schema muss Folgendes beachtet werden:

* Die Bindung für das DDE, das dem Collection-Element entspricht, muss der absolute XPfad sein

* Es sollte keine Bindung für das DDE, das den Typ des Collection-Elements darstellt, angegeben werden.  Wenn eine Bindung angegeben wird, wird sie ignoriert.

* Die Bindung für alle untergeordneten DDEs muss relativ zum übergeordneten Collection-Element sein.

Im folgenden XML-Schema wird ein Element mit dem Namen „Tokens“ und ein Attribut „maxOccurs“ mit „unbounded“ gezeigt. Daher ist „Tokens“ ein Collection-Element.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Tokens>
    <TokenID>string</TokenID>
    <TokenText>
      <TextHeading>string</TextHeading>
      <TextBody>string</TextBody>
    </TokenText>
  </Tokens>
  <Tokens>
    <TokenID>string</TokenID>
    <TokenText>
      <TextHeading>string</TextHeading>
      <TextBody>string</TextBody>
    </TokenText>
  </Tokens>
  <Tokens>
    <TokenID>string</TokenID>
    <TokenText>
      <TextHeading>string</TextHeading>
      <TextBody>string</TextBody>
    </TokenText>
  </Tokens>
</Root>
```

Die mit diesem Beispiel verknüpfte „Token.xsd“ lautet wie folgt:

```xml
<xs:element name="Root">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="Tokens" type="TokenType" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>

<xs:complexType name="TokenType">
  <xs:sequence>
    <xs:element name="TokenID" type="xs:string"/>
    <xs:element name="TokenText">
      <xs:complexType>
        <xs:sequence>
          <xs:element name="TextHeading" type="xs:string"/>
          <xs:element name="TextBody" type="xs:string"/>
        </xs:sequence>
      </xs:complexType>
    </xs:element>
  </xs:sequence>
</xs:complexType>
```

| **Datenwörterbuchelement** | **XML-Standardbindung** |
|---|---|
| Stamm | empty(null) |
| Tokens | /Root/Tokens |
| Composite | empty(null) |
| TokenID | TokenID |
| TokenText | empty(null) |
| TokenHeading | TokenText/TextHeading |
| TokenBody | TokenText/TextBody |
