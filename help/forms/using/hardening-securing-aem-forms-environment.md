---
title: Härten (Absichern) und Schützen von AEM-Formularen in OSGi-Umgebungen
description: Hier finden Sie Empfehlungen und Best Practices zum Schutz von AEM Forms auf einem OSGi-Server.
topic-tags: Security
role: Admin,User
exl-id: 5da3cc59-4243-4098-b1e0-438304fcd0c5
solution: Experience Manager, Experience Manager Forms
feature: Document Security,Adaptive Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: ht
source-wordcount: '1434'
ht-degree: 100%

---

# Härten (Absichern) und Schützen von AEM-Formularen in OSGi-Umgebungen {#hardening-and-securing-aem-forms-on-osgi-environment}

Hier finden Sie Empfehlungen und Best Practices zum Schutz von AEM Forms auf einem OSGi-Server.

Der Schutz der Server-Umgebung ist von größter Wichtigkeit für ein Unternehmen. In diesem Artikel werden Empfehlungen und Best Practices für den Schutz der Server beschrieben, auf denen AEM Forms ausgeführt wird. Dieses Dokument stellt keine umfassende Anleitung zum Härten (Absichern) des Betriebssystems dar. Stattdessen wird in diesem Artikel eine Reihe von Einstellungen zum Stärken der Sicherheit beschrieben, die Sie implementieren sollten, um die Sicherheit der bereitgestellten Anwendung zu verbessern. Um den Schutz der Anwendungs-Server sicherzustellen, sollten Sie jedoch außer den in diesem Artikel empfohlenen Maßnahmen auch Überwachungs-, Erkennungs- und Reaktionsabläufe für die Sicherheit implementieren. Das Dokument enthält ferner Best Practices und Richtlinien zum Schützen von PII (Personally Identifiable Information, personenbezogene Informationen).

Die Zielgruppe dieses Artikels sind IT-Beraterinnen und -Berater, Sicherheitsfachkräfte, Systemarchitektinnen und Systemarchitekten sowie IT-Fachkräfte, die für die Planung der Anwendungs- oder Infrastrukturentwicklung sowie die Bereitstellung von AEM Forms verantwortlich sind. Zu diesen Rollen zählen die folgenden gängigen Rollen:

* IT- und Produktionsingenieurinnen und -ingenieure, die sichere Web-Anwendungen und -Server in ihren eigenen oder Kundenunternehmen bereitstellen müssen.
* Architekten und Systemplaner mit der Aufgabe, die Architekturentwicklung für die Kunden in ihren Unternehmen zu planen.
* Fachkräfte für IT-Sicherheit, die schwerpunktmäßig für die plattformübergreifende Sicherheit innerhalb ihrer Unternehmen zuständig sind.
* Beraterinnen und Berater von Adobe sowie Partner, die detaillierte Ressourcen für Kundschaft sowie Partner benötigen.

Die folgende Abbildung zeigt Komponenten und Protokolle, die in einer typischen AEM Forms-Bereitstellung verwendet werden, einschließlich der entsprechenden Firewall-Topologie:

![typical-architecture](assets/typical-architecture.png)

AEM Forms kann in hohem Maß angepasst und in vielen verschiedenen Umgebungen eingesetzt werden. Einige der Empfehlungen sind möglicherweise für Ihr Unternehmen nicht relevant.

## Sichere Transportebene {#secure-transport-layer}

Sicherheitslücken in der Transportebene gehören zu den Hauptbedrohungen für Internet- oder Intranet-orientierte Anwendungs-Server. In diesem Abschnitt wird der Prozess zum Absichern von Hostrechnern im Netzwerk gegen diese Schwachstellen beschrieben. Dabei geht es um die Netzwerksegmentierung, das Härten des TCP/IP-Stacks (Transmission Control Protocol/Internet Protocol) und die Verwendung von Firewalls für den Schutz des Hosts.

### Begrenzen offener Endpunkte  {#limit-open-endpoints}

