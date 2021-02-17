---
title: Prüfungen und Fehlerbehebung nach einer Aktualisierung
seo-title: Prüfungen und Fehlerbehebung nach einer Aktualisierung
description: Erfahren Sie, wie Sie Probleme beheben, die nach einer Aktualisierung auftreten können.
seo-description: Erfahren Sie, wie Sie Probleme beheben, die nach einer Aktualisierung auftreten können.
uuid: 3f525f2c-8d25-4bb8-a57e-3adf667edde8
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5a67aa9f-e5eb-4d7e-89da-2ee1a45eb8ce
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 92%

---


# Prüfungen und Fehlerbehebung nach einer Aktualisierung{#post-upgrade-checks-and-troubleshooting}

## Prüfungen nach einer Aktualisierung {#post-upgrade-checks}

Nach einer [ersetzenden Aktualisierung](/help/sites-deploying/in-place-upgrade.md) sollten folgende Schritte durchgeführt werden, um die Aktualisierung abzuschließen. Es wird davon ausgegangen, dass AEM mit der 6.5-JAR-Datei gestartet und die upgegradete Codebasis bereitgestellt wurde.

* [Überprüfen der Protokolle auf eine erfolgreiches Aktualisierung](#main-pars-header-290365562)

* [Überprüfen von OSGi-Bundles](#main-pars-header-1637350649)

* [Überprüfen der Oak-Version](#main-pars-header-1293049773)

* [Überprüfen des Ordners „PreUpgradeBackup“](#main-pars-header-988995987)

* [Erstüberprüfung von Seiten](#main-pars-header-20827371)
* [Anwenden von AEM Service Packs](#main-pars-header-215142387)

* [Migrieren von AEM-Funktionen](#main-pars-header-1434457709)

* [Überprüfen der Konfigurationen für die geplante Wartung](#main-pars-header-1552730183)

* [Aktivieren von Replikationsagenten](#main-pars-header-823243751)

* [Aktivieren von benutzerdefinierten geplanten Aufträgen](#main-pars-header-244535083)

* [Durchführen des Testplans](#main-pars-header-1167972233)

### Überprüfen der Protokolle auf eine erfolgreiche Aktualisierung {#verify-logs-for-upgrade-success}

**upgrade.log**

Bisher mussten diverse Protokolldateien, Teile des Repositorys und das Launchpad sorgfältig überprüft werden, um den Status Ihrer Instanz nach einer Aktualisierung zu bestimmen. Durch das Generieren von Berichten nach einer Aktualisierung können defekte Aktualisierungen erkannt werden, bevor Instanzen zum Einsatz kommen.

Der primäre Zweck dieser Funktion besteht darin, den manuellen Interpretationsaufwand zu reduzieren oder eine komplexe Parsing-Logik für mehrere Endpunkte zu vermeiden, die erforderlich sind, um den Erfolg einer Aktualisierung zu qualifizieren. Ziel der Lösung ist es, eindeutige Informationen für externe Automatisierungssysteme bereitzustellen, damit diese auf den Erfolg oder das festgestellte Fehlschlagen einer Aktualisierung reagieren können.

Sie dient vor allem dazu, Folgendes sicherzustellen:

* Fehlgeschlagene Aktualisierungen, die vom Aktualisierungs-Framework erkannt werden, werden in einem einzigen Aktualisierungsbericht zusammengefasst.
* Der Bericht enthält Indikatoren über notwendige manuelle Eingriffe.

Um diesem Rechnung zu tragen, wurde das Verfahren für die Generierung von Protokollen in der Datei `upgrade.log` geändert.

Dies ist ein Beispielbericht für eine Aktualisierung ohne Fehler:

![1487887443006](assets/1487887443006.png)

Dies ist ein Beispielbericht mit einem Bundle, das beim Aktualisierungsvorgang nicht installiert wurde:

![1487887532730](assets/1487887532730.png)

**error.log**

Die Datei „error.log“ sollte beim Start von AEM und danach anhand der JAR-Datei der Zielversion sorgfältig überprüft werden. Alle Warnungen und Fehler müssen dabei geprüft werden. Im Allgemeinen ist es am besten, am Anfang der Datei nach möglichen Problemen zu suchen. Fehler, die weiter unten im Protokoll aufgeführt werden, sind u. U. Nebeneffekte einer Grundursache, die sich am Dateianfang findet. Wenn wiederholte Fehler und Warnungen auftreten, finden Sie im nachfolgenden Abschnitt [Analysieren von Problemen bei der Aktualisierung](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade) weitere Informationen.

### Überprüfen von OSGi-Bundles {#verify-osgi-bundles}

Navigieren Sie zur OSGi-Konsole `/system/console/bundles` und prüfen Sie, ob keine Pakete gestartet wurden. Wenn sich Pakete in einem installierten Zustand befinden, ermitteln Sie das Stammproblem mit dem `error.log`.

### Überprüfen der Oak-Version {#verify-oak-version}

Nach der Aktualisierung sollte ersichtlich sein, dass die Oak-Version auf Version **1.10.2** aktualisiert wurde. Um die Oak-Version zu überprüfen, navigieren Sie zur OSGi-Konsole und sehen Sie sich die Version an, die den Oak-Bundles zugeordnet ist: Eichenkern, EichenCommons, Eichensegmentter.

### Überprüfen des Ordners „PreUpgradeBackup“{#inspect-preupgradebackup-folder}

Während der Aktualisierung versucht AEM, Anpassungen zu sichern und sie unter `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>` zu speichern. Um diesen Ordner in CRXDE Lite anzuzeigen, müssen Sie [CRXDE Lite vorübergehend aktivieren](/help/sites-administering/enabling-crxde-lite.md).

Der Ordner mit dem Zeitstempel sollte die Eigenschaft `mergeStatus` mit dem Wert `COMPLETED` aufweisen. Der Ordner **to-process** sollte leer sein und der Knoten **overwritten** zeigt an, welche Knoten bei der Aktualisierung überschrieben wurden. Unter dem Knoten **leftovers** angezeigte Inhalte konnten bei der Aktualisierung nicht problemlos zusammengeführt werden. Wenn Ihre Implementierung von einem der untergeordneten Knoten abhängig ist (und nicht bereits von Ihrem aktualisierten Codepaket installiert wurde), muss eine manuelle Zusammenführung durchgeführt werden.

Deaktivieren Sie CRXDE Lite nach dieser Übung, wenn eine Staging- oder Produktionsumgebung verwendet wird.

### Erstüberprüfung von Seiten  {#initial-validation-of-pages}

Führen Sie in AEM eine Erstüberprüfung mithilfe von mehreren Seiten durch. Wenn Sie eine Authoring-Umgebung aktualisieren, öffnen Sie die Beginn- und Begrüßungsseite ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). Öffnen Sie in Autoren- und Veröffentlichungsumgebungen einige Anwendungsseiten und prüfen Sie, ob diese richtig angezeigt werden. Wenn Probleme auftreten, finden Sie in der Datei `error.log` weitere Informationen zur Fehlerbehebung.

### Anwenden von AEM Service Packs {#apply-aem-service-packs}

Wenden Sie alle relevanten AEM 6.5 Service Packs an, die veröffentlicht wurden.

### Migrieren von AEM-Funktionen {#migrate-aem-features}

Für eine Reihe von Funktionen in AEM sind nach einer Aktualisierung zusätzliche Schritte erforderlich. Eine vollständige Liste dieser Funktionen und die erforderlichen Schritte zum Migrieren derselben auf AEM 6.5 finden Sie auf der Seite [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md).

### Überprüfen der Konfigurationen für die geplante Wartung {#verify-scheduled-maintenance-configurations}

#### Aktivieren der Bereinigung des Datenspeichers {#enable-data-store-garbage-collection}

Wenn Sie einen Dateidatenspeicher verwenden, stellen Sie sicher, dass die Aufgabe „Data Store-Abfallsammlung“ aktiviert ist und zur Liste für die wöchentliche Wartung hinzugefügt wurde. Anweisungen hierzu finden Sie unter [hier](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Die Aufgabe wird nicht für benutzerdefinierte S3-Datenspeicherinstallationen empfohlen oder wenn ein freigegebener Datenspeicher verwendet wird.

#### Aktivieren der Online-Revisionsbereinigung  {#enable-online-revision-cleanup}

Wenn Sie MongoMK oder das neue TarMK-Segmentformat verwenden, stellen Sie sicher, dass die Aufgabe „Revisionsbereinigung“ aktiviert ist und zur Liste für die tägliche Wartung hinzugefügt wurde. Anweisungen hierzu finden Sie [hier](/help/sites-deploying/revision-cleanup.md).

### Durchführen des Testplans  {#execute-test-plan}

Führen Sie einen detaillierten Testplan durch, wie unter [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) im Abschnitt **Testverfahren** beschrieben.

### Aktivieren von Replikationsagenten  {#enable-replication-agents}

Wenn eine Veröffentlichungsumgebung vollständig aktualisiert und überprüft wurde, aktivieren Sie die Replikationsagenten in der Autorenumgebung. Vergewissern Sie sich, dass die Agenten eine Verbindung mit den jeweiligen Veröffentlichungsinstanzen herstellen können. Weitere Einzelheiten zur Reihenfolge der Ereignisse finden Sie unter [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md)

### Aktivieren von benutzerdefinierten geplanten Aufträgen {#enable-custom-scheduled-jobs}

Zu diesem Zeitpunkt können alle geplanten Aufträge, die Teil der Codebasis sind, aktiviert werden.

## Analysieren von Aktualisierungsproblemen  {#analyzing-issues-with-upgrade}

In diesem Abschnitt sind einige Problemszenarien enthalten, die möglicherweise im Zuge der Aktualisierung auf AEM 6.3 auftreten.

Diese Szenarien sollen dabei helfen, die Grundursache der mit der Aktualisierung im Zusammenhang stehenden Probleme zu identifizieren. Ferner sollen sie dazu beitragen, projekt- oder produktspezifische Probleme zu ermitteln.

### Fehler bei der Repository-Migration  {#repository-migration-failing-}

Die Datenmigration von CRX2 auf OAK sollte für alle Szenarien mit Quellinstanzen auf Basis von CQ 5.4 durchführbar sein. Stellen Sie sicher, dass Sie die Aktualisierungsanweisungen in diesem Dokument genau befolgen. Dazu gehört auch, dass Sie die Datei `repository.xml` entsprechend vorbereiten und sicherstellen, dass keine benutzerdefinierte Authentifizierung über JAAS gestartet wurde und dass die Instanz vor dem Start der Migration auf Inkonsistenzen überprüft wurde.

Wenn bei der Migration weiterhin Fehler auftreten, können Sie die Grundursache bestimmen, indem Sie die Datei `upgrade.log` überprüfen. Wenn das Problem bislang unbekannt ist, melden Sie es dem Kundensupport.

### Aktualisierung wurde nicht ausgeführt  {#the-upgrade-did-not-run}

Stellen Sie vor Beginn der vorbereitenden Schritte sicher, dass zuerst die **Quellinstanz** ausgeführt wird. Verwenden Sie hierzu den Java-Befehl „-jar aem-quickstart.jar“. Dieser Schritt ist notwendig, um zu gewährleisten, dass die Datei „quickstart.properties“ ordnungsgemäß generiert wird. Fehlt diese Datei, wird die Aktualisierung nicht durchgeführt. Alternativ dazu können Sie im Installationsordner der Quellinstanz unter `crx-quickstart/conf` prüfen, ob die Datei vorhanden ist. Darüber hinaus muss sie beim Starten von AEM für die Aktualisierung mit dem Java-Befehl „-jar aem-quickstart.jar“ ausgeführt werden. Beim Starten mit einem Startskript wird AEM nicht im Aktualisierungsmodus gestartet.

### Fehlerhafte Aktualisierung von Paketen und Bundles   {#packages-and-bundles-fail-to-update-}

Wenn Pakete während der Aktualisierung nicht installiert werden können, werden die darin enthaltenen Bundles ebenfalls nicht aktualisiert. Diese Kategorie von Problemen geht für gewöhnlich auf eine Fehlkonfiguration des Datenspeichers zurück. Sie werden auch als **ERROR**- und **WARN**-Meldungen in der Datei error.log angezeigt. Da in den meisten dieser Fälle die Standardanmeldung möglicherweise nicht funktioniert, können Sie CRXDE direkt verwenden, um die Konfigurationsprobleme zu untersuchen und zu finden.

### Einige AEM-Bundles wechseln nicht in den aktiven Status  {#some-aem-bundles-are-not-switching-to-the-active-state}

Im Falle nicht startender Bundles sollten Sie diese auf nicht erfüllte Abhängigkeiten überprüfen.

Wenn dieses Problem auftritt, jedoch auf eine fehlerhafte Paketinstallation zurückzuführen ist, wodurch Bundles nicht aktualisiert werden, werden diese für die neue Version als inkompatibel angesehen. Weitere Informationen über die entsprechende Fehlerbehebung finden Sie oben unter **Fehlerhafte Aktualisierung von Paketen und Bundles**.

Es wird zudem empfohlen, die Bundle-Liste einer aktuellen AEM 6.5-Instanz mit der aktualisierten zu vergleichen, um nicht aktualisierte Bundles zu ermitteln. Dadurch kann der Bereich der zu suchenden Elemente in der Datei `error.log` eingegrenzt werden.

### Benutzerdefinierte Bundles wechseln nicht in den aktiven Status {#custom-bundles-not-switching-to-the-active-state}

Wenn Ihre benutzerdefinierten Bundles nicht in den aktiven Status wechseln, liegt dies höchstwahrscheinlich an Code, der die geänderte API nicht importiert. Dies führt oftmals zu nicht erfüllten Abhängigkeiten.

Eine gelöschte API sollte in einer der vorherigen Versionen als veraltet markiert werden. In diesem Hinweis zur veralteten Version finden Sie u. U. Anweisungen über eine direkte Migration Ihres Codes. Adobe ist bestrebt, nach Möglichkeit eine semantische Versionierung zu verwenden, sodass die Versionen Änderungen anzeigen können, die Probleme verursachen.

Es empfiehlt sich zudem, zu überprüfen, ob die Änderung, die das Problem verursacht hat, unbedingt nötig war, und sie zurückzusetzen, wenn dies nicht der Fall ist. Überprüfen Sie zudem, ob die Version des Paketexports unter Beachtung einer strengen semantischen Versionierung mehr als nötig erhöht wurde.

### Fehlerhafte Plattform-Benutzeroberfläche  {#malfunctioning-platform-ui}

Im Falle bestimmter Benutzeroberflächenfunktionen, die nach der Aktualisierung nicht richtig funktionieren, sollten Sie zunächst eine Überprüfung auf benutzerdefinierte Überlagerungen der Oberfläche vornehmen. Möglicherweise haben sich einige Strukturen geändert und die Überlagerung muss u. U. aktualisiert werden oder ist veraltet.

Führen Sie anschließend eine Überprüfung auf JavaScript-Fehler durch, die möglicherweise auf benutzerdefinierte, hinzugefügte Erweiterungen zurückzuführen sind, welche mit Client-Bibliotheken verknüpft sind. Dies kann auch auf ein benutzerdefiniertes CSS zutreffen, das möglicherweise Probleme am AEM-Layout verursacht.

Führen Sie abschließend eine Überprüfung auf fehlerhafte Konfigurationen durch, die von JavaScript möglicherweise nicht verarbeitet werden können. Dies ist für gewöhnlich bei unsachgemäß deaktivierten Erweiterungen der Fall.

### Fehlerhafte benutzerdefinierte Komponenten, Vorlagen oder Benutzeroberflächenerweiterungen  {#malfunctioning-custom-components-templates-or-ui-extensions}

In den meisten Fällen sind die Grundursachen für diese Probleme dieselben wie für nicht gestartete Bundles oder nicht installierte Pakete. Der einzige Unterschied besteht darin, dass die Probleme bei der ersten Verwendung der Komponenten auftreten.

Bei fehlerhaftem benutzerdefiniertem Code sollten Sie zunächst Feuerproben durchführen, um die Ursache zu identifizieren. Sobald Sie sie gefunden haben, sehen Sie sich die Empfehlungen in diesem Abschnitt [link] des Artikels an, um diese zu beheben.

### Fehlende Anpassungen unter „/etc“{#missing-customizations-under-etc}

`/apps` und  `/libs` werden durch die Aktualisierung gut behandelt, aber Änderungen unter  `/etc` Umständen müssen manuell von  `/var/upgrade/PreUpgradeBackup` nach der Aktualisierung wiederhergestellt werden. Überprüfen Sie diesen Speicherort auf Inhalte, die manuell zusammengeführt werden müssen.

### Analysieren der Dateien „error.log“ und „upgrade.log“  {#analyzing-the-error.log-and-upgrade.log}

In den meisten Situationen müssen die Protokolle auf Fehler untersucht werden, um die Ursache eines Problems zu ermitteln. Im Falle von Aktualisierungen ist es jedoch ebenfalls erforderlich, Abhängigkeitsfehler zu überwachen, da alte Bundles möglicherweise nicht ordnungsgemäß aktualisiert werden.

Dafür sollten Sie alle Meldungen aus der Datei „error.log“ entfernen, die erwartungsgemäß nicht mit Ihrem Problem in Zusammenhang stehen. Dies ist mit einem Tool wie grep möglich, indem Sie Folgendes verwenden:

```shell
grep -v UnrelatedErrorString
```

Einige Fehlermeldungen sind möglicherweise nicht sofort selbsterklärend. In diesem Fall kann die Anzeige des Kontexts, in dem sie auftreten, verdeutlichen, wo der Fehler verursacht wurde. Sie können den Fehler mithilfe der folgenden Befehle trennen:

* `grep -B` zum Hinzufügen von Zeilen vor dem Fehler;

oder

* `grep -A` zum Hinzufügen von Zeilen nach.

In einigen Fällen können Fehler auch in WARN-Meldungen gefunden werden, da gültige Fälle vorliegen können, die zu diesem Status führen. Die Anwendung kann darüber hinaus nicht immer entscheiden, ob ein tatsächlicher Fehler vorliegt. Sie sollten diese Meldungen ebenfalls lesen.

### Kontaktaufnahme mit dem Adobe-Support  {#contacting-adobe-support}

Wenn Sie die Empfehlungen auf dieser Seite befolgt haben und weiterhin Fehler auftreten, wenden Sie sich an den Adobe-Support. Um dem Supportmitarbeiter für Ihren Fall so viele Informationen wie möglich bereitzustellen, fügen Sie Ihrer Supportanfrage die Datei „upgrade.log“ für die Aktualisierung hinzu.
