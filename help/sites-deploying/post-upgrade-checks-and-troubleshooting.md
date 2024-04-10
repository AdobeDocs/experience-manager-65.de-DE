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
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '1793'
ht-degree: 41%

---

# Prüfungen und Fehlerbehebung nach einem Upgrade{#post-upgrade-checks-and-troubleshooting}

## Prüfungen nach einem Upgrade {#post-upgrade-checks}

Nach einem [ersetzenden Upgrade](/help/sites-deploying/in-place-upgrade.md) sollten folgende Schritte durchgeführt werden, um das Upgrade abzuschließen. Es wird davon ausgegangen, dass AEM mit 6.5 JAR gestartet und die aktualisierte Code-Basis bereitgestellt wurde.

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

Der primäre Zweck dieser Funktion besteht darin, den manuellen Interpretationsaufwand zu reduzieren oder eine komplexe Parsing-Logik für mehrere Endpunkte zu vermeiden, die erforderlich sind, um den Erfolg eines Upgrades zu qualifizieren. Die Lösung zielt darauf ab, für externe Automatisierungssysteme eindeutige Informationen bereitzustellen, um auf den Erfolg oder das identifizierte Fehlschlagen einer Aktualisierung reagieren zu können.

Insbesondere wird sichergestellt, dass:

* Fehlgeschlagene Upgrades, die vom Upgrade-Framework erkannt werden, werden in einem einzigen Upgrade-Bericht zusammengefasst.
* Der Upgrade-Bericht enthält Indikatoren über notwendige manuelle Eingriffe.

Um diesem Rechnung zu tragen, wurde das Verfahren für die Generierung von Protokollen in der `upgrade.log` -Datei.

Im Folgenden finden Sie einen Beispielbericht, der während des Upgrades keine Fehler anzeigt:

![1487887443006](assets/1487887443006.png)

Dies ist ein Beispielbericht mit einem Paket, das beim Upgrade-Vorgang nicht installiert wurde:

![1487887532730](assets/1487887532730.png)

**error.log**

Die Datei error.log sollte beim und nach dem Start von AEM mit der JAR-Datei der Zielversion sorgfältig überprüft werden. Alle Warnungen und Fehler müssen dabei geprüft werden. Im Allgemeinen ist es am besten, am Anfang des Protokolls nach Problemen zu suchen. Fehler, die weiter unten im Protokoll aufgeführt werden, sind u. U. Nebeneffekte einer Grundursache, die sich am Dateianfang findet. Wenn wiederholte Fehler und Warnungen auftreten, finden Sie im nachfolgenden Abschnitt [Analysieren von Problemen beim Upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade) weitere Informationen.

### Überprüfen von OSGi-Paketen {#verify-osgi-bundles}

Navigieren Sie zur OSGi-Konsole unter `/system/console/bundles` und überprüfen Sie, ob irgendwelche Pakete nicht gestartet wurden. Wenn Pakete den Status „Installiert“ aufweisen, konsultieren Sie die Datei `error.log` um das Grundurteil zu ermitteln.

### Überprüfen der Oak-Version {#verify-oak-version}

Nach dem Upgrade sollte ersichtlich sein, dass die Oak-Version auf aktualisiert wurde. **1,10,2**. Um die Oak-Version zu überprüfen, navigieren Sie zur OSGi-Konsole und sehen Sie sich die mit den Oak-Bundles verknüpfte Version an: Oak Core, Oak Commons, Oak Segment Tar.

### Überprüfen des Ordners „PreUpgradeBackup“ {#inspect-preupgradebackup-folder}

Während des Upgrades versucht AEM, die Anpassungen zu sichern und sie unter zu speichern `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`. Um diesen Ordner auf CRXDE Lite anzuzeigen, müssen Sie möglicherweise [CRXDE Lite vorübergehend aktivieren](/help/sites-administering/enabling-crxde-lite.md).

Der Ordner mit dem Zeitstempel sollte die Eigenschaft `mergeStatus` mit dem Wert `COMPLETED` aufweisen. Der Ordner **to-process** sollte leer sein und der Knoten **overwritten** zeigt an, welche Knoten beim Upgrade überschrieben wurden. Unter dem Knoten leftovers angezeigte Inhalte konnten beim Upgrade nicht problemlos zusammengeführt werden. Wenn Ihre Implementierung von einem der untergeordneten Knoten abhängig ist (und noch nicht von Ihrem aktualisierten Code-Paket installiert wurde), müssen diese manuell zusammengeführt werden.

