---
title: Einführung in das Verwalten von Formularen
description: AEM Forms bietet Tools zum Verwalten adaptiver Formulare und zugehöriger Assets. In diesem Artikel werden die wichtigsten Funktionen zur Formularverwaltung und Elemente der Benutzeroberfläche vorgestellt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager, introduction
docset: aem65
exl-id: 3e063456-7f96-483d-86a3-6a414746db8a
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1566'
ht-degree: 73%

---

# Einführung in das Verwalten von Formularen {#introduction-to-managing-forms}

AEM [!DNL Forms] bietet eine vereinfachte und dennoch leistungsstarke Benutzeroberfläche zum Erstellen und Verwalten von Formularen, Dokumenten, Themen, Briefen, Dokumentfragmenten, Datenwörterbüchern und ähnlichen Assets. Es vereinfacht die Verwaltung des gesamten Formularzyklusvon Formularen, Dokumente und damit zusammenhängenden Assets – vom Desktop eines Entwicklers bis zur Bereitstellung auf einem Portalserver für Endbenutzer. Sie können die Benutzeroberfläche von AEM [!DNL Forms] für folgendes verwenden:

* Zugriff auf AEM [!DNL Forms]-Komponenten
* Zugriff auf AEM [!DNL Forms]-Konfigurationen

>[!NOTE]
>
>Ausführliche Informationen zu anderen AEM-Tools und Optionen finden Sie unter [Authoring](/help/sites-authoring/author.md).

## Zugriff auf AEM Forms-Komponenten {#access-aem-forms-components}

Neben Optionen zum Erstellen von Formularen, Dokumenten und zugehörigen Assets bietet AEM Optionen zum Erstellen von Sites, Assets, Verwalten einer AEM-Instanz und mehr. Sie können auf das Experience Manager-Logo ![adobeexperiencemanager](assets/adobeexperiencemanager.png) klicken, um zu allen verfügbaren Tools zu navigieren. Zusätzlich zu Konsolen von anderen Komponenten enthält es auch Links zu AEM [!DNL Forms]. Um zu AEM [!DNL Forms] zu navigieren, klicken Sie auf das Experience Manager-Logo ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Navigation ![compass](assets/compass.png) > **[!UICONTROL Forms]**. Links der folgenden Konsolen werden angezeigt:

* Formulare und Dokumente
* Designs
* Briefe
* Dokumentfragmente
* Datenwörterbücher

  ![AEM Forms-Konsole](assets/aem_forms_console_new.png)

### Formulare und Dokumente  {#forms-documents}

Forms und Dokumente bieten Optionen zum Erstellen einer interaktiven Kommunikation, eines adaptiven Formulars, adaptiven Formularfragments und eines Formularsatzes. Nur für AEM [!DNL Forms] auf JEE bietet „Formulare und Dokumente“ eine Option zum Importieren von Dateien von lokalen Speicherorten und zum Synchronisieren von AEM [!DNL Forms]-Assets mit Workbench.

Die Schaltfläche zum Erstellen ist der Startpunkt des Prozesses zur Erstellung oder zum Hochladen von AEM [!DNL Forms]-Assets. Sie bietet Ihnen Optionen zum Erstellen:

* **Interaktive Kommunikation**: Eine interaktive Kommunikation ist ein personalisiertes, interaktives und gerätefreundliches HTML-basiertes digitales Schriftstück, ein Bericht oder ein Dokument. Interaktive Kommunikationen sind responsiv, d. h., ihr Layout und Design passt sich automatisch an das Gerät und die Einstellungen des Benutzers an. Detaillierte Informationen finden Sie unter [Interaktive Kommunikation - Übersicht](/help/forms/using/interactive-communications-overview.md)

* **Adaptives Formular:** Ein adaptives Formular ist ein ansprechendes und interaktives Formular. Sie können adaptive Formulare erstellen, die sich dynamisch an Benutzereingaben anpassen, indem Felder oder Abschnitte je nach Antwort, Gerät oder Arbeitsumgebung des Benutzers hinzugefügt oder entfernt werden. Weitere Informationen zu adaptiven Formularen finden Sie unter [Einführung zum Erstellen adaptiver Formulare](../../forms/using/introduction-forms-authoring.md).

