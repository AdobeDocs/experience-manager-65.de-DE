---
title: '"Tutorial: Veröffentlichen des adaptiven Formulars"'
seo-title: '"Tutorial: Veröffentlichen des adaptiven Formulars"'
description: Veröffentlichen Sie das adaptive Formular als AEM, betten Sie das Formular auf einer AEM Sites-Seite ein oder betten Sie das adaptive Formular in eine externe Webseite ein.
seo-description: Veröffentlichen Sie das adaptive Formular als AEM, betten Sie das Formular auf einer AEM Sites-Seite ein oder betten Sie das adaptive Formular in eine externe Webseite ein.
uuid: 1b164376-e61a-40aa-9f16-c79d24a72e20
contentOwner: khsingh
topic-tags: introduction
discoiquuid: e24dbd0e-4481-4f9d-9570-3a4046b3ef35
docset: aem65
feature: Adaptive Formulare
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 9%

---


# Übung: Veröffentlichen des adaptiven Formulars {#tutorial-publish-your-adaptive-form}

![](do-not-localize/13-publish-your-adaptive-form-small.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

Nachdem das adaptive Formular fertig ist, können Sie es veröffentlichen, um es für Endbenutzer verfügbar zu machen. Die Endbenutzer können das veröffentlichte Formular auf jedem Gerät und in jedem Internetbrowser öffnen. Wenn ein adaptives Formular veröffentlicht wird, werden das Formular und der zugehörige Inhalt von einer AEM Autoreninstanz in eine AEM Veröffentlichungsinstanz kopiert. Das Formular wird dem Endbenutzer über die Veröffentlichungsinstanz zur Verfügung gestellt.

Sie haben die folgenden Methoden, um ein adaptives Formular zu veröffentlichen:

* [Veröffentlichen des adaptiven Formulars als AEM](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Einbetten des adaptiven Formulars in eine AEM Sites-Seite](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Einbetten des adaptiven Formulars in eine externe Webseite (eine nicht AEM Webseite, die außerhalb AEM gehostet wird)](../../forms/using/publish-your-adaptive-form.md)

## Bevor Sie beginnen {#before-you-start}

* **[Einrichten einer AEM Forms-Veröffentlichungsinstanz](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)**: Die Instanz im Veröffentlichungsmodus ist eine öffentliche Instanz AEM, die im Veröffentlichungsmodus  [!DNL Forms] ausgeführt wird. In einer Produktions-Umgebung befindet sich die Veröffentlichungsinstanz außerhalb der Firewall des Unternehmens.
* **[Richten Sie Replizierung und umgekehrte Replizierung](https://helpx.adobe.com/experience-manager/6-3/help/sites-deploying/replication.html)** ein: Replizierung kopiert Inhalte aus der Autoreninstanz in eine Veröffentlichungsinstanz und gibt Benutzereingaben (z. B. Formulareingaben) aus der Veröffentlichungsinstanz an die Autoreninstanz zurück.

## Veröffentlichen Sie das adaptive Formular als AEM Seite {#publish-the-adaptive-form-as-an-aem-page}

Wenn das adaptive Formular als AEM veröffentlicht wird, enthält die gesamte Webseite nur das veröffentlichte Formular. Sie können die URL des adaptiven Formulars verwenden, um es von einer anderen Webseite aus zu verknüpfen. So veröffentlichen Sie das adaptive Formular **shipping-address-add-update-form** als AEM Seite:

1. Melden Sie sich bei AEM [!DNL Forms] Autoreninstanz an und suchen Sie das adaptive Formular shipping-address-add-update-form in der AEM [!DNL Forms]-Benutzeroberfläche.
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Wählen Sie das adaptive Formular shipping-address-add-update-form und tippen Sie auf **[!UICONTROL Publish]**. Ein Dialogfeld mit Assets, die mit dem adaptiven Formular in Verbindung stehen, wird angezeigt. Tippen Sie auf **[!UICONTROL Veröffentlichen]**. Das adaptive Formular wird veröffentlicht und ein Dialogfeld mit Erfolg wird angezeigt.
1. Öffnen Sie das Formular in der Veröffentlichungsinstanz. Das Formular kann vom Endbenutzer ausgefüllt und gesendet werden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Einbetten des adaptiven Formulars in eine AEM Sites-Seite {#embed-the-adaptive-form-in-an-aem-sites-page}

AEM [!DNL Forms] ermöglicht es Formularentwicklern, adaptive Formulare nahtlos in eine AEM [!DNL Sites]-Seite einzubetten. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

AEM [!DNL Forms] geben Sie eine Komponente AEM [!DNL Forms]-Container ein, um ein adaptives Formular in eine AEM [!DNL Sites]-Seite einzubetten. Standardmäßig ist die Komponente im Container AEM [!DNL Sites] nicht sichtbar. Führen Sie die folgenden Schritte aus, um die Komponente AEM [!DNL Forms] Container zu aktivieren und das adaptive Formular in eine AEM [!DNL Sites]-Seite einzubetten:

1. Erstellen und öffnen Sie eine Seite auf der Website We.Retail zur Bearbeitung. Beispiel: [https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). Das adaptive Formular wird in die Seite [!DNL Sites] eingebettet.

   Sie können das adaptive Formular auch in eine bestehende Web.Retail [!DNL Site's]-Seite einbetten. Beispielsweise die Seite &quot;ABOUT US&quot;[https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Dadurch sparen Sie Zeit, eine Seite zu erstellen. Die folgenden Schritte verwenden die neu erstellte Seite.

   Die Website We.Retail wird mit AEM ausgeliefert. Wenn Sie die Website We.Retail nicht installiert haben, lesen Sie [We.Retail Reference Implementation](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/we-retail.html) installieren Sie die Site.

1. Tippen Sie auf ![properties](assets/properties.png)-Seiteninformationen und wählen Sie die Option **[!UICONTROL Vorlage bearbeiten]** auf der neu erstellten Website. Die Vorlage der Seite wird in einer neuen Registerkarte des Browsers geöffnet.
1. Tippen Sie im Feld **[!UICONTROL layout Container]** auf ![feed management](assets/feedmanagement.png). Erweitern Sie auf der Registerkarte **[!UICONTROL Zulässige Komponenten]** das Akkordeon **[!UICONTROL Allgemein]**, wählen Sie die Option **[!UICONTROL AEM Formular]** und tippen Sie auf ![save_icon](assets/save_icon.svg). Die AEM [!DNL Forms]-Container-Komponente ist für die Seite aktiviert.

1. Öffnen Sie die Registerkarte &quot;Browser&quot;, die AEM [!DNL Sites] Seite enthält, die in Schritt 1 geöffnet wurde. Tippen Sie auf das Feld **[!UICONTROL Komponenten hierher ziehen]** und dann auf **+.** Tippen Sie im Feld &quot;Neue Komponente  **[!UICONTROL einfügen&quot;]** auf  **[!UICONTROL AEM Formular]**. Die Komponente **[!UICONTROL AEM Forms Container]** wird der Seite hinzugefügt.
1. Tippen Sie auf die Komponente **[!UICONTROL AEM Forms Container]** und dann auf ![configure-icon](assets/configure-icon.svg). Ein Dialogfeld mit den Eigenschaften AEM [!DNL Forms]-Containers wird angezeigt. Suchen Sie im Feld **[!UICONTROL Asset Path]** das adaptive Formular shipping-address-add-update-form und wählen Sie es aus. Tippen Sie auf ![save_icon](assets/save_icon.svg). Das adaptive Formular ist in die Seite eingebettet.
1. Veröffentlichen Sie das adaptive Formular und die Seite [!DNL Sites]. Beachten Sie dabei Folgendes:

   * Wenn Sie die AEM [!DNL Sites]-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes Formular enthält, veröffentlichen Sie die [!DNL Sites]-Seite und das eingebettete Formular.
   * Wenn Sie nur das eingebettete Formular auf einer veröffentlichten Siteseite ändern, veröffentlichen Sie das Originalformular und die Änderungen werden auf der veröffentlichten Siteseite übernommen. Die veröffentliche Siteseite enthält einen Verweis auf das Formular ein und erfordert kein erneutes Veröffentlichen der Seite.
   * Wenn Sie die Seite [!DNL Sites] und das eingebettete Formular ändern, veröffentlichen Sie die Seite [!DNL Sites] und das Formular erneut.

      ![embed-in-aem-sites](assets/embed-in-aem-sites.png)
   Formular zur Änderung der Liefer- und Rechnungsadresse, das einer AEM [!DNL Sites] hinzugefügt wird.

## Einbetten des adaptiven Formulars in eine externe Webseite {#embed-the-adaptive-form-in-an-external-webpage}

Sie können ein adaptives Formular in eine externe Webseite einbetten (eine nicht AEM Webseite, die außerhalb AEM gehostet wird), indem Sie einige Zeilen JavaScript in die externe Webseite einfügen. Der JavaScript-Code sendet eine HTTP-Anforderung für das adaptive Formular und die zugehörigen Ressourcen an den AEM [!DNL Forms]-Server und fügt das adaptive Formular der Webseite hinzu. Ausführliche Anweisungen finden Sie unter [Einbetten des adaptiven Formulars in eine externe Webseite](/help/forms/using/embed-adaptive-form-external-web-page.md).
