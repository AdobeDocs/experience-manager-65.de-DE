---
title: Aktualisierung von Code und Anpassungen
seo-title: Aktualisierung von Code und Anpassungen
description: Erfahren Sie mehr über das Aktualisieren von benutzerdefiniertem Code in AEM.
seo-description: Erfahren Sie mehr über das Aktualisieren von benutzerdefiniertem Code in AEM.
uuid: dec11ef0-bf85-4e4e-80ac-dcb94cc3c256
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
discoiquuid: 59780112-6a9b-4de2-bf65-f026c8c74a31
docset: aem65
targetaudience: target-audience upgrader
translation-type: tm+mt
source-git-commit: f24142064b15606a5706fe78bf56866f7f9a40ae

---


# Aktualisierung von Code und Anpassungen{#upgrading-code-and-customizations}

Beim Planen einer Aktualisierung sollten folgende Bereiche der Implementierung untersucht und berücksichtigt werden.

* [Aktualisieren der Codebasis](#upgrade-code-base)
* [Anpassung an die 6.5-Repository-Struktur](#align-repository-structure)
* [AEM-Anpassungen](#aem-customizations)
* [Testverfahren](#testing-procedure) 

## Übersicht {#overview}

1. **Mustererkennung** : Führen Sie den Musterdetektor wie in der Aktualisierungsplanung beschrieben und auf [dieser Seite](/help/sites-deploying/pattern-detector.md) detailliert beschrieben aus, um einen Musterdetektorbericht mit weiteren Details zu Bereichen zu erhalten, die zusätzlich zu den nicht verfügbaren APIs/Bundles in der Zielgruppe von AEM behoben werden müssen. Der Bericht &quot;Mustererkennung&quot;sollte Sie auf Inkompatibilitäten im Code hinweisen. Wenn keine Kompatibilität besteht und Ihre Bereitstellung bereits 6.5 kompatibel ist, können Sie dennoch eine neue Entwicklung für die Verwendung der 6.5-Funktionalität durchführen. Sie benötigen sie jedoch nicht nur zur Aufrechterhaltung der Kompatibilität. Wenn Inkompatibilitäten gemeldet werden, können Sie entweder a) Im Kompatibilitätsmodus ausführen und Ihre Entwicklung auf neue 6.5-Funktionen oder Kompatibilität verschieben, b) beschließen, die Entwicklung nach der Aktualisierung durchzuführen und zu Schritt 2 wechseln. Please see please see [Backward Compatibility in AEM 6.5](/help/sites-deploying/backward-compatibility.md) for more details.

1. **Codebasis für 6.5 entwickeln **- Erstellen Sie eine dedizierte Verzweigung oder ein Repository für die Codebasis für die Zielgruppe. Nutzen Sie bei der Kompatibilitätsprüfung die vor der Aktualisierung erfassten Daten, um die Codebereiche zu planen, die aktualisiert werden sollen.
1. **Compile with 6.5 Uber jar **- Update code base POMs to point to 6.5 uber jar und Kompilieren von Code dagegen.
1. **AEM-Anpassungen** aktualisieren* - *Alle Anpassungen oder Erweiterungen von AEM sollten aktualisiert/validiert werden, um in 6.5 zu funktionieren, und der 6.5-Codebasis hinzugefügt werden. Dies beinhaltet Benutzeroberflächen-Suchformulare, Asset-Anpassungen und alle Komponenten, die „/mnt/overlay“ verwenden.

1. **Bereitstellung auf 6.5 Umgebung** - Eine saubere Instanz von AEM 6.5 (Autor + Veröffentlichung) sollte in einer Dev/QA-Umgebung stehen. Stellen Sie die aktualisierte Codebasis und ein repräsentatives Inhaltsbeispiel (aus der aktuellen Produktion) bereit.
1. **Validierung und Fehlerbehebung bei** der Qualitätssicherung: Die Qualitätssicherung sollte die Anwendung sowohl in der Autoreninstanz als auch in der Veröffentlichungsinstanz von 6.5 validieren. Alle gefundenen Fehler sollten behoben und an die 6.5-Codebasis gebunden werden. Wiederholen Sie den Entwicklungszyklus, falls erforderlich, bis alle Fehler korrigiert sind.

Bevor Sie mit der Aktualisierung beginnen, benötigen Sie eine stabile Anwendungscodebasis, die sorgfältig gegen die Zielversion von AEM getestet wurde. Basierend auf den im Rahmen der Tests gemachten Beobachtungen kann möglicherweise der benutzerdefinierte Code optimiert werden. Dazu können die Umgestaltung des Codes zum Durchsuchen des Repositorys, die benutzerdefinierte Indizierung für optimierte Suchabfragen, die Verwendung von unsortierten Knoten in JCR und andere Optimierungen gehören.

AEM 6.5 bietet Ihnen die Option, Ihre Codebasis und Ihre Anpassungen für die Zusammenarbeit mit der neuen AEM-Version zu aktualisieren. Außerdem hilft Ihnen AEM 6.5, Ihre Anpassungen mit der Abwärtskompatibilitätsfunktion effizienter zu verwalten, was auf [dieser Seite](/help/sites-deploying/backward-compatibility.md) beschrieben wird.

Wie oben bereits erwähnt und im folgenden Diagramm dargestellt, hilft Ihnen das Ausführen des [Musterdetektors](/help/sites-deploying/pattern-detector.md) im ersten Schritt, die gesamte Komplexität der Aktualisierung zu beurteilen und zu entscheiden, ob Sie den Kompatibilitätsmodus nutzen oder Ihre Anpassungen aktualisieren möchten, um alle neuen Funktionen von AEM 6.5 zu verwenden. Please see the [Backward Compatibility in AEM 6.5](/help/sites-deploying/backward-compatibility.md) page for more details.
[ ![opt_cut](assets/opt_cropped.png)](assets/upgrade-code-base-highlevel.png)

## Aktualisieren der Codebasis {#upgrade-code-base}

### Erstellen einer dedizierten Verzweigung für 6.5-Code in der Versionskontrolle {#create-a-dedicated-branch-for-6.5-code-in-version-control}

Es empfiehlt sich, den Code und die Konfigurationen für die AEM-Implementierung in einer Versionskontrolle zu verwalten. Erstellen Sie eine dedizierte Verzweigung in der Versionskontrolle, um Änderungen an der Codebasis in der AEM-Zielversion zu verwalten. Iterative Tests der Codebasis für die Zielversion von AEM und anschließende Fehlerkorrekturen können in dieser Verzweigung verwaltet werden.

### Aktualisieren der UberJar-Version von AEM {#update-the-aem-uber-jar-version}

AEM-UberJar beinhaltet alle AEM-APIs als einzelne Abhängigkeiten in der Datei `pom.xml` des Maven-Projekts. Als beste Vorgehensweise empfiehlt es sich immer, UberJar als einzige Abhängigkeit anstelle von individuellen AEM-API-Abhängigkeiten zu verwenden. Bei der Aktualisierung der Codebasis sollte die UberJar-Version so geändert werden, dass sie auf die Zielversion von AEM verweist. Falls das Projekt mit einer Version von AEM entwickelt wurde, für die UberJar noch nicht verfügbar war, müssen alle individuellen AEM-API-Abhängigkeiten entfernt und durch eine einzige UberJar-Abhängigkeit für die Zielversion von AEM ersetzt werden. Kompilieren Sie dann die Codebasis erneut gegen die neue Version von UberJar. Alle veralteten APIs und Methoden müssen aktualisiert werden, um mit der Zielversion von AEM kompatibel zu sein.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Einstellen der Verwendung des administrativen Ressourcen-Resolver {#phase-out-use-of-administrative-resource-resolver}

The use of an administrative session through `SlingRepository.loginAdministrative()` and `ResourceResolverFactory.getAdministrativeResourceResolver()` was quite prevalent in code bases prior to AEM 6.0. These methods have been deprecated for security reasons as they give too broad of a level of access. [In künftigen Versionen von Sling ist diese Methode nicht mehr enthalten](https://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecation-of-administrative-authentication). Es wird dringend empfohlen, stattdessen „Dienstbenutzer“ für den Code zu verwenden. Weitere Informationen zu Dienstbenutzern und dazu, [wie Sie die Verwendung von administrativen Sessions einstellen, finden Sie hier](/help/sites-administering/security-service-users.md#how-to-phase-out=admin-sessions).

### Abfragen und Oak-Indizes {#queries-and-oak-indexes}

Abfragen in der Codebasis müssen im Rahmen der Aktualisierung sorgfältig getestet werden. Für Kunden, die von Jackrabbit 2 (ältere Versionen als AEM 6.0) aus eine Aktualisierung durchführen, ist dies besonders wichtig, da Inhalt von Oak nicht automatisch indiziert wird und möglicherweise benutzerdefinierte Indizes erstellt werden müssen. Falls Sie von einer AEM 6.x-Version aus eine Aktualisierung durchführen, haben sich die vorkonfigurierten Oak-Indexdefinitionen möglicherweise geändert, was sich auf vorhandene Abfragen auswirken kann.

Es sind mehrere Tools zum Analysieren und Überprüfen der Abfrageleistung verfügbar:

* [AEM-Indizierungs-Tools](/help/sites-deploying/queries-and-indexing.md)

* [Vorgangsdiagnose-Tools für die Abfrageleistung](/help/sites-administering/operations-dashboard.md#diagnosis-tools)

* [Oak-Dienstprogramme](https://oakutils.appspot.com/). Hierbei handelt es sich um Open-Source-Tools, die nicht von Adobe stammen.

### Klassisches UI-Authoring {#classic-ui-authoring}

Das klassische Benutzeroberflächen-Authoring ist in AEM 6.5 weiterhin verfügbar, ist jedoch veraltet. Weitere Informationen finden Sie [hier](/help/release-notes/deprecated-removed-features.md#pre-announcement-for-next-release). Falls die Applikation derzeit in einer Umgebung mit klassischem Benutzeroberflächen-Authoring ausgeführt wird, wird empfohlen, auf AEM 6.5 zu aktualisieren und die klassische Benutzeroberfläche weiterhin zu verwenden. Die Migration zur Touch-optimierten Benutzeroberfläche kann als separates Projekt geplant und in mehreren Entwicklungszyklen abgeschlossen werden. Um die klassische Benutzeroberfläche in AEM 6.5 zu verwenden, sind mehrere OSGi-Konfigurationen erforderlich, die in der Codebasis gespeichert werden müssen. Einzelheiten zur Konfiguration finden Sie [hier](/help/sites-administering/enable-classic-ui.md).

## Anpassung an die 6.5-Repository-Struktur {#align-repository-structure}

Um Aktualisierungen zu vereinfachen und sicherzustellen, dass Konfigurationen während einer Aktualisierung nicht überschrieben werden, wird das Repository in 6.4 umstrukturiert, um Inhalt und Konfiguration voneinander zu trennen.

Therefore, a number of settings must be moved to no longer reside under `/etc` as had been the case in the past. To review the full set of repository restructuring concerns that must be reviewed and accomodated in the updated to AEM 6.4, see [Repository Restructuring in AEM 6.4](/help/sites-deploying/repository-restructuring.md).

## AEM-Anpassungen  {#aem-customizations}

Alle Anpassungen der AEM-Authoring-Umgebung in der Quellversion von AEM müssen identifiziert werden. Sobald die Anpassungen identifiziert sind, wird empfohlen, diese in der Versionskontrolle oder als minimale Sicherungskopie als Teil eines Inhaltspakets zu speichern. Vor einer Produktionsaktualisierung müssen alle Anpassungen in einer QA- oder Staging-Umgebung bereitgestellt und validiert werden, die auf der Zielversion von AEM ausgeführt wird.

### Allgemeine Hinweise zu Überlagerungen {#overlays-in-general}

Es ist üblich, vorkonfigurierte AEM-Funktionen durch Überlagerung von Knoten und/oder Dateien unter /libs mit zusätzlichen Knoten unter /apps zu erweitern. Diese Überlagerungen sollten in der Versionskontrolle nachverfolgt und für die Zielversion von AEM getestet werden. Falls eine Datei (z. B. JS, JSP, HTL) überlagert wird, wird empfohlen, einen Kommentar mit Informationen zu speichern, welche Funktionalität erweitert wurde. Dies erleichtert Regressionstests auf der Zielversion von AEM. Weitere allgemeine Informationen zu Überlagerungen finden Sie [hier](/help/sites-developing/overlays.md). Anweisungen für spezifische AEM-Überlagerungen finden Sie unten.

### Aktualisieren von benutzerdefinierten Suchformularen {#upgrading-custom-search-forms}

Benutzerdefinierte Suchfacetten müssen nach der Aktualisierung teilweise manuell angepasst werden, damit sie ordnungsgemäß funktionieren. Weitere Einzelheiten finden Sie unter [Aktualisieren von benutzerdefinierten Suchformularen](/help/sites-deploying/upgrading-custom-search-forms.md).

### Assets-UI-Anpassungen {#assets-ui-customizations}

>[!NOTE]
>
>Dieses Verfahren ist nur für Aktualisierungen von Versionen vor AEM 6.2 erforderlich.

Instanzen mit benutzerdefinierten bereitgestellten Assets müssen für die Aktualisierung vorbereitet werden. Damit soll sichergestellt werden, dass alle benutzerdefinierten Inhalte mit der neuen Knotenstruktur von AEM 6.4 kompatibel sind.

Sie können Anpassungen der Benutzeroberfläche &quot;Assets&quot;wie folgt vorbereiten:

1. On the instance that needs to be upgraded, open CRXDE Lite by going to *https://server:port/crx/de/index.jsp*

1. Navigieren Sie zum folgenden Knoten:

   * `/apps/dam/content`

1. Benennen Sie den Knoten content in **content_backup** um. Hierzu können Sie mit der rechten Maustaste auf den Explorer-Bereich links im Fenster klicken und **Umbenennen** auswählen.

1. Once the node has been renamed, create a new node named content under `/apps/dam` named **content** and set its node type to **sling:Folder**.

1. Verschieben Sie alle untergeordneten Knoten von **content_backup** in den neu erstellten Knoten content. Hierzu können Sie mit der rechten Maustaste auf die einzelnen untergeordneten Knoten im Explorer-Bereich klicken und **Verschieben** auswählen.

1. Löschen Sie den Knoten **content_backup**.

1. The updated nodes beneath `/apps/dam` with the correct node type of `sling:Folder` should ideally be saved into version control and deployed with the code base or at a minimum backed up as content package.

### Generieren von Asset-IDs für vorhandene Assets {#generating-asset-ids-for-existing-assets}

Um Asset-IDs für vorhandene Assets zu generieren, aktualisieren Sie diese, wenn Sie die AEM-Instanz auf AEM 6.5 aktualisieren. Dies ist erforderlich, um die Funktion [Assets Insights](/help/assets/touch-ui-asset-insights.md) zu aktivieren. For more details, see [Add embed code](/help/assets/touch-ui-using-page-tracker.md#add-embed-code).

Um Assets zu aktualisieren, konfigurieren Sie das Paket „Associate Asset IDs“ in der JMX-Konsole. Je nach Anzahl der Assets im Repository kann das Ausführen von `migrateAllAssets` lange dauern. Internen Tests zufolge liegt der Schätzwert für TarMK bei einem Durchsatz von 125000 Assets pro Stunde.

![1487758945977](assets/1487758945977.png)

Falls Sie Asset-IDs für eine Untermenge Ihrer gesamten Assets benötigen, verwenden Sie die API `migrateAssetsAtPath`.

For all other purposes, use the `migrateAllAssets()` API.

### InDesign-Skript-Anpassungen {#indesign-script-customizations}

Adobe recommends putting custom scripts at `/apps/settings/dam/indesign/scripts` location. Weitere Informationen zu InDesign-Skript-Anpassungen finden Sie [hier](/help/assets/indesign.md#configuring-the-aem-assets-workflow).

### Wiederherstellen von ContextHub-Konfigurationen {#recovering-contexthub-configurations}

ContextHub-Konfigurationen sind von einer Aktualisierung betroffen. Anweisungen, wie Sie vorhandene ContextHub-Konfigurationen wiederherstellen, finden Sie [hier](/help/sites-administering/contexthub-config.md#recovering-contexthub-configurations-after-upgrading).

### Workflow-Anpassungen {#workflow-customizations}

Vorkonfigurierte Workflows werden häufig angepasst, um Funktionen hinzuzufügen oder nicht erforderliche Funktionen zu löschen. A common workflow that is customized is the [!UICONTROL DAM Update Asset] workflow. Erstellen Sie eine Sicherungskopie aller für eine angepasste Implementierung erforderlichen Workflows und speichern Sie diese in der Versionskontrolle, da sie möglicherweise bei einer Aktualisierung überschrieben werden.

### Bearbeitbare Vorlagen {#editable-templates}

>[!NOTE]
>
>Dieses Verfahren ist nur für Site-Aktualisierungen, bei denen bearbeitbare Vorlagen aus AEM 6.2 verwendet werden, erforderlich.

Die Struktur bearbeitbarer Vorlagen in AEM 6.2 wurde in Version 6.3 geändert. Wenn Sie ein Upgrade von 6.2 oder älter durchführen und wenn Sie Site-Inhalt mit bearbeitbaren Vorlagen erstellt haben, müssen Sie das [Responsive Nodes Clean Up-Tool](https://github.com/Adobe-Marketing-Cloud/aem-sites-template-migration) verwenden. Das Tool muss **nach** einer Aktualisierung ausgeführt werden, um Inhalt zu bereinigen. Es muss auf der Autoren- und der Veröffentlichungsschicht ausgeführt werden.

### Änderungen der CUG-Implementierung {#cug-implementation-changes}

Die Implementierung geschlossener Benutzergruppen (Closed User Groups, CUG) wurde weitgehend geändert, um die Leistungs- und Skalierbarkeitsbeschränkungen früherer AEM-Versionen zu beheben. Die vorherige Version von CUG ist in 6.3 nicht mehr enthalten. Die neue Implementierung wird nur in der Touch-optimierten Benutzeroberfläche unterstützt. If you are upgrading from 6.2 or ealier then Instructions to migrate to the new CUG implementation can be found [here](/help/sites-administering/closed-user-groups.md#upgradetoaem63).

## Testverfahren {#testing-procedure}

Zum Testen von Aktualisierungen sollte ein umfassender Testplan erstellt werden. Das Testen der aktualisierten Codebasis und Anwendung muss zuerst in Umgebungen auf niedrigerer Ebene erfolgen. Alle Fehler müssen iterativ korrigiert werden, bis die Codebasis stabil ist. Aktualisieren Sie erst dann Umgebungen auf höherer Ebene.

### Testen des Aktualisierungsverfahrens {#testing-the-upgrade-procedure}

Testen Sie das hier beschriebene Aktualisierungsverfahren in Entwicklungs- und QA-Umgebungen, wie im benutzerdefinierten Runbook dokumentiert (siehe [Planung der Aktualisierung](/help/sites-deploying/upgrade-planning.md)). Das Aktualisierungsverfahren muss wiederholt werden, bis alle Schritte im Aktualisierungs-Runbook dokumentiert sind und das Aktualisierungsverfahren reibungslos läuft.

### Testbereiche der Implementierung  {#implementation-test-areas-}

Im Folgenden sind wichtige Bereiche einer AEM-Implementierung genannt, die vom Testplan abgedeckt sein müssen, sobald die Umgebung aktualisiert und die aktualisierte Codebasis bereitgestellt wurde.

<table>
 <tbody>
  <tr>
   <td><strong>Funktioneller Testbereich</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Veröffentlichte Websites</td>
   <td>Testen von AEM-Implementierung und zugehörigem Code auf der Veröffentlichungsschicht<br /> durch den Dispatcher. Muss Kriterien für Seitenaktualisierungen und<br /> Cache-Invalidierungen enthalten.</td>
  </tr>
  <tr>
   <td>Authoring – </td>
   <td>Testen von AEM-Implementierung und zugehörigem Code auf der Autorenschicht. Dabei sollten Seiten, Komponenten-Authoring und Dialoge berücksichtigt werden.</td>
  </tr>
  <tr>
   <td>Integrationen mit Marketing Cloud-Lösungen</td>
   <td>Validieren von Integrationen mit Analyseprodukten wie Analytics, DTM und Target.</td>
  </tr>
  <tr>
   <td>Integrationen mit Drittanbietersystemen</td>
   <td>Drittanbieter-Integrationen müssen auf der Autoren- und Veröffentlichungsschicht validiert werden.</td>
  </tr>
  <tr>
   <td>Authentifizierung, Sicherheit und Berechtigungen</td>
   <td>Alle Authentifizierungsmechanismen wie LDAP/SAML müssen validiert werden.<br /> Berechtigungen und Gruppen müssen auf der Autoren- und der Veröffentlichungsschicht<br /> getestet werden.</td>
  </tr>
  <tr>
   <td>Abfragen</td>
   <td>Benutzerdefinierte Indizes und Abfragen müssen zusammen mit der Abfrageleistung getestet werden.</td>
  </tr>
  <tr>
   <td>UI-Anpassungen</td>
   <td>Alle Erweiterungen und Anpassungen der AEM-Benutzeroberfläche in der Autorenumgebung.</td>
  </tr>
  <tr>
   <td>Workflows  </td>
   <td>Benutzerdefinierte und/oder vorkonfigurierte Workflows und Funktionen.</td>
  </tr>
  <tr>
   <td>Leistungstests</td>
   <td>Lasttests müssen auf der Autoren- und Veröffentlichungsschicht erfolgen und echte Szenarien simulieren.</td>
  </tr>
 </tbody>
</table>

### Dokumentieren von Testplänen und Ergebnissen {#document-test-plan-and-results}

Erstellen Sie einen Testplan, der die oben genannten Testbereiche der Implementierung abdeckt. In vielen Fällen ist es sinnvoll, den Testplan nach Aufgabenlisten für Autoren- und Veröffentlichungsumgebungen zu trennen. Dieser Testplan muss auf Entwicklungs-, QA- und Staging-Umgebung ausgeführt werden, bevor Produktionsumgebungen aktualisiert werden. Erfassen Sie die Testergebnisse und Leistungsmetriken aus Umgebungen niedrigerer Ebenen als Referenzwerte für die Aktualisierung der Staging- und Produktionsumgebungen.
