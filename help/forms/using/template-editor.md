---
title: Adaptive Formularvorlagen
description: Erstellen Sie Vorlagen für adaptive Formulare, indem Sie die grundlegende Struktur und den anfänglichen Formularinhalt mithilfe des Vorlagen-Editors definieren.
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms
exl-id: d7287ee7-fb4e-4d47-b37e-0a9260344070
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '2029'
ht-degree: 73%

---

# Adaptive Formularvorlagen{#adaptive-form-templates}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/template-editor.html?lang=de) |
| AEM 6.5 | Dieser Artikel |



Wenn Sie ein Formular erstellen, fügen Sie Felder und Komponenten hinzu, um Formularstruktur, Inhalt und Aktionen im Editor zu definieren. Sie können Felder und Komponenten im`guideRootPanel` des Formularcontainers hinzufügen. Mit dem Vorlageneditor können Sie eine Vorlage erstellen, die eine grundlegende Struktur und anfänglichen Inhalt enthält, die Autorinnen und Autoren zum Erstellen von Formularen verwenden können.

Beispiel: Sie möchten, dass alle Autoren in einem Registrierungsformular bestimmte Textfelder, Navigationsschaltflächen und eine Schaltfläche zum Senden verwenden. Sie können eine Vorlage mit den Komponenten erstellen, die Autoren verwenden können, damit ihr Formular konsistent mit anderen Registrierungsformularen ist. Wenn Autoren die Vorlage zum Erstellen eines adaptiven Formulars verwenden, übernimmt das neue Formular die Struktur und die Komponenten, die Sie in der Vorlage angegeben haben. Mit dem Vorlageneditor können Sie:

* Kopf- und Fußzeilenkomponenten eines Formulars in der Strukturebene hinzufügen.
* Den anfänglichen Inhalt für das Formular angeben.
* Geben Sie ein Design und Übermittlungsaktionen an.

## Arbeiten mit Vorlagen {#working-with-templates}

Sie können über das Menü Tools auf den Vorlagen-Editor zugreifen, indem Sie zu **Adobe Experience Manager > Tools > Vorlagen**. Hier befinden sich die Vorlagen in Ordnern für bearbeitbare Vorlagen. AEM bietet einen globalen Ordner zum Organisieren von Vorlagen. Er ist jedoch nicht standardmäßig aktiviert. Sie können Ihren Administrator bitten, den globalen Ordner zu aktivieren, oder einen Ordner für Vorlagen erstellen. Weitere Informationen zum Erstellen von Ordnern finden Sie unter [Vorlagenordner](/help/sites-developing/page-templates-editable.md).

Nachdem Sie ausgewählt haben, um einen Ordner zu öffnen, wird die Schaltfläche Erstellen angezeigt, mit der Sie eine Vorlage für adaptive Formulare erstellen können.

### Erstellen einer Vorlage {#create-template}

Nachdem Sie einen Ordner erstellt haben, öffnen Sie den Ordner und führen Sie die folgenden Schritte aus, um eine Vorlage zu erstellen:

1. Wählen Sie in der Vorlagenkonsole die Option **Erstellen** in dem Ordner, den Sie erstellt haben.
1. Wählen Sie im Abschnitt Vorlagentyp auswählen die Option **Adaptive Formularvorlage** und wählen **Nächste**.

1. Geben Sie im Bereich &quot;Vorlagendetails&quot;einen Vorlagentitel ein und wählen Sie **Erstellen**.
Sie können eine Beschreibung und eine Miniaturansicht hinzufügen, die angezeigt wird, wenn Sie die erstellte Vorlage beim Formular-Authoring auswählen.

1. Auswählen **Fertig** , um zur Konsole zurückzukehren, oder wählen Sie **Öffnen** , um die Vorlage im Editor zu öffnen.

### Benutzeroberfläche des Vorlageneditors {#template-editor-ui}

Wenn Sie eine Vorlage zum Bearbeiten öffnen, können Sie die folgenden AEM-Editor-Komponenten sehen:

* **Seitensymbolleiste**: Enthält die folgenden Optionen:

   * **Seitliches Bedienfeld ein/aus**: Hier können Sie die Seitenleiste ein- oder ausblenden.
   * **Seiteninformationen**: Ermöglicht Ihnen die Angabe von Informationen wie dem Zeitpunkt der Veröffentlichung oder der Zurücknahme der Veröffentlichung, Miniaturen, Client-seitigen Bibliotheken, einer Seitenrichtlinie und dem Seiten-Design einer Client-seitigen Bibliothek.
   * **Emulator**: Hier können Sie das Erscheinungsbild für verschiedene Geräte simulieren und anpassen.
   * **Ebenenselektor**: Hiermit können Sie die Ebene ändern.
Sie können die Ebene **Struktur** oder die Ebene **Anfänglicher Inhalt** auswählen. In der Ebene „Struktur“ können Sie die Kopf- und Fußzeile hinzufügen und anpassen. In der Ebene „Anfänglicher Inhalt“ können Sie den Formularinhalt anpassen.

   * **Vorschau**: Hier können Sie das Aussehen der Vorlage bei Veröffentlichung in einer Vorschau simulieren. Sie können den Ebenenselektor und die Vorschau verwenden, um zwischen Bearbeitungs- und Vorschau-Modus zu wechseln.

* **Seitenleiste**: Enthält Inhalts-, Eigenschaften-, Elemente- und Komponenten-Browser.
* **Komponenten-Symbolleiste**: Wenn Sie eine Komponente auswählen, sehen Sie eine Symbolleiste, in der Sie die Komponente anpassen können.
* **Seite**: Der Bereich, in dem Sie Inhalt hinzufügen, um die Vorlage zu erstellen.

Weitere Informationen zum Touch UI-Editor finden Sie unter [Einführung in das Authoring adaptiver Formulare.](../../forms/using/introduction-forms-authoring.md)

### Bearbeiten einer Vorlage {#editing-a-template}

Eine adaptive Formularvorlage wird mit zwei Ebenen erstellt:

* Struktur
* Anfänglicher Inhalt

Der Ebenenselektor ist neben der Option „Vorschau“ in der rechten oberen Ecke des Bildschirms verfügbar.

### Struktur {#structure}

Wenn Sie die Strukturebene im Vorlageneditor auswählen, werden die Layout-Container über und unter dem Container für adaptive Formulare angezeigt. Autorinnen und Autoren können diese Layout-Container für Kopf- und Fußzeilen verwenden. Sie können die Kopf- und Fußzeile hinzufügen, bearbeiten oder anpassen. Ziehen Sie die Kopfzeilenkomponente des adaptiven Formulars in den Layout-Container über dem Container des adaptiven Formulars, um die Vorlagenkopfzeile anzupassen. Ziehen Sie die Fußzeilenkomponente des adaptiven Formulars in den Layout-Container unter dem Container des adaptiven Formulars, um die Vorlagenfußzeile anzupassen.

![Layout-Container in der Strukturebene](assets/header-layer-selector.png)

Layout-Container in der Strukturebene

**A.** Layout-Container für die Kopfzeilenkomponente **B.** Layout-Container für die Fußzeilenkomponente

Ziehen Sie die Kopfzeilenkomponente des adaptiven Formulars in den Layout-Container über dem Container des adaptiven Formulars. Nachdem Sie die Komponente hinzugefügt haben, können Sie deren Eigenschaften festlegen, mit denen Sie ein Logo hinzufügen und dessen Titel angeben können.

Wenn Sie die Fußzeilenkomponente in den Layout-Container unter dem Container des adaptiven Formulars ziehen, können Sie ebenso Urheberrechtsinformationen und Unternehmensdetails angeben.

![Kopf- und Fußzeile in der Strukturebene hinzugefügt](assets/header-and-footer.png)

Kopf- und Fußzeile in der Strukturebene hinzugefügt

#### Sperren/Entsperren von Komponenten in der Strukturebene {#locking-unlocking-components-in-the-structure-layer}

