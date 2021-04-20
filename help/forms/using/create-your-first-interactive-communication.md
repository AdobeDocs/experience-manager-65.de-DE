---
title: Übung - Erste interaktive Kommunikation erstellen
seo-title: Erstellen Sie Ihre erste interaktive Kommunikation
description: Erfahren Sie, wie Sie Ihre erste interaktive Kommunikation erstellen.
seo-description: Erfahren Sie, wie Sie Ihre erste interaktive Kommunikation erstellen.
uuid: ed5003c6-ba3a-4fcb-8645-c7b607b22fb5
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications, introduction
discoiquuid: 954da8da-a30b-477d-bde7-3edd86a5be11
feature: Interactive Communication
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 91%

---


# Tutorial: Erstellen Sie Ihre erste interaktive Kommunikation {#tutorial-create-your-first-interactive-communication}

Erfahren Sie, wie Sie Ihre erste interaktive Kommunikation erstellen.

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

Interaktive Kommunikation zentralisiert und verwaltet die Erstellung, Anordnung und Bereitstellung von sicheren, personalisierten und interaktiven Korrespondenzen wie Geschäftskorrespondenz, Dokumente, Kontoauszüge, Dokumente, Auszüge, Marketing-Mails, Rechnungen und Begrüßungssets. Interaktive Kommunikation kann über zwei Kanäle erfolgen: Druck und Web. Der Druckkanal wird zum Erstellen von PDFs und zur Kommunikation auf Papier verwendet, während der Webkanal zur Bereitstellung von Online-Erlebnissen verwendet wird.

Diese Schulung bietet ein End-to-End-Framework zum Erstellen einer interaktiven Kommunikation. Die Schulung ist in einen Anwendungsfall und mehrere Leitfäden unterteilt. Mit jedem Handbuch können Sie Features erstellen, die als Bausteine &#x200B;&#x200B;für die Erstellung einer interaktiven Kommunikation verwendet werden.

Die folgende Abbildung zeigt die Bausteine, die zum Erstellen einer interaktiven Kommunikation erforderlich sind.

![ Workflow](assets/workflow.gif)

Am Ende dieser Schulung können Sie Folgendes:

* Erstellen von Bausteinen (Formulardatenmodell, Dokumentfragmente und Vorlagen)
* Erstellen einer interaktiven Kommunikation
* Testen und veröffentlichen Sie eine interaktive Kommunikation

## Anwendungsfall {#use-case}

Die Reise beginnt mit dem Erlernen des Anwendungsfalls:

Ein Telekommunikationsbetreiber sendet monatliche Rechnungen über die E-Mail an die Kunden. Die Rechnung ist eine interaktive Kommunikation. Die E-Mail enthält Folgendes:

* Eine kennwortgeschützte PDF-Datei, in diesem Tutorial als Druckkanal bezeichnet. Sie enthält Kundendaten, Rechnungsdetails, eine Zusammenfassung der Gebühren, praktische Zahlungsmodi und Verwendungsdetails.
* Ein Link zur Webversion der Rechnung, in diesem Tutorial als Webkanal bezeichnet. Die Webversion der Rechnung bietet zusätzlich zu den Details in der PDF-Version eine grafische Darstellung der Nutzungsdetails und personalisierter Angebote auf Basis von Adobe Target. Die Webversion enthält auch ein Online-Zahlungsformular. Online-Zahlungen werden dadurch erleichtert, ohne die IK zu verlassen.
* Ein Link zu Mehrwert-Services wie Online-Speicher, Musikabonnements und Videoabonnements auf Abruf.

## Voraussetzungen {#prerequisites}

* Richten Sie eine AEM-Author-Instanz ein.
* Installieren Sie das [AEM Forms-Add-On](/help/forms/using/installing-configuring-aem-forms-osgi.md) auf der Author-Instanz
* Richten Sie die MYSQL-Datenbank ein
* Beziehen Sie den JDBC-Datenbanktreiber (JAR-Datei) vom Datenbankanbieter. Beispiele im Tutorial basieren auf der MySQL-Datenbank und verwenden Sie Oracle [MySQL JDBC-Datenbanktreiber](https://dev.mysql.com/downloads/connector/j/5.1.html).

## Schritt 1: Planen Sie die interaktive Kommunikation {#step-plan-the-interactive-communication}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Der erste Schritt bei der Planung einer interaktiven Kommunikation besteht darin, den Inhalt der interaktiven Kommunikation abzuschließen. Nachdem der Inhalt abgeschlossen ist, müssen Sie ihn analysieren, um die verschiedenen Asset-Typen zu ermitteln, die zum Erstellen der interaktiven Kommunikation erforderlich sind.

**Ziele:**

So erstellen Sie eine Anatomie für die interaktive Kommunikation mit den folgenden Eingabemodi:

* Statischer Text
* Formulardatenmodell
* Agent-Benutzeroberfläche
* Bedingte Daten
* Bilder

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](/help/forms/using/planning-interactive-communications.md)

## Schritt 2: Erstellen eines Formulardatenmodells {#step-create-form-data-model}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Ein Formulardatenmodell ermöglicht es, eine interaktive Kommunikation mit unterschiedlichen Datenquellen zu verbinden. Zum Beispiel AEM-Benutzerprofil, RESTful-Webdienste, SOAP-basierte Webdienste, OData-Dienste und relationale Datenbanken. Ein Formulardatenmodell ist ein einheitliches Datenrepräsentationsschema von Geschäftseinheiten und Diensten, die in verbundenen Datenquellen verfügbar sind. Sie können das Formulardatenmodell mit einer interaktiven Kommunikation verwenden, um Daten aus verbundenen Datenquellen abzurufen. Weitere Informationen zum Formulardatenmodell finden Sie unter [AEM Forms Data Integration](/help/forms/using/data-integration.md).

