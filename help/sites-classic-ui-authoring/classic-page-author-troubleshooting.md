---
title: Fehlerbehebung in AEM bei der Bearbeitung
seo-title: Fehlerbehebung in AEM bei der Bearbeitung
description: Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.
seo-description: Der folgende Abschnitt beschäftigt sich mit einigen Problemen, auf die Sie bei der Arbeit mit AEM stoßen können, und liefert entsprechende Lösungsvorschläge.
uuid: eb95e5ba-1eed-4ffb-80c1-9b8468820c22
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 9b492b17-9029-46ae-9dc0-bb21e6b484df
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

      `http://localhost:4502/sites.html/content?`

      Dadurch wird die Seite direkt von AEM abgerufen und der Dispatcher wird umgangen. Wenn die aktualisierte Seite angezeigt wird, ist dies ein Hinweis darauf, dass Sie den Dispatcher-Cache löschen müssen.

   * Wenden Sie sich an den Systemadministrator, wenn Probleme mit den Replikations-Warteschlangen vorliegen.

## Sidekick wird nicht angezeigt {#sidekick-not-visible}

* **Problem**:

   * Beim Bearbeiten einer Inhaltsseite in der Autorenumgebung wird der Sidekick nicht angezeigt.

* **Grund**:

   * In seltenen Fällen kann es vorkommen, dass Sie die Kopfzeile des Sidekicks außerhalb des aktuellen Fensterbereichs platziert haben. Sie können ihn dann nicht neu platzieren.

* **Lösung**:

   * Melden Sie sich bei Ihrer aktuellen Sitzung ab und melden Sie sich erneut an. Der Sidekick wird wieder an der Standardposition angezeigt.

## Suchen und Ersetzen: nicht alle Instanzen werden ersetzt {#find-replace-not-all-instances-are-replaced}

* **Problem:**

   * When using the **Find &amp; Replace** option it can happen that not all instances of the `find` term are replaced on a page.

* **Grund**:

   * Die ordnungsgemäße Funktion von **Suchen und Ersetzen** ist davon abhängig, wie der Inhalt gespeichert wurde und ob er durchsucht werden kann. Beispiel: Ein Blog-Text wird in der Eigenschaft `jcr:text` gespeichert, die der Konfiguration entsprechend nicht durchsucht werden kann. Der Standardbereich für das Servlet „Suchen und Ersetzen“ deckt die folgenden Eigenschaften ab:

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Lösung**:

   * Diese Definitionen können mit der Konfiguration für **Day CQ WCM Find Replace Servlet** geändert werden, indem z. B. die **Web-Konsole** verwendet wird:

      `http://localhost:4502/system/console/configMgr`