Wenn Sie die Vorlage bearbeiten, wenn die Strukturebene ausgewählt ist, können Sie die Kopf- und Fußzeile der Vorlage entsperren. Wenn eine Komponente in der Vorlage entsperrt ist, können Formularautoren die Komponente im adaptiven Formular bearbeiten, das die Vorlage verwendet. Das Sperren einer Komponente verhindert, dass Formularautoren sie im adaptiven Formular bearbeiten. Die Sperroption ist in der Komponenten-Symbolleiste verfügbar.

Beispielsweise können Sie die Kopfzeilenkomponente zur Vorlage hinzufügen. Wenn Sie die Komponente auswählen, wird in der Komponenten-Symbolleiste eine Sperroption angezeigt. In der Regel enthält die Kopfzeile den Firmennamen und das Logo und Sie möchten nicht, dass Formularautoren das Logo und die Kopfzeile in einer Vorlage ändern. In einem adaptiven Formular, das mit der Vorlage erstellt wurde, in der die Kopfzeilenkomponente gesperrt ist, können Formularautoren das Logo und den Unternehmensnamen nicht ändern.

>[!NOTE]
>
>Es wird davon abgeraten, ein Bild oder Logo in der Kopfzeilenkomponente einzeln zu sperren oder zu entsperren. Sie können die Kopfzeilenkomponente entsperren.

### Anfänglicher Inhalt {#initial-content}

Wenn die Option Anfänglicher Inhalt ausgewählt ist, wird der Container des adaptiven Formulars der Vorlage wie ein adaptives Formular zur Bearbeitung geöffnet. Wie beim Authoring eines adaptiven Formulars können Sie anfängliche Einstellungen festlegen, z. B. ein Design und Übermittlungsaktionen.

Formularautorinnen und -autoren verwenden sie als Grundlage zum Erstellen eines Formulars. Die Struktur des Inhaltsflusses wird in der Ebene „Anfänglicher Inhalt“ der Vorlage angegeben. Um zum Bearbeiten des anfänglichen Inhalts der Formularvorlage zu wechseln, wählen Sie vor der Vorschau in der Seitensymbolleiste die Option ![Arbeitsfläche-Dropdown](assets/canvas-drop-down.png) **> Anfänglicher Inhalt**.
![Ebene „Anfänglicher Inhalt“ im Vorlageneditor](assets/initial-content-layer.png)

In der Ebene „Anfänglicher Inhalt“ im Vorlageneditor ist der Container des adaptiven Formulars zum Festlegen von Eigenschaften ausgewählt.

![Anfänglicher Inhalt](assets/initial-content-layer-1.png)

Auf der Ebene Anfänglicher Inhalt erstellen Sie die adaptive Formularvorlage, die Ihre Autoren als Grundlage verwenden. Das Erstellen einer Vorlage ähnelt dem Erstellen eines Formulars. Sie verwenden die in der Seitenleiste verfügbaren Optionen. Die Seitenleiste bietet Browser für Inhalte, Eigenschaften, Assets und Komponenten.

