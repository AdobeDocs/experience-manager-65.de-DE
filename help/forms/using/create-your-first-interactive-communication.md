---
title: 'Tutorial: Erstellen Sie Ihre erste interaktive Kommunikation'
description: Erfahren Sie, wie Sie Ihre erste interaktive Kommunikation erstellen.
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications, introduction
feature: Interactive Communication
exl-id: b20bb719-5686-466e-8dde-279b8471bfe3
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 27%

---

# Tutorial: Erstellen Sie Ihre erste interaktive Kommunikation {#tutorial-create-your-first-interactive-communication}

Erfahren Sie, wie Sie Ihre erste interaktive Kommunikation erstellen.

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

Interaktive Kommunikation zentralisiert und verwaltet die Erstellung, Zusammenstellung und Bereitstellung sicherer, personalisierter und interaktiver Schriftstücke wie Geschäftskorrespondenz, Dokumente, Mitteilungen, Marketing-E-Mails, Rechnungen und Willkommenskits. Interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: Druck und Web. Der Druckkanal wird verwendet, um PDF- und Papiernachrichten zu erstellen, während der Webkanal zur Bereitstellung von Online-Erlebnissen verwendet wird.

Dieses Tutorial bietet ein End-to-End-Framework zum Erstellen einer interaktiven Kommunikation. Das Tutorial ist in einen Anwendungsfall und mehrere Handbücher unterteilt. Jedes Handbuch hilft Ihnen beim Erstellen von Funktionen, die als Bausteine für die Erstellung einer interaktiven Kommunikation verwendet werden.

Die folgende Abbildung zeigt die Bausteine, die zum Erstellen einer interaktiven Kommunikation erforderlich sind.

![ Workflow](assets/workflow.gif)

Am Ende dieses Tutorials können Sie Folgendes:

* Erstellen von Bausteinen (Formulardatenmodell, Dokumentfragmente und Vorlagen)
* Erstellen einer interaktiven Kommunikation
* Interaktive Kommunikation testen und veröffentlichen

## Nutzungsszenario {#use-case}

Die Journey beginnt mit dem Erlernen des Anwendungsfalls:

Ein Telekommunikationsbetreiber sendet monatliche Rechnungen an die Kunden über die E-Mail. Die Rechnung ist eine interaktive Kommunikation. Die E-Mail enthält:

* Eine kennwortgeschützte PDF, in diesem Tutorial als Druckkanal bezeichnet. Es enthält Kundendetails, Rechnungsdetails, Zusammenfassung der Gebühren, bequeme Zahlungsmodi der Rechnung und Nutzungsdetails.
* Ein Link zur Webversion der Rechnung, in diesem Tutorial als Webkanal bezeichnet. Die Webversion der Rechnung bietet zusätzlich zu den Details in der PDF-Version eine grafische Darstellung der Nutzungsdetails und personalisierter Angebote auf Basis von Adobe Target. Die Web-Version enthält auch ein Online-Zahlungsformular. Es hilft, Online-Zahlungen zu tätigen, ohne die IC zu verlassen.
* Ein Link zu Mehrwertdiensten wie Online-Speicher, Musikabonnements und On-Demand-Videoabonnements.

## Voraussetzungen {#prerequisites}

* Richten Sie eine AEM-Author-Instanz ein.
* Installieren Sie das [AEM Forms-Add-On](/help/forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz
* Richten Sie die MYSQL-Datenbank ein
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Die Beispiele in diesem Tutorial basieren auf der MySQL-Datenbank und verwenden den [MySQL JDBC-Datenbanktreiber von Oracle](https://dev.mysql.com/downloads/connector/j/5.1.html).

## Schritt 1: Planen Sie die interaktive Kommunikation {#step-plan-the-interactive-communication}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Der erste Schritt bei der Planung einer interaktiven Kommunikation besteht darin, den Inhalt der interaktiven Kommunikation fertigzustellen. Nach Abschluss des Inhalts müssen Sie ihn analysieren, um die verschiedenen Asset-Typen zu identifizieren, die zum Erstellen der interaktiven Kommunikation erforderlich sind.

**Ziele:**

So erstellen Sie eine Anatomie für die interaktive Kommunikation mit den folgenden Arten der Dateneingabe:

* Statischer Text
* Formulardatenmodell
* Agent-Benutzeroberfläche
* Bedingte Daten
* Bilder

[](/help/forms/using/planning-interactive-communications.md)

## Schritt 2: Erstellen eines Formulardatenmodells {#step-create-form-data-model}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Mit einem Formulardatenmodell können Sie eine interaktive Kommunikation mit unterschiedlichen Datenquellen verbinden. Zum Beispiel AEM Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datendarstellungsschema von Geschäftsentitäten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einer interaktiven Kommunikation verwenden, um Daten aus verbundenen Datenquellen abzurufen. Weitere Informationen zum Formulardatenmodell finden Sie unter [AEM Forms-Datenintegration](/help/forms/using/data-integration.md).

**Ziele:**

* Konfigurieren der Datenbankinstanz (MySQL-Datenbank) als eine Datenquelle
* Formulardatenmodell mit MySQL-Datenbank als Datenquelle erstellen
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Erstellen von Verknüpfungen zwischen Datenmodellobjekten
* Automatisch generierte Beispieldaten anzeigen
* Beispieldaten bearbeiten
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

[](/help/forms/using/create-form-data-model0.md)

## Schritt 3: Erstellen Sie Dokumentfragmente {#step-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Dokumentfragmente sind wiederverwendbare Komponenten einer Korrespondenz, die zum Erstellen einer interaktiven Kommunikation verwendet werden. Die Dokumentfragmente weisen die folgenden Typen auf: Text, Liste und Bedingung.

**Ziele:**

* Dokumentfragmente erstellen
* Erstellen von Variablen
* Regeln erstellen und anwenden

[](/help/forms/using/create-document-fragments.md)

## Schritt 4: Erstellen Sie Vorlagen {#step-create-templates}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Um eine interaktive Kommunikation zu erstellen, müssen auf dem AEM-Server Vorlagen für Druck- und Webkanäle verfügbar sein.

Die Vorlagen für den Druckkanal werden in Adobe Forms Designer erstellt und auf den AEM hochgeladen. Diese Vorlagen können dann beim Erstellen einer interaktiven Kommunikation verwendet werden.

Die Vorlagen für den Webkanal werden in AEM erstellt. Vorlagenautoren und -administratoren können Webvorlagen erstellen, bearbeiten und aktivieren. Nach der Erstellung und Aktivierung sind diese Vorlagen zur Verwendung beim Erstellen einer interaktiven Kommunikation verfügbar.

**Ziele:**

* Erstellen von XDP-Vorlagen für den Druckkanal mit Adobe Forms Designer
* Hochladen der XDP-Vorlagen auf den AEM Forms-Server
* Erstellen und Aktivieren von Vorlagen für den Webkanal

[](/help/forms/using/create-templates-print-web.md)

## Schritt 5: Erstellen Sie interaktive Kommunikation {#step-create-an-interactive-communication}

![09-style-your-adaptive-form-small](assets/09-style-your-adaptive-form-small.png)

Nachdem Sie alle Bausteine wie Formulardatenmodell, Dokumentfragmente und Vorlagen für die Webversion erstellt haben, können Sie mit der Erstellung einer interaktiven Kommunikation beginnen.

Interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: Druck und Web. Sie können auch eine interaktive Kommunikation mit dem Druckkanal als Master erstellen. Die Option &quot;Als Master drucken&quot;für den Webkanal stellt sicher, dass der Inhalt, die Vererbung und die Datenbindung des Webkanals vom Druckkanal abgeleitet werden.

**Ziele:**

* Erstellen der interaktiven Kommunikation für den Druckkanal
* Erstellen der interaktiven Kommunikation für den Webkanal
* Erstellen Sie Print- und Web-interaktive Kommunikation mit Print als Master.
* Erstellen einer dynamischen Tabelle in der Webversion der interaktiven Kommunikation
* Erstellen eines Diagramms in der Webversion der interaktiven Kommunikation
* Erstellen von Hyperlinks in der Web-Version von interaktiver Kommunikation

[](/help/forms/using/create-interactive-communication0.md)

## Schritt 6: Veröffentlichen Sie Ihre interaktive Kommunikation {#step-publish-your-interactive-communication}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Nachdem Sie interaktive Kommunikation mit Druck- und Webkanälen erstellt und getestet haben, können Sie diese Assets veröffentlichen. Der in diesem Tutorial beschriebene Anwendungsfall konzentriert sich auf die Integration dieser Assets in einen E-Mail-Client. Der E-Mail-Client dient als Brücke zum Senden der interaktiven Kommunikation an mehrere E-Mail-Adressen.

**Ziele:**

* Integrieren Sie interaktive Kommunikation mit einem E-Mail-Client, um eine Kommunikation an die Kunden senden zu können.
* Ein PDF-Dokument als Anhang einschließen (interaktive Kommunikation, die im Druckkanal erstellt wurde)
* Einen Link zur Webversion der interaktiven Kommunikation einschließen
