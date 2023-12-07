---
title: Härten (Absichern) und Schützen von AEM-Formularen in OSGi-Umgebungen
description: Erfahren Sie mehr über Empfehlungen und Best Practices zum Schützen von AEM Forms auf einem OSGi-Server.
topic-tags: Security
role: Admin
exl-id: 5da3cc59-4243-4098-b1e0-438304fcd0c5
source-git-commit: 8b4cb4065ec14e813b49fb0d577c372790c9b21a
workflow-type: tm+mt
source-wordcount: '1434'
ht-degree: 18%

---

# Härten (Absichern) und Schützen von AEM-Formularen in OSGi-Umgebungen {#hardening-and-securing-aem-forms-on-osgi-environment}

Erfahren Sie mehr über Empfehlungen und Best Practices zum Schützen von AEM Forms auf einem OSGi-Server.

Die Sicherung einer Serverumgebung ist für ein Unternehmen von größter Bedeutung. In diesem Artikel werden Empfehlungen und Best Practices zum Schützen von Servern beschrieben, auf denen AEM Forms ausgeführt wird. Dies ist kein umfangreiches Dokument zur Härtung von Hosts für Ihr Betriebssystem. Stattdessen werden in diesem Artikel verschiedene Einstellungen für die Sicherheitshärtung beschrieben, die Sie implementieren sollten, um die Sicherheit Ihrer bereitgestellten Anwendung zu erhöhen. Um sicherzustellen, dass die Anwendungsserver sicher bleiben, sollten Sie jedoch zusätzlich zu den Empfehlungen in diesem Artikel auch Verfahren zur Sicherheitsüberwachung, -erkennung und -reaktion implementieren. Das Dokument enthält auch Best Practices und Richtlinien zum Schützen von personenbezogenen Daten (PII).

Dieser Artikel richtet sich an Berater, Sicherheitsexperten, Systemarchitekten und IT-Fachleute, die für die Planung der Anwendungs- oder Infrastrukturentwicklung und -implementierung von AEM Forms verantwortlich sind. Diese Rollen umfassen die folgenden allgemeinen Rollen:

* IT- und Betriebsingenieure, die sichere Webanwendungen und -server in ihren eigenen oder Kundenorganisationen bereitstellen müssen.
* Architekten und Systemplaner mit der Aufgabe, die Architekturentwicklung für die Kunden in ihren Unternehmen zu planen.
* IT-Sicherheitsspezialisten, die sich auf die plattformübergreifende Sicherheit innerhalb ihres Unternehmens konzentrieren.
* Berater von Adobe und Partner, die detaillierte Ressourcen für Kunden und Partner benötigen.

Die folgende Abbildung zeigt Komponenten und Protokolle, die in einer typischen AEM Forms-Bereitstellung verwendet werden, einschließlich der entsprechenden Firewall-Topologie:

![typical-architecture](assets/typical-architecture.png)

AEM Forms ist in hohem Maße anpassbar und kann in vielen verschiedenen Umgebungen verwendet werden. Einige der Empfehlungen gelten möglicherweise nicht für Ihre Organisation.

## Sichere Transportschicht {#secure-transport-layer}

Sicherheitslücken in der Transportschicht gehören zu den ersten Bedrohungen für einen Internet-orientierten oder Intranet-orientierten Anwendungsserver. In diesem Abschnitt wird der Prozess zum Absichern von Hostrechnern im Netzwerk gegen diese Schwachstellen beschrieben. Dabei geht es um die Netzwerksegmentierung, das Härten des TCP/IP-Stacks (Transmission Control Protocol/Internet Protocol) und die Verwendung von Firewalls für den Schutz des Hosts.

### Beliebige offene Endpunkte begrenzen  {#limit-open-endpoints}

Eine Organisation kann über eine externe Firewall verfügen, um den Zugriff zwischen einem Endbenutzer und einer AEM Forms-Veröffentlichungsfarm zu beschränken. Die Organisation kann auch über eine interne Firewall verfügen, um den Zugriff zwischen einer Veröffentlichungsfarm und anderen Elementen innerhalb der Organisation zu beschränken (z. B. Autoreninstanz, Verarbeitungsinstanz, Datenbanken). Lassen Sie mithilfe von Firewalls den Zugriff auf eine begrenzte Anzahl von AEM Forms-URLs für Endbenutzer und zwischen den Elementen innerhalb des Unternehmens zu:

#### Externe Firewall konfigurieren  {#configure-external-firewall}

Sie können eine externe Firewall konfigurieren, um bestimmten AEM Forms-URLs den Zugriff auf das Internet zu ermöglichen. Der Zugriff auf diese URLs ist erforderlich zum Ausfüllen eines adaptiven Formulars, für HTML5, einen Correspondence Management-Brief oder die Anmeldung bei einem AEM Forms-Server:

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

#### Interne Firewall konfigurieren  {#configure-internal-firewall}

