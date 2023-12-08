---
title: Adaptive Formularfragmente
description: Adaptive Formulare bietet einen Mechanismus zum Erstellen eines Formularsegments (z. B. eines Bedienfelds oder einer Gruppe von Feldern) und zum Nutzen des Segments in einer beliebigen adaptiven Form. Sie können auch ein vorhandenes Bedienfeld als Fragment speichern.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms
exl-id: 2f276e9d-b3c1-48f7-a94a-bdf7eb15a031
source-git-commit: 6b24067c1808475044a612f21d5d4d2793c13e17
workflow-type: tm+mt
source-wordcount: '2359'
ht-degree: 50%

---

# Adaptive Formularfragmente{#adaptive-form-fragments}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/adaptive-form-fragments-core-components.html) |
| AEM 6.5 | Dieser Artikel |

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

Zwar wird jedes Formular für einen bestimmten Zweck entwickelt, doch enthalten die meisten Formularen einige gängige Elemente (z. B. für persönliche Angaben wie Name und Anschrift, Angaben zu Familienstand, Einkommen usw.). Formularentwicklerinnen und -entwickler müssen diese gängigen Segmente jedes Mal erstellen, wenn ein neues Formular erstellt wird.

Adaptive Formulare bieten einen bequemen Mechanismus, um Formularsegmente wie ein Bedienfeld oder eine Gruppe von Feldern nur einmal zu erstellen und sie in allen adaptiven Formularen wiederzuverwenden. Diese wiederverwendbaren und eigenständigen Segmente werden als adaptive Formularfragmente bezeichnet.

## Erstellen eines Fragments {#create-a-fragment}

Sie können ein adaptives Formularfragment von Grund auf neu erstellen oder ein Bedienfeld in einem vorhandenen adaptiven Formular als Fragment speichern.

### Neuerstellen von Fragmenten {#create-fragment-from-scratch}

1. Melden Sie sich bei der Author-Instanz von AEM Forms unter https://[*Hostname*]:[*Port*]/aem/forms.html an.
1. Klicken Sie auf **Erstellen > Adaptives Formularfragment**.
1. Geben Sie Titel, Namen, Beschreibung und Tags für das Fragment an.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.

1. Klicken Sie, um die Registerkarte **Formularmodell** zu öffnen. Wählen Sie dann aus der Dropdown-Liste **Auswählen** eines der folgenden Fragmentmodelle:

   * **Keins**: Gibt an, dass das Fragment von Grund auf ohne Formularmodell erstellt werden soll.

     >[!NOTE]
     >
     > Im adaptiven Forms, das auf Kernkomponenten basiert, können Sie ein einzelnes Formularfragment mehrmals in einem Formular verwenden. Es unterstützt nicht-basierte und schemabasierte Formularfragmente.

   * **Formularvorlage**: Das Fragment mit mithilfe einer XDP-Vorlage erstellt, die auf AEM Forms hochgeladen wurde. Wählen Sie die entsprechende XDP-Vorlage als Formularmodell für das Fragment aus.

   ![Erstellen eines adaptiven Formulars mit einer Formularvorlage als Modell](assets/form-template-model.png)

   Die Teilformulare, die als Fragmente in der ausgewählten Vorlage markiert sind, werden ebenfalls angezeigt. Sie können ein Teilformular für ein adaptives Formularfragment aus der Dropdownliste auswählen.

   ![Auswählen von Teilformularen aus der angegebenen Formularvorlage](assets/fragment-subform.png)

   Darüber hinaus können Sie ein adaptives Formularfragment mithilfe von Teilformularen erstellen, die nicht als Fragmente in der Formularvorlage markiert sind, indem Sie den SOM-Ausdruck für das Teilformular in der Dropdown-Liste angeben.

   * **XML-Schema**: Das Fragment wird mithilfe eines XML-Schemas erstellt, das auf AEM Forms hochgeladen wurde. Sie können ein XML-Schema als Formularmodell hochladen oder aus den verfügbaren Schemas wählen.

   ![Erstellen eines adaptiven Formularfragments, das auf einem XML-Schema basiert](assets/xml-schema-model.png)

   Sie können ein adaptives Formularfragment auch erstellen, indem Sie einen „complexType“ im ausgewählten Schema aus der Dropdownliste wählen.

   ![Wählen Sie einen komplexen Typ aus dem angegebenen XML-Schema-Modell.](assets/complex-type.png)

1. Klicken Sie auf **Erstellen** und dann auf **Öffnen**, um das Fragment mit einer Standardvorlage im Bearbeitungsmodus zu öffnen.

