---
title: Planung von Upgrades
description: Dieser Artikel unterstützt Sie bei der Formulierung von klaren Zielen, Phasen und Arbeitsergebnissen bei der Planung eines Upgrades von AEM.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: 0dea2b3e-fd7c-4811-a04a-6852ffc1e6d6
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2423'
ht-degree: 100%

---

# Planung von Upgrades{#planning-your-upgrade}

## AEM-Projektüberblick {#aem-project-overview}

AEM kommt häufig in umfangreichen Bereitstellungen zum Einsatz, die möglicherweise von Millionen von Benutzern genutzt werden. In der Regel werden auf den Instanzen auch benutzerdefinierte Anwendungen bereitgestellt, wodurch die Komplexität weiter erhöht wird. Jedes Upgrade einer solchen Bereitstellung muss deshalb methodisch angegangen werden.

Dieser Leitfaden unterstützt Sie bei der Formulierung von klaren Zielen, Phasen und Ergebnissen bei der Planung des Upgrades. Im Mittelpunkt des Leitfadens stehen die Abwicklung und die Richtlinien des gesamten Projekts. Er gibt einen Überblick über die konkreten Upgrade-Schritte und verweist auf verfügbare technische Ressourcen, falls erforderlich. Es sollte mit den verfügbaren technischen Ressourcen verwendet werden, auf die in dem Dokument verwiesen wird.

Der Upgrade-Prozess für AEM erfordert sorgfältig ausgeführte Planungs-, Analyse- und Durchführungsphasen, für die jeweils wichtige Ergebnisse festgelegt werden müssen.

Ein direktes Upgrade von AEM 6.0 und höheren Versionen auf Version 6.5 ist möglich. Kundinnen und Kunden mit AEM 5.6.x und älteren Versionen müssen jedoch zuerst ein Upgrade auf Version 6.0 oder höher durchführen (empfohlen wird 6.0 SP3). Außerdem wird seit 6.3 jetzt das neue Oak Segment Tar-Format für den Segment-Knotenspeicher verwendet, und die Repository-Migration auf dieses neue Format ist auch schon für 6.0, 6.1 und 6.2 obligatorisch.

>[!CAUTION]
>
>Wenn Sie von AEM 6.2 auf 6.3 upgraden, sollten Sie ENTWEDER von den Versionen **6.2-SP1-CFP1 - 6.2-SP1-CFP12.1** oder ab der Version **6.2-SP1-CFP15** upgraden. Wenn Sie jedoch von **6.2-SP1-CFP13/6.2-SP1CFP14** auf AEM 6.3 upgraden, müssen Sie mindestens auf Version **6.3.2.2** upgraden. Ansonsten kann AEM Sites nach der Aktualisierung nicht ausgeführt werden.

## Upgrade-Umfang und -Anforderungen {#upgrade-scope-requirements}

Nachfolgend finden Sie eine Liste der Bereiche, die von einem typischen AEM-Upgrade-Projekt betroffen sind:

<table>
 <tbody>
  <tr>
   <td><strong>Komponente</strong></td>
   <td><strong>Auswirkungen</strong></td>
   <td><strong>Beschreibung</strong></td>
  </tr>
  <tr>
   <td>Betriebssystem</td>
   <td>Ungewisse, aber subtile Auswirkungen</td>
   <td>Möglicherweise muss beim Upgrade von AEM auch das Betriebssystem aktualisiert werden. Dies kann gewisse Auswirkungen haben.</td>
  </tr>
  <tr>
   <td>Java™ Runtime</td>
   <td>Moderate Auswirkung</td>
   <td>AEM 6.3 erfordert JRE 1.7.x (64 Bit) oder höher. JRE 1.8 ist derzeit die einzige Version, die von Oracle unterstützt wird.</td>
  </tr>
  <tr>
   <td>Hardware</td>
   <td>Moderate Auswirkung</td>
   <td>Für die Online-Revisionsbereinigung sind freier<br /> Speicherplatz, der 25 % des Repository-Volumens entspricht, sowie 15 % freier Heap-Speicher erforderlich,<br /> um die Bereinigung erfolgreich abzuschließen. Möglicherweise müssen Sie Ihre Hardware aufrüsten, um<br /> sicherzustellen, dass ausreichend Ressourcen für die vollständige Ausführung der Online-Revisionsbereinigung<br /> verfügbar sind. Wenn ein Upgrade von einer Version vor AEM 6 durchgeführt wird,<br /> kann es zusätzliche Speicheranforderungen geben.</td>
  </tr>
  <tr>
   <td>Content Repository (CRX oder Oak)</td>
   <td>Starke Auswirkungen</td>
   <td>Ab Version 6.1 bietet AEM keine Unterstützung für CRX2, sodass eine Migration auf<br /> Oak (CRX3) erforderlich ist, wenn eine Aktualisierung von einer älteren Version durchgeführt wird. In AEM 6.3 wurde<br /> ein neuer Segment-Knotenspeicher implementiert, der ebenfalls migriert werden muss. Zu<br /> diesem Zweck wird das Tool crx2oak verwendet.</td>
  </tr>
  <tr>
   <td>AEM-Komponenten/-Inhalte</td>
   <td>Moderate Auswirkung</td>
   <td><code>/libs</code> und <code>/apps</code> werden beim Upgrade problemlos verarbeitet; <code>/etc</code> erfordert in der Regel jedoch eine erneute Anwendung der Anpassungen.</td>
  </tr>
  <tr>
   <td>AEM-Services</td>
   <td>Geringe Auswirkungen</td>
   <td>Der Großteil der AEM-Core Services wird für ein Upgrade getestet. Dies ist ein Bereich mit geringen Auswirkungen.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Anwendungsdienste</td>
   <td>Geringe bis starke Auswirkungen</td>
   <td>Je nach Anwendung und Anpassung kann es<br /> Abhängigkeiten von JVM, Betriebssystemversionen und einigen Änderungen im Zusammenhang mit der Indizierung<br /> geben, da Indizes in Oak nicht automatisch generiert werden.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Anwendungsinhalte</td>
   <td>Geringe bis starke Auswirkungen</td>
   <td>Inhalte, die vom Upgrade nicht betroffen sind, können vorher gesichert<br /> und dann wieder in das Repository verschoben werden.<br /> Die meisten Inhalte können mithilfe des Migrationstools verarbeitet werden.</td>
  </tr>
 </tbody>
</table>

Sie müssen sicherstellen, dass ein unterstütztes Betriebssystem, eine unterstützte Java™-Laufzeitumgebung sowie eine unterstützte httpd- und Dispatcher-Version ausgeführt werden. Weitere Informationen finden Sie auf der Seite [Technische Anforderungen für AEM 6.5](/help/sites-deploying/technical-requirements.md). Die Aktualisierung dieser Komponenten muss in Ihrem Projektplan berücksichtigt werden und sollte vor dem Upgrade von AEM erfolgen.

## Projektphasen {#project-phases}

Die Planung und Durchführung eines AEM-Upgrades ist mit viel Arbeit verbunden. Um den unterschiedlichen Aufwand zu verdeutlichen, der mit diesem Prozess verbunden ist, hat Adobe die Planung und Ausführung in verschiedene Phasen unterteilt. In den folgenden Abschnitten führt jede Phase zu einer zu erbringenden Leistung, die häufig in einer späteren Projektphase verwendet wird.

### Planen der Autorenschulung {#planning-for-author-training}

In jeder neuen Version ist mit potenziellen Änderungen an der Benutzeroberfläche und den Benutzer-Workflows zu rechnen. Außerdem werden in neuen Versionen neue Funktionen eingeführt, deren Nutzung sich für das Unternehmen als vorteilhaft erweisen kann. Adobe empfiehlt, die eingeführten Funktionsänderungen zu überprüfen und einen Plan für die Schulung der Benutzenden zu erstellen, damit diese die neuen Funktionen effektiv nutzen können.

![unu_cropped](assets/unu_cropped.png)

