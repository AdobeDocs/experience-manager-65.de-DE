---
title: Architektur und Bereitstellungstopologien für AEM Forms
seo-title: Architecture and deployment topologies for AEM Forms
description: Architekturdetails für AEM Forms und empfohlene Topologien für neue und bestehende AEM und Kunden, die ein Upgrade von LiveCycle ES4 auf AEM Forms durchführen.
seo-description: Architecture details for AEM Forms and recommended topologies for new and existing AEM customers and customers upgrading from LiveCycle ES4 to AEM Forms.
uuid: 90baa57a-4785-4b49-844c-a44717d3c12d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 0156b5c3-3bef-4213-9ada-c7b6ae96ada4
role: Admin
exl-id: d4421d46-cfc9-424e-8a88-9d0a2994a5cf
source-git-commit: 1683338f02d01d5d9843368955fa42f309718f26
workflow-type: tm+mt
source-wordcount: '2481'
ht-degree: 83%

---

# Architektur und Bereitstellungstopologien für AEM Forms {#architecture-and-deployment-topologies-for-aem-forms}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/aem-forms-cloud-service-architecture.html) |
| AEM 6.5 | Dieser Artikel |

## Architektur {#architecture}

AEM Forms ist eine Anwendung, die in AEM als AEM bereitgestellt wird. Das Paket wird als AEM Forms Add-On-Paket bezeichnet. AEM Forms-Pakete enthalten sowohl Services (API-Anbieter), die im AEM OSGI-Container bereitgestellt werden, als auch Servlets (die Frontend- und REST-API-Funktion bereitstellen), die über das AEM Sling-Framework verwaltet werden. Das folgende Diagramm zeigt diese Einrichtung:

![Architektur](assets/architecture.png)

Die Architektur für AEM Forms umfasst die folgenden Komponenten:

* **Hauptdienste AEM:** Grundlegende Dienste, die für eine bereitgestellte Anwendung bereitgestellt AEM. Zu den Services gehören ein JCR-kompatibles Inhalts-Repository, ein OSGi-Service-Container, eine Workflow-Engine, ein Trust Store, ein Key Store usw. Diese Services sind für die AEM Forms-Anwendung verfügbar, werden aber nicht von AEM Forms-Paketen bereitgestellt. Die Services sind ein integraler Bestandteil des gesamten AEM-Stapels und verschiedene AEM Forms-Komponenten verwenden diese Services.
* **Formular-Services:** Stellen formularbezogene Funktionen bereit, z. B. das Erstellen, Zusammenführen, Verteilen und Archivieren von PDF-Dokumenten, das Hinzufügen digitaler Signaturen zum Beschränken des Zugriffs auf Dokumente und das Dekodieren von Barcode-Formularen. Viele dieser Services sind öffentlich für die Nutzung durch benutzerdefinierten Code verfügbar, der in AEM bereitgestellt wird.
* **Weblayer:** JSPs oder Servlets, die auf allgemeine Services oder Formular-Services aufgesetzt wurden und folgende Funktionalität bieten:

   * **Authoring-Frontend**: Eine Benutzeroberfläche zum Erstellen und Verwalten von Formularen.
   * **Formularwiedergabe und -übermittlungs-Frontend**: Eine Benutzeroberfläche für Endbenutzer, die von Endbenutzern der AEM Forms verwendet werden kann (z. B. Bürger, die auf eine Behördenseite zugreifen). Dadurch werden Formularwiedergabe (Formular in einem Webbrowser anzeigen) und Sendefunktionen bereitgestellt.
   * **REST APIs**: JSPs und Servlets exportieren einen Teil der Formula-Services zur Nutzung durch HTTP-basierte Clients wie das SDK für mobile Formulare.

**AEM Forms on OSGi:** Bei einer AEM Forms on OSGi-Umgebung handelt es sich um ein standardmäßiges AEM-Autor- oder AEM-Veröffentlichungspaket, auf dem das AEM Forms-Paket bereitgestellt ist. Sie können AEM Forms on OSGi in [Einzel-Server-Umgebungen, Farm- und Cluster-Setups ausführen](/help/sites-deploying/recommended-deploys.md). Die Cluster-Setup ist nur für AEM Autoreninstanzen verfügbar. 

