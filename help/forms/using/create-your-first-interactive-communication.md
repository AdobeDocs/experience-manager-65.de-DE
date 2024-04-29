---
title: 'Tutorial: Erstellen Sie Ihre erste interaktive Kommunikation'
description: Erfahren Sie, wie Sie Ihre erste interaktive Kommunikation erstellen.
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications, introduction
feature: Interactive Communication
exl-id: b20bb719-5686-466e-8dde-279b8471bfe3
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '976'
ht-degree: 100%

---

# Tutorial: Erstellen Sie Ihre erste interaktive Kommunikation {#tutorial-create-your-first-interactive-communication}

Erfahren Sie, wie Sie Ihre erste interaktive Kommunikation erstellen.

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

Durch interaktive Kommunikation lassen sich die Erstellung, Zusammenstellung und Bereitstellung von sicheren, personalisierten und interaktiven Korrespondenzen wie Geschäftskorrespondenz, Dokumenten, Aufstellungen, Marketing-Mails, Rechnungen und Willkommens-Sets zentralisieren und verwalten. Die interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: den Druckkanal und den Web-Kanal. Der Druckkanal wird zum Erstellen von PDF-Dokumenten und papierbasierter Kommunikation verwendet, der Web-Kanal hingegen zum Bereitstellen von Online-Erlebnissen.

Dieses Tutorial bietet ein End-to-End-Framework zum Erstellen einer interaktiven Kommunikation. Das Tutorial ist in einen Anwendungsfall und mehrere Handbücher unterteilt. Jedes Handbuch enthält dabei Informationen zum Erstellen von Funktionen, die als Bausteine für eine interaktive Kommunikation dienen.

Die folgende Abbildung zeigt die Bausteine, die zum Erstellen einer interaktiven Kommunikation erforderlich sind.

![ Workflow](assets/workflow.gif)

Am Ende dieses Tutorials können Sie Folgendes:

* Erstellen von Bausteinen (Formulardatenmodell, Dokumentfragmente und Vorlagen)
* Erstellen einer interaktiven Kommunikation
* Testen und Veröffentlichen einer interaktiven Kommunikation

## Nutzungsszenario {#use-case}

Das Ganze beginnt mit dem Kennenlernen des Anwendungsfalls:

Ein Telekommunikationsanbieter sendet monatliche Rechnungen per E-Mail an seine Kundinnen und Kunden. Bei diesen Rechnungen handelt es sich um eine interaktive Kommunikation. Die entsprechenden E-Mails enthalten Folgendes:

* eine kennwortgeschützte PDF, in diesem Tutorial als Druckkanal bezeichnet. Diese enthält Kundendetails, Rechnungsdetails, eine Übersicht der Gebühren, bequeme Zahlungsmodi für die Rechnung und Nutzungsdetails.
* einen Link zur Web-Version der Rechnung, in diesem Tutorial als Web-Kanal bezeichnet. Die Webversion der Rechnung bietet zusätzlich zu den Details in der PDF-Version eine grafische Darstellung der Nutzungsdetails und personalisierter Angebote auf Basis von Adobe Target. Die Web-Version enthält auch ein Online-Zahlungsformular. So können Online-Zahlungen getätigt werden, ohne die interaktive Kommunikation zu verlassen.
* einen Link zu Mehrwert-Services wie Online-Speicher, Musikabonnements und Videoabonnements auf Abruf.

## Voraussetzungen {#prerequisites}

