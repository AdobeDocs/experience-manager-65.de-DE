---
title: Betten Sie ein adaptives Formular oder eine interaktive Kommunikation in die AEM Sites-Seite ein.
description: Sie können adaptive Formulare in AEM Sites-Seiten einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Sites-Seiten zu verlassen.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author, interactive-communications
feature: Adaptive Forms, Foundation Components
exl-id: 00ee7929-649f-4cbb-be79-ba13ac73a16d
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 100%

---

# Betten Sie ein adaptives Formular oder eine interaktive Kommunikation in die AEM Sites-Seite ein. {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/embed-adaptive-form-aem-sites.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


## Übersicht {#overview}

Mit AEM Forms können Formularentwickler nahtlos adaptive Formulare in eine AEM Sites-Seite oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular und die interaktive Kommunikation sind voll funktionsfähig und die Benutzenden können es ausfüllen und abschicken, ohne die Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular oder der interaktiven Kommunikation zu interagieren.

Weitere Informationen zum Einbetten eines adaptiven Formulars in eine externe Website finden Sie unter [Adaptive Formulare in externe Webseiten einbetten](/help/forms/using/embed-adaptive-form-external-web-page.md).

Auf einer AEM Sites-Seite können Sie ein adaptives Formular oder interaktive Kommunikation auf folgende Weise hinzufügen:

* **[AEM Forms-Container-Komponente](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms stellt eine Komponente bereit, die Sie Ihren Sites-Seiten hinzufügen können. Über die AEM Forms-Container-Komponente können Sie ein adaptives Formular und interaktive Kommunikation einbetten.

* **[Asset Browser](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)** Alle Formulare und interaktiven Kommunikationen, die Sie erstellen, sind unter „Assets“ verfügbar. Sie können das Formular als Asset mittels Drag-and-Drop auf Ihrer Seite einfügen.

## Voraussetzungen {#prerequisites}

Wenn Sie ein adaptives Formular oder die interaktive Kommunikation in eine AEM Sites-Seite einbetten möchten, die eine bearbeitbare Vorlage verwendet, stellen Sie sicher, dass die AEM Form-Komponente als zulässige Komponente in der verknüpften Vorlage konfiguriert ist. Weitere Informationen finden Sie im Abschnitt **Richtlinie und Eigenschaften (Layout-Container)** unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

Wenn eine Sites-Seite eine statische Vorlage verwendet, müssen Sie sie im Absatzsystem der Seite konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Design-Modus](/help/sites-authoring/default-components-designmode.md).

## Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation {#af-component}

Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation mithilfe der AEM Forms-Container-Komponente:

1. Öffnen Sie im Bearbeitungsmodus die AEM Sites-Seite, in die Sie ein adaptives Formular oder interaktive Kommunikation einfügen möchten.
1. Ziehen Sie die AEM Forms-Container-Komponente aus dem Komponenten-Browser auf die Seite.

   Alternativ dazu können Sie im Assets-Browser nach einem adaptiven Formular suchen und es dann per Drag-and-drop auf die Sites-Seite ziehen. Dadurch wird das Formular in einen AEM Forms-Container eingebettet.

   >[!NOTE]
   >
   >Mehrere AEM Forms-Container-Komponenten auf einer Seite werden nicht unterstützt.

