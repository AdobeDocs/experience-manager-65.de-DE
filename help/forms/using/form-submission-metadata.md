---
title: Hinzufügen von Informationen aus Benutzerdaten zu Formularübermittlungsmetadaten
description: Erfahren Sie, wie Sie den Metadaten eines übermittelten Formulars mit vom Benutzer bereitgestellten Daten Informationen hinzufügen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms, Foundation Components
discoiquuid: 2c971da0-5bd5-40d1-820d-4efc2a44b49d
docset: aem65
exl-id: 5ca850e3-30f0-4384-b615-356dc3c2ad0d
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 100%

---

# Hinzufügen von Informationen aus Benutzerdaten zu Formularübermittlungsmetadaten{#adding-information-from-user-data-to-form-submission-metadata}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>

Sie können Werte verwenden, die in ein Element Ihres Formulars eingegeben wurden, um Metadatenfelder eines Entwurfs oder einer Formularübermittlung zu berechnen. Mit Metadaten können Sie Inhalte auf der Grundlage von Benutzerdaten filtern. Beispiel: Ein Benutzer gibt „Hans Mustermann“ in das Namensfeld Ihres Formulars ein. Sie können diese Informationen verwenden, um Metadaten zu berechnen, die diese Übermittlung unter den Initialen „HM“ kategorisieren können.

Um die Metadatenfelder mit den vom Benutzer eingegebenen Werten zu berechnen, müssen Sie Elemente Ihres Formulars in den Metadaten hinzufügen. Wenn ein Benutzer einen Wert in diesem Element eingibt, verwendet ein Skript den Wert, um diese Informationen zu berechnen. Diese Informationen werden den Metadaten hinzugefügt. Wenn Sie ein Element als Metadatenfeld hinzufügen, stellen Sie einen Schlüssel dafür bereit. Der Schlüssel wird als Feld in den Metadaten hinzugefügt und die berechneten Informationen werden damit protokolliert.

Beispielsweise veröffentlicht eine Krankenversicherung ein Formular. In diesem Formular erfasst ein Feld das Alter der Endbenutzenden. Die Kundin bzw. der Kunde möchte alle Übermittlungen in einer bestimmten Altersgruppe überprüfen, nachdem mehrere Benutzende das Formular übermittelt haben. Statt alle Daten einzeln zu überprüfen, was mit zunehmender Anzahl an Formularen schwieriger wird, helfen dabei zusätzliche Metadaten. Die Autorin oder der Autor des Formulars kann konfigurieren, welche Eigenschaften/Daten von Endbenutzenden auf der obersten Ebene gespeichert werden, damit die Suche möglichst einfach ist. Zusätzliche Metadaten sind von Benutzenden ausgefüllte Informationen, die auf der obersten Ebene des Metadatenknotens gespeichert werden, wie der Autor bzw. die Autorin es konfiguriert hat.

Ein weiteres Beispiel ist ein Formular, das E-Mail-IDs und Telefonnummern erfasst. Wenn eine Benutzerin bzw. ein Benutzer dieses Formular anonym besucht und das Formular verlässt, kann die Autorin bzw. der Autor das Formular so konfigurieren, dass die E-Mail-Adresse und die Telefonnummer automatisch gespeichert werden. Dieses Formular wird automatisch gespeichert und die Telefonnummer und die E-Mail-Adresse werden im Metadatenknoten des Entwurfs gespeichert. Ein Anwendungsfall dieser Konfiguration ist das Lead-Management-Dashboard.

## Hinzufügen von Formularelementen zu Metadaten {#adding-form-elements-to-metadata}

Führen Sie die folgenden Schritte aus, um den Metadaten ein Element hinzuzufügen:

1. Öffnen Sie Ihr adaptives Formular im Bearbeitungsmodus.\
   Um das Formular im Bearbeitungsmodus zu öffnen, wählen Sie es in Forms Manager aus und wählen Sie **Öffnen** aus.
1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, wählen Sie ![field-level](assets/field-level.png) > **Adaptiver Formular-Container** und dann ![cmppr](assets/cmppr.png) aus.
1. Klicken Sie in der Seitenleiste auf **Metadaten**.
1. Klicken Sie im Abschnitt „Metadaten“ auf **Hinzufügen**.
1. Verwenden Sie das Feld „Wert“ auf der Registerkarte „Metadaten“, um Skripte hinzuzufügen. Die Skripte, die Sie hinzufügen, erfassen Daten aus Elementen im Formular und berechnen Werte, die an die Metadaten übergeben werden.

   Zum Beispiel wird in den Metadaten **true** protokolliert, wenn das eingegebene Alter größer als 21 ist, und **false**, wenn es kleiner als 21 ist. Sie können das folgende Skript auf der Registerkarte „Metadaten“ eingeben:

   `(agebox.value >= 21) ? true : false`

   ![Metadatenskript](assets/add-element-metadata.png)

   Skript, das auf der Registerkarte „Metadaten“ eingegeben wurde

1. Klicken Sie auf **OK**.

Nachdem eine Benutzerin bzw. ein Benutzer Daten in das als Metadatenfeld ausgewählte Element eingegeben hat, werden die berechneten Informationen in den Metadaten protokolliert. Sie können die Metadaten im Repository sehen, das Sie zum Speichern von Metadaten konfiguriert haben.

## Anzeigen der aktualisierten Formularübermittlungsmetadaten: {#seeing-updated-form-nbsp-submission-metadata}

Für das obige Beispiel werden die Metadaten im CRX-Repository gespeichert. Die Metadaten sehen wie folgt aus:

![Metadaten](assets/metadata_entry_new.png)

Wenn Sie ein Kontrollkästchenelement in die Metadaten hinzufügen, werden die ausgewählten Werte als kommagetrennter String gespeichert. Angenommen, Sie fügen Ihrem Formular ein Kontrollkästchenelement hinzu und legen als Namen `checkbox1` fest. Sie fügen den Eigenschaften der Kontrollkästchenkomponente die Elemente „Führerschein“, „Sozialversicherungsnummer“ und „Reisepass“ für die Werte 0, 1 und 2 hinzu.

![Speichern mehrerer Werte aus einem Kontrollkästchen](assets/checkbox-metadata.png)

Wählen Sie einen Container für das adaptive Formular und in den Formulareigenschaften fügen Sie einen Metadatenschlüssel `cb1` hinzu, der `checkbox1.value` speichert und dann veröffentlichen Sie das Formular. Wenn eine Kundin oder ein Kunde das Formular ausfüllt, wählt sie bzw. er die Optionen „Reisepass“ und „Sozialversicherungsnummer“ in den Kontrollkästchen aus.  Die Werte 1 und 2 werden als 1, 2 im Feld „cb1“ der Übermittlungsmetadaten gespeichert.

![Metadatenelement für mehrere Werte, ausgewählt in einem Kontrollkästchenfeld](assets/metadata-entry.png)

>[!NOTE]
>
>Das obige Beispiel ist lediglich für Schulungszwecke gedacht. Stellen Sie sicher, dass Sie nach Metadaten am richtigen Ort suchen, wie in Ihrer AEM Forms-Implementierung konfiguriert.
