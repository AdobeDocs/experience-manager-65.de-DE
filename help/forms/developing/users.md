---
title: Verwalten von Benutzern
seo-title: Verwalten von Benutzern
description: Verwenden Sie die User Management-API, um Clientanwendungen zu erstellen, die Rollen, Berechtigungen und Prinzipale (d. h. Benutzer oder Gruppen) verwalten und Benutzer authentifizieren können.
seo-description: Verwenden Sie die User Management-API, um Clientanwendungen zu erstellen, die Rollen, Berechtigungen und Prinzipale (d. h. Benutzer oder Gruppen) verwalten und Benutzer authentifizieren können.
uuid: 68d8a0bc-6e3d-4286-ba5c-534dcf58cb84
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 95804bff-9e6f-4807-aae4-790bd9e7cb57
role: Developer
exl-id: d7c5bb84-a988-4b2e-a587-f4e5b50fea58
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '6257'
ht-degree: 4%

---

# Verwalten von Benutzern {#managing-users}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

**Über die Benutzerverwaltung**

Sie können die User Management-API verwenden, um Clientanwendungen zu erstellen, die Rollen, Berechtigungen und Prinzipale (d. h. Benutzer oder Gruppen) verwalten und Benutzer authentifizieren können. Die User Management-API besteht aus den folgenden AEM Forms-APIs:

* Directory Manager-Dienst-API
* Authentifizierungs-Manager-Dienst-API
* Autorisierungsmanager-Dienst-API

Mit der Benutzerverwaltung können Sie Rollen und Berechtigungen zuweisen, entfernen und festlegen. Außerdem können Sie Domänen, Benutzer und Gruppen zuweisen, entfernen und abfragen. Schließlich können Sie User Management verwenden, um Benutzer zu authentifizieren.

