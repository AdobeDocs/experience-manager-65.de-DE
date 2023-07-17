---
title: Einführung in das Veröffentlichen von Formularen in einem Portal
description: Adobe Experience Manager Forms stellt Komponenten bereit, mit denen Sie Ihr Forms-Portal erstellen können. In diesem Artikel werden die verfügbaren Forms Portal-Komponenten vorgestellt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: 240ed4d8-b21b-46eb-80a9-9e8093b77235
source-git-commit: 60924e7ee204e43a2ff833fbc394beca8db9c9d9
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 46%

---

# Einführung in das Veröffentlichen von Formularen in einem Portal{#introduction-to-publishing-forms-on-a-portal}

## Übersicht über AEM Forms Portal-Komponenten {#aem-forms-portal-components-overview}

In einem typischen formularzentrierten Portal-Bereitstellungsszenario sind die Formularentwicklung und die Portalentwicklung zwei getrennte Aktivitäten. Während Formularentwickler Formulare in einem Repository entwerfen und speichern, erstellen Webentwickler eine Webanwendung, um Formulare aufzulisten und die Übermittlung von Formularen zu verarbeiten. Forms wird in die Webstufe kopiert, da keine Kommunikation zwischen dem Formular-Repository und der Webanwendung besteht.

Solche Szenarien führen oft zu Managementproblemen und Produktionsverzögerungen. Wenn beispielsweise eine neuere Version eines Formulars im Repository verfügbar ist, müssen Sie das Formular auf der Webstufe ersetzen, die Webanwendung ändern und das Formular erneut auf der öffentlichen Website bereitstellen. Die erneute Bereitstellung der Webanwendung kann zu Serverausfällen führen. In der Regel handelt es sich bei dem Serverausfall um eine geplante Aktivität, weshalb die Änderungen nicht sofort an die öffentliche Site gesendet werden können.

AEM Forms bietet Portalkomponenten, die den Verwaltungsaufwand und Produktionsverzögerungen reduzieren. Mit den Komponenten können Web-Entwickler Formularportale auf mit Adobe Experience Manager (AEM) erstellten Websites erstellen und anpassen. 

![AEM Forms-Portal](assets/aem-forms-portal.png)

Mit den Formularportalkomponenten können Sie die folgenden Funktionen hinzufügen:

* Auflisten von Formularen in benutzerdefinierten Layouts. Standardmäßig werden die Layouts für Listenansicht, Kartenansicht und Bereichsansicht bereitgestellt. Sie können auch eigene benutzerdefinierte Layouts erstellen.
* Sie können benutzerdefinierte Metadaten und benutzerdefinierte Aktionen beim Auflisten anzeigen.
* Auflisten von Formularen, die von der AEM Forms-Benutzeroberfläche auf der Veröffentlichungsinstanz veröffentlicht wurden, in der Formularportal-Komponenten verwendet werden.
* Endbenutzern ermöglichen, Formulare im HTML- und PDF-Format anzuzeigen.
* Verwenden benutzerdefinierter HTML-Profile, um Formulare anzuzeigen.
* Aktivieren der Suche nach Formularen anhand einer Reihe von Kriterien, wie zum Beispiel Formulareigenschaften, Metadaten und Tags.
* Senden von Formulardaten an ein Servlet.
* Verwenden von benutzerdefiniertem CSS, um das Erscheinungsbild des Portals anzupassen.
* Erstellen von Links zu Formularen.
* Listet Entwürfe und Übermittlungen im Zusammenhang mit dem vom Endbenutzer erstellten adaptiven Formular auf.

## Verfügbare AEM Forms Portal-Komponenten {#available-aem-forms-portal-components}

AEM Forms stellt standardmäßig die folgenden Portalkomponenten bereit, gruppiert unter **Document Services** und **Document Services-Eigenschaften** Komponentengruppen:

### Suche und Auflister {#search-amp-lister}

Mit der Komponente &quot;Search &amp; Lister&quot;können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten und Konfigurationsoptionen bereitstellen, um Formulare basierend auf angegebenen Kriterien aufzulisten. Außerdem können Sie mit der Komponente Suchkriterien angeben, damit die Portalbenutzer die gesamte Liste der Formulare durchsuchen können.

### Entwürfe und Einsendungen {#drafts-amp-submissions}

Während die Komponente „Suche und Auflister“ Formulare anzeigt, die vom Formularautor veröffentlicht wurden, zeigt die Komponente „Entwürfe und Sendungen“ Formulare, die für den späteren Abschluss als Entwurf gespeichert wurden, sowie gesendete Formulare an. Diese Komponente bietet jedem angemeldeten Benutzer ein personalisiertes Erlebnis.

### Verknüpfung {#link}