**AEM Forms on JEE:** AEM Forms on JEE ist ein AEM Forms-Server, der auf dem JEE-Stapel ausgeführt wird. Es verfügt über AEM Author mit AEM Forms-Add-On-Pakete und zusätzliche AEM Forms JEE-Funktionen, die gemeinsam auf einem einzigen JEE-Stapel bereitgestellt werden, der auf einem Anwendungs-Server ausgeführt wird. Sie können AEM Forms on JEE in Einze-Server- und Cluster-Setups ausführen. AEM Forms on JEE ist nur für Dokumentensicherheit, Prozessmanagement und LiveCycle-Kunden, die auf AEM Forms aktualisieren, erforderlich. Im Folgenden finden Sie einige zusätzliche Szenarien für die Verwendung von AEM Forms on JEE:

* **HTML Workspace-Unterstützung (für Kunden, die HTML Workspace verwenden)**: AEM Forms on JEE ermöglicht Single Sign-on auf Verarbeitungsinstanzen, unterstützt bestimmte auf Verarbeitungsinstanzen wiedergegebene Assets und verwaltet das Übermitteln von Formularen, die in HTML Workspace wiedergegeben werden.
* **Erweiterte zusätzliche Verarbeitung von Formular-/interaktiven Kommunikationsdaten**: AEM Forms on JEE kann bei anspruchsvollen Anwendungsfällen, die eine erweiterte Prozessverwaltung erfordern, zur zusätzlichen Verarbeitung von Formular- bzw. interaktiven Kommunikationsdaten (und zum Speichern der Ergebnisse in einem geeigneten Datenspeicher) verwendet werden.

AEM Forms on JEE umfasst auch die folgenden unterstützenden Services für die AEM Komponenten:

* **Integriertes Benutzermanagement:** Ermöglicht die Erkennung von Benutzern von AEM Forms on JEE als AEM Formulare on OSGi-Benutzern und die Aktivierung von SSO für OSGi- und JEE-Benutzer. Dies ist in Fällen erforderlich, in denen Single Sign-on für AEM Forms on JEE und AEM Forms-Add-On on OSGi erforderlich ist (z. B. HTML Workspace).
* **Asset-Hosting:** AEM Forms on JEE kann Assets (z. B. HTML5-Formulare) bereitstellen, die auf AEM Forms on OSGi wiedergegeben werden.

Von der AEM Forms-Authoring-Benutzeroberfläche wird das Erstellen von Datensatzdokumenten (DOR), PDF-Formularen und HTML5-Formularen nicht unterstützt. Solche Assets werden mit der eigenständigen Forms Designer-Anwendung entworfen und einzeln in AEM Forms Manager hochgeladen. Alternativ können Formulare für AEM Forms on JEE als Anwendungs-Assets (in AEM Forms Workbench) entworfen und auf dem AEM Forms on JEE-Server bereitgestellt werden.

Sowohl AEM Forms on OSGi als auch AEM Forms on JEE verfügen über Workflow-Funktionen. Sie können grundlegende Workflows für verschiedene Aufgaben in AEM Forms on OSGi schnell erstellen und bereitstellen, ohne die vollständige Prozessverwaltungsfunktion von AEM Forms on JEE installieren zu müssen. Die [Funktionen des formularzentrierten Workflows in AEM Forms on OSGi und Prozessverwaltungsfunktionen von AEM Forms on JEE](capabilities-osgi-jee-workflows.md) unterscheiden sich etwas. Für Bereitstellung und Verwaltung der formularzentrierten Workflows in AEM Forms on OSGi werden die gewohnten Funktionen von AEM-Workflow und AEM-Posteingang verwendet.

## Begriffe {#terminologies}

Das folgende Bild zeigt verschiedene AEM Forms-Server-Konfigurationen und ihre Komponenten, die in einer typischen AEM Forms-Bereitstellung verwendet werden: 

![aem_forms_-_recommendedtopology](assets/aem_forms_-_recommendedtopology.png)

