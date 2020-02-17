---
title: Architektur und Bereitstellungstopologien für AEM Forms
seo-title: Architektur und Bereitstellungstopologien für AEM Forms
description: Architekturdetails für AEM Forms und empfohlene Topologien für neue und vorhandene AEM-Kunden und Kunden, die ein Upgrade von LiveCycle ES4 auf AEM Forms durchführen.
seo-description: Architekturdetails für AEM Forms und empfohlene Topologien für neue und vorhandene AEM-Kunden und Kunden, die ein Upgrade von LiveCycle ES4 auf AEM Forms durchführen.
uuid: 90baa57a-4785-4b49-844c-a44717d3c12d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 0156b5c3-3bef-4213-9ada-c7b6ae96ada4
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Architektur und Bereitstellungstopologien für AEM Forms {#architecture-and-deployment-topologies-for-aem-forms}

## Architektur {#architecture}

AEM Forms ist eine Anwendung, die in AEM als AEM-Paket bereitgestellt wird. Das Paket wird als Add-On-Paket für AEM Forms bezeichnet. Das Add-On-Paket für AEM Forms enthält sowohl Dienste (API-Anbieter), die im AEM OSGi-Container bereitgestellt werden, als auch Servlets oder JSPs (mit Front-End- und REST-API-Funktionalität), die vom AEM Sling-Framework verwaltet werden. Das folgende Diagramm zeigt diese Einrichtung:

![Architektur](assets/architecture.png)

Die Architektur für AEM Forms beinhaltet die folgenden Komponenten:

* **Kern-AEM-Dienste:** Grundlegende Dienste, die von AEM für eine bereitgestellte Anwendung verfügbar gemacht werden. Zu diesen Diensten gehören ein JCR-kompatibles Inhalts-Repository, ein OSGI-Dienstcontainer, eine Workflow-Engine, ein Trust Store, ein Schlüsselspeicher usw. Diese Dienste sind für die AEM Forms-Anwendung verfügbar, werden aber nicht von AEM Forms-Paketen bereitgestellt. Diese Dienste sind integraler Bestandteil des AEM-Gesamtstapels und verschiedene AEM Forms-Komponenten verwenden diese Dienste.
* **** Forms-Dienste: Stellen Sie formularbezogene Funktionen bereit, wie z. B. das Erstellen, Zusammenstellen, Verteilen und Archivieren von PDF-Dokumenten, das Hinzufügen digitaler Signaturen, um den Zugriff auf Dokumente zu beschränken, und das Dekodieren von Formularen mit Strichcode. Diese Dienste sind öffentlich für den Gebrauch durch benutzerdefinierten Code verfügbar, der in AEM gemeinsam bereitgestellt wird.
* **Weblayer:** JSPs oder Servlets, die auf allgemeine Dienste oder Formulardienste aufgesetzt wurden und folgende Funktionalität bieten:

   * **Authoring-Frontend**: Eine Benutzeroberfläche zum Erstellen und Verwalten von Formularen.
   * **Formularwiedergabe und -übermittlungs-Frontend**: Eine Benutzeroberfläche für Endbenutzer von AEM Forms (z. B. Bürger, die auf eine Behördenseite zugreifen). Dadurch werden Formularwiedergaben (Formular in einem Webbrowser anzeigen) und Sendefunktionen bereitgestellt.
   * **REST APIs**: JSPs und Servlets exportieren einen Teil der Formulardienste zur Nutzung durch HTTP-basierte Clients wie das SDK für mobile Formulare.

**** AEM Forms auf OSGi: Bei einer AEM Forms on OSGi-Umgebung handelt es sich um eine standardmäßige AEM Author- oder AEM Publish-Umgebung mit AEM Forms-Paket, das darauf bereitgestellt ist. You can run AEM Forms on OSGi in a [single server environment, Farm, and clustered setups](/help/sites-deploying/recommended-deploys.md). Cluster-Setup ist nur für AEM Author-Instanzen verfügbar.

**** AEM Forms on JEE: AEM Forms on JEE ist ein AEM Forms-Server, der auf einem JEE-Stapel ausgeführt wird. Es verfügt über AEM Author mit Add-On-Paketen für AEM Forms und zusätzliche AEM Forms JEE-Funktionen, die auf einem einzelnen JEE-Stapel, der auf einem Anwendungsserver ausgeführt wird, gemeinsam bereitgestellt werden. Sie können AEM Forms on JEE in Einzelserver- und Clusterkonfigurationen ausführen. AEM Forms on JEE ist nur zum Ausführen von Document Security, Process Management und zum Aktualisieren auf AEM Forms für LiveCycle-Kunden erforderlich. Im Folgenden finden Sie einige weitere Szenarien zur Verwendung von AEM Forms on JEE:

* **** Unterstützung von HTML Workspace (für Kunden, die HTML Workspace verwenden): AEM Forms on JEE aktiviert Single Sign-On mit Verarbeitungsinstanzen, stellt bestimmte Assets bereit, die auf Verarbeitungsinstanzen gerendert werden, und verarbeitet die Übermittlung von Formularen, die im HTML Workspace wiedergegeben werden.
* **Erweiterte Verarbeitung zusätzlicher Formular-/interaktiver Kommunikationsdaten**: Mit AEM Forms on JEE können in komplexen Anwendungsfällen, in denen erweiterte Prozessverwaltungsfunktionen erforderlich sind, zusätzlich Formular-/interaktive Kommunikationsdaten verarbeitet (und die Ergebnisse in einem geeigneten Datenspeicher gespeichert) werden.

AEM Forms on JEE enthält außerdem die folgenden Dienste, die AEM-Komponenten unterstützen:

* **** Integrierte Benutzerverwaltung: Ermöglicht Benutzern von AEM Forms on JEE die Erkennung als AEM Forms on OSGi-Benutzer und die Aktivierung der einmaligen Anmeldung für OSGi- und JEE-Benutzer. Dies ist in Szenarien erforderlich, in denen eine einmalige Anmeldung zwischen AEM Forms on OSGi und AEM Forms on JEE erforderlich ist (z. B. HTML Workspace).
* **** Asset-Hosting: AEM Forms on JEE kann Assets (z. B. HTML5-Formulare) bereitstellen, die auf AEM Forms on OSGi wiedergegeben werden.

Die Authoring-Benutzeroberfläche von AEM Forms unterstützt nicht das Erstellen von DOR (Document of Record), PDF Forms und HTML5-Formularen. Solche Assets werden mit der eigenständigen Forms Designer-Anwendung entwickelt und einzeln in AEM Forms Manager hochgeladen. Alternativ können Formulare für AEM Forms on JEE als Anwendungselemente (in AEM Forms Workbench) entworfen und auf dem AEM Forms on JEE-Server bereitgestellt werden.

AEM Forms on OSGi und AEM Forms on JEE verfügen beide über Workflow-Funktionen. Sie können einfache Workflows für verschiedene Aufgaben auf AEM Forms on OSGi schnell erstellen und bereitstellen, ohne die vollständige Prozessverwaltungsfunktion von AEM Forms on JEE installieren zu müssen. Die [Funktionen des formularzentrierten Workflows auf AEM Forms on OSGi und die Prozessverwaltungsfunktionen von AEM Forms on JEE](/help/forms/using/capabilities-osgi-jee-workflows.md)unterscheiden sich in gewissem Maße. Die Entwicklung und Verwaltung formularorientierter Workflows auf AEM Forms on OSGi verwendet die vertrauten AEM Workflow- und AEM Inbox-Funktionen.

## Terminologie {#terminologies}

Das folgende Bild zeigt verschiedene AEM Forms-Serverkonfigurationen und ihre Komponenten, die in einer typischen AEM Forms-Bereitstellung verwendet werden: 

![aem_forms_-_recommendations_dtopology](assets/aem_forms_-_recommendedtopology.png)

**Autor:** Eine Autoreninstanz ist ein AEM Forms-Server, der im Standardmodus „Autor“ ausgeführt wird. Dies kann AEM Forms on JEE oder AEM Forms on OSGi-Umgebung sein. Dies ist für interne Benutzer, Designer von Formularen und interaktiver Kommunikation und Entwickler vorgesehen. Ermöglicht werden folgende Funktionen:

* **Erstellen und Verwalten von Formularen und interaktiver Kommunikation:** Designer und Entwickler können adaptive Formulare und interaktive Kommunikation erstellen und bearbeiten, extern erstellte Formulare anderer Art, z. B. in Adobe Forms Designer erstellte Formulare, hochladen und diese Elemente mithilfe der Forms Manager-Konsole verwalten.
* **Veröffentlichen von Formularen und interaktiver Kommunikation:** In einer Autoreninstanz gehostete Assets können in einer Veröffentlichungsinstanz veröffentlicht werden, um Laufzeitvorgänge durchzuführen. Asset-Veröffentlichung verwendet die Replikationsfunktionen von AEM. Adobe empfiehlt, auf jeder Autoreninstanz einen Replikationsagenten für die manuelle Übertragung von veröffentlichten Formularen an die Verarbeitungsinstanzen und auf jeder Verarbeitungsinstanz einen Replikationsagenten mit aktiviertem Auslöser *Bei Empfang* zu konfigurieren, damit die empfangenen Formulare automatisch zur Veröffentlichung repliziert werden.

**** Veröffentlichen: Eine Veröffentlichungsinstanz ist ein AEM Forms-Server, der im Standard-Veröffentlichungsmodus ausgeführt wird. Veröffentlichungsinstanzen sind für Endbenutzer von formularbasierten Anwendungen vorgesehen, z. B. Benutzer, die auf eine öffentliche Website zugreifen und Formulare senden. Ermöglicht werden folgende Funktionen:

* Rendern und Senden von Formularen für Endbenutzer.
* Transport unbearbeiteter gesendeter Formulardaten zur weiteren Verarbeitung an Verarbeitungsinstanzen und zum Speichern im endgültigen Aufzeichnungssystem. Die Standardimplementierung in AEM Forms erreicht dies mit den von AEM bereitgestellten Funktionen zur Rückwärtsreplikation. Eine alternative Implementierung ist auch das direkte Weiterleiten der Formulardaten an Verarbeitungsserver, anstatt sie zuerst lokal zu speichern (letzteres ist eine Voraussetzung für die Aktivierung der Rückwärtsreplikation ). Customers having concerns about storage of potentially sensitive data on publish instances can go in for this [alternative implementation](/help/forms/using/configuring-draft-submission-storage.md), since processing instances typically lie in a more secure zone.
* Wiedergabe und Senden interaktiver Kommunikation und Briefe: Interaktive Kommunikation und Brief werden in Veröffentlichungsinstanzen gerendert und entsprechende Daten werden zur Speicherung und Nachbearbeitung an Verarbeitungsinstanzen gesendet. Die Daten können entweder lokal in einer Veröffentlichungsinstanz gespeichert und später an eine Verarbeitungsinstanz rückrepliziert (Standardoption) oder ohne Speicherung auf der Veröffentlichungsinstanz direkt an die Verarbeitungsinstanz gesendet wrden. Die letztere Implementierung ist für sicherheitsbewusste Kunden nützlich.

**** Verarbeitung: Eine Instanz von AEM Forms, die im Ausführungsmodus &quot;Autor&quot;ausgeführt wird, ohne dass Benutzer der Forms-Manager-Gruppe zugewiesen sind. Sie können AEM Forms on JEE oder AEM Forms on OSGi als Verarbeitungsinstanz bereitstellen. Den Benutzern wird nicht zugewiesen, um sicherzustellen, dass Authoring- und Verwaltungsaktivitäten nicht auf der Verarbeitungsinstanz und nur auf der Autoreninstanz ausgeführt werden. Eine Verarbeitungsinstanz ermöglicht die folgenden Funktionen:

* **** Verarbeitung von Formularrohdaten aus einer Veröffentlichungsinstanz: Dies wird hauptsächlich auf einer Verarbeitungsinstanz über AEM-Workflows erreicht, die ausgelöst werden, wenn die Daten eingehen. Die Workflows können den vordefinierten Schritt des Formulardatenmodells verwenden, um die Daten oder Dokumente in einem geeigneten Datenspeicher zu archivieren.
* **Sicheres Speichern der Formulardaten**: Die Verarbeitung bietet ein hinter der Firewall befindliches Repository für Formularrohdaten, auf das die Benutzer keinen Zugriff haben. Weder Formularentwickler in der Autoreninstanz noch Endbenutzer in der Veröffentlichungsinstanz können auf dieses Repository zugreifen.

   >[!NOTE]
   >
   > Adobe empfiehlt die Verwendung eines Drittanbieter-Datenspeichers zum Speichern der endgültigen verarbeiteten Daten, anstatt das AEM-Repository zu verwenden.

* **** Speichern und Nachbearbeiten von Korrespondenzdaten, die von einer Veröffentlichungsinstanz eingehen: AEM-Workflows führen die optionale Nachbearbeitung der entsprechenden Briefdefinitionen durch. Diese Workflows können die endgültigen verarbeiteten Daten in geeigneten externen Datenspeichern speichern. 

* **HTML Workspace-Hosting**: Eine Verarbeitungsinstanz hostet das Frontend für HTML Workspace. HTML Workspace bietet die Benutzeroberfläche für die zugewiesene Aufgabe/Gruppenzuweisung für Review- und Genehmigungsprozesse.

Eine Verarbeitungsinstanz ist für die Ausführung im Autorenmodus konfiguriert, da:

* Dies ermöglicht die Rückwärtsreplikation von Formularrohdaten aus der Veröffentlichungsinstanz. Der standardmäßige Datenspeicherhandler erfordert die Funktion zur Rückwärtsreplikation.
* Es wird empfohlen, AEM-Workflows, die die Hauptmethode zur Verarbeitung von Formularrohdaten sind, die von einer Veröffentlichungsinstanz stammen, auf einem Autorensystem auszuführen.

## Physiche Beispieltopologien für AEM Forms on JEE {#sample-physical-topologies-for-aem-forms-on-jee}

Die unten empfohlenen AEM Forms on JEE-Topologien richten sich vor allem an Kunden, die ein Upgrade von LiveCycle oder einer früheren Version von AEM Forms on JEE durchführen. Adobe empfiehlt die Verwendung von AEM Forms on OSGi für neue Installationen. Eine Neuinstallation von AEM Forms on JEE wird nur für die Verwendung von Document Security- und Process Management-Funktionen empfohlen.

### Topologie für die Verwendung von Document Services oder Document Security-Funktionen {#topology-for-using-document-services-or-document-security-capabilities}

AEM Forms-Kunden, die nur Dokumentdienste oder Document Security-Funktionen verwenden möchten, können eine ähnliche Topologie nutzen wie die unten abgebildete. Diese Topologie empfiehlt die Verwendung einer einzelnen Instanz von AEM Forms. Sie können bei Bedarf auch einen Cluster oder eine Farm der AEM Forms-Server erstellen. Diese Topologie wird empfohlen, wenn die meisten Benutzer programmgesteuert auf die Funktionen des AEM Forms-Servers zugreifen und die Intervention über die Benutzeroberfläche minimal ist. Die Topologie ist bei der Stapelverarbeitung von Document Services hilfreich. Verwenden Sie beispielsweise den Ausgabedienst, um täglich Hunderte von nicht bearbeitbaren PDF-Dokumenten zu erstellen.

Obwohl Sie mit AEM Forms alle Funktionen von einem einzelnen Server aus einrichten und ausführen können, sollten Sie dennoch Kapazitätsplanung, Lastenausgleich und die Einrichtung dedizierter Server für bestimmte Funktionen in einer Produktionsumgebung durchführen. Für eine Umgebung, in der beispielsweise mit dem PDF Generator-Dienst Tausende von Seiten pro Tag konvertiert und digitale Signaturen hinzugefügt werden, um den Zugriff auf Dokumente zu beschränken, richten Sie separate AEM Forms-Server für den PDF Generator-Dienst und die Funktionen für digitale Signaturen ein. Dies bietet optimale Leistung und skaliert die Server unabhängig voneinander.

![Basisfunktionen](assets/basic-features.png)

### Topology for using AEM Forms process management {#topology-for-using-aem-forms-process-management}

AEM Forms-Kunden, die AEM Forms-Prozessverwaltungsfunktionen verwenden möchten, können z. B. HTML Workspace über eine Topologie verfügen, die der unten angezeigten ähnelt. Der AEM Forms on JEE-Server kann sich in einer einzelnen Server- oder Clusterkonfiguration befinden.

Wenn Sie eine Aktualisierung von LiveCycle ES4 durchführen, entspricht diese Topologie genau dem, was Sie bereits in LiveCycle haben, mit Ausnahme der Tatsache, dass AEM Author integriert zu AEM Forms on JEE hinzugefügt wurde. Darüber hinaus ändern sich die Clusteranforderungen für Kunden, die ein Upgrade durchführen, nicht. Wenn Sie AEM Forms in einer Clusterumgebung verwenden, können Sie diese in AEM 6.5 Forms fortsetzen. Bei einer Neuinstallation von AEM Forms of JEE für die Verwendung von HTML Workspace ist das Ausführen der in der JEE-Umgebung integrierten AEM-Autoreninstanz eine zusätzliche Anforderung.

Der Formulardatenspeicher ist ein Drittanbieter-Datenspeicher, der zum Speichern der endgültigen verarbeiteten Daten von Formularen und interaktiver Kommunikation verwendet wird. Dies ist ein optionales Element in der Topologie. Sie können auch eine Verarbeitungsinstanz einrichten und bei Bedarf ihr Repository als finales Aufzeichnungssystem verwenden.

![topology_for_usinghtmlworkspace_formsApp](assets/topology_for_usinghtmlworkspaceandformsapp.png)

Die Topologie wird Kunden empfohlen, die planen, den AEM Forms on JEE-Server für Prozessverwaltungsfunktionen (HTML Workspace) zu verwenden, ohne dass nachbearbeitende adaptive Formulare, HTML5-Formulare und interaktive Kommunikationsfunktionen verwendet werden.

### Topologie für die Verwendung adaptiver Formulare, HTML5-Formulare, interaktive Kommunikationsfunktionen {#topology-for-using-adaptive-forms-html-forms-interactive-communication-capabilities}

AEM Forms-Kunden, die AEM Forms-Datenerfassungsfunktionen verwenden möchten, z. B. adaptive Formulare, HTML5 Formulare, PDF-Formulare, können eine ähnliche Topologie nutzen wie die unten abgebildete. Diese Topologie wird auch für die Verwendung der interaktiven Kommunikationsfunktionen von AEM Forms empfohlen.

![topology-for-using-forms-osgi-modules](assets/topology-for-using-forms-osgi-modules.png)

Sie können die folgenden Änderungen/Anpassungen an der oben vorgeschlagenen Topologie vornehmen:

* Für die Verwendung von HTML Workspace und der AEM Forms-App ist ein AEM-Autor oder eine Verarbeitungsinstanz erforderlich. Sie können die AEM-Autoreninstanz verwenden, die in AEM Forms on JEE-Server integriert ist, anstatt einen zusätzlichen externen AEM-Autorenserver einzurichten.
* Eine AEM-Instanz im Autorenmodus oder für die Verarbeitung ist nur für formularorientierte Workflows auf OSGi, adaptiven Formularen, Formularportalen und interaktiver Kommunikation erforderlich.
* Die Oberfläche für interaktive Kommunikationsagenten wird im Allgemeinen innerhalb des Unternehmens ausgeführt. Sie können also einen Veröffentlichungsserver für die Agent-Benutzeroberfläche im privaten Netzwerk belassen.
* Die auf dem AEM Forms on JEE-Server integrierte AEM Forms on OSGi-Instanz kann auch formularzentrierte Workflows auf OSGi und überwachten Ordnern ausführen.

## Beispiele für physikalische Topologien für die Verwendung von AEM Forms on OSGi {#sample-physical-topologies-for-using-aem-forms-on-osgi}

### Topology for data capture, interactive communication, Form-Centric Workflow on OSGi capabilities {#topology-for-data-capture-interactive-communication-form-centric-workflow-on-osgi-capabilities}

AEM Forms-Kunden, die AEM Forms-Datenerfassungsfunktionen verwenden möchten, z. B. adaptive Formulare, HTML5 Formulare, PDF-Formulare, können eine ähnliche Topologie nutzen wie die unten abgebildete. Diese Topologie wird auch für die Verwendung interaktiver Kommunikation und formularzentrierte Workflows für OSGi empfohlen, z. B. für die Verwendung von AEM Inbox und AEM Forms App für Geschäftsprozess-Workflows.

![interactive-use-case-af-cm-osgi-workflow](assets/interactive-use-cases-af-cm-osgi-workflow.png)

### Topologie für die Verwendung von Funktionen für überwachte Ordner für die Offline-Stapelverarbeitung {#topology-for-using-watched-folder-capabilities-for-offline-batch-processing}

AEM Forms-Kunden, die überwachte Ordner für die Stapelverarbeitung verwenden möchten, können eine ähnliche Topologie wie die unten gezeigte nutzen. Die Topologie zeigt eine Clusterumgebung an, Sie entscheiden sich jedoch, je nach Laden eine einzelne Instanz oder eine Farm der AEM Forms-Server zu verwenden. Die Drittanbieter-Datenquelle ist Ihr eigenes System von Datensätzen. Es fungiert als Eingabequelle für überwachte Ordner. Die Topologie zeigt auch die Ausgabe in Form einer gedruckten Datei an. Sie können den Ausgabeinhalt auch in einem Dateisystem speichern, per E-Mail senden und andere benutzerdefinierte Methoden verwenden, um die Ausgabe zu nutzen.

![offline-batch-processing-via-watched-folders](assets/offline-batch-processing-via-watched-folders.png)

### Topologie für die Verwendung von Document Service-Funktionen für die API-basierte Offline-Verarbeitung {#topology-for-using-document-services-capabilities-for-offline-api-based-processing}

AEM Forms-Kunden, die nur Document Services-Funktionen verwenden möchten, können eine ähnliche Topologie wie die unten angezeigte nutzen. Für diese Topologie empfiehlt sich die Verwendung eines Clusters von AEM Forms auf OSGi-Servern. Diese Topologie wird empfohlen, wenn die meisten Benutzer programmatisch (über APIs) auf die Funktionen des AEM Forms-Servers zugreifen und das Eingreifen über die Benutzeroberfläche minimal ist. Die Topologie ist in mehreren Software-Client-Szenarien sehr hilfreich. Beispiel: Mehrere Clients, die PDF Generator-Dienst verwenden, um PDF-Dokumente bei Bedarf zu erstellen.

Obwohl Sie in AEM Forms alle Funktionen von einem einzelnen Server einrichten und ausführen können, sollten Sie Kapazitätsplanung und Lastenausgleich durchführen und dedizierte Server für bestimmte Funktionen in einer Produktionsumgebung festlegen. So sollten Sie beispielsweise in einer Umgebung, in der mit dem PDF-Generator-Dienst Tausende von Seiten pro Tag konvertiert und mithilfe mehrerer adaptiver Formulare Daten erfasst werden, separate AEM Forms-Server für den PDF Generator-Dienst und adaptive Formularfunktionen einrichten. Dies bietet optimale Leistung und skaliert die Server unabhängig voneinander.

![offline-api-based-processing](assets/offline-api-based-processing.png)

