---
title: Einführung in das Verwalten von Formularen
seo-title: Einführung in das Verwalten von Formularen
description: AEM Forms bietet Tools zum Verwalten adaptiver Formulare und zugehöriger Assets. Dieser Artikel stellt Ihnen die wichtigsten Formularverwaltungsfunktionen und Elemente der Benutzeroberfläche vor.
seo-description: AEM Forms bietet Tools zum Verwalten adaptiver Formulare und zugehöriger Assets. Dieser Artikel stellt Ihnen die wichtigsten Formularverwaltungsfunktionen und Elemente der Benutzeroberfläche vor.
uuid: 2275a0b6-b31e-4d8e-8154-ccdfff3705aa
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager, introduction
discoiquuid: c0e4c9bb-e12a-4f9a-a8fa-1a8ad41d3995
docset: aem65
exl-id: 3e063456-7f96-483d-86a3-6a414746db8a
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1593'
ht-degree: 67%

---

# Einführung in das Verwalten von Formularen {#introduction-to-managing-forms}

AEM [!DNL Forms] bietet eine vereinfachte, aber leistungsstarke Benutzeroberfläche zum Erstellen und Verwalten von Formularen, Dokumenten, Designs, Briefen, Dokumentfragmenten, Datenwörterbüchern und zugehörigen Assets. Es vereinfacht die Verwaltung des gesamten Formularzyklusvon Formularen, Dokumente und damit zusammenhängenden Assets – vom Desktop eines Entwicklers bis zur Bereitstellung auf einem  Portalserver für Endbenutzer. Sie können die AEM [!DNL Forms]-Benutzeroberfläche für Folgendes verwenden:

* Zugriff auf AEM [!DNL Forms]-Komponenten
* Zugriff auf AEM [!DNL Forms]-Konfigurationen

>[!NOTE]
>
>Ausführliche Informationen zu anderen AEM Tools und Optionen finden Sie unter [Authoring](/help/sites-authoring/author.md).

## Auf AEM Forms-Komponenten zugreifen {#access-aem-forms-components}

Neben anderen Optionen zum Erstellen von Formularen, Dokumenten und verknüpften Asstes bietet AEM Optionen zum Erstellen von Sites, Asstes, zum Verwalten einer AEM-Instanz und mehr. Sie können auf das Experience Manager-Logo ![adobeexperiencemanager](assets/adobeexperiencemanager.png) klicken, um zu allen verfügbaren Tools zu navigieren. Zusätzlich zu Konsolen von anderen Komponenten enthält es auch Links zu AEM [!DNL Forms]. Um zu AEM [!DNL Forms] zu navigieren, klicken Sie auf das Experience Manager-Logo ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > navigation ![compass](assets/compass.png) > **[!UICONTROL Forms]**. Links der folgenden Konsolen werden angezeigt:

* Formulare und Dokumente
* Designs
* Briefe
* Dokumentfragmente
* Datenwörterbücher

   ![AEM Forms-Konsole](assets/aem_forms_console_new.png)

### Formulare und Dokumente  {#forms-documents}

Formulare und Dokumente bietet Optionen zum Erstellen einer interaktiven Kommunikation, adaptiven Formularen, adaptiven Formularfragmenten und Formularsätzen. Nur für AEM [!DNL Forms] auf JEE bietet Forms &amp; Documents eine Option zum Importieren von Dateien aus dem lokalen Speicher und Synchronisieren AEM [!DNL Forms] Assets mit Workbench.

Die Schaltfläche &quot;Erstellen&quot;ist der Ausgangspunkt für das Erstellen oder Hochladen AEM [!DNL Forms]-Assets. Sie bietet Ihnen Optionen zum Erstellen:

* **Interaktive Kommunikation**: Eine interaktive Kommunikation ist eine personalisierte, interaktive und gerätefreundliche HTML-basierte digitale Korrespondenz, Anweisung oder Dokument. Interaktive Kommunikationen sind responsiv, d. h., ihr Layout und Design passt sich automatisch an das Gerät und die Einstellungen des Benutzers an. Detaillierte Informationen finden Sie unter [Interaktive Kommunikation - Übersicht](/help/forms/using/interactive-communications-overview.md)