Deaktivieren Sie das CRXDE Lite nach dieser Übung, wenn Sie sich in einer Staging- oder Produktionsumgebung befinden.

### Erstüberprüfung von Seiten {#initial-validation-of-pages}

Führen Sie in AEM eine Erstüberprüfung mithilfe von mehreren Seiten durch. Wenn eine Autorenumgebung ein Upgrade erhält, öffnen Sie die Startseite und die Begrüßungsseite (`/aem/start.html`, `/libs/cq/core/content/welcome.html`). Öffnen Sie sowohl in der Autoren- als auch in der Veröffentlichungsumgebung einige Anwendungsseiten und testen Sie, ob sie korrekt gerendert werden. Wenn Probleme auftreten, finden Sie in der Datei `error.log` weitere Informationen zur Fehlerbehebung.

### Anwenden von AEM Service Packs {#apply-aem-service-packs}

Wenden Sie alle relevanten AEM 6.5 Service Packs an, wenn sie veröffentlicht wurden.

### AEM-Funktionen migrieren {#migrate-aem-features}

Für eine Reihe von Funktionen in AEM sind nach einem Upgrade zusätzliche Schritte erforderlich. Eine vollständige Liste dieser Funktionen und Schritte zur Migration in AEM 6.5 finden Sie im [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) Seite.

### Überprüfen der Konfigurationen für die geplante Wartung {#verify-scheduled-maintenance-configurations}

#### Aktivieren der automatischen Datenspeicherbereinigung {#enable-data-store-garbage-collection}

