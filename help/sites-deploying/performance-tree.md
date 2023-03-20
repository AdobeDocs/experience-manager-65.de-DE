---
title: Leistungsübersicht
seo-title: Performance Tree
description: Erfahren Sie mehr über die Schritte, die zur Behebung von Leistungsproblemen in AEM erforderlich sind.
seo-description: Learn about the steps that need to be taken in order to troubleshoot performance issues in AEM.
uuid: ab0624f7-6b39-4255-89e0-54c74b54cd98
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 5febbb1e-795c-49cd-a8f4-c6b4b540673d
exl-id: f2f968b8-b21c-487d-bc0d-ed60903bc4bf
source-git-commit: 30327950779337ce869b6ca376120bc09826be21
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 57%

---

# Leistungsübersicht{#performance-tree}

## Anwendungsbereich {#scope}

Das nachfolgende Diagramm zeigt die erforderlichen Schritte zur Behebung von Leistungsproblemen. Es ist in 5 Abschnitte unterteilt, um das Lesen zu erleichtern.

Jeder Schritt im Diagramm ist mit einer Dokumentationsressource oder einer Empfehlung verknüpft.

## Voraussetzungen und Annahmen {#prerequisites-and-assumptions}

Es wird davon ausgegangen, dass ein Leistungsproblem auf einer Seite auftritt (einer AEM-Konsole oder einer Webseite) und konsistent reproduziert werden kann. Eine Möglichkeit, die Leistung zu testen oder zu überwachen, ist eine Voraussetzung, bevor mit der Untersuchung begonnen wird.

Die Analyse beginnt mit Schritt 0. Das Ziel besteht darin, festzustellen, welche Einheit (Dispatcher, externer Host oder AEM) das Leistungsproblem verursacht, und dann zu bestimmen, welcher Bereich (Server oder Netzwerk) untersucht werden muss.

### Bereich 1 {#section}

![chlimage_1-103](assets/chlimage_1-103.png)

### Bereich 2 {#section-1}

![chlimage_1-104](assets/chlimage_1-104.png)

### Bereich 3 {#section-2}

![chlimage_1-105](assets/chlimage_1-105.png)

### Bereich 4 {#section-3}

![chlimage_1-106](assets/chlimage_1-106.png)

### Bereich 5 {#section-4}

![chlimage_1-107](assets/chlimage_1-107.png)

## Referenzlinks {#reference-links}

