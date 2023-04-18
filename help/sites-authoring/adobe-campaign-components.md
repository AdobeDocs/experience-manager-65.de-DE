---
title: Integration mit Adobe Campaign-Komponenten
description: Wenn Sie eine Integration mit Adobe Campaign durchführen, stehen Ihnen Komponenten für die Arbeit mit Newslettern und Formularen zur Verfügung.
uuid: a858d5ca-aa6e-4bde-92db-a6dcd8b48ae6
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 9da34dab-7e89-4127-ab26-532687746b2a
docset: aem65
exl-id: d1132fcd-e6a0-44a2-8753-d250f68fbd78
source-git-commit: f4b6eb2ded17ec641f23a1fc3b977ce77169c8a1
workflow-type: tm+mt
source-wordcount: '2828'
ht-degree: 65%

---

# Adobe Campaign-Komponenten{#adobe-campaign-components}

Wenn Sie eine Integration mit Adobe Campaign durchführen, stehen Ihnen Komponenten für die Arbeit mit Newslettern und Formularen zur Verfügung. Beide werden in diesem Dokument beschrieben.

>[!CAUTION]
>
>Die E-Mail-Komponenten von AEM werden nicht mehr unterstützt. Aufgrund der Art von E-Mails, bei denen Inhalt und Stil zusammengeführt werden, können die standardmäßig von AEM bereitgestellten E-Mail-Komponenten von Kunden nur eingeschränkt wiederverwendet werden, da benutzerdefinierte Stile in allen Komponenten implementiert werden müssen, die für Projekte erforderlich sind.
>
>E-Mail-Komponenten können auf Projektebene implementiert werden. Die veralteten AEM-E-Mail-Komponenten veranschaulichen, wie dies erreicht werden kann. Diese veralteten Komponenten sollten jedoch nicht für Projekte verwendet werden.

## Adobe Campaign-Newsletter-Komponenten {#adobe-campaign-newsletter-components}