In einem Unternehmen kann eine externe Firewall vorhanden sein, um den Zugriff zwischen den Endbenutzenden und der AEM Forms-Veröffentlichungsfarm zu begrenzen. Das Unternehmen kann außerdem eine interne Firewall verwenden, um den Zugriff zwischen einer Veröffentlichungsfarm und anderen unternehmensinternen Elementen (z. B. Autoreninstanz, Verarbeitungsinstanz, Datenbanken) zu begrenzen. Lassen Sie mithilfe von Firewalls den Zugriff auf eine begrenzte Anzahl von AEM Forms-URLs für Endbenutzer und zwischen den Elementen innerhalb des Unternehmens zu:

#### Konfigurieren der externen Firewall  {#configure-external-firewall}

Sie können eine externe Firewall konfigurieren, um für bestimmte AEM Forms-URLs den Zugriff auf das Internet zu erlauben. Der Zugriff auf diese URLs ist erforderlich zum Ausfüllen eines adaptiven Formulars, für HTML5, einen Correspondence Management-Brief oder die Anmeldung bei einem AEM Forms-Server:

<table> 
 <tbody>
  <tr>
   <td>Komponente</td> 
   <td>URI</td> 
  </tr>
  <tr>
   <td>Adaptive Formulare</td> 
   <td>
    <ul> 
     <li>/content/dam/formsanddocuments/AF_PATH/jcr:content</li> 
     <li>/etc/clientlibs/fd/</li> 
     <li>/content/forms/af/AF_PATH</li> 
     <li>/libs/granite/csrf/</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>HTML5-Formulare</td> 
   <td>
    <ul> 
     <li>/content/forms/formsets/profiles/</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Correspondence Management </td> 
   <td>
    <ul> 
     <li>/aem/forms/createcorrespondence* </li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Formularportal </td> 
   <td>
    <ul> 
     <li>/content/forms/portal/</li> 
     <li>/libs/cq/ui/widgets*</li> 
     <li>/libs/cq/security/</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td> AEM Forms-App</td> 
   <td>
    <ul> 
     <li>/j_security_check*</li> 
     <li>/soap/services/AuthenticationManagerService</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

#### Konfigurieren der internen Firewall  {#configure-internal-firewall}

Sie können die interne Firewall konfigurieren, um bestimmten Komponenten von AEM Forms (z. B. Autoreninstanz, Verarbeitungsinstanz, Datenbanken) die Kommunikation mit der Veröffentlichungsfarm und anderen im Topologiediagramm genannten internen Komponenten zu ermöglichen:

<table> 
 <tbody>
  <tr>
   <td>Host<br /> </td> 
   <td>URI</td> 
  </tr>
  <tr>
   <td>Veröffentlichungsfarm (Veröffentlichungsknoten)</td> 
   <td>/bin/receive</td> 
  </tr>
  <tr>
   <td>Verarbeitungs-Server</td> 
   <td>/content/forms/fp/*</td> 
  </tr>
  <tr>
   <td>Forms Workflow-Add-On-Server (AEM Forms auf JEE-Server)</td> 
   <td>/soap/sdk</td> 
  </tr>
 </tbody>
</table>

#### Einrichten von Repository-Berechtigungen und Zugriffskontrolllisten (Access Control Lists, ACLs) {#setup-repository-permissions-and-access-control-lists-acls}

Standardmäßig sind Assets auf den Veröffentlichungsknoten für alle Benutzenden zugänglich. Der Lesezugriff ist für alle Assets aktiviert. Dies ist erforderlich, um anonymen Zugriff zuzulassen. Wenn Sie die Formularansicht einschränken und nur authentifizierten Personen Zugriff gewähren möchten, verwenden Sie eine gemeinsame Gruppe, um nur authentifizierten Personen schreibgeschützten Zugriff auf die auf den Veröffentlichungsknoten verfügbaren Assets zu gewähren. Die folgenden Speicherorte/Verzeichnisse enthalten Formular-Assets, die durch Beschränken des Lesezugriffs auf authentifizierte Personen abgesichert („gehärtet“) werden müssen:

* /content/&amp;ast;
* /etc.clientlibs/fd/&amp;ast;
* /libs/fd/&amp;ast;

## Sichere Verarbeitung von Formulardaten  {#securely-handle-forms-data}

AEM Forms speichert Daten unter vordefinierten Speicherorten und temporären Ordnern. Schützen Sie diese Daten, um eine unbefugte Nutzung zu verhindern.

### Einrichten einer periodischen Bereinigung des temporären Ordners {#setup-periodic-cleanup-of-temporary-folder}

Wenn Sie Formulare für Dateianhänge konfigurieren, überprüfen oder Komponenten in der Vorschau anzeigen, werden die entsprechenden Daten auf den Veröffentlichungsknoten unter „/tmp/fd/“ gespeichert. Die Daten werden regelmäßig bereinigt. Sie können den Auftrag zur standardmäßigen Datenbereinigung ändern und aggressiver einstellen. Um den geplanten Auftrag zur Bereinigung der Daten zu ändern, öffnen Sie die AEM Web-Konsole und dann die Aufgabe zum Bereinigen des temporären Speichers von AEM Forms und ändern Sie den Cron-Ausdruck.

In den oben genannten Szenarien werden die Daten nur für authentifizierte Benutzende gespeichert. Darüber hinaus sind die Daten durch Zugriffskontrolllisten (Access Control Lists, ACLs) geschützt. Die Änderung der Datenbereinigung ist damit ein weiterer Schritt zum Schutz der Informationen.

### Sichern der durch die Übermittlungsaktion des Formularportals gespeicherten Daten {#secure-data-saved-by-forms-portal-submit-action}

Standardmäßig speichert die Übermittlungsaktion von adaptiven Formularen im Formularportal Daten im lokalen Repository des Veröffentlichungsknotens. Die Daten werden unter „/content/forms/fp“ gespeichert. **Wir raten davon ab, Daten auf der Veröffentlichungsinstanz zu speichern.**

Sie können den Speicherdienst so konfigurieren, dass er über das Netzwerk an den Verarbeitungs-Cluster sendet, ohne dass Daten lokal auf dem Veröffentlichungsknoten gespeichert werden. Der Verarbeitungs-Cluster befindet sich in einer sicheren Zone hinter der privaten Firewall und die Daten bleiben sicher.

Verwenden Sie die Anmeldedaten des Verarbeitungs-Servers für den AEM DS-Einstellungsdienst, um Daten vom Veröffentlichungsknoten an den Verarbeitungs-Server zu senden. Verwenden Sie die Anmeldedaten einer Person mit eingeschränkten Rechten, die nicht zu den Admins gehört und über Lese- und Schreibzugriff auf das Repository des Verarbeitungs-Servers verfügt. Weitere Informationen finden Sie unter [Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md).

### Sichern der durch das Formulardatenmodell (FDM) verarbeiteten Daten {#secure-data-handled-by-form-data-model-fdm}

Verwenden Sie Benutzerkonten mit den minimal erforderlichen Berechtigungen zum Konfigurieren der Datenquellen für das Formulardatenmodell (FDM). Wenn Sie ein Konto mit administrativen Rechten verwenden, erhalten nicht autorisierte Personen möglicherweise offenen Zugriff auf Metadaten und Schema-Entitäten.\
Die Datenintegration stellt außerdem Methoden zum Autorisieren von FDM-Dienstanfragen bereit. Sie können vor und nach der Ausführung Autorisierungsmechanismen einfügen, um Anfragen zu validieren. Die Dienstanforderungen werden beim Vorausfüllen und beim Absenden eines Formulars sowie beim Aufrufen von Diensten mithilfe einer Regel generiert.

**Autorisierung vor Verarbeitung:** Mithilfe der Autorisierung vor der Verarbeitung können Sie die Authentizität einer Anfrage validieren, bevor diese ausgeführt wird. Dabei können Sie die Ausführung der Anfrage mithilfe von Eingaben sowie Dienst- und Anfragedetails zulassen oder blockieren. Für den Fall, dass die Ausführung gestoppt wird, können Sie die Datenintegrationsausnahme „OPERATION_ACCESS_DENIED“ ausgeben lassen. Sie können darüber hinaus die Client-Anfrage ändern, bevor sie zur Ausführung übermittelt wird. So könnten Sie beispielsweise die Eingabe ändern und zusätzliche Informationen hinzufügen.

**Autorisierung nach Verarbeitung:** Mithilfe der Autorisierung nach Verarbeitung können Sie die Ergebnisse validieren und kontrollieren, bevor sie an den Anforderer zurückgegeben werden. Sie können auch zusätzliche Daten filtern, bereinigen und in Ergebnisse einfügen.

### Begrenzen des Benutzerzugriffs {#limit-user-access}

Für Autoren-, Veröffentlichungs- und Verarbeitungsinstanzen sind unterschiedliche Benutzerrollen erforderlich. Führen Sie keine Instanzen mit Administrator-Anmeldedaten aus.

**In einer Veröffentlichungsinstanz:**

* Nur Benutzende der Gruppe „forms-users“ können Formulare in der Vorschau anzeigen, Entwürfe erstellen und Formulare absenden.
* Nur Benutzende der Gruppe „cm-user-agent“ können Korrespondenzverwaltungs-Briefe in der Vorschau anzeigen.
* Deaktivieren Sie jeglichen nicht erforderlichen anonymen Zugriff.

**Auf einer Autoreninstanz:**

* Für jede Rolle steht jeweils eine Reihe vordefinierter Gruppen mit spezifischen Berechtigungen zur Verfügung. Benutzer zu Gruppe zuordnen.

   * Benutzende der Gruppe „forms-user“:

      * können ein Formular erstellen, ausfüllen, veröffentlichen und absenden
      * können kein XDP-basiertes adaptives Formular erstellen
      * sind nicht berechtigt, Skripte für adaptive Formulare zu schreiben
      * können weder XDP importieren noch Pakete, die XDP enthalten

   * Benutzer der Gruppe „forms-power-user“ können alle Typen von Formularen erstellen, ausfüllen, veröffentlichen und senden, Skripte für adaptive Formulare schreiben und Pakete importieren, die XDP enthalten.
   * Benutzende der Gruppen „template-authors“ und „template-power-user“ können Vorlagen in der Vorschau anzeigen und erstellen.
   * Benutzende der Gruppe „fdm-authors“ können Formulardatenmodelle erstellen und ändern.
   * Benutzende der Gruppe „cm-user-agent“ können Korrespondenzverwaltungs-Briefe erstellen, in der Vorschau anzeigen und veröffentlichen.
   * Benutzende der Gruppe „workflow-editors“ können Posteingang-Anwendungen und Workflow-Modelle erstellen.

**Beim Verarbeiten des Authorings:**

* Erstellen Sie für Anwendungsfälle zum Remote-Speichern und -Absenden Benutzende mit Lese-, Erstellungs- und Änderungsberechtigungen für den Pfad „content/form/fp“ des CRX-Repositorys.
* Fügen Sie Benutzende zur Gruppe „workflow-user“ hinzu, um ihnen die Verwendung der AEM-Posteingang-Anwendungen zu ermöglichen.

## Sichern von Intranet-Elementen einer AEM Forms-Umgebung {#secure-intranet-elements-of-an-aem-forms-environment}

Im Allgemeinen werden Verarbeitungs-Cluster und das Forms Workflow-Add-on (AEM Forms on JEE) hinter einer Firewall ausgeführt. Sie können daher als sicher betrachtet werden. Dennoch können Sie diese Umgebungen mit einigen weiteren Maßnahmen absichern:

### Sichern eines Verarbeitungs-Clusters {#secure-processing-cluster}

Ein Verarbeitungs-Cluster wird im Authoring-Modus ausgeführt. Verwenden Sie ihn jedoch nicht für Entwicklungszwecke. Lassen Sie nicht zu, dass normale Benutzer in die Gruppen „content-authors“ und „form-users“ aufgenommen werden.

### Verwenden der Best Practices in AEM zur Sicherung einer AEM Forms-Umgebung {#use-aem-best-practices-to-secure-an-aem-forms-environment}

Dieses Dokument enthält spezifische Anweisungen für eine AEM Forms-Umgebung. Sie sollten sicherstellen, dass Ihre zugrundeliegende AEM-Installation bei der Bereitstellung sicher ist. Detaillierte Anweisungen finden Sie in der Dokumentation zur [AEM-Sicherheits-Checkliste](/help/sites-administering/security-checklist.md).
