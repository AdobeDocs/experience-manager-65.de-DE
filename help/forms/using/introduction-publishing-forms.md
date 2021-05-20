---
title: Einführung in das Veröffentlichen von Formularen in einem Portal
seo-title: Einführung in das Veröffentlichen von Formularen in einem Portal
description: AEM Forms bietet Komponenten, mit denen Sie Ihr Formularportal erstellen können. In diesem Artikel werden die verfügbaren Forms Portal-Komponenten vorgestellt.
seo-description: AEM Forms bietet Komponenten, mit denen Sie Ihr Formularportal erstellen können. In diesem Artikel werden die verfügbaren Forms Portal-Komponenten vorgestellt.
uuid: 658de12b-66e5-438b-ae8f-872ec11a9c3e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 9f1beb89-8eb1-4e37-a5e8-19752b21374a
docset: aem65
exl-id: 240ed4d8-b21b-46eb-80a9-9e8093b77235
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 62%

---

# Einführung in das Veröffentlichen von Formularen in einem Portal{#introduction-to-publishing-forms-on-a-portal}

## Überblick über die AEM Forms Portal-Komponenten {#aem-forms-portal-components-overview}

In einer typischen formularzentrierten Bereitstellung sind die Entwicklung von Formularen und die Entwicklung von Portalen zwei getrennte Aktivitäten. Während Formularentwickler Formulare in einem Repository erstellen und speichern, erstellen Webentwickler eine Webanwendung, um Formulare aufzulisten und gesendete Formulare zu verarbeiten. Formulare werden in die Webstufe kopiert, da keine Kommunikation zwischen dem Formular-Repository und der Webanwendung besteht.

Solche Fälle führen oft zu Verwaltungsproblemen und Produktionsverzögerungen. Wenn beispielsweise eine neuere Version eines Formulars im Repository verfügbar ist, müssen Sie das Formular auf der Webstufe ersetzen, die Webanwendung ändern und das Formular erneut auf der öffentlichen Site bereitstellen. Die erneute Bereitstellung der Webanwendung verursacht möglicherweise einen Serverausfall. Normalerweise ist der Serverausfall eine geplante Aktivität. Daher können die Änderungen nicht sofort an die öffentliche Site gesendet werden.

AEM Forms bietet Portalkomponenten, die den Verwaltungsaufwand und Produktionsverzögerungen reduzieren. Mit den Komponenten können Webentwickler Formularportalen auf mit Adobe Experience Manager (AEM) erstellten Websites erstellen und anpassen. 

![AEM Forms-Portal](assets/aem-forms-portal.png)

Die Formularportalkomponenten ermöglichen es Ihnen, die folgende Funktion hinzuzufügen:

* Auflisten von Formularen in benutzerdefinierten Layouts. Standardmäßig werden Layouts für Listenansicht, Kartenansicht und Bereichsansicht bereitgestellt. Sie können auch eigene benutzerdefinierte Layouts erstellen.
* Sie können benutzerdefinierte Metadaten sowie benutzerdefinierte Aktionen beim Auflisten anzeigen.
* Auflisten von Formularen, die von der AEM Forms-Benutzeroberfläche auf der Veröffentlichungsinstanz veröffentlicht wurden, in der Forms Portal-Komponenten verwendet werden.
* Endbenutzern ermöglichen, Formulare in HTML- und im PDF-Format anzuzeigen.
* Verwenden benutzerdefinierter HTML-Profile, um Formulare anzuzeigen.
* Aktivieren der Suche nach Formularen anhand einer Reihe von Kriterien, wie zum Beispiel Formulareigenschaften, Metadaten und Tags.
* Senden von Formulardaten an ein Servlet.
* Verwenden von benutzerdefiniertem CSS, um das Erscheinungsbild des Portals anzupassen.
* Erstellen von Links zu Formularen.
* Auflisten von n und Übermittlungen für das vom Benutzer erstellte adaptive Formular.

## Verfügbare AEM Forms Portal-Komponenten {#available-aem-forms-portal-components}

AEM Forms bietet standardmäßig die folgenden Portalkomponenten, die in die Komponentengruppen **** und **Dokumentdienst-Eigenschaften** unterteilt sind:

### Suche und Auflister {#search-amp-lister}

Mit der Komponente „Search &amp; Lister“ können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten. Außerdem enthält sie Konfigurationsoptionen, um Formulare basierend auf angegebenen Kriterien aufzulisten. Außerdem können Sie mit der Komponente Suchkriterien angeben, damit die Portalbenutzer die gesamte Liste der Formulare durchsuchen können.

### Entwürfe und Einsendungen {#drafts-amp-submissions}

Während die Komponente „Search &amp; Lister“ Formulare anzeigt, die vom Formularautor veröffentlicht wurden, zeigt die Komponente „Drafts &amp; Submissions“ Formulare, die für den späteren Abschluss als Entwurf gespeichert wurden, sowie gesendete Formulare an. Diese Komponente bietet jedem angemeldeten Benutzer eine personalisierte Nutzung.

### Verknüpfung {#link}

Mithilfe der Komponente „Link“ können Sie einen Link zu einem Formular an jeder beliebigen Stelle auf der Seite erstellen. Angenommen, Sie bieten ein Schulungsprogramm an und fordern die Benutzer auf, sich über ein Formular für die Schulung anzumelden. Auf Ihrer Website stellen Sie die Programmdetails bereit. Unterhalb der Details möchten Sie einen Link zum Registrierungsformular einfügen. Diesen Link können Sie mithilfe der Komponente „Link“ erstellen.

## Forms Portal-Workflow {#forms-portal-workflow}