Im Bearbeitungsmodus können Sie eine beliebige adaptive Formularkomponente aus dem AEM Sidekick auf das Fragment ziehen. Weitere Informationen zu adaptiven Formularkomponenten finden Sie unter [Einführung in das Authoring adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

Wenn Sie außerdem ein XML-Schema oder eine XDP-Formularvorlage als Formularmodell für Ihr Fragment ausgewählt haben, wird in der Inhaltssuche eine neue Registerkarte mit der Formularmodellhierarchie angezeigt. Sie können dann Formularmodellelemente per Drag-and-Drop auf das Fragment ziehen. Die hinzugefügten Formularmodellelemente werden in Formularkomponenten konvertiert, während die ursprünglichen Eigenschaften aus der zugehörigen XDP oder XSD beibehalten werden.

### Bereich als Fragment speichern {#save-panel-as-a-fragment}

1. Öffnen Sie ein adaptives Formular, das den Bereich enthält, den Sie als adaptives Formularfragment speichern möchten.
1. Klicken Sie in der Symbolleiste des Bedienfelds auf **[!UICONTROL Als Fragment speichern]**. Das Dialogfeld „Als Fragment speichern“ wird geöffnet.

   >[!NOTE]
   >
   >Wenn das Bedienfeld, das Sie gerade speichern, ein untergeordnetes Bedienfeld enthält, wird dieses auch im resultierenden Fragment enthalten sein.

1. Geben Sie im Dialogfeld „Fragmenterstellung“ die folgenden Informationen an:

   * **Name**: Name des Fragments. Der Standardwert ist der Elementname des Bedienfelds. Dies ist ein Pflichtfeld.
     >[!NOTE]
     >
     >Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.

   * **Titel**: Titel des Formulars. Der Standardwert ist der Titel des Bedienfelds.

   * **Beschreibung**: Beschreibung des Fragments.

   * **Tags**: Kennzeichnet Metadaten für das Fragment.

   * **Zielpfad**: Pfad für das Repository, in dem das Fragment gespeichert wird. Wenn Sie keinen Pfad angeben, wird neben dem Knoten, der das adaptive Formular enthält, ein Knoten mit demselben Namen wie der des Fragments erstellt. Das Fragment wird in diesem Knoten gespeichert.

   * **Formularmodell**: Je nach Formularmodell für das adaptive Formular zeigt dieses Feld die **XML-Schema**, **Formularvorlage** oder **Keines**. Dies ist ein Feld, das nicht bearbeitet werden kann.

   * **Fragmentmodellstamm**: Wird nur in XSD-basierten adaptiven Formularen angezeigt. Sie gibt den Stamm für das Fragmentmodell an. Sie können auch **/** oder den komplexen XSD-Typ aus der Dropdown-Liste auswählen. Beachten Sie, dass Sie das Fragment nur in einem anderen adaptiven Formular wiederverwenden können, wenn Sie den komplexen Typ als Fragmentmodellstamm auswählen.
Wenn Sie **/** als Fragmentmodellstamm auswählen, wird die vollständige XSD-Struktur vom Stamm in der Registerkarte für das Datenmodell des adaptiven Formulars angezeigt. Für Fragmentmodellstamm eines komplexen Typs sind nur die untergeordneten Elemente des ausgewählten komplexen Typs auf der Registerkarte des Datenmodells des adaptiven Formulars sichtbar. Wenn Sie ein Fragment erstellen und einen komplexen Typ als **Fragmentmodellstamm** können Sie sie überall dort verwenden, wo dieser komplexe Typ verwendet wird, entweder innerhalb desselben Formulars oder über mehrere Formulare hinweg.

   * **XSD-REF**: Diese Option ist nur in den XSD-basierten adaptiven Formularen verfügbar. Sie zeigt den Ort des XML-Schemas an.

   * **XDP Ref**: Wird nur in XDP-basierten adaptiven Formularen angezeigt. Es wird der Speicherort der XDP-Vorlage angezeigt.

   ![save-fragment](assets/save-fragment.png)

   Dialogfeld „Als Fragment speichern“

1. Klicken Sie auf **OK**.

   Das Bedienfeld wird am angegebenen oder am Standardspeicherort im Repository gespeichert. Im adaptiven Formular wird das Bedienfeld durch eine Momentaufnahme des Fragments ersetzt. Wie unten gezeigt, werden das Bedienfeld „Allgemeine Informationen“ und seine untergeordneten Bedienfelder, „Persönliche Informationen“ und „Adresse“, als Fragment gespeichert.

   Um das Fragment zu bearbeiten, klicken Sie in der Symbolleiste des Bedienfelds auf das Symbol **[!UICONTROL Element bearbeiten]**. Das Fragment wird in einer neuen Registerkarte oder einem neuen Fenster im Bearbeitungsmodus geöffnet.

   ![Bearbeiten von Fragmenten](assets/edit-fragment.png)

## Arbeiten mit Fragmenten {#working-with-fragments}

### Konfigurieren des Erscheinungsbildes von Fragmenten {#configure-fragment-appearance}

Jedes Fragment, das Sie in adaptive Formulare einfügen, wird als Platzhalterbild angezeigt. Der Platzhalter zeigt die Titel von bis zu maximal zehn untergeordneten Bedienfeldern im Fragment an. Sie können AEM Forms so konfigurieren, dass das vollständige Fragment anstelle des Platzhalterbilds angezeigt wird.

Führen Sie die folgenden Schritte aus, um vollständige Fragmente in Formularen anzuzeigen:

1. Wechseln Sie zur Seite zur Konfiguration der AEM-Web-Konsole unter https://[*Host*]:[*Port*]/system/console/configMgr.

1. Suchen und klicken Sie auf **[!UICONTROL Webkanal-Konfiguration für adaptive Formulare und interaktive Kommunikation]**, um sie im Bearbeitungsmodus zu öffnen.
1. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Platzhalter anstelle des Fragments aktivieren]**, um vollständige Fragmente anstelle des Platzhalterbildes anzuzeigen.

