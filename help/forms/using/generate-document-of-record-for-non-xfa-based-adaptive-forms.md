---
title: Generierung eines Datensatzdokuments für adaptive Formulare
seo-title: Generierung eines Datensatzdokuments für adaptive Formulare
description: Sie erfahren in diesem Artikel, wie Sie eine Vorlage für ein Datensatzdokument (DoR, Document of Record) für adaptive Formulare erstellen können.
seo-description: Sie erfahren in diesem Artikel, wie Sie eine Vorlage für ein Datensatzdokument (DoR, Document of Record) für adaptive Formulare erstellen können.
uuid: 2dc7e0de-fff9-43fa-9426-e9b047eb2595
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ce65cb5f-94ec-4423-9fa9-d617e9703091
docset: aem65
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2665'
ht-degree: 68%

---


# Generierung eines Datensatzdokuments für adaptive Formulare{#generate-document-of-record-for-adaptive-forms}

## Überblick {#overview}

Nachdem Ihre Kunden ein Formular übermittelt haben, möchten sie im Allgemeinen in gedruckter Form oder im Dokumentformat Aufzeichnungen über die eingegebenen Informationen behalten, um später darauf zurückzukommen. Dies wird als Datensatzdokument bezeichnet.

Sie erfahren in diesem Artikel, wie Sie ein Datensatzdokument für adaptive Formulare erstellen können.

>[!NOTE]
>
>Die automatische Generierung von Dokument aus Datensatz wird für XFA-basierte adaptive Formulare nicht unterstützt. Sie können jedoch XDP verwenden, um das adaptive Formular als Datensatzdokument zu erstellen.

## Typen adaptiver Formulare und ihre Datensatzdokumente {#adaptive-form-types-and-their-documents-of-record}

Beim Erstellen eines adaptiven Formulars können Sie ein Formularmodell auswählen. Ihre Optionen sind:

* [Formularvorlagen](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template) Sie können eine XFA-Vorlage für Ihr adaptives Formular auswählen. Wenn Sie eine XFA-Vorlage auswählen, können Sie die zugehörige XDP-Datei wie oben beschrieben zum Dokument des Datensatzes verwenden.

* [XML-Schema](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema) Sie können eine XML-Schemadefinition für Ihr adaptives Formular auswählen. Wenn Sie ein XML-Schema für Ihr adaptives Formular auswählen, können Sie Folgendes tun:

   * XFA-Vorlage für Datensatzdokument verknüpfen. Vergewissern Sie sich, dass die verknüpfte XFA-Vorlage dasselbe XML-Schema verwendet wie Ihr adaptives Formular.
   * Dokument aus Datensatz automatisch generieren

* Mit der Option „Ohne“ können Sie ein adaptives Formular ohne Formularmodell erstellen. Das Dokument des Datensatzes wird automatisch für Ihr adaptives Formular generiert.