Weitere Informationen finden Sie unter [Randleiste](../../forms/using/introduction-forms-authoring.md#sidebar).

>[!NOTE]
>
>Wenn Sie als Übermittlungsaktion „Inhalt speichern“ oder „PDF speichern“ auswählen, wird die Option zum Angeben des Speicherpfads angezeigt. Wenn Sie den Pfad in der Vorlage angeben, haben alle daraus erstellten Formulare denselben Pfad. Sie können den richtigen Speicherpfad angeben oder sicherstellen, dass Formularautorinnen und -autoren ihn aktualisieren, um zu verhindern, dass Daten aus jedem Formular an demselben Speicherort gespeichert werden.

#### Erstellen einer adaptiven Formularvorlage mit Registerkarten und Bedienfeldern  {#creating-an-adaptive-form-template-with-tabs-and-panels-nbsp}

Nehmen wir an, Sie möchten eine Vorlage mit den folgenden Registerkarten erstellen:

* Allgemeine Informationen
* Berufliche Informationen

Sie haben ein Logo hinzugefügt, einen Titel angegeben und eine Fußzeile in der Strukturebene hinzugefügt. Sperren Sie die Kopf- und Fußzeile, damit Autoren sie nicht bearbeiten, wenn sie die Vorlage zum Erstellen von Formularen verwenden.

Ändern Sie die Ebene von „Struktur“ in „Anfänglicher Inhalt“ und beginnen Sie mit dem Hinzufügen von Inhalten zum Formular. Um eine Struktur mit Registerkarten zu erstellen, fügen Sie ein untergeordnetes Bedienfeld im guideRootPanel des Containers für adaptive Formulare hinzu. So fügen Sie ein Bedienfeld hinzu:

* Sie können ein Bedienfeld hinzufügen, indem Sie auf die Schaltfläche **+** tippen, wenn Sie die Option **Komponenten hierher ziehen** auswählen.

* Sie können die Bedienfeldkomponente aus dem Komponenten-Browser in der Seitenleiste ziehen.
* Sie können ein untergeordnetes Bedienfeld von `guideRootPanel` aus der Symbolleiste hinzufügen.

Um die Registerkarten „Allgemeine Informationen“ und „Berufliche Informationen“ zu erstellen, fügen Sie zwei Bedienfelder im untergeordneten Bedienfeld von `guideRootPanel` hinzu. Wählen Sie die Bedienfelder aus und wählen Sie ![cmppr](assets/cmppr.png) , um die Eigenschaften in der Seitenleiste zu öffnen. Ändern Sie die Elementnamen in `general-info` und `professional-info` und die Titel in „Allgemeine Informationen“ bzw. „Berufliche Informationen“. Wählen Sie in der Seitenleiste Inhalt aus, um den Inhaltsbrowser zu öffnen. Wählen Sie in der Registerkarte „Formularobjekte“ `guideRootPanel` aus. Im Editor ist „guideRootPanel“ ausgewählt. Auswählen ![cmppr](assets/cmppr.png) in der Komponentensymbolleiste, um die Eigenschaften zu öffnen. Wählen Sie im Feld Bedienfeldlayout die Option **Registerkarten oben** und wählen **Fertig**. Die Vorlagenstruktur mit Registerkarten wird angewendet.

#### Hinzufügen von Inhalten in Registerkarten {#adding-content-in-tabs}

![Hinzufügen von Feldern in Vorlagen für adaptive Formulare](assets/template-edit-initial-content.png)

Nachdem Sie Bedienfelder hinzugefügt und als Registerkarten strukturiert haben, können Sie Felder in den Registerkarten hinzufügen. Wenn Sie eine Registerkarte im Editor auswählen, wird die Option **Komponenten hierhin ziehen** sichtbar. Sie können Komponenten wie Textboxen, Listenelemente und Schaltflächen per Drag-and-Drop verschieben. Sie können Komponenten aus dem Komponenten-Browser in der Seitenleiste ziehen.

Jede Komponente verfügt über Eigenschaften, die die Datenerfassung und -bearbeitung verbessern. Beispielsweise können Sie die Eigenschaft **Erforderliches Feld** einer Komponente aktivieren. Ihre Autorinnen und Autoren können eine Nachricht angeben, die Ihre Kundinnen und Kunden sehen sollen, wenn sie beim Ausfüllen ein erforderliches Feld überspringen. Geben Sie die Meldung in der Eigenschaft **Erforderliches Feld** an.

In der Beispielvorlage werden die Felder „Name“, „Telefonnummer“ und „Geburtsdatum“ auf der Registerkarte „Allgemeine Informationen“ hinzugefügt. Auf der Registerkarte „Berufliche Informationen“ werden die Felder „Derzeit beschäftigt“, „Beschäftigungstyp“ und „Bildungsabschluss“ hinzugefügt.

Nachdem Sie Felder hinzugefügt haben, können Sie Schaltflächen wie „Senden“ und „Zurücksetzen“ hinzufügen.

### Aktivieren der Vorlage {#enabling-the-template}

Wenn Sie eine Vorlage erstellen, wird sie als Entwurf hinzugefügt. Aktivieren Sie die Vorlage, um sie zum Erstellen adaptiver Formulare zu verwenden. Aktivieren einer Vorlage:

1. Navigieren Sie zu **Adobe Experience Manager > Werkzeuge > Vorlagen** und öffnen Sie den Ordner, in dem Sie die Vorlage erstellt haben.

1. Die Vorlage, die Sie erstellt haben, ist als Entwurf gekennzeichnet.
1. Wählen Sie die Vorlage aus und wählen Sie **Aktivieren** in der Symbolleiste.
Wenn Sie ein adaptives Formular erstellen, wird die Vorlage aufgeführt, wenn Sie aufgefordert werden, eine Vorlage auszuwählen.

## Importieren oder Exportieren einer Vorlage {#importing-or-exporting-a-template}

Ein Formular funktioniert mit seiner Vorlage. Wenn Sie ein adaptives Formular herunterladen, das mit einer benutzerdefinierten Vorlage erstellt wurde, wird die Vorlage nicht heruntergeladen. Wenn Sie das Formular in eine andere AEM Forms-Instanz importieren, wird es ohne Vorlage importiert. Wenn ein Formular importiert wird, aber die Vorlage nicht verfügbar ist, wird das Formular nicht gerendert. Es ist auch möglich, die benutzerdefinierte Vorlage vom `/conf`-Knoten in `https://<server>:<port>/crx/packmgr` zu verpacken und es in die AEM Forms-Instanz zu importieren, in die Sie das Formular hochladen möchten.

## Erstellen eines adaptiven Formulars mithilfe der Vorlage {#creating-an-adaptive-form-using-the-template}

Nachdem Sie eine Vorlage erstellt und aktiviert haben, ist sie im Forms Manager verfügbar, wenn Sie ein adaptives Formular erstellen. Informationen zum Verwenden einer Vorlage und Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md).