### Einfügen eines Fragments in ein adaptives Formular {#insert-a-fragment-in-an-adaptive-form}

Die von Ihnen erstellten adaptiven Formularfragmente werden auf der Registerkarte Adaptive Formularfragmente in der AEM Inhaltssuche angezeigt. Einfügen eines adaptiven Formularfragments in ein adaptives Formular:

1. Öffnen Sie das adaptive Formular im Bearbeitungsmodus, in das Sie ein adaptives Formularfragment einfügen möchten.
1. Klicken Sie in der Seitenleiste auf **Assets** ![assets-browser](assets/assets-browser.png). Wählen Sie im Assets-Browser **Adaptive Formularfragmente** aus der Dropdown-Liste.

   Sie können auch festlegen, dass alle adaptiven Formularfragmente angezeigt oder nach Formularmodell (Formularvorlage, XML-Schema oder Allgemein) gefiltert werden.

1. Ziehen Sie ein adaptives Formularfragment per Drag-and-Drop in das adaptive Formular.

   >[!NOTE]
   >
   >Das Fragment des adaptiven Formulars ist nicht für das Authoring vom adaptiven Formular aus aktiviert. Außerdem können Sie kein XSD-basiertes Fragment in einem JSON-basierten adaptiven Formular und umgekehrt verwenden.

Das adaptive Formularfragment wird als Verweis in das adaptive Formular eingefügt und mit dem eigenständigen adaptiven Formularfragment synchronisiert. Das bedeutet, dass die Änderungen beim Aktualisieren des adaptiven Formularfragments in allen adaptiven Formularen übernommen werden, in denen das Fragment verwendet wird.

### Einbetten eines Fragments in ein adaptives Formular {#embed-a-fragment-in-adaptive-form}

Sie können ein adaptives Formularfragment in ein adaptives Formular einbetten, indem Sie in der Symbolleiste des hinzugefügten Fragments auf **Fragment einbetten: &lt;*fragmentName*>** (siehe Beispielbild unten) klicken.

![Einbetten eines Formularfragments in ein adaptives Formular](assets/embed-fragment.png)

>[!NOTE]
>
>Das eingebettete Fragment ist nicht mehr mit dem eigenständigen Fragment verknüpft. Sie können die Komponenten im eingebetteten Fragment aus dem adaptiven Formular heraus bearbeiten.

### Verwenden von Fragmenten innerhalb von Fragmenten {#using-fragments-within-fragments}

Sie können verschachtelte adaptive Formularfragmente erstellen, d. h. Sie können ein Fragment per Drag-and-Drop in ein anderes Fragment ziehen und eine verschachtelte Fragmentstruktur haben.

### Ändern von Fragmenten {#change-fragments}

Sie können ein adaptives Formularfragment durch ein anderes ersetzen oder ändern, indem Sie **Fragment-Asset auswählen** -Eigenschaft im Dialogfeld &quot;Komponente bearbeiten&quot;für ein adaptives Formularfragment-Bedienfeld.

### Generieren des Datensatzdokuments für adaptives Formularfragment {#generate-DOR-for-fragments}

