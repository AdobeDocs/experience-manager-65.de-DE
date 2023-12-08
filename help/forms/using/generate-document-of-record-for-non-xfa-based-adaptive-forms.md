---
title: Generieren eines Datensatzdokuments für adaptive Formulare
description: Erklärt, wie Sie eine Vorlage für ein Datensatzdokument (DoR) für adaptive Formulare generieren können.
content-type: reference
topic-tags: adaptive_forms, develop
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms
exl-id: 7240897f-6b3a-427a-abc6-66310c2998f3
source-git-commit: 6b24067c1808475044a612f21d5d4d2793c13e17
workflow-type: tm+mt
source-wordcount: '3583'
ht-degree: 71%

---

# Generieren von Datensatzdokumenten für adaptive Formulare oder adaptive Formularfragmente {#generate-document-of-record-for-adaptive-forms}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


## Übersicht {#overview}

Nachdem Ihre Kunden ein Formular gesendet haben, möchten sie im Allgemeinen einen Beleg (in gedruckter Form oder im Dokumentformat) über die eingegebenen Informationen behalten, um später darauf Bezug nehmen zu können. Dies wird als Datensatzdokument bezeichnet.

In diesem Artikel wird erläutert, wie Sie ein Datensatzdokument für adaptive Forms- oder adaptive Formularfragmente generieren können.

>[!NOTE]
>
>Die automatische Generierung von Datensatzdokumenten wird für XFA-basierte adaptive Formulare nicht unterstützt. Sie können jedoch die XDP verwenden, die zum Erstellen des adaptiven Formulars als Datensatzdokument verwendet wird.

## Adaptive Formulartypen und ihre Datensatzdokumente {#adaptive-form-types-and-their-documents-of-record}

Wenn Sie ein adaptives Formular erstellen, können Sie ein Formularmodell auswählen. Ihre Optionen sind:

* [Formularvorlagen](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template) Sie können eine XFA-Vorlage für Ihr adaptives Formular auswählen. Wenn Sie eine XFA-Vorlage auswählen, können Sie die dazugehörige XDP-Datei als Datensatzdokument verwenden (siehe oben). 

* [XML-Schema](../../forms/using/creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema) Sie können eine XML-Schemadefinition für Ihr adaptives Formular auswählen. Wenn Sie ein XML-Schema für Ihr adaptives Formular auswählen, können Sie:

   * Verknüpfen Sie eine XFA-Vorlage für das Datensatzdokument. Stellen Sie sicher, dass die zugeordnete XFA-Vorlage dasselbe XML-Schema wie Ihr adaptives Formular verwendet
   * Datensatzdokument automatisch generieren

* Mit der Option „Ohne“ können Sie ein adaptives Formular ohne Formularmodell erstellen. Das Datensatzdokument für Ihr adaptives Formular wird automatisch generiert.

