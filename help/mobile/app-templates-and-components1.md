---
title: App-Vorlagen und -Komponenten
description: Auf dieser Seite erfahren Sie mehr über App-Vorlagen und -Komponenten. Es enthält detaillierte Informationen zur Struktur von Vorlagen.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-on-demand-services-app
exl-id: 58d95325-7cb1-4204-842d-17add70e1fbf
solution: Experience Manager
feature: Mobile
role: User
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 53%

---

# App-Vorlagen und -Komponenten{#app-templates-and-components}

>[!NOTE]
>
>Adobe empfiehlt die Verwendung des SPA-Editors für Projekte, für die ein Framework-basiertes Client-seitiges Rendering für einzelne Seiten (z. B. React) erforderlich ist. [Weitere Informationen](/help/sites-developing/spa-overview.md)

Eine Vorlage wird verwendet, um eine Seite zu erstellen. Sie definiert, welche Komponenten im ausgewählten Umfang genutzt werden können. Eine Vorlage ist eine Hierarchie von Knoten, die dieselbe Struktur aufweist wie die zu erstellende Seite, aber keine Inhalte.

Jede Vorlage stellt Ihnen eine Auswahl an Komponenten bereit, die Sie verwenden können.

* Vorlagen bestehen aus [Komponenten](/help/sites-developing/components.md);
* Komponenten nutzen Widgets und bieten Zugriff auf Widgets. Mit Widgets werden die Inhalte gerendert.

>[!NOTE]
>
>Informationen zum Entwickeln Ihrer Adobe Experience Manager-Anwendung (AEM) mithilfe von CRXDE Lite finden Sie unter [Entwickeln mit CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

Eine Vorlage ist die Basis einer Seite.

Um eine Seite zu erstellen, muss die Vorlage (Knotenbaum **/apps/&lt;myapp>/templates/&lt;mytemplate>**) an die entsprechende Position im Site-Baum kopiert werden: Dies geschieht, wenn eine Seite über die Registerkarte **Websites** erstellt wird.

Über diesen Kopiervorgang erhält die Seite auch ihren anfänglichen Inhalt (in der Regel nur den Inhalt der obersten Ebene) und die Eigenschaft „sling:resourceType“, den Pfad zur Seitenkomponente, die zum Rendern der Seite verwendet wird (alles im untergeordneten Knoten „jcr:content“).

## Struktur einer Vorlage {#structure-of-a-template}

Zwei Aspekte müssen berücksichtigt werden:

* die Struktur der Vorlage selbst
* die Struktur des Inhalts, der bei Verwendung einer Vorlage erstellt wird

Eine Vorlage wird unter einem Knoten vom Typ **cq:Template** erstellt.

Verschiedene Eigenschaften können festgelegt werden, insbesondere:

* **jcr:title** – Titel für die Vorlage; wird beim Erstellen einer Seite im Dialogfeld angezeigt.
* **jcr:description** – Beschreibung für die Vorlage; wird beim Erstellen einer Seite im Dialogfeld angezeigt.

Dieser Knoten enthält den Knoten *a jcr:content (cq:PageContent)* , der als Grundlage für den Inhaltsknoten der resultierenden Seiten verwendet wird. Dadurch wird mithilfe von *sling:resourceType* auf die Komponente verwiesen, die zum Rendern des tatsächlichen Inhalts einer neuen Seite verwendet werden soll.

>[!NOTE]
>
>Informationen zu den Grundlagen für Vorlagen und Komponenten in AEM finden Sie in den folgenden Ressourcen:
>
>* [Vorlagen](/help/sites-developing/templates.md)
>* [Komponenten](/help/sites-developing/components.md)
>

Nachdem Sie über grundlegende Kenntnisse zu Vorlagen und Komponenten verfügen, lesen Sie die folgenden Ressourcen:

* [Erstellen und Hinzufügen von Vorlagen und Komponenten](/help/mobile/mobile-ondemand-app-templates.md)
* [Verwenden von Inhaltseigenschaften zum Exportieren von Inhalten](/help/mobile/on-demand-content-properties-exporting.md)
* [Best Practices](/help/mobile/best-practices-aem-mobile.md)
* [Entwickeln von AEM Mobile Content Services](/help/mobile/developing-content-services.md)

### Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zu zusätzlichen Themen zu mobilen Apps finden Sie unter den folgenden Links:

* [Mobil mit Inhaltssynchronisierung](/help/mobile/mobile-ondemand-contentsync.md)
* [Testen von mobilen Apps](/help/mobile/develop-mobile-apps-testing.md)