## Ändern der Anzeigeoption von nativen Vorlagen  {#change-display-option-of-out-of-the-box-templates}

Sie können benutzerdefinierte Vorlagen für adaptive Formulare erstellen, um die grundlegende Struktur und den anfänglichen Inhalt zu definieren. AEM Forms bietet außerdem eine Standardvorlage für adaptive Formulare. Sie können wählen, ob Sie die Vorlagen anzeigen oder ausblenden möchten.

Führen Sie die folgenden Schritte aus, um Vorlagen ein- und auszublenden:

1. Melden Sie sich bei der Autor-Instanz von AEM Forms an und navigieren Sie zu **Tools** > **Vorgänge** > **Web-Konsole**.

   >[!NOTE]
   >
   >Die URL der AEM-Web-Konsole lautet „https://&#39;[Server]:[Port]&#39;/system/console/configMgr“

1. Suchen und öffnen Sie die **FormsManager-Konfigurations** einstellungen:

   * Um die adaptiven Formularvorlage ein- oder auszublenden, aktivieren oder deaktivieren Sie die Option **Einbeziehen der standardmäßigen AF- und AD-Vorlagen**.
   * Um die adaptiven Formularvorlage, die in AEM 6.0 Forms oder AEM 6.1 Forms hinzugefügt wurden, jetzt aber veraltet sind, ein- oder auszublenden, aktivieren oder deaktivieren Sie die Option **Einbeziehen der AEM 6.0 AF-Vorlagen**. Wenn diese Option aktiviert ist, muss die **Vordefinierte AF- und AD-Vorlagen einschließen** Konfiguration zu aktivieren.

1. Klicken Sie auf **Speichern**. Die Anzeigeoptionen für die vordefinierten Vorlagen werden geändert.

## Empfehlungen {#recommendations}

* Wenn Sie Eigenschaften des Formulars im Vorlageneditor ändern, verwenden Sie nicht die Eigenschaft „BindReference“.
* Wenn Sie einen Haltepunkt hinzufügen möchten, erstellen Sie ihn, wenn Sie eine Vorlage für ein adaptives Formular bearbeiten.
Weitere Informationen zu Haltepunkten finden Sie unter [Responsive Layout](/help/sites-authoring/responsive-layout.md).
