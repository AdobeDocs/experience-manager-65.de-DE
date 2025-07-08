---
title: Kumulative wichtige Funktionen und Verbesserungen in Adobe Experience Manager 6.5.
description: Eine kumulative Liste der wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5 aus den letzten acht Service Pack-Versionen vorgenommen wurden.
content-type: reference
docset: aem65
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 01fe5b53-2244-445f-a4d0-bd58ea38b611
solution: Experience Manager
source-git-commit: 03c070f7bba1d66ce2a5309d2ab79567dbef3264
workflow-type: tm+mt
source-wordcount: '3539'
ht-degree: 71%

---

# Wichtige kumulative Funktionen und Verbesserungen

Eine kumulative Liste der wichtigsten Funktionen und Verbesserungen in Adobe Experience Manager 6.5 für frühere Service Pack-Versionen.

Siehe auch die [Versionshinweise zum neuesten Service Pack von Adobe Experience Manager 6.5](/help/release-notes/release-notes.md).


## AEM 6.5, Service Pack 23 - 22. Mai 2025

### Forms {#forms-sp23}

* [Barrierefreie Hyperlinks mit verschiedenen Textstilen in statischen PDFs](https://helpx.adobe.com/content/dam/help/de/experience-manager/6-5/forms/pdf/using-designer.pdf): Hyperlinks, die verschiedene Textstile in statischen PDFs enthalten, werden jetzt als einzelnes, barrierefreies Element getaggt. Diese Verbesserung vereinfacht die Tag-Baumstruktur sowie die Navigation der Bildschirmlesehilfe und unterstützt eine bessere Einhaltung von Vorgaben zur Barrierefreiheit.

* [Aktualisierte unterstützte Plattform-Matrix](/help/forms/using/aem-forms-jee-supported-platforms.md)

  Die neueste Version führt Aktualisierungen der unterstützten Plattform-Matrix ein, um die Kompatibilität mit neueren Technologien sicherzustellen.

   * IBM® Content Manager Client 8.7

   * MongoDB Enterprise 7.0

   * MySQL 8.4

   * Microsoft® SQL Server 2022

   * Microsoft® SQL Server JDBC-Treiber 12.8

   * Red Hat® Enterprise Linux® 9 (Kernel 4.x, 64-Bit)

* [Robuste Dateianhangskomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment): Als Sicherheitsmaßnahme verhindert die Komponente jetzt die Übermittlung von Dateien mit geänderten Erweiterungen, die versuchen, Prüfungen zulässiger Dateitypen zu umgehen. Solche Dateien werden während der Übermittlung blockiert, um sicherzustellen, dass nur gültige Dateitypen akzeptiert werden.

## AEM 6.5, Service Pack 22 - 21. November 2024

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

## AEM 6.5, Service Pack 21 - 6. Juni 2024

### [!DNL Assets]

#### Verbesserungen

Die Registerkarte „IPTC“ bietet nun Unterstützung für die Textfelder [!UICONTROL Alternativtext] und [!UICONTROL Erweiterte Beschreibung]. (Assets-34918)

#### Barrierefreiheit

* Wenn der Verarbeitungsstatus eines Assets Fehlgeschlagen oder Metadaten fehlgeschlagen ist, funktioniert die Benutzeroberfläche für Beschriftungen und Audiospuren jetzt ordnungsgemäß. (Assets-37281)
* Wenn Sie Asset-Metadaten speichern und versuchen, sie zu bearbeiten, wird jetzt der Sprachname angezeigt. (Assets-37281)

### [!DNL Forms]

Einige der wichtigsten Funktionen und Verbesserungen, die in dieser Version enthalten sind:

* **Unterstützung für OAuth-Anmeldedaten**: Neue, benutzerfreundlichere Anmeldedaten für die Server-zu-Server-Authentifizierung, die den vorhandenen Anmeldedatentyp „Service-Konto (JWT)“ ersetzt. (NPR-41994)
* [Verbesserungen des Regeleditors in AEM Forms](/help/forms/using/rule-editor-core-components.md):
   * Unterstützung für die Implementierung verschachtelter Bedingungen mit `When-then-else`-Funktionalität.
   * Überprüfen oder Zurücksetzen von Panels und Formularen, einschließlich Feldern.
   * Unterstützung für moderne JavaScript-Funktionen wie Let- und Pfeilfunktionen (ES10-Unterstützung) innerhalb der benutzerdefinierten Funktionen.
* [AutoTag-API für PDF-Barrierefreiheit](/help/forms/using/aem-document-services-programmatically.md#doc-utility-services-doc-utility-services): AEM Forms auf OSGi unterstützt jetzt die neue AutoTag-API zur Verbesserung von PDFs entsprechend den Barrierefreiheitsstandards durch Hinzufügen von Tags: Absätze und Listen. Dadurch werden PDFs für Benutzende mit Hilfstechnologien leichter zugänglich.
* **16-Bit-PNG-Unterstützung**: Der ImageToPdf-Dienst von PDF Generator unterstützt jetzt die Konversion von PNGs mit einer 16-Bit-Farbtiefe.
* **Anwenden von Artefakten auf einzelne Textblöcke in XDPs**: Mit Forms Designer können Benutzende jetzt Einstellungen für einzelne Textblöcke in XDP-Dateien konfigurieren. Mit dieser Funktion können Sie die Elemente steuern, die in den resultierenden PDFs als Artefakte behandelt werden. Diese Elemente – wie Kopf- und Fußzeilen – werden für Hilfstechnologien verfügbar gemacht. Zu den Hauptfunktionen gehören das Markieren von Textbausteinen als Artefakte und das Einbetten dieser Einstellungen in die XDP-Metadaten. Der Ausgabe-Service von Forms wendet diese Einstellungen während der PDF-Erstellung an und stellt dabei ein ordnungsgemäßes PDF/UA-Tagging sicher.
* **AEM Forms Designer ist nach dem Standard `GB18030:2022` zertifiziert**: Mit der Zertifizierung `GB18030:2022` unterstützt Forms Designer jetzt den chinesischen Unicode-Zeichensatz, was die Eingabe chinesischer Zeichen in alle bearbeitbaren Felder und Dialogfelder ermöglicht.
* [Unterstützung für die WebToPDF-Route in JEE Server](/help/forms/using/admin-help/configure-service-settings.md#generate-pdf-service-settings-generate-pdf-service-settings) Die Verwendung des PDF Generator-Services unterstützt jetzt die WebToPDF-Route zum Konvertieren von HTML-Dateien in PDF-Dokumente in JEE. Diese Unterstützung erfolgt zusätzlich zu den vorhandenen WebKit- und WebCapture-Routen (nur Windows). Während die WebToPDF-Route bereits auf OSGi verfügbar war, wurde sie auf JEE erweitert. Jetzt unterstützt der PDF Generator-Dienst sowohl auf JEE- als auch auf OSGi-Plattformen die folgenden Routen über verschiedene Betriebssysteme hinweg:
   * **Windows**: Webkit, WebCapture, WebToPDF
   * **Linux®**: Webkit, WebToPDF


## AEM 6.5, Service Pack 20 - 22. Februar 2024

### [!DNL Assets]

* Dynamic Media unterstützt jetzt das verlustfreie HEIC-Bildformat für Apple iOS/iPadOS. Siehe [fmt](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt) in der Bildbereitstellungs- und Rendering-API von Dynamic Media.
* Der Multisite Manager (MSM) unterstützt jetzt Experience Fragment-Strukturen, einschließlich Ordnern und Unterordnern, für ein effizientes Massen-Rollout von Experience Fragments in Live Copies.

### [!DNL Forms]

* **Transaktionsberichte in AEM Forms on JEE**: Für AEM Forms on JEE wurde die Funktion „Transaktionsberichte“ eingeführt. Dies ermöglicht eine umfassende Aufzeichnung von Dokumenttransaktionen wie Konvertierungen, Ausgabedarstellungen und Übermittlungen. Diese Erweiterung erhöht die Effizienz und bessere Aufzeichnungen. Die Funktion ist standardmäßig deaktiviert. Sie können sie über die Admin-Benutzeroberfläche aktivieren.
* **Höhere Sicherheit mit ECDSA-Unterstützung**: AEM Forms bietet nun eine zuverlässige Unterstützung für den Elliptic Curve Digital Signature Algorithm (ECDSA) bei JEE- und OSGi-Stacks. Benutzende können jetzt PDF-Dokumente mit erhöhter Sicherheit signieren, zertifizieren und überprüfen. Zu den unterstützten EC-Kurvenalgorithmen gehören:
   * ECDSA – Elliptische Kurve P256 mit SHA256-Digest-Algorithmus
   * ECDSA – Elliptische Kurve P384 mit SHA384-Digest-Algorithmus
   * ECDSA – Elliptische Kurve P512 mit SHA512-Digest-Algorithmus
* **Nahtlose Kompatibilität von Forms Designer mit Windows 11**: AEM Forms Designer unterstützt nun Windows 11. Dadurch werden eine reibungslose Installation und ein reibungsloser Betrieb sichergestellt. Benutzende können problemlos auf Windows 11 aktualisieren, ohne Forms Designer neu installieren zu müssen oder sich um Kompatibilitätsprobleme zu sorgen. Dies ermöglicht unterbrechungsfreie Arbeitsabläufe.
* **Verbesserte Barrierefreiheit mit der benutzerdefinierten Rolle „Beschriftung“ in AEM Forms Designer**: AEM Forms Designer umfasst nun eine benutzerdefinierte Rolle für Barrierefreiheit. Sie heißt „Beschriftung“ und ermöglicht es Benutzenden, XDPs mit personalisierten Beschriftungselementen zu erstellen. Diese Funktion verbessert die Barrierefreiheit, da Benutzende damit benutzerdefinierte Beschriftungen in ihre Dokumententwürfe integrieren können, wodurch sie die Inklusion und das Anwendererlebnis verbessern können.

## AEM 6.5, Service Pack 19 - 7. Dezember 2023

* Ermöglicht den Benutzenden des Seiteneditors bzw. der Bildkomponente die Referenzierung von Assets aus dem Remote Assets Cloud Service.  (SITES-13448, SITES-13433)
* AEM unterstützt jetzt die Server-seitige Sortierung für eine schnellere Projektnavigation in der Listenansicht. Projektknoten werden nach der von der Benutzerin bzw. dem Benutzer ausgewählten Spalte sortiert, bevor sie in der Benutzeroberfläche angezeigt werden.

### [!DNL Forms]

* **Neue Kernkomponenten für adaptive Formulare**: Es werden vertikale Registerkarten, Geschäftsbedingungen und Kontrollkästchen hinzugefügt, um die Skalierbarkeit von Formularen zu verbessern.
   * **[Kontrollkästchen-Komponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt eine Kontrollkästchen-Komponente enthalten. Sie ermöglicht Benutzenden, binäre Entscheidungen zu treffen, indem sie eine bestimmte Option auswählen oder eine Auswahl aufheben. Sie wird normalerweise als kleines Feld angezeigt, auf das geklickt oder getippt werden kann, um zwischen zwei Status zu wechseln: „aktiviert“ und „deaktiviert“. Das Kontrollkästchen ist ein gängiges Formularelement, das verwendet wird, um eine Ja/Nein- oder „true/false“-Auswahl zu treffen.

   * **[Geschäftsbedingungskomponente](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions)**: Die auf Kernkomponenten basierende adaptive Forms enthält jetzt eine Geschäftsbedingungskomponente. Formularautoren fügen diesen Abschnitt hinzu, um Benutzern die Bedingungen oder rechtlichen Vereinbarungen für den Service, das Produkt oder die Plattform anzuzeigen. Diese Komponente hat das Ziel, Benutzende über die Regeln, Vorschriften und Verpflichtungen zu informieren, denen sie zustimmen, wenn sie das Formular übermitteln.

     ![Die Komponenten „Vertikale Registerkarten“, „Geschäftsbedingungen“ und „Kontrollkästchen“](/help/forms/using/assets/forms-components.png)

   * **[Komponente „Vertikale Registerkarten“](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt Formularinhalte in einer vertikalen Liste von Registerkarten organisieren und so ein strukturiertes und navigierbares Layout bieten. Vertikale Registerkarten in einem Formular verbessern das Benutzererlebnis, indem sie die Navigation vereinfachen und Inhalte organisieren. Sie sind besonders hilfreich, wenn das Formular mehrere Abschnitte oder komplexe Informationen enthält.

* **[64-Bit-Version von AEM Forms Designer](/help/forms/using/installing-configuring-designer.md)**: Die 64-Bit-Version von AEM Forms Designer bietet eine verbesserte Leistung, Skalierbarkeit und Speicherverwaltung, um die Erstellung von Formularen zu optimieren. Mit der 64-Bit-Architektur können Sie noch größere und komplexere Projekte einfach angehen, um nahtlose Design-Workflows und eine optimierte Effizienz zu gewährleisten. Verbessern Sie Ihre Formularentwurfsfähigkeiten und nutzen Sie die Zukunft von AEM Forms Designer mit dieser innovativen Version.

* **[Verbinden eines adaptiven Formulars mit einer Microsoft® SharePoint-Liste](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)**: AEM Forms bietet eine vorkonfigurierte Integration zum direkten Versand von Formulardaten an eine SharePoint-Liste, sodass Sie die Listenfunktionen von SharePoint verwenden können. Sie können die Microsoft® SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die Übermittlungsaktion „Senden mit Formulardatenmodell“ verwenden, um ein adaptives Formular mit der SharePoint-Liste zu verbinden.

* **[Unterstützung für die Konfiguration der Eigenschaften von Datensatzdokumenten für adaptive Formularfragmente](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)**: Sie können jetzt Ihre adaptiven Formularfragmente und deren Felder im Editor für adaptive Formulare einfach anpassen.

* **64-Bit XMLFM**: Die 64-Bit-Iteration von XMLFM führt zu verbesserter Performance, Skalierbarkeit und Speicherverwaltung. Dies ist der erste native 64-Bit-Dienst, der Server-seitig bereitgestellt wird. Durch die Nutzung seiner inhärenten Fähigkeit, auf größere Speicherressourcen im Vergleich zu seinem 32-Bit-Gegenstück zuzugreifen, ermöglicht XMLFM 64-Bit die nahtlose Handhabung größerer Rendering-Workloads. Dieser Meilenstein stellt nicht nur einen Performance-Sprung dar, sondern führt auch wichtige Verbesserungen am nativen Service-Framework innerhalb des AEM Forms-Servers ein. Durch dieses Update kann der AEM Forms-Server nahtlos alle nativen 64-Bit-Services unterstützen.

## AEM 6.5, Service Pack 18 – 24. August 2023

* Assets, Dynamic Media - [Unterstützung für mehrere Untertitel und Audiospuren für Videos in Dynamic Media](/help/assets/video.md#about-msma) - Sie können nun auf einfache Weise mehrere Untertitel und mehrere Audiospuren zu einem Primärvideo hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.
* Assets – Von den Suchergebnissen aus können Sie jetzt zum Ordnerspeicherort navigieren, der ein Asset enthält, damit Sie verschiedene Asset-Management-Aufgaben ausführen können.
* Sites Polaris Picker in Inhaltsfragmenten hat eine verbesserte Leistung.
* Ermöglicht den Benutzenden des Seiteneditors bzw. der Bildkomponente die Referenzierung von Assets aus dem Remote Assets Cloud Service.
* Um ein Projekt schnell in der Listenansicht zu finden, in der sich möglicherweise viele Projekte befinden, unterstützt Adobe jetzt die Server-seitige Sortierung. Projektknoten werden nach der von Benutzenden ausgewählten Spalte im Backend sortiert, bevor sie in der Benutzeroberfläche gerendert werden.
* AEM 6.5.18.0 unterstützt MongoDB 5.0 bis 6.0.

### [!DNL Forms]

* **[Verbesserte Fehlerbehandlung mit benutzerdefinierten Fehler-Handlern im Regeleditor](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms)** – Sie können jetzt eine benutzerdefinierte Funktion (unter Verwendung der Client-Bibliothek) als Reaktion auf einen von einem externen Dienst zurückgegebenen Fehler aufrufen. Und Sie können eine maßgeschneiderte Antwort für Endbenutzerinnen und Endbenutzer bereitstellen. Oder Sie können bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst ausgefallen ist.

* **[Verbesserter Workflow-Schritt in Adobe Sign](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/workflows/aem-forms-workflow-step-reference#sign-document-step)** – Der Adobe Sign-Workflow-Schritt in AEM-Workflows ist mit den folgenden Verbesserungen verfügbar.

   * **Erweiterte Sicherheit mit Authentifizierung mit amtlichem Lichtbildausweis für Adobe Sign** - Die Authentifizierung mit amtlichem Lichtbildausweis von Adobe Acrobat Sign bietet eine zusätzliche Verifizierungsebene. Sie ermöglicht Benutzenden die Authentifizierung ihrer Identität mithilfe von amtlichem Lichtbildausweisen (Führerschein, Personalausweis, Reisepass). Durch die Nutzung von vertrauenswürdigen Identifikationsdokumenten verleiht diese Erweiterung dem Unterzeichnungsprozess ein zusätzliches Maß an Vertrauen und ist somit ideal für Szenarien, die erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Verbesserte Transparenz durch Audit-Protokoll für Adobe Sign-Dokumente** - Verwenden Sie die Audit-Protokoll-Funktion, um detaillierte Einblicke in den Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt alle Aktionen und Interaktionen im Zusammenhang mit Ihren Dokumenten umfassend aufzeichnen. Zu diesen Aktionen und Interaktionen gehören Personen, die das Dokument angesehen, bearbeitet oder signiert haben, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist entscheidend für die Einhaltung von Vorschriften, die Beilegung von Streitigkeiten und die Gewährleistung der Integrität Ihrer digitalen Vereinbarungen.


   * **Die Rollen für Empfänger von Vereinbarungen wurden über den Unterzeichner hinaus erweitert** - Mit Adobe Acrobat Sign können Sie die Rollen für Empfänger von Vereinbarungen über den Unterzeichner hinaus erweitern, um ihre Workflow-Anforderungen besser zu erfüllen. Wenn diese Option aktiviert ist, kann die Rolle jeder Empfängerin und jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei die Unterzeichnerin bzw. der Unterzeichner die Standardeinstellung ist.


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

* **Dynamic Media _Momentaufnahme_**&#x200B;ermöglicht die Vorschau von Bildmodifikatoren und Optimierungen der intelligenten Bildbearbeitung - wie WebP- oder AVIF-Ausgabe, bandbreitenabhängige Komprimierung und Skalierung des Gerätepixelverhältnisses - mithilfe von Testbildern oder Dynamic Media-URLs. Sie können dann sofort vergleichen, wie sich jede Einstellung auf die Qualität und Dateigröße auswirkt.
Siehe [Dynamic Media Snapshot](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot).
* **DASH-Streaming mit Dynamic Media** - Neues Protokoll (DASH - Dynamic Adaptive Streaming über HTTP), das für adaptives Streaming in der Dynamic Media-Videobereitstellung (mit aktiviertem CMAF) gestartet wurde. Jetzt für alle Regionen verfügbar.
* **Integration von Experience Manager Sites und Inhaltsfragmenten mit Assets Dynamic Media der nächsten Generation** - Anwender können jetzt ihre in der Cloud gehosteten Assets in Experience Manager Sites 6.5 verwenden. Sie können diese Assets On-Premise- oder Managed Services-Instanzen erstellen und bereitstellen.

### [!DNL Forms]

* **[Adaptive Forms im AEM Seiteneditor](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)** - Sie können jetzt den AEM Seiteneditor verwenden, um schnell mehrere Formulare zu Ihren Sites-Seiten zu erstellen und hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautorinnen und -autoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie die Möglichkeiten der Komponenten adaptiver Formulare nutzen, einschließlich dynamisches Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:
   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in den Container für adaptive Forms im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Forms im AEM Sites-Editor, damit Sie Formulare unabhängig von einer Sites-Seite erstellen können und diese Formulare dann auf mehreren Seiten wiederverwenden können.
   * Fügen Sie mehrere Formulare zu einer Sites-Seite hinzu, was das Benutzererlebnis optimiert und mehr Flexibilität bietet.
* **[Unterstützung von reCAPTCHA Enterprise in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)** - Unterstützung für reCAPTCHA Enterprise in Experience Manager Forms wurde hinzugefügt. Diese Funktion bietet zusätzlich zur bestehenden Google reCAPTCHA v2-Unterstützung einen erweiterten Schutz vor betrügerischen Aktivitäten und Spam.
* **[Adobe Acrobat Sign for Government wird jetzt mit Experience Manager Forms unterstützt](/help/forms/using/adobe-sign-integration-adaptive-forms.md)** - AEM Forms kann jetzt mit Adobe Acrobat Sign for Government (FedRAMP-kompatibel) integriert werden. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für E-Signaturen mit adaptiven Formularen für staatlich verbundene Konten (Regierungsabteilungen und Behörden). Die Integration mit Adobe Acrobat Sign for Government ermöglicht Adobe-Partnern und Regierungskunden die Verwendung elektronischer Signaturen in Adaptive Forms für einige der geschäftskritischsten und sensibelsten Geschäftsbereiche. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig konform mit der Richtlinie „FedRAMP Moderate“ sind, was Regierungskunden von Adobe Gewissheit bietet.
* **Salesforce-Integration mit Experience Manager Forms für den Datenaustausch aktivieren** - Konfigurieren der Integration zwischen Experience Manager Forms und der Salesforce-Anwendung mithilfe des OAuth 2.0-Flusses der Client-Anmeldeinformationen. Diese Funktion ermöglicht eine sichere und direkte Authentifizierung und Autorisierung der Anwendung und ermöglicht eine nahtlose Kommunikation ohne Einbindung der Benutzenden.
* **Optimierung und verbesserte Funktionalität der Workflow-Engine**: Erhöhen Sie die Leistung der Workflow-Engines, indem Sie die Anzahl der Workflow-Instanzen minimieren. Zusätzlich zu den Statuswerten `COMPLETED` und `RUNNING` unterstützt der Workflow auch drei neue Statuswerte: `ABORTED`, `SUSPENDED`, und `FAILED`.

## AEM 6.5, Service Pack 16 – 23. Februar 2023

Das neue Protokoll DASH (Dynamic Adaptive Streaming over HTTP) wurde für adaptives Bitrate-Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF, [Common Media Application Format]) eingeführt.

* Adaptives Streaming (DASH/HLS) sorgt für ein besseres Zuschauererlebnis bei der Videoanzeige.
* DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weitläufig verwendet.
* Jetzt in Asien-Pazifik und Nordamerika verfügbar; in Kürze in Europa, im Nahen Osten und in Afrika verfügbar.

### [!DNL Forms]

* [Headless Adaptive Forms](https://experienceleague.adobe.com/de/docs/experience-manager-headless-adaptive-forms/using/overview) ermöglichen es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann.

* [Kernkomponenten für adaptive Formulare](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/introduction#features) sind eine Gruppe von 24 BEM-kompatiblen Open-Source-Komponenten, die auf der Grundlage der Adobe Experience Manager WCM-Kernkomponenten erstellt wurden. Diese Komponenten sind Open-Source-Komponenten und bieten Entwicklern die Möglichkeit, diese Komponenten einfach anzupassen und zu erweitern, um sie an die spezifischen Anforderungen ihrer Organisation anzupassen. Jeder, der über vorhandene Fähigkeiten zum Anpassen von [WCM-Kernkomponenten](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/get-started/authoring) verfügt, kann diese Komponenten einfach anpassen und gestalten.

* Der Reader Extension-Dienst für OSGi bietet jetzt separate Optionen, um Import- und Export-Verwendungsrechte für PDF zum Importieren oder Exportieren von Daten in Adobe Acrobat Reader zu ermöglichen.

## AEM 6.5, Service Pack 15 – 24. November 2022

### [!DNL Forms]

* AEM Forms Designer ist jetzt im [spanischen Gebietsschema](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) verfügbar. 
* Sie können jetzt [OAuth2 verwenden, um sich bei Microsoft® Office 365-Mailserver-Protokollen (SMTP und IMAP) zu authentifizieren](/help/forms/using/oauth2-support-for-mail-service.md).
* Sie können die Eigenschaft [Auf dem Server erneut überprüfen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#enabling-server-side-validation-br) auf „true“ setzen, um die ausgeblendeten Felder zum Ausschließen aus dem Datensatzdokument Server-seitig zu identifizieren.
* AEM Forms Designer erfordert eine 32-Bit-Version von Visual C++ 2019 Redistributable (x86).

## AEM 6.5, Service Pack 14 – 25. August 2022

Nur Fehlerbehebungen.

## AEM 6.5, Service Pack 13 – 26. May 2022

* Verwenden eines unsichtbaren CAPTCHA in einem adaptiven Formular: Sie können jetzt ein unsichtbares CAPTCHA verwenden, um die CAPTCHA-Abfrage nur dann anzuzeigen, wenn eine verdächtige Aktivität festgestellt wird. Wenn keine verdächtige Aktivität gefunden wird, wird die CAPTCHA-Frage nicht angezeigt. Dies hilft bei der Bewertung des Ausfüllens von Formularen durch Menschen ohne Kontrollkästchenanforderungen, reduziert den Anpassungsaufwand und verbessert das Erlebnis für Endbenutzerinnen und -benutzer.

* Es wurde Unterstützung zum Abrufen von Antwort-Headern im Nachbearbeitungsprogramm des Formulardatenmodells für REST-Endpunkte hinzugefügt.

* Beim Generieren einer Übersetzungsdatei für ein adaptives Formular ist nun dieselbe Textsequenz in der generierten XLIFF-Datei identisch mit der Komponentensequenz im entsprechenden adaptiven Formular.

* Wenn Sie ein adaptives Formular lokalisieren und auch nur eine kleine Änderung am Text der Basissprache vornehmen, geht die vollständige Übersetzung für alle anderen Sprachen verloren. Das Problem wurde in [!DNL Experience Manager] 6.5.13.0 behoben.

* Verbesserungen der Barrierefreiheit für Forms:

   * Es wurde Unterstützung für Bildschirmlesehilfen hinzugefügt, um die Kopfzeile und den Hauptteil einer Tabelle als fortgesetzte und verbundene Entitäten zu erkennen. Dadurch wird Bildschirmlesehilfen die korrekte Navigation in den Tabellen erleichtert. (NPR-37139)
   * Unterstützung für Bildschirmlesehilfen wurde hinzugefügt, um die Navigation im HTML-Arbeitsbereich zu stoppen, bis ein Dialogfeld geöffnet ist.

## AEM 6.5, Service Pack 12 – 24. Februar 2022

* Nach dem Konfigurieren einer Verbindung zwischen Remote-DAM- und Sites-Bereitstellungen werden die Assets auf Remote-DAM in der Sites-Bereitstellung verfügbar gemacht. Sie können jetzt Remote-DAM-Assets oder -Ordner aktualisieren, löschen, umbenennen und verschieben. Die Aktualisierungen stehen mit etwas Verzögerung automatisch in der Sites-Bereitstellung zur Verfügung.
* Push-Rollouts von einer Live Copy-Quelle an mehrere Live Copies sind jetzt standardmäßig möglich, ohne dass eine Blueprint-Konfiguration erforderlich ist.
* Der Status laufender asynchroner Vorgänge wird jetzt auf der Benutzeroberfläche angezeigt, um zu verhindern, dass versehentlich mehrere asynchrone Vorgänge auf demselben Pfad ausgelöst werden.
* Es wird Unterstützung für die IMS-basierte Authentifizierung für Analytics 2.0-APIs bereitgestellt.
* API-Unterstützung für JSON-Experience Fragments vom Angebotstyp.
* In IMS wird jetzt die Angebotsanforderung für Löschangebote (Experience Fragment-API) bereitgestellt.
* Das integrierte Repository (Apache Jackrabbit Oak) verbleibt bei 1.22.9.
