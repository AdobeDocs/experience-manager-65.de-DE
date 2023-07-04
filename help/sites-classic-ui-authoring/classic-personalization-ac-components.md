---
title: Adobe Campaign-Komponenten
description: Wenn Sie eine Integration mit Adobe Campaign durchführen, stehen Ihnen Komponenten für die Arbeit mit Newslettern und Formularen zur Verfügung.
uuid: cc9417c9-4cc1-4554-858e-2ecd682dc92f
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 5afe864d-5794-4ffa-99e7-a3233f982aff
docset: aem65
exl-id: eeff89c1-41b3-403d-b4bf-c79b09b24d4a
source-git-commit: f4b6eb2ded17ec641f23a1fc3b977ce77169c8a1
workflow-type: ht
source-wordcount: '2534'
ht-degree: 100%

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

* Überschrift (Campaign)
* Bild (Campaign)
* Link (Kampagne)
* Scene7-Bildvorlage (Campaign)
* Zielgerichteter Verweis (Campaign)
* Text und Bild (Campaign).
* Text und Personalisierung (Kampagne)

Eine Beschreibung dieser Komponenten finden Sie im folgenden Abschnitt.

![chlimage_1-81](assets/chlimage_1-81.png)

### Überschrift (Campaign) {#heading-campaign}

Die Titelkomponente kann entweder:

* Den Namen der aktuellen Seite anzeigen, indem Sie das Feld **Titel** leer lassen.
* Einen Text anzeigen, den Sie im Feld **Titel** angeben.

Sie bearbeiten die Komponente **Überschrift (Campaign)** direkt. Frei lassen, um den Seitentitel zu verwenden.

![chlimage_1-82](assets/chlimage_1-82.png)

Sie können Folgendes konfigurieren:

* **Titel**
Wenn Sie einen anderen Namen als den Seitentitel verwenden möchten, geben Sie ihn hier ein.

* **Überschriftenebene (1, 2, 3, 4)**
Die Überschriftenebene basierend auf der HTML-Überschriftgröße (1–4).

Im folgenden Beispiel sehen Sie, wie die Komponente „Überschrift (Kampagne)“ dargestellt wird.

![chlimage_1-83](assets/chlimage_1-83.png)

### Bild (Campaign) {#image-campaign}

Die Komponente „Bild (Campaign)“ zeigt ein Bild und begleitenden Text gemäß den festgelegten Parametern an.

Sie können ein Bild hochladen und dieses anschließend bearbeiten und anpassen (beispielsweise zuschneiden, drehen oder Links/Titel/Text hinzufügen).

