---
title: Verwenden eines adaptiven Formulars in HTML Workspace
seo-title: Verwenden eines adaptiven Formulars in HTML Workspace
description: Verwenden eines adaptiven Formulars in HTML Workspace
seo-description: Verwenden eines adaptiven Formulars in HTML Workspace
uuid: 473d5daf-a3ed-449f-9136-585755b59922
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
discoiquuid: 2b6875cd-2ee7-4aa8-90c7-d33583dc2f0e
docset: aem65
exl-id: 15b9ae98-059f-4bf7-bfdd-9cfeb8eb30a4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 70%

---

# Verwenden eines adaptiven Formulars in HTML Workspace{#using-an-adaptive-form-in-html-workspace}

AEM Forms on JEE bietet die Möglichkeit, ein adaptives Formular in HTML Workspace zu verwenden.

Da während des Prozessentwurfs eine XDP ausgewählt werden kann, wurde die Möglichkeit hinzugefügt, ein vorhandenes adaptives Formular AEM Repository zu durchsuchen. Die Funktion gibt dem Prozessentwickler die Möglichkeit, ein adaptives Formular sowohl im Ausgangspunkt als auch in der Aufgabe zu konfigurieren.

## Prozessdesign {#process-design-experience}

Führen Sie folgende Schritte durch, damit adaptive Formulare im Prozessdesign verwendet werden können:

* Sie können in „Aufgabe zuweisen“ und in „Ausgangspunkt“ zum adaptiven Formularelement im CRX-Repository navigieren, wenn Sie ein Formularelement einer Aufgabe zuweisen.
* Sie können im Eigenschaftenblatt „Aufgabe zuweisen/Ausgangspunkt“ die Symbolleiste der obersten Ebene/die globale Symbolleiste eines adaptiven Formulars ausblenden.
* Sie können neue Aktionsprofile für Wiedergabe- und Sendeaktionen in adaptiven Formularen verwenden.

### LiveCycle-Anwendung importieren und exportieren {#livecycle-application-export-and-import}

Da adaptive Formulare im AEM-Repository vorhanden sind, enthält der Export der LiveCycle-Anwendung nur die Verweise für die verwendeten adaptiven Formulare. Daher erfolgt der Export und Import der LiveCycle-Anwendung in zwei Schritten. Die LiveCycle-Anwendung enthält Prozessdefinitionen usw. Ein separates Paket, das adaptive Formulare enthält, wird als ZIP-Datei aus AEM exportiert. Beim Importieren wird die LiveCycle-Anwendung über Workbench importiert und adaptive Formulare werden über AEM importiert.

## Benutzerfreundlichkeit adaptiver Formulare in HTML Workspace  {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace bietet adaptive formularspezifische Steuerelemente zusätzlich zu den Steuerelementen, die für Mobile Forms verfügbar sind. Ein Benutzer kann Anlagen hinzufügen, die adaptiven Formulare im HTML Workspace speichern, signieren, senden und navigieren, wenn der Benutzer eine Aufgabe oder einen Ausgangspunkt öffnet. Spezifikationen:

1. Verwenden Sie zum Anhängen von Dateien Aufgabenanhänge, genau wie in Mobile Forms. Schaltflächen für Dateianhänge des adaptiven Formulars werden ausgeblendet.

1. Klicken Sie zum Speichern des adaptiven Formulars auf **Speichern**, genau wie in Mobile Forms. Schaltflächen zum Speichern des adaptiven Formulars werden ausgeblendet.

1. Verwenden Sie zum Senden eines adaptiven Formulars die Schaltfläche **Senden** oder die verfügbaren Route-Aktionen, wie in Mobile Forms. Schaltflächen zum Senden des adaptiven Formulars werden ausgeblendet.

1. **Sichtbarkeit der globalen Symbolleiste des adaptiven Formulars**: Wenn Prozessentwickler die globale Symbolleiste/Symbolleiste der obersten Ebene ausblendet, werden die Symbolleiste und die Schaltflächen nicht in adaptiven Formularen angezeigt.

1. **Workspace-Navigationssteuerelemente für adaptive Forms**: Die Schaltflächen &quot;Weiter/Zurück&quot;stehen zusammen mit den Schaltflächen &quot;Speichern&quot;, &quot;Senden&quot;und &quot;Route-Aktion&quot;für ein adaptives Formular in HTML Workspace zur Verfügung. Klicken Sie auf die Schaltflächen „Weiter/Zurück“, um zwischen den Bereichen der adaptiven Formulare in HTML Workspace zu navigieren. Die Schaltflächen „Weiter/Zurück“ ermöglichen die Navigation, ähnlich der Navigationssteuerelemente in der Ansicht „Mobil“ der adaptiven Formulare.

1. **eSign-Dienste und die Übersichtskomponente des adaptiven Formulars**: Die Zusammenfassungskomponente ist in HTML Workspace nicht funktionsfähig. Das heißt, wenn ein adaptives Formular eine Übersichtkomponente beinhaltet, ist sie im Arbeitsbereich nicht sichtbar. Klicken Sie in der Esign-Komponente anstelle von „Automatisch senden“ auf „Senden“ oder eine Route-Aktion in HTML Workspace. Nach der Unterzeichnung des Dokuments ist es als reduziertes signiertes Dokument sichtbar. Klicken Sie auf **Senden** oder eine Route-Aktion, um die Aufgabe oder den Ausgangspunkt zu schließen/abzuschließen.\
   Das signierte Dokument wird vom eSign-Dienste-Server erfasst und die Daten-XML-Datei wird im nächsten Schritt weitergeleitet.

## Schritte zum Verwenden adaptiver Formulare im Prozessdesign {#steps-to-use-adaptive-forms-in-process-design}

1. Öffnen Sie Adobe Experience Manager Forms Workbench.

1. Gehen Sie zu **Datei > Neu > Anwendung** oder verwenden Sie die vorhandene Anwendung, um eine Anwendung zu erstellen.

   ![Neue Anwendung erstellen](assets/create_new_appl.png)

   Neue Anwendung erstellen

1. Erstellen Sie einen Prozess oder verwenden Sie einen vorhandenen Prozess in der Anwendung.

   ![Neuen Prozess erstellen](assets/create_new_process.png)

   Neuen Prozess erstellen

1. Erstellen Sie einen Startpunkt oder eine Aufgabe zuweisen und doppelklicken Sie darauf.
1. Wählen Sie im Abschnitt **[!UICONTROL Präsentation und Daten]** **[!UICONTROL Ein CRX-Element verwenden]** und klicken Sie vor den Elementen auf die Ellipsen.

   ![Use a CRX asset](assets/use_crx_asset.png)

   Use a CRX asset

1. Wählen Sie das adaptive Formular aus, das über die Benutzeroberfläche &quot;Assets verwalten&quot;erstellt wurde, und klicken Sie auf **[!UICONTROL OK]**.

   ![Ein adaptives Formular auswählen](assets/selecting_form.png)

   Ein adaptives Formular auswählen

   >[!NOTE]
   >
   >Weitere Informationen zur Erstellung eines adaptiven Formulars, finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md).
   >
   >
   >Weitere Informationen zum Erstellen eines Prozesses finden Sie unter [Erstellen und Verwalten von Prozessen](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/WS92d06802c76abadb-1cc35bda128261a20dd-7ff7.2.html).
