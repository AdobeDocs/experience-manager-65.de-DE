---
title: Link-Checker
description: Die Link-Prüfung hilft bei der Validierung sowohl interner als auch externer Links und ermöglicht das Umschreiben von Links.
translation-type: tm+mt
source-git-commit: 861cd74e1b2fd3d210647d83dee5d9a6fcead22a
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 1%

---


# Link-Checker {#the-link-checker}

Inhaltsersteller sollten sich nicht mit der Validierung jedes Links beschäftigen müssen, den sie in ihre Inhaltsseiten aufnehmen.

Die Link-Prüfung wird automatisch ausgeführt, um Autoren von Inhalten mit folgenden Links zu unterstützen:

* Validieren von Links beim Hinzufügen zu Inhalten
* Anzeigen einer Liste aller externen Links im Inhalt
* Ausführen von Linktransformationen

Die Link-Checker verfügt über eine Reihe von [Konfigurationsoptionen](#configuring), wie z. B. das Definieren der internen Validierung, das Auslassen bestimmter Links oder Link-Muster bei der Validierung und das Umschreiben von Linkregeln.

Die Link-Prüfung validiert sowohl [interne als auch [externe Links.](#external)](#internal)

>[!NOTE]
>
>Da der Link-Prüfer die Links jeder Inhaltsseite überprüft, kann die Link-Prüfer die Leistung bei großen Repositorys beeinflussen. In solchen Fällen müssen Sie unter Umständen [konfigurieren, wie oft die Link-Checker ](#configuring) oder [deaktiviert wird.](#disabling)

## Interne Linküberprüfung {#internal}

Interne Links sind Links zu anderen Inhalten in Ihrem AEM Repository. Interne Links können über die Pfadauswahl der RTE oder über eine benutzerdefinierte Komponente hinzugefügt werden. Beispiel:

* Ihre Seite `/content/wknd/us/en/adventures/ski-touring.html`
* Enthält einen Link zu `/content/wknd/us/en/adventures/extreme-ironing.html` in einer [Textkomponente.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

Interne Links werden validiert, sobald der Autor einer Seite einen internen Link hinzufügt. Wenn der Link ungültig wird:

* Es wird aus dem Herausgeber entfernt. Der Text des Links bleibt erhalten, aber der Link selbst wird entfernt.
* Es wird als beschädigter Link in der Authoring-Oberfläche angezeigt.

![Interner Link beim Authoring einer Seite beschädigt](assets/link-checker-invalid-link-internal.png)

## Überprüfung des externen Links {#external}

Externe Links sind Links zu Inhalten außerhalb des AEM Repository. Externe Links können mit der RTE oder einer benutzerdefinierten Komponente hinzugefügt werden. Beispiel:

* Ihre Seite `/content/wknd/us/en/adventures/ski-touring.html`
* Enthält einen Link zu `https://bunwarmerthermalunderwear.com` in einer [Textkomponente.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html)

Externe Links werden auf ihre Syntax überprüft und auf ihre Verfügbarkeit hin überprüft. Diese Prüfung wird asynchron in einem konfigurierbaren internen Verfahren durchgeführt. Wenn der Link-Prüfer einen externen Link ungültig findet:

* Es wird aus dem Herausgeber entfernt. Der Text des Links bleibt erhalten, aber der Link selbst wird entfernt.
* Es wird als beschädigter Link in der Authoring-Oberfläche angezeigt.

![Interner Link beim Authoring einer Seite beschädigt](assets/link-checker-invalid-link-external.png)

Darüber hinaus bietet die Oberfläche [Checker für externe Links](#external-link-checker) einen Überblick über alle externen Links auf Ihren Inhaltsseiten.

### Verwenden des externen Link-Checkers {#external-link-checker}

So verwenden Sie die externe Link-Checker:

1. Wählen Sie über die **** Navigation den Eintrag **Tools** und dann **Sites** aus.
1. Wählen Sie **Externe Link-Checker** und eine Liste aller externen Links wird angezeigt.

![](assets/external-link-checker.png)

Die folgenden Informationen werden angezeigt:

* **Status**  - Der Überprüfungsstatus des Links
   * **Gültig** : Der externe Link ist über die Link-Checker erreichbar.
   * **Ausstehend**  - Der externe Link wurde dem Site-Inhalt hinzugefügt, wurde jedoch noch nicht von der Link Checker validiert.
   * **Ungültig**  - Der externe Link kann nicht über die Link-Checker erreicht werden.
* **URL**  - Der externe Link
* **Werber**  - Die Inhaltsseite mit dem externen Link
   * Dies wird nur ausgefüllt, wenn konfiguriert.](#configuring)[
* **Zuletzt überprüft**  - Das letzte Mal, wenn der Link-Prüfer den externen Link validiert hat
   * Wie oft Links überprüft werden, ist konfigurierbar.[](#configuring)
* **Letzter Status** : Der letzte HTML-Statuscode, der zurückgegeben wurde, wenn der externe Link zum letzten Mal vom Typ Link geprüft wurde
* **Zuletzt verfügbar**  - Zeit, seit der Link zuletzt für die Link-Checker verfügbar war
* **Letzter Zugriff**  - Zeit, seit der Link zuletzt von der Link-Checker aufgerufen wurde

Sie können den Inhalt des Fensters mithilfe der beiden Schaltflächen oben in der Liste der Links bearbeiten:

* **Aktualisieren**  - So aktualisieren Sie den Inhalt der Liste
* **Prüfung**  - So prüfen Sie einen in der Liste ausgewählten externen Link

### Funktionsweise des externen Linkprüfers {#how-it-works}

Der externe Link-Checker ist zwar einfach zu verwenden, aber er basiert auf einer Reihe von Diensten. Anhand dieser Informationen können Sie erkennen, wie [Sie den Link-Checker](#configuring) für Ihre Anforderungen konfigurieren können.

1. Wenn ein Inhaltsautor einen Link zu einer Seite speichert, wird ein Ereignis-Handler ausgelöst.
1. Der Ereignis-Handler durchläuft alle Inhalte unter `/content` und sucht nach neuen oder aktualisierten Links und fügt sie einem Cache für die Link-Checker hinzu.
1. Der **Day CQ Link Checker Service** wird dann regelmäßig ausgeführt, um die Einträge im Cache auf gültige Syntax zu überprüfen.
1. Die syntax-validierten Links werden dann im Fenster [Externe Link-Prüfung](#external-link-checker) angezeigt. Sie befinden sich jedoch im Status **Ausstehend**.
1. Die **Day CQ Link Checker-Aufgabe** wird dann regelmäßig ausgeführt, um die Links durch einen GET-Aufruf zu validieren.
1. Die Aufgabe **Day CQ Link Checker** aktualisiert dann die Einträge im Fenster External Link Checker mit den Ergebnissen der GET-Aufrufe.

## Konfigurieren der Link-Checker {#configuring}

Die Link-Checker ist in AEM automatisch standardmäßig verfügbar. Es gibt jedoch eine Reihe von OSGi-Konfigurationen, die geändert werden können, um ihr Verhalten zu ändern:

* **Day CQ Link Checker Info Datenspeicherung Service**  - Dieser Dienst definiert die Größe des Link Checker-Cache im Repository.
* **Day CQ Link Checker Service**  - Dieser Dienst führt eine asynchrone Überprüfung der Syntax externer Links durch. Sie können den Prüfzeitraum festlegen und festlegen, welche Links unter anderem von der Prüfung übersprungen werden.
* **Day CQ Link Checker-Aufgabe**  - Dieser Dienst führt die GET Validierung externer Links durch. Es ermöglicht separate Definitionen von Intervallen, um schlechte und gute Links unter anderen Optionen zu überprüfen.
* **Day CQ Link Checker Transformer**  - Ermöglicht die Konvertierung von Links basierend auf einem benutzerdefinierten Regelsatz.

Weitere Informationen zum Ändern der OSGi-Einstellungen finden Sie im Dokument [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md).

## Deaktivieren der Link-Checker {#disabling}

Sie können die Link-Checker vollständig deaktivieren. Gehen Sie dazu wie folgt vor:

1. Öffnen Sie die OSGi-Konsole.
1. Bearbeiten Sie den **Day CQ Link Checker Transformer**
1. Aktivieren Sie die zu deaktivierenden Optionen:
   * **Überprüfung**  deaktivieren - zur Deaktivierung der Überprüfung von Links
   * **Umschreiben**  deaktivieren - Linktransformationen deaktivieren

>[!NOTE]
>
>Wenn Sie die Linkprüfung deaktivieren, nachdem Sie mit der Erstellung des Inhalts begonnen haben, werden möglicherweise weiterhin Einträge im Fenster [Externe Link-Prüfung](#external-link-checker) angezeigt, die jedoch nicht mehr aktualisiert werden.
