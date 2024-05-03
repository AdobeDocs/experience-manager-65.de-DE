---
title: Adaptive Formularfragmente
description: Adaptive Formulare bietet einen Mechanismus zum Erstellen eines Formularsegments (z. B. eines Bedienfelds oder einer Gruppe von Feldern) und zum Nutzen des Segments in einem beliebigen adaptiven Formular. Sie können auch ein vorhandenes Bedienfeld als Fragment speichern.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
discoiquuid: 1a32eb24-db3b-4fad-b1c7-6326b5af4e5e
docset: aem65
exl-id: 2f276e9d-b3c1-48f7-a94a-bdf7eb15a031
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '2372'
ht-degree: 100%

---

# Adaptive Formularfragmente{#adaptive-form-fragments}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/adaptive-form-fragments-core-components.html?lang=de) |
| AEM 6.5 | Dieser Artikel |

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

Zwar wird jedes Formular für einen bestimmten Zweck entwickelt, aber in den meisten Formularen gibt es gängige Segmente für persönliche Angaben wie Name und Anschrift, Familienstand und Einkommen. Eine Formularentwicklerin bzw. ein Formularentwickler muss diese gängigen Segmente jedes Mal erstellen, wenn ein neues Formular erstellt wird.

Adaptive Formulare bieten einen praktischen Mechanismus, mit dem Formularsegmente wie ein Bedienfeld oder eine Gruppe von Feldern nur einmal erstellt werden müssen und dann in adaptiven Formularen wiederverwendet werden können. Diese wiederverwendbaren, unabhängigen Segmente werden als adaptive Formularfragmente bezeichnet.

>[!NOTE]
>
> Mit dem [Konfigurationsdialogfeld und dem Design-Dialogfeld der Formularfragment-Komponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/form-fragment.html?lang=de) können Sie Ihre Fragmente ganz einfach an die Bedürfnisse der Benutzenden anpassen.

## Erstellen eines Fragments {#create-a-fragment}

Sie können adaptive Formularfragmente von Grund auf neu erstellen oder ein Bedienfeld in einem vorhandenen adaptiven Formular als Fragment speichern.

### Neuerstellen von Fragmenten {#create-fragment-from-scratch}

1. Melden Sie sich bei der Author-Instanz von AEM Forms unter https://[*Hostname*]:[*Port*]/aem/forms.html an.
1. Klicken Sie auf **Erstellen > Adaptives Formularfragment**.
1. Geben Sie Titel, Name, Beschreibung und Tags für das Fragment an.

   >[!NOTE]
   >
   >Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.

1. Klicken Sie, um die Registerkarte **Formularmodell** zu öffnen. Wählen Sie dann aus der Dropdown-Liste **Auswählen** eines der folgenden Fragmentmodelle:

   * **Keine**: Gibt an, dass das Fragment von Grund auf ohne Formularmodell erstellt werden soll.

     >[!NOTE]
     >
     > Im adaptiven Formularen, die auf Kernkomponenten basieren, können Sie ein einzelnes Formularfragment mehrmals in einem Formular verwenden. Es werden sowohl auf nichts basierende als auch schemabasierte Formularfragmente unterstützt.

   * **Formularvorlage**: Das Fragment mit mithilfe einer XDP-Vorlage erstellt, die auf AEM Forms hochgeladen wurde. Wählen Sie die entsprechende XDP-Vorlage als Formularmodell für das Fragment aus.

   ![Erstellen eines adaptiven Formulars mit einer Formularvorlage als Modell](assets/form-template-model.png)

   Die Teilformulare, die als Fragmente in der ausgewählten Vorlage markiert sind, werden ebenfalls angezeigt. Sie können ein Teilformular für ein adaptives Formularfragment aus der Dropdown-Liste auswählen.

   ![Auswählen von Teilformularen aus der angegebenen Formularvorlage](assets/fragment-subform.png)

   Außerdem können Sie ein adaptives Formularfragment aus Unterformularen erstellen, die nicht als Fragmente in der Formularvorlage markiert sind, indem Sie den SOM-Ausdruck für das Unterformular in der Dropdown-Liste angeben.

   * **XML-Schema**: Das Fragment wird mithilfe eines XML-Schemas erstellt, das auf AEM Forms hochgeladen wurde. Sie können ein XML-Schema als Formularmodell hochladen oder aus den verfügbaren Schemas wählen.

   ![Erstellen eines adaptiven Formularfragments, das auf einem XML-Schema basiert](assets/xml-schema-model.png)

   Sie können ein adaptives Formularfragment auch erstellen, indem Sie einen „complexType“ im ausgewählten Schema aus der Dropdownliste wählen.

   ![Wählen Sie einen komplexen Typ aus dem angegebenen XML-Schema-Modell.](assets/complex-type.png)

