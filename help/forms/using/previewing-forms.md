---
title: Formularvorschau
description: Sie können Ihre Formulare in der Vorschau anzeigen, bevor Sie sie veröffentlichen oder aktivieren, um sicherzustellen, dass sie den Erwartungen entsprechen.  Die Vorschauoptionen können abhängig von den unterstützten Formulartypen variieren.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
feature: Adaptive Forms,Foundation Components
exl-id: aed5703e-4fe6-4839-9657-c660ac48521e
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '406'
ht-degree: 100%

---

# Formularvorschau {#previewing-a-form}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

## Überblick {#overview}

In AEM Forms können Sie die Formulare und Dokumente im Repository in der Vorschau anzeigen. So wissen Sie genau, wie die Formulare aussehen und sich verhalten, wenn sie an die Endbenutzenden ausgegeben werden.

Bei der Vorschau von Formularen werden diese in der interaktiven Benutzeroberfläche gerendert und die Benutzenden können die Formulare mit Daten ausfüllen. Bei der Vorschau von Dokumenten werden diese im nicht interaktiven Modus gerendert und die Benutzenden können nur das Dokument anzeigen. Für Formulare ist eine zusätzliche Option der benutzerdefinierten Vorschau verfügbar. Mit dieser Option können Sie eine Vorschau des Formulars mit Daten aus einer XML-Datei anzeigen. Die Daten füllen dabei einige oder alle Felder des Formulars aus, das in der Vorschau angezeigt wird.

In der folgenden Tabelle sind die Vorschauoptionen aufgeführt, die für verschiedene Typen unterstützter Formulare verfügbar sind:

<table>
 <tbody>
  <tr>
   <td><strong>Asset-Typ</strong><br /> </td>
   <td><strong>Verfügbare Vorschauoptionen</strong><br /> </td>
  </tr>
  <tr>
   <td>Dokument</td>
   <td>PDF-Vorschau</td>
  </tr>
  <tr>
   <td>PDF-Formular</td>
   <td>PDF-Vorschau und Vorschau mit Daten<br /> </td>
  </tr>
  <tr>
   <td>Adaptives Formular</td>
   <td>HTML-Vorschau und HTML-Vorschau mit Daten</td>
  </tr>
  <tr>
   <td>Formularvorlage</td>
   <td>PDF-Vorschau, PDF-Vorschau mit Daten HTML-Vorschau, HTML-Vorschau mit Daten<br /> </td>
  </tr>
 </tbody>
</table>

## Formularvorschau {#previewing-a-form-1}

1. Wählen Sie ein Asset aus, das Sie in der Vorschau anzeigen möchten, und klicken Sie in der Symbolleiste „Aktionen“ auf „Vorschau“ ![aem6forms_preview](assets/aem6forms_preview.png).

   >[!NOTE]
   >
   >Um ein Asset auszuwählen, wechseln Sie aus der standardmäßigen Kartenansicht in die Listenansicht. Klicken Sie auf ![aem6forms_viewlist](assets/aem6forms_viewlist.png) oder ![aem6forms_viewcard](assets/aem6forms_viewcard.png), um die Ansichten zu wechseln.

1. Durch das Klicken auf „Vorschau“ werden die möglichen Vorschauoptionen aufgelistet, die für den ausgewählten Asset-Typ anwendbar sind. Klicken Sie auf die gewünschte Option, um das ausgewählte Asset in einer neuen Registerkarte zu rendern.

   Ihre Optionen sind:

   * Anzeigen als HTML-Vorschau
   * Vorschau mit Daten
   * Vorschau als PDF (verfügbar für Formularvorlagen)

## Vorschau mit Daten {#preview-with-data}

Wenn Sie **Vorschau mit Daten** auswählen, können Sie sehen, wie das Formular mit echten eingegebenen Daten aussieht.  Mit der Option „Vorschau mit Daten“ können Sie eine XML-Datei hochladen, die Beispielbenutzerdaten enthält. Die Beispielbenutzerdaten werden zum Ausfüllen des Vorschauformulars in dem von Ihnen ausgewählten Format verwendet.

1. Wählen Sie ein Asset aus, klicken Sie auf „Vorschau“ ![aem6forms_preview](assets/aem6forms_preview.png) und wählen Sie **Vorschau mit Daten** aus.
1. Geben Sie im Dialogfeld „Formularvorschau“ FormData als XML-Datei an. Klicken Sie auf „Vorschau“, um das Formular mit den zusammengeführten Daten aus der XML-Datei zu rendern.
