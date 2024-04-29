---
title: '„Tutorial: Erstellen Sie Ihr erstes adaptives Formular“'
description: Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen.
topic-tags: introduction
docset: aem65
feature: Adaptive Forms
exl-id: 77a05f83-ac9a-4221-85ac-439e82623a28
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '913'
ht-degree: 100%

---

# Tutorial: Erstellen Sie Ihr erstes adaptives Formular {#tutorial-create-your-first-adaptive-form}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Einführung {#introduction}

Wenn Sie auf der Suche nach einem mobilfreundlichen **Formularerlebnis** sind, das die Registrierung vereinfacht, das Engagement steigert und die Bearbeitungszeit verkürzt, sind **adaptive Formulare** die perfekte Lösung für Sie. Adaptive Formulare bieten ein mobiles, automatisierungs- und analysefreundliches Formularerlebnis. Sie können auf einfache Weise Formulare erstellen, die reaktionsschnell und interaktiv sind, automatisierte Prozesse verwenden, um administrative und sich wiederholende Aufgaben zu reduzieren, und Datenanalysen verwenden, um das Erlebnis, das Kunden mit Ihren Formularen haben, zu verbessern und zu personalisieren.

Dieses Tutorial bietet ein End-to-End-Framework zum Erstellen eines adaptiven Formulars. Das Tutorial ist in einen Anwendungsfall und mehrere Handbücher unterteilt. Jedes Handbuch hilft Ihnen dabei, neue Funktionen zu erlernen und zum adaptiven Formular hinzuzufügen, das in diesem Tutorial erstellt wird. Sie verfügen nach jedem Handbuch über ein funktionierendes adaptives Formular. Das Handbuch zum Erstellen eines adaptiven Formulars ist verfügbar. Nachfolgende Handbücher sind in Kürze verfügbar. Am Ende dieses Tutorials sollten Sie zu Folgendem in der Lage sein:

* Adaptive Formulare und ein Formulardatenmodell erstellen.
* Adaptive Formulare gestalten.
* Den Regeleditor für adaptive Formulare zum Erstellen von Geschäftsregeln verwenden.
* Adaptive Formulare testen und veröffentlichen.

![create-adaptive-form-workflow](assets/create-daptive-form-workflow.png)

Die Tour beginnt mit dem Kennenlernen des Anwendungsfalls:

Eine Website bietet eine Reihe von Produkten für verschiedene Kundinnen bzw. Kunden. Kundinnen bzw. Kunden durchsuchen das Portal, wählen die Produkte aus und bestellen sie. Jede Kundin bzw. jeder Kunde erstellt ein Konto und gibt Versand- und Rechnungsadressen an. Eine bestehende Kundin, Sara Rose, möchte ihre Versandadresse zur Website hinzufügen. Die Website bietet ein Online-Formular zum Hinzufügen und Aktualisieren von Versandadressen.

Die Website wird mit Adobe Experience Manager (AEM) ausgeführt und verwendet AEM [!DNL Forms] für die Erfassung und Verarbeitung von Daten. Das Formular zum Hinzufügen und Aktualisieren von Adressen ist ein adaptives Formular. Die Website speichert Kundendetails in einer Datenbank. Das Formular zum Hinzufügen und Aktualisieren von Adressen dient dazu, verfügbare Adressen abzurufen und anzuzeigen. Außerdem wird das adaptive Formular dazu verwendet, aktualisierte und neue Adressen zu akzeptieren.

### Voraussetzung {#prerequisite}

* Richten Sie eine [AEM-Autoreninstanz ein](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/deploying/deploy.html?lang=de#author-and-publish-installs)
* Installieren Sie das [AEM Forms-Add-On](../../forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz.
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Die Beispiele im Tutorial basieren auf einer [!DNL MySQL]-Datenbank und verwenden [!DNL Oracle's] [MySQL JDBC-Datenbanktreiber](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Richten Sie eine Datenbank mit Kundendaten in den unten gezeigten Feldern ein. Eine Datenbank ist nicht unbedingt notwendig zum Erstellen eines adaptiven Formulars. In diesem Tutorial wird eine Datenbank zur Demonstration der Formulardatenmodell- und Persistenzfunktionen von AEM [!DNL Forms] verwendet.

![adaptiveformdata](assets/adaptiveformdata.png)

## Schritt 1: Erstellen Sie ein adaptives Formular {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Adaptive Formulare repräsentieren eine neue Generation: ansprechend, interaktiv, dynamisch und anpassungsfähig. Mit adaptiven Formularen können Sie personalisierte und zielgerichtete Erlebnisse bieten. AEM [!DNL Forms] bietet einen Drag-and-Drop-WYSIWYG-Editor zum Erstellen von adaptiven Formularen. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung in das Authoring adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

Ziele:

* Erstellen eines adaptiven Formulars, mit dem Kundinnen und Kunden eine Versandadresse hinzufügen können.
* Anzeigen von Layout-Feldern eines adaptiven Formulars und Akzeptieren von Informationen einer Kundin oder eines Kunden.
* Erstellen einer Sendeaktion zum Senden einer E-Mail mit Formularinhalt.
* Anzeigen eines adaptiven Formulars in der Vorschau und Senden des Formulars.

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-adaptive-form.md)

## Schritt 2: Erstellen Sie ein Formulardatenmodell {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Ein Formulardatenmodell ermöglicht es, ein adaptives Formular mit unterschiedlichen Datenquellen zu verbinden. z. B. mit AEM-Benutzerprofilen, RESTful-Web-Diensten, SOAP-basierten Web-Diensten, OData-Diensten und relationalen Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einem adaptiven Formular verwenden, um Daten von verbundenen Datenquellen abzurufen, zu aktualisieren, zu löschen und ihnen hinzuzufügen.

Ziele:

* Konfigurieren der Datenbankinstanz der Website ([!DNL MySQL]-Datenbank) als Datenquelle.
* Erstellen des Formulardatenmodells mithilfe der [!DNL MySQL]-Datenbank als Datenquelle.
* Hinzufügen von Datenmodellobjekten zum Datenmodell.
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte.
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten.

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-form-data-model.md)

## Schritt 3: Wenden Sie Regeln auf adaptive Formularfelder an {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Adaptive Formulare stellen einen Editor zum Schreiben von Regeln für adaptive Formularobjekte bereit. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dies hilft, die Genauigkeit zu gewährleisten, und beschleunigt das Ausfüllen der Formulare.

Ziele:

* Erstellen und Anwenden von Regeln in adaptiven Formularfeldern.
* Verwenden von Regeln zum Auslösen von Formulardatenmodelldiensten, um Daten in der Datenbank zu aktualisieren.

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](apply-rules-to-adaptive-form-fields.md)

## Schritt 4: Gestalten Sie Ihr adaptives Formular {#step-style-your-adaptive-form}

![adaptive-form-styling](/help/forms/using/assets/09-style-your-adaptive-form-small.png)

Adaptive Formulare bieten Designs und einen [Editor](../../forms/using/themes.md), um Designs für die adaptiven Formulare zu erstellen. Ein Design umfasst Formatierungsdetails für Komponenten und Bereiche, und Sie können ein Design in verschiedenen Formularen wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf ein Formular anwenden, wird der festgelegte Stil auf die entsprechenden Komponenten des Formulars angewendet. Adaptive Formulare unterstützen auch das Inline-Styling für Designs, die spezifisch für ein Formular sind.

Ziele:

* Anwenden eines vorkonfigurierten Designs auf ein adaptives Formular.
* Erstellen eines Designs für ein adaptives Formular mit dem Design-Editor.
* Verwenden von Web Fonts in einem benutzerdefinierten Design.

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Schritt 5: Veröffentlichen Sie Ihr adaptives Formular {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Sie können adaptive Formulare als eigenständiges Formular (Einzelseitenprogramm) veröffentlichen, in eine AEM [Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md) einbinden oder mithilfe des [Formularportals](../../forms/using/introduction-publishing-forms.md) in einer AEM-[!DNL Site] auflisten.

Ziele:

* Veröffentlichen des adaptiven Formulars als AEM-Seite.
* Einbetten des adaptiven Formulars in eine AEM [!DNL Sites]-Seite.
* Einbetten des adaptiven Formulars in eine externe Web-Seite (eine außerhalb von AEM gehostete, nicht zu AEM gehörende Web-Seite).

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](publish-your-adaptive-form.md)
