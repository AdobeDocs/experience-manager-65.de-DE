---
title: Planung von Upgrades
description: Dieser Artikel hilft bei der Planung des AEM-Upgrades, klare Ziele, Phasen und Lieferziele festzulegen.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: 0dea2b3e-fd7c-4811-a04a-6852ffc1e6d6
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2423'
ht-degree: 43%

---

# Planung von Upgrades{#planning-your-upgrade}

## AEM Project Overview {#aem-project-overview}

AEM kommt häufig in umfangreichen Bereitstellungen zum Einsatz, die möglicherweise von Millionen von Benutzern genutzt werden. Normalerweise werden auf den Instanzen benutzerdefinierte Programme bereitgestellt, was die Komplexität erhöht. Das Upgrade einer solchen Bereitstellung muss deshalb methodisch angegangen werden.

Dieses Handbuch hilft bei der Festlegung klarer Ziele, Phasen und Lieferziele bei der Planung Ihrer Aktualisierung. Im Mittelpunkt des Leitfadens stehen die Abwicklung und die Richtlinien des gesamten Projekts. Er gibt einen Überblick über die konkreten Upgrade-Schritte und verweist auf verfügbare technische Ressourcen, falls erforderlich. Es sollte mit den verfügbaren technischen Ressourcen verwendet werden, auf die in dem Dokument verwiesen wird.

Der AEM-Upgrade-Prozess muss sorgfältig mit Planungs-, Analyse- und Ausführungsphasen durchgeführt werden, wobei für jede Phase die wichtigsten Ergebnisse definiert sind.

Es ist möglich, direkt von AEM Version 6.0 und bis zu 6.5 zu aktualisieren. Kunden, die 5.6.x und älter ausführen, müssen zunächst ein Upgrade auf Version 6.0 oder höher durchführen, wobei 6.0 (SP3) empfohlen wird. Außerdem wird jetzt das neue Oak Segment Tar-Format für den Segment-Knotenspeicher seit 6.3 verwendet, und die Repository-Migration auf dieses neue Format ist auch für 6.0, 6.1 und 6.2 obligatorisch.

>[!CAUTION]
>
>Wenn Sie von AEM 6.2 auf 6.3 upgraden, sollten Sie ENTWEDER von den Versionen **6.2-SP1-CFP1 - 6.2-SP1-CFP12.1** oder ab der Version **6.2-SP1-CFP15** upgraden. Wenn Sie jedoch von **6.2-SP1-CFP13/6.2-SP1CFP14** auf AEM 6.3 upgraden, müssen Sie mindestens auf Version **6.3.2.2** upgraden. Andernfalls würde AEM Sites nach der Aktualisierung fehlschlagen.

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
   <td>Ungewisse, aber feine Effekte</td>
   <td>Möglicherweise muss beim Upgrade von AEM auch das Betriebssystem aktualisiert werden. Dies kann gewisse Auswirkungen haben.</td>
  </tr>
  <tr>
   <td>Java™ Runtime</td>
   <td>Moderate Auswirkung</td>
   <td>Für AEM 6.3 ist JRE 1.7.x (64 Bit) oder höher erforderlich. JRE 1.8 ist die einzige Version, die derzeit von Oracle unterstützt wird.</td>
  </tr>
  <tr>
   <td>Hardware</td>
   <td>Moderate Auswirkung</td>
   <td>Für die Online-Revisionsbereinigung sind freier<br /> Speicherplatz, der 25 % des Repository-Volumens entspricht, sowie 15 % freier Heap-Speicher erforderlich,<br /> um die Bereinigung erfolgreich abzuschließen. Möglicherweise müssen Sie Ihre Hardware auf<br /> Sicherstellung ausreichender Ressourcen für die Online-Revisionsbereinigung<br /> ausführen. Wenn ein Upgrade von einer Version vor AEM 6 durchgeführt wird, gibt es außerdem<br /> kann zusätzliche Speicheranforderungen umfassen.</td>
  </tr>
  <tr>
   <td>Content Repository (CRX oder Oak)</td>
   <td>Hohe Auswirkung</td>
   <td>Ab Version 6.1 bietet AEM keine Unterstützung für CRX2, sodass eine Migration auf<br /> Oak (CRX3) erforderlich ist, wenn eine Aktualisierung von einer älteren Version durchgeführt wird. In AEM 6.3 wurde<br /> ein neuer Segment-Knotenspeicher implementiert, der ebenfalls migriert werden muss. Die<br /> Zu diesem Zweck wird das crx2oak-Tool verwendet.</td>
  </tr>
  <tr>
   <td>AEM Komponenten/Inhalte</td>
   <td>Moderate Auswirkung</td>
   <td><code>/libs</code> und <code>/apps</code> sind während des Upgrades leicht zu handhaben, <code>/etc</code> erfordert normalerweise eine manuelle Neuanwendung der Anpassungen.</td>
  </tr>
  <tr>
   <td>AEM</td>
   <td>Geringe Auswirkung</td>
   <td>Der Großteil der AEM-Core Services wird für ein Upgrade getestet. Dies ist ein Bereich mit geringer Auswirkung.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Anwendungsdienste</td>
   <td>Geringe bis große Auswirkung</td>
   <td>Je nach Anwendung und Anpassung kann es<br /> Abhängigkeiten von JVM, Betriebssystemversionen und einigen Indizierungszusammenhängen<br /> geändert, da Indizes in Oak nicht automatisch generiert werden.</td>
  </tr>
  <tr>
   <td>Benutzerdefinierte Anwendungsinhalte</td>
   <td>Geringe bis große Auswirkung</td>
   <td>Inhalte, die vom Upgrade nicht betroffen sind, können vorher gesichert<br /> und dann wieder in das Repository verschoben werden.<br /> Die meisten Inhalte können mithilfe des Migrationstools verarbeitet werden.</td>
  </tr>
 </tbody>
