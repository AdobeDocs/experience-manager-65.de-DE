---
title: Replikation
description: Erfahren Sie, wie Sie Replikationsagenten in Adobe Experience Manager konfigurieren und überwachen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
docset: aem65
feature: Configuring
exl-id: 09943de5-8d62-4354-a37f-0521a66b4c49
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '3363'
ht-degree: 100%

---

# Replikation{#replication}

Replikationsagenten bilden einen zentralen Bestandteil von Adobe Experience Manager (AEM). Sie dienen als Mechanismus zum:

* [Veröffentlichen (Aktivieren)](/help/sites-authoring/publishing-pages.md#activatingcontent) von Inhalten von einer Autorenumgebung in einer Veröffentlichungsumgebung.
* expliziten Leeren von Inhalten aus dem Dispatcher-Cache.
* Zurückgeben von Benutzereingaben (z. B. Formulareingaben) aus der Veröffentlichungsumgebung an die Autorenumgebung (unter Kontrolle der Autorenumgebung)

Anfragen werden zur Verarbeitung durch den entsprechenden Agenten in eine [Warteschlange gestellt](/help/sites-deploying/osgi-configuration-settings.md#apacheslingjobeventhandler).

>[!NOTE]
>
>Benutzerdaten (Benutzende, Benutzergruppen und Benutzerprofile) werden nicht zwischen Autoren- und Veröffentlichungsinstanzen repliziert.
>
>Bei mehreren Veröffentlichungsinstanzen werden Benutzerdaten mithilfe von Sling verteilt, wenn die [Benutzersynchronisierung](/help/sites-administering/sync.md) aktiviert ist.

## Replizieren von der Autoren- in die Veröffentlichungsinstanz {#replicating-from-author-to-publish}

Die Replikation in eine Veröffentlichungsinstanz oder auf einen Dispatcher verläuft in mehreren Schritten:

* Die Autoreninstanz fordert die Veröffentlichung (Aktivierung) bestimmter Inhalte an. Dabei kann es sich um eine manuelle oder eine automatisch ausgelöste, vorkonfigurierte Anfrage handeln.
* Die Anfrage wird an den entsprechenden standardmäßigen Replikationsagenten übergeben. Eine Umgebung kann mehrere Standardagenten aufweisen, die immer für diese Aktionen ausgewählt werden.
* Der Replikationsagent „verpackt“ die Inhalte und stellt sie in die Replikationswarteschlange.
* Auf der Registerkarte „Websites“ kann die [farbige Statusanzeige](/help/sites-authoring/publishing-pages.md#determiningpagepublicationstatus) für die einzelnen Seiten eingestellt werden.
* Die Inhalte werden aus der Warteschlange abgerufen und mithilfe des konfigurierten Protokolls (in der Regel HTTP) an die Veröffentlichungsumgebung übertragen.
* Ein Servlet in der Veröffentlichungsumgebung empfängt die Anfrage und veröffentlicht die empfangenen Inhalte. Das Standard-Servlet ist `https://localhost:4503/bin/receive`.

* Es können mehrere Autoren- und Veröffentlichungsumgebungen konfiguriert werden.

![chlimage_1-21](assets/chlimage_1-21.png)

### Replizieren von der Veröffentlichungs- in die Autoreninstanz {#replicating-from-publish-to-author}

Benutzende können eine Reihe von Funktionen zum Eingeben von Daten in einer Veröffentlichungsinstanz nutzen.

Mitunter ist eine bestimmte Form der Replikation erforderlich (die sogenannte Rückwärtsreplikation), um diese Daten an die Autorenumgebung zurückzuleiten, von wo sie an andere Veröffentlichungsumgebungen neu verteilt werden. Aus Sicherheitsgründen muss der gesamte Traffic von der Veröffentlichungs- an die Autorenumgebung streng kontrolliert werden.

Die Rückwärtsreplikation nutzt einen Agenten in der Veröffentlichungsumgebung, der die Autorenumgebung referenziert. Dieser Agent legt die Daten in einem Postausgang ab. Diesem Postausgang sind Replikations-Listener in der Autorenumgebung zugeordnet. Die Listener fragen die Postausgänge ab, um darin abgelegte Daten abzurufen und diese dann ggf. zu verteilen. So wird sichergestellt, dass die Autorenumgebung den gesamten Traffic steuert.

In anderen Fällen wie etwa bei Communities-Funktionen (z. B. Foren, Blogs, Kommentaren und Bewertungen) ist es schwierig, das hohe Volumen der in der Veröffentlichungsumgebung eingegebenen, nutzergenerierten Inhalte (User-Generated Content, UGC) mittels Replikation effizient mit allen AEM-Instanzen zu synchronisieren.

AEM [Communities](/help/communities/overview.md) verwendet keine Replikation für benutzergenerierte Inhalte. Stattdessen ist zur Bereitstellung von benutzergenerierten Inhalten für Communities ein Common Store erforderlich (siehe [Community-Inhaltsspeicher](/help/communities/working-with-srp.md)).

### Replikation – vorkonfiguriert {#replication-out-of-the-box}

Am Beispiel der we-retail-Website, die Teil der Standardinstallation von AEM ist, kann die Replikation illustriert werden.

Um diesem Beispiel zu folgen und die standardmäßigen Replikationsagenten zu verwenden, müssen Sie [AEM installieren](/help/sites-deploying/deploy.md) und dabei Folgendes konfigurieren:

* die Autorenumgebung an Port `4502`
* die Veröffentlichungsumgebung an Port `4503`

>[!NOTE]
>
>Standardmäßig aktiviert:
>
>* Agenten für Autor: Standardagent („publish“)
>
>Standardmäßig deaktiviert (ab AEM 6.1):
>
>* Agenten für Autor: Rückwärtsreplikationsagent („publish_reverse“)
>* Agenten bei Veröffentlichung: Rückwärtsreplikation („outbox“)
>
>Der Status des Agenten oder der Warteschlange kann mithilfe der **Tools-Konsole** überprüft werden.
>Weitere Informationen finden Sie unter [Überwachen der Replikationsagenten](#monitoring-your-replication-agents).

#### Replikation (von der Autoren- in die Veröffentlichungsinstanz) {#replication-author-to-publish}

1. Navigieren Sie zur Support-Seite in der Autorenumgebung.
   **https://localhost:4502/content/we-retail/us/en/experience.html** `<pi>`
1. Bearbeiten Sie die Seite, um neuen Text hinzuzufügen.
1. **Aktivieren Sie die Seite**, um die Änderungen zu veröffentlichen.
1. Öffnen Sie die Support-Seite in der Veröffentlichungsumgebung:
   **https://localhost:4503/content/we-retail/us/en/experience.html**
1. Nun können Sie die Änderungen sehen, die Sie in der Autorenumgebung eingegeben haben.

Diese Replikation wird von der Autorenumgebung aus durch folgende Komponente durchgeführt:

* **Standardagent („publish“)**
Dieser Agent repliziert Inhalte in die standardmäßige Veröffentlichungsinstanz.
Der Zugriff auf entsprechende Details (Konfiguration und Protokolle) ist über die Tools-Konsole der Autorenumgebung oder
  `https://localhost:4502/etc/replication/agents.author/publish.html` möglich.

#### Replikationsagenten – vorkonfiguriert {#replication-agents-out-of-the-box}

Die folgenden Agenten sind in der AEM-Standardinstallation verfügbar:

* [Standardagent](#replication-author-to-publish)
Dient zum Replizieren von der Autoren- in die Veröffentlichungsinstanz.

* Dispatcher Flush
Dient zum Verwalten des Dispatcher-Caches. Weitere Informationen finden Sie unter [Invalidieren des Dispatcher-Cache aus der Autorenumgebung](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=de#invalidating-dispatcher-cache-from-the-authoring-environment) und [Invalidieren des Dispatcher-Cache von einer Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=de#invalidating-dispatcher-cache-from-a-publishing-instance).

* [Rückwärtsreplikation](#reverse-replication-publish-to-author)
Dient zum Replizieren von der Veröffentlichungs- in die Autoreninstanz. Die Rückwärtsreplikation wird nicht für Communities-Funktionen wie Foren, Blogs und Kommentare verwendet. Sie ist effektiv deaktiviert, da der Postausgang nicht aktiviert ist. Für die Rückwärtsreplikation ist eine benutzerdefinierte Konfiguration erforderlich.

* Statischer Agent
Dies ist ein „Agent, der eine statische Repräsentation eines Knotens im Dateisystem speichert“.
Bei den Standardeinstellungen werden beispielsweise Inhaltsseiten und DAM-Assets unter `/tmp` gespeichert, entweder im HTML- oder im entsprechenden Asset-Format. Weitere Einzelheiten zur Konfiguration finden Sie auf den Registerkarten `Settings` und `Rules`.
Der Grund hierfür war, dass die Inhalte sichtbar sein sollten, wenn die Seite direkt vom Anwendungs-Server angefordert wird. Hierbei handelt es sich um einen speziellen Agenten, der (wahrscheinlich) für den Großteil der Instanzen nicht benötigt wird.

## Replikationsagenten – Konfigurationsparameter {#replication-agents-configuration-parameters}

Beim Konfigurieren eines Replikationsagenten in der Tools-Konsole stehen vier Registerkarten im Dialogfeld zur Verfügung:

### Einstellungen {#settings}

* **Name**

  Ein eindeutiger Name für den Replikationsagenten.

* **Beschreibung**

  Eine Beschreibung des Zwecks, den dieser Replikationsagent erfüllt.

* **Aktiviert**

  Gibt an, ob der Replikationsagent aktiviert ist.

  Wenn der Agent **aktiviert** ist, wird der Status der Warteschlange wie folgt angezeigt:

   * **Aktiv**, wenn Elemente verarbeitet werden.
   * **Leer**, wenn die Warteschlange leer ist.
   * **Blockiert**, wenn die Warteschlange Elemente enthält, die jedoch nicht verarbeitet werden können, z. B. wenn die empfangende Warteschlange deaktiviert ist.

* **Anordnungstyp**

  Der Anordnungstyp:

   * **Standard**: Legen Sie diese Einstellung fest, wenn der Agent automatisch ausgewählt werden soll.
   * **Dispatcher Flush**: Wählen Sie diese Einstellung aus, wenn der Agent zum Leeren des Dispatcher-Caches verwendet werden soll.

* **Verzögerung wiederholen**

  Die Verzögerung (Wartezeit in Millisekunden) zwischen zwei Wiederholungen, wenn ein Problem auftritt.

  Standard: `60000`

* **Agenten-Benutzer-ID**

  Abhängig von der Umgebung verwendet der Agent dieses Benutzerkonto, um folgende Aktionen durchzuführen:

   * Erfassen und Verpacken der Inhalte aus der Autorenumgebung
   * Erstellen und Schreiben der Inhalte in der Veröffentlichungsumgebung

  Lassen Sie dieses Feld leer, um das Systembenutzerkonto zu verwenden (das in Sling als Admin definierte Konto – standardmäßig ist dies das `admin`-Konto).

  >[!CAUTION]
  >
  >Für einen Agenten in der Autorenumgebung *muss* dieses Konto Lesezugriff auf alle Pfade haben, die repliziert werden sollen.

  >[!CAUTION]
  >
  >Für einen Agenten in der Veröffentlichungsumgebung *muss* dieses Konto über die erforderlichen Erstellungs-/Schreibberechtigungen zum Replizieren der Inhalte verfügen.

  >[!NOTE]
  >
  >Dies kann als Mechanismus zum Auswählen bestimmter Inhalte für die Replikation dienen.

* **Protokollebene**

  Gibt den Detaillierungsgrad an, der für Protokollmeldungen verwendet werden soll.

   * `Error`: Es werden nur Fehler protokolliert
   * `Info`: Fehler, Warnungen und andere Informationsmeldungen werden protokolliert
   * `Debug`: Es wird ein hoher Detaillierungsgrad für die Meldungen verwendet. Dieser dient vor allem Debugging-Zwecken

  Standard: `Info`

* **Für Rückwärtsreplikation verwenden**

  Gibt an, ob dieser Agent für die Rückwärtsreplikation verwendet wird, und leitet Benutzereingaben von der Veröffentlichungsumgebung an die Autorenumgebung zurück.

* **Alias-Aktualisierung**

  Durch Auswahl dieser Option werden Anforderungen an den Dispatcher zur Invalidierung des Alias- oder Vanity-Pfads aktiviert. Weitere Informationen finden Sie auch unter [Konfigurieren eines Dispatcher Flush-Agenten](/help/sites-deploying/replication.md#configuring-a-dispatcher-flush-agent).

#### Transport {#transport}

* **URI**

  Gibt das Empfangs-Servlet am Zielspeicherort an. Insbesondere können Sie hier den Host-Namen (oder Alias) und den Kontextpfad zur Zielinstanz angeben.

  Beispiel:

   * Ein Standardagent wird möglicherweise unter `https://localhost:4503/bin/receive` repliziert.
   * Ein Dispatcher Flush-Agent wird möglicherweise unter `https://localhost:8000/dispatcher/invalidate.cache` repliziert.

  Das hier angegebene Protokoll (HTTP oder HTTPS) bestimmt die Transportmethode.

  Für Dispatcher Flush-Agenten wird die URI-Eigenschaft nur verwendet, wenn Sie pfadbasierte „VirtualHost“-Einträge nutzen, um zwischen Farmen zu unterscheiden. Dieses Feld dient dazu, die zu invalidierende Farm anzugeben. Beispiel: Farm 1 hat den virtuellen Host `www.mysite.com/path1/*` und Farm 2 den virtuellen Host `www.mysite.com/path2/*`. Mit der URL `/path1/invalidate.cache` können Sie die erste Farm und mit `/path2/invalidate.cache` die zweite Farm bestimmen.

* **Benutzer**

  Der Benutzername für das Konto, das zum Zugreifen auf das Ziel verwendet werden soll.

* **Kennwort**

  Das Kennwort für das Konto, das zum Zugreifen auf das Ziel verwendet werden soll.

* **NTLM-Domäne**

  Die Domäne für die NTLM-Authentifizierung.

* **NTLM-Host**

  Der Host für die NTLM-Authentifizierung.

* **Relaxed SSL aktivieren**

  Aktivieren Sie diese Option, wenn selbstzertifizierte SSL-Zertifikate akzeptiert werden sollen.

* **Abgelaufene Zertifikate zulassen**

  Aktivieren Sie diese Option, wenn abgelaufene SSL-Zertifikate akzeptiert werden sollen.

#### Proxy {#proxy}

Die folgenden Einstellungen müssen nur festgelegt werden, wenn ein Proxy benötigt wird:

* **Proxy-Host**

  Der Host-Name des für den Transport verwendeten Proxys.

* **Proxy-Port**

  Der Proxy-Port.

* **Proxy-Benutzer**

  Der Benutzername des zu verwendenden Kontos.

* **Proxy-Kennwort**

  Das Kennwort des zu verwendenden Kontos.

* **Proxy-NTLM-Domäne**

  Die NTLM-Domain des Proxys.

* **Proxy-NTLM-Host**

  Die NTLM-Domain des Proxys.

#### Erweitert {#extended}

* **Benutzeroberfläche**

  Hier können Sie die Socket-Schnittstelle für die Verbindung definieren.

  Dadurch wird beim Erstellen von Verbindungen die lokale Adresse verwendet. Wurde diese Einstellung nicht festgelegt, wird die Standardadresse verwendet. Dies ist zum Festlegen der Schnittstelle nützlich, die für Multicast- oder Cluster-Systeme verwendet werden soll.

* **HTTP-Methode**

  Die zu verwendende HTTP-Methode.

  Für einen Dispatcher Flush-Agenten ist dies fast immer „GET“ und sollte nicht geändert werden (ein weiterer möglicher Wert ist POST).

* **HTTP-Kopfzeilen**

  Sie werden für Dispatcher Flush-Agenten verwendet und geben Elemente an, die entfernt werden müssen.

  Es sollte nicht notwendig sein, die drei Standardeinträge für einen Dispatcher Flush-Agenten zu ändern:

   * `CQ-Action:{action}`
   * `CQ-Handle:{path}`
   * `CQ-Path:{path}`

  Diese dienen ggf. dazu, die Aktion anzugeben, die beim Leeren des Handles oder Pfades verwendet werden soll. Die Unterparameter sind dynamisch:

   * `{action}` zeigt eine Replikationsaktion an

   * `{path}` gibt einen Pfad an

  Sie werden durch den für die Anforderungen relevanten Pfad bzw. die relevante Aktion ersetzt und müssen deshalb nicht fest codiert sein:

  >[!NOTE]
  >
  >Wenn Sie AEM in einem anderen als dem empfohlenen Standardkontext installiert haben, müssen Sie den Kontext in den HTTP-Kopfzeilen registrieren. Beispiel:
  >`CQ-Handle:/<*yourContext*>{path}`

* **Verbindung schließen**

  Aktivieren Sie diese Option, damit Sie die Verbindung nach jeder Anfrage schließen können.

* **Verbindungs-Zeitüberschreitung**

  Anzuwendende Zeitüberschreitung (in Millisekunden) beim Versuch, eine Verbindung herzustellen.

* **Socket-Zeitüberschreitung**

  Anzuwendende Zeitüberschreitung (in Millisekunden) beim Warten auf Traffic nach dem Herstellen einer Verbindung.

* **Protokollversion**

  Die Version des Protokolls, z. B. `1.0` für HTTP/1.0.

#### Auslöser {#triggers}

Diese Einstellungen werden verwendet, um Auslöser für die automatisierte Replikation zu definieren:

* **Standard ignorieren**

  Ist diese Option aktiviert, wird der Agent von der Standardreplikation ausgeschlossen, d. h., er wird nicht verwendet, wenn eine Inhaltsautorin oder ein Inhaltsautor eine Replikationsaktion ausführt.

* **Bei Modifizierung**

  Hiermit wird automatisch eine Replikation durch diesen Agenten ausgelöst, wenn eine Seite geändert wird. Diese Einstellung wird für Dispatcher Flush-Agenten verwendet, aber auch für die Rückwärtsreplikation.

* **Bei Verteilung**

  Ist diese Option aktiviert, repliziert der Agent automatisch alle zur Verteilung markierten Inhalte, wenn diese geändert werden.

* **Einschaltzeit/Ausschaltzeit erreicht**

  Diese Einstellung löst eine automatische Replikation aus (um eine Seite ggf. zu aktivieren oder zu deaktivieren), wenn die für die Seite definierten Ein- oder Ausschaltzeiten erreicht werden. Sie wird hauptsächlich für Dispatcher Flush-Agenten verwendet.

* **Auf Empfang**

  Ist diese Option aktiviert, führt der Agent beim Erhalt von Replikationsereignissen eine Kettenreplizierung durch.

* **Keine Statusaktualisierung**

  Ist diese Option aktiviert, erzwingt der Agent keine Aktualisierung des Replikationsstatus.

* **Keine Versionierung**

  Ist diese Option aktiviert, erzwingt der Agent keine Versionierung aktivierter Seiten.

## Konfigurieren von Replikationsagenten {#configuring-your-replication-agents}

Weitere Informationen zum Verbinden von Replikationsagenten mit der Veröffentlichungsinstanz über MSSL finden Sie unter [Replizieren mit bidirektionaler SSL-Kommunikation](/help/sites-deploying/mssl-replication.md).

### Konfigurieren der Replikationsagenten über die Autorenumgebung {#configuring-your-replication-agents-from-the-author-environment}

Auf der Registerkarte „Tools“ der Autorenumgebung können Sie Replikationsagenten konfigurieren, die sich in der Autorenumgebung (**Agenten für Autor**) oder der Veröffentlichungsumgebung (**Agenten bei Veröffentlichung**) befinden. Das nachfolgende Verfahren zeigt das Konfigurieren eines Agenten für die Autorenumgebung. Es kann jedoch für beide Umgebungen verwendet werden.

>[!NOTE]
>
>Wenn ein Dispatcher HTTP-Anfragen für Autoren- oder Veröffentlichungsinstanzen verarbeitet, muss die HTTP-Anfrage vom Replikationsagenten den Header „PATH“ enthalten. Zusätzlich zur nachfolgenden Vorgehensweise müssen Sie den Header „PATH“ zur Dispatcher-Liste der Client-Header hinzufügen. Weitere Informationen finden Sie unter [/clientheaders (Client-Header)](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#specifying-the-http-headers-to-pass-through-clientheaders).
>

1. Greifen Sie auf die Registerkarte **Tools** in AEM zu.
1. Klicken Sie auf **Replikation** (linker Bereich), um den Ordner zu öffnen.
1. Doppelklicken Sie auf **Agenten für Autor** (linker oder rechter Bereich).
1. Klicken Sie auf den jeweiligen Agentennamen (der als Link dargestellt ist), um detaillierte Informationen zu diesem Agenten anzuzeigen.
1. Klicken Sie auf **Bearbeiten**, damit das Konfigurationsdialogfeld geöffnet wird:

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Die angegebenen Werte sollten für eine Standardinstallation ausreichend sein. Wenn Sie Änderungen vornehmen, klicken Sie auf **OK**, um diese zu speichern. (Weitere Informationen zu den einzelnen Parametern finden Sie unter [Replikationsagenten – Konfigurationsparameter](#replication-agents-configuration-parameters).)

>[!NOTE]
>
>Bei einer Standardinstallation von AEM wird `admin` als Benutzerin oder Benutzer für die Transport-Anmeldedaten in den Standard-Replikationsagenten angegeben.
>
>Diese Angabe muss in ein Site-spezifisches Benutzerkonto für die Replikation geändert werden, das über Berechtigung zum Replizieren der erforderlichen Pfade verfügt.

### Konfigurieren der Rückwärtsreplikation {#configuring-reverse-replication}

Die Rückwärtsreplikation dient dazu, Benutzerinhalte abzurufen, die in einer Veröffentlichungsinstanz generiert wurden, und sie an die Autoreninstanz zurückzuleiten. Diese Art der Replikation wird im Allgemeinen für Funktionen wie Umfrage- und Registrierungsformulare verwendet.

Aus Sicherheitsgründen lassen die meisten Netzwerktopologien keine Verbindungen *aus* der „demilitarisierten Zone“ (DMZ) zu (ein Subnetzwerk, das externe Dienste für ein nicht vertrauenswürdiges Netzwerk wie das Internet bereitstellt).

Da sich die Veröffentlichungsumgebung in der Regel in der DMZ befindet, muss eine Verbindung von der Autoreninstanz aus initiiert werden, um Inhalte an die Autorenumgebung zurückzuleiten. Dies geschieht mithilfe:

* eines *Postausgangs* in der Veröffentlichungsumgebung, in dem die Inhalte abgelegt werden.
* eines Agenten ( „publish“) in der Autorenumgebung, der den Postausgang regelmäßig hinsichtlich neuer Inhalte abfragt.

>[!NOTE]
>
>Für AEM [Communities](/help/communities/overview.md) wird die Replikation nicht für nutzergenerierte Inhalte in einer Veröffentlichungsinstanz verwendet. Weitere Informationen finden Sie unter [Community-Inhaltsspeicher](/help/communities/working-with-srp.md).

Hierzu benötigen Sie Folgendes:

**Agenten für die Rückwärtsreplikation in der Autorenumgebung**: Dieser dient als aktive Komponente zum Erfassen von Informationen aus dem Postausgang in der Veröffentlichungsumgebung.

Falls Sie die Rückwärtsreplikation nutzen möchten, muss dieser Agent aktiviert sein.

![chlimage_1-23](assets/chlimage_1-23.png)

**Agenten für die Rückwärtsreplikation in der Veröffentlichungsumgebung (ein Postausgang)**: Dieser ist das passive Element, da er als „Postausgang“ fungiert. Benutzereingaben werden hier abgelegt und vom Agenten in der Autorenumgebung abgerufen.

![chlimage_1-1](assets/chlimage_1-1.jpeg)

### Konfigurieren der Replikation für mehrere Veröffentlichungsinstanzen {#configuring-replication-for-multiple-publish-instances}

>[!NOTE]
>
>Nur Inhalte werden repliziert – keine Benutzerdaten (Benutzende, Benutzergruppen und Benutzerprofile).
>
>Um Benutzerdaten in mehreren Veröffentlichungsinstanzen zu synchronisieren, aktivieren Sie die [Benutzersynchronisierung](/help/sites-administering/sync.md).

Nach der Installation ist bereits ein Standardagent für die Replikation von Inhalten in eine Veröffentlichungsinstanz konfiguriert, die auf dem localhost-Port 4503 ausgeführt wird.

Zum Konfigurieren der Replikation von Inhalten für eine weitere Veröffentlichungsinstanz erstellen und konfigurieren Sie einen neuen Replikationsagenten:

1. Öffnen Sie die Registerkarte **Tools** in AEM.
1. Wählen Sie **Replikation** und dann **Agenten für Autor** im linken Bedienfeld aus.
1. Wählen Sie **Neu** aus.
1. Geben Sie den **Titel** und den **Namen** ein und wählen Sie dann **Replikationsagent** aus.
1. Klicken Sie auf **Erstellen**, um einen neuen Agenten zu erstellen.
1. Doppelklicken Sie auf das neue Agentenelement, um das Bedienfeld „Konfiguration“ zu öffnen.
1. Klicken Sie auf **Bearbeiten**. Daraufhin wird das Dialogfeld **Agenteneinstellungen** geöffnet. Der **Anordnungstyp** ist bereits auf „Standard“ gesetzt und diese Einstellung muss beibehalten werden.

   * Führen Sie auf der Registerkarte **Einstellungen** folgende Schritte aus:

      * Aktivieren Sie die Option **Aktiviert**.
      * Geben Sie eine **Beschreibung** ein.
      * Setzen Sie den Wert für **Verzögerung wiederh.** auf `60000`.

      * Behalten Sie für den **Anordnungstyp** die Einstellung `Default` bei.

   * Führen Sie auf der Registerkarte **Transport** folgende Schritte aus:

      * Geben Sie den erforderlichen URI für die neue Veröffentlichungsinstanz ein, z. B. ist
        `https://localhost:4504/bin/receive` möglich.

      * Geben Sie das Site-spezifische Benutzerkonto für die Replikation ein.
      * Die anderen Parameter können nach Bedarf konfiguriert werden.

1. Klicken Sie auf **OK**.

Sie können dann einen Funktionstest durchführen, indem Sie eine Seite in der Autorenumgebung aktualisieren und anschließend veröffentlichen.

Die Aktualisierungen werden in allen Veröffentlichungsinstanzen angezeigt, die wie oben beschrieben konfiguriert wurden.

Falls Probleme auftreten, können Sie die Protokolle der Autoreninstanz überprüfen. Abhängig vom erforderlichen Detaillierungsgrad können Sie die Einstellung für die **Protokollebene** auf `Debug` festlegen. Verwenden Sie hierzu das Dialogfeld **Agenteneinstellungen**, wie oben beschrieben.

>[!NOTE]
>
>Diese Einstellung kann zusammen mit der [Agenten-Benutzer-ID](#agentuserid) verwendet werden, um andere Inhalte für die Replikation in den einzelnen Veröffentlichungsumgebungen auszuwählen. Gehen Sie für jede Veröffentlichungsumgebung wie folgt vor:
>
>1. Konfigurieren Sie einen Replikationsagenten für die Replikation in dieser Veröffentlichungsumgebung.
>1. Konfigurieren Sie ein Benutzerkonto mit den nötigen Zugriffsrechten zum Lesen der Inhalte, die in der spezifischen Veröffentlichungsumgebung repliziert werden.
>1. Weisen Sie das Benutzerkonto als **Agenten-Benutzer-ID** für den Replikationsagenten zu.
>

### Konfigurieren eines Dispatcher Flush-Agenten {#configuring-a-dispatcher-flush-agent}

Die Installation umfasst Standardagenten. Es müssen jedoch trotzdem gewisse Konfigurationen vorgenommen werden. Dies gilt auch, wenn Sie einen neuen Agenten definieren:

1. Öffnen Sie die Registerkarte **Tools** in AEM.
1. Klicken Sie auf **Bereitstellung**.
1. Wählen Sie **Replikation** und dann **Agenten bei Veröffentlichung** aus.
1. Doppelklicken Sie auf das Element **Dispatcher Flush**, um die Übersicht zu öffnen.
1. Klicken Sie auf **Bearbeiten**. Daraufhin wird das Dialogfeld **Agenteneinstellungen** geöffnet:

   * Führen Sie auf der Registerkarte **Einstellungen** folgende Schritte aus:

      * Aktivieren Sie die Option **Aktiviert**.
      * Geben Sie eine **Beschreibung** ein.
      * Behalten Sie als **Anordnungstyp** die Option `Dispatcher Flush` bei oder legen Sie diese Einstellung fest, wenn Sie einen neuen Agenten erstellen.

      * (Optional) Wählen Sie **Alias-Aktualisierung** aus, um Invalidierungsanforderungen an den Dispatcher für Alias- oder Vanity-Pfade zu aktivieren.

   * Führen Sie auf der Registerkarte **Transport** folgende Schritte aus:

      * Geben Sie den erforderlichen URI für die neue Veröffentlichungsinstanz ein, z. B. ist
        `https://localhost:80/dispatcher/invalidate.cache` möglich.

      * Geben Sie das Site-spezifische Benutzerkonto für die Replikation ein.
      * Die anderen Parameter können nach Bedarf konfiguriert werden.

   Für Dispatcher Flush-Agenten wird die URI-Eigenschaft nur verwendet, wenn Sie pfadbasierte „VirtualHost“-Einträge nutzen, um zwischen Farmen zu unterscheiden. Dieses Feld dient dazu, die zu invalidierende Farm anzugeben. Beispiel: Farm 1 hat den virtuellen Host `www.mysite.com/path1/*` und Farm 2 den virtuellen Host `www.mysite.com/path2/*`. Mit der URL `/path1/invalidate.cache` können Sie die erste Farm und mit `/path2/invalidate.cache` die zweite Farm bestimmen.

   >[!NOTE]
   >
   >Wenn Sie AEM in einem anderen als dem empfohlenen Standardkontext installiert haben, konfigurieren Sie auf der Registerkarte **Erweitert** die [HTTP-Kopfzeilen](#extended).

1. Klicken Sie auf **OK**.
1. Kehren Sie zur Registerkarte **Tools** zurück. Dort können Sie den Agenten **Dispatcher Flush** (**Agenten bei Veröffentlichung**) **aktivieren**.

In der Autorenumgebung ist der Replikationsagent **Dispatcher Flush** nicht aktiv. In der Veröffentlichungsumgebung können Sie mit dem entsprechenden URI auf dieselbe Seite zugreifen, z. B. `https://localhost:4503/etc/replication/agents.publish/flush.html`.

### Steuern des Zugriffs auf Replikationsagenten {#controlling-access-to-replication-agents}

Der Zugriff auf die Seiten zum Konfigurieren der Replikationsagenten kann mithilfe von Berechtigungen für Benutzer- und/oder Gruppenseiten auf dem Knoten `etc/replication` gesteuert werden.

>[!NOTE]
>
>Das Festlegen dieser Berechtigungen hat keine Auswirkungen auf Benutzende, die Inhalte replizieren (z. B. über die Websites-Konsole oder die Sidekick-Option). Das Replikations-Framework verwendet keine Benutzersitzung des aktuellen Benutzers, um beim Replizieren von Seiten auf Replikationsagenten zuzugreifen.

### Konfigurieren der Replikationsagenten mit CRXDE Lite {#configuring-your-replication-agents-from-crxde-lite}

>[!NOTE]
>
>Die Erstellung von Replikationsagenten wird nur im Repository-Speicherort `/etc/replication` unterstützt. Dies ist erforderlich, damit die zugehörigen ACLs ordnungsgemäß verarbeitet werden können. Das Erstellen eines Replikationsagenten an einem anderen Speicherort der Baumstruktur kann zu nicht autorisiertem Zugriff führen.

Mit CRXDE Lite können verschiedene Parameter der Replikationsagenten konfiguriert werden.

Navigieren Sie zu `/etc/replication`, um die drei folgenden Knoten anzuzeigen:

* `agents.author`
* `agents.publish`
* `treeactivation`

Die beiden `agents`-Elemente beinhalten Konfigurationsinformationen über die entsprechende Umgebung und sind nur aktiv, wenn diese Umgebung ausgeführt wird. Beispielsweise wird `agents.publish` nur in der Veröffentlichungsumgebung verwendet. Der nachfolgende Screenshot zeigt den Veröffentlichungsagenten der Autorenumgebung, der im Lieferumfang von AEM WCM enthalten ist:

![chlimage_1-24](assets/chlimage_1-24.png)

## Überwachen der Replikationsagenten {#monitoring-your-replication-agents}

So überwachen Sie einen Replikationsagenten:

1. Greifen Sie auf die Registerkarte **Tools** in AEM zu.
1. Klicken Sie auf **Replikation**.
1. Doppelklicken Sie auf den Link zu Agenten für die entsprechende Umgebung (entweder im linken oder im rechten Bereich), z. B. **Agenten für Autor**.

   Das daraufhin eingeblendete Fenster zeigt eine Übersicht über alle Replikationsagenten für die Autorenumgebung, einschließlich ihres Ziels und Status.

1. Klicken Sie auf den Link mit dem entsprechenden Agentennamen, um detaillierte Informationen zu diesem Agenten anzuzeigen:

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

   Hier haben Sie folgende Möglichkeiten:

   * Überprüfen, ob der Agent aktiviert ist.
   * Anzeige der Zielgruppe jeder Replikation.
   * Überprüfen, ob die Replikations-Warteschlange aktiv (aktiviert) ist.
   * Überprüfen, ob sich Elemente in der Warteschlange befinden.
   * **Aktualisieren** oder **Löschen**, um die Anzeige der Warteschlangeneinträge zu aktualisieren. Dadurch können Sie Elemente sehen, die in die Warteschlange gelangen oder diese wieder verlassen.

   * **Protokoll anzeigen**, um auf das Protokoll jeder Aktion des Replikationsagenten zuzugreifen.
   * **Testen der Verbindung** mit der Zielinstanz.
   * **Erzwingen einer Wiederholung** für alle Warteschlangenelemente bei Bedarf.

   >[!CAUTION]
   >
   >Verwenden Sie nicht den Link „Verbindung testen“ für den Postausgang „Rückwärtsreplikation“ in einer Veröffentlichungsinstanz.
   >
   >
   >Falls ein Replikationstest für eine Warteschlange in einem Postausgang durchgeführt wird, werden Elemente, die älter als die Testreplikation sind, bei jeder Rückwärtsreplikation erneut verarbeitet.
   >
   >
   >Falls solche Elemente in einer Warteschlange vorliegen, können Sie sie mit der folgenden XPath-JCR-Abfrage suchen und entfernen.
   >
   >
   >`/jcr:root/var/replication/outbox//*[@cq:repActionType='TEST']`

## Batch-Replikation {#batch-replication}

Die Batch-Replikation repliziert keine einzelnen Seiten oder Assets, sondern wartet darauf, dass der erste Schwellenwert der beiden ausgelöst wird, basierend auf Zeit oder Größe.

Anschließend werden alle Replikationselemente in einem Paket zusammengefasst, das dann als einzelne Datei in die Veröffentlichungsinstanz repliziert wird.

Dort werden alle Elemente entpackt, gespeichert und der Autoreninstanz gemeldet.

### Konfigurieren der Batch-Replikation {#configuring-batch-replication}

1. Wechseln Sie zu `http://serveraddress:serverport/siteadmin`.
1. Wählen Sie oben auf dem Bildschirm das Symbol **[!UICONTROL Tools]** aus.
1. Navigieren Sie in der linken Navigationsleiste zu **[!UICONTROL Replikation – Agenten für Autor]** und doppelklicken Sie auf **[!UICONTROL Standardagent]**.
   * Sie können den Standardagenten für die Veröffentlichungsreplikation auch aufrufen, indem Sie direkt zu `http://serveraddress:serverport/etc/replication/agents.author/publish.html` wechseln
1. Wählen Sie die Schaltfläche **[!UICONTROL Bearbeiten]** oberhalb der Replikationswarteschlange.
1. Rufen Sie im folgenden Fenster die Registerkarte **[!UICONTROL Batch]** auf:
   ![Batch-Replikation](assets/batchreplication.png)
1. Konfigurieren Sie den Agenten.

### Parameter {#parameters}

* `[!UICONTROL Enable Batch Mode]`: Aktivierung oder Deaktivierung des Batch-Replikationsmodus
* `[!UICONTROL Max Wait Time]`: Maximale Wartezeit bis zum Start einer Batch-Anforderung in Sekunden. Der Standardwert ist 2 Sekunden.
* `[!UICONTROL Trigger Size]`: Start der Batch-Replikation bei dieser Größenbeschränkung

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zur Fehlerbehebung finden Sie unter [Fehlerbehebung bei der Replikation](/help/sites-deploying/troubleshoot-rep.md).
