---
title: '"Tutorial: Publish your adaptive form"'
seo-title: '"Tutorial: Publish your adaptive form"'
description: Publish the adaptive form as an AEM page, embed the form to an AEM Sites page, or embed the adaptive form in an external webpage
seo-description: Publish the adaptive form as an AEM page, embed the form to an AEM Sites page, or embed the adaptive form in an external webpage
uuid: 1b164376-e61a-40aa-9f16-c79d24a72e20
contentOwner: khsingh
topic-tags: introduction
discoiquuid: e24dbd0e-4481-4f9d-9570-3a4046b3ef35
docset: aem65
translation-type: tm+mt
source-git-commit: 1a816672b3e97346f5a7a984fcb4dc0df1a5b0da
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 9%

---


# Tutorial: Publish your adaptive form {#tutorial-publish-your-adaptive-form}

![](do-not-localize/13-publish-your-adaptive-form-small.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

After the adaptive form is ready, you can publish the form to make it available for end users. The end users can open the published form on any device and internet browser. When an adaptive form is published, the form and related content are copied from an AEM author instance to an AEM publish instance. Das Formular wird dem Endbenutzer über die Veröffentlichungsinstanz zur Verfügung gestellt.

Sie haben die folgenden Methoden, um ein adaptives Formular zu veröffentlichen:

* [Veröffentlichen des adaptiven Formulars als AEM](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Einbetten des adaptiven Formulars in eine AEM Sites-Seite](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Einbetten des adaptiven Formulars in eine externe Webseite (eine nicht AEM Webseite, die außerhalb AEM gehostet wird)](../../forms/using/publish-your-adaptive-form.md)

## Bevor Sie beginnen {#before-you-start}

* **[Einrichten einer AEM Forms-Veröffentlichungsinstanz](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)**: Die Instanz im Veröffentlichungsmodus ist eine öffentlich zugängliche Instanz von AEM, die im Veröffentlichungsmodus ausgeführt [!DNL Forms] wird. In einer Produktions-Umgebung befindet sich die Veröffentlichungsinstanz außerhalb der Firewall des Unternehmens.
* **[Richten Sie Replizierung und umgekehrte Replizierung](https://helpx.adobe.com/experience-manager/6-3/help/sites-deploying/replication.html)** ein: Replizierung kopiert Inhalte aus der Autoreninstanz in eine Veröffentlichungsinstanz und gibt Benutzereingaben (z. B. Formulareingaben) aus der Veröffentlichungsinstanz an die Autoreninstanz zurück.

## Veröffentlichen des adaptiven Formulars als AEM {#publish-the-adaptive-form-as-an-aem-page}

Wenn das adaptive Formular als AEM veröffentlicht wird, enthält die gesamte Webseite nur das veröffentlichte Formular. Sie können die URL des adaptiven Formulars verwenden, um es von einer anderen Webseite aus zu verknüpfen. So veröffentlichen Sie das adaptive Formular **shipping-address-add-update-form** als AEM:

1. Melden Sie sich bei AEM [!DNL Forms] Autoreninstanz an und suchen Sie das adaptive Formular &quot;shipping-address-add-update-form&quot;in der AEM [!DNL Forms] -Benutzeroberfläche.
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Wählen Sie das adaptive Formular &quot;shipping-address-add-update-form&quot;und klicken Sie auf **[!UICONTROL Veröffentlichen]**. Ein Dialogfeld mit Assets, die mit dem adaptiven Formular in Verbindung stehen, wird angezeigt. Tippen Sie auf **[!UICONTROL Veröffentlichen]**. Das adaptive Formular wird veröffentlicht und ein Dialogfeld mit Erfolg wird angezeigt.
1. Öffnen Sie das Formular in der Veröffentlichungsinstanz. Das Formular kann vom Endbenutzer ausgefüllt und gesendet werden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Einbetten des adaptiven Formulars in eine AEM Sites-Seite {#embed-the-adaptive-form-in-an-aem-sites-page}

AEM [!DNL Forms] ermöglicht es Formularentwicklern, adaptive Formulare nahtlos in eine AEM [!DNL Sites] Seite einzubetten. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

AEM [!DNL Forms] stellen Sie eine Komponente AEM [!DNL Forms] Container bereit, um ein adaptives Formular in eine AEM [!DNL Sites] Seite einzubetten. Standardmäßig ist die Komponente im AEM [!DNL Sites] Container nicht sichtbar. Führen Sie die folgenden Schritte aus, um die Komponente AEM [!DNL Forms] Container zu aktivieren und das adaptive Formular in eine AEM [!DNL Sites] Seite einzubetten:

1. Erstellen und öffnen Sie eine Seite auf der Website We.Retail zur Bearbeitung. Beispiel: [https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). The adaptive form is embedded to the [!DNL Sites] page.

   Sie können das adaptive Formular auch in eine bestehende [!DNL Site's] Seite &quot;We.Retail&quot;einbetten. Zum Beispiel die Seite &quot;ABOUT US&quot; [https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Dadurch sparen Sie Zeit, eine Seite zu erstellen. Die folgenden Schritte verwenden die neu erstellte Seite.

   Die Website We.Retail wird mit AEM ausgeliefert. Wenn Sie die Website &quot;We.Retail&quot;nicht installiert haben, lesen Sie die Informationen unter [We.Retail Reference Implementation](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/we-retail.html) installieren.

1. Tippen Sie auf die ![Eigenschaften](assets/properties.png) -Seiteninformationen und wählen Sie auf der neu erstellten Website &quot;Wir.Einzelhandel&quot;die Option &quot;Vorlage **** bearbeiten&quot;aus. Die Vorlage der Seite wird in einer neuen Registerkarte des Browsers geöffnet.
1. Tippen Sie im Feld **[!UICONTROL Layout-Container]** auf ![Feedmanagement](assets/feedmanagement.png). Erweitern Sie auf der Registerkarte &quot; **[!UICONTROL Zulässige Komponenten]** &quot;das Akkordeon &quot; **[!UICONTROL Allgemein]** &quot;, wählen Sie die Option &quot; **[!UICONTROL AEM Formular]** &quot;und klicken Sie auf &quot; ![save_icon](assets/save_icon.svg)&quot;. Die Komponente &quot;AEM [!DNL Forms] Container&quot;ist für die Seite aktiviert.

1. Open the browser tab containing AEM [!DNL Sites] page opened in step 1. Tap the **[!UICONTROL Drag components here]** box and tap **+.** In the **[!UICONTROL Insert New Component]** box, tap **[!UICONTROL AEM Form]**. The **[!UICONTROL AEM Forms Container]** component is added to the page.
1. Tippen Sie auf die Komponente **[!UICONTROL AEM Forms Container]** und dann auf ![configure-icon](assets/configure-icon.svg). Ein Dialogfeld mit den Eigenschaften AEM [!DNL Forms] Containers wird angezeigt. Suchen Sie im Feld **[!UICONTROL Asset Path]** das adaptive Formular shipping-address-add-update-form und wählen Sie es aus. Tippen Sie auf ![save_icon](assets/save_icon.svg). Das adaptive Formular ist in die Seite eingebettet.
1. Veröffentlichen Sie das adaptive Formular und die [!DNL Sites] Seite. Beachten Sie dabei Folgendes:

   * If you publish the AEM [!DNL Sites] page for the first time and it includes an embedded form, publish the [!DNL Sites] page and the embedded form.
   * Wenn Sie nur das eingebettete Formular auf einer veröffentlichten Siteseite ändern, veröffentlichen Sie das Originalformular und die Änderungen werden auf der veröffentlichten Siteseite übernommen. Die veröffentliche Siteseite enthält einen Verweis auf das Formular ein und erfordert kein erneutes Veröffentlichen der Seite.
   * Wenn Sie die [!DNL Sites] Seite und das eingebettete Formular ändern, veröffentlichen Sie die [!DNL Sites] Seite und das Formular erneut.

      ![embed-in-aem-sites](assets/embed-in-aem-sites.png)
   Formular zur Änderung der Lieferungs- und Rechnungsadresse, das zu einer AEM [!DNL Sites] Seite hinzugefügt wurde.

## Embed the adaptive form in an external webpage {#embed-the-adaptive-form-in-an-external-webpage}

You can embed an adaptive form to an external web page (a non-AEM webpage hosted outside AEM) by inserting a few lines of JavaScript in the external web page. The JavaScript code sends an HTTP request to the AEM [!DNL Forms] server for the adaptive form and related resources and adds the adaptive form to the web page. For detailed steps, see [embed the adaptive form to an external web page](/help/forms/using/embed-adaptive-form-external-web-page.md).
