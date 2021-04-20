---
title: Grundlegende Konfigurationskonzepte
seo-title: Grundlegende Konfigurationskonzepte
description: Anleitung zur Konfiguration von AEM
seo-description: Anleitung zur Konfiguration von AEM
uuid: edcdd4bd-5917-417e-8913-40d488383ea9
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 2673ea92-1651-4b1b-9aac-f4ba8b36782e
feature: Configuring
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2133'
ht-degree: 88%

---


# Grundlegende Konfigurationskonzepte{#basic-configuration-concepts}

Alle Parameter von Adobe Experience Manager (AEM) weisen bei der Installation Standardeinstellungen auf. Dadurch ist die Software sofort einsatzbereit. Sie können AEM jedoch entsprechend Ihren eigenen spezifischen Anforderungen konfigurieren.

Konfigurationen sind für zahlreiche Aspekte von AEM möglich:

* Manche werden [normalerweise für jede Projektinstallation](#primary-configuration-considerations) konfiguriert und müssen dahingehend überprüft werden, ob sie auf Ihr jeweiliges Projekt anwendbar sind.
* [Andere Konfigurationen](#further-configuration-considerations) können zwar vorgenommen werden, sind aber nicht zwingend erforderlich. Sie betreffen Funktionen sowie die Systemleistung und -stabilität.
* Wiederum andere sind nur für bestimmte optionale Funktionen von AEM nötig (diese werden gemeinsam mit der entsprechenden Funktion erläutert).

Abhängig von der jeweiligen Konfiguration können diese Änderungen mithilfe einer der folgenden Optionen durchgeführt werden:

* **Adobe CQ Web Console**

   Dies ist ein Standardspeicherort zum Konfigurieren von OSGi-Paketen und -Diensten.

   Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

* **Repository**

   Manche OSGi-Konfigurationen sind im Repository verfügbar. Dadurch wird gewährleistet, dass durch das Kopieren oder Replizieren von Repository-Inhalten identische Konfigurationen erzeugt werden. Je nach Ausführungsmodus können Sie auch Ihre eigenen Konfigurationen zum Repository hinzufügen.

   Weitere Informationen finden Sie unter [OSGi-Konfiguration im Repository](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository), insbesondere unter [Hinzufügen einer neuen Konfiguration zum Repository](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository).

* **Dateisystem**

   Einige Konfigurationsdateien befinden sich im Dateisystem.

* **AEM-WCM**

   Innerhalb AEM WCM selbst können verschiedene Aspekte konfiguriert werden, viele mit der Konsole [Tools](/help/sites-administering/tools-consoles.md); Replizierungsagenten.

>[!NOTE]
>
>Um die Konfigurationseinstellungen für OSGi-Services zu verwalten (Konsolen- oder Repository-Knoten), stehen Ihnen in Adobe Experience Manager mehrere Methoden zur Verfügung.
>
>Weitere Informationen hierzu finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Die Konfiguration von AEM ist unkompliziert, beachten Sie dabei aber Folgendes:
>
>Manche Änderungen können erhebliche Auswirkungen auf die Anwendung(en) haben. Achten Sie deshalb darauf, dass Sie über die nötige Erfahrung und Expertise verfügen, bevor Sie mit der Konfiguration von AEM beginnen, und nehmen Sie nur notwendige Änderungen vor. Alle über die OSGi-Konsole durchgeführten Änderungen werden **sofort** auf das laufende System angewendet (kein Neustart erforderlich).

## Primäre Überlegungen zur Konfiguration {#primary-configuration-considerations}

In dieser Liste finden Sie Informationen zu den primären Bereichen, die häufig für ein neues Projekt konfiguriert werden. Überprüfen Sie anhand dieser Liste, welche Bereiche auf Ihr Projekt zutreffen. Möglicherweise werden nicht alle benötigt.

Die Liste enthält eine kurze Übersicht über alle Konfigurationsaspekte sowie Links zu den Seiten, die vollständige Informationen enthalten.

### Sicherheitscheckliste {#security-checklist}

In der [Sicherheitscheckliste](/help/sites-administering/security-checklist.md) finden Sie die wichtigsten Konfigurationsprobleme. Lesen Sie sich die Liste durch und ergreifen Sie die für Ihre Installation nötigen Maßnahmen. 

### Konfigurieren der Standard-Benutzeroberfläche: Touch-optimiert oder klassisch {#configuring-the-default-ui-touch-optimized-or-classic}

In AEM sind zwei Benutzeroberflächen verfügbar:

* Die Touch-optimierte Benutzeroberfläche
* Klassische Benutzeroberfläche

Sie können die von Ihnen benötigte Benutzeroberfläche mithilfe von [Root Mapping](/help/sites-deploying/osgi-configuration-settings.md) konfigurieren.

>[!NOTE]
>
>Weitere Informationen zur Auswahl der Benutzeroberflächen finden Sie unter [Auswählen der Benutzeroberfläche](/help/sites-authoring/select-ui.md).

### IPv4 und IPv6 {#ipv-and-ipv}

Alle Elemente von AEM (z. B. das Repository und der Dispatcher) können sowohl in IPv4- als auch IPv6-Netzwerken installiert werden.

Der Betrieb funktioniert optimal, da keine spezielle Konfiguration erforderlich ist. Bei Bedarf können Sie eine IP-Adresse einfach mithilfe des Ihrem Netzwerktyp entsprechenden Formats angeben.

Wenn eine IP-Adresse angegeben werden muss, können Sie (je nach Bedarf) aus den folgenden Optionen auswählen:

* eine IPv6-Adresse

   zum Beispiel `https://[ab12::34c5:6d7:8e90:1234]:4502`

* eine IPv4-Adresse

   zum Beispiel `https://123.1.1.4:4502`

* einen Servernamen

   zum Beispiel `https://www.yourserver.com:4502`

* Der Standardfall von `localhost` wird für IPv4- und IPv6-Netzwerkinstallationen interpretiert.

   zum Beispiel `http://localhost:4502`

### Versionsbereinigung {#version-purging}

In einer Standardinstallation erstellt AEM bei jeder Aktivierung einer Seite (nach der Aktualisierung des Inhalts) eine neue Version einer Seite oder eines Knotens. Sie können zusätzliche Versionen auch über die Registerkarte **Versionierung** im Sidekick erstellen. Alle diese Versionen werden im Repository gespeichert und können bei Bedarf wiederhergestellt werden.

Diese Versionen werden nie bereinigt. Daher wächst die Größe des Repositorys im Laufe der Zeit an und muss verwaltet werden.

Weitere Informationen hierzu finden Sie unter [Bereinigen der Version](/help/sites-deploying/version-purging.md), insbesondere unter [Versions-Manager](/help/sites-deploying/version-purging.md#version-manager). Hier wird erläutert, wie Sie AEM konfigurieren müssen, um ältere Versionen zu bereinigen, wenn eine neue Version erstellt wird.

### Protokollierung {#logging}

Mit AEM können Sie Folgendes konfigurieren:

* Globale Parameter für den zentralen Protokollierungsdienst
* Anforderung einer Datenprotokollierung; eine spezielle Protokollierungskonfiguration zum Anfordern von Informationen
* Spezifische Einstellungen für die einzelnen Dienste; zum Beispiel eine einzelne Protokolldatei und ein bestimmtes Format für die Protokollmeldungen

Weitere Informationen finden Sie unter [Protokollierung](/help/sites-deploying/configure-logging.md). 

### Ausführungsmodi {#run-modes}

Mithilfe von Ausführungsmodi können Sie Ihre AEM-Instanz an einen bestimmten Zweck anpassen, z. B. Inhaltserstellung, Veröffentlichung, Test, Entwicklung oder Intranet.

Dies erfolgt durch die Definition von Gruppen von Konfigurationsparametern für jeden Ausführungsmodus. Ein Grundbestand an Konfigurationsparametern wird auf alle Ausführungsmodi angewendet. Sie können dann zusätzliche Parameter entsprechend den Anforderungen Ihrer spezifischen Umgebung einstellen. Diese werden nach Bedarf angewendet.

Sämtliche Konfigurationseinstellungen werden im selben Repository gespeichert und durch Definition des **Ausführungsmodus** aktiviert.

Weitere Informationen finden Sie unter [Ausführungsmodi](/help/sites-deploying/configure-runmodes.md).

### Single Sign-On  {#single-sign-on}

Mithilfe von Single Sign-On (SSO) können Sie durch die einmalige Eingabe Ihrer Zugangsdaten (z. B. Ihres Benutzernamens und Passworts) auf mehrere Systeme zugreifen. Ein separates System (der so genannte vertrauenswürdige Authentifikator) führt die Authentifizierung durch und liefert die Zugangsdaten an Experience Manager. Experience Manager überprüft diese und erzwingt die Zugriffsberechtigungen für den Benutzer (d. h. legt fest, auf welche Ressourcen der Benutzer zugreifen darf). 

Weitere Informationen finden Sie unter [Single Sign-On](/help/sites-deploying/single-sign-on.md).

### Ressourcenzuordnung {#resource-mapping}

Die Ressourcenzuordnung wird zur Definition von Umleitungen, Vanity-URLs und virtuellen Hosts für AEM verwendet.

Diese Zuordnungen können Sie beispielsweise folgendermaßen verwenden:

* Präfix aller Anforderungen mit `/content`, damit die interne Struktur von den Besuchern Ihrer Website ausgeblendet wird.
* Definieren Sie eine Umleitung, damit alle Anforderungen an die `/content/en/gateway`-Seite Ihrer Website an `https://gbiv.com/` umgeleitet werden.

Weitere Informationen finden Sie unter [Ressourcen-Mapping](/help/sites-deploying/resource-mapping.md).

### Replikation, Rückwärtsreplikation und Replikationsagenten  {#replication-reverse-replication-and-replication-agents}

Replikationsagenten werden in AEM für folgende Aufgaben verwendet:

* [Veröffentlichen (Aktivieren)](/help/sites-authoring/publishing-pages.md) von Inhalten von einer Autoren- in einer Veröffentlichungsumgebung
* Leeren von Inhalt im Dispatcher-Cache
* Zurückleiten von Benutzereingaben (z. B. Formulareingaben) von der Veröffentlichungs- an die Autorenumgebung (gesteuert von der Autorenumgebung).

Weitere Informationen finden Sie unter [Replikation](/help/sites-deploying/replication.md)

### OSGi-Konfigurationseinstellungen {#osgi-configuration-settings}

[](https://www.osgi.org/) OSGiist ein grundlegendes Element im Technologiestapel von AEM. OSGi wird zur Steuerung der AEM-Bundles und ihrer Konfiguration verwendet.

Eine Liste der verschiedenen Bundles, die für die Projektimplementierung relevant sind (nach Bundle aufgelistet), finden Sie unter [OSGi-Konfigurationseinstellungen](/help/sites-deploying/osgi-configuration-settings.md). Nicht alle aufgeführten Einstellungen müssen angepasst werden. Einige werden nur zum besseren Verständnis von AEM erwähnt.

Bei der Verwendung von AEM gibt es mehrere Methoden zur Verwaltung der Konfigurationseinstellungen für solche Services. Weitere Informationen und empfohlene Praktiken finden Sie unter [Konfigurieren von OSGi](/help/sites-deploying/configuring-osgi.md).

### Konfigurieren von LDAP  {#configuring-ldap}

LDAP-Authentifizierung ist für Benutzer erforderlich, die in einem (zentralen) LDAP-Verzeichnis wie im Active Directory gespeichert sind. Dies verringert den Aufwand bei der Verwaltung von Benutzerkonten.

Die LDAP-Authentifizierung erfolgt auf Repository-Ebene, sie wird also direkt vom Repository durchgeführt. Weitere Informationen finden Sie unter [Konfigurieren von LDAP mit AEM](/help/sites-administering/ldap-config.md).

Weitere Informationen zur Benutzerverwaltung in AEM (einschließlich der Zuweisung von Zugriffsrechten) finden Sie unter [Benutzerverwaltung und Sicherheit](/help/sites-administering/security.md).

### Konfigurieren des Dispatchers  {#configuring-the-dispatcher}

Dispatcher ist das Caching- und/oder Lastenausgleichstool von Adobe Experience Manager, das in Verbindung mit einem Webserver der Unternehmensklasse verwendet werden kann.

Weitere Informationen zur Konfiguration finden Sie unter [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html), insbesondere unter [Konfigurieren des Dispatchers](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

### Konfigurieren von AEM LiveCycle Connector {#configuring-aem-livecycle-connector}

Mit der Veröffentlichung von AEM Doc Services und AEM Doc Security haben wir jetzt die Möglichkeit, mithilfe der LiveCycle Doc Services ein XFA-Formular zu erstellen, ein Dokument in das PDF-Format umzuwandeln und ein Dokument durch eine Richtlinie zu schützen. Weitere Informationen finden Sie unter [AEM LiveCycle Connector](https://helpx.adobe.com/livecycle/help/aem/aem-livecycle-connector.html).

### Auftragsabladung und Topologieverwaltung {#job-offloading-and-topology-administration}

Mit der [Abladung](/help/sites-deploying/offloading.md) werden Verarbeitungsaufgaben auf Experience Manager-Instanzen in einer Topologie verteilt. Mit der Abladung können Sie bestimmte Experience Manager-Instanzen zur Durchführung bestimmter Verarbeitungsarten verwenden. Mit dieser gezielten Verarbeitung kann die Nutzung der verfügbaren Serverressourcen maximiert werden.

Topologien sind lose verknüpfte Experience Manager-Cluster, die an der Abladung beteiligt sind. Ein Cluster besteht aus einer oder mehreren Experience Manager-Serverinstanzen (eine einzelne Instanz wird als Cluster betrachtet).

Weitere Informationen zur Ansicht oder Änderung der Topologie-Mitgliedschaft finden Sie unter [Verwalten von Topologien](/help/sites-deploying/offloading.md#administering-topologies).

### Konfigurieren der Willkommens-Konsole  {#configuring-the-welcome-console}

Die Willkommens-Konsole der klassischen Benutzeroberfläche bietet eine Liste mit Links zu den unterschiedlichen Konsolen und Funktionen innerhalb von AEM.

Die sichtbaren Links können konfiguriert werden. Weitere Informationen dazu finden Sie unter [Konfigurieren der Willkommens-Konsole](/help/sites-developing/customizing-the-welcome-console.md).

### Konfiguration zur Leistungsoptimierung  {#configuring-for-performance}

Die [Leistung](/help/sites-deploying/configuring-performance.md) ist für Ihr Projekt ausschlaggebend. Bestimmte Aspekte von AEM (bzw. des zugrunde liegenden Repositorys) können so konfiguriert werden, dass die Leistung optimiert wird.

Weitere Informationen finden Sie unter [Konfiguration zur Optimierung der Leistung](/help/sites-deploying/configuring-performance.md#configuring-for-performance).

<!--delete ### Scaling {#scaling}

Scaling a CQ installation correctly depends greatly on the details of your particular use case. A detailed discussion of solution patterns for various situations can be found in [Scaling CQ](/help/sites-deploying/scaling.md).-->

### Freigegebener Datenspeicher {#shared-data-store}

Der Repository-Datenspeicher wird verwendet, um die Datenspeicherung großer Binärdateien aus dem eigentlichen Repository in einen separaten Bereich zu verschieben, sodass mehrere Instanzen derselben Binärdatei (z. B. ein Bild) innerhalb der Repository-Struktur nur einmal gespeichert werden.

Die Funktion zum einmaligen Speichern, aber mehrfachen Referenzieren kann erweitert werden, sodass nicht nur ein einziger Repository-Baum bedient wird, sondern getrennte Repositorys. Der Datenspeicher eines jeden Repositorys wird dabei so konfiguriert, dass er auf denselben gemeinsamen Dateisystem-Speicherort verweist.

Ein derartiger Datenspeicher kann folgendermaßen gemeinsam genutzt werden: über unterschiedliche Knoten im selben Cluster, über unterschiedliche Veröffentlichungs- und/oder Autoreninstanzen in derselben Installation oder sogar über getrennte Instanzen in unterschiedlichen Installationen.

Weitere Informationen finden Sie unter [Konfigurieren von Daten- und Knotenspeichern](/help/sites-deploying/data-store-config.md).

## Weitere Überlegungen zur Konfiguration  {#further-configuration-considerations}

### Aktivieren von HTTP über SSL {#enabling-http-over-ssl}

Sie können HTTP über SSL aktivieren, um die Verbindungssicherheit zu Ihren Servern zu erhöhen.

Weitere Informationen finden Sie unter [Aktivieren von HTTP über SSL](/help/sites-administering/ssl-by-default.md).

### AEM-Portale und Portlets  {#aem-portals-and-portlets}

Ein Portal ist eine Webanwendung, die Personalisierung, Single Sign-On und Inhaltsintegration aus verschiedenen Quellen ermöglicht und die Präsentationsebene von Informationssystemen hostet. Mit der Portlet-Komponente können Sie zudem ein Portlet auf der Seite einbetten. Um auf von CQ5 WCM bereitgestellten Inhalt zuzugreifen, kann der Portalserver mit dem CQ5 Portal Director Portlet ausgestattet werden. Installieren Sie zu diesem Zweck das Portlet, konfigurieren Sie es und fügen Sie es zur Portalseite hinzu.

Weitere Informationen finden Sie unter [Portal und Portlets](/help/sites-administering/aem-as-portal.md).

### Ablauf statischer Objekte {#expiration-of-static-objects}

Statische Objekte (wie Symbole) ändern sich nicht. Daher sollte das System so konfiguriert werden, dass diese Objekte (über einen angemessenen Zeitraum) nicht ablaufen, damit unnötiger Traffic reduziert wird. 

Weitere Informationen finden Sie unter [Ablaufen von statischen Objekten](/help/sites-deploying/expiration-static-objects.md).

### Öffnen von Dateien im Java-Prozess  {#open-files-in-the-java-process}

Bei jedem Java-Prozess kann auf Dateien zugegriffen werden. Dieser Vorgang verbraucht Systemressourcen. Aus diesem Grund wird ein oberes Limit definiert, das angibt, auf wie viele Dateien in jedem Prozess gleichzeitig zugegriffen werden darf. Wenn dieses Limit überschritten wird, kann ein Ausnahmefehler auftreten.

Wenn der AEM-Prozess diesen Maximalwert überschreitet, wird die Meldung &quot; `too many open files`&quot;in `error.log` angezeigt.

Um solche Ausnahmen zu vermeiden, gehen Sie folgendermaßen vor:

1. Prüfen Sie, wie viele offene Dateien Ihr AEM-Prozess verwendet.

   Wie Sie diese Prüfung durchführen, hängt davon ab, auf welcher Plattform Ihre Instanz ausgeführt wird. Hilfsprogramme wie lsof (Unix) oder Process Explorer (Windows) können verwendet werden.

   Dieser Wert sollte bei der Entwicklung und bei Tests aus folgenden Gründen überwacht werden:

   * Zur Bestätigung, dass Dateien ordnungsgemäß geschlossen werden 
   * Zur Bestimmung des erforderlichen Höchstwerts (in verschiedenen Situationen)

1. Legen Sie den erlaubten Höchstwert fest.

   Der neue Wert sollte sowohl für die aktuellen Anforderungen als auch für etwaige künftige Spitzen ausreichend sein. Deshalb ist es ratsam, den Wert für die aktuellen Anforderungen zu verdoppeln.

   Standardmäßig konfiguriert `serverctl` `CQ_MAX_OPEN_FILES` `8192`; dies sollte für die meisten Szenarien ausreichen.

### Konfigurieren des Rich-Text-Editors {#configuring-the-rich-text-editor}

Der **Rich-Text-Editor** (**RTE**) bietet Autoren umfassende [Funktionen](/help/sites-authoring/rich-text-editor.md) zum Bearbeiten von Texten. Zudem stellt er Symbole, Auswahlfelder und Menüs für die WYSIWYG-Nutzung zur Verfügung.

Weitere Informationen finden Sie unter [Konfigurieren des Rich-Text-Editors](/help/sites-administering/rich-text-editor.md).

### Konfigurieren von „Rückgängig machen“ zur Bearbeitung von Seiten  {#configuring-undo-for-page-editing}

Es gibt mehrere Eigenschaften, mit denen das Verhalten der Befehle „Rückgängig machen“ und „Wiederholen“ zur Bearbeitung von Seiten gesteuert werden kann. Diese können konfiguriert werden. Weitere Informationen finden Sie unter [Konfigurieren von „Rückgängig machen“ zur Bearbeitung von Seiten](/help/sites-administering/config-undo.md).

### Konfigurieren der Videokomponente  {#configuring-the-video-component}

Mit der [Videokomponente](/help/sites-authoring/default-components-foundation.md#video) können Sie ein vordefiniertes Standard-Videoelement auf Ihrer Seite platzieren.

Damit die Codeumsetzung korrekt erfolgt, muss der Administrator [FFmpeg](/help/sites-administering/config-video.md#install-ffmpeg) separat installieren. Darüber hinaus kann er auch Ihre [Videoprofile](/help/sites-administering/config-video.md#configure-video-profiles) für die Verwendung mit HTML5-Elementen konfigurieren.

### Konfigurieren und Anpassen von Berichten  {#configuring-and-customizing-reports}

Zur Überwachung und Analyse des Zustands Ihrer Instanz bietet CQ eine Auswahl von Standardberichten, die nach Ihren persönlichen Anforderungen konfiguriert werden können:

Weitere Informationen finden Sie unter [Grundlagen zur Anpassung von Berichten](/help/sites-administering/reporting.md#the-basics-of-report-customization).

### Konfigurieren von E-Mail-Benachrichtigungen  {#configuring-email-notification}

CQ sendet E-Mail-Benachrichtigungen an folgende Benutzer:

* Seitenereignisse wie Änderungen oder Replikationen abonniert haben.
* Benutzer, die sich für Forenereignisse angemeldet haben.
* Benutzer, die einen Schritt in einem Workflow ausführen müssen.

Weitere Informationen finden Sie unter [Konfigurieren von E-Mail-Benachrichtigungen](/help/sites-administering/notification.md).

### Aktivieren von Seitenimpressionen  {#enabling-page-impressions}

Seitenimpressionen werden in der klassischen Benutzeroberfläche der Siteadmin-Konsole in der Spalte **Impressionen** angezeigt. Um das Erfassen von Seitenimpressionen zu ermöglichen, müssen Sie Folgendes konfigurieren:

* In der Veröffentlichungsinstanz:

   * [Day CQ WCM-Seitenstatistiken](/help/sites-deploying/osgi-configuration-settings.md)

* In der Autoreninstanz:

   * [Adobe Page Impressions Tracke](/help/sites-deploying/osgi-configuration-settings.md)

>[!CAUTION]
>
>Die Konfiguration von Adobe Page Impressions Tracker in der Autorenumgebung ermöglicht anonyme Anfragen an den Tracking-Service.

