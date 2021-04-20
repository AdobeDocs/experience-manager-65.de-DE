---
title: Betten Sie ein adaptives Formular oder eine interaktive Kommunikation in die AEM-Sites-Seite ein.
seo-title: Betten Sie ein adaptives Formular oder eine interaktive Kommunikation in die AEM-Sites-Seite ein.
description: Sie können adaptive Formulare in den AEM-Site-Seiten einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Site-Seiten zu verlassen.
seo-description: Sie können adaptive Formulare in den AEM-Site-Seiten einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Site-Seiten zu verlassen.
uuid: 59b49e2f-6d95-42e5-b31e-fc40936c42d2
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author, interactive-communications
discoiquuid: 43362643-69cd-4006-a613-f998c79eeddc
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 75%

---


# Betten Sie ein adaptives Formular oder eine interaktive Kommunikation in die AEM-Sites-Seite ein.{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

## Überblick {#overview}

Mit AEM Forms können Formularentwickler nahtlos adaptive Formulare in eine AEM-Site-Seite oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und versenden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular oder der interaktiven Kommunkation zu interagieren.

Informationen zum Einbetten eines adaptiven Formulars in eine externe Webseite finden Sie unter [Adaptives Formular in externe Webseite einbetten](/help/forms/using/embed-adaptive-form-external-web-page.md).

Auf der Seite &quot;AEM Sites&quot;können Sie ein adaptives Formular oder eine interaktive Kommunikation hinzufügen, indem Sie:

* **[AEM Forms-Container-Komponente](/help/forms/using/embed-adaptive-form-aem-sites.md#af-component)** AEM Forms bietet eine Komponente, die Sie Ihren Siteseiten hinzufügen können. Über die AEM Forms-Container-Komponente können Sie ein adaptives Formular und interaktive Kommunikation einbetten.

* **[Asset Browser](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)** Alle Formulare und interaktiven Kommunikationen, die Sie erstellen, sind unter „Assets“ verfügbar. Sie können das Formular als Asset auf Ihrer Seite per Drag&amp;Drop einfügen.

## Voraussetzungen {#prerequisites}

Um ein adaptives Formular oder eine interaktive Kommunikation in eine AEM Siteseite einzubetten, die eine bearbeitbare Vorlage verwendet, stellen Sie sicher, dass die AEM-Formularkomponente in der zugehörigen Vorlage als zulässige Komponente konfiguriert ist. Weitere Informationen finden Sie im Abschnitt **Richtlinie und Eigenschaften (Layout-Container)** unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

Falls eine Siteseite eine statische Vorlage verwendet, müssen Sie es im Absatzsystem der Seite konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](/help/sites-authoring/default-components-designmode.md).

## Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation {#af-component}

Einbetten eines adaptiven Formulars oder einer interaktiven Kommunikation mithilfe der AEM Forms-Container-Komponente:

1. Öffnen Sie im Bearbeitungsmodus die AEM-Site-Seite, in die Sie ein adaptives Formular oder interaktive Kommunikation einfügen möchten.
1. Ziehen Sie die AEM Forms-Container-Komponente aus dem Komponenten-Browser auf die Seite.

   Alternativ können Sie nach einem adaptiven Formular oder einer interaktiven Kommunikation im Assets-Browser suchen und per Drag &amp; Drop auf die Site-Seite ziehen. Dadurch wird das Formular in einen AEM Forms-Container eingebettet.

   >[!NOTE]
   >
   >Mehrere AEM Forms-Container-Komponenten auf einer Seite werden nicht unterstützt.

