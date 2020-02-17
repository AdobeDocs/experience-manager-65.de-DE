---
title: '"Tutorial: Veröffentlichen des adaptiven Formulars"'
seo-title: '"Tutorial: Veröffentlichen des adaptiven Formulars"'
description: Veröffentlichen des adaptiven Formulars als AEM-Seite, Einbetten des Formulars in eine AEM-Siteseite oder Einbetten des adaptiven Formulars in eine externe Webseite
seo-description: Veröffentlichen des adaptiven Formulars als AEM-Seite, Einbetten des Formulars in eine AEM-Siteseite oder Einbetten des adaptiven Formulars in eine externe Webseite
uuid: 1b164376-e61a-40aa-9f16-c79d24a72e20
contentOwner: khsingh
topic-tags: introduction
discoiquuid: e24dbd0e-4481-4f9d-9570-3a4046b3ef35
docset: aem65
translation-type: tm+mt
source-git-commit: 709d8fe467f5449eb1e844a49126535a4a4a6e7a

---


# Tutorial: Publish your adaptive form {#tutorial-publish-your-adaptive-form}

![](do-not-localize/13-publish-your-adaptive-form-small.png)

Diese Schulung ist ein Schritt in der Serie [Erstellen Sie Ihr erstes adaptives Formular](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). Es wird empfohlen, der Serie in chronologischer Reihenfolge zu folgen, um den vollständigen Anwendungsfall zu verstehen, auszuführen und zu demonstrieren.

Nachdem das adaptive Formular fertig ist, können Sie es veröffentlichen, um es für Endbenutzer verfügbar zu machen. Endbenutzer können das veröffentlichte Formular auf jedem Gerät und in jedem Internetbrowser öffnen. Wenn ein adaptives Formular veröffentlicht wird, werden das Formular und der zugehörige Inhalt von einer AEM-Autoreninstanz in eine AEM-Veröffentlichungsinstanz kopiert. Das Formular wird dem Endbenutzer über die Veröffentlichungsinstanz zur Verfügung gestellt.

Sie haben die folgenden Methoden, um ein adaptives Formular zu veröffentlichen:

* [Veröffentlichen des adaptiven Formulars als AEM-Seite](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Einbetten des adaptiven Formulars in eine AEM-Siteseite](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Einbetten des adaptiven Formulars in eine externe Webseite (eine Nicht-AEM-Webseite, die außerhalb von AEM gehostet wird)](../../forms/using/publish-your-adaptive-form.md)

## Bevor Sie beginnen {#before-you-start}