Mit dem Datensatzdokument (Document of Record, DOR) können Sie Informationen zu Ihren Formularen im Druck- oder Dokumentformat speichern. Dadurch können Sie jederzeit Informationen über Ihre Kunden nachverfolgen und mithilfe des Datensatzdokuments Formulare und Inhalte im PDF-Format archivieren. [Erfahren Sie, wie Sie ein Datensatzdokument für adaptive Formularfragmente generieren](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).

### Verwenden eines Formularfragments mehrmals in einem adaptiven Formular {#using-form-fragment-mutiple-times-in-af}

Sie können ein schemabasiertes Formularfragment mehrmals in einem adaptiven Formular verwenden, um Daten eindeutig für jedes Formularfragmentfeld zu speichern. Sie können beispielsweise ein Adressformularfragment verwenden, um Adressdetails für permanente Kommunikation und die Darstellung lebender Adressen in einem Kreditantragsformular zu erfassen.

![Verwenden mehrerer Fragmente im adaptiven Formular](/help/forms/using/assets/using-multiple-fragment-af.gif)

>[!NOTE]
>
> * Wenn Sie nicht basierte Formularfragmente mehrmals in einem adaptiven Formular verwenden, erfolgt eine Datensynchronisation zwischen den Feldern der Fragmente. Das Problem mit der Datensynchronisierung tritt nicht in auf Kernkomponenten basierenden Formularfragmenten auf, in denen Sie ein Fragment entweder schemabasiert oder nicht-basiert mehrmals in einem Formular verwenden können.

## Automatisches Zuordnen von Fragmenten für die Datenbindung {#auto-mapping-of-fragments-for-data-binding}

Wenn Sie ein adaptives Formularfragment mit einer XFA-Formularvorlage oder einem komplexen XSD-Typ erstellen und das Fragment in ein adaptives Formular ziehen, wird das XFA-Fragment oder der komplexe XSD-Typ automatisch durch das entsprechende adaptive Formularfragment ersetzt, dessen Fragmentmodellstamm dem XFA-Fragment oder komplexen XSD-Typ zugeordnet ist.

Das Fragment-Asset und dessen Bindungen können im Dialogfeld „Komponente bearbeiten“ geändert werden.

>[!NOTE]
>
>Sie können auch ein gebundenes adaptives Formularfragment aus der Bibliothek für adaptive Formularfragmente per Drag-and-Drop in AEM Inhaltssuche ziehen und die richtige Bindungsverweis aus dem Dialogfeld &quot;Komponente bearbeiten&quot;des Bereichs für adaptive Formularfragmente bereitstellen.

## Verwalten von Fragmenten {#manage-fragments}

Sie können mithilfe der AEM Forms-Benutzeroberfläche mehrere Vorgänge für adaptive Formularfragmente ausführen.

1. Rufen Sie `https://[hostname]:'port'/aem/forms.html` auf.

1. Klicks **Auswählen** Wählen Sie in der Symbolleiste der AEM Forms-Benutzeroberfläche ein adaptives Formularfragment aus. In der Symbolleiste werden die folgenden Vorgänge angezeigt, die Sie für das ausgewählte adaptive Formularfragment ausführen können.

