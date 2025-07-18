---
title: Kumulative wichtige Funktionen und Verbesserungen in Adobe Experience Manager 6.5.
description: Eine kumulative Liste der wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5 aus den letzten acht Service Pack-Versionen vorgenommen wurden.
content-type: reference
docset: aem65
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 01fe5b53-2244-445f-a4d0-bd58ea38b611
solution: Experience Manager
source-git-commit: eef3ad559612c338de0c4232aadc4133c910aaf8
workflow-type: ht
source-wordcount: '3109'
ht-degree: 100%

---

# Wichtige kumulative Funktionen und Verbesserungen

Eine kumulative Liste der wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5 für die letzten acht Service Pack-Versionen vorgenommen wurden.

Siehe auch die [Versionshinweise zum neuesten Service Pack von Adobe Experience Manager 6.5](/help/release-notes/release-notes.md).


## AEM 6.5, Service Pack 23 – 22. Mai 2025

### Forms {#forms-sp23}

* [Barrierefreie Hyperlinks mit verschiedenen Textstilen in statischen PDFs](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/using-designer.pdf): Hyperlinks, die verschiedene Textstile in statischen PDFs enthalten, werden jetzt als einzelnes, barrierefreies Element getaggt. Diese Verbesserung vereinfacht die Tag-Baumstruktur sowie die Navigation der Bildschirmlesehilfe und unterstützt eine bessere Einhaltung von Vorgaben zur Barrierefreiheit.

* [Aktualisierte unterstützte Plattform-Matrix](/help/forms/using/aem-forms-jee-supported-platforms.md)

  Die neueste Version führt Aktualisierungen der unterstützten Plattform-Matrix ein, um die Kompatibilität mit neueren Technologien sicherzustellen.

   * IBM® Content Manager Client 8.7

   * MongoDB Enterprise 7.0

   * MySQL 8.4

   * Microsoft® SQL Server 2022

   * Microsoft® SQL Server JDBC-Treiber 12.8

   * Red Hat® Enterprise Linux® 9 (Kernel 4.x, 64 Bit) 

* [Robuste Dateianhangskomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment): Als Sicherheitsmaßnahme verhindert die Komponente jetzt die Übermittlung von Dateien mit geänderten Erweiterungen, die versuchen, Prüfungen zulässiger Dateitypen zu umgehen. Solche Dateien werden während der Übermittlung blockiert, um sicherzustellen, dass nur gültige Dateitypen akzeptiert werden.

## AEM 6.5, Service Pack 22 – 21. November 2024

### Sites {#sites}

[Der universelle Editor](/help/sites-developing/universal-editor/introduction.md) ist jetzt in AEM 6.5 für Headless-Anwendungsfälle verfügbar, wenn ein Feature Pack angewendet wird.

### [!DNL Assets]

Die Registerkarte „IPTC“ bietet nun Unterstützung für die Textfelder [!UICONTROL Alternativtext] und [!UICONTROL Erweiterte Beschreibung]. (Assets-34918)

### Forms {#forms-sp22}

#### Neue, allgemein verfügbare Funktionen in AEM Forms {#ga-aem-forms-sp22}

