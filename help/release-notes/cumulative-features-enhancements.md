---
title: Kumulative wichtige Funktionen und Verbesserungen in Adobe Experience Manager 6.5.
description: Eine kumulative Liste der wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5 aus den letzten acht Service Pack-Versionen vorgenommen wurden.
content-type: reference
docset: aem65
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 01fe5b53-2244-445f-a4d0-bd58ea38b611
solution: Experience Manager
source-git-commit: 10268f617b8a1bb22f1f131cfd88236e7d5beb47
workflow-type: ht
source-wordcount: '2334'
ht-degree: 100%

---

# Wichtige kumulative Funktionen und Verbesserungen

Eine kumulative Liste der wichtigsten Funktionen und Verbesserungen, die in Adobe Experience Manager 6.5 für die letzten acht Service Pack-Versionen vorgenommen wurden.

Siehe auch die [Versionshinweise zum neuesten Service Pack von Adobe Experience Manager 6.5](/help/release-notes/release-notes.md).

## AEM 6.5, Service Pack 18 – 7. Dezember 2023

* Ermöglicht den Benutzenden des Seiteneditors bzw. der Bildkomponente die Referenzierung von Assets aus dem Remote Assets Cloud Service.  (SITES-13448, SITES-13433)
* AEM unterstützt jetzt die Server-seitige Sortierung für eine schnellere Projektnavigation in der Listenansicht. Projektknoten werden nach der von der Benutzerin bzw. dem Benutzer ausgewählten Spalte sortiert, bevor sie in der Benutzeroberfläche angezeigt werden.

### [!DNL Forms]

* **Neue Kernkomponenten für adaptive Formulare**: Es werden vertikale Registerkarten, Geschäftsbedingungen und Kontrollkästchen hinzugefügt, um die Skalierbarkeit von Formularen zu verbessern.
   * **[Kontrollkästchen-Komponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html?lang=de)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt eine Kontrollkästchen-Komponente enthalten. Sie ermöglicht Benutzenden, binäre Entscheidungen zu treffen, indem sie eine bestimmte Option auswählen oder eine Auswahl aufheben. Sie wird normalerweise als kleines Feld angezeigt, auf das geklickt oder getippt werden kann, um zwischen zwei Status zu wechseln: „aktiviert“ und „deaktiviert“. Das Kontrollkästchen ist ein gängiges Formularelement, das verwendet wird, um eine Ja/Nein- oder „true/false“-Auswahl zu treffen.

   * **[Komponente „Geschäftsbedingungen“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html?lang=de)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt eine Komponente für Geschäftsbedingungen enthalten. Sie ermöglicht es Formularautorinnen und -autoren, einen bestimmten Abschnitt innerhalb des Formulars einzuführen, in dem den Benutzenden die Nutzungsbedingungen im Zusammenhang mit der Verwendung eines Dienstes, Produkts oder einer Plattform präsentiert werden. Diese Komponente hat das Ziel, Benutzende über die Regeln, Vorschriften und Verpflichtungen zu informieren, denen sie zustimmen, wenn sie das Formular übermitteln.

     ![Die Komponenten „Vertikale Registerkarten“, „Geschäftsbedingungen“ und „Kontrollkästchen“](/help/forms/using/assets/forms-components.png)

   * **[Komponente „Vertikale Registerkarten“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html?lang=de)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt Formularinhalte in einer vertikalen Liste von Registerkarten organisieren und so ein strukturiertes und navigierbares Layout bieten. Die Verwendung von vertikalen Registerkarten in einem Formular kann das gesamte Benutzererlebnis verbessern, indem die Navigation vereinfacht und die Organisation des Formularinhalts verbessert wird, insbesondere in Situationen, in denen ein Formular mehrere Abschnitte oder komplexe Informationen enthält.

* **[64-Bit-Version von AEM Forms Designer](/help/forms/using/installing-configuring-designer.md)**: Die 64-Bit-Version von AEM Forms Designer bietet eine verbesserte Leistung, Skalierbarkeit und Speicherverwaltung, um die Erstellung von Formularen zu optimieren. Mit der 64-Bit-Architektur können Sie noch größere und komplexere Projekte einfach angehen, um nahtlose Design-Workflows und eine optimierte Effizienz zu gewährleisten. Verbessern Sie Ihre Formularentwurfsfähigkeiten und nutzen Sie die Zukunft von AEM Forms Designer mit dieser innovativen Version.