* **Adaptive Formularfragmente:** Zwar wurde jedes Formular für einen bestimmten Zweck entwickelt, aber es gibt gängige Segmente in den meisten Formularen (z. B. für persönliche Angaben wie Name und Anschrift, Familienmitglieder, Einkommen usw.). Sie können ein individuelles Asset für derartige Abschnitte erstellen. Diese wiederverwendbaren, eigenständigen Segmente werden als „adaptive Formularfragmente“ bezeichnet. Weitere Informationen finden Sie unter [Adaptive Formularfragmente](../../forms/using/adaptive-form-fragments.md).

* **Formularsatz:** Ein Formularsatz ist eine Sammlung von HTML5 Formularen, die gruppiert sind und Endbenutzern als ein Formularsatz präsentiert werden. Wenn der Benutzer ein Formularsatz ausfüllt, werden diese Informationen von einem Formular zu einem anderen übertragen. Am Ende kann ein Benutzer alle Formulare mit nur einem Mausklick als eine Einheit absenden. Weitere Informationen finden Sie unter[ Formularsatz in AEM Forms](../../forms/using/formset-in-aem-forms.md).

* **Ordner:** Die Benutzeroberfläche von AEM [!DNL Forms] verwendet Ordner zum Anordnen von Assets. Sie unterstützt zwei Typen von Ordnern:

   * **Allgemeine Ordner:** Diese Ordner werden für Elemente verwendet, die in der Benutzeroberfläche von AEM [!DNL Forms] erstellt werden. Diese Ordner haben keine feste Ordnerstruktur. Sie können sie umbenennen, Unterordner erstellen und adaptive Formulare, interaktive Kommunikation adaptive Formularfragmente, Formularvorlagen (XDPs), PDF-Formulare, Dokumente und verwandte Assets in diesen Ordnern erstellen.
   * **Workflow-Ordner von**: Diese Ordner werden erstellt, wenn Workbench-Prozesse (LiveCycle-Archieve) mit der Benutzeroberfläche von AEM [!DNL Forms] migriert und synchronisiert werden. Sie dürfen sie nicht umbenennen, einen Unterordner erstellen, eine interaktive Kommunikation erstellen, ein adaptives Formularfragment oder eine interaktive Kommunikation erstellen. Sie dürfen auch keinen Versionsordner löschen oder parallel zum Versionsordner ein adaptives Formular, ein adaptives Formularfragment oder eine interaktive Kommunikation erstellen und hochladen.

  ![Ordner](assets/folders.png)

  **A.** Allgemeiner Ordner **B.** Ordner „Forms Workflow“

Das Bedienfeld &quot;Forms&quot;und &quot;Dokument&quot;bietet außerdem Optionen für Folgendes:

* **Importieren Sie Dateien aus dem lokalen Speicher:** Sie können PDF forms und Dokumente, Formularvorlagen (XFA-Formulare) und andere Ressourcen (Bild- und XML-Schema für XSDs) importieren. Eine schrittweise Anleitung finden Sie unter [Importieren und Exportieren von Assets in AEM Forms](../../forms/using/import-export-forms-templates.md).
* **Syncchronisieren von AEM Forms-Assets mit Workbench:** Sie können die Option „Dateien von Workbench“ verwenden, um Assets zwischen der Benutzeroberfläche von AEM Forms und Workbench zu synchronisieren. Das gewährleistet, dass alle Assets in der Benutzeroberfläche von AEM [!DNL Forms] und in der Asset-Auswahl im CRX-Repository von Workbench vorhanden sind.

### Designs  {#themes}

Ein Design enthält Stildetails für Komponenten und Bereiche. Themen haben eine unabhängige Identität. Sie können also ein Design für mehrere adaptive Formulare wiederverwenden. Sie können Stile für eine Komponente angeben oder CSS-Eigenschaften für verschiedene Komponenten ändern, die in Ihren Formularen verwendet werden. Stile umfassen Eigenschaften wie Hintergrundfarben, Statusfarben, Transparenz und Größe. Sie können Anpassungen in einem Design speichern und sie als Vorgabe auf Komponenten Ihres Formulars portieren. Wenn Sie das Design zum Formular hinzufügen, spiegelt der angegebene Stil die entsprechenden Komponenten des Formulars wider. Mit AEM [!DNL Forms] 6.2 können Sie Designs erstellen und sie auf Ihre Formulare anwenden.