Sie können die interne Firewall so konfigurieren, dass bestimmte AEM Forms-Komponenten (z. B. Autoreninstanz, Verarbeitungsinstanz, Datenbanken) mit der Veröffentlichungs-Farm und anderen im Topologieschema erwähnten internen Komponenten kommunizieren können:

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
   <td>Verarbeitungsserver</td> 
   <td>/content/forms/fp/*</td> 
  </tr>
  <tr>
   <td>Forms Workflow Add-On-Server (AEM Forms on JEE-Server)</td> 
   <td>/soap/sdk</td> 
  </tr>
 </tbody>
</table>

#### Einrichten von Repository-Berechtigungen und Zugriffssteuerungslisten (ACLs) {#setup-repository-permissions-and-access-control-lists-acls}

Standardmäßig sind auf den Veröffentlichungsknoten verfügbare Assets für alle zugänglich. Der schreibgeschützte Zugriff ist für alle Assets aktiviert. Sie ist erforderlich, um den anonymen Zugriff zu aktivieren. Wenn Sie die Formularansicht beschränken und den Zugriff nur an authentifizierte Benutzer senden möchten, verwenden Sie eine gemeinsame Gruppe, um nur authentifizierten Benutzern Lesezugriff auf die Assets zu gewähren, die auf den Veröffentlichungsknoten verfügbar sind. Die folgenden Speicherorte/Verzeichnisse enthalten Formularelemente, die gehärtet werden müssen (schreibgeschützter Zugriff für authentifizierte Benutzer):

* /content/&amp;ast;
* /etc.clientlibs/fd/&amp;ast;
* /libs/fd/&amp;ast;

## Sichere Verarbeitung von Formulardaten  {#securely-handle-forms-data}

AEM Forms speichert Daten an vordefinierten Speicherorten und temporären Ordnern. Schützen Sie diese Daten, um eine unbefugte Nutzung zu verhindern.

### Periodische Bereinigung des temporären Ordners einrichten {#setup-periodic-cleanup-of-temporary-folder}

Wenn Sie Formulare für Dateianhänge konfigurieren, überprüfen oder eine Vorschau von Komponenten anzeigen, werden die entsprechenden Daten auf den Veröffentlichungsknoten unter /tmp/fd/ gespeichert. Die Daten werden regelmäßig bereinigt. Sie können den standardmäßigen Bereinigungsauftrag für Daten so ändern, dass er aggressiver ist. Um den für die Datenbereinigung geplanten Auftrag zu ändern, öffnen Sie AEM Web Console, öffnen Sie die Aufgabe &quot;Bereinigung des temporären AEM Forms-Speichers&quot;und ändern Sie den Cron-Ausdruck.

In den oben genannten Szenarien werden die Daten nur für authentifizierte Benutzer gespeichert. Darüber hinaus sind die Daten durch Zugriffssteuerungslisten (ACLs) geschützt. Die Änderung der Datenbereinigung ist daher ein weiterer Schritt zum Schutz von Informationen.

### Sichere Daten, die von der Sendeaktion des Forms Portal gespeichert werden {#secure-data-saved-by-forms-portal-submit-action}

Standardmäßig speichert die Übermittlungsaktion des Forms Portal für adaptive Formulare Daten im lokalen Repository des Veröffentlichungsknotens. Die Daten werden unter /content/forms/fp gespeichert. **Es wird nicht empfohlen, Daten in der Veröffentlichungsinstanz zu speichern.**

Sie können den Speicherdienst so konfigurieren, dass er über den Kabel an den Verarbeitungscluster sendet, ohne dass irgendetwas lokal auf dem Veröffentlichungsknoten gespeichert wird. Der Verarbeitungscluster befindet sich in einer sicheren Zone hinter der privaten Firewall und die Daten bleiben geschützt.

Verwenden Sie die Anmeldeinformationen des Verarbeitungsservers für AEM DS-Einstellungsdienst, um Daten vom Veröffentlichungsknoten an den Verarbeitungsserver zu posten. Verwenden Sie die Anmeldeinformationen eines eingeschränkten Benutzers ohne Administratorrechte mit Lese- und Schreibzugriff auf das Repository des Verarbeitungsservers. Weitere Informationen finden Sie unter [Konfigurieren von Speicherdiensten für Entwürfe und Übermittlungen](/help/forms/using/configuring-draft-submission-storage.md).

### Sichere Daten, die vom Formulardatenmodell (FDM) verarbeitet werden {#secure-data-handled-by-form-data-model-fdm}

Verwenden Sie Benutzerkonten mit den erforderlichen Mindestberechtigungen zum Konfigurieren von Datenquellen für das Formulardatenmodell (FDM). Die Verwendung des Administratorkontos kann unbefugten Benutzern den offenen Zugriff auf Metadaten- und Schemaentitäten ermöglichen.\
Die Datenintegration stellt außerdem Methoden zum Autorisieren von FDM-Dienstanfragen bereit. Sie können zur Validierung einer Anforderung Berechtigungsmechanismen vor und nach der Ausführung einfügen. Die Dienstanforderungen werden beim Vorausfüllen eines Formulars, beim Senden eines Formulars und beim Aufrufen von Diensten über eine Regel generiert.

**Autorisierung vor der Verarbeitung:** Sie können die Autorisierung vor der Verarbeitung verwenden, um die Authentizität einer Anforderung zu überprüfen, bevor Sie sie ausführen. Sie können Eingaben, Dienst- und Anfragedetails verwenden, um die Ausführung der Anfrage zu ermöglichen oder zu stoppen. Wenn die Ausführung angehalten wird, können Sie die Datenintegrationsausnahme OPERATION_ACCESS_DENIED zurückgeben. Sie können auch die Clientanforderung ändern, bevor Sie sie zur Ausführung senden. Beispielsweise durch Ändern der Eingabe und Hinzufügen zusätzlicher Informationen.

**Autorisierung nach Verarbeitung:** Mithilfe der Autorisierung nach Verarbeitung können Sie die Ergebnisse validieren und kontrollieren, bevor sie an den Anforderer zurückgegeben werden. Sie können auch zusätzliche Daten filtern, prunen und in Ergebnisse einfügen.

### Benutzerzugriff beschränken {#limit-user-access}

Für Autoren-, Veröffentlichungs- und Verarbeitungsinstanzen sind unterschiedliche Benutzerrollen erforderlich. Führen Sie keine Instanzen mit Administrator-Anmeldedaten aus.

**Auf einer Veröffentlichungsinstanz:**

* Nur Benutzer der Gruppe &quot;forms-users&quot;können Formulare in der Vorschau anzeigen, Entwürfe erstellen und senden.
* Nur Benutzer der Gruppe &quot;cm-user-agent&quot;können Correspondence Management-Briefe in der Vorschau anzeigen.
* Deaktivieren Sie den gesamten nicht erforderlichen anonymen Zugriff.

**Auf einer Autoreninstanz:**

* Es gibt einen anderen Satz vordefinierter Gruppen mit spezifischen Berechtigungen für jede Person. Benutzer zu Gruppe zuordnen.

   * Benutzer der Gruppe &quot;forms-user&quot;:

      * kann ein Formular erstellen, ausfüllen, veröffentlichen und senden.
      * kann kein XDP-basiertes adaptives Formular erstellen.
      * nicht berechtigt sind, Skripte für adaptive Formulare zu schreiben.
      * kann XDP nicht importieren oder ein Paket, das XDP enthält

   * Benutzer der Gruppe „forms-power-user“ können alle Typen von Formularen erstellen, ausfüllen, veröffentlichen und senden, Skripte für adaptive Formulare schreiben und Pakete importieren, die XDP enthalten.
   * Ein Benutzer von template-authors und template-power-user kann eine Vorlage in der Vorschau anzeigen und erstellen.
   * Ein Benutzer von fdm-authors kann ein Formulardatenmodell erstellen und ändern.
   * Ein Benutzer der Gruppe &quot;cm-user-agent&quot;kann Correspondence Management-Briefe erstellen, in der Vorschau anzeigen und veröffentlichen.
   * Ein Benutzer der Gruppe &quot;Workflow-Editoren&quot;kann eine Inbox-Anwendung und ein Workflow-Modell erstellen.

**Beim Verarbeitungsautor:**

* Erstellen Sie für Anwendungsfälle zum Remote-Speichern und Senden einen Benutzer mit Lese-, Erstellungs- und Änderungsberechtigungen für den Inhalts-/Formular-/fp-Pfad des CRX-Repository.
* Fügen Sie Benutzer zu Workflow-Benutzergruppen hinzu, um einem Benutzer die Verwendung AEM Posteingangsanwendungen zu ermöglichen.

## Sichern von Intranetelementen einer AEM Forms-Umgebung {#secure-intranet-elements-of-an-aem-forms-environment}

Im Allgemeinen werden Verarbeitungscluster und Forms Workflow-Add-on (AEM Forms on JEE) hinter einer Firewall ausgeführt. Diese werden also als sicher betrachtet. Dennoch können Sie diese Umgebungen mit einigen weiteren Maßnahmen absichern:

### Sicherer Verarbeitungscluster {#secure-processing-cluster}

Ein Verarbeitungscluster wird im Autorenmodus ausgeführt, verwendet ihn jedoch nicht für Entwicklungsaktivitäten. Lassen Sie nicht zu, dass normale Benutzer in die Gruppen „content-authors“ und „form-users“ aufgenommen werden.

### Verwenden AEM Best Practices zur Sicherung einer AEM Forms-Umgebung {#use-aem-best-practices-to-secure-an-aem-forms-environment}

Dieses Dokument enthält spezifische Anweisungen für die AEM Forms-Umgebung. Sie sollten sicherstellen, dass Ihre zugrunde liegende AEM-Installation bei der Bereitstellung sicher ist. Detaillierte Anweisungen finden Sie in der Dokumentation zur [AEM-Sicherheits-Checkliste](/help/sites-administering/security-checklist.md).
