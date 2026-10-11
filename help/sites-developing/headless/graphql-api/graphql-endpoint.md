---
title: Verwalten von GraphQL-Endpunkten in AEM
description: Erfahren Sie, wie Sie GraphQL-Endpunkte in Adobe Experience Manager für die Headless-Inhaltsbereitstellung verwalten.
exl-id: a59a5e50-0787-4c1c-a83d-bb3eac1479a8
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
source-wordcount: '510'
ht-degree: 100%
---
# Verwalten von GraphQL-Endpunkten in AEM {#graphql-aem-endpoint}

Der Endpunkt ist der Pfad, der für den Zugriff auf GraphQL für AEM verwendet wird. Mit diesem Pfad können Sie (oder Ihr Programm):

* auf das GraphQL-Schema zugreifen,
* Ihre GraphQL-Abfragen senden,
* Antworten (auf Ihre GraphQL-Abfragen) empfangen.

Es gibt zwei Arten von Endpunkten in AEMٔ:

* Global
  * Verfügbar zur Verwendung durch alle Websites.
  * Dieser Endpunkt kann alle Inhaltsfragmentmodelle aus allen Sites-Konfigurationen verwenden (definiert im [Konfigurations-Browser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser)).
  * Wenn es Inhaltsfragmentmodelle gibt, die unter Sites-Konfigurationen freigegeben werden sollen, sollten diese unter den globalen Sites-Konfigurationen erstellt werden.
* Sites-Konfigurationen:
  * Entspricht einer Sites-Konfiguration, wie im [Konfigurations-Browser](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) definiert.
  * Spezifisch für eine bestimmte Website / ein bestimmtes Projekt.
  * Ein für die Sites-Konfiguration spezifischer Endpunkt verwendet die Inhaltsfragmentmodelle aus dieser spezifischen Sites-Konfiguration zusammen mit denen aus der globalen Sites-Konfiguration.

>[!CAUTION]
>
>Der Inhaltsfragment-Editor kann zulassen, dass ein Inhaltsfragment einer Sites-Konfiguration (über Richtlinien) auf ein Inhaltsfragment einer anderen Sites-Konfiguration verweist.
>
>In diesem Fall können nicht alle Inhalte mithilfe eines für eine Sites-Konfiguration spezifischen Endpunkts abgerufen werden.
>
>Der Inhaltsautor sollte dieses Szenario steuern. Beispielsweise kann es nützlich sein, freigegebene Inhaltsfragmentmodelle unter die globale Sites-Konfiguration zu stellen.

Der Repository-Pfad des GraphQL für den globalen Endpunkt in AEM lautet:

`/content/cq:graphql/global/endpoint`

Ihr Programm kann den folgenden Pfad in der Anfrage-URL verwenden:

`/content/_cq_graphql/global/endpoint.json`

Um den GraphQL-Endpunkt für AEM zu aktivieren, gehen Sie folgendermaßen vor:

* [Aktivieren des GraphQL-Endpunkts](#enabling-graphql-endpoint)
* [Veröffentlichen des GraphQL-Endpunkts](#publishing-graphql-endpoint)

## Aktivieren des GraphQL-Endpunkts {#enabling-graphql-endpoint}

Um einen GraphQL-Endpunkt zu aktivieren, benötigen Sie zunächst eine entsprechende Konfiguration. Siehe [Inhaltsfragmente – Konfigurations-Browser](/help/assets/content-fragments/content-fragments-configuration-browser.md).

>[!CAUTION]
>
>Wenn die [Verwendung von Inhaltsfragmentmodellen nicht aktiviert wurde](/help/assets/content-fragments/content-fragments-configuration-browser.md), ist die Option **Erstellen** nicht verfügbar.

So aktivieren Sie den entsprechenden Endpunkt:

1. Gehen Sie zu **Tools**, **Assets** und wählen Sie **GraphQL** aus.
1. Wählen Sie **Erstellen** aus.
1. Das Dialogfeld **Neuen GraphQL-Endpunkt erstellen** wird geöffnet. Hier können Sie Folgendes angeben:
   * **Name**: Name des Endpunkts; Sie können einen beliebigen Text eingeben.
   * **GraphQL-Schema verwenden, das bereitgestellt wurde von**: Verwenden Sie das Dropdown-Menü, um die gewünschte Website / das gewünschte Projekt auszuwählen.

   >[!NOTE]
   >
   >Die folgende Warnung wird im Dialogfeld angezeigt:
   >
   >* *GraphQL-Endpunkte können Probleme mit der Datensicherheit und Leistung verursachen, wenn sie nicht sorgfältig verwaltet werden. Bitte stellen Sie sicher, dass Sie nach dem Erstellen eines Endpunkts die entsprechenden Berechtigungen festlegen.*

1. Bestätigen Sie mit **Erstellen**.
1. Das Dialogfeld **Nächste Schritte** stellt einen direkten Link zur Sicherheitskonsole bereit, sodass Sie sicherstellen können, dass der neu erstellte Endpunkt über geeignete Berechtigungen verfügt.

   >[!CAUTION]
   >
   >Der Endpunkt ist für jeden zugänglich. Dies kann – insbesondere bei Veröffentlichungsinstanzen – Sicherheitsbedenken aufwerfen, da GraphQL-Abfragen eine hohe Server-Belastung verursachen können.
   >
   >Sie können am Endpunkt geeignete ACLs für Ihr Programm einrichten.

## Veröffentlichen des GraphQL-Endpunkts {#publishing-graphql-endpoint}

Wählen Sie den neuen Endpunkt und **Veröffentlichen** aus, um ihn in allen Umgebungen vollständig verfügbar zu machen.

>[!CAUTION]
>
>Der Endpunkt ist für jeden zugänglich.
>
>Dies kann – insbesondere bei Veröffentlichungsinstanzen – Sicherheitsbedenken aufwerfen, da GraphQL-Abfragen eine hohe Server-Belastung verursachen können.
>
>Sie müssen am Endpunkt geeignete ACLs für Ihren Anwendungsfall einrichten.