1. Klicken Sie auf **Erstellen** und dann auf **Öffnen**, um das Fragment mit einer Standardvorlage im Bearbeitungsmodus zu öffnen.

Im Bearbeitungsmodus können Sie eine beliebige adaptive Formularkomponente aus dem AEM-Sidekick auf das Fragment ziehen. Weitere Informationen zu adaptiven Formularkomponenten finden Sie in der [Einführung in das Authoring adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

Wenn Sie außerdem ein XML-Schema oder eine XDP-Formularvorlage als Formularmodell für Ihr Fragment ausgewählt haben, wird in der Inhaltssuche eine neue Registerkarte mit der Formularmodellhierarchie angezeigt. Sie können dann Formularmodellelemente auf das Fragment ziehen. Die hinzugefügten Formularmodellelemente werden in Formularkomponenten konvertiert, wobei die ursprünglichen Eigenschaften des verbundenen XDP oder XSD beibehalten werden.

### Bereich als Fragment speichern {#save-panel-as-a-fragment}

1. Öffnen Sie ein adaptives Formular mit dem Panel, das Sie als adaptives Formularfragment speichern möchten.
1. Klicken Sie in der Symbolleiste des Bedienfelds auf **[!UICONTROL Als Fragment speichern]**. Das Dialogfeld „Als Fragment speichern“ wird geöffnet.

   >[!NOTE]
   >
   >Wenn das Bedienfeld, das Sie als Fragment speichern, ein untergeordnetes Bedienfeld umfasst, ist dieses auch im resultierenden Fragment enthalten.

1. Geben Sie im Dialogfeld für die Fragmenterstellung die folgenden Informationen an:

   * **Name**: Name des Fragments. Der Standardwert ist der Elementname des Panels. Dies ist ein Pflichtfeld.
     >[!NOTE]
     >
     >Stellen Sie sicher, dass Sie einen eindeutigen Namen für das Fragment angeben. Wenn ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.

   * **Titel**: Titel des Formulars. Der Standardwert ist der Titel des Bedienfelds.

   * **Beschreibung**: Beschreibung des Fragments.

   * **Tags**: Kennzeichnet Metadaten für das Fragment.

   * **Zielpfad**: Pfad zum Repository, in dem das Fragment gespeichert wird. Wenn Sie keinen Pfad angeben, wird ein Knoten mit dem Namen des Fragments neben dem Knoten erstellt, der das adaptive Formular enthält. Das Fragment wird in diesem Knoten gespeichert.

   * **Formularmodell**: Je nach Formularmodell für das adaptive Formular wird im Feld das **XML-Schema**, die **Formularvorlage** oder **Keine** angezeigt. Dies ist ein Feld, das nicht bearbeitet werden kann.

   * **Fragmentmodellstamm**: Diese Option wird nur in XSD-basierten adaptiven Formularen angezeigt. Sie gibt den Stamm für das Fragmentmodell an. Sie können auch **/** oder den komplexen XSD-Typ aus der Dropdown-Liste auswählen. Sie können das Fragment nur in einem anderen adaptiven Formular wiederverwenden, wenn Sie als Fragmentmodellstamm den komplexen Typ auswählen.
Wenn Sie **/** als Fragmentmodellstamm auswählen, wird die vollständige XSD-Struktur vom Stamm in der Registerkarte für das Datenmodell des adaptiven Formulars angezeigt. Für einen Fragmentmodellstamm mit komplexem Typ werden lediglich die untergeordneten Elemente des ausgewählten komplexen Typs auf der Registerkarte „Datenmodell“ des adaptiven Formulars angezeigt. Wenn Sie ein Fragment erstellen und einen komplexen Typ als **Fragmentmodellstamm** festlegen, können Sie es überall dort einsetzen, wo dieser komplexe Typ verwendet wird (entweder innerhalb desselben Formulars oder formularübergreifend).

   * **XSD-REF**: Diese Option ist nur in den XSD-basierten adaptiven Formularen verfügbar. Sie zeigt den Ort des XML-Schemas an.

   * **XDP-Ref**: Diese Option wird nur in XDP-basierten adaptiven Formularen angezeigt. Es wird der Speicherort der XDP-Vorlage angezeigt.

   ![save-fragment](assets/save-fragment.png)

   Dialogfeld „Als Fragment speichern“.

1. Klicken Sie auf **OK**.

   Das Panel wird am angegebenen oder am Standardspeicherort im Repository gespeichert. In einem adaptiven Formular wird das Panel durch eine Momentaufnahme des Fragments ersetzt. Wie unten gezeigt, werden das Bedienfeld „Allgemeine Informationen“ und seine untergeordneten Bedienfelder, „Persönliche Informationen“ und „Adresse“, als Fragment gespeichert.

   Um das Fragment zu bearbeiten, klicken Sie in der Symbolleiste des Bedienfelds auf das Symbol **[!UICONTROL Element bearbeiten]**. Das Fragment wird auf einer neuen Registerkarte oder in einem neuen Fenster im Bearbeitungsmodus geöffnet.

   ![Bearbeiten von Fragmenten](assets/edit-fragment.png)

## Arbeiten mit Fragmenten {#working-with-fragments}

### Konfigurieren des Erscheinungsbildes von Fragmenten {#configure-fragment-appearance}

Alle Fragmente, die Sie in adaptive Formulare einfügen, werden als Platzhalterbild angezeigt. Der Platzhalter zeigt die Titel von bis zu maximal zehn untergeordneten Bedienfeldern im Fragment an. Sie können AEM Forms so konfigurieren, dass das vollständige Fragment anstelle des Platzhalterbilds angezeigt wird.

Führen Sie die folgenden Schritte aus, um vollständige Fragmente in Formularen anzeigen zu können:

1. Wechseln Sie zur Seite zur Konfiguration der AEM-Web-Konsole unter https://[*Host*]:[*Port*]/system/console/configMgr.

1. Suchen Sie die **[!UICONTROL Web-Kanal-Konfiguration für adaptive Formulare und interaktive Kommunikation]** und klicken Sie darauf, um sie im Bearbeitungsmodus zu öffnen.
1. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Platzhalter anstelle des Fragments aktivieren]**, um vollständige Fragmente anstelle des Platzhalterbildes anzuzeigen.

