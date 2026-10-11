---
title: Headful und Headless in AEM
description: AEM-Projekte können in einem Headful- und in einem Headless-Modell implementiert werden, Sie müssen sich jedoch nicht entscheiden. AEM bietet die Flexibilität, die Vorteile beider Modelle in einem Projekt zu nutzen.
exl-id: c9597c78-be05-42ff-84fe-f7451119e83d
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: bfd4bc52-c397-5127-8f86-8953ba9fc0a3
    internal-label: Headless
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: a642c50e-80eb-4fc1-a5d2-f3762d1f841d
    internal-label: Administration
  - id: d429a63e-ade4-4117-b04e-9b996d1c94ef
    internal-label: Integrations
  - id: c124fa01-25c5-42ec-adf6-21d1c114058b
    internal-label: Developer tools
subfeature_v2:
  - id: e9db7c79-8f65-4281-a439-c9049296d903
    internal-label: Content Fragments
  - id: a02b73a7-bdfc-4225-bdfd-69f7891ab55e
    internal-label: GraphQL
  - id: d781bc8f-52af-43f6-84d0-b73e59a130d5
    internal-label: Persisted queries
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 80%
---
# Headful und Headless in AEM {#headful-headless}

Adobe Experience Manager-Projekte können sowohl als Headful- als auch als Headless-Modell implementiert werden, Sie müsse sich jedoch nicht entscheiden. AEM bietet die Flexibilität, die Vorteile beider Modelle in einem Projekt zu nutzen. Dieses Dokument bietet einen Überblick über die verschiedenen Modelle und beschreibt die Stufen der SPA-Integration.

## Übersicht {#overview}

AEM bietet leistungsstarke Tools zur Verwaltung der Inhaltserstellung und der Bereitstellung auf einer Plattform. Dies ist ein traditionelles „Headful“-Modell für das Content-Management, bei dem Autoren und Entwickler von Content auf derselben Plattform arbeiten, um die Erlebnisse für Nutzer bereitzustellen.

AEM kann auch zur einfachen Verwaltung von Inhalten verwendet werden, sodass ihre Präsentation und Bereitstellung über eine andere Plattform verwaltet werden können. Dies ist das „Headless“-Modell für das Content-Management, bei dem Autoren und Entwickler von Content auf verschiedenen Plattformen arbeiten, um Erlebnisse für Nutzer bereitzustellen.

Aber dies muss keine binäre Wahl sein. AEM bietet beispiellose Flexibilität, sodass Sie die Vorteile beider Modelle für Ihr Projekt nutzen können.

![AEM-Implementierungsmodelle](/help/sites-developing/headless/getting-started/assets/aem-implementation-models.png)

In einem Headful- oder Full-Stack-Modell wird der Inhalt im AEM-Repository verwaltet, und es werden AEM Komponenten verwendet, die auf Java und HTL basieren, um den Inhalt für das Anwendererlebnis zu rendern. In diesem Modell erfolgen die Erstellung, Formatierung, Präsentation und Bereitstellung des Contents in AEM.

Bei einem Headless-Modell wird der Content im AEM-Repository verwaltet, aber über APIs wie REST und GraphQL an ein anderes System gesendet, um ihn für das Anwendererlebnis wiederzugeben. In diesem Modell wird Content in AEM erstellt, aber die Formatierung, Präsentation und Bereitstellung erfolgen auf einer anderen Plattform.

Single Page Applications (SPAs) sind häufig das Ziel für Content, der von AEM im Headless-Modell bereitgestellt wird. Diese SPAs müssen jedoch nicht vollständig von AEM abgekoppelt sein. AEM ermöglicht es Ihnen, zu entscheiden, in welchem Umfang Ihre SPAs in AEM integriert sind. Nehmen wir ein Beispiel.

## Webshop-Beispiel {#web-shop-example}

Angenommen, Sie haben einen Webshop für Ihre Firma als SPA. Darin haben Sie alle Produktdetails und Bilder. Anschließend führen Sie AEM ein, um Ihre Marketing-Maßnahmen wie Werbeseiten, Blogs und Kampagneninhalte zu unterstützen. Wie integrieren Sie beides? AEM bietet eine Reihe von Optionen:

* **Die Systeme können unabhängig betrieben werden.**
* **Geben Sie dem Webshop über GraphQL begrenzte Inhalte aus AEM.** Inhalte können von Autorinnen und Autoren in AEM erstellt, aber nur über die Webshop-SPA angezeigt werden.
* **Einbetten der Webshop-SPA in AEM.** Inhalte können von Autorinnen und Autoren in AEM erstellt und in AEM im Kontext des Webshops angezeigt, jedoch nicht bearbeitet werden.
* **Betten Sie die Webshop-SPA in AEM ein und aktivieren Sie bearbeitbare Punkte.** Inhalte können von Autorinnen und Autoren in AEM erstellt und in AEM im Kontext des Webshops angezeigt werden. Die Autorinnen und Autoren haben nur begrenzte Möglichkeiten, den Inhalt der Webshop-SPA in AEM zu bearbeiten.
* **Betten Sie die Web-Shop-SPA in AEM ein und aktivieren Sie ganze Zonen für die Bearbeitung.** Inhalte können von Autorinnen und Autoren in AEM erstellt und in AEM im Kontext des Webshops angezeigt werden. Die Autorinnen und Autoren haben nur begrenzte Möglichkeiten, den Inhalt der Webshop-SPA in AEM zu bearbeiten.

Im nächsten Abschnitt werden diese Integrationsstufen genauer untersucht.

>[!NOTE]
>
>Sie können die Webshop-SPA natürlich auch als voll funktionsfähige AEM-SPA (mit [ AEM-SPA-Editor-Framework) neu implementieren](/help/sites-developing/spa-walkthrough.md) Wenn Sie bereits über AEM verfügen und einen Webshop oder eine andere SPA erstellen möchten, ist dies die empfohlene Methode, sie liegt jedoch außerhalb des Bereichs dieses Dokuments.

## SPA-Integrationsstufen {#integration-levels}

In AEM gibt es vier Stufen der SPA-Integration.

* **Stufe 0: Keine Integration**
  * Die SPA und AEM sind getrennt und tauschen keine Informationen aus.
  * Content wird in zwei separaten Systemen erstellt, verwaltet und bereitgestellt.
* **Ebene 1: Integration von Inhaltsfragmenten**
  * [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um eingeschränkte Inhalte für die SPA zu erstellen und zu verwalten.
  * Die SPA ruft diesen Content über die [GraphQL-API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) von AEM ab.
  * Ein Teil des Contents wird in AEM und ein anderer in einem externen System verwaltet.
  * Content kann nur in der SPA angezeigt werden.
* **Ebene 2: Einbetten der SPA in AEM**
  * [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um Content für die SPA zu erstellen und zu verwalten.
  * Die SPA ruft diesen Content über die [GraphQL-API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) von AEM ab.
  * Ein Teil des Contents wird in AEM und ein anderer in einem externen System verwaltet.
  * Content kann in AEM im Kontext angezeigt werden.
  * Eingeschränkter Content kann in AEM bearbeitet werden.
* **Ebene 3: Einbetten und vollständiges Aktivieren der SPA in AEM**
  * [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um Content für die SPA zu erstellen und zu verwalten.
  * Die SPA ruft diesen Content über die [GraphQL-API](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) von AEM ab.
  * Content kann in AEM im Kontext angezeigt werden.
  * Die meisten Inhalte können in AEM bearbeitet werden.

Stufe 1 ist ein Beispiel für eine typische Headless-Implementierung. Autoren können ihren Content jedoch nur innerhalb der SPA im Kontext anzeigen. AEM ist nur ein Authoring-Tool.

Die Vorteile und die Flexibilität von AEM machen sich auf Stufe 2 und 3 bemerkbar, während die Vorteile der SPA erhalten bleiben. Autoren können ihren Content in AEM erstellen, aber auch in AEM im Kontext anzeigen. Die SPA kann in AEM erstellt und dennoch als SPA bereitgestellt werden.

## Implementieren der Integrationsstufen {#implementing}

In AEM stehen verschiedene Tools zur Verfügung, je nach gewählter Integrationsstufe. Jede Stufe baut auf den zuvor verwendeten Werkzeugen auf. In der folgenden Liste finden Sie Links zu den entsprechenden Ressourcen.

* **Stufe 1:** Inhaltsfragmente und das [AEM-Headless-Framework](/help/sites-developing/headless/introduction.md) können verwendet werden, um AEM-Content für die SPA bereitzustellen.
* **Stufe 2:** Zusätzlich zu Stufe 1:
  * [Die RemotePage-Komponente](/help/sites-developing/spa-remote-page.md) kann verwendet werden, um die externe SPA in AEM einzubetten, wo AEM-Content im Kontext angezeigt werden kann.
  * Bestimmte Punkte auf der SPA können auch aktiviert werden, um eine [eingeschränkte Bearbeitung in AEM zuzulassen](/help/sites-developing/spa-edit-external.md).
* **Stufe 3:** Zusätzlich zu Stufe 2:
  * Ganze Bereiche der SPA können aktiviert werden, um eine umfassende Bearbeitung in AEM zu ermöglichen.