* Die Einbettung von Schriftarten in [interaktive Kommunikations-Batch-APIs](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/interactive-communications/create-interactive-communication#output-format-print-channel) wird jetzt unterstützt: Interaktive Kommunikationen unterstützen jetzt das Einbetten von Adobe Ming- und Adobe Myungjo-Schriftarten in PDFs, die durch das Batch-API generiert wurden. Diese Verbesserung sorgt für eines genaues Rendering von Text in generierten Dokumenten, auch wenn Schriftartteilmengen verwendet werden, und bietet eine verbesserte Unterstützung für mehrsprachige Inhalte in PDF-Ausgaben.

* [Inhaltsverzeichnis-API für PDF-Barrierefreiheit](/help/forms/using/aem-document-services-programmatically.md#auto-tag-pdf-documents-auto-tag-api): AEM Forms auf OSGi unterstützt jetzt das neue TOC-Tag-API zur Verbesserung von PDFs entsprechend den Barrierefreiheitsstandards. Dadurch werden PDFs für Benutzende durch Hilfstechnologien leichter zugänglich.

* [Fragment-XDP-Auflösung](/help/forms/using/assembler-service.md#resolve-references-on-crx-repository-resolve-references-on-crx-repository): AEM Forms auf OSGi löst jetzt Fragment-XDPs auf, die in Primär-XDPs referenziert und im AEM CRX-Repository gespeichert sind.

* [Verbesserungen bei der PDF/A-Compliance](/help/forms/developing/pdf-a-documents.md#converting-documents-to-pdfa-documents-converting-documents-to-pdf-a-documents): Benutzende können jetzt PDFs für Archivierungszwecke in PDF/A-Formate (1a, 2a, 3a) konvertieren und dabei die Barrierefreiheit sicherstellen sowie die Einhaltung dieser Standards überprüfen.

* **Unterstützung der automatischen Schriftgrößenanpassung für statische PDF-Dokumente**: AEM Forms Designer, OutputService und FormsService unterstützen jetzt die automatische Schriftgrößenanpassung für statische PDFs. Wenn Benutzende den Schriftgrad 0 für Text-, numerische, Kennwort- oder Datum/Uhrzeit-Felder festlegen, passt sich der Schriftgrad in diesen Feldern automatisch an, ohne die Gesamtgröße des Feldes zu ändern. Zum Verwenden der Funktion übergeben Benutzende eine Markierung in die benutzerdefinierte XCI: `<behaviorOverride>patch-LC-3921991:1</behaviorOverride>`.

#### Neue Beta-Funktionen in AEM Forms {#beta-aem-forms-sp22}

Die Beta-Funktion bietet Ihnen die einmalige Möglichkeit, exklusiven Zugriff auf aktuelle Innovationen zu erhalten und deren Entwicklung mitzugestalten. Möchten Sie eine Beta-Funktion für Ihre Umgebungen aktivieren? Senden Sie von Ihrer offiziellen E-Mail-Adresse eine Nachricht an aem-forms-ea@adobe.com mit der Liste der Funktionen, an denen Sie interessiert sind.

* [hCaptcha-](/help/forms/using/integrate-adaptive-forms-hcaptcha.md) und [Cloudfare Turnstile Captcha-Dienste](/help/forms/using/integrate-adaptive-forms-turnstile.md): AEM Forms unterstützt die folgenden Captcha-Dienste:
   * hCaptcha schützt Formulare vor Bots, Spam und automatisiertem Missbrauch, indem Benutzende zum Ausfüllen eines Kontrollkästchen-Widgets aufgefordert werden. Dadurch wird sichergestellt, dass nur menschliche Benutzende fortfahren, und die Sicherheit für Online-Transaktionen wird erhöht.
   * Cloudflare Turnstile bietet eine Sicherheitsmaßnahme zum Schutz von Formularen vor automatisierten Bots, bösartigen Angriffen, Spams und unerwünschtem automatisierten Traffic. Bei der Formularübermittlung wird ein Kontrollkästchen angezeigt, mit dem überprüft wird, ob es sich um menschliche Benutzende handelt, bevor das Formular übermittelt werden kann.

* Versionierung adaptiver Formulare:
   * [Erstellen mehrerer Versionen eines adaptiven Formulars](/help/forms/using/add-versioning-reviews-comments.md): Benutzende können jetzt problemlos Varianten vorhandener Formulare verwalten. Dieser Prozess vereinfacht die Versionskontrolle und erleichtert den Vergleich für die Formularoptimierung – alles innerhalb eines einzigen, optimierten Workflows.
   * [Vergleichen adaptiver Formulare](/help/forms/using/compare-forms-core-components.md): Benutzende können jetzt ganz einfach zwei Formulare vergleichen, um Unterschiede zu identifizieren. Dies erleichtert die reibungslose Zusammenarbeit, da Team-Mitglieder nun Revisionen vergleichen und Änderungen effizient diskutieren können.

## AEM 6.5, Service Pack 21 – 6. Juni 2024

### [!DNL Assets]

#### Verbesserungen

Die Registerkarte „IPTC“ bietet nun Unterstützung für die Textfelder [!UICONTROL Alternativtext] und [!UICONTROL Erweiterte Beschreibung]. (Assets-34918)

#### Barrierefreiheit

* Wenn der Verarbeitungsstatus eines Assets „Fehlgeschlagen“ oder „Metadaten fehlgeschlagen“ lautet, funktioniert die Benutzeroberfläche „Untertitel und Audiospuren“ jetzt ordnungsgemäß. (Assets-37281)
* Wenn Sie Asset-Metadaten speichern und bearbeiten möchten, wird die Sprachbezeichnung jetzt angezeigt. (Assets-37281)

### [!DNL Forms]

* **Unterstützung für OAuth-Anmeldedaten**: Neue, benutzerfreundlichere Anmeldedaten für die Server-zu-Server-Authentifizierung, die den vorhandenen Anmeldedatentyp „Service-Konto (JWT)“ ersetzt. (NPR-41994)
* [Verbesserungen des Regeleditors in AEM Forms](/help/forms/using/rule-editor-core-components.md):
   * Unterstützung für die Implementierung verschachtelter Bedingungen mit `When-then-else`-Funktionalität.
   * Überprüfen oder Zurücksetzen von Panels und Formularen, einschließlich Feldern.
   * Unterstützung für moderne JavaScript-Funktionen wie Let- und Pfeilfunktionen (ES10-Unterstützung) innerhalb der benutzerdefinierten Funktionen.
* [AutoTag-API für PDF-Barrierefreiheit](/help/forms/using/aem-document-services-programmatically.md#doc-utility-services-doc-utility-services): AEM Forms auf OSGi unterstützt jetzt die neue AutoTag-API zur Verbesserung von PDFs entsprechend den Barrierefreiheitsstandards durch Hinzufügen von Tags: Absätze und Listen. Dadurch werden PDFs für Benutzende mit Hilfstechnologien leichter zugänglich.
* **16-Bit-PNG-Unterstützung**: Der ImageToPdf-Dienst von PDF Generator unterstützt jetzt die Konversion von PNGs mit einer 16-Bit-Farbtiefe.
* **Anwenden von Artefakten auf einzelne Textblöcke in XDPs**: Mit Forms Designer können Benutzende jetzt Einstellungen für einzelne Textblöcke in XDP-Dateien konfigurieren. Mit dieser Funktion können Sie die Elemente steuern, die in den resultierenden PDFs als Artefakte behandelt werden. Diese Elemente – wie Kopf- und Fußzeilen – werden für Hilfstechnologien verfügbar gemacht. Zu den Hauptfunktionen gehören das Markieren von Textbausteinen als Artefakte und das Einbetten dieser Einstellungen in die XDP-Metadaten. Der Ausgabe-Service von Forms wendet diese Einstellungen während der PDF-Erstellung an und stellt dabei ein ordnungsgemäßes PDF/UA-Tagging sicher.
* **AEM Forms Designer ist nach dem Standard `GB18030:2022` zertifiziert**: Mit der Zertifizierung `GB18030:2022` unterstützt Forms Designer jetzt den chinesischen Unicode-Zeichensatz, was die Eingabe chinesischer Zeichen in alle bearbeitbaren Felder und Dialogfelder ermöglicht.
* [Unterstützung der WebToPDF-Route auf JEE-Server](/help/forms/using/admin-help/configure-service-settings.md#generate-pdf-service-settings-generate-pdf-service-settings): Der PDF Generator-Dienst unterstützt jetzt die WebToPDF-Route für die Konvertierung von HTML-Dateien in PDF-Dokumente auf JEE. Diese Unterstützung besteht zusätzlich zu den bereits vorhandenen Routen „Webkit“ und „WebCapture“ (nur Windows). Während die WebToPDF-Route bereits auf OSGi verfügbar war, wurde sie auf JEE erweitert. Jetzt unterstützt der PDF Generator-Dienst sowohl auf JEE- als auch auf OSGi-Plattformen die folgenden Routen über verschiedene Betriebssysteme hinweg:
   * **Windows**: Webkit, WebCapture, WebToPDF
   * **Linux®**: Webkit, WebToPDF


## AEM 6.5, Service Pack 20 – 22. Februar 2024

### [!DNL Assets]

* Dynamic Media unterstützt jetzt das verlustfreie HEIC-Bildformat für Apple iOS/iPadOS. Siehe [fmt](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt) in der Bildbereitstellungs- und Rendering-API von Dynamic Media.
* Der Multisite Manager (MSM) unterstützt jetzt Experience Fragment-Strukturen, einschließlich Ordnern und Unterordnern, für ein effizientes Massen-Rollout von Experience Fragments in Live Copies.

### [!DNL Forms]

* **Transaktionsberichte in AEM Forms on JEE**: Für AEM Forms on JEE wurde die Funktion „Transaktionsberichte“ eingeführt. Sie ermöglicht die umfassende Aufzeichnung von Dokumententransaktionen wie Konvertierungen, Ausgabedarstellungen und Übermittlungen. Diese Erweiterung erhöht die Effizienz und bessere Aufzeichnungen. Die Funktion ist standardmäßig deaktiviert. Sie können sie über die Admin-Benutzeroberfläche aktivieren.
* **Höhere Sicherheit mit ECDSA-Unterstützung**: AEM Forms bietet nun eine zuverlässige Unterstützung für den Elliptic Curve Digital Signature Algorithm (ECDSA) bei JEE- und OSGi-Stacks. Benutzende können jetzt PDF-Dokumente mit erhöhter Sicherheit signieren, zertifizieren und überprüfen. Zu den unterstützten EC-Kurvenalgorithmen gehören:
   * ECDSA – Elliptische Kurve P256 mit SHA256-Digest-Algorithmus
   * ECDSA – Elliptische Kurve P384 mit SHA384-Digest-Algorithmus
   * ECDSA – Elliptische Kurve P512 mit SHA512-Digest-Algorithmus
* **Nahtlose Kompatibilität von Forms Designer mit Windows 11**: AEM Forms Designer unterstützt nun Windows 11. Dadurch werden eine reibungslose Installation und ein reibungsloser Betrieb sichergestellt. Benutzende können problemlos auf Windows 11 aktualisieren, ohne Forms Designer neu installieren zu müssen oder sich um Kompatibilitätsprobleme zu sorgen. Dies ermöglicht unterbrechungsfreie Arbeitsabläufe.
* **Verbesserte Barrierefreiheit mit der benutzerdefinierten Rolle „Beschriftung“ in AEM Forms Designer**: AEM Forms Designer umfasst nun eine benutzerdefinierte Rolle für Barrierefreiheit. Sie heißt „Beschriftung“ und ermöglicht es Benutzenden, XDPs mit personalisierten Beschriftungselementen zu erstellen. Diese Funktion verbessert die Barrierefreiheit, da Benutzende damit benutzerdefinierte Beschriftungen in ihre Dokumententwürfe integrieren können, wodurch sie die Inklusion und das Anwendererlebnis verbessern können.

## AEM 6.5, Service Pack 19 – 7. Dezember 2023

* Ermöglicht den Benutzenden des Seiteneditors bzw. der Bildkomponente die Referenzierung von Assets aus dem Remote Assets Cloud Service.  (SITES-13448, SITES-13433)
* AEM unterstützt jetzt die Server-seitige Sortierung für eine schnellere Projektnavigation in der Listenansicht. Projektknoten werden nach der von der Benutzerin bzw. dem Benutzer ausgewählten Spalte sortiert, bevor sie in der Benutzeroberfläche angezeigt werden.

### [!DNL Forms]

* **Neue Kernkomponenten für adaptive Formulare**: Es werden vertikale Registerkarten, Geschäftsbedingungen und Kontrollkästchen hinzugefügt, um die Skalierbarkeit von Formularen zu verbessern.
   * **[Kontrollkästchen-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt eine Kontrollkästchen-Komponente enthalten. Sie ermöglicht Benutzenden, binäre Entscheidungen zu treffen, indem sie eine bestimmte Option auswählen oder eine Auswahl aufheben. Sie wird normalerweise als kleines Feld angezeigt, auf das geklickt oder getippt werden kann, um zwischen zwei Status zu wechseln: „aktiviert“ und „deaktiviert“. Das Kontrollkästchen ist ein gängiges Formularelement, das verwendet wird, um eine Ja/Nein- oder „true/false“-Auswahl zu treffen.

   * **[Nutzungsbedingungskomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions)**: Die auf Kernkomponenten basierenden adaptiven Formulare enthalten jetzt eine Nutzungsbedingungskomponente. Formularautorinnen bzw. -autoren fügen diesen Abschnitt hinzu, um Benutzern und Benutzerinnen über die Bedingungen oder rechtlichen Vereinbarungen für den Service, das Produkt oder die Plattform zu informieren. Diese Komponente hat das Ziel, Benutzende über die Regeln, Vorschriften und Verpflichtungen zu informieren, denen sie zustimmen, wenn sie das Formular übermitteln.

     ![Die Komponenten „Vertikale Registerkarten“, „Geschäftsbedingungen“ und „Kontrollkästchen“](/help/forms/using/assets/forms-components.png)

   * **[Komponente „Vertikale Registerkarten“](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt Formularinhalte in einer vertikalen Liste von Registerkarten organisieren und so ein strukturiertes und navigierbares Layout bieten. Vertikale Registerkarten in einem Formular verbessern das Kundenerlebnis, indem sie die Navigation vereinfachen und Inhalte organisieren. Sie sind besonders hilfreich, wenn das Formular mehrere Abschnitte oder komplexe Informationen enthält.

* **[64-Bit-Version von AEM Forms Designer](/help/forms/using/installing-configuring-designer.md)**: Die 64-Bit-Version von AEM Forms Designer bietet eine verbesserte Leistung, Skalierbarkeit und Speicherverwaltung, um die Erstellung von Formularen zu optimieren. Mit der 64-Bit-Architektur können Sie noch größere und komplexere Projekte einfach angehen, um nahtlose Design-Workflows und eine optimierte Effizienz zu gewährleisten. Verbessern Sie Ihre Formularentwurfsfähigkeiten und nutzen Sie die Zukunft von AEM Forms Designer mit dieser innovativen Version.

* **[Verbinden eines adaptiven Formulars mit einer Microsoft® SharePoint-Liste](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)**: AEM Forms bietet eine vorkonfigurierte Integration zum direkten Versand von Formulardaten an eine SharePoint-Liste, sodass Sie die Listenfunktionen von SharePoint verwenden können. Sie können die Microsoft® SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die Übermittlungsaktion „Senden mit Formulardatenmodell“ verwenden, um ein adaptives Formular mit der SharePoint-Liste zu verbinden.

* **[Unterstützung zum Konfigurieren der Eigenschaften des Nachweises für adaptive Formularfragmente](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)**: Sie können jetzt Ihre adaptiven Formularfragmente und deren Felder im Editor für adaptive Formulare einfach anpassen.

* **64-Bit XMLFM**: Die 64-Bit-Iteration von XMLFM führt zu verbesserter Performance, Skalierbarkeit und Speicherverwaltung. Dies ist der erste native 64-Bit-Dienst, der Server-seitig bereitgestellt wird. Durch die Nutzung seiner inhärenten Fähigkeit, auf größere Speicherressourcen im Vergleich zu seinem 32-Bit-Gegenstück zuzugreifen, ermöglicht XMLFM 64-Bit die nahtlose Handhabung größerer Rendering-Workloads. Dieser Meilenstein stellt nicht nur einen Performance-Sprung dar, sondern führt auch wichtige Verbesserungen am nativen Service-Framework innerhalb des AEM Forms-Servers ein. Mit diesem Update wird der AEM Forms-Server für die nahtlose Unterstützung nativer 64-Bit-Dienste ausgestattet.

## AEM 6.5, Service Pack 18 – 24. August 2023

* Assets, Dynamic Media – [Unterstützung für mehrere Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/video.md#about-msma) – Sie können einem primären Video jetzt ganz einfach mehrere Untertitel und mehrere Audiospuren hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.
* Assets – Von den Suchergebnissen aus können Sie jetzt zum Ordnerspeicherort navigieren, der ein Asset enthält, damit Sie verschiedene Asset-Management-Aufgaben ausführen können.
* Sites Polaris Picker in Inhaltsfragmenten hat eine verbesserte Leistung.
* Ermöglicht den Benutzenden des Seiteneditors bzw. der Bildkomponente die Referenzierung von Assets aus dem Remote Assets Cloud Service.
* Um in der Listenansicht, in der sich möglicherweise viele Projekte in Ihrem System befinden, schnell ein Projekt zu finden, unterstützt Adobe jetzt die Server-seitige Sortierung. Projektknoten werden nach der von Benutzenden ausgewählten Spalte im Backend sortiert, bevor sie in der Benutzeroberfläche gerendert werden.
* AEM 6.5.18.0 unterstützt MongoDB 5.0 bis 6.0.

### [!DNL Forms]

* **[Verbesserte Fehlerbehandlung mit benutzerdefinierten Fehler-Handlern im Regeleditor](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms)** – Sie können jetzt eine benutzerdefinierte Funktion (unter Verwendung der Client-Bibliothek) als Reaktion auf einen von einem externen Dienst zurückgegebenen Fehler aufrufen. Und Sie können eine maßgeschneiderte Antwort für Endbenutzerinnen und Endbenutzer bereitstellen. Oder Sie können bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst ausgefallen ist.

* **[Verbesserter Workflow-Schritt in Adobe Sign](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/workflows/aem-forms-workflow-step-reference#sign-document-step)** – Der Adobe Sign-Workflow-Schritt in AEM-Workflows ist mit den folgenden Verbesserungen verfügbar.

   * **Verbesserte Sicherheit mit ID-basierter Authentifizierung für Adobe Sign** – Die ID-basierte Authentifizierung von Adobe Acrobat Sign bietet eine zusätzliche Verifizierungsebene. Sie ermöglicht Benutzenden die Authentifizierung ihrer Identität mithilfe von amtlichem Lichtbildausweisen (Führerschein, Personalausweis, Reisepass). Durch die Nutzung von vertrauenswürdigen Identifikationsdokumenten verleiht diese Erweiterung dem Unterzeichnungsprozess ein zusätzliches Maß an Vertrauen und ist somit ideal für Szenarien, die erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Verbesserte Transparenz mit dem Audit-Protokoll für Adobe Sign-Dokumente** – Verwenden Sie die Audit-Protokoll-Funktion, um detaillierte Erkenntnisse zum Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt eine umfassende Aufzeichnung aller Aktionen und Interaktionen führen, die mit Ihren Dokumenten verbunden sind. Zu diesen Aktionen und Interaktionen gehören Details wie etwa die Personen, die das Dokument angesehen, bearbeitet oder unterschrieben haben, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist entscheidend für die Einhaltung von Vorschriften, die Beilegung von Streitigkeiten und die Gewährleistung der Integrität Ihrer digitalen Vereinbarungen.


   * **Erweiterte Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Unterzeichnenden hinaus** – Adobe Acrobat Sign bietet die Möglichkeit, die Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Personen hinaus zu erweitern, die unterzeichnet haben, um die Anforderungen an den Workflow besser zu erfüllen.  Wenn diese Option aktiviert ist, kann die Rolle jeder Empfängerin und jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei die Unterzeichnerin bzw. der Unterzeichner die Standardeinstellung ist.


* **[AEM Forms auf JEE-Vollinstallationsprogramm](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/install-aem-forms/jee-installation/aem-forms-jee-supported-platforms)** – Das Service Pack enthält ein vollständiges Installationsprogramm für AEM Forms auf JEE, das mehrere neue Software-Kombinationen unterstützt, darunter:
   * Microsoft® Windows Server 2022
   * Microsoft® Active Directory 2022
   * Oracle WebLogic 14C unter Windows Server 2022
   * Red Hat® JBoss® 7.4.10
   * MongoDB 6.0 <!-- it was previously MongoDB 4.4 -->
   * MySQL JDBC Connector 8

Wenn Sie eine Installation durchführen oder die Verwendung der neuesten Software für Ihre AEM 6.5 Forms auf JEE-Umgebung planen, empfiehlt Adobe die Verwendung des Vollinstallationsprogramms für AEM 6.5.18.0 Forms auf JEE. Die vollständige Liste der neu hinzugefügten und veralteten Software finden Sie in der Dokumentation zu AEM Forms auf JEE oder AEM Forms auf OSGi.

## AEM 6.5, Service Pack 17 – 25. Mai 2023

* **Verbesserungen des Sucherlebnisses**: Sie können jetzt schnell die folgenden Vorgänge für die Assets ausführen, die in den Suchergebnissen angezeigt werden:
   * Erstellen eines Workflows
   * Version erstellen
   * Zuordnung für Assets herstellen oder aufheben

  Sie müssen nicht erst zum Asset-Speicherort navigieren und seine Eigenschaften anzeigen, um diese Vorgänge durchzuführen.

* **Dynamic Media _Snapshot_**ermöglicht die Vorschau von Bild-Modifikatoren und Optimierungen der intelligenten Bildbearbeitung – wie WebP- oder AVIF-Ausgabe, bandbreitenabhängige Komprimierung und Skalierung des Geräte-Pixel-Verhältnisses – mithilfe von Testbildern oder Dynamic Media-URLs. Sie können dann sofort vergleichen, wie sich die einzelnen Einstellungen auf die Qualität und die Dateigröße auswirken.
Siehe [Dynamic Media Snapshot](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot).
* **DASH-Streaming mit Dynamic Media** – Neues Protokoll (DASH – Dynamic Adaptive Streaming over HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF) eingeführt. Jetzt für alle Regionen verfügbar.
* **Integration von Experience Manager Sites und Inhaltsfragmenten mit Dynamic Media der nächsten Generation in Assets** – Benutzende können jetzt ihre in der Cloud gehosteten Assets in Experience Manager Sites 6.5 verwenden. Sie können diese Assets auf On-Premise- oder Managed Services-Instanzen erstellen und bereitstellen.

### [!DNL Forms]

* **[Adaptive Formulare im AEM-Seiteneditor](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)** – Sie können jetzt den AEM-Seiteneditor verwenden, um schnell mehrere Formulare zu Ihren Site-Seiten hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautorinnen und -autoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie die Möglichkeiten der Komponenten adaptiver Formulare nutzen, einschließlich dynamisches Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:
   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in die Container-Komponente für adaptive Formulare im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Formulare im AEM Sites-Editor, damit Sie unabhängig von einer beliebigen Sites-Seite Formulare erstellen und diese Formulare auch auf mehreren Seiten wiederverwenden können.
   * Fügen Sie mehrere Formulare zu einer Sites-Seite hinzu, um das Benutzererlebnis zu optimieren und mehr Flexibilität zu bieten.
* **[Unterstützung für reCAPTCHA Enterprise in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)** – Die Unterstützung von reCAPTCHA Enterprise in Experience Manager Forms wurde hinzugefügt. Diese Funktion bietet zusätzlich zur bestehenden Unterstützung von Google reCAPTCHA v2 einen erweiterten Schutz vor betrügerischen Aktivitäten und Spam.
* **[Unterstützung für Adobe Acrobat Sign für Regierungsbehörden mit Experience Manager Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)** – AEM Forms kann jetzt mit Adobe Acrobat Sign für Regierungsbehörden (FedRAMP-konform) integriert werden. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für E-Signaturen mit adaptiven Formularen für staatlich verbundene Konten (Regierungsabteilungen und Behörden). Durch die Integration mit Adobe Acrobat Sign für Behörden können Partner und Regierungskunden von Adobe elektronische Signaturen in adaptiven Formularen für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig konform mit der Richtlinie „FedRAMP Moderate“ sind, was Regierungskunden von Adobe Gewissheit bietet.
* **Aktivieren der Salesforce-Integration mit Experience Manager Forms für den Datenaustausch** – Konfigurieren Sie die Integration zwischen Experience Manager Forms und der Salesforce-Anwendung unter Verwendung des OAuth 2.0-Client-Anmeldedatenflusses. Diese Funktion ermöglicht eine sichere und direkte Authentifizierung und Autorisierung der Anwendung und ermöglicht eine nahtlose Kommunikation ohne Einbindung der Benutzenden.
* **Optimierung und verbesserte Funktionalität der Workflow-Engine**: Erhöhen Sie die Leistung der Workflow-Engines, indem Sie die Anzahl der Workflow-Instanzen minimieren. Zusätzlich zu den Statuswerten `COMPLETED` und `RUNNING` unterstützt der Workflow auch drei neue Statuswerte: `ABORTED`, `SUSPENDED`, und `FAILED`.

## AEM 6.5, Service Pack 16 – 23. Februar 2023

Das neue Protokoll DASH (Dynamic Adaptive Streaming over HTTP) wurde für adaptives Bitrate-Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF, [Common Media Application Format]) eingeführt.

* Adaptives Streaming (DASH/HLS) sorgt für ein besseres Anwendererlebnis bei der Videoanzeige.
* DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weitläufig verwendet.
* Jetzt in Asien-Pazifik und Nordamerika verfügbar; in Kürze in Europa, im Nahen Osten und in Afrika verfügbar.

### [!DNL Forms]

* [Headless Adaptive Forms](https://experienceleague.adobe.com/de/docs/experience-manager-headless-adaptive-forms/using/overview) ermöglichen es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann.

* [Kernkomponenten für adaptive Formulare](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/introduction#features) sind eine Gruppe von 24 BEM-kompatiblen Open-Source-Komponenten, die auf der Grundlage der Adobe Experience Manager WCM-Kernkomponenten erstellt wurden. Diese Komponenten sind Open-Source-Komponenten und bieten Entwicklerinnen und Entwicklern die Möglichkeit, diese Komponenten einfach anzupassen und zu erweitern, um sie an den spezifischen Anforderungen ihrer Organisation auszurichten. Jede Person, die über vorhandene Fähigkeiten zum Anpassen von [WCM-Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/get-started/authoring) verfügt, kann diese Komponenten einfach anpassen und gestalten.

* Der Reader Extension-Dienst für OSGi bietet jetzt separate Optionen, um Import- und Export-Verwendungsrechte für PDF zum Importieren oder Exportieren von Daten in Adobe Acrobat Reader zu ermöglichen.
