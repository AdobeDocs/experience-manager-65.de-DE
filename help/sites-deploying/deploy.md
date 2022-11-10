---
title: Bereitstellen und Verwalten
seo-title: Deploying and Maintaining
description: Informationen zu den ersten Schritten der AEM-Installation
seo-description: Learn how to get started with the AEM installation.
uuid: 4429ac4d-abd7-47d8-b19d-773accb7cc7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: e48cc0ed-688c-44c8-b6d6-5f3c8593a295
docset: aem65
exl-id: 3df0662a-0768-4b56-8b94-c517657b4bd9
source-git-commit: 63f066013c34a5994e2c6a534d88db0c464cc905
workflow-type: tm+mt
source-wordcount: '1802'
ht-degree: 99%

---

# Bereitstellen und Verwalten{#deploying-and-maintaining}

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

Adobe Experience Manager ist ein webbasiertes Client-Server-System für das Erstellen, Verwalten und Bereitstellen von kommerziellen Websites und zugehörigen Diensten. Es kombiniert einige Funktionen auf Infrastrukturebene und Anwendungsebene in einem einzelnen integrierten Paket.

Auf Infrastrukturebene bietet AEM Folgendes:

* **Webanwendungsserver**: AEM kann im eigenständigen Modus (umfasst einen Intergated-Jetty-Webserver) oder als eine Webanwendung auf einem Drittanbieter-Anwendungsserver bereitgestellt werden.
* **Framework für Webanwendungen**: AEM verfügt über das Sling Web Application Framework (Sling-Webanwendungsframework). Dieses vereinfacht das Schreiben von RESTful- und inhaltsorientierten Webanwendungen.
* **Inhalts-Repository**: AEM umfasst ein Java Content Repository (JCR). Hierbei handelt es sich um einen Typ hierarchischer Datenbank, die speziell für unstrukturierte und halb strukturierte Daten entwickelt wurde. Das Repository speichert nicht nur die benutzerseitigen Inhalte, sondern auch alle durch die Anwendung verwendeten Codes, Vorlagen und internen Daten.

Auf dieser Grundlage bietet AEM einige Funktionen auf Anwendungsebene für die Verwaltung von:

* **Websites**
* **Mobilanwendungen**
* **digitalen Veröffentlichungen**
* **Formulare**
* **Digitale Assets**
* **Communities**
* **Online-Handel**

Benutzer können diese Bausteine auf Infrastruktur- und Anwendungsebene schließlich dazu verwenden, um angepasste Lösungen zu erstellen, indem sie ihre eigenen Anwendungen erstellen.

Der AEM-Server ist **Java-basiert** und kann auf den meisten Betriebssystemen ausgeführt werden, die diese Plattform unterstützen. Die gesamte Client-Interaktion mit AEM erfolgt über einen **Webbrowser**.

### Typische Bereitstellungsszenarien {#typical-deployment-scenarios}

In der AEM-Terminologie entspricht eine „Instanz“ einer Kopie von AEM, die auf einem Server ausgeführt wird. AEM-Installationen beziehen für gewöhnlich mindestens zwei Instanzen ein, die normalerweise auf separaten Computern ausgeführt werden:

* **Autor**: Eine zum Erstellen, Hochladen und Bearbeiten von Inhalten sowie zum Verwalten der Website verwendete AEM-Instanz. Sobald der Inhalt für die Veröffentlichung bereit ist, wird er an die Veröffentlichungsinstanz repliziert.
* **Veröffentlichen**: Eine AEM-Instanz, die den Inhalt veröffentlicht.

Diese Instanzen sind hinsichtlich der installierten Software identisch. Sie unterscheiden sich nur in Bezug auf ihre Konfiguration. Zusätzlich verwenden die meisten Installationen einen Dispatcher:

* **Dispatcher**: Ein um das AEM-Dispatcher-Modul erweiterter statischer Webserver (Apache httpd, Microsoft IIS usw.). Er speichert durch die Veröffentlichungsinstanz generierte Web-Seiten zwischen, um die Leistung zu verbessern.

Es gibt viele erweiterte Optionen und Ausarbeitungen dieser Einrichtung. Das allgemeine Muster von „author“ (erstellen), „publish“ (veröffentlichen) und „dispatcher“ befindet sich im Zentrum der meisten Bereitstellungen. Zunächst konzentrieren wir uns auf ein relativ einfaches Setup. Die Erläuterung erweiterter Bereitstellungsoptionen folgt.

Die folgenden Abschnitte beschreiben beide Szenarien:

* **On-Premise**: AEM in Ihrer Unternehmensumgebung bereitgestellt und verwaltet.