</table>

Es muss sichergestellt werden, dass Sie ein unterstütztes Betriebssystem, eine unterstützte Java™-Laufzeitumgebung, HTTPD und Dispatcher-Version ausführen. Weitere Informationen finden Sie auf der Seite [Technische Anforderungen für AEM 6.5](/help/sites-deploying/technical-requirements.md). Die Aktualisierung dieser Komponenten muss in Ihrem Projektplan berücksichtigt werden und sollte vor der Aktualisierung von AEM erfolgen.

## Projektphasen {#project-phases}

Viel Arbeit geht in die Planung und Durchführung eines AEM-Upgrades. Um die verschiedenen Bemühungen zu verdeutlichen, die in diesem Prozess unternommen werden, hat die Adobe die Planungs- und Ausführungsübungen in separate Phasen unterteilt. In den folgenden Abschnitten führt jede Phase zu einem Lieferziel, das häufig von einer künftigen Projektphase verwendet wird.

### Planen der Autorenschulung {#planning-for-author-training}

In jeder neuen Version ist mit potenziellen Änderungen an der Benutzeroberfläche und den Benutzer-Workflows zu rechnen. Darüber hinaus werden durch neue Versionen neue Funktionen eingeführt, die für das Unternehmen von Vorteil sein können. Adobe empfiehlt, die eingeführten Funktionsänderungen zu überprüfen und einen Plan zu organisieren, um Ihre Benutzer auf ihre effektive Nutzung zu trainieren.

![unu_cropped](assets/unu_cropped.png)

