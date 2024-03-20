---
title: Anwenden elektronischer Signaturen auf ein Formular mithilfe der Freihandsignatur
description: Erfahren Sie, wie Sie AEM Adaptive Forms mithilfe der Freihandsignatur signieren. Sie können die Freihandsignatur und den Unterschriftsschritt verwenden, um die Signatur auf einem Formular zu zeichnen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 096f61b0-59f4-4699-9093-8fb1ed81fded
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 81%

---

# Anwenden elektronischer Signaturen auf ein Formular mithilfe der Freihandsignatur{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

<span class="preview"> Adobe empfiehlt, die modernen und erweiterbaren [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zur Datenerfassung zu verwenden, um [neue adaptive Formulare zu erstellen](/help/forms/using/create-an-adaptive-form-core-components.md) oder [adaptive Formulare zu AEM Sites-Seiten hinzuzufügen](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Formulare mithilfe von Foundation-Komponenten beschrieben. </span>


| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-components-to-an-adaptive-form/signing-forms-using-scribble.html) |
| AEM 6.5 | Dieser Artikel |


Sie können die Komponente **Freihandsignatur** und die Komponente **Signaturschritt** verwenden, um eine Signatur in ein adaptives Formular zu zeichnen. Die Signaturschritt-Komponente zeigt eine PDF-Version des adaptiven Formulars an. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare, um die Signaturschritt-Komponente zu verwenden.

![Dialogfeld für Freihandsignatur](/help/forms/using/assets/scribble-signature.png)

## Verfügbare Optionen im Signaturfenster

* **A:** Klicken Sie auf das **Pinselsymbol**, um Ihre Signatur auf der Arbeitsfläche zu zeichnen.
* **B:** Klicken Sie auf das Symbol **Löschen**, um die Signatur auf der Arbeitsfläche zu löschen.
* **C:** Klicken Sie auf das Symbol **Geolocation**, um die Geolocation zusammen mit der Signatur hinzuzufügen.
* **D:** Klicken Sie auf das **Tastatursymbol**, um Ihren Namen auf der Arbeitsfläche einzugeben.

Nachdem Sie die Option Fertig ausgewählt haben![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) im Scribble-Signaturfenster angezeigt, können Sie die Signatur nicht bearbeiten. Wenn Sie die Signatur bearbeiten möchten, müssen Sie die aktuelle Signatur ignorieren und mit der obigen Option „Pinsel“/„Tastatur“ erneut signieren.

Sie können die **Konfigurieren** ![konfigurieren](assets/configure.png) -Symbol, um das Seitenverhältnis der Arbeitsfläche für Scribble-Signaturen festzulegen.
* Wenn das Seitenverhältnis der Arbeitsfläche für Freihandsignaturen kleiner als 1 ist, werden die Geolocation-Informationen am unteren Rand der Arbeitsfläche für die Freihandsignatur hinzugefügt.

* Wenn das Seitenverhältnis der Arbeitsfläche für Freihandsignaturen größer als 1 ist, werden die Geolocation-Informationen auf der rechten Seite der Arbeitsfläche für Freihandsignaturen hinzugefügt.

![scribble signature-bottom](/help/forms/using/assets/scribble-signature-aspectratio.PNG)


>[!NOTE]
>
>Signaturen werden immer im PNG-Format gespeichert.
>

## Adaptives Formular konfigurieren, um Freihandsignatur zu verwenden {#configure-an-adaptive-form-to-use-scribble-signature}

1. Erstellen Sie ein adaptives Formular mit aktivierter Option „Datensatzdokument“ oder basierend auf eine Formularvorlage. Einzelschritte finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md).
1. Ziehen Sie die Komponente **Freihandsignatur** aus dem Komponenten-Browser in das adaptive Formular.
1. Klicken Sie auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und Eigenschaften der Komponente „Freihandsignatur“ angezeigt. Konfigurieren Sie die Eigenschaften der Komponente „Freihandsignatur“.
1. Ziehen Sie die Signaturschritt-Komponente aus dem Komponenten-Browser in das adaptive Formular.

   >[!NOTE]
   >
   >Die Komponente „Signaturschritt“ nimmt die gesamte für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Komponente „Signaturschritt“ enthält.
   >

1. Wählen Sie im Inhalts-Browser **Formular-Container** und das Symbol **Konfigurieren** ![configure](/help/forms/using/assets/configure.png) aus. Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Containers für adaptive Formulare anzeigt. Navigieren Sie zu **Container für adaptive Formulare** > **Elektronische Signatur** und heben Sie die Auswahl der Option **Adobe Sign aktivieren** auf. Wählen Sie Fertig aus ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) -Symbol, um die Änderungen zu speichern.

   >[!NOTE]
   >
   >Wenn Sie einem adaptiven Formular eine Signaturschritt-Komponente hinzufügen, wird die Option „Adobe Sign aktivieren“ ausgewählt.
   >

1. Klicken Sie auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet, der die Eigenschaften des Signaturschritts anzeigt. Konfigurieren Sie die folgenden Eigenschaften:

   * **Elementname**: Geben Sie den Namen der Komponente an.

   * **Titel**: Geben Sie den eindeutigen Titel der Komponente an.
   * **Vorlagennachricht**: Geben Sie die Nachricht an, die angezeigt werden soll, während das PDF-Signaturdokument geladen wird. Adobe Sign-Dienste benötigen einige Zeit, um das PDF-Signaturdokument vorzubereiten und zu laden.
   * **Signaturdienst**: Wählen Sie die Option **Freihandsignatur** aus.

   * **CSS-Klasse**: Geben Sie ggf. die CSS-Klasse der Client-Bibliothek an. Verwendung [themes](../../forms/using/themes.md) und [Inline-Stile](../../forms/using/inline-style-adaptive-forms.md) anstelle der CSS-Klasse.

   Wählen Sie Fertig aus ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) -Symbol, um die Änderungen zu speichern. Die Signatur wurde erfolgreich konfiguriert.

   Wenn Sie jetzt ein Formular ausfüllen, wird eine PDF-Version des adaptiven Formulars angezeigt und es werden Optionen zum Signieren des PDF-Dokuments bereitgestellt. Weitere Informationen finden Sie unter [Unterschreiben eines adaptiven Formulars mit Freihandsignatur](../../forms/using/signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature). 

## Signieren eines adaptiven Formulars mit Freihandsignatur {#sign-an-adaptive-form-using-scribble-signature}

1. Nachdem Sie ein adaptives Formular ausgefüllt und die Seite &quot;Signaturschritt&quot;erreicht haben, wird der Signaturbildschirm angezeigt.

   ![Dialogfeld für Freihandsignatur](/help/forms/using/assets/esignscribblesign.jpg)

1. Klicken Sie auf **[!UICONTROL Signieren]**. Das Dialogfeld „Freihandsignatur“ wird angezeigt. Signieren Sie das Formular und klicken Sie auf das Symbol „Fertig“ ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Signatur zu speichern.

   ![Dialogfeld für Freihandsignatur](/help/forms/using/assets/scribblewidget.png)

1. Klicken Sie auf „Abschließen“, um den Signiervorgang abzuschließen.

   ![Signiervorgang abschließen](/help/forms/using/assets/scribblecomplete.jpg)

Die Signaturen werden dem Formular hinzugefügt und die Formularsteuerung wechselt zum nächsten Bereich.