* **Adaptives Formular:** Ein adaptives Formular ist ein ansprechendes und interaktives Formular. Sie können adaptive Formulare erstellen, die sich dynamisch an Benutzereingaben anpassen, indem Felder oder Abschnitte je nach Antwort, Gerät oder Arbeitsumgebung des Benutzers hinzugefügt oder entfernt werden. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung zum Erstellen adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

* **Adaptive Formularfragmente:** Zwar wurde jedes Formular für einen bestimmten Zweck entwickelt, aber es gibt gängige Segmente in den meisten Formularen (z. B. für persönliche Angaben wie Name und Anschrift, Familienmitglieder, Einkommen usw.). Sie können ein individuelles Asset für derartige Abschnitte erstellen.  Diese wiederverwendbaren, eigenständigen Segmente werden als adaptive Formularfragmente bezeichnet. Weitere Informationen finden Sie unter [Adaptive Formularfragmente](../../forms/using/adaptive-form-fragments.md).

* **Formularsatz**: Ein Formularsatz ist eine Sammlung von HTML5-Formularen, die zusammen gruppiert sind und als einzelner Formularsatz dem Endbenutzern präsentiert wird. Wenn der Benutzer ein Formularsatz ausfüllt, werden diese Informationen von einem Formular zu einem anderen übertragen. Am Ende kann ein Benutzer alle Formulare mit nur einem Klick als einzelne Entität senden. Weitere Informationen finden Sie unter[ Formularsatz in AEM Forms](../../forms/using/formset-in-aem-forms.md).

* **Ordner:**[!DNL Forms]Die Benutzeroberfläche von AEM verwendet Ordner zum Anordnen von Assets. Sie unterstützt zwei Typen von Ordnern:

   * **Allgemeine Ordner:**[!DNL Forms]Diese Ordner werden für Elemente verwendet, die in der Benutzeroberfläche von AEM erstellt werden. Diese Ordner haben keine feste Ordnerstruktur. Sie können sie umbenennen, Unterordner erstellen und adaptive Formulare, interaktive Kommunikation adaptive Formularfragmente, Formularvorlagen (XDPs), PDF-Formulare, Dokumente und verwandte Assets in diesen Ordnern erstellen.
   * **Workflow-Ordner von**[!DNL Forms]: Diese Ordner werden erstellt, wenn Workbench-Prozesse (LiveCycle-Archieve) mit der Benutzeroberfläche von AEM Forms migriert und synchronisiert werden. Sie dürfen sie nicht umbenennen, einen Unterordner erstellen, eine interaktive Kommunikation erstellen, ein adaptives Formularfragment oder eine interaktive Kommunikation erstellen. Es ist auch nicht zulässig, einen Versionsordner zu löschen oder ein adaptives Formular, ein adaptives Formularfragment oder eine interaktive Kommunikation parallel zum Versionsordner zu erstellen und hochzuladen.

   ![Ordner](assets/folders.png)

   **A.** Ordner &quot;Allgemeiner&quot;Ordner  **B.** Forms Workflow

Der Formular &amp; Dokumente-Bereich bietet auch Optionen für Folgendes:

* **Importieren von Dateien vom lokalen Speicherort:** Sie können PDF Formulare &amp; Dokumente importieren, Formularvorlagen (XFA-Formulare) und andere Ressourcen (Bild und XML-Schema für XSDs) importieren. Eine schrittweise Anleitung finden Sie unter [Importieren und Exportieren von Assets in AEM Forms](../../forms/using/import-export-forms-templates.md).
* **Syncchronisieren von AEM Forms-Assets mitWorkbench:** Sie können die Option „Dateien von Workbench“ verwenden, um Assets zwischen der Benutzeroberfläche von AEM Forms und Workbench zu synchronisieren. Dadurch wird sichergestellt, dass alle Assets in der AEM [!DNL Forms]-Benutzeroberfläche und in der CRX-Repository-Asset-Auswahl von Workbench verfügbar sind.

### Designs  {#themes}