<table>
 <tbody>
  <tr>
   <td><strong>Schritt</strong></td>
   <td><strong>Titel</strong></td>
   <td><strong>Ressourcen</strong></td>
  </tr>
  <tr>
   <td><strong>Schritt 0</strong></td>
   <td>Anforderungsfluss analysieren</td>
   <td><p>Mit der Standard-HTTP-Anforderungsanalyse im Browser können Sie den Anforderungsablauf analysieren. Weitere Informationen dazu, wie Sie dies in Chrome durchführen, finden Sie unter:<br /> </p> <p><a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading">https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/resource-loading</a><a href="https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/understanding-resource-timing"><br /> https://developers.google.com/web/tools/chrome-devtools/profile/network-performance/understanding-resource-timing</a><br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 2</strong></td>
   <td>Kommen Anforderungen von externen Hosts?</td>
   <td>Mit der Standard-HTTP-Anforderungsanalyse im Browser können Sie den Anforderungsablauf analysieren. Informationen dazu, wie Sie dies in Chrome durchführen, finden Sie unter den obigen Links.<br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 3</strong></td>
   <td>Können die Anforderungen zwischengespeichert werden?</td>
   <td>Weitere Informationen zu zwischenspeicherbaren Anforderungen und allgemeine Empfehlungen zur Leistungsoptimierung des Dispatchers finden Sie unter <a href="/help/sites-deploying/configuring-performance.md#optimizing-performance-when-using-the-dispatcher">Leistungsoptimierung des Dispatchers</a>.</td>
  </tr>
  <tr>
   <td><strong>Schritt 4</strong></td>
   <td>Gehen Anforderungen vom Dispatcher ein?</td>
   <td><p>Überprüfen Sie die <a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html#debugging">Dokumentation zum Dispatcher-Debugging</a>, um festzustellen, ob die Anforderungen ordnungsgemäß zwischengespeichert werden.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 5</strong></td>
   <td>Versucht der Dispatcher jede Anforderung über AEM zu authentifizieren?</td>
   <td>Überprüfen Sie, ob der Dispatcher <code>HEAD</code>-Anforderungen zur Authentifizierung an AEM sendet, bevor er die zwischengespeicherte Ressource bereitstellt. Dazu können Sie im <code>HEAD</code> von AEM nach der <code>access.log</code>-Anforderung suchen. Weitere Informationen finden Sie unter <a href="/help/sites-deploying/configure-logging.md">Protokollierung</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 6</strong></td>
   <td>Ist der geografische Standort des Dispatchers weit von den Benutzern entfernt?</td>
   <td>Verschieben Sie den Dispatcher näher an die Benutzer.</td>
  </tr>
  <tr>
   <td><strong>Schritt 7</strong></td>
   <td>Arbeitet die Netzwerkschicht des Dispatchers ordnungsgemäß?</td>
   <td><br /> Überprüfen Sie die Netzwerkschicht auf Sättigungs- und Latenzprobleme.<p> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 8</strong></td>
   <td>Ist die Langsamkeit bei einer lokalen Instanz reproduzierbar?</td>
   <td><br /> <p>Stellen Sie die Echtzeitbedingungen der Produktionsinstanzen mithilfe von <a href="/help/sites-developing/tough-day.md">Tough Day</a> nach. Wenn dies für die Geschwindigkeit Ihrer Entwicklung nicht realistisch ist, testen Sie die Produktionsinstanz (oder eine identische Staging-Instanz) in einem anderen Netzwerkkontext.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 9</strong></td>
   <td>Ist der geografische Standort des Servers weit von den Benutzern entfernt?</td>
   <td>Verschieben Sie den Server näher an die Benutzer.</td>
  </tr>
  <tr>
   <td><strong>Schritte 10 und 29</strong></td>
   <td>Untersuchung der Netzwerkschicht</td>
   <td><p>Überprüfen Sie die Netzwerkschicht auf Sättigungs- und Latenzprobleme.</p> <p>Für die Autorenstufe wird empfohlen, dass die Latenz 100 Millisekunden nicht überschreitet.</p> <p>Weitere Tipps zur Leistungsoptimierung finden Sie auf <a href="https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html">dieser Seite</a>.</p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 11</strong></td>
   <td>Server in der Nähe der Benutzer platzieren oder einen pro Region hinzufügen</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Schritt 12</strong></td>
   <td>Fehlerbehebung für AEM Server</td>
   <td>Weitere Informationen finden Sie in den folgenden Unterschritten im Diagramm.</td>
  </tr>
  <tr>
   <td><strong>Schritt 13</strong></td>
   <td>Überprüfen der Hardwareanforderungen</td>
   <td>Überprüfen Sie die Dokumentation unter <a href="/help/managing/hardware-sizing-guidelines.md">Richtlinien zur Hardware-Skalierung</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 14</strong></td>
   <td>Überprüfung der häufigen Ursachen für Leistungsprobleme</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Schritt 15</strong></td>
   <td>Suche nach langsamen Anforderungen</td>
   <td><p>Um nach langsamen Anforderungen zu suchen, können Sie das Protokoll <code>request.log</code> analysieren oder die Datei <code>rlog.jar</code> verwenden.</p> <p>Weitere Informationen zur Verwendung von rlog.jar finden Sie auf dieser Seite.</p> <p>Siehe <a href="/help/sites-deploying/monitoring-and-maintaining.md#using-rlog-jar-to-find-requests-with-long-duration-times">Verwenden von rlog.jar zum Suchen von Anforderungen mit langer Dauer</a>.<br /> </p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 16</strong></td>
   <td>Profilserver</td>
   <td><p>Informationen zu Profiling-Tools, die Sie mit AEM verwenden können, finden Sie unter <a href="/help/sites-deploying/monitoring-and-maintaining.md#tools-for-monitoring-and-analyzing-performance">Tools zur Leistungsüberwachung und -analyse</a>.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 17</strong></td>
   <td>Suche nach langsamen Methoden bei der Profilerstellung</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Schritt 18</strong></td>
   <td>Allgemeine Szenarien für die Profilerstellung</td>
   <td>Siehe <a href="/help/sites-deploying/monitoring-and-maintaining.md#analyzing-specific-scenarios">Analysieren spezifischer Szenarien</a> im Abschnitt Leistungsoptimierung .<br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 19</strong></td>
   <td>CPU-Auslastung 100 %</td>
   <td><a href="/help/sites-deploying/monitoring-and-maintaining.md#monitoring-performance">https://helpx.adobe.com/de/experience-manager/6-3/sites-deploying/monitoring-and-maintaining.html#MonitoringPerformance</a></td>
  </tr>
  <tr>
   <td><strong>Schritt 20</strong></td>
   <td>Unzureichender Speicher</td>
   <td><br />
    <ol>
     <li><a href="/help/sites-deploying/monitoring-and-maintaining.md#out-of-memory">Unzureichender Speicher</a></li>
     <li><a href="/help/sites-deploying/troubleshooting.md">Meine Anwendung gibt Fehler über unzureichenden Speicher aus</a></li>
     <li><a href="https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html">Analyse von Speicherproblemen mit der Helpx-Funktion.</a><br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Schritt 21</strong></td>
   <td>Datenträger-E/A</td>
   <td><p>Siehe <a href="/help/sites-deploying/monitoring-and-maintaining.md#disk-i-o">Datenträger-E/A</a> in der Dokumentation zu Überwachung und Wartung .</p> </td>
  </tr>
  <tr>
   <td><strong>Schritte 22 und 22.1</strong></td>
   <td>Cache-Verhältnis</td>
   <td>Siehe <a href="/help/sites-deploying/configuring-performance.md#calculating-the-dispatcher-cache-ratio">Berechnung des Dispatcher-Cache-Verhältnisses</a>.<br /> <br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 23</strong></td>
   <td>Langsame Abfragen</td>
   <td><a href="/help/sites-deploying/best-practices-for-queries-and-indexing.md">Best Practices für Abfragen und Indizierung</a></td>
  </tr>
  <tr>
   <td><strong>Schritt 24</strong></td>
   <td>Repository-Optimierung</td>
   <td>
    <ul>
     <li><a href="https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html">Tipps zur Leistungsoptimierung </a></li>
     <li><a href="/help/sites-deploying/configuring-performance.md#configuring-for-performance">Konfiguration zur Leistungsoptimierung</a></li>
     <li><a href="https://www.slideshare.net/jukka/repository-performance-tuning">Optimierung der Repository-Leistung</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Schritt 25</strong></td>
   <td>Ausführung von Workflows</td>
   <td>
    <ul>
     <li><a href="/help/sites-deploying/configuring-performance.md#concurrent-workflow-processing">Gleichzeitige Verarbeitung von Workflows</a></li>
     <li><a href="/help/sites-deploying/configuring-performance.md#configure-the-queue-for-a-specific-workflow">Konfigurieren der Warteschlange für einen spezifischen Workflow</a></li>
     <li><a href="/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances">Regelmäßiges Bereinigen von Workflow-Instanzen</a></li>
     <li><a href="/help/sites-developing/workflows.md#transient-workflows">Übergangs-Workflows</a><br /> </li>
    </ul> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 26</strong></td>
   <td>MSM-Infrastruktur</td>
   <td><p><a href="/help/sites-administering/msm-best-practices.md">Multi-Site-Manager – Best Practices</a><br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 27</strong></td>
   <td>Optimierung von Assets</td>
   <td>
    <ol>
     <li><a href="/help/sites-deploying/configuring-performance.md#cq-dam-asset-synchronization-service">Synchronisierungsdienst für Assets</a></li>
     <li><a href="/help/sites-deploying/configuring-performance.md#multiple-dam-instances">Mehrere DAM-Instanzen</a></li>
     <li>Artikel mit Tipps zur Leistungsoptimierung finden Sie <a href="https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html">hier</a> und <a href="https://helpx.adobe.com/de/experience-manager/kb/performance-tuning-tips.html">hier</a>.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Schritt 28</strong></td>
   <td>Nicht beendete Sitzungen</td>
   <td><p> </p> <p><a href="/help/sites-administering/troubleshoot.md#checking-for-unclosed-jcr-sessions">Überprüfung auf nicht beendete JCR-Sitzungen</a></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 30</strong></td>
   <td>Platzierung des Dispatchers in der Nähe der Benutzer (einen pro „Region“ hinzufügen?)</td>
   <td> </td>
  </tr>
  <tr>
   <td><strong>Schritt 31</strong></td>
   <td>Verwendung von CDN vor dem Dispatcher</td>
   <td><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html#using-dispatcher-with-a-cdn">Verwenden des Dispatchers mit einem CDN </a><br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 32</strong></td>
   <td>Nutzung der Sitzungsverwaltung auf Dispatcher-Ebene für die AEM-Serverabladung</td>
   <td><p><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement">Aktivierung von Sicherheitssitzungen</a></p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 33</strong></td>
   <td>Anforderungen zwischenspeicherbar machen</td>
   <td>
    <ol>
     <li><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher.html">Allgemeine Dispatcher-Konfiguration</a></li>
     <li><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache">Konfigurieren des Dispatcher-Caches</a></li>
    </ol> <p>Verbesserung des Cache-Verhältnisses; Anforderungen zwischenspeicherbar machen (Best Practices für Dispatcher)</p> <p>Berücksichtigen Sie auch die folgenden Einstellungen, um Ihre Caching-Konfigurationen zu optimieren.<br /> </p>
    <ol>
     <li>Festlegen einer Nicht-Cache-Regel für HTTP-Anforderungen, die keine GET sind</li>
     <li>Konfigurieren von nicht zwischenspeicherbaren Abfragezeichenfolgen</li>
     <li>URLs mit fehlenden Erweiterungen nicht zwischenspeichern</li>
     <li>Cache-Authentifizierungs-Header (möglich seit Dispatcher-Version 4.1.10)</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Schritt 34</strong></td>
   <td>Aktualisierung der Dispatcher-Version</td>
   <td><p>Sie können die neueste Dispatcher-Version hier herunterladen:</p> <p><a href="https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html">Link folgen</a></p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 35</strong></td>
   <td>Konfiguration des Dispatchers</td>
   <td><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/dispatcher-configuration.html">Konfigurieren des Dispatchers</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 36</strong></td>
   <td>Überprüfung der Cache-Invalidierung</td>
   <td><br />
    <ul>
     <li><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-the-authoring-environment">Cache-Invalidierung für die Autorenschicht</a></li>
     <li><a href="https://helpx.adobe.com/de/experience-manager/dispatcher/using/page-invalidate.html#invalidating-dispatcher-cache-from-a-publishing-instance">Cache-Invalidierung für die Veröffentlichungsschicht</a></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Schritte 37 und 38</strong></td>
   <td>Verzögertes Laden</td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html?lang=en">Weitere Informationen finden Sie in der Gem-Sitzung „AEM Web Performance“.</a><br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 39</strong></td>
   <td>Verwenden Sie Pre-Connect, um den Verbindungsaufwand zu reduzieren.</td>
   <td>Weitere Informationen finden Sie in der oben genannten Gem-Sitzung Zusätzliche Dokumentationsvorverknüpfung auf W3c:<a href="https://www.w3.org/TR/resource-hints/#dfn-preconnect"> https://www.w3.org/TR/resource-hints/#dfn-preconnect</a></td>
  </tr>
  <tr>
   <td><strong>Schritte 40 und 41</strong><br /> </td>
   <td>Latenz externer Hosts und Reaktionszeit</td>
   <td>Untersuchen Sie die Latenz und Reaktionszeit für die externen Hosts.</td>
  </tr>
  <tr>
   <td><strong>Schritte 45<br /> und 47</strong><br /> </td>
   <td>Verwendung von HTTP/2</td>
   <td>Weitere Informationen finden Sie in der Gem-Sitzung für die Schritte 37, 38 und 39 und in <a href="https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.topic.html/forum__kdzc-does_anyoneknowwhe.html">diesem</a> Forumsbeitrag zur HTTP/2-Unterstützung.<br /> </td>
  </tr>
  <tr>
   <td><strong>Schritt 49</strong></td>
   <td>Shrink-Payload-Größe</td>
   <td><a href="/help/sites-deploying/osgi-configuration-settings.md">Gzip aktivieren</a> und <a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html?lang=en">Bildgröße verkleinern</a>.<br /> </td>
  </tr>
  <tr>
   <td><strong>Schritte 42 und 43</strong></td>
   <td>Keep-Alive</td>
   <td><p>Ist der <code>Keep-Alive</code>-Header in den verschiedenen Anforderungen zur Wiederverwendung von Verbindungen vorhanden? Andernfalls führen alle Anforderungen dazu, dass eine weitere Verbindung hergestellt wird, wodurch ein unnötiger Verbindungsaufwand entsteht. (Standard-HTTP-Anforderungsanalyse im Browser)</p> <p>Sie können die <a href="/help/sites-administering/proxy-jar.md">Proxy-Server-Tool</a> um nach Keep-Alive-Verbindungen zu suchen.<br /> </p> </td>
  </tr>
  <tr>
   <td><strong>Schritt 44</strong></td>
   <td>Wie viele Anfragen werden gestellt?</td>
   <td>Führen Sie eine standardmäßige HTTP-Anforderungsanalyse im Browser durch.</td>
  </tr>
  <tr>
   <td><strong>Schritt 46</strong></td>
   <td>Anzahl der Anforderungen reduzieren</td>
   <td>
    <ol>
     <li>Verketten von Ressourcen (Bilder, CSS-Sprites, JSON usw.)<br /> </li>
     <li>Einbetten von Clientlibs:
      <ol>
       <li><a href="/help/sites-developing/clientlibs.md#creating-client-library-folders">Erstellen von Client-Bibliotheks-Ordnern</a> – siehe den Beitrag zur Minimierung von Anforderungen durch Einbetten</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Schritt 48</strong></td>
   <td>Wie groß ist die Payload?</td>
   <td>Standard-HTTP-Anforderungsanalyse im Browser</td>
  </tr>
  <tr>
   <td><strong>Schritte 50 und 51</strong></td>
   <td>JS-Codeblockierung</td>
   <td><a href="https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html?lang=en">https://experienceleague.adobe.com/docs/experience-manager-gems-events/gems/gems2016/aem-web-performance.html?lang=en</a></td>
  </tr>
 </tbody>
</table>