Wenn Sie ein Formularmodell auswählen, konfigurieren Sie das Datensatzdokument mithilfe der Optionen, die unter „Konfiguration von Dokument aus Datensatzvorlage“ verfügbar sind. Weitere Informationen dazu finden Sie unter [Konfiguration der Datensatzdokument-Vorlage](#document-of-record-template-configuration).

## Automatisch generiertes Datensatzdokument {#automatically-generated-document-of-record}

Mit einem Datensatzdokument können Ihre Kunden eine Kopie des übermittelten Formulars zum Drucken aufbewahren. Wenn Sie automatisch ein Datensatzdokument generieren, wird jedes Mal das Datensatzdokument sofort aktualisiert, wenn Sie das Formular ändern. Beispiel: Sie entfernen für Kunden, die als ihr Land die USA angeben, das Feld „Alter“. Wenn diese Kunden ein Datensatzdokument generieren, ist das Feld &quot;age&quot;für sie im Datensatzdokument nicht sichtbar.

 Ein automatisch generiertes Datensatzdokument bietet folgende Vorteile:

* Es kümmert sich um die Datenbindung.
* Dadurch werden automatisch Felder ausgeblendet, die im Datensatzdokument zum Zeitpunkt des Sendens entsprechend markiert sind. Zusätzlicher Aufwand ist nicht erforderlich.
* Dies spart Zeit für die Entwicklung der Datensatzdokument-Vorlage.
* Außerdem können Sie auch verschiedene Formatierungsstile und Erscheinungsbilder ausprobieren, indem Sie unterschiedliche Basisvorlagen verwenden und dann das beste Design für Ihr Datensatzdokument auswählen. Stil und Erscheinungsbild sind optional. Wenn Sie sich auf keinen Stil festlegen, werden Systemstile als Standard festgelegt.
* Dadurch wird sichergestellt, dass jede Änderung im Formular sofort im Datensatzdokument angezeigt wird.

## Komponenten zum automatischen Generieren eines Datensatzdokuments {#components-to-automatically-generate-a-document-of-record}

Sie benötigen die folgenden Komponenten, um ein Datensatzdokument für adaptive Formulare zu generieren:

**Adaptives Formular** Das adaptive Formular, für das Sie ein Datensatzdokument generieren möchten.

**Adaptives Formularfragment** Adaptives Formularfragment, für das Sie ein Datensatzdokument generieren möchten.

**Basisvorlage (empfohlen)** Das ist eine in AEM Designer erstellte XFA-Vorlage (XDP-Datei). Eine Basisvorlage wird verwendet, um die Stile und Branding-Informationen für die Datensatzdokument-Vorlage festzulegen.

Siehe [Basisvorlage eines Datensatzdokuments](#base-template-of-a-document-of-record)

>[!NOTE]
>
>Die Basisvorlage eines Datensatzdokuments wird auch als Metavorlage des Datensatzdokuments bezeichnet.

**Datensatzdokument-Vorlage** Eine aus einem adaptiven Formular generierte XFA-Vorlage (XDP-Datei).

Weitere Informationen dazu finden Sie unter [Konfiguration der Datensatzdokument-Vorlage](#document-of-record-template-configuration).

**Formulardaten** Informationen, die von einem Benutzer in das adaptive Formular eingetragen werden. Sie werden mit der Datensatzdokument-Vorlage zusammengeführt, um das Datensatzdokument zu generieren.

## Zuordnung von adaptiven Formularelementen {#mapping-of-adaptive-form-elements}

In den folgenden Abschnitten wird beschrieben, wie adaptive Formularelemente im Datensatzdokument angezeigt werden.

### Felder {#fields}

<table>
 <tbody>
  <tr>
   <th>Komponente des adaptiven Formulars</th>
   <th>Zugehörige XFA-Komponente</th>
   <th>Standardmäßig in der Datensatzdokument-Vorlage enthalten?</th>
   <th>Anmerkungen</th>
  </tr>
  <tr>
   <td>Schaltfläche</td>
   <td>Schaltfläche</td>
   <td>Falsch</td>
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
   <td>Freihändige Unterschrift</td>
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
   <td>Falsch</td>
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
   <td>Falsch</td>
   <td> </td>
  </tr>
  <tr>
   <td>Schaltfläche „Senden“</td>
   <td><p>Schaltfläche „E-Mail senden“</p> <p>Schaltfläche „HTTP senden“</p> </td>
   <td>Falsch</td>
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
   <td>Falsch</td>
   <td>In Datensatzdokument-Vorlage nicht verfügbar. In Datensatzdokument-Vorlage nur über Anlagen verfügbar.</td>
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
   <td>Wiederholbare Bedienfelder werden wiederholbaren Teilformularen zugeordnet.</td>
  </tr>
 </tbody>
</table>

### Statische Komponenten {#static-components}

| Komponente des adaptiven Formulars | Zugehörige XFA-Komponente | Anmerkungen |
|---|---|---|
| Bild | Bild | Die Komponenten TextDraw und Image (egal ob gebunden oder nicht) werden immer im Datensatzdokument eines XSD-basierten adaptiven Formulars angezeigt, es sei denn, sie werden mithilfe der Datensatzdokument-Einstellungen ausgeschlossen. |
| Text | Text |

>[!NOTE]
>
>In der klassischen Benutzeroberfläche sind verschiedene Registerkarten zum Bearbeiten der Feldeigenschaften vorhanden.

### Tabellen {#tables}

Die Tabellenkomponenten für adaptive Formulare wie Kopf- und Fußzeile sowie Zeilen werden den entsprechenden XFA-Komponenten zugeordnet. Sie können wiederholbare Bereiche Tabellen im Datensatzdokument zuordnen.

## Basisvorlage eines Datensatzdokuments {#base-template-of-a-document-of-record}

Die Basisvorlage stellt Formatierungs- und Darstellungsinformationen für das Datensatzdokument bereit. Damit können Sie die standardmäßige Darstellung des automatisch erstellten Datensatzdokuments anpassen. Beispiel: Sie möchten Ihr Firmenlogo in der Kopfzeile und Copyright-Informationen in der Fußzeile des Datensatzdokuments hinzufügen. Die Masterseite aus der Basisvorlage wird als Masterseite für die Datensatzdokumentvorlage verwendet. Die Masterseite kann Informationen wie Seitenkopf, Seitenfußzeile und Seitenzahl enthalten, die Sie auf das Datensatzdokument anwenden können. Sie können solche Informationen mithilfe der Basisvorlage für die automatische Erstellung des Datensatzdokuments auf das Datensatzdokument anwenden. Die Verwendung der Basisvorlage ermöglicht es Ihnen, die Standardeinstellungen von Feldern zu ändern.

Stellen Sie sicher, dass Sie [Konventionen für Basisvorlagen](#base-template-conventions) wenn Sie eine Basisvorlage erstellen.

## Konventionen für Basisvorlagen {#base-template-conventions}

Eine Basisvorlage wird verwendet, um Kopf- und Fußzeile, Stil und Erscheinungsbild eines Datensatzdokuments zu definieren. Die Kopf- und die Fußzeile können Informationen wie Firmenlogo und Copyright-Vermerk enthalten. Die erste Masterseite in der Basisvorlage wird als Masterseite für das Datensatzdokument kopiert und verwendet. Sie enthält Kopfzeile, Fußzeile und Seitenanzahl oder auch andere Informationen, die im Datensatzdokument auf allen Seiten angezeigt werden sollen. Wenn Sie eine Basisvorlage verwenden, die nicht den Konventionen für Basisvorlagen entspricht, wird die erste Masterseite aus der Basisvorlage dennoch in der Datensatzdokument-Vorlage verwendet. Es wird dringend empfohlen, Ihre Basisvorlage gemäß den Konventionen zu entwerfen und sie für die automatische Generierung des Datensatzdokuments zu verwenden.

**Konventionen für Musterseiten**

* In der Basisvorlage sollten Sie das Stamm-Unterformular mit `AF_METATEMPLATE` und die Musterseite mit `AF_MASTERPAGE` benennen.

* Die Musterseite mit dem Namen `AF_MASTERPAGE`, die sich unterhalb des Stamm-Unterformulars `AF_METATEMPLATE` befindet, hat beim Extrahieren von Kopfzeilen-, Fußzeilen- und Stilinformationen Vorrang.

* Wenn `AF_MASTERPAGE` fehlt, wird die erste Musterseite in der Basisvorlage verwendet.

**Stilkonventionen für Felder**

* Um einen Stil auf die Felder im Datensatzdokument anzuwenden, stellt die Basisvorlage Felder im `AF_FIELDSSUBFORM` Unterabschnitt unter `AF_METATEMPLATE` Stammteilformular.

* Die Eigenschaften dieser Felder werden auf die Felder im Datensatzdokument angewendet. Benennungen für diese Felder sollten der Form `AF_<name of field in all caps>_XFO` folgen. So sollte beispielsweise der Feldname für ein Kontrollkästchen `AF_CHECKBOX_XFO` lauten.

Gehen Sie wie folgt vor, um eine Basisvorlage in AEM Designer zu erstellen:

1. Klicken Sie auf **Datei > Neu**.
1. Wählen Sie die Option **Auf Basis einer Vorlage** aus.

1. Wählen Sie die Kategorie **Formulare – Aufzuzeichnendes Dokument**.
1. Wählen Sie **DoR-Basisvorlage** aus.
1. Klicken Sie auf **Weiter** und geben Sie die erforderlichen Informationen ein.

1. (Optional) Ändern Sie die Formatierung und Darstellung von Feldern, die Sie auf die Felder im Datensatzdokument anwenden möchten.
1. Speichern Sie das Formular.

Sie können das gespeicherte Formular jetzt als Basisvorlage für das Datensatzdokument verwenden.
Ändern oder entfernen Sie keine Skripte, die in der Basisvorlage vorhanden sind.

**Ändern der Basisvorlage**

* Wenn Sie keine Formatierung auf Felder in der Basisvorlage anwenden, ist es ratsam, diese Felder aus der Basisvorlage zu entfernen, damit alle Aktualisierungen auf die Basisvorlage automatisch abgerufen werden.
* Während des Änderns der Basisvorlage dürfen Sie keine Skripte entfernen, hinzufügen oder ändern.

>[!NOTE]
>
>Entwickeln Sie die Basisvorlage gemäß den Konventionen und folgen Sie dabei genau den oben beschriebenen Schritten.

## Konfiguration von Vorlagen für Datensatzdokumente {#document-of-record-template-configuration}

Konfigurieren Sie die Datensatzdokument-Vorlage Ihres Formulars, damit Ihre Kunden eine benutzerfreundliche Kopie des gesendeten Formulars zum Drucken herunterladen können. Als Datensatzdokument-Vorlage dient eine XDP-Datei. Das vom Kunden heruntergeladene Datensatzdokument ist entsprechend dem Layout formatiert, das in der XDP-Datei festgelegt ist.

Führen Sie die folgenden Schritte aus, um ein Datensatzdokument für adaptive Formulare zu konfigurieren:

1. Klicken Sie in der AEM-Autor-Instanz auf **Formulare > Formulare und Dokumente**.
1. Wählen Sie ein Formular aus und klicken Sie auf **Eigenschaften anzeigen**.
1. Wählen Sie im Fenster Eigenschaften die Option **Formularmodell**.
Sie können ein Formularmodell auch bei der Erstellung eines Formulars auswählen.

   >[!NOTE]
   >
   >Achten Sie auf der Registerkarte „Formularmodell“ darauf, dass Sie **Schema** oder **Ohne** aus dem Dropdown-Menü **Auswählen** auswählen. **[!UICONTROL Das Datensatzdokument wird nicht für XFA-basierte oder adaptive Formulare mit einer Formularvorlage als Formularmodell unterstützt.]**

1. Wählen Sie auf der Registerkarte &quot;Formularmodell&quot;im Abschnitt Konfiguration der Datensatzvorlagenkonfiguration eine der folgenden Optionen aus:

   **Keine** Wählen Sie diese Option aus, wenn Sie kein Datensatzdokument für das Formular konfigurieren möchten.

   **Formularvorlage als Dokument einer Datensatzvorlage verknüpfen** Wählen Sie diese Option, wenn Sie eine XDP-Datei haben, die Sie als Vorlage für das Datensatzdokument verwenden möchten. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   Die ausgewählte XDP-Datei wird mit dem adaptiven Formular verknüpft.

   **Datensatzdokument generieren** Wählen Sie diese Option aus, um eine XDP-Datei als Basisvorlage zum Definieren von Stil und Erscheinungsbild des Datensatzdokuments zu verwenden. Wenn Sie diese Option wählen, werden alle im AEM Forms-Repository verfügbaren XDP-Dateien angezeigt. Wählen Sie die entsprechende Datei aus.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass das zum Erstellen des adaptiven Formulars und Schemas (Datenschema) des XFA-Formulars verwendete Schema identisch ist, wenn:
   >
   >
   >
   >    * Ihr adaptives Formular ist schemabasiert
   >    * Sie verwenden die Datensatzdokument-Option „**Formularvorlage als Dokument aus Datensatzvorlage zuordnen**“.
   >
   >

1. Klicken Sie auf **Fertig**.

## Anpassen der Branding-Informationen im Datensatzdokument {#customize-the-branding-information-in-document-of-record}

Beim Generieren eines Datensatzdokuments können Sie Branding-Informationen für das Datensatzdokument auf der Registerkarte Datensatzdokument ändern. Die Registerkarte „Datensatzdokument“ enthält Optionen für Logos, Aussehen, Layout, Kopf- und Fußzeile, zum Anpassen des Haftungsausschlusses sowie eine Optionen zum Entscheiden, ob Sie deaktivierte Kontrollkästchen und Optionsfeldern berücksichtigen möchten.

Für die Lokalisierung der Branding-Informationen, die Sie auf der Registerkarte für das Datensatzdokument eingeben, müssen Sie sicherstellen, dass das Gebietsschema des Browsers richtig eingestellt ist. Führen Sie die folgenden Schritte aus, um die Branding-Informationen des Datensatzdokuments anzupassen:

1. Wählen Sie einen Bereich (Stammbereich) im Datensatzdokument aus und wählen Sie dann ![konfigurieren](assets/configure.png).
1. Auswählen ![dortab](/help/forms/using/assets/dortab.png). Die Registerkarte „Datensatzdokument“ wird angezeigt.
1. Wählen Sie entweder die Standardvorlage oder eine benutzerdefinierte Vorlage zum Rendern des Datensatzdokuments aus. Wenn Sie die Standardvorlage auswählen, wird unter der Dropdown-Liste Vorlage eine Miniaturansicht des Datensatzdokuments angezeigt.

   ![brandingtemplate](/help/forms/using/assets/brandingtemplate.png)

   Wenn Sie eine benutzerdefinierte Vorlage auswählen, durchsuchen Sie eine XDP auf Ihrem AEM Forms-Server. Wenn Sie eine Vorlage verwenden möchten, die sich noch nicht auf Ihrem AEM Forms-Server befindet, müssen Sie zunächst die XDP auf Ihren AEM Forms-Server hochladen.

1. Je nachdem, ob Sie eine Standard- oder eine benutzerdefinierte Vorlage auswählen, werden auf der Registerkarte &quot;Datensatzdokument&quot;einige oder alle der folgenden Eigenschaften angezeigt. Legen Sie die folgenden entsprechend fest:

   * **Logo-Bild:** Sie können entweder das Logo-Bild des adaptiven Formulars verwenden, eines in DAM auswählen oder eines von Ihrem Computer hochladen.
   * **Formulartitel**
   * **Header Text**
   * **Haftungsausschluss-Bezeichnung**
   * **Haftungsausschluss**
   * **Haftungsausschlusstext**
   * **Akzentfarbe:** Die Farbe, in der Kopfzeilentext und Trennlinien im PDF des aufzuzeichnenden Dokuments dargestellt werden.
   * **Schriftfamilie:** Schriftfamilie des Textes im Datensatzdokument-PDF. 
   * **Für Kontrollkästchen- und Optionsfeld-Komponenten nur die ausgewählten Werte anzeigen**
   * **Trennzeichen für mehrere ausgewählte Werte**
   * **Formularobjekte einschließen, die nicht an das Datenmodell gebunden sind**
   * **Ausgeblendete Felder aus dem Datensatzdokument ausschließen**
   * **Beschreibung von Bereichen ausblenden**

   Wenn die von Ihnen ausgewählte benutzerdefinierte XDP-Vorlage mehrere Masterseiten enthält, werden die Eigenschaften für diese Seiten im Abschnitt **[!UICONTROL Inhalt]** auf der Registerkarte **[!UICONTROL Datensatzdokument]** angezeigt.

   ![Eigenschaften primäre seite ](assets/master-page-properties.png)

   Die Eigenschaften der Masterseiten umfassen Logobild, Kopfzeilentext, Formulartitel, Haftungsausschlussüberschrift und Haftungsausschlusstext. Sie können Eigenschaften für adaptive Formulare oder XDP-Vorlagen auf das Datensatzdokument anwenden. AEM Forms wendet standardmäßig die Vorlageneigenschaften auf das Datensatzdokument an. Sie können auch benutzerdefinierte Werte für die Eigenschaften der Masterseiten definieren. Informationen zum Anwenden mehrerer Masterseiten in einem Datensatzdokument finden Sie unter [Anwenden mehrerer Masterseiten in einem Datensatzdokument](#apply-multiple-master-pages-dor).

   >[!NOTE]
   >
   >Wenn Sie eine Vorlage für ein adaptives Formular verwenden, die mit einer Version von Designer vor 6.3 erstellt wurde, müssen Sie sicherstellen, dass im Root-Unterformular der Vorlage für das adaptive Formular folgendes vorhanden ist, damit Akzentfarbe und Schriftfamilie funktionieren:

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

1. Um die Branding-Änderungen zu speichern, wählen Sie Fertig aus.

## Tabellen- und Spalten-Layouts für Bereiche im Datensatzdokument {#table-and-column-layouts-for-panels-in-document-of-record}

Ihr adaptives Formular ist möglicherweise sehr lange und umfasst mehrere Formularfelder. Möglicherweise möchten Sie ein Datensatzdokument nicht als exakte Kopie des adaptiven Formulars speichern. Jetzt können Sie ein Tabellen- oder Spaltenlayout zum Speichern eines oder mehrerer adaptiver Formularbedienfelder im Datensatzdokument-PDF auswählen.

Wählen Sie vor dem Generieren eines Datensatzdokuments in den Einstellungen eines Bedienfelds die Option Layout für das Datensatzdokument für diesen Bereich als Tabelle oder Spalte. Die Felder im Bedienfeld werden entsprechend im Datensatzdokument organisiert.

![Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet](assets/dortablelayout.png)

Felder in einem Bedienfeld, im Datensatzdokument im Tabellenlayout angeordnet

![Felder in einem Bedienfeld, im Datensatzdokument im Spaltenlayout angeordnet](assets/dorcolumnlayout.png)

Felder in einem Bedienfeld, im Datensatzdokument im Spalten-Layout angeordnet

## Einstellungen für Datensatzdokumente {#document-of-record-settings}

Über die Datensatzdokument-Einstellungen können Sie Optionen festlegen, die Sie in das Datensatzdokument aufnehmen möchten. Eine Bank akzeptiert zum Beispiel Name, Alter, Sozialversicherungsnummer und Telefonnummer in einem Formular. Das Formular generiert eine Bankkontonummer und Details zur Zweigstelle. Sie können festlegen, dass nur der Name, die Sozialversicherungsnummer, das Bankkonto und die Details der Zweigstellen im Datensatzdokument angezeigt werden.

Die Datensatzdokument-Einstellungen einer Komponente sind unter den Eigenschaften verfügbar. Um auf die Eigenschaften einer Komponente zuzugreifen, wählen Sie die Komponente aus und klicken Sie auf ![cmppr](assets/cmppr.png) in der Überlagerung. Die Eigenschaften werden in der Seitenleiste mit den folgenden Einstellungen angezeigt.

**Einstellungen auf Feldebene**

* **Aus Datensatzdokument ausschließen**: Wenn Sie die Eigenschaft &quot;true&quot;festlegen, wird das Feld aus dem Datensatzdokument ausgeschlossen. Dies ist eine skriptfähige Eigenschaft namens `excludeFromDoR`. Ihr Verhalten ist von der auf Formularebene befindlichen Eigenschaft **Felder aus DoR ausschließen, wenn sie ausgeblendet sind** abhängig.

* **Bereich als Tabelle anzeigen:** Durch die Aktivierung dieser Eigenschaft wird der Bereich im Datensatzdokument als Tabelle angezeigt, wenn er weniger als 6 Felder enthält. Gilt nur für den Bereich.
* **Titel aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint der Titel des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.
* **Beschreibung aus Datensatzdokument ausschließen:** Wird diese Eigenschaft aktiviert, erscheint die Beschreibung des Bereichs bzw. der Tabelle im Datensatzdokument nicht. Gilt nur für Bereiche und Tabellen.
* **[!UICONTROL Seitenumbruch]** > **[!UICONTROL Ort]**: Legt fest, wo Sie das Bedienfeld platzieren möchten.
   * **[!UICONTROL Platzieren nach]** > **[!UICONTROL Vorherigem]**: Platziert den Bereich nach dem vorherigen Objekt im übergeordneten Bereich.
   * **[!UICONTROL Platzieren im]** > **[!UICONTROL Inhaltsbereich]** > Name des Inhaltsbereichs: Platziert den Bereich im angegebenen Inhaltsbereich.
   * **[!UICONTROL Ort]** > **[!UICONTROL Anfang des nächsten Inhaltsbereichs]**: Platziert das Bedienfeld am Anfang des nächsten Inhaltsbereichs.
   * **[!UICONTROL Ort]** > **[!UICONTROL Anfang des Inhaltsbereichs]** > Name des Inhaltsbereichs: Platziert das Bedienfeld am Anfang des angegebenen Inhaltsbereichs.
   * **[!UICONTROL Ort]** > **[!UICONTROL Auf Seite]** > Name der Master-Seite: Platziert den Bereich auf der angegebenen Seite. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
   * **[!UICONTROL Ort]** > **[!UICONTROL Anfang der nächsten Seite]**: Platziert das Bedienfeld am Anfang der nächsten Seite. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
   * **[!UICONTROL Ort]** > **[!UICONTROL Seitenanfang]** > Name der Master-Seite: Platziert das Bedienfeld am Anfang der Seite, wenn die angegebene Seite gerendert wird. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
* **[!UICONTROL Paginierung]** > **[!UICONTROL Nachher]**: Legt fest, welcher Bereich ausgefüllt werden soll, nachdem ein Bedienfeld platziert wurde. Die folgenden Felder sind im Abschnitt **[!UICONTROL Nachher]** vorhanden:
   * **[!UICONTROL Nachher]** > **[!UICONTROL Fortsetzen von übergeordnetem Ausfüllen]**: Setzt das Zusammenführen von Daten für alle Objekte fort, die im übergeordneten Bereich noch ausgefüllt werden sollen.
   * **[!UICONTROL Nachher]** > **[!UICONTROL Wechseln zum nächsten Inhaltsbereich]**: Startet das Füllen des nächsten Inhaltsbereichs nach dem Platzieren des Bedienfelds.
   * **[!UICONTROL Nachher]** > **[!UICONTROL Wechseln zum Inhaltsbereich]** > Name des Inhaltsbereichs: Startet das Füllen des angegebenen Inhaltsbereichs nach dem Platzieren des Bedienfelds.
   * **[!UICONTROL Nachher]** > **[!UICONTROL Wechseln zur nächsten Seite]**: Startet das Füllen der nächsten Seite, nachdem der Bereich platziert wurde.
   * **[!UICONTROL Nachher]** > **[!UICONTROL Wechseln zur Seite]** > Name der Seite: Startet das Füllen der angegebenen Seite nach dem Platzieren des Bedienfelds.
* **[!UICONTROL Paginierung]** > **[!UICONTROL Überlauf]**: Legt einen Überlauf für einen Bereich oder eine Tabelle fest, der/die sich über Seiten spannt. Die folgenden Felder sind im Abschnitt **[!UICONTROL Überlauf]** verfügbar:
   * **[!UICONTROL Überlauf]** > **[!UICONTROL Keines]**: Startet das Füllen der nächsten Seite. Wenn ein Seitenumbruch nicht automatisch eingefügt wird, fügt [!DNL AEM Forms] einen Seitenumbruch hinzu.
   * **[!UICONTROL Überlauf]** > **[!UICONTROL Wechseln zum Inhaltsbereich]** > Name des Inhaltsbereichs: Startet das Füllen des angegebenen Inhaltsbereichs.
   * **[!UICONTROL Überlauf]** > **[!UICONTROL Wechseln zu Seite]** > Name der Seite: Startet das Füllen der angegebenen Seite.

  >[!NOTE]
  >
  > Die Eigenschaft &quot;Paginierung&quot;ist nicht für adaptive Formularfragmente verfügbar.

Informationen zum Anwenden von Seitenumbrüchen und zum Anwenden mehrerer Master-Seiten in einem Datensatzdokument finden Sie unter [Anwenden eines Seitenumbruchs in einem Datensatzdokument](#apply-page-breaks-in-dor) und [Anwenden mehrerer Master-Seiten auf ein Datensatzdokument](#apply-multiple-master-pages-dor).

**Einstellungen auf Formularebene**

* **Ungebundene Felder in DoR einbeziehen:** Durch Festlegen dieser Eigenschaft werden ungebundenen Felder aus dem Schema-basierten adaptiven Formular im Datensatzdokument berücksichtigt. Diese Option ist standardmäßig aktiviert.
* **Felder aus DoR ausschließen, falls ausgeblendet**: Legen Sie die Eigenschaft fest, um beim Senden des Formulars die ausgeblendeten Felder vom [!UICONTROL Datensatzdokument] auszuschließen. Wenn Sie [Auf dem Server erneut überprüfen](/help/forms/using/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form) aktivieren, berechnet der Server die ausgeblendeten Felder neu, bevor er diese Felder aus dem [!UICONTROL Datensatzdokument] ausschließt.

## Anwenden eines Seitenumbruchs in einem Datensatzdokument {#apply-page-breaks-in-dor}

Sie können Seitenumbrüche in einem Datensatzdokument mithilfe mehrerer Methoden anwenden.

So wenden Sie einen Seitenumbruch auf ein Datensatzdokument an:

1. Wählen Sie das Bedienfeld aus und wählen Sie ![Konfigurieren](/help/forms/using/assets/configure.png)
1. Erweitern Sie das **[!UICONTROL Datensatzdokument]**, um die Eigenschaften anzuzeigen.

1. Im **[!UICONTROL Paginierung]** Bereich, wählen Sie ![Ordner](/help/forms/using/assets/folder-icon.png) im **[!UICONTROL Ort]** -Feld.
1. Auswählen **[!UICONTROL Anfang der nächsten Seite]** und wählen **[!UICONTROL Auswählen]**. Sie können auch **[!UICONTROL Seitenanfang]**, wählen Sie die Masterseite aus und wählen Sie **[!UICONTROL Auswählen]** , um den Seitenumbruch anzuwenden.
1. Auswählen ![Speichern](/help/forms/using/assets/save_icon.png) , um die Eigenschaften zu speichern.

Das ausgewählte Bedienfeld wechselt zur nächsten Seite.

## Anwenden mehrerer Master-Seiten auf ein Datensatzdokument {#apply-multiple-master-pages-dor}

Wenn die von Ihnen ausgewählte benutzerdefinierte XDP-Vorlage mehrere Master-Seiten enthält, werden die Eigenschaften für diese Seiten im Abschnitt [!UICONTROL Inhalt] der Registerkarte [!UICONTROL Datensatzdokument] angezeigt. Weitere Informationen finden Sie unter [Anpassen der Branding-Informationen im Datensatzdokument](#customize-the-branding-information-in-document-of-record).

Sie können mehrere übergeordnete Seiten auf ein Datensatzdokument anwenden, indem Sie verschiedene Master-Seiten auf die Komponenten eines adaptiven Formulars anwenden. Verwenden Sie den Abschnitt [Paginierung](#document-of-record-settings) der Datensatzeigenschaften, um mehrere Master-Seiten anzuwenden.

Im Folgenden finden Sie ein Beispiel dafür, wie Sie mehrere Master-Seiten auf ein Datensatzdokument anwenden: 
Sie laden eine XDP-Vorlage, die vier Master-Seiten enthält, auf den [!DNL AEM Forms]-Server hoch. [!DNL AEM Forms] wendet die Vorlageneigenschaften standardmäßig auf das Datensatzdokument an. [!DNL AEM Forms] wendet auch die ersten Master-Seiteneigenschaften in der Vorlage auf das Datensatzdokument an.

Führen Sie die folgenden Schritte aus, um die zweiten Master-Seiteneigenschaften auf ein Bedienfeld und die dritten Master- Seiteneigenschaften auf die nachfolgenden Bedienfelder anzuwenden:

1. Wählen Sie das Bedienfeld aus, um die zweite Masterseite anzuwenden, und wählen Sie ![Konfigurieren](assets/cmppr.png).
1. Im **[!UICONTROL Paginierung]** Bereich, wählen Sie ![Ordner](/help/forms/using/assets/folder-icon.png) im **[!UICONTROL Ort]** -Feld.
1. Auswählen **[!UICONTROL Auf Seite]**, wählen Sie die zweite Masterseite aus und wählen Sie **[!UICONTROL Auswählen]**.
AEM Forms wendet die zweite Master-Seite auf das Bedienfeld und alle nachfolgenden Bedienfelder im adaptiven Formular an.
1. Im **[!UICONTROL Paginierung]** Bereich, wählen Sie ![Ordner](/help/forms/using/assets/folder-icon.png) im **[!UICONTROL Nachher]** -Feld.
1. Auswählen **[!UICONTROL Gehe zu Seite]**, wählen Sie die dritte Masterseite aus und wählen Sie **[!UICONTROL Auswählen]**.
1. Auswählen ![Speichern](/help/forms/using/assets/save_icon.png) , um die Eigenschaften zu speichern.
AEM Forms wendet die dritte Master-Seite auf das Bedienfeld und alle nachfolgenden Bedienfelder im adaptiven Formular an.

>[!NOTE]
>
> Sie können nicht mehrere Masterseiten auf ein Datensatzdokument für ein adaptives Formularfragment anwenden.

## Wichtige Aspekte beim Arbeiten mit einem Datensatzdokument {#key-considerations-when-working-with-document-of-record}

Beachten Sie die folgenden Hinweise und Einschränkungen beim Arbeiten mit einem Datensatzdokument für adaptive Formulare.

* Datensatzdokument-Vorlagen unterstützen keinen Rich-Text. Rich-Text im statischen adaptiven Formular oder in den vom Endbenutzer eingegebenen Informationen wird daher als Nur-Text im Datensatzdokument angezeigt.
* Dokumentfragmente in einem adaptiven Formular werden nicht im Datensatzdokument angezeigt. Adaptive Formularfragmente werden jedoch unterstützt.
* Die Inhaltsbindung in Datensatzdokumenten, die für XML-Schema-Basierte adaptive Formulare generiert werden, wird nicht unterstützt.
* Die lokalisierte Version des Datensatzdokuments wird bei Bedarf für ein Gebietsschema erstellt, wenn der Benutzer die Wiedergabe des Datensatzdokuments anfordert. Die Lokalisierung des Datensatzdokuments erfolgt zusammen mit der Lokalisierung des adaptiven Formulars. Siehe [Verwenden von AEM-Übersetzungs-Arbeitsablauf zum Lokalisieren von adaptiven Formularen und Datensatzdokumenten](/help/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.md).