Zu einem Design gehört die Formatierung von Details für Komponenten und Bereiche. Design haben eine unabhängige Identität. Daher können Sie ein Design für mehrere adaptive Formulare wierverwenden. Sie können die Stile für eine Komponente festlegen oder CSS-Eigenschaften für die verschiedenen Komponenten in Ihrem Formular ändern. Die Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz und Größe. Sie können Anpassungen in einem Design speichern und diese als Voreinstellung auf Komponenten des Formulars übertragen. Wenn Sie das Design zu einem Formular hinzufügen, bestimmt der festgelegte Stil die entsprechenden Komponenten des Formulars. Mit AEM 6.2 [!DNL Forms] können Sie Designs erstellen und sie auf Ihre Formulare anwenden.

Weitere Informationen finden Sie unter [Designs in AEM Forms](../../forms/using/themes.md).

### Briefe  {#letters}

Ein AEM [!DNL Forms]-Brief ist eine sichere, personalisierte und interaktive Korrespondenz. Sie können AEM [!DNL Forms] verwenden, um schnell Briefe (auch als Korrespondenzen bezeichnet) aus vorab genehmigten und benutzerdefinierten Inhalten in einem optimierten Prozess zusammenzustellen.

Weitere Informationen finden Sie unter [Erstellen von Briefen](../../forms/using/create-letter.md).

### Dokumentfragmente {#document-fragments}

Dokumentfragmente sind wiederverwendbare Teile/Komponenten einer Korrespondenz, mit der Sie Briefe/Korrespondenz erstellen können. Die Dokumentfragmente sind Texte, Listen, Bedingungen und Layoutfragmente. Detaillierte Informationen zu Dokumentfragmenten finden Sie unter [Erstellen von Fragmenten](/help/forms/using/document-fragments.md).

### Datenwörterbücher {#data-dictionaries}

In der Regel müssen Geschäftsbenutzer keine Kenntnisse über Metadatendarstellungen wie XSD (XML-Schema) und Java-Klassen haben. Sie müssen allerdings in der Regel Zugriff auf diese Datenstrukturen und Attribute haben, um Lösungen erstellen zu können. AEM [!DNL Forms] verwendet Datenwörterbuch, das es Geschäftsbenutzern ermöglicht, Informationen aus Back-End-Datenquellen zu verwenden, ohne technische Details zu den zugrunde liegenden Datenmodellen zu kennen.

Detaillierte Informationen zum Erstellen und Verwenden von Datenwörterbüchern finden Sie unter [Erstellen von Datenwörterbüchern](../../forms/using/data-dictionary.md).

## Zugriff auf AEM [!DNL Forms] Konfigurationen {#accessing-aem-forms-configurations}

AEM Tools-Bereich enthält Tools für verschiedene Komponenten. Um zu AEM Forms-spezifischen Tools zu navigieren, klicken Sie auf das Experience Manager-Logo ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > tools ![hammer](assets/hammer.png) > **[!UICONTROL Forms]**. Tools zum Durchführen folgender Funktionen werden angezeigt:

* **Konfigurieren eines überwachten Ordners:** Ein Administrator kann einen Netzwerkordner konfigurieren, der als überwachter Ordner bezeichnet wird, sodass ein vorkonfigurierter Dienstvorgang zur Verarbeitung einer Datei gestartet wird, wenn ein Benutzer eine Datei (z. B. eine PDF-Datei) in diesem überwachten Ordner ablegt. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren eines überwachten Ordners](/help/forms/using/creating-configure-watched-folder.md).
* **Offline-Dienst für die Forms App konfigurieren:** Der Offlinedienst für die AEM  [!DNL Forms] App speichert die Pfade oder URLs der in einem Formular verwendeten Ressourcen zwischen. Durch das Zwischenspeichern der Pfa oder URLs der in einem Formular verwendeten Ressourcen wird die serverseitige Leistung verbessert. Informationen zum Konfigurieren der serverseitigen Offline-Komponente der AEM Forms-App finden Sie unter [Arbeiten im Offline-Modus](/help/forms/using/work-offline-mode.md).

   ![AEM Forms-Tools](assets/aem_forms_tools_new.png)

