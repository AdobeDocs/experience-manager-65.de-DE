---
title: Link-Checker
description: Der Link-Prüfer hilft bei der Validierung sowohl interner als auch externer Links und ermöglicht das Neuschreiben von Links.
exl-id: 8ec4c399-b192-46fd-be77-3f49b83ce711
source-git-commit: 0b9de3261d8747f3e7107962b6aea1dbdf9d6773
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---

# Link-Checker {#the-link-checker}

Inhaltsautoren sollten sich nicht mit der Validierung aller Links befassen müssen, die sie in ihre Inhaltsseiten aufnehmen.

Der Link-Checker wird automatisch ausgeführt, um Inhaltsautoren bei ihren Links zu unterstützen, darunter:

* Validieren von Links beim Hinzufügen zu Inhalten
* Liste aller externen Links im Inhalt anzeigen
* Linktransformationen durchführen

Der Link-Checker verfügt über eine Reihe von [Konfigurationsoptionen](#configuring) wie die Definition der internen Validierung, das Auslassen bestimmter Links oder Link-Muster in der Validierung und das Neuschreiben von Linkumschreibungsregeln.

Der Link Checker überprüft beide [interne Links](#internal) und [externe Links.](#external)

>[!NOTE]
>
>Da der Link-Checker die Links jeder Inhaltsseite überprüft, kann der Link-Checker die Leistung bei großen Repositorys beeinträchtigen. In solchen Fällen müssen Sie möglicherweise [konfigurieren, wie oft der Link Checker ausgeführt wird](#configuring) oder [deaktivieren.](#disabling)

## Prüfung interner Links {#internal}

Interne Links sind Links zu anderen Inhalten in Ihrem AEM-Repository. Interne Links können mit der Pfadauswahl des RTE oder mithilfe einer benutzerdefinierten Komponente hinzugefügt werden. Beispiel:

* Ihre Seite `/content/wknd/us/en/adventures/ski-touring.html`
* Link enthalten zu `/content/wknd/us/en/adventures/extreme-ironing.html` in [Textkomponente.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html?lang=de)

Interne Links werden validiert, sobald der Inhaltsautor interne Links zu einer Seite hinzufügt. Wenn der Link ungültig wird:

* Es wird aus dem Herausgeber entfernt. Der Text des Links bleibt erhalten, der Link selbst wird jedoch entfernt.
* Er wird in der Authoring-Oberfläche als defekter Link angezeigt.

![Interner Link beim Bearbeiten einer Seite beschädigt](assets/link-checker-invalid-link-internal.png)

## Überprüfung externer Links {#external}

Externe Links sind Links zu Inhalten außerhalb Ihres AEM-Repositorys. Externe Links können über den RTE oder eine benutzerdefinierte Komponente hinzugefügt werden. Beispiel:

* Ihre Seite `/content/wknd/us/en/adventures/ski-touring.html`
* Link enthalten zu `https://bunwarmerthermalunderwear.com` in [Textkomponente.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

Externe Links werden auf Syntax und Verfügbarkeit überprüft. Diese Prüfung wird asynchron in einem konfigurierbaren internen Modus durchgeführt. Wenn der Link-Checker einen externen Link ungültig findet:

* Es wird aus dem Herausgeber entfernt. Der Text des Links bleibt erhalten, der Link selbst wird jedoch entfernt.
* Er wird in der Authoring-Oberfläche als defekter Link angezeigt.

![Interner Link beim Bearbeiten einer Seite beschädigt](assets/link-checker-invalid-link-external.png)

Darüber hinaus wird die [Externer Link-Checker](#external-link-checker) -Oberfläche bietet einen Überblick über alle externen Links auf Ihren Inhaltsseiten.

### Verwenden des Checkers für externe Links {#external-link-checker}

So verwenden Sie den Prüfer für externe Links:

1. Wählen Sie über die **** Navigation den Eintrag **Tools** und dann **Sites** aus.
1. Auswählen **Externer Link-Checker** und es wird eine Liste aller externen Links angezeigt.

![Das Fenster &quot;Checker für externe Links&quot;](assets/external-link-checker.png)

Die folgenden Informationen werden angezeigt:

* **Status** - Der Validierungsstatus des Links, der einer der folgenden sein kann:
   * **Gültig** - Der externe Link ist über den Link-Checker erreichbar.
   * **Ausstehend** - Der externe Link wurde zum Site-Inhalt hinzugefügt, wurde jedoch noch nicht vom Link-Checker validiert
   * **Ungültig** - Der externe Link kann vom Link-Checker nicht erreicht werden.
* **URL** - Der externe Link
* **Referrer** - Die Inhaltsseite, die den externen Link enthält
   * Dies wird nur ausgefüllt [falls konfiguriert.](#configuring)
* **Zuletzt aktiviert** - Das letzte Mal, dass der Link Checker den externen Link validiert hat
   * Wie oft Links überprüft werden [ist konfigurierbar.](#configuring)
* **Letzter Status** - Der letzte HTML-Statuscode, der zurückgegeben wurde, als der Link überprüft den externen Link zuletzt überprüft hat
* **Zuletzt verfügbar** - Zeit, seit der Link zuletzt für den Link-Checker verfügbar war
* **Zuletzt aufgerufen** - Zeit seit dem letzten Zugriff auf die Seite mit dem externen Link in der Authoring-Oberfläche

Sie können den Inhalt des Fensters mithilfe der beiden Schaltflächen oben in der Liste der Links bearbeiten:

* **Aktualisieren** - Aktualisieren des Listeninhalts
* **Überprüfen** - So prüfen Sie einen einzelnen externen Link, der in der Liste ausgewählt ist

### Funktionsweise des Checkers für externe Links {#how-it-works}

Der Checker für externe Links ist zwar benutzerfreundlich, stützt sich aber auf eine Reihe von Diensten, die Ihnen helfen, zu verstehen, wie diese funktionieren. [Konfigurieren des Link-Checkers](#configuring) um Ihre Bedürfnisse zu erfüllen.

1. Wenn ein Inhaltsautor einen Link zu einer Seite speichert, wird ein Ereignis-Handler ausgelöst.
1. Der Ereignishandler durchläuft alle Inhalte unter `/content` und sucht nach neuen oder aktualisierten Links und fügt sie einem Cache für den Link-Checker hinzu.
1. Die **Day CQ Link Checker Service** führt dann nach einem regulären Zeitplan aus, um die Einträge im Cache auf gültige Syntax zu überprüfen.
1. Die durch die Syntax validierten Links werden dann im [Externer Link-Checker](#external-link-checker) Fenster. Sie werden jedoch in einer **Ausstehend** state.
1. Die **Day CQ Link Checker Task** führt dann regelmäßig aus, um die Links durch einen GET-Aufruf zu validieren.
1. Die **Day CQ Link Checker Task** aktualisiert dann die Einträge im Fenster Checker für externe Links mit den Ergebnissen der GET-Aufrufe.

## Konfigurieren des Link-Checkers {#configuring}

Der Link-Checker ist in AEM automatisch standardmäßig verfügbar. Es gibt jedoch eine Reihe von OSGi-Konfigurationen, die geändert werden können, um ihr Verhalten zu ändern:

* **Day CQ Link Checker Info Storage Service** - Dieser Dienst definiert die Größe des Link Checker-Cache im Repository.
* **Day CQ Link Checker Service** - Dieser Dienst führt eine asynchrone Überprüfung der Syntax von externen Links durch. Sie können den Prüfzeitraum festlegen und festlegen, welche Links vom Prüfer unter anderem übersprungen werden.
* **Day CQ Link Checker Task** - Dieser Dienst führt die GET von externen Links durch. Es ermöglicht separate Definitionen von Intervallen, um fehlerhafte und gute Verknüpfungen unter anderen Optionen zu überprüfen.
* **Day CQ Link Checker Transformer** - Ermöglicht das Konvertieren von Links basierend auf einem benutzerdefinierten Regelsatz.

Siehe Dokument . [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) Weitere Informationen zum Ändern der OSGi-Einstellungen.

## Deaktivieren des Link-Checkers {#disabling}

Sie können den Link Checker vollständig deaktivieren. Gehen Sie dazu wie folgt vor:

1. Öffnen Sie die OSGi-Konsole.
1. Bearbeiten Sie die **Day CQ Link Checker Transformer**
1. Aktivieren Sie die Option(en), die Sie deaktivieren möchten:
   * **Überprüfung deaktivieren** - zur Deaktivierung der Validierung von Links
   * **Umschreiben deaktivieren** - zur Deaktivierung von Linktransformationen

>[!NOTE]
>
>Wenn Sie die Linküberprüfung deaktivieren, nachdem Sie mit der Erstellung des Inhalts begonnen haben, werden möglicherweise trotzdem Einträge in der [Fenster &quot;Überprüfung externer Links&quot;](#external-link-checker), werden jedoch nicht mehr aktualisiert.