### Einfügen eines Fragments in ein adaptives Formular {#insert-a-fragment-in-an-adaptive-form}

Die adaptiven Formularfragmente, die Sie erstellen, werden auf der Registerkarte „Adaptive Formularfragmente“ der AEM-Inhaltssuche angezeigt. So fügen Sie ein adaptives Formularfragment in ein adaptives Formular ein:

1. Öffnen Sie im Bearbeitungsmodus das adaptive Formular, in das Sie ein adaptives Formularfragment einfügen möchten.
1. Klicken Sie in der Seitenleiste auf **Assets** ![assets-browser](assets/assets-browser.png). Wählen Sie im Assets-Browser **Adaptive Formularfragmente** aus der Dropdown-Liste.

   Sie können auch festlegen, dass alle adaptiven Formularfragmente angezeigt werden oder dass nach Formularmodell (Formularvorlage, XML-Schema oder Allgemein) gefiltert wird.

1. Ziehen Sie ein adaptives Formularfragment auf das adaptive Formular.

   >[!NOTE]
   >
   >Das Fragment des adaptiven Formulars ist nicht für das Authoring vom adaptiven Formular aus aktiviert. Darüber hinaus ist es nicht möglich, ein XSD-basiertes Fragment in einem JSON-basierten adaptiven Formular und umgekehrt zu verwenden.

Das adaptive Formularfragment wird als Verweis in das adaptive Formular eingefügt und mit dem eigenständigen adaptiven Formularfragment synchronisiert. Das bedeutet, dass beim Aktualisieren des adaptiven Formularfragments die Änderungen in allen adaptiven Formularen übernommen werden, in denen das Fragment verwendet wird.

### Einbetten eines Fragments in ein adaptives Formular {#embed-a-fragment-in-adaptive-form}

