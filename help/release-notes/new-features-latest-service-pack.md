---
title: Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 4
description: Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 4
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: da9d682a0392e5de8e012e254fb82bd15547a542

---


# Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 4 {#aem-whats-new-service-pack-4}

Adobe Experience Manager (AEM) 6.5 bietet Funktionen und kontinuierliche Verbesserungen durch vierteljährliche Service Packs. Der neue Ansatz kommt unseren Kunden zugute, wenn sie die Innovationen schneller umsetzen.

Das neueste AEM Service Pack 4 (6.5.4.0) wird am 5. **März 2020** veröffentlicht. In diesem Artikel werden die Funktionen der neuesten Service Pack-Angebot vorgestellt, mit denen Sie Ihre AEM-Reise noch bereichern können.

## AEM Sites {#aem-sites}

AEM 6.5.4.0 enthält Verbesserungen am Stilsystem. Sie können jetzt Stile im Komponentendialogfeld auswählen.

### Leistungsverbesserungen in verschiedenen Bereichen {#performance-improvements}

* Verkürzte Ladezeit und Initialisierung von ContextHub innerhalb einer Site (`contexthub.kernel.js`). Das führt zu schnelleren Seitenladevorgängen während eines Site-Besuchs.

* Die Zeit zum Aktualisieren einer Seite nach dem Ziehen von Erlebnisfragmenten in den Seiten-Editor der Sites wurde verringert.

* Die Ladezeit für Einträge auf einer Seite &quot;Sites&quot;mit mehr als 200 Live-Kopien in der Übersicht über **[!UICONTROL Live Copy wurde verkürzt]**.

* Verbesserte Verarbeitung von unvollständigen oder ungültigen URLs. Solche URLs können den Vorlageneditor verlangsamen.

## AEM Assets {#aem-assets}

### Konfigurieren von AEM Assets mit Brand Portal {#configure-assets-bp}

Der Kanal für die Autorisierung zwischen AEM Assets und Brand Portal wurde geändert. Zuvor wurde Brand Portal über das Legacy-OAuth-Gateway in der klassischen Benutzeroberfläche konfiguriert. Das Gateway ruft mithilfe des JWT-Token-Austauschs ein IMS-Zugriffstoken zur Autorisierung ab. AEM Assets wird jetzt über Adobe I/O in Brand Portal konfiguriert. Die Konsole ruft das IMS-Token zur Authentifizierung Ihres Brand Portal-Mandanten ab.

Die Schritte zum Konfigurieren von AEM Assets mit Brand Portal unterscheiden sich je nach Ihrer AEM-Version und davon, ob Sie zum ersten Mal eine Konfiguration durchführen oder die vorhandenen Konfigurationen aktualisieren. See [Configure AEM Assets with Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html) for details.


### Accessibility enhancements {#accessibility-enhancements}

Experience Manager Assets umfasst die folgenden Verbesserungen der Barrierefreiheit:

* Mit den Pfeiltasten auf der Tastatur können Sie Bereiche innerhalb gezoomter Bilder verschieben und schwenken. Weitere Informationen finden Sie unter [Vorschau-Assets nur](../assets/managing-assets-touch-ui.md#previewing-assets)mit Tastaturbefehlen.

* Die Kontrollkästchen für gemischten Status (bei denen, sofern Sie nicht alle verschachtelten Kontrollkästchen auswählen, vorausgesagt, dass die Kontrollkästchen der ersten Ebene nicht ausgewählt sind und durchgestrichen werden) im Bedienfeld &quot;Filter&quot;sind für Bildschirmlesehilfen lesbar.

* Datums- und Uhrzeitformateinschränkungen werden in den Feldbezeichnungen der Datumsfelder bereitgestellt, damit die Benutzer das Datum mit der Tastatur im korrekten Format eingeben können.

   Beispiel: `On Time (MM-DD-YYYY HH:mm)`. Hier ist MM Monat im zweistelligen Format, JJJJ ist Jahr, TT ist Tag im zweistelligen Format, HH ist Stunde im 24-Stunden-Militärformat und mm ist Minute.

* Das `X` Symbol auf der Schaltfläche zum Entfernen der aktuell ausgewählten Tags wird jetzt von Bildschirmlesehilfen zusammen mit der Anzahl der ausgewählten Tags angekündigt.

## AEM Forms {#aem-forms}

### Generieren einer druckbaren Ausgabe in AEM Forms Workflows {#generate-printable-output}

Mit dem neuen Arbeitsablaufschritt &quot;Druckbare Ausgabe generieren&quot;können Sie eine Quellvorlagendatei in eine Datendatei integrieren. Mit dieser Integration können Sie verschiedene Kopien der Vorlagendatei drucken oder speichern. Beispielsweise können Sie ein Quellformular mit einem anderen Namen jedes Mal drucken, wenn es gedruckt wird. Speichern Sie die Namen in der Datendatei und integrieren Sie die Datendatei in eine Standardvorlagendatei. Weitere Informationen zu dieser Funktion finden Sie unter [Forms-zentrierter Arbeitsablauf auf OSGi - Schritt-Referenz](../forms/using/aem-forms-workflow-step-reference.md).

![Druckbare Ausgabe generieren](assets/generate-print-output-demo.gif)

### Unterstützung mehrerer Spalten für adaptive Formulare und interaktive Kommunikation im Layoutmodus {#multi-column-adaptive-forms}

Sie können jetzt die Anzahl der Spalten für ein Bedienfeld in adaptiven Formularen und in interaktiver Kommunikation definieren. Wechseln Sie zum Layoutmodus, um die neue Option für mehrere Spalten zu verwenden. Weitere Informationen finden Sie unter [Verwenden des Layoutmodus zum Ändern der Größe von Komponenten](../forms/using/resize-using-layout-mode.md).


![Mehrspaltiges Layout](assets/multi-column-layout.gif)



### AEM Inbox-Anpassungen {#aem-inbox}

Die neue Option &quot;Admin-Steuerung&quot;ermöglicht den Administratoren Folgendes:

* Anpassen von Kopfzeilentext und Logo

* Steuern der Anzeige der in der Kopfzeile verfügbaren Navigationslinks

Die Option &quot;Admin-Steuerung&quot;ist nur für die Mitglieder der Gruppe &quot;Administratoren&quot;oder &quot;Workflow-Administratoren&quot;sichtbar. Weitere Informationen zu dieser Funktion finden Sie unter [Ihr Posteingang](../sites-authoring/inbox.md).

### Rich-Text-Unterstützung in HTML5-Formularen {#rich-text-support}

Sie können jetzt ein Textfeld in einem XFA-Formular in ein Rich-Text-Feld konvertieren, wenn es in einem HTML5-Formular wiedergegeben wird. Daher zeigt das Textfeld eine Liste anderer Formatierungsoptionen in einem HTML5-Formular an. Weitere Informationen finden Sie unter [Entwerfen von Formularvorlagen für HTML5-Formulare](../forms/using/designing-form-template.md).

### Accessibility enhancements {#forms-accessibility-enhancements-6540}

Experience Manager Forms umfasst die folgenden Verbesserungen der Barrierefreiheit:

* Benutzer können den Fokus auf Registerkarten ohne Probleme für das Referenz-Design Ultramarine-Accessible eines adaptiven Formulars verschieben.

* Kontrollkästchen, Links, Datumsauswahl und Datumseingabefelder werden von Bildschirmlesehilfen korrekt in einem adaptiven Formular angekündigt.

* Jede Seite eines adaptiven Formulars enthält jetzt einen Titel und eine Hauptmarkenbeschriftung.

## Wichtige Funktionen früherer AEM 6.5 Service Packs

### Smart Imaging for Dynamic Media (6.5.3.0) {#smart-imaging}

Die intelligente Bildbearbeitung nutzt die einzigartigen Ansichtsmerkmale der einzelnen Benutzer, um automatisch die richtigen Bilder bereitzustellen, die für ihr Erlebnis optimiert wurden, was zu einer besseren Leistung und Interaktion führt. Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert in der letzten Sekunde abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. Siehe [Smart Imaging](../assets/imaging-faq.md).

### Visuelle Suche nach AEM Assets (6.5.2.0) {#visual-search}

Assets-Benutzer können nach visuell ähnlichen Bildern suchen. AEM zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. See [Visual search](../assets/search-assets.md).

### Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers (6.5.3.0) {#share-request-access}

Sie können Ihre Inbox-Elemente für andere Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente erhält, kann der Benutzer für freigegebene Elemente entsprechende Aktionen anfordern. Ebenso können Sie von anderen Benutzern den Zugriff auf Posteingangselemente anfordern. Siehe [Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers](../forms/using/configure-shared-queues-osgi.md).

### Konfigurieren Sie die Abwesenheitseinstellung für Ihre Posteingangselemente (6.5.3.0) {#configure-out-of-office}

Wenn Sie planen, abwesend zu sein, können Sie angeben, was mit Artikeln geschieht, die Ihnen für diesen Zeitraum zugewiesen wurden.
Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Sie können eine Standardperson festlegen, an die alle Elemente gesendet werden sollen. Siehe Abwesenheitseinstellungen [konfigurieren](../forms/using/configure-out-of-office-settings.md).

### Generieren mehrerer interaktiver Kommunikation mit der Batch-API (6.5.3.0) {#generate-multiple-ic}

Sie können die Stapel-API verwenden, um mehrere interaktive Mitteilungen aus einer Vorlage zu erstellen. Die Vorlage ist eine interaktive Kommunikation ohne Daten. Die Stapel-API kombiniert Daten mit einer Vorlage, um eine interaktive Kommunikation zu erzeugen. Die API ist bei der Massenproduktion interaktiver Kommunikation nützlich. Zum Beispiel Telefonrechnungen, Kreditkartenauszüge für mehrere Kunden. Siehe [Generieren mehrerer interaktiver Kommunikation mit der Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

## Wichtige Versionen seit AEM 6.5 SP3

Zwischen dem 12. Dezember 2019 und dem 5. März 2020 hat Adobe die folgenden Funktionen veröffentlicht, die außerhalb der AEM-Hauptversion verfügbar sind:

* AEM Cloud Manager 2020.1.0 und 2020.2.0

   Die Versionsupdates verbessern den Pipeline-Status und die Möglichkeit, Protokolle für verschiedene Schritte herunterzuladen. Weitere Informationen finden Sie unter:

   * [Cloud Manager 2020.1.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-1-0.html)


   * [Cloud Manager 2020.2.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-current.html)


* Aktualisierungen der AEM Cloud Manager-CLI

   Zu den Versionsupdates gehören die Automatisierung von Cloud Manager-Aufgaben mit dem Befehlszeilenwerkzeug. Siehe [GitHub](https://github.com/adobe/aio-cli-plugin-cloudmanager/releases).

* AEM-Sites: Projektarchiv 23

   Die beste Möglichkeit zum Beginn eines neuen AEM-Projekts. Archetype 23 führt den [Projektarchiv für SPA und reguläre Sites zu einem](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-23) und stellt ein Standarddesign zur Verfügung, um Ihre Front-End-Entwicklung voranzutreiben.

* AEM-Sites: WKND-Referenz-Website

   [Neues Referenzprojekt](https://www.wknd.site/) mit Best Practices zum Erstellen von Sites mit AEM. Weitere Informationen finden Sie im aktualisierten [WKND-Tutorial](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html). Sie können den neuesten Code aus [GitHub](https://github.com/adobe/aem-guides-wknd/releases)nehmen.

* AEM-Sites: Commerce CIF-Kernkomponenten 0.7.0 und 0.9.0

   Integrieren von AEM-Sites mit dem Magento-Commerce. Siehe [Erweitern spezialisierter Kernkomponenten und Projektarchiv mit Schwerpunkt Handel](https://github.com/adobe/aem-core-cif-components/releases).

* AEM Assets: Desktop-App 2.0.1.1

   Weitere Informationen finden Sie unter [Desktop-Zugriff auf die Assets](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)erhalten.

* AEM-Bildschirme: Feature Pack 202001

   Digital Signage direkt aus AEM heraus. Installieren Sie die Verbesserungen mit dem neuesten Feature Pack, um die synchrone Wiedergabe über mehrere Medienplayer [zu](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202001.html)aktivieren.

## Hilfreiche Ressourcen

* [AEM 6.5-Benutzerhandbücher](../user-guide/home.md)

* [Allgemeine Versionshinweise zu Adobe Experience Manager 6.5](release-notes.md)

* [Service Pack-Versionshinweise für Adobe Experience Manager 6.5](sp-release-notes.md)
