---
title: Der Link-Checker
description: Der Link-Checker hilft bei der Validierung sowohl interner als auch externer Links und ermöglicht das Neuschreiben von Links.
exl-id: 8ec4c399-b192-46fd-be77-3f49b83ce711
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '969'
ht-degree: 92%

---

# Der Link-Checker {#the-link-checker}

Inhaltsautoren sollten sich nicht mit der Validierung aller Links befassen müssen, die sie in ihre Inhaltsseiten aufnehmen.

Der Link-Checker wird automatisch ausgeführt, um Autorinnen und Autoren von Inhalten bei ihren Links zu unterstützen, darunter:

* Validieren von Links beim Hinzufügen zu Inhalten
* Anzeigen einer Liste aller externen Links im Inhalt
* Durchführen von Linktransformationen

Der Link-Checker verfügt über mehrere [Konfigurationsoptionen](#configuring) wie das Definieren der internen Validierung, das Auslassen bestimmter Links oder Link-Muster in der Validierung und das Neuschreiben von Linkumschreibungsregeln.

Der Link-Checker überprüft sowohl [interne Links](#internal) als auch [externe Links](#external).

>[!NOTE]
>
>Da der Link-Checker die Links jeder Inhaltsseite überprüft, kann der Link-Checker bei großen Repositorys die Leistung beeinträchtigen. In solchen Fällen müssen Sie möglicherweise [konfigurieren, wie oft der Link Checker ausgeführt wird](#configuring) oder [ihn deaktivieren](#disabling).

## Prüfung interner Links {#internal}

Interne Links sind Links zu anderen Inhalten in Ihrem AEM-Repository. Interne Links können mit der Pfadauswahl des RTE oder mithilfe einer benutzerdefinierten Komponente hinzugefügt werden. Beispiel:

* Ihre Seite `/content/wknd/us/en/adventures/ski-touring.html`
* enthält einen Link zu `/content/wknd/us/en/adventures/extreme-ironing.html` in einer [Textkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html?lang=de).

Interne Links werden validiert, sobald der Inhaltsautor interne Links zu einer Seite hinzufügt. Wenn der Link ungültig wird:

* wird er aus der Veröffentlichungebene entfernt. bleibt der Text des Links erhalten, der Link selbst wird jedoch entfernt.
* wird er in der Authoring-Oberfläche als defekter Link angezeigt.

![Beim Bearbeiten einer Seite beschädigter interner Link](assets/link-checker-invalid-link-internal.png)

## Überprüfung externer Links {#external}

Externe Links sind Links zu Inhalten außerhalb Ihres AEM-Repositorys. Externe Links können mit dem RTE oder mithilfe einer benutzerdefinierten Komponente hinzugefügt werden. Beispiel:

* Ihre Seite `/content/wknd/us/en/adventures/ski-touring.html`
* enthält einen Link zu `https://bunwarmerthermalunderwear.com` in einer [Textkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html?lang=de).

Externe Links werden auf Syntax und Verfügbarkeit überprüft. Diese Prüfung wird asynchron in einem konfigurierbaren internen Modus durchgeführt. Wenn der Link-Checker einen externen Link für ungültig befindet:

* wird er aus der Veröffentlichungebene entfernt. bleibt der Text des Links erhalten, der Link selbst wird jedoch entfernt.
* wird er in der Authoring-Oberfläche als defekter Link angezeigt.

![Beim Bearbeiten einer Seite beschädigter interner Link](assets/link-checker-invalid-link-external.png)

Darüber hinaus bietet die [Externer-Link-Checker](#external-link-checker)-Oberfläche einen Überblick über alle externen Links auf Ihren Inhaltsseiten.

### Verwenden des Externer-Link-Checker {#external-link-checker}

So verwenden Sie den Externer-Link-Checker:

1. Wählen Sie über die **Navigation** die Option **Tools** und dann **Sites** aus.
1. Wählen Sie **Externer-Link-Checker**. Eine Liste aller externen Links wird erstellt.

![Das Fenster „Externer-Link-Checker“](assets/external-link-checker.png)

Daraufhin werden die folgenden Informationen angezeigt:

* **Status**: Der Validierungsstatus des Links, der einer der folgenden sein kann:
   * **Gültig**: Der externe Link ist über den Link-Checker erreichbar.
   * **Ausstehend**: Der externe Link wurde zum Website-Inhalt hinzugefügt, wurde jedoch noch nicht vom Link-Checker validiert.
   * **Ungültig**: Der externe Link kann vom Link-Checker nicht erreicht werden.
* **URL**: Der externe Link.
* **Referrer**: Die Inhaltsseite, die den externen Link enthält.
   * Dies wird nur ausgefüllt, [falls konfiguriert](#configuring).
* **Zuletzt aktiviert**: Das letzte Mal, dass der Link-Checker den externen Link validiert hat.
   * Wie oft Links überprüft werden, [ist konfigurierbar](#configuring).
* **Letzter Status**: Der letzte HTML-Status-Code, der zurückgegeben wurde, als der Link-Checker den externen Link zuletzt überprüft hat.
* **Zuletzt verfügbar**: Zeit, seit der Link zuletzt für den Link-Checker verfügbar war.
* **Zuletzt aufgerufen**: Zeit seit dem letzten Zugriff auf die Seite mit dem externen Link in der Authoring-Oberfläche.

Sie können den Inhalt des Fensters mithilfe der beiden Schaltflächen oben in der Liste der Links bearbeiten:

* **Aktualisieren**: Aktualisieren des Listeninhalts
* **Überprüfen**: Zum Prüfen eines einzelnen externen Links, der in der Liste ausgewählt ist.

### Funktionsweise des Externer-Link-Checkers {#how-it-works}

Der Checker für externe Links ist zwar benutzerfreundlich, stützt sich aber auf mehrere Dienste und zeigt Ihnen, wie diese funktionieren. [Konfigurieren des Link-Checkers](#configuring) um Ihre Bedürfnisse zu erfüllen.

1. Wenn ein Inhaltsautor einen Link zu einer Seite speichert, wird ein Ereignis-Handler ausgelöst.
1. Der Ereignis-Handler durchläuft alle Inhalte unter `/content` und sucht nach neuen oder aktualisierten Links und fügt sie einem Cache für den Link-Checker hinzu.
1. Der **Day CQ Link Checker Service** wird dann nach einem regulären Zeitplan ausgeführt, um die Einträge im Cache auf gültige Syntax zu überprüfen.
1. Die durch die Syntax validierten Links werden dann im Fenster [Externer-Link-Checker](#external-link-checker) angezeigt. Sie werden sich jedoch im Status **Ausstehend** befinden.
1. Die **Day CQ Link Checker Task** wird dann regelmäßig ausgeführt, um die Links durch einen GET-Aufruf zu validieren.
1. Die **Day CQ Link Checker Task** aktualisiert dann die Einträge im Fenster „Externer-Link-Checker“ mit den Ergebnissen der GET-Aufrufe.

## Konfigurieren des Link-Checkers {#configuring}

Der Link-Checker ist in AEM automatisch vorkonfiguriert verfügbar. Es gibt jedoch mehrere OSGi-Konfigurationen, die geändert werden können, um ihr Verhalten zu ändern:

* **Day CQ Link Checker Info Storage Service**: Dieser Dienst definiert die Größe des Link-Checker-Cache im Repository.
* **Day CQ Link Checker Service**: Dieser Dienst führt eine asynchrone Überprüfung der Syntax von externen Links durch. Sie können unter anderem den Prüfzeitraum festlegen und festlegen, welche Links vom Checker übersprungen werden.
* **Day CQ Link Checker Task**: Dieser Dienst führt die GET-Validierung von externen Links durch. Er ermöglicht unter anderem separate Definitionen von Intervallen, um fehlerhafte und gute Links zu überprüfen.
* **Day CQ Link Checker Transformer**: Ermöglicht das Konvertieren von Links basierend auf einem benutzerdefinierten Regelsatz.

Weitere Informationen zum Ändern von OSGi-Einstellungen finden Sie im Dokument [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).

## Deaktivieren des Link-Checkers {#disabling}

Sie können den Link-Checker vollständig deaktivieren. Gehen Sie dazu wie folgt vor:

1. Öffnen Sie die OSGi-Konsole.
1. Bearbeiten Sie den **Day CQ Link Checker Transformer**.
1. Markieren Sie die Option(en), die Sie deaktivieren möchten:
   * **Überprüfung deaktivieren**: zur Deaktivierung der Validierung von Links
   * **Umschreiben deaktivieren**: zur Deaktivierung von Linktransformationen

>[!NOTE]
>
>Wenn Sie die Linküberprüfung deaktivieren, nachdem Sie mit der Erstellung von Inhalten begonnen haben, werden möglicherweise trotzdem Einträge im [Fenster „Externer-Link-Checker“](#external-link-checker) angezeigt, sie werden jedoch nicht mehr aktualisiert.
