---
title: Formularvorschau
description: Sie können eine Vorschau Ihrer Formulare anzeigen, bevor Sie sie veröffentlichen oder aktivieren, um sicherzustellen, dass sie den Erwartungen entsprechen. Die Vorschauoptionen können je nach unterstützten Formulartypen variieren.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms
exl-id: aed5703e-4fe6-4839-9657-c660ac48521e
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 42%

---

# Formularvorschau {#previewing-a-form}

<span class="preview"> Adobe empfiehlt die Verwendung der modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung für das [Erstellen neuer adaptiver Formulare](/help/forms/using/create-an-adaptive-form-core-components.md) oder das [Hinzufügen von adaptiven Formularen zu AEM Sites-Seiten](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Benutzererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen von adaptiven Formularen mithilfe von Foundation-Komponenten beschrieben. </span>

## Übersicht {#overview}

In AEM Forms können Sie die Formulare und Dokumente im Repository in der Vorschau anzeigen. Die Vorschau zeigt genau, wie die Formulare aussehen und sich verhalten, wenn sie für die Endbenutzer freigegeben werden.

Bei der Vorschau von Formularen werden diese in der interaktiven Benutzeroberfläche wiedergegeben und der Benutzer kann die Formulare mit Daten ausfüllen. Bei der Vorschau von Dokumenten werden diese im nicht interaktiven Modus gerendert und der Benutzer kann nur das Dokument anzeigen. Für Formulare ist eine zusätzliche Option der benutzerdefinierten Vorschau verfügbar. Mit dieser Option können Sie eine Vorschau des Formulars mit Daten aus einer XML-Datei anzeigen. Die Daten füllen einige oder alle Felder des Formulars aus, das in der Vorschau angezeigt wird.

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
   <td>adaptives Formular</td>
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

1. Durch Klicken auf Vorschau werden die möglichen Vorschauoptionen aufgelistet, die für den ausgewählten Asset-Typ gelten. Klicken Sie auf die gewünschte Option, um das ausgewählte Asset in einer neuen Registerkarte anzuzeigen.

   Ihre Optionen sind:

   * Anzeigen als HTML-Vorschau
   * Vorschau mit Daten
   * Vorschau als PDF (verfügbar für Formularvorlagen)

## Vorschau mit Daten {#preview-with-data}

Wenn Sie **Vorschau mit Daten** können Sie sehen, wie das Formular mit echten eingegebenen Daten aussieht. Mit der Option Vorschau mit Daten können Sie eine XML-Datei hochladen, die Beispielbenutzerdaten enthält. Die Beispielbenutzerdaten werden zum Ausfüllen des Vorschauformulars in dem von Ihnen ausgewählten Format verwendet.

1. Wählen Sie ein Asset aus, klicken Sie auf „Vorschau“ ![aem6forms_preview](assets/aem6forms_preview.png) und wählen Sie **Vorschau mit Daten** aus.
1. Geben Sie im Dialogfeld &quot;Formularvorschau&quot;FormData als XML-Datei an. Klicken Sie auf Vorschau , um das Formular mit den zusammengeführten Daten aus XML wiederzugeben.
