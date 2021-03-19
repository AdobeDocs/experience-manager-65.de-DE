---
title: Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in eine AEM Sites-Einzelseitenanwendung
seo-title: Adaptive Formulare oder interaktive Kommunikation in AEM Sites-Seiten einbetten
description: Betten Sie adaptive Formulare oder interaktive Kommunikation in AEM Sites-Seiten ein. Benutzer können Formulare ausfüllen und senden, ohne die Seite "Sites"zu verlassen.
seo-description: Sie können adaptive Formulare oder interaktive Kommunikation in AEM Sites-Seiten einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Seite "Sites"zu verlassen.
uuid: 4c75494e-e9d2-43b9-bbae-562e0eda8abb
topic-tags: author, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a74ed6c1-3006-4baf-bd77-ad4045e23c22
docset: aem65
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1123'
ht-degree: 11%

---


# Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in eine AEM Sites-Einzelseitenanwendung{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-single-page-application}

## Überblick {#overview}

Mit AEM Forms können Formularentwickler adaptive Formulare und interaktive Kommunikation nahtlos in eine AEM Sites-Einzelseitenanwendung (SPA) einbetten. Das eingebettete adaptive Formular und die interaktive Kommunikation sind voll funktionsfähig. Benutzer können das Formular ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem adaptiven Formular oder der interaktiven Kommunikation zu interagieren.

In der AEM Sites-Einzelseitenanwendung können Sie ein adaptives Formular oder eine interaktive Kommunikation mit der Komponente [AEM Forms SPA Container](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component)[ hinzufügen.](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) Es handelt sich um eine AEM Forms-Komponente für AEM Sites SPA, die Sie Ihrer Siteseite hinzufügen können.

Informationen zum Einbetten eines adaptiven Formulars in ein Nicht-SPA-AEM Sites finden Sie unter [Adaptives Formular oder interaktive Kommunikation in AEM Sites einbetten](/help/forms/using/embed-adaptive-form-aem-sites.md).

## Voraussetzungen {#prerequisites}

Um ein adaptives Formular oder eine interaktive Kommunikation in eine AEM mit der Komponente AEM Forms SPA Container einzubetten, stellen Sie sicher, dass Sie Folgendes installiert haben:

* Java SE Development Kit 8 oder neuer
* Apache Maven 3.3.1 oder neuer
* AEM Autoreninstanz
* [AEM Forms 6.4.2 Add-On-](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) Paket auf Autoreninstanz

## AEM Forms SPA Container-Komponente {#install-aem-forms-spa-container-component} installieren

Führen Sie die folgenden Schritte aus, um die Komponente AEM Forms SPA Container zu installieren:

1. [Klonen oder laden Sie die AEM Forms-Komponente für SPA](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa) herunter.
1. Installieren Sie die AEM Forms-Komponente für SPA. Die Anweisungen zum Installieren der Komponente finden Sie in der Datei [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa#aem-form-component).

   Die Komponente enthält eine [Beispiel-React-Komponente](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component), die verwendet werden kann, um SPA Container-Komponente in ein react-basiertes SPA zu integrieren.

1. [Klonen oder Herunterladen eines react-basierten SPA Projekts](https://github.com/adobe/aem-sample-we-retail-journal).
1. Integrieren Sie SPA Container-Komponente in ein react-basiertes SPA mithilfe der Anweisungen, die in der Datei [README.md](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component#aem-form-react-component-for-spa---editor) verfügbar sind.

   Nach der Installation der Komponente AEM Forms SPA Container und der Integration der Komponente in ein react-basiertes SPA können Sie adaptive Formulare und interaktive Kommunikation in die AEM Sites-Seite einbetten.

## Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation {#af-component}

So betten Sie ein adaptives Formular oder eine interaktive Kommunikation mit AEM Forms für SPA Container ein:

1. Öffnen Sie die Seite &quot;AEM Sites&quot;im Bearbeitungsmodus, in die Sie ein adaptives Formular oder interaktive Kommunikation einbetten möchten.
1. Fügen Sie die Komponente **AEM Formular für SPA** mit einer der folgenden Optionen auf der Seite ein:

   * Tippen Sie auf der Seite &quot;Sites&quot;auf den Container layout, klicken Sie auf **+** und wählen Sie das **AEM Formular für SPA** aus.

   * Ziehen Sie im Komponenten-Browser die Komponente **AEM Formular für SPA** auf die Seite.
   * Suchen Sie im Asset-Browser nach einem adaptiven Formular oder einer interaktiven Kommunikation und ziehen Sie es auf die Seite &quot;Sites&quot;. Bettet das Formular in ein AEM Forms für SPA Komponenten-Container ein.

   >[!NOTE]
   >
   >Das Rendern mehrerer AEM Forms SPA Container-Komponenten auf einer Seite wird nicht unterstützt. Sie können mehrere AEM Forms SPA Container auf einer Seite haben, es wird jedoch jeweils nur eine Komponente gerendert. Stellen Sie sicher, dass nur eine Komponente auf einer Seite sichtbar ist, um Diskrepanzen zu vermeiden.

1. Tippen Sie auf der Seite &quot;Sites&quot;auf die eingebettete Komponente &quot;AEM Forms SPA Container&quot;und dann in der Aktionsleiste auf ![settings_icon](assets/settings_icon.png). Das Dialogfeld **AEM Forms SPA Container bearbeiten** wird geöffnet.
1. Geben Sie im Dialogfeld **AEM Forms-Container bearbeiten** Folgendes an:

   * **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets. Die Optionen sind **Adaptives Formular** und **Interaktive Kommunikation**

   * **Asset-Pfad**: Navigieren Sie zum einzubettenden adaptiven Formular oder zur einzubettenden interaktiven Kommunikation und wählen Sie sie aus. Das Feld wird automatisch ausgefüllt, wenn ein adaptives Formular oder eine interaktive Kommunikation über den Assets-Browser eingefügt wird.
   * **Kanal**  (nur interaktive Kommunikation): Wählen Sie den Typ des einzubettenden interaktiven Kanals aus. Die Optionen sind **Web Kanal** und **Kanal drucken**.

   * **Thema**: Wählen Sie ein Design aus, das die Formatierung für Komponenten Ihres adaptiven Formulars oder der interaktiven Kommunikation definiert. Die Formatierung enthält Erscheinungsbildeigenschaften wie Schriftart, Hintergrundfarbe, Größe und Ausrichtung ein.

1. Tippen Sie auf ![done_icon](assets/done_icon.png), um die Einstellungen zu speichern. Das adaptive Formular oder die interaktive Kommunikation sind jetzt in die Seite eingebettet.

## Veröffentlichen von eingebetteten adaptiven Formularen und interaktiver Kommunikation {#publish-embedded-adaptive-form-and-interactive-communication}

Betrachten Sie die folgenden Szenarien zum Veröffentlichen eines eingebetteten Assets (adaptives Formular oder interaktive Kommunikation) auf der AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular oder eine interaktive Kommunikation enthält, veröffentlichen Sie die Seite &quot;Sites&quot;und das eingebettete Asset.
* Wenn Sie nur das eingebettete adaptive Formular oder die interaktive Kommunikation auf einer Seite mit veröffentlichten Sites geändert haben, veröffentlichen Sie das ursprüngliche Asset und die Änderungen werden auf der Seite &quot;Sites&quot;übernommen. Die Seite &quot;Veröffentlichte Sites&quot;enthält einen Verweis auf das Asset und erfordert keine erneute Veröffentlichung der Seite.
* Wenn Sie die Seite &quot;Sites&quot;und das eingebettete adaptive Formular oder die interaktive Kommunikation geändert haben, veröffentlichen Sie die Seite &quot;Sites&quot;und das eingebettete Asset erneut.

## Eingebettetes adaptives Formular und Interaktive Kommunikation ändern {#modify-embedded-adaptive-form-and-interactive-communication}

AEM Siteseite behält einen Verweis auf das adaptive Formular und die interaktive Kommunikation im AEM Forms-Container bei. Daher werden alle Konfigurationen und Eigenschaften, wie das Design, die Stile und die Übermittlungsaktion, die im ursprünglichen adaptiven Formular und in der interaktiven Kommunikation konfiguriert wurden, im eingebetteten adaptiven Formular und in der interaktiven Kommunikation beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars und der interaktiven Kommunikation zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen oder in der interaktiven Kommunikation in den entsprechenden Editoren und ändern Sie es.
* Tippen Sie auf der Seite &quot;Sites&quot;im Bearbeitungsmodus auf das adaptive Formular oder die interaktive Kommunikation und dann auf **In einem neuen Fenster bearbeiten**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet.

## Überlegungen und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM-Siteseiten einbetten:

* Die Kopf- und Fußzeile im Originalformular werden im eingebetteten Formular nicht übernommen.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf der entsprechenden Registerkarte im Forms Portal sichtbar.
* Die im Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten Formular nicht. Sie können jedoch Erlebnis-Targeting auf der Seite &quot;Sites&quot;verwenden, um verschiedene Formulare basierend auf den Profilen des Benutzers anzuzeigen.
* Wenn Sie Adobe Analytics für das Originalformular konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