Wenn Sie ein Formularmodell auswählen, konfigurieren Sie das Dokument des Datensatzes mit den Optionen, die unter Dokument der Konfiguration der Datensatzvorlage verfügbar sind. Siehe [Dokument der Konfiguration der Datensatzvorlage](#document-of-record-template-configuration).

## Automatisch generiertes Datensatzdokument {#automatically-generated-document-of-record}

Dank Datensatzdokument erhalten Ihre Kunden eine Kopie des übermittelten Formulars zum Ausdrucken. Wenn Sie automatisch ein Dokument aus Datensatz generieren, wird das Dokument des Datensatzes bei jeder Formularänderung sofort aktualisiert. Beispiel: Sie entfernen das Altersfeld für Kunden, die als Land die USA auswählen. Wenn diese Kunden ein Datensatzdokument erstellen, ist das Altersfeld im Datensatzdokument nicht sichtbar.

Das automatisch generierte Dokument des Datensatzes hat folgende Vorteile:

* Es führt die Datenbindung durch.
* Es blendet automatisch Felder aus, die zum Zeitpunkt der Übermittlung vom Dokument des Datensatzes ausgeschlossen sind. Es ist kein zusätzlicher Aufwand erforderlich.
* Dadurch sparen Sie Zeit, um Dokument der Datensatzvorlage zu entwerfen.
* Außerdem können Sie mithilfe der verschiedenen Vorlagen auch Stil und Erscheinungsbild wechseln dadurch für Ihr Datensatzdokument optimal anpassen. Der Stil ist optional. Wenn Sie sich auf keinen Stil festlegen, werden Systemstile als Standard festgelegt.
* Es stellt sicher, dass eine Änderung im Formular sofort im Datensatzdokument umgesetzt wird.

## Komponenten für die automatische Generierung eines Datensatzdokuments  {#components-to-automatically-generate-a-document-of-record}

Um ein Dokument aus Datensatz für adaptive Formulare zu erstellen, benötigen Sie die folgenden Komponenten:

**Adaptives** FormularAdaptives Formular, für das Sie ein Dokument Datensatz generieren möchten.

**Basisvorlage (empfohlen)** XFA-Vorlage (XDP-Datei), die in AEM Designer erstellt wurde. Die Basisvorlage wird verwendet, um die Formatierungs- und Brandinginformationen für das Dokument der Datensatzvorlage anzugeben.

Siehe [Basisvorlage eines Dokuments Datensatz](#base-template-of-a-document-of-record)

>[!NOTE]
>
>Die Basisvorlage eines Dokuments aus Datensatz wird auch als Metavorlage eines Dokuments aus Datensatz bezeichnet.

**Dokument der** Vorlage &quot;recordXFA&quot;(XDP-Datei), die aus einem adaptiven Formular generiert wurde.

Siehe [Dokument der Konfiguration der Datensatzvorlage](#document-of-record-template-configuration).

**Formulardaten** Informationen, die von einem Benutzer im adaptiven Formular ausgefüllt werden. Es wird mit dem Dokument der Datensatzvorlage zusammengeführt, um das Dokument des Datensatzes zu generieren.

## Zuordnen von adaptiven Formularelementen {#mapping-of-adaptive-form-elements}

Die folgenden Abschnitte beschreiben, wie adaptive Formularelemente im Datensatzdokument angezeigt werden.

### Felder {#fields}

<table>
 <tbody>
  <tr>
   <th>Komponente des adaptiven Formulars</th>
   <th>Zugehörige XFA-Komponente</th>
   <th>Wird das Dokument der Datensatzvorlage standardmäßig einbezogen?</th>
   <th>Hinweise</th>
  </tr>
  <tr>
   <td>Schaltfläche</td>
   <td>Schaltfläche</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Kontrollkästchen</td>
   <td>Kontrollkästchen</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Datumsauswahl</td>
   <td>Datums-/Uhrzeitfeld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Dropdownliste</td>
   <td>Dropdown-Liste</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Scribble-Signatur</td>
   <td>Scribble-Signatur</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Numerisches Feld</td>
   <td>Numerisches Feld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Kennwortfeld</td>
   <td>Kennwort-Feld</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Optionsfeld</td>
   <td>Optionsfeld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Textfeld</td>
   <td>Textfeld</td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Zurücksetzen-Schaltfläche</td>
   <td>Schaltfläche „Zurücksetzen“</td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Senden-Schaltfläche</td>
   <td><p>E-Mail-Senden-Schaltfläche</p> <p>HTTP-Senden-Schaltfläche</p> </td>
   <td>false</td>
   <td> </td>
  </tr>
  <tr>
   <td>Geschäftsbedingungen</td>
   <td> </td>
   <td>true</td>
   <td> </td>
  </tr>
  <tr>
   <td>Dateianhang</td>
   <td> </td>
   <td>false</td>
   <td>Nicht verfügbar im Dokument der Datensatzvorlage. Nur im Dokument des Datensatzes über Anlagen verfügbar.</td>
  </tr>
 </tbody>
</table>

### Container {#containers}

<table>
 <tbody>
  <tr>
   <th>Komponente des adaptiven Formulars</th>
   <th>Zugehörige XFA-Komponente</th>
   <th>Hinweise</th>
  </tr>
  <tr>
   <td>Fenster<br /> </td>
   <td>Teilformular<br /> </td>
   <td>Wiederholbare Bereichs-Maps, zugeordnet zu wiederholbarem Teilformular.</td>
  </tr>
 </tbody>
</table>

### Statische Komponenten  {#static-components}

| Komponente des adaptiven Formulars | Zugehörige XFA-Komponente | Hinweise |
|---|---|---|
| Bild | Bild | Die TextDraw- und Bildkomponenten, ob gebunden oder ungebunden, werden für ein XSD-basiertes adaptives Formular immer im Dokument des Datensatzes angezeigt, es sei denn, sie werden mithilfe des Dokuments der Datensatzeinstellungen ausgeschlossen. |
| Text | Text |

>[!NOTE]
>
>In klassischen Benutzeroberfläche sind verschiedene Registerkarten zum Bearbeiten der Feldeigenschaften vorhanden.

### Tabellen {#tables}

Die Tabellenkomponenten adaptiver Formulare, wie Kopf- und Fußzeile sowie Zeilen sind den entsprechenden XFA-Komponenten zugeordnet. Sie können wiederholbare Bereiche Tabellen im Datensatzdokument zuordnen.

## Basisvorlage eines Datensatzdokuments {#base-template-of-a-document-of-record}

Die Basisvorlage beinhaltet Informationen zu Stil und Erscheinungsbild des Datensatzdokuments. Es bietet Ihnen die Möglichkeit, das Standarderscheinungsbild des automatisch generierten Datensatzdokuments anzupassen. Beispiel: Sie möchten das Logo Ihres Unternehmens in der Kopfzeile und die Copyright-Informationen in der Fußzeile des Datensatzdokuments einfügen. Die Masterseite der Basisvorlage wird als Masterseite für die Datensatzdokument-Vorlage verwendet. Die Masterseite kann Informationen wie Kopfzeile, Fußzeile und Seitenzahl enthalten, die Sie auf das Datensatzdokument anwenden können. Sie können diese Informationen mithilfe der Basisvorlage für die automatische Generierung des Dokuments des Datensatzes auf das Dokument des Datensatzes anwenden. Dank Verwendung der Basisvorlage können Sie die Standardeinstellungen der Felder ändern.

Bitte folgen Sie bei der Entwicklung Ihrer Basisvorlage den [Konventionen für Basisvorlagen](#base-template-conventions).

## Konventionen für Basisvorlagen  {#base-template-conventions}

Eine Basisvorlage wird verwendet, um Kopf- und Fußzeile, Stil und Erscheinungsbild eines Datensatzdokuments zu definieren. Die Kopf- und Fußzeile kann Informationen wie Firmenlogo- und Copyright-Informationen enthalten. Die erste Übergeordnet-Seite in der Basisvorlage wird kopiert und als Übergeordnet-Seite für das Dokument des Datensatzes verwendet, das Kopf- und Fußzeilen sowie Seitenzahlen und andere Informationen enthält, die auf allen Seiten im Dokument des Datensatzes angezeigt werden sollen. Wenn Sie eine Basisvorlage verwenden, die nicht den Konventionen der Basisvorlage entspricht, wird die erste Übergeordnet-Seite der Basisvorlage weiterhin im Dokument der Datensatzvorlage verwendet. Es wird dringend empfohlen, dass Sie Ihre Basisvorlage gemäß den Konventionen entwerfen und sie für die automatische Erstellung von Datensatzdokumenten verwenden.

**Konventionen für Masterseiten**

* In der Basisvorlage sollten Sie dem Stammteilformular den Namen `AF_METATEMPLATE` und der Übergeordnet den Namen `AF_MASTERPAGE` geben.

* Die Übergeordnet-Seite mit dem Namen `AF_MASTERPAGE`, die sich unter dem Stammteilformular `AF_METATEMPLATE` befindet, wird bevorzugt zum Extrahieren von Kopf- und Fußzeileninformationen und Stilinformationen verwendet.

* Wenn `AF_MASTERPAGE` fehlt, wird die erste Masterseite in der Basisvorlage verwendet.

**Stilkonventionen für Felder**

* Wenn Sie einen Stil auf die Felder im Datensatzdokument anwenden, stellt die Basisvorlage die Felder im Teilformular `AF_FIELDSSUBFORM` bereit, das sich unter dem Stammteilformular `AF_METATEMPLATE` befindet.

* Die Eigenschaften dieser Felder werden auf die Felder im Datensatzdokument angewendet. Diese Felder sollten der Benennungsregel `AF_<name of field in all caps>_XFO` folgen. Das Kontrollkästchen sollte beispielsweise `AF_CHECKBOX_XFO` heißen.

Zum Erstellen einer Basisvorlage führen Sie in AEM-Designer folgende Schritte durch.

1. Wählen Sie „**Datei“ > „Neu**“.
1. Wählen Sie „**Vorlage verwenden**“.

1. Wählen Sie die Kategorie „**Formulare – Datensatzdokument**“.
1. Wählen Sie „**DoR-Basisvorlage**“.
1. Klicken Sie auf „**Weiter**“ und geben Sie die erforderlichen Informationen ein.

1. (Optional) Ändern Sie den Stil und das Erscheinungsbild von Feldern, die Sie auf die Felder im Datensatzdokument anwenden möchten.
1. Speichern Sie das Formular.

Sie können das gespeicherte Formular jetzt als Basisvorlage für das Datensatzdokument verwenden.
Ändern bzw. entfernen Sie keine Skripts, die in der Basisvorlage vorhanden sind.

**Ändern der Basisvorlage**

* Wenn Sie auf Felder in der Basisvorlage keinen Stil anwenden, wird empfohlen, diese Felder aus der Basisvorlage zu entfernen, damit alle Aktualisierungen der Basisvorlage automatisch übernommen werden.
* Während des Änderns der Basisvorlage dürfen Sie keine Skripte entfernen, hinzufügen oder ändern.

>[!NOTE]
>
>Entwickeln Sie die Basisvorlage mithilfe von Konventionen und folgen Sie dabei genau den oben beschriebenen Schritten.

## Konfiguration von Dokument aus Datensatzvorlage {#document-of-record-template-configuration}

Konfigurieren Sie das Dokument der Datensatzvorlage Ihres Formulars, damit Ihre Kunden eine druckfreundliche Kopie des gesendeten Formulars herunterladen können. Eine XDP-Datei dient als Dokument einer Datensatzvorlage. Das Dokument des Downloads von Datensatzkunden wird entsprechend dem in der XDP-Datei angegebenen Layout formatiert.

Führen Sie die folgenden Schritte aus, um ein Dokument aus Datensatz für adaptive Formulare zu konfigurieren:

1. Klicken Sie in AEM Autoreninstanz auf **Forms > Forms und Dokumente.**
1. Wählen Sie ein Formular aus und klicken Sie auf „**Eigenschaften anzeigen**“.
1. Tippen Sie im Fenster Eigenschaften auf **Formularmodell**.
Sie können auch ein Formularmodell beim Erstellen eines Formulars auswählen.

   >[!NOTE]
   >
   >Wählen Sie auf der Registerkarte &quot;Formularmodell&quot;in der Dropdown-Liste **Schema** oder **Keine** aus. **** **[!UICONTROL Dokument of record wird nicht für XFA-basierte oder adaptive Formulare mit Formularvorlage als Formularmodell unterstützt.]**

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Abschnitt „Konfiguration von Dokument aus Datensatzvorlage“ eine der folgenden Optionen aus.

   **Wählen Sie** diese Option, wenn Sie das Dokument des Datensatzes für das Formular nicht konfigurieren möchten.

   **Formularvorlage als Dokument einer Datensatzvorlage zuordnen Wählen Sie diese** Option, wenn Sie eine XDP-Datei haben, die Sie als Vorlage für das Dokument des Datensatzes verwenden möchten. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   Die ausgewählte XDP-Datei wird mit dem adaptiven Formular verknüpft.

   **Dokument aus** Datensatz erstellenWählen Sie diese Option, um eine XDP-Datei als Basisvorlage zum Definieren des Stils und Erscheinungsbilds für das Dokument des Datensatzes zu verwenden. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   >[!NOTE]
   >
   >Stellen Sie in folgenden Fällen sicher, dass das Schema, das für die Erstellung von adaptivem Formular und Schema (Datenschema) des XFA-Formulars verwendet wird, gleich sind:
   >
   >
   >
   >    * Ihr adaptives Formular ist Schema-basiert
   >    * Sie verwenden die Option **Formularvorlage als Dokument der Datensatzvorlage** als Dokument der Datensatzvorlage zuordnen


1. Klicken Sie auf **Fertig.**

## Anpassen der Branding-Informationen im Datensatzdokument {#customize-the-branding-information-in-document-of-record}

Beim Generieren eines Datensatzdokuments können Sie auf der Registerkarte „Datensatzdokument“ Branding-Informationen für das Datensatzdokument ändern. Die Registerkarte „Datensatzdokument“ enthält Optionen für Logos, Aussehen, Layout, Kopf- und Fußzeile, zum Anpassen des Haftungsausschlusses sowie eine Optionen zum Entscheiden, ob Sie deaktivierte Kontrollkästchen und Optionsfeldern berücksichtigen möchten.

Für die Lokalisierung der Branding-Informationen, die Sie auf der Registerkarte für das Datensatzdokument eingeben, müssen Sie sicherstellen, dass das Gebietsschema des Browsers richtig eingestellt ist. Um die Branding-Informationen im Datensatzdokument anzupassen, gehen Sie wie folgt vor:

1. Wählen Sie im Dokument des Datensatzes einen Bereich (Stammbereich) aus und tippen Sie dann auf ![configure](assets/configure.png).
1. Tippen Sie auf ![dortab](assets/dortab.png). Die Registerkarte „Datensatzdokument“ wird eingeblendet.
1. Wählen Sie entweder die Standardvorlage oder eine benutzerdefinierte Vorlage für das Rendern von Datensatzdokumenten aus. Wenn Sie die Standardvorlage auswählen, wird eine Miniaturvorschau des Datensatzdokuments in der Dropdown-Liste für Vorlagen angezeigt.

   ![Brandingvorlage](assets/brandingtemplate.png)

   Wenn Sie eine benutzerdefinierte Vorlage auswählen, navigieren zu einer XDP auf Ihrem AEM Forms-Server und wählen sie aus. Wenn Sie eine Vorlage verwenden möchten, die sich noch nicht auf Ihrem AEM Forms-Server befindet, müssen Sie die XDP zuerst auf Ihren AEM-Server hochladen.

1. Abhängig davon, ob Sie eine Standard- oder eine benutzerdefinierte Vorlage wählen, werden einige oder alle der folgenden Eigenschaften auf der Registerkarte „Datensatzdokument“ angezeigt. Legen Sie die relevanten Eigenschaften fest:

   * **Logo-Bild:** Sie können entweder das Logo-Bild des adaptiven Formulars verwenden, eines in DAM auswählen oder eines von Ihrem Computer hochladen.
   * **Formulartitel**
   * **Kopfzeilentext**
   * **Haftungsausschluss-Bezeichnung**
   * **Haftungsausschluss**
   * **Text des Haftungsausschlusses**
   * **Akzentfarbe:** Die Farbe, in der Kopfzeilentext und Trennlinien im Datensatzdokument-PDF dargestellt werden.
   * **Schriftfamilie**: Schriftfamilie des Textes im Dokument des PDF-Datensatzes
   * **Für Kontrollkästchen und Optionsschaltflächenkomponenten nur ausgewählte Werte einblenden**
   * **Trennzeichen für mehrere ausgewählte Werte**
   * **Formularobjekte, die nicht mit dem Datenmodell verbunden sind, einschließen**
   * **Ausgeblendete Felder vom Datensatzdokument ausschließen**
   * **Beschreibung der Bedienfelder ausblenden**

   >[!NOTE]
   >
   >Wenn Sie eine Vorlage für ein adaptives Formular mit einem Designer-Version vor 6.3 verwenden, müssen Sie sicherstellen, dass im Root-Unterformular der Vorlage für das adaptive Formular folgendes vorhanden ist, damit Akzentfarbe und Schriftfamilie funktionieren:

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. Tippen Sie auf „Fertig“, um die Branding-Änderungen zu speichern.

## Tabellen- und Spaltenlayouts für Bereiche im Datensatzdokument  {#table-and-column-layouts-for-panels-in-document-of-record}

Ihr adaptives Formular kann lang sein und mehrere Formularfelder enthalten. Sie möchten eventuell das Datensatzdokument nicht als exakte Kopie des adaptiven Formulars speichern. Im Editor für adaptive Formulare können Sie jetzt das Tabellen- oder Spaltenlayout zum Speichern eines oder mehrerer Bereiche des adaptiven Formulars im Datensatzdokument auswählen.

Bevor Sie ein Datensatzdokument generieren, wählen Sie in den Einstellungen für den betreffenden Bereich unter „Layout für Dokument aus Datensatz“ entweder „Tabelle“ oder „Spalte“ aus. Die Felder im Bereich werden im Datensatzdokument entsprechend angeordnet.

![Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet](assets/dortablelayout.png)

Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet

![Felder in einem Bedienfeld, im Datensatzdokument im Spaltenlayout angeordnet](assets/dorcolumnlayout.png)

Felder in einem Bereich, im Datensatzdokument im Spaltenlayout angeordnet

## Datensatzdokument-Einstellungen {#document-of-record-settings}

Mit dem Dokument der Datensatzeinstellungen können Sie Optionen auswählen, die Sie in das Dokument des Datensatzes aufnehmen möchten. Beispiel: Eine Bank akzeptiert in einem Formular Name, Alter, Sozialversicherungsnummer und Telefonnummer. Das Formular generiert eine Bankkontonummer und Details zur Filiale. Sie können festlegen, dass nur Name, Sozialversicherungsnummer, Bankkonto und Filialendetails im Datensatzdokument angezeigt werden.

Das Dokument der Datensatzeinstellungen einer Komponente ist unter ihren Eigenschaften verfügbar. Um auf die Eigenschaften einer Komponente zuzugreifen, wählen Sie die Komponente aus und klicken Sie in der Überlagerung auf ![cmppr](assets/cmppr.png). Die Eigenschaften werden in der Seitenleiste angezeigt. Sie finden darin die folgenden Einstellungen.

**Einstellungen auf Feldebene**

* **Aus Datensatzdokument ausschließen**: Wird diese Eigenschaft aktiviert, erscheint das Feld im Datensatzdokument nicht. Dies ist eine skriptfähige Eigenschaft namens `excludeFromDoR`. Ihr Verhalten ist abhängig von der Eigenschaft **Felder aus DoR ausschließen, wenn sie ausgeblendet sind** auf Formularebene.

* **Bereich als Tabelle anzeigen:** Wenn die Eigenschaft festgelegt ist, wird der Bereich als Tabelle im Dokument des Datensatzes angezeigt, wenn der Bereich weniger als 6 Felder enthält. Gilt nur für den Bereich.
* **Titel aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint der Titel des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.
* **Beschreibung aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint die Beschreibung des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.

**Einstellungen auf Formularebene**

* **Ungebundene Felder in DoR einbeziehen:** Durch Festlegen dieser Eigenschaft werden ungebundenen Felder aus dem Schema-basierten adaptiven Formular im Datensatzdokument berücksichtigt. Diese Option ist standardmäßig aktiviert.
* **Felder aus DoR ausschließen, wenn sie ausgeblendet sind:** Durch Festlegen dieser Eigenschaft wird das Verhalten der Eigenschaft „Aus Datensatzdokument ausschließen“ auf Feldebene außer Kraft gesetzt, wenn diese nicht den Wert „true“ hat. Wenn Felder zum Zeitpunkt der Formularübermittlung ausgeblendet sind, werden sie vom Dokument des Datensatzes ausgeschlossen, wenn die Eigenschaft auf &quot;true&quot;gesetzt ist, vorausgesetzt, die Eigenschaft &quot;Aus Dokument des Datensatzes ausschließen&quot;ist nicht eingestellt.

## Wichtige Aspekte beim Arbeiten mit einem Datensatzdokument {#key-considerations-when-working-with-document-of-record}

Beachten Sie beim Arbeiten am Dokument der Aufzeichnung für adaptive Formulare die folgenden Hinweise und Einschränkungen.

* Dokument von Datensatzvorlagen unterstützt keinen Rich-Text. Rich-Text im statischen adaptiven Formular oder bei den vom Endbenutzer ausgefüllten Informationen wird daher im Datensatzdokument als Nur-Text angezeigt.
* Dokumentfragmente in einem adaptiven Formular werden im Datensatzdokument nicht angezeigt. Adaptive Formularfragmente werden jedoch nicht unterstützt.
* Die Inhaltsbindung in Datensatzdokumenten, die für XML-Schema-Basierte adaptive Formulare generiert werden, wird nicht unterstützt.
* Lokalisierte Versionen des DoR werden nach Wunsch für ein Gebietsschema erstellt, wenn der Benutzer das Rendern des DoR anfordert. Die Lokalisierung von DoR tritt zusammen mit der Lokalisierung des adaptiven Formulars auf. Siehe [Verwenden von AEM-Übersetzungs-Arbeitsablauf zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).

