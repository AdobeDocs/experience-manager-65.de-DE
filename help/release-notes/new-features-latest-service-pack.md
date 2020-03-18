---
title: Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 4
description: Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 4
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 1fde7fc5dd32b5a2a83fe6c01cfa2b24be32a899

---


# Neue Funktionen in Adobe Experience Manager 6.5 Service Pack 4 {#aem-whats-new-service-pack-4}

Adobe Experience Manager (AEM) 6.5 bietet Funktionen und kontinuierliche Verbesserungen durch vierteljährliche Service Packs in diesem Jahr. Der neue Ansatz kommt unseren Kunden zugute, wenn sie die Innovationen schneller umsetzen.

Das neueste AEM Service Pack 4 (6.5.4.0) wird am 5. **März 2020** veröffentlicht. In diesem Artikel werden die Funktionen der neuesten Service Pack-Angebot vorgestellt, mit denen Sie Ihre AEM-Reise noch bereichern können.

## AEM Sites {#aem-sites}

### Leistungsverbesserungen in verschiedenen Bereichen {#performance-improvements}

* Verkürzte Ladezeit und Initialisierung von ContextHub innerhalb einer Site (contexthub.kernel.js). Das führt zu schnelleren Seitenladevorgängen während eines Site-Besuchs.

* Die Zeit zum Aktualisieren einer Seite nach dem Ziehen und Ablegen von Erlebnisfragmenten in den Seiten-Editor für Sites wurde verringert.

* Die Zeit zum Laden von Einträgen für eine Siteseite mit mehr als 200 Live-Kopien in der Live Copy-Übersicht wurde verkürzt.

* Verbesserte Verarbeitung von unvollständigen oder ungültigen URLs. Solche URLs können den Vorlageneditor verlangsamen.

Darüber hinaus enthält AEM 6.5.4.0 Style-Systemverbesserungen. Sie können jetzt Stile im Komponentendialogfeld auswählen.

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

Wenn eine Lösung mehrere Kopien einer Quellvorlagendatei drucken oder speichern und in eine Datendatei mit zahlreichen Datensätzen integrieren soll, steht in AEM Forms ein neuer Arbeitsablaufschritt zum Generieren druckbarer Ausgabe zur Verfügung. Wenn Sie z. B. ein Quellformular mit einem anderen Namen jedes Mal drucken möchten, wenn es gedruckt wird, können Sie diese Namen in der Datendatei enthalten und in eine Standardvorlagendatei integrieren.

Nutzen Sie diese Funktion mithilfe von **Tools** > **[!UICONTROL Workflow]** > **[!UICONTROL Modelle]** > **[!UICONTROL Erstellen]** und suchen Sie dann nach dem Workflow **[!UICONTROL Generate Printable Output]** .

![Druckbare Ausgabe generieren](assets/generate-print-output-demo.gif)

Weitere Informationen zu dieser Funktion finden Sie unter [Forms-zentrierter Arbeitsablauf auf OSGi - Schritt-Referenz](../forms/using/aem-forms-workflow-step-reference.md).

### Unterstützung für mehrere Spalten für adaptive Formulare und interaktive Kommunikation im Layoutmodus {#multi-column-adaptive-forms}

Sie können jetzt die Anzahl der Spalten für ein Bedienfeld in adaptiven Formularen und in interaktiver Kommunikation definieren.

Sie können die neue Option finden, indem Sie in den Layoutmodus wechseln. Tippen Sie auf das Bedienfeld, das Sie in ein mehrspaltiges Format konvertieren möchten, wählen Sie das übergeordnete Element aus und tippen Sie auf das Symbol für mehrere Spalten, um die Anzahl der Spalten für das Bedienfeld zu definieren.

![Mehrspaltiges Layout](assets/multi-column-layout.gif)

Weitere Informationen finden Sie unter [Verwenden des Layoutmodus zum Ändern der Größe von Komponenten](../forms/using/resize-using-layout-mode.md).

### AEM Inbox-Anpassungen {#aem-inbox}

Müssen Sie die in AEM-Kopfzeilen verfügbaren Optionen je anpassen? Es ist jetzt mit unserer neuen Service Pack Version mit der Einführung einer **[!UICONTROL Admin Control]** Option möglich.

**Kopfzeilentext anpassen**

Workflow-Administratoren können jetzt den Kopfzeilentext Ihrer Wahl angeben.

Die neue Option Kopfzeilentext **** anpassen finden Sie unter Ansicht-Selektor (rechts oben in der Symbolleiste verfügbar) > **[!UICONTROL Admin-Steuerung]**.

**Logo anpassen**

Ähnlich wie beim Anpassen des Kopfzeilentextes können Workflow-Administratoren jetzt ein Kopfzeilenlogo Ihrer Wahl festlegen.

Die neue **[!UICONTROL Option Logo]** anpassen finden Sie unter Ansicht-Auswahl > **[!UICONTROL Admin-Kontrolle]**.

Weitere Informationen zu dieser Funktion finden Sie unter [Ihr Posteingang](../sites-authoring/inbox.md).

### Benutzernavigationssteuerung {#user-navigation-control}

Workflow-Administratoren haben jetzt die Möglichkeit, die Benutzer je nach Rolle in einem eingeschränkten Modus mit AEM arbeiten zu lassen. Die Administratoren können die Anzeige der in der Kopfzeile verfügbaren Navigationsoptionen steuern, um die Benutzer auf den Workflow-Authoring-Modus oder andere Lösungslinks zu beschränken.

Sehen Sie sich die neuen **[!UICONTROL Navigationsoptionen]** &quot;Ausblenden&quot;unter &quot;Ansicht-Auswahl&quot;> &quot; **[!UICONTROL Admin-Kontrolle]**&quot;an.

Weitere Informationen zu dieser Funktion finden Sie unter [Ihr Posteingang](../sites-authoring/inbox.md).

### Rich-Text-Unterstützung in HTML5-Formularen {#rich-text-support}

Das Textfeld kann jetzt eine Liste von Formatierungsoptionen im gerenderten HTML5-Formular anzeigen. Sie müssen ein Format für das Textfeld in Forms Designer definieren, um geeignete Einstellungen auf das Feld anzuwenden.

Um diese Funktion zu verwenden, tippen Sie in Forms Designer in der **[!UICONTROL Design-Ansicht]** auf das Textfeld. Wählen Sie auf der Registerkarte &quot; **[!UICONTROL Feld]** &quot;in der Dropdown-Liste &quot; **[!UICONTROL Feldformat]** &quot;die Option &quot; **[!UICONTROL Rich Text]** &quot;aus, um die Einstellungen anzuwenden.

Weitere Informationen finden Sie unter [Entwerfen von Formularvorlagen für HTML5-Formulare](../forms/using/designing-form-template.md).

## Wichtigste Highlights

Zusätzlich zu den neuen Funktionen umfasst AEM 6.5 Service Pack 4 die folgenden wichtigen Highlights:

* Sie können jetzt ausgewählte Inhaltsunterbauten mit *dynamischen Medien - Scene7-Modus* und nicht mit allen verfügbaren Elementen synchronisieren `content/dam`.

* Die Integration des Formulardatenmodells mit dem SOAP-Webdienst unterstützt jetzt Auswahlgruppen oder Attribute für Elemente.

* SOAP-Eingabe- oder -Ausgabe und komplexe Datenstrukturen unterstützen jetzt die dynamische Gruppenersetzung.

## Wichtige Funktionen früherer AEM 6.5 Service Packs

### Smart Imaging für dynamische Medien {#smart-imaging}

Intelligente Bildbearbeitung nutzt die individuellen anzeigebezogenen Benutzermerkmale, um automatisch die richtigen Bilder für ein optimiertes individuelles Erlebnis zu präsentieren. Das Ergebnis: mehr Leistung und Interaktion. Die intelligente Bildbearbeitung arbeitet mit bestehenden Bildvorgaben und reduziert in der letzten Sekunde abhängig vom Browser oder der Geschwindigkeit der Netzverbindung die Größe der Bilddatei intelligent noch weiter. Siehe [Smart Imaging](../assets/imaging-faq.md).

### Visuelle Suche nach AEM Assets {#visual-search}

Assets-Benutzer können nach visuell ähnlichen Bildern suchen. AEM zeigt die Bilder mit Smart-Tags aus dem DAM-Repository an, die einem vom Benutzer ausgewählten Bild ähnlich sind. See [Visual search](../assets/search-assets.md).

### Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers {#share-request-access}

Sie können Ihre Inbox-Elemente für andere Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente hat, kann der Benutzer für freigegebene Elemente entsprechende Aktionen anfordern. Ebenso können Sie von anderen Benutzern den Zugriff auf Posteingangselemente anfordern. Siehe [Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers](../forms/using/configure-shared-queues-osgi.md).

### Abwesenheitseinstellungen für Ihre Posteingangselemente konfigurieren {#configure-out-of-office}

Wenn Sie planen, abwesend zu sein, können Sie angeben, was mit Artikeln geschieht, die Ihnen für diesen Zeitraum zugewiesen wurden.
Sie haben die Möglichkeit, ein Anfangs- und Enddatum sowie eine Anfangs- und Enduhrzeit für die Gültigkeit der Abwesenheitseinstellungen anzugeben. Sie können eine Standardperson festlegen, an die alle Elemente gesendet werden. Siehe Abwesenheitseinstellungen [konfigurieren](../forms/using/configure-out-of-office-settings.md).

### Generieren mehrerer interaktiver Kommunikation mit der Batch-API {#generate-multiple-ic}