Folgen Sie in den Campaign-Komponenten den Best Practices, die Sie unter [Best Practices für E-Mail-Vorlagen](/help/sites-administering/best-practices-for-email-templates.md) finden und die auf der Adobe-Markup-Sprache [HTL](https://helpx.adobe.com/de/experience-manager/htl/using/overview.html) basieren.

Wenn Sie eine E-Mail oder einen Newsletter öffnen, der oder die für die Integration mit Adobe Campaign konfiguriert wurde, werden Ihnen im Abschnitt **Adobe Campaign-Newsletter** folgende Optionen angezeigt:

* Überschrift (Kampagne)
* Bild (Kampagne)
* Link (Kampagne)
* Scene7-Bildvorlage (Kampagne)
* Zielgerichteter Verweis (Campaign)
* Text und Bild (Kampagne).
* Text und Personalisierung (Kampagne)

Eine Beschreibung dieser Komponenten finden Sie im folgenden Abschnitt.

Die Komponenten werden wie folgt angezeigt:

![chlimage_1-43](assets/chlimage_1-43.png)

### Überschrift (Kampagne) {#heading-campaign}

Die Überschriftenkomponente kann entweder:

* Den Namen der aktuellen Seite anzeigen, indem Sie die **Titel** Feld leer.
* Anzeigen von Text, den Sie im **Titel** -Feld.

Sie bearbeiten die **Überschrift (Kampagne)** direkt. Frei lassen, um den Seitentitel zu verwenden.

![chlimage_1-44](assets/chlimage_1-44.png)

Sie können Folgendes konfigurieren:

* **Titel**
Wenn Sie einen anderen Namen als den Seitentitel verwenden möchten, geben Sie ihn hier ein.

* **Überschriftenebene (1, 2, 3, 4)**
Die Überschriftenebene basierend auf der HTML-Überschriftgröße (1–4).

Im folgenden Beispiel sehen Sie, wie die Komponente „Überschrift (Kampagne)“ dargestellt wird.

![chlimage_1-45](assets/chlimage_1-45.png)

### Bild (Kampagne) {#image-campaign}

Die image-Komponente (Kampagne) zeigt ein Bild und begleitenden Text gemäß den angegebenen Parametern an.

Sie können ein Bild hochladen und es dann bearbeiten (z. B. zuschneiden, drehen, Link/Titel/Text hinzufügen).

Sie können ein Bild entweder per Drag-and-Drop aus dem [Asset-Browser](/help/sites-authoring/author-environment-tools.md#assetsbrowsertouchoptimizedui) direkt auf die Komponente oder ihre [Dialogfeld &quot;Konfigurieren&quot;](/help/sites-authoring/editing-content.md#editconfigurecopycutdeletepastetouchoptimizedui). Sie können auch ein Bild aus dem Dialogfeld &quot;Konfigurieren&quot;hochladen. Dieses Dialogfeld steuert auch alle Definitionen und Bearbeitungen des Bildes:

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>Sie müssen im Feld **ALT-Text** Informationen eingeben, da das Bild sonst nicht gespeichert werden kann.

Nachdem das Bild hochgeladen wurde (und nicht vorher), können Sie es mittels [Direktbearbeitung](/help/sites-authoring/editing-content.md#editcontenttouchoptimizedui) zuschneiden und drehen:

![](do-not-localize/chlimage_1-10.png)

>[!NOTE]
>
>Der integrierte Editor zeigt bei der Bearbeitung die Originalgröße und das Seitenverhältnis des Bildes an. Sie können auch die Höhe und die Breite festlegen. Alle in den Eigenschaften definierten Beschränkungen der Größe und des Seitenverhältnisses werden angewendet, sobald Sie Ihre Änderungen speichern.
>
>Abhängig von Ihrer Instanz können Mindest- und Höchstbeschränkungen auch durch das [Design der Seite](/help/sites-developing/designer.md) vorgegeben sein. Diese werden bei der Implementierung des Projekts festgelegt.

Im Vollbildbearbeitungsmodus stehen verschiedene zusätzliche Optionen zur Verfügung, beispielsweise Karte und Zoom:

![](do-not-localize/chlimage_1-11.png)

Wenn ein Bild geladen wird, können folgende Konfigurationen durchgeführt werden:

* **Zuweisen**
Wählen Sie „Zuweisen“ aus, um ein Bild zuzuweisen. Sie legen fest, wie die Imagemap (Rechteck, Polygon usw.) erstellt werden soll, und geben an, worauf der Bereich verweisen soll.

* **Zuschneiden**
Wählen Sie „Zuschneiden“ aus, um ein Bild zuzuschneiden. Verwenden Sie die Maus, um das Bild zuzuschneiden.

* **Drehen**
Wählen Sie „Drehen“ aus, um ein Bild zu drehen. Wiederholen Sie das Drehen so lange, bis das Bild die gewünschte Ausrichtung hat.

* **Entfernen**
Damit entfernen Sie das aktuelle Bild.

* Zoom-Leiste (nur klassische Benutzeroberfläche)
Verwenden Sie den Regler unter dem Bild (und über den Schaltflächen „OK“ und „Abbrechen“), um das Bild ein- und auszuzoomen.
* **Titel**
Der Titel des Bildes.

* **Alt-Text**
Ein alternativer Text, der für barrierefreie Inhalte verwendet wird.

* **Verknüpfen mit**
Erstellen Sie einen Link zu Assets oder anderen Seiten innerhalb Ihrer Website.

* **Beschreibung**
Eine Beschreibung des Bildes.

* **Größe**
Legt die Höhe und Breite des Bildes fest.

>[!NOTE]
>
>Sie müssen im Feld **ALT-Text** der Registerkarte **Erweitert** Informationen eingeben, da das Bild sonst nicht gespeichert werden kann und die folgende Fehlermeldung ausgegeben wird:
>
>`Validation failed. Verify the values of the marked fields.`

Im folgenden Beispiel sehen Sie, wie die Komponente „Bild (Kampagne)“ dargestellt wird.

![chlimage_1-47](assets/chlimage_1-47.png)

### Link (Kampagne) {#link-campaign}

Mit der Komponente Link (Kampagne) können Sie einen Link zu Ihrem Newsletter hinzufügen.

Folgendes können Sie in den Registerkarten **Anzeige**, **URL-Info** oder **Erweitert** konfigurieren:

* **Verknüpfungsbeschriftung**
Die Beschriftung des Links. Dies ist der Text, der den Benutzern angezeigt wird.

* **Link-QuickInfo**
Mit dieser Option werden weitere Informationen zur Verwendung des Links hinzugefügt.

* **LinkType**
Wählen Sie in der Dropdown-Liste zwischen 
**Benutzerdefinierte URL** und **Adaptives Dokument**. Dieses Feld ist obligatorisch. Wenn Sie &quot;Benutzerdefinierte URL&quot;auswählen, können Sie die Link-URL angeben. Wenn Sie Adaptives Dokument auswählen, können Sie den Dokumentpfad angeben.

* **Zusätzlicher URL-Parameter**
Fügen Sie weitere URL-Parameter hinzu. Klicken Sie auf „Element hinzufügen“, um mehrere Elemente hinzuzufügen.

>[!NOTE]
>
>Sie müssen im Feld **Verknüpfungstyp** auf der Registerkarte **URL-Info** Daten eingeben, da die Komponente sonst nicht gespeichert werden kann und folgende Fehlermeldung ausgegeben wird:
>
>`Validation failed. Verify the values of the marked fields.`

Im folgenden Beispiel sehen Sie, wie die Komponente „Link (Kampagne)“ dargestellt wird.

![chlimage_1-48](assets/chlimage_1-48.png)

### Dynamic Media Classic (Scene7)-Bildvorlage (Kampagne) {#scene-image-template-campaign}

Dynamic Media Classic Scene7-Bildvorlagen sind in Schichten angeordnete Bilddateien, in denen Inhalte und Eigenschaften mit Parametern versehen werden können, um sie zu variieren. Mithilfe der Komponente **[!UICONTROL Bildvorlage]** können Sie Scene7-Vorlagen in Newslettern verwenden und die Werte der Vorlagenparameter bearbeiten. Darüber hinaus können Sie Adobe Campaign-Metadatenvariablen innerhalb der Parameter nutzen, sodass allen Benutzenden eine personalisierte Version des Bilds angezeigt wird.

![chlimage_1-49](assets/chlimage_1-49.png)

Klicken Sie auf **Bearbeiten**, um die Komponente zu konfigurieren. Die in diesem Abschnitt beschriebenen Einstellungen lassen sich anpassen. Diese Scene7-Bildvorlage wird im Abschnitt [Scene7-Bildvorlagen-Komponente](/help/assets/scene7.md#image-template) ausführlich beschrieben.

Darüber hinaus listet das Parameterbedienfeld alle Vorlagenparameter auf, die für die Vorlage in Scene7 definiert wurden. Für jeden dieser Parameter können Sie den Wert anpassen, Variablen einfügen oder auf seinen Standardwert zurücksetzen.

![chlimage_1-50](assets/chlimage_1-50.png)

### Zielgerichteter Verweis (Campaign) {#targeted-reference-campaign}

Mit der Komponente Zielgerichteter Verweis (Kampagne) können Sie einen Verweis auf einen zielgerichteten Absatz erstellen.

In dieser Komponente navigieren Sie zum zielgerichteten Absatz, um ihn auszuwählen.

Klicken Sie auf das Ordnersymbol, um zu dem Absatz zu navigieren, auf den Sie verweisen möchten. Klicken Sie abschließend auf das Häkchen.

### Text und Bild (Kampagne). {#text-image-campaign}

Die Komponente Text und Bild (Kampagne) fügt einen Textblock und ein Bild hinzu.

Klicken Sie zur Konfiguration auf die Komponente und wählen Sie „Text“ oder „Bild“ aus.

![chlimage_1-51](assets/chlimage_1-51.png)

Auswählen **Text** zeigt einen Inline-Editor an:

![](do-not-localize/chlimage_1-12.png)

Auswählen **Bild** zeigt den Editor für Bilder im Kontext an:

![](do-not-localize/chlimage_1-13.png)

Siehe [Komponente &quot;Bild (Kampagne)&quot;](#image-campaign) für weitere Informationen zum Arbeiten mit Bildern. Siehe [Komponente &quot;Text und Personalisierung (Kampagne)&quot;](#text-personalization-campaign) für weitere Informationen zum Arbeiten mit Text.

Wie bei den Komponenten „Text und Personalisierung (Kampagne)“ und „Bild (Kampagne)“ können Sie Folgendes konfigurieren:

* **Text**
Geben Sie einen Text ein. Verwenden Sie die Symbolleiste, um die Formatierung zu ändern, Listen zu erstellen und Links hinzuzufügen.

* **Bild**
Ziehen Sie ein Bild aus dem Content Finder oder klicken Sie, um zu einem Bild zu navigieren. Schneiden Sie es gegebenenfalls zu oder drehen Sie es.

* **Bildeigenschaften** (**Erweiterte Bildeigenschaften**)
Sie können Folgendes festlegen:

   * **Titel**
Der Titel des Blocks, der angezeigt wird, wenn Sie mit der Maus darauf zeigen.

   * **ALT-Text**
Alternativer Text, der angezeigt wird, wenn das Bild nicht dargestellt werden kann.

   * **Verknüpfen mit**
Erstellen Sie einen Link zu Assets oder anderen Seiten innerhalb Ihrer Website.

   * **Beschreibung**
Eine Beschreibung des Bildes.

   * **Größe**
Legt die Höhe und Breite des Bildes fest.

>[!NOTE]
>
>Das Feld **ALT-Text** auf der Registerkarte **Erweitert** muss ausgefüllt werden, da die Komponente anderenfalls nicht gespeichert werden kann und folgende Fehlermeldung ausgegeben wird:
>
>`Validation failed. Verify the values of the marked fields.`

Im folgenden Beispiel sehen Sie, wie die Komponente „Text und Bild (Kampagne)“ dargestellt wird.

![chlimage_1-52](assets/chlimage_1-52.png)

### Text und Personalisierung (Kampagne) {#text-personalization-campaign}

Mit der Komponente „Text-und-Personalisierung (Kampagne)“ können Sie über einen WYSIWYG-Editor, dessen Funktionen der [Rich-Text-Editor](/help/sites-authoring/rich-text-editor.md) bereitstellt, einen Textblock eingeben. Darüber hinaus können Sie mithilfe dieser Komponente Kontextfelder und Personalisierungsblöcke aus Adobe Campaign verwenden. Weitere Informationen hierzu finden Sie unter [Personalisierungen einfügen](/help/sites-authoring/campaign.md#inserting-personalization).

Über mehrere Symbole können Sie den Text formatieren, darunter Schriftmerkmale, Ausrichtung, Links, Listen und Einzüge: Die Funktionalität ist für [beide Benutzeroberflächen](/help/sites-authoring/editing-content.md) grundsätzlich identisch, Aussehen und Verhalten unterscheiden sich jedoch:

![chlimage_1-53](assets/chlimage_1-53.png)

Im Editor für die Bearbeitung im Kontext können Sie Text hinzufügen, die Ausrichtung ändern, Links hinzufügen und entfernen, Kontextfelder oder Gestaltungsbausteine hinzufügen und in den Vollbildmodus wechseln. Wenn Sie Text/Personalisierung hinzugefügt haben, wählen Sie das Häkchen aus, um Ihre Änderungen zu speichern (oder x zum Abbrechen). Weitere Informationen finden Sie unter [Bearbeitung im Kontext](/help/sites-authoring/editing-content.md#editcontenttouchoptimizedui).

>[!NOTE]
>
>* Welche Personalisierungsfelder Ihnen zur Verfügung stehen, hängt davon ab, mit welcher Adobe Campaign-Vorlage Ihr Newsletter verknüpft ist.
>* Nach der Auswahl eines Profils im ContextHub werden die Personalisierungsfelder automatisch durch Daten des gewählten Profils ersetzt.
>
>Siehe [Personalisierung einfügen](/help/sites-authoring/campaign.md#inserting-personalization).

![chlimage_1-54](assets/chlimage_1-54.png)

>[!NOTE]
>
>Nur die Felder, die im Schema **nms:seedMember** oder einer seiner Erweiterungen festgelegt wurden, werden berücksichtigt. Die Attribute der mit **nms:seedMember** verknüpften Tabellen stehen nicht zur Verfügung.

## Adobe Campaign-Formular-Komponenten {#adobe-campaign-form-components}

Sie verwenden Adobe Campaign-Komponenten, um ein Formular zu erstellen, das Benutzer ausfüllen, um entweder einen Newsletter zu abonnieren, sich von einem Newsletter abzumelden oder ihre Benutzerprofile zu aktualisieren. Siehe [Erstellen von Adobe Campaign Forms](/help/sites-authoring/adobe-campaign-forms.md) für weitere Informationen.

Jedes Komponentenfeld kann mit einem Adobe Campaign-Datenbankfeld verknüpft werden. Die verfügbaren Felder unterscheiden sich je nach Datentyp, den sie enthalten, wie im Abschnitt beschrieben [Komponenten und Datentyp](#components-and-data-type). Wenn Sie Ihr Empfängerschema in Adobe Campaign erweitern, stehen die neuen Felder in den Komponenten zur Verfügung, deren Datentypen übereinstimmen.

Wenn Sie ein Formular öffnen, das für die Integration mit Adobe Campaign konfiguriert wurde, werden Ihnen im Abschnitt **Adobe Campaign** folgende Komponenten angezeigt:

* Kontrollkästchen (Kampagne)
* „Datumsfeld (Kampagne)“ und „Datumsfeld/HTML 5 (Kampagne)“
* Verschlüsselter Primärschlüssel (Kampagne)
* Fehleranzeige (Kampagne)
* Ausgeblendeter Abstimmschlüssel (Kampagne)
* Numerisches Feld (Kampagne)
* Optionsfeld (Kampagne)
* Abonnement-Checkliste (Kampagne)
* Textfeld (Kampagne)

Die Komponenten werden wie folgt angezeigt:

![chlimage_1-55](assets/chlimage_1-55.png)

In diesem Abschnitt werden die einzelnen Komponenten detailliert beschrieben.

### Komponenten und Datentyp {#components-and-data-type}

In der folgenden Tabelle werden die Komponenten beschrieben, die zum Anzeigen und Ändern von Adobe Campaign-Profildaten verfügbar sind. Jede Komponente kann einem Adobe Campaign-Profilfeld zugeordnet werden, um den zugehörigen Wert anzuzeigen und das Feld beim Senden des Formulars zu aktualisieren. Die verschiedenen Komponenten können nur Feldern eines entsprechenden Datentyps zugeordnet werden.

<table>
 <tbody>
  <tr>
   <td><p><strong>Komponente</strong></p> </td>
   <td><p><strong>Datentyp des Adobe Campaign-Felds</strong></p> </td>
   <td><p><strong>Beispielfeld</strong></p> </td>
  </tr>
  <tr>
   <td><p>Kontrollkästchen (Kampagne)</p> </td>
   <td><p>Boolean (Boolesch)</p> </td>
   <td><p>No longer contact (by any channel)</p> </td>
  </tr>
  <tr>
   <td><p>Datumsfeld (Kampagne)</p> <p>Datumsfeld/HTML 5 (Kampagne)</p> </td>
   <td><p>Datum</p> </td>
   <td><p>Geburtsdatum</p> </td>
  </tr>
  <tr>
   <td><p>Numerisches Feld (Kampagne)</p> </td>
   <td><p>numerisch (byte, short, long, double)</p> </td>
   <td><p>Alter</p> </td>
  </tr>
  <tr>
   <td><p>Optionsfeld (Kampagne)</p> </td>
   <td><p>Byte mit zugehörigen Werten</p> </td>
   <td><p>Geschlecht</p> </td>
  </tr>
  <tr>
   <td><p>Textfeld (Kampagne)</p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>E-Mail</p> </td>
  </tr>
 </tbody>
</table>

### Für die meisten Komponenten übliche Einstellungen {#settings-common-to-most-components}

Die Adobe Campaign-Komponenten verfügen über Einstellungen, die in allen Komponenten verwendet werden (mit Ausnahme der Komponenten &quot;Verschlüsselter Primärer Schlüssel&quot;und &quot;Ausgeblendeter Abstimmschlüssel&quot;).

In den meisten Komponenten können Sie Folgendes konfigurieren:

#### Titel und Text {#title-and-text}

![chlimage_1-56](assets/chlimage_1-56.png)

* **Titel**
Wenn Sie einen anderen Namen als Elementnamen verwenden möchten, geben Sie ihn hier ein.

* **Titel ausblenden**
Aktivieren Sie diese Option, wenn der Titel nicht angezeigt werden soll.

* **Beschreibung**
Fügen Sie eine Beschreibung des Felds hinzu, um Benutzern weitere Informationen zur Verfügung zu stellen.

* **Nur Wert anzeigen**
Zeigt nur den Wert an, falls dieser vorhanden ist.

#### Adobe Campaign {#adobe-campaign}

Sie können Folgendes konfigurieren:

* **Zuordnung**
Wählen Sie ein Adobe Campaign-Personalisierungsfeld aus, falls gewünscht.

* **Abstimmschlüssel**
Aktivieren Sie diese Option, wenn das Feld Teil des Abstimmschlüssels ist.

![chlimage_1-57](assets/chlimage_1-57.png)

#### Begrenzungen {#constraints}

* **Erforderlich** Aktivieren Sie diese Option, wenn die Komponente als Pflichtangabe eingestellt werden soll und Benutzende einen Wert eingeben müssen.
* **Erforderliche Meldung** Sie können optional eine Meldung eingeben, mit der darauf hingewiesen wird, dass das Feld eine Pflichtangabe ist.

![chlimage_1-58](assets/chlimage_1-58.png)

#### Stile {#styling}

* **CSS**
Geben Sie die CSS-Klassen ein, die Sie für diese Komponente verwenden möchten.

![chlimage_1-59](assets/chlimage_1-59.png)

### Kontrollkästchen (Kampagne) {#checkbox-campaign}

Mit der Komponente &quot;Kontrollkästchen (Kampagne)&quot;kann der Benutzer Adobe Campaign-Profilfelder ändern, die vom booleschen Datentyp sind. Beispielsweise könnte eine Komponente vom Typ Kontrollkästchen (Kampagne) vorhanden sein, mit der der Empfänger angeben kann, dass er über keinen Kanal kontaktiert werden möchte.

Sie können [Konfigurieren von Einstellungen, die für die meisten Adobe Campaign-Komponenten gelten](#settings-common-to-most-components) in der Komponente &quot;Kontrollkästchen (Kampagne)&quot;.

Das folgende Beispiel zeigt, wie eine Checkbox-Komponente (Kampagne) angezeigt wird.

![chlimage_1-60](assets/chlimage_1-60.png)

### „Datumsfeld (Campaign)“ und „Datumsfeld/HTML 5 (Campaign)“ {#date-field-campaign-and-date-field-html-campaign}

Verwenden Sie das Datumsfeld, um Empfängern ein Datum zu ermöglichen. Sie können beispielsweise von den Empfängern verlangen, ihr Geburtsdatum anzugeben. Das Datumsformat entspricht dem Format, das in Ihrer Adobe Campaign-Instanz verwendet wird.

Neben den [von den meisten Adobe Campaign-Komponenten genutzten Einstellungen](#settings-common-to-most-components) können Sie auch Folgendes konfigurieren:

* **Beschränkungen**: Im Dropdown-Menü für Beschränkungen können Sie aus Folgendem wählen: **Keine** oder **Datum**, um ein Datum oder keine Beschränkung festzulegen. Wählen Sie „Datum“ aus, müssen Benutzende ihre Angaben im Datumsformat machen.

* **Beschränkungsmeldung** Außerdem können Sie eine Beschränkungsmeldung hinzufügen, die Benutzern mitteilt, wie Antworten richtig formatiert werden.
* **Stile – Breite** Passen Sie die Breite des Felds an, indem Sie auf **+** oder **-** tippen oder eine Zahl eingeben.

Im folgenden Beispiel sehen Sie, wie die Komponente „Datumsfeld (Kampagne)“ mit angepasster Breite angezeigt wird.

![chlimage_1-61](assets/chlimage_1-61.png)

### Verschlüsselter Primärschlüssel (Kampagne) {#encrypted-primary-key-campaign}

Diese Komponente definiert den Namen des URL-Parameters, der die Kennung eines Adobe Campaign-Profils enthält (**Hauptressourcenkennung** oder **Verschlüsselter Primärschlüssel** in Adobe Campaign Standard bzw. 6.1).

Jedes Formular, in dem Adobe Campaign-Profildaten angezeigt und geändert werden **must** enthalten eine Komponente mit verschlüsseltem Primären Schlüssel .

Sie können Folgendes in der Komponente Verschlüsselter Primärer Schlüssel (Kampagne) konfigurieren:

* **Titel und Text – Elementname** Standardeinstellung: encryptedPK. Sie müssen den Elementnamen nur ändern, wenn er mit dem Namen eines anderen Elements im Formular in Konflikt steht. Zwei Formularfelder dürfen nicht denselben Elementnamen haben.
* **Adobe Campaign – URL-Parameter** Fügen Sie den URL-Parameter des EPK hinzu. Sie können beispielsweise den Wert **epk**.

Das folgende Beispiel zeigt die Anzeige der Komponente &quot;Verschlüsselter Primärer Schlüssel (Kampagne)&quot;.

![chlimage_1-62](assets/chlimage_1-62.png)

### Fehleranzeige (Kampagne) {#error-display-campaign}

Mit dieser Komponente können Sie Backend-Fehler anzeigen. Die Fehlerbehandlung des Formulars muss auf &quot;Weiterleiten&quot;eingestellt sein, damit die Komponente ordnungsgemäß funktioniert.

Das folgende Beispiel zeigt, wie die Komponente Fehleranzeige (Kampagne) angezeigt wird.

![chlimage_1-63](assets/chlimage_1-63.png)

### Ausgeblendeter Abstimmschlüssel (Kampagne) {#hidden-reconciliation-key-campaign}

Mit der Komponente „Ausgeblendeter Abstimmschlüssel (Kampagne)“ können Sie einem Formular ausgeblendete Felder als Teil des Abstimmschlüssels hinzuzufügen.

In der Komponente „Ausgeblendeter Abstimmschlüssel (Kampagne)“ können Sie Folgendes konfigurieren:

* **Titel und Text – Elementname** Standardeinstellung: reconcilKey. Sie müssen den Elementnamen nur ändern, wenn er mit dem Namen eines anderen Elements im Formular in Konflikt steht. Zwei Formularfelder dürfen nicht denselben Elementnamen haben.
* **Adobe Campaign – Zuordnung** Zuordnung zu einem Personalisierungsfeld von Adobe Campaign.

Im folgenden Beispiel sehen Sie, wie die Komponente „Ausgeblendeter Abstimmschlüssel (Kampagne)“ dargestellt wird.

![chlimage_1-64](assets/chlimage_1-64.png)

### Numerisches Feld (Kampagne) {#numeric-field-campaign}

Verwenden Sie das numerische Feld, um Empfängern die Eingabe von Zahlen zu ermöglichen, z. B. ihres Alters.

Neben den [von den meisten Adobe Campaign-Komponenten genutzten Einstellungen](#settings-common-to-most-components) können Sie auch Folgendes konfigurieren:

* **Beschränkungen – Dropdown „Beschränkung“**
Sie können **Keine** oder **Numerisch** auswählen, um eine Zahlenbeschränkung oder keine Beschränkung hinzuzufügen. Wählen Sie die numerische Beschränkung, können Benutzende ausschließlich Zahlen in das Feld eingeben.

* **Beschränkungsmeldung** Außerdem können Sie eine Beschränkungsmeldung hinzufügen, die Benutzern mitteilt, wie Antworten richtig formatiert werden.
* **Stile – Breite** Passen Sie die Breite des Felds an, indem Sie auf **+** oder **-** tippen oder eine Zahl eingeben.

Im folgenden Beispiel sehen Sie, wie die Komponente „Numerisches Feld (Kampagne)“ mit konfigurierter Breite angezeigt wird.

![chlimage_1-65](assets/chlimage_1-65.png)

### Optionsfeld (Kampagne) {#option-field-campaign}

In dieser Dropdownliste können Sie eine Option auswählen. beispielsweise das Geschlecht oder den Status eines Empfängers.

Sie können [Konfigurieren von Einstellungen, die für die meisten Adobe Campaign-Komponenten gelten](#settings-common-to-most-components) in der Komponente &quot;Optionsfeld (Kampagne)&quot;. Um die Dropdown-Liste zu füllen, wählen Sie das entsprechende Feld in den Adobe Campaign-Personalisierungsfeldern aus, indem Sie auf das Adobe Campaign-Symbol klicken oder tippen und zum entsprechenden Feld navigieren.

![chlimage_1-66](assets/chlimage_1-66.png)

Im folgenden Beispiel sehen Sie, wie die Komponente „Optionsfeld (Kampagne)“ dargestellt wird.

![chlimage_1-67](assets/chlimage_1-67.png)

### Abonnement-Checkliste (Kampagne) {#subscriptions-checklist-campaign}

Mithilfe der Komponente **Abonnement-Checkliste (Kampagne)** können Sie die mit einem Adobe Campaign-Profil verknüpften Abonnements bearbeiten.

Wird die Komponente einem Formular hinzugefügt, werden alle verfügbaren Abonnements als Kontrollkästchen angezeigt, aus denen die Benutzer das gewünschte auswählen können. Wenn Benutzer das Formular senden, sorgt diese Komponente für ein Abonnement oder die Beendigung eines Abonnements der vom Benutzer ausgewählten Services. Dies hängt vom Formularaktionstyp ab (**Adobe Campaign: Services abonnieren** oder **Adobe Campaign: Abonnement von Services beenden**).

>[!NOTE]
>
>Von der Komponente wird nicht geprüft, welche Services der Benutzer bereits abonniert oder abbestellt hat und welche nicht.

Sie können [Konfigurieren von Einstellungen, die für die meisten Adobe Campaign-Komponenten gelten](#settings-common-to-most-components) in der Komponente Abonnement-Checkliste (Kampagne) . (Für diese Komponente sind keine Adobe Campaign-Konfigurationen verfügbar.)

Das folgende Beispiel zeigt, wie die Komponente Abonnement-Checkliste (Kampagne) angezeigt wird.

![chlimage_1-68](assets/chlimage_1-68.png)

### Textfeld (Kampagne) {#text-field-campaign}

Die Komponente &quot;Textfeld (Kampagne)&quot;, mit der Sie Daten vom Typ Zeichenfolge eingeben können, z. B. Vorname, Nachname, Adresse, E-Mail-Adresse usw.

Neben den [von den meisten Adobe Campaign-Komponenten genutzten Einstellungen](#settings-common-to-most-components) können Sie auch Folgendes konfigurieren:

* **Beschränkungen**: Im Dropdown-Menü
für Beschränkungen können Sie **Keine**, **E-Mail** oder **Name** (keine Umlaute) auswählen, um keine Beschränkung festzulegen oder die Eingabe auf E-Mail-Adressen und Namen einzugrenzen. Entscheiden Sie sich für „E-Mail“, können Benutzende ausschließlich E-Mail-Adressen in das Feld eingeben. Entscheiden Sie sich für „Name“, muss ein Name eingegeben werden (hierbei sind jedoch keine Umlaute gestattet).

* **Beschränkungsmeldung** Außerdem können Sie eine Beschränkungsmeldung hinzufügen, die Benutzern mitteilt, wie Antworten richtig formatiert werden.
* **Stile – Breite** Passen Sie die Breite des Felds an, indem Sie auf **+** oder **-** tippen oder eine Zahl eingeben.

Im folgenden Beispiel sehen Sie, wie die Komponente „Textfeld (Kampagne)“ dargestellt wird.

![chlimage_1-69](assets/chlimage_1-69.png)
