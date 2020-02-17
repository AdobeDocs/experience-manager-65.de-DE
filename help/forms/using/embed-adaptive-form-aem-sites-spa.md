---
title: Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in AEM Sites-Einzelseitenanwendung
seo-title: Adaptive Formulare oder interaktive Kommunikation in AEM-Siteseiten einbetten
description: Betten Sie adaptive Formulare oder interaktive Kommunikation in AEM-Siteseiten ein. Benutzer können Formulare ausfüllen und senden, ohne die Seite "Sites"zu verlassen.
seo-description: Sie können adaptive Formulare oder interaktive Kommunikation in AEM-Siteseiten einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Seite "Sites"zu verlassen.
uuid: 4c75494e-e9d2-43b9-bbae-562e0eda8abb
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a74ed6c1-3006-4baf-bd77-ad4045e23c22
docset: aem65
translation-type: tm+mt
source-git-commit: d12d35bf8355d3069071523427a7794b88c09b13

---


# Embed an adaptive form or Interactive Communication in AEM Sites Single Page Application{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-single-page-application}

## Überblick {#overview}

Mit AEM Forms können Formularentwickler adaptive Formulare und interaktive Kommunikation nahtlos in eine AEM Sites-Einzelseitenanwendung (SPA) einbetten. Das eingebettete adaptive Formular und die interaktive Kommunikation sind voll funktionsfähig. Benutzer können das Formular ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem adaptiven Formular oder der interaktiven Kommunikation zu interagieren.

In der Einzelseitenanwendung für AEM-Sites können Sie ein adaptives Formular oder eine interaktive Kommunikation mit der Komponente [AEM Forms SPA-Container hinzufügen](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component)[.](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) Es handelt sich um eine AEM Forms-Komponente für AEM-Sites-SPAs, die Sie Ihrer Siteseite hinzufügen können.

Weitere Informationen zum Einbetten eines adaptiven Formulars in Nicht-SPA-AEM-Sites finden Sie unter [Einbetten eines adaptiven Formulars oder interaktive Kommunikation in AEM-Sites](/help/forms/using/embed-adaptive-form-aem-sites.md).

## Voraussetzungen {#prerequisites}

Um ein adaptives Formular oder eine interaktive Kommunikation mit der Komponente AEM Forms SPA-Container in eine AEM-Site-SPA einzubetten, stellen Sie sicher, dass Sie Folgendes installiert haben:

* Java SE Development Kit 8 oder neuer
* Apache Maven 3.3.1 oder neuer
* AEM-Autoreninstanz
* [Add-On-Paket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) für AEM Forms 6.4.2 in der Autoreninstanz

## Installieren der AEM Forms SPA-Container-Komponente {#install-aem-forms-spa-container-component}

Führen Sie die folgenden Schritte aus, um die AEM Forms SPA-Container-Komponente zu installieren:

1. [Klonen oder laden Sie die AEM Forms-Komponente für SPA](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa)herunter.
1. Installieren Sie die AEM Forms-Komponente für SPA. Die Anweisungen zum Installieren der Komponente finden Sie in der Datei [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa#aem-form-component) .

   Die Komponente enthält eine [Beispielkomponente](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component) &quot;React&quot;, die zur Integration der SPA-Container-Komponente in ein reaktives SPA-Projekt verwendet werden kann.

1. [Klonen oder Herunterladen eines react-basierten SPA-Projekts](https://github.com/adobe/aem-sample-we-retail-journal).
1. Integrieren Sie die SPA-Container-Komponente mit einem react-basierten SPA-Projekt, indem Sie die Anweisungen in der Datei [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component#aem-form-react-component-for-spa---editor) verwenden.

   Nach der Installation der AEM Forms SPA-Container-Komponente und der Integration der Komponente in ein reaktives SPA-Projekt können Sie adaptive Formulare und interaktive Kommunikation in die AEM-Siteseite einbetten.

## Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation {#af-component}

So betten Sie ein adaptives Formular oder eine interaktive Kommunikation mit AEM Forms für SPA-Container ein:

1. Öffnen Sie die AEM-Siteseite im Bearbeitungsmodus, in die Sie ein adaptives Formular oder eine interaktive Kommunikation einbetten möchten.
1. Fügen Sie die **AEM Form for SPA** -Komponente mit einer der folgenden Optionen auf der Seite ein:

   * Tippen Sie auf der Seite &quot;Sites&quot;auf den Layout-Container, tippen Sie auf **+** und wählen Sie die **AEM Form for SPA** -Komponente aus.

   * From the Component browser panel, drag-drop the **AEM Form for SPA** component on the page.
   * Suchen Sie im Asset-Browser nach einem adaptiven Formular oder einer interaktiven Kommunikation und ziehen Sie es auf die Seite &quot;Sites&quot;. Bettet das Formular in einen AEM Forms for SPA-Komponentenbehälter ein.
   >[!NOTE]
   >
   >Die Wiedergabe mehrerer AEM Forms-SPA-Container-Komponenten auf einer Seite wird nicht unterstützt. Sie können mehrere AEM Forms SPA-Container auf einer Seite haben, es wird jedoch jeweils nur eine Komponente gerendert. Stellen Sie sicher, dass nur eine Komponente auf einer Seite sichtbar ist, um Diskrepanzen zu vermeiden.

1. Tap the embedded AEM Forms SPA Container component in the sites page, and then tap ![settings_icon](assets/settings_icon.png) on the action bar. The **Edit AEM Forms SPA Container** dialog opens.
1. In the **Edit AEM Forms Container** dialog, specify the following:

   * **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets. The options are **Adaptive Form** and **Interactive Communication**

   * **Asset-Pfad**: Navigieren Sie zum einzubettenden adaptiven Formular oder zur einzubettenden interaktiven Kommunikation und wählen Sie sie aus. Das Feld wird automatisch ausgefüllt, wenn ein adaptives Formular oder eine interaktive Kommunikation über den Assets-Browser eingefügt wird.
   * **Kanal** (nur interaktive Kommunikation): Wählen Sie den Typ des einzubettenden interaktiven Kanals aus. Die Optionen sind **Webkanal** und **Druckkanal**.

   * **Thema**: Wählen Sie ein Design aus, das die Formatierung für Komponenten Ihres adaptiven Formulars oder der interaktiven Kommunikation definiert. Die Formatierung enthält Erscheinungsbildeigenschaften wie Schriftart, Hintergrundfarbe, Größe und Ausrichtung ein.

1. Tap ![](assets/done_icon.png) to save the settings. Das adaptive Formular oder die interaktive Kommunikation sind jetzt in die Seite eingebettet.

## Veröffentlichen von eingebetteten adaptiven Formularen und interaktiver Kommunikation {#publish-embedded-adaptive-form-and-interactive-communication}

Betrachten Sie die folgenden Szenarien zum Veröffentlichen eines eingebetteten Assets (adaptives Formular oder interaktive Kommunikation) auf der Seite AEM-Sites:

* Wenn Sie die Seite &quot;AEM-Sites&quot;zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular oder eine interaktive Kommunikation enthält, veröffentlichen Sie die Seite &quot;Sites&quot;und das eingebettete Asset.
* Wenn Sie nur das eingebettete adaptive Formular oder die interaktive Kommunikation auf einer Seite mit veröffentlichten Sites geändert haben, veröffentlichen Sie das ursprüngliche Asset und die Änderungen werden auf der Seite &quot;Sites&quot;übernommen. Die Seite &quot;Veröffentlichte Sites&quot;enthält einen Verweis auf das Asset und erfordert keine erneute Veröffentlichung der Seite.
* Wenn Sie die Seite &quot;Sites&quot;und das eingebettete adaptive Formular oder die interaktive Kommunikation geändert haben, veröffentlichen Sie die Seite &quot;Sites&quot;und das eingebettete Asset erneut.

## Eingebettetes adaptives Formular und interaktive Kommunikation ändern {#modify-embedded-adaptive-form-and-interactive-communication}

Die AEM-Siteseite enthält einen Verweis auf das adaptive Formular und die interaktive Kommunikation im AEM Forms-Container. Daher werden alle Konfigurationen und Eigenschaften, wie das Design, die Stile und die Übermittlungsaktion, die im ursprünglichen adaptiven Formular und in der interaktiven Kommunikation konfiguriert wurden, im eingebetteten adaptiven Formular und in der interaktiven Kommunikation beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars und der interaktiven Kommunikation zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen oder in der interaktiven Kommunikation in den entsprechenden Editoren und ändern Sie es.
* Tap the adaptive form or Interactive Communication from within the Sites page in edit mode and then tap **Edit in a new window**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet.

## Überlegungen und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM-Siteseiten einbetten:

* Die Kopf- und Fußzeile im Originalformular werden im eingebetteten Formular nicht übernommen.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf der entsprechenden Registerkarte im Forms Portal sichtbar.
* Die im Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten Formular nicht. Sie können jedoch Erlebnis-Targeting auf der Seite &quot;Sites&quot;verwenden, um verschiedene Formulare basierend auf Benutzerprofilen darzustellen.
* Wenn Adobe Analytics für das Originalformular konfiguriert ist, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