**Autor:** Eine Autoreninstanz ist ein AEM Forms-Server, der im Standardmodus „Autor“ ausgeführt wird. Dies kann AEM Forms on JEE oder AEM Forms in einer OSGi-Umgebung sein. Sie ist für interne Benutzer, Formularentwickler und Entwickler interaktiver Kommunikation gedacht. Ermöglicht werden folgende Funktionen:

* **Erstellen und Verwalten von Formularen und interaktiver Kommunikation:** Designer und Entwickler können adaptive Formulare und interaktive Kommunikation erstellen und bearbeiten, extern erstellte Formulare anderer Art, z. B. in Adobe Forms Designer erstellte Formulare, hochladen und diese Elemente mithilfe der Forms Manager-Konsole verwalten.
* **Veröffentlichen von Formularen und interaktiver Kommunikation:** Auf einer Autoreninstanz gehostete Assets können in einer Veröffentlichungsinstanz veröffentlicht werden, um Laufzeitvorgänge durchzuführen. Die Asset-Veröffentlichung verwendet AEM Replikationsfunktionen. Adobe empfiehlt, in jeder Autoreninstanz einen Replikationsagenten für die manuelle Übertragung von veröffentlichten Formularen an die Verarbeitungsinstanzen und in jeder Verarbeitungsinstanz einen Replikationsagenten mit aktiviertem Auslöser *Bei Empfang* zu konfigurieren, damit die empfangenen Formulare automatisch zur Veröffentlichung repliziert werden.

**Veröffentlichen:** Eine Veröffentlichungsinstanz ist ein AEM Forms-Server, der im Standardmodus „Veröffentlichen“ ausgeführt wird. Veröffentlichungsinstanzen sind für Endbenutzer formularbasierter Anwendungen vorgesehen, z. B. Benutzer, die auf eine öffentliche Website zugreifen und Formulare senden. Ermöglicht werden folgende Funktionen:

* Rendern und Senden von Forms für Endbenutzer
* Transport von Formularrohdaten zur Verarbeitung an Instanzen zur weiteren Verarbeitung und Speicherung im endgültigen Aufzeichnungssystem. Die in AEM Forms bereitgestellte Standardimplementierung erreicht dies mithilfe der Reverse-Replizierungsfunktionen von AEM. Eine alternative Implementierung ist auch das direkte Senden der Formulardaten an Verarbeitungsserver, anstatt sie zunächst lokal zu speichern (letzteres ist eine Voraussetzung für die Aktivierung der Rückwärtsreplikation). Kunden, die Bedenken bei der Speicherung potenziell vertraulicher Daten auf Veröffentlichungsinstanzen haben, können diese [alternative Implementierung](/help/forms/using/configuring-draft-submission-storage.md) wählen, da die Verarbeitung üblicherweise in einer sichereren Zone erfolgt.
* Rendern und Übermitteln von interaktiven Kommunikationen und Briefen: Eine interaktive Kommunikation und Briefe werden auf Veröffentlichungsinstanzen gerendert und die entsprechenden Daten werden zur Speicherung und Nachbearbeitung an Verarbeitungsinstanzen übermittelt. Die Daten können entweder lokal in einer Veröffentlichungsinstanz gespeichert und später an eine Verarbeitungsinstanz rückrepliziert (Standardoption) oder ohne Speicherung auf der Veröffentlichungsinstanz direkt an die Verarbeitungsinstanz gesendet werden. Letztere Implementierung ist für sicherheitsbewusste Kunden nützlich.

**Verarbeitung:** Eine Instanz von AEM Forms, die im Autorenmodus ausgeführt wird, wobei kein Benutzer der Gruppe „forms-manager“ zugewiesen ist. Sie können AEM Forms on JEE oder AEM Forms on OSGi als Verarbeitungsinstanz bereitstellen. Die Benutzer werden nicht zugewiesen, um sicherzustellen, dass Formularerstellungs- und -verwaltungsaktivitäten nicht in der Verarbeitungsinstanz ausgeführt werden, sondern nur in der Autoreninstanz stattfinden. Eine Verarbeitungsinstanz ermöglicht die folgenden Funktionen:

* **Die Verarbeitung von Formularrohdaten aus der Veröffentlichungsinstanz:** Dies wird hauptsächlich auf der Verarbeitungsinstanz über AEM-Workflows erreicht, die ausgelöst werden, wenn die Daten eingehen. Die Workflows können den standardmäßig bereitgestellten Schritt „Formulardatenmodell“ verwenden, um die Daten oder Dokumente in einem geeigneten Datenspeicher zu archivieren.
* **Sicheres Speichern der Formulardaten**: Die Verarbeitung bietet ein hinter der Firewall befindliches Repository für Formularrohdaten, auf das die Benutzer keinen Zugriff haben. Weder Formular-Designer in der Autoreninstanz noch Endbenutzer in der Veröffentlichungsinstanz können auf dieses Repository zugreifen.

  >[!NOTE]
  >
  >Adobe empfiehlt die Verwendung eines Datenspeichers von Drittanbietern zum Speichern abgeschlossener verarbeiteter Daten, anstatt AEM Repository zu verwenden.

* **Speicherung und Nachbearbeitung von Korrespondenzdaten aus einer Veröffentlichungsinstanz:** AEM-Workflows führen die optionale Nachbearbeitung der entsprechenden Briefdefinitionen durch. Diese Workflows können die endgültigen verarbeiteten Daten in geeigneten externen Datenspeichern speichern. 

* **HTML Workspace-Hosting**: Eine Verarbeitungsinstanz hostet das Frontend für HTML Workspace. HTML Workspace bietet die Benutzeroberfläche für die zugehörige Aufgaben-/Gruppenzuweisung für Prüfungs- und Genehmigungsprozesse.

Eine Verarbeitungsinstanz wurde aus folgenden Gründen für die Ausführung im Autorenmodus konfiguriert:

* Dies ermöglicht die Rückwärtsreplikation von Formularrohdaten aus der Veröffentlichungsinstanz. Der standardmäßige Datenspeicher-Handler benötigt die Rückwärtsreplikationsfunktion.
* Es wird empfohlen, dass AEM-Workflows (die Hauptmethode zur Verarbeitung von Formularrohdaten aus der Veröffentlichungsinstanz) auf einem Autorensystem ausgeführt werden.

## Physische Beispieltopologien für AEM Forms on JEE {#sample-physical-topologies-for-aem-forms-on-jee}

Die unten empfohlenen AEM Forms on JEE-Topologien richten sich vor allem an Kunden, die ein Upgrade von LiveCycle oder einer früheren Version von AEM Forms on JEE durchführen. Adobe empfiehlt für Neuinstallationen die Verwendung von AEM Forms on OSGi. Eine Neuinstallation von AEM Forms on JEE wird nur für die Verwendung von Document Security- und Process Management-Funktionen empfohlen.

### Topologie für die Verwendung von Document Services- oder Document Security-Funktionen {#topology-for-using-document-services-or-document-security-capabilities}

AEM Forms-Kunden, die ausschließlich Document Services oder Document Security-Funktionen verwenden möchten, können eine ähnliche Topologie wie die unten angezeigte haben. Für diese Topologie wird die Verwendung einer einzigen Instanz von AEM Forms empfohlen. Sie können bei Bedarf auch einen Cluster oder eine Farm von AEM Forms-Servern erstellen. Diese Topologie wird empfohlen, wenn die meisten Benutzer programmgesteuert (über APIs) auf die Funktionen des AEM Forms-Servers zugreifen und nur minimal über die Benutzeroberfläche eingegriffen wird. Die Topologie ist bei Stapelverarbeitungsvorgängen von Dokumenten-Services sehr hilfreich. Verwenden Sie beispielsweise den Ausgabe-Service, um täglich Hunderte von nicht bearbeitbaren PDF-Dokumenten zu erstellen.

