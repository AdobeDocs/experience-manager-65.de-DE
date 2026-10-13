---
title: Fehlerbehebung beim Authoring in AEM
description: Einige Probleme, die bei der Verwendung von AEM auftreten können.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: 05586b17-35d4-496e-8f0e-293c755eb066
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: e2c1b6d3-bb7e-4fe8-8c72-f7b403298e91
    internal-label: Authoring
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 751e1826ed53df7522418e50a206f0fe622256a4
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 97%
---
# Fehlerbehebung in AEM beim Authoring{#troubleshooting-aem-when-authoring}

Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.

>[!NOTE]
>
>Wenn Probleme auftreten, sollten Sie auch die Liste der [bekannten Probleme](/help/release-notes/release-notes.md) für Ihre Instanz (Version und Service Packs) prüfen.

>[!NOTE]
>
>Benutzer mit Administratorrechten, die Probleme in AEM beheben möchten, können die unter [Fehlerbehebung in AEM (für Administratoren)](/help/sites-administering/troubleshoot.md) beschriebenen Lösungen nutzen. Wenn Sie nicht über ausreichende Rechte verfügen, wenden Sie sich bezüglich der Problembehebung in AEM an Ihre Admins.

## Alte Seitenversion wird weiterhin auf der veröffentlichten Website angezeigt {#old-page-version-still-on-published-site}

* **Problem**:

  * Sie haben Änderungen an einer Seite vorgenommen und die Seite auf die Veröffentlichungs-Site repliziert, aber auf der Veröffentlichungs-Site wird immer noch die *alte* Version der Seite angezeigt.

* **Grund**:

  * Dies kann verschiedene Gründe haben. Meist liegt es am Cache (entweder dem Ihres lokalen Browsers oder dem des Dispatchers), gelegentlich kann es sich jedoch auch um ein Problem mit der Replikations-Warteschlange handeln.

* **Lösungen**:

  * Hier gibt es mehrere Möglichkeiten:
  * Überprüfen Sie, ob die Seite korrekt repliziert wurde. Überprüfen Sie den Seitenstatus und ggf. den Status der Replikations-Warteschlange.
  * Löschen Sie den Cache des lokalen Browsers und rufen Sie die Seite erneut auf.
  * Fügen Sie am Ende der Seiten-URL `?` hinzu. Beispiel:

    * `http://localhost:4502/sites.html/content?`
    * Dadurch wird die Seite direkt von AEM abgerufen und der Dispatcher wird umgangen. Wenn die aktualisierte Seite angezeigt wird, ist dies ein Hinweis darauf, dass Sie den Dispatcher-Cache löschen müssen.

  * Wenden Sie sich an den Systemadministrator, wenn Probleme mit den Replikationswarteschlangen vorliegen.

## Komponentenaktionen nicht in der Symbolleiste sichtbar {#component-actions-not-visible-on-toolbar}

* **Problem**:

  * Sämtliche entsprechenden Komponentenaktionen sind nicht sichtbar, wenn eine Seite in der Autorenumgebung bearbeitet wird.

* **Grund**:

  * In seltenen Fällen kann sich eine frühere Aktion auf die Symbolleiste auswirken.

* **Lösung**:

  * Aktualisieren Sie die Seite.
