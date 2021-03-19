---
title: Anwenden von elektronischen Signaturen auf ein Formular mithilfe von Freihandsignaturen
seo-title: Anwenden von elektronischen Signaturen auf ein Formular mithilfe von Freihandsignaturen
description: Signieren von Formularen mit Freihandsignaturen
seo-description: Signieren von Formularen mit Freihandsignaturen
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 76d178d1-8e40-41b3-80d4-66b2f8d04211
docset: aem65
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 79%

---


# Anwenden von elektronischen Signaturen auf ein Formular mithilfe von Freihandsignaturen{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

Sie können die Komponente **Freihandsignatur** und die Komponente **Signaturschritt** verwenden, um eine Signatur in ein adaptives Formular zu zeichnen. Die Signaturschritt-Komponente zeigt eine PDF-Version des adaptiven Formulars an. Sie benötigen ein Formular mit aktivierter Option „Datensatzdokument“ oder auf Vorlagen basierende adaptive Formulare, um die Signaturschritt-Komponente zu verwenden.

Wie unten dargestellt, stellen beide Komponenten ein Fenster bereit, um ein Formular zu signieren. Sie können auch auf das Geolocation-Symbol ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) klicken, um der Signatur Geolocation hinzuzufügen.

![Dialogfeld für Freihandsignatur](assets/scribble-signature.png)

## Adaptives Formular konfigurieren, um Freihandsignatur zu verwenden {#configure-an-adaptive-form-to-use-scribble-signature}

1. Erstellen Sie ein adaptives Formular mit aktivierter Option „Datensatzdokument“ oder basierend auf eine Formularvorlage. Schrittweise Informationen finden Sie unter [Erstellen eines adaptiven Formulars](../../forms/using/creating-adaptive-form.md).
1. Ziehen Sie die Komponente **Scribble Signature** aus dem Komponenten-Browser in das adaptive Formular.
1. Tippen Sie auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und Eigenschaften der Freihandsignatur-Komponente angezeigt. Konfigurieren Sie die Eigenschaften der Freihandsignatur-Komponente.
1. Ziehen Sie die Komponente &quot;Signature Step&quot;aus dem Komponenten-Browser in das adaptive Formular.

   >[!NOTE]
   >
   >Die Signaturschritt-Komponente nimmt die volle für das Formular verfügbare Breite ein. Wir empfehlen, keine anderen Komponenten in dem Abschnitt zu platzieren, der die Signaturschritt-Komponente enthält.

1. Tippen Sie im Inhaltsbrowser auf **Form-Container** und dann auf das Symbol **Konfigurieren**![](/help/forms/using/assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Containers für adaptive Formulare an. Navigieren Sie zu **Container für adaptive Formulare** >**Elektronische Signatur** und heben Sie die Auswahl der Option **Adobe Sign aktivieren** auf. Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Änderungen zu speichern.

   >[!NOTE]
   >
   >Wenn Sie einem adaptiven Formular eine Signaturschritt-Komponente hinzufügen, wird die Option „Adobe Sign aktivieren“ ausgewählt.

1. Tippen Sie auf das Symbol **Konfigurieren** ![configure](assets/configure.png). Dadurch wird der Eigenschaftenbrowser geöffnet und zeigt Eigenschaften des Signaturschritts an. Konfigurieren Sie die folgenden Eigenschaften:

   * **Elementname**: Geben Sie den Namen der Komponente an.

   * **Titel:** Geben Sie den eindeutigen Titel der Komponente an.
   * **Vorlagennachricht:** Geben Sie die Nachricht an, die angezeigt werden soll, während die Signatur-PDF geladen wird. Die Adobe Sign-Dienste benötigen einige Zeit, um die Signatur-PDF vorzubereiten und zu laden.
   * **Signaturdienst:** Wählen Sie die Option **Freihandsignatur** aus.

   * **CSS-Klasse**: Geben Sie ggf. die CSS-Klasse der Client-Bibliothek an. Es wird empfohlen, anstelle der CSS-Klasse [Designs](../../forms/using/themes.md) und [Inline-Stile](../../forms/using/inline-style-adaptive-forms.md) zu verwenden.

   Tippen Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Änderungen zu speichern. Die Signatur wurde erfolgreich konfiguriert.

   Wenn Sie jetzt ein Formular ausfüllen, wird eine PDF-Version des adaptiven Formulars angezeigt und es sind Optionen zum Signieren des PDF-Dokuments verfügbar. Ausführliche Informationen finden Sie unter [Signieren eines adaptiven Formulars mit der Scribble-Signatur](../../forms/using/signing-forms-using-scribble.md#sign-an-adaptive-form-using-scribble-signature).

## Unterschreiben eines adaptiven Formulars mit Freihandsignatur {#sign-an-adaptive-form-using-scribble-signature}

1. Wenn Sie ein adaptives Formular ausgefüllt und die Signaturschritt-Seite erreichen, wird der Signaturbildschirm angezeigt.

   ![Signaturbildschirm für EchoSign-Seite](assets/esignscribblesign.jpg)

1. Klicken Sie auf **[!UICONTROL Signieren]**. Das Dialogfeld „Freihandsignatur“ wird angezeigt. Signieren Sie das Formular und klicken Sie auf das Symbol Fertig ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png), um die Signatur zu speichern.

   ![Dialogfeld für Freihandsignatur](assets/scribblewidget.jpg)

1. Klicken Sie auf „Abschließen“, um den Unterzeichnungsvorgang abzuschließen.

   ![Unterzeichnungsvorgang abschließen](assets/scribblecomplete.jpg)

Die Signaturen werden dem Formular hinzugefügt und die Formularsteuerung wechselt zum nächsten Bedienfeld.

