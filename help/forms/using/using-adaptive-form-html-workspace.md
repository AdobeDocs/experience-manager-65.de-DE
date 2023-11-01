---
title: Verwenden eines adaptiven Formulars in HTML Workspace
description: Erfahren Sie, wie Sie ein adaptives Formular in HTML Workspace verwenden, mit dem Außendienstmitarbeiter auf ihren Geräten auf das Formular zugreifen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 15b9ae98-059f-4bf7-bfdd-9cfeb8eb30a4
source-git-commit: 000c22028259eb05a61625d43526a2e8314a1d60
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 46%

---

# Verwenden eines adaptiven Formulars in HTML Workspace{#using-an-adaptive-form-in-html-workspace}

AEM Forms on JEE bietet die Möglichkeit, ein adaptives Formular in HTML Workspace zu verwenden.

Da während des Prozess-Designs ein XDP ausgewählt werden kann, wurde die Funktion zum Durchsuchen eines bestehenden adaptiven Formular-AEM-Repository hinzugefügt. Die Funktion gibt dem Prozess-Designer die Möglichkeit, ein adaptives Formular in &quot;Ausgangspunkt&quot;und &quot;Aufgabe&quot;zu konfigurieren.

## Prozessdesign {#process-design-experience}

Führen Sie die folgenden Schritte aus, um die Verwendung adaptiver Formulare im Prozessentwurf zu ermöglichen:

* In &quot;Aufgabe zuweisen&quot;und &quot;Ausgangspunkt&quot;können Sie beim Zuweisen eines Formular-Assets zu einer Aufgabe zu einem adaptiven Formular-Asset im CRX-Repository navigieren.
* Im Eigenschaftenblatt &quot;Aufgabe zuweisen/Ausgangspunkt&quot;können Sie die Symbolleiste der obersten Ebene/die globale Symbolleiste eines adaptiven Formulars ausblenden.
* Sie können neue Aktionsprofile für Wiedergabe- und Sendeaktionen in adaptiven Formularen verwenden.

### Export und Import von LiveCycle-Anwendungen {#livecycle-application-export-and-import}

Da sich adaptive Formulare im AEM-Repository befinden, enthält der LiveCycle-Anwendungsexport nur die Verweise für verwendete adaptive Formulare. Deshalb umfasst der Export und Import des LiveCycle-Programms zwei Schritte. Die LiveCycle-Anwendung enthält Prozessdefinitionen usw. Ein separates Paket, das adaptive Formulare enthält, wird als ZIP-Datei aus AEM exportiert. Beim Importieren wird die LiveCycle-Anwendung über Workbench importiert und adaptive Formulare werden über AEM importiert.

## Anwendererlebnis des adaptiven Formulars in HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace bietet einige adaptive formularspezifische Steuerelemente zusätzlich zu den Steuerelementen, die für mobile Formulare verfügbar sind. Benutzer können in HTML Workspace Anlagen hinzufügen, speichern, signieren, senden und navigieren, wenn sie eine Aufgabe oder einen Startpunkt öffnen. Im Folgenden finden Sie die Details:

1. Verwenden Sie zum Anhängen von Dateien Aufgabenanlagen, wie es in Mobile Forms der Fall war. Schaltflächen für Dateianhänge des adaptiven Formulars werden ausgeblendet.

1. Klicken Sie zum Speichern des adaptiven Formulars auf **Speichern**, genau wie in Mobile Forms. Schaltflächen zum Speichern des adaptiven Formulars werden ausgeblendet.

1. Verwenden Sie zum Senden eines adaptiven Formulars die Schaltfläche **Senden** oder die verfügbaren Route-Aktionen, wie in Mobile Forms. Schaltflächen zum Senden des adaptiven Formulars werden ausgeblendet.

1. **Sichtbarkeit der globalen Symbolleiste des adaptiven Formulars**: Wenn Process Designer die globale Symbolleiste/Symbolleiste der obersten Ebene ausblendet, werden die Symbolleiste und die Schaltflächen nicht in adaptiven Formularen angezeigt.

1. **Navigationssteuerelemente des Arbeitsbereichs für adaptive Formulare**: Die Schaltflächen „Weiter“/„Zurück“ zusammen mit den Schaltflächen „Speichern“, „Senden“ und „Route-Aktion“ sind für ein adaptives Formular in HTML Workspace verfügbar. Klicken Sie auf die Schaltflächen Weiter/Zurück , damit Sie in Bedienfeldern adaptiver Formulare in HTML Workspace navigieren können. Die Schaltflächen „Weiter/Zurück“ ermöglichen die Navigation, ähnlich der Navigationssteuerelemente in der Ansicht „Mobil“ der adaptiven Formulare.

1. **eSign-Services und die Übersichtskomponente des adaptiven Formulars**: Die Übersichtskomponente ist in HTML Workspace nicht funktional. Anders ausgedrückt: Wenn ein adaptives Formular über eine Zusammenfassungskomponente verfügt, ist es im Arbeitsbereich nicht sichtbar. Anstelle des automatischen Sendevorgangs in der E-Signaturkomponente klickt der Workspace-Benutzer auf die Übermittlungs- oder Routenaktion in HTML Workspace. Nachdem ein Dokument signiert wurde, ist es als reduziertes signiertes Dokument sichtbar. Klicks **Einsenden** oder einer Route-Aktion, damit Sie die Aufgabe oder den Startpunkt schließen/abschließen können.\
   Das signierte Dokument wird vom eSign-Dienste-Server erfasst und die Daten-XML-Datei wird im nächsten Schritt weitergeleitet.

## Schritte zum Verwenden adaptiver Formulare im Prozessdesign {#steps-to-use-adaptive-forms-in-process-design}

1. Öffnen Sie Adobe Experience Manager Forms Workbench.

1. Wählen Sie **Datei > Neu > Anwendung** ais oder verwenden Sie das bestehende Programm, um ein Programm zu erstellen.

   ![Neue Anwendung erstellen](assets/create_new_appl.png)

   Anwendung erstellen

1. Erstellen Sie einen Prozess oder verwenden Sie einen vorhandenen Prozess im Programm.

   ![Neuen Prozess erstellen](assets/create_new_process.png)

   Prozess erstellen

1. Erstellen Sie einen Ausgangspunkt oder einen Vorgang „Aufgabe zuweisen“ und doppelklicken Sie darauf.
1. Wählen Sie im Abschnitt **[!UICONTROL Präsentation und Daten]** **[!UICONTROL Ein CRX-Element verwenden]** und klicken Sie vor den Elementen auf die Ellipsen.

   ![Use a CRX asset](assets/use_crx_asset.png)

   Use a CRX asset

1. Wählen Sie das adaptive Formular aus, das durch Benutzeroberfläche „Elemente verwalten“ erstellt wurde, und klicken Sie auf **[!UICONTROL OK]**.

   ![Ein adaptives Formular auswählen](assets/selecting_form.png)

   Auswählen eines adaptiven Formulars

   >[!NOTE]
   >
   >Weitere Informationen zum Erstellen eines adaptiven Formulars finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md).
   >
   >
   >Weitere Informationen zur Erstellung eines Prozesses finden Sie unter [Erstellen und Verwalten von Prozessen](https://help.adobe.com/de_DE/AEMForms/6.1/WorkbenchHelp/WS92d06802c76abadb-1cc35bda128261a20dd-7ff7.2.html).
