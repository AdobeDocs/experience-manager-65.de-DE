---
title: Konfigurieren von OSGi
seo-title: Configuring OSGi
description: OSGi ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet. In diesem Artikel wird beschrieben, wie Sie die Konfigurationseinstellungen für solche Bundles verwalten können.
seo-description: OSGi is a fundamental element in the technology stack of Adobe Experience Manager (AEM). It is used to control the composite bundles of AEM and their configuration. This article details how you can manage the configuration settings for such bundles.
uuid: b39059a5-dd61-486a-869a-0d7a732c3a47
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: d701e4ba-417f-4b57-b103-27fd25290736
feature: Configuring
exl-id: 5ecd09a3-c4be-4361-9816-03106435346f
source-git-commit: 55f6aab3e41159735e332b2740e3a21c563c1157
workflow-type: tm+mt
source-wordcount: '1950'
ht-degree: 39%

---

# Konfigurieren von OSGi{#configuring-osgi}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

OSGi &quot;*stellt die standardisierten Grundbausteine bereit, mit denen Anwendungen aus kleinen, wiederverwendbaren und kollaborativen Komponenten erstellt werden können. Diese Komponenten können zu einem Programm zusammengefügt und bereitgestellt werden*&quot;.

Dies ermöglicht eine einfache Verwaltung von Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://www.osgi.org/Specifications/HomePage)) ist in einem der Bundles enthalten.

Sie können die Konfigurationseinstellungen für solche Bundles wie folgt verwalten:

* mithilfe der [Adobe CQ-Webkonsole](#osgi-configuration-with-the-web-console)
* using [Konfigurationsdateien](#osgi-configuration-with-configuration-files)
* durch die Konfiguration von [Inhaltsknoten ( `sling:OsgiConfig`) im Repository](#osgi-configuration-in-the-repository)

Jede dieser Methoden kann verwendet werden, es gibt aber leichte Unterschiede vor allem in Bezug auf [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md):

* [Adobe CQ Web-Konsole](#osgi-configuration-with-the-web-console)

   * Die Web-Konsole ist die Standardschnittstelle für die OSGi-Konfiguration. Es bietet eine Benutzeroberfläche für die Bearbeitung der verschiedenen Eigenschaften, wo mögliche Werte aus vordefinierten Listen ausgewählt werden können.

      Dies ist die einfachste Methode.

   * Alle über die Web-Konsole durchgeführten Konfigurationen werden unmittelbar auf die aktuelle Instanz angewendet, und zwar unabhängig davon, welcher Ausführungsmodus gerade aktiv ist oder wie dieser zu einem späteren Zeitpunkt geändert werden könnte.

* [Konfigurationsdateien](#osgi-configuration-with-configuration-files)

   * Enthält in der Web-Konsole definierte Einstellungen.
   * Kann in Inhaltspakete zur Verwendung in anderen Instanzen enthalten sein.

* [Inhaltsknoten (sling:osgiConfig) im Repository](#osgi-configuration-in-the-repository)

   * Erfordert manuelle Konfiguration mithilfe von CRXDE Lite.
   * Aufgrund der Namenskonventionen der `sling:OsgiConfig`-Knoten können Sie die Konfiguration an einen bestimmten [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) knüpfen. Sie können sogar Konfigurationen für mehr als einen Ausführungsmodus im selben Repository speichern.
   * Alle entsprechenden Konfigurationen werden sofort angewendet (abhängig vom Ausführungsmodus).

Unabhängig von der verwendeten Konfigurationsmethode bieten die Konfigurationen Folgendes: 

* Stellen Sie sicher, dass beim Kopieren oder Replizieren des Repository-Inhalts identische Konfigurationen neu erstellt werden.
* Ermöglicht Ihnen das Auschecken von Konfigurationen in FileVault oder Subversion; entweder für Sicherheits- oder weitere Updates.
* Kann in Paketen gespeichert werden, die beim Einrichten anderer Instanzen verwendet werden können.
* Ermöglicht Ihnen, Konfigurations-Rollouts mithilfe von Skripten durchzuführen, um die Konfigurationsdetails zu propagieren.

>[!NOTE]
>
>Details wichtiger Einstellungen werden unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) aufgelistet. 

## OSGi-Konfiguration mit der Web-Konsole {#osgi-configuration-with-the-web-console}

Die [Webkonsole](/help/sites-deploying/web-console.md) in AEM bietet eine standardisierte Schnittstelle zum Konfigurieren der Bundles. Die **Konfiguration** -Tab wird zur Konfiguration der OSGi-Bundles verwendet und ist daher der zugrunde liegende Mechanismus zur Konfiguration AEM Systemparameter.

Alle vorgenommenen Änderungen werden sofort auf die entsprechende OSGi-Konfiguration angewendet. Ein Neustart ist nicht erforderlich.

>[!NOTE]
>
>In der Web-Konsole durchgeführte Änderungen werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Diese Dateien können in Inhaltspaketen zur Wiederverwendung in weiteren Installationen enthalten sein.

>[!NOTE]
>
>In der Webkonsole beziehen sich alle Beschreibungen, in denen Standardeinstellungen erwähnt werden, auf die Sling-Standardeinstellungen.
>
>Adobe Experience Manager verfügt über eigene Standardeinstellungen, sodass die festgelegten Standardeinstellungen von den in der Konsole dokumentierten Standardeinstellungen abweichen können.

So aktualisieren Sie eine Konfiguration mit der Web-Konsole:

1. Zugriff auf **Konfiguration** Registerkarte der Web-Konsole durch:

   * Öffnen Sie die Web-Konsole über den Link im Menü **Tool > Vorgänge**. Nach der Anmeldung bei der Konsole können Sie das Dropdown-Menü von Folgendem verwenden:

      **OSGi >**

   * Die direkte URL, zum Beispiel:

      `http://localhost:4502/system/console/configMgr`
   Eine Liste wird angezeigt.

1. Wählen Sie das Bundle aus, das Sie konfigurieren möchten, indem Sie eine dieser Optionen auswählen:

   * durch Klicken auf **Bearbeiten** Symbol für dieses Bundle
   * durch Klicken auf **Name** des Bundles

1. Ein Dialogfeld wird geöffnet. Hier können Sie nach Bedarf Änderungen vornehmen. Legen Sie beispielsweise die **Protokollebene** nach `INFO`:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Aktualisierungen werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Um diese Dateien anschließend zu finden und sie in ein Inhaltspaket einzuschließen, das für eine andere Instanz verwendet werden soll, notieren Sie sich beispielsweise die beständige Identität ( `PID`).

1. Klicken Sie auf **Speichern**.

   Ihre Änderungen werden unmittelbar auf die relevante OSGi-Konfiguration des aktuellen Systems angewendet. Es ist kein Neustart erforderlich. 

   >[!NOTE]
   >
   >Sie können jetzt die zugehörige [Konfigurationsdateien](#osgi-configuration-with-configuration-files). Beispiel: Aufnahme in ein Inhaltspaket zur Verwendung in einer anderen Instanz.

## OSGi-Konfiguration mit Konfigurationsdateien {#osgi-configuration-with-configuration-files}

Mit der Web-Konsole durchgeführte Konfigurationsänderungen werden im Repository als Konfigurationsdateien ( `.config`) hier gespeichert:

`/apps`

Diese Dateien können in Inhaltspakete enthalten und auf anderen Instanzen wiederverwendet werden.

>[!NOTE]
>
>Das Format der Konfigurationsdateien ist spezifisch - siehe [Sling Apache-Dokumentation](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format) für ausführliche Informationen.
>
>Aus diesem Grund wird empfohlen, die Konfigurationsdatei zu erstellen und zu verwalten, indem Sie tatsächliche Änderungen in der Web-Konsole vornehmen.

Die Web-Konsole zeigt nicht an, wo im Repository Ihre Änderungen gespeichert wurden. Sie kann jedoch leicht gefunden werden:

1. Erstellen Sie die Konfigurationsdatei durch [Erstmalige Änderung an der Web-Konsole](#osgi-configuration-with-the-web-console).
1. Öffnen Sie CRXDE Lite.
1. Im **Instrumente** Menü auswählen **Abfrage ...** .
1. Um nach der PID der Konfiguration zu suchen, die Sie aktualisiert haben, senden Sie eine Abfrage von **Typ** `SQL`.

   Beispiel: **Apache Felix OSGi Management Console** hat den Persistent Identifier (PID):

   `org.apache.felix.webconsole.internal.servlet.OsgiManager`

   Die SQL-Abfrage könnte also wie folgt lauten:

   ```shell
   select * from nt:base where jcr:path like '/apps/%' and contains(*, 'org.apache.felix.webconsole.internal.servlet.OsgiManager')
   ```

1. Der Konfigurationsdatei-Knoten wird angezeigt.

   Für das obige Beispiel:

   `/apps/system/config/org.apache.felix.webconsole.internal.servlet.OsgiManager.config`

   >[!CAUTION]
   >
   >Sie können diese Datei öffnen, um Ihre Änderungen anzuzeigen. Um Tippfehler zu vermeiden, wird jedoch empfohlen, tatsächliche Änderungen mit der Konsole vorzunehmen.

1. Sie können jetzt ein Inhaltspaket erstellen, das diesen Knoten enthält, und nach Bedarf für Ihre anderen Instanzen verwenden.

## OSGi-Konfiguration im Repository {#osgi-configuration-in-the-repository}

Zusätzlich zur Verwendung der Web-Konsole können Sie auch Konfigurationsdetails im Repository definieren. Auf diese Weise können Sie Ihre verschiedenen Ausführungsmodi einfach konfigurieren.

Diese Konfigurationen werden vorgenommen, indem `sling:OsgiConfig`-Knoten im Repository erstellt werden, auf die das System verweist. Diese Knoten spiegeln die OSGi-Konfigurationen wider, und ihnen wird eine Benutzeroberfläche gebildet. Um die Konfigurationsdaten zu aktualisieren, aktualisieren Sie die Knoteneigenschaften.

Wenn Sie die Konfigurationsdaten im Repository ändern, werden die Änderungen sofort auf die entsprechende OSGi-Konfiguration angewendet. Es ist, als ob die Änderungen über die Web-Konsole mit den entsprechenden Validierungs- und Konsistenzprüfungen vorgenommen worden wären. Dieser Workflow gilt auch für das Kopieren einer Konfiguration aus `/libs/` nach `/apps/`.

Da derselbe Konfigurationsparameter an mehreren Stellen vorhanden ist, hat das System folgende Möglichkeiten:

* nach allen Knoten des Typs `sling:OsgiConfig` sucht.
* Es filtert nach dem Dienstnamen;
* Es filtert nach dem Ausführungsmodus.

>[!NOTE]
>
>Lesen Sie auch [nur eine Repository-basierte Konfiguration für eine bestimmte Instanz definieren](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17500.html?lang=en).

### Hinzufügen einer neuen Konfiguration zum Repository {#adding-a-new-configuration-to-the-repository}

#### Wissenswertes {#what-you-need-to-know}

Um eine Konfiguration zum Repository hinzuzufügen, müssen Sie Folgendes wissen:

1. Die **Persistente Identität** (PID) des Services.

   Referenzieren Sie das Feld **Konfigurationen** in der Web-Konsole. Der Name wird in Klammern hinter dem Bundle-Namen angezeigt (oder in den **Konfigurationsinformationen** am unteren Seitenrand).

   Erstellen Sie beispielsweise einen Knoten `com.day.cq.wcm.core.impl.VersionManagerImpl.` zum Konfigurieren von **AEM WCM-Versions-Manager**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Ist eine bestimmte [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) erforderlich? Erstellen Sie den Ordner:

   * `config` – für alle Ausführungsmodi
   * `config.author` – für die Autorenumgebung
   * `config.publish` – für die Veröffentlichungsumgebung
   * `config.<run-mode>` – soweit erforderlich

1. Ist eine **Konfiguration** oder **Factory-Konfiguration** erforderlich?
1. Die einzelnen zu konfigurierenden Parameter, einschließlich aller vorhandenen Parameterdefinitionen, die neu erstellt werden müssen.

   Referenzieren Sie das einzelne Parameterfeld in der Web-Konsole. Der Name wird für jeden Parameter in Klammern angezeigt.

   Erstellen Sie beispielsweise eine Eigenschaft
   `versionmanager.createVersionOnActivation`, um **Version bei Aktivierung erstellen** zu konfigurieren.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Existiert eine Konfiguration in `/libs`? Um alle Konfigurationsknoten in Ihrer Instanz aufzulisten, senden Sie über das **Abfrage**-Tool in CRXDE Lite die folgende SQL-Abfrage:

   `select * from sling:OsgiConfig`

   Wenn dies der Fall ist, kann diese Konfiguration nach ` /apps/<yourProject>/` kopiert und dann am neuen Ort angepasst werden.

#### Erstellen der Konfiguration im Repository {#creating-the-configuration-in-the-repository}

Um die neue Konfiguration zum Repository hinzuzufügen, gehen Sie folgendermaßen vor:

1. Navigieren Sie mithilfe der CRXDE Lite zu:

   ` /apps/<yourProject>`

1. Wenn nicht vorhanden, erstellen Sie die `config` Ordner ( `sling:Folder`):

   * `config` – anwendbar auf alle Ausführungsmodi
   * `config.<run-mode>` – für einen bestimmten Ausführungsmodus

1. Erstellen Sie unter diesem Ordner einen Knoten:

   * Typ: `sling:OsgiConfig`
   * Name: die persistente Identität (PID),

      Für den AEM WCM-Versions-Manager verwenden Sie z. B. `com.day.cq.wcm.core.impl.VersionManagerImpl`
   >[!NOTE]
   >
   >Wenn Sie eine Werkskonfiguration durchführen, hängen Sie an den Namen `-<identifier>` an.
   >
   >Wie in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >Wobei `<identifier>` durch einen freien Text ersetzt wird, den Sie eingeben (müssen), um die Instanz zu identifizieren (diese Information darf nicht weggelassen werden); Beispiel:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Erstellen Sie für jeden Parameter, den Sie konfigurieren möchten, eine Eigenschaft für diesen Knoten:

   * Name: den Parameternamen, wie in der Web-Konsole angezeigt; wird der Name in Klammern am Ende der Feldbeschreibung angezeigt. Für `Create Version on Activation` verwenden sie z. B. `versionmanager.createVersionOnActivation`
   * Typ: entsprechend 
   * Wert: nach Bedarf.

   Sie müssen nur Eigenschaften für die Parameter erstellen, die Sie konfigurieren möchten, andere verwenden weiterhin die von AEM festgelegten Standardwerte.

1. Speichern Sie alle Änderungen.

   Änderungen werden angewendet, wenn der Knoten aktualisiert wird, indem der Dienst neu gestartet wird (wie bei Änderungen, die in der Webkonsole vorgenommen werden).

>[!CAUTION]
>
>Ändern Sie nichts im `/libs` Pfad.

>[!CAUTION]
>
>Der vollständige Pfad einer Konfiguration muss korrekt sein, damit er beim Start gelesen werden kann.

## Konfigurationsdetails {#configuration-details}

### Auflösungsreihenfolge beim Start {#resolution-order-at-startup}

Die folgende Rangfolge wird verwendet:

1. Repository-Knoten unter `/apps/*/config...`, entweder vom Typ `sling:OsgiConfig` oder mit Eigenschaftsdateien.

1. Repository-Knoten vom Typ `sling:OsgiConfig` unter `/libs/*/config...`. (vorgefertigte Definitionen).

1. Alle `.config`-Dateien aus `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. im lokalen Dateisystem.

Eine generische Konfiguration in `/libs` kann durch eine projektspezifische Konfiguration in maskiert werden `/apps`.

### Auflösungsreihenfolge zur Laufzeit {#resolution-order-at-runtime}

Konfigurationsänderungen, die beim Ausführen des Systems vorgenommen werden, führen zu einem Neuladen mit der geänderten Konfiguration.

Dann gilt die folgende Rangfolge:

1. Das Ändern einer Konfiguration in der Web-Konsole wird sofort wirksam, da sie zur Laufzeit Vorrang hat.
1. Ändern einer Konfiguration in `/apps` sofort wirksam wird.
1. Ändern einer Konfiguration in `/libs` tritt sofort in Kraft, es sei denn, es wird durch eine Konfiguration in `/apps`.

### Auflösung mehrerer Ausführungsmodi {#resolution-of-multiple-run-modes}

Für Ausführungsmodusspezifische Konfigurationen können mehrere Ausführungsmodi kombiniert werden. Sie können beispielsweise Konfigurationsordner im folgenden Stil erstellen:

`/apps/*/config.<runmode1>.<runmode2>/`

Konfigurationen in solchen Ordnern werden angewendet, wenn alle Ausführungsmodi mit dem beim Start definierten Ausführungsmodus übereinstimmen.

Wenn beispielsweise eine Instanz mit den Ausführungsmodi gestartet wurde `author,dev,emea`, Konfigurationsknoten in `/apps/*/config.emea`, `/apps/*/config.author.dev/`und `/apps/*/config.author.emea.dev/` angewendet wird, während Konfigurationsknoten in `/apps/*/config.author.asean/` und `/config/author.dev.emea.noldap/` nicht angewendet werden.

Wenn mehrere Konfigurationen für dieselbe PID anwendbar sind, wird die Konfiguration mit der höchsten Anzahl an passenden Ausführungsmodi angewendet.

Wenn beispielsweise eine Instanz mit den Ausführungsmodi gestartet wurde `author,dev,emea`, und beide `/apps/*/config.author/` und `/apps/*/config.emea.author/` Konfiguration für
`com.day.cq.wcm.core.impl.VersionManagerImpl`, die Konfiguration in `/apps/*/config.emea.author/` angewendet wird.

Die Granularität dieser Regel liegt auf PID-Ebene.
Es ist nicht möglich, für dieselbe PID einige Eigenschaften in `/apps/*/config.author/` und spezifischere in `/apps/*/config.emea.author/` zu definieren.
Die Konfiguration mit der höchsten Anzahl an übereinstimmenden Ausführungsmodi gilt für die gesamte PID.

### Standardkonfigurationen {#standard-configurations}

Die folgende Liste zeigt eine kleine Auswahl der verfügbaren Konfigurationen (in einer Standardinstallation) im Repository:

* Autor – AEM WCM-Filter:

   `libs/wcm/core/config.author/com.day.cq.wcm.core.WCMRequestFilter`

* Veröffentlichung – AEM WCM-Filter:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.WCMRequestFilter`

* Veröffentlichung – AEM WCM-Seitenstatistiken:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.stats.PageViewStatistics`

>[!NOTE]
>
>Da diese Konfigurationen in `/libs` gespeichert sind, dürfen sie nicht direkt bearbeitet werden, sondern müssen vor der Anpassung in Ihren Anwendungsbereich (`/apps`) kopiert werden.

Um alle Konfigurationsknoten in Ihrer Instanz aufzulisten, senden Sie über die **Abfrage**-Funktion in CRXDE Lite die folgende SQL-Abfrage:

`select * from sling:OsgiConfig`

### Persistenz von Konfigurationen {#configuration-persistence}

* Wenn Sie eine Konfiguration über die Web-Konsole ändern, wird sie (normalerweise) über folgenden Pfad in das Repository geschrieben:

   `/apps/{somewhere}`

   * Das standardmäßige `{somewhere}` ist `system/config`, sodass die Konfiguration in diesen Pfad geschrieben wird:

      `/apps/system/config`

   * Wenn Sie jedoch eine Konfiguration bearbeiten, die ursprünglich von einem anderen Ort im Repository stammte, zum Beispiel:

      /libs/foo/config/someconfig

      dann wird die aktualisierte Konfiguration unter dem ursprünglichen Speicherort geschrieben. Beispiel:

      `/apps/foo/config/someconfig`

* Einstellungen, die vom `admin` geändert werden, werden in `*.config`-Dateien gespeichert, und zwar unter:

   ```
      /crx-quickstart/launchpad/config
   ```

   * Dieser Bereich enthält die privaten Daten des OSGi-Konfigurationsadmins und enthält alle Konfigurationsdetails, die von `admin`, unabhängig davon, wie sie in das System eingetreten sind.
   * Dieser Bereich ist ein Implementierungsdetails und Sie dürfen diesen Ordner nie direkt bearbeiten.
   * Es ist jedoch nützlich, den Speicherort dieser Konfigurationsdateien zu kennen, damit Kopien für eine Sicherung, mehrere Installationen oder beides erstellt werden können:

      * Apache Felix OSGi-Management Console

         `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * CRX Sling Client Repository

         `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>Bearbeiten Sie niemals die Ordner oder Dateien unter:
>
>`/crx-quickstart/launchpad/config`