Neue Funktionen in AEM 6.5 finden Sie im [Bereich zu AEM auf adobe.com](/help/release-notes/release-notes.md). Achten Sie vor allem auf Änderungen an Benutzeroberflächen oder Produktfunktionen, die in Ihrem Unternehmen häufig verwendet werden. Wenn Sie sich über die neuen Funktionen informieren, achten Sie auch auf neue Funktionen, die für Ihr Unternehmen von Nutzen sein können. Sobald Sie sich mit den Änderungen in AEM 6.5 vertraut gemacht haben, entwickeln Sie einen Schulungsplan für Ihre Autoren. Dazu kann die Verwendung frei verfügbarer Ressourcen wie Videos zu Hilfefunktionen oder formelles Training über [Adobe Digital Learning Services](https://learning.adobe.com/).

### Erstellen eines Testplans {#creating-a-test-plan}

Jede Kundenimplementierung von AEM ist einzigartig und auf die Geschäftsanforderungen des Unternehmens zugeschnitten. Daher ist es wichtig, alle am System vorgenommenen Anpassungen zu bestimmen, damit sie in einen Testplan aufgenommen werden können. Dieser Testplan ermöglicht die Qualitätssicherung, die Adobe auf der aktualisierten Instanz durchführt.

![test-plan](assets/test-plan.png)

Die Produktionsumgebung muss exakt dupliziert und nach dem Upgrade getestet werden, um sicherzustellen, dass alle Anwendungen und benutzerdefinierter Code weiterhin wie gewünscht ausgeführt werden. Nehmen Sie alle Anpassungen vor und führen Sie Leistungs-, Last- und Sicherheitstests durch. Stellen Sie bei der Organisation Ihres Testplans sicher, dass Sie alle Anpassungen, die am System vorgenommen wurden, sowie die vordefinierten Benutzeroberflächen und Workflows abdecken, die in Ihren täglichen Vorgängen verwendet werden. Dazu gehören benutzerdefinierte OSGi-Dienste und Servlets, Integrationen in Adobe Experience Cloud, Integrationen mit Drittanbietern über AEM Connectoren, benutzerdefinierte Drittanbieterintegrationen, benutzerdefinierte Komponenten und Vorlagen, benutzerdefinierte UI-Überlagerungen in AEM und benutzerdefinierte Workflows. Kunden, die eine Migration von einer Version vor AEM 6 durchführen, sollten alle benutzerdefinierten Abfragen analysieren, da diese u. U. indiziert werden müssen. Kunden, die bereits eine AEM 6.x-Version verwenden, sollten diese Abfragen dennoch testen, um sicherzustellen, dass ihre Indizes nach der Aktualisierung weiterhin effektiv funktionieren.

### Ermittlung der erforderlichen Architektur- und Infrastrukturänderungen {#determining-architectural-and-infrastructure-changes-needed}

Sie müssen bei einem Upgrade möglicherweise auch andere Komponenten Ihres Technologie-Stacks upgraden, z. B. das Betriebssystem oder JVM. Außerdem ist es möglich, dass aufgrund von Änderungen im Repository-Aufbau zusätzliche Hardware erforderlich ist. Dies gilt nur für Kunden, die von Instanzen vor 6.x migrieren, ist jedoch zu beachten. Schließlich können Änderungen an Ihren betrieblichen Verfahren erforderlich sein, einschließlich Überwachungs-, Wartungs-, Sicherungs- und Notfallwiederherstellungsprozessen.

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

Mit AEM werden Änderungen an der Repository-Struktur eingeführt, mit denen Upgrades noch nahtloser durchgeführt werden können. Diese Änderungen erfordern, dass Inhalte aus dem Ordner /etc in Ordner wie /libs, /apps und /content verschoben werden – je nachdem, ob Adobe oder der Kunde Eigentümer des Inhalts ist – um die Wahrscheinlichkeit zu verringern, dass Inhalte durch Aktualisierungen überschrieben werden. Die Repository-Neustrukturierung wurde so durchgeführt, dass zum Zeitpunkt der Aktualisierung auf 6.5 keine Codeänderungen erforderlich sind. Es wird jedoch empfohlen, die Details unter [Repository-Neustrukturierung in AEM](/help/sites-deploying/repository-restructuring.md) bei der Planung eines Upgrades.

### Bewertung der Komplexität des Upgrades {#assessing-upgrade-complexity}

Aufgrund der großen Vielfalt an Anpassungen, die Adobe-Kunden für ihre AEM-Umgebungen anwenden, ist es wichtig, einige Zeit vor dem Upgrade zu verbringen, um den Gesamtaufwand zu ermitteln, der bei Ihrem Upgrade erwartet werden sollte.

Es gibt zwei Ansätze, mit denen Sie die Komplexität des Upgrades bewerten können. Eine Vorphase kann den neu eingeführten Musterdetektor verwenden, der für Ihre AEM 6.1, 6.2 und 6.3-Instanzen verfügbar ist. Der Musterdetektor bietet die einfachste Möglichkeit, die erwartete Gesamtkomplexität des Upgrades anhand der gefundenen Muster zu bewerten. Der Musterdetektorbericht enthält Muster zum Identifizieren nicht verfügbarer APIs, die von der benutzerdefinierten Codebase verwendet werden (dies wurde mithilfe von Kompatibilitätsprüfungen vor der Aktualisierung in 6.3 durchgeführt).

Nach dieser anfänglichen Bewertung kann in einem umfangreicheren nächsten Schritt ein Upgrade einer Testinstanz durchgeführt werden, um einige grundlegende Tests durchzuführen. Adobe bietet auch einige . Die Liste der [Eingestellte und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md) sollten nicht nur auf die Version überprüft werden, auf die Sie aktualisieren, sondern auch auf alle Versionen zwischen Ihren Quell- und Zielversionen. Bei einer Aktualisierung von AEM 6.2 auf 6.5 ist es beispielsweise wichtig, die veralteten und entfernten Funktionen von AEM 6.3 neben denen von AEM 6.5 zu überprüfen.

![trei_cropped](assets/trei_cropped.png)

Der kürzlich eingeführte Musterdetektor liefert Ihnen eine recht genaue Schätzung dessen, was Sie während eines Upgrades in den meisten Fällen erwarten können. Für komplexere Anpassungen und Bereitstellungen, in denen inkompatible Änderungen vorhanden sind, können Sie jedoch eine Entwicklungsinstanz auf AEM 6.5 upgraden. Eine Anleitung finden Sie unter [Durchführen eines In-Place-Upgrades](/help/sites-deploying/in-place-upgrade.md). Führen Sie nach der Aktualisierung eine Reihe Feuerproben der hohen Stufe für die Umgebung durch. Sie dienen nicht dazu, das Nutzungsszenario umfassend zu testen und eine formelle Liste mit Defekten zu erstellen. Vielmehr soll der geschätzte erforderliche Arbeitsaufwand für das Upgrade des Codes ermittelt werden, um die Kompatibilität mit Version 6.5 sicherzustellen. Wenn die [Mustererkennung](/help/sites-deploying/pattern-detector.md) mit den Änderungen an der Architektur kombiniert wird, die im vorherigen Abschnitt beschrieben wurden, liefert dies eine grobe Schätzung, mit deren Hilfe das Projektleiter-Team das Upgrade planen kann.

### Erstellen des Runbooks für das Upgrade und das Rollback {#building-the-upgrade-and-rollback-runbook}

Während Adobe den Prozess zum Aktualisieren einer AEM-Instanz dokumentiert hat, erfordern das Netzwerklayout, die Bereitstellungsarchitektur und die Anpassungen jedes Kunden eine Feinabstimmung und Anpassung dieses Ansatzes. Aus diesem Grund empfiehlt Ihnen Adobe, die gesamte bereitgestellte Dokumentation zu lesen und sie zu verwenden, um ein projektspezifisches Runbook zu informieren, in dem die spezifischen Upgrade- und Rollback-Verfahren beschrieben werden, die Sie in Ihrer Umgebung anwenden werden. Stellen Sie bei einer Aktualisierung von CRX2 sicher, dass Sie die Dauer der Inhaltsmigration von CRX2 auf Oak evaluieren. Für große Repositorys könnte dies erheblich sein.

![runbook-diagram](assets/runbook-diagram.png)

Adobe hat Upgrade- und Rollback-Verfahren in [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md) und schrittweise Anleitungen zum Anwenden des Upgrades unter Ausführen eines [Ersetzende Aktualisierung](/help/sites-deploying/in-place-upgrade.md). Diese Anweisungen sollten überprüft und mit Ihrer Systemarchitektur, Ihren Anpassungen und Ihrer Ausfallzeittoleranz in Betracht gezogen werden, um die geeigneten Umstellungs- und Rollback-Verfahren zu bestimmen, die Sie während des Upgrades ausführen werden. Änderungen an der Architektur oder Servergröße sollten bei der Erstellung Ihres benutzerdefinierten Runbooks miteinbezogen werden. Beachten Sie, dass diese Version als erster Entwurf gelten sollte. Möglicherweise sind nach Abschluss der QS- und Entwicklungszyklen und der Bereitstellung des Upgrades in der Staging-Umgebung weitere Schritte erforderlich. Die Informationen im Dokument sollten möglichst umfassend sein, sodass Ihr Betriebspersonal das Upgrade anhand der darin enthaltenen Informationen vollständig durchführen und abschließen kann.

### Entwickeln eines Projektplans {#developing-a-project-plan}

Die Ergebnisse früherer Übungen können verwendet werden, um einen Projektplan zu erstellen, der die erwarteten Zeitpläne für Ihre Test- oder Entwicklungsbemühungen, Schulungen und die tatsächliche Durchführung der Aktualisierung abdeckt.

![develop-project-plan](assets/develop-project-plan.png)

Ein umfassender Projektplan sollte folgende Punkte beinhalten:

* Finalisierung der Entwicklungs- und Testpläne
* Aktualisierung von Entwicklungs- und QS-Umgebungen
* Aktualisierung der benutzerdefinierten Code-Basis für AEM 6.5
* Test- und Fehlerbehebungszyklus zur Qualitätssicherung
* Aktualisierung der Staging-Umgebung
* Integration, Leistung und Belastungstests
* Zertifizierung der Umgebung
* Live schalten

### Entwicklung und Qualitätssicherung durchführen {#performing-development-and-qa}

Adobe hat Verfahren für die [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) mit AEM 6.5 kompatibel sein. Da dieser iterative Prozess ausgeführt wird, sollten bei Bedarf Änderungen am Runbook vorgenommen werden. Siehe auch [Abwärtskompatibilität in AEM 6.5](/help/sites-deploying/backward-compatibility.md) Informationen dazu, wie Ihre Anpassungen in der Regel abwärtskompatibel bleiben können, ohne dass sofort nach der Aktualisierung eine Entwicklung erforderlich ist.

![patru_cropped](assets/patru_cropped.png)

Der Entwicklungs- und Testprozess ist in der Regel iterativ. Änderungen, die aufgrund von Anpassungen während des Upgrades vorgenommen werden, können potenziell einen kompletten Teil des Produkts unbrauchbar machen. Wenn die Entwickler die Ursache des Problems behoben und das Test-Team Zugriff auf die Funktionen hat, um diese zu testen, werden möglicherweise weitere Probleme gefunden. Werden Probleme identifiziert, die Anpassungen des Upgrade-Prozesses erfordern, stellen Sie sicher, dass Sie diese zum benutzerdefinierten Runbook für das Upgrade hinzufügen. Nach mehreren Iterationen von Tests und Fehlerbehebung sollte die Codebasis vollständig validiert und für die Bereitstellung in der Staging-Umgebung bereit sein.

### Abschließende Tests {#final-testing}

Adobe empfiehlt eine letzte Testrunde, nachdem die Codebase vom QA-Team Ihres Unternehmens zertifiziert wurde. Diese Testrunde beinhaltet die Validierung Ihres Runbooks in einer Staging-Umgebung, gefolgt von Benutzerakzeptanz-, Leistungs- und Sicherheitstests.

![cinci_cropped](assets/cinci_cropped.png)

Dieser Schritt ist notwendig, da dies die einzige Gelegenheit ist, bei der Sie die Schritte im Runbook in einer produktionsähnlichen Umgebung überprüfen können. Nach der Aktualisierung der Umgebung ist es wichtig, Endbenutzern Zeit zu geben, sich anzumelden und die Aktivitäten zu durchlaufen, die sie bei der Verwendung des Systems in ihren täglichen Aktivitäten durchführen. Es ist nicht ungewöhnlich, dass Benutzer einen Teil des Systems verwenden, der zuvor nicht berücksichtigt wurde. Durch die Identifizierung und Behebung von Fehlern in diesen Bereichen vor einer Live-Schaltung können teure Produktionsausfälle verhindert werden. Da eine neue Version von AEM erhebliche Änderungen an der zugrunde liegenden Plattform enthält, ist es auch wichtig, Leistungs-, Last- und Sicherheitstests für das System durchzuführen, als ob Sie es zum ersten Mal starten würden.

### Durchführen des Upgrades {#performing-the-upgrade}

Sobald die endgültige Abnahme von allen Beteiligten eingegangen ist, ist es an der Zeit, die definierten Runbook-Verfahren auszuführen. Adobe hat Schritte für die Aktualisierung und das Rollback in [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md) und Installationsschritte unter Ausführen einer [Ersetzende Aktualisierung](/help/sites-deploying/in-place-upgrade.md) als Referenzpunkt.

![perform-upgrade](assets/perform-upgrade.png)

Adobe hat einige Schritte in den Upgrade-Anweisungen zur Umgebungsvalidierung bereitgestellt. Dazu gehören grundlegende Prüfungen wie das Überprüfen der Upgrade-Protokolle und das Überprüfen, ob alle OSGi-Bundles ordnungsgemäß gestartet wurden. Adobe empfiehlt jedoch, anhand Ihrer Geschäftsprozesse auch eigene Testfälle zu validieren. Adobe empfiehlt außerdem, den Zeitplan für die AEM Online-Revisionsbereinigung und die damit verbundenen Routinen zu überprüfen, um sicherzustellen, dass sie in einer stillen Zeit für Ihr Unternehmen stattfinden. Diese Routinen sind für die langfristige AEM von entscheidender Bedeutung.