* **Konfigurieren von PDF Generator:**[!DNL Forms] Ein Administrator kann AEM PDF Generator-Einstellungen konfigurieren, Benutzerkonten hinzufügen und Konfiguration in PDF Generator importieren oder exportieren. 
* **Correspondence Management-Assets veröffentlichen:**[!DNL Forms] Mit AEM können Sie sofort alle Briefe, Dokumentfragmente, und Datenwörterbücher und verknüpfte Abhängigkeiten von einer Autorinstanz veröffentlichen. Die veröffentlichten Assets umfassen sämtliche Correspondence Management-Assets und ihre zugehörigen Abhängigkeiten. Detaillierte Informationen finden Sie unter [Veröffentlichen und Rückgängigmachen der Veröffentlichung von Formularen und Dokumenten](../../forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets).
* **Correspondence Management-Assets exportieren:** Sie können alle Correspondence Management-Assets und die zugehörigen Abhängigkeiten als Paket von einer AEM  [!DNL Forms] Instanz herunterladen. Detaillierte Informationen finden Sie unter [Importieren und Exportieren von Assets in AEM Forms](../../forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## Häufige Elemente der Benutzeroberfläche {#commonelements}

* **Linke Leiste:** Sie können auf das linke Schienensymbol klicken,  ![](assets/railleftpng.png) um die Funktionen Timeline und Verweise von AEM anzuzeigen  [!DNL Forms].

   * **Zeitleiste:** Sie können Kommentare zu einem Asset hinzufügen, das für Review in der Zeitleiste verfügbar ist. Detaillierte Anweisungen finden Sie unter [Erstellen und Verwalten von Überprüfungen von Assets in Formularen](../../forms/using/create-reviews-forms.md).
   * **Verweise:** Ein AEM  [!DNL Forms] Asset kann in mehreren AEM  [!DNL Forms] Assets verwendet werden. Ein Dokumentfragment kann beispielsweise in mehreren Briefen verwendet werden. Referenzen sind eine Liste von Assets (andere Formulare oder Ressourcen), in denen das ausgewählte Asset verwendet wird, sowie die Liste anderer Assets, die das ausgewählte Asset verwendet.

* **Breadcrumbs:** Ein Breadcrumb gibt den Titel der aktuellen Konsole oder des Ordners an. Sie können auf die Breadcrumb-Option klicken, um zwischen den Ordnerebenen, die höher in der Hierarchie sind, zu navigieren.
* **Ansichtschalter:** Sie können auf den Ansichtschalter klicken, um  ![](assets/viewlist.png) den Viewer oder  ![](assets/viewcard.png) den Viewer zu öffnen und schnell zwischen Listen- und Kartenansicht zu wechseln. Weitere Informationen zu allgemeinen Komponenten der Benutzeroberfläche finden Sie unter [Authoring](/help/sites-authoring/author.md).
* **Suche:** Die Suche nach der  ![](assets/search.png) Suchoption bietet die Möglichkeit, schnell nach den benötigten Inhalten und Tools zu suchen und diese aufzurufen. Geben Sie den Namen des Inhalts oder der Produktfunktion ein und wählen Sie aus den Vorschlägen aus, z. B. &quot;Dokumente&quot;, um schnell zu finden und zu **[!UICONTROL Forms &amp; Documents]** oder Dokumentfragmentkonsole zu navigieren. Weitere Informationen zu  finden Sie im AEM 6.2-Artikel [Suche](/help/sites-authoring/search.md)

* **Aktionssymbolleiste**: Bei der Auswahl eines Assets wird die Aktionssymbolleiste über der Liste von Assets angezeigt. Sie enthält alle Management-Tools für das ausgewählte Asset. Sie können die Maus über ein Symbol bewegen, um die QuickInfo anzuzeigen, die die zugehörige Funktion beschreibt

>[!NOTE]
>
>Wenn ein Benutzer eine Suche auf einer beliebigen Konsole von Fomulare und Dokumente durchführt, dann enthält die Leiste nur **Filters &amp; Optionen**. Sie können Filter &amp; Optionen verwenden, um eine erweiterte Suche durchzuführen.

* **Aktionssymbolleiste**: Bei der Auswahl eines Assets wird die Aktionssymbolleiste über der Liste von Assets angezeigt. Sie enthält alle Management-Tools für das ausgewählte Asset. Sie können die Maus über ein Symbol bewegen, um die QuickInfo anzuzeigen, die die zugehörige Funktion beschreibt

   ![Aktionssymbolleiste für ein adaptives Formular](assets/action_toolbar_new.png)

   Aktionssymbolleiste für ein adaptives Formular
