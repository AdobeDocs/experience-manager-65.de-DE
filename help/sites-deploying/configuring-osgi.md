---
title: Konfigurieren von OSGi
seo-title: Konfigurieren von OSGi
description: OSGi ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet. In diesem Artikel erfahren Sie, wie Sie die Konfigurationseinstellungen solcher Bundles verwalten können.
seo-description: OSGi ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet. In diesem Artikel erfahren Sie, wie Sie die Konfigurationseinstellungen solcher Bundles verwalten können.
uuid: b39059a5-dd61-486a-869a-0d7a732c3a47
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: d701e4ba-417f-4b57-b103-27fd25290736
feature: Konfiguration
exl-id: 5ecd09a3-c4be-4361-9816-03106435346f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 72%

---

# Konfigurieren von OSGi{#configuring-osgi}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von Adobe Experience Manager (AEM). OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet.

OSGi *bietet standardisierte Grundbausteine – kleine, wiederverwendbare, gemeinsame genutzte Komponenten. Diese Komponenten können zu einem Programm zusammengefügt und bereitgestellt werden*&quot;.

Dies ermöglicht die einfache Verwaltung von Bundles, da diese einzeln angehalten, installiert und gestartet werden können. Die gegenseitigen Abhängigkeiten werden automatisch verwaltet. Jede OSGi-Komponente (siehe [OSGi-Spezifikation](https://www.osgi.org/Specifications/HomePage)) ist in einem der Bundles enthalten.

Für die Festlegung der Konfigurationseinstellungen derartiger Bundles haben Sie folgende Möglichkeiten:

* mit der [Adobe CQ Web-Konsole](#osgi-configuration-with-the-web-console) 
* mit [Konfigurationsdateien](#osgi-configuration-with-configuration-files) 
* Konfigurieren von [content-nodes ( `sling:OsgiConfig`) im Repository](#osgi-configuration-in-the-repository)

Jede dieser Methoden kann verwendet werden, es gibt aber leichte Unterschiede vor allem in Bezug auf [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md):

* [Adobe CQ Web-Konsole](#osgi-configuration-with-the-web-console)

   * Die Web-Konsole ist die Standard-Benutzeroberfläche für die OSGi-Konfiguration. In dieser Benutzeroberfläche können Sie die unterschiedlichen Eigenschaften bearbeiten, indem Sie aus vordefinierten Listen einen Wert auswählen.

      Dies ist die einfachste Methode.

   * Alle über die Web-Konsole durchgeführten Konfigurationen werden unmittelbar auf die aktuelle Instanz angewendet, und zwar unabhängig davon, welcher Ausführungsmodus gerade aktiv ist oder wie dieser zu einem späteren Zeitpunkt geändert werden könnte.

* [Konfigurationsdateien](#osgi-configuration-with-configuration-files)

   * Enthalten die in der Web-Konsole definierten Einstellungen
   * Können in Inhaltspakete zur Verwendung in anderen Instanzen eingeschlossen werden.

* [Inhaltsknoten (sling:osgiConfig) im Repository](#osgi-configuration-in-the-repository)

   * Dies erfordert die manuelle Konfiguration mithilfe von CRXDE Lite.
   * Aufgrund der Namenskonventionen der `sling:OsgiConfig`-Knoten können Sie die Konfiguration an einen bestimmten [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) knüpfen. Sie können sogar Konfigurationen für mehrere Ausführungsmodi im selben Repository speichern.
   * Alle Konfigurationen werden sofort angewendet (abhängig vom Ausführungsmodus).

Unabhängig von der verwendeten Konfigurationsmethode bieten die Konfigurationen Folgendes: 

* Sie gewährleisten, dass das Kopieren oder Replizieren von Inhalten im Repository identische Konfigurationen erzeugt.
* Sie ermöglichen es Ihnen, Konfigurationen entweder zur Verbesserung der Sicherheit oder für Aktualisierungen an das FileVault- oder Subversion-Tool zu übermitteln.
* Sie können in Paketen gespeichert werden, die zur Einrichtung anderer Instanzen verwendet werden können.
* Sie ermöglichen es Ihnen, mithilfe von Skripts Konfigurations-Rollouts zur Verteilung der Konfigurationsdetails durchzuführen.

>[!NOTE]
>
>Details wichtiger Einstellungen werden unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) aufgelistet. 

## OSGi-Konfiguration mit der Web-Konsole {#osgi-configuration-with-the-web-console}

Die [Web-Konsole](/help/sites-deploying/web-console.md) in AEM bietet eine standardisierte Benutzeroberfläche für die Konfiguration der Bundles. Die Registerkarte **Konfiguration** dient zur Konfiguration der OSGi-Bundles und bildet deshalb den zugrunde liegenden Mechanismus für die Konfiguration der AEM-Systemparameter.

Alle Änderungen werden unverzüglich auf die entsprechende OSGi-Konfiguration angewendet. Es ist kein Neustart erforderlich.

>[!NOTE]
>
>Änderungen, die in der Web-Konsole vorgenommen werden, werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Diese können in Inhaltspakete eingefügt und für weitere Installationen erneut verwendet werden.

>[!NOTE]
>
>In der Web-Konsole beziehen sich alle Beschreibungen mit Standardeinstellungen auf Sling-Standardwerte.
>
>Adobe Experience Manager verfügt über eigene Standardwerte. Deshalb können die eingestellten Standardwerte von den in der Konsole dokumentierten abweichen.

Um eine Konfiguration mit der Web-Konsole zu aktualisieren, gehen Sie folgendermaßen vor:

1. Öffnen Sie die Registerkarte **Konfiguration** in der Web-Konsole, indem Sie einen dieser Schritte ausführen:

   * Öffnen Sie die Web-Konsole über den Link im Menü **Tool > Vorgänge**. Nach der Anmeldung bei der Konsole können Sie das Dropdown-Menü von:

      **OSGi >**

   * die direkte URL; Beispiel:

      `http://localhost:4502/system/console/configMgr`
   Eine Liste wird angezeigt. 

1. Wählen Sie das Bundle aus, das Sie konfigurieren möchten, indem Sie eine dieser Optionen auswählen:

   * Klicken Sie auf das Symbol **Bearbeiten** für dieses Bundle.
   * Klicken Sie auf den **Namen** des Bundles.

1. Ein Dialogfeld wird geöffnet. Hier können Sie nach Bedarf Änderungen vornehmen. Beispielsweise können Sie für die **Protokollebene** `INFO` festlegen:

   ![chlimage_1-140](assets/chlimage_1-140.png)

   >[!NOTE]
   >
   >Aktualisierungen werden im Repository als [Konfigurationsdateien](#osgi-configuration-with-configuration-files) gespeichert. Um diese anschließend zu finden (z. B. um sie in ein Inhaltspaket zur Verwendung in einer anderen Instanz einzuschließen), sollten Sie die beständige Identität ( `PID`) notieren.

1. Klicken Sie auf **Speichern**.

   Ihre Änderungen werden unmittelbar auf die relevante OSGi-Konfiguration des aktuellen Systems angewendet. Es ist kein Neustart erforderlich. 

   >[!NOTE]
   >
   >Sie können nun die zugehörigen Konfigurationsdateien [suchen. z. B. in ein Inhaltspaket zur Verwendung in einer anderen Instanz einschließen.](#osgi-configuration-with-configuration-files)

## OSGi-Konfiguration mit Konfigurationsdateien {#osgi-configuration-with-configuration-files}

Konfigurationsänderungen, die mithilfe der Web-Konsole vorgenommen werden, werden im Repository als Konfigurationsdateien ( `.config`) unter folgendem Pfad beibehalten:

`/apps`

Diese können in Inhaltspaketen eingeschlossen und in anderen Instanzen wiederverwendet werden.

>[!NOTE]
>
>Das Format der Konfigurationsdateien ist sehr spezifisch - vollständige Details finden Sie in der [Sling Apache-Dokumentation](https://sling.apache.org/documentation/development/slingstart.html#default-configuration-format) .
>
>Aus diesem Grund ist es empfehlenswert, die Erstellung und Wartung der Konfigurationsdatei in der Web-Konsole durchzuführen.

Die Web-Konsole zeigt nicht an, wo im Repository Ihre Änderungen gespeichert wurden, sie können aber einfach gefunden werden:

1. Erstellen Sie die Konfigurationsdatei, indem Sie [eine Änderung in der Web-Konsole vornehmen](#osgi-configuration-with-the-web-console).
1. Öffnen Sie CRXDE Lite.
1. Wählen Sie im Menü **Tools** die Option **Abfrage ...** aus.
1. Führen Sie eine Abfrage vom **Typ** `SQL` durch, um nach der PID der Konfiguration zu suchen, die Sie aktualisiert haben.

   Beispiel: **Apache Felix OSGi Management Console** hat den Persistent Identifier (PID):

   `org.apache.felix.webconsole.internal.servlet.OsgiManager`

   Die SQL-Abfrage könnte also folgendermaßen lauten:

   ```shell
   select * from nt:base where jcr:path like '/apps/%' and contains(*, 'org.apache.felix.webconsole.internal.servlet.OsgiManager')
   ```

1. Der Knoten der Konfigurationsdatei wird angezeigt.

   Für das oben genannte Beispiel:

   `/apps/system/config/org.apache.felix.webconsole.internal.servlet.OsgiManager.config`

   >[!CAUTION]
   >
   >Sie können diese Datei öffnen, um sich Ihre Änderungen anzusehen, doch um Schreibfehler zu vermeiden, wird empfohlen, die tatsächlichen Änderungen in der Konsole vorzunehmen.

1. Sie können jetzt ein Inhaltspaket erstellen, das diesen Knoten enthält, und es nach Bedarf in Ihren anderen Instanzen verwenden.

## OSGi-Konfiguration im Repository  {#osgi-configuration-in-the-repository}

Neben der Verwendung der Web-Konsole ist die Definition der Konfigurationsdetails auch im Repository möglich. Damit können Sie die unterschiedlichen Ausführungsmodi einfach konfigurieren.

Diese Konfigurationen werden vorgenommen, indem `sling:OsgiConfig`-Knoten im Repository erstellt werden, auf die das System verweist. Diese Knoten bilden die OSGi-Konfigurationen ab und stellen für sie eine Benutzeroberfläche bereit. Um die Konfigurationsdaten zu aktualisieren, aktualisieren Sie die Knoteneigenschaften.

Wenn Sie die Konfigurationsdaten im Repository ändern, werden die Änderungen sofort auf die entsprechende OSGi-Konfiguration angewendet, so als ob die Änderungen in der Web-Konsole vorgenommen worden wären, einschließlich der entsprechenden Validierungs- und Konsistenzprüfungen. Dies gilt auch für das Kopieren einer Konfiguration von `/libs/` in `/apps/`.

Da derselbe Konfigurationsparameter an mehreren Orten gespeichert werden kann, geht das System folgendermaßen vor:

* sucht nach allen Knoten des Typs `sling:OsgiConfig`
* Es filtert nach dem Dienstnamen;
* Es filtert nach dem Ausführungsmodus.

>[!NOTE]
>
>Lesen Sie auch, [wie Sie eine Konfiguration im Repository nur für eine bestimmte Instanz definieren können](https://helpx.adobe.com/experience-manager/kb/RunModeDependentConfigAndInstall.html).

### Hinzufügen einer neuen Konfiguration zum Repository  {#adding-a-new-configuration-to-the-repository}

#### Informationen, die Sie dafür benötigen {#what-you-need-to-know}

Um eine neue Konfiguration zum Repository hinzuzufügen, benötigen Sie folgende Informationen:

1. Die **Persistent Identity** (PID) des Dienstes.

   Verweisen Sie in der Web-Konsole auf das Feld **Konfigurationen** . Der Name wird in eckigen Klammern hinter dem Bundle-Namen (oder in den **Konfigurationsinformationen** am unteren Rand der Seite) angezeigt.

   Erstellen Sie beispielsweise einen Knoten `com.day.cq.wcm.core.impl.VersionManagerImpl.`, um **AEM WCM-Versionsmanager** zu konfigurieren.

   ![chlimage_1-141](assets/chlimage_1-141.png)

1. Gibt an, ob ein bestimmter [Ausführungsmodus](/help/sites-deploying/configure-runmodes.md) erforderlich ist. Erstellen Sie den Ordner:

   * `config` - für alle Ausführungsmodi
   * `config.author` - für die Autorenumgebung
   * `config.publish` - für die Veröffentlichungsumgebung
   * `config.<run-mode>` - gegebenenfalls

1. Ob eine **Konfiguration** oder **Werkskonfiguration** erforderlich ist.
1. Die einzelnen Parameter, die konfiguriert werden müssen, einschließlich etwaiger vorhandener Parameterdefinitionen, die neu erstellt werden müssen.

   Referenzieren Sie das einzelne Parameterfeld in der Web-Konsole. Der Name wird für jeden Parameter in Klammern angezeigt.

   Erstellen Sie beispielsweise eine Eigenschaft
   `versionmanager.createVersionOnActivation` , um die Option  **Version bei Aktivierung erstellen** zu konfigurieren.

   ![chlimage_1-142](assets/chlimage_1-142.png)

1. Gibt es bereits eine Konfiguration in `/libs`? Um alle Konfigurationen in Ihrer Instanz aufzulisten, verwenden Sie das Tool **Abfrage** in CRXDE Lite, um die folgende SQL-Abfrage zu senden:

   `select * from sling:OsgiConfig`

   Wenn ja, kann diese Konfiguration nach ` /apps/<yourProject>/` kopiert und dann am neuen Speicherort angepasst werden.

#### Erstellen der Konfiguration im Repository {#creating-the-configuration-in-the-repository}

Um die neue Konfiguration zum Repository hinzuzufügen, gehen Sie folgendermaßen vor:

1. Navigieren Sie mit CRXDE Lite zu:

   ` /apps/<yourProject>`

1. Wenn noch nicht vorhanden, erstellen Sie den Ordner `config` ( `sling:Folder`):

   * `config` – anwendbar auf alle Ausführungsmodi
   * `config.<run-mode>` - spezifisch für einen bestimmten Ausführungsmodus

1. Erstellen Sie unter diesem Ordner einen Knoten:

   * Typ: `sling:OsgiConfig`
   * Name: die persistente Identität (PID);

      Verwenden Sie beispielsweise AEM WCM-Versionsmanager `com.day.cq.wcm.core.impl.VersionManagerImpl`
   >[!NOTE]
   >
   >Hängen Sie beim Erstellen einer Werkskonfiguration `-<identifier>` an den Namen an.
   >
   >Wie in: `org.apache.sling.commons.log.LogManager.factory.config-<identifier>`
   >
   >wobei `<identifier>` durch freien Text ersetzt wird, den Sie eingeben (müssen), um die Instanz zu identifizieren (diese Information darf nicht weggelassen werden); Beispiel:
   >
   >`org.apache.sling.commons.log.LogManager.factory.config-MINE`

1. Erstellen Sie für jeden Parameter, den Sie konfigurieren möchten, eine Eigenschaft auf diesem Knoten:

   * Name: der Parametername, wie er in der Web-Konsole gezeigt wird. Der Name erscheint in Klammern am Ende der Feldbeschreibung. Verwenden Sie beispielsweise für `Create Version on Activation` `versionmanager.createVersionOnActivation`
   * Typ: entsprechend 
   * Wert: nach Bedarf

   Sie müssen nur Eigenschaften für die Parameter erstellen, die Sie konfigurieren möchten. Die anderen übernehmen die Standardwerte von AEM.

1. Speichern Sie alle Änderungen.

   Die Änderungen werden angewendet, wenn der Knoten durch den Neustart des Dienstes aktualisiert wird (ebenso wie die in der Web-Konsole vorgenommenen Änderungen).

>[!CAUTION]
>
>Sie dürfen keinerlei Änderungen im Pfad `/libs` vornehmen.

>[!CAUTION]
>
>Der vollständige Pfad einer Konfiguration muss korrekt sein, damit er beim Start gelesen werden kann.

## Konfigurationsdetails  {#configuration-details}

### Auflösungsreihenfolge beim Start {#resolution-order-at-startup}

Die folgende Reihenfolge wird verwendet:

1. Repository-Knoten unter `/apps/*/config...`.entweder mit Typ `sling:OsgiConfig` oder Eigenschaftendateien.

1. Repository-Knoten mit Typ `sling:OsgiConfig` unter `/libs/*/config...`. (vorgefertigte Definitionen).

1. Alle `.config`-Dateien von `<*cq-installation-dir*>/crx-quickstart/launchpad/config/...`. im lokalen Dateisystem.

Dies bedeutet, dass eine generische Konfiguration in `/libs` durch eine projektspezifische Konfiguration in `/apps` maskiert werden kann.

### Auflösungsreihenfolge während der Laufzeit {#resolution-order-at-runtime}

Konfigurationsänderungen, die während der Laufzeit des Systems vorgenommen werden, lösen einen neuen Ladevorgang mit der geänderten Konfiguration aus.

Anschließend wird die folgende Reihenfolge angewendet:

1. Die Änderung einer Konfiguration in der Web-Konsole wird sofort angewendet, da sie während der Laufzeit Vorrang hat.
1. Die Änderung einer Konfiguration in `/apps` wird sofort wirksam.
1. Die Änderung einer Konfiguration in `/libs` wird sofort wirksam, es sei denn, sie wird durch eine Konfiguration in `/apps` verdeckt.

### Auflösung mehrerer Ausführungsmodi {#resolution-of-multiple-run-modes}

Für Ausführungsmodus-spezifische Konfigurationen können mehrere Ausführungsmodi kombiniert werden. Beispielsweise können Sie Konfigurationsordner vom folgenden Typ erstellen:

`/apps/*/config.<runmode1>.<runmode2>/`

Konfigurationen in derartigen Ordnern werden angewendet, wenn alle Ausführungsmodi mit einem beim Start definierten Ausführungsmodus übereinstimmen.

Wenn beispielsweise eine Instanz mit den Ausführungsmodi `author,dev,emea` gestartet wurde, werden Konfigurationsknoten in `/apps/*/config.emea`, `/apps/*/config.author.dev/` und `/apps/*/config.author.emea.dev/` angewendet, während Konfigurationsknoten in `/apps/*/config.author.asean/` und `/config/author.dev.emea.noldap/` nicht angewendet werden.

Wenn mehrere Konfigurationen für dieselbe PID anwendbar sind, wird die Konfiguration mit der höchsten Anzahl an passenden Ausführungsmodi angewendet.

Wenn beispielsweise eine Instanz mit den Ausführungsmodi `author,dev,emea` gestartet wurde und sowohl `/apps/*/config.author/` als auch `/apps/*/config.emea.author/` eine Konfiguration für
`com.day.cq.wcm.core.impl.VersionManagerImpl` wird die Konfiguration in `/apps/*/config.emea.author/` angewendet.

Die Granularität dieser Regel liegt auf PID-Ebene.
Es ist nicht möglich, einige Eigenschaften für dieselbe PID in `/apps/*/config.author/` und spezifischere in `/apps/*/config.emea.author/` für dieselbe PID zu definieren.
Die Konfiguration mit der höchsten Anzahl von übereinstimmenden Ausführungsmodi tritt für die gesamte PID in Kraft. 

### Standardkonfigurationen {#standard-configurations}

In der folgenden Liste finden Sie eine kleine Auswahl an verfügbaren Konfigurationen (in einer Standardinstallation) im Repository:

* Autor - AEM WCM-Filter:

   `libs/wcm/core/config.author/com.day.cq.wcm.core.WCMRequestFilter`

* Publish - AEM WCM-Filter:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.WCMRequestFilter`

* Veröffentlichen - AEM WCM-Seitenstatistiken:

   `libs/wcm/core/config.publish/com.day.cq.wcm.core.stats.PageViewStatistics`

>[!NOTE]
>
>Da sich diese Konfigurationen in `/libs` befinden, dürfen sie nicht direkt bearbeitet, sondern vor der Anpassung in den Anwendungsbereich ( `/apps`) kopiert werden.

Um alle Konfigurationsknoten in Ihrer Instanz aufzulisten, senden Sie über die **Abfrage**-Funktion in CRXDE Lite die folgende SQL-Abfrage:

`select * from sling:OsgiConfig`

### Persistenz von Konfigurationen {#configuration-persistence}

* Wenn Sie eine Konfiguration über die Web-Konsole ändern, wird sie (in der Regel) in das Repository geschrieben unter:

   `/apps/{somewhere}`

   * Standardmäßig ist `{somewhere}` `system/config` , sodass die Konfiguration in

      `/apps/system/config`

   * Wenn Sie jedoch eine Konfiguration bearbeiten, die ursprünglich von einem anderen Speicherort im Repository stammte: Beispiel:

      /libs/foo/config/someconfig

      Anschließend wird die aktualisierte Konfiguration unter dem ursprünglichen Speicherort geschrieben. Beispiel:

      `/apps/foo/config/someconfig`

* Einstellungen, die von `admin` geändert werden, werden in `*.config` Dateien unter folgendem Pfad gespeichert:

   ```
      /crx-quickstart/launchpad/config
   ```

   * Dies ist der private Datenbereich der OSGi-Konfigurationsverwaltung. Er enthält alle Konfigurationsdetails, die durch `admin` spezifiziert wurden, und zwar unabhängig davon, wie sie in das System gelangt sind. 
   * Dies ist ein Implementierungsdetail; Sie dürfen dieses Verzeichnis nie direkt bearbeiten.
   * Es ist jedoch hilfreich, den Speicherort dieser Konfigurationsdateien zu kennen, damit Sie Kopien zur Sicherung und/oder mehrere Installationen erstellen können:

      * Apache Felix OSGi-Management Console

         `../crx/org/apache/felix/webconsole/internal/servlet/OsgiManager.config`

      * CRX Sling Client Repository

         `../com/day/crx/sling/client/impl/CRXSlingClientRepository/<pid-nr>.config`

>[!CAUTION]
>
>Die Ordner oder Dateien an diesem Speicherort dürfen Sie ***niemals*** bearbeiten:
>
>`/crx-quickstart/launchpad/config`