1. Wählen Sie die eingebettete AEM Forms-Container-Komponente in der Sites-Seite und dann ![settings_icon](assets/settings_icon.png) in der Aktionsleiste aus. Das Dialogfeld **[!UICONTROL AEM Forms-Container bearbeiten]** wird geöffnet.
1. Geben Sie im Dialogfeld „AEM Forms-Container bearbeiten“ Folgendes an.

   * **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets. Die Optionen sind „Adaptives Formular“ und „Interaktive Kommunikation“
   * **Asset-Pfad**: Suchen Sie nach dem einzubettenden adaptiven Formular und wählen Sie es aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
   * (Nur adaptives Formular) **Nach dem Senden**: Wählen Sie die Aktion aus, die nach der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankesseite angezeigt werden soll.

      * **Dankesnachricht**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
      * **Dankesseite**: Klicken Sie auf „Durchsuchen“ und wählen Sie die Seite aus, die bei Übermittlung eines Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
      * **Seite beim Senden aktualisieren**: Aktivieren Sie diese Option, um die Seite mit dem eingebetteten adaptiven Formular zu aktualisieren und die Dankesseite anzuzeigen. Andernfalls ersetzt die Dankesseite das adaptive Formular im AEM Forms-Container, ohne die Seite zu aktualisieren. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.

   * **Thema**: Wählen Sie ein Thema, das die Formatierung der Komponenten in Ihrem adaptiven Formular oder interaktiver Kommunikation definiert. Zur Formatierung gehören Eigenschaften des Erscheinungsbildes, wie Schriftschnitt, Hintergrundfarbe, Abmessungen und Ausrichtung.
   * **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie es leer, um die Größe des Containers automatisch zu anzupassen.
   * **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.

1. Speichern Sie die Einstellungen. Das adaptive Formular bzw. die interaktive Kommunikation wird jetzt in der Seite eingebettet.

## Veröffentlichen eingebetteter adaptiver Formulare und interaktiver Kommunikation {#publishing-embedded-adaptive-form-and-interactive-communication}

Betrachten wir die folgenden Szenarien für die Veröffentlichung eines eingebetteten Assets (eingebettetes Formular oder interaktive Kommunikation) in der AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular oder interaktive Kommunikation enthält, veröffentlichen Sie die Siteseite und das eingebettete Formular oder Dokument.
* Wenn Sie nur das eingebettete adaptive Formular oder die interaktive Kommunikation auf einer veröffentlichten Seite geändert haben, werden beim Veröffentlichen des Original-Assets die Änderungen in die veröffentlichte Seite übernommen. Die veröffentlichte Sites-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Site-Seite und das eingebettete adaptive Formular oder die interaktive Kommunikation geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Eingebettete adaptive Formulare und interaktive Kommunikation bearbeiten {#modifying-embedded-adaptive-form-and-interactive-communication}

Die AEM Sites-Seite behält einen Verweis auf das adaptive Formular und die interaktive Kommunikation im AEM Forms-Container bei. Deshalb werden alle Konfigurationen und Eigenschaften, beispielsweise Design, Stile und die Sendeaktion, die im ursprünglichen adaptiven Formular und der interaktiven Kommunikation konfiguriert wurden, im eingebetteten adaptiven Formular und der interaktiven Kommunikation beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das ursprüngliche Formular in adaptiven Formularen oder interaktiver Kommunikation in den entsprechenden Editoren und modifizieren Sie diese.
* Wählen Sie auf der Site-Seite im Bearbeitungsmodus das adaptive Formular bzw. die interaktive Kommunikation und dann **[!UICONTROL In neuem Fenster bearbeiten]** aus. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass Sie es bearbeiten können.

>[!NOTE]
>
>Die im ursprünglichen adaptiven Formular oder in der interaktiven Kommunikation vorgenommenen Änderungen werden automatisch in das eingebettete Formular übernommen. Allerdings müssen Sie das adaptive Formular oder die Sites-Seite erneut veröffentlichen, damit die Änderungen in der veröffentlichten Seite angezeigt werden.

## Aspekte und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM Sites-Seiten einbetten:

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den entsprechenden Registerkarten im Formularportal sichtbar.
* Die im Originalformular konfigurierte Übermittlungsaktion wird im eingebetteten Formular beibehalten.
* Die Experience Targeting- und A/B-Test-Konfigurationen im Originalformular funktionieren nicht im eingebetteten Formular. Sie können jedoch auf der Sites-Seite das Experience Targeting verwenden, um verschiedene Formulare auf der Grundlage von Benutzerprofilen anzuzeigen.
* Wenn Sie für das Originalformular Adobe Analytics konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
