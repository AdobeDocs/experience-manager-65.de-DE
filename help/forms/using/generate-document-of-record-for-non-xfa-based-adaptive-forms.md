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
feature: Adaptive Formulare
exl-id: 7240897f-6b3a-427a-abc6-66310c2998f3
source-git-commit: a81367c2a07031d8c6cf549050a1445ff0c1a8dc
workflow-type: tm+mt
source-wordcount: '3508'
ht-degree: 55%

---

# Generierung eines Datensatzdokuments für adaptive Formulare{#generate-document-of-record-for-adaptive-forms}

## Überblick {#overview}

Nachdem Ihre Kunden ein Formular gesendet haben, möchten sie im Allgemeinen einen Beleg (in gedruckter Form oder im Dokumentformat) über die eingegebenen Informationen behalten, um später darauf Bezug nehmen zu können. Dies wird als Datensatzdokument bezeichnet.

Sie erfahren in diesem Artikel, wie Sie ein Datensatzdokument für adaptive Formulare erstellen können.

>[!NOTE]
>
>Die automatische Generierung des Datensatzdokuments wird für XFA-basierte adaptive Formulare nicht unterstützt. Sie können jedoch XDP verwenden, um das adaptive Formular als Datensatzdokument zu erstellen.

## Typen adaptiver Formulare und ihre Datensatzdokumente {#adaptive-form-types-and-their-documents-of-record}

Beim Erstellen eines adaptiven Formulars können Sie ein Formularmodell auswählen. Ihre Optionen sind:

* [Formularvorlagen](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template) Sie können eine XFA-Vorlage für Ihr adaptives Formular auswählen. Wenn Sie eine XFA-Vorlage auswählen, können Sie die zugehörige XDP-Datei für das Datensatzdokument wie oben beschrieben verwenden.

* [XML-Schema](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema) Sie können eine XML-Schemadefinition für Ihr adaptives Formular auswählen. Wenn Sie ein XML-Schema für Ihr adaptives Formular auswählen, können Sie Folgendes tun:

   * XFA-Vorlage für Datensatzdokument verknüpfen. Vergewissern Sie sich, dass die verknüpfte XFA-Vorlage dasselbe XML-Schema verwendet wie Ihr adaptives Formular.
   * Datensatzdokument automatisch generieren

* Mit der Option „Ohne“ können Sie ein adaptives Formular ohne Formularmodell erstellen. Das Datensatzdokument wird automatisch für Ihr adaptives Formular generiert.

