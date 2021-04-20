---
title: Benutzer verwalten
seo-title: Benutzer verwalten
description: Verwenden Sie die User Management-API, um Clientanwendungen zu erstellen, die Rollen, Berechtigungen und Prinzipale (d. h. Benutzer oder Gruppen) verwalten und Benutzer authentifizieren können.
seo-description: Verwenden Sie die User Management-API, um Clientanwendungen zu erstellen, die Rollen, Berechtigungen und Prinzipale (d. h. Benutzer oder Gruppen) verwalten und Benutzer authentifizieren können.
uuid: 68d8a0bc-6e3d-4286-ba5c-534dcf58cb84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 95804bff-9e6f-4807-aae4-790bd9e7cb57
role: Developer
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '6258'
ht-degree: 4%

---


# Verwalten von Benutzern {#managing-users}

**Beispiele und Beispiele in diesem Dokument gelten nur für die Umgebung AEM Forms on JEE.**

**Info zu User Management**

Sie können die User Management-API verwenden, um Clientanwendungen zu erstellen, die Rollen, Berechtigungen und Prinzipale (d. h. Benutzer oder Gruppen) verwalten und Benutzer authentifizieren können. Die User Management-API besteht aus den folgenden AEM Forms-APIs:

* Directory Manager-Dienst-API
* Authentication Manager-Dienst-API
* Authorization Manager-Dienst-API

Mit User Management können Sie Rollen und Berechtigungen zuweisen, entfernen und festlegen. Außerdem können Sie Domänen, Benutzer und Abfragen zuweisen, entfernen und Gruppen zuweisen. Schließlich können Sie User Management verwenden, um Benutzer zu authentifizieren.

