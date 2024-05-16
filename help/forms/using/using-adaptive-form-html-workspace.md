---
title: Verwenden eines adaptiven Formulars in HTML Workspace
description: Erfahren Sie, wie Sie ein adaptives Formular in HTML Workspace verwenden, mit dem Mitarbeiterinnen und Mitarbeiter im Außendienst auf ihren Geräten auf das Formular zugreifen können.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
exl-id: 15b9ae98-059f-4bf7-bfdd-9cfeb8eb30a4
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: ht
source-wordcount: '690'
ht-degree: 100%

---

# Verwenden eines adaptiven Formulars in HTML Workspace{#using-an-adaptive-form-in-html-workspace}

Mit AEM Forms on JEE können adaptive Formulare in HTML Workspace verwendet werden.

Da während des Prozess-Designs ein XDP ausgewählt werden kann, wurde die Funktion zum Durchsuchen eines bestehenden AEM-Repositorys für adaptive Formulare hinzugefügt. Mit der Funktion kann der Prozess-Designer ein adaptives Formular sowohl in „Ausgangspunkt“ als auch in „Aufgabe“ konfigurieren.

## Erlebnis des Prozess-Designs {#process-design-experience}

Führen Sie Folgendes aus, um die Verwendung adaptiver Formulare im Prozess-Design zu ermöglichen:

* Unter „Aufgabe und Startpunkt zuweisen“ können Sie das CRX-Repository nach einem adaptiven Formular-Asset durchsuchen, wenn Sie einer Aufgabe ein Formular-Asset zuweisen.
* Im Eigenschaftenblatt „Aufgabe zuweisen/Startpunkt-Workbench“ können Sie die Symbolleiste der obersten Ebene bzw. die globale Symbolleiste eines adaptiven Formulars ausblenden.
* Sie können neue Aktionsprofile für die Aktionen „Rendern“ und „Absenden“ in adaptiven Formularen verwenden.

### Exportieren und Importieren von LiveCycle-Anwendungen {#livecycle-application-export-and-import}

Da sich adaptive Formulare im AEM-Repository befinden, enthält der LiveCycle-Anwendungsexport nur die Verweise für verwendete adaptive Formulare. Deshalb umfasst der Export und Import des LiveCycle-Programms zwei Schritte. Die LiveCycle-Anwendung umfasst die Prozessdefinitionen usw. Ein separates Paket mit adaptiven Formularen wird als ZIP-Datei aus AEM exportiert. Beim Importieren wird die LiveCycle-Anwendung über Workbench importiert und adaptive Formulare über AEM.

## Anwendererlebnis eines adaptiven Formulars in HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace bietet zusätzlich zu den Steuerelementen, die für mobile Formulare verfügbar sind, einige Steuerelemente, die für adaptive Formulare spezifisch sind. Sie können Anhänge hinzufügen, speichern, signieren, absenden und durch die adaptiven Formulare in HTML Workspace navigieren, wenn Sie eine Aufgabe oder einen Startpunkt öffnen. Im Folgenden sind die Einzelheiten aufgeführt:

1. Verwenden Sie zum Anhängen von Dateien Aufgabenanhänge, genau wie in Mobile-Formularen. Schaltflächen für Dateianhänge des adaptiven Formulars werden ausgeblendet.

1. Klicken Sie zum Speichern des adaptiven Formulars auf **Speichern**, genau wie in Mobile Forms. Schaltflächen zum Speichern des adaptiven Formulars werden ausgeblendet.

1. Verwenden Sie zum Senden eines adaptiven Formulars die Schaltfläche **Senden** oder die verfügbaren Route-Aktionen, wie in Mobile Forms. Schaltflächen zum Senden des adaptiven Formulars werden ausgeblendet.

1. **Sichtbarkeit der globalen Symbolleiste des adaptiven Formulars**: Wenn im Prozess-Designer die globale Symbolleiste bzw. die Symbolleiste der obersten Ebene ausgeblendet wird, werden die Symbolleiste und die Schaltflächen nicht in adaptiven Formularen angezeigt.

1. **Navigationssteuerelemente des Arbeitsbereichs für adaptive Formulare**: Die Schaltflächen „Weiter“ und „Zurück“ zusammen mit den Schaltflächen „Speichern“, „Senden“ und „Route-Aktion“ sind für ein adaptives Formular in HTML Workspace verfügbar. Klicken Sie auf die Schaltflächen „Weiter“/„Zurück“, um zwischen den Bereichen der adaptiven Formulare in HTML Workspace zu navigieren. Die Schaltflächen „Weiter/Zurück“ ermöglichen die Navigation, ähnlich der Navigationssteuerelemente in der Ansicht „Mobil“ der adaptiven Formulare.

1. **eSign-Services und die Übersichtskomponente des adaptiven Formulars**: Die Übersichtskomponente ist in HTML Workspace nicht funktional. Mit anderen Worten: Wenn ein adaptives Formular über eine Zusammenfassungskomponente verfügt, ist diese in Workspace nicht sichtbar. Anstelle von „Automatisch absenden“ in der E-Sign-Komponente klicken Benutzende von Workspace auf „Absenden“ oder auf eine Weiterleitungsaktion in HTML Workspace. Nachdem ein Dokument signiert wurde, ist es als flaches, signiertes Dokument sichtbar. Klicken Sie auf **Absenden** oder auf eine Route-Aktion, damit Sie die Aufgabe oder den Startpunkt schließen bzw. abschließen können.\
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