Sie können ein Bild hochladen und dieses anschließend bearbeiten und manipulieren (beispielsweise zuschneiden, drehen oder Links/Titel/Text hinzufügen). Sie können ein Bild aus der [Inhaltssuche](/help/sites-authoring/author-environment-tools.md#thecontentfinderclassicui) per Drag-and-Drop direkt auf die Komponente oder ihren Bearbeitungsdialog ziehen. Sie können auch im zentralen Bereich des Bearbeitungsdialogs doppelklicken, um Ihr lokales Dateisystem zu durchsuchen und ein Bild hochzuladen. Die beiden Registerkarten des Bearbeitungsdialogs steuern auch alle Definitionen und Bearbeitungen des Bildes:

![chlimage_1-84](assets/chlimage_1-84.png)

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

![chlimage_1-85](assets/chlimage_1-85.png)

### Link (Kampagne) {#link-campaign}

Mithilfe der Komponente „Link (Campaign)“ können Sie Ihrem Newsletter einen Link hinzufügen. Diese Komponente ist nur in der klassischen Benutzeroberfläche verfügbar, sie kann jedoch auch in der Touch-optimierten Benutzeroberfläche hinzugefügt und im Kompatibilitätsmodus geöffnet werden.

![chlimage_1-86](assets/chlimage_1-86.png)

Folgendes können Sie in den Registerkarten **Anzeige**, **URL-Info** oder **Erweitert** konfigurieren:

* **Verknüpfungsbeschriftung**
Die Beschriftung des Links. Dies ist der Text, der den Benutzern angezeigt wird.

* **Link-QuickInfo**
Mit dieser Option werden weitere Informationen zur Verwendung des Links hinzugefügt.

* **LinkType**
Wählen Sie in der Dropdown-Liste zwischen 
**Benutzerdefinierte URL** und **Adaptives Dokument**. Dieses Feld ist obligatorisch. Wenn Sie „Benutzerdefinierte URL“ auswählen, können Sie die URL des Links angeben. Entscheiden Sie sich für ein adaptives Dokument, können Sie den Dokumentenpfad festlegen.

* **Zusätzlicher URL-Parameter**
Fügen Sie weitere URL-Parameter hinzu. Klicken Sie auf „Element hinzufügen“, um mehrere Elemente hinzuzufügen.

>[!NOTE]
>
>Sie müssen im Feld **Verknüpfungstyp** auf der Registerkarte **URL-Info** Daten eingeben, da die Komponente sonst nicht gespeichert werden kann und folgende Fehlermeldung ausgegeben wird:
>
>`Validation failed. Verify the values of the marked fields.`

Im folgenden Beispiel sehen Sie, wie die Komponente „Link (Kampagne)“ dargestellt wird.

![chlimage_1-87](assets/chlimage_1-87.png)

### Zielgerichteter Verweis (Campaign) {#targeted-reference-campaign}

Mithilfe der Komponente „Zielgerichteter Verweis (Campaign)“ können Sie einen Verweis auf einen zielgerichteten Abschnitt erstellen.

In dieser Komponente navigieren Sie zum zielgerichteten Absatz, um ihn auszuwählen.

Klicken Sie auf das Dropdown-Menü, um zu dem Absatz zu navigieren, auf den Sie verweisen möchten. Wenn Sie fertig sind, klicken Sie auf **OK**.

### Text und Bild (Campaign). {#text-image-campaign}

Mit der Komponente „Text und Bild (Campaign)“ werden ein Textblock und ein Bild hinzugefügt.

![chlimage_1-88](assets/chlimage_1-88.png)

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

![chlimage_1-89](assets/chlimage_1-89.png)

### Text und Personalisierung (Kampagne) {#text-personalization-campaign}

Mit der Komponente „Text-und-Personalisierung (Kampagne)“ können Sie über einen WYSIWYG-Editor, dessen Funktionen der [Rich-Text-Editor](/help/sites-authoring/rich-text-editor.md) bereitstellt, einen Textblock eingeben. Darüber hinaus können Sie mit dieser Komponente die Kontextfelder und Personalisierungsblöcke verwenden, die in Adobe Campaign verfügbar sind. Siehe auch [Einfügen von Personalisierung](/help/sites-classic-ui-authoring/classic-personalization-ac-campaign.md#inserting-personalization).

Über mehrere Symbole können Sie den Text formatieren, darunter Schriftmerkmale, Ausrichtung, Links, Listen und Einzug.

Fügen Sie Text wie gewohnt im Rich-Text-Editor hinzu. Fügen Sie Personalisierungen hinzu, indem Sie aus dem Dropdown-Menü von Adobe Campaign die gewünschten Optionen auswählen.

![chlimage_1-90](assets/chlimage_1-90.png)

Sie fügen die Text- und Kontextfelder oder Gestaltungsbausteine hinzu, um den Inhalt zu erstellen. Wählen Sie als Nächstes den Client-Kontext aus, um die Daten in den Rollenprofilen zu testen. Nach der Auswahl eines Profils werden die Personalisierungsfelder automatisch durch Daten des ausgewählten Profils ersetzt.

>[!NOTE]
>
>Nur die Felder, die im Schema **nms:seedMember** oder einer seiner Erweiterungen festgelegt wurden, werden berücksichtigt. Die Attribute der mit `nms:seedMember` verknüpften Tabellen stehen nicht zur Verfügung.

## Adobe Campaign-Formular-Komponenten {#adobe-campaign-form-components}

Sie können mithilfe der Adobe Campaign-Komponenten Formulare erstellen, die Benutzende ausfüllen können, um Newsletter zu abonnieren oder abzubestellen oder ihre Benutzerprofile zu aktualisieren. Siehe [Erstellen von Adobe Campaign-Formularen](/help/sites-classic-ui-authoring/classic-personalization-ac-forms.md) für weitere Informationen.

Jedes Komponentenfeld kann mit einem Adobe Campaign-Datenbankfeld verknüpft werden. Die verfügbaren Felder variieren je nach dem enthaltenen Datentyp. Eine genauere Beschreibung finden Sie im Abschnitt [Komponenten und Datentyp](#components-and-data-type). Wenn Sie Ihr Empfängerschema in Adobe Campaign erweitern, stehen die neuen Felder in den Komponenten zur Verfügung, deren Datentypen übereinstimmen.

Wenn Sie ein Formular öffnen, das für die Integration mit Adobe Campaign konfiguriert wurde, werden Ihnen im Abschnitt **Adobe Campaign** folgende Komponenten angezeigt:

* Kontrollkästchen (Campaign)
* „Datumsfeld (Kampagne)“ und „Datumsfeld/HTML 5 (Kampagne)“
* Verschlüsselter Primärschlüssel (Campaign)
* Fehleranzeige (Campaign)
* Ausgeblendeter Abstimmschlüssel (Kampagne)
* Numerisches Feld (Campaign)
* Optionsfeld (Campaign)
* Abonnement-Checkliste (Kampagne)
* Textfeld (Campaign)

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
   <td><p>Kontrollkästchen (Campaign)</p> </td>
   <td><p>Boolean (Boolesch)</p> </td>
   <td><p>Kein Kontakt mehr (egal über welchen Kanal)</p> </td>
  </tr>
  <tr>
   <td><p>Datumsfeld (Campaign)</p> <p>Datumsfeld/HTML 5 (Kampagne)</p> </td>
   <td><p>Datum</p> </td>
   <td><p>Geburtsdatum</p> </td>
  </tr>
  <tr>
   <td><p>Numerisches Feld (Campaign)</p> </td>
   <td><p>Numerisch (byte, short, long, double)</p> </td>
   <td><p>Alter</p> </td>
  </tr>
  <tr>
   <td><p>Optionsfeld (Campaign)</p> </td>
   <td><p>Byte mit zugehörigen Werten</p> </td>
   <td><p>Geschlecht</p> </td>
  </tr>
  <tr>
   <td><p>Textfeld (Campaign)</p> </td>
   <td><p>Zeichenfolge</p> </td>
   <td><p>E-Mail</p> </td>
  </tr>
 </tbody>
</table>

### Für die meisten Komponenten übliche Einstellungen {#settings-common-to-most-components}

Adobe Campaign-Komponenten verfügen über Einstellungen, die in allen Komponenten verwendet werden (mit Ausnahme der Komponenten „Verschlüsselter Primärschlüssel“ und „Ausgeblendeter Abstimmschlüssel“).

In den meisten Komponenten können Sie Folgendes konfigurieren:

#### Titel und Text {#title-and-text}

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

#### Beschränkungen {#constraints}

* **Erforderlich**: Aktivieren Sie dieses Kontrollkästchen, um diese Komponente zu einem erforderlichen Feld zu machen. Das bedeutet, dass Benutzer einen Wert eingeben müssen.
* **Erforderliche Meldung**: Geben Sie optional eine Meldung ein, die angibt, dass das Feld erforderlich ist.

#### Stile {#styling}

* **CSS**
Geben Sie die CSS-Klassen ein, die Sie für diese Komponente verwenden möchten.

### Kontrollkästchen (Campaign) {#checkbox-campaign}

Die Komponente „Kontrollkästchen (Campaign)“ ermöglicht es Benutzenden, Adobe Campaign-Profilfelder zu ändern, die vom booleschen Datentyp sind. Beispielsweise können Sie über eine Komponente des Typs „Kontrollkästchen (Campaign)“ verfügen, mit der empfangende Personen angeben können, dass sie über keinen Kanal kontaktiert werden möchten.

Sie können in der Komponente „Kontrollkästchen (Campaign)“ [Einstellungen konfigurieren, die für die meisten Adobe Campaign-Komponenten üblich sind](#settings-common-to-most-components).

Im folgenden Beispiel sehen Sie, wie die Komponente „Kontrollkästchen (Campaign)“ dargestellt wird.

![chlimage_1-91](assets/chlimage_1-91.png)

### „Datumsfeld (Kampagne)“ und „Datumsfeld/HTML 5 (Kampagne)“ {#date-field-campaign-and-date-field-html-campaign}

Verwenden Sie das Datumsfeld, um den Empfängerinnen und Empfängern eine Datumseingabe zu ermöglichen. Sie können beispielsweise von ihnen verlangen, ihr Geburtsdatum anzugeben. Das Datumsformat entspricht dem Format, das in Ihrer Adobe Campaign-Instanz verwendet wird.

Neben den [von den meisten Adobe Campaign-Komponenten genutzten Einstellungen](#settings-common-to-most-components) können Sie auch Folgendes konfigurieren:

* **Beschränkungen – „Beschränkung“** Sie können **Keine** oder **Datum** auswählen, um eine Datumsbeschränkung oder keine Beschränkung hinzuzufügen. Wählen Sie „Datum“ aus, müssen Benutzer ihre Angaben im Datumsformat machen.

* **Beschränkungsmeldung**: Außerdem können Sie eine Beschränkungsmeldung hinzufügen, die Benutzern mitteilt, wie Antworten richtig formatiert werden.
* **Stile – Breite**: Passen Sie die Breite des Felds an, indem Sie auf **+** oder **-** tippen oder eine Zahl eingeben.

Im folgenden Beispiel sehen Sie, wie die Komponente „Datumsfeld (Kampagne)“ mit angepasster Breite angezeigt wird.

![chlimage_1-92](assets/chlimage_1-92.png)

### Verschlüsselter Primärschlüssel (Campaign) {#encrypted-primary-key-campaign}

Diese Komponente definiert den Namen des URL-Parameters, der die Kennung eines Adobe Campaign-Profils enthält (**Hauptressourcenkennung** oder **Verschlüsselter Primärschlüssel** in Adobe Campaign Standard bzw. 6.1).

Jedes Formular, mit dem Adobe Campaign-Profildaten angezeigt und bearbeitet werden, **muss** den verschlüsselten Primärschlüssel enthalten.

In der Komponente „Verschlüsselter Primärschlüssel (Campaign)“ können Sie Folgendes konfigurieren:

* **Titel und Text – Elementname**: Die Standardeinstellung ist encryptedPK. Sie müssen den Elementnamen nur ändern, wenn er mit dem Namen eines anderen Elements im Formular in Konflikt steht. Zwei Formularfelder dürfen nicht denselben Elementnamen haben.
* **Adobe Campaign – URL-Parameter**: Fügen Sie den URL-Parameter des EPK hinzu. Sie können beispielsweise den Wert **epk** verwenden.

Im folgenden Beispiel sehen Sie, wie die Komponente „Verschlüsselter Primärschlüssel (Campaign)“ dargestellt wird.

![chlimage_1-93](assets/chlimage_1-93.png)

### Fehleranzeige (Campaign) {#error-display-campaign}

Mit dieser Komponente können Sie Backend-Fehler anzeigen. Damit die Komponente ordnungsgemäß funktioniert, muss die Fehlerhandhabung auf „Weiterleiten“ eingestellt werden.

Im folgenden Beispiel sehen Sie, wie die Komponente „Fehleranzeige (Campaign)“ dargestellt wird.

![chlimage_1-94](assets/chlimage_1-94.png)

### Ausgeblendeter Abstimmschlüssel (Kampagne) {#hidden-reconciliation-key-campaign}

Mit der Komponente „Ausgeblendeter Abstimmschlüssel (Kampagne)“ können Sie einem Formular ausgeblendete Felder als Teil des Abstimmschlüssels hinzuzufügen.

In der Komponente „Ausgeblendeter Abstimmschlüssel (Kampagne)“ können Sie Folgendes konfigurieren:

* **Titel und Text – Elementname**: Die Standardeinstellung ist reconcilKey. Sie müssen den Elementnamen nur ändern, wenn er mit dem Namen eines anderen Elements im Formular in Konflikt steht. Zwei Formularfelder dürfen nicht denselben Elementnamen haben.
* **Adobe Campaign – Zuordnung**: Zuordnung zu einem Personalisierungsfeld von Adobe Campaign.

Im folgenden Beispiel sehen Sie, wie die Komponente „Ausgeblendeter Abstimmschlüssel (Kampagne)“ dargestellt wird.

![chlimage_1-95](assets/chlimage_1-95.png)

### Numerisches Feld (Campaign) {#numeric-field-campaign}

Verwenden Sie das numerische Feld, um Empfängerinnen und Empfängern die Eingabe von Zahlen zu ermöglichen, z. B. ihres Alters.

Neben den [von den meisten Adobe Campaign-Komponenten genutzten Einstellungen](#settings-common-to-most-components) können Sie auch Folgendes konfigurieren:

* **Beschränkungen – Dropdown „Beschränkung“**
Sie können **Keine** oder **Numerisch** auswählen, um eine Zahlenbeschränkung oder keine Beschränkung hinzuzufügen. Wählen Sie die numerische Beschränkung, können Benutzer ausschließlich Zahlen in das Feld eingeben.

* **Beschränkungsmeldung**: Außerdem können Sie eine Beschränkungsmeldung hinzufügen, die Benutzern mitteilt, wie Antworten richtig formatiert werden.
* **Stile – Breite**: Passen Sie die Breite des Felds an, indem Sie auf **+** oder **-** tippen oder eine Zahl eingeben.

Im folgenden Beispiel sehen Sie, wie die Komponente „Numerisches Feld (Kampagne)“ mit konfigurierter Breite angezeigt wird.

![chlimage_1-96](assets/chlimage_1-96.png)

### Optionsfeld (Campaign) {#option-field-campaign}

In dieser Dropdown-Liste können Sie eine Option auswählen. z. B. das Geschlecht oder den Status einer Empfängerin bzw. eines Empfängers.

Sie können in der Komponente „Optionsfeld (Campaign)“ [Einstellungen konfigurieren, die für die meisten Adobe Campaign-Komponenten üblich sind](#settings-common-to-most-components). Um die Dropdown-Liste zu füllen, wählen Sie das entsprechende Feld in den Adobe Campaign-Personalisierungsfeldern aus, indem Sie auf das Adobe Campaign-Symbol klicken oder tippen und zum entsprechenden Feld navigieren.

Im folgenden Beispiel sehen Sie, wie die Komponente „Optionsfeld (Kampagne)“ dargestellt wird.

![chlimage_1-97](assets/chlimage_1-97.png)

### Abonnement-Checkliste (Kampagne) {#subscriptions-checklist-campaign}

Mithilfe der Komponente **Abonnement-Checkliste (Kampagne)** können Sie die mit einem Adobe Campaign-Profil verknüpften Abonnements bearbeiten.

Wird die Komponente einem Formular hinzugefügt, werden alle verfügbaren Abonnements als Kontrollkästchen angezeigt, aus denen die Benutzer das gewünschte auswählen können. Wenn Benutzer das Formular senden, sorgt diese Komponente für ein Abonnement oder die Beendigung eines Abonnements der vom Benutzer ausgewählten Services. Dies hängt vom Formularaktionstyp ab (**Adobe Campaign: Services abonnieren** oder **Adobe Campaign: Abonnement von Services beenden**).

>[!NOTE]
>
>Von der Komponente wird nicht geprüft, welche Services der Benutzer bereits abonniert oder abbestellt hat und welche nicht.

Sie können in der Komponente „Abonnement-Checkliste (Campaign)“ [Einstellungen konfigurieren, die für die meisten Adobe Campaign-Komponenten üblich sind](#settings-common-to-most-components). (Für diese Komponente sind keine Adobe Campaign-Konfigurationen verfügbar.)

Im folgenden Beispiel sehen Sie, wie die Komponente „Abonnement-Checkliste (Campaign)“ dargestellt wird.

![chlimage_1-98](assets/chlimage_1-98.png)

### Textfeld (Campaign) {#text-field-campaign}

Die Komponente „Textfeld (Campaign)“ ermöglicht Ihnen die Eingabe von Daten im Zeichenfolgenformat, etwa Vornamen, Nachnamen, Adressen, E-Mail-Adressen usw.

Neben den [von den meisten Adobe Campaign-Komponenten genutzten Einstellungen](#settings-common-to-most-components) können Sie auch Folgendes konfigurieren:

* **Beschränkungen – Dropdown „Beschränkung“**: Sie können **Keine**, **E-Mail** oder **Name** (ohne Umlaute) auswählen, um die Eingabe in diesem Feld auf eine E-Mail-Adresse oder einen Namen zu beschränken oder keine Beschränkung festzulegen. Entscheiden Sie sich für „E-Mail“, können Benutzer ausschließlich E-Mail-Adressen in das Feld eingeben. Entscheiden Sie sich für „Name“, muss ein Name eingegeben werden (hierbei sind jedoch keine Umlaute gestattet).

* **Beschränkungsmeldung**: Außerdem können Sie eine Beschränkungsmeldung hinzufügen, die Benutzern mitteilt, wie Antworten richtig formatiert werden.
* **Stile – Breite**: Passen Sie die Breite des Felds an, indem Sie auf **+** oder **-** tippen oder eine Zahl eingeben.

Im folgenden Beispiel sehen Sie, wie die Komponente „Textfeld (Kampagne)“ dargestellt wird.

![chlimage_1-99](assets/chlimage_1-99.png)