* Richten Sie eine AEM-Author-Instanz ein.
* Installieren Sie das [AEM Forms-Add-On](/help/forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz
* Richten Sie die MYSQL-Datenbank ein
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Die Beispiele in diesem Tutorial basieren auf der MySQL-Datenbank und verwenden den [MySQL JDBC-Datenbanktreiber von Oracle](https://dev.mysql.com/downloads/connector/j/5.1.html).

## Schritt 1: Planen Sie die interaktive Kommunikation {#step-plan-the-interactive-communication}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Der erste Schritt bei der Planung einer interaktiven Kommunikation besteht darin, den Inhalt der interaktiven Kommunikation fertigzustellen. Anschließend müssen Sie den Inhalt analysieren, um die verschiedenen Asset-Typen zu ermitteln, die zum Erstellen der interaktiven Kommunikation erforderlich sind.

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

Mit einem Formulardatenmodell können Sie eine interaktive Kommunikation mit unterschiedlichen Datenquellen verbinden, z. B. mit AEM-Benutzerprofilen, RESTful-Web-Diensten, SOAP-basierten Web-Diensten, OData-Diensten und relationalen Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einer interaktiven Kommunikation verwenden, um Daten aus verbundenen Datenquellen abzurufen. Weitere Informationen zum Formulardatenmodell finden Sie unter [AEM Forms-Datenintegration](/help/forms/using/data-integration.md).

**Ziele:**

* Konfigurieren der Datenbankinstanz (MySQL-Datenbank) als eine Datenquelle
* Erstellen des Formulardatenmodells mithilfe der MySQL-Datenbank als Datenquelle
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Erstellen von Verknüpfungen zwischen den Datenmodellobjekten
* Anzeigen automatisch generierter Beispieldaten
* Beispieldaten bearbeiten
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

[](/help/forms/using/create-form-data-model0.md)

## Schritt 3: Erstellen Sie Dokumentfragmente {#step-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Dokumentfragmente sind wiederverwendbare Komponenten einer Korrespondenz, die zum Erstellen einer interaktiven Kommunikation verwendet werden. Dokumentfragmente sind vom Typ „Text“, „Liste“ und „Bedingung“.

**Ziele:**

* Erstellen von Dokumentfragmenten
* Erstellen von Variablen
* Erstellen und Anwenden von Regeln

[](/help/forms/using/create-document-fragments.md)

## Schritt 4: Erstellen Sie Vorlagen {#step-create-templates}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Für eine interaktive Kommunikation müssen auf dem AEM-Server Vorlagen für Druck- und Web-Kanäle verfügbar sein.

Die Vorlagen für den Druckkanal werden in Adobe Forms Designer erstellt und auf den AEM-Server hochgeladen. Diese Vorlagen stehen dann zur Verfügung, wenn Sie eine interaktive Kommunikation erstellen.

Die Vorlagen für den Web-Kanal werden in AEM erstellt. Autorinnen und Autoren sowie Administratorinnen und Administratoren von Vorlagen können Web-Vorlagen erstellen, bearbeiten und aktivieren. Nach ihrer Erstellung und Aktivierung stehen diese Vorlagen zur Verfügung, wenn Sie eine interaktive Kommunikation erstellen.

**Ziele:**

* Erstellen von XDP-Vorlagen für den Druckkanal mit Adobe Forms Designer
* Hochladen der XDP-Vorlagen auf den AEM Forms-Server
* Erstellen und Aktivieren von Vorlagen für den Web-Kanal

[](/help/forms/using/create-templates-print-web.md)

## Schritt 5: Erstellen Sie interaktive Kommunikation {#step-create-an-interactive-communication}

![09-style-your-adaptive-form-small](assets/09-style-your-adaptive-form-small.png)

Nachdem Sie alle Bausteine wie Formulardatenmodell, Dokumentfragmente und Vorlagen für die Web-Version erstellt haben, können Sie mit der Erstellung einer interaktiven Kommunikation beginnen.

Eine interaktive Kommunikation kann über zwei Kanäle bereitgestellt werden: den Druckkanal und den Web-Kanal. Sie können auch eine interaktive Kommunikation mit dem Druckkanal als Primär erstellen. Die Option zum Drucken als Primär für den Web-Kanal stellt sicher, dass Inhalt, Vererbung und Datenbindung des Web-Kanals vom Druckkanal abgeleitet werden.

**Ziele:**

* Erstellen einer interaktiven Kommunikation für den Druckkanal
* Erstellen einer interaktiven Kommunikation für den Web-Kanal
* Erstellen einer interaktiven Kommunikation für den Druck- und Web-Kanal mit der Option zum Drucken als Primär
* Erstellen einer dynamischen Tabelle in der Web-Version der interaktiven Kommunikation
* Erstellen eines Diagramms in der Web-Version der interaktiven Kommunikation
* Erstellen von Hyperlinks in der Web-Version von interaktiver Kommunikation

[](/help/forms/using/create-interactive-communication0.md)

## Schritt 6: Veröffentlichen Sie Ihre interaktive Kommunikation {#step-publish-your-interactive-communication}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Wenn Sie eine interaktive Kommunikation mit Druck- und Web-Kanälen erstellt und getestet haben, können Sie diese Assets veröffentlichen. Der in diesem Tutorial beschriebene Anwendungsfall konzentriert sich auf die Integration dieser Assets in einen E-Mail-Client. Der E-Mail-Client dient als Brücke, um die interaktive Kommunikation an mehrere E-Mail-Adressen zu senden.

**Ziele:**

* Integrieren der interaktiven Kommunikation in einem E-Mail-Client zum Kommunikationsversand an Kundinnen und Kunden
* Anfügen eines PDF-Dokuments als Anhang (interaktive Kommunikation, die im Druckkanal erstellt wurde)
* Einschließen eines Links zur Web-Version der interaktiven Kommunikation
