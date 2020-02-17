---
title: '"Tutorial: Erstellen Sie das erste adaptive Formular"'
seo-title: '"Tutorial: Erstellen Sie das erste adaptive Formular"'
description: Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen.
seo-description: Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen.
uuid: ee351a3f-ea6a-4b4c-8045-4948ad51b7c1
topic-tags: introduction
discoiquuid: 1142bcd4-e3a7-41ce-a710-132ae6c21dbe
docset: aem65
translation-type: tm+mt
source-git-commit: d2d4e0d8b538c96a7a05be6ad1012343f49694b3

---


# Tutorial: Create your first adaptive form{#tutorial-create-your-first-adaptive-form}

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Einführung {#introduction}

Sind Sie auf der Suche nach einer benutzerfreundlichen **Formularerfahrung**, die die Einschreibung vereinfacht, das Engagement erhöht und die Bearbeitungszeit verkürzt, dann passen **adaptive Formulare** perfekt für Sie. Adaptive Formulare bieten eine für Mobilgeräte, Automatisierung und Analysen geeignete Formularerfahrung. Sie können auf einfache Weise Formulare erstellen, die reaktionsschnell und interaktiv sind, automatisierte Prozesse verwenden, um administrative und sich wiederholende Aufgaben zu reduzieren, und Datenanalysen verwenden, um das Erlebnis, das Kunden mit Ihren Formularen haben, zu verbessern und zu personalisieren.

Diese Schulung bietet ein End-to-End-Framework zum Erstellen eines adaptiven Formulars. Die Schulung ist in einen Anwendungsfall und mehrere Leitfäden unterteilt. Jeder Leitfaden hilft Ihnen beim Erlernen und Hinzufügen neuer Funktionen zu dem adaptiven Formular, das in dieser Schulung erstellt wird. Sie haben nach jedem Leitfaden ein funktionierendes adaptives Formular. Der Leitfaden zum Erstellen eines adaptiven Formulars ist verfügbar. Weitere Leitfäden werden in Kürze verfügbar sein. Am Ende dieser Schulung können Sie Folgendes:

* Adaptive Formulare und ein Formulardatenmodell erstellen.
* Adaptive Formulare gestalten.
* Den Regel-Editor für adaptive Formulare zum Erstellen von Geschäftsregeln verwenden.
* Adaptive Formulare testen und veröffentlichen.

![create-adaptive-form-workflow](assets/create-daptive-form-workflow.png)

Die Reise beginnt mit dem Erlernen des Anwendungsfalls:

Eine Website bietet eine Reihe von Produkten für verschiedene Kunden. Kunden durchsuchen das Portal, wählen und bestellen die Produkte. Jeder Kunde legt ein Konto an und stellt Versand- und Rechnungsadressen bereit. Eine bestehende Kundin, Sara Rose, möchte ihre Versandadresse auf der Website eintragen. Die Website bietet ein Online-Formular zum Hinzufügen und Aktualisieren von Versandadressen.

Die Website wird mit Adobe Experience Manager (AEM) ausgeführt und verwendet AEM Forms für die Erfassung und Verarbeitung von Daten. Das Formular zum Hinzufügen und Aktualisieren von Adressen ist ein adaptives Formular. Die Website speichert Kundendaten in einer Datenbank. Sie verwenden das Formular für die Adresserweiterung und die Aktualisierung, um verfügbare Adressen abzurufen und anzuzeigen. Außerdem wird das adaptive Formular dazu verwendet, aktualisierte und neue Adressen zu akzeptieren.

### Voraussetzung {#prerequisite}

* Eine AEM Author-Instanz einrichten.
* Installieren Sie das [AEM Forms-Add-On](../../forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz.
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Examples in the tutorial are based on MySQL database and use Oracle&#39;s [MySQL JDBC database driver](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Richten Sie eine Datenbank mit Kundendaten in den unten gezeigten Feldern ein. Eine Datenbank ist nicht unbedingt notwendig zum Erstellen eines adaptiven Formulars. In diesem Lernprogramm wird eine Datenbank zur Demonstration der Formulardatenmodell- und Persistenzfunktionen von AEM Forms verwendet.

![adaptiveformdata](assets/adaptiveformdata.png)

## Schritt 1: Erstellen Sie ein adaptives Formular {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Adaptive Formulare repräsentieren eine neue Generation: ansprechend, interaktiv, dynamisch und anpassungsfähig. Mit adaptiven Formularen können Sie personalisierte und zielgerichtete Erlebnisse bieten. AEM Forms bietet einen Drag &amp; Drop-WYSIWYG-Editor zum Erstellen von adaptiven Formularen. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung in das Authoring adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

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

* Konfigurieren der Datenbankinstanz der Website (MySQL-Datenbank) als Datenquelle
* Erstellen des Formulardatenmodells mithilfe der MySQL-Datenbank als Datenquelle
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

Adaptive forms provide themes and an [editor](../../forms/using/themes.md) to create themes for the adaptive forms. Ein Design umfasst Formatierungsdetails für Komponenten und Bereiche und Sie können ein Design in verschiedenen Formularen wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf ein Formular anwenden, wird der festgelegte Stil auf die entsprechenden Komponenten des Formulars angewendet. Adaptive Formulare unterstützen auch das Inline-Styling für Designs, die spezifisch für ein Formular sind.

Ziele:

* Wenden Sie ein Standarddesign auf ein adaptives Formular an
* Erstellen Sie mithilfe des Designeditors ein Design für das adaptive Formular
* Verwenden von Webschriftarten in einem benutzerdefinierten Design

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Schritt 5: Testen Sie Ihr adaptives Formular {#step-test-your-adaptive-form}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Adaptive Formulare sind für die Interaktion mit Ihren Kunden von wesentlicher Bedeutung. Es ist wichtig, Ihre adaptiven Formulare bei jeder Änderung, die Sie daran vornehmen, zu testen. Das Testen jedes Felds eines Formulars ist mühsam. AEM Forms bietet ein SDK (Calvin SDK) zum automatischen Testen von adaptiven Formularen. Calvin ermöglicht es Ihnen das automatische Testen der adaptiven Formulare im Webbrowser.

Ziele:

* Testsuite für das adaptive Formular erstellen
* Testfälle für adaptive Formulare erstellen
* Führen Sie die Testfälle aus

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](testing-your-adaptive-form.md)

## Schritt 6: Veröffentlichen Sie Ihr adaptives Formular {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Sie können adaptive Formulare als eigenständige Formulare (Einzelseitenanwendung) veröffentlichen, sie auf der AEM[-Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md) einbeziehen oder sie auf einer AEM-Site über das[ Forms Portal](../../forms/using/introduction-publishing-forms.md) auflisten.

Ziele:

* Veröffentlichen des adaptiven Formulars als AEM-Seite
* Einbetten des adaptiven Formulars in eine AEM-Siteseite
* Einbetten des adaptiven Formulars in eine externe Webseite (eine Nicht-AEM-Webseite, die außerhalb von AEM gehostet wird)

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](publish-your-adaptive-form.md)