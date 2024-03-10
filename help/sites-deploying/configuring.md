---
title: Grundlegende Konfigurationskonzepte
description: Erfahren Sie, wie Sie Adobe Experience Manager für Ihre spezifischen Anforderungen konfigurieren.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 3777a1ba-cc4e-41b9-9098-236f8141925f
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '2093'
ht-degree: 96%

---

# Grundlegende Konfigurationskonzepte{#basic-configuration-concepts}

Alle Parameter von Adobe Experience Manager (AEM) weisen bei der Installation Standardeinstellungen auf. Dadurch ist die Software sofort einsatzbereit. Sie können AEM jedoch für Ihre eigenen spezifischen Anforderungen konfigurieren.

Es gibt viele Aspekte von AEM, die konfiguriert werden können:

* Einige sind [allgemein für jede Projektinstallation konfiguriert](#primary-configuration-considerations) und müssen überprüft werden, um festzustellen, ob sie auf Ihr Projekt zutreffen.
* [Weitere Konfigurationen](#further-configuration-considerations) können üblich, jedoch nicht zwingend erforderlich sein; sie beziehen sich auf Funktionen oder die Systemleistung und -stabilität.
* Andere sind nur für bestimmte optionale Funktionen von AEM erforderlich (diese sind zusammen mit der entsprechenden Funktion dokumentiert).

Abhängig von der spezifischen Konfiguration können diese Änderungen mithilfe der folgenden Methoden vorgenommen werden:

* **Adobe CQ Web-Konsole**

  Dies ist ein Standardspeicherort für die Konfiguration von OSGi-Bundles und -Services.

  Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

* **Repository**

  Manche OSGi-Konfigurationen sind im Repository verfügbar. Dadurch wird sichergestellt, dass beim Kopieren oder Replizieren von Repository-Inhalten identische Konfigurationen neu erstellt werden. Sie können auch Ihre eigenen Konfigurationen, abhängig vom Ausführungsmodus, zum Repository hinzufügen.

  Weitere Informationen finden Sie unter [OSGi-Konfiguration im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository), insbesondere unter [Hinzufügen einer neuen Konfiguration zum Repository](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

* **Dateisystem**

  Einige wenige Konfigurationsdateien befinden sich im Dateisystem.

* **AEM-WCM**

  Diverse Aspekte können auch im AEM-WCM selbst konfiguriert werden. Häufig wird hierfür die [Tools](/help/sites-administering/tools-consoles.md)-Konsole verwendet, z. B. Replikationsagenten.

>[!NOTE]
>
>Um die Konfigurationseinstellungen für OSGi-Dienste zu verwalten (Konsolen- oder Repository-Knoten), stehen Ihnen in Adobe Experience Manager mehrere Methoden zur Verfügung.
>
>Ausführliche Informationen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Die Konfiguration von AEM ist unkompliziert. Einige Änderungen können sich jedoch erheblich auf die Anwendungen auswirken. Stellen Sie daher sicher, dass Sie über die nötige Erfahrung und das erforderliche Wissen verfügen, bevor Sie mit der AEM-Konfiguration beginnen. Nehmen Sie außerdem nur die Änderungen vor, von denen Sie wissen, dass sie erforderlich sind. Alle über die OSGi-Konsole vorgenommenen Änderungen werden **sofort** auf das aktive System angewendet (kein Neustart erforderlich).

## Wesentliche Konfigurationsaspekte {#primary-configuration-considerations}

Diese Liste beschreibt die wesentlichen Bereiche, die normalerweise für jedes neue Projekt konfiguriert werden. Nicht alle sind erforderlich, aber die Liste muss gelesen und überprüft werden, um zu ermitteln, was auf Ihr Projekt zutrifft.

Die Liste liefert einen kurzen Überblick über die einzelnen Konfigurationsaspekte sowie Links zu den Seiten mit den vollständigen Details.

### Sicherheitscheckliste {#security-checklist}

Einige wichtige Konfigurationsprobleme werden im Abschnitt [Sicherheitscheckliste](/help/sites-administering/security-checklist.md) aufgeführt. Lesen Sie sich die Liste durch und ergreifen Sie die für Ihre Installation nötigen Maßnahmen.

### Konfigurieren der Standard-Benutzeroberfläche – Touch-optimiert oder klassisch {#configuring-the-default-ui-touch-optimized-or-classic}

In AEM sind zwei Benutzeroberflächen verfügbar:

* Die Touch-optimierte Benutzeroberfläche
* Klassische Benutzeroberfläche

Sie können die von Ihnen benötigte Benutzeroberfläche mithilfe von [Root Mapping](/help/sites-deploying/osgi-configuration-settings.md) konfigurieren.

>[!NOTE]
>
>Weitere Informationen zur Auswahl der Benutzeroberflächen finden Sie unter [Auswählen der Benutzeroberfläche](/help/sites-authoring/select-ui.md).

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente von AEM (z. B. das Repository und der Dispatcher) können sowohl in IPv4- als auch in IPv6-Netzwerken installiert werden.

Der Betrieb funktioniert reibungslos, da keine spezielle Konfiguration erforderlich ist. Bei Bedarf können Sie eine IP-Adresse einfach mithilfe des für Ihren Netzwerktyp entsprechenden Formats angeben.

Wenn eine IP-Adresse angegeben werden muss, können Sie demnach (entsprechend Ihren Wünschen) aus den folgenden Optionen auswählen:

* eine IPv6-Adresse

  Beispiel: `https://[ab12::34c5:6d7:8e90:1234]:4502`

* eine IPv4-Adresse

  Beispiel: `https://123.1.1.4:4502`

* einen Server-Namen

  zum Beispiel `https://www.yourserver.com:4502`

* der Standardfall von `localhost` wird für IPv4- und IPv6-Netzwerkinstallationen interpretiert

  zum Beispiel `http://localhost:4502`

### Versionsbereinigung {#version-purging}

In einer Standardinstallation erstellt AEM eine Version einer Seite oder eines Knotens, sobald Sie eine Seite aktivieren (nach Aktualisierung des Inhalts). Mit der Registerkarte **Versionierung** im Sidekick können Sie auf Anforderung auch zusätzliche Versionen erstellen. Alle diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie bereinigt, sodass die Repository-Größe im Laufe der Zeit zunimmt und daher verwaltet werden muss.

Weitere Informationen hierzu finden Sie unter [Bereinigen der Version](/help/sites-deploying/version-purging.md), insbesondere unter [Versions-Manager](/help/sites-deploying/version-purging.md#version-manager). Hier wird erläutert, wie Sie AEM konfigurieren müssen, um ältere Versionen zu bereinigen, wenn eine neue Version erstellt wird.

### Protokollierung {#logging}

Mit AEM können Sie Folgendes konfigurieren:

* globale Parameter für den zentralen Protokollierungsdienst
* Anfragedatenprotokollierung; eine spezielle Protokollierungskonfiguration für Anfrageinformationen
* spezifische Einstellungen für die einzelnen Dienste, z. B. eine einzelne Protokolldatei und ein bestimmtes Format für die Protokollmeldungen

Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md). 

### Ausführungsmodi {#run-modes}

Mit Ausführungsmodi können Sie Ihre AEM-Instanz für einen bestimmten Zweck anpassen, z. B. für Erstellung oder Veröffentlichung, Tests, Entwicklung, Intranet usw.

Dies geschieht durch Definition von Sammlungen von Konfigurationsparametern für jeden Ausführungsmodus. Ein Grundbestand an Konfigurationsparametern wird auf alle Ausführungsmodi angewendet. Sie können dann zusätzliche Parameter entsprechend den Anforderungen Ihrer spezifischen Umgebung einstellen. Diese werden dann nach Bedarf angewendet.

Sämtliche Konfigurationseinstellungen werden in einem Repository gespeichert und durch Festlegen des **Ausführungsmodus** aktiviert.

Ausführliche Informationen finden Sie unter [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md).

### Single Sign-On {#single-sign-on}

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (auch als vertrauenswürdiger Authenticator bezeichnet) führt die Authentifizierung durch und stellt Experience Manager die Benutzeranmeldeinformationen zur Verfügung. Experience Manager überprüft die Zugriffsberechtigungen und setzt diese für die Benutzerin oder den Benutzer durch (legt also fest, auf welche Ressourcen die Benutzerin oder der Benutzer zugreifen darf).

Ausführliche Informationen finden Sie unter [Single Sign-on](/help/sites-deploying/single-sign-on.md).

### Ressourcenzuordnung {#resource-mapping}

Die Ressourcenzuordnung wird verwendet, um Umleitungen, Vanity-URLs und virtuelle Hosts für AEM zu definieren.

Diese Zuordnungen können Sie beispielsweise verwenden, um:

* Allen Anfragen das Präfix `/content` voranzustellen, sodass die interne Struktur für Besucher Ihrer Website ausgeblendet wird.
* Eine Umleitung zu definieren, sodass alle Anfragen an die Seite `/content/en/gateway` Ihrer Website zu `https://gbiv.com/` umgeleitet werden.

Weitere Informationen finden Sie unter [Ressourcenzuordnung](/help/sites-deploying/resource-mapping.md).

### Replikation, umgekehrte Replikation und Replikationsagenten {#replication-reverse-replication-and-replication-agents}

Replikationsagenten sind als Mechanismus für folgende Vorgänge von zentraler Bedeutung für AEM:

* [Veröffentlichen (Aktivieren)](/help/sites-authoring/publishing-pages.md) von Inhalten von einer Autoren- in einer Veröffentlichungsumgebung
* explizites Leeren von Inhalten aus dem Dispatcher-Cache
* Zurückgeben von Benutzereingaben (z. B. Formulareingaben) aus der Veröffentlichungsumgebung an die Autorenumgebung (unter Kontrolle der Autorenumgebung).

Weitere Informationen finden Sie unter [Replikation](/help/sites-deploying/replication.md).

### OSGi-Konfigurationseinstellungen {#osgi-configuration-settings}

[OSGi](https://www.osgi.org/) ist ein wesentlicher Bestandteil der Technologien von AEM. Es wird zur Steuerung der zusammengesetzten AEM-Bundles und ihrer Konfiguration verwendet.

Unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md) finden Sie eine Liste der verschiedenen Bundles, die für die Projektimplementierung relevant sind (aufgelistet nach Bundle). Nicht alle aufgeführten Einstellungen müssen angepasst werden. Einige werden hier nur zum besseren Verständnis von AEM erwähnt.

Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Dienste. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

### Konfigurieren von LDAP {#configuring-ldap}

Die LDAP-Authentifizierung ist erforderlich, um Benutzende zu authentifizieren, die in einem (zentralen) LDAP-Verzeichnis wie Active Directory gespeichert sind. Dies reduziert den Aufwand bei der Verwaltung von Benutzerkonten.

Die LDAP-Authentifizierung erfolgt auf Repository-Ebene, sie wird also direkt vom Repository durchgeführt. Weitere Informationen finden Sie unter [Konfigurieren von LDAP mit AEM](/help/sites-administering/ldap-config.md).

Informationen zur Benutzerverwaltung in AEM (einschließlich der Zuweisung von Zugriffsrechten) finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

### Konfigurieren des Dispatchers {#configuring-the-dispatcher}

Der Dispatcher ist das Adobe Experience Manager-Tool zum Caching oder Lastenausgleich bzw. für beides. Er kann mit einem Webserver der Unternehmensklasse eingesetzt werden.

Weitere Informationen zur Konfiguration finden Sie unter [Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de), insbesondere unter [Konfigurieren des Dispatchers](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de).

### Konfigurieren von AEM LiveCycle Connector {#configuring-aem-livecycle-connector}

Mit der Veröffentlichung der AEM-Dokumentendienste und AEM-Dokumentsicherheit hat AEM jetzt die Möglichkeit, mithilfe der LiveCycle-Dokumentendienste ein XFA-Formular zu rendern, ein Dokument in das PDF-Format zu konvertieren und ein Dokument durch eine Richtlinie zu schützen. Weitere Informationen finden Sie unter [AEM LiveCycle Connector](https://helpx.adobe.com/de/livecycle/help/aem/aem-livecycle-connector.html).

### Abladung von Vorgängen und Topologieverwaltung {#job-offloading-and-topology-administration}

[Mit der Abladung werden Verarbeitungsaufgaben auf die Experience Manager-Instanzen in einer Topologie verteilt. ](/help/sites-deploying/offloading.md) Mit der Abladung können Sie bestimmte Experience Manager-Instanzen zur Durchführung bestimmter Verarbeitungsarten verwenden. Durch eine spezielle Verarbeitung können Sie die Nutzung der verfügbaren Server-Ressourcen maximieren.

Topologien sind lose gekoppelte Experience Manager-Cluster, die an der Abladung beteiligt sind. Ein Cluster besteht aus einer oder mehreren Experience Manager-Server-Instanzen (eine einzelne Instanz gilt als Cluster).

Weitere Informationen zum Anzeigen oder Ändern der Topologiemitgliedschaft finden Sie unter [Verwalten von Topologien](/help/sites-deploying/offloading.md#administering-topologies).

### Konfigurieren der Willkommenskonsole {#configuring-the-welcome-console}

Die Willkommenskonsole der klassischen Benutzeroberfläche bietet eine Liste mit Links zu den verschiedenen Konsolen und Funktionen innerhalb von AEM

Es ist möglich, die sichtbaren Links zu konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der Willkommenskonsole](/help/sites-developing/customizing-the-welcome-console.md).

### Konfigurieren zur Leistungsoptimierung {#configuring-for-performance}

Der [Leistungsaspekt](/help/sites-deploying/configuring-performance.md) ist entscheidend für Ihr Projekt. Bestimmte Aspekte von AEM (bzw. des zugrunde liegenden Repositorys) können so konfiguriert werden, dass die Leistung optimiert wird.

Weitere Informationen finden Sie unter [Konfigurieren zur Leistungsoptimierung](/help/sites-deploying/configuring-performance.md#configuring-for-performance).

<!--delete ### Scaling {#scaling}

Scaling a CQ installation correctly depends greatly on the details of your particular use case. A detailed discussion of solution patterns for various situations can be found in [Scaling CQ](/help/sites-deploying/scaling.md).-->

### Freigegebener Datenspeicher {#shared-data-store}

Der Datenspeicher des Repositorys wird verwendet, um gespeicherte Daten großer Binärdateien aus dem Repository in einen separaten Bereich abzuladen. Dadurch werden mehrere Instanzen derselben Binärdatei (z. B. eines Bildes) innerhalb der Repository-Struktur nur einmal gespeichert.

Diese „Einmal speichern, mehrmals referenzieren“-Funktion kann erweitert werden, um nicht nur eine einzige Repository-Struktur, sondern vollständig separate Repositorys bereitzustellen, indem der Datenspeicher jeweils so konfiguriert wird, dass er auf denselben Speicherort des gemeinsam genutzten Dateisystems verweist.

Ein solcher Datenspeicher kann von verschiedenen Knoten im selben Cluster, verschiedenen Veröffentlichungs- und/oder Autoreninstanzen in derselben Installation oder sogar völlig separaten Instanzen in verschiedenen Installationen gemeinsam genutzt werden.

Weitere Informationen finden Sie unter [Konfigurieren von Datenspeichern und Knotenspeichern](/help/sites-deploying/data-store-config.md).

## Weitere Konfigurationsaspekte {#further-configuration-considerations}

### Aktivieren von HTTP über SSL {#enabling-http-over-ssl}

Sie können HTTP über SSL aktivieren, um sicherere Verbindungen zu Ihren Servern herzustellen.

Weitere Informationen finden Sie unter [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

### AEM-Portale und Portlets {#aem-portals-and-portlets}

Ein Portal ist eine Web-Anwendung, die Personalisierung, Single Sign-on und Inhaltsintegration aus verschiedenen Quellen ermöglicht und die Präsentationsebene von Informationssystemen hostet. Mit der Portlet-Komponente können Sie zudem ein Portlet auf der Seite einbetten. Um auf von CQ5-WCM bereitgestellte Inhalte zuzugreifen, muss der Portal-Server mit dem CQ5 Portal Director Portlet ausgestattet werden. Führen Sie dazu die erforderlichen Schritte aus, um das Portlet zu installieren, zu konfigurieren und der Portalseite hinzuzufügen.

Weitere Einzelheiten finden Sie unter [Portal und Portlets](/help/sites-administering/aem-as-portal.md).

### Ablauf der Gültigkeit statischer Objekte {#expiration-of-static-objects}

Statische Objekte (z. B. Symbole) ändern sich nicht. Daher sollte das System so konfiguriert werden, dass diese Objekte (über einen angemessenen Zeitraum) nicht ablaufen, damit unnötiger Traffic reduziert wird.

Weitere Informationen finden Sie unter [Ablauf statischer Objekte](/help/sites-deploying/expiration-static-objects.md).

### Geöffnete Dateien im Java™-Prozess {#open-files-in-the-java-process}

Jeder Java™-Prozess kann auf Dateien zugreifen, was Systemressourcen beansprucht. Aus diesem Grund wird ein oberes Limit definiert, das angibt, auf wie viele Dateien in jedem Prozess gleichzeitig zugegriffen werden darf. Wird dieser Wert überschritten, kann ein Ausnahmefehler auftreten.

Wenn der AEM-Prozess dieses obere Limit überschreitet, wird die Melldung „`too many open files`“ in `error.log` angezeigt.

Gehen Sie wie folgt vor, um solche Ausnahmen zu vermeiden:

1. Überprüfen Sie, wie viele geöffnete Dateien von Ihrem AEM-Prozess verwendet werden.

   Diese Prüfung hängt von der Plattform ab, auf der Ihre Instanz ausgeführt wird. Es können hierfür Dienstprogramme wie lsof (UNIX®) oder Process Explorer (Windows) verwendet werden.

   Dieser Wert sollte bei der Entwicklung und bei Tests aus folgenden Gründen überwacht werden:

   * Zur Bestätigung, dass Dateien ordnungsgemäß geschlossen werden 
   * zur Bestimmung des erforderlichen Maximalwerts (unter verschiedenen Umständen)

1. Legen Sie das zulässige Maximum fest.

   Der neue Wert sollte sowohl für die aktuellen Anforderungen als auch für etwaige künftige Spitzen ausreichend sein. Deshalb ist es ratsam, den Wert für die aktuellen Anforderungen zu verdoppeln.

   Standardmäßig konfiguriert `serverctl` `CQ_MAX_OPEN_FILES` mit `8192`. Dies sollte für die meisten Szenarien ausreichend sein.

### Konfigurieren des Rich-Text-Editors {#configuring-the-rich-text-editor}

Der **Rich-Text-Editor** (**RTE**) bietet Autorinnen und Autoren eine Vielzahl von [Funktionen](/help/sites-authoring/rich-text-editor.md) für die Bearbeitung ihrer Textinhalte und durch die Bereitstellung von Symbolen, Auswahlfeldern und Menüs ein WYSIWYG-Erlebnis.

Weitere Informationen finden Sie unter [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md).

### Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung {#configuring-undo-for-page-editing}

Es gibt mehrere Eigenschaften, mit denen das Verhalten der Befehle „Rückgängig machen“ und „Wiederholen“ zur Bearbeitung von Seiten gesteuert werden kann. Diese können konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von Rückgängig-Vorgängen zur Seitenbearbeitung](/help/sites-administering/config-undo.md).

### Konfigurieren der Videokomponente {#configuring-the-video-component}

Mit der [Videokomponente](/help/sites-authoring/default-components-foundation.md#video) können Sie ein vordefiniertes, vorkonfiguriertes Videoelement auf Ihrer Seite platzieren.

Damit die Transkodierung korrekt erfolgt, muss die oder der Administrierende [FFmpeg](/help/sites-administering/config-video.md#install-ffmpeg) separat installieren. Darüber können auch Ihre [Videoprofile](/help/sites-administering/config-video.md#configure-video-profiles) für die Verwendung mit HTML5-Elementen konfiguriert werden.

### Konfigurieren und Anpassen von Berichten {#configuring-and-customizing-reports}

Um Ihnen bei der Überwachung und Analyse des Status Ihrer Instanz zu helfen, stellt CQ eine Auswahl an Standardberichten bereit, die für Ihre individuellen Anforderungen konfiguriert werden können:

Weitere Informationen finden Sie unter [Grundlagen der Berichtsanpassung](/help/sites-administering/reporting.md#the-basics-of-report-customization).

### Konfigurieren von E-Mail-Benachrichtigungen {#configuring-email-notification}

CQ sendet E-Mail-Benachrichtigungen an Benutzende, die:

* Sie haben Seitenereignisse abonniert, z. B. Änderungen oder Replikation.
* Forumsveranstaltungen abonniert haben.
* Einen Schritt in einem Workflow ausführen müssen.

Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md).

### Aktivieren von Page-Impressions {#enabling-page-impressions}

Page-Impressions werden in der Spalte **Impressions** der SiteAdmin-Konsole der klassischen Benutzeroberfläche angezeigt. Um die Erfassung von Page-Impressions zu aktivieren, konfigurieren Sie Folgendes:

* In der Autoreninstanz:

   * [Day CQ WCM-Seitenstatistiken](/help/sites-deploying/osgi-configuration-settings.md)

* In der Autoreninstanz:

   * [Adobe Page Impressions Tracker](/help/sites-deploying/osgi-configuration-settings.md)

>[!CAUTION]
>
>Die Konfiguration von Adobe Page Impressions Tracker in der Autorenumgebung ermöglicht anonyme Anfragen an den Tracking-Dienst.