<table>
 <tbody>
  <tr>
   <td><p><strong>Vorgang</strong></p> </td>
   <td><p><strong>Beschreibung</strong></p> </td>
  </tr>
  <tr>
   <td><p>Öffnen</p> </td>
   <td><p>Öffnet das ausgewählte adaptive Formularfragment im Bearbeitungsmodus.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Eigenschaften anzeigen</p> </td>
   <td><p>Öffnet das Bedienfeld „Eigenschaften“. Im Bedienfeld „Eigenschaften“ können Sie Eigenschaften anzeigen und bearbeiten, eine Vorschau erstellen und ein Miniaturbild für das ausgewählte Fragment hochladen. Weitere Informationen finden Sie unter <a href="../../forms/using/manage-form-metadata.md" target="_blank">Verwalten von Metadaten</a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Kopieren</p> </td>
   <td><p>Kopiert das ausgewählte Fragment. Das Symbol „Einfügen“ wird in der Symbolleiste angezeigt.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Download</p> </td>
   <td><p>Lädt das ausgewählte Fragment herunter.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Vorschau</p> </td>
   <td><p>Enthält Optionen zum Anzeigen einer HTML- oder benutzerdefinierten Vorschau des Fragments durch Zusammenführen von Daten aus einer XML-Datei und dem Fragment. Weitere Informationen finden Sie unter <a href="/help/forms/using/previewing-forms.md" target="_blank">Erstellen einer Vorschau für ein Formular</a>. <br /><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Review starten/verwalten</p> </td>
   <td><p>Initiieren und Verwalten einer Review des ausgewählten Fragments. Weitere Informationen finden Sie unter <a href="../../forms/using/create-reviews-forms.md" target="_blank">Erstellen und Verwalten von Reviews</a>. <br /><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Wörterbuch erstellen</p> </td>
   <td><p>Erzeugt ein Wörterbuch zum Lokalisieren des ausgewählten Fragments. Weitere Informationen finden Sie unter <a href="/help/forms/using/lazy-loading-adaptive-forms.md" target="_blank">Lokalisieren adaptiver Formulare</a>. <br /><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Veröffentlichen/Veröffentlichung rückgängig machen</p> </td>
   <td><p>Veröffentlicht das ausgewählte Fragment bzw. macht die Veröffentlichung rückgängig.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Löschen</p> </td>
   <td><p>Löscht das ausgewählte Fragment.<br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Lokalisieren von adaptiven Formularen mit Fragmenten {#localizing-adaptive-form-containing-fragments}

Um ein adaptives Formular zu lokalisieren, das adaptive Formularfragmente enthält, müssen Sie das Fragment und das Formular separat lokalisieren. Es wird empfohlen, ein Fragment einmal zu lokalisieren und es in mehreren adaptiven Formularen wiederzuverwenden.

>[!NOTE]
>
>Die Lokalisierungsschlüssel im Fragment werden nicht in der XLIFF-Datei für ein adaptives Formular angezeigt.

## Wichtige Hinweise zum Arbeiten mit Fragmenten {#key-points-to-remember-when-working-with-fragments}

* Stellen Sie sicher, dass der Fragmentname eindeutig ist. Das Fragment kann nicht erstellt werden, wenn ein vorhandenes Fragment mit demselben Namen vorhanden ist.
* Wenn Sie in einem XDP-basierten adaptiven Formular ein Bedienfeld speichern, das ein anderes XDP-Fragment enthält, wird das daraus resultierende Fragment automatisch an das untergeordnete XDP-Fragment gebunden. Wenn ein XSD-basiertes adaptives Formular vorhanden ist, wird das resultierende Fragment an den Schemastamm gebunden.
* Wenn Sie ein adaptives Formularfragment erstellen, wird ein Fragmentknoten erstellt, der dem Knoten „guideContainer“ für ein adaptives Formular in CRXDe Lite ähnelt.
* Ein Fragment in einem adaptiven Formular, das ein anderes Formulardatenmodell verwendet, wird nicht unterstützt. Beispielsweise wird ein XDP-basiertes Fragment in einem XSD-basierten adaptiven Formular nicht unterstützt und umgekehrt.
* Adaptive Formularfragmente sind über die Registerkarte Adaptive Formularfragmente in AEM Inhaltssuche verfügbar.
* Alle Ausdrücke, Skripte oder Stile in einem eigenständigen adaptiven Formularfragment bleiben erhalten, wenn es als Verweis eingefügt oder in ein adaptives Formular eingebettet wird.
* Sie können ein adaptives Formularfragment, das als Verweis eingefügt wird, nicht in einem adaptiven Formular bearbeiten. Sie bearbeiten das eigenständige adaptive Formularfragment oder betten das Fragment im adaptiven Formular ein.
* Wenn Sie ein adaptives Formular veröffentlichen, müssen Sie die eigenständigen adaptiven Formularfragmente veröffentlichen, die als Verweis in das adaptive Formular eingefügt wurden.
* Wenn Sie ein aktualisiertes adaptives Formularfragment erneut veröffentlichen, werden die Änderungen in den veröffentlichten Instanzen des adaptiven Formulars übernommen, in denen das Fragment verwendet wird.
* Das adaptive Formular, das die Überprüfungskomponente enthält, unterstützt keine anonymen Benutzer. Außerdem wird nicht empfohlen, die Verify-Komponente in einem adaptiven Formularfragment zu verwenden.
* (**Nur Mac**) Um sicherzustellen, dass die Formularfragmentfunktionalität in allen Szenarien einwandfrei funktioniert, fügen Sie der Datei „/private/etc/hosts“ den folgenden Eintrag hinzu:
  `127.0.0.1 <Host machine>` **Hostcomputer**: Der Apple Mac-Computer, auf dem AEM Forms bereitgestellt wird.

## Referenzfragmente {#reference-fragments}

Es sind Referenzfragmente für adaptive Formulare verfügbar, mit denen Sie Ihr Formular erstellen können. Weitere Informationen finden Sie unter [Referenzfragmente](../../forms/using/reference-adaptive-form-fragments.md).