**Ziele:**

* Konfigurieren der Datenbankinstanz (MySQL-Datenbank) als eine Datenquelle
* Erstellen des Formulardatenmodells mithilfe der MySQL-Datenbank als Datenquelle
* Hinzufügen von Datenmodellobjekten zum Datenmodell
* Konfigurieren der Lese- und Schreibdienste für Datenmodellobjekte
* Erstellen Sie Verknüpfungen zwischen den Datenmodellobjekten
* Automatisch generierte Beispieldaten anzeigen
* Beispieldaten bearbeiten
* Testen des Formulardatenmodells und der konfigurierten Dienste mit Testdaten

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-form-data-model0.md)

## Schritt 3: Erstellen Sie Dokumentfragmente {#step-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Dokumentfragmente sind wiederverwendbare Komponenten einer Korrespondenz, die zum Erstellen einer interaktiven Kommunikation verwendet werden. Die Dokumentfragmente sind: Text, Liste und Bedingung.

**Ziele:**

* Erstellen Sie Dokumentfragmente
* Variablen erstellen
* Regeln erstellen und anwenden

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-document-fragments.md)

## Schritt 4: Erstellen Sie Vorlagen {#step-create-templates}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Um eine interaktive Kommunikation zu erstellen, müssen auf dem AEM-Server Vorlagen für Druck- und Webkanäle verfügbar sein.

Die Vorlagen für den Druckkanal werden in Adobe Forms Designer erstellt und auf den AEM-Server hochgeladen. Diese Vorlagen stehen dann zur Verfügung, während Sie eine interaktive Kommunikation erstellen.

Die Vorlagen für den Webkanal werden in AEM erstellt. Vorlagenautoren und Administratoren können Webvorlagen erstellen, bearbeiten und aktivieren. Nachdem sie erstellt und aktiviert wurden, stehen diese Vorlagen zur Verfügung, während Sie eine interaktive Kommunikation erstellen.

**Ziele:**

* Erstellen Sie XDP-Vorlagen für den Druckkanal mit Adobe Forms Designer
* Laden Sie die XDP-Vorlagen auf den AEM Forms Server hoch
* Erstellen und aktivieren Sie Vorlagen für den Webkanal

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-templates-print-web.md)

## Schritt 5: Erstellen Sie interaktive Kommunikation {#step-create-an-interactive-communication}

![09-style-your-adaptive-form-small](assets/09-style-your-adaptive-form-small.png)

Nachdem Sie alle Bausteine &#x200B;&#x200B;wie Formulardatenmodell, Dokumentfragmente und Vorlagen für die Webversion erstellt haben, können Sie mit der Erstellung einer interaktiven Kommunikation beginnen.

Interaktive Kommunikation kann über zwei Kanäle erfolgen: Druck und Web. Sie können auch eine interaktive Kommunikation mit dem Druckkanal als Master erstellen. Druck als Master-Option für Webkanal stellt sicher, dass Inhalt, Vererbung und Datenbindung des Webkanals vom Druckkanal abgeleitet werden.

**Ziele:**

* Erstellen Sie interaktive Kommunikation für den Druckkanal
* Erstellen Sie interaktive Kommunikation für den Webkanal
* Erstellen Sie interaktive Kommunikation für den Druck- und Webkanal mit Druck als Master
* Erstellen Sie eine dynamische Tabelle in der Webversion der interaktiven Kommunikation
* Erstellen Sie ein Diagramm in der Webversion der interaktiven Kommunikation
* Erstellen von Hyperlinks in der Webversion der interaktiven Kommunikation

   [ ![see-the-guide-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-interactive-communication0.md)

## Schritt 6: Testen Sie Ihre interaktive Kommunikation {#step-test-your-interactive-communication}

![11-test-your-adaptive-form](assets/11-test-your-adaptive-form.png)

Nachdem Sie eine interaktive Kommunikation erstellt haben, ist es wichtig, dass Sie jede Änderung testen, die Sie daran vornehmen. Das Testen aller Bereiche einer interaktiven Kommunikation ist mühsam. AEM Forms bietet ein SDK (Calvin SDK) zum automatischen Testen von adaptiven Formularen.

**Ziele:**

* Erstellen Sie eine Testreihe
* Erstellen Sie Testfälle
* Führen Sie die Testfälle aus

## Schritt 7: Veröffentlichen Sie Ihre interaktive Kommunikation {#step-publish-your-interactive-communication}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Wenn Sie interaktive Kommunikation mit Druck- und Webkanälen erstellt und getestet haben, können Sie diese Assets veröffentlichen. Der in diesem Tutorial beschriebene Anwendungsfall konzentriert sich auf die Integration dieser Assets in einen E-Mail-Client. Der E-Mail-Client dient als Brücke, um die interaktive Kommunikation an mehrere E-Mail-Adressen zu senden.

**Ziele:**

* Integrieren Sie interaktive Kommunikation in einen E-Mail-Client, um eine Mitteilung an die Kunden senden zu können
* Fügen Sie ein PDF-Dokument als Anhang ein (interaktive Kommunikation, die im Druckkanal erstellt wurde)
* Fügen Sie einen Link zur Webversion der interaktiven Kommunikation hinzu

