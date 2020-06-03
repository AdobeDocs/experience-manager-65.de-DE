---
title: What's new in Adobe Experience Manager 6.5 Service Pack 5
description: What's new in Adobe Experience Manager 6.5 Service Pack 5
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: cc423a199e860429e85895690f6c1a81c20d1a19
workflow-type: tm+mt
source-wordcount: '1853'
ht-degree: 14%

---


# What&#39;s new in AEM 6.5 Service Pack 5 {#aem-whats-new-service-pack-5}

Adobe Experience Manager 6.5 service packs provide you new features, customer requested enhancements, performance, and stability related improvements at quarterly intervals. The quarterly delivery model makes it easier to access and adopt new features and innovations.

This article highlights the features included in the latest 6.5 Service Pack, [key features included in the previous 6.5 Service Packs](#key-features-previous-service-packs), and some of the [key releases since Experience Manager 6.5.4.0](#key-features-sice-sp3) release.

## AEM Sites {#aem-sites}

### Verbesserungen der Zugänglichkeit {#accessibility-sites}

* Improved error reporting by adding text information

* Improved UI focus during keyboard navigation

* Improved text contrast (luminosity ratio)

* Improved consistency of alt attributes for page images

* Improved consistency of Accessible Rich Internet Applications (ARIA) labels

* Improved Non-Visual Desktop Access (NVDA) capabilities

* Improved screen reader support

### Other key enhancements {#other-enhancements-sites}

* When copying or pasting a page tree, you now have the option of either pasting the root page or pasting the root page with the subpages of the tree.

* AEM Experience Fragments exported to Adobe Target workspaces now appear as unique offer types and offer sources in [!DNL Target].

* Multi Site Manager - The Publish trigger now successfully deletes a component from the published page if a component is deleted from the source page.

* Multi Site Manager - When the name of a local component in a LiveCopy is identical to the name of a component in the blueprint and the component is rolled out from blueprint, term _msm_moved is now successfully added to the name of the local component.

## AEM Assets {#aem-assets}

### Accessibility enhancements in Assets {#assets-accessibility}

[!DNL Adobe Experience Manager] Assets-Funktionen sind jetzt in Übereinstimmung mit den Web Content Accessibility Guidelines (WCAG) leichter zugänglich. Die Zugänglichkeit wurde in den folgenden Bereichen verbessert:

* User interface elements, controls, pages and dialogs are screen reader friendly.

* Auf Benutzeroberflächenelemente, Steuerelemente und Eingabefelder kann über die Tastatur zugegriffen werden.

* Änderung der Farbe und des Kontrasts einiger Grafiken, um von Benutzern mit eingeschränktem Sehvermögen und ohne Farbwahrnehmung zu unterscheiden. Beispielsweise wird die Farbe der Bewertungssymbole für Sterne (z. B. im [!UICONTROL Bewertungsabschnitt] auf der Registerkarte &quot; [!UICONTROL Erweitert] &quot;in den Asset- [!UICONTROL Eigenschaften] oder in der Ansicht der Karten) für einen entsprechenden Kontrast geändert.

![color of star rating icons changed to improve contrast](assets/star-rating-icons.png)

### Enhanced Exception handling {#exception-handling}

Assets user interface flow has better exception handling. Earlier if an asset did not have proper type for its dimension, exception was observed that was caught silently with no trace in logs. This behavior has changed and all exceptions are caught in logs.

## [!DNL Dynamic Media] {#dynamic-media}

### 3D support in [!DNL Dynamic Media] {#support-for-3d}

3D Support in [!DNL Dynamic Media] now enables customers to publish and add 3D content to web pages and applications. It includes:

* Publishing of common 3D asset formats to generate an asset URL.

* Interaktive Anzeige veröffentlichter 3D-Assets mit einem neuen, in der [!DNL Dynamic Media] Viewer-Bibliothek verfügbaren 3D-Web Viewer, powered by Adobe Dimension.

* 3D-Veröffentlichung und -Anzeige auf [!DNL Experience Manager Sites] einer Seite mithilfe der [!DNL Sites] WCM-Komponente.

## AEM Forms {#aem-forms}

### Customize the AEM Inbox columns {#customize-aem-inbox-columns}

You can customize an AEM Inbox to change the default title of a column, reorder the position of a column, and display additional columns based on the data of a workflow. You shall be a member of `administrators` or `workflow-administrators` group to customize the columns.

![Customize AEM Inbox columns](assets/customize-columns.gif)

### Save Interactive Communications as a draft {#save-as-draft}

Sie können die Agent-Benutzeroberfläche verwenden, um einen oder mehrere Entwürfe für jede interaktive Kommunikation zu speichern und den Entwurf später abzurufen, um weiter daran zu arbeiten. Zur einfacheren Identifizierung können Sie für jeden Entwurf einen anderen Namen angeben.

![Als Entwurf speichern](assets/save-as-draft.gif)

### [!DNL Oracle WebLogic] Anwendungsserverunterstützung {#weblogic-support}

AEM Forms hat Unterstützung für [!DNL Oracle WebLogic 12] AEM Forms on JEE hinzugefügt. Sie können von einer früheren Version aktualisieren oder einen neuen AEM 6.5 Forms on JEE-Server auf [!DNL Oracle WebLogic] 12.2.1.4 und höher einrichten. Später entspricht den Änderungen der kleineren Version, wobei x in 12.2.1.x durch eine Versionsnummer ersetzt wird.

### Verbesserungen der Zugänglichkeit {#accessibility-improvements}

AEM Forms includes the following accessibility enhancements:

* When a user previews an adaptive form as an HTML form, the [!UICONTROL Scribble Signature] field retains the tab focus.

* Die Fehlermeldungen, die beim Senden eines adaptiven Formulars angezeigt werden, enthalten jetzt das `aria-describedBy` Attribut. The attribute is attached to the fields referred in the error message. The `aria-describedby` attribute indicates IDs of the elements that describe the object. It helps establish a relationship between widgets or groups and text that described them.

* If an adaptive form has some mandatory fields, the mandatory attribute is set to `True` for such fields in ARIA accessibility schema.

### X-509 certificate-based authentication for SOAP-based web services in form data model {#x509-based-authentication-soap}

Form data model now supports X-509 certificate-based authentication while using SOAP web services as the data source.

### Other key improvements {#other-improvements}

* AEM 6.5 Forms on JEE Document Security is now based on [!DNL Apache Struts 2].

* Added support for [!DNL Oracle Real Applications Cluster (RAC) 19c].

## Key features in previous AEM 6.5 Service Packs {#key-features-previous-service-packs}

### AEM Sites {#aem-sites-previous-service-packs}

#### Style System enhancements (6.5.4.0) {#style-system-enhancements}

You can now select styles within the component dialog using the enhanced Style System.

#### Performance improvements in various areas (6.5.4.0) {#performance-improvements}

* Reduced the time for loading and initializing ContextHub within a site (`contexthub.kernel.js`). It results in faster page loads during a site visit.

* Reduced the time to refresh a page after dragging Experience Fragments to Sites Page Editor.

* Shortened the load time for entries on a Sites page with more than 200 live copies in **[!UICONTROL Live Copy Overview]**.

* Improved handling of incomplete or invalid URLs. Such URLs can slow down the Template Editor.

### AEM Assets {#aem-assets-previous-service-packs}

#### Configure AEM Assets with Brand Portal (6.5.4.0) {#configure-assets-bp}

Der Kanal für die Autorisierung zwischen AEM Assets und Brand Portal wurde geändert. Zuvor wurde Brand Portal über das alte OAuth-Gateway in der klassischen Benutzeroberfläche konfiguriert. Das Gateway ruft mithilfe des JWT-Token-Austauschs ein IMS-Zugriffstoken zur Autorisierung ab. AEM Assets wird jetzt über Adobe I/O in Brand Portal konfiguriert. Die Konsole ruft das IMS-Token zur Authentifizierung Ihres Brand Portal-Mandanten ab.

Die Schritte zum Konfigurieren von AEM Assets mit Brand Portal unterscheiden sich je nach Ihrer AEM-Version und davon, ob Sie zum ersten Mal eine Konfiguration durchführen oder die vorhandenen Konfigurationen aktualisieren. Weitere Informationen finden Sie unter [Konfigurieren von AEM Assets mit Brand Portal.](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/publish/configure-aem-assets-with-brand-portal.html)

#### Accessibility enhancements (6.5.4.0) {#accessibility-enhancements}

Experience Manager Assets includes the following accessibility enhancements:

* Arrow keys on keyboard can be used to move and pan areas within zoomed images. For more information, see [preview assets using keyboard keys only](../assets/managing-assets-touch-ui.md#previewing-assets).

* The mixed state checkboxes (in which unless you select all the nested predicates the first-level checkboxes are not selected and are stricken through) in Filters panel are readable by screen readers.

* Date and time format constraints are provided in field labels of date fields, to enable the users to enter the date in correct format using keyboard.

   Beispiel: `On Time (MM-DD-YYYY HH:mm)`. Here MM is month in two-digit format, YYYY is year, DD is day in two-digit format, HH is hour in 24-hour military format, and mm is minute.

* The `X` symbol on the button to remove the currently selected tags are now announced by screen readers along with the number of selected tags.

#### Visuelle Suche nach AEM Assets (6.5.2.0) {#visual-search}

Assets-Benutzer können nach visuell ähnlichen Bildern suchen. AEM zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. See [Visual search](../assets/search-assets.md).

### Dynamic Media {#dynamic-media-previous-service-packs}

#### Smart Imaging for Dynamic Media {#smart-imaging}

Die intelligente Bildbearbeitung nutzt die einzigartigen Ansichtsmerkmale der einzelnen Benutzer, um automatisch die richtigen Bilder bereitzustellen, die für ihr Erlebnis optimiert wurden, was zu einer besseren Leistung und Interaktion führt. Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert im letzten Moment abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. See [Smart Imaging](../assets/imaging-faq.md).

#### Smart-Zuschneiden in Video-Profilen für dynamische Medien (6.5.3.0) {#smart-crop-video}

Smartes Zuschneiden für Video – eine optionale Funktion, die in Videoprofilen verfügbar ist – ist ein Tool, das die Leistung von künstlicher Intelligenz in Adobe Sensei nutzt, um den Fokuspunkt in adaptiven oder progressiven Videos, die Sie hochgeladen haben, unabhängig von der Größe automatisch zu erkennen und zu beschneiden. See [About using smart crop in video profiles](../assets/video-profiles.md).

### AEM Forms {#aem-forms-previous-service-packs}

#### Generieren einer druckbaren Ausgabe in AEM Forms Workflows (6.5.4.0) {#generate-printable-output}

Mit dem Arbeitsablaufschritt &quot;Druckbare Ausgabe generieren&quot;können Sie eine Quellvorlagendatei in eine Datendatei integrieren. Mit dieser Integration können Sie verschiedene Kopien der Vorlagendatei drucken oder speichern. Der Schritt generiert eine PCL-, PostScript-, ZPL-, IPL-, TPCL- oder DPL-Ausgabe. Weitere Informationen zu dieser Funktion finden Sie unter [Forms-zentrierter Arbeitsablauf auf OSGi - Schritt-Referenz](../forms/using/aem-forms-workflow-step-reference.md).

![Druckbare Ausgabe generieren](assets/generate-print-output-step.gif)

#### Unterstützung für mehrere Spalten bei adaptiven Formularen und interaktiver Kommunikation im Layoutmodus (6.5.4.0) {#multi-column-adaptive-forms}

Sie können jetzt die Anzahl der Spalten für ein Bedienfeld in adaptiven Formularen und in interaktiver Kommunikation definieren. Wechseln Sie zum Layoutmodus, um die neue Option für mehrere Spalten zu verwenden. Weitere Informationen finden Sie unter [Verwenden des Layoutmodus zum Ändern der Größe von Komponenten](../forms/using/resize-using-layout-mode.md).

![Mehrspaltiges Layout](assets/multi-column-layout.gif)

#### AEM Inbox-Anpassungen (6.5.4.0) {#aem-inbox}

Die neue Option &quot;Admin-Steuerung&quot;ermöglicht den Administratoren Folgendes:

* Anpassen von Kopfzeilentext und Logo

* Steuern der Anzeige der in der Kopfzeile verfügbaren Navigationslinks

Die Option &quot;Admin-Steuerung&quot;ist nur für die Mitglieder der Gruppe &quot;Administratoren&quot;oder &quot;Workflow-Administratoren&quot;sichtbar. Weitere Informationen zu dieser Funktion finden Sie unter [Ihr Posteingang](../sites-authoring/inbox.md).

#### Rich-Text-Unterstützung in HTML5-Formularen (6.5.4.0) {#rich-text-support}

Konvertieren Sie ein Textfeld in einem XFA-Formular in ein Rich-Text-Feld in einem HTML5-Formular. Weitere Informationen finden Sie unter [Entwerfen von Formularvorlagen für HTML5-Formulare](../forms/using/designing-form-template.md).

#### Accessibility enhancements (6.5.4.0) {#forms-accessibility-enhancements-6540}

Experience Manager Forms umfasst die folgenden Verbesserungen der Barrierefreiheit:

* Kontrollkästchen, Links, Datumsauswahl und Datumseingabefelder werden von Bildschirmlesehilfen korrekt in einem adaptiven Formular angekündigt.

* Jede Seite eines adaptiven Formulars enthält jetzt einen Titel und eine Hauptmarkenbeschriftung.

#### Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines AEM Forms-Benutzers (6.5.3.0) {#share-request-access}

Sie können Ihre Inbox-Elemente für andere Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente erhält, kann der Benutzer für freigegebene Elemente entsprechende Aktionen anfordern. Ebenso können Sie von anderen Benutzern den Zugriff auf Posteingangselemente anfordern. Siehe [Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers](../forms/using/configure-shared-queues-osgi.md).

#### Abwesenheitseinstellungen für Posteingangselemente eines AEM Forms-Benutzers konfigurieren (6.5.3.0) {#configure-out-of-office}

Wenn Sie planen, abwesend zu sein, können Sie angeben, was mit Artikeln geschieht, die Ihnen für diesen Zeitraum zugewiesen wurden.
Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Sie können eine Standardperson festlegen, an die alle Elemente gesendet werden sollen. Siehe Abwesenheitseinstellungen [konfigurieren](../forms/using/configure-out-of-office-settings.md).

#### Generieren mehrerer interaktiver Kommunikation mit der Batch-API für AEM Forms (6.5.3.0) {#generate-multiple-ic}

Sie können die Stapel-API verwenden, um mehrere interaktive Mitteilungen aus einer Vorlage zu erstellen. Die Vorlage ist eine interaktive Kommunikation ohne Daten. Die Stapel-API kombiniert Daten mit einer Vorlage, um eine interaktive Kommunikation zu erzeugen. Die API ist bei der Massenproduktion interaktiver Kommunikation nützlich. Zum Beispiel Telefonrechnungen, Kreditkartenauszüge für mehrere Kunden. Siehe [Generieren mehrerer interaktiver Kommunikation mit der Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

## Wichtige Versionen seit AEM 6.5 SP4 {#key-releases-since-last-sp}

Zwischen dem 05. März 2020 und dem 04. Juni 2020 hat Adobe die folgenden Funktionen veröffentlicht, die außerhalb der AEM-Hauptversion verfügbar sind:

* AEM Cloud Manager [2020.3.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-3-0.html), [2020.4.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-4-0.html)und [2020.5.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-current.html)

* [AEM Assets: Desktop-App 2.0.2.0](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)

* [AEM-Bildschirme: Feature Pack 202004](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202004.html)

## Hilfreiche Ressourcen

* [AEM 6.5-Benutzerhandbücher](../user-guide/home.md)

* [Allgemeine Versionshinweise zu Adobe Experience Manager 6.5](release-notes.md)

* [Service Pack-Versionshinweise für Adobe Experience Manager 6.5](sp-release-notes.md)