* **[Verbinden eines adaptiven Formulars mit einer Microsoft® SharePoint-Liste](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)**: AEM Forms bietet eine vorkonfigurierte Integration zum direkten Versand von Formulardaten an eine SharePoint-Liste, sodass Sie die Listenfunktionen von SharePoint verwenden können. Sie können die Microsoft® SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die Übermittlungsaktion „Senden mit Formulardatenmodell“ verwenden, um ein adaptives Formular mit der SharePoint-Liste zu verbinden.

* **[Unterstützung zum Konfigurieren der Eigenschaften des Datensatzdokuments für adaptive Formularfragmente](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)**: Sie können jetzt Ihre adaptiven Formularfragmente und deren Felder im Editor für adaptive Formulare einfach anpassen.

* **64-Bit XMLFM**: Die 64-Bit-Iteration von XMLFM führt zu verbesserter Performance, Skalierbarkeit und Speicherverwaltung. Dies ist der erste native 64-Bit-Dienst, der Server-seitig bereitgestellt wird. Durch die Nutzung seiner inhärenten Fähigkeit, auf größere Speicherressourcen im Vergleich zu seinem 32-Bit-Gegenstück zuzugreifen, ermöglicht XMLFM 64-Bit die nahtlose Handhabung größerer Rendering-Workloads. Dieser Meilenstein stellt nicht nur einen Performance-Sprung dar, sondern führt auch wichtige Verbesserungen am nativen Service-Framework innerhalb des AEM Forms-Servers ein. Mit diesem Update wird der AEM Forms-Server für die nahtlose Unterstützung nativer 64-Bit-Dienste ausgestattet.

## AEM 6.5, Service Pack 18 – 24. August 2023

