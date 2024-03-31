---
title: "Anleitung: Veröffentlichen Sie Ihr adaptives Formular"
description: Veröffentlichen Sie das adaptive Formular als AEM-Seite, betten Sie es auf einer AEM Sites-Seite ein, oder betten Sie das adaptive Formular in eine externe Webseite ein
contentOwner: khsingh
topic-tags: introduction
docset: aem65
feature: Adaptive Forms
exl-id: c039faec-f832-43d5-8a86-22afa3bef2a4
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 100%

---

# Tutorial: Veröffentlichen des adaptiven Formulars {#tutorial-publish-your-adaptive-form}

![Hero-image](do-not-localize/13-publish-your-adaptive-form-small.png)

Dieses Tutorial ist ein Teil der Serie [Erstellen Ihres ersten adaptives Formulars](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Es wird empfohlen, die Serie in chronologischer Reihenfolge zu durchlaufen, um den vollständigen Anwendungsfall des Tutorials zu verstehen, durchzuführen und zu demonstrieren.

Nachdem das adaptive Formular bereit ist, können Sie das Formular veröffentlichen, um es für Endbenutzer verfügbar zu machen. Die Endbenutzer können das veröffentlichte Formular auf jedem Gerät und in jedem Internet-Browser öffnen. Wenn ein adaptives Formular veröffentlicht wird, werden das Formular und der zugehörige Inhalt aus einer AEM-Autoreninstanz in eine AEM-Veröffentlichungsinstanz kopiert. Das Formular wird dem Endbenutzer über die Veröffentlichungsinstanz zur Verfügung gestellt.

Sie haben folgende Möglichkeiten, um ein adaptives Formular zu veröffentlichen:

* [Veröffentlichen des adaptiven Formulars als AEM-Seite](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Einbetten eines adaptiven Formulars in eine AEM Sites-Seite](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Einbetten des adaptiven Formulars in eine externe Web-Seite (eine außerhalb von AEM gehostete, nicht zu AEM gehörende Web-Seite)](../../forms/using/publish-your-adaptive-form.md)

## Bevor Sie beginnen {#before-you-start}

* **[Einrichten einer AEM Forms-Veröffentlichungsinstanz](https://helpx.adobe.com/de/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)**: Die Veröffentlichungsinstanz ist eine öffentlich zugängliche Instanz von AEM [!DNL Forms] die im Veröffentlichungsmodus ausgeführt wird. In einer Produktionsumgebung befindet sich die Veröffentlichungsinstanz außerhalb der Firewall des Unternehmens.
* **[Einrichten der Replikation und Rückwärtsreplikation](https://helpx.adobe.com/de/experience-manager/6-3/help/sites-deploying/replication.html)**: Die Replikation kopiert Inhalte von der Autoreninstanz an eine Veröffentlichungsinstanz und gibt Benutzereingaben (beispielsweise Formulareingaben) von der Veröffentlichungsinstanz an die Autoreninstanz zurück.

## Veröffentlichen des adaptiven Formulars als AEM-Seite {#publish-the-adaptive-form-as-an-aem-page}

Wenn das adaptive Formular als AEM-Seite veröffentlicht wird, enthält die gesamte Webseite nur veröffentlichte Formulare. Sie können die URL des adaptiven Formulars verwenden, um es von einer anderen Webseite aus zu verknüpfen. So veröffentlichen Sie das adaptive Formular **shipping-address-add-update-form** als AEM-Seite:

1. Melden Sie sich bei der AEM [!DNL Forms]-Autoreninstanz an und suchen Sie in der AEM [!DNL Forms]-Benutzeroberfläche das adaptive Formular „shipping-address-add-update-form“.
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Wählen Sie das adaptive Formular „shipping-address-add-update-form“ und dann **[!UICONTROL Veröffentlichen]** aus. Es wird ein Dialogfeld mit den Assets, die sich auf das adaptive Formular beziehen, angezeigt. Wählen Sie **[!UICONTROL Veröffentlichen]** aus. Das adaptive Formular wird veröffentlicht und eine Erfolgsmeldung erscheint.
1. Öffnen Sie das Formular in der Veröffentlichungsinstanz. Das Formular kann vom Endbenutzer ausgefüllt und gesendet werden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Einbetten eines adaptiven Formulars in eine AEM Sites-Seite {#embed-the-adaptive-form-in-an-aem-sites-page}

AEM [!DNL Forms] ermöglicht es Formularentwicklern, adaptive Formulare nahtlos in eine AEM-[!DNL Sites]-Seite einzubetten. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

AEM [!DNL Forms] bietet eine Komponente, AEM [!DNL Forms]-Container, zum Einbetten eines adaptiven Formulars in eine AEM [!DNL Sites]-Seite. Standardmäßig ist die Komponente im AEM [!DNL Sites]-Container nicht sichtbar. Führen Sie die folgenden Schritte aus, um die AEM [!DNL Forms]-Container-Komponente zu aktivieren und das adaptive Formular in eine AEM [!DNL Sites]-Seite einzubetten:

1. Erstellen und öffnen Sie eine Seite in der „We.Retail“-Website zur Bearbeitung. Zum Beispiel: [https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). Das adaptive Formular ist in die [!DNL Sites]-Seite eingebettet.

   Sie können das adaptive Formular auch in eine vorhandene We.Retail-[!DNL Site's]-Seite einbetten. Zum Beispiel die Seite „ÜBER UNS“ [https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Es spart Ihnen die Zeit, eine Seite zu erstellen. Die folgenden Schritte verwenden die neu erstellte Seite.

   Die „We.Retail“-Seite wird mit AEM ausgeliefert. Wenn Sie die „We.Retail“-Seite nicht installiert haben, lesen Sie [„We.Retail“-Verweis-Implementierung](https://helpx.adobe.com/de/experience-manager/6-3/help/sites-developing/we-retail.html) um die Seite zu installieren.

1. Wählen Sie die Seiteninformation ![Eigenschaften](assets/properties.png) und die Option **[!UICONTROL Vorlage bearbeiten]** auf der neu erstellten „We.Retail“-Webseite aus. Die Vorlage der Seite wird in einer neuen Registerkarte des Browsers geöffnet.
1. Wählen Sie im Feld **[!UICONTROL Layout-Container]** die Option ![Feed-Management](assets/feedmanagement.png) aus. Erweitern Sie auf der Registerkarte **[!UICONTROL Erlaubte Komponenten]** das Akkordeon **[!UICONTROL Allgemein]**, wählen Sie die Option **[!UICONTROL AEM Form]** und anschließend ![save_icon](assets/save_icon.svg) aus. Die AEM [!DNL Forms]-Container-Komponente ist für die Seite aktiviert.

1. Öffnen Sie die Browser-Registerkarte mit der AEM [!DNL Sites]-Seite, die in Schritt 1 geöffnet wurde. Wählen Sie das Feld **[!UICONTROL Komponenten hierher ziehen]** und **+.** Wählen Sie im Feld **[!UICONTROL Neue Komponente einfügen]** die Option **[!UICONTROL AEM-Forms]** aus. Die Komponente **[!UICONTROL AEM Forms-Container]** wird der Seite hinzugefügt.
1. Wählen Sie die Komponente **[!UICONTROL AEM Forms-Container]** und dann ![configure-icon](assets/configure-icon.svg) aus. Es wird ein Dialogfeld mit den Eigenschaften des AEM [!DNL Forms]-Containers angezeigt. Durchsuchen Sie das Feld **[!UICONTROL Asset-Pfad]** nach dem adaptiven Formular „shipping-address-add-update-form“ und wählen Sie es aus. Wählen Sie ![save_icon](assets/save_icon.svg) aus. Das adaptive Formular wird in die Seite eingebettet.
1. Veröffentlichen Sie sowohl das adaptive Formular als auch die [!DNL Sites]-Seite. Beachten Sie dabei Folgendes:

   * Wenn Sie die AEM [!DNL Sites]-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes Formular enthält, veröffentlichen Sie die [!DNL Sites]-Seite und das eingebettete Formular.
   * Wenn Sie nur das eingebettete Formular in einer veröffentlichte Site-Seite geändert haben, veröffentlichen Sie das Originalformular, und die Änderungen werden auf der veröffentlichten Site-Seite übernommen. Die veröffentliche Siteseite enthält einen Verweis auf das Formular ein und erfordert kein erneutes Veröffentlichen der Seite.
   * Wenn Sie die [!DNL Sites]-Seite und das eingebettete Formular geändert haben, veröffentlichen Sie die [!DNL Sites]-Seite und das Formular erneut.

     ![embed-in-aem-sites](assets/embed-in-aem-sites.png)

   Formular zur Änderung der Versand- und Rechnungsadresse zu einer AEM [!DNL Sites]-Seite hinzugefügt.

## Einbetten des adaptiven Formulars in eine externe Web-Seite {#embed-the-adaptive-form-in-an-external-webpage}

Sie können ein adaptives Formular in eine externe Web-Seite (d. h. eine von AEM verschiedene Web-Seite, die außerhalb von AEM gehostet wird) einbetten, indem Sie einige Zeilen JavaScript in die externe Web-Seite einfügen. Der JavaScript-Code sendet eine HTTP-Anfrage an den AEM [!DNL Forms]-Server für das adaptive Formular und die zugehörigen Ressourcen und fügt das adaptive Formular der Web-Seite hinzu. Detaillierte Anweisungen dazu finden Sie unter [Einbetten des adaptiven Formulars in eine externe Web-Seite](/help/forms/using/embed-adaptive-form-external-web-page.md).
