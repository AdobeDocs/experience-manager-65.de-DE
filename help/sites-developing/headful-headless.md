---
title: Headful und Headless in AEM
description: AEM Projekte können in einem Headful- und Headless-Modell implementiert werden, aber die Auswahl ist nicht binär. AEM bietet die Flexibilität, die Vorteile beider Modelle in einem Projekt zu nutzen.
source-git-commit: cf7e9061bac9004c7efd2f045b4900e4a92d67e9
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 94%

---

# Headful und Headless in AEM {#headful-headless}

Adobe Experience Manager-Projekte können sowohl in Headful- als auch in Headless-Modellen implementiert werden, die Auswahl ist jedoch nicht binär. AEM bietet die Flexibilität, die Vorteile beider Modelle in einem Projekt zu nutzen. Dieses Dokument bietet einen Überblick über die verschiedenen Modelle und beschreibt die Integrationsstufen SPA.

## Übersicht {#overview}

AEM bietet leistungsstarke Tools zur Verwaltung der Inhaltserstellung und der Bereitstellung auf einer Plattform. Dies ist ein traditionelles „Headful“-Modell für das Content-Management, bei dem Autoren und Entwickler von Content auf derselben Plattform arbeiten, um die Erlebnisse für Nutzer bereitzustellen.

AEM kann auch zur einfachen Verwaltung von Inhalten verwendet werden, sodass ihre Präsentation und Bereitstellung über eine andere Plattform verwaltet werden können. Dies ist das „Headless“-Modell für das Content-Management, bei dem Autoren und Entwickler von Content auf verschiedenen Plattformen arbeiten, um Erlebnisse für Nutzer bereitzustellen.

Das muss aber keine Entweder-Oder-Entscheidung sein. AEM bietet beispiellose Flexibilität, sodass Sie die Vorteile beider Modelle für Ihr Projekt nutzen können.

![AEM-Implementierungsmodelle](headless/assets/aem-implementation-models.png)

In einem Headful- oder Full-Stack-Modell wird der Content im AEM-Repository verwaltet. AEM-Komponenten auf der Grundlage von Java, HTL usw. werden verwendet, um den Content für das Anwendererlebnis wiederzugeben. In diesem Modell erfolgen die Erstellung, Formatierung, Präsentation und Bereitstellung des Contents in AEM.

Bei einem Headless-Modell wird der Content im AEM-Repository verwaltet, aber über APIs wie REST und GraphQL an ein anderes System gesendet, um ihn für das Anwendererlebnis wiederzugeben. In diesem Modell wird Content in AEM erstellt, aber die Formatierung, Präsentation und Bereitstellung erfolgen auf einer anderen Plattform.

Single Page Applications (SPAs) sind häufig das Ziel für Content, der von AEM im Headless-Modell bereitgestellt wird. Diese SPAs müssen jedoch nicht vollständig von AEM abgekoppelt sein. AEM ermöglicht es Ihnen, zu entscheiden, in welchem Umfang Ihre SPAs in AEM integriert sind. Nehmen wir ein Beispiel.

## Webshop-Beispiel {#web-shop-example}

Angenommen, Sie haben einen Webshop für Ihre Firma als SPA. Darin haben Sie alle Produktdetails und Bilder. Anschließend führen Sie AEM ein, um Ihre Marketing-Bemühungen wie Werbe-Websites, Blogs und Kampagnen-Content zu unterstützen. Wie integrieren Sie beides? AEM bietet eine Reihe von Optionen:

* **Die Systeme können unabhängig betrieben werden.**
* **Der Webshop wird mit eingeschränktem Inhalt von AEM über GraphQL versorgt.** Content kann von Autoren in AEM erstellt, aber nur über die Webshop-SPA angezeigt werden.
* **Die Webshop-SPA wird in AEM eingebettet.** Content kann von Autoren in AEM erstellt und in AEM im Kontext des Webshops angezeigt, aber nicht bearbeitet werden.
* **Die Webshop-SPA wird in AEM eingebettet und bearbeitbare Punkte werden aktiviert.** Content kann von Autoren in AEM erstellt und in AEM im Kontext des Webshops angezeigt werden. Die Autoren haben nur begrenzte Möglichkeiten, den Content der Webshop-SPA in AEM zu manipulieren.
* **Die Webshop-SPA wird in AEM eingebettet und ganze Zonen werden für die Bearbeitung aktiviert.** Content kann von Autoren in AEM erstellt und in AEM im Kontext des Webshops angezeigt werden. Die Autoren haben nur begrenzte Möglichkeiten, den Content der Webshop-SPA in AEM zu manipulieren.

Im nächsten Abschnitt werden diese Integrationsstufen genauer untersucht.

>[!NOTE]
>
>Natürlich könnten Sie die Webshop-SPA als voll funktionsfähige AEM-SPA erneut implementieren. [Dafür verwenden Sie das AEM-SPA Editor-Framework.](/help/sites-developing/spa-walkthrough.md) Wenn Sie bereits AEM haben und einen neuen Webshop oder eine andere SPA erstellen möchten, ist dies die empfohlene Methode. Diese würde den Umfang dieses Dokuments allerdings sprengen.

## SPA-Integrationsstufen {#integration-levels}

In AEM gibt es vier Stufen der SPA-Integration.

* **Stufe 0: Keine Integration**
   * Die SPA und AEM sind getrennt und tauschen keine Informationen aus.
   * Content wird in zwei separaten Systemen erstellt, verwaltet und bereitgestellt.
* **Ebene 1: Integration von Inhaltsfragmenten**
   * [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um eingeschränkte Inhalte für die SPA zu erstellen und zu verwalten.
   * Die SPA ruft diesen Content über die [GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md) von AEM ab.
   * Ein Teil des Contents wird in AEM und ein anderer in einem externen System verwaltet.
   * Content kann nur in der SPA angezeigt werden.
* **Ebene 2: Einbetten der SPA in AEM**
   * [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um Content für die SPA zu erstellen und zu verwalten.
   * Die SPA ruft diesen Content über die [GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md) von AEM ab.
   * Ein Teil des Contents wird in AEM und ein anderer in einem externen System verwaltet.
   * Content kann in AEM im Kontext angezeigt werden.
   * Eingeschränkter Content kann in AEM bearbeitet werden.
* **Ebene 3: Einbetten und vollständiges Aktivieren der SPA in AEM**
   * [Inhaltsfragmente](/help/assets/content-fragments/content-fragments.md) werden in AEM verwendet, um Content für die SPA zu erstellen und zu verwalten.
   * Die SPA ruft diesen Content über die [GraphQL-API](/help/assets/content-fragments/graphql-api-content-fragments.md) von AEM ab.
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