Neue Funktionen in AEM 6.5 finden Sie im [Bereich zu AEM auf adobe.com](/help/release-notes/release-notes.md). Achten Sie vor allem auf Änderungen an Benutzeroberflächen oder Produktfunktionen, die in Ihrem Unternehmen häufig verwendet werden. Wenn Sie sich über die neuen Funktionen informieren, achten Sie auch auf neue Funktionen, die für Ihr Unternehmen von Nutzen sein können. Sobald Sie sich mit den Änderungen in AEM 6.5 vertraut gemacht haben, entwickeln Sie einen Schulungsplan für Ihre Autoren. Dazu kann die Verwendung frei verfügbarer Ressourcen wie Videos zu Hilfefunktionen oder formales Training über [Adobe Digital Learning Services](https://learning.adobe.com/) beitragen.

### Erstellen eines Testplans {#creating-a-test-plan}

Jede Kundenimplementierung von AEM ist einzigartig und auf die Geschäftsanforderungen des Unternehmens zugeschnitten. Deshalb ist es wichtig, alle am System vorgenommenen Anpassungen zu ermitteln, damit sie in einen Testplan einbezogen werden können. Dieser Testplan bildet die Basis für den QS-Prozess, den Adobe für die aktualisierten Instanzen durchführt.

![test-plan](assets/test-plan.png)

Die Produktionsumgebung muss exakt dupliziert und nach dem Upgrade getestet werden, um sicherzustellen, dass alle Anwendungen und benutzerdefinierter Code weiterhin wie gewünscht ausgeführt werden. Sie müssen alle Anpassungen rückgängig machen und Leistungs-, Last- und Sicherheitstests durchführen. Beziehen Sie beim Organisieren des Testplans neben den vorkonfigurierten Benutzeroberflächen und Workflows, die für Ihre täglichen Betriebsabläufe genutzt werden, alle am System vorgenommenen Anpassungen in den Plan mit ein. Hierzu gehören möglicherweise benutzerdefinierte OSGi-Dienste und -Servlets, Integrationen mit Adobe Experience Cloud, Integrationen mit Drittanbieteranwendungen über AEM-Connectoren, benutzerdefinierte Drittanbieterintegrationen, benutzerdefinierte Komponenten und Vorlagen, benutzerdefinierte Benutzeroberflächen-Überlagerungen in AEM und benutzerdefinierte Workflows. Kunden, die eine Migration von einer Version vor AEM 6 durchführen, sollten alle benutzerdefinierten Abfragen analysieren, da diese u. U. indiziert werden müssen. Kundinnen und Kunden, die bereits eine Version AEM 6.x verwenden, sollten diese Abfragen dennoch testen, um sicherzustellen, dass ihre Indizes nach der Aktualisierung weiterhin effektiv funktionieren.

### Ermitteln der erforderlichen Architektur- und Infrastrukturänderungen {#determining-architectural-and-infrastructure-changes-needed}

Sie müssen bei einem Upgrade möglicherweise auch andere Komponenten Ihres Technologie-Stacks upgraden, z. B. das Betriebssystem oder JVM. Darüber hinaus kann aufgrund von Änderungen an der Repository-Konfiguration u. U. zusätzliche Hardware erforderlich sein. Dies betrifft zwar nur Kundinnen und Kunden, die eine Migration von Instanzen vor Version 6.x durchführen, muss jedoch berücksichtigt werden. Schließlich können Änderungen an Ihren betrieblichen Verfahren erforderlich sein, einschließlich Überwachungs-, Wartungs-, Sicherungs- und Notfallwiederherstellungsprozessen.

![doi_cropped](assets/doi_cropped.png)

Überprüfen Sie die technischen Anforderungen für AEM 6.5 und stellen Sie sicher, dass Ihre Hardware und Software die Voraussetzungen erfüllen. Informationen zu potenziellen Änderungen an Ihren Betriebsabläufen finden Sie in den folgenden Dokumenten:

**Überwachung und Wartung**

[Vorgangs-Dashboard](/help/sites-administering/operations-dashboard.md)

[Asset-Überwachung – Best Practices](/help/assets/assets-monitoring-best-practices.md)

[Überwachen von Server-Ressourcen mit der JMX-Konsole](/help/sites-administering/jmx-console.md)

[Revisionsbereinigung](/help/sites-deploying/revision-cleanup.md)

**Sicherung/Wiederherstellung und Notfallwiederherstellung:**

[Sichern und Wiederherstellen](/help/sites-administering/backup-and-restore.md)

[Leistung und Skalierbarkeit](/help/sites-deploying/performance.md)

[Ausführen von AEM mit der TarMK-Cold-Standby-Funktion](/help/sites-deploying/tarmk-cold-standby.md)

#### Überlegungen zur Neustrukturierung des Contents {#content-restructuring-considerations}

Mit AEM werden Änderungen an der Repository-Struktur eingeführt, mit denen Upgrades noch nahtloser durchgeführt werden können. Diese Änderungen erfordern, dass Inhalte aus dem Ordner /etc in Ordner wie /libs, /apps und /content verschoben werden – je nachdem, ob Adobe oder der Kunde Eigentümer des Inhalts ist – um die Wahrscheinlichkeit zu verringern, dass Inhalte durch Aktualisierungen überschrieben werden. Die Repository-Umstrukturierung wurde so vorgenommen, dass zum Zeitpunkt des Upgrades auf 6.5 keine Code-Änderungen erforderlich sein sollten. Es wird jedoch empfohlen, bei der Planung eines Upgrades die Details unter [Repository-Umstrukturierung in AEM](/help/sites-deploying/repository-restructuring.md) zu lesen.

### Bewertung der Komplexität des Upgrades {#assessing-upgrade-complexity}

Aufgrund der von Adobe-Kundinnen und -Kunden an ihren AEM-Umgebungen vorgenommenen Anpassungen, die sich hinsichtlich des Umfangs und der Art der Anpassung weitgehend unterscheiden, ist es wichtig, vor einem Upgrade den damit verbundenen Aufwand zu bestimmen.

Es gibt zwei Ansätze zur Bewertung der Komplexität des Upgrades. In einer Vorbereitungsphase können Sie den neuen Musterdetektor verwenden, der auf Ihren AEM 6.1-, 6.2- und 6.3-Instanzen ausgeführt werden kann. Der Musterdetektor bietet die einfachste Möglichkeit, die erwartete Gesamtkomplexität des Upgrades anhand der gefundenen Muster zu bewerten. Der Bericht des Musterdetektors enthält Muster, mit denen veraltete APIs identifiziert werden können, die von der benutzerdefinierten Code-Basis verwendet werden (dies wurde in 6.3 mithilfe von Kompatibilitätsprüfungen vor dem Upgrade durchgeführt).

Nach dieser anfänglichen Bewertung kann in einem umfangreicheren nächsten Schritt ein Upgrade einer Testinstanz durchgeführt werden, um einige grundlegende Tests durchzuführen. Adobe bietet ebenfalls einige. Außerdem sollte die Liste der [veralteten und entfernten Funktionen](/help/release-notes/deprecated-removed-features.md) überprüft werden, und zwar nicht nur in Bezug auf die Version, auf die Sie die Aktualisierung durchführen, sondern auch bezüglich der Versionen zwischen Ihrer Quell- und Zielversion. Bei einer Aktualisierung von AEM 6.2 auf 6.5 ist es beispielsweise wichtig, die veralteten und entfernten Funktionen von AEM 6.3 neben denen von AEM 6.5 zu überprüfen.

![trei_cropped](assets/trei_cropped.png)

Der kürzlich eingeführte Musterdetektor liefert Ihnen eine recht genaue Schätzung dessen, was Sie während eines Upgrades in den meisten Fällen erwarten können. Für komplexere Anpassungen und Bereitstellungen, in denen inkompatible Änderungen vorhanden sind, können Sie jedoch eine Entwicklungsinstanz auf AEM 6.5 upgraden. Eine Anleitung finden Sie unter [Durchführen eines In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md). Führen Sie nach der Aktualisierung eine Reihe Feuerproben der hohen Stufe für die Umgebung durch. Sie dienen nicht dazu, das Nutzungsszenario umfassend zu testen und eine formelle Liste mit Defekten zu erstellen. Vielmehr soll der geschätzte erforderliche Arbeitsaufwand für das Upgrade des Codes ermittelt werden, um die Kompatibilität mit Version 6.5 sicherzustellen. Wenn die [Mustererkennung](/help/sites-deploying/pattern-detector.md) mit den Änderungen an der Architektur kombiniert wird, die im vorherigen Abschnitt beschrieben wurden, liefert dies eine grobe Schätzung, mit deren Hilfe das Projektleiter-Team das Upgrade planen kann.

### Erstellen des Runbooks für das Upgrade und das Rollback {#building-the-upgrade-and-rollback-runbook}

Obwohl Adobe den Prozess für die Aktualisierung von AEM-Instanzen dokumentiert hat, muss der Ansatz entsprechend dem Netzwerk-Layout, der Bereitstellungsarchitektur und den Anpassungen jeder Kundin und jedes Kunden optimiert und darauf zugeschnitten werden. Adobe empfiehlt deshalb, die gesamte verfügbare Dokumentation zu lesen und auf dieser Basis ein projektspezifisches Runbook mit den speziellen Upgrade- und Rollback-Verfahren für Ihre Umgebung zu erstellen. Stellen Sie bei einer Aktualisierung von CRX2 sicher, dass Sie die Dauer der Inhaltsmigration von CRX2 auf Oak evaluieren. Für große Repositorys könnte diese erheblich sein.

![runbook-diagram](assets/runbook-diagram.png)

Unter [Upgrade-Verfahren](/help/sites-deploying/upgrade-procedure.md) finden Sie Upgrade- und Rollback-Verfahren sowie Schritt-für-Schritt-Anleitungen für die Durchführung eines [In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md). Diese Anweisungen sollten überprüft und für Ihre Systemarchitektur, Anpassungen und Ausfallzeitentoleranz berücksichtigt werden, um die entsprechenden Switchover- und Rollback-Vorgänge zu bestimmen, die Sie während des Upgrades ausführen. Änderungen an der Architektur oder Servergröße sollten bei der Erstellung Ihres benutzerdefinierten Runbooks miteinbezogen werden. Beachten Sie, dass diese Version als erster Entwurf gelten sollte. Möglicherweise sind nach Abschluss der QS- und Entwicklungszyklen und der Bereitstellung des Upgrades in der Staging-Umgebung weitere Schritte erforderlich. Die Informationen im Dokument sollten möglichst umfassend sein, sodass Ihr Betriebspersonal das Upgrade anhand der darin enthaltenen Informationen vollständig durchführen und abschließen kann.

### Entwickeln eines Projektplans {#developing-a-project-plan}

Anhand der Ergebnisse aus den vorherigen Schritten kann ein Projektplan erstellt werden, der die erwarteten Zeitrahmen für den Test- oder Entwicklungsaufwand, Schulungen und das tatsächliche Upgrade beinhaltet.

![develop-project-plan](assets/develop-project-plan.png)

Ein umfassender Projektplan sollte folgende Punkte beinhalten:

* Finalisierung der Entwicklungs- und Testpläne
* Aktualisierung von Entwicklungs- und QS-Umgebungen
* Aktualisierung der benutzerdefinierten Code-Basis für AEM 6.5
* Test- und Fehlerbehebungszyklus zur Qualitätssicherung
* Aktualisierung der Staging-Umgebung
* Integrations-, Leistungs- und Lasttests
* Zertifizierung der Umgebung
* Live schalten

### Durchführung von Entwicklung und Qualitätssicherung {#performing-development-and-qa}

Wir haben Verfahren für das [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) bereitgestellt, damit diese mit AEM 6.5 kompatibel sind. Wenn dieser iterative Prozess ausgeführt wird, sollten nach Bedarf Änderungen am Runbook vorgenommen werden. Auch unter [Abwärtskompatibilität in AEM 6.5](/help/sites-deploying/backward-compatibility.md) finden Sie Informationen darüber, wie Sie Ihre Anpassungen in den meisten Fällen abwärtskompatibel halten können, ohne dass sofort nach dem Upgrade Entwicklungsarbeiten erforderlich sind.

![patru_cropped](assets/patru_cropped.png)

Der Entwicklungs- und Testprozess ist in der Regel iterativ. Änderungen, die aufgrund von Anpassungen während des Upgrades vorgenommen werden, können potenziell einen kompletten Teil des Produkts unbrauchbar machen. Wenn die Entwickler die Ursache des Problems behoben und das Test-Team Zugriff auf die Funktionen hat, um diese zu testen, werden möglicherweise weitere Probleme gefunden. Werden Probleme identifiziert, die Anpassungen des Upgrade-Prozesses erfordern, stellen Sie sicher, dass Sie diese zum benutzerdefinierten Runbook für das Upgrade hinzufügen. Nach mehreren Iterationen von Tests und Fehlerbehebung sollte die Code-Basis vollständig validiert und für die Bereitstellung in der Staging-Umgebung bereit sein.

### Abschließende Tests {#final-testing}

Nach der Zertifizierung der Code-Basis durch das Qualitätssicherungs-Team Ihres Unternehmens wird eine abschließende Testrunde empfohlen. Diese Testrunde beinhaltet die Validierung Ihres Runbooks in einer Staging-Umgebung, gefolgt von Benutzerakzeptanz-, Leistungs- und Sicherheitstests.

![cinci_cropped](assets/cinci_cropped.png)

Dieser Schritt ist notwendig, da dies die einzige Gelegenheit ist, bei der Sie die Schritte im Runbook in einer produktionsähnlichen Umgebung überprüfen können. Wenn ein Upgrade für die Umgebung durchgeführt wurde, müssen die Endbenutzenden genügend Zeit haben, um sich anzumelden und ihre üblichen täglichen Aktivitäten im System durchzuführen. Nicht selten verwenden Benutzende einen Teil des Systems, dessen Nutzung zuvor nicht vorgesehen war. Durch die Identifizierung und Behebung von Fehlern in diesen Bereichen vor einer Live-Schaltung können teure Produktionsausfälle verhindert werden. Da eine neue Version von AEM erhebliche Änderungen an der zugrunde liegenden Plattform enthält, ist es auch wichtig, Leistungs-, Last- und Sicherheitstests für das System durchzuführen, als ob Sie es zum ersten Mal starten würden.

### Durchführen des Upgrades {#performing-the-upgrade}

Sobald die endgültige Abnahme von allen Beteiligten eingegangen ist, ist es an der Zeit, die definierten Runbook-Verfahren auszuführen. Adobe hat unter [Upgrade-Verfahren](/help/sites-deploying/upgrade-procedure.md) Schritte für das Upgrade und das Rollback sowie als Referenz die Installationsschritte bei der Durchführung eines [In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md) zur Verfügung gestellt.

![perform-upgrade](assets/perform-upgrade.png)

Adobe hat in den Upgrade-Anweisungen eine Reihe von Schritten für die Validierung der Umgebung bereitgestellt. Hierzu gehören grundlegende Prüfungen wie das Überprüfen der Upgrade-Protokolle und die Verifizierung des ordnungsgemäßen Starts aller OSGi-Bundles. Adobe empfiehlt jedoch auch eine Validierung anhand eigener Nutzungsszenarien für Ihre Geschäftsprozesse. Darüber hinaus empfiehlt Adobe die Überprüfung des Zeitplans für die Online-Revisionsbereinigung von AEM sowie der zugehörigen Routinen, um sicherzustellen, dass diese nicht zu Stoßzeiten durchgeführt werden. Diese Routinen sind für die langfristige Leistungsfähigkeit von AEM von entscheidender Bedeutung.