Sie können ein adaptives Formularfragment in ein adaptives Formular einbetten, indem Sie in der Symbolleiste des hinzugefügten Fragments auf **Fragment einbetten: &lt;*fragmentName*>** (siehe Beispielbild unten) klicken.

![Einbetten eines Formularfragments in ein adaptives Formular](assets/embed-fragment.png)

>[!NOTE]
>
>Das eingebettete Fragment ist nicht mehr mit dem eigenständigen Fragment verknüpft. Sie können die Komponenten im eingebetteten Fragment aus dem adaptiven Formular heraus bearbeiten.

### Verwenden von Fragmenten innerhalb von Fragmenten {#using-fragments-within-fragments}

Sie können verschachtelte adaptive Formularfragmente erstellen, d. h. ein Fragment in ein anderes Fragment ziehen, um eine verschachtelte Fragmentstruktur zu erhalten.

### Ändern von Fragmenten {#change-fragments}

Sie können ein adaptives Formularfragment ändern oder durch ein anderes ersetzen, indem Sie im Dialogfeld „Komponente bearbeiten“ die Eigenschaft **Fragment-Asset auswählen** für ein Panel mit adaptivem Formularfragment verwenden.

### Generieren eines Datensatzdokuments für adaptive Formularfragmente {#generate-DOR-for-fragments}

Mit dem Nachweis (Document of Record, DoR) können Sie Informationen zu Ihren Formularen im Druck- oder Dokumentformat speichern. Dadurch können Sie jederzeit Informationen über Ihre Kundinnen und Kunden nachverfolgen und mithilfe des Nachweises Formulare und Inhalte im PDF-Format archivieren. [Erfahren Sie, wie Sie ein Datensatzdokument für adaptive Formularfragmente generieren](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md).

### Mehrfaches Verwenden eines Formularfragments in einem adaptiven Formular {#using-form-fragment-mutiple-times-in-af}

Sie können ein schemabasiertes Formularfragment mehrfach in einem adaptiven Formular verwenden, um Daten für jedes Formularfragmentfeld eindeutig zu speichern. Es ist beispielsweise möglich, ein Adressformularfragment zu verwenden, um Adressangaben zum ständigen Wohnsitz, zur Kommunikation und zum aktuellen Wohnsitz in einem Kreditantragsformular zu erfassen.

![Verwenden mehrerer Fragmente in einem adaptiven Formular](/help/forms/using/assets/using-multiple-fragment-af.gif)

>[!NOTE]
>
> * Wenn Sie auf nichts basierende Formularfragmente mehrfach in einem adaptiven Formular verwenden, wird eine Datensynchronisierung zwischen den Feldern der Fragmente durchgeführt. Das Problem mit der Datensynchronisierung tritt nicht in auf Kernkomponenten basierenden Formularfragmenten auf, bei denen Sie ein Fragment entweder auf einem Schema basierend oder auf nichts basierend mehrmals in einem Formular verwenden können.

## Automatisches Zuordnen von Fragmenten für die Datenbindung {#auto-mapping-of-fragments-for-data-binding}

Wenn Sie ein adaptives Formularfragment mit einer XFA-Formularvorlage oder einem komplexen XSD-Typ erstellen und es auf ein adaptives Formular ziehen, wird das XFA-Fragment bzw. der komplexe XSD-Typ automatisch durch das entsprechende adaptive Formularfragment ersetzt, dessen Fragmentmodellstamm dem XFA-Fragment bzw. komplexen XSD-Typ zugeordnet ist.

Das Fragment-Asset und dessen Bindungen können im Dialogfeld „Komponente bearbeiten“ geändert werden.

>[!NOTE]
>
>Sie können auch ein gebundenes adaptives Formularfragment aus der adaptiven Formularfragment-Bibliothek in der AEM-Inhaltssuche ziehen und den richtigen Bindungsverweis aus dem Dialogfeld „Komponente bearbeiten“ des Panels des adaptiven Formularfragments angeben.

## Verwalten von Fragmenten {#manage-fragments}

Sie können mithilfe von AEM Forms mehrere Aktionen für adaptive Formularfragmente ausführen.

1. Rufen Sie `https://[hostname]:'port'/aem/forms.html` auf.