Informationen zum Erstellen und Verwenden von Designs finden Sie unter [Designs in AEM Forms](../../forms/using/themes.md).

### Briefe  {#letters}

Ein AEM [!DNL Forms]-Brief ist ein sicheres, personalisiertes und interaktives Stück Korrespondenz. Sie können AEM [!DNL Forms] verwenden, um Briefe (auch als Schriftstücke oder Korrespondenzen bezeichnet) aus zuvor genehmigten und benutzerdefinierten Inhalten in einem vereinfachten Prozess zusammenzustellen.

Informationen zur Erstellung und Verwendung von Briefen finden Sie unter [Brief erstellen](../../forms/using/create-letter.md).

### Dokumentfragmente {#document-fragments}

Dokumentfragmente sind wiederverwendbare Teile/Komponenten einer Korrespondenz, mit der Sie Briefe/Korrespondenz erstellen können. Die Dokumentfragmente weisen den Typ Text, Liste, Bedingung und Layout-Fragment auf. Informationen zum Erstellen und Verwenden von Dokumentfragmenten finden Sie unter [Erstellen von Dokumentfragmenten](/help/forms/using/document-fragments.md).

### Datenwörterbücher {#data-dictionaries}

In der Regel müssen Geschäftsbenutzer keine Kenntnisse über Metadatendarstellungen wie XSD (XML-Schema) und Java-Klassen haben. Sie müssen allerdings in der Regel Zugriff auf diese Datenstrukturen und Attribute haben, um Lösungen erstellen zu können. AEM [!DNL Forms] verwendet ein Datenwörterbuch, das es Geschäftsbenutzern ermöglicht, Informationen aus Back-End-Datenquellen zu verwenden, ohne technische Details über die zugrunde liegenden Datenmodelle zu kennen.

Detaillierte Informationen zum Erstellen und Verwenden von Datenwörterbüchern finden Sie unter [Erstellen von Datenwörterbüchern](../../forms/using/data-dictionary.md).

## Zugriff auf AEM [!DNL Forms]-Konfigurationen {#accessing-aem-forms-configurations}

AEM Tools-Bereich enthält Tools für verschiedene Komponenten. Um zu den spezifischen Tools von AEM Forms zu navigieren, klicken Sie auf das Experience Manager-Logo ![adobeexperiencemanager](assets/adobeexperiencemanager.png) > Tools ![hammer](assets/hammer.png) > **[!UICONTROL Forms]**. Es werden Tools zur Ausführung der folgenden Funktionen angezeigt:

* **Überwachten Ordner konfigurieren:** Ein Administrator kann einen Netzwerkordner konfigurieren, der als überwachter Ordner bezeichnet wird, sodass ein vorkonfigurierter Vorgang gestartet wird, wenn ein Benutzer eine PDF-Datei (z. B. eine Datei) in den überwachten Ordner legt, und die Datei bearbeitet wird. Weitere Informationen finden Sie unter [Erstellen und Konfigurieren eines überwachten Ordners](/help/forms/using/creating-configure-watched-folder.md).
* **Konfigurieren des Offline-Services der Forms-App**: Der Offline-Service der AEM [!DNL Forms]-App legt die Pfade oder URLs der in einem Formular verwendeten Ressourcen im Zwischenspeicher ab. Durch das Zwischenspeichern der Pfa oder URLs der in einem Formular verwendeten Ressourcen wird die serverseitige Leistung verbessert. Um die Server-seitige Offline-Komponente der AEM Forms-App zu konfigurieren, siehe [Arbeiten im Offlinemodus](/help/forms/using/work-offline-mode.md).

  ![AEM Forms-Tools](assets/aem_forms_tools_new.png)