Mit dem Forms-Portal können Sie Formulare aus dem Formular-Repository auf Ihrer Portalseite auflisten. Außerdem können Sie mit der Komponente Suchkriterien angeben, damit die Portalbenutzer die gesamte Liste der Formulare durchsuchen können. Sie können die Komponente &quot;Drafts &amp; Submissions&quot;auch verwenden, um Formulare anzuzeigen, die als Entwurf zum Ausfüllen späterer und gesendeter Formulare gespeichert wurden. Sie müssen bestimmte Vorgänge ausführen, bevor diese Funktionen auf einer Sites-Seite verfügbar werden. Führen Sie die Schritte in der angegebenen Reihenfolge aus, um die Komponenten und die entsprechenden Funktionen auf einer Siteseite verfügbar zu machen:

1. **Aktivieren Sie Forms Portal-Komponenten**: Standardmäßig sind Forms Portal-Komponenten nicht verfügbar. [Aktivieren Sie die Komponenten in AEM ](/help/forms/using/enabling-forms-portal-components.md) Sidekickers für eine AEM Sites-Seite.
1. **Formulare auf einer Seite auflisten (Forms Portal-Seite erstellen):**  Sie können Formulare auf AEM Sites- und Nicht-AEM-Seiten auflisten. Die Liste enthält Formulare, die in der Veröffentlichungsinstanz verfügbar sind. Ein Benutzer kann Formulare öffnen und diese ausfüllen. Wenn ein Benutzer ein Formular öffnet, wird eine neue Instanz des Formulars erstellt:

   1. **Auflisten von Formularen auf einer AEM Sites-Seite**: Fügen Sie die  **[Komponente &quot;Search &amp;](../../forms/using/creating-form-portal-page.md)** Lister&quot;zur Seite hinzu und konfigurieren Sie den  **[Listenbereich](../../forms/using/creating-form-portal-page.md#p-list-pane-p)** darin, um Formulare auf einer Seite aufzulisten. Fügen Sie die Komponente **Suchbereich** zur Komponente **Search &amp; Lister** hinzu und konfigurieren Sie sie, um der Seite Suchfunktionen hinzuzufügen. Die Seite mit der Forms Portal-Komponente wird als [Forms Portal-Seite](../../forms/using/creating-form-portal-page.md) bezeichnet.

   1. **Auflisten von Formularen auf einer Nicht-AEM Sites-Seite:** Verwenden Sie die  [Forms Portal-Such-](/help/forms/using/listing-forms-webpage-using-apis.md) APIs, um Formulare auf Nicht-AEM Sites-Seiten abzufragen, abzurufen und aufzulisten.

1. **Auflisten von Entwurfs- und gesendeten Formularen auf einer Forms Portal-Seite**: Fügen Sie die Komponente Drafts &amp; Submissions zur Forms Portal-Seite hinzu und konfigurieren Sie sie. Mit der Komponente „“ können Sie alle Formulare auflisten, die den Status „Entwurf“ aufweisen, und diejenigen, die bereits gesendet wurden.

   Damit ein gesendetes adaptives Formular auf der Registerkarte für Übermittlungen angezeigt werden kann, setzen Sie die **Übermittlungsaktion** auf **[Forms Portal-Übermittlungsaktion](configuring-submit-actions.md).** Alternativ können Sie die Option &quot;Forms Portal Submit&quot;aktivieren. Jedes Mal, wenn ein Benutzer das Formular sendet, wird das Formular zur Registerkarte &quot;Übermittlungen&quot;hinzugefügt.

1. **Konfigurieren Sie den Speicher für die Entwurfs- und gesendeten Formulardaten:** Standardmäßig werden Entwurfs- und Sendedaten im AEM-Repository gespeichert. In einer Produktionsumgebung wird empfohlen, keine Entwurfs- oder gesendete Formulardaten nicht im AEM-Repository zu speichern. [Konfigurieren Sie die Forms Portal-Komponente, um Daten an einem sicheren Speicherort](../../forms/using/draft-submission-component.md#customizing-the-storage) zu speichern.
1. **(Optional) Anpassen der Forms Portal-Komponenten:** [Passen Sie Ihre Forms Portal-](../../forms/using/customizing-templates-forms-portal-components.md) Seitenvorlagen an, um den Komponenten ein charakteristisches Erscheinungsbild zu verleihen.
1. **(Optional) Fügen Sie benutzerdefinierte Metadaten zu Formularen hinzu:** [Fügen Sie benutzerdefinierte Metadaten zu ](../../forms/using/customizing-templates-forms-portal-components.md) Formularen hinzu, um die Liste zu verbessern und das Sucherlebnis zu verbessern.
1. **Veröffentlichen Sie die Forms Portal-Seite:**  Ihre Forms Portal-Seite ist jetzt bereit. Veröffentlichen Sie die Seite.

## Verwandte Artikel {#related-articles}

* [Aktivieren von Forms Portal-Komponenten](/help/forms/using/enabling-forms-portal-components.md)
* [Forms Portal-Seite erstellen](../../forms/using/creating-form-portal-page.md)
* [Auflisten von Formularen auf einer Webseite mithilfe von APIs](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Komponente &quot;Drafts and Submissions&quot;verwenden](../../forms/using/draft-submission-component.md)
* [Anpassen der Speicherung von Entwürfen und gesendeten Formularen](../../forms/using/draft-submission-component.md#customizing-the-storage)
* [Beispiel zur Integrierung der Komponente für Entwurf und Übermittlung in die Datenbank](integrate-draft-submission-database.md)
* [Anpassen von Vorlagen für Forms Portal-Komponenten](../../forms/using/customizing-templates-forms-portal-components.md)
* [Einführung in das Veröffentlichen von Formularen in einem Portal](../../forms/using/introduction-publishing-forms.md)
