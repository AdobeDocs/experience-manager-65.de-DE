---
title: Einführung in das Veröffentlichen von Formularen in einem Portal
description: Adobe Experience Manager Forms stellt Komponenten bereit, mit denen Sie Ihr Formularportal erstellen können. In diesem Artikel werden die verfügbaren Formularportal-Komponenten vorgestellt.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
exl-id: 240ed4d8-b21b-46eb-80a9-9e8093b77235
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 100%

---

# Einführung in das Veröffentlichen von Formularen in einem Portal{#introduction-to-publishing-forms-on-a-portal}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html?lang=de) |
| AEM 6.5 | Dieser Artikel |


## Überblick über die AEM Forms-Portalkomponenten {#aem-forms-portal-components-overview}

Bei einer typischen formularzentrierten Portal-Bereitstellung erfolgen Formular- und Portalentwicklung getrennt voneinander. Während Formular-Designerinnen und -Designer Formulare in einem Repository entwerfen und speichern, erstellen Web-Entwicklerinnen und -Entwickler eine Web-Anwendung, um Formulare aufzulisten und die Übermittlung von Formularen zu verarbeiten. Formulare werden in die Web-Stufe kopiert, da keine Kommunikation zwischen Formular-Repository und Web-Anwendung vorhanden ist.

Solche Szenarien führen oft zu Management-Problemen und Produktionsverzögerungen. Wenn beispielsweise eine neuere Version eines Formulars im Repository verfügbar ist, müssen Sie das Formular in der Web-Stufe ersetzen, die Web-Anwendung ändern und das Formular erneut auf der öffentlichen Website bereitstellen. Die erneute Bereitstellung der Web-Anwendung kann zu Server-Downtime führen. In der Regel handelt es sich bei Server-Downtime um eine geplante Aktivität, weshalb die Änderungen nicht sofort an die öffentliche Site gesendet werden können.

AEM Forms bietet Portalkomponenten, die den Verwaltungsaufwand und Produktionsverzögerungen reduzieren. Mit den Komponenten können Web-Entwickler Formularportale auf mit Adobe Experience Manager (AEM) erstellten Websites erstellen und anpassen. 

![AEM Forms-Portal](assets/aem-forms-portal.png)

Über Formularportal-Komponenten können Sie folgende Funktionen hinzufügen:

* Auflisten von Formularen in benutzerdefinierten Layouts. Es werden vorkonfigurierte Layouts für die Listenansicht, Kartenansicht und Bedienfeldansicht bereitgestellt. Sie können auch eigene benutzerdefinierte Layouts erstellen.
* Anzeigen von benutzerdefinierten Metadaten und Aktionen bei deren Auflistung.
* Auflisten von Formularen, die von der AEM Forms-Benutzeroberfläche auf der Veröffentlichungsinstanz veröffentlicht wurden, in der Formularportal-Komponenten verwendet werden.
* Endbenutzern ermöglichen, Formulare im HTML- und PDF-Format anzuzeigen.
* Verwenden benutzerdefinierter HTML-Profile, um Formulare anzuzeigen.
* Aktivieren der Suche nach Formularen anhand einer Reihe von Kriterien, wie zum Beispiel Formulareigenschaften, Metadaten und Tags.
* Senden von Formulardaten an ein Servlet.
* Verwenden von benutzerdefiniertem CSS, um das Erscheinungsbild des Portals anzupassen.
* Erstellen von Links zu Formularen.
* Auflisten von Entwürfen und Übermittlungen für das von einer Endbenutzerin oder einem Endbenutzer erstellte adaptive Formular.

## Verfügbare AEM Forms-Portalkomponenten {#available-aem-forms-portal-components}

AEM Forms bietet standardmäßig die folgenden Portalkomponenten, die in die Komponentengruppen **Dokumentendienste** und **Dokumentdienst-Eigenschaften** unterteilt sind:

### Suche und Auflister {#search-amp-lister}

Mit der Komponente „Suche und Auflister“ können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten. Außerdem enthält sie Konfigurationsoptionen, um Formulare basierend auf angegebenen Kriterien aufzulisten. Außerdem können Sie Suchkriterien angeben, damit die Portalbenutzenden die gesamte Liste der Formulare durchsuchen können.

### Entwürfe und Einsendungen {#drafts-amp-submissions}

Während die Komponente „Suche und Auflister“ Formulare anzeigt, die vom Formularautor veröffentlicht wurden, zeigt die Komponente „Entwürfe und Sendungen“ Formulare, die für den späteren Abschluss als Entwurf gespeichert wurden, sowie gesendete Formulare an. Diese Komponente bietet jeder angemeldeten Benutzerin und jedem angemeldeten Benutzer ein personalisiertes Erlebnis.

### Verknüpfung {#link}

Mithilfe der Komponente „Link“ können Sie einen Link zu einem Formular an jeder beliebigen Stelle auf der Seite erstellen. Angenommen, Sie bieten ein Schulungsprogramm an und möchten, dass sich die Benutzenden über ein Formular für die Schulung anmelden. Auf Ihrer Website haben Sie die Programmdetails veröffentlicht. Unterhalb der Details möchten Sie einen Link zum Anmeldeformular einfügen. Diesen Link können Sie mithilfe der Komponente „Link“ erstellen.

