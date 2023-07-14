---
title: Prüfungen und Fehlerbehebung nach einem Upgrade
description: Erfahren Sie, wie Sie Probleme beheben, die nach einem Upgrade auftreten können.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
exl-id: ceac2b52-6885-496d-9517-5fc7291ad070
source-git-commit: 69346a710708ee659ee97e9fdc193c8ea2658fe6
workflow-type: tm+mt
source-wordcount: '1785'
ht-degree: 42%

---

# Prüfungen und Fehlerbehebung nach einem Upgrade{#post-upgrade-checks-and-troubleshooting}

## Prüfungen nach einem Upgrade {#post-upgrade-checks}

Nach einem [ersetzenden Upgrade](/help/sites-deploying/in-place-upgrade.md) sollten folgende Schritte durchgeführt werden, um das Upgrade abzuschließen. Es wird davon ausgegangen, dass AEM mit der 6.5-JAR-Datei gestartet wurde und die aktualisierte Codebasis bereitgestellt wurde.

* [Überprüfen der Protokolle auf ein erfolgreiches Upgrade](#main-pars-header-290365562)

* [Überprüfen von OSGi-Paketen](#main-pars-header-1637350649)

* [Überprüfen der Oak-Version](#main-pars-header-1293049773)

* [Überprüfen des Ordners „PreUpgradeBackup“](#main-pars-header-988995987)

* [Erstüberprüfung von Seiten](#main-pars-header-20827371)
* [Anwenden von AEM Service Packs](#main-pars-header-215142387)

* [Migrieren von AEM-Funktionen](#main-pars-header-1434457709)

* [Überprüfen der Konfigurationen für die geplante Wartung](#main-pars-header-1552730183)

* [Aktivieren von Replikationsagenten](#main-pars-header-823243751)

* [Aktivieren von benutzerdefinierten geplanten Aufträgen](#main-pars-header-244535083)

* [Testplan ausführen](#main-pars-header-1167972233)

### Überprüfen der Protokolle auf ein erfolgreiches Upgrade {#verify-logs-for-upgrade-success}

**upgrade.log**

Bisher mussten diverse Protokolldateien, Teile des Repositorys und das Launchpad sorgfältig überprüft werden, um den Status Ihrer Instanz nach einem Upgrade zu bestimmen. Durch das Generieren von Berichten nach einer Aktualisierung können defekte Upgrades erkannt werden, bevor Instanzen zum Einsatz kommen.

Der primäre Zweck dieser Funktion besteht darin, den manuellen Interpretationsaufwand zu reduzieren oder eine komplexe Parsing-Logik für mehrere Endpunkte zu vermeiden, die erforderlich sind, um den Erfolg eines Upgrades zu qualifizieren. Die Lösung zielt darauf ab, für externe Automatisierungssysteme eindeutige Informationen bereitzustellen, damit diese auf den Erfolg oder das festgestellte Fehlschlagen einer Aktualisierung reagieren können.

Insbesondere wird Folgendes sichergestellt:

* Aktualisierungsfehler, die vom Upgrade-Framework erkannt werden, werden in einem einzigen Aktualisierungsbericht zusammengefasst.
* Der Upgrade-Bericht enthält Indikatoren über notwendige manuelle Eingriffe.

Um dies zu berücksichtigen, wurden Änderungen an der Art und Weise vorgenommen, wie Protokolle in der `upgrade.log` -Datei.

Im Folgenden finden Sie einen Beispielbericht, der während der Aktualisierung keine Fehler anzeigt:

![1487887443006](assets/1487887443006.png)

Dies ist ein Beispielbericht mit einem Paket, das beim Upgrade-Vorgang nicht installiert wurde:

![1487887532730](assets/1487887532730.png)

**error.log**

Die Datei error.log sollte während und nach dem Start der AEM mit der Zielversion jar sorgfältig geprüft werden. Alle Warnungen und Fehler müssen dabei geprüft werden. Im Allgemeinen ist es am besten, am Anfang des Protokolls nach Problemen zu suchen. Fehler, die weiter unten im Protokoll aufgeführt werden, sind u. U. Nebeneffekte einer Grundursache, die sich am Dateianfang findet. Wenn wiederholte Fehler und Warnungen auftreten, finden Sie im nachfolgenden Abschnitt [Analysieren von Problemen beim Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade) weitere Informationen.

### Überprüfen von OSGi-Paketen {#verify-osgi-bundles}

Navigieren Sie zur OSGi-Konsole unter `/system/console/bundles` und überprüfen Sie, ob irgendwelche Pakete nicht gestartet wurden. Wenn sich Pakete in einem installierten Zustand befinden, lesen Sie den Abschnitt `error.log` , um das Problem zu ermitteln.

### Überprüfen der Oak-Version {#verify-oak-version}

Nach dem Upgrade sollten Sie sehen, dass die Oak-Version auf **1,10,2**. Um die Oak-Version zu überprüfen, navigieren Sie zur OSGi-Konsole und sehen Sie sich die Version an, die Oak-Bundles zugeordnet ist: Oak-Kern, Oak-Commons, Oak-Segment-Tar.

### Überprüfen des Ordners „PreUpgradeBackup“ {#inspect-preupgradebackup-folder}

Während des Upgrades versucht AEM, Anpassungen zu sichern und unter `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`. Um diesen Ordner in CRXDE Lite anzuzeigen, müssen Sie möglicherweise [vorübergehend CRXDE Lite aktivieren](/help/sites-administering/enabling-crxde-lite.md).

Der Ordner mit dem Zeitstempel sollte die Eigenschaft `mergeStatus` mit dem Wert `COMPLETED` aufweisen. Der Ordner **to-process** sollte leer sein und der Knoten **overwritten** zeigt an, welche Knoten beim Upgrade überschrieben wurden. Der Inhalt unter dem Knoten links zeigt Inhalte an, die während der Aktualisierung nicht sicher zusammengeführt werden konnten. Wenn Ihre Implementierung von einem der untergeordneten Knoten abhängig ist (und noch nicht von Ihrem aktualisierten Code-Paket installiert wurde), müssen diese manuell zusammengeführt werden.

Deaktivieren Sie die CRXDE Lite nach dieser Übung, wenn Sie sich in einer Staging- oder Produktionsumgebung befinden.

### Erstüberprüfung von Seiten {#initial-validation-of-pages}

Führen Sie in AEM eine Erstüberprüfung mithilfe von mehreren Seiten durch. Wenn eine Autorenumgebung ein Upgrade erhält, öffnen Sie die Startseite und die Begrüßungsseite (`/aem/start.html`, `/libs/cq/core/content/welcome.html`). Öffnen Sie in der Autoren- und Veröffentlichungsumgebung einige Anwendungsseiten und testen Sie, ob sie korrekt dargestellt werden. Wenn Probleme auftreten, finden Sie in der Datei `error.log` weitere Informationen zur Fehlerbehebung.

### Anwenden von AEM Service Packs {#apply-aem-service-packs}

Wenden Sie alle relevanten AEM 6.5 Service Packs an, falls diese veröffentlicht wurden.

### Migrieren AEM Funktionen {#migrate-aem-features}

Für eine Reihe von Funktionen in AEM sind nach einem Upgrade zusätzliche Schritte erforderlich. Eine vollständige Liste dieser Funktionen und Schritte zur Migration in AEM 6.5 finden Sie im [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) Seite.

### Überprüfen der Konfigurationen für die geplante Wartung {#verify-scheduled-maintenance-configurations}

#### Datenspeicherbereinigung aktivieren {#enable-data-store-garbage-collection}

Stellen Sie bei Verwendung eines Dateidatenspeichers sicher, dass die Aufgabe &quot;Datenspeicherbereinigung&quot;aktiviert ist und der Liste &quot;Wöchentliche Wartung&quot;hinzugefügt wird. Anweisungen hierzu finden Sie [hier](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Dies wird für benutzerdefinierte S3-Datenspeicherinstallationen oder bei Verwendung eines freigegebenen Datenspeichers nicht empfohlen.

#### Aktivieren der Online-Revisionsbereinigung {#enable-online-revision-cleanup}

Wenn Sie MongoMK oder das neue TarMK-Segmentformat verwenden, stellen Sie sicher, dass die Aufgabe &quot;Revisionsbereinigung&quot;aktiviert und zur Liste &quot;Tägliche Wartung&quot;hinzugefügt ist. Anleitungen [here](/help/sites-deploying/revision-cleanup.md).

### Testplan ausführen {#execute-test-plan}

Ausführlichen Testplan gemäß Definition ausführen [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) unter **Testverfahren** Abschnitt.

### Aktivieren von Replikationsagenten {#enable-replication-agents}

Wenn eine Veröffentlichungsumgebung vollständig upgegradet und überprüft wurde, aktivieren Sie die Replikationsagenten in der Autorenumgebung. Vergewissern Sie sich, dass die Agenten eine Verbindung mit den jeweiligen Veröffentlichungsinstanzen herstellen können. Weitere Einzelheiten zur Reihenfolge der Ereignisse finden Sie unter [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md)

### Aktivieren von benutzerdefinierten geplanten Aufträgen {#enable-custom-scheduled-jobs}

Alle geplanten Aufträge, die Teil der Codebasis sind, können zu diesem Zeitpunkt aktiviert werden.

## Analysieren von Upgrade-Problemen {#analyzing-issues-with-upgrade}

In diesem Abschnitt sind einige Problemszenarien enthalten, die möglicherweise im Zuge des Upgrades auf AEM 6.3 auftreten.

Diese Szenarien sollten dazu beitragen, die Grundursache von Aktualisierungsproblemen zu ermitteln, und dabei helfen, Projekt- oder produktspezifische Probleme zu identifizieren.

### Repository-Migration fehlgeschlagen  {#repository-migration-failing-}

Die Datenmigration von CRX2 zu Oak sollte für alle Szenarien möglich sein, die mit Quellinstanzen auf Grundlage von CQ 5.4 beginnen. Achten Sie darauf, dass Sie genau die Aktualisierungsanweisungen in diesem Dokument befolgen, die die Vorbereitung der `repository.xml`, stellen Sie sicher, dass kein benutzerdefinierter Authentifizierer über JAAS gestartet wurde und die Instanz vor dem Starten der Migration auf Inkonsistenzen überprüft wurde.

Wenn die Migration weiterhin fehlschlägt, können Sie die Grundursache ermitteln, indem Sie die `upgrade.log`. Wenn das Problem noch nicht bekannt ist, melden Sie es dem Support.

### Upgrade wurde nicht ausgeführt {#the-upgrade-did-not-run}

Bevor Sie mit den vorbereitenden Schritten beginnen, müssen Sie die **source** -Instanz zuerst mit dem Java™ -jar-Befehl aem-quickstart.jar ausführen. Dies ist erforderlich, um sicherzustellen, dass die Datei &quot;quickstart.properties&quot;ordnungsgemäß generiert wird. Fehlt diese Datei, wird das Upgrade nicht durchgeführt. Alternativ dazu können Sie im Installationsordner der Quellinstanz unter `crx-quickstart/conf` prüfen, ob die Datei vorhanden ist. Wenn Sie mit dem Starten des Upgrades AEM, muss dieses mit dem Java™ -jar aem-quickstart.jar -Befehl ausgeführt werden. Beim Starten mit einem Startskript wird AEM nicht im Upgrade-Modus gestartet.

### Fehlerhafte Aktualisierung von Paketen  {#packages-and-bundles-fail-to-update-}

Wenn Pakete während des Upgrades nicht installiert werden können, werden die darin enthaltenen Pakete ebenfalls nicht aktualisiert. Diese Kategorie von Problemen wird durch eine Fehlkonfiguration des Datenspeichers verursacht. Sie werden auch als **FEHLER** und **WARN** Meldungen in der Datei error.log. Da in den meisten dieser Fälle die Standardanmeldung möglicherweise nicht funktioniert, können Sie CRXDE direkt verwenden, um die Konfigurationsprobleme zu untersuchen und zu finden.

### Einige AEM-Pakete wechseln nicht in den aktiven Status {#some-aem-bundles-are-not-switching-to-the-active-state}

Wenn Bundles nicht gestartet werden, überprüfen Sie, ob nicht zufrieden gestellte Abhängigkeiten vorliegen.

Wenn dieses Problem auftritt, jedoch auf eine fehlerhafte Paketinstallation zurückzuführen ist, wodurch Pakete nicht aktualisiert werden, werden diese für die neue Version als inkompatibel angesehen. Weitere Informationen über die entsprechende Fehlerbehebung finden Sie oben unter **Fehlerhafte Aktualisierung von Pakete**.

Es wird außerdem empfohlen, die Bundle-Liste einer neuen AEM 6.5-Instanz mit der aktualisierten zu vergleichen, um die Bundles zu erkennen, die nicht aktualisiert wurden. Dadurch kann der Bereich der zu suchenden Elemente in der Datei `error.log` eingegrenzt werden.

### Benutzerdefinierte Pakete wechseln nicht in den aktiven Status {#custom-bundles-not-switching-to-the-active-state}

Wenn Ihre benutzerdefinierten Bundles nicht zum aktiven Status wechseln, gibt es höchstwahrscheinlich Code, der die API für Änderungen nicht importiert. Dies führt meist zu nicht zufrieden stellenden Abhängigkeiten.

Eine gelöschte API sollte in einer der vorherigen Versionen als veraltet markiert werden. In diesem Hinweis zur veralteten Version finden Sie u. U. Anweisungen über eine direkte Migration Ihres Codes. Die Adobe zielt nach Möglichkeit auf die semantische Versionierung ab, sodass die Versionen auf brechende Änderungen hinweisen können.

Es ist auch am besten zu überprüfen, ob die Änderung, die das Problem verursacht hat, notwendig war, und sie zurückzusetzen, wenn dies nicht der Fall ist. Überprüfen Sie außerdem, ob die Versionssteigerung des Package-Exports nach strikter semantischer Versionierung mehr als nötig erhöht wurde.

### Fehlerhafte Benutzeroberfläche der Plattform {#malfunctioning-platform-ui}

Wenn bestimmte Funktionen der Benutzeroberfläche nach dem Upgrade nicht ordnungsgemäß funktionieren, sollten Sie zunächst nach benutzerdefinierten Überlagerungen der Benutzeroberfläche suchen. Einige Strukturen haben sich möglicherweise geändert und die Überlagerung muss möglicherweise aktualisiert werden oder ist veraltet.

Überprüfen Sie anschließend, ob JavaScript-Fehler vorliegen, die auf benutzerdefinierte hinzugefügte Erweiterungen, die mit Client-Bibliotheken verknüpft sind, nachverfolgt werden können. Dasselbe kann für benutzerdefiniertes CSS gelten, das möglicherweise Probleme beim AEM-Layout verursacht.

Überprüfen Sie abschließend, ob JavaScript möglicherweise nicht in der Lage ist, mit Fehlkonfigurationen umzugehen. Dies ist normalerweise bei falsch deaktivierten Erweiterungen der Fall.

### Fehlerhafte benutzerdefinierte Komponenten, Vorlagen oder Benutzeroberflächen-Erweiterungen {#malfunctioning-custom-components-templates-or-ui-extensions}

Normalerweise sind die Grundursachen für diese Probleme dieselben wie für Pakete, die nicht gestartet werden oder nicht installiert werden, mit dem einzigen Unterschied, dass die Probleme beim erstmaligen Verwenden der Komponenten auftreten.

Um mit fehlerhaftem benutzerdefiniertem Code umzugehen, führen Sie zuerst Rauch-Tests durch, um die Ursache zu identifizieren. Anschließend sollten Sie in diesem Abschnitt [Link] des Artikels nach Empfehlungen suchen, wie das Problem behoben werden kann.

### Fehlende Anpassungen unter „/etc“ {#missing-customizations-under-etc}

`/apps` und `/libs` werden bei einem Upgrade problemlos verarbeitet. Änderungen unter `/etc` müssen jedoch möglicherweise nach dem Upgrade manuell aus `/var/upgrade/PreUpgradeBackup` wiederhergestellt werden. Überprüfen Sie diesen Speicherort auf Inhalte, die manuell zusammengeführt werden müssen.

### Analysieren der Dateien „error.log“ und „upgrade.log“   {#analyzing-the-error.log-and-upgrade.log}

In den meisten Fällen müssen die Protokolle bei Fehlern konsultiert werden, um die Ursache eines Problems zu finden. Bei Upgrades ist es jedoch auch erforderlich, Abhängigkeitsprobleme zu überwachen, da alte Bundles möglicherweise nicht ordnungsgemäß aktualisiert werden.

Dafür sollten Sie alle Meldungen aus der Datei „error.log“ entfernen, die erwartungsgemäß nicht mit Ihrem Problem in Zusammenhang stehen. Dies ist mit einem Tool wie grep möglich, indem Sie Folgendes verwenden:

```shell
grep -v UnrelatedErrorString
```

Einige Fehlermeldungen sind möglicherweise nicht sofort selbsterklärend. In diesem Fall kann die Anzeige des Kontexts, in dem sie auftreten, verdeutlichen, wo der Fehler verursacht wurde. Sie können den Fehler wie folgt trennen:

* `grep -B` für das Hinzufügen von Zeilen vor dem Fehler

oder

* `grep -A` für das Hinzufügen von Zeilen nach dem Fehler.

In einigen Fällen können Fehler auch in WARN-Meldungen gefunden werden, da gültige Fälle vorliegen können, die zu diesem Status führen. Die Anwendung kann darüber hinaus nicht immer entscheiden, ob ein tatsächlicher Fehler vorliegt. Stellen Sie sicher, dass Sie auch diese Nachrichten konsultieren.

### Kontaktaufnahme mit dem Adobe-Support {#contacting-adobe-support}

Wenn Sie die Ratschläge auf dieser Seite befolgt haben und weiterhin Probleme auftreten, wenden Sie sich an den Support von Adobe. Stellen Sie sicher, dass Sie die Datei upgrade.log aus Ihrem Upgrade einbeziehen, damit Sie dem Support-Mitarbeiter, der an Ihrem Fall arbeitet, möglichst viele Informationen zur Verfügung stellen können.
