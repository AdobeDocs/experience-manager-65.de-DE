---
title: Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in ein Einzelseiten-Programm von AEM Sites
description: Betten Sie adaptive Formulare oder interaktive Kommunikation in AEM Sites-Seiten ein. Benutzer können Formulare ausfüllen und senden, ohne die Sites-Seite zu verlassen.
topic-tags: author, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms
exl-id: b549f176-409a-4d81-8c2b-73d0dd0c6649
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1107'
ht-degree: 100%

---

# Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in ein Einzelseiten-Programm von AEM Sites{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-single-page-application}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

## Übersicht {#overview}

Mit AEM Forms können Formularentwickler adaptive Formulare und interaktive Kommunikation nahtlos in eine AEM Sites-Einzelseiten-Anwendung (SPA) einbetten. Das eingebettete adaptive Formular und die interaktive Kommunikation sind voll funktionsfähig und die Benutzer können es ausfüllen und abschicken, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular oder der interaktiven Kommunkation zu interagieren.

In AEM Sites-Einzelseiten-Anwendungen können Sie ein adaptives Formular oder eine interaktive Kommunikation mit der [AEM Forms SPA-Container-Komponente](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component)[ hinzufügen.](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) Es handelt sich um eine AEM Forms-Komponente für AEM Sites SPA, die Sie Ihrer Sites-Seite hinzufügen können.

Informationen zum Einbetten eines adaptiven Formulars in eine AEM Sites, die keine SPA ist, finden Sie unter [Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation in AEM Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md).

## Voraussetzungen {#prerequisites}

Um ein adaptives Formular oder eine interaktive Kommunikation mithilfe der AEM Forms SPA Container-Komponente in ein AEM Sites SPA einzubetten, müssen Sie sicherstellen, dass Sie Folgendes installiert haben:

* Java SE Development Kit 8 oder höher
* Apache Maven 3.3.1 oder höher
* AEM-Autoreninstanz
* [AEM Forms 6.4.2 Add-On-Paket](https://helpx.adobe.com/de/aem-forms/kb/aem-forms-releases.html) auf Autoreninstanz

## AEM Forms SPA-Container-Komponente installieren {#install-aem-forms-spa-container-component}

Führen Sie die folgenden Schritte aus, um die AEM Forms SPA-Container-Komponente zu installieren:

1. [AEM Forms-Komponente für SPA klonen oder herunterladen](https://de.github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa).
1. Installieren Sie die AEM Forms-Komponente für SPA. Die Anweisungen zum Installieren der Komponente finden Sie in der [README.md](https://de.github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa#aem-form-component)-Datei.

   Die Komponente enthält eine [Beispiel-React-Komponente](https://de.github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component), die verwendet werden kann, um die SPA Container-Komponente in ein React-basiertes SPA-Projekt zu integrieren.

1. [React-basiertes SPA-Projekt klonen oder herunterladen](https://de.github.com/adobe/aem-sample-we-retail-journal).
1. Integrieren Sie SPA-Container-Komponente mit einem React-basierten SPA-Projekt, mithilfe der Anweisungen in der [README.md](https://de.github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component#aem-form-react-component-for-spa---editor)-Datei.

   Nachdem Sie die AEM Forms SPA-Container-Komponente installiert und die Komponente in ein React-basiertes SPA-Projekt integriert haben, können Sie adaptive Formulare und interaktive Kommunikation in die AEM Sites-Seite einbetten.

## Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation {#af-component}

Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation mit der AEM Forms-Container-Komponente:

1. Öffnen Sie die Seite AEM Sites im Bearbeitungsmodus, in die Sie ein adaptives Formular oder eine interaktive Kommunikation einbetten möchten.
1. Fügen Sie die Komponente **AEM Forms for SPA** auf der Seite ein, indem Sie eine der folgenden Optionen verwenden:

   * Wählen Sie den Layout-Container auf der Seite „Sites“, dann **+** und schließlich die Komponente **AEM Forms for SPA** aus.

   * Ziehen Sie die Komponente **AEM Forms for SPA** aus dem Komponenten-Browser auf die Seite.
   * Suchen Sie im Assets-Browser nach einem adaptiven Formular oder einer interaktiven Kommunikation und ziehen Sie es per Drag &amp; Drop auf die Seite „Sites“. Es bettet das Formular in einen AEM Forms for SPA-Komponenten-Container ein.

   >[!NOTE]
   >
   >Das Rendern von mehreren AEM Forms SPA-Container-Komponenten auf einer Seite wird nicht unterstützt. Sie können mehrere AEM Forms SPA-Container auf einer Seite haben, es wird jedoch jeweils nur eine Komponente gerendert. Stellen Sie sicher, dass nur eine Komponente auf einer Seite sichtbar ist, um Abweichungen zu vermeiden.

1. Wählen Sie auf der Seite „Sites“ die eingebettete AEM Forms-Container-Komponente und dann in der Aktionsleiste das Symbol ![settings_icon](assets/settings_icon.png) aus. Das Dialogfeld **AEM Forms-Container bearbeiten** wird geöffnet.
1. Geben Sie im Dialogfeld **AEM Forms-Container bearbeiten** Folgendes an:

   * **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets. Die Optionen sind **adaptives Formular** und **interaktive Kommunikation**

   * **Asset Path**: Durchsuchen Sie das adaptive Formular oder die interaktive Kommunikation, die Sie einbetten möchten, und wählen Sie sie aus. Das Feld wird automatisch ausgefüllt, wenn ein adaptives Formular oder eine interaktive Kommunikation über den Assets-Browser eingefügt wird.
   * **Kanal** (Nur interaktive Kommunikation): Wählen Sie den Typ des einzubettenden interaktiven Kanals aus. Die Optionen sind **Webkanal** und **Druckkanal**.

   * **Design**: Wählen Sie ein Design, das die Formatierung der Komponenten in Ihrem adaptiven Formular oder interaktiver Kommunikation definiert. Zur Formatierung gehören Eigenschaften des Erscheinungsbildes, wie Schriftschnitt, Hintergrundfarbe, Abmessungen und Ausrichtung.

1. Wählen Sie ![done_icon](assets/done_icon.png), um die Änderungen zu speichern. Das adaptive Formular oder die interaktive Kommunikation ist jetzt in der Seite eingebettet.

## Veröffentlichen von eingebetteten adaptiven Formularen und interaktiver Kommunikation {#publish-embedded-adaptive-form-and-interactive-communication}

Betrachten Sie die folgenden Szenarien für die Veröffentlichung eines eingebetteten Assets (eingebettetes Formular oder interaktive Kommunikation) in der AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular oder interaktive Kommunikation enthält, veröffentlichen Sie die Site-Seite und das eingebettete Asset.
* Wenn Sie nur das eingebettete adaptive Formular oder die interaktive Kommunikation in einer veröffentlichte Site-Seite geändert haben, veröffentlichen Sie das Original-Asset und die Änderungen werden auf der veröffentlichten Site-Seite übernommen. Die veröffentliche Site-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Site-Seite und das eingebettete adaptive Formular oder die interaktive Kommunikation geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern des eingebetteten adaptiven Formulars und der interaktiven Kommunikation {#modify-embedded-adaptive-form-and-interactive-communication}

Die AEM Sites-Seite behält einen Verweis auf das adaptive Formular und die interaktive Kommunikation im AEM Forms-Container bei. Deshalb werden alle Konfigurationen und Eigenschaften, beispielsweise Design, Stile und die Sendeaktion, die im ursprünglichen adaptiven Formular und der interaktiven Kommunikation konfiguriert wurden, im eingebetteten adaptiven Formular und der interaktiven Kommunikation beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das ursprüngliche Formular in adaptiven Formularen oder interaktiver Kommunikation in den entsprechenden Editoren und modifizieren Sie diese.
* Wählen Sie das adaptive Formular oder die interaktive Kommunikation auf der Sites-Seite im Bearbeitungsmodus und dann **In neuem Fenster bearbeiten** aus. Das ursprügliche Formular wird im Bearbeitungsmodus geöffnet. 

## Aspekte und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM Sites-Seiten einbetten:

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den entsprechenden Registerkarten im Formularportal sichtbar.
* Die im Originalformular konfigurierte Übermittlungsaktion wird im eingebetteten Formular beibehalten.
* Die Experience Targeting- und A/B-Test-Konfigurationen im Originalformular funktionieren nicht im eingebetteten Formular. Sie können jedoch auf der Sites-Seite das Erfahrungs-Targeting verwenden, um verschiedene Formulare auf der Grundlage von Benutzerprofilen anzuzeigen.
* Wenn Sie für das Originalformular Adobe Analytics konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