Obwohl Sie in AEM Forms alle Funktionen auf einem einzelnen Server einrichten und von dort ausführen können, sollten Sie Kapazitätsplanung und Lastenausgleich berücksichtigen und dedizierte Server für bestimmte Funktionen in einer Produktionsumgebung einrichten. Für eine Umgebung, die den PDF Generator-Service zum Konvertieren von Tausenden von Seiten pro Tag und mehrere adaptive Formulare zum Erfassen von Daten verwendet, richten Sie beispielsweise separate AEM Forms-Server für den PDF Generator-Service und die Funktionen für adaptive Formulare ein. Dies erleichtert es, eine optimale Leistung zu erzielen und die Server unabhängig voneinander zu skalieren.

![basic-features](assets/basic-features.png)

### Topologie für die Verwendung der AEM Forms-Prozessverwaltung {#topology-for-using-aem-forms-process-management}

AEM Forms-Kunden, die AEM Forms-Prozessverwaltungsfunktionen, z. B. HTML Workspace, verwenden möchten, können eine ähnliche Topologie wie die unten abgebildete verwenden. Der AEM Forms on JEE-Server kann sich in einer Einzelserver- oder Cluster-Konfiguration befinden.

Wenn Sie ein Upgrade von LiveCycle ES4 durchführen, entspricht diese Topologie weitgehend dem, was Sie bereits in LiveCycle haben, mit Ausnahme des zusätzlichen AEM Author, das in AEM Forms on JEE integriert ist. Darüber hinaus ändern sich die Cluster-Anforderungen für Kunden, die ein Upgrade durchführen, nicht. Wenn Sie AEM Forms in einer Cluster-Umgebung verwenden, können Sie diese in AEM 6.5 Forms fortsetzen. Für eine Neuinstallation von AEM Forms von JEE zur Verwendung von HTML Workspace ist die Ausführung AEM in die JEE-Umgebung integrierten Autoreninstanz eine zusätzliche Voraussetzung.

Der Formulardatenspeicher ist ein Datenspeicher eines Drittanbieters, der zum Speichern von endgültig verarbeiteten Daten von Formularen und interaktiver Kommunikation verwendet wird. Dies ist ein optionales Element in der Topologie. Sie können sich auch dafür entscheiden, eine Verarbeitungsinstanz einzurichten und gegebenenfalls ihr Repository als endgültiges System für das System zu verwenden.

![topology_for_usinghtmlworkspaces eandformsapp](assets/topology_for_usinghtmlworkspaceandformsapp.png)

Die Topologie wird den Kunden empfohlen, die AEM Forms on JEE-Server für Prozessverwaltungsfunktionen (HTML Workspace) verwenden möchten, ohne Nachbearbeitung, adaptive Formulare, HTML5-Formulare und interaktive Kommunikationsfunktionen zu verwenden.

### Topologie für die Verwendung adaptiver Formulare, HTML5-Formulare, interaktive Kommunikationsfunktionen {#topology-for-using-adaptive-forms-html-forms-interactive-communication-capabilities}

AEM Forms-Kunden, die AEM Forms-Datenerfassungsfunktionen verwenden möchten, z. B. adaptive Formulare, HTML5-Formulare, PDF-Formulare, können eine ähnliche Topologie nutzen wie die unten abgebildete. Diese Topologie wird auch für die Verwendung interaktiver Kommunikationsfunktionen von AEM Forms empfohlen. 

![topology-for-using-forms-osgi-modules](assets/topology-for-using-forms-osgi-modules.png)

Sie können die folgenden Änderungen/Anpassungen an der oben vorgeschlagenen Topologie vornehmen:

* Für die Verwendung von HTML Workspace und das AEM Forms-Programm ist eine AEM Autoren- oder Verarbeitungsinstanz erforderlich. Sie können die AEM-Autoreninstanz verwenden, die in AEM Forms on JEE-Server integriert ist, anstatt einen zusätzlichen externen AEM-Autorenserver einzurichten.
* Eine AEM-Autoren- oder Verarbeitungsinstanz ist nur für Forms-orientierte Workflows in OSGi, adaptiven Formularen, Formularportalen und interaktiver Kommunikation erforderlich.
* Die Agent UI für interaktive Kommunikation wird in der Regel in der Organisation ausgeführt. Sie können also einen Veröffentlichungsserver für die Agent-Benutzeroberfläche im privaten Netzwerk behalten.
* AEM Forms on OSGi-Instanzen, die in AEM Forms auf JEE-Server integriert sind, können auch Forms-zentrierte Workflows in OSGi- und überwachten Ordnern ausführen.