Wenn Sie ein Formularmodell auswählen, konfigurieren Sie das Datensatzdokument mit den Optionen, die unter Konfiguration der Datensatzdokumentvorlage verfügbar sind. Weitere Informationen dazu finden Sie unter [Konfiguration der Datensatzdokument-Vorlage](#document-of-record-template-configuration).

## Automatisch generiertes Datensatzdokument {#automatically-generated-document-of-record}

Dank Datensatzdokument erhalten Ihre Kunden eine Kopie des übermittelten Formulars zum Ausdrucken. Wenn Sie automatisch ein Datensatzdokument generieren, wird jedes Mal, wenn Sie Ihr Formular ändern, sein Datensatzdokument sofort aktualisiert. Beispiel: Sie entfernen für Kunden, die als ihr Land die USA angeben, das Feld „Alter“. Wenn diese Kunden ein Datensatzdokument erstellen, ist das Altersfeld im Datensatzdokument nicht sichtbar.

Das automatisch generierte Datensatzdokument bietet die folgenden Vorteile:

* Es kümmert sich um die Datenbindung.
* Dadurch werden automatisch Felder ausgeblendet, die zum Zeitpunkt der Übermittlung aus dem Datensatzdokument ausgeschlossen sind. Zusätzlicher Aufwand ist nicht erforderlich.
* Dies spart Zeit für die Erstellung der Datensatzdokumentvorlage.
* Außerdem können Sie auch verschiedene Formatierungsstile und Erscheinungsbilder ausprobieren, indem Sie unterschiedliche Basisvorlagen verwenden und dann das beste Design für Ihr Datensatzdokument auswählen. Stil und Erscheinungsbild sind optional. Wenn Sie sich auf keinen Stil festlegen, werden Systemstile als Standard festgelegt.
* Es stellt sicher, dass eine Änderung im Formular sofort im Datensatzdokument umgesetzt wird.

## Komponenten für die automatische Generierung eines Datensatzdokuments {#components-to-automatically-generate-a-document-of-record}

Um ein Datensatzdokument für adaptive Formulare zu generieren, benötigen Sie die folgenden Komponenten:

**Adaptives** Formular Adaptives Formular, für das Sie ein Datensatzdokument generieren möchten.

**Basisvorlage (empfohlen)** Das ist eine in AEM Designer erstellte XFA-Vorlage (XDP-Datei). Die Basisvorlage wird verwendet, um Stile und Branding-Informationen für die Datensatzdokumentvorlage anzugeben.

Siehe [Basisvorlage eines Datensatzdokuments](#base-template-of-a-document-of-record)

>[!NOTE]
>
>Die Basisvorlage eines Datensatzdokuments wird auch als Metavorlage eines Datensatzdokuments bezeichnet.

**Datensatzdokument** templateXFA-Vorlage (XDP-Datei), das aus einem adaptiven Formular generiert wurde.

Weitere Informationen dazu finden Sie unter [Konfiguration der Datensatzdokument-Vorlage](#document-of-record-template-configuration).

**Formulardaten:** Informationen, die von einem Benutzer im adaptiven Formular ausgefüllt werden. Es wird mit der Datensatzdokument-Vorlage zusammengeführt, um das Datensatzdokument zu generieren.

## Zuordnen von adaptiven Formularelementen {#mapping-of-adaptive-form-elements}

Die folgenden Abschnitte beschreiben, wie adaptive Formularelemente im Datensatzdokument angezeigt werden.

### Felder {#fields}

<table>
 <tbody>
  <tr>
   <th>Komponente des adaptiven Formulars</th>
   <th>Zugehörige XFA-Komponente</th>
   <th>Standardmäßig in Datensatzdokument-Vorlage eingeschlossen?</th>
   <th>Anmerkungen</th>
  </tr>
  <tr>
   <td>Schaltfläche</td>
   <td>Schaltfläche</td>
   <td>Nein</td>
   <td> </td>
  </tr>
  <tr>
   <td>Kontrollkästchen</td>
   <td>Kontrollkästchen</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Datumsauswahl</td>
   <td>Datum-/Uhrzeitfeld</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Dropdown-Liste</td>
   <td>Dropdown-Liste</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Freihändige Unterschrift</td>
   <td>Unterschrift freihändig</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Numerisches Feld</td>
   <td>Numerisches Feld</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Kennwortfeld</td>
   <td>Kennwortfeld</td>
   <td>Nein</td>
   <td> </td>
  </tr>
  <tr>
   <td>Optionsfeld</td>
   <td>Optionsfeld</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Textfeld</td>
   <td>Textfeld</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Schaltfläche „Zurücksetzen“</td>
   <td>Schaltfläche „Zurücksetzen“</td>
   <td>Nein</td>
   <td> </td>
  </tr>
  <tr>
   <td>Schaltfläche „Senden“</td>
   <td><p>Schaltfläche „E-Mail senden“</p> <p>Schaltfläche „HTTP senden“</p> </td>
   <td>Nein</td>
   <td> </td>
  </tr>
  <tr>
   <td>Allgemeine Geschäftsbedingungen</td>
   <td> </td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Dateianhang</td>
   <td> </td>
   <td>Nein</td>
   <td>Nicht verfügbar in Datensatzdokument-Vorlage. Nur im Datensatzdokument über Anlagen verfügbar.</td>
  </tr>
 </tbody>
</table>

### Container {#containers}

<table>
 <tbody>
  <tr>
   <th>Komponente des adaptiven Formulars</th>
   <th>Zugehörige XFA-Komponente</th>
   <th>Anmerkungen</th>
  </tr>
  <tr>
   <td>Bereich<br /> </td>
   <td>Teilformular<br /> </td>
   <td>Wiederholbare Bereichs-Maps, zugeordnet zu wiederholbarem Teilformular.</td>
  </tr>
 </tbody>
</table>

### Statische Komponenten {#static-components}

| Komponente des adaptiven Formulars | Zugehörige XFA-Komponente | Anmerkungen |
|---|---|---|
| Bild | Bild | Die Komponenten TextDraw und Bild, ob gebunden oder ungebunden, werden immer im Datensatzdokument für ein XSD-basiertes adaptives Formular angezeigt, es sei denn, sie werden mithilfe der Datensatzdokument-Einstellungen ausgeschlossen. |
| Text | Text |

>[!NOTE]
>
>In der klassischen Benutzeroberfläche sind verschiedene Registerkarten zum Bearbeiten der Feldeigenschaften vorhanden.

### Tabellen {#tables}

Die Tabellenkomponenten adaptiver Formulare, wie Kopf- und Fußzeile sowie Zeilen sind den entsprechenden XFA-Komponenten zugeordnet. Sie können wiederholbare Bereiche Tabellen im Datensatzdokument zuordnen.

## Basisvorlage eines Datensatzdokuments {#base-template-of-a-document-of-record}

Die Basisvorlage beinhaltet Informationen zu Stil und Erscheinungsbild des Datensatzdokuments. Es bietet Ihnen die Möglichkeit, das Standarderscheinungsbild des automatisch generierten Datensatzdokuments anzupassen. Beispiel: Sie möchten das Logo Ihres Unternehmens in der Kopfzeile und die Copyright-Informationen in der Fußzeile des Datensatzdokuments einfügen. Die Masterseite der Basisvorlage wird als Masterseite für die Datensatzdokument-Vorlage verwendet. Die Masterseite kann Informationen wie Kopfzeile, Fußzeile und Seitenzahl enthalten, die Sie auf das Datensatzdokument anwenden können. Sie können diese Informationen mithilfe der Basisvorlage für die automatische Erstellung des Datensatzdokuments auf das Datensatzdokument anwenden. Die Verwendung der Basisvorlage ermöglicht es Ihnen, die Standardeinstellungen von Feldern zu ändern.

Bitte folgen Sie bei der Entwicklung Ihrer Basisvorlage den [Konventionen für Basisvorlagen](#base-template-conventions).

## Konventionen für Basisvorlagen {#base-template-conventions}

Eine Basisvorlage wird verwendet, um Kopf- und Fußzeile, Stil und Erscheinungsbild eines Datensatzdokuments zu definieren. Die Kopf- und die Fußzeile können Informationen wie Firmenlogo und Copyright-Vermerk enthalten. Die erste Übergeordnete Seite in der Basisvorlage wird kopiert und als Übergeordnete Seite für das Datensatzdokument verwendet, die Kopf- und Fußzeilen sowie Seitenzahlen und andere Informationen enthält, die im Datensatzdokument auf allen Seiten angezeigt werden sollen. Wenn Sie eine Basisvorlage verwenden, die nicht den Konventionen für Basisvorlagen entspricht, wird die erste Übergeordnete Seite aus der Basisvorlage weiterhin in der Datensatzdokumentvorlage verwendet. Es wird dringend empfohlen, dass Sie Ihre Basisvorlage gemäß den Konventionen entwerfen und sie für die automatische Erstellung von Datensatzdokumenten verwenden.

**Konventionen für Musterseiten**

* In der Basisvorlage sollten Sie das Stamm-Unterformular mit `AF_METATEMPLATE` und die Musterseite mit `AF_MASTERPAGE` benennen.

* Die Musterseite mit dem Namen `AF_MASTERPAGE`, die sich unterhalb des Stamm-Unterformulars `AF_METATEMPLATE` befindet, hat beim Extrahieren von Kopfzeilen-, Fußzeilen- und Stilinformationen Vorrang.

* Wenn `AF_MASTERPAGE` fehlt, wird die erste Musterseite in der Basisvorlage verwendet.

**Stilkonventionen für Felder**

* Wenn Sie einen Stil auf die Felder im Datensatzdokument anwenden, stellt die Basisvorlage die Felder im Teilformular `AF_FIELDSSUBFORM` bereit, das sich unter dem Stammteilformular `AF_METATEMPLATE` befindet.

* Die Eigenschaften dieser Felder werden auf die Felder im Datensatzdokument angewendet. Benennungen für diese Felder sollten der Form `AF_<name of field in all caps>_XFO` folgen. So sollte beispielsweise der Feldname für ein Kontrollkästchen `AF_CHECKBOX_XFO` lauten.

Zum Erstellen einer Basisvorlage führen Sie in AEM-Designer folgende Schritte durch.

1. Wählen Sie „**Datei“ > „Neu**“.
1. Wählen Sie die Option **Auf Basis einer Vorlage** aus.

1. Wählen Sie die Kategorie **Formulare – Aufzuzeichnendes Dokument**.
1. Wählen Sie „**DoR-Basisvorlage**“.
1. Klicken Sie auf **Weiter** und geben Sie die erforderlichen Informationen ein.

1. (Optional) Ändern Sie den Stil und das Erscheinungsbild von Feldern, die Sie auf die Felder im Datensatzdokument anwenden möchten.
1. Speichern Sie das Formular.

Sie können das gespeicherte Formular jetzt als Basisvorlage für das Datensatzdokument verwenden.
Ändern oder entfernen Sie keine Skripte, die in der Basisvorlage vorhanden sind.

**Ändern der Basisvorlage**

* Wenn Sie auf Felder in der Basisvorlage keinen Stil anwenden, wird empfohlen, diese Felder aus der Basisvorlage zu entfernen, damit alle Aktualisierungen der Basisvorlage automatisch übernommen werden.
* Während des Änderns der Basisvorlage dürfen Sie keine Skripte entfernen, hinzufügen oder ändern.

>[!NOTE]
>
>Entwickeln Sie die Basisvorlage gemäß den Konventionen und folgen Sie dabei genau den oben beschriebenen Schritten.

## Konfiguration von Vorlagen für Datensatzdokumente {#document-of-record-template-configuration}

Konfigurieren Sie die Datensatzdokumentvorlage Ihres Formulars, damit Ihre Kunden eine benutzerfreundliche Kopie des gesendeten Formulars zum Drucken herunterladen können. Eine XDP-Datei dient als Datensatzdokument-Vorlage. Das Dokument aus Datensätzen, das Kunden herunterladen, ist gemäß dem in der XDP-Datei angegebenen Layout formatiert.

Führen Sie die folgenden Schritte aus, um ein Datensatzdokument für adaptive Formulare zu konfigurieren:

1. Klicken Sie in der AEM-Autor-Instanz auf **Formulare > Formulare und Dokumente**.
1. Wählen Sie ein Formular aus und klicken Sie auf **Eigenschaften anzeigen**.
1. Klicken Sie im Fenster „Eigenschaften“ auf **Formularmodell**.
Sie können ein Formularmodell auch bei der Erstellung eines Formulars auswählen.

   >[!NOTE]
   >
   >Achten Sie auf der Registerkarte „Formularmodell“ darauf, dass Sie **Schema** oder **Ohne** aus dem Dropdown-Menü **Auswählen** auswählen. **[!UICONTROL Das Datensatzdokument wird für XFA-basierte oder adaptive Formulare mit Formularvorlage als Formularmodell nicht unterstützt.]**

1. Wählen Sie auf der Registerkarte „Formularmodell“ im Abschnitt „Konfiguration der Datensatzdokument-Vorlage“ eine der folgenden Optionen aus.

   **** NoneWählen Sie diese Option, wenn Sie das Datensatzdokument für das Formular nicht konfigurieren möchten.

   **Formularvorlage als Datensatzdokumentvorlage verknüpfen Wählen Sie diese** Option, wenn Sie eine XDP-Datei haben, die Sie als Vorlage für das Datensatzdokument verwenden möchten. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   Die ausgewählte XDP-Datei wird mit dem adaptiven Formular verknüpft.

   **Generate Document of** RecordWählen Sie diese Option, um eine XDP-Datei als Basisvorlage zum Definieren des Stils und Erscheinungsbilds für das Datensatzdokument zu verwenden. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   >[!NOTE]
   >
   >Stellen Sie in folgenden Fällen sicher, dass das Schema, das für die Erstellung von adaptivem Formular und Schema (Datenschema) des XFA-Formulars verwendet wird, gleich sind:
   >
   >
   >
   >    * Ihr adaptives Formular ist Schema-basiert
   >    * Sie verwenden die Option **Formularvorlage als Datensatzdokumentvorlage zuordnen** für Datensatzdokument


1. Klicken Sie auf **Fertig.**

## Anpassen der Branding-Informationen im Datensatzdokument {#customize-the-branding-information-in-document-of-record}

Beim Generieren eines Datensatzdokuments können Sie auf der Registerkarte „Datensatzdokument“ Branding-Informationen für das Datensatzdokument ändern. Die Registerkarte „Datensatzdokument“ enthält Optionen für Logos, Aussehen, Layout, Kopf- und Fußzeile, zum Anpassen des Haftungsausschlusses sowie eine Optionen zum Entscheiden, ob Sie deaktivierte Kontrollkästchen und Optionsfeldern berücksichtigen möchten.

Für die Lokalisierung der Branding-Informationen, die Sie auf der Registerkarte für das Datensatzdokument eingeben, müssen Sie sicherstellen, dass das Gebietsschema des Browsers richtig eingestellt ist. Um die Branding-Informationen im Datensatzdokument anzupassen, gehen Sie wie folgt vor:

1. Wählen Sie ein Bedienfeld (Stammbedienfeld) im Datensatzdokument aus und tippen Sie dann auf ![configure](assets/configure.png).
1. Tippen Sie auf ![dortab](assets/dortab.png). Die Registerkarte „Datensatzdokument“ wird angezeigt.
1. Wählen Sie entweder die Standardvorlage oder eine benutzerdefinierte Vorlage für das Rendern von Datensatzdokumenten aus. Wenn Sie die Standardvorlage auswählen, wird eine Miniaturvorschau des Datensatzdokuments in der Dropdown-Liste für Vorlagen angezeigt.

   ![brandingtemplate](assets/brandingtemplate.png)

   Wenn Sie eine benutzerdefinierte Vorlage auswählen, navigieren zu einer XDP auf Ihrem AEM Forms-Server und wählen sie aus. Wenn Sie eine Vorlage verwenden möchten, die sich noch nicht auf Ihrem AEM Forms-Server befindet, müssen Sie die XDP zuerst auf Ihren AEM-Server hochladen.

1. Abhängig davon, ob Sie eine Standard- oder eine benutzerdefinierte Vorlage wählen, werden einige oder alle der folgenden Eigenschaften auf der Registerkarte „Datensatzdokument“ angezeigt. Legen Sie die folgenden entsprechend fest:

   * **Logo-Bild:** Sie können entweder das Logo-Bild des adaptiven Formulars verwenden, eines in DAM auswählen oder eines von Ihrem Computer hochladen.
   * **Formulartitel**
   * **Kopfzeilentext**
   * **Haftungsausschluss-Bezeichnung**
   * **Haftungsausschluss**
   * **Text des Haftungsausschlusses**
   * **Akzentfarbe:** Die Farbe, in der Kopfzeilentext und Trennlinien im Datensatzdokument-PDF dargestellt werden.
   * **Schriftfamilie**: Schriftfamilie des Textes im Datensatzdokument-PDF
   * **Für Kontrollkästchen und Optionsschaltflächenkomponenten nur ausgewählte Werte einblenden**
   * **Trennzeichen für mehrere ausgewählte Werte**
   * **Formularobjekte, die nicht mit dem Datenmodell verbunden sind, einschließen**
   * **Ausgeblendete Felder vom Datensatzdokument ausschließen**
   * **Beschreibung von Bereichen ausblenden**

   Wenn die von Ihnen ausgewählte benutzerdefinierte XDP-Vorlage mehrere Übergeordnete Seiten enthält, werden die Eigenschaften für diese Seiten im Abschnitt **[!UICONTROL content]** der Registerkarte **[!UICONTROL Datensatzdokument]** angezeigt.

   ![Übergeordnete Seiteneigenschaften](assets/master-page-properties.png)

   Die Übergeordneten Seiteneigenschaften umfassen Logobild, Kopfzeilentext, Formulartitel, Haftungsausschluss-Bezeichnung und Haftungsausschlusstext. Sie können Eigenschaften für adaptive Formulare oder XDP-Vorlagen auf das Datensatzdokument anwenden. AEM Forms wendet die Vorlageneigenschaften standardmäßig auf das Datensatzdokument an. Sie können auch benutzerdefinierte Werte für die Übergeordneten Seiteneigenschaften definieren. Informationen zum Anwenden mehrerer Übergeordneter Seiten in einem Datensatzdokument finden Sie unter [Anwenden mehrerer Übergeordneter Seiten auf ein Datensatzdokument](#apply-multiple-master-pages-dor).

   >[!NOTE]
   >
   >Wenn Sie eine adaptive Formularvorlage verwenden, die mit einer Designer-Version vor 6.3 erstellt wurde, müssen Sie sicherstellen, dass in Ihrer adaptiven Formularvorlage unter dem Stammteilformular Folgendes vorhanden ist, damit die Eigenschaften für Accent Color und Font Family funktionieren:

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

## Tabellen- und Spalten-Layouts für Bereiche im Datensatzdokument {#table-and-column-layouts-for-panels-in-document-of-record}

Ihr adaptives Formular kann lang sein und mehrere Formularfelder enthalten. Sie möchten eventuell das Datensatzdokument nicht als exakte Kopie des adaptiven Formulars speichern. Im Editor für adaptive Formulare können Sie jetzt das Tabellen- oder Spaltenlayout zum Speichern eines oder mehrerer Bereiche des adaptiven Formulars im Datensatzdokument auswählen.

Bevor Sie ein Datensatzdokument generieren, wählen Sie in den Einstellungen für den betreffenden Bereich unter „Layout für Dokument aus Datensatz“ entweder „Tabelle“ oder „Spalte“ aus. Die Felder im Bereich werden im Datensatzdokument entsprechend angeordnet.

![Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet](assets/dortablelayout.png)

Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet

![Felder in einem Bedienfeld, im Datensatzdokument im Spaltenlayout angeordnet](assets/dorcolumnlayout.png)

Felder in einem Bedienfeld, im Datensatzdokument im Spaltenlayout angeordnet

## Einstellungen für Datensatzdokumente {#document-of-record-settings}

Mit den Datensatzdokument-Einstellungen können Sie Optionen auswählen, die Sie in das Datensatzdokument aufnehmen möchten. Beispiel: Eine Bank akzeptiert in einem Formular Name, Alter, Sozialversicherungsnummer und Telefonnummer. Das Formular generiert eine Bankkontonummer und Details zur Filiale. Sie können festlegen, dass nur Name, Sozialversicherungsnummer, Bankkonto und Filialendetails im Datensatzdokument angezeigt werden.

Die Datensatzdokument-Einstellungen einer Komponente sind unter ihren Eigenschaften verfügbar. Um auf die Eigenschaften einer Komponente zuzugreifen, wählen Sie die Komponente aus und klicken Sie auf ![cmppr](assets/cmppr.png) in der Überlagerung. Die Eigenschaften werden in der Seitenleiste mit den folgenden Einstellungen angezeigt.

**Einstellungen auf Feldebene**

* **Aus Datensatzdokument ausschließen**: Wird diese Eigenschaft aktiviert, erscheint das Feld im Datensatzdokument nicht. Dies ist eine skriptfähige Eigenschaft namens `excludeFromDoR`. Ihr Verhalten ist von der auf Formularebene befindlichen Eigenschaft **Felder aus DoR ausschließen, wenn sie ausgeblendet sind** abhängig.

* **Bedienfeld als Tabelle anzeigen:** Durch Festlegen der Eigenschaft wird der Bereich als Tabelle im Datensatzdokument angezeigt, wenn der Bereich weniger als 6 Felder enthält. Gilt nur für den Bereich.
* **Titel aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint der Titel des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.
* **Beschreibung aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint die Beschreibung des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.
* **[!UICONTROL Paginierung]**  >  **[!UICONTROL Platzieren]**: Legt fest, wo Sie das Bedienfeld platzieren möchten.
   * **[!UICONTROL Ort]**  >  **[!UICONTROL Vorherige]**: Platziert den Bereich nach dem vorherigen Objekt im übergeordneten Bereich.
   * **[!UICONTROL Platzieren]**  >  **[!UICONTROL Im Inhaltsbereich]**  > Name des Inhaltsbereichs: Platziert den Bereich im angegebenen Inhaltsbereich.
   * **[!UICONTROL Ort]**  >  **[!UICONTROL Anfang des nächsten Inhaltsbereichs]**: Platziert das Bedienfeld am Anfang des nächsten Inhaltsbereichs.
   * **[!UICONTROL Ort]**  >  **[!UICONTROL Anfang des Inhaltsbereichs]**  > Name des Inhaltsbereichs: Platziert das Bedienfeld am Anfang des angegebenen Inhaltsbereichs.
   * **[!UICONTROL Ort]**  >  **[!UICONTROL Auf Seite]**  > Name der Übergeordneten Seite: Platziert den Bereich auf der angegebenen Seite. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
   * **[!UICONTROL Ort]**  >  **[!UICONTROL Anfang der nächsten Seite]**: Platziert das Bedienfeld am Anfang der nächsten Seite. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
   * **[!UICONTROL Ort]**  >  **[!UICONTROL Seitenanfang]**  > Name der Übergeordneten Seite: Platziert das Bedienfeld am Anfang der Seite, wenn die angegebene Seite gerendert wird. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
* **[!UICONTROL Paginierung]**  >  **[!UICONTROL Nach]**: Legt fest, welcher Bereich gefüllt werden soll, nachdem ein Bedienfeld platziert wurde. Die folgenden Felder sind im Abschnitt  **** Anschluss verfügbar:
   * **[!UICONTROL Nach]**  >  **[!UICONTROL Übergeordnetes Ausfüllen fortsetzen]**: Setzt das Zusammenführen von Daten für alle Objekte fort, die im übergeordneten Bereich noch ausgefüllt werden sollen.
   * **[!UICONTROL Nach]**  >  **[!UICONTROL Navigieren Sie zum nächsten Inhaltsbereich]**: Startet das Füllen des nächsten Inhaltsbereichs nach dem Platzieren des Bedienfelds.
   * **[!UICONTROL Nach]**  >  **[!UICONTROL Navigieren Sie zum Inhaltsbereich]**  > Name des Inhaltsbereichs: Startet das Füllen des angegebenen Inhaltsbereichs nach dem Platzieren des Bedienfelds.
   * **[!UICONTROL Nach]**  >  **[!UICONTROL Gehe zur nächsten Seite]**: Startet das Füllen der nächsten Seite, nachdem der Bereich platziert wurde.
   * **[!UICONTROL Nach]**  >  **[!UICONTROL Gehe zu Seite]**  > Name der Seite: Startet das Füllen der angegebenen Seite nach dem Platzieren des Bedienfelds.
* **[!UICONTROL Paginierung]**  >  **[!UICONTROL Überlauf]**: Legt einen Überlauf für einen Bereich oder eine Tabelle fest, der/die Seiten umfasst. Die folgenden Felder sind im Abschnitt **[!UICONTROL Überlauf]** verfügbar:
   * **[!UICONTROL Überlauf]**  >  **[!UICONTROL Keine]**: Startet das Füllen der nächsten Seite. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
   * **[!UICONTROL Überlauf]**  >  **[!UICONTROL Gehe zum Inhaltsbereich]**  > Name des Inhaltsbereichs: Startet das Füllen des angegebenen Inhaltsbereichs.
   * **[!UICONTROL Überlauf]**  >  **[!UICONTROL Gehe zu Seite]**  > Name der Seite: Startet das Füllen der angegebenen Seite.

Informationen zum Anwenden von Seitenumbrüchen und zum Anwenden mehrerer Übergeordneter Seiten in einem Datensatzdokument finden Sie unter [Anwenden von Seitenumbrüchen in einem Datensatzdokument](#apply-page-breaks-in-dor) und [Anwenden mehrerer Übergeordneter Seiten auf ein Datensatzdokument](#apply-multiple-master-pages-dor).

**Einstellungen auf Formularebene**

* **Ungebundene Felder in DoR einbeziehen:** Durch Festlegen dieser Eigenschaft werden ungebundenen Felder aus dem Schema-basierten adaptiven Formular im Datensatzdokument berücksichtigt. Diese Option ist standardmäßig aktiviert.
* **Felder aus DoR ausschließen, wenn sie ausgeblendet sind**: Wenn aktiviert, wird das Verhalten der auf Feldebene befindlichen Eigenschaft „Aus Datensatzdokument ausschließen“ überschrieben, wenn sie nicht den Wert „true“ hat. Wenn Felder zum Zeitpunkt der Formularübermittlung ausgeblendet sind, werden sie aus dem Datensatzdokument ausgeschlossen, wenn die Eigenschaft auf &quot;true&quot;festgelegt ist, vorausgesetzt, die Eigenschaft &quot;Aus Datensatzdokument ausschließen&quot;ist nicht festgelegt.

## Anwenden eines Seitenumbruchs in einem Datensatzdokument {#apply-page-breaks-in-dor}

Sie können Seitenumbrüche in einem Datensatzdokument mit mehreren Methoden anwenden.

So wenden Sie einen Seitenumbruch auf ein Datensatzdokument an:

1. Tippen Sie auf das Bedienfeld und wählen Sie ![Konfigurieren](assets/configure-icon.svg) aus.

1. Erweitern Sie **[!UICONTROL Datensatzdokument]** , um die Eigenschaften anzuzeigen.

1. Tippen Sie im Abschnitt **[!UICONTROL Paginierung]** im Feld ![Ordner](assets/folder-icon.svg) auf **[!UICONTROL Platzieren]** .
1. Tippen Sie auf **[!UICONTROL Anfang der nächsten Seite]** und tippen Sie auf **[!UICONTROL Auswählen]**. Sie können auch auf **[!UICONTROL Seitenanfang]** tippen, die Übergeordnete Seite auswählen und auf **[!UICONTROL Auswählen]** tippen, um den Seitenumbruch anzuwenden.
1. Tippen Sie auf ![Speichern](assets/save_icon.svg), um die Eigenschaften zu speichern.

Das ausgewählte Bedienfeld wechselt zur nächsten Seite.

## Anwenden mehrerer Übergeordneter Seiten auf ein Datensatzdokument {#apply-multiple-master-pages-dor}

Wenn die von Ihnen ausgewählte benutzerdefinierte XDP-Vorlage mehrere Übergeordnete Seiten enthält, werden die Eigenschaften für diese Seiten im Abschnitt [!UICONTROL content] der Registerkarte [!UICONTROL Datensatzdokument] angezeigt. Weitere Informationen finden Sie unter [Anpassen der Branding-Informationen im Datensatzdokument](#customize-the-branding-information-in-document-of-record).

Sie können mehrere Übergeordnete Seiten auf ein Datensatzdokument anwenden, indem Sie verschiedene Übergeordnete Seiten auf die Komponenten eines adaptiven Formulars anwenden. Verwenden Sie den Abschnitt [Paginierung](#document-of-record-settings) der Eigenschaften des Datensatzdokuments, um mehrere Übergeordnete Seiten anzuwenden.

Im Folgenden finden Sie ein Beispiel dafür, wie Sie mehrere Übergeordnete Seiten auf ein Datensatzdokument anwenden:
Sie laden eine XDP-Vorlage mit vier Übergeordneten Seiten auf den [!DNL AEM Forms]-Server hoch. [!DNL AEM Forms] wendet die Vorlageneigenschaften standardmäßig auf das Datensatzdokument an. [!DNL AEM Forms] wendet auch die ersten Übergeordneten Seiteneigenschaften in der Vorlage auf das Datensatzdokument an.

Führen Sie die folgenden Schritte aus, um die zweiten Übergeordneten Seiteneigenschaften auf ein Bedienfeld und die dritten Übergeordneten Seiteneigenschaften auf die Bedienfelder anzuwenden:

1. Tippen Sie auf das Bedienfeld, um die zweite Übergeordnete Seite anzuwenden, und wählen Sie ![Konfigurieren](assets/configure-icon.svg) aus.
1. Tippen Sie im Abschnitt **[!UICONTROL Paginierung]** im Feld ![Ordner](assets/folder-icon.svg) auf **[!UICONTROL Platzieren]** .
1. Tippen Sie auf **[!UICONTROL Wählen Sie auf Seite]** die zweite Übergeordnete Seite aus und tippen Sie auf **[!UICONTROL Auswählen]**.
AEM Forms wendet die zweite Übergeordnete Seite auf das Bedienfeld und alle nachfolgenden Bedienfelder im adaptiven Formular an.
1. Tippen Sie im Abschnitt **[!UICONTROL Paginierung]** im Feld ![Ordner](assets/folder-icon.svg) auf **[!UICONTROL Nach]** .
1. Tippen Sie auf **[!UICONTROL Gehe zu Seite]**, wählen Sie die dritte Übergeordnete Seite aus und tippen Sie auf **[!UICONTROL Auswählen]**.
1. Tippen Sie auf ![Speichern](assets/save_icon.svg), um die Eigenschaften zu speichern.
AEM Forms wendet die dritte Übergeordnete Seite auf das Bedienfeld und alle nachfolgenden Bedienfelder im adaptiven Formular an.


## Wichtige Aspekte beim Arbeiten mit einem Datensatzdokument {#key-considerations-when-working-with-document-of-record}

Beachten Sie die folgenden Überlegungen und Einschränkungen bei der Arbeit an einem Datensatzdokument für adaptive Formulare.

* Datensatzdokumentvorlagen unterstützen keinen Rich-Text. Rich-Text im statischen adaptiven Formular oder bei den vom Endbenutzer ausgefüllten Informationen wird daher im Datensatzdokument als Nur-Text angezeigt.
* Dokumentfragmente in einem adaptiven Formular werden im Datensatzdokument nicht angezeigt. Adaptive Formularfragmente werden jedoch nicht unterstützt.
* Die Inhaltsbindung in Datensatzdokumenten, die für XML-Schema-Basierte adaptive Formulare generiert werden, wird nicht unterstützt.
* Lokalisierte Versionen des DoR werden nach Wunsch für ein Gebietsschema erstellt, wenn der Benutzer das Rendern des DoR anfordert. Die Lokalisierung von DoR tritt zusammen mit der Lokalisierung des adaptiven Formulars auf. Siehe [Verwenden von AEM-Übersetzungs-Arbeitsablauf zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).
