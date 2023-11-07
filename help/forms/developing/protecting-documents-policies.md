---
title: Schützen von Dokumenten durch Richtlinien
description: Verwenden Sie den Document Security-Service, um Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten. Der Document Security-Service ermöglicht es den Benutzern außerdem, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: ff42579e-6aaf-433d-8b5d-9e9dd0957250
source-git-commit: fc2f26a69c208947c14e8c6036825bb217901481
workflow-type: tm+mt
source-wordcount: '15468'
ht-degree: 82%

---

# Schützen von Dokumenten durch Richtlinien {#protecting-documents-with-policies}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

**Informationen zum Document Security-Service**

Der Document Security-Service ermöglicht es Benutzern, Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten, unabhängig davon, wie weit sie verteilt werden.

Der Document Security-Dienst verhindert, dass Informationen über die Reichweite des Benutzers hinaus verbreitet werden, indem er es Benutzern ermöglicht, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden. Benutzer können angeben, wer ein Dokument öffnen kann, einschränken, wie es verwendet werden kann, und das Dokument nach seiner Verteilung überwachen. Benutzer können auch den Zugriff auf ein richtliniengeschütztes Dokument dynamisch steuern und sogar den Zugriff auf das Dokument dynamisch sperren.

Der Document Security-Service schützt auch andere Dateitypen wie Microsoft Word-Dateien (DOC-Dateien). Sie können die Document Security Client-API verwenden, um mit diesen Dateitypen zu arbeiten. Die folgenden Versionen werden unterstützt:

* Microsoft Office 2003-Dateien (DOC-, XLS-, PPT-Dateien)
* Microsoft Office 2007-Dateien (DOCX-, XLSX-, PPTX-Dateien)
* PTC Pro/E-Dateien

In den beiden folgenden Abschnitten wird die Arbeit mit Word-Dokumenten erläutert:

* [Anwenden von Richtlinien auf Word-Dokumente](protecting-documents-policies.md#applying-policies-to-word-documents)
* [Entfernen von Richtlinien aus Word-Dokumenten](protecting-documents-policies.md#removing-policies-from-word-documents)

Sie können diese Aufgaben mithilfe des Document Security-Services ausführen:

* Erstellen von Richtlinien. Weitere Informationen finden Sie unter [Erstellen von Richtlinien](protecting-documents-policies.md#creating-policies).
* Richtlinien ändern. Weitere Informationen finden Sie unter [Ändern von Richtlinien](protecting-documents-policies.md#modifying-policies).
* Richtlinien löschen. Weitere Informationen finden Sie unter [Löschen von Richtlinien](protecting-documents-policies.md#deleting-policies).
* Richtlinien auf Dokumente anwenden. Weitere Informationen finden Sie unter [Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents).
* Richtlinien aus PDF-Dokumenten entfernen. Weitere Informationen finden Sie unter [Entfernen von Richtlinien aus PDF-Dokumenten](protecting-documents-policies.md#removing-policies-from-pdf-documents).
* Richtliniengeschützte Dokumente prüfen. Weitere Informationen finden Sie unter [Überprüfen von richtliniengeschützten PDF-Dokumenten](protecting-documents-policies.md#inspecting-policy-protected-pdf-documents).
* Den Zugriff auf PDF-Dokumente sperren. Weitere Informationen finden Sie unter [Sperren des Zugriff auf Dokumente](protecting-documents-policies.md#revoking-access-to-documents).
* Erneut Zugriff auf gesperrte Dokumente gewähren. Weitere Informationen finden Sie unter [Wiederherstellen des Zugriffs auf gesperrte Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents).
* Wasserzeichen erstellen. Weitere Informationen finden Sie unter [Erstellen von Wasserzeichen](protecting-documents-policies.md#creating-watermarks).
* Nach Ereignissen suchen. Weitere Informationen finden Sie unter [Suchen nach Ereignissen](protecting-documents-policies.md#searching-for-events).

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen von Richtlinien {#creating-policies}

Sie können Richtlinien programmgesteuert mit der Document Security Java-API oder der Web Service-API erstellen. Eine *Richtlinie* ist eine Sammlung von Informationen, die Dokumentensicherheitseinstellungen, autorisierte Benutzer und Verwendungsrechte umfasst. Sie können eine beliebige Anzahl von Richtlinien erstellen und speichern, wobei Sie Sicherheitseinstellungen verwenden, die für unterschiedliche Situationen und Benutzer geeignet sind.

Richtlinien ermöglichen Ihnen die Durchführung folgender Aufgaben:

* Geben Sie die Personen an, die das Dokument öffnen können. Die Empfänger können entweder zu Ihrer Organisation gehören oder externe Personen sein.
* Geben Sie an, wie Empfänger das Dokument verwenden können. Sie können den Zugriff auf verschiedene Acrobat- und Adobe Reader-Funktionen einschränken. Zu diesen Funktionen gehört die Möglichkeit, Text zu drucken und zu kopieren, das Hinzufügen von Signaturen und das Hinzufügen von Kommentaren zu einem Dokument.
* Sie können die Zugriffs- und Sicherheitseinstellungen jederzeit ändern, auch nachdem Sie das richtliniengeschützte Dokument verteilt haben.
* Überwachen Sie die Verwendung des Dokuments nach seiner Verteilung. Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können beispielsweise feststellen, wann ein Benutzer das Dokument geöffnet hat.

### Erstellen einer Richtlinie mithilfe von Web-Services {#creating-a-policy-using-web-services}

Wenn Sie eine Richtlinie mithilfe der Webservice-API erstellen, verweisen Sie auf eine bestehende XML-Datei für Portable Document Rights Language (PDRL), die die Richtlinie beschreibt. Richtlinienberechtigungen und der Prinzipal werden im PDRL-Dokument definiert. Das folgende XML-Dokument ist ein Beispiel für ein PDRL-Dokument.

```xml
 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <Policy PolicyInstanceVersion="1" PolicyID="5DA3F847-DE76-F9CC-63EA-49A8D59154DE" PolicyCreationTime="2004-08-30T00:02:28.294+00:00" PolicyType="1" PolicySchemaVersion="1.0" PolicyName="SDK Test Policy -4344050357301573237" PolicyDescription="An SDK Test policy" xmlns="https://www.adobe.com/schema/1.0/pdrl">
       <PolicyEntry>
          <ns1:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns1="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns2:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns2="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns3:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns3="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns4:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns4="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
          <Principal PrincipalNameType="SYSTEM">
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain>
 
             <PrincipalName>all_internal_users</PrincipalName>
          </Principal>
       </PolicyEntry>
       <PolicyEntry>
          <ns5:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns5="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns6:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns6="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns7:Permission PermissionName="com.adobe.aps.pdf.copy" Access="ALLOW" xmlns:ns7="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns8:Permission PermissionName="com.adobe.aps.pdf.printLow" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns8="https://www.adobe.com/schema/1.0/pdrl" />
 
          <ns9:Permission PermissionName="com.adobe.aps.policySwitch" Access="ALLOW" xmlns:ns9="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns10:Permission PermissionName="com.adobe.aps.revoke" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns10="https://www.adobe.com/schema/1.0/pdrl" />
 
          <ns11:Permission PermissionName="com.adobe.aps.pdf.edit" Access="ALLOW" xmlns:ns11="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns12:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns12="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns13:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns13="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns14:Permission PermissionName="com.adobe.aps.pdf.printHigh" Access="ALLOW" xmlns:ns14="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <Principal PrincipalNameType="SYSTEM">
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain>
 
             <PrincipalName>publisher</PrincipalName>
          </Principal>
       </PolicyEntry>
 
       <OfflineLeasePeriod>
          <Duration>P31D</Duration>
       </OfflineLeasePeriod>
 
       <AuditSettings isTracked="true" />
 
       <PolicyValidityPeriod isAbsoluteTime="false">
          <ValidityPeriodRelative>
             <NotBeforeRelative>PT0S</NotBeforeRelative>
 
             <NotAfterRelative>P20D</NotAfterRelative>
          </ValidityPeriodRelative>
       </PolicyValidityPeriod>
 </Policy>
 
```

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um eine Richtlinie zu erstellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Legen Sie die Attribute der Richtlinie fest.
1. Erstellen Sie einen Richtlinieneintrag.
1. Registrieren Sie die Richtlinie.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

Die folgenden JAR-Dateien müssen zum Klassenpfad Ihres Projekts hinzugefügt werden:

* adobe-rightsmanagement-client.jar
* namespace.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-api.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-impl.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-libs.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* jaxb-xjc.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* relaxngDatatype.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* xsdlib.jar (wenn AEM Forms auf JBoss bereitgestellt wird)
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar
* jbossall-client.jar (verwenden Sie eine andere JAR-Datei, wenn AEM Forms nicht auf JBoss bereitgestellt wird)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einbeziehen von AEM Forms-Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security Service-Vorgang programmgesteuert durchführen können, erstellen Sie ein Document Security Service-Client-Objekt.

**Festlegen der Richtlinienattribute**

Legen Sie zum Erstellen einer Richtlinie Richtlinienattribute fest. Ein obligatorisches Attribut ist der Richtlinienname. Richtliniennamen müssen für jeden Richtliniensatz eindeutig sein. Ein Richtliniensatz ist lediglich eine Sammlung von Richtlinien. Es kann zwei Richtlinien mit demselben Namen geben, wenn die Richtlinien zu separaten Richtliniensätzen gehören. Zwei Richtlinien in einem einzigen Richtliniensatz dürfen jedoch nicht denselben Richtliniennamen haben.

Ein weiteres nützliches Attribut, das festgelegt werden kann, ist der Gültigkeitszeitraum. Ein Gültigkeitszeitraum ist der Zeitraum, in dem autorisierte Empfänger auf ein richtliniengeschütztes Dokument zugreifen können. Wenn Sie dieses Attribut nicht festlegen, ist die Richtlinie immer gültig.

Für einen Gültigkeitszeitraum kann eine der folgenden Optionen festgelegt werden:

* Eine bestimmte Anzahl von Tagen, an denen das Dokument ab der Veröffentlichung des Dokuments verfügbar ist
* Ein Enddatum, nach dem das Dokument nicht mehr verfügbar ist
* Ein bestimmter Datumsbereich, für den auf das Dokument zugegriffen werden kann
* Immer gültig

Sie können einfach nur ein Startdatum angeben, was dazu führt, dass die Richtlinie nach dem Startdatum gültig ist. Wenn Sie nur ein Enddatum angeben, ist die Richtlinie bis zum Enddatum gültig. Es wird jedoch eine Ausnahme ausgelöst, wenn weder ein Start- noch ein Enddatum definiert sind.

Beim Festlegen von Attributen, die zu einer Richtlinie gehören, können Sie auch Verschlüsselungseinstellungen festlegen. Diese Verschlüsselungseinstellungen werden wirksam, wenn die Richtlinie auf ein Dokument angewendet wird. Sie können die folgenden Verschlüsselungswerte festlegen:

* **AES256**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 256-Bit-Schlüssel dar.
* **AES128**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 128-Bit-Schlüssel dar.
* **NoEncryption:** Stellt keine Verschlüsselung dar.

Wenn Sie die Option `NoEncryption` angeben, können Sie die Option `PlaintextMetadata` nicht auf `false` festlegen. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie unter Beschreibung der `Policy`-Benutzeroberfläche in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Einen Richtlinieneintrag erstellen**

Ein Richtlinieneintrag fügt Prinzipale, d. h. Gruppen und Benutzer, sowie Berechtigungen einer Richtlinie hinzu. Eine Richtlinie muss mindestens einen Richtlinieneintrag enthalten. Nehmen Sie beispielsweise an, dass Sie die folgenden Aufgaben ausführen:

* Erstellen und registrieren Sie einen Richtlinieneintrag, der es einer Gruppe ermöglicht, ein Dokument nur im Online-Modus anzuzeigen, und Empfängern das Kopieren untersagt.
* Fügen Sie den Richtlinieneintrag der Richtlinie hinzu.
* Sichern Sie mithilfe von Acrobat ein Dokument mit der Richtlinie.

Diese Aktionen haben zur Folge, dass die Empfänger das Dokument nur online einsehen und nicht kopieren können. Das Dokument bleibt sicher, bis die Sicherheit entfernt wurde.

**Richtlinie registrieren**

Eine neue Richtlinie muss registriert werden, bevor sie verwendet werden kann. Nachdem Sie eine Richtlinie registriert haben, können Sie sie zum Schutz von Dokumenten verwenden.

### Erstellen einer Richtlinie mit der Java-API {#create-a-policy-using-the-java-api}

Erstellen Sie eine Richtlinie mithilfe der Document Security-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie eine `Policy` -Objekt durch Aufrufen der `InfomodelObjectFactory` Statisches Objekt `createPolicy` -Methode. Diese Methode gibt ein `Policy`-Objekt zurück.
   * Legen Sie das Namensattribut der Richtlinie fest, indem Sie die `Policy` -Objekt `setName` -Methode verwenden und einen string -Wert übergeben, der den Richtliniennamen angibt.
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie die `Policy` -Objekt `setDescription` -Methode verwenden und einen string -Wert übergeben, der die Beschreibung der Richtlinie angibt.
   * Geben Sie den Richtliniensatz an, zu dem die neue Richtlinie gehört, indem Sie die `Policy` -Objekt `setPolicySetName` -Methode verwenden und einen string -Wert übergeben, der den Namen des Richtliniensatzes angibt. (Sie können für diesen Parameter den Wert `null` angeben, der dazu führt, dass die Richtlinie dem Richtliniensatz *Meine Richtlinien* hinzugefügt wird.)
   * Erstellen Sie den Gültigkeitszeitraum der Richtlinie durch Aufrufen der `InfomodelObjectFactory` Statisches Objekt `createValidityPeriod` -Methode. Diese Methode gibt ein `ValidityPeriod`-Objekt zurück.
   * Legen Sie die Anzahl der Tage fest, für die ein richtliniengeschütztes Dokument zugänglich ist, indem Sie die `ValidityPeriod` -Objekt `setRelativeExpirationDays` -Methode verwenden und einen ganzzahligen Wert übergeben, der die Anzahl der Tage angibt.
   * Legen Sie den Gültigkeitszeitraum der Richtlinie fest, indem Sie die `Policy` -Objekt `setValidityPeriod` -Methode und Übergabe der `ValidityPeriod` -Objekt.

1. Erstellen Sie einen Richtlinieneintrag.

   * Erstellen Sie einen Richtlinieneintrag durch Aufrufen der `InfomodelObjectFactory` Statisches Objekt `createPolicyEntry` -Methode. Diese Methode gibt ein `PolicyEntry`-Objekt zurück.
   * Geben Sie die Berechtigungen der Richtlinie an, indem Sie die `InfomodelObjectFactory` Statisches Objekt `createPermission` -Methode. Übergeben Sie ein statisches Datenelement, das zur `Permission`-Schnittstelle gehört, die die Berechtigung darstellt. Diese Methode gibt ein `Permission`-Objekt zurück. Um beispielsweise die Berechtigung hinzuzufügen, die es Benutzern ermöglicht, Daten aus einem richtliniengeschützten PDF-Dokument zu kopieren, übergeben Sie `Permission.COPY`. (Wiederholen Sie diesen Schritt für jede hinzuzufügende Berechtigung.)
   * Hinzufügen der Berechtigung zum Richtlinieneintrag durch Aufrufen der `PolicyEntry` -Objekt `addPermission` -Methode und Übergabe der `Permission` -Objekt. (Wiederholen Sie diesen Schritt für jedes `Permission`-Objekt, das Sie erstellt haben.)
   * Erstellen Sie den Richtlinienprinzipal durch Aufrufen der `InfomodelObjectFactory` Statisches Objekt `createSpecialPrincipal` -Methode. Übergeben Sie ein Datenelement, das zu dem `InfomodelObjectFactory`-Objekt, das den Prinzipal darstellt, gehört. Diese Methode gibt ein `Principal`-Objekt zurück. Um beispielsweise den Herausgeber des Dokuments als Prinzipal hinzuzufügen, übergeben Sie `InfomodelObjectFactory.PUBLISHER_PRINCIPAL`.
   * Fügen Sie den Prinzipal zum Richtlinieneintrag hinzu, indem Sie die `PolicyEntry` -Objekt `setPrincipal`-Methode und Übergabe der `Principal` -Objekt.
   * Fügen Sie den Richtlinieneintrag zur Richtlinie hinzu, indem Sie die `Policy` -Objekt `addPolicyEntry` -Methode und Übergabe der `PolicyEntry` -Objekt.

1. Registrieren Sie die Richtlinie.

   * Erstellen Sie eine `PolicyManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getPolicyManager` -Methode.
   * Registrieren Sie die Richtlinie, indem Sie die `PolicyManager` -Objekt `registerPolicy` -Methode verwenden und die folgenden Werte übergeben:

      * Das `Policy`-Objekt, das die zu registrierende Richtlinie darstellt.

   * Einen Zeichenfolgenwert für den Richtliniensatz, zu dem die Richtlinie gehört.

   Wenn Sie in den Verbindungseinstellungen ein AEM Forms-Administratorkonto verwenden, erstellen Sie die `DocumentSecurityClient` -Objekt ein und geben Sie dann den Namen des Richtliniensatzes an, wenn Sie die `registerPolicy` -Methode. Wenn Sie einen Wert `null` für den Richtliniensatz übergeben, wird die Richtlinie im Richtliniensatz *Meine Richtlinien* des Administrators erstellt.

   Wenn Sie einen Document Security-Benutzer in den Verbindungseinstellungen verwenden, können Sie die überladene Methode `registerPolicy` aufrufen, die nur die Richtlinie akzeptiert. Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch zu dem Richtliniensatz mit dem Namen *Meine Richtlinien* hinzugefügt. Wenn Sie die neue Richtlinie nicht zu diesem Richtliniensatz hinzufügen möchten, geben Sie beim Aufrufen der Methode `registerPolicy` einen Richtliniensatznamen an.

   >[!NOTE]
   >
   >Referenzieren Sie beim Erstellen einer Richtlinie einen bestehenden Richtliniensatz. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Code-Beispiele, die den Document Security-Service verwenden, finden Sie unter folgenden Themen:

* „Schnellstartanleitung (SOAP-Modus): Erstellen einer Richtlinie mithilfe der Java-API“

### Erstellen einer Richtlinie mithilfe der Webservice-API {#create-a-policy-using-the-web-service-api}

So erstellen Sie eine Richtlinie mithilfe der Document Security-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `RightsManagementServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie ein Objekt `PolicySpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Namen der Richtlinie fest, indem Sie dem `PolicySpec` -Objekt `name` Datenelement.
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie dem `PolicySpec` -Objekt `description` Datenelement.
   * Geben Sie den Richtliniensatz an, zu dem die Richtlinie gehört, indem Sie dem `PolicySpec` -Objekt `policySetName` Datenelement. Geben Sie einen vorhandenen Richtliniensatznamen an. (Sie können für diesen Parameterwert `null` angeben, was dazu führt, dass die Richtlinie zu *Meine Richtlinien* hinzugefügt wird).
   * Legen Sie die Offline-Nutzungsdauer der Richtlinie fest, indem Sie dem `PolicySpec` -Objekt `offlineLeasePeriod` Datenelement.
   * Legen Sie die `PolicySpec` -Objekt `policyXml` -Datenelement mit einem string -Wert, der PDRL-XML-Daten darstellt. Um diese Aufgabe durchzuführen, erstellen Sie ein .NET `StreamReader`-Objekt mithilfe seines Konstruktors. Übergeben Sie den Speicherort einer PDRL-XML-Datei, die die Richtlinie darstellt, an den `StreamReader`-Konstruktor. Rufen Sie als Nächstes die `StreamReader` -Objekt `ReadLine` -Methode und weisen Sie den Rückgabewert einer Zeichenfolgenvariablen zu. Iterieren Sie durch das `StreamReader`-Objekt, bis die Methode `ReadLine` null zurückgibt. Weisen Sie die Zeichenfolgenvariable dem `PolicySpec` -Objekt `policyXml` Datenelement.

1. Erstellen Sie einen Richtlinieneintrag.

   Es ist beim Erstellen einer Richtlinie mithilfe der Document Security-Webservice-API nicht erforderlich, einen Richtlinieneintrag zu erstellen. Der Richtlinieneintrag wird im PDRL-Dokument definiert.

1. Registrieren Sie die Richtlinie.

   Registrieren Sie die Richtlinie, indem Sie die `DocumentSecurityServiceClient` -Objekt `registerPolicy` -Methode verwenden und die folgenden Werte übergeben:

   * Das `PolicySpec`-Objekt, das die zu registrierende Richtlinie darstellt.
   * Ein Zeichenfolgenwert, der den Richtliniensatz darstellt, zu dem die Richtlinie gehört. Sie können einen Wert `null` angeben, was dazu führt, dass die Richtlinie zum Richtliniensatz *Meine Richtlinien* hinzugefügt wird.

   Wenn Sie in den Verbindungseinstellungen ein AEM Forms-Administratorkonto verwenden, erstellen Sie die `DocumentSecurityClient` -Objekt, geben Sie den Richtliniensatznamen an, wenn Sie die `registerPolicy` -Methode.

   Wenn Sie in den Verbindungseinstellungen einen Document Security-Benutzer verwenden, können Sie die überladene `registerPolicy`-Methode aufrufen, die nur die Richtlinie akzeptiert. Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch zu dem Richtliniensatz mit dem Namen *Meine Richtlinien* hinzugefügt. Wenn Sie die neue Richtlinie nicht zu diesem Richtliniensatz hinzufügen möchten, geben Sie beim Aufrufen der Methode `registerPolicy` einen Richtliniensatznamen an.

   >[!NOTE]
   >
   >Stellen Sie beim Erstellen einer Richtlinie und beim Angeben eines Richtliniensatzes sicher, dass Sie einen bestehenden Richtliniensatz angeben. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Erstellen einer Richtlinie mithilfe der Webservice-API“
* „Schnellstartanleitung (SwaRef): Erstellen einer Richtlinie mithilfe der Webservice-API“

## Ändern von Richtlinien {#modifying-policies}

Sie können eine bestehende Richtlinie mit der Document Security-Java-API oder der Webservice-API ändern. Um Änderungen an einer bestehenden Richtlinie vorzunehmen, rufen Sie sie ab, ändern Sie sie und aktualisieren Sie dann die Richtlinie auf dem Server. Angenommen, Sie rufen z. B. eine bestehende Richtlinie ab und verlängern ihre Gültigkeitsdauer. Bevor die Änderung wirksam wird, müssen Sie die Richtlinie aktualisieren.

Sie können eine Richtlinie ändern, wenn sich die Geschäftsanforderungen ändern und die Richtlinie diese Anforderungen nicht mehr widerspiegelt. Anstatt eine Richtlinie zu erstellen, können Sie einfach eine vorhandene Richtlinie aktualisieren.

Um Richtlinienattribute mithilfe eines Webservices zu ändern (z. B. mithilfe von Java-Proxy-Klassen, die mit JAX-WS erstellt wurden), müssen Sie sicherstellen, dass die Richtlinie beim Document Security-Service registriert ist. Sie können dann mithilfe der Methode `PolicySpec.getPolicyXml` auf die bestehende Richtlinie verweisen und die Richtlinienattribute mithilfe der entsprechenden Methoden ändern. Sie können beispielsweise die Offline-Nutzungsdauer ändern, indem Sie die Methode `PolicySpec.setOfflineLeasePeriod` aufrufen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um eine bestehende Richtlinie zu ändern, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie eine bestehende Richtlinie ab.
1. Ändern Sie die Richtlinienattribute.
1. Aktualisieren Sie die Richtlinie.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Services erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient`-Objekt. Wenn Sie die Document Security-Webservice-API verwenden, erstellen Sie ein `RightsManagementServiceService`-Objekt.

**Abrufen einer bestehenden Richtlinie**

Rufen Sie eine vorhandene Richtlinie ab, um sie zu ändern. Um eine Richtlinie abzurufen, geben Sie den Richtliniennamen und den Richtliniensatz an, zu dem die Richtlinie gehört. Wenn Sie für den Richtliniensatznamen einen Wert `null` angeben, wird die Richtlinie aus dem Richtliniensatz *Meine Richtlinien* abgerufen.

**Festlegen der Richtlinienattribute**

Um eine Richtlinie zu ändern, ändern Sie den Wert von Richtlinienattributen. Das einzige Richtlinienattribut, das Sie nicht ändern können, ist das Namensattribut. Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, können Sie den Wert des Attributs für die Offline-Nutzungsdauer der Richtlinie ändern.

Wenn Sie die Offline-Nutzungsdauer einer Richtlinie mithilfe eines Webdiensts ändern, wird die Variable `offlineLeasePeriod` im Feld `PolicySpec` -Benutzeroberfläche ignoriert wird. Um die Offline-Nutzungsdauer zu aktualisieren, ändern Sie die Element `OfflineLeasePeriod` im PDRL-XML-Dokument. Verweisen Sie dann mithilfe der `PolicySpec` -Benutzeroberfläche `policyXML` Datenelement.

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie in der Beschreibung der `Policy`-Benutzeroberfläche in [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Aktualisieren der Richtlinie**

Bevor die Änderungen, die Sie an einer Richtlinie vornehmen, wirksam werden, müssen Sie die Richtlinie mit dem Document Security-Service aktualisieren. Änderungen an Richtlinien, die Dokumente schützen, werden aktualisiert, wenn das richtliniengeschützte Dokument das nächste Mal mit dem Document Security-Service synchronisiert wird.

### Ändern bestehender Richtlinien mit Hilfe der Java-API {#modify-existing-policies-using-the-java-api}

So ändern Sie eine bestehende Richtlinie mithilfe der Document Security-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie eine bestehende Richtlinie ab.

   * Erstellen Sie eine `PolicyManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getPolicyManager` -Methode.
   * Erstellen Sie eine `Policy` -Objekt, das die zu aktualisierende Richtlinie darstellt, indem das `PolicyManager` -Objekt `getPolicy` -Methode und Übergabe der folgenden Werte&quot;

      * Ein Zeichenfolgenwert, der den Namen des Richtliniensatzes darstellt, zu dem die Richtlinie gehört. Sie können `null` angeben, was dazu führt, dass der Richtliniensatz `MyPolicies` verwendet wird.
      * Ein Zeichenfolgenwert, der den Richtliniennamen darstellt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen. Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, rufen Sie die `Policy` -Objekt `setOfflineLeasePeriod` -Methode.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren der Richtlinie durch Aufrufen von `PolicyManager` -Objekt `updatePolicy` -Methode. Übergeben Sie das `Policy`-Objekt, das die zu aktualisierende Richtlinie darstellt.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie im Abschnitt „Kurzanleitung (SOAP-Modus): Ändern einer Richtlinie mithilfe der Java-API“.

### Ändern bestehender Richtlinien mit Hilfe der Webservice API {#modify-existing-policies-using-the-web-service-api}

So ändern Sie eine bestehende Richtlinie mithilfe der Document Security-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `RightsManagementServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie eine bestehende Richtlinie ab.

   Erstellen Sie eine `PolicySpec` -Objekt, das die zu ändernde Richtlinie darstellt, indem das `RightsManagementServiceClient` -Objekt `getPolicy` -Methode verwenden und die folgenden Werte übergeben:

   * Einen Zeichenfolgenwert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` angeben, was dazu führt, dass der Richtliniensatz `MyPolicies` verwendet wird.
   * Ein Zeichenfolgenwert, der den Namen der neuen Richtlinie angibt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren Sie die Richtlinie, indem Sie die `RightsManagementServiceClient` -Objekt `updatePolicyFromSDK` -Methode und Übergabe der `PolicySpec` -Objekt, das die zu aktualisierende Richtlinie darstellt.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Ändern einer Richtlinie mithilfe der Webservice-API“
* „Schnellstartanleitung (SwaRef): Ändern einer Richtlinie mithilfe der Webservice-API“

## Löschen von Richtlinien {#deleting-policies}

Sie können eine bestehende Richtlinie mithilfe der Document Security-Java-API oder der Webservice-API löschen. Nachdem eine Richtlinie gelöscht wurde, kann sie nicht mehr zum Schutz von Dokumenten verwendet werden. Vorhandene richtliniengeschützte Dokumente, die die Richtlinie verwenden, sind jedoch weiterhin geschützt. Sie können eine Richtlinie löschen, wenn eine neuere verfügbar ist.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um eine bestehende Richtlinie zu löschen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Löschen Sie die Richtlinie.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmatisch ausführen können, müssen Sie ein Client-Objekt für den Document Security-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient`-Objekt. Wenn Sie die Document Security-Webservice-API verwenden, erstellen Sie ein `RightsManagementServiceService`-Objekt.

**Löschen der Richtlinie**

Um eine Richtlinie zu löschen, geben Sie die zu löschende Richtlinie und den Richtliniensatz an, zu dem die Richtlinie gehört. Der Benutzer, dessen Einstellungen zum Aufrufen von AEM Forms verwendet werden, muss über die Berechtigung zum Löschen der Richtlinie verfügen. andernfalls tritt eine Ausnahme auf. Wenn Sie versuchen, eine nicht vorhandene Richtlinie zu löschen, tritt ebenfalls eine Ausnahme auf.

### Löschen von Richtlinien mithilfe der Java-API {#delete-policies-using-the-java-api}

So löschen Sie eine Richtlinie mithilfe der Document Security-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Löschen Sie die Richtlinie.

   * Erstellen Sie eine `PolicyManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getPolicyManager` -Methode.
   * Löschen Sie die Richtlinie, indem Sie die `PolicyManager` -Objekt `deletePolicy` -Methode verwenden und die folgenden Werte übergeben:

      * Einen Zeichenfolgenwert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` angeben, wodurch der Richtliniensatz `MyPolicies` verwendet wird.
      * Einen Zeichenfolgenwert, der den Namen der zu löschenden Richtlinie angibt.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (SOAP-Modus): Löschen einer Richtlinie mithilfe der Java-API“

### Richtlinien mithilfe der Web-Service-API löschen {#delete-policies-using-the-web-service-api}

Löschen einer Richtlinie mithilfe der Document Security-API (Web Service):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `RightsManagementServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Löschen Sie die Richtlinie.

   Löschen einer Richtlinie durch Aufrufen der `RightsManagementServiceClient` -Objekt `deletePolicy` -Methode verwenden und die folgenden Werte übergeben:

   * Einen Zeichenfolgenwert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` angeben, wodurch der Richtliniensatz `MyPolicies` verwendet wird.
   * Einen Zeichenfolgenwert, der den Namen der zu löschenden Richtlinie angibt.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Löschen einer Richtlinie mithilfe der Web-Service-API“
* „Schnellstartanleitung(SwaRef): Löschen einer Richtlinie mithilfe der Web-Service-API“

## Anwenden von Richtlinien auf PDF-Dokumente {#applying-policies-to-pdf-documents}

Sie können eine Richtlinie auf ein PDF-Dokument anwenden, um das Dokument zu schützen. Durch Anwendung einer Richtlinie auf ein PDF-Dokument können Sie den Zugriff auf das Dokument einschränken. Sie können eine Richtlinie nicht auf ein Dokument anwenden, das bereits durch eine Richtlinie geschützt ist.

Solange das Dokument geöffnet ist, können Sie auch den Zugriff auf Acrobat- und Adobe Reader-Funktionen einschränken, einschließlich der Möglichkeit, Text zu drucken und zu kopieren, Änderungen vorzunehmen und Signaturen und Kommentare zu einem Dokument hinzuzufügen. Darüber hinaus können Sie ein richtliniengeschütztes PDF-Dokument sperren, wenn Benutzer nicht mehr auf das Dokument zugreifen sollen.

Sie können die Verwendung eines richtliniengeschützten Dokuments nach dessen Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

Um eine Richtlinie auf ein PDF-Dokument anzuwenden, führen Sie folgende Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument ab, auf das eine Richtlinie angewendet wird.
1. Wenden Sie eine vorhandene Richtlinie auf das PDF-Dokument an.
1. Speichern Sie das richtliniengeschützte PDF-Dokument.

**Projektdateien einbinden**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Ein Document Security Client-API-Objekt erstellen**

Bevor Sie einen Document Security-Service-Vorgang programmgesteuert durchführen können, erstellen Sie ein Document Security-Service-Client-Objekt. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient`-Objekt. Wenn Sie die Document Security-Web-Service-API verwenden, erstellen Sie ein `DocumentSecurityServiceService`-Objekt.

**Ein PDF-Dokument abrufen**

Sie können ein PDF-Dokument abrufen, um eine Richtlinie anzuwenden. Nachdem Sie eine Richtlinie auf das PDF-Dokument angewendet haben, wird die Verwendung des Dokuments durch die Benutzer eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offline-Modus ermöglicht, müssen die Benutzer online sein, um das Dokument zu öffnen.

**Vorhandene Richtlinie auf das PDF-Dokument anwenden**

Um eine Richtlinie auf ein PDF-Dokument anzuwenden, verweisen Sie auf eine vorhandene Richtlinie und geben an, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften festlegt, muss Zugriff auf die angegebene Richtlinie haben. Andernfalls wird eine Ausnahme ausgelöst.

**PDF-Dokument speichern**

Nachdem der Document Security-Service eine Richtlinie auf ein PDF-Dokument angewendet hat, können Sie das richtliniengeschützte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Eine Richtlinie mithilfe der Java-API auf ein PDF-Dokument anwenden {#apply-a-policy-to-a-pdf-document-using-the-java-api}

Wenden Sie mithilfe der Document Security-API (Java) eine Richtlinie auf ein PDF-Dokument an:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie mithilfe seines Konstruktors ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Wenden Sie eine vorhandene Richtlinie auf das PDF-Dokument an.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getDocumentManager` -Methode.
   * Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `DocumentManager` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Einen Zeichenfolgenwert, der die Versionsnummer des Dokuments angibt.
      * Einen Zeichenfolgenwert, der den Namen des Satzes angibt, zu dem die Richtlinie gehört. Sie können einen `null`-Wert angeben, der dazu führt, dass der Richtliniensatz `MyPolicies` verwendet wird.
      * Einen Zeichenfolgenwert, der den Richtliniennamen angibt.
      * Einen Zeichenfolgenwert für den Namen die User Manager-Domain des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert null sein.)
      * Ein Zeichenfolgenwert für den kanonischen Namen des User Manager-Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null` lauten.)
      * Ein `com.adobe.livecycle.rightsmanagement.Locale`-Element, das das Gebietsschema darstellt, das für die Auswahl der MS Office-Vorlage verwendet wird. Dieser Parameterwert ist optional und wird nicht für PDF-Dokumente verwendet. Um ein PDF-Dokument zu sichern, geben Sie `null` an.

     Die `protectDocument`-Methode gibt ein `RMSecureDocumentResult`-Objekt zurück, das das richtliniengeschützte PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Rufen Sie die `RMSecureDocumentResult` -Objekt `getProtectedDoc` -Methode zum Abrufen des richtliniengeschützten PDF-Dokuments. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück.
   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung PDF lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `getProtectedDoc` -Methode).

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (EJB-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API“
* „Schnellstartanleitung (SOAP-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API“

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Web-Service-API {#apply-a-policy-to-a-pdf-document-using-the-web-service-api}

Wenden Sie mithilfe der Document Security-API (Web Service) eine Richtlinie auf ein PDF-Dokument an:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der dem Forms-Service die WSDL angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) Sie brauchen das Attribut `lc_version` nicht zu verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `RightsManagementServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Bestimmen Sie die Byte-Array-Größe, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie dessen Feld `MTOM` mit dem Inhalt des Byte-Arrays belegen.

1. Wenden Sie eine vorhandene Richtlinie auf das PDF-Dokument an.

   Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `RightsManagementServiceClient` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Einen Zeichenfolgenwert, der die Versionsnummer des Dokuments angibt.
   * Einen Zeichenfolgenwert, der den Namen des Satzes angibt, zu dem die Richtlinie gehört. Sie können einen `null`-Wert angeben, der dazu führt, dass der Richtliniensatz `MyPolicies` verwendet wird.
   * Einen Zeichenfolgenwert, der den Richtliniennamen angibt.
   * Einen Zeichenfolgenwert für den Namen die User Manager-Domain des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert `null` sein).
   * Ein Zeichenfolgenwert für den kanonischen Namen des User Manager-Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null` sein).
   * Ein `RMLocale`-Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein Zeichenfolgen-Ausgabeparameter, der zum Speichern des Richtlinienkennungswerts verwendet wird.
   * Ein Zeichenfolgen-Ausgabeparameter, der zum Speichern des Werts der richtliniengeschützten Kennung verwendet wird.
   * Ein Zeichenfolgen-Ausgabeparameter, der zum Speichern des MIME-Typs verwendet wird (z. B. `application/pdf`).

   Die Methode `protectDocument` gibt ein `BLOB`-Objekt zurück, das das richtliniengeschützte PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des richtliniengeschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `protectDocument` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webservice-API“
* „Schnellstartanleitung (SwaRef): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webservice-API“

## Entfernen von Richtlinien aus PDF-Dokumenten {#removing-policies-from-pdf-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, Sie möchten nicht mehr, dass das Dokument durch eine Richtlinie geschützt wird. Wenn Sie ein richtliniengeschütztes Dokument mit einer neueren Richtlinie aktualisieren möchten, ist es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

Um eine Richtlinie aus einem richtliniengeschützten PDF-Dokument zu entfernen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.
1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.
1. Speichern Sie das ungesicherte PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security Service-Vorgang programmgesteuert durchführen können, erstellen Sie ein Document Security Service-Client-Objekt.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Sie können ein richtliniengeschütztes PDF-Dokument abrufen, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem PDF-Dokument zu entfernen, das nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme ausgelöst.

**Entfernen der Richtlinie aus dem PDF-Dokument**

Sie können eine Richtlinie aus einem richtliniengeschützten PDF-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Andernfalls muss die zum Schützen eines Dokuments verwendete Richtlinie die `SWITCH_POLICY` Berechtigung zum Entfernen einer Richtlinie aus einem PDF-Dokument. Außerdem muss der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Ungesichertes PDF-Dokument speichern**

Nachdem der Document Security-Service eine Richtlinie aus einem PDF-Dokument entfernt hat, können Sie das ungesicherte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Eine Richtlinie mithilfe der Java-API aus einem PDF-Dokument entfernen {#remove-a-policy-from-a-pdf-document-using-the-java-api}

Entfernen Sie mithilfe der Document Security-API (Java) eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem es seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Entfernen Sie eine Richtlinie aus dem PDF-Dokument, indem Sie die `DocumentManager` -Objekt `removeSecurity` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das ungesicherte PDF-Dokument.

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung PDF lautet.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `removeSecurity` -Methode).

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (SOAP-Modus): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Java-API“

### Eine Richtlinie mithilfe der Web-Service-API entfernen {#remove-a-policy-using-the-web-service-api}

Entfernen Sie mithilfe der Document Security-API (Web-Service) eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `DocumentSecurityServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des richtliniengeschützten PDF-Dokuments verwendet, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem `MTOM`-Feld den Inhalt des Byte-Arrays zuweisen.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   Entfernen Sie die Richtlinie aus dem PDF-Dokument, indem Sie die `DocumentSecurityServiceClient` -Objekt `removePolicySecurity` -Methode und Übergabe der `BLOB` -Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `BLOB`-Objekt zurück, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das ungesicherte PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und ihm einen Zeichenfolgenwert, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt, übergeben.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des von der `removePolicySecurity`-Methode zurückgegebenen `BLOB`-Objekts enthält. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Web-Service-API“
* „Schnellstartanleitung (SwaRef): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Webservice-API“

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zugriff auf Dokumente sperren {#revoking-access-to-documents}

Sie können den Zugriff auf ein richtliniengeschütztes PDF-Dokument widerrufen, sodass alle Dokumentkopien für Benutzer unzugänglich sind. Wenn ein Benutzer versucht, ein widerrufenes PDF-Dokument zu öffnen, wird er an eine angegebene URL weitergeleitet, wo ein überarbeitetes Dokument angezeigt werden kann. Die URL, an die der Benutzer umgeleitet wird, muss programmgesteuert angegeben werden. Wenn Sie den Zugriff auf ein Dokument widerrufen, wird die Änderung wirksam, sobald der Benutzer das richtliniengeschützte Dokument das nächste Mal mit dem Document Security-Service synchronisiert, indem er es online öffnet.

Die Möglichkeit, den Zugriff auf ein Dokument zu widerrufen, bietet zusätzliche Sicherheit. Angenommen, eine neuere Version eines Dokuments ist verfügbar, und Sie möchten nicht mehr, dass jemand die veraltete Version anzeigt. In diesem Fall kann der Zugriff auf das ältere Dokument widerrufen werden und niemand kann das Dokument anzeigen, es sei denn, der Zugriff wird wieder aktiviert.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Um ein richtliniengeschütztes Dokument zu widerrufen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.
1. Widerrufen Sie das richtliniengeschützte Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmatisch ausführen können, müssen Sie ein Client-Objekt für den Document Security-Service erstellen.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Rufen Sie ein richtliniengeschütztes PDF-Dokument ab, um es zu sperren. Sie können ein Dokument, das bereits widerrufen wurde oder nicht richtliniengeschützt ist, nicht widerrufen.

Wenn Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments kennen, ist es nicht erforderlich, das richtliniengeschützte PDF-Dokument abzurufen. In den meisten Fällen müssen Sie jedoch das PDF-Dokument abrufen, um den Lizenzkennungswert zu erhalten.

**Widerrufen des richtliniengeschützten Dokuments**

Um ein richtliniengeschütztes Dokument zu widerrufen, geben Sie die Lizenzkennung des richtliniengeschützten Dokuments an. Darüber hinaus können Sie die URL einer anderen Dokumentversion angeben, die der Benutzer anzeigen kann, wenn er versucht, das widerrufene Dokument zu öffnen. Angenommen, ein veraltetes Dokument wird widerrufen. Wenn ein Benutzer versucht, das widerrufene Dokument zu öffnen, wird ihm anstelle des widerrufenen Dokuments ein aktualisiertes Dokument angezeigt.

>[!NOTE]
>
>Wenn Sie versuchen, ein bereits widerrufenes Dokument zu widerrufen, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Wiederherstellen des Zugriffs auf widerrufene Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents)

### Widerrufen des Zugriffs auf Dokumente mithilfe der Java-API {#revoke-access-to-documents-using-the-java-api}

So widerrufen Sie mithilfe der Document Security-API (Java) den Zugriff auf ein richtliniengeschütztes PDF-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security-Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Widerrufen des richtliniengeschützten Dokuments

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `DocumentManager` -Objekt `getLicenseId` -Methode. Übergeben Sie das `com.adobe.idp.Document`-Objekt, das das richtliniengeschützte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Lizenzkennung darstellt.
   * Erstellen Sie eine `LicenseManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getLicenseManager` -Methode.
   * Das richtliniengeschützte Dokument durch Aufrufen der `LicenseManager` -Objekt `revokeLicense` -Methode verwenden und die folgenden Werte übergeben:

      * Ein string -Wert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert von `DocumentManager` -Objekt `getLicenseId` -Methode).
      * Ein statisches Datenelement der `License`-Schnittstelle, die den Grund zum Widerrufen des Dokuments angibt. Sie können beispielsweise `License.DOCUMENT_REVISED` angeben.
      * Ein `java.net.URL`-Wert, der den Speicherort angibt, an dem sich ein überarbeitetes Dokument befindet. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie `null` übergeben.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (SOAP-Modus): Widerrufen eines Dokuments mithilfe der Java-API“

### Widerrufen des Zugriffs auf Dokumente mithilfe der Webservice-API {#revoke-access-to-documents-using-the-web-service-api}

So widerrufen Sie den Zugriff auf ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security-API ( Webservice):

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security-Client-API-Objekts

   * Erstellen Sie ein `DocumentSecurityServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `DocumentSecurityServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um ein richtliniengeschütztes PDF-Dokument zu speichern, das widerrufen wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu widerrufenden richtliniengeschützten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Widerrufen des richtliniengeschützten Dokuments

   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `DocumentSecurityServiceClient` -Objekt `getLicenseID` -Methode und Übergabe der `BLOB` -Objekt, das das richtliniengeschützte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Das richtliniengeschützte Dokument durch Aufrufen der `DocumentSecurityServiceClient` -Objekt `revokeLicense` -Methode verwenden und die folgenden Werte übergeben:

      * Ein string -Wert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert von `DocumentSecurityServiceService` -Objekt `getLicenseId` -Methode).
      * Ein statisches Datenelement der Aufzählung `Reason`, das den Grund für das Widerrufen des Dokuments angibt. Sie können beispielsweise `Reason.DOCUMENT_REVISED` angeben.
      * Ein `string`-Wert, der den URL-Speicherort angibt, an dem sich ein überarbeitetes Dokument befindet. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie `null` angeben.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Widerrufen eines Dokuments mithilfe der Webservice-API“
* „Schnellstartanleitung (SwaRef): Widerrufen eines Dokuments mithilfe der Webservice-API“

**Siehe auch**

[Entfernen von Richtlinien aus Word-Dokumenten](protecting-documents-policies.md#removing-policies-from-word-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wiederherstellen des Zugriffs auf widerrufene Dokumente {#reinstating-access-to-revoked-documents}

Sie können den Zugriff auf ein widerrufenes PDF-Dokument wiederherstellen, sodass alle Kopien des widerrufenen Dokuments für Benutzer zugänglich sind. Wenn ein Benutzer ein Dokument öffnet, das widerrufen worden war und wieder freigegeben wurde, kann der Benutzer das Dokument anzeigen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Führen Sie die folgenden Schritte aus, um den Zugriff auf ein widerrufenes PDF-Dokument wiederherzustellen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie die Lizenzkennung des widerrufenen PDF-Dokuments ab.
1. Reaktivieren Sie den Zugriff auf das widerrufene PDF-Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmatisch ausführen können, müssen Sie ein Client-Objekt für den Document Security-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient`-Objekt. Wenn Sie die Document Security-Webservice-API verwenden, erstellen Sie ein `DocumentSecurityServiceService`-Objekt.

**Abrufen der Lizenzkennung des widerrufenen PDF-Dokuments**

Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab, um ein gesperrtes PDF-Dokument erneut zu aktivieren. Nachdem Sie den Wert der Lizenzkennung erhalten haben, können Sie ein widerrufenes Dokument erneut zugänglich machen. Wenn Sie versuchen, ein Dokument erneut zugänglich zu machen, das nicht widerrufen wurde, wird eine Ausnahme ausgelöst.

**Wiederherstellen des Zugriffs auf das widerrufene PDF-Dokument**

Um den Zugriff auf ein widerrufenes PDF-Dokument wieder zu aktivieren, müssen Sie die Lizenzkennung des widerrufenen Dokuments angeben. Wenn Sie versuchen, den Zugriff auf ein PDF-Dokument wiederherzustellen, das nicht widerrufen wurde, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Wiederherstellen des Zugriffs auf widerrufene Dokumente mithilfe der Java-API {#reinstate-access-to-revoked-documents-using-the-java-api}

So stellen Sie den Zugriff auf ein widerrufenes Dokument mithilfe der Document Security-API (Java) wieder her:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie die Lizenzkennung des widerrufenen PDF-Dokuments ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das widerrufene PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `DocumentManager` -Objekt `getLicenseId` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das gesperrte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.

1. Reaktivieren Sie den Zugriff auf das widerrufene PDF-Dokument.

   * Erstellen Sie eine `LicenseManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getLicenseManager` -Methode.
   * Den Zugriff auf das gesperrte PDF-Dokument durch Aufrufen der `LicenseManager` -Objekt `unrevokeLicense` -Methode verwenden und den Wert der Lizenzkennung des gesperrten Dokuments übergeben.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (SOAP-Modus): Wiederherstellen des Zugriffs auf ein widerrufenes Dokument mithilfe der Webservice-API“

### Wiederherstellen des Zugriffs auf widerrufene Dokumente mithilfe der Webservice-API {#reinstate-access-to-revoked-documents-using-the-web-service-api}

So stellen Sie den Zugriff auf ein widerrufenes Dokument mithilfe der Document Security-API (Webservice) wieder her:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `DocumentSecurityServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie die Lizenzkennung des widerrufenen PDF-Dokuments ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird verwendet, um ein widerrufenes PDF-Dokument zu speichern, auf das der Zugriff wiederhergestellt wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des widerrufenen PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Reaktivieren Sie den Zugriff auf das widerrufene PDF-Dokument.

   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `DocumentSecurityServiceClient` -Objekt `getLicenseID` -Methode und Übergabe der `BLOB` -Objekt, das das gesperrte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Den Zugriff auf das gesperrte PDF-Dokument durch Aufrufen der `DocumentSecurityServiceClient` -Objekt `unrevokeLicense` -Methode verwenden und einen string -Wert übergeben, der den Lizenzkennungswert des gesperrten PDF-Dokuments angibt (geben Sie den Rückgabewert der `DocumentSecurityServiceClient` -Objekt `getLicenseId` -Methode).

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Wiederherstellen des Zugriffs auf ein widerrufenes Dokument mithilfe der Webservice-API“
* „Schnellstartanleitung (SwaRef): Wiederherstellen des Zugriffs auf ein widerrufenes Dokument mithilfe der Webservice-API“

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Überprüfen von richtliniengeschützten PDF-Dokumenten {#inspecting-policy-protected-pdf-documents}

Sie können die Document Security Service-API (Java und Webservice) verwenden, um richtliniengeschützte PDF-Dokumente zu überprüfen. Beim Überprüfen richtliniengeschützter PDF-Dokumente werden Informationen zum richtliniengeschützten PDF-Dokument zurückgegeben. Sie können beispielsweise die Richtlinie ermitteln, die zum Schützen des Dokuments verwendet wurde, sowie das Datum, an dem das Dokument geschützt wurde.

Sie können diese Aufgabe nicht ausführen, wenn Ihre LiveCycle-Version 8.x oder eine frühere Version ist. In AEM Forms wird die Überprüfung richtliniengeschützter Dokumente unterstützt. Wenn Sie versuchen, ein richtliniengeschütztes Dokument mit LiveCycle 8.x (oder früher) zu überprüfen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

Um ein richtliniengeschütztes PDF-Dokument zu überprüfen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.
1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmgesteuert durchführen können, erstellen Sie ein Document Security-Service-Client-Objekt. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient`-Objekt. Wenn Sie die Document Security-Webservice-API verwenden, erstellen Sie ein `RightsManagementServiceService`-Objekt.

**Abrufen eines richtliniengeschützten Dokuments zum Überprüfen**

Um ein richtliniengeschütztes Dokument zu überprüfen, rufen Sie es ab. Wenn Sie versuchen, ein Dokument zu überprüfen, das nicht mit einer Richtlinie gesichert ist oder das widerrufen wurde, wird eine Ausnahme ausgelöst.

**Überprüfen des Dokuments**

Nachdem Sie ein richtliniengeschütztes Dokument abgerufen haben, können Sie es überprüfen.

**Abrufen von Informationen über das richtliniengeschützte Dokument**

Nachdem Sie ein richtliniengeschütztes PDF-Dokument überprüft haben, können Sie Informationen dazu abrufen. Sie können beispielsweise die Richtlinie ermitteln, die zum Schützen des Dokuments verwendet wird.

Wenn Sie ein Dokument mit einer Richtlinie schützen, die zu „Meine Richtlinien“ gehört, und dann `RMInspectResult.getPolicysetName` oder `RMInspectResult.getPolicysetId` aufrufen, wird null zurückgegeben.

Wenn das Dokument mit einer Richtlinie gesichert wird, die in einem anderen Richtliniensatz als „Meine Richtlinien“ enthalten ist, dann geben `RMInspectResult.getPolicysetName` und `RMInspectResult.getPolicysetId` gültige Zeichenfolgen zurück.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Überprüfen von richtliniengeschützten PDF-Dokumenten mithilfe der Java-API {#inspect-policy-protected-pdf-documents-using-the-java-api}

So überprüfen Sie ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security Service-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-rightsmanagement-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Überprüfen Sie das Dokument.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getDocumentManager` -Methode.
   * Inspect das richtliniengeschützte Dokument durch Aufrufen der `LicenseManager` -Objekt `inspectDocument` -Methode. Übergeben Sie das `com.adobe.idp.Document`-Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `RMInspectResult`-Objekt zurück, das Informationen zum richtliniengeschützten Dokument enthält.

1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

   Um Informationen über das richtliniengeschützte Dokument zu erhalten, rufen Sie die entsprechende Methode auf, die zum `RMInspectResult`-Objekt gehört. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie die `RMInspectResult` -Objekt `getPolicyName` -Methode.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (SOAP-Modus): Überprüfung richtliniengeschützter PDF-Dokumente mithilfe der Java-API“

### Überprüfen von richtliniengeschützten PDF-Dokumenten mithilfe der Webservice-API {#inspect-policy-protected-pdf-documents-using-the-web-service-api}

So überprüfen Sie ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security Service-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `RightsManagementServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines zu überprüfenden PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor verwenden. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die Länge des zu lesenden Streams.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Überprüfen Sie das Dokument.

   Inspect das richtliniengeschützte Dokument durch Aufrufen der `RightsManagementServiceClient` -Objekt `inspectDocument` -Methode. Übergeben Sie das `BLOB`-Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `RMInspectResult`-Objekt zurück, das Informationen zum richtliniengeschützten Dokument enthält.

1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

   Um Informationen über das richtliniengeschützte Dokument zu erhalten, rufen Sie den Wert des entsprechenden Feldes ab, das zum `RMInspectResult`-Objekt gehört. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie den Wert der `RMInspectResult` -Objekt `policyName` -Feld.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Überprüfen von richtliniengeschützten PDF-Dokumenten mithilfe der Webservice-API“
* „Schnellstartanleitung (SwaRef): Überprüfen von richtliniengeschützten PDF-Dokumenten mithilfe der Webservice-API“

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erstellen von Wasserzeichen {#creating-watermarks}

Wasserzeichen tragen dazu bei, die Sicherheit eines Dokuments zu gewährleisten, indem sie das Dokument eindeutig identifizieren und die Verletzung des Urheberrechts kontrollieren. Sie können beispielsweise ein Wasserzeichen mit dem Wort „Vertraulich“ erstellen und auf jeder Seite eines Dokuments platzieren. Nachdem ein Wasserzeichen erstellt wurde, können Sie es als Teil einer Richtlinie einbeziehen. Das heißt, Sie können das Wasserzeichenattribut der Richtlinie mit dem neu erstellten Wasserzeichen festlegen. Nachdem eine Richtlinie, die ein Wasserzeichen enthält, auf ein Dokument angewendet wurde, wird das Wasserzeichen im richtliniengeschützten Dokument angezeigt.

>[!NOTE]
>
>Nur Benutzer mit Administratorrechten für Document Security können Wasserzeichen erstellen. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Client-Objekts des Document Security-Services erforderlich sind.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Um ein Wasserzeichen zu erstellen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Legen Sie die Wasserzeichenattribute fest.
1. Registrieren Sie das Wasserzeichen beim Document Security-Service.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmatisch ausführen können, müssen Sie ein Client-Objekt für den Document Security-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient`-Objekt. Wenn Sie die Document Security-Webservice-API verwenden, erstellen Sie ein `RightsManagementServiceService`-Objekt.

**Festlegen der Wasserzeichenattribute**

Um ein Wasserzeichen zu erstellen, müssen Sie Wasserzeichenattribute festlegen. Das Namensattribut muss immer definiert sein. Zusätzlich zum Namensattribut müssen Sie mindestens eines der folgenden Attribute festlegen:

* Benutzerdefinierter Text
* DateIncluded
* UserIdIncluded
* UserNameIncluded

In der folgenden Tabelle sind Schlüssel-Wert-Paare aufgeführt, die zum Erstellen eines Wasserzeichens mithilfe von Web-Services erforderlich sind.

<table>
 <thead>
  <tr>
   <th><p>Schlüsselname</p></th>
   <th><p>Beschreibung</p></th>
   <th><p>Wert</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code>WaterBackCmd:IS_USERNAME_ENABLED</code></p></td>
   <td><p>Gibt an, ob der Benutzername des Benutzers, der das Dokument öffnet, Teil des Wasserzeichens ist.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_USERID_ENABLED</code></p></td>
   <td><p>Gibt an, ob die Kennung des Benutzers, der das Dokument öffnet, Teil des Wasserzeichens ist.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_CURRENTDATE_ENABLED</code></p></td>
   <td><p>Gibt an, ob das aktuelle Datum Teil des Wasserzeichens ist.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code></p></td>
   <td><p>Wenn dieser Wert „true“ ist, muss der Wert des benutzerdefinierten Textes mithilfe von <code>WaterBackCmd:SRCTEXT</code> angegeben werden.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:OPACITY</code></p></td>
   <td><p>Gibt die Deckkraft des Wasserzeichens an. Der Standardwert ist 0,5, wenn er nicht angegeben ist.</p></td>
   <td><p>Ein Wert zwischen 0,0 und 1,0.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:ROTATION</code></p></td>
   <td><p>Gibt die Drehung des Wasserzeichens an. Der Standardwert ist 0 Grad.</p></td>
   <td><p>Ein Wert zwischen 0 und 359.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:SCALE</code></p></td>
   <td><p>Wenn dieser Wert angegeben wird, muss <code>WaterBackCmd:IS_SIZE_ENABLED</code> vorhanden sein und den Wert „true“ haben. Wenn dieses Attribut nicht angegeben wird, ist das Standardverhalten die Anpassung an die Seitengröße.</p></td>
   <td><p>Ein Wert größer als 0.0 und kleiner gleich 1.0.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:HORIZ_ALIGN</code></p></td>
   <td><p>Gibt die horizontale Ausrichtung des Wasserzeichens an. Der Standardwert ist „Zentriert“.</p></td>
   <td><p>„Links“, „Zentriert“ oder „Rechts“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:VERT_ALIGN</code></p></td>
   <td><p>Gibt die vertikale Ausrichtung des Wasserzeichens an. Der Standardwert ist „Zentriert“.</p></td>
   <td><p>„Oben“, „Mitte“ oder „Unten“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_USE_BACKGROUND</code></p></td>
   <td><p>Gibt an, ob das Wasserzeichen ein Hintergrund ist. Der Standardwert lautet false.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_SIZE_ENABLED</code></p></td>
   <td><p>„True“, wenn eine benutzerdefinierte Skala angegeben ist. Wenn dieser Wert „true“ ist, muss auch „SCALE“ angegeben werden. Wenn dieser Wert „false“ ist, ist die Standardeinstellung die Anpassung an die Seitengröße.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:SRCTEXT</code></p></td>
   <td><p>Gibt den benutzerdefinierten Text für ein Wasserzeichen an. Wenn dieser Wert vorhanden ist, dann muss <code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code> ebenfalls vorhanden sein und auf „true“ gesetzt sein.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
 </tbody>
</table>

Für alle Wasserzeichen muss eines der folgenden Attribute definiert sein:

* `WaterBackCmd:IS_USERNAME_ENABLED`
* `WaterBackCmd:IS_USERID_ENABLED`
* `WaterBackCmd:IS_CURRENTDATE_ENABLED`
* `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`

Alle anderen Attribute sind optional.

**Registrieren des Wasserzeichens**

Ein neues Wasserzeichen muss beim Document Security-Service registriert werden, bevor es verwendet werden kann. Nachdem Sie ein Wasserzeichen registriert haben, können Sie es in Richtlinien verwenden.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Erstellen von Wasserzeichen mithilfe der Java-API {#create-watermarks-using-the-java-api}

So erstellen Sie ein Wasserzeichen mithilfe der Document Security-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien ein, z. B. die `adobe-rightsmanagement-client.jar`im Klassenpfad Ihres Java-Projekts.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen der Wasserzeichenattribute

   * Erstellen Sie eine `Watermark` -Objekt durch Aufrufen der `InfomodelObjectFactory` Statisches Objekt `createWatermark` -Methode. Diese Methode gibt ein `Watermark`-Objekt zurück.
   * Legen Sie das Attribut name des Wasserzeichens fest, indem Sie die `Watermark` -Objekt `setName` -Methode verwenden und einen string -Wert übergeben, der den Richtliniennamen angibt.
   * Legen Sie das Hintergrundattribut des Wasserzeichens fest, indem Sie die `Watermark` -Objekt `setBackground` Methode und Übergabe `true`. Wenn Sie dieses Attribut festlegen, wird das Wasserzeichen im Hintergrund des Dokuments angezeigt.
   * Festlegen des benutzerdefinierten Textattributs des Wasserzeichens durch Aufrufen der `Watermark` -Objekt `setCustomText` -Methode verwenden und einen string -Wert übergeben, der den Text des Wasserzeichens darstellt.
   * Festlegen des Deckkraftattributs des Wasserzeichens durch Aufrufen der `Watermark` -Objekt `setOpacity` -Methode verwenden und einen ganzzahligen Wert übergeben, der die Deckkraft angibt. Der Wert 100 zeigt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 zeigt an, dass das Wasserzeichen vollständig transparent ist.

1. Registrieren Sie das Wasserzeichen.

   * Erstellen Sie eine `WatermarkManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getWatermarkManager` -Methode. Diese Methode gibt ein `WatermarkManager`-Objekt zurück.
   * Registrieren Sie das Wasserzeichen, indem Sie die `WatermarkManager` -Objekt `registerWatermark` -Methode und Übergabe der `Watermark` -Objekt, das das zu registrierende Wasserzeichen darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Identifizierungswert des Wasserzeichens darstellt.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (SOAP-Modus): Erstellen eines Wasserzeichens mithilfe der Java-API“

### Erstellen von Wasserzeichen mit der Web-Service-API {#create-watermarks-using-the-web-service-api}

Erstellen Sie ein Wasserzeichen mithilfe der Document Security-API (Web-Service):

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `RightsManagementServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie ein `WatermarkSpec`-Objekt, indem Sie den Konstruktor `WatermarkSpec` aufrufen.
   * Legen Sie den Namen des Wasserzeichens fest, indem Sie dem `WatermarkSpec` -Objekt `name` Datenelement.
   * Festlegen der `id` -Attribut durch Zuweisen eines Zeichenfolgenwerts zum `WatermarkSpec` -Objekt `id` Datenelement.
   * Erstellen Sie für jede festzulegende Wasserzeicheneigenschaft ein separates `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` Datenelement (z. B. `WaterBackCmd:OPACITY)`.
   * Legen Sie den Wert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` Datenelement (z. B. `.25`).
   * Erstellen Sie ein `MyArrayOf_xsd_anyType`-Objekt. Für jeden `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt, rufen Sie die `MyArrayOf_xsd_anyType` -Objekt `Add` -Methode. Übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Zuweisen der `MyArrayOf_xsd_anyType` -Objekt `WatermarkSpec` -Objekt `values` Datenelement.

1. Registrieren Sie das Wasserzeichen.

   Registrieren Sie das Wasserzeichen, indem Sie die `RightsManagementServiceClient` -Objekt `registerWatermark` -Methode und Übergabe der `WatermarkSpec` -Objekt, das das zu registrierende Wasserzeichen darstellt.

**Code-Beispiele**

Code-Beispiele zur Verwendung des Document Security-Services finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Erstellen eines Wasserzeichens mithilfe der Web-Service-API“
* „Schnellstartanleitung (SwaRef): Erstellen eines Wasserzeichens mithilfe der Web-Service-API“

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Ändern von Wasserzeichen {#modifying-watermarks}

Sie können ein vorhandenes Wasserzeichen mithilfe der Document Security Java-API oder der Web-Service-API ändern. Sie nehmen Änderungen an einem vorhandenen Wasserzeichen vor, indem Sie es abrufen, seine Attribute ändern und es dann auf dem Server aktualisieren. Angenommen, Sie rufen ein Wasserzeichen ab und ändern dessen Attribut für die Deckkraft. Die Änderung wird erst wirksam, nachdem Sie das Wasserzeichen aktualisiert haben.

Wenn Sie ein Wasserzeichen ändern, wirkt sich die Änderung auf zukünftige Dokumente aus, auf die das Wasserzeichen angewendet wird. Vorhandene PDF-Dokumente, die das Wasserzeichen enthalten, sind also nicht betroffen.

>[!NOTE]
>
>Nur Benutzer mit Administratorrechten für Document Security können Wasserzeichen ändern. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Client-Objekts des Document Security-Services erforderlich sind.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-9}

Gehen Sie wie folgt vor, um ein Wasserzeichen zu ändern:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie das zu ändernde Wasserzeichen ab.
1. Legen Sie die Wasserzeichenattribute fest.
1. Aktualisieren Sie das Wasserzeichen.

**Projektdateien einbinden**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmatisch ausführen können, müssen Sie ein Client-Objekt für den Document Security-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient`-Objekt. Wenn Sie die Document Security-Web-Service-API verwenden, erstellen Sie ein `DocumentSecurityServiceService`-Objekt.

**Das zu ändernde Wasserzeichen abrufen**

Um ein Wasserzeichen zu ändern, müssen Sie ein vorhandenes Wasserzeichen abrufen. Sie können ein Wasserzeichen abrufen, indem Sie dessen Namen oder dessen Kennungswert angeben.

**Wasserzeichenattribute festlegen**

Um ein vorhandenes Wasserzeichen zu ändern, ändern Sie den Wert eines oder mehrerer Wasserzeichenattribute. Beim programmatischen Aktualisieren eines Wasserzeichens mithilfe eines Webdiensts müssen Sie alle ursprünglich festgelegten Attribute festlegen, auch wenn sich der Wert nicht ändert. Angenommen, die folgenden Wasserzeichenattribute sind festgelegt: `WaterBackCmd:IS_USERID_ENABLED`, `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`, `WaterBackCmd:OPACITY` und `WaterBackCmd:SRCTEXT`. Selbst wenn Sie nur das Attribut `WaterBackCmd:OPACITY` ändern möchten, müssen Sie auch die anderen Werte festlegen.

>[!NOTE]
>
>Wenn Sie die Java-API zum Ändern eines Wasserzeichens verwenden, müssen Sie nicht alle Attribute angeben. Legen Sie das Wasserzeichenattribut fest, das Sie ändern möchten.

>[!NOTE]
>
>Weitere Informationen zu den Namen der Wasserzeichenattribute finden Sie unter [Erstellen von Wasserzeichen](protecting-documents-policies.md#creating-watermarks).

**Wasserzeichen aktualisieren**

Nachdem Sie die Attribute eines Wasserzeichens geändert haben, müssen Sie das Wasserzeichen aktualisieren.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Erstellen von Wasserzeichen](protecting-documents-policies.md#creating-watermarks)

### Ändern von Wasserzeichen mithilfe der Java-API {#modify-watermarks-using-the-java-api}

So ändern Sie ein Wasserzeichen mithilfe der Document Security-API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-rightsmanagement-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Erstellen Sie eine `WatermarkManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getWatermarkManager` -Methode verwenden und einen string -Wert übergeben, der den Namen des Wasserzeichens angibt. Diese Methode gibt ein `Watermark`-Objekt zurück, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   Festlegen des Deckkraftattributs des Wasserzeichens durch Aufrufen der `Watermark` -Objekt `setOpacity` -Methode verwenden und einen ganzzahligen Wert übergeben, der die Deckkraft angibt. Der Wert 100 zeigt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 zeigt an, dass das Wasserzeichen vollständig transparent ist.

   >[!NOTE]
   >
   >In diesem Beispiel wird nur das Attribut für die Deckkraft geändert.

1. Aktualisieren Sie das Wasserzeichen.

   * Aktualisieren Sie das Wasserzeichen, indem Sie die `WatermarkManager` -Objekt `updateWatermark` -Methode und übergeben Sie `Watermark` -Objekt, dessen -Attribut geändert wurde.

**Code-Beispiele**

Code-Beispiele, die den Document Security-Service verwenden, finden Sie im Abschnitt „Schnellstart (SOAP-Modus): Ändern eines Wasserzeichens mithilfe der Java-API“.

### Ändern von Wasserzeichen mithilfe der Webservice-API {#modify-watermarks-using-the-web-service-api}

Ändern eines Wasserzeichens mithilfe der Document Security-API (Webservice):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `DocumentSecurityServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zum `BasicHttpBindingSecurity.Security.Mode`-Feld zu.

1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Rufen Sie das zu ändernde Wasserzeichen ab, indem Sie die `DocumentSecurityServiceClient` -Objekt `getWatermarkByName` -Methode. Übergeben Sie einen Zeichenfolgenwert, der den Namen des Wasserzeichens angibt. Diese Methode gibt ein `WatermarkSpec`-Objekt zurück, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie für jede zu aktualisierende Wasserzeicheneigenschaft ein separates `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `key` Datenelement (z. B. `WaterBackCmd:OPACITY)`.
   * Legen Sie den Wert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt `value` Datenelement (z. B. `.50`).
   * Erstellen Sie ein `MyArrayOf_xsd_anyType`-Objekt. Für jeden `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt, rufen Sie die `MyArrayOf_xsd_anyType` -Objekt `Add` -Methode. Übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Zuweisen der `MyArrayOf_xsd_anyType` -Objekt `WatermarkSpec` -Objekt `values` Datenelement.

1. Aktualisieren Sie das Wasserzeichen.

   Aktualisieren Sie das Wasserzeichen, indem Sie die `DocumentSecurityServiceClient` -Objekt `updateWatermark` -Methode und Übergabe der `WatermarkSpec` -Objekt, das das zu ändernde Wasserzeichen darstellt.

**Code-Beispiele**

Code-Beispiele, die den Document Security-Service verwenden, finden Sie in folgendem Schnellstart:

* „Schnellstartanleitung (MTOM): Ändern eines Wasserzeichens mithilfe der Webservice-API“

## Suchen nach Ereignissen {#searching-for-events}

Der Rights Management-Service verfolgt bestimmte Aktionen, während sie auftreten, z. B. das Anwenden einer Richtlinie auf ein Dokument, das Öffnen eines richtliniengeschützten Dokuments und das Sperren des Zugriffs auf Dokumente. Die Ereignisprüfung muss für den Rights Management-Service aktiviert sein, sonst werden Ereignisse nicht verfolgt.

Ereignisse werden in die folgenden Kategorien unterteilt:

* Administrator-Ereignisse sind Aktionen, die sich auf einen Administrator beziehen, z. B. die Erstellung eines Administratorkontos.
* Dokumentereignisse sind Aktionen im Zusammenhang mit einem Dokument, z. B. das Schließen eines richtliniengeschützten Dokuments.
* Richtlinienereignisse sind Aktionen im Zusammenhang mit einer Richtlinie, z. B. das Erstellen einer Richtlinie.
* Service-Ereignisse sind Aktionen im Zusammenhang mit dem Rights Management-Service, z. B. die Synchronisierung mit dem Benutzerverzeichnis.

Sie können mit der Rights Management-Java-API oder der Webservice-API nach bestimmten Ereignissen suchen. Durch die Suche nach Ereignissen können Sie Aufgaben ausführen, z. B. eine Protokolldatei bestimmter Ereignisse erstellen.

>[!NOTE]
>
>Weitere Informationen zum Rights Management-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-10}

Um nach einem Rights Management-Ereignis zu suchen, führen Sie die folgenden Schritte aus:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Rights Management-Client-API-Objekt.
1. Geben Sie das Ereignis an, nach dem gesucht werden soll.
1. Suchen Sie nach dem Ereignis.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Rights Management-Client-API-Objekts**

Bevor Sie einen Rights Management-Service-Vorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt für den Rights Management-Service erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient`-Objekt. Wenn Sie die Rights Management-Webservice-API verwenden, erstellen Sie ein `DocumentSecurityServiceService`-Objekt.

**Geben Sie die Ereignisse an, nach denen gesucht werden soll**

Geben Sie das zu suchende Ereignis an. Sie können beispielsweise nach dem Richtlinienerstellungsereignis suchen, das beim Erstellen einer neuen Richtlinie auftritt.

**Suchen nach dem Ereignis**

Nachdem Sie das zu suchende Ereignis angegeben haben, können Sie entweder die Rights Management Java-API oder die Rights Management-Webservice-API verwenden, um nach dem Ereignis zu suchen.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Suchen nach Ereignissen mithilfe der Java-API {#search-for-events-using-the-java-api}

So suchen Sie mithilfe der Rights Management-API (Java) nach Ereignissen:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Rights Management-Client-API-Objekts

   Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory`-Objekt übergeben, das Verbindungseigenschaften enthält.

1. Angeben der Ereignisse, nach denen gesucht werden soll

   * Erstellen Sie eine `EventManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getEventManager` -Methode. Diese Methode gibt ein `EventManager`-Objekt zurück.
   * Erstellen Sie ein `EventSearchFilter`-Objekt, indem Sie seinen Konstruktor aufrufen.
   * Geben Sie das zu suchende Ereignis an, indem Sie die `EventSearchFilter` -Objekt `setEventCode` -Methode und Übergeben eines statischen Datenelements, das zu der `EventManager` -Klasse, die das zu suchende Ereignis darstellt. Um beispielsweise nach dem Richtlinienerstellungsereignis zu suchen, übergeben Sie `EventManager.POLICY_CREATE_EVENT`.

   >[!NOTE]
   >
   >Sie können zusätzliche Suchkriterien definieren, indem Sie die Methoden des `EventSearchFilter`-Objekts aufrufen. Rufen Sie beispielsweise die Methode `setUserName` auf, um einen mit dem Ereignis verknüpften Benutzer anzugeben.

1. Suchen nach dem Ereignis

   Suchen Sie nach dem Ereignis, indem Sie die `EventManager` -Objekt `searchForEvents` -Methode und Übergabe der `EventSearchFilter` -Objekt, das die Ereignissuchkriterien definiert. Diese Methode gibt ein Array von `Event`-Objekten zurück.

**Code-Beispiele**

Code-Beispiele, die den Rights Management-Service verwenden, finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (SOAP): Suchen nach Ereignissen mithilfe der Java-API“

### Suchen nach Ereignissen mithilfe der Webservice-API {#search-for-events-using-the-web-service-api}

So suchen Sie mithilfe der Rights Management-API (Webservice) nach Ereignissen:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Rights Management-Client-API-Objekts

   * Erstellen Sie ein `DocumentSecurityServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `DocumentSecurityServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Angeben der Ereignisse, nach denen gesucht werden soll

   * Erstellen Sie ein `EventSpec`-Objekt, indem Sie seinen Konstruktor verwenden.
   * Geben Sie den Beginn des Zeitraums an, in dem das Ereignis aufgetreten ist, indem Sie die `EventSpec` -Objekt `firstTime.date` Datenelement mit `DataTime` -Instanz, die den Beginn des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Wert zuweisen `true` der `EventSpec` -Objekt `firstTime.dateSpecified` Datenelement.
   * Geben Sie das Ende des Zeitraums an, in dem das Ereignis aufgetreten ist, indem Sie die `EventSpec` -Objekt `lastTime.date` Datenelement mit `DataTime` -Instanz, die das Ende des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Wert zuweisen `true` der `EventSpec` -Objekt `lastTime.dateSpecified` Datenelement.
   * Legen Sie das zu suchende Ereignis fest, indem Sie dem `EventSpec` -Objekt `eventCode` Datenelement. In der folgenden Tabelle sind die numerischen Werte aufgeführt, die Sie dieser Eigenschaft zuweisen können:

   <table>
    <thead>
    <tr>
    <th><p>Ereignistyp</p></th>
    <th><p>Wert</p></th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td><p><code>ALL_EVENTS</code></p></td>
    <td><p>999</p></td>
    </tr>
    <tr>
    <td><p><code>USER_CHANGE_PASSWORD_EVENT</code></p></td>
    <td><p>1000</p></td>
    </tr>
    <tr>
    <td><p><code>USER_REGISTER_EVENT</code></p></td>
    <td><p>1001</p></td>
    </tr>
    <tr>
    <td><p><code>USER_PREREGISTER_EVENT</code></p></td>
    <td><p>1002</p></td>
    </tr>
    <tr>
    <td><p><code>USER_ACTIVATE_EVENT</code></p></td>
    <td><p>1003</p></td>
    </tr>
    <tr>
    <td><p><code>USER_DEACTIVATE_EVENT</code></p></td>
    <td><p>1004</p></td>
    </tr>
    <tr>
    <td><p><code>USER_AUTHENTICATE_EVENT</code></p></td>
    <td><p>1005</p></td>
    </tr>
    <tr>
    <td><p><code>USER_AUTHENTICATE_DENY_EVENT </code></p></td>
    <td><p>1006</p></td>
    </tr>
    <tr>
    <td><p><code>USER_ACCOUNT_LOCK_EVENT</code></p></td>
    <td><p>1007</p></td>
    </tr>
    <tr>
    <td><p><code>USER_DELETE_EVENT </code></p></td>
    <td><p>1008</p></td>
    </tr>
    <tr>
    <td><p><code>USER_UPDATE_PROFILE_EVENT </code></p></td>
    <td><p>1009</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_VIEW_EVENT </code></p></td>
    <td><p>2.000</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_PRINT_LOW_EVENT </code></p></td>
    <td><p>2001</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_PRINT_HIGH_EVENT </code></p></td>
    <td><p>2002</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_SIGN_EVENT </code></p></td>
    <td><p>2003</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_ADD_ANNOTATION_EVENT </code></p></td>
    <td><p>2004</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_FORM_FILL_EVENT </code></p></td>
    <td><p>2005</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_CLOSE_EVENT </code></p></td>
    <td><p>2006</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_MODIFY_EVENT </code></p></td>
    <td><p>2007</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_CHANGE_SECURITY_HANDLER_EVENT </code></p></td>
    <td><p>2008</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_SWITCH_POLICY_EVENT </code></p></td>
    <td><p>2009</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_REVOKE_EVENT </code></p></td>
    <td><p>2010</p></td>
    </tr>
    <tr>
    <td><p><code>$1</code></p></td>
    <td><p>2011</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_SECURE_EVENT </code></p></td>
    <td><p>2012</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_UNKNOWN_CLIENT_EVENT </code></p></td>
    <td><p>2013</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_CHANGE_REVOKE_URL_EVENT </code></p></td>
    <td><p>2014</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_CHANGE_EVENT </code></p></td>
    <td><p>3000</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_ENABLE_EVENT </code></p></td>
    <td><p>3001</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_DISABLE_EVENT </code></p></td>
    <td><p>3002</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_CREATE_EVENT </code></p></td>
    <td><p>3003</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_DELETE_EVENT </code></p></td>
    <td><p>3004</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_CHANGE_OWNER_EVENT </code></p></td>
    <td><p>3005</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_CLIENT_SYNC_EVENT </code></p></td>
    <td><p>4000</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_SYNC_DIR_INFO_EVENT </code></p></td>
    <td><p>4001</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_SYNC_DIR_COMPLETE_EVENT </code></p></td>
    <td><p>4002</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_VERSION_MISMATCH_EVENT </code></p></td>
    <td><p>4003</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_CONFIG_CHANGE_EVENT </code></p></td>
    <td><p>4004</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_ENABLE_OFFLINE_ACCESS_EVENT </code></p></td>
    <td><p>4005</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_ADD_EVENT </code></p></td>
    <td><p>5.000</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_DELETE_EVENT </code></p></td>
    <td><p>5001</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_EDIT_EVENT </code></p></td>
    <td><p>5002</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_ACTIVATE_EVENT </code></p></td>
    <td><p>5003</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_DEACTIVATE_EVENT </code></p></td>
    <td><p>5004</p></td>
    </tr>
    <tr>
    <td><p><code>ERROR_DIRECTORY_SERVICE_EVENT </code></p></td>
    <td><p>6.000</p></td>
    </tr>
    <tr>
    <td><p><code>CREATED_POLICYSET_EVENT</code></p></td>
    <td><p>7000</p></td>
    </tr>
    <tr>
    <td><p><code>DELETED_POLICYSET_EVENT</code></p></td>
    <td><p>7001</p></td>
    </tr>
    <tr>
    <td><p><code>MODIFIED_POLICYSET_EVENT</code></p></td>
    <td><p>7002</p></td>
    </tr>
    </tbody>
    </table>

1. Suchen nach dem Ereignis

   Suchen Sie nach dem Ereignis, indem Sie die `DocumentSecurityServiceClient` -Objekt `searchForEvents` -Methode und Übergabe der `EventSpec` -Objekt, das das Ereignis, für das gesucht werden soll, und die maximale Anzahl von Ergebnissen darstellt. Diese Methode gibt eine `MyArrayOf_xsd_anyType`-Sammlung zurück, in der jedes Element eine `AuditSpec`-Instanz ist. Mithilfe einer `AuditSpec`-Instanz können Sie Informationen zum Ereignis abrufen, z. B. den Zeitpunkt, zu dem es aufgetreten ist. Die `AuditSpec`-Instanz enthält ein `timestamp`-Datenelement, das diese Informationen angibt.

**Code-Beispiele**

Code-Beispiele, die den Rights Management-Service verwenden, finden Sie in den folgenden Kurzanleitungen:

* „Schnellstartanleitung (MTOM): Suchen nach Ereignissen mithilfe der Web-Service-API“
* „Schnellstartanleitung (SwaRef): Suchen nach Ereignissen mithilfe der Web-Service-API“

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Anwenden von Richtlinien auf Word-Dokumente {#applying-policies-to-word-documents}

Neben PDF-Dokumenten unterstützt der Rights Management-Service auch weitere Dokumentenformate wie Microsoft Word-Dokumente (DOC-Dateien) und andere Microsoft Office-Dateiformate. Sie können beispielsweise eine Richtlinie auf ein Word-Dokument anwenden, um es zu schützen. Durch Anwendung einer Richtlinie auf ein Word-Dokument können Sie den Zugriff auf das Dokument einschränken. Sie können eine Richtlinie nicht auf ein Dokument anwenden, das bereits durch eine Richtlinie geschützt ist.

Sie können die Verwendung eines richtliniengeschützten Word-Dokuments nach dessen Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-11}

So wenden Sie eine Richtlinie auf ein Word-Dokument an:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie ein Word-Dokument ab, auf das eine Richtlinie angewendet werden soll.
1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.
1. Speichern Sie das richtliniengeschützte Word-Dokument.

**Projektdateien einbinden**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Service-Vorgang programmatisch ausführen können, müssen Sie ein Client-Objekt für den Document Security-Service erstellen.

**Abrufen eines Word-Dokuments**

Rufen Sie ein Word-Dokument ab, um eine Richtlinie anzuwenden. Nachdem Sie eine Richtlinie auf das Word-Dokument angewendet haben, sind Benutzer bei der Verwendung des Dokuments eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offline-Modus ermöglicht, müssen die Benutzer online sein, um das Dokument zu öffnen.

**Vorhandene Richtlinie auf das Word-Dokument anwenden**

Um eine Richtlinie auf ein Word-Dokument anzuwenden, müssen Sie auf eine vorhandene Richtlinie verweisen und angeben, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften festlegt, muss Zugriff auf die angegebene Richtlinie haben. Andernfalls wird eine Ausnahme ausgelöst.

**Word-Dokument speichern**

Nachdem der Document Security-Service eine Richtlinie auf ein Word-Dokument angewendet hat, können Sie das richtliniengeschützte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Eine Richtlinie auf ein Word-Dokument mithilfe der Java-API anwenden {#apply-a-policy-to-a-word-document-using-the-java-api}

Wenden Sie mithilfe der Document Security-API (Java) eine Richtlinie auf ein Word-Dokument an:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein Word-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das Word-Dokument darstellt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `DocumentSecurityClient` -Objekt `getDocumentManager` -Methode.
   * Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `DocumentManager` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document`-Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Einen Zeichenfolgenwert, der die Versionsnummer des Dokuments angibt.
      * Einen Zeichenfolgenwert, der den Namen des Satzes angibt, zu dem die Richtlinie gehört. Sie können einen `null`-Wert angeben, der dazu führt, dass der Richtliniensatz `MyPolicies` verwendet wird.
      * Einen Zeichenfolgenwert, der den Richtliniennamen angibt.
      * Einen Zeichenfolgenwert für den Namen die User Manager-Domain des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert null sein.)
      * Ein Zeichenfolgenwert für den kanonischen Namen des User Manager-Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` sein (wenn dieser Parameter `null` ist, muss der vorherige Parameterwert `null` sein).
      * Ein `com.adobe.livecycle.rightsmanagement.Locale`-Objekt, die das Gebietsschema darstellt, das für die Auswahl der MS Office-Vorlage verwendet wird. Dieser Parameterwert ist optional und Sie können `null` angeben.

     Die `protectDocument`-Methode gibt ein `RMSecureDocumentResult`-Objekt zurück, das das richtliniengeschützte Word-Dokument enthält.

1. Speichern Sie das Word-Dokument.

   * Rufen Sie die `RMSecureDocumentResult` -Objekt `getProtectedDoc` -Methode zum Abrufen des richtliniengeschützten Word-Dokuments. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück.
   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung DOC lautet.
   * Rufen Sie die `com.adobe.idp.Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `getProtectedDoc` -Methode).

**Code-Beispiele**

Code-Beispiele, die den Document Security-Service verwenden, finden Sie in folgendem Schnellstart:

* „Schnellstartanleitung (SOAP-Modus): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Java-API“

### Eine Richtlinie auf ein Word-Dokument mithilfe der Web Service-API anwenden {#apply-a-policy-to-a-word-document-using-the-web-service-api}

Wenden Sie mithilfe der Document Security-API (Web-Service) eine Richtlinie auf ein Word-Dokument an:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DocumentSecurityService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security-Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `DocumentSecurityServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Rufen Sie ein Word-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines Word-Dokuments verwendet, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Bestimmen Sie die Byte-Array-Größe, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Datenstromlänge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `DocumentSecurityServiceClient` -Objekt `protectDocument` -Methode verwenden und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Einen Zeichenfolgenwert, der die Versionsnummer des Dokuments angibt.
   * Einen Zeichenfolgenwert, der den Namen des Satzes angibt, zu dem die Richtlinie gehört. Sie können einen `null`-Wert angeben, der dazu führt, dass der Richtliniensatz `MyPolicies` verwendet wird.
   * Einen Zeichenfolgenwert, der den Richtliniennamen angibt.
   * Einen Zeichenfolgenwert für den Namen die User Manager-Domain des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert `null` sein).
   * Ein Zeichenfolgenwert für den kanonischen Namen des User Manager-Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null` sein).
   * Ein `RMLocale`-Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein Zeichenfolgen-Ausgabeparameter, der zum Speichern des Richtlinienkennungswerts verwendet wird.
   * Ein Zeichenfolgen-Ausgabeparameter, der zum Speichern des Werts der richtliniengeschützten Kennung verwendet wird.
   * Ein Zeichenfolgen-Ausgabeparameter, der zum Speichern des MIME-Typs verwendet wird (z. B. `application/doc`).

   Die Methode `protectDocument` gibt ein `BLOB`-Objekt zurück, das das richtliniengeschützte Word-Dokument enthält.

1. Speichern Sie das Word-Dokument.

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des richtliniengeschützten Word-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `protectDocument` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` Datenelement.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine Word-Datei, indem Sie die `System.IO.BinaryWriter` -Objekt `Write` -Methode verwenden und das Byte-Array übergeben.

**Code-Beispiele**

Code-Beispiele, die den Document Security-Service verwenden, finden Sie in folgendem Schnellstart:

* „Schnellstartanleitung (MTOM): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Webservice-API“

## Entfernen von Richtlinien aus Word-Dokumenten {#removing-policies-from-word-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, Sie möchten nicht mehr, dass das Dokument durch eine Richtlinie geschützt wird. Wenn Sie ein richtliniengeschütztes Word-Dokument mit einer neueren Richtlinie aktualisieren möchten, ist es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Service finden Sie in der [Service-Referenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-12}

Um eine Richtlinie aus einem richtliniengeschützten Word-Dokument zu entfernen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security-Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Word-Dokument ab.
1. Entfernen Sie die Richtlinie aus dem Word-Dokument.
1. Speichern Sie die ungesicherten Word-Dokumente.

**Einschließen von Projektdateien**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie ein Client-Programm mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Web-Services verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security-Client-API-Objekts**

Bevor Sie einen Document Security Service-Vorgang programmgesteuert durchführen können, erstellen Sie ein Document Security Service-Client-Objekt.

**Abrufen eines richtliniengeschützten Word-Dokuments**

Rufen Sie ein richtliniengeschütztes Word-Dokument ab, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem Word-Dokument zu entfernen, das gar nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme verursacht.

**Entfernen der Richtlinie aus dem Word-Dokument**

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Andernfalls muss die zum Schützen eines Dokuments verwendete Richtlinie die `SWITCH_POLICY` Berechtigung zum Entfernen einer Richtlinie aus einem Word-Dokument. Außerdem muss der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Speichern des ungesicherten Word-Dokuments**

Nachdem der Document Security-Webservice eine Richtlinie aus einem Word-Dokument entfernt hat, können Sie das ungesicherte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf Word-Dokumente](protecting-documents-policies.md#applying-policies-to-word-documents)

### Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Java-API {#remove-a-policy-from-a-word-document-using-the-java-api}

So entfernen Sie mithilfe der Document Security-API (Java) eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security-Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte Word-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen der Richtlinie aus dem Word-Dokument

   * Erstellen Sie eine `DocumentManager` -Objekt durch Aufrufen der `RightsManagementClient` -Objekt `getDocumentManager` -Methode.
   * Entfernen Sie eine Richtlinie aus dem Word-Dokument, indem Sie die `DocumentManager` -Objekt `removeSecurity` -Methode und Übergabe der `com.adobe.idp.Document` -Objekt, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt ein `com.adobe.idp.Document`-Objekt zurück, das ein ungesichertes Word-Dokument enthält.

1. Speichern des ungesicherten Word-Dokuments

   * Erstellen Sie ein `java.io.File`-Objekt und stellen Sie sicher, dass die Dateierweiterung .doc ist.
   * Rufen Sie die `Document` -Objekt `copyToFile` -Methode zum Kopieren des Inhalts der `Document` -Objekt auf die Datei verweist (stellen Sie sicher, dass Sie die `Document` -Objekt, das von der `removeSecurity` -Methode).

**Code-Beispiele**

Code-Beispiele, die den Document Security-Service verwenden, finden Sie in folgendem Schnellstart:

* „Schnellstartanleitung (SOAP-Modus): Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Java-API“

### Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Webservice-API {#remove-a-policy-from-a-word-document-using-the-web-service-api}

So entfernen Sie mithilfe der Document Security-API (Webservice) eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security-Client-API-Objekts

   * Erstellen Sie ein `RightsManagementServiceClient`-Objekt, indem Sie seinen Standardkonstruktor verwenden.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt, indem Sie den Konstruktor `System.ServiceModel.EndpointAddress` verwenden. Übergeben Sie einen Zeichenfolgenwert, der die WSDL für den AEM Forms-Service angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version`-Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie einen Service-Verweis erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding`-Objekt durch Abrufen des Werts des Felds `RightsManagementServiceClient.Endpoint.Binding`. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie die `System.ServiceModel.BasicHttpBinding` -Objekt `MessageEncoding` -Feld zu `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Schritte ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den AEM Forms-Benutzernamen zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Passwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den konstanten Wert `HttpClientCredentialType.Basic` zu.

   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den konstanten Wert `BasicHttpSecurityMode.TransportCredentialOnly` zu.

1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des richtliniengeschützten Word-Dokuments verwendet, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des `System.IO.FileStream`-Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` -Objekt `Length` -Eigenschaft.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `System.IO.FileStream` -Objekt `Read` -Methode verwenden und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie seinem Feld `MTOM` den Inhalt des Byte-Arrays zuweisen.

1. Entfernen der Richtlinie aus dem Word-Dokument

   Entfernen Sie die Richtlinie aus dem Word-Dokument, indem Sie die `RightsManagementServiceClient` -Objekt `removePolicySecurity` -Methode und Übergabe der `BLOB` -Objekt, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt ein `BLOB`-Objekt zurück, das ein ungesichertes Word-Dokument enthält.

1. Speichern des ungesicherten Word-Dokuments

   * Erstellen Sie ein `System.IO.FileStream`-Objekt, indem Sie seinen Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des ungesicherten Word-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB`-Objekts speichert, das von der Methode `removePolicySecurity` zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert der `BLOB` -Objekt `MTOM` -Feld.
   * Erstellen Sie ein `System.IO.BinaryWriter`-Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream`-Objekt übergeben.

**Code-Beispiele**

Code-Beispiele, die den Document Security-Service verwenden, finden Sie in folgendem Schnellstart:

* „Schnellstartanleitung (MTOM): Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Webservice-API“

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
