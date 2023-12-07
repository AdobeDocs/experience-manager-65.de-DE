---
title: Konfigurieren von OSGi
description: OSGi ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet. In diesem Artikel wird beschrieben, wie Sie die Konfigurationseinstellungen für solche Bundles verwalten können.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 5ecd09a3-c4be-4361-9816-03106435346f
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1954'
ht-degree: 95%

---

# Konfigurieren von OSGi{#configuring-osgi}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

OSGi „*stellt die standardisierten Primitive bereit, mit denen Anwendungen aus kleinen, wiederverwendbaren und gemeinsamen Komponenten konstruiert werden können. Diese Komponenten können zu einer Anwendung zusammengestellt und bereitgestellt werden*“.

Dies ermöglicht die einfache Verwaltung von Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://docs.osgi.org/specification/)) ist in einem der Bundles enthalten.

Sie können die Konfigurationseinstellungen für solche Bundles wie folgt verwalten:

* mithilfe der [Adobe CQ-Web-Konsole](#osgi-configuration-with-the-web-console)
* mithilfe der [Konfigurationsdateien](#osgi-configuration-with-configuration-files)
* durch die Konfiguration von [Inhaltsknoten ( `sling:OsgiConfig`) im Repository](#osgi-configuration-in-the-repository)

Jede dieser Methoden kann verwendet werden, es gibt aber leichte Unterschiede vor allem in Bezug auf [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md):

* [Adobe CQ Web-Konsole](#osgi-configuration-with-the-web-console)

   * Die Web-Konsole ist die Standardschnittstelle für die OSGi-Konfiguration. Sie bietet eine Benutzeroberfläche für die Bearbeitung der verschiedenen Eigenschaften, wobei mögliche Werte aus vordefinierten Listen ausgewählt werden können.

     Dies ist die einfachste Methode.

   * Alle über die Web-Konsole durchgeführten Konfigurationen werden unmittelbar auf die aktuelle Instanz angewendet, und zwar unabhängig davon, welcher Ausführungsmodus gerade aktiv ist oder wie dieser zu einem späteren Zeitpunkt geändert werden könnte.

* [Konfigurationsdateien](#osgi-configuration-with-configuration-files)

   * Enthalten in der Web-Konsole definierte Einstellungen.
   * Können in Inhaltspakete zur Verwendung auf anderen Instanzen aufgenommen werden.

* [Inhaltsknoten (sling:osgiConfig) im Repository](#osgi-configuration-in-the-repository)

   * Dies erfordert die manuelle Konfiguration mithilfe von CRXDE Lite.
   * Aufgrund der Namenskonventionen der `sling:OsgiConfig`-Knoten können Sie die Konfiguration an einen bestimmten [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) knüpfen. Sie können sogar Konfigurationen für mehr als einen Ausführungsmodus im selben Repository speichern.
   * Alle entsprechenden Konfigurationen werden sofort angewendet (abhängig vom Ausführungsmodus).

Unabhängig von der verwendeten Konfigurationsmethode bieten die Konfigurationen Folgendes: 

* Stellen Sie sicher, dass beim Kopieren oder Replizieren des Repository-Inhalts identische Konfigurationen neu erstellt werden.
* Ermöglicht Ihnen das Auschecken von Konfigurationen in FileVault oder Subversion, entweder zur Sicherheit oder zu weiteren Aktualisierungen.
* Kann in Paketen gespeichert werden, die beim Einrichten anderer Instanzen verwendet werden können.
* Ermöglicht Ihnen das Ausführen von Konfigurations-Rollouts mithilfe von Skripten, um die Konfigurationsdetails zu propagieren.

>[!NOTE]
>
>Details wichtiger Einstellungen werden unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) aufgelistet. 

## OSGi-Konfiguration mit der Web-Konsole {#osgi-configuration-with-the-web-console}

Die [Web-Konsole](/help/sites-deploying/web-console.md) in AEM bietet eine standardisierte Schnittstelle zum Konfigurieren der Bundles. Die Registerkarte **Konfiguration** wird zur Konfiguration der OSGi-Bundles verwendet und ist daher der zugrunde liegende Mechanismus zur Konfiguration der AEM-Systemparameter.

Alle vorgenommenen Änderungen werden sofort auf die entsprechende OSGi-Konfiguration angewendet. Ein Neustart ist nicht erforderlich.

>[!NOTE]
>
>In der Web-Konsole durchgeführte Änderungen werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Diese Dateien können in Inhaltspakete aufgenommen und in weiteren Installationen wiederverwendet werden.

>[!NOTE]
>
>In der Web-Konsole beziehen sich alle Beschreibungen, in denen Standardeinstellungen erwähnt werden, auf die Sling-Standardeinstellungen.
>
>Adobe Experience Manager verfügt über eigene Standardeinstellungen. Deshalb können die eingestellten Standardeinstellungen von den in der Konsole dokumentierten abweichen.

So aktualisieren Sie mit der Web-Konsole eine Konfiguration:

1. Greifen Sie mithilfe einer der folgenden Methoden auf die Registerkarte **Konfiguration** der Web-Konsole zu:

   * Öffnen der Web-Konsole über den Link auf der **Tool > Vorgänge** Menü. Nach der Anmeldung in der Konsole können Sie dieses Dropdown-Menü verwenden:

     **OSGi >**

   * Die direkte URL, zum Beispiel:

     `http://localhost:4502/system/console/configMgr`

   Eine Liste wird angezeigt.

1. Wählen Sie das Bundle aus, das Sie konfigurieren möchten, indem Sie eine dieser Optionen auswählen:

   * Klicken Sie auf das Symbol **Bearbeiten** für dieses Bundle.
   * Klicken Sie auf den **Namen** des Bundles

1. Ein Dialogfeld wird angezeigt. Hier können Sie nach Bedarf Änderungen vornehmen. Legen Sie beispielsweise die **Protokollebene** nach `INFO`:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Aktualisierungen werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Um diese Dateien zu einem späteren Zeitpunkt zu finden (z. B. um sie in einem Inhaltspaket für die Verwendung in einer anderen Instanz einzuschließen), sollten Sie sich die persistente Identität (`PID`) notieren.

1. Klicken Sie auf **Speichern**.

   Ihre Änderungen werden unmittelbar auf die relevante OSGi-Konfiguration des aktuellen Systems angewendet. Es ist kein Neustart erforderlich.

   >[!NOTE]
   >
   >Sie können nun die zugehörigen [Konfigurationsdateien](#osgi-configuration-with-configuration-files) auffinden. Beispielsweise zum Einschließen in ein Inhaltspaket zur Verwendung in einer anderen Instanz.

## OSGi-Konfiguration mit Konfigurationsdateien {#osgi-configuration-with-configuration-files}

Mit der Web-Konsole durchgeführte Konfigurationsänderungen werden im Repository als Konfigurationsdateien ( `.config`) hier gespeichert:

`/apps`

Diese Dateien können in Inhaltspaketen eingeschlossen und in anderen Instanzen wiederverwendet werden.

>[!NOTE]
>
>Das Format der Konfigurationsdateien ist spezifisch. Weitere Informationen finden Sie in der Sling Apache-Dokumentation für:
>* vollständige Angaben zu [das Apache Sling Provisioning Model und Apache SlingStart](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format).
>* Tutorials und Beispiele [Abrufen von Ressourcen und Eigenschaften in Sling](https://sling.apache.org/documentation/tutorials-how-tos/getting-resources-and-properties-in-sling.html).
>
>Aus diesem Grund wird empfohlen, die Konfigurationsdatei zu erstellen und zu pflegen, indem Sie die effektiven Änderungen in der Web-Konsole vornehmen.

Die Web-Konsole zeigt nicht an, wo im Repository die Änderungen gespeichert wurden. Sie können jedoch leicht gefunden werden:

1. Erstellen Sie die Konfigurationsdatei, indem Sie [eine erstmalige Änderung in der Web-Konsole vornehmen](#osgi-configuration-with-the-web-console).
1. Öffnen Sie CRXDE Lite.
1. Wählen Sie im Menü **Werkzeuge** die Option **Abfrage…** aus.
1. Um nach der PID der Konfiguration zu suchen, die Sie aktualisiert haben, senden Sie eine Abfrage vom **Typ** `SQL`.

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
   >Sie können diese Datei zwar öffnen, um Ihre Änderungen anzuzeigen. Um Tippfehler zu vermeiden, wird jedoch empfohlen, tatsächliche Änderungen mit der Konsole vorzunehmen.

1. Sie können jetzt ein Inhaltspaket erstellen, das diesen Knoten enthält, und es nach Bedarf in anderen Instanzen verwenden.

## OSGi-Konfiguration im Repository {#osgi-configuration-in-the-repository}

Zusätzlich zur Verwendung der Web-Konsole können Sie auch im Repository Konfigurationsdetails definieren. Auf diese Weise können Sie Ihre verschiedenen Ausführungsmodi einfach konfigurieren.

Diese Konfigurationen werden vorgenommen, indem `sling:OsgiConfig`-Knoten im Repository erstellt werden, auf die das System verweist. Diese Knoten spiegeln die OSGi-Konfigurationen wider, und für sie wird eine Benutzeroberfläche gebildet. Aktualisieren Sie die Knoteneigenschaften, um die Konfigurationsdaten zu aktualisieren.

Wenn Sie die Konfigurationsdaten im Repository ändern, werden die Änderungen sofort auf die entsprechende OSGi-Konfiguration angewendet. Es ist so, als ob die Änderungen über die Web-Konsole mit den entsprechenden Validierungs- und Konsistenzprüfungen vorgenommen worden wären. Dieser Workflow gilt auch für das Kopieren einer Konfiguration von `/libs/` nach `/apps/`.

Da derselbe Konfigurationsparameter an mehreren Orten gespeichert wird, geht das System folgendermaßen vor:

* nach allen Knoten des Typs `sling:OsgiConfig` sucht.
* Es filtert nach dem Dienstnamen;
* Es filtert nach dem Ausführungsmodus.

>[!NOTE]
>
>Lesen Sie auch, [wie Sie eine Repository-basierte Konfiguration für nur eine bestimmte Instanz definieren](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17500.html?lang=de).

### Hinzufügen einer neuen Konfiguration zum Repository {#adding-a-new-configuration-to-the-repository}

#### Wissenswertes {#what-you-need-to-know}

Um eine Konfiguration zum Repository hinzuzufügen, müssen Sie Folgendes wissen:

1. Die **Persistente Identität** (PID) des Services.

   Referenzieren Sie das Feld **Konfigurationen** in der Web-Konsole. Der Name wird in Klammern hinter dem Bundle-Namen angezeigt (oder in den **Konfigurationsinformationen** am unteren Seitenrand).

   Erstellen Sie beispielsweise einen Knoten `com.day.cq.wcm.core.impl.VersionManagerImpl.` zum Konfigurieren von **AEM WCM-Versions-Manager**.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Ist eine bestimmter [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) erforderlich? Erstellen Sie den Ordner:

   * `config` – für alle Ausführungsmodi
   * `config.author` – für die Autorenumgebung
   * `config.publish` – für die Veröffentlichungsumgebung
   * `config.<run-mode>` – soweit erforderlich

1. Ist eine **Konfiguration** oder **Werkskonfiguration** erforderlich?
1. Die einzelnen Parameter, die konfiguriert werden sollen, einschließlich aller vorhandenen Parameterdefinitionen, die neu erstellt werden müssen.

   Referenzieren Sie das einzelne Parameterfeld in der Web-Konsole. Der Name wird für jeden Parameter in Klammern angezeigt.

   Erstellen Sie beispielsweise eine Eigenschaft
   `versionmanager.createVersionOnActivation`, um **Version bei Aktivierung erstellen** zu konfigurieren.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Gibt es bereits eine Konfiguration in `/libs`? Um alle Konfigurationsknoten in Ihrer Instanz aufzulisten, senden Sie über das **Abfrage**-Tool in CRXDE Lite die folgende SQL-Abfrage:

   `select * from sling:OsgiConfig`

   Wenn dies der Fall ist, kann diese Konfiguration nach ` /apps/<yourProject>/` kopiert und dann am neuen Ort angepasst werden.

#### Erstellen der Konfiguration im Repository {#creating-the-configuration-in-the-repository}

Um die neue Konfiguration zum Repository hinzuzufügen, gehen Sie folgendermaßen vor:

1. Navigieren Sie mithilfe von CRXDE Lite zu:

   ` /apps/<yourProject>`

1. Falls nicht vorhanden, erstellen Sie den Ordner `config` (`sling:Folder`):

   * `config` – anwendbar auf alle Ausführungsmodi
   * `config.<run-mode>` – für einen bestimmten Ausführungsmodus

1. Erstellen Sie unter diesem Ordner einen Knoten:

   * Typ: `sling:OsgiConfig`
   * Name: die persistente Identität (PID),

     Verwenden Sie beispielsweise AEM WCM-Versionsmanager . `com.day.cq.wcm.core.impl.VersionManagerImpl`

   >[!NOTE]
   >
   >Wenn Sie eine Werkskonfiguration durchführen, hängen Sie an den Namen `-<identifier>` an.
   >
   >Wie in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >Wobei `<identifier>` durch einen freien Text ersetzt wird, den Sie eingeben (müssen), um die Instanz zu identifizieren (diese Information darf nicht weggelassen werden); Beispiel:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Erstellen Sie für jeden Parameter, den Sie konfigurieren möchten, eine Eigenschaft in diesem Knoten:

   * Name: der Parametername, wie er in der Web-Konsole angezeigt wird. Der Name wird in Klammern am Ende der Feldbeschreibung angezeigt. Für `Create Version on Activation` verwenden sie z. B. `versionmanager.createVersionOnActivation`
   * Typ: entsprechend 
   * Wert: nach Bedarf.

   Sie müssen nur Eigenschaften für die Parameter erstellen, die Sie konfigurieren möchten. Die anderen verwenden weiterhin die von AEM festgelegten Standardwerte.

1. Speichern Sie alle Änderungen.

   Änderungen werden angewendet, wenn der Knoten aktualisiert wird, indem der Dienst neu gestartet wird (wie bei Änderungen, die in der Web-Konsole vorgenommen werden).

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.

>[!CAUTION]
>
>Der vollständige Pfad einer Konfiguration muss korrekt sein, damit er beim Start gelesen werden kann.

## Konfigurationsdetails {#configuration-details}

### Auflösungsreihenfolge beim Start {#resolution-order-at-startup}

Die folgende Rangfolge wird verwendet:

1. Repository-Knoten unter `/apps/*/config...`, entweder vom Typ `sling:OsgiConfig` oder mit Eigenschaftsdateien.

1. Repository-Knoten vom Typ `sling:OsgiConfig` unter `/libs/*/config...`. (vorgefertigte Definitionen).

1. Alle `.config`-Dateien aus `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. im lokalen Dateisystem.

Eine generische Konfiguration in `/libs` kann durch eine projektspezifische Konfiguration in `/apps` maskiert werden.

### Auflösungsreihenfolge zur Laufzeit {#resolution-order-at-runtime}

Konfigurationsänderungen bei laufendem System lösen ein Neuladen mit der geänderten Konfiguration aus.

Dann gilt die folgende Rangfolge:

1. Das Ändern einer Konfiguration in der Web-Konsole wird sofort wirksam, da sie zur Laufzeit Vorrang hat.
1. Eine Änderung einer Konfiguration in `/apps` tritt sofort in Kraft.
1. Eine Änderung einer Konfiguration in `/libs` wird sofort wirksam, sofern sie nicht durch eine Konfiguration in `/apps` maskiert wird.

### Auflösung mehrerer Ausführungsmodi {#resolution-of-multiple-run-modes}

Für Konfigurationen, die für den Ausführungsmodus spezifisch sind, können mehrere Laufmodi kombiniert werden. Sie können beispielsweise Konfigurationsordner im folgenden Stil erstellen:

`/apps/*/config.<runmode1>.<runmode2>/`

Konfigurationen in derartigen Ordnern werden angewendet, wenn alle Ausführungsmodi mit einem beim Start definierten Ausführungsmodus übereinstimmen.

Beispiel: Wenn eine Instanz mit den Ausführungsmodi `author,dev,emea` gestartet wurde, werden die Konfigurationsknoten in `/apps/*/config.emea`, `/apps/*/config.author.dev/` und `/apps/*/config.author.emea.dev/` angewendet, während die Konfigurationsknoten in `/apps/*/config.author.asean/` und `/config/author.dev.emea.noldap/` nicht angewendet werden.

Wenn für dieselbe PID mehrere Konfigurationen anwendbar sind, wird die Konfiguration mit der höchsten Anzahl an passenden Ausführungsmodi angewendet.

Beispiel: Wenn eine Instanz mit den Ausführungsmodi `author,dev,emea` gestartet wurde und sowohl `/apps/*/config.author/` als auch `/apps/*/config.emea.author/` eine Konfiguration für
`com.day.cq.wcm.core.impl.VersionManagerImpl` definieren, wird die Konfiguration in `/apps/*/config.emea.author/` angewendet.

Die Granularität dieser Regel liegt auf PID-Ebene.
Es ist nicht möglich, für dieselbe PID einige Eigenschaften in `/apps/*/config.author/` und spezifischere in `/apps/*/config.emea.author/` zu definieren.
Die Konfiguration mit der höchsten Anzahl von übereinstimmenden Ausführungsmodi ist für die gesamte PID wirksam.

### Standardkonfigurationen {#standard-configurations}

Die folgende Liste zeigt eine kleine Auswahl der im Repository verfügbaren Konfigurationen (in einer Standardinstallation):

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

   * Dies ist der private Datenbereich der OSGi-Konfigurationsverwaltung und enthält alle von `admin` angegebenen Konfigurationsdetails, unabhängig davon, wie sie in das System gelangt sind.
   * Dieser Bereich ist ein Implementierungsdetail, und Sie dürfen diesen Ordner niemals direkt bearbeiten.
   * Es ist jedoch nützlich, den Speicherort dieser Konfigurationsdateien zu kennen, damit Kopien für eine Sicherung, mehrfache Installationen oder beides erstellt werden können:

      * Apache Felix OSGi-Management Console

        `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * CRX Sling Client Repository

        `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>Die Ordner oder Dateien am folgenden Speicherort dürfen Sie niemals bearbeiten:
>
>`/crx-quickstart/launchpad/config`