Sie können die Stapel-API verwenden, um mehrere interaktive Mitteilungen aus einer Vorlage zu erstellen. Die Vorlage ist eine interaktive Kommunikation ohne Daten. Die Stapel-API kombiniert Daten mit einer Vorlage, um eine interaktive Kommunikation zu erzeugen. Die API ist bei der Massenproduktion interaktiver Kommunikation nützlich. Zum Beispiel Telefonrechnungen, Kreditkartenauszüge für mehrere Kunden. Siehe [Generieren mehrerer interaktiver Kommunikation mit der Batch-API](../forms/using/generate-multiple-interactive-communication-using-batch-api.md).

### Standardmäßige Prüffehlermeldungen für adaptive Formulare {#standard-validation}

Adaptive Formulare können jetzt in benutzerdefinierte Dienste integriert werden, um Datenvalidierungen durchzuführen. Wenn die eingegebenen Werte die Überprüfungskriterien nicht erfüllen und die vom Server zurückgegebene Prüffehlermeldung im Standardmeldungsformat vorliegt, werden die Fehlermeldungen auf Feldebene im Formular angezeigt. Wenn die Eingabewerte die Überprüfungskriterien nicht erfüllen und die Fehlermeldung zur Servervalidierung nicht im Standardmeldungsformat vorliegt, stellen die adaptiven Formulare einen Mechanismus bereit, mit dem die Prüffehlermeldungen in ein Standardformat umgewandelt werden können, sodass sie auf Feldebene im Formular angezeigt werden. Siehe Fehlermeldungen bei der [Standardüberprüfung für adaptive Formulare](../forms/using/standard-validation-error-messages-adaptive-forms.md).

## Wichtige Versionen seit AEM 6.5 SP3

Zwischen dem 12. Dezember 2019 und dem 5. März 2020 hat Adobe die folgenden Funktionen veröffentlicht, die außerhalb der AEM-Hauptversion verfügbar sind:

* Verbesserungen für AEM Cloud Manager 2020.1.0 und 2020.2.0 Monatliche Verbesserungen für Cloud Manager. Die letzten zwei Versionen konzentrierten sich auf die Verbesserung des Pipeline-Status und die Möglichkeit, Protokolle für die verschiedenen Schritte herunterzuladen. Die vollständigen Versionshinweise finden Sie hier:
   * [Cloud Manager 2020.1.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-2020-1-0.html)

   * [Cloud Manager 2020.2.0](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/release-notes/release-notes-current.html)

* CLI-Aktualisierungen für AEM Cloud ManagerAutomatisieren von Cloud Manager-Aufgaben mit dem Befehlszeilenwerkzeug. Wir erweitern den CLI kontinuierlich - nehmen an [GitHub](https://github.com/adobe/aio-cli-plugin-cloudmanager/releases)teil.

* AEM-Sites: Project Archetype 23Die beste Möglichkeit, ein neues AEM-Projekt Beginn. Mit Archetype 23 [verschmelzen wir den Projektarchiv für SPA und reguläre Sites zu einem](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-23)und bieten damit ein Standarddesign, um Ihre Front-End-Entwicklung voranzutreiben.

* AEM-Sites: WKND-ReferenzseiteAlle [neuen Referenzprojekte](https://www.wknd.site/) mit Best Practices zum Erstellen von Sites mit AEM. Erfahren Sie mehr, indem Sie das komplett aktualisierte [WKND-Tutorial](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html) lesen und den Code von [GitHub](https://github.com/adobe/aem-guides-wknd/releases)erfassen.

* AEM-Sites: Commerce CIF-Kernkomponenten 0.7.0 und 0.9.0Integration von AEM-Sites und Magento Commerce. Wir [erweitern kontinuierlich dedizierte Kernkomponenten und einen Projektarchiv mit Schwerpunkt Handel](https://github.com/adobe/aem-core-cif-components/releases).

* AEM Assets: Desktop-App 2.0.1.1
   [Desktop-Zugriff auf Assets](https://docs.adobe.com/content/help/en/experience-manager-desktop-app/using/release-notes.html)

* AEM-Bildschirme: Feature Pack 202001Digitale Signatur direkt in AEM Nehmen Sie die neuesten Verbesserungen mit dem neuesten Feature Pack zur Kenntnis. Diesmal [aktivieren wir die synchrone Wiedergabe über mehrere Medienplayer](https://docs.adobe.com/content/help/en/experience-manager-screens/user-guide/release-notes/release-notes-fp-202001.html)hinweg.

## Hilfreiche Ressourcen

* [AEM 6.5-Benutzerhandbücher](../user-guide/capabilities.md)

* [Allgemeine Versionshinweise zu Adobe Experience Manager 6.5](release-notes.md)

* [Service Pack-Versionshinweise für Adobe Experience Manager 6.5](sp-release-notes.md)
