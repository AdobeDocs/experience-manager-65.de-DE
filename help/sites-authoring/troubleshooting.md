---
title: Fehlerbehebung in AEM bei der Bearbeitung
seo-title: Fehlerbehebung in AEM bei der Bearbeitung
description: Probleme, die bei der Verwendung mit AEM auftreten können
seo-description: Probleme, die bei der Verwendung mit AEM auftreten können
uuid: 99af51ea-8628-4811-83f2-ab3f88f0279e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: da0a5644-2e1d-4394-a6aa-11bb41406ba6
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Fehlerbehebung in AEM bei der Bearbeitung{#troubleshooting-aem-when-authoring}

Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.

>[!NOTE]
>
>Wenn Probleme auftreten, sollten Sie auch die Liste der [bekannten Probleme](/help/release-notes/known-issues.md) für Ihre Instanz (Version und Service Packs) prüfen.

>[!NOTE]
>
>Benutzer mit Administratorrechten, die Probleme in AEM beheben möchten, können die unter [Fehlerbehebung in AEM (für Administratoren)](/help/sites-administering/troubleshoot.md) beschriebenen Lösungen nutzen. Wenn Sie nicht über ausreichende Rechte verfügen, wenden Sie sich bezüglich der Problembehebung in AEM an Ihren Administrator.

## Alte Seitenversion wird weiterhin auf der Veröffentlichungs-Website angezeigt {#old-page-version-still-on-published-site}

* **Problem**:

   * Sie haben Änderungen an einer Seite vorgenommen und die Seite in die Veröffentlichungs-Website repliziert, die *alte* Version der Seite wird aber weiterhin auf der Veröffentlichungs-Website angezeigt.

* **Grund**:

   * Dies kann verschiedene Gründe haben. Meist liegt es am Cache (entweder dem Ihres lokalen Browsers oder dem des Dispatchers), gelegentlich kann es sich jedoch auch um ein Problem mit der Replikations-Warteschlange handeln.

* **Lösungen**:

   * Hier gibt es mehrere Möglichkeiten:
   * Überprüfen Sie, ob die Seite korrekt repliziert wurde. Prüfen Sie den Seitenstatus und ggf. den Status der Replikations-Warteschlange.
   * Löschen Sie den Cache des lokalen Browsers und rufen Sie die Seite erneut auf.
   * Add `?` to the end of the page URL. For example:

      * `http://localhost:4502/sites.html/content?`
      * Dadurch wird die Seite direkt von AEM abgerufen und der Dispatcher wird umgangen. Wenn die aktualisierte Seite angezeigt wird, ist dies ein Hinweis darauf, dass Sie den Dispatcher-Cache löschen müssen.
   * Wenden Sie sich an den Systemadministrator, wenn Probleme mit den Replikations-Warteschlangen vorliegen.


## Komponentenaktionen nicht in der Symbolleiste sichtbar {#component-actions-not-visible-on-toolbar}

* **Problem**:

   * Sämtliche entsprechenden Komponentenaktionen sind nicht sichtbar, wenn eine Seite in der Autorenumgebung bearbeitet wird. 

* **Grund**:

   * In seltenen Fällen kann eine frühere Aktion die Symbolleiste beeinflussen.

* **Lösung**:

   * Aktualisieren Sie die Seite.

