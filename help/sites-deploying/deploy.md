---
title: Bereitstellen und Verwalten
description: Erfahren Sie, wie Sie mit der AEM-Installation beginnen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
exl-id: 3df0662a-0768-4b56-8b94-c517657b4bd9
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1792'
ht-degree: 100%

---

# Bereitstellen und Verwalten {#deploying-and-maintaining}

Inhalt dieser Seite:

* [Grundlegende Konzepte](#basic-concepts)

   * [Was ist AEM?](#what-is-aem)
   * [Typische Bereitstellungen](#typical-deployment-scenarios)

      * [On-Premise](#on-premise)
      * [Managed Services mit Cloud Manager](#managed-services-using-cloud-manager)

* [Erste Schritte](#getting-started)

   * [Voraussetzungen](#prerequisites)
   * [Abrufen der Software](#getting-the-software)
   * [Standardmäßige lokale Installation](#default-local-install)
   * [Installation von Erstellungs- und Veröffentlichungsinstanzen](#author-and-publish-installs)
   * [Entpacktes Installationsverzeichnis](#unpacked-install-directory)
   * [Starten und Anhalten](#starting-and-stopping)

Nachdem Sie sich mit diesen Grundlagen vertraut gemacht haben, finden Sie auf den folgenden Unterseiten komplexere und ausführlichere Informationen:

* [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)
* [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md)
* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Anwendungsserver-Installation](/help/sites-deploying/application-server-install.md)
* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)
* [Konfiguration](/help/sites-deploying/configuring.md)
* [Aktualisieren auf AEM 6.5](/help/sites-deploying/upgrade.md)
* [E-Commerce](/help/commerce/cif-classic/deploying/ecommerce.md)
* [Artikel mit Anleitungen für die Konfiguration](/help/sites-deploying/ht-deploy.md)
* [Web-Konsole](/help/sites-deploying/web-console.md)
* [Fehlerbehebung bei Replikationsproblemen](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Bereitstellen von Communities](/help/communities/deploy-communities.md)
* [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md)
* [Leistungsrichtlinien](/help/sites-deploying/performance-guidelines.md)
* [Erste Schritte mit AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Was ist AEM Screens? ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html?lang=de)

## Grundlegende Konzepte {#basic-concepts}

### Was ist AEM? {#what-is-aem}

Adobe Experience Manager ist ein Web-basiertes Client-Server-System für das Erstellen, Verwalten und Bereitstellen von kommerziellen Websites und zugehörigen Services. Es kombiniert mehrere Funktionen auf Infrastrukturebene und Anwendungsebene in einem einzelnen integrierten Paket.

Auf Infrastrukturebene bietet AEM Folgendes:

* **Web-Anwendungs-Server**: AEM kann im eigenständigen Modus (es umfasst einen integrierten Jetty-Webserver) oder als Web-Anwendung innerhalb eines Anwendungs-Servers eines Drittanbieters bereitgestellt werden.
* **Web-Anwendungs-Framework**: AEM beinhaltet das Sling-Web-Anwendungs-Framework, das das Schreiben von RESTful-Web-Anwendungen vereinfacht.
* **Content-Repository**: AEM enthält ein Java Content™ Repository (JCR), eine Art hierarchische Datenbank, die speziell für unstrukturierte und teilstrukturierte Daten entwickelt wurde. Das Repository speichert nicht nur den für die Benutzenden sichtbaren Inhalt, sondern auch den gesamten Code, die Vorlagen und die internen Daten, die von der Anwendung verwendet werden.

Auf dieser Grundlage bietet AEM einige Funktionen auf Anwendungsebene für die Verwaltung von:

* **Websites**
* **Mobile Apps**
* **Digitalen Veröffentlichungen**
* **Formulare und Dokumente**
* **Digitale Assets**
* **Communities**
* **Online-Commerce**

Schließlich können Kundinnen und Kunden diese Bausteine auf Infrastruktur- und Anwendungsebene nutzen, um individuelle Lösungen zu erstellen, indem sie eigene Anwendungen entwickeln.

Der AEM-Server ist **Java-basiert** und kann auf den meisten Betriebssystemen ausgeführt werden, die diese Plattform unterstützen. Die gesamte Client-Interaktion mit AEM erfolgt über einen **Webbrowser**.

>[!NOTE]
>
>Die Funktion „Adaptive Formulare“, verfügbar im AEM 6.5-Schnellstart, dient nur zu Kennenlern- und Evaluierungszwecken.  Für die Verwendung in der Produktion muss eine gültige Lizenz für AEM Forms erworben werden, da für die Funktion „Adaptive Formulare“ eine Lizenzierung erforderlich ist.

### Typische Bereitstellungsszenarien {#typical-deployment-scenarios}

In der Terminologie von AEM entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server ausgeführt wird. AEM-Installationen betreffen in der Regel mindestens zwei Instanzen, die normalerweise auf separaten Computern ausgeführt werden:

* **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
* **Publish**: Eine AEM-Instanz, die den Inhalt veröffentlicht.

Diese Instanzen sind hinsichtlich der installierten Software identisch. Sie unterscheiden sich nur in Bezug auf ihre Konfiguration. Darüber hinaus verwenden die meisten Installationen einen Dispatcher:

* **Dispatcher**: Ein mit dem AEM-Dispatcher-Modul angereicherter statischer Webserver (Apache httpd, Microsoft® IIS).  Er speichert die durch die Veröffentlichungsinstanz generierten Web-Seiten zwischen, um die Leistung zu verbessern.

Es gibt viele erweiterte Optionen und Ausarbeitungen dieses Setups, aber das grundlegende Muster von Author, Publish und Dispatcher bildet den Kern der meisten Bereitstellungen. Zunächst konzentrieren wir uns auf ein einfaches Setup.  Die Erläuterung der erweiterten Bereitstellungsoptionen folgt.

In den folgenden Abschnitten werden beide Szenarien beschrieben:

* **On-Premise**: AEM in Ihrer Unternehmensumgebung bereitgestellt und verwaltet.

* **Managed Services – Cloud-Manager für Adobe Experience Manager**: AEM von Adobe Managed Services bereitgestellt und verwaltet.

### On-Premise {#on-premise}

Sie können AEM auf Servern in Ihrer Unternehmensumgebung installieren. Typische Installationsinstanzen umfassen: Bereitstellungs-, Test- und Veröffentlichungsumgebungen. Unter [Erste Schritte](/help/sites-deploying/deploy.md#getting%20started) finden Sie grundlegende Informationen darüber, wie Sie die AEM-Software erhalten, um sie lokal zu installieren.

Weitere Informationen zu typischen On-Premise-Bereitstellungen erhalten Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md).

### Managed Services mit Cloud Manager {#managed-services-using-cloud-manager}

AEM Managed Services ist eine Komplettlösung für das Management digitaler Erlebnisse. Sie bietet die Vorteile einer Lösung zur Erlebnisbereitstellung in der Cloud unter Beibehaltung aller Vorteile hinsichtlich Kontrolle, Sicherheit und Personalisierung einer On-Premise-Bereitstellung. AEM Managed Services ermöglicht Kunden schnellere Launches, indem sie in der Cloud bereitstellen und dabei auf die Best Practices und die Unterstützung von Adobe vertrauen können. Unternehmen und Anwenderinnen bzw. Anwender im Geschäftsbereich können Kundinnen und Kunden in kürzester Zeit ansprechen, Marktanteile steigern und sich auf die Erstellung innovativer Marketing-Kampagnen konzentrieren, während die IT-Abteilung entlastet wird.

Mit AEM Managed Services können Kundinnen und Kunden die folgenden Vorteile erzielen:

**Schnellere Markteinführungszeiten:** Dank der flexiblen Cloud-Infrastruktur von Adobe Managed Services können Organisationen erfolgreiche digitale Erlebnisse schnell planen, starten und optimieren. Adobe verwaltet die Cloud-Architektur, ohne dass zusätzliches Kapital, Hardware oder Software erforderlich ist. Die Adobe-Fachleute für Kundenlösungen helfen bei der AEM-Architektur, der Bereitstellung, der Anpassung für die Verbindung mit Back-End-Anwendungen und den Best Practices für die Inbetriebnahme.

**Höhere Leistung:** Bietet zuverlässige digitale Erlebnisse für Ihr Unternehmen mit vier Service-Verfügbarkeitsoptionen: 99,5 %, 99,9 %, 99,95 % und 99,99 %. Außerdem ermöglicht es eine automatische Sicherung und Modelle zur Multimodus-Notfallwiederherstellung und hilft so, Sicherheit und kontinuierliche Verwaltung sicherzustellen.

**Optimierte IT-Kosten:** Proaktive Unterstützung und Know-how helfen Unternehmen, über neue Entwicklungen von AEM auf dem Laufenden zu bleiben. Adobe Platinum Maintenance und Support ist bei neuen Bereitstellungen von AMS Enterprise/Basic automatisch enthalten und bietet technisches Know-how und operative Erfahrung, um Unternehmen bei der Verwaltung ihrer unternehmenskritischen Anwendungen zu helfen. Kostenlose grundlegende Analytics- oder Target-Funktionen bieten zusätzlichen Mehrwert für mittelständische Unternehmen mit begrenztem Bedarf hinsichtlich Analysen und Personalisierung.

**Oberste Sicherheit:** Stellt physische, Netzwerk- und Datensicherheit auf Unternehmensniveau sicher, indem Kunden-Applikationen in einer Einrichtung mit beschränktem Zugang, hinter Firewall-Systemen oder in einer virtuellen, privaten Cloud, gehostet werden. Es beinhaltet virtuelle Maschinen für Einzelmandanten mit robuster Datenspeicherverschlüsselung, Virenschutz und Datenisolierung.

**Cloud Manager**: Cloud Manager, Teil von Adobe Experience Manager Managed Services, bietet ein Selbstbedienungsportal, das es Organisationen besser ermöglicht, Adobe Experience Manager in der Cloud selbst zu verwalten. Es enthält eine moderne kontinuierliche Integration und eine kontinuierliche Bereitstellungs-Pipeline (CI/CD), die IT-Teams und Implementierungspartner dazu nutzen können, die Geschwindigkeit der Lieferung von Personalisierungen oder Aktualisierungen zu erhöhen, ohne bei der Leistung oder Sicherheit Abstriche zu machen. Cloud Manager ist nur für Kundinnen und Kunden von Adobe Managed Services verfügbar.

Weitere Informationen zu Cloud Manager und den zugehörigen Ressourcen finden Sie im [**Benutzerhandbuch zu Cloud Manager**](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=de).

## Erste Schritte {#getting-started}

### Voraussetzungen {#prerequisites}

Während Produktionsinstanzen für gewöhnlich auf dedizierten Computern ausgeführt werden, auf denen wiederum offiziell unterstützte Betriebssysteme ausgeführt werden (siehe [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)), kann der Experience Manager-Server tatsächlich auf jedem System ausgeführt werden, das [**Java™ Standard Edition 8**](https://www.oracle.com/java/technologies/downloads/#java8) unterstützt.

Um sich mit AEM vertraut zu machen bzw. um die Entwicklung auf AEM vorzunehmen, wird häufig eine auf Ihrem lokalen Computer installierte Instanz verwendet, auf der Apple OS X oder Desktop-Versionen von Microsoft® Windows oder Linux® ausgeführt werden.

Client-seitig funktioniert AEM mit allen modernen Browsern (**Microsoft® Edge**, **Internet Explorer** 11, **Chrome **51+** **, Firefox **47+, **Safari** 8+) unter Desktop- und Tablet-Betriebssystemen. Details finden Sie unter [Unterstützte Clientplattformen](/help/sites-deploying/technical-requirements.md#supported-client-platforms).

### Abrufen der Software {#getting-the-software}

Kunden mit einem gültigen Wartungs- und Supportvertrag sollten eine E-Mail-Benachrichtigung mit einem Code erhalten haben und in der Lage sein, AEM über die [**Adobe-Lizenzierungswebsite**](https://licensing.adobe.com/) herunterzuladen. Geschäftspartner können den Downloadzugriff über [**spphelp@adobe.com**](mailto:spphelp@adobe.com) anfordern.

Das AEM-Software-Paket steht in zwei Formen zur Verfügung:

* **cq-quickstart-6.5.0.jar:** Eine eigenständige, ausführbare *JAR*-Datei, die alles enthält, was für die Einrichtung und Ausführung benötigt wird.

* **cq-quickstart-6.5.0.war:** Eine *WAR*-Datei für die Bereitstellung auf dem Anwendungsserver eines Drittanbieters.

Im folgenden Abschnitt wird die **eigenständige Installation** beschrieben. Weitere Informationen zum Installieren von AEM auf einem Anwendungs-Server finden Sie unter [Anwendungs-Server-Installation](/help/sites-deploying/application-server-install.md).

### Standardmäßige lokale Installation {#default-local-install}

1. Erstellen Sie auf Ihrem lokalen Computer ein Installationsverzeichnis. Beispiel:

   UNIX®-Installationsspeicherort: **/opt/aem**

   Windows-Installationsspeicherort: **`C:\Program Files\aem`**

   Ebenso ist es üblich, Beispielinstanzen in einem Ordner direkt auf dem Desktop zu installieren. In jedem Fall wird bei Adobe dieser Speicherort meist wie folgt bezeichnet:

   `<aem-install>`

   *Der Pfad des Dateiverzeichnisses darf nur aus US-ASCII-Zeichen bestehen.*

1. Platzieren Sie die **jar**- und **license**-Dateien in diesem Verzeichnis:

   ```shell
   <aem-install>/
       cq-quickstart-6.5.0.jar
       license.properties
   ```

   Wenn Sie keine Datei `license.properties` bereitstellen, leitet AEM Ihren Browser beim Start zu einem **Begrüßungsbildschirm** um, wo Sie Ihren Lizenzschlüssel eingeben können. Sie müssen einen gültigen Lizenzschlüssel von Adobe anfordern, wenn Sie noch nicht über einen verfügen.

1. Doppelklicken Sie zum Starten der Instanz in einer GUI-Umgebung einfach auf die Datei **`cq-quickstart-6.5.0.jar`**.

   Alternativ können Sie AEM über die Befehlszeile starten:

   ```shell
       java -Xmx1024M -jar cq-quickstart-6.5.0.jar
   ```

AEM braucht ein paar Minuten, um die JAR-Datei zu entpacken, sich selbst zu installieren und zu starten. Das obige Verfahren führt zu:

* einer **AEM author**-Instanz,
* die auf **localhost**
* auf Port **4502** ausgeführt wird

Lassen Sie Ihren Browser für den Zugriff auf die Instanz auf die folgende URL verweisen:

**`https://localhost:4502`**

Das Ergebnis in der Erstellungsinstanz wird automatisch so konfiguriert, dass eine Verbindung zu einer **Veröffentlichungsinstanz** auf **`localhost:4503`** hergestellt wird.

### Installation von Erstellungs- und Veröffentlichungsinstanzen {#author-and-publish-installs}

Die Standardinstallation (eine **author**-Instanz auf **`localhost:4502`**) kann einfach durch das Umbenennen der `jar`-Datei geändert werden, bevor sie das erste Mal gestartet wird. Das Benennungsmuster lautet:

**`cq-<instance-type>-p<port-number>.jar`**

So führt beispielsweise das Umbenennen der Datei zu

**`cq-author-p4502.jar`**

und das Starten dieser Datei zu einer Autoreninstanz, die auf **`localhost:4502`** ausgeführt wird.

Ähnlich verhält es sich beim Umbenennen und Starten der Datei

**`cq-publish-p4503.jar`**

Dies führt zu einer Veröffentlichungsinstanz, die auf **`localhost:4503`** ausgeführt wird.

Diese zwei Instanzen würden Sie beispielsweise installieren in:

`<aem-install>/author`und

**`<aem-install>/publish`**

Weitere Informationen über das Anpassen Ihrer Installation finden Sie unter:

* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md)

### Entpacktes Installationsverzeichnis {#unpacked-install-directory}

Wenn die JAR-Datei für den Schnellstart erstmals gestartet wird, entpackt sie sich selbst im selben Verzeichnis unter einem neuen Unterverzeichnis mit dem Namen `crx-quickstart`. Sie müssen über Folgendes verfügen:

```xml
<aem-install>/
    license.properties
    cq-quickstart-6.5.0.jar
    crx-quickstart/
        app/
        bin/
        conf/
        launchpad/
        logs/
        metrics/
        monitoring/
        opt/
        repository/
        threaddumps/
        eula-de_DE.html
        eula-en_US.html
        eula-fr_FR.html
        eula-ja_JP.html
        readme.txt
```

Wenn die Instanz über die Benutzeroberfläche installiert wurde, werden automatisch ein Browser-Fenster und ein Desktop-Anwendungsfenster geöffnet, in denen der Host und Port der Instanz sowie ein Ein-/Aus-Schalter angezeigt werden:

![Startbildschirm](assets/screen_shot_.png)

>[!NOTE]
>
>Wenn Sie Symlinks verwenden, sehen Sie sich den Artikel [Probleme mit Symlink](https://helpx.adobe.com/de/experience-manager/kb/changing-symlink.html) an.

### Starten und Anhalten {#starting-and-stopping}

Nachdem sich AEM selbst entpackt und erstmals gestartet hat, lässt sich die Instanz durch einfaches Doppelklicken auf die JAR-Datei im Installationsverzeichnis starten. Sie wird dadurch nicht erneut installiert.

Um die Instanz über die grafische Benutzeroberfläche zu stoppen, klicken Sie einfach auf den **Ein-/Aus**-Schalter im Fenster der Desktop-Anwendung.

Sie können AEM auch über die Befehlszeile anhalten und starten. Angenommen, Sie haben die Instanz bereits erstmalig installiert, dann befinden sich die **Befehlszeilenskripte** hier:

**`<aem-install>/crx-quickstart/bin/`**

Dieser Ordner enthält die folgenden Unix®-Bash-Shell-Skripte:

* **`start`**: Startet die Instanz
* `stop`: Hält die Instanz an
* **`status`**: Meldet den Status der Instanz
* **`quickstart`**: Wird bei Bedarf zum Konfigurieren der Startinformationen verwendet

Es stehen auch entsprechende **`bat`**-Dateien für Windows zur Verfügung. Detaillierte Informationen finden Sie in:

* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)

AEM startet und leitet Ihren Webbrowser automatisch zur entsprechenden Seite um. Für gewöhnlich handelt es sich um die Anmeldeseite, beispielsweise:

`https://localhost:4502/`

![Anmeldebildschirm](assets/screen_shot_2019-04-08at83533am.png)

Nach der Anmeldung haben Sie Zugriff auf AEM. Weitere Informationen finden Sie je nach Ihrer Rolle hier:

* [Authoring –](/help/sites-authoring/first-steps.md)
* [Verwalten](/help/sites-administering/home.md)
* [Entwickeln](/help/sites-developing/getting-started.md)
* [Verwaltung](/help/managing/best-practices.md)

## Erweiterte Bereitstellung {#advanced-deployment}

Der obige Abschnitt sollte Ihnen ein gutes Verständnis der Grundlagen zur AEM-Installation vermitteln. Die Installation eines vollständigen Produktionssystems von AEM kann jedoch erheblich komplexer sein. In den folgenden Unterseiten wird die erweiterte Installation vollständig abgedeckt:

* [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)
* [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md)
* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Anwendungsserver-Installation](/help/sites-deploying/application-server-install.md)
* [Fehlerbehebung](/help/sites-deploying/troubleshooting.md)
* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)
* [Konfiguration](/help/sites-deploying/configuring.md)
* [Aktualisieren auf AEM 6.5](/help/sites-deploying/upgrade.md)
* [E-Commerce](/help/commerce/cif-classic/deploying/ecommerce.md)
* [Artikel mit Anleitungen für die Konfiguration](/help/sites-deploying/ht-deploy.md)
* [Web-Konsole](/help/sites-deploying/web-console.md)
* [Fehlerbehebung bei Replikationsproblemen](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Bereitstellen von Communities](/help/communities/deploy-communities.md)
* [Einführung in die AEM-Plattform](/help/sites-deploying/platform.md)
* [Leistungsrichtlinien](/help/sites-deploying/performance-guidelines.md)
* [Erste Schritte mit AEM Mobile](/help/mobile/getting-started-aem-mobile.md)
* [Was ist AEM Screens? ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html?lang=de)
