---
title: Formularvorschau
seo-title: Formularvorschau
description: Sie können Ihre Formulare in der Vorschau anzeigen, bevor Sie sie veröffentlichen oder aktivieren, um sicherzustellen, dass sie den Erwartungen entsprechen. Vorschauoptionen variieren abhängig von den unterstützten Formulartypen.
seo-description: Sie können Ihre Formulare in der Vorschau anzeigen, bevor Sie sie veröffentlichen oder aktivieren, um sicherzustellen, dass sie den Erwartungen entsprechen. Vorschauoptionen variieren abhängig von den unterstützten Formulartypen.
uuid: 9ec359ea-f518-441c-9c3d-e3c1ea07a532
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 377d804d-4a75-4c93-8125-d2660cf56418
feature: Adaptive Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 89%

---


# Formularvorschau {#previewing-a-form}

## Überblick {#overview}

In AEM Forms können Sie die Formulare und Dokumente im Repository in der Vorschau anzeigen. So wissen Sie genau, wie die Formulare aussehen und sich verhalten, wenn sie an die Endbenutzer ausgegeben werden.

Wenn Sie Formulare in der Vorschau anzeigen, werden diese in der interaktiven Oberfläche wiedergegeben und der Benutzer kann die Formulare mit Daten füllen. Wenn Sie Dokumente in der Vorschau anzeigen, werden diese im nicht interaktiven Modus wiedergegeben und der Benutzer kann das Dokument nur anzeigen. Bei Formularen ist die zusätzliche Option „Custom Preview“ (Benutzerdefinierte Vorschau) verfügbar. Mit dieser Option können Sie das Formular mit Daten aus einer XML-Datei in der Vorschau anzeigen. Die Daten füllen einige oder alle Felder des Formulars, das in der Vorschau angezeigt wird.

In der folgenden Tabelle sind die Vorschauoptionen aufgeführt, für unterschiedliche Typen unterstützter Formulare verfügbar sind:

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
   <td>PDF-Vorschau, PDF-Vorschau mit Daten HTML-Vorschau, HTML-Vorschau mit Daten<br />  </td>
  </tr>
 </tbody>
</table>

## Formularvorschau {#previewing-a-form-1}

1. Wählen Sie ein Asset aus, das Sie Vorschauen vornehmen möchten, und klicken Sie in der Aktionsleiste auf Vorschau ![aem6forms_Vorschau](assets/aem6forms_preview.png).

   >[!NOTE]
   >
   >Um ein Asset auszuwählen, wechseln Sie aus der Standardkartenansicht in die Listenansicht. Klicken Sie auf ![aem6forms_viewlist](assets/aem6forms_viewlist.png) oder ![aem6forms_viewcard](assets/aem6forms_viewcard.png), um die Ansichten zu wechseln.

1. Wenn Sie auf „Vorschau“ klicken, werden die möglichen Vorschauoptionen für den ausgewählten Asset-Typ aufgelistet. Klicken Sie auf die gewünschte Option, um das ausgewählte Asset in einer neuen Registerkarte anzuzeigen.

   Ihre Optionen sind:

   * Vorschau als HTML
   * Vorschau mit Daten
   * Vorschau als PDF (verfügbar für Formularvorlagen)

## Vorschau mit Daten {#preview-with-data}

Wenn Sie **Vorschau mit Daten** auswählen, können Sie das Formular mit echten eingegebenen Daten sehen. Bei der Option „Vorschau mit Daten“ können Sie eine XML hochladen, die Beispielbenutzerdaten enthält. Die Beispielbenutzerdaten werden verwendet, um das Vorschauformular in dem ausgewählten Format auszufüllen.

1. Wählen Sie ein Asset aus, klicken Sie auf Vorschau ![aem6forms_Vorschau](assets/aem6forms_preview.png) und wählen Sie **Vorschau mit Daten**.
1. Geben Sie im Dialogfeld „Preview Form“ (Formularvorschau) FormData als XML-Datei an. Klicken Sie auf „Vorschau“, um das Formular mit den zusammengeführten Daten aus der XML anzuzeigen.