## Formularportal-Workflow {#forms-portal-workflow}

Im Formularportal können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten. Außerdem können Sie Suchkriterien angeben, damit die Portalbenutzenden die gesamte Liste der Formulare durchsuchen können. Sie können die Komponente „Drafts &amp; Submissions“ auch verwenden, um als Entwurf zum späteren Ausfüllen gespeicherte Formulare sowie übermittelte Formulare anzuzeigen. Sie müssen bestimmte Vorgänge ausführen, bevor diese Funktionen auf einer Sites-Seite verfügbar werden. Führen Sie die Schritte in der angegebenen Reihenfolge aus, um die Komponenten und die entsprechenden Funktionen auf einer Sites-Seite verfügbar zu machen:

1. **Aktivieren von Formularportal-Komponenten:** Standardmäßig sind Formularportal-Komponenten nicht verfügbar. [Aktivieren der Komponenten aus AEM Sidekick](/help/forms/using/enabling-forms-portal-components.md) für eine AEM Sites-Seite.
1. **Auflisten von Formularen auf einer Seite (Erstellen der Formularportal-Seite):** Sie können Formulare auf AEM Sites- und AEM Sites-fremden Seiten auflisten. Die Liste enthält Formulare, die in der Veröffentlichungsinstanz verfügbar sind. Benutzer können Formulare öffnen und ausfüllen. Wenn ein Benutzer ein Formular öffnet, wird eine neue Instanz des Formulars erstellt:

   1. **Auflisten von Formularen auf einer AEM Sites-Seite**: Fügen Sie der Seite die Komponente **[Search &amp; Lister](../../forms/using/creating-form-portal-page.md)** hinzu und konfigurieren Sie den darin enthaltenen **[Listenbereich](../../forms/using/creating-form-portal-page.md#p-list-pane-p)**, sodass Formulare auf einer Seite aufgelistet werden. Fügen Sie der Komponente **Search &amp; Lister** auch die Komponente **Suchbereich** hinzu und konfigurieren Sie diese, um der Seite Suchfunktionen hinzuzufügen. Die Seite mit der Formularportal-Komponente wird als [Formularportal-Seite](../../forms/using/creating-form-portal-page.md) bezeichnet.

   1. **Auflisten von Formularen auf einer AEM Sites-fremden Seite:** Verwenden Sie die [APIs für die Formularportal-Suche](/help/forms/using/listing-forms-webpage-using-apis.md), um Formulare auf AEM Sites-fremden Seiten abzufragen, abzurufen und aufzulisten.

1. **Auflisten von Formularentwürfen und übermittelten Formularen auf einer Formularportal-Seite:** Fügen Sie der Formularportal-Seite die Komponente „Entwürfe und Sendungen“ hinzu und konfigurieren Sie sie. Mit der Komponente „“ können Sie alle Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden.

   Damit ein übermitteltes adaptives Formular auf der Registerkarte für Übermittlungen angezeigt werden kann, legen Sie als **Übermittlungsaktion** die Option **[Übermittlungsaktion für Formularportal](configuring-submit-actions.md) fest.** Sie können stattdessen auch die Option „Forms Portal Submit“ aktivieren. Wenn ein Benutzer das Formular übermittelt, wird dieses der Registerkarte „Übermittlungen“ hinzugefügt.

1. **Konfigurieren Sie den Speicher für die Daten von Formularentwürfen und gesendeten Formularen:** Standardmäßig werden die Daten von Entwürfen und Übermittlungen im AEM Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. [Konfigurieren Sie die Formularportal-Komponente, um Daten an einem sicheren Speicherort zu speichern](../../forms/using/draft-submission-component.md#customizing-the-storage).
1. **(Optional) Anpassen der Formularportal-Komponenten:** [Passen Sie Ihre Vorlagen für Formularportal-Seiten an](../../forms/using/customizing-templates-forms-portal-components.md), um den Komponenten ein charakteristisches Erscheinungsbild zu verleihen.
1. **(Optional) Hinzufügen benutzerdefinierter Metadaten zu Formularen:** [Fügen Sie Formularen benutzerdefinierte Metadaten hinzu](../../forms/using/customizing-templates-forms-portal-components.md), um die Auflistung und Suche zu verbessern.
1. **Veröffentlichen der Formularportal-Seite:** Ihre Formularportal-Seite ist nun einsatzbereit. Veröffentlichen Sie die Seite.

## Verwandte Artikel {#related-articles}

* [Aktivieren von Formularportal-Komponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Erstellen einer Formularportal-Seite](../../forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Verwenden der Komponente „Entwurf und Übermittlung“](../../forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](../../forms/using/draft-submission-component.md#customizing-the-storage)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Formularportal-Komponenten](../../forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](../../forms/using/introduction-publishing-forms.md)
