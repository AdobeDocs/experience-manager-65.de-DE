---
title: '„Tutorial: Erstellen Sie Ihr erstes adaptives Formular“'
seo-title: "Tutorial: Create your first adaptive form"
description: Lernen Sie, wie Sie Business-Class-, interaktive und Responsive-Formulare erstellen.
seo-description: Learn to create business class, interactive, and responsive forms.
uuid: ee351a3f-ea6a-4b4c-8045-4948ad51b7c1
topic-tags: introduction
discoiquuid: 1142bcd4-e3a7-41ce-a710-132ae6c21dbe
docset: aem65
feature: Adaptive Forms
exl-id: 77a05f83-ac9a-4221-85ac-439e82623a28
source-git-commit: e9f64722ba7df0a7f43aaf1005161483e04142f5
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 58%

---

# Tutorial: Erstellen Sie Ihr erstes adaptives Formular {#tutorial-create-your-first-adaptive-form}

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Einführung {#introduction}

Suchen Sie einen mobilfreundlichen **Formularerfahrung** das die Einschreibung vereinfacht, die Interaktion erhöht und die Bearbeitungszeit verkürzt, **adaptive Formulare** ist perfekt für dich geeignet. Adaptive Formulare bieten ein mobiles, automatisierungs- und analysefreundliches Formularerlebnis. Sie können auf einfache Weise Formulare erstellen, die reaktionsschnell und interaktiv sind, automatisierte Prozesse verwenden, um administrative und sich wiederholende Aufgaben zu reduzieren, und Datenanalysen verwenden, um das Erlebnis, das Kunden mit Ihren Formularen haben, zu verbessern und zu personalisieren.

Dieses Tutorial bietet ein End-to-End-Framework zum Erstellen eines adaptiven Formulars. Das Tutorial ist in einen Anwendungsfall und mehrere Handbücher unterteilt. Jedes Handbuch hilft Ihnen dabei, neue Funktionen zu lernen und zum adaptiven Formular hinzuzufügen, das in diesem Tutorial erstellt wird. Sie haben nach jedem Handbuch ein funktionierendes adaptives Formular. Das Handbuch zum Erstellen eines adaptiven Formulars ist verfügbar. Nachfolgende Handbücher werden in Kürze verfügbar sein. Am Ende dieser Schulung können Sie Folgendes:

* Erstellen Sie ein adaptives Formular und ein Formulardatenmodell.
* Gestalten Sie Ihr adaptives Formular.
* Verwenden Sie den Regeleditor für adaptive Formulare, um Geschäftsregeln zu erstellen.
* Testen und veröffentlichen Sie ein adaptives Formular.

![create-adaptive-form-workflow](assets/create-daptive-form-workflow.png)

Die Journey beginnt mit dem Erlernen des Anwendungsfalls:

Eine Website bietet eine Reihe von Produkten für verschiedene Kunden. Kunden durchsuchen das Portal, wählen die Produkte aus und bestellen sie. Jeder Kunde erstellt ein Konto und stellt Versand- und Rechnungsadressen bereit. Eine bestehende Kundin, Sara Rose, möchte ihre Versandadresse zur Website hinzufügen. Die Website bietet ein Online-Formular zum Hinzufügen und Aktualisieren von Versandadressen.

Die Website wird mit Adobe Experience Manager (AEM) ausgeführt und verwendet AEM [!DNL Forms] für die Erfassung und Verarbeitung von Daten. Das Formular zum Hinzufügen und Aktualisieren von Adressen ist ein adaptives Formular. Die Website speichert Kundendetails in einer Datenbank. Das Formular zum Hinzufügen und Aktualisieren von Adressen dient dazu, verfügbare Adressen abzurufen und anzuzeigen. Sie verwenden auch das adaptive Formular, um aktualisierte und neue Adressen zu akzeptieren.

### Voraussetzung {#prerequisite}

* Einrichten einer [AEM-Autoreninstanz](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=de#author-and-publish-installs)
* Installieren Sie das [AEM Forms-Add-On](../../forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz.
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Die Beispiele im Tutorial basieren auf einer [!DNL MySQL]-Datenbank und verwenden [!DNL Oracle's] [MySQL JDBC-Datenbanktreiber](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Richten Sie eine Datenbank mit Kundendaten mit den unten angezeigten Feldern ein. Eine Datenbank ist nicht erforderlich, um ein adaptives Formular zu erstellen. In diesem Tutorial wird eine Datenbank zur Demonstration der Formulardatenmodell- und Persistenzfunktionen von AEM [!DNL Forms] verwendet.

![adaptiveformdata](assets/adaptiveformdata.png)

## Schritt 1: Erstellen Sie ein adaptives Formular {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Adaptive Formulare sind neue Generationen, ansprechend, responsiv, dynamisch und adaptiv. Mit adaptiven Formularen können Sie personalisierte und zielgerichtete Erlebnisse bereitstellen. AEM [!DNL Forms] bietet einen Drag-and-Drop-WYSIWYG-Editor zum Erstellen von adaptiven Formularen. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung in das Authoring adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

Ziele:

* Erstellen eines adaptiven Formulars, mit dem ein Kunde eine Versandadresse hinzufügen kann
* Layout-Felder eines adaptiven Formulars zum Anzeigen und Akzeptieren von Informationen eines Kunden
* Erstellen Sie eine Sendeaktion zum Senden einer E-Mail mit Formularinhalt
* Anzeigen und Senden eines adaptiven Formulars in der Vorschau

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-adaptive-form.md)

## Schritt 2: Erstellen Sie ein Formulardatenmodell {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Ein Formulardatenmodell ermöglicht die Verbindung eines adaptiven Formulars mit unterschiedlichen Datenquellen. Zum Beispiel AEM Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datendarstellungsschema von Geschäftsentitäten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einem adaptiven Formular verwenden, um Daten abzurufen, zu aktualisieren, zu löschen und zu verbundenen Datenquellen hinzuzufügen.

Ziele:

* Konfigurieren der Datenbankinstanz der Website ([!DNL MySQL]-Datenbank) als Datenquelle
* Erstellen des Formulardatenmodells mithilfe der [!DNL MySQL]-Datenbank als Datenquelle
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-form-data-model.md)

## Schritt 3: Wenden Sie Regeln auf adaptive Formularfelder an {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Adaptive Formulare stellen einen Editor zum Schreiben von Regeln für adaptive Formularobjekte bereit. Diese Regeln definieren Aktionen für Formularobjekte, die durch voreingestellte Bedingungen, Benutzereingaben und Benutzeraktionen im Formular ausgelöst werden. Dies hilft, die Genauigkeit zu gewährleisten, und beschleunigt das Ausfüllen der Formulare.

Ziele:

* Erstellen und Anwenden von Regeln auf adaptive Formularfelder
* Verwenden Sie Regeln zum Auslösen von Formulardatenmodelldiensten, um Daten in der Datenbank zu aktualisieren 

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](apply-rules-to-adaptive-form-fields.md)

## Schritt 4: Gestalten Sie Ihr adaptives Formular {#step-style-your-adaptive-form}

![adaptive-form-styling](/help/forms/using/assets/09-style-your-adaptive-form-small.png)

Adaptive Formulare bieten Designs und einen [Editor](../../forms/using/themes.md), um Designs für die adaptiven Formulare zu erstellen. Ein Design enthält Stildetails für Komponenten und Bereiche und Sie können ein Design in verschiedenen Formularen wiederverwenden. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz, Ausrichtung und Größe. Wenn Sie das Design auf Ihr Formular anwenden, spiegelt der angegebene Stil die entsprechenden Komponenten des Formulars wider. Adaptive Formulare unterstützen auch die Inline-Formatierung für Formularstile.

Ziele:

* Anwenden eines Standarddesigns auf ein adaptives Formular
* Erstellen eines Designs für ein adaptives Formular mit dem Design-Editor
* Verwenden von Webfonts in einem benutzerdefinierten Design

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Schritt 5: Veröffentlichen Sie Ihr adaptives Formular {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Sie können adaptive Formulare als eigenständiges Formular (Einzelseitenprogramm) veröffentlichen, in eine AEM [Sites-Seite](/help/forms/using/embed-adaptive-form-aem-sites.md) einbinden oder mithilfe des [Formularportals](../../forms/using/introduction-publishing-forms.md) in einer AEM-[!DNL Site] auflisten.

Ziele:

* Veröffentlichen des adaptiven Formulars als AEM-Seite
* Einbetten des adaptiven Formulars in eine AEM [!DNL Sites]-Seite
* Einbetten des adaptiven Formulars in eine externe Web-Seite (eine außerhalb von AEM gehostete, nicht zu AEM gehörende Web-Seite)

[![Siehe Handbuch](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](publish-your-adaptive-form.md)
