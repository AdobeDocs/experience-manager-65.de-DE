---
title: '"Tutorial: Erstellen des ersten adaptiven Formulars"'
seo-title: '"Tutorial: Erstellen des ersten adaptiven Formulars"'
description: Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen.
seo-description: Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen.
uuid: ee351a3f-ea6a-4b4c-8045-4948ad51b7c1
topic-tags: introduction
discoiquuid: 1142bcd4-e3a7-41ce-a710-132ae6c21dbe
docset: aem65
feature: Adaptive Formulare
exl-id: 77a05f83-ac9a-4221-85ac-439e82623a28
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 65%

---

# Tutorial: Erstellen Sie Ihr erstes adaptives Formular {#tutorial-create-your-first-adaptive-form}

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Einführung {#introduction}

Sind Sie auf der Suche nach einer benutzerfreundlichen **Formularerfahrung**, die die Einschreibung vereinfacht, das Engagement erhöht und die Bearbeitungszeit verkürzt, dann passen **adaptive Formulare** perfekt für Sie. Adaptive Formulare bieten eine für Mobilgeräte, Automatisierung und Analysen geeignete Formularerfahrung. Sie können auf einfache Weise Formulare erstellen, die interaktiv und interaktiv sind, automatisierte Prozesse zur Reduzierung administrativer und sich wiederholender Aufgaben verwenden und Datenanalysen verwenden, um das Erlebnis, das Kunden mit Ihren Formularen haben, zu verbessern und zu personalisieren.

Diese Schulung bietet ein End-to-End-Framework zum Erstellen eines adaptiven Formulars. Die Schulung ist in einen Anwendungsfall und mehrere Leitfäden unterteilt. Jeder Leitfaden hilft Ihnen beim Erlernen und Hinzufügen neuer Funktionen zu dem adaptiven Formular, das in dieser Schulung erstellt wird. Sie haben nach jedem Leitfaden ein funktionierendes adaptives Formular. Der Leitfaden zum Erstellen eines adaptiven Formulars ist verfügbar. Weitere Leitfäden werden in Kürze verfügbar sein. Am Ende dieser Schulung können Sie Folgendes:

* Adaptive Formulare und ein Formulardatenmodell erstellen.
* Adaptive Formulare gestalten.
* Den Regel-Editor für adaptive Formulare zum Erstellen von Geschäftsregeln verwenden.
* Adaptive Formulare testen und veröffentlichen.

![create-adaptive-form-workflow](assets/create-daptive-form-workflow.png)

Die Reise beginnt mit dem Erlernen des Anwendungsfalls:

Eine Website bietet eine Reihe von Produkten für verschiedene Kunden. Kunden durchsuchen das Portal, wählen und bestellen die Produkte. Jeder Kunde legt ein Konto an und stellt Versand- und Rechnungsadressen bereit. Eine bestehende Kundin, Sara Rose, möchte ihre Versandadresse auf der Website eintragen. Die Website bietet ein Online-Formular zum Hinzufügen und Aktualisieren von Versandadressen.

Die Website wird auf Adobe Experience Manager (AEM) ausgeführt und verwendet AEM [!DNL Forms] für die Datenerfassung und -verarbeitung. Das Formular zum Hinzufügen und Aktualisieren von Adressen ist ein adaptives Formular. Die Website speichert Kundendaten in einer Datenbank. Sie verwenden das Formular zum Hinzufügen und Aktualisieren von Adressen, um verfügbare Adressen abzurufen und anzuzeigen. Außerdem wird das adaptive Formular dazu verwendet, aktualisierte und neue Adressen zu akzeptieren.

### Voraussetzung {#prerequisite}

* Eine AEM Author-Instanz einrichten.
* Installieren Sie das [AEM Forms-Add-On](../../forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz.
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Die Beispiele im Tutorial basieren auf der [!DNL MySQL]-Datenbank und verwenden [!DNL Oracle's] [MySQL JDBC-Datenbanktreiber](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Richten Sie eine Datenbank mit Kundendaten in den unten gezeigten Feldern ein. Eine Datenbank ist nicht unbedingt notwendig zum Erstellen eines adaptiven Formulars. Dieses Tutorial verwendet eine Datenbank, um Formulardatenmodell und Persistenzfunktionen von AEM [!DNL Forms] anzuzeigen.

![adaptiveformdata](assets/adaptiveformdata.png)

## Schritt 1: Erstellen Sie ein adaptives Formular {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Adaptive Formulare repräsentieren eine neue Generation: ansprechend, interaktiv, dynamisch und anpassungsfähig. Mit adaptiven Formularen können Sie personalisierte und zielgerichtete Erlebnisse bieten. AEM [!DNL Forms] stellen Sie einen Drag &amp; Drop-WYSIWYG-Editor bereit, um adaptive Formulare zu erstellen. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung in das Authoring adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

Ziele:

* Erstellen Sie ein adaptives Formular, mit dem ein Kunde eine Versandadresse hinzufügen kann
* Layout-Felder eines adaptiven Formulars zum Anzeigen und Akzeptieren von Informationen eines Kunden
* Erstellen Sie eine Sendeaktion zum Senden einer E-Mail mit Formularinhalt
* Anzeigen und Senden eines adaptiven Formulars in der Vorschau

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-adaptive-form.md)

## Schritt 2: Erstellen Sie ein Formulardatenmodell {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Ein Formulardatenmodell ermöglicht es, ein adaptives Formular mit unterschiedlichen Datenquellen zu verbinden. Zum Beispiel AEM-Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einem adaptiven Formular verwenden, um Daten von verbundenen Datenquellen abzurufen, zu aktualisieren, zu löschen und ihnen hinzuzufügen.

Ziele:

* Konfigurieren der Datenbankinstanz der Website ([!DNL MySQL] Datenbank) als Datenquellen
* Erstellen Sie das Formulardatenmodell mit der Datenbank [!DNL MySQL] als Datenquelle
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-form-data-model.md)

## Schritt 3: Wenden Sie Regeln auf adaptive Formularfelder an {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Adaptive Formulare stellen einen Editor zum Schreiben von Regeln für adaptive Formularobjekte bereit. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dies hilft, die Genauigkeit zu gewährleisten, und beschleunigt das Ausfüllen der Formulare.

Ziele:

* Erstellen und Anwenden von Regeln in adaptiven Formularfeldern
* Verwenden Sie Regeln zum Auslösen von Formulardatenmodelldiensten, um Daten in der Datenbank zu aktualisieren 

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](apply-rules-to-adaptive-form-fields.md)

## Schritt 4: Gestalten Sie Ihr adaptives Formular {#step-style-your-adaptive-form}

![](/help/forms/using/assets/09-style-your-adaptive-form-small.png)

Adaptive Formulare stellen Designs und einen [Editor](../../forms/using/themes.md) bereit, um Designs für adaptive Formulare zu erstellen. Ein Design umfasst Formatierungsdetails für Komponenten und Bereiche und Sie können ein Design in verschiedenen Formularen wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf ein Formular anwenden, wird der festgelegte Stil auf die entsprechenden Komponenten des Formulars angewendet. Adaptive Formulare unterstützen auch das Inline-Styling für Designs, die spezifisch für ein Formular sind.

Ziele:

* Wenden Sie ein Standarddesign auf ein adaptives Formular an
* Erstellen Sie mithilfe des Designeditors ein Design für das adaptive Formular
* Verwenden von Webfonts in einem benutzerdefinierten Design

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Schritt 5: Testen Sie Ihr adaptives Formular {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Adaptive Formulare sind für die Interaktion mit Ihren Kunden von wesentlicher Bedeutung. Es ist wichtig, Ihre adaptiven Formulare bei jeder Änderung, die Sie daran vornehmen, zu testen. Das Testen jedes Felds eines Formulars ist mühsam. AEM [!DNL Forms] stellen Sie ein SDK (Calvin SDK) bereit, um das Testen adaptiver Formulare zu automatisieren. Calvin ermöglicht es Ihnen das automatische Testen der adaptiven Formulare im Webbrowser.

Ziele:

* Erstellen einer Testsuite für das adaptive Formular
* Erstellen von Testfällen für die adaptiven Formulare
* Führen Sie die Testfälle aus

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](testing-your-adaptive-form.md)

## Schritt 6: Veröffentlichen Sie Ihr adaptives Formular {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Sie können adaptive Formulare als eigenständiges Formular veröffentlichen (Einzelseitenanwendung), in AEM [Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md) einschließen oder eine Liste auf einem AEM [!DNL Site] mithilfe von [Forms Portal](../../forms/using/introduction-publishing-forms.md) erstellen.

Ziele:

* Veröffentlichen des adaptiven Formulars als AEM
* Einbetten des adaptiven Formulars in eine AEM [!DNL Sites] Seite
* Betten Sie das adaptive Formular in eine externe Webseite ein (eine nicht AEM Webseite, die außerhalb von AEM gehostet wird).

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](publish-your-adaptive-form.md)