1. Tippen Sie auf der Siteseite auf die eingebettete AEM Forms-Container-Komponente und dann auf ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Das Dialogfeld **[!UICONTROL AEM Forms Container bearbeiten]** wird geöffnet.
1. Geben Sie im Dialogfeld „AEM Forms-Container“ Folgendes an.

   * **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets. Die Optionen sind „Adaptives Formular“ und „Interaktive Kommunikation“
   * **Asset-Pfad**: Navigieren Sie zum einzubettenden adaptiven Formular oder zur einzubettenden interaktiven Kommunikation und wählen Sie sie aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
   * (Nur adaptives Formular) **Post-Übermittlung**: Wählen Sie die Aktion aus, die beim Senden des Formulars Trigger werden soll. Sie können auswählen, dass eine Meldung oder Seite mit einer Danksagung angezeigt wird.

      * **Danksagung**: Schreiben Sie eine Nachricht mit dem Rich-Text-Editor, um sie beim Senden des Formulars anzuzeigen. Diese Option ist nur verfügbar, wenn Sie eine Dankesnachricht anzeigen möchten.
      * **Danksagungsseite**: Durchsuchen Sie die Seite, die beim Senden des Formulars angezeigt werden soll, und wählen Sie sie aus. Diese Option steht nur zur Verfügung, wenn Sie die Anzeige einer Dankesseite auswählen.
      * **Seite beim Senden aktualisieren**: Aktivieren Sie diese Option, um die Seite mit dem eingebetteten adaptiven Formular zu aktualisieren und die Dankesseite anzuzeigen. Andernfalls ersetzt die Dankesseite das adaptive Formular im AEM Forms-Container, ohne die Seite zu aktualisieren. Diese Option steht nur zur Verfügung, wenn Sie die Anzeige einer Dankesseite auswählen.
   * **Thema**: Wählen Sie ein Thema, das die Formatierung der Komponenten in Ihrem adaptiven Formular oder interaktiver Kommunikation definiert. Die Formatierung enthält Erscheinungsbildeigenschaften wie Schriftart, Hintergrundfarbe, Größe und Ausrichtung ein.
   * **Höhe:** Geben Sie die Höhe des Containers an. Lassen Sie sie leer, um die Größe des Containers automatisch anzupassen.
   * **Css-Kundenbibliothek**: Geben Sie den Pfad zu einer CSS-Kundenbibliothek an.


1. Speichern Sie die Einstellungen. Das adaptive Formular oder die interaktive Kommunikation sind jetzt in die Seite eingebettet.

## Veröffentlichen von eingebetteten adaptiven Formularen und interaktiver Kommunikation {#publishing-embedded-adaptive-form-and-interactive-communication}

Betrachten wir die folgenden Szenarien für die Veröffentlichung eines eingebetteten Assets (eingebettetes Formular oder interaktive Kommunikation) in der AEM-Site-Seite:

* Wenn Sie die AEM-Siteseite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular oder interaktive Kommunikation enthält, veröffentlichen Sie die Siteseite und das eingebettete Formular oder Dokument.
* Wenn Sie nur das eingebettete adaptive Formular oder die interaktive Kommunikation auf einer veröffentlichten Siteseite geändert haben, veröffentlichen Sie das ursprüngliche Asset und die Änderungen werden auf der veröffentlichten Siteseite übernommen. Die veröffentliche Site-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Site-Seite und das eingebettete adaptive Formular oder die interaktive Kommunikation geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern des eingebetteten adaptiven Formulars und der interaktiven Kommunikation {#modifying-embedded-adaptive-form-and-interactive-communication}

Die AEM-Sites-Seite behält einen Verweis auf das adaptive Formular und die interaktive Kommunikation im AEM Forms-Container bei. Deshalb werden alle Konfigurationen und Eigenschaften, beispielsweise Design, Stile und die Sendeaktion, die im adaptiven Originalformular und der interaktiven Kommunikation konfiguriert wurden, im eingebetteten adaptiven Formular und der interaktiven Kommunikation beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen oder interaktiver Kommunikation in entsprechenden Editoren und modifizieren Sie diese.
* Tippen Sie im Bearbeitungsmodus auf das adaptive Formular oder die interaktive Kommunikation von der Seite der Site und dann auf **[!UICONTROL In einem neuen Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass sie es bearbeiten können.

>[!NOTE]
>
>Die Änderungen im adaptiven Originalformular oder in der interaktiven Kommunikation werden automatisch vom eingebetteten Formular übernommen. Allerdings müssen Sie das adaptive Formular oder die Site-Seite neu veröffentlichen, damit die Änderungen in der veröffentlichten Seite angezeigt werden.

## Überlegungen und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM-Siteseiten einbetten:

* Die Kopf- und Fußzeile im Originalformular werden im eingebetteten Formular nicht übernommen.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf der entsprechenden Registerkarte im Forms Portal sichtbar.
* Die im Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten Formular nicht. Sie können jedoch Erlebnis-Targeting auf der Siteseite verwenden, um verschiedene Formular je nach Benutzerprofil darzustellen.
* Wenn Sie Adobe Analytics für das Originalformular konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