* **[Einrichten einer AEM Forms-Veröffentlichungsinstanz](https://helpx.adobe.com/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)**: Die Veröffentlichungsinstanz ist eine öffentliche Instanz von AEM Forms, die im Veröffentlichungsmodus ausgeführt wird. In einer Produktionsumgebung befindet sich die Veröffentlichungsinstanz außerhalb der Firewall des Unternehmens.
* **[Richten Sie Replizierung und umgekehrte Replizierung](https://helpx.adobe.com/experience-manager/6-3/help/sites-deploying/replication.html)**ein: Replizierung kopiert Inhalte aus der Autoreninstanz in eine Veröffentlichungsinstanz und gibt Benutzereingaben (z. B. Formulareingaben) aus der Veröffentlichungsinstanz an die Autoreninstanz zurück.

## Veröffentlichen des adaptiven Formulars als AEM-Seite {#publish-the-adaptive-form-as-an-aem-page}

Wenn das adaptive Formular als AEM-Seite veröffentlicht wird, enthält die gesamte Webseite nur das veröffentlichte Formular. Sie können die URL des adaptiven Formulars verwenden, um es von einer anderen Webseite aus zu verknüpfen. So veröffentlichen Sie das adaptive Formular **shipping-address-add-update-form** als AEM-Seite:

1. Melden Sie sich bei der Autoreninstanz von AEM Forms an und suchen Sie das adaptive Formular shipping-address-add-update-form in der AEM Forms-Benutzeroberfläche.
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Wählen Sie das adaptive Formular &quot;shipping-address-add-update-form&quot;und klicken Sie auf **Veröffentlichen**. Ein Dialogfeld mit Assets, die mit dem adaptiven Formular in Verbindung stehen, wird angezeigt. Tippen Sie auf **Veröffentlichen**. Das adaptive Formular wird veröffentlicht und ein Dialogfeld mit Erfolg wird angezeigt.
1. Öffnen Sie das Formular in der Veröffentlichungsinstanz. Das Formular kann vom Endbenutzer ausgefüllt und gesendet werden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Einbetten des adaptiven Formulars in eine AEM-Siteseite {#embed-the-adaptive-form-in-an-aem-sites-page}

Mit AEM Forms können Formularentwickler adaptive Formulare nahtlos in eine AEM-Siteseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzern, im Kontext anderer Elemente auf der Webseite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

AEM Forms bietet eine Komponente, den AEM Forms-Container, um ein adaptives Formular in eine AEM-Siteseite einzubetten. Standardmäßig ist die Komponente nicht im AEM-Sites-Container sichtbar. Führen Sie die folgenden Schritte aus, um die AEM Forms-Container-Komponente zu aktivieren und das adaptive Formular in eine AEM-Siteseite einzubetten:

1. Erstellen und öffnen Sie eine Seite auf der Website We.Retail zur Bearbeitung. Beispiel: [https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). Das adaptive Formular ist in die Siteseite eingebettet.

   Sie können das adaptive Formular auch in eine bestehende Website von We.Retail einbetten. Zum Beispiel die Seite &quot;ABOUT US&quot; [https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Dadurch sparen Sie Zeit, eine Seite zu erstellen. Die folgenden Schritte verwenden die neu erstellte Seite.

   Die Website We.Retail wird mit AEM ausgeliefert. Wenn Sie die Website &quot;We.Retail&quot;nicht installiert haben, lesen Sie die Informationen unter [We.Retail Reference Implementation](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/we-retail.html) installieren.

1. Tippen Sie auf die ![Eigenschaften](assets/properties.png) -Seiteninformationen und wählen Sie auf der neu erstellten Website &quot;Wir.Einzelhandel&quot;die Option &quot;Vorlage **** bearbeiten&quot;aus. Die Vorlage der Seite wird in einer neuen Registerkarte des Browsers geöffnet.
1. Tippen Sie in das Feld **Layout-Container** und dann auf ![Feedmanagement](assets/feedmanagement.png). Erweitern Sie auf der Registerkarte &quot; **Zulässige Komponenten** &quot;das Akkordeon &quot; **Allgemein** &quot;, wählen Sie die Option &quot; **AEM Form** &quot;und tippen Sie auf ![](https://helpx.adobe.com/content/dam/help/en/aem-forms/icons/AEM_6_3_Forms_save.PNG). Die AEM Forms-Container-Komponente ist für die Seite aktiviert.

1. Öffnen Sie die Browser-Registerkarte mit der Seite AEM-Sites, die in Schritt 1 geöffnet wurde. Tippen Sie auf das Feld Komponenten hierher **** ziehen und dann auf **+.** Tippen Sie im Feld Neue Komponente **** einfügen auf **AEM Form.** Die **AEM Forms-Container** -Komponente wird der Seite hinzugefügt.
1. Tippen Sie auf die **AEM Forms-Container** -Komponente und dann auf ![](https://helpx.adobe.com/content/dam/help/en/aem-forms/6-2/cmppr.png). Ein Dialogfeld mit Eigenschaften des AEM Forms-Containers wird angezeigt. Suchen Sie im Feld **Asset Path** das adaptive Formular shipping-address-add-update-form und wählen Sie es aus. Tippen Sie auf ![](https://helpx.adobe.com/content/dam/help/en/aem-forms/icons/AEM_6_3_Forms_save.PNG). Das adaptive Formular ist in die Seite eingebettet.
1. Veröffentlichen Sie das adaptive Formular und die Siteseite. Beachten Sie dabei Folgendes:

   * Wenn Sie die AEM-Siteseite zum ersten Mal veröffentlichen und sie ein eingebettetes Formular enthält, veröffentlichen Sie die Siteseite und das eingebettete Formular.
   * Wenn Sie nur das eingebettete Formular auf einer veröffentlichten Siteseite ändern, veröffentlichen Sie das Originalformular und die Änderungen werden auf der veröffentlichten Siteseite übernommen. Die veröffentliche Siteseite enthält einen Verweis auf das Formular ein und erfordert kein erneutes Veröffentlichen der Seite.
   * Wenn Sie die Siteseite und das eingebettete Formular ändern, veröffentlichen Sie die Siteseite und das Formular erneut.
   ![embed-in-aem-sites](assets/embed-in-aem-sites.png)

   Formular zur Änderung der Liefer- und Rechnungsadresse, das zu einer AEM-Siteseite hinzugefügt wurde.

## Einbetten des adaptiven Formulars in eine externe Webseite {#embed-the-adaptive-form-in-an-external-webpage}

Sie können ein adaptives Formular in eine externe Webseite einbetten (eine Nicht-AEM-Webseite, die außerhalb von AEM gehostet wird), indem Sie einige Zeilen JavaScript in die externe Webseite einfügen. Der JavaScript-Code sendet eine HTTP-Anforderung an den AEM Forms-Server für das adaptive Formular und zugehörige Ressourcen und fügt das adaptive Formular der Webseite hinzu. Ausführliche Anweisungen finden Sie unter [Einbetten des adaptiven Formulars in eine externe Webseite](/help/forms/using/embed-adaptive-form-external-web-page.md).
