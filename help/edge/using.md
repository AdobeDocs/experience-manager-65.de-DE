---
title: Verwenden von Edge Delivery Services
description: Verwenden von Edge Delivery Services
exl-id: 6c9178b0-c8f3-4fc7-8614-8e71ffc2f0b8
solution: Experience Manager, Experience Manager Assets
feature: Edge Delivery Services
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 100%

---

# Verwenden von Edge Delivery Services {#usingedge}

Mit Edge Delivery können Sie schnelle Entwicklungsumgebungen erstellen, in denen Autorinnen und Autoren Inhalte schnell aktualisieren und veröffentlichen können und neue Sites schnell gestartet werden können. Zu diesem Zweck können Sie mit mehreren Inhaltsquellen auf derselben Website arbeiten, und die Veröffentlichung erfolgt unabhängig von der ausgewählten Quelle nahtlos und optimiert. Es vergehen also nur ein paar Sekunden von der Bearbeitung bis zur Anzeige des Inhalts im Internet.

## Authoring {#authoring-edge}

Mit Edge Delivery ist das Authoring einfach, schnell und flexibel. Sie können zwei verschiedene Pfade zum Authoring im Kontext von Edge Delivery Services verwenden:

* Dokumentenbasiertes Authoring (z. B. Microsoft Word oder Google Docs) – [Weitere Informationen finden Sie unter diesem Link](https://www.hlx.live/docs/authoring).
* Seiteneditor/Universeller Editor – Wenden Sie sich an den Adobe-Vertrieb.

Beim dokumentenbasierten Authoring können Sie mit verschiedenen Quellen wie Microsoft Word und Google Docs arbeiten. Dokumente aus diesen Quellen werden zu Seiten auf Ihrer Website. Überschriften, Listen, Bilder, Schriftelemente und Videos können von der ursprünglichen Quelle auf Ihre Website übertragen werden. Sie können Metadaten für SEO-Zwecke hinzufügen oder Blöcke verwenden, um mit strukturierten Inhalten zu arbeiten und Funktionen hinzuzufügen.

## Veröffentlichung {#publishing-edge}

Mit Edge Delivery erfolgt die Veröffentlichung von Inhalten unabhängig von Ihrer Inhaltsquelle nahtlos. Der Prozess stellt sich wie folgt dar: Sie verwenden die [Sidekick-Erweiterung](#using-sidekick), um den Veröffentlichungsmechanismus auszulösen, und Ihr Inhalt ist innerhalb weniger Sekunden auf Ihrer Website verfügbar.

## Edge Delivery Services und GitHub {#github-edge}

Edge Delivery nutzt GitHub, damit Kundinnen und Kunden Code direkt über ihr GitHub-Repository verwalten und bereitstellen können. Sie können beispielsweise Inhalte entweder in Google Docs oder Microsoft Word schreiben und die Funktionalität Ihrer Site mithilfe von CSS und JavaScript in GitHub entwickeln. Websites werden automatisch für jede Ihrer Verzweigungen erstellt, von der Inhaltsvorschau bis zur Produktion. Jede Ressource, die Sie in Ihr GitHub-Repository einfügen, steht auf Ihrer Website ohne Erstellungsprozess zur Verfügung.

## Verwenden des Sidekicks {#using-sidekick}

Der AEM Sidekick bietet eine Symbolleiste mit kontextabhängigen Optionen, mit denen Sie Inhalte einfach bearbeiten, in der Vorschau anzeigen und veröffentlichen können. Nach dem [Installieren](https://www.hlx.live/docs/sidekick-extension) der AEM Sidekick-Erweiterung kann diese entweder in Projektumgebungen oder beim Bearbeiten Ihres Inhalts (z. B. in Google Docs) verwendet werden. Je nach Umgebung stehen verschiedene Aktionen zur Verfügung, darunter: Vorschau, Neu laden, Bearbeiten und Veröffentlichen. Sie können auch die Umgebung wechseln, wenn Sie den Sidekick verwenden, indem Sie von der Vorschau zur Produktion und umgekehrt wechseln.

**Zum Veröffentlichen** öffnen Sie den Sidekick auf einer Vorschauseite und verwenden Sie die Aktion „Veröffentlichen“. Nachdem Sie auf „Veröffentlichen“ geklickt haben, ist die aktuelle Vorschauversion der Seite in Live- und Produktionsumgebungen verfügbar.

## Integrieren von AEM Assets mit dokumentbasiertem Authoring {#integrate-assets-edge}

Mit Edge Delivery können Sie in AEM Assets-Repositorys verfügbare Bilder verwenden, während Sie Dokumente in Microsoft Word oder Google Docs erstellen.

Die Optionen zur Verwendung von Bildern in Ihren Dokumenten sind nur nach dem [Konfigurieren des AEM Assets-Sidekick-Plug-ins](https://www.hlx.live/developer/configuring-aem-assets-sidekick-plugin) verfügbar.

Das Sidekick-Plug-in für AEM Assets unterstützt den Zugriff auf:

* AEM Assets as a Cloud Service

* AEM Assets Essentials

Nachdem Sie das AEM Assets-Sidekick-Plug-in konfiguriert haben, können Sie damit beginnen, [Bilder in Ihren Google Docs- oder Microsoft Word-Dokumenten zu verwenden](https://www.hlx.live/docs/aem-assets-sidekick-plugin).

## Weitere Informationen {#further-reading}

Weitere Informationen finden Sie auf den folgenden Seiten:

* Weitere Informationen zu den ersten Schritten mit Edge Delivery finden Sie im Abschnitt [Build](https://www.hlx.live/docs/#build) der Edge Delivery-Dokumentation.
* Informationen zum Erstellen und Veröffentlichen von Inhalten mithilfe von Edge Delivery finden Sie im Abschnitt [Veröffentlichen](https://www.hlx.live/docs/authoring).
* Informationen zur Verwendung der Sidekick-Erweiterung finden Sie auf der Seite [Sidekick verwenden](https://www.hlx.live/docs/sidekick).
* Informationen zum AEM-Authoring finden Sie auf der Seite [Authoring-Konzepte](/help/sites-authoring/author.md)