Unter [Hinzufügen von Benutzern](users.md#adding-users) erfahren Sie, wie Sie Benutzer programmatisch hinzufügen. In diesem Abschnitt wird die Directory Manager-Dienst-API verwendet.

Unter [Löschen von Benutzern](users.md#deleting-users) erfahren Sie, wie Sie Benutzer programmatisch löschen. In diesem Abschnitt wird die Directory Manager-Dienst-API verwendet.

Unter [Verwalten von Benutzern und Gruppen](users.md#managing-users-and-groups) verstehen Sie den Unterschied zwischen einem lokalen Benutzer und einem Ordnerbenutzer und sehen Beispiele für die Verwendung der Java- und Webdienst-APIs zum programmgesteuerten Verwalten von Benutzern und Gruppen. In diesem Abschnitt wird die Directory Manager-Dienst-API verwendet.

Unter [Verwalten von Rollen und Berechtigungen](users.md#managing-roles-and-permissions) erfahren Sie mehr über die Systemrollen und -berechtigungen und was Sie programmgesteuert tun können, um sie zu erweitern. Außerdem finden Sie Beispiele für die Verwendung der Java- und Webdienst-APIs zum programmgesteuerten Verwalten von Rollen und Berechtigungen. In diesem Abschnitt werden sowohl die Directory Manager-Dienst-API als auch die Authorization Manager-Dienst-API verwendet.

Unter [Authentifizieren von Benutzern](users.md#authenticating-users) finden Sie Beispiele dafür, wie Sie die Java- und Webdienst-APIs zur programmatischen Authentifizierung von Benutzern verwenden. In diesem Abschnitt wird die Autorisierungs-Manager-Dienst-API verwendet.

**Authentifizierungsprozess**

User Management bietet integrierte Authentifizierungsfunktionen und die Möglichkeit, diese mit Ihrem eigenen Authentifizierungsanbieter zu verbinden. Wenn User Management eine Authentifizierungsanforderung erhält (z. B. wenn ein Benutzer versucht, sich anzumelden), werden Benutzerinformationen zur Authentifizierung an den Authentifizierungsanbieter weitergeleitet. User Management erhält die Ergebnisse vom Authentifizierungsanbieter, nachdem der Benutzer authentifiziert wurde.

Das folgende Diagramm zeigt die Interaktion zwischen einem Endbenutzer, der versucht, sich anzumelden, User Management und dem Authentifizierungsanbieter.

![mu_mu_umauth_process](assets/mu_mu_umauth_process.png)

In der folgenden Tabelle werden die einzelnen Schritte des Authentifizierungsprozesses beschrieben.

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Ein Benutzer versucht, sich bei einem Dienst anzumelden, der User Management aufruft. Der Benutzer gibt einen Benutzernamen und ein Kennwort an. </p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>User Management sendet den Benutzernamen und das Kennwort sowie Konfigurationsinformationen an den Authentifizierungsanbieter.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Der Authentifizierungsanbieter stellt eine Verbindung zum Benutzerspeicher her und authentifiziert den Benutzer.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Der Authentifizierungsanbieter gibt die Ergebnisse an User Management zurück.</p></td>
  </tr>
  <tr>
   <td><p>5</p></td>
   <td><p>Mit der Benutzerverwaltung können Benutzer sich entweder anmelden oder den Zugriff auf das Produkt verweigern.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Wenn sich die Zeitzone des Servers von der Zeitzone des Clients unterscheidet und der WSDL-Dienst für den AEM Forms Generate PDF-Dienst auf einem nativen SOAP-Stapel mit einem .NET-Client auf einem WebSphere Application Server-Cluster verwendet wird, kann der folgende User Management-Authentifizierungsfehler auftreten:

`[com.adobe.idp.um.webservices.WSSecurityHandler] errorCode:12803 errorCodeHEX:0x3203 message:WSSecurityHandler: UM authenticate returns exception : An error was discovered processing the <wsse:Security> header. (WSSecurityEngine: Invalid timestamp The security semantics of message have expired).`

**Informationen zur Ordnerverwaltung**

User Management wird mit einem Directory Dienstleister (dem DirectoryManagerService) verpackt, der Verbindungen zu LDAP-Ordnern unterstützt. Wenn Ihr Unternehmen Benutzerdatensätze mit einem Nicht-LDAP-Repository speichert, können Sie einen eigenen Dienstleister erstellen, der mit Ihrem Repository funktioniert.

Directory-Dienstleister rufen auf Anfrage von User Management Datensätze aus einem Benutzerspeicher ab. User Management speichert Benutzer- und Gruppendatensätze in der Datenbank regelmäßig zwischen, um die Leistung zu verbessern.

Der Dienstleister &quot;directory&quot;kann zum Synchronisieren der User Management-Datenbank mit dem Benutzerspeicher verwendet werden. Dieser Schritt stellt sicher, dass alle Benutzerordnerinformationen sowie alle Benutzer- und Gruppendatensätze auf dem neuesten Stand sind.

Darüber hinaus bietet Ihnen der DirectoryManagerService die Möglichkeit, Domänen zu erstellen und zu verwalten. Domänen definieren unterschiedliche Benutzergrundlagen. Die Begrenzung einer Domäne wird in der Regel entsprechend der Struktur Ihres Unternehmens oder der Einrichtung Ihres Benutzerspeichers definiert. User Management-Domänen bieten Konfigurationseinstellungen, die von Authentifizierungsanbietern und Dienstleistern verwendet werden.

In der Konfigurationsdatei, die User Management exportiert, enthält der Stammknoten mit dem Attributwert `Domains` ein XML-Element für jede für User Management definierte Domäne. Jedes dieser Elemente enthält andere Elemente, die bestimmte Aspekte der Domäne definieren, die bestimmten Dienstleistern zugeordnet sind.

**Grundlegendes zu objectSID-Werten**

Bei der Verwendung von Active Directory ist zu beachten, dass ein `objectSID`-Wert kein eindeutiges Attribut über mehrere Domänen hinweg ist. Dieser Wert speichert die Sicherheitskennung eines Objekts. In einer Umgebung mit mehreren Domänen (z. B. einer Struktur von Domänen) kann der `objectSID`-Wert unterschiedlich sein.

Ein `objectSID`-Wert würde sich ändern, wenn ein Objekt von einer Active Directory-Domäne in eine andere Domäne verschoben wird. Einige Objekte haben denselben `objectSID`-Wert an einer beliebigen Stelle in der Domäne. Zum Beispiel hätten Gruppen wie BUILTIN\Administratoren, BUILTIN\Power Users usw. unabhängig von den Domänen denselben `objectSID`-Wert. Diese `objectSID`-Werte sind bekannt.

## Hinzufügen von Benutzern {#adding-users}

Sie können die Directory Manager-Dienst-API (Java und Webdienst) verwenden, um AEM Forms programmgesteuert Benutzer hinzuzufügen. Nachdem Sie einen Benutzer hinzugefügt haben, können Sie ihn bei einem Dienstvorgang verwenden, für den ein Benutzer erforderlich ist. Sie können dem neuen Benutzer beispielsweise eine Aufgabe zuweisen.

### Zusammenfassung der Schritte {#summary-of-steps}

So fügen Sie einen Benutzer hinzu:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Legen Sie Benutzerinformationen fest.
1. hinzufügen den Benutzer nach AEM Forms.
1. Vergewissern Sie sich, dass der Benutzer hinzugefügt wird.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Directory Manager-Dienstvorgang programmgesteuert durchführen können, erstellen Sie einen Directory Manager-Dienst-API-Client.

**Benutzerinformationen definieren**

Wenn Sie einen neuen Benutzer mithilfe der Directory Manager-Dienst-API hinzufügen, definieren Sie Informationen für diesen Benutzer. Wenn Sie einen neuen Benutzer hinzufügen, definieren Sie in der Regel die folgenden Werte:

* **Domänenname**: Die Domäne, zu der der Benutzer gehört (z. B.  `DefaultDom`).
* **Benutzerkennungswert**: Der Bezeichnerwert des Benutzers (z. B.  `wblue`).
* **Prinzipaltyp**: Der Typ des Benutzers (z. B. können Sie ihn angeben  `USER)`.
* **Vorname**: Ein Vorname für den Benutzer (z. B.  `Wendy`).
* **Nachname**: Der Familienname des Benutzers (z. B.  `Blue)`.
* **Gebietsschema**: Gebietsschema-Informationen für den Benutzer.

**hinzufügen des Benutzers auf AEM Forms**

Nachdem Sie Benutzerinformationen definiert haben, können Sie den Benutzer zu AEM Forms hinzufügen. Um einen Benutzer hinzuzufügen, rufen Sie die `DirectoryManagerServiceClient`-Methode des Objekts `createLocalUser` auf.

**Überprüfen, ob der Benutzer hinzugefügt wurde**

Sie können überprüfen, ob der Benutzer hinzugefügt wurde, um sicherzustellen, dass keine Probleme aufgetreten sind. Suchen Sie den neuen Benutzer mithilfe des Benutzerkennungswerts.

**Siehe auch**

[hinzufügen Benutzer mit der Java-API](users.md#add-users-using-the-java-api)

[hinzufügen mit der Webdienst-API](users.md#add-users-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Löschen von Benutzern](users.md#deleting-users)

### hinzufügen Benutzer, die die Java-API {#add-users-using-the-java-api} verwenden

hinzufügen Benutzer mithilfe der Directory Manager-Dienst-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerServices-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Legen Sie Benutzerinformationen fest.

   * Erstellen Sie ein Objekt `UserImpl`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Standardnamen fest, indem Sie die `UserImpl`-Methode des Objekts `setDomainName` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Domänennamen angibt.
   * Legen Sie den Prinzipaltyp fest, indem Sie die `UserImpl`-Methode des Objekts `setPrincipalType` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Typ des Benutzers angibt. Sie können beispielsweise `USER` angeben.
   * Legen Sie den Wert für die Benutzerkennung fest, indem Sie die `UserImpl`-Methode des Objekts `setUserid` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Wert der Benutzerkennung angibt. Sie können beispielsweise `wblue` angeben.
   * Legen Sie den kanonischen Namen fest, indem Sie die `UserImpl`-Methode des Objekts `setCanonicalName` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den kanonischen Namen des Benutzers angibt. Sie können beispielsweise `wblue` angeben.
   * Legen Sie den angegebenen Namen fest, indem Sie die `UserImpl`-Methode des Objekts `setGivenName` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Vornamen des Benutzers angibt. Sie können beispielsweise `Wendy` angeben.
   * Legen Sie den Nachnamen fest, indem Sie die `UserImpl`-Methode des Objekts `setFamilyName` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Nachnamen des Benutzers angibt. Sie können beispielsweise `Blue` angeben.

   >[!NOTE]
   >
   >Rufen Sie eine Methode auf, die zum `UserImpl`-Objekt gehört, um andere Werte festzulegen. Sie können beispielsweise den Wert des Gebietsschemas festlegen, indem Sie die `UserImpl`-Methode des Objekts `setLocale` aufrufen.

1. hinzufügen den Benutzer nach AEM Forms.

   Rufen Sie die `createLocalUser`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`DirectoryManagerServiceClient`

   * Das `UserImpl`-Objekt, das den neuen Benutzer darstellt
   * Ein Zeichenfolgenwert, der das Kennwort des Benutzers darstellt

   Die `createLocalUser`-Methode gibt einen Zeichenfolgenwert zurück, der den lokalen Benutzer-ID-Wert angibt.

1. Vergewissern Sie sich, dass der Benutzer hinzugefügt wurde.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Wert für die Benutzerkennung fest, indem Sie die `PrincipalSearchFilter`-Methode des Objekts `setUserId` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Wert der Benutzerkennung darstellt.
   * Rufen Sie die `findPrincipals`-Methode des Objekts auf und übergeben Sie das `PrincipalSearchFilter`-Objekt. `DirectoryManagerServiceClient` Diese Methode gibt eine `java.util.List`-Instanz zurück, wobei jedes Element ein `User`-Objekt ist. Durchlaufen Sie die `java.util.List`-Instanz, um den Benutzer zu suchen.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Hinzufügen von Benutzern mit der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-adding-users-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### hinzufügen Benutzer, die die Webdienst-API {#add-users-using-the-web-service-api} verwenden

hinzufügen Benutzer mithilfe der Directory Manager-Dienst-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition für die Dienstreferenz verwenden: `http://localhost:8080/soap/services/DirectoryManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen DirectoryManagerService-Client.

   * Erstellen Sie ein `DirectoryManagerServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `DirectoryManagerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der den WSDL-Wert an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Stellen Sie sicher, dass Sie `?blob=mtom` angeben.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `DirectoryManagerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Legen Sie Benutzerinformationen fest.

   * Erstellen Sie ein Objekt `UserImpl`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Hauptnamen fest, indem Sie dem Feld `UserImpl` des Objekts `domainName` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den Prinzipaltyp fest, indem Sie dem Feld `UserImpl` des Objekts `principalType` einen Zeichenfolgenwert zuweisen. Sie können beispielsweise `USER` angeben.
   * Legen Sie den Wert für die Benutzerkennung fest, indem Sie dem Feld `UserImpl` des Objekts `userid` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den kanonischen Namenswert fest, indem Sie dem Feld `UserImpl` des Objekts `canonicalName` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den Wert für den angegebenen Namen fest, indem Sie dem Feld `UserImpl` des Objekts `givenName` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den Wert für den Nachnamen fest, indem Sie dem Feld `UserImpl` des Objekts `familyName` einen Zeichenfolgenwert zuweisen.

1. hinzufügen den Benutzer nach AEM Forms.

   Rufen Sie die `createLocalUser`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`DirectoryManagerServiceClient`

   * Das `UserImpl`-Objekt, das den neuen Benutzer darstellt
   * Ein Zeichenfolgenwert, der das Kennwort des Benutzers darstellt

   Die `createLocalUser`-Methode gibt einen Zeichenfolgenwert zurück, der den lokalen Benutzer-ID-Wert angibt.

1. Vergewissern Sie sich, dass der Benutzer hinzugefügt wurde.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Wert für die Benutzerkennung des Benutzers fest, indem Sie dem Feld `userId` des Objekts `PrincipalSearchFilter` einen Zeichenfolgenwert zuweisen, der den Wert für die Benutzerkennung darstellt.
   * Rufen Sie die `findPrincipals`-Methode des Objekts auf und übergeben Sie das `PrincipalSearchFilter`-Objekt. `DirectoryManagerServiceClient` Diese Methode gibt ein Collection-Objekt `MyArrayOfUser` zurück, wobei jedes Element ein `User`-Objekt ist. Durchlaufen Sie die `MyArrayOfUser`-Sammlung, um den Benutzer zu suchen.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Löschen von Benutzern {#deleting-users}

Sie können die Directory Manager-Dienst-API (Java und Webdienst) verwenden, um Benutzer programmgesteuert aus AEM Forms zu löschen. Nach dem Löschen eines Benutzers kann der Benutzer nicht mehr für einen Dienstvorgang verwendet werden, für den ein Benutzer erforderlich ist. Beispielsweise können Sie einer gelöschten Aufgabe keine ID zuweisen.

### Zusammenfassung der Schritte {#summary_of_steps-1}

So löschen Sie einen Benutzer:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Geben Sie den zu löschenden Benutzer an.
1. Löschen Sie den Benutzer aus AEM Forms.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxydateien ein.

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Directory Manager-Dienst-API-Vorgang programmgesteuert durchführen können, erstellen Sie einen Directory Manager-Dienstclient.

**Benutzer zum Löschen angeben**

Sie können einen Benutzer angeben, der gelöscht werden soll, indem Sie den Bezeichnerwert des Benutzers verwenden.

**Benutzer aus AEM Forms löschen**

Um einen Benutzer zu löschen, rufen Sie die `DirectoryManagerServiceClient`-Methode des Objekts `deleteLocalUser` auf.

**Siehe auch**

[Benutzer mit der Java-API löschen](users.md#delete-users-using-the-java-api)

[Löschen von Benutzern mit der Webdienst-API](users.md#delete-users-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Hinzufügen von Benutzern](users.md#adding-users)

### Benutzer mit der Java-API {#delete-users-using-the-java-api} löschen

Löschen Sie Benutzer mithilfe der Directory Manager-Dienst-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den zu löschenden Benutzer an.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Wert für die Benutzerkennung fest, indem Sie die `PrincipalSearchFilter`-Methode des Objekts `setUserId` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Wert der Benutzerkennung darstellt.
   * Rufen Sie die `findPrincipals`-Methode des Objekts auf und übergeben Sie das `PrincipalSearchFilter`-Objekt. `DirectoryManagerServiceClient` Diese Methode gibt eine `java.util.List`-Instanz zurück, wobei jedes Element ein `User`-Objekt ist. Durchlaufen Sie die `java.util.List`-Instanz, um den zu löschenden Benutzer zu suchen.

1. Löschen Sie den Benutzer aus AEM Forms.

   Rufen Sie die `deleteLocalUser`-Methode des Objekts auf und übergeben Sie den Wert des Felds `User` des Objekts `oid`. `DirectoryManagerServiceClient` Rufen Sie die `User`-Methode des Objekts `getOid` auf. Verwenden Sie das `User`-Objekt, das von der `java.util.List`-Instanz abgerufen wird.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Quick Beginn (EJB-Modus): Löschen von Benutzern mit der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Quick Beginn (SOAP-Modus): Löschen von Benutzern mit der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Benutzer mit der Webdienst-API {#delete-users-using-the-web-service-api} löschen

Löschen Sie Benutzer mithilfe der Directory Manager-Dienst-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerService-Client.

   * Erstellen Sie ein `DirectoryManagerServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `DirectoryManagerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der den WSDL-Wert an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Stellen Sie sicher, dass Sie `blob=mtom.` angeben
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `DirectoryManagerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Geben Sie den zu löschenden Benutzer an.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Wert für die Benutzerkennung fest, indem Sie dem Feld `PrincipalSearchFilter` des Objekts `userId` einen Zeichenfolgenwert zuweisen.
   * Rufen Sie die `findPrincipals`-Methode des Objekts auf und übergeben Sie das `PrincipalSearchFilter`-Objekt. `DirectoryManagerServiceClient` Diese Methode gibt ein Collection-Objekt `MyArrayOfUser` zurück, wobei jedes Element ein `User`-Objekt ist. Durchlaufen Sie die `MyArrayOfUser`-Sammlung, um den Benutzer zu suchen. Das `User`-Objekt, das aus dem `MyArrayOfUser`-Sammlungsobjekt abgerufen wird, wird zum Löschen des Benutzers verwendet.

1. Löschen Sie den Benutzer aus AEM Forms.

   Löschen Sie den Benutzer, indem Sie den Feldwert `oid` des Objekts an die `DirectoryManagerServiceClient`-Methode des Objekts `deleteLocalUser` übergeben.`User`

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erstellen von Gruppen      {#creating-groups}

Sie können die Directory Manager-Dienst-API (Java und Webdienst) verwenden, um AEM Forms-Gruppen programmgesteuert zu erstellen. Nachdem Sie eine Gruppe erstellt haben, können Sie diese Gruppe verwenden, um einen Dienstvorgang durchzuführen, für den eine Gruppe erforderlich ist. Beispielsweise können Sie der neuen Gruppe einen Benutzer zuweisen. (Siehe [Verwalten von Benutzern und Gruppen](users.md#managing-users-and-groups).)

### Zusammenfassung der Schritte {#summary_of_steps-2}

So erstellen Sie eine Gruppe:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Stellen Sie fest, dass die Gruppe nicht vorhanden ist.
1. Erstellen Sie die Gruppe.
1. Führen Sie eine Aktion mit der Gruppe durch.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)
* jbossall-client.jar (Erforderlich, wenn AEM Forms unter JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Directory Manager-Dienstvorgang programmgesteuert durchführen können, erstellen Sie einen Directory Manager-Dienst-API-Client.

**Bestimmen, ob die Gruppe vorhanden ist**

Wenn Sie eine Gruppe erstellen, stellen Sie sicher, dass die Gruppe nicht in derselben Domäne vorhanden ist. Das heißt, zwei Gruppen können nicht denselben Namen innerhalb derselben Domäne haben. Um diese Aufgabe durchzuführen, führen Sie eine Suche durch und filtern Sie die Suchergebnisse anhand zweier Werte. Stellen Sie den Prinzipaltyp auf `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` ein, um sicherzustellen, dass nur Gruppen zurückgegeben werden. Achten Sie außerdem darauf, den Domänennamen anzugeben.

**Gruppe erstellen**

Nachdem Sie festgestellt haben, dass die Gruppe nicht in der Domäne vorhanden ist, erstellen Sie die Gruppe und geben Sie die folgenden Attribute an:

* **CommonName**: Der Name der Gruppe.
* **Domäne**: Die Domäne, in der die Gruppe hinzugefügt wird.
* **Beschreibung**: Eine Beschreibung der Gruppe.

**Durchführen einer Aktion mit der Gruppe**

Nachdem Sie eine Gruppe erstellt haben, können Sie eine Aktion mit der Gruppe durchführen. Sie können der Gruppe beispielsweise einen Benutzer hinzufügen. Um einen Benutzer zu einer Gruppe hinzuzufügen, rufen Sie den eindeutigen Bezeichnerwert des Benutzers und der Gruppe ab. Übergeben Sie diese Werte an die `addPrincipalToLocalGroup`-Methode.

**Siehe auch**

[Erstellen von Gruppen mit der Java-API](users.md#create-groups-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Hinzufügen von Benutzern](users.md#adding-users)

[Löschen von Benutzern](users.md#deleting-users)

### Gruppen mit der Java-API {#create-groups-using-the-java-api} erstellen

Erstellen Sie eine Gruppe mithilfe der Directory Manager Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Bestimmen Sie, ob die Gruppe vorhanden ist.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Prinzipaltyp fest, indem Sie das `PrincipalSearchFilter`-Objekt des Objekts `setPrincipalType` aufrufen. Übergeben Sie den Wert `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP`.
   * Legen Sie die Domäne fest, indem Sie das `PrincipalSearchFilter`-Objekt des Objekts `setSpecificDomainName` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Domänennamen angibt.
   * Um eine Gruppe zu suchen, rufen Sie die `DirectoryManagerServiceClient`-Methode des Objekts `findPrincipals` auf (ein Prinzipal kann eine Gruppe sein). Übergeben Sie das `PrincipalSearchFilter`-Objekt, das den Prinzipaltyp und den Domänennamen angibt. Diese Methode gibt eine `java.util.List`-Instanz zurück, bei der jedes Element eine `Group`-Instanz ist. Jede Gruppeninstanz entspricht dem mit dem `PrincipalSearchFilter`-Objekt angegebenen Filter.
   * Durchlaufen Sie die `java.util.List`-Instanz. Rufen Sie für jedes Element den Gruppennamen ab. Stellen Sie sicher, dass der Gruppenname nicht dem neuen Gruppennamen entspricht.

1. Erstellen Sie die Gruppe.

   * Wenn die Gruppe nicht vorhanden ist, rufen Sie die `Group`-Methode des Objekts `setCommonName` auf und übergeben Sie einen Zeichenfolgenwert, der den Gruppennamen angibt.
   * Rufen Sie die `setDescription`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der die Gruppenbeschreibung angibt.`Group`
   * Rufen Sie die `setDomainName`-Methode des Objekts auf und übergeben Sie einen Zeichenfolgenwert, der den Domänennamen angibt.`Group`
   * Rufen Sie die `createLocalGroup`-Methode des Objekts auf und übergeben Sie die `Group`-Instanz.`DirectoryManagerServiceClient`

   Die `createLocalUser`-Methode gibt einen Zeichenfolgenwert zurück, der den lokalen Benutzer-ID-Wert angibt.

1. Führen Sie eine Aktion mit der Gruppe durch.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Wert für die Benutzerkennung fest, indem Sie die `PrincipalSearchFilter`-Methode des Objekts `setUserId` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Wert der Benutzerkennung darstellt.
   * Rufen Sie die `findPrincipals`-Methode des Objekts auf und übergeben Sie das `PrincipalSearchFilter`-Objekt. `DirectoryManagerServiceClient` Diese Methode gibt eine `java.util.List`-Instanz zurück, wobei jedes Element ein `User`-Objekt ist. Durchlaufen Sie die `java.util.List`-Instanz, um den Benutzer zu suchen.
   * hinzufügen Sie einen Benutzer zur Gruppe, indem Sie die `DirectoryManagerServiceClient`-Objektmethode `addPrincipalToLocalGroup` aufrufen. Übergeben Sie den Rückgabewert der `User`-Methode des Objekts `getOid`. Übergeben Sie den Rückgabewert der `Group`-Methode des Objekts `getOid` (verwenden Sie die `Group`-Instanz, die die neue Gruppe darstellt).

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verwalten von Benutzern und Gruppen {#managing-users-and-groups}

In diesem Thema wird beschrieben, wie Sie Domänen, Abfragen und Benutzergruppen programmgesteuert zuweisen, entfernen und zur  verwenden können (Java).

>[!NOTE]
>
>Beim Konfigurieren einer Domäne müssen Sie den eindeutigen Bezeichner für Gruppen und Benutzer festlegen. Das ausgewählte Attribut muss nicht nur innerhalb der LDAP-Umgebung eindeutig sein, sondern muss auch unveränderlich sein und darf sich nicht im Ordner ändern. Dieses Attribut muss auch ein einfacher Zeichenfolgendatentyp sein (die einzige Ausnahme, die derzeit für Active Directory 2000/2003 zulässig ist, ist `"objectsid"`, ein binärer Wert). Das Novell eDirectory-Attribut `"GUID"` ist beispielsweise kein einfacher String-Datentyp und funktioniert daher nicht.

* Verwenden Sie für Active Directory `"objectsid"`.
* Verwenden Sie für SunOne `"nsuniqueid"`.

>[!NOTE]
>
>Das Erstellen mehrerer lokaler Benutzer und Gruppen während der Synchronisierung des LDAP-Ordners wird nicht unterstützt. Wird dies dennoch versucht, können Fehler auftreten.

### Zusammenfassung der Schritte {#summary_of_steps-3}

So verwalten Sie Benutzer und Gruppen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Rufen Sie die entsprechenden Benutzer- oder Gruppenvorgänge auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Directory Manager-Dienstvorgang programmgesteuert durchführen können, müssen Sie einen Directory Manager-Dienstclient erstellen. Mit der Java-API wird dies erreicht, indem ein `DirectoryManagerServiceClient`-Objekt erstellt wird. Mit der Webdienst-API wird dies durch Erstellen eines Objekts `DirectoryManagerServiceService` erreicht.

**Aufrufen der entsprechenden Benutzer- oder Gruppenvorgänge**

Nachdem Sie den Dienstclient erstellt haben, können Sie die Benutzer- oder Gruppenverwaltungsvorgänge aufrufen. Mit dem Dienstclient können Sie Domänen, Benutzer und Abfragen zuweisen, entfernen und Gruppen zuweisen. Beachten Sie, dass es möglich ist, einer lokalen Gruppe entweder einen Ordnerprinzipal oder einen lokalen Prinzipal hinzuzufügen, es ist jedoch nicht möglich, einen lokalen Prinzipal zu einer Ordnergruppe hinzuzufügen.

**Siehe auch**

[Verwalten von Benutzern und Gruppen mithilfe der Java-API](users.md#managing-users-and-groups-using-the-java-api)

[Verwalten von Benutzern und Gruppen mithilfe der Webdienst-API](users.md#managing-users-and-groups-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur User Manager API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Verwalten von Benutzern und Gruppen mit der Java-API {#managing-users-and-groups-using-the-java-api}

So verwalten Sie Benutzer, Gruppen und Domänen programmgesteuert mit Java:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält. Weitere Informationen finden Sie unter [Verbindungseigenschaften festlegen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)*.*

1. Rufen Sie die entsprechenden Benutzer- oder Gruppenvorgänge auf.

   Um einen Benutzer oder eine Gruppe zu suchen, rufen Sie eine der Methoden des Objekts `DirectoryManagerServiceClient` auf, um Prinzipale zu finden (da Prinzipale ein Benutzer oder eine Gruppe sein können). Im folgenden Beispiel wird die `findPrincipals`-Methode mit einem Suchfilter (einem `PrincipalSearchFilter`-Objekt) aufgerufen.

   Da der Rückgabewert in diesem Fall ein `java.util.List`-Objekt mit `Principal`-Objekten ist, durchlaufen Sie das Ergebnis und konvertieren Sie die `Principal`-Objekte in entweder `User`- oder `Group`-Objekte.

   Rufen Sie mithilfe des Zielobjekts `User` oder `Group` (das beide von der `Principal`-Schnittstelle erben) die Informationen ab, die Sie in Ihrer Workflows benötigen. Beispielsweise können Domänennamen und kanonische Namenswerte in Kombination einen Prinzipal eindeutig identifizieren. Diese werden abgerufen, indem die Methoden `Principal` des Objekts `getDomainName` bzw. `getCanonicalName` aufgerufen werden.

   Um einen lokalen Benutzer zu löschen, rufen Sie die `DirectoryManagerServiceClient`-Methode des Objekts `deleteLocalUser` auf und übergeben Sie den Bezeichner des Benutzers.

   Um eine lokale Gruppe zu löschen, rufen Sie die `DirectoryManagerServiceClient`-Methode des Objekts `deleteLocalGroup` auf und übergeben Sie die Kennung der Gruppe.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verwalten von Benutzern und Gruppen mithilfe der Webdienst-API {#managing-users-and-groups-using-the-web-service-api}

Führen Sie die folgenden Aufgaben aus, um Benutzer, Gruppen und Domänen mit der Directory Manager-Dienst-API (Webdienst) programmgesteuert zu verwalten:

1. Schließen Sie Projektdateien ein.

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Directory Manager-WSDL verwendet. (Siehe [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding) verwendet.)

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceService`-Objekt mit dem Konstruktor der Proxyklasse.

1. Rufen Sie die entsprechenden Benutzer- oder Gruppenvorgänge auf.

   Um einen Benutzer oder eine Gruppe zu suchen, rufen Sie eine der Methoden des Objekts `DirectoryManagerServiceService` auf, um Prinzipale zu finden (da Prinzipale ein Benutzer oder eine Gruppe sein können). Im folgenden Beispiel wird die `findPrincipalsWithFilter`-Methode mit einem Suchfilter (einem `PrincipalSearchFilter`-Objekt) aufgerufen. Bei Verwendung eines `PrincipalSearchFilter`-Objekts werden lokale Prinzipale nur zurückgegeben, wenn die `isLocal`-Eigenschaft auf `true` eingestellt ist. Dieses Verhalten unterscheidet sich von dem mit der Java-API.

   >[!NOTE]
   >
   >Wenn die maximale Anzahl von Ergebnissen nicht im Suchfilter angegeben ist (über das Feld `PrincipalSearchFilter.resultsMax`), werden maximal 1000 Ergebnisse zurückgegeben. Dieses Verhalten unterscheidet sich von dem, was mit der Java-API passiert, bei der 10 Ergebnisse das standardmäßige Maximum sind. Die Suchmethoden wie `findGroupMembers` geben nur dann Ergebnisse zurück, wenn die maximale Anzahl von Ergebnissen im Suchfilter angegeben ist (z. B. über das Feld `GroupMembershipSearchFilter.resultsMax`). Dies gilt für alle Filter, die von der `GenericSearchFilter`-Klasse erben. Weitere Informationen finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Da der Rückgabewert in diesem Fall ein `object[]`-Objekt mit `Principal`-Objekten ist, durchlaufen Sie das Ergebnis und konvertieren Sie die `Principal`-Objekte in entweder `User`- oder `Group`-Objekte.

   Rufen Sie mithilfe des Zielobjekts `User` oder `Group` (das beide von der `Principal`-Schnittstelle erben) die Informationen ab, die Sie in Ihrer Workflows benötigen. Beispielsweise können Domänennamen und kanonische Namenswerte in Kombination einen Prinzipal eindeutig identifizieren. Diese werden abgerufen, indem die Felder `Principal` des Objekts `domainName` bzw. `canonicalName` aufgerufen werden.

   Um einen lokalen Benutzer zu löschen, rufen Sie die `DirectoryManagerServiceService`-Methode des Objekts `deleteLocalUser` auf und übergeben Sie den Bezeichner des Benutzers.

   Um eine lokale Gruppe zu löschen, rufen Sie die `DirectoryManagerServiceService`-Methode des Objekts `deleteLocalGroup` auf und übergeben Sie die Kennung der Gruppe.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Verwalten von Rollen und Berechtigungen {#managing-roles-and-permissions}

In diesem Thema wird beschrieben, wie Sie mit der Autorisierungs-Manager-Dienst-API (Java) Rollen und Berechtigungen programmgesteuert zuweisen, entfernen und festlegen können.

Unter AEM Forms ist eine *role* eine Gruppe von Berechtigungen für den Zugriff auf eine oder mehrere Ressourcen auf Systemebene. Diese Berechtigungen werden über User Management erstellt und von den Dienstkomponenten erzwungen. Beispielsweise könnte ein Administrator einer Benutzergruppe die Rolle &quot;Richtliniensatzautor&quot;zuweisen. Rights Management würde es dann den Benutzern dieser Gruppe mit dieser Rolle ermöglichen, Richtliniensätze über Administration Console zu erstellen.

Es gibt zwei Arten von Rollen: *Standardrollen* und *benutzerdefinierte Rollen*. Standardrollen (*Systemrollen)* befinden sich bereits in AEM Forms. Es wird davon ausgegangen, dass Standardrollen vom Administrator möglicherweise nicht gelöscht oder geändert werden und daher unveränderlich sind. Benutzerdefinierte Rollen, die vom Administrator erstellt wurden und die dann geändert oder gelöscht werden können, sind somit veränderbar.

Rollen erleichtern die Verwaltung von Berechtigungen. Wenn einem Prinzipal eine Rolle zugewiesen wird, wird diesem Prinzipal automatisch eine Reihe von Berechtigungen zugewiesen, und alle spezifischen Entscheidungen zum Zugriff für den Prinzipal basieren auf dieser Gesamtzahl zugewiesener Berechtigungen.

### Zusammenfassung der Schritte {#summary_of_steps-4}

So verwalten Sie Rollen und Berechtigungen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen AuthorizationManagerService-Client.
1. Rufen Sie die entsprechenden Rollen- oder Berechtigungsvorgänge auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines AuthorizationManagerService-Clients**

Bevor Sie einen User Management AuthorizationManagerService-Vorgang programmgesteuert durchführen können, müssen Sie einen AuthorizationManagerService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `AuthorizationManagerServiceClient`-Objekt erstellt wird.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Dienstclient erstellt haben, können Sie die Rollen- oder Berechtigungsvorgänge aufrufen. Mit dem Dienstclient können Sie Rollen und Berechtigungen zuweisen, entfernen und festlegen.

**Siehe auch**

[Rollen und Berechtigungen mithilfe der Java-API verwalten](users.md#managing-roles-and-permissions-using-the-java-api)

[Rollen und Berechtigungen mithilfe der Webdienst-API verwalten](users.md#managing-roles-and-permissions-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur User Manager API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Rollen und Berechtigungen mithilfe der Java-API {#managing-roles-and-permissions-using-the-java-api} verwalten

Führen Sie die folgenden Aufgaben aus, um Rollen und Berechtigungen mithilfe der Authorization Manager-Dienst-API (Java) zu verwalten:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen AuthorizationManagerService-Client.

   Erstellen Sie ein `AuthorizationManagerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie die entsprechenden Rollen- oder Berechtigungsvorgänge auf.

   Um einem Prinzipal eine Rolle zuzuweisen, rufen Sie die `AuthorizationManagerServiceClient`-Methode des Objekts `assignRole` auf und übergeben Sie die folgenden Werte:

   * Ein `java.lang.String`-Objekt, das die Rollenkennung enthält
   * Ein Array von `java.lang.String`-Objekten, die die Hauptkennungen enthalten.

   Um eine Rolle aus einem Prinzipal zu entfernen, rufen Sie die `AuthorizationManagerServiceClient`-Methode des Objekts `unassignRole` auf und übergeben Sie die folgenden Werte:

   * Ein `java.lang.String`-Objekt, das die Rollenkennung enthält.
   * Ein Array von `java.lang.String`-Objekten, die die Hauptkennungen enthalten.


**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Quick Beginn (SOAP-Modus): Rollen und Berechtigungen mithilfe der Java-API verwalten](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Rollen und Berechtigungen mithilfe der Webdienst-API {#managing-roles-and-permissions-using-the-web-service-api} verwalten

Rollen und Berechtigungen mithilfe der Authorization Manager-Dienst-API (Webdienst) verwalten:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AuthorizationManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen AuthorizationManagerService-Client.

   * Erstellen Sie ein `AuthorizationManagerServiceClient`-Objekt mit dem Standardkonstruktor.
   * Erstellen Sie ein `AuthorizationManagerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress`. Übergeben Sie einen Zeichenfolgenwert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AuthorizationManagerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt, indem Sie den Wert des Felds `AuthorizationManagerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das Feld `System.ServiceModel.BasicHttpBinding` des Objekts auf `MessageEncoding`. `WSMessageEncoding.Mtom` Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AuthorizationManagerServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `AuthorizationManagerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie die entsprechenden Rollen- oder Berechtigungsvorgänge auf.

   Um einem Prinzipal eine Rolle zuzuweisen, rufen Sie die `AuthorizationManagerServiceClient`-Methode des Objekts `assignRole` auf und übergeben Sie die folgenden Werte:

   * Ein `string`-Objekt, das die Rollenkennung enthält
   * Ein `MyArrayOf_xsd_string`-Objekt, das die Hauptkennungen enthält.

   Um eine Rolle aus einem Prinzipal zu entfernen, rufen Sie die `AuthorizationManagerServiceService`-Methode des Objekts `unassignRole` auf und übergeben Sie die folgenden Werte:

   * Ein `string`-Objekt, das die Rollenkennung enthält.
   * Ein Array von `string`-Objekten, die die Hauptkennungen enthalten.


**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Authentifizieren von Benutzern {#authenticating-users}

In diesem Thema wird beschrieben, wie Sie mit der Authentication Manager Service API (Java) die programmgesteuerte Authentifizierung von Benutzern durch Clientanwendungen aktivieren können.

Die Benutzerauthentifizierung ist ggf. erforderlich, um mit einer Unternehmensdatenbank oder anderen Enterprise-Repositorys zu interagieren, die sichere Daten speichern.

Beispiel: Ein Benutzer gibt einen Benutzernamen und ein Kennwort auf einer Webseite ein und sendet die Werte an einen J2EE-Anwendungsserver, auf dem Forms gehostet wird. Eine benutzerdefinierte Forms-Anwendung kann den Benutzer mit dem Authentication Manager-Dienst authentifizieren.

Bei erfolgreicher Authentifizierung greift die Anwendung auf eine gesicherte Unternehmensdatenbank zu. Andernfalls wird eine Meldung gesendet, dass der Benutzer kein autorisierter Benutzer ist.

Das folgende Diagramm zeigt den logischen Ablauf der Anwendung.

![au_au_umauth_process](assets/au_au_umauth_process.png)

Die folgende Tabelle beschreibt die Schritte in diesem Diagramm

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>3</p></td>
   <td><p>Der Benutzer greift auf eine Website zu und gibt einen Benutzernamen und ein Kennwort an. Diese Informationen werden an einen J2EE-Anwendungsserver übermittelt, der als Host für AEM Forms dient.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Die Benutzeranmeldeinformationen werden beim Authentication Manager-Dienst authentifiziert. Wenn die Benutzerberechtigungen gültig sind, fährt der Workflow mit Schritt 3 fort. Andernfalls wird eine Meldung gesendet, dass der Benutzer kein autorisierter Benutzer ist.</p></td>
  </tr>
  <tr>
   <td><p>3</p></td>
   <td><p>Benutzerinformationen und Formularentwürfe werden aus einer gesicherten Unternehmensdatenbank abgerufen. </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Benutzerinformationen werden mit einem Formularentwurf zusammengeführt und das Formular wird dem Benutzer wiedergegeben. </p></td>
  </tr>
 </tbody>
</table>

### Zusammenfassung der Schritte {#summary_of_steps-5}

So authentifizieren Sie einen Benutzer programmatisch:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen AuthenticationManagerService-Client.
1. Rufen Sie den Authentifizierungsvorgang auf.
1. Rufen Sie bei Bedarf den Kontext ab, damit die Clientanwendung ihn zur Authentifizierung an einen anderen AEM Forms-Dienst weiterleiten kann.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines AuthenticationManagerService-Clients**

Bevor Sie einen Benutzer programmgesteuert authentifizieren können, müssen Sie einen AuthenticationManagerService-Client erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `AuthenticationManagerServiceClient`-Objekt.

**Authentifizierungsvorgang aufrufen**

Nachdem Sie den Dienstclient erstellt haben, können Sie den Authentifizierungsvorgang aufrufen. Dieser Vorgang erfordert Informationen zum Benutzer, z. B. den Namen und das Kennwort des Benutzers. Wenn der Benutzer sich nicht authentifiziert, wird eine Ausnahme ausgelöst.

**Authentifizierungskontext abrufen**

Nachdem Sie den Benutzer authentifiziert haben, können Sie einen Kontext erstellen, der auf dem authentifizierten Benutzer basiert. Anschließend können Sie mit den Inhalten weitere AEM Forms-Dienste aufrufen. Sie können beispielsweise den Kontext verwenden, um ein `EncryptionServiceClient` zu erstellen und ein PDF-Dokument mit einem Kennwort zu verschlüsseln. Stellen Sie sicher, dass der authentifizierte Benutzer die Rolle `Services User` hat, die zum Aufrufen eines AEM Forms-Dienstes erforderlich ist.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur User Manager API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[PDF-Dokumente mit einem Kennwort verschlüsseln](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Authentifizieren Sie einen Benutzer mit der Java-API {#authenticate-a-user-using-the-java-api}

Authentifizieren Sie einen Benutzer mit der Authentication Manager Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen AuthenticationManagerServices-Client.

   Erstellen Sie ein `AuthenticationManagerServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie den Authentifizierungsvorgang auf.

   Rufen Sie die `authenticate`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AuthenticationManagerServiceClient`

   * Ein `java.lang.String`-Objekt, das den Namen des Benutzers enthält.
   * Ein Bytearray (ein `byte[]`-Objekt), das das Kennwort des Benutzers enthält. Sie können das `byte[]`-Objekt abrufen, indem Sie die `java.lang.String`-Methode des Objekts `getBytes` aufrufen.

   Die Methode authentication gibt ein `AuthResult`-Objekt zurück, das Informationen zum authentifizierten Benutzer enthält.

1. Rufen Sie den Authentifizierungskontext ab.

   Rufen Sie die `getContext`-Methode des Objekts auf, die ein `Context`-Objekt zurückgibt.`ServiceClientFactory`

   Rufen Sie dann die `Context`-Methode des Objekts `initPrincipal` auf und übergeben Sie `AuthResult`.

### Authentifizieren Sie einen Benutzer mit der Webdienst-API {#authenticate-a-user-using-the-web-service-api}

Authentifizieren Sie einen Benutzer mit der Authentication Manager-Dienst-API (Webdienst):

1. Schließen Sie Projektdateien ein.

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL des Authentication Manager verwendet. (Siehe [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. (Siehe &quot;Referenzieren der .NET-Clientassembly&quot;in [Aufrufen von AEM Forms mit Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

1. Erstellen Sie einen AuthenticationManagerService-Client.

   Erstellen Sie ein `AuthenticationManagerServiceService`-Objekt mit dem Konstruktor der Proxyklasse.

1. Rufen Sie den Authentifizierungsvorgang auf.

   Rufen Sie die `authenticate`-Methode des Objekts auf und übergeben Sie die folgenden Werte:`AuthenticationManagerServiceClient`

   * Ein `string`-Objekt, das den Namen des Benutzers enthält
   * Ein Bytearray (ein `byte[]`-Objekt), das das Kennwort des Benutzers enthält. Sie können das `byte[]`-Objekt abrufen, indem Sie ein `string`-Objekt, das das Kennwort enthält, in ein `byte[]`-Array konvertieren, indem Sie die im folgenden Beispiel dargestellte Logik verwenden.
   * Der zurückgegebene Wert ist ein `AuthResult`-Objekt, mit dem Informationen zum Benutzer abgerufen werden können. Im unten stehenden Beispiel werden die Informationen des Benutzers abgerufen, indem zunächst das `AuthResult`-Objektfeld `authenticatedUser` abgerufen und anschließend die Felder `User` des Objekts `canonicalName` und `domainName` abgerufen werden.

**Siehe auch**

[Aufrufen von AEM Forms mit MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mit SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Programmgesteuertes Synchronisieren von Benutzern {#programmatically-synchronizing-users}

Sie können Benutzer mithilfe der User Management-API programmgesteuert synchronisieren. Wenn Sie Benutzer synchronisieren, aktualisieren Sie AEM Forms mit Benutzerdaten, die sich im Benutzerrepository befinden. Angenommen, Sie fügen Ihrem Benutzerrepository neue Benutzer hinzu. Nachdem Sie einen Synchronisierungsvorgang durchgeführt haben, werden die neuen Benutzer zu AEM Formularbenutzern. Außerdem werden Benutzer, die sich nicht mehr in Ihrer Benutzerrolle befinden, aus AEM Forms entfernt.

Das folgende Diagramm zeigt die Synchronisierung AEM Forms mit einem Benutzerverantwortlichen.

![ps_ps_umauth_sync](assets/ps_ps_umauth_sync.png)

Die folgende Tabelle beschreibt die Schritte in diesem Diagramm

<table>
 <thead>
  <tr>
   <th><p>Schritt</p></th>
   <th><p>Beschreibung</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>1</p></td>
   <td><p>Eine Clientanwendung fordert von AEM Forms einen Synchronisierungsvorgang an.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>AEM Forms führt einen Synchronisierungsvorgang durch.</p></td>
  </tr>
  <tr>
   <td><p>1</p></td>
   <td><p>Benutzerinformationen werden aktualisiert.</p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Ein Benutzer kann die aktualisierten Benutzerinformationen Ansicht haben. </p></td>
  </tr>
 </tbody>
</table>

### Zusammenfassung der Schritte {#summary_of_steps-6}

So synchronisieren Sie Benutzer programmgesteuert:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie einen UserManagerUtilServiceClient-Client.
1. Geben Sie die Unternehmensdomäne an.
1. Rufen Sie den Authentifizierungsvorgang auf.
1. Überprüfen Sie, ob der Synchronisierungsvorgang abgeschlossen ist.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**UserManagerUtilServiceClient erstellen**

Bevor Sie Benutzer programmgesteuert synchronisieren können, müssen Sie ein `UserManagerUtilServiceClient`-Objekt erstellen.

**Unternehmensdomäne angeben**

Bevor Sie einen Synchronisierungsvorgang mit der User Management-API durchführen, geben Sie die Unternehmensdomäne an, zu der die Benutzer gehören. Sie können eine oder mehrere Unternehmensdomänen angeben. Bevor Sie einen Synchronisierungsvorgang programmgesteuert durchführen können, müssen Sie eine Unternehmensdomäne mit Administration Console einrichten. (Siehe [Administration help](https://www.adobe.com/go/learn_aemforms_admin_63).)

**Synchronisierungsvorgang aufrufen**

Nachdem Sie eine oder mehrere Unternehmensdomänen angegeben haben, können Sie den Synchronisierungsvorgang durchführen. Die für die Durchführung dieses Vorgangs benötigte Zeit hängt von der Anzahl der Benutzerdatensätze ab, die sich im Benutzerrepository befinden.

**Überprüfen Sie, ob der Synchronisierungsvorgang abgeschlossen ist.**

Nachdem Sie einen Synchronisierungsvorgang programmgesteuert durchgeführt haben, können Sie feststellen, ob der Vorgang abgeschlossen ist.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beginn zur User Manager API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[PDF-Dokumente mit einem Kennwort verschlüsseln](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Programmierbare Synchronisierung von Benutzern mit der Java-API {#programmatically-synchronizing-users-using-the-java-api}

Synchronisieren Sie Benutzer mithilfe der User Management API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-usermanager-client.jar&quot;und &quot;adobe-usermanager-util-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen UserManagerUtilServiceClient-Client.

   Erstellen Sie ein `UserManagerUtilServiceClient`-Objekt, indem Sie den Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie die Unternehmensdomäne an.

   * Rufen Sie die `scheduleSynchronization`-Methode des Objekts auf, um den Benutzersynchronisierungsvorgang Beginn.`UserManagerUtilServiceClient`
   * Erstellen Sie eine `java.util.Set`-Instanz mit einem `HashSet`-Konstruktor. Stellen Sie sicher, dass Sie `String` als Datentyp angeben. Diese `Java.util.Set`-Instanz speichert die Domänennamen, für die der Synchronisierungsvorgang gilt.
   * Rufen Sie für jeden hinzuzufügenden Domänennamen die add-Methode des Objekts `java.util.Set` auf und übergeben Sie den Domänennamen.

1. Rufen Sie den Synchronisierungsvorgang auf.

   Rufen Sie die `getContext`-Methode des Objekts auf, die ein `Context`-Objekt zurückgibt.`ServiceClientFactory`

   Rufen Sie dann die `Context`-Methode des Objekts `initPrincipal` auf und übergeben Sie `AuthResult`.

**Siehe auch**

[Programmgesteuertes Synchronisieren von Benutzern](users.md#programmatically-synchronizing-users)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