Mit der Komponente &quot;Link&quot;können Sie einen Link zu einem Formular an einer beliebigen Stelle auf der Seite erstellen. Angenommen, Sie bieten ein Schulungsprogramm an und möchten, dass Ihre Benutzer ein Formular zur Registrierung für das Training einreichen. Auf Ihrer Website haben Sie die Programmdetails veröffentlicht. Unter den Details möchten Sie einen Link zum Registrierungsformular angeben. Die Komponente Link kann Ihnen beim Erstellen dieses Links helfen.

## Formularportal-Workflow {#forms-portal-workflow}

Mit Forms Portal können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten. Außerdem können Sie Suchkriterien angeben, damit Ihre Portal-Benutzer in der Formularliste suchen können. Sie können die Komponente „Drafts &amp; Submissions“ auch verwenden, um als Entwurf zum späteren Ausfüllen gespeicherte Formulare sowie übermittelte Formulare anzuzeigen. Sie führen bestimmte Vorgänge durch, bevor diese Funktionen auf einer Sites-Seite verfügbar werden. Führen Sie die Schritte in der angegebenen Reihenfolge aus, um die Komponenten und die entsprechenden Funktionen auf einer Sites-Seite verfügbar zu machen:

1. **Aktivieren von Forms Portal-Komponenten**: Standardmäßig sind Forms Portal-Komponenten nicht verfügbar. [Aktivieren der Komponenten aus AEM Sidekick](/help/forms/using/enabling-forms-portal-components.md) für eine AEM Sites-Seite.
1. **Auflisten von Formularen auf einer Seite (Erstellen der Forms Portal-Seite):** Sie können Formulare auf AEM Sites- und Nicht-AEM-Seiten auflisten. Die Liste enthält Formulare, die in der Veröffentlichungsinstanz verfügbar sind. Benutzer können Formulare öffnen und ausfüllen. Wenn ein Benutzer ein Formular öffnet, wird eine neue Instanz des Formulars erstellt:

   1. **Auflisten von Formularen auf einer AEM Sites-Seite**: Fügen Sie der Seite die Komponente **[Search &amp; Lister](../../forms/using/creating-form-portal-page.md)** hinzu und konfigurieren Sie den darin enthaltenen **[Listenbereich](../../forms/using/creating-form-portal-page.md#p-list-pane-p)**, sodass Formulare auf einer Seite aufgelistet werden. Fügen Sie der Komponente **Search &amp; Lister** auch die Komponente **Suchbereich** hinzu und konfigurieren Sie diese, um der Seite Suchfunktionen hinzuzufügen. Die Seite mit der Forms Portal-Komponente wird als [Forms Portal-Seite](../../forms/using/creating-form-portal-page.md).

   1. **Auflisten von Formularen auf einer Nicht-AEM Sites-Seite:** Verwenden Sie die [Forms Portal-Such-APIs](/help/forms/using/listing-forms-webpage-using-apis.md) , um Formulare auf Nicht-AEM Sites-Seiten abzufragen, abzurufen und aufzulisten.

1. **Auflisten von Entwurfs- und gesendeten Formularen auf einer Forms Portal-Seite**: Fügen Sie die Komponente Drafts &amp; Submissions zur Forms Portal-Seite hinzu und konfigurieren Sie sie. Mit der Komponente „“ können Sie alle Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden.

   Damit ein übermitteltes adaptives Formular auf der Registerkarte für Übermittlungen angezeigt werden kann, legen Sie als **Übermittlungsaktion** die Option **[Übermittlungsaktion für Formularportal](configuring-submit-actions.md) fest.** Sie können stattdessen auch die Option „Forms Portal Submit“ aktivieren. Wenn ein Benutzer das Formular übermittelt, wird dieses der Registerkarte „Übermittlungen“ hinzugefügt.

1. **Konfigurieren Sie den Speicher für die Daten von Formularentwürfen und gesendeten Formularen:** Standardmäßig werden die Daten von Entwürfen und Übermittlungen im AEM Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. [Konfigurieren der Forms Portal-Komponente zum Speichern von Daten an einem sicheren Speicherort](../../forms/using/draft-submission-component.md#customizing-the-storage).
1. **(Optional) Anpassen der Forms Portal-Komponenten:** [Anpassen der Seitenvorlagen in Forms Portal](../../forms/using/customizing-templates-forms-portal-components.md) um den Komponenten ein charakteristisches Erscheinungsbild zu verleihen.
1. **(Optional) Hinzufügen benutzerdefinierter Metadaten zu Formularen:** [Fügen Sie Formularen benutzerdefinierte Metadaten hinzu](../../forms/using/customizing-templates-forms-portal-components.md), um die Auflistung und Suche zu verbessern.
1. **Veröffentlichen Sie die Forms Portal-Seite:** Ihre Forms Portal-Seite ist jetzt bereit. Veröffentlichen Sie die Seite.

## Verwandte Artikel {#related-articles}

* [Aktivieren von Forms Portal-Komponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Forms Portal-Seite erstellen](../../forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](../../forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](../../forms/using/draft-submission-component.md#customizing-the-storage)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](../../forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](../../forms/using/introduction-publishing-forms.md)