* **Verwaltete Dienste - Cloud Manager für Adobe Experience Manager**: AEM von Adobe Managed Services bereitgestellt und verwaltet.

### On-Premise {#on-premise}

Sie können AEM auf Servern in Ihrer Unternehmensumgebung installieren. Typische Installationsinstanzen umfassen: Bereitstellungs-, Test- und Veröffentlichungsumgebungen. Nähere Informationen finden Sie im Abschnitt [Erste Schritte](/help/sites-deploying/deploy.md#getting%20started). Dort erhalten Sie grundlegende Informationen darüber, wie Sie die AEM-Software erhalten, um sie lokal zu installieren.

Weitere Informationen zu typischen On-Premise-Bereitstellungen erhalten Sie unter [Empfohlene Bereitstellungen](/help/sites-deploying/recommended-deploys.md).

### Managed Services mit Cloud Manager {#managed-services-using-cloud-manager}

AEM Managed Services ist eine Komplettlösung für das Management digitaler Erlebnisse. Sie bietet die Vorteile einer Lösung zur Erlebnisbereitstellung in der Cloud unter Beibehaltung aller Vorteile hinsichtlich Kontrolle, Sicherheit und Personalisierung einer On-Premise-Bereitstellung. AEM Managed Services ermöglicht Kunden schnellere Launches, indem sie in der Cloud bereitstellen und dabei auf die Best Practices und die Unterstützung von Adobe vertrauen können. Organisationen und Geschäftskunden können so in kürzester Zeit Kunden ansprechen, den Marktanteil steigern und sich auf innovative Marketing-Kampagnen konzentrieren, wobei die Belastung auf die IT reduziert wird.

Mit AEM Managed Services können Kunden die folgenden Vorteile nutzen:

**Schnellere Markteinführungszeiten:** Dank flexibler Cloud-Infrastruktur von Adobe Managed Services können Organisationen erfolgreiche digitale Erlebnisse schnell planen, starten und optimieren. Adobe verwaltet die Cloud-Architektur ohne zusätzliche Anforderungen an Kapital, Hardware oder Software und die Customer Success Engineers von Adobe helfen bei AEM-Architektur, Bereitstellung, Anpassung zur Verbindung mit Backend-Applikationen und Best Practices bei der Live-Schaltung.

**Höhere Leistung:** Bietet zuverlässige digitale Erlebnisse für Ihr Unternehmen mit vier Service-Verfügbarkeitsoptionen, 99,5 %, 99,9 %, 99,95 % und 99,99 %. Zusätzlich ermöglicht es eine automatische Sicherung und Modelle zur Notfallwiederherstellung und hilft so, Sicherheit und kontinuierliche Verwaltung sicherzustellen.

**Optimierte IT-Kosten:** Proaktive Unterstützung und Know-how helfen Unternehmen, über neue Entwicklungen von AEM auf dem Laufenden zu bleiben. Adobe Platinum Maintenance und Support ist bei neuen Bereitstellungen von AMS Enterprise/Basic automatisch enthalten und bietet technisches Know-how und operative Erfahrung, um Unternehmen bei der Verwaltung ihrer unternehmenskritischen Applikationen zu helfen. Kostenlose grundlegende Analytics- oder Target-Funktionen bieten zusätzlichen Mehrwert für mittelständische Unternehmen mit begrenztem Bedarf hinsichtlich Analysen und Personalisierung.

**Oberste Sicherheit:** Stellt physische, Netzwerk- und Datensicherheit auf Unternehmensniveau sicher, indem Kunden-Applikationen in einer Einrichtung mit beschränktem Zugang, hinter Firewall-Systemen oder in einer virtuellen, privaten Cloud, gehostet werden. Es beinhaltet virtuelle Maschinen für jeden einzelnen Mandanten mit robuster Datenspeicherungsverschlüsselung, Anti-Viren-Programmen und Datenisolierung.

**Cloud Manager**: Cloud Manager, Teil von Adobe Experience Manager Managed Services, bietet ein Selbstbedienungsportal, das es Organisationen besser ermöglicht, Adobe Experience Manager in der Cloud selbst zu verwalten. Es enthält eine moderne kontinuierliche Integration und eine kontinuierliche Bereitstellungs-Pipeline (CI/CD), die IT-Teams und Implementierungspartner dazu nutzen können, die Geschwindigkeit der Lieferung von Personalisierungen oder Aktualisierungen zu erhöhen, ohne bei der Leistung oder Sicherheit Abstriche zu machen. Cloud Manager ist nur für Adobe Managed Service-Kunden verfügbar.

Weitere Informationen zu Cloud Manager und den zugehörigen Ressourcen finden Sie im [**Benutzerhandbuch zu Cloud Manager**](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html).

## Erste Schritte {#getting-started}

### Voraussetzungen {#prerequisites}

Während Produktionsinstanzen für gewöhnlich auf dedizierten Computern ausgeführt werden, auf denen wiederum offiziell unterstützte Betriebssysteme ausgeführt werden (siehe [Technische Anforderungen](/help/sites-deploying/technical-requirements.md)), kann der Experience Manager-Server tatsächlich auf jedem System ausgeführt werden, das [**Java Standard Edition 8**](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) unterstützt.

Um sich mit AEM vertraut zu machen bzw. um die Entwicklung auf AEM vorzunehmen, wird häufig eine auf Ihrem lokalen Computer installierte Instanz verwendet, auf der Apple OS X oder Desktopcomputerversionen von Microsoft Windows oder Linux ausgeführt werden.

Auf der Clientseite funktioniert AEM mit allen modernen Browsern (**Microsoft Edge**, **Internet Explorer** 11, **Chrome **51+****, **Firefox **47+, **Safari** 8+) auf Desktopcomputer- und Tablet-Betriebssystemen. Details finden Sie unter [Unterstützte Clientplattformen](/help/sites-deploying/technical-requirements.md#supported-client-platforms).

### Abrufen der Software {#getting-the-software}

Kunden mit einem gültigen Wartungs- und Supportvertrag sollten eine E-Mail-Benachrichtigung mit einem Code erhalten haben und in der Lage sein, AEM über die [**Adobe-Lizenzierungswebsite**](https://licensing.adobe.com/) herunterzuladen. Geschäftspartner können den Downloadzugriff über [**spphelp@adobe.com**](mailto:spphelp@adobe.com) anfordern.

Das AEM-Softwarepaket steht in zwei Formen zur Verfügung:

* **cq-quickstart-6.5.0.jar:** Eine eigenständige ausführbare *JAR*-Datei, die alles für die Einrichtung und Ausführung enthält.

* **cq-quickstart-6.5.0.war:** Eine *WAR*-Datei für die Bereitstellung auf dem Anwendungsserver eines Drittanbieters.

Im folgenden Abschnitt wird die **eigenständige Installation** beschrieben. Details über das Installieren von AEM auf einem Anwendungsserver finden Sie unter [Applikationsserver-Installation](/help/sites-deploying/application-server-install.md).

### Standardmäßige lokale Installation {#default-local-install}

1. Erstellen Sie ein Installationsverzeichnis auf Ihrem lokalen Computer. Beispiel:

   UNIX-Installationsspeicherort: **/opt/aem**

   Windows-Installationsspeicherort: **`C:\Program Files\aem`**

   Gleichermaßen werden häufig Beispielinstanzen in einem Ordner installiert, der sich direkt auf dem Desktop befindet. Dieser Speicherort wird hier im Allgemeinen wie folgt bezeichnet::

   `<aem-install>`

   *Beachten Sie, dass der Pfad des Dateiverzeichnisses nur aus US ASCII-Zeichen bestehen darf.*

1. Platzieren Sie die **JAR**- und **Lizenz**-Dateien in diesem Verzeichnis:

   ```shell
   <aem-install>/
       cq-quickstart-6.5.0.jar
       license.properties
   ```

   Wenn Sie keine `license.properties`-Datei bereitstellen, leitet AEM Ihren Browser beim Start zu einem **Begrüßungsbildschirm** um, wo Sie Ihren Lizenzschlüssel eingeben können. Sie müssen einen gültigen Lizenzschlüssel von Adobe anfordern, wenn Sie noch nicht über einen verfügen.

1. Doppelklicken Sie zum Starten der Instanz in einer GUI-Umgebung einfach auf die Datei **`cq-quickstart-6.5.0.jar`**.

   Alternativ können Sie AEM an der Befehlszeile starten:

   ```shell
       java -Xmx1024M -jar cq-quickstart-6.5.0.jar
   ```

AEM braucht einige Minuten, um die JAR-Datei zu entpacken, sich selbst zu installieren und zu starten. Die obige Prozedur führt zu Folgendem:

* einer **AEM author**-Instanz,
* die auf **localhost**
* auf Port **4502** ausgeführt wird

Navigieren Sie für den Zugriff auf den Instanzpunkt zu:

**`https://localhost:4502`**

Das Ergebnis in der Erstellungsinstanz wird automatisch so konfiguriert, dass eine Verbindung zu einer **Veröffentlichungsinstanz** auf **`localhost:4503`** hergestellt wird.

### Installation von Erstellungs- und Veröffentlichungsinstanzen {#author-and-publish-installs}

Die Standardinstallation (eine **author**-Instanz auf **`localhost:4502`**) kann einfach durch das Umbenennen der `jar`-Datei geändert werden, bevor sie das erste Mal gestartet wird. Das Benennungsmuster lautet:

**`cq-<instance-type>-p<port-number>.jar`**

So führt beispielsweise das Umbenennen der Datei zu

**`cq-author-p4502.jar`**

und das Starten dieser Datei zu einer „author“-Instanz, die auf **`localhost:4502`** ausgeführt wird.

Ähnlich verhält es sich beim Umbenennen und Starten der Datei

**`cq-publish-p4503.jar`**

Dies führt zu einer „publish“-Instanz, die auf **`localhost:4503`** ausgeführt wird.

Diese zwei Instanzen würden Sie beispielsweise installieren in:

`<aem-install>/author`und

**`<aem-install>/publish`**

Weitere Informationen über das Anpassen Ihrer Installation finden Sie unter:

* [Benutzerdefinierte Standalone-Installation](/help/sites-deploying/custom-standalone-install.md)
* [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md)

### Entpacktes Installationsverzeichnis {#unpacked-install-directory}

Wenn die JAR-Datei für den Schnellstart erstmals gestartet wird, entpackt sie sich selbst im selben Verzeichnis unter einem neuen Unterverzeichnis mit dem Namen `crx-quickstart`. Sie sollten Folgendes erhalten:

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

Wenn die Instanz über die Benutzeroberfläche installiert wurde, werden automatisch ein Browserfenster und ein Desktopanwendungsfenster geöffnet, in denen der Host und Port der Instanz sowie ein Ein-/Aus-Schalter angezeigt werden:

![Startbildschirm](assets/screen_shot_.png)

>[!NOTE]
>
>Wenn Sie symlinks verwenden, lesen Sie auch [Probleme mit symlink](https://helpx.adobe.com/de/experience-manager/kb/changing-symlink.html).

### Starten und Anhalten {#starting-and-stopping}

Nachdem sich AEM selbst entpackt und erstmals gestartet hat, wird die Instanz durch einfaches Doppelklicken auf die JAR-Datei im Installationsverzeichnis gestartet. Es wird hingegen dadurch nicht erneut installiert.

Um die Instanz von der GUI anzuhalten, müssen Sie einfach im Desktopanwendungsfenster auf den **Ein-/Aus**-Schalter klicken.

Sie können AEM auch an der Befehlszeile anhalten und starten. Angenommen, Sie haben die Instanz bereits erstmals installiert, dann befinden sich die **Befehlszeilenskripts** hier:

**`<aem-install>/crx-quickstart/bin/`**

Dieser Ordner enthält die folgenden Unix-Bash-Shell-Skripts:

* **`start`**: Startet die Instanz
* `stop`: Hält die Instanz an
* **`status`**: Meldet den Status der Instanz
* **`quickstart`**: Wird bei Bedarf zum Konfigurieren der Startinformationen verwendet

Es stehen auch entsprechende **`bat`**-Dateien für Windows zur Verfügung. Detaillierte Informationen finden Sie in:

* [Start und Stopp über die Befehlszeile](/help/sites-deploying/command-line-start-and-stop.md)

AEM startet und leitet Ihren Webbrowser automatisch zur entsprechenden Seite um. Für gewöhnlich handelt es sich um die Anmeldeseite, beispielsweise:

`https://localhost:4502/`

![Anmeldebildschirm](assets/screen_shot_2019-04-08at83533am.png)

Nachdem Sie sich angemeldet haben, verfügen Sie über Zugriff auf AEM. Weitere Informationen in Abhängigkeit von Ihrer Rolle finden Sie unter den folgenden Punkten:

* [Authoring –](/help/sites-authoring/home.md)
* [Verwalten](/help/sites-administering/home.md)
* [Entwickeln](/help/sites-developing/home.md)
* [Verwaltung](/help/managing/best-practices.md)

## Erweiterte Bereitstellung {#advanced-deployment}

Im obigen Abschnitt sollten Sie ein solides Verständnis der Grundlagen der AEM-Installation gewonnen haben. Das Installieren eines vollständigen Produktionssystems von AEM kann erheblich komplexer sein. Informationen über die vollständige Abdeckung der erweiterten Installation finden Sie auf den folgenden Unterseiten:

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
* [Was ist AEM Screens? ](https://experienceleague.adobe.com/docs/experience-manager-screens/user-guide/aem-screens-introduction.html)