1. Klicken Sie in der Symbolleiste der AEM Forms-Benutzeroberfläche auf **Auswählen** und wählen Sie ein adaptives Formularfragment aus. Die Symbolleiste zeigt die folgenden Vorgänge an, die Sie für das ausgewählte adaptive Formularfragment ausführen können.

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
   <td><p>Kopiert das ausgewählte Fragment. Die Schaltfläche „Einfügen“ wird in der Symbolleiste angezeigt.<br /> <br /> </p> </td>
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
   <td><p>Generiert ein Wörterbuch zum Lokalisieren des ausgewählten Fragments. Weitere Informationen finden Sie unter <a href="/help/forms/using/lazy-loading-adaptive-forms.md" target="_blank">Lokalisieren adaptiver Formulare</a>. <br /><br /> </p> </td>
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

Zum Lokalisieren eines adaptiven Formulars, das adaptive Formularfragmente enthält, müssen Sie die Fragmente und das Formular separat lokalisieren. Auf diese Weise muss ein Fragment nur einmal lokalisiert werden und kann dann später in mehreren adaptiven Formularen wiederverwendet werden.

>[!NOTE]
>
>Die Lokalisierungsschlüssel im Fragment werden nicht in der XLIFF-Datei für ein adaptives Formular angezeigt.

## Wichtige Hinweise zum Arbeiten mit Fragmenten {#key-points-to-remember-when-working-with-fragments}

* Stellen Sie sicher, dass der Fragmentname eindeutig ist. Wenn bereits ein anderes Fragment mit demselben Namen vorhanden ist, kann das Fragment nicht erstellt werden.
* Wenn Sie in einem XDP-basierten adaptiven Formular ein Bedienfeld, das ein anderes XDP-Fragment enthält, als Fragment speichern, wird das daraus resultierende Fragment automatisch an das untergeordnete XDP-Fragment gebunden. Im Falle eines XSD-basierten adaptiven Formulars ist das resultierende Fragment an den Schemastamm gebunden.
* Wenn Sie ein adaptives Formularfragment erstellen, wird ein Fragmentknoten erstellt, der dem Knoten „guideContainer“ für ein adaptives Formular in CRXDE Lite ähnelt.
* Ein Fragment, das ein anderes Formulardatenmodell verwendet, wird in einem adaptiven Formular nicht unterstützt. Zum Beispiel wird in einem XSD-basierten adaptiven Formular ein XDP-basiertes Fragment nicht unterstützt und umgekehrt.
* Adaptive Formularfragmente sind auf der Registerkarte „Adaptive Formularfragmente“ der AEM-Inhaltssuche verfügbar.
* Alle Ausdrücke, Skripte oder Stile in einem eigenständigen adaptiven Formularfragment bleiben erhalten, wenn es als Verweis eingefügt oder in ein adaptives Formular eingebettet wird.
* Adaptive Formularfragmente, die als Verweis eingefügt wurden, können nicht in einem adaptiven Formular bearbeitet werden. Sie bearbeiten stattdessen entweder das eigenständige adaptive Formularfragment oder betten das Fragment in das adaptive Formular ein.
* Wenn Sie ein adaptives Formular veröffentlichen, müssen Sie die eigenständigen adaptiven Formularfragmente veröffentlichen, die als Verweis im adaptiven Formular eingefügt wurden.
* Wenn Sie ein aktualisiertes adaptives Formularfragment veröffentlichen, werden die Änderungen in den veröffentlichten Instanzen des adaptiven Formulars übernommen, in denen das Fragment verwendet wird.
* Adaptive Formulare, die die Überprüfungskomponente enthalten, unterstützen keine anonymen Benutzenden. Außerdem wird davon abgeraten, die Überprüfungskomponente in einem adaptiven Formularfragment zu verwenden.
* (**Nur Mac**) Um sicherzustellen, dass die Formularfragmentfunktionalität in allen Szenarien einwandfrei funktioniert, fügen Sie der Datei „/private/etc/hosts“ den folgenden Eintrag hinzu:
  `127.0.0.1 <Host machine>` **Hostcomputer**: Der Apple Mac-Computer, auf dem AEM Forms bereitgestellt wird.

## Referenzfragmente {#reference-fragments}

Es sind Referenzfragmente für adaptive Formulare verfügbar, die Sie zum Erstellen von Formularen verwenden können. Weitere Informationen finden Sie unter [Referenzfragmente](../../forms/using/reference-adaptive-form-fragments.md).