## Beispiele für physikalische Topologien für die Verwendung von AEM Forms on OSGi {#sample-physical-topologies-for-using-aem-forms-on-osgi}

### Topologie für die Datenerfassung, interaktive Kommunikation, formularzentrierten Workflow on OSGi-Fähigkeiten {#topology-for-data-capture-interactive-communication-form-centric-workflow-on-osgi-capabilities}

AEM Forms-Kunden, die AEM Forms-Datenerfassungsfunktionen verwenden möchten, z. B. adaptive Formulare, HTML5-Formulare, PDF-Formulare, können eine ähnliche Topologie nutzen wie die unten abgebildete. Diese Topologie wird auch für die Verwendung interaktiver Kommunikation und formularzentrierte Workflows für OSGi empfohlen, z. B. für die Verwendung von AEM Inbox und AEM Forms Programm für Geschäftsprozess-Workflows.

![interactive-use-cases-af-cm-osgi-workflow](assets/interactive-use-cases-af-cm-osgi-workflow.png)

### Topologie für die Verwendung von Funktionen für überwachte Ordner für die Offline-Stapelverarbeitung {#topology-for-using-watched-folder-capabilities-for-offline-batch-processing}

AEM Forms-Kunden, die überwachte Ordner für die Stapelverarbeitung verwenden möchten, können über eine ähnliche Topologie wie die unten angezeigte verfügen. Die Topologie zeigt eine Cluster-Umgebung. Sie entscheiden sich jedoch je nach Auslastung, ob Sie eine einzelne Instanz oder eine Farm von AEM Forms Server verwenden. Die Datenquelle eines Drittanbieters ist Ihr eigenes Aufzeichnungssystem. Sie fungiert als Eingabequelle für überwachte Ordner. Die Topologie zeigt auch die Ausgabe in Form einer gedruckten Datei an. Sie können den Ausgabeinhalt auch in einem Dateisystem speichern, per E-Mail versenden und andere benutzerdefinierte Methoden verwenden, um die Ausgabe zu nutzen.

![offline-batch-processing-via-watched-folders](assets/offline-batch-processing-via-watched-folders.png)

### Topologie für die Verwendung von Document Services-Funktionen für die Offline-API-basierte Verarbeitung {#topology-for-using-document-services-capabilities-for-offline-api-based-processing}

AEM Forms-Kunden, die nur Document Services-Funktionen verwenden möchten, können über eine Topologie verfügen, die der unten dargestellten ähnelt. Diese Topologie empfiehlt die Verwendung eines Clusters von AEM Forms auf OSGi-Servern. Diese Topologie wird empfohlen, wenn die meisten Benutzer programmatisch (mithilfe von APIs) auf die AEM Forms-Server-Zugriffsfunktionen zugreifen und die Eingriffe über die Benutzeroberfläche minimal sind. Die Topologie ist in mehreren Software-Client-Szenarien sehr hilfreich. Beispiel: Mehrere Clients, die PDF Generator-Service verwenden, um PDF-Dokumente bei Bedarf zu erstellen.

Obwohl Sie in AEM Forms alle Funktionen von einem einzelnen Server einrichten und ausführen können, sollten Sie Kapazitätsplanung und Lastenausgleich durchführen und dedizierte Server für bestimmte Funktionen in einer Produktionsumgebung festlegen. So sollten Sie beispielsweise in einer Umgebung, in der mit dem PDF-Generator-Service Tausende von Seiten pro Tag konvertiert und mithilfe mehrerer adaptiver Formulare Daten erfasst werden, separate AEM Forms-Server für den PDF Generator-Service und adaptive Formularfunktionen einrichten. Dies erleichtert es, eine optimale Leistung zu erzielen und die Server unabhängig voneinander zu skalieren.

![offline-api-based-processing](assets/offline-api-based-processing.png)