Unter [Hinzufügen von Benutzern](users.md#adding-users) erfahren Sie, wie Sie Benutzer programmgesteuert hinzufügen. In diesem Abschnitt wird die Directory Manager-Dienst-API verwendet.

Unter [Löschen von Benutzern](users.md#deleting-users) erfahren Sie, wie Sie Benutzer programmgesteuert löschen. In diesem Abschnitt wird die Directory Manager-Dienst-API verwendet.

Unter [Verwalten von Benutzern und Gruppen](users.md#managing-users-and-groups) finden Sie Informationen zum Unterschied zwischen einem lokalen Benutzer und einem Ordnerbenutzer. Außerdem finden Sie Beispiele für die Verwendung der Java- und Webdienst-APIs zur programmgesteuerten Verwaltung von Benutzern und Gruppen. In diesem Abschnitt wird die Directory Manager-Dienst-API verwendet.

Unter [Verwalten von Rollen und Berechtigungen](users.md#managing-roles-and-permissions) erfahren Sie mehr über die Systemrollen und -berechtigungen und darüber, was Sie programmgesteuert tun können, um sie zu erweitern, und Beispiele für die Verwendung der Java- und Webdienst-APIs zur programmatischen Verwaltung von Rollen und Berechtigungen. In diesem Abschnitt werden sowohl die Directory Manager-Dienst-API als auch die Authorization Manager-Dienst-API verwendet.

Unter [Authentifizieren von Benutzern](users.md#authenticating-users) finden Sie Beispiele für die Verwendung der Java- und Webdienst-APIs zur programmatischen Authentifizierung von Benutzern. In diesem Abschnitt wird die Autorisierungs-Manager-Dienst-API verwendet.

**Grundlagen zum Authentifizierungsprozess**

User Management bietet integrierte Authentifizierungsfunktionen und bietet Ihnen außerdem die Möglichkeit, eine Verbindung zu Ihrem eigenen Authentifizierungsanbieter herzustellen. Wenn User Management eine Authentifizierungsanfrage erhält (z. B. ein Benutzer versucht, sich anzumelden), werden Benutzerinformationen zur Authentifizierung an den Authentifizierungsanbieter weitergeleitet. User Management erhält die Ergebnisse vom Authentifizierungsanbieter, nachdem er den Benutzer authentifiziert hat.

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
   <td><p>User Management ermöglicht dem Benutzer entweder die Anmeldung oder verweigert den Zugriff auf das Produkt.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Wenn die Zeitzone des Servers von der Zeitzone des Clients abweicht und der WSDL-Dienst für den AEM Forms Generate PDF-Dienst auf einem nativen SOAP-Stapel mit einem .NET-Client auf einem WebSphere Application Server-Cluster verwendet wird, kann der folgende User Management-Authentifizierungsfehler auftreten:

`[com.adobe.idp.um.webservices.WSSecurityHandler] errorCode:12803 errorCodeHEX:0x3203 message:WSSecurityHandler: UM authenticate returns exception : An error was discovered processing the <wsse:Security> header. (WSSecurityEngine: Invalid timestamp The security semantics of message have expired).`

**Grundlegendes zur Ordnerverwaltung**

User Management ist mit einem Verzeichnisdienstanbieter (dem DirectoryManagerService) gepackt, der Verbindungen zu LDAP-Ordnern unterstützt. Wenn Ihr Unternehmen zum Speichern von Benutzerdatensätzen ein Nicht-LDAP-Repository verwendet, können Sie einen eigenen Ordnerdienstanbieter erstellen, der mit Ihrem Repository funktioniert.

Verzeichnisdienstanbieter rufen auf Anfrage von User Management Einträge aus einem Benutzerspeicher ab. User Management speichert regelmäßig Benutzer- und Gruppendatensätze in der Datenbank zwischen, um die Leistung zu verbessern.

Der Ordnerdienstanbieter kann verwendet werden, um die User Management-Datenbank mit dem Benutzerspeicher zu synchronisieren. Dieser Schritt stellt sicher, dass alle Benutzerordnerinformationen sowie alle Benutzer- und Gruppendatensätze auf dem neuesten Stand sind.

Darüber hinaus bietet Ihnen der DirectoryManagerService die Möglichkeit, Domänen zu erstellen und zu verwalten. Domänen definieren unterschiedliche Benutzergrundlagen. Die Begrenzung einer Domäne wird in der Regel entsprechend der Struktur Ihres Unternehmens oder der Einrichtung Ihres Benutzerspeichers definiert. User Management-Domänen bieten Konfigurationseinstellungen, die von Authentifizierungs- und Ordnerdienstanbietern verwendet werden.

In der Konfigurations-XML, die User Management exportiert, enthält der Stammknoten mit dem Attributwert `Domains` ein XML-Element für jede für User Management definierte Domäne. Jedes dieser Elemente enthält andere Elemente, die Aspekte der Domäne definieren, die bestimmten Dienstleistern zugeordnet sind.

**Grundlegendes zu objectSID-Werten**

Bei der Verwendung von Active Directory ist es wichtig zu verstehen, dass ein `objectSID` -Wert kein eindeutiges Attribut über mehrere Domänen hinweg ist. Dieser Wert speichert die Sicherheitskennung eines Objekts. In einer Umgebung mit mehreren Domänen (z. B. einer Baumstruktur von Domänen) kann der Wert `objectSID` unterschiedlich sein.

Ein `objectSID` -Wert würde sich ändern, wenn ein Objekt von einer Active Directory-Domäne auf eine andere Domäne verschoben wird. Einige Objekte haben denselben `objectSID`-Wert an einer beliebigen Stelle in der Domäne. Beispielsweise hätten Gruppen wie &quot;BUILTIN\Administrators&quot;, &quot;BUILTIN\Power Users&quot;usw. unabhängig von den Domänen denselben `objectSID`-Wert. Diese `objectSID`-Werte sind bekannt.

## Benutzer hinzufügen {#adding-users}

Sie können die Directory Manager-Dienst-API (Java und Webdienst) verwenden, um AEM Forms programmgesteuert Benutzer hinzuzufügen. Nachdem Sie einen Benutzer hinzugefügt haben, können Sie diesen Benutzer beim Ausführen eines Dienstvorgangs verwenden, für den ein Benutzer erforderlich ist. Beispielsweise können Sie dem neuen Benutzer eine Aufgabe zuweisen.

### Zusammenfassung der Schritte {#summary-of-steps}

Gehen Sie wie folgt vor, um einen Benutzer hinzuzufügen:

1. Projektdateien einschließen.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Definieren Sie Benutzerinformationen.
1. Fügen Sie den Benutzer zu AEM Forms hinzu.
1. Stellen Sie sicher, dass der Benutzer hinzugefügt wird.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Verzeichnismanager-Dienstvorgang programmgesteuert ausführen können, erstellen Sie einen Directory Manager-Dienst-API-Client.

**Definieren von Benutzerinformationen**

Wenn Sie einen neuen Benutzer mithilfe der Directory Manager-Dienst-API hinzufügen, definieren Sie Informationen für diesen Benutzer. Wenn Sie einen neuen Benutzer hinzufügen, definieren Sie normalerweise die folgenden Werte:

* **Domänenname**: Die Domäne, zu der der Benutzer gehört (z. B.  `DefaultDom`).
* **User identifier value**: Der Kennungswert des Benutzers (z. B.  `wblue`).
* **Prinzipaltyp**: Der Typ des Benutzers (Sie können beispielsweise  `USER)`angeben).
* **Vorname**: Ein Vorname für den Benutzer (z. B.  `Wendy`).
* **Nachname**: Der Familienname für den Benutzer (z. B.  `Blue)`.
* **Gebietsschema**: Gebietsschema-Informationen für den Benutzer.

**Benutzer zu AEM Forms hinzufügen**

Nachdem Sie Benutzerinformationen definiert haben, können Sie den Benutzer zu AEM Forms hinzufügen. Um einen Benutzer hinzuzufügen, rufen Sie die `createLocalUser` -Methode des Objekts `DirectoryManagerServiceClient` auf.

**Überprüfen, ob der Benutzer hinzugefügt wurde**

Sie können überprüfen, ob der Benutzer hinzugefügt wurde, um sicherzustellen, dass keine Probleme aufgetreten sind. Suchen Sie den neuen Benutzer mithilfe des Wertes der Benutzer-ID.

**Siehe auch**

[Hinzufügen von Benutzern mithilfe der Java-API](users.md#add-users-using-the-java-api)

[Hinzufügen von Benutzern mithilfe der Webdienst-API](users.md#add-users-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Löschen von Benutzern](users.md#deleting-users)

### Benutzer mit der Java-API hinzufügen {#add-users-using-the-java-api}

Fügen Sie Benutzer mithilfe der Directory Manager Service API (Java) hinzu:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerServices-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Definieren Sie Benutzerinformationen.

   * Erstellen Sie ein Objekt `UserImpl`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Standardnamen fest, indem Sie die `setDomainName` -Methode des Objekts `UserImpl` aufrufen. Übergeben Sie einen string -Wert, der den Domänennamen angibt.
   * Legen Sie den Prinzipaltyp fest, indem Sie die `setPrincipalType` -Methode des Objekts `UserImpl` aufrufen. Übergeben Sie einen string -Wert, der den Typ des Benutzers angibt. Sie können beispielsweise `USER` angeben.
   * Legen Sie den Benutzer-ID-Wert fest, indem Sie die `setUserid` -Methode des Objekts `UserImpl` aufrufen. Übergeben Sie einen string -Wert, der den Benutzer-ID-Wert angibt. Sie können beispielsweise `wblue` angeben.
   * Legen Sie den kanonischen Namen fest, indem Sie die `setCanonicalName` -Methode des Objekts `UserImpl` aufrufen. Übergeben Sie einen string -Wert, der den kanonischen Namen des Benutzers angibt. Sie können beispielsweise `wblue` angeben.
   * Legen Sie den angegebenen Namen fest, indem Sie die `setGivenName` -Methode des Objekts `UserImpl` aufrufen. Übergeben Sie einen string -Wert, der den Vornamen des Benutzers angibt. Sie können beispielsweise `Wendy` angeben.
   * Legen Sie den Familiennamen fest, indem Sie die `setFamilyName` -Methode des Objekts `UserImpl` aufrufen. Übergeben Sie einen string -Wert, der den Familiennamen des Benutzers angibt. Sie können beispielsweise `Blue` angeben.

   >[!NOTE]
   >
   >Rufen Sie eine Methode auf, die zum `UserImpl`-Objekt gehört, um andere Werte festzulegen. Sie können beispielsweise den Gebietsschemawert festlegen, indem Sie die `setLocale` -Methode des Objekts `UserImpl` aufrufen.

1. Fügen Sie den Benutzer zu AEM Forms hinzu.

   Rufen Sie die `createLocalUser` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Das `UserImpl`-Objekt, das den neuen Benutzer darstellt
   * Ein string -Wert, der das Kennwort des Benutzers darstellt

   Die `createLocalUser`-Methode gibt einen Zeichenfolgenwert zurück, der den lokalen Benutzer-ID-Wert angibt.

1. Stellen Sie sicher, dass der Benutzer hinzugefügt wurde.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Benutzer-ID-Wert fest, indem Sie die `setUserId` -Methode des Objekts `PrincipalSearchFilter` aufrufen. Übergeben Sie einen string -Wert, der den Benutzer-ID-Wert darstellt.
   * Rufen Sie die `findPrincipals` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie das `PrincipalSearchFilter` -Objekt. Diese Methode gibt eine `java.util.List`-Instanz zurück, wobei jedes Element ein `User`-Objekt ist. Durchsuchen Sie die `java.util.List`-Instanz, um den Benutzer zu suchen.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Benutzer mithilfe der Java-API hinzufügen](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-adding-users-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Hinzufügen von Benutzern mithilfe der Webdienst-API {#add-users-using-the-web-service-api}

Fügen Sie Benutzer mithilfe der Directory Manager-Dienst-API (Webdienst) hinzu:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition für die Dienstreferenz verwenden: `http://localhost:8080/soap/services/DirectoryManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen DirectoryManagerService-Client.

   * Erstellen Sie ein `DirectoryManagerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DirectoryManagerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Stellen Sie sicher, dass Sie `?blob=mtom` angeben.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DirectoryManagerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Definieren Sie Benutzerinformationen.

   * Erstellen Sie ein Objekt `UserImpl`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Standardnamen fest, indem Sie dem `domainName` -Feld des Objekts `UserImpl` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den Prinzipaltyp fest, indem Sie dem `principalType` -Feld des Objekts `UserImpl` einen Zeichenfolgenwert zuweisen. Sie können beispielsweise `USER` angeben.
   * Legen Sie den Benutzer-ID-Wert fest, indem Sie dem `userid` -Feld des Objekts `UserImpl` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den kanonischen Namenswert fest, indem Sie dem `canonicalName` -Feld des Objekts `UserImpl` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den angegebenen Namenswert fest, indem Sie dem `givenName` -Feld des Objekts `UserImpl` einen Zeichenfolgenwert zuweisen.
   * Legen Sie den Familiennamen-Wert fest, indem Sie dem `familyName` -Feld des Objekts `UserImpl` einen Zeichenfolgenwert zuweisen.

1. Fügen Sie den Benutzer zu AEM Forms hinzu.

   Rufen Sie die `createLocalUser` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Das `UserImpl`-Objekt, das den neuen Benutzer darstellt
   * Ein string -Wert, der das Kennwort des Benutzers darstellt

   Die `createLocalUser`-Methode gibt einen Zeichenfolgenwert zurück, der den lokalen Benutzer-ID-Wert angibt.

1. Stellen Sie sicher, dass der Benutzer hinzugefügt wurde.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Benutzer-ID-Wert des Benutzers fest, indem Sie dem `userId` -Feld des Objekts `PrincipalSearchFilter` einen Zeichenfolgenwert zuweisen, der den Benutzer-ID-Wert darstellt.
   * Rufen Sie die `findPrincipals` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie das `PrincipalSearchFilter` -Objekt. Diese Methode gibt ein Kollektionsobjekt `MyArrayOfUser` zurück, bei dem jedes Element ein `User`-Objekt ist. Durchsuchen Sie die `MyArrayOfUser`-Sammlung, um den Benutzer zu finden.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Löschen von Benutzern {#deleting-users}

Sie können die Directory Manager-Dienst-API (Java und Webdienst) verwenden, um Benutzer programmgesteuert aus AEM Forms zu löschen. Nachdem Sie einen Benutzer gelöscht haben, kann der Benutzer nicht mehr zum Ausführen eines Dienstvorgangs verwendet werden, für den ein Benutzer erforderlich ist. Beispielsweise können Sie einem gelöschten Benutzer keine Aufgabe zuweisen.

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um einen Benutzer zu löschen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Geben Sie den zu löschenden Benutzer an.
1. Löschen Sie den Benutzer aus AEM Forms.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, schließen Sie die Proxy-Dateien ein.

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Directory Manager-Dienst-API-Vorgang programmgesteuert ausführen können, erstellen Sie einen Directory Manager-Dienstclient.

**Benutzer zum Löschen angeben**

Sie können einen Benutzer angeben, der gelöscht werden soll, indem Sie den Kennungswert des Benutzers verwenden.

**Benutzer aus AEM Forms löschen**

Um einen Benutzer zu löschen, rufen Sie die `deleteLocalUser` -Methode des Objekts `DirectoryManagerServiceClient` auf.

**Siehe auch**

[Benutzer mithilfe der Java-API löschen](users.md#delete-users-using-the-java-api)

[Benutzer mithilfe der Webdienst-API löschen](users.md#delete-users-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Benutzer hinzufügen](users.md#adding-users)

### Löschen von Benutzern mit der Java-API {#delete-users-using-the-java-api}

Löschen Sie Benutzer mithilfe der Directory Manager Service API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie den zu löschenden Benutzer an.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Benutzer-ID-Wert fest, indem Sie die `setUserId` -Methode des Objekts `PrincipalSearchFilter` aufrufen. Übergeben Sie einen string -Wert, der den Benutzer-ID-Wert darstellt.
   * Rufen Sie die `findPrincipals` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie das `PrincipalSearchFilter` -Objekt. Diese Methode gibt eine `java.util.List`-Instanz zurück, wobei jedes Element ein `User`-Objekt ist. Iterieren Sie durch die `java.util.List`-Instanz, um den zu löschenden Benutzer zu suchen.

1. Löschen Sie den Benutzer aus AEM Forms.

   Rufen Sie die `deleteLocalUser` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie den Wert des `User` -Felds des Objekts `oid`. Rufen Sie die `getOid` -Methode des Objekts `User` auf. Verwenden Sie das `User`-Objekt, das von der `java.util.List`-Instanz abgerufen wird.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Schnellstart (EJB-Modus): Löschen von Benutzern mit der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Schnellstart (SOAP-Modus): Löschen von Benutzern mit der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-deleting-users-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Benutzer mithilfe der Webdienst-API löschen {#delete-users-using-the-web-service-api}

Löschen Sie Benutzer mithilfe der Directory Manager-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerService-Client.

   * Erstellen Sie ein `DirectoryManagerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DirectoryManagerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DirectoryManagerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen. Stellen Sie sicher, dass Sie `blob=mtom.` angeben.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DirectoryManagerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DirectoryManagerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Geben Sie den zu löschenden Benutzer an.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Benutzer-ID-Wert fest, indem Sie dem `userId` -Feld des Objekts `PrincipalSearchFilter` einen Zeichenfolgenwert zuweisen.
   * Rufen Sie die `findPrincipals` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie das `PrincipalSearchFilter` -Objekt. Diese Methode gibt ein Kollektionsobjekt `MyArrayOfUser` zurück, bei dem jedes Element ein `User`-Objekt ist. Durchsuchen Sie die `MyArrayOfUser`-Sammlung, um den Benutzer zu finden. Das `User`-Objekt, das aus dem Kollektionsobjekt `MyArrayOfUser` abgerufen wird, wird zum Löschen des Benutzers verwendet.

1. Löschen Sie den Benutzer aus AEM Forms.

   Löschen Sie den Benutzer, indem Sie den `User` -Feldwert des Objekts `oid` an die `DirectoryManagerServiceClient` -Methode des Objekts `deleteLocalUser` übergeben.

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erstellen von Gruppen {#creating-groups}

Sie können die Directory Manager-Dienst-API (Java und Webdienst) verwenden, um AEM Forms-Gruppen programmgesteuert zu erstellen. Nachdem Sie eine Gruppe erstellt haben, können Sie diese Gruppe verwenden, um einen Dienstvorgang durchzuführen, für den eine Gruppe erforderlich ist. Beispielsweise können Sie der neuen Gruppe einen Benutzer zuweisen. (Siehe [Verwalten von Benutzern und Gruppen](users.md#managing-users-and-groups).)

### Zusammenfassung der Schritte {#summary_of_steps-2}

Gehen Sie wie folgt vor, um eine Gruppe zu erstellen:

1. Projektdateien einschließen.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Stellen Sie fest, dass die Gruppe nicht vorhanden ist.
1. Erstellen Sie die Gruppe.
1. Führen Sie eine Aktion mit der Gruppe aus.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)
* jbossall-client.jar (erforderlich, wenn AEM Forms auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Verzeichnismanager-Dienstvorgang programmgesteuert ausführen können, erstellen Sie einen Directory Manager-Dienst-API-Client.

**Bestimmen, ob die Gruppe vorhanden ist**

Stellen Sie beim Erstellen einer Gruppe sicher, dass die Gruppe nicht in derselben Domäne vorhanden ist. Das heißt, zwei Gruppen können nicht denselben Namen innerhalb derselben Domäne haben. Führen Sie dazu eine Suche durch und filtern Sie die Suchergebnisse anhand von zwei Werten. Setzen Sie den Prinzipaltyp auf `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP` , um sicherzustellen, dass nur Gruppen zurückgegeben werden. Geben Sie außerdem den Domänennamen an.

**Gruppe erstellen**

Nachdem Sie festgestellt haben, dass die Gruppe nicht in der Domäne vorhanden ist, erstellen Sie die Gruppe und geben Sie die folgenden Attribute an:

* **CommonName**: Der Name der Gruppe.
* **Domäne**: Die Domäne, in der die Gruppe hinzugefügt wird.
* **Beschreibung**: Eine Beschreibung der Gruppe.

**Durchführen einer Aktion mit der Gruppe**

Nachdem Sie eine Gruppe erstellt haben, können Sie eine Aktion mit der Gruppe durchführen. Sie können beispielsweise einen Benutzer zur Gruppe hinzufügen. Um einen Benutzer zu einer Gruppe hinzuzufügen, rufen Sie den eindeutigen Kennungswert sowohl des Benutzers als auch der Gruppe ab. Übergeben Sie diese Werte an die `addPrincipalToLocalGroup`-Methode.

**Siehe auch**

[Erstellen von Gruppen mithilfe der Java-API](users.md#create-groups-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Benutzer hinzufügen](users.md#adding-users)

[Löschen von Benutzern](users.md#deleting-users)

### Erstellen von Gruppen mithilfe der Java-API {#create-groups-using-the-java-api}

Erstellen Sie eine Gruppe mithilfe der Directory Manager Service API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Bestimmen Sie, ob die Gruppe vorhanden ist.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Prinzipaltyp fest, indem Sie das `setPrincipalType` -Objekt des Objekts `PrincipalSearchFilter` aufrufen. Übergeben Sie den Wert `com.adobe.idp.um.api.infomodel.Principal.PRINCIPALTYPE_GROUP`.
   * Legen Sie die Domäne fest, indem Sie das `setSpecificDomainName`-Objekt des `PrincipalSearchFilter`-Objekts aufrufen. Übergeben Sie einen string -Wert, der den Domänennamen angibt.
   * Um eine Gruppe zu finden, rufen Sie die `findPrincipals` -Methode des `DirectoryManagerServiceClient` -Objekts auf (ein Prinzipal kann eine Gruppe sein). Übergeben Sie das `PrincipalSearchFilter` -Objekt, das den Prinzipal-Typ und den Domänennamen angibt. Diese Methode gibt eine `java.util.List`-Instanz zurück, bei der jedes Element eine `Group`-Instanz ist. Jede Gruppeninstanz entspricht dem Filter, der mithilfe des Objekts `PrincipalSearchFilter` angegeben wird.
   * Iterate through the `java.util.List` instance. Rufen Sie für jedes Element den Gruppennamen ab. Stellen Sie sicher, dass der Gruppenname nicht mit dem neuen Gruppennamen übereinstimmt.

1. Erstellen Sie die Gruppe.

   * Wenn die Gruppe nicht vorhanden ist, rufen Sie die `setCommonName` -Methode des Objekts `Group` auf und übergeben Sie einen string -Wert, der den Gruppennamen angibt.
   * Rufen Sie die `setDescription` -Methode des Objekts `Group` auf und übergeben Sie einen Zeichenfolgenwert, der die Gruppenbeschreibung angibt.
   * Rufen Sie die `setDomainName` -Methode des Objekts `Group` auf und übergeben Sie einen string -Wert, der den Domänennamen angibt.
   * Rufen Sie die `createLocalGroup` -Methode des `DirectoryManagerServiceClient` -Objekts auf und übergeben Sie die `Group` -Instanz.

   Die `createLocalUser`-Methode gibt einen Zeichenfolgenwert zurück, der den lokalen Benutzer-ID-Wert angibt.

1. Führen Sie eine Aktion mit der Gruppe aus.

   * Erstellen Sie ein Objekt `PrincipalSearchFilter`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Benutzer-ID-Wert fest, indem Sie die `setUserId` -Methode des Objekts `PrincipalSearchFilter` aufrufen. Übergeben Sie einen string -Wert, der den Benutzer-ID-Wert darstellt.
   * Rufen Sie die `findPrincipals` -Methode des Objekts `DirectoryManagerServiceClient` auf und übergeben Sie das `PrincipalSearchFilter` -Objekt. Diese Methode gibt eine `java.util.List`-Instanz zurück, wobei jedes Element ein `User`-Objekt ist. Durchsuchen Sie die `java.util.List`-Instanz, um den Benutzer zu suchen.
   * Fügen Sie der Gruppe einen Benutzer hinzu, indem Sie die `addPrincipalToLocalGroup` -Methode des Objekts `DirectoryManagerServiceClient` aufrufen. Übergeben Sie den Rückgabewert der `getOid` -Methode des `User` -Objekts. Übergeben Sie den Rückgabewert der `Group` -Methode der `getOid` -Objekte (verwenden Sie die `Group` -Instanz, die die neue Gruppe darstellt).

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Verwalten von Benutzern und Gruppen {#managing-users-and-groups}

In diesem Thema wird beschrieben, wie Sie (Java) verwenden können, um Domänen, Benutzer und Gruppen programmgesteuert zuzuweisen, zu entfernen und abzufragen.

>[!NOTE]
>
>Beim Konfigurieren einer Domäne müssen Sie die eindeutige Kennung für Gruppen und Benutzer festlegen. Das ausgewählte Attribut darf nicht nur innerhalb der LDAP-Umgebung eindeutig sein, sondern muss auch unveränderlich sein und darf sich nicht im Ordner ändern. Dieses Attribut muss auch einen einfachen String-Datentyp aufweisen (die einzige Ausnahme, die derzeit für Active Directory 2000/2003 zulässig ist, ist `"objectsid"`, was ein binärer Wert ist). Das Novell eDirectory-Attribut `"GUID"` ist beispielsweise kein einfacher String-Datentyp und funktioniert daher nicht.

* Verwenden Sie für Active Directory `"objectsid"`.
* Verwenden Sie für SunOne `"nsuniqueid"`.

>[!NOTE]
>
>Das Erstellen mehrerer lokaler Benutzer und Gruppen während einer LDAP-Ordnersynchronisierung wird nicht unterstützt. Wird dies dennoch versucht, können Fehler auftreten.

### Zusammenfassung der Schritte {#summary_of_steps-3}

Führen Sie die folgenden Schritte aus, um Benutzer und Gruppen zu verwalten:

1. Projektdateien einschließen.
1. Erstellen Sie einen DirectoryManagerService-Client.
1. Rufen Sie die entsprechenden Benutzer- oder Gruppenvorgänge auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines DirectoryManagerService-Clients**

Bevor Sie einen Verzeichnismanager-Dienstvorgang programmgesteuert ausführen können, müssen Sie einen Verzeichnismanager-Dienstclient erstellen. Mit der Java-API wird dies erreicht, indem ein `DirectoryManagerServiceClient` -Objekt erstellt wird. Mit der Webdienst-API wird dies erreicht, indem ein `DirectoryManagerServiceService` -Objekt erstellt wird.

**Aufrufen der entsprechenden Benutzer- oder Gruppenvorgänge**

Nachdem Sie den Service-Client erstellt haben, können Sie die Benutzer- oder Gruppenverwaltungsvorgänge aufrufen. Mit dem Service-Client können Sie Domänen, Benutzer und Gruppen zuweisen, entfernen und abfragen. Beachten Sie, dass es möglich ist, entweder einen Ordnerprinzipal oder einen lokalen Prinzipal zu einer lokalen Gruppe hinzuzufügen. Es ist jedoch nicht möglich, einen lokalen Prinzipal zu einer Ordnergruppe hinzuzufügen.

**Siehe auch**

[Verwalten von Benutzern und Gruppen mithilfe der Java-API](users.md#managing-users-and-groups-using-the-java-api)

[Verwalten von Benutzern und Gruppen mithilfe der Webdienst-API](users.md#managing-users-and-groups-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur User Manager-API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Verwalten von Benutzern und Gruppen mithilfe der Java-API {#managing-users-and-groups-using-the-java-api}

Führen Sie die folgenden Aufgaben aus, um Benutzer, Gruppen und Domänen programmgesteuert mit (Java) zu verwalten:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält. Weitere Informationen finden Sie unter [Festlegen von Verbindungseigenschaften ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)*.*

1. Rufen Sie die entsprechenden Benutzer- oder Gruppenvorgänge auf.

   Um einen Benutzer oder eine Gruppe zu finden, rufen Sie eine der Methoden des Objekts `DirectoryManagerServiceClient` auf, um Prinzipale zu finden (da ein Prinzipal ein Benutzer oder eine Gruppe sein kann). Im folgenden Beispiel wird die `findPrincipals`-Methode mithilfe eines Suchfilters (ein `PrincipalSearchFilter`-Objekt) aufgerufen.

   Da der Rückgabewert in diesem Fall ein `java.util.List` -Objekt mit `Principal` -Objekten ist, navigieren Sie durch das Ergebnis und wandeln die `Principal` -Objekte in entweder `User` - oder `Group` -Objekte um.

   Rufen Sie mithilfe des resultierenden `User` - oder `Group` -Objekts (das beide von der `Principal` -Schnittstelle übernehmen) die Informationen ab, die Sie in Ihren Workflows benötigen. Beispielsweise identifizieren die Werte für Domänenname und kanonische Namen gemeinsam einen Prinzipal eindeutig. Diese werden abgerufen, indem die `getDomainName`- bzw. `getCanonicalName`-Methoden des `Principal`-Objekts aufgerufen werden.

   Um einen lokalen Benutzer zu löschen, rufen Sie die Methode `deleteLocalUser` des Objekts auf und übergeben Sie die Kennung des Benutzers.`DirectoryManagerServiceClient`

   Um eine lokale Gruppe zu löschen, rufen Sie die Methode `deleteLocalGroup` des Objekts auf und übergeben Sie die Kennung der Gruppe.`DirectoryManagerServiceClient`

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verwalten von Benutzern und Gruppen mithilfe der Webdienst-API {#managing-users-and-groups-using-the-web-service-api}

Führen Sie die folgenden Aufgaben aus, um Benutzer, Gruppen und Domänen mithilfe der Directory Manager Service-API (Webdienst) programmgesteuert zu verwalten:

1. Projektdateien einschließen.

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die Directory Manager-WSDL verwendet. (Siehe [AEM Forms mit Base64-Codierung aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. (Siehe [Erstellen einer .NET-Client-Assembly, die die Base64-Kodierung](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding) verwendet.)

1. Erstellen Sie einen DirectoryManagerService-Client.

   Erstellen Sie ein `DirectoryManagerServiceService`-Objekt mithilfe des Konstruktors Ihrer Proxy-Klasse.

1. Rufen Sie die entsprechenden Benutzer- oder Gruppenvorgänge auf.

   Um einen Benutzer oder eine Gruppe zu finden, rufen Sie eine der Methoden des Objekts `DirectoryManagerServiceService` auf, um Prinzipale zu finden (da ein Prinzipal ein Benutzer oder eine Gruppe sein kann). Im folgenden Beispiel wird die `findPrincipalsWithFilter`-Methode mithilfe eines Suchfilters (ein `PrincipalSearchFilter`-Objekt) aufgerufen. Bei Verwendung eines `PrincipalSearchFilter` -Objekts werden lokale Prinzipale nur zurückgegeben, wenn die `isLocal` -Eigenschaft auf `true` gesetzt ist. Dieses Verhalten unterscheidet sich von dem mit der Java-API.

   >[!NOTE]
   >
   >Wenn die maximale Anzahl von Ergebnissen nicht im Suchfilter angegeben ist (über das Feld `PrincipalSearchFilter.resultsMax` ), werden maximal 1000 Ergebnisse zurückgegeben. Dieses Verhalten unterscheidet sich von dem, was mit der Java-API auftritt, bei der 10 Ergebnisse das standardmäßige Maximum sind. Außerdem liefern die Suchmethoden wie `findGroupMembers` nur Ergebnisse, wenn die maximale Anzahl von Ergebnissen im Suchfilter angegeben ist (z. B. über das Feld `GroupMembershipSearchFilter.resultsMax` ). Dies gilt für alle Suchfilter, die von der Klasse `GenericSearchFilter` erben. Weitere Informationen finden Sie unter [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

   Da der Rückgabewert in diesem Fall ein `object[]` mit `Principal` -Objekten ist, navigieren Sie durch das Ergebnis und wandeln die `Principal` -Objekte in die Objekte `User` oder `Group` um.

   Rufen Sie mithilfe des resultierenden `User` - oder `Group` -Objekts (das beide von der `Principal` -Schnittstelle übernehmen) die Informationen ab, die Sie in Ihren Workflows benötigen. Beispielsweise identifizieren die Werte für Domänenname und kanonische Namen gemeinsam einen Prinzipal eindeutig. Diese werden durch Aufrufen der Felder `Principal` des Objekts `domainName` bzw. `canonicalName` abgerufen.

   Um einen lokalen Benutzer zu löschen, rufen Sie die Methode `deleteLocalUser` des Objekts auf und übergeben Sie die Kennung des Benutzers.`DirectoryManagerServiceService`

   Um eine lokale Gruppe zu löschen, rufen Sie die Methode `deleteLocalGroup` des Objekts auf und übergeben Sie die Kennung der Gruppe.`DirectoryManagerServiceService`

**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Verwalten von Rollen und Berechtigungen {#managing-roles-and-permissions}

In diesem Thema wird beschrieben, wie Sie mit der Autorisierungs-Manager-Dienst-API (Java) Rollen und Berechtigungen programmgesteuert zuweisen, entfernen und bestimmen können.

In AEM Forms ist eine *role* eine Gruppe von Berechtigungen für den Zugriff auf eine oder mehrere Ressourcen auf Systemebene. Diese Berechtigungen werden über User Management erstellt und von den Dienstkomponenten erzwungen. Beispielsweise könnte ein Administrator einer Benutzergruppe die Rolle &quot;Richtliniensatzautor&quot;zuweisen. Rights Management würde es dann den Benutzern dieser Gruppe mit dieser Rolle ermöglichen, Richtliniensätze über Administration Console zu erstellen.

Es gibt zwei Arten von Rollen: *Standardrollen* und *benutzerdefinierte Rollen*. Standardrollen (*Systemrollen)* sind bereits in AEM Forms enthalten. Es wird davon ausgegangen, dass Standardrollen vom Administrator möglicherweise nicht gelöscht oder geändert werden und daher unveränderlich sind. Benutzerdefinierte Rollen, die vom Administrator erstellt wurden und diese später ändern oder löschen können, sind somit veränderbar.

Rollen erleichtern die Verwaltung von Berechtigungen. Wenn einem Prinzipal eine Rolle zugewiesen wird, wird diesem Prinzipal automatisch eine Reihe von Berechtigungen zugewiesen, und alle spezifischen Zugriffsentscheidungen für den Prinzipal basieren auf dieser Gesamtzahl zugewiesener Berechtigungen.

### Zusammenfassung der Schritte {#summary_of_steps-4}

Führen Sie die folgenden Schritte aus, um Rollen und Berechtigungen zu verwalten:

1. Projektdateien einschließen.
1. Erstellen Sie einen Client AuthorizationManagerService .
1. Rufen Sie die entsprechenden Rollen- oder Berechtigungsvorgänge auf.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Client AuthorizationManagerService**

Bevor Sie einen User Management AuthorizationManagerService-Vorgang programmgesteuert ausführen können, müssen Sie einen AuthorizationManagerService-Client erstellen. Mit der Java-API wird dies erreicht, indem ein `AuthorizationManagerServiceClient` -Objekt erstellt wird.

**Aufrufen der entsprechenden Rollen- oder Berechtigungsvorgänge**

Nachdem Sie den Service-Client erstellt haben, können Sie die Rollen- oder Berechtigungsvorgänge aufrufen. Mit dem Service Client können Sie Rollen und Berechtigungen zuweisen, entfernen und bestimmen.

**Siehe auch**

[Verwalten von Rollen und Berechtigungen mithilfe der Java-API](users.md#managing-roles-and-permissions-using-the-java-api)

[Verwalten von Rollen und Berechtigungen mithilfe der Webdienst-API](users.md#managing-roles-and-permissions-using-the-web-service-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur User Manager-API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

### Verwalten von Rollen und Berechtigungen mithilfe der Java-API {#managing-roles-and-permissions-using-the-java-api}

Führen Sie die folgenden Aufgaben aus, um Rollen und Berechtigungen mithilfe der Autorisierungs-Manager-Dienst-API (Java) zu verwalten:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen Client AuthorizationManagerService .

   Erstellen Sie ein `AuthorizationManagerServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie die entsprechenden Rollen- oder Berechtigungsvorgänge auf.

   Um einem Prinzipal eine Rolle zuzuweisen, rufen Sie die `assignRole` -Methode des Objekts `AuthorizationManagerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `java.lang.String` -Objekt, das die Rollenkennung enthält
   * Ein Array von `java.lang.String` -Objekten, die die Prinzipal-IDs enthalten.

   Um eine Rolle aus einem Prinzipal zu entfernen, rufen Sie die `unassignRole` -Methode des Objekts `AuthorizationManagerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `java.lang.String` -Objekt, das die Rollenkennung enthält.
   * Ein Array von `java.lang.String` -Objekten, die die Prinzipal-IDs enthalten.


**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[Schnellstart (SOAP-Modus): Verwalten von Rollen und Berechtigungen mithilfe der Java-API](/help/forms/developing/user-manager-java-api-quick.md#quick-start-soap-mode-managing-roles-and-permissions-using-the-java-api)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Verwalten von Rollen und Berechtigungen mithilfe der Webdienst-API {#managing-roles-and-permissions-using-the-web-service-api}

Verwalten Sie Rollen und Berechtigungen mithilfe der Autorisierungs-Manager-Dienst-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/AuthorizationManagerService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie einen Client AuthorizationManagerService .

   * Erstellen Sie ein `AuthorizationManagerServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `AuthorizationManagerServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/AuthorizationManagerService?blob=mtom`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `AuthorizationManagerServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `AuthorizationManagerServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `AuthorizationManagerServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie die entsprechenden Rollen- oder Berechtigungsvorgänge auf.

   Um einem Prinzipal eine Rolle zuzuweisen, rufen Sie die `assignRole` -Methode des Objekts `AuthorizationManagerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `string` -Objekt, das die Rollenkennung enthält
   * Ein `MyArrayOf_xsd_string` -Objekt, das die Prinzipal-IDs enthält.

   Um eine Rolle aus einem Prinzipal zu entfernen, rufen Sie die `unassignRole` -Methode des Objekts `AuthorizationManagerServiceService` auf und übergeben Sie die folgenden Werte:

   * Ein `string` -Objekt, das die Rollenkennung enthält.
   * Ein Array von `string` -Objekten, die die Prinzipal-IDs enthalten.


**Siehe auch**

[Zusammenfassung der Schritte](users.md#summary-of-steps)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

## Authentifizieren von Benutzern {#authenticating-users}

In diesem Thema wird beschrieben, wie Sie mit der Authentication Manager Service API (Java) Benutzer programmgesteuert authentifizieren können, damit Ihre Clientanwendungen Benutzer programmgesteuert authentifizieren können.

Die Benutzerauthentifizierung kann erforderlich sein, um mit einer Unternehmensdatenbank oder anderen Unternehmensrepositorys zu interagieren, die sichere Daten speichern.

Angenommen, ein Benutzer gibt einen Benutzernamen und ein Kennwort auf einer Webseite ein und sendet die Werte an einen J2EE-Anwendungsserver, der als Host für Forms dient. Ein benutzerdefiniertes Forms-Programm kann den Benutzer mit dem Authentication Manager-Dienst authentifizieren.

Bei erfolgreicher Authentifizierung greift die Anwendung auf eine gesicherte Unternehmensdatenbank zu. Andernfalls wird dem Benutzer eine Nachricht gesendet, in der er darauf hingewiesen wird, dass er kein autorisierter Benutzer ist.

Das folgende Diagramm zeigt den Logikfluss der Anwendung.

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
   <td><p>1</p></td>
   <td><p>Der Benutzer greift auf eine Website zu und gibt einen Benutzernamen und ein Kennwort an. Diese Informationen werden an einen J2EE-Anwendungsserver übermittelt, der als Host für AEM Forms dient.</p></td>
  </tr>
  <tr>
   <td><p>2</p></td>
   <td><p>Die Benutzeranmeldeinformationen werden beim Authentication Manager-Dienst authentifiziert. Wenn die Benutzeranmeldeinformationen gültig sind, fährt der Workflow mit Schritt 3 fort. Andernfalls wird dem Benutzer eine Nachricht gesendet, in der er darauf hingewiesen wird, dass er kein autorisierter Benutzer ist.</p></td>
  </tr>
  <tr>
   <td><p>1</p></td>
   <td><p>Benutzerinformationen und Formularentwürfe werden aus einer gesicherten Unternehmensdatenbank abgerufen. </p></td>
  </tr>
  <tr>
   <td><p>4</p></td>
   <td><p>Benutzerinformationen werden mit einem Formularentwurf zusammengeführt und das Formular wird für den Benutzer wiedergegeben. </p></td>
  </tr>
 </tbody>
</table>

### Zusammenfassung der Schritte {#summary_of_steps-5}

Um einen Benutzer programmatisch zu authentifizieren, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie einen AuthenticationManagerService-Client.
1. Rufen Sie den Authentifizierungsvorgang auf.
1. Rufen Sie bei Bedarf den Kontext ab, damit die Client-Anwendung ihn zur Authentifizierung an einen anderen AEM Forms-Dienst weiterleiten kann.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines AuthenticationManagerService-Clients**

Bevor Sie einen Benutzer programmgesteuert authentifizieren können, müssen Sie einen AuthenticationManagerService-Client erstellen. Erstellen Sie bei Verwendung der Java-API ein `AuthenticationManagerServiceClient`-Objekt.

**Aufrufen des Authentifizierungsvorgangs**

Nachdem Sie den Service-Client erstellt haben, können Sie den Authentifizierungsvorgang aufrufen. Für diesen Vorgang sind Informationen zum Benutzer erforderlich, z. B. der Name und das Kennwort des Benutzers. Wenn sich der Benutzer nicht authentifiziert, wird eine Ausnahme ausgelöst.

**Authentifizierungskontext abrufen**

Nachdem Sie den Benutzer authentifiziert haben, können Sie einen Kontext basierend auf dem authentifizierten Benutzer erstellen. Anschließend können Sie den Inhalt verwenden, um andere AEM Forms-Dienste aufzurufen. Beispielsweise können Sie den Kontext verwenden, um ein `EncryptionServiceClient` zu erstellen und ein PDF-Dokument mit einem Kennwort zu verschlüsseln. Stellen Sie sicher, dass der authentifizierte Benutzer über die Rolle `Services User` verfügt, die zum Aufrufen eines AEM Forms-Dienstes erforderlich ist.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur User Manager-API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Authentifizieren eines Benutzers mit der Java-API {#authenticate-a-user-using-the-java-api}

Authentifizieren Sie einen Benutzer mit der Authentication Manager Service API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen AuthenticationManagerServices-Client.

   Erstellen Sie ein `AuthenticationManagerServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Rufen Sie den Authentifizierungsvorgang auf.

   Rufen Sie die `authenticate` -Methode des Objekts `AuthenticationManagerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `java.lang.String` -Objekt, das den Namen des Benutzers enthält.
   * Ein Byte-Array (ein `byte[]`-Objekt), das das Kennwort des Benutzers enthält. Sie können das `byte[]`-Objekt abrufen, indem Sie die `getBytes` -Methode des Objekts `java.lang.String` aufrufen.

   Die Authentifizierungsmethode gibt ein `AuthResult` -Objekt zurück, das Informationen zum authentifizierten Benutzer enthält.

1. Rufen Sie den Authentifizierungskontext ab.

   Rufen Sie die `getContext` -Methode des Objekts `ServiceClientFactory` auf, die ein `Context` -Objekt zurückgibt.

   Rufen Sie dann die `initPrincipal`-Methode des Objekts `Context` auf und übergeben Sie die `AuthResult`-Methode.

### Authentifizieren eines Benutzers mithilfe der Webdienst-API {#authenticate-a-user-using-the-web-service-api}

Authentifizieren Sie einen Benutzer mit der Authentication Manager Service API (Webdienst):

1. Projektdateien einschließen.

   * Erstellen Sie eine Microsoft .NET-Client-Assembly, die die WSDL von Authentication Manager verwendet. (Siehe [AEM Forms mit Base64-Codierung aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)
   * Verweisen Sie auf die Microsoft .NET-Clientassembly. (Siehe &quot;Referenzieren der .NET-Clientassembly&quot;in [Aufrufen von AEM Forms mit Base64-Codierung](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding).)

1. Erstellen Sie einen AuthenticationManagerService-Client.

   Erstellen Sie ein `AuthenticationManagerServiceService`-Objekt mithilfe des Konstruktors Ihrer Proxy-Klasse.

1. Rufen Sie den Authentifizierungsvorgang auf.

   Rufen Sie die `authenticate` -Methode des Objekts `AuthenticationManagerServiceClient` auf und übergeben Sie die folgenden Werte:

   * Ein `string` -Objekt, das den Namen des Benutzers enthält
   * Ein Byte-Array (ein `byte[]`-Objekt), das das Kennwort des Benutzers enthält. Sie können das `byte[]`-Objekt abrufen, indem Sie ein `string`-Objekt, das das Kennwort enthält, in ein `byte[]`-Array konvertieren, indem Sie die im folgenden Beispiel dargestellte Logik verwenden.
   * Der zurückgegebene Wert ist ein `AuthResult` -Objekt, mit dem Informationen zum Benutzer abgerufen werden können. Im folgenden Beispiel werden die Informationen des Benutzers abgerufen, indem zunächst das `AuthResult` -Feld des Objekts `authenticatedUser` abgerufen und anschließend die `User` -Felder des Objekts `canonicalName` und `domainName` abgerufen werden.

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Programmgesteuerte Synchronisation von Benutzern {#programmatically-synchronizing-users}

Sie können Benutzer mithilfe der User Management-API programmgesteuert synchronisieren. Wenn Sie Benutzer synchronisieren, aktualisieren Sie AEM Forms mit Benutzerdaten, die sich in Ihrem Benutzerrepository befinden. Angenommen, Sie fügen Ihrem Benutzer-Repository neue Benutzer hinzu. Nachdem Sie einen Synchronisierungsvorgang durchgeführt haben, werden die neuen Benutzer zu AEM Formularbenutzern. Außerdem werden Benutzer, die sich nicht mehr in Ihrem Benutzerregister befinden, aus AEM Forms entfernt.

Das folgende Diagramm zeigt die Synchronisierung von AEM Forms mit einem Benutzerreaktor.

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
   <td><p>Eine Client-Anwendung fordert von AEM Forms einen Synchronisierungsvorgang an.</p></td>
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
   <td><p>Ein Benutzer kann die aktualisierten Benutzerinformationen anzeigen. </p></td>
  </tr>
 </tbody>
</table>

### Zusammenfassung der Schritte {#summary_of_steps-6}

Führen Sie die folgenden Schritte aus, um Benutzer programmatisch zu synchronisieren:

1. Projektdateien einschließen.
1. Erstellen Sie einen UserManagerUtilServiceClient-Client.
1. Geben Sie die Unternehmensdomäne an.
1. Rufen Sie den Authentifizierungsvorgang auf.
1. Prüfen Sie, ob der Synchronisierungsvorgang abgeschlossen ist.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines UserManagerUtilServiceClient**

Bevor Sie Benutzer programmgesteuert synchronisieren können, müssen Sie ein `UserManagerUtilServiceClient` -Objekt erstellen.

**Unternehmensdomäne angeben**

Bevor Sie mithilfe der User Management-API einen Synchronisierungsvorgang durchführen, geben Sie die Unternehmensdomäne an, zu der die Benutzer gehören. Sie können eine oder mehrere Unternehmensdomänen angeben. Bevor Sie einen Synchronisierungsvorgang programmgesteuert durchführen können, müssen Sie eine Unternehmensdomäne mithilfe von Administration Console einrichten. (Siehe [Administration-Hilfe](https://www.adobe.com/go/learn_aemforms_admin_63).)

**Synchronisierungsvorgang aufrufen**

Nachdem Sie eine oder mehrere Unternehmensdomänen angegeben haben, können Sie den Synchronisierungsvorgang durchführen. Die für die Durchführung dieses Vorgangs benötigte Zeit hängt von der Anzahl der Benutzerdatensätze ab, die sich im Benutzer-Repository befinden.

**Prüfen Sie, ob der Synchronisierungsvorgang abgeschlossen ist.**

Nachdem Sie einen Synchronisierungsvorgang programmgesteuert durchgeführt haben, können Sie feststellen, ob der Vorgang abgeschlossen ist.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Schnellstarts zur User Manager-API](/help/forms/developing/user-manager-java-api-quick.md#user-manager-java-api-quick-start-soap)

[Verschlüsseln von PDF-Dokumenten mit einem Kennwort](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Programmgesteuerte Synchronisation von Benutzern mit der Java-API {#programmatically-synchronizing-users-using-the-java-api}

Synchronisieren Sie Benutzer mithilfe der User Management API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-usermanager-client.jar und adobe-usermanager-util-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie einen UserManagerUtilServiceClient-Client.

   Erstellen Sie ein `UserManagerUtilServiceClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie die Unternehmensdomäne an.

   * Rufen Sie die `scheduleSynchronization` -Methode des Objekts `UserManagerUtilServiceClient` auf, um den Benutzersynchronisierungsvorgang zu starten.
   * Erstellen Sie eine `java.util.Set`-Instanz mithilfe eines `HashSet`-Konstruktors. Stellen Sie sicher, dass Sie `String` als Datentyp angeben. Diese `Java.util.Set`-Instanz speichert die Domänennamen, für die der Synchronisierungsvorgang gilt.
   * Rufen Sie für jeden hinzuzufügenden Domänennamen die Methode add des Objekts `java.util.Set` auf und übergeben Sie den Domänennamen.

1. Rufen Sie den Synchronisierungsvorgang auf.

   Rufen Sie die `getContext` -Methode des Objekts `ServiceClientFactory` auf, die ein `Context` -Objekt zurückgibt.

   Rufen Sie dann die `initPrincipal`-Methode des Objekts `Context` auf und übergeben Sie die `AuthResult`-Methode.

**Siehe auch**

[Programmgesteuerte Synchronisierung von Benutzern](users.md#programmatically-synchronizing-users)

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