* Assets, Dynamic Media: [-Unterstützung für mehrere Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/video.md#about-msma) – Sie können jetzt ganz einfach mehrere Untertitel und mehrere Audiospuren zu einem primären Video hinzufügen.  Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.
* Assets – Von den Suchergebnissen aus können Sie jetzt zum Ordnerspeicherort navigieren, der ein Asset enthält, damit Sie verschiedene Asset-Management-Aufgaben ausführen können.
* Sites Polaris Picker in Inhaltsfragmenten hat eine verbesserte Leistung.
* Ermöglicht den Benutzenden des Seiteneditors bzw. der Bildkomponente die Referenzierung von Assets aus dem Remote Assets Cloud Service.
* Um in der Listenansicht, in der sich möglicherweise viele Projekte in Ihrem System befinden, schnell ein Projekt zu finden, unterstützt Adobe jetzt die Server-seitige Sortierung. Projektknoten werden nach der von Benutzenden ausgewählten Spalte im Backend sortiert, bevor sie in der Benutzeroberfläche gerendert werden.
* AEM 6.5.18.0 unterstützt MongoDB 5.0 bis 6.0.

### [!DNL Forms]

* **[Verbesserte Fehlerbehandlung mit benutzerdefinierten Fehler-Handlern im Regeleditor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html?lang=de)** – Sie können jetzt eine benutzerdefinierte Funktion (unter Verwendung der Client-Bibliothek) als Reaktion auf einen von einem externen Dienst zurückgegebenen Fehler aufrufen. Und Sie können eine maßgeschneiderte Antwort für Endbenutzerinnen und Endbenutzer bereitstellen. Oder Sie können bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst ausgefallen ist.

* **[Verbesserter Workflow-Schritt in Adobe Sign](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html?lang=de#sign-document-step)** – Der Adobe Sign-Workflow-Schritt in AEM-Workflows ist mit den folgenden Verbesserungen verfügbar.

   * **Verbesserte Sicherheit mit ID-basierter Authentifizierung für Adobe Sign** – Die ID-basierte Authentifizierung von Adobe Acrobat Sign bietet eine zusätzliche Verifizierungsebene. Sie ermöglicht Benutzenden die Authentifizierung ihrer Identität mithilfe von amtlichem Lichtbildausweisen (Führerschein, Personalausweis, Reisepass). Durch die Nutzung von vertrauenswürdigen Identifikationsdokumenten verleiht diese Erweiterung dem Unterzeichnungsprozess ein zusätzliches Maß an Vertrauen und ist somit ideal für Szenarien, die erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Verbesserte Transparenz mit dem Audit-Protokoll für Adobe Sign-Dokumente** – Verwenden Sie die Audit-Protokoll-Funktion, um detaillierte Einblicke in den Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt eine umfassende Aufzeichnung aller Aktionen und Interaktionen führen, die mit Ihren Dokumenten verbunden sind. Dazu gehören Details wie etwa die Personen, die das Dokument angesehen, bearbeitet oder unterschrieben haben, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist entscheidend für die Einhaltung von Vorschriften, die Beilegung von Streitigkeiten und die Gewährleistung der Integrität Ihrer digitalen Vereinbarungen.


   * **Erweiterte Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Unterzeichnenden hinaus** – Adobe Acrobat Sign bietet die Möglichkeit, die Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Personen hinaus zu erweitern, die unterzeichnet haben, um die Anforderungen an den Workflow besser zu erfüllen.  Wenn diese Option aktiviert ist, kann die Rolle jeder Empfängerin und jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei die Unterzeichnerin bzw. der Unterzeichner die Standardeinstellung ist.


* **[AEM Forms auf JEE-Vollinstallationsprogramm](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/aem-forms-jee-supported-platforms.html?lang=de)** – Das Service Pack enthält ein vollständiges Installationsprogramm für AEM Forms auf JEE, das mehrere neue Software-Kombinationen unterstützt, darunter:
   * Microsoft® Windows Server 2022
   * Microsoft® Active Directory 2022
   * Oracle WebLogic 14C unter Windows Server 2022
   * Red Hat® JBoss® 7.4.10
   * MongoDB 6.0 <!-- it was previously MongoDB 4.4 -->
   * MySQL JDBC Connector 8

Wenn Sie eine Installation durchführen oder die Verwendung der neuesten Software für Ihre AEM 6.5 Forms auf JEE-Umgebung planen, empfiehlt Adobe die Verwendung des Vollinstallationsprogramms für AEM 6.5.18.0 Forms auf JEE. Die vollständige Liste der neu hinzugefügten und veralteten Software finden Sie in der Dokumentation zu AEM Forms auf JEE oder AEM Forms auf OSGi.

## AEM 6.5, Service Pack 17 – 25. Mai 2023

* **Verbesserungen des Sucherlebnisses**: Sie können jetzt schnell die folgenden Vorgänge für die Assets ausführen, die in den Suchergebnissen angezeigt werden:
   * Erstellen eines Workflows
   * Version erstellen
   * Zuordnung für Assets herstellen oder aufheben

  Sie müssen nicht erst zum Asset-Speicherort navigieren und seine Eigenschaften anzeigen, um diese Vorgänge durchzuführen.
* **Dynamic Media _Snapshot_**– Experimentieren Sie mit Testbildern oder Dynamic Media-URLs, um die Ausgabe verschiedener Bildmodifikatoren zu sehen, und optimieren Sie die intelligente Bildbearbeitung für Dateigröße (mit WebP- und AVIF-Bereitstellung), Netzwerkbandbreite und Pixel-Seitenverhältnis der Geräte. Siehe [Dynamic Media Snapshot](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html?lang=de).
* **DASH Streaming mit Dynamic Media** – Neue Protokollunterstützung (DASH – Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF). Ist jetzt für alle Regionen verfügbar und [kann über ein Support-Ticket aktiviert werden](/help/assets/video.md#enable-dash-on-your-account-enable-dash).
* **Integration von Experience Manager Sites und Inhaltsfragmenten in Assets der nächsten Generation für Dynamic Media** – Benutzerinnen und Benutzer von Experience Manager Assets as a Cloud Service für Dynamic Media der nächsten Generation können diese in der Cloud gehosteten Assets jetzt für die Bearbeitung und Bereitstellung mit On-Premise- oder Managed Services-Instanzen von Experience Manager Sites 6.5 verwenden.

### [!DNL Forms]

* **[Adaptive Formulare im AEM-Seiteneditor](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)**: Sie können jetzt den AEM-Seiteneditor verwenden, um schnell mehrere Formulare zu erstellen und sie zu Ihren Sites-Seiten hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautorinnen und -autoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie die Möglichkeiten der Komponenten adaptiver Formulare nutzen, einschließlich dynamisches Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:
   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in die Container-Komponente für adaptive Formulare im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Formulare im AEM Sites-Editor, damit Sie unabhängig von einer Sites-Seite Formulare erstellen können. So können Sie solche Formulare auf mehreren Seiten wiederverwenden.
   * Optimieren Sie das Anwendererlebnis und bieten Sie mehr Flexibilität, indem Sie mehrere Formulare zu einer Sites-Seite hinzufügen.
* **[Unterstützung für reCAPTCHA Enterprise in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)**: Es wurde Unterstützung für reCAPTCHA Enterprise in Experience Manager Forms hinzugefügt, um zusätzlich zur bestehenden Google reCAPTCHA v2-Unterstützung weiteren Schutz vor betrügerischen Aktivitäten und Spam zu bieten.
* **[Unterstützung für Adobe Acrobat Sign für Regierungsbehörden mit Experience Manager Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)**: AEM Forms kann jetzt mit Adobe Acrobat Sign für Regierungsbehörden (FedRAMP-konform) integriert werden. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für E-Signaturen mit adaptiven Formularen für staatlich verbundene Konten (Regierungsabteilungen und Behörden). Durch die Integration mit Adobe Acrobat Sign für Behörden können Partnerinnen oder Partner und Regierungskundschaft von Adobe elektronische Signaturen in adaptiven Formularen für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig mit der Einhaltung der FedRAMP Moderate Compliance konform sind, sodass die Regierungskundschaft von Adobe beruhigt sein kann.
* **Aktivieren der Salesforce-Integration mit Experience Manager Forms für den Datenaustausch**: Konfigurieren Sie die Integration zwischen Experience Manager Forms und der Salesforce-Applikation unter Verwendung des OAuth 2.0-Client-Anmeldedatenflusses. Diese Funktion ermöglicht eine sichere und direkte Authentifizierung und Autorisierung der Anwendung und ermöglicht eine nahtlose Kommunikation ohne Einbindung der Benutzenden.
* **Optimierung und verbesserte Funktionalität der Workflow-Engine**: Erhöhen Sie die Leistung der Workflow-Engines, indem Sie die Anzahl der Workflow-Instanzen minimieren. Zusätzlich zu den Statuswerten `COMPLETED` und `RUNNING` unterstützt der Workflow auch drei neue Statuswerte: `ABORTED`, `SUSPENDED`, und `FAILED`.

## AEM 6.5, Service Pack 16 – 23. Februar 2023

Die Unterstützung des neuen Protokolls DASH (Dynamic Adaptive Streaming over HTTP) wurde für adaptives Bit-Rate-Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF, [Common Media Application Format]) eingeführt.

* Adaptives Streaming (DASH/HLS) sorgt für ein besseres Anwendererlebnis bei der Videoanzeige.
* DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weitläufig verwendet.
* Jetzt in Asien-Pazifik und Nordamerika verfügbar (kann über ein Support-Ticket aktiviert werden); in Kürze in Europa, im Nahen Osten und in Afrika erhältlich.

Siehe [Aktivieren von DASH in Ihrem Konto](/help/assets/video.md#enable-dash).

### [!DNL Forms]

* [Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) ermöglichen es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann.

* [Kernkomponenten für adaptive Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de#features) sind eine Gruppe von 24 BEM-kompatiblen Open-Source-Komponenten, die auf der Grundlage der Adobe Experience Manager WCM-Kernkomponenten erstellt wurden. Diese Komponenten sind Open-Source-Komponenten und bieten Entwicklerinnen und Entwicklern die Möglichkeit, diese Komponenten einfach anzupassen und zu erweitern, um sie an die spezifischen Anforderungen ihrer Organisation anzupassen. Jeder, der über vorhandene Fähigkeiten zum Anpassen von [WCM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/authoring.html?lang=de) verfügt, kann diese Komponenten einfach anpassen und gestalten.

* Der Reader Extension-Dienst für OSGi bietet jetzt separate Optionen, um Import- und Export-Verwendungsrechte für PDF zum Importieren oder Exportieren von Daten in Adobe Acrobat Reader zu ermöglichen.

## AEM 6.5, Service Pack 15 – 24. November 2022

### [!DNL Forms]

* AEM Forms Designer ist jetzt im [spanischen Gebietsschema](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=de) verfügbar. 
* Sie können jetzt [OAuth2 verwenden, um sich bei Microsoft® Office 365-Mailserver-Protokollen (SMTP und IMAP) zu authentifizieren](/help/forms/using/oauth2-support-for-mail-service.md).
* Sie können die Eigenschaft [Auf dem Server erneut überprüfen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=de#enabling-server-side-validation-br) auf „true“ setzen, um die ausgeblendeten Felder zum Ausschließen aus dem Datensatzdokument serverseitig zu identifizieren.
* AEM Forms Designer erfordert die 32-Bit-Version von Visual C++ 2019 Redistributable (x86).

## AEM 6.5, Service Pack 14 – 25. August 2022

Nur Fehlerbehebungen.

## AEM 6.5, Service Pack 13 – 26. May 2022

* Unsichtbares CAPTCHA in einem adaptiven Formular verwenden: Sie können jetzt ein unsichtbares CAPTCHA verwenden, um die CAPTCHA-Frage nur im Falle einer verdächtigen Aktivität anzuzeigen. Wenn keine verdächtige Aktivität gefunden wird, wird die CAPTCHA-Frage nicht angezeigt. Dies hilft bei der Bewertung des Ausfüllens von Formularen durch Menschen ohne Kontrollkästchenanforderungen, reduziert den Anpassungsaufwand und verbessert das Erlebnis für Endbenutzerinnen und -benutzer.

* Es wurde Unterstützung zum Abrufen von Antwort-Headern im Nachbearbeitungsprogramm des Formulardatenmodells für REST-Endpunkte hinzugefügt.

* Bei der Erstellung einer Übersetzungsdatei für ein adaptives Formular ist nun die gleiche Abfolge von Texten in der generierten XLIFF-Datei identisch mit der Abfolge der Komponenten im entsprechenden adaptiven Formular.

* Wenn Sie ein adaptives Formular lokalisierten und auch nur eine kleine Änderung am Text in der Basissprache vornahmen, ging die komplette Übersetzung für alle anderen Sprachen verloren. Das Problem wurde in [!DNL Experience Manager] 6.5.13.0 behoben.

* Verbesserungen der Barrierefreiheit für Forms:

   * Es wurde Unterstützung für Bildschirmlesehilfen hinzugefügt, um Kopfzeilen und Körper einer Tabelle als fortgesetzte und verbundene Einheiten zu erkennen. Dadurch wird Bildschirmlesehilfen die korrekte Navigation in den Tabellen erleichtert. (NPR-37139)
   * Es wurde Unterstützung für Bildschirmlesehilfen hinzugefügt, um die Navigation im HTML-Arbeitsbereich zu stoppen, bis ein Dialogfeld geöffnet ist.

## AEM 6.5, Service Pack 12 – 24. Februar 2022

* Nach dem Konfigurieren einer Verbindung zwischen Remote-DAM- und Sites-Bereitstellungen werden die Assets auf Remote-DAM in der Sites-Bereitstellung verfügbar gemacht. Sie können jetzt Remote-DAM-Assets oder -Ordner aktualisieren, löschen, umbenennen und verschieben. Die Aktualisierungen stehen mit etwas Verzögerung automatisch in der Sites-Bereitstellung zur Verfügung.
* Push-Rollouts von einer Live Copy-Quelle an mehrere Live Copies sind jetzt standardmäßig möglich, ohne dass eine Blueprint-Konfiguration erforderlich ist.
* Der Status laufender asynchroner Vorgänge wird jetzt auf der Benutzeroberfläche angezeigt, um zu verhindern, dass versehentlich mehrere asynchrone Vorgänge auf demselben Pfad ausgelöst werden.
* Es wird Unterstützung für die IMS-basierte Authentifizierung für Analytics 2.0-APIs bereitgestellt.
* API-Unterstützung für JSON-Experience Fragments vom Angebotstyp.
* In IMS wird jetzt die Angebotsanforderung für Löschangebote (Experience Fragment-API) bereitgestellt.
* Das integrierte Repository (Apache Jackrabbit Oak) verbleibt weiterhin auf 1.22.9.