* **Konfigurieren von PDF Generator:** Ein Administrator kann AEM [!DNL Forms] PDF Generator-Einstellungen konfigurieren, Benutzerkonten hinzufügen und Konfiguration in PDF Generator importieren oder exportieren. 
* **Correspondence Management-Assets veröffentlichen:** Mit AEM [!DNL Forms] können Sie sofort alle Briefe, Dokumentfragmente, und Datenwörterbücher und verknüpfte Abhängigkeiten von einer Autorinstanz veröffentlichen. Die veröffentlichten Assets umfassen sämtliche Correspondence Management-Assets und ihre zugehörigen Abhängigkeiten. Ausführliche Informationen finden Sie unter [Veröffentlichen und Aufheben des Veröffentlichens von Formularen und Dokumenten](../../forms/using/publishing-unpublishing-forms.md#publishallthecorrespondencemanagementassets).
* **Exportieren von Correspondence Management-Assets**: Verwenden Sie diese Option, um alle Correspondence Management-Assets und die zugehörigen Abhängigkeiten als Paket aus einer AEM [!DNL Forms]-Instanz herunterzuladen. Detaillierte Informationen finden Sie unter [Importieren und Exportieren von Assets in AEM Forms](../../forms/using/import-export-forms-templates.md#importandexportassetsincorrespondencemanagement)

## Häufige Elemente der Benutzeroberfläche {#commonelements}

* **Linke Leiste**: Sie können auf das Symbol für die linke Leiste ![railleftpng](assets/railleftpng.png) klicken, um die Timeline- und Referenzfunktionen von AEM [!DNL Forms] anzuzeigen.

   * **Zeitleiste:** Sie können Kommentare zu einem Asset hinzufügen, das für Review in der Zeitleiste verfügbar ist. Detaillierte Anweisungen finden Sie unter [Erstellen und Verwalten von Überprüfungen von Assets in Formularen](../../forms/using/create-reviews-forms.md).
   * **Referenzen**: Ein AEM [!DNL Forms]-Asset kann in mehreren AEM [!DNL Forms]-Assets verwendet werden. Ein Dokumentfragment kann beispielsweise in mehreren Briefen verwendet werden. „Referenzen“ besteht aus einer Liste von Assets (andere Formulare oder Ressourcen), in denen das ausgewählte Asset verwendet wird, und einer Liste anderer Assets, die das ausgewählte Asset seinerseits verwendet. 

* **Breadcrumbs:** Eine Breadcrumb-Leiste stellt den Titel der aktuellen Konsole oder des aktuellen Ordners dar. Sie können auf die Option Breadcrumb klicken, um zwischen den Ebenen der Ordner zu navigieren, die in der Hierarchie höher sind.
* **Umschalter anzeigen**: Sie können auf das Symbol „Umschalter anzeigen“ ![viewlist](assets/viewlist.png) oder ![viewcard](assets/viewcard.png) klicken, um schnell zwischen Listen- und Kartenansicht zu wechseln. Weitere Informationen zu allgemeinen Komponenten der Benutzeroberfläche finden Sie unter [Authoring](/help/sites-authoring/author.md).
* **Suche**: Die Suchoption ![search](assets/search.png) bietet Funktionen zum schnellen Suchen und Springen zu benötigten Inhalten und Tools. Geben Sie den Namen des Inhalts oder der Produktfunktion ein und wählen Sie aus den Vorschlägen. Geben Sie z. B. „Dokumente“ ein, um schnell die Konsole der **[!UICONTROL Formulare und Dokumente]** oder der Dokumentfragmente zu finden und dorthin zu navigieren. Weitere Informationen zu finden Sie im AEM 6.2-Artikel [Suche](/help/sites-authoring/search.md)

* **Aktionen-Symbolleiste**: Bei Auswahl eines Assets wird die Aktionssymbolleiste über der Liste der Assets angezeigt. Es enthält alle Verwaltungstools für das ausgewählte Asset. Sie können die Maus über ein Symbol bewegen, um die QuickInfo anzuzeigen, die die zugehörige Funktion beschreibt

>[!NOTE]
>
>Wenn ein Benutzer eine beliebige Konsole von Forms und Dokumenten durchsucht, enthält die Leiste nur **Filter und Optionen**. Sie können Filter und Optionen verwenden, um eine erweiterte Suche durchzuführen.

* **Aktionen-Symbolleiste**: Bei Auswahl eines Assets wird die Aktionssymbolleiste über der Liste der Assets angezeigt. Es enthält alle Verwaltungstools für das ausgewählte Asset. Sie können die Maus über ein Symbol bewegen, um die QuickInfo anzuzeigen, die die zugehörige Funktion beschreibt

  ![Aktionssymbolleiste für ein adaptives Formular](assets/action_toolbar_new.png)

  Aktionssymbolleiste für ein adaptives Formular