Wenn Sie einen Dateidatenspeicher verwenden, stellen Sie sicher, dass die Aufgabe Automatische Datenspeicherbereinigung aktiviert ist und zur Liste für die wöchentliche Wartung hinzugefügt wurde. Anweisungen hierzu finden Sie [hier](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Dies wird für benutzerdefinierte S3-Datenspeicherinstallationen oder bei Verwendung eines freigegebenen Datenspeichers nicht empfohlen.

#### Aktivieren der Online-Revisionsbereinigung {#enable-online-revision-cleanup}

Wenn Sie MongoMK oder das neue TarMK-Segmentformat verwenden, stellen Sie sicher, dass die Aufgabe Revisionsbereinigung aktiviert ist und zur Liste Tägliche Wartung hinzugefügt wurde. Anleitungen [hier](/help/sites-deploying/revision-cleanup.md).

### Testplan ausführen {#execute-test-plan}

Ausführen eines detaillierten Testplans für wie definiert [Aktualisieren von Code und Anpassungen](/help/sites-deploying/upgrading-code-and-customizations.md) unter dem **Testverfahren** -Abschnitt.

### Aktivieren von Replikationsagenten {#enable-replication-agents}

Wenn eine Veröffentlichungsumgebung vollständig upgegradet und überprüft wurde, aktivieren Sie die Replikationsagenten in der Autorenumgebung. Vergewissern Sie sich, dass die Agenten eine Verbindung mit den jeweiligen Veröffentlichungsinstanzen herstellen können. Weitere Einzelheiten zur Reihenfolge der Ereignisse finden Sie unter [Aktualisierungsverfahren](/help/sites-deploying/upgrade-procedure.md)

### Aktivieren von benutzerdefinierten geplanten Aufträgen {#enable-custom-scheduled-jobs}

Alle geplanten Aufträge als Teil der Code-Basis können zu diesem Zeitpunkt aktiviert werden.

## Analysieren von Upgrade-Problemen {#analyzing-issues-with-upgrade}

In diesem Abschnitt sind einige Problemszenarien enthalten, die möglicherweise im Zuge des Upgrades auf AEM 6.3 auftreten.

Diese Szenarien sollten dabei helfen, die Grundursache der Probleme im Zusammenhang mit dem Upgrade zu ermitteln und projekt- oder produktspezifische Probleme zu identifizieren.

### Repository-Migration fehlgeschlagen  {#repository-migration-failing-}

Die Datenmigration von CRX2 auf Oak sollte für jedes Szenario möglich sein, das mit Quellinstanzen auf der Grundlage von CQ 5.4 beginnt. Stellen Sie sicher, dass Sie die Upgrade-Anweisungen in diesem Dokument genau befolgen, einschließlich der Vorbereitung der `repository.xml`Stellen Sie jedoch sicher, dass keine benutzerdefinierte Authentifizierung über JAAS gestartet wurde und die Instanz vor dem Start der Migration auf Inkonsistenzen überprüft wurde.

Wenn die Migration weiterhin fehlschlägt, können Sie die Grundursache bestimmen, indem Sie die Datei `upgrade.log`. Wenn das Problem noch nicht bekannt ist, melden Sie es dem Support.

### Upgrade wurde nicht ausgeführt {#the-upgrade-did-not-run}

Bevor Sie mit den Vorbereitungsschritten beginnen, stellen Sie sicher, dass Sie das **Quelle** Führen Sie zuerst die Instanz aus, indem Sie sie mit dem Java™-jar-Befehl aem-quickstart.jar ausführen. Dies ist erforderlich, um sicherzustellen, dass die Datei quickstart.properties ordnungsgemäß generiert wird. Fehlt diese Datei, wird das Upgrade nicht durchgeführt. Alternativ dazu können Sie im Installationsordner der Quellinstanz unter `crx-quickstart/conf` prüfen, ob die Datei vorhanden ist. Außerdem muss AEM zum Starten des Upgrades mit dem Java™-Befehl „-jar aem-quickstart.jar“ ausgeführt werden. Beim Starten mit einem Startskript wird AEM nicht im Upgrade-Modus gestartet.

### Fehlerhafte Aktualisierung von Paketen  {#packages-and-bundles-fail-to-update-}

Wenn Pakete während des Upgrades nicht installiert werden können, werden die darin enthaltenen Pakete ebenfalls nicht aktualisiert. Diese Problemkategorie ist auf eine fehlerhafte Konfiguration des Datenspeichers zurückzuführen. Sie werden auch angezeigt als **FEHLER** und **WARNEN** Meldungen im Fehlerprotokoll. Da in den meisten Fällen die Standardanmeldung möglicherweise nicht funktioniert, können Sie CRXDE direkt verwenden, um die Konfigurationsprobleme zu überprüfen und zu finden.

### Einige AEM-Pakete wechseln nicht in den aktiven Status {#some-aem-bundles-are-not-switching-to-the-active-state}

Wenn Bundles nicht gestartet werden, überprüfen Sie diese auf nicht erfüllte Abhängigkeiten.

Wenn dieses Problem auftritt, jedoch auf eine fehlerhafte Paketinstallation zurückzuführen ist, wodurch Pakete nicht aktualisiert werden, werden diese für die neue Version als inkompatibel angesehen. Weitere Informationen über die entsprechende Fehlerbehebung finden Sie oben unter **Fehlerhafte Aktualisierung von Pakete**.

Es wird außerdem empfohlen, die Bundle-Liste einer neuen AEM 6.5-Instanz mit der upgegradeten zu vergleichen, um nicht upgegradete Bundles zu erkennen. Dadurch kann der Bereich der zu suchenden Elemente in der Datei `error.log` eingegrenzt werden.

### Benutzerdefinierte Pakete wechseln nicht in den aktiven Status {#custom-bundles-not-switching-to-the-active-state}

Falls Ihre benutzerdefinierten Bundles nicht in den aktiven Status wechseln, liegt dies höchstwahrscheinlich an Code, der die Änderungen-API nicht importiert. Dies führt meist zu unzureichenden Abhängigkeiten.

Eine gelöschte API sollte in einer der vorherigen Versionen als veraltet markiert werden. In diesem Hinweis zur veralteten Version finden Sie u. U. Anweisungen über eine direkte Migration Ihres Codes. Adobe zielt nach Möglichkeit auf die semantische Versionierung ab, sodass die Versionen auf grundlegende Änderungen hinweisen können.

Es empfiehlt sich außerdem zu überprüfen, ob die Änderung, die das Problem verursacht hat, erforderlich war, und sie zurückzusetzen, wenn dies nicht der Fall ist. Überprüfen Sie außerdem, ob die Versionssteigerung des Paketexports nach strenger semantischer Versionierung mehr als nötig erhöht wurde.

### Fehlerhafte Platform-Benutzeroberfläche {#malfunctioning-platform-ui}

Wenn es bestimmte Benutzeroberflächenfunktionen gibt, die nach dem Upgrade nicht richtig funktionieren, sollten Sie zunächst nach benutzerdefinierten Überlagerungen der Benutzeroberfläche suchen. Einige Strukturen haben sich möglicherweise geändert und die Überlagerung benötigt möglicherweise eine Aktualisierung oder ist veraltet.

Überprüfen Sie anschließend, ob JavaScript-Fehler vorliegen, die auf benutzerdefinierte hinzugefügte Erweiterungen zurückzuführen sind, die mit Client-Bibliotheken verknüpft sind. Dasselbe kann für benutzerdefiniertes CSS gelten, das möglicherweise Probleme für das AEM-Layout verursacht.

Überprüfen Sie abschließend, ob eine Fehlkonfiguration vorliegt, die von JavaScript möglicherweise nicht verarbeitet werden kann. Dies ist normalerweise der Fall bei falsch deaktivierten Erweiterungen.

### Fehlerhafte benutzerdefinierte Komponenten, Vorlagen oder UI-Erweiterungen {#malfunctioning-custom-components-templates-or-ui-extensions}

Normalerweise sind die Grundursachen für diese Probleme dieselben wie für nicht gestartete oder nicht installierte Pakete. Der einzige Unterschied besteht darin, dass die Probleme bei der ersten Verwendung der Komponenten auftreten.

Um mit fehlerhaftem benutzerdefiniertem Code umgehen zu können, führen Sie zunächst Feuerproben durch, um die Ursache zu identifizieren. Anschließend sollten Sie in diesem Abschnitt [Link] des Artikels nach Empfehlungen suchen, wie das Problem behoben werden kann.

### Fehlende Anpassungen unter „/etc“ {#missing-customizations-under-etc}

`/apps` und `/libs` werden bei einem Upgrade problemlos verarbeitet. Änderungen unter `/etc` müssen jedoch möglicherweise nach dem Upgrade manuell aus `/var/upgrade/PreUpgradeBackup` wiederhergestellt werden. Überprüfen Sie diesen Speicherort auf Inhalte, die manuell zusammengeführt werden müssen.

### Analysieren von error.log und upgrade.log {#analyzing-the-error.log-and-upgrade.log}

In den meisten Fällen müssen die Protokolle auf Fehler überprüft werden, um die Ursache eines Problems zu finden. Bei Upgrades ist es jedoch auch erforderlich, Abhängigkeitsprobleme zu überwachen, da alte Bundles möglicherweise nicht ordnungsgemäß aktualisiert werden.

Dafür sollten Sie alle Meldungen aus der Datei „error.log“ entfernen, die erwartungsgemäß nicht mit Ihrem Problem in Zusammenhang stehen. Dies ist mit Tools wie grep möglich, indem Sie Folgendes verwenden:

```shell
grep -v UnrelatedErrorString
```

Einige Fehlermeldungen sind möglicherweise nicht sofort selbsterklärend. In diesem Fall kann die Anzeige des Kontexts, in dem sie auftreten, verdeutlichen, wo der Fehler verursacht wurde. Sie können den Fehler wie folgt trennen:

* `grep -B` für das Hinzufügen von Zeilen vor dem Fehler

oder

* `grep -A` für das Hinzufügen von Zeilen nach dem Fehler.

In einigen Fällen können Fehler auch in WARN-Meldungen gefunden werden, da gültige Fälle vorliegen können, die zu diesem Status führen. Die Anwendung kann darüber hinaus nicht immer entscheiden, ob ein tatsächlicher Fehler vorliegt. Stellen Sie sicher, dass Sie auch diese Nachrichten konsultieren.

### Kontaktaufnahme mit dem Adobe-Support {#contacting-adobe-support}

Wenn Sie die Empfehlungen auf dieser Seite befolgt haben und weiterhin Probleme auftreten, wenden Sie sich an den Adobe-Support. Um dem Supportmitarbeiter für Ihren Fall so viele Informationen wie möglich bereitzustellen, fügen Sie in Ihrem Upgrade unbedingt die Datei upgrade.log ein.
