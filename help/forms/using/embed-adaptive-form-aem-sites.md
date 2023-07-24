---
title: Betten Sie ein adaptives Formular oder eine interaktive Kommunikation in die AEM Sites-Seite ein.
seo-title: Embed an adaptive form or interactive communication in AEM sites page
description: Sie können adaptive Formulare in Seiten AEM Sites einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Sites-Seiten zu verlassen.
seo-description: You can embed adaptive forms in AEM sites pages. Users can fill and submit forms without leaving the site pages.
uuid: 59b49e2f-6d95-42e5-b31e-fc40936c42d2
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author, interactive-communications
discoiquuid: 43362643-69cd-4006-a613-f998c79eeddc
feature: Adaptive Forms
exl-id: 00ee7929-649f-4cbb-be79-ba13ac73a16d
source-git-commit: e7a3558ae04cd6816ed73589c67b0297f05adce2
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 71%

---

# Betten Sie ein adaptives Formular oder eine interaktive Kommunikation in die AEM Sites-Seite ein. {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) für [Erstellen neuer adaptiver Forms](/help/forms/using/create-an-adaptive-form-core-components.md) oder [Hinzufügen von Adaptive Forms zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Forms dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von Adaptive Forms mithilfe von Foundation-Komponenten beschrieben. </span>

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/embed-adaptive-form-aem-sites.html) |
| AEM 6.5 | Dieser Artikel |


## Übersicht {#overview}

Mit AEM Forms können Formularentwickler nahtlos adaptive Formulare in eine AEM Sites-Seite oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular und die interaktive Kommunikation sind voll funktionsfähig und Benutzer können das Formular ausfüllen und senden, ohne die Seite zu verlassen. Dies hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular oder der interaktiven Kommunikation zu interagieren.

Weitere Informationen zum Einbetten eines adaptiven Formulars in eine externe Website finden Sie unter [Adaptive Formulare in externe Webseiten einbetten](/help/forms/using/embed-adaptive-form-external-web-page.md).

Auf einer AEM Sites-Seite können Sie ein adaptives Formular oder interaktive Kommunikation auf folgende Weise hinzufügen:

* **[AEM Forms-Container-Komponente](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)**
AEM Forms stellt eine Komponente bereit, die Sie Ihren Sites-Seiten hinzufügen können. Über die AEM Forms-Container-Komponente können Sie ein adaptives Formular und interaktive Kommunikation einbetten.

* **[Asset Browser](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)** Alle Formulare und interaktiven Kommunikationen, die Sie erstellen, sind unter „Assets“ verfügbar. Sie können das Formular als Asset mittels Drag-and-Drop auf Ihrer Seite einfügen.

## Voraussetzungen {#prerequisites}

Wenn Sie ein adaptives Formular oder die interaktive Kommunikation in eine AEM Sites-Seite einbetten möchten, die eine bearbeitbare Vorlage verwendet, stellen Sie sicher, dass die AEM Form-Komponente als zulässige Komponente in der verknüpften Vorlage konfiguriert ist. Weitere Informationen finden Sie im Abschnitt **Richtlinie und Eigenschaften (Layout-Container)** unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

Falls eine Sites-Seite eine statische Vorlage verwendet, müssen Sie sie im Absatzsystem der Seite konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](/help/sites-authoring/default-components-designmode.md).

## Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation {#af-component}

So betten Sie ein adaptives Formular oder eine interaktive Kommunikation mithilfe der AEM Forms Container-Komponente ein:

1. Öffnen Sie im Bearbeitungsmodus die AEM Sites-Seite, in die Sie ein adaptives Formular oder interaktive Kommunikation einfügen möchten.
1. Ziehen Sie die AEM Forms-Container-Komponente aus dem Komponenten-Browser auf die Seite.

   Alternativ können Sie nach einem adaptiven Formular oder einer interaktiven Kommunikation im Assets-Browser suchen und es per Drag-and-Drop auf die Sites-Seite ziehen. Dadurch wird das Formular in einen AEM Forms-Container eingebettet.

   >[!NOTE]
   >
   >Mehrere AEM Forms-Container-Komponenten auf einer Seite werden nicht unterstützt.

1. Tippen Sie auf die eingebettete AEM Forms-Container-Komponente in der Sites-Seite und tippen Sie dann auf ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Das Dialogfeld **[!UICONTROL AEM Forms-Container bearbeiten]** wird geöffnet.
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
* Wenn Sie die Siteseite und das eingebettete adaptive Formular oder die interaktive Kommunikation geändert haben, veröffentlichen Sie die Siteseite und das eingebettete Asset erneut.

## Eingebettete adaptive Formulare und interaktive Kommunikation bearbeiten {#modifying-embedded-adaptive-form-and-interactive-communication}

Die AEM Sites-Seite behält einen Verweis auf das adaptive Formular und die interaktive Kommunikation im AEM Forms-Container bei. Daher werden alle Konfigurationen und Eigenschaften wie das Design, die Stile und die Sendeaktion, die im ursprünglichen adaptiven Formular konfiguriert sind, sowie die interaktive Kommunikation im eingebetteten adaptiven Formular und in der interaktiven Kommunikation beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars und der interaktiven Kommunikation zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen oder in der interaktiven Kommunikation in den entsprechenden Editoren und ändern Sie es.
* Tippen Sie auf der Seite im Bearbeitungsmodus auf das adaptive Formular und anschließend auf **[!UICONTROL In neuem Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass Sie es bearbeiten können.

>[!NOTE]
>
>Die Änderungen, die im ursprünglichen adaptiven Formular oder in der interaktiven Kommunikation vorgenommen wurden, werden automatisch im eingebetteten Formular übernommen. Veröffentlichen Sie das adaptive Formular, die interaktive Kommunikation oder die Site-Seite jedoch erneut, um die Änderungen auf der veröffentlichten Seite widerzuspiegeln.

## Aspekte und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM Sites-Seiten einbetten:

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den Registerkarten &quot;Entwürfe&quot;und &quot;Gesendete Forms&quot;im Formularportal sichtbar.
* Die im Originalformular konfigurierte Übermittlungsaktion wird im eingebetteten Formular beibehalten.
* Erlebnis-Targeting und im Originalformular konfigurierte A/B-Tests funktionieren im eingebetteten Formular nicht. Sie können jedoch Erlebnis-Targeting auf der Siteseite verwenden, um verschiedene Formulare basierend auf Benutzerprofilen darzustellen.
* Wenn Sie für das Originalformular Adobe Analytics konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
