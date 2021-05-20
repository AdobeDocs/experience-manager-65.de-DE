---
title: Schützen von Dokumenten mit Richtlinien
seo-title: Schützen von Dokumenten mit Richtlinien
description: Verwenden Sie den Document Security-Dienst, um Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten. Der Document Security-Dienst ermöglicht es den Benutzern auch, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden.
seo-description: Verwenden Sie den Document Security-Dienst, um Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten. Der Document Security-Dienst ermöglicht es den Benutzern auch, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden.
uuid: 6feb69ef-7b61-4d0b-8c87-d65d98bae9b5
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9b1d2bf3-f28c-41b2-9026-1f3311556422
role: Developer
exl-id: ff42579e-6aaf-433d-8b5d-9e9dd0957250
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '15558'
ht-degree: 4%

---

# Schützen von Dokumenten mit Richtlinien {#protecting-documents-with-policies}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

**Informationen zum Document Security-Dienst**

Der Document Security-Dienst ermöglicht es Benutzern, Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten, unabhängig davon, wie weit sie verteilt sind.

Der Document Security-Dienst verhindert, dass Informationen über die Reichweite des Benutzers verteilt werden, indem er es Benutzern ermöglicht, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden. Ein Benutzer kann angeben, wer ein Dokument öffnen, einschränken, wie es verwendet werden kann, und das Dokument nach seiner Verteilung überwachen. Ein Benutzer kann auch den Zugriff auf ein richtliniengeschütztes Dokument dynamisch steuern und sogar den Zugriff auf das Dokument dynamisch sperren.

Der Document Security-Dienst schützt auch andere Dateitypen wie Microsoft Word-Dateien (DOC-Dateien). Sie können die Document Security Client-API verwenden, um mit diesen Dateitypen zu arbeiten. Die folgenden Versionen werden unterstützt:

* Microsoft Office 2003-Dateien (DOC-, XLS-, PPT-Dateien)
* Microsoft Office 2007-Dateien (DOCX-, XLSX-, PPTX-Dateien)
* PTC Pro/E-Dateien

In den beiden folgenden Abschnitten wird die Verwendung von Word-Dokumenten erläutert:

* [Anwenden von Richtlinien auf Word-Dokumente](protecting-documents-policies.md#applying-policies-to-word-documents)
* [Entfernen von Richtlinien aus Word-Dokumenten](protecting-documents-policies.md#removing-policies-from-word-documents)

Sie können diese Aufgaben mithilfe des Document Security-Dienstes ausführen:

* Erstellen von Richtlinien. Weitere Informationen finden Sie unter [Erstellen von Richtlinien](protecting-documents-policies.md#creating-policies).
* Richtlinien ändern. Weitere Informationen finden Sie unter [Ändern von Richtlinien](protecting-documents-policies.md#modifying-policies).
* Richtlinien löschen Weitere Informationen finden Sie unter [Löschen von Richtlinien](protecting-documents-policies.md#deleting-policies).
* Anwenden von Richtlinien auf PDF-Dokumente. Weitere Informationen finden Sie unter [Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents).
* Richtlinien aus PDF-Dokumenten entfernen. Weitere Informationen finden Sie unter [Entfernen von Richtlinien aus PDF-Dokumenten](protecting-documents-policies.md#removing-policies-from-pdf-documents).
* Richtliniengeschützte Inspect-Dokumente. Weitere Informationen finden Sie unter [Überprüfen von richtliniengeschützten PDF-Dokumenten](protecting-documents-policies.md#inspecting-policy-protected-pdf-documents).
* Zugriff auf PDF-Dokumente sperren. Weitere Informationen finden Sie unter [Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents).
* Neuer Zugriff auf gesperrte Dokumente. Weitere Informationen finden Sie unter [Wiedereinsetzen des Zugriffs auf gesperrte Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents).
* Erstellen Sie Wasserzeichen. Weitere Informationen finden Sie unter [Erstellen von Wasserzeichen](protecting-documents-policies.md#creating-watermarks).
* Suchen Sie nach Ereignissen. Weitere Informationen finden Sie unter [Suchen nach Ereignissen](protecting-documents-policies.md#searching-for-events).

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Erstellen von Richtlinien {#creating-policies}

Sie können Richtlinien programmgesteuert mit der Document Security Java-API oder der Web Service-API erstellen. Eine *policy* ist eine Sammlung von Informationen, die Document Security-Einstellungen, autorisierte Benutzer und Verwendungsrechte umfasst. Sie können eine beliebige Anzahl von Richtlinien erstellen und speichern, indem Sie Sicherheitseinstellungen verwenden, die für unterschiedliche Situationen und Benutzer geeignet sind.

Richtlinien ermöglichen Ihnen die Durchführung folgender Aufgaben:

* Geben Sie die Personen an, die das Dokument öffnen können. Die Empfänger können entweder zu Ihrer Organisation gehören oder diese externe Person sein.
* Geben Sie an, wie Empfänger das Dokument verwenden können. Sie können den Zugriff auf verschiedene Acrobat- und Adobe Reader-Funktionen einschränken. Zu diesen Funktionen gehört die Möglichkeit, Text zu drucken und zu kopieren, Signaturen hinzuzufügen und einem Dokument Kommentare hinzuzufügen.
* Ändern Sie die Zugriffs- und Sicherheitseinstellungen jederzeit, auch nachdem Sie das richtliniengeschützte Dokument verteilt haben.
* Überwachen Sie die Verwendung des Dokuments nach seiner Verteilung. Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können beispielsweise feststellen, wann ein Benutzer das Dokument geöffnet hat.

### Erstellen einer Richtlinie mithilfe von Webdiensten {#creating-a-policy-using-web-services}

Wenn Sie eine Richtlinie mit der Webdienst-API erstellen, verweisen Sie auf eine vorhandene XML-Datei für Portable Document Rights Language (PDRL), die die Richtlinie beschreibt. Richtlinienberechtigungen und der Prinzipal werden im PDRL-Dokument definiert. Das folgende XML-Dokument ist ein Beispiel für ein PDRL-Dokument.

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
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

Um eine Richtlinie zu erstellen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Legen Sie die Attribute der Richtlinie fest.
1. Erstellen Sie einen Richtlinieneintrag.
1. Registrieren Sie die Richtlinie.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

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
* jbossall-client.jar (verwenden Sie eine andere JAR-Datei, wenn AEM Forms nicht auf JBoss bereitgestellt ist)

Informationen zum Speicherort dieser JAR-Dateien finden Sie unter [Einschließen von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Festlegen der Richtlinienattribute**

Legen Sie zum Erstellen einer Richtlinie Richtlinienattribute fest. Ein obligatorisches Attribut ist der Richtlinienname. Richtliniennamen müssen für jeden Richtliniensatz eindeutig sein. Ein Richtliniensatz ist lediglich eine Sammlung von Richtlinien. Es kann zwei Richtlinien mit demselben Namen geben, wenn die Richtlinien zu separaten Richtliniensätzen gehören. Zwei Richtlinien in einem einzigen Richtliniensatz dürfen jedoch nicht denselben Richtliniennamen haben.

Ein weiteres nützliches Attribut, das festgelegt werden kann, ist der Gültigkeitszeitraum. Ein Gültigkeitszeitraum ist der Zeitraum, in dem autorisierte Empfänger auf ein richtliniengeschütztes Dokument zugreifen können. Wenn Sie dieses Attribut nicht festlegen, ist die Richtlinie immer gültig.

Für einen Gültigkeitszeitraum kann eine der folgenden Optionen festgelegt werden:

* Eine bestimmte Anzahl von Tagen, an denen das Dokument ab der Veröffentlichung des Dokuments verfügbar ist
* Enddatum, nach dem das Dokument nicht mehr verfügbar ist
* Ein bestimmter Datumsbereich, auf den das Dokument zugreifen kann
* Immer gültig

Sie können nur ein Startdatum angeben, was dazu führt, dass die Richtlinie nach dem Startdatum gültig ist. Wenn Sie nur ein Enddatum angeben, ist die Richtlinie bis zum Enddatum gültig. Eine Ausnahme wird jedoch ausgelöst, wenn sowohl ein Start- als auch ein Enddatum nicht definiert sind.

Beim Festlegen von Attributen, die zu einer Richtlinie gehören, können Sie auch Verschlüsselungseinstellungen festlegen. Diese Verschlüsselungseinstellungen wirken sich darauf aus, wenn die Richtlinie auf ein Dokument angewendet wird. Sie können die folgenden Verschlüsselungswerte angeben:

* **AES256**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 256-Bit-Schlüssel dar.
* **AES128**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 128-Bit-Schlüssel dar.
* **NoEncryption:** Stellt keine Verschlüsselung dar.

Bei der Angabe der Option `NoEncryption` können Sie die `PlaintextMetadata`-Option nicht auf `false` setzen. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie in der `Policy` -Schnittstellenbeschreibung in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Einen Richtlinieneintrag erstellen**

Ein Richtlinieneintrag hängt Prinzipale, d. h. Gruppen und Benutzer, sowie Berechtigungen an eine Richtlinie an. Eine Richtlinie muss mindestens einen Richtlinieneintrag enthalten. Nehmen Sie beispielsweise an, dass Sie die folgenden Aufgaben ausführen:

* Erstellen und registrieren Sie einen Richtlinieneintrag, der es einer Gruppe ermöglicht, ein Dokument nur im Online-Modus anzuzeigen, und Empfängern das Kopieren untersagt.
* Hängen Sie den Richtlinieneintrag an die Richtlinie an.
* Sichern Sie ein Dokument mit der Richtlinie mithilfe von Acrobat.

Dadurch können Empfänger das Dokument nur online anzeigen und nicht kopieren. Das Dokument bleibt sicher, bis die Sicherheit entfernt wurde.

**Richtlinie registrieren**

Eine neue Richtlinie muss registriert sein, bevor sie verwendet werden kann. Nachdem Sie eine Richtlinie registriert haben, können Sie sie zum Schutz von Dokumenten verwenden.

### Erstellen Sie eine Richtlinie mit der Java-API {#create-a-policy-using-the-java-api}

Erstellen Sie eine Richtlinie mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie ein `Policy` -Objekt, indem Sie die statische `createPolicy` -Methode des `InfomodelObjectFactory` -Objekts aufrufen. Diese Methode gibt ein `Policy` -Objekt zurück.
   * Legen Sie das Attribut name der Richtlinie fest, indem Sie die Methode `setName` des Objekts `Policy` aufrufen und einen Zeichenfolgenwert übergeben, der den Richtliniennamen angibt.
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie die `setDescription` -Methode des Objekts `Policy` aufrufen und einen Zeichenfolgenwert übergeben, der die Beschreibung der Richtlinie angibt.
   * Legen Sie den Richtliniensatz, zu dem die neue Richtlinie gehört, fest, indem Sie die `setPolicySetName` -Methode des Objekts `Policy` aufrufen und einen string -Wert übergeben, der den Richtliniensatznamen angibt. (Sie können `null` für diesen Parameterwert angeben, wodurch die Richtlinie zum Richtliniensatz *Meine Richtlinien* hinzugefügt wird.)
   * Erstellen Sie die Gültigkeitsdauer der Richtlinie, indem Sie die statische `createValidityPeriod` -Methode des Objekts `InfomodelObjectFactory` aufrufen. Diese Methode gibt ein `ValidityPeriod` -Objekt zurück.
   * Legen Sie die Anzahl der Tage fest, für die auf ein richtliniengeschütztes Dokument zugegriffen werden kann, indem Sie die `setRelativeExpirationDays` -Methode des Objekts `ValidityPeriod` aufrufen und einen ganzzahligen Wert übergeben, der die Anzahl der Tage angibt.
   * Legen Sie die Gültigkeitsdauer der Richtlinie fest, indem Sie die `setValidityPeriod` -Methode des Objekts `Policy` aufrufen und das `ValidityPeriod` -Objekt übergeben.

1. Erstellen Sie einen Richtlinieneintrag.

   * Erstellen Sie einen Richtlinieneintrag, indem Sie die statische `createPolicyEntry` -Methode des Objekts `InfomodelObjectFactory` aufrufen. Diese Methode gibt ein `PolicyEntry` -Objekt zurück.
   * Geben Sie die Berechtigungen der Richtlinie an, indem Sie die statische `createPermission`-Methode des Objekts `InfomodelObjectFactory` aufrufen. Übergeben Sie ein statisches Datenelement, das zur `Permission`-Schnittstelle gehört, die die Berechtigung darstellt. Diese Methode gibt ein `Permission` -Objekt zurück. Um beispielsweise die Berechtigung hinzuzufügen, mit der Benutzer Daten aus einem richtliniengeschützten PDF-Dokument kopieren können, übergeben Sie `Permission.COPY`. (Wiederholen Sie diesen Schritt für jede hinzuzufügende Berechtigung.)
   * Fügen Sie die Berechtigung zum Richtlinieneintrag hinzu, indem Sie die `addPermission` -Methode des Objekts `PolicyEntry` aufrufen und das `Permission` -Objekt übergeben. (Wiederholen Sie diesen Schritt für jedes `Permission`-Objekt, das Sie erstellt haben).
   * Erstellen Sie den Richtlinienprinzipal, indem Sie die statische `createSpecialPrincipal` -Methode des Objekts `InfomodelObjectFactory` aufrufen. Übergeben Sie ein Datenelement, das zum `InfomodelObjectFactory` -Objekt gehört, das den Prinzipal darstellt. Diese Methode gibt ein `Principal` -Objekt zurück. Um beispielsweise den Herausgeber des Dokuments als Prinzipal hinzuzufügen, übergeben Sie `InfomodelObjectFactory.PUBLISHER_PRINCIPAL`.
   * Fügen Sie den Prinzipal zum Richtlinieneintrag hinzu, indem Sie die `setPrincipal`Methode des `PolicyEntry`-Objekts aufrufen und das `Principal`-Objekt übergeben.
   * Fügen Sie den Richtlinieneintrag zur Richtlinie hinzu, indem Sie die `addPolicyEntry` -Methode des Objekts `Policy` aufrufen und das `PolicyEntry` -Objekt übergeben.

1. Registrieren Sie die Richtlinie.

   * Erstellen Sie ein `PolicyManager` -Objekt, indem Sie die `getPolicyManager` -Methode des Objekts `DocumentSecurityClient` aufrufen.
   * Registrieren Sie die Richtlinie, indem Sie die `registerPolicy` -Methode des `PolicyManager` -Objekts aufrufen und die folgenden Werte übergeben:

      * Das `Policy`-Objekt, das die zu registrierende Richtlinie darstellt.
   * Ein string -Wert für den Richtliniensatz, zu dem die Richtlinie gehört.

   Wenn Sie in den Verbindungseinstellungen ein AEM Forms-Administratorkonto zum Erstellen des `DocumentSecurityClient`-Objekts verwenden, geben Sie beim Aufrufen der `registerPolicy`-Methode den Richtliniensatznamen an. Wenn Sie den Wert `null` für den Richtliniensatz übergeben, wird die Richtlinie im Richtliniensatz *Meine Richtlinien* für die Administratoren erstellt.

   Wenn Sie einen Document Security-Benutzer in den Verbindungseinstellungen verwenden, können Sie die überladene `registerPolicy`-Methode aufrufen, die nur die Richtlinie akzeptiert. Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch zum Richtliniensatz *Meine Richtlinien* hinzugefügt. Wenn Sie diesem Richtliniensatz die neue Richtlinie nicht hinzufügen möchten, geben Sie beim Aufrufen der `registerPolicy`-Methode einen Richtliniensatznamen an.

   >[!NOTE]
   >
   >Referenzieren Sie beim Erstellen einer Richtlinie einen vorhandenen Richtliniensatz. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie unter folgenden Themen:

* &quot;Schnellstart (SOAP-Modus): Erstellen einer Richtlinie mit der Java-API&quot;

### Erstellen Sie eine Richtlinie mithilfe der Webdienst-API {#create-a-policy-using-the-web-service-api}

Erstellen Sie eine Richtlinie mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `RightsManagementServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie ein Objekt `PolicySpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Namen der Richtlinie fest, indem Sie dem `name`-Datenelement des `PolicySpec`-Objekts einen Zeichenfolgenwert zuweisen.
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie dem `description`-Datenelement des `PolicySpec`-Objekts einen Zeichenfolgenwert zuweisen.
   * Legen Sie den Richtliniensatz fest, zu dem die Richtlinie gehören soll, indem Sie dem `policySetName` -Datenelement des Objekts `PolicySpec` einen Zeichenfolgenwert zuweisen. Sie müssen einen vorhandenen Richtliniensatznamen angeben. (Sie können `null` für diesen Parameterwert angeben, wodurch die Richtlinie *Meine Richtlinien* hinzugefügt wird.)
   * Legen Sie die Offline-Nutzungsdauer der Richtlinie fest, indem Sie dem `offlineLeasePeriod` -Datenelement des `PolicySpec` -Objekts einen ganzzahligen Wert zuweisen.
   * Legen Sie das `PolicySpec`-Datenelement des `policyXml`-Objekts mit einem Zeichenfolgenwert fest, der die PDRL-XML-Daten darstellt. Erstellen Sie dazu ein .NET `StreamReader` -Objekt mit dessen Konstruktor. Übergeben Sie den Speicherort einer PDRL-XML-Datei, die die Richtlinie darstellt, an den Konstruktor `StreamReader` . Rufen Sie als Nächstes die `ReadLine` -Methode des Objekts auf und weisen Sie den Rückgabewert einer Zeichenfolgenvariablen zu. `StreamReader` Iterieren Sie durch das `StreamReader`-Objekt, bis die `ReadLine`-Methode null zurückgibt. Weisen Sie die Zeichenfolgenvariable dem `policyXml` -Datenelement des `PolicySpec` -Objekts zu.

1. Erstellen Sie einen Richtlinieneintrag.

   Es ist nicht erforderlich, beim Erstellen einer Richtlinie mithilfe der Document Security-Webdienst-API einen Richtlinieneintrag zu erstellen. Der Richtlinieneintrag wird im PDRL-Dokument definiert.

1. Registrieren Sie die Richtlinie.

   Registrieren Sie die Richtlinie, indem Sie die `registerPolicy` -Methode des `DocumentSecurityServiceClient` -Objekts aufrufen und die folgenden Werte übergeben:

   * Das `PolicySpec`-Objekt, das die zu registrierende Richtlinie darstellt.
   * Ein string -Wert für den Richtliniensatz, zu dem die Richtlinie gehört. Sie können einen `null`-Wert angeben, der dazu führt, dass die Richtlinie zum Richtliniensatz *MyPolies* hinzugefügt wird.

   Wenn Sie in den Verbindungseinstellungen ein AEM Forms-Administratorkonto zum Erstellen des `DocumentSecurityClient`-Objekts verwenden, geben Sie beim Aufrufen der `registerPolicy`-Methode den Richtliniensatznamen an.

   Wenn Sie einen Document Security Document Security-Benutzer in den Verbindungseinstellungen verwenden, können Sie die überladene `registerPolicy`-Methode aufrufen, die nur die Richtlinie akzeptiert. Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch zum Richtliniensatz *Meine Richtlinien* hinzugefügt. Wenn Sie diesem Richtliniensatz die neue Richtlinie nicht hinzufügen möchten, geben Sie beim Aufrufen der `registerPolicy`-Methode einen Richtliniensatznamen an.

   >[!NOTE]
   >
   >Stellen Sie beim Erstellen einer Richtlinie und beim Angeben eines Richtliniensatzes sicher, dass Sie einen vorhandenen Richtliniensatz angeben. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Erstellen einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Erstellen einer Richtlinie mithilfe der Webdienst-API&quot;

## Ändern von Richtlinien {#modifying-policies}

Sie können eine vorhandene Richtlinie mit der Document Security Java-API oder der Web Service-API ändern. Um Änderungen an einer vorhandenen Richtlinie vorzunehmen, rufen Sie sie ab, ändern Sie sie und aktualisieren Sie dann die Richtlinie auf dem Server. Angenommen, Sie rufen eine vorhandene Richtlinie ab und verlängern ihre Gültigkeitsdauer. Bevor die Änderung wirksam wird, müssen Sie die Richtlinie aktualisieren.

Sie können eine Richtlinie ändern, wenn sich die Geschäftsanforderungen ändern und die Richtlinie diese Anforderungen nicht mehr widerspiegelt. Anstatt eine neue Richtlinie zu erstellen, können Sie einfach eine vorhandene Richtlinie aktualisieren.

Um Richtlinienattribute mithilfe eines Webdiensts zu ändern (z. B. mithilfe von Java-Proxy-Klassen, die mit JAX-WS erstellt wurden), müssen Sie sicherstellen, dass die Richtlinie beim Document Security-Dienst registriert ist. Anschließend können Sie mithilfe der `PolicySpec.getPolicyXml`-Methode auf die vorhandene Richtlinie verweisen und die Richtlinienattribute mithilfe der entsprechenden Methoden ändern. Sie können beispielsweise die Offline-Nutzungsdauer ändern, indem Sie die Methode `PolicySpec.setOfflineLeasePeriod` aufrufen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

Um eine vorhandene Richtlinie zu ändern, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Abrufen einer vorhandenen Richtlinie.
1. Richtlinienattribute ändern.
1. Aktualisieren Sie die Richtlinie.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` -Objekt.

**Vorhandene Richtlinie abrufen**

Sie müssen eine vorhandene Richtlinie abrufen, um sie zu ändern. Um eine Richtlinie abzurufen, geben Sie den Richtliniennamen und den Richtliniensatz an, zu dem die Richtlinie gehört. Wenn Sie einen `null` -Wert für den Richtliniensatznamen angeben, wird die Richtlinie aus dem Richtliniensatz *Meine Richtlinien* abgerufen.

**Festlegen der Richtlinienattribute**

Um eine Richtlinie zu ändern, ändern Sie den Wert von Richtlinienattributen. Das einzige Richtlinienattribut, das Sie nicht ändern können, ist das Attribut name . Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, können Sie den Wert des Attributs für die Offline-Nutzungsdauer der Richtlinie ändern.

Wenn Sie die Offline-Nutzungsdauer einer Richtlinie mithilfe eines Webdiensts ändern, wird das Feld `offlineLeasePeriod` auf der `PolicySpec`-Benutzeroberfläche ignoriert. Um die Offline-Nutzungsdauer zu aktualisieren, ändern Sie das Element `OfflineLeasePeriod` im XML-Dokument PDRL . Verweisen Sie anschließend mithilfe des `PolicySpec`-Datenelements der `policyXML`-Schnittstelle auf das aktualisierte PDF-XML-Dokument.

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie in der `Policy` -Schnittstellenbeschreibung in der [AEM Forms API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Richtlinie aktualisieren**

Bevor die Änderungen, die Sie an einer Richtlinie vornehmen, wirksam werden, müssen Sie die Richtlinie mit dem Document Security-Dienst aktualisieren. Änderungen an Richtlinien, die Dokumente schützen, werden aktualisiert, wenn das richtliniengeschützte Dokument das nächste Mal mit dem Document Security-Dienst synchronisiert wird.

### Ändern vorhandener Richtlinien mithilfe der Java-API {#modify-existing-policies-using-the-java-api}

Ändern Sie eine vorhandene Richtlinie mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen einer vorhandenen Richtlinie.

   * Erstellen Sie ein `PolicyManager` -Objekt, indem Sie die `getPolicyManager` -Methode des Objekts `RightsManagementClient` aufrufen.
   * Erstellen Sie ein `Policy` -Objekt, das die zu aktualisierende Richtlinie darstellt, indem Sie die `getPolicy` -Methode des Objekts `PolicyManager` aufrufen und die folgenden Werte übergeben.

      * Ein string -Wert, der den Richtliniensatznamen darstellt, zu dem die Richtlinie gehört. Sie können `null` angeben, sodass der `MyPolicies`-Richtliniensatz verwendet wird.
      * Ein string -Wert, der den Richtliniennamen darstellt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen. Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, rufen Sie die `setOfflineLeasePeriod` -Methode des Objekts `Policy` auf.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren Sie die Richtlinie, indem Sie die `updatePolicy` -Methode des Objekts `PolicyManager` aufrufen. Übergeben Sie das `Policy`-Objekt, das die zu aktualisierende Richtlinie darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie im Schnellstart-Modus (SOAP-Modus): Ändern einer Richtlinie mithilfe des Abschnitts Java-API .

### Ändern vorhandener Richtlinien mithilfe der Webdienst-API {#modify-existing-policies-using-the-web-service-api}

Ändern Sie eine vorhandene Richtlinie mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `RightsManagementServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Abrufen einer vorhandenen Richtlinie.

   Erstellen Sie ein `PolicySpec` -Objekt, das die zu ändernde Richtlinie darstellt, indem Sie die `getPolicy` -Methode des Objekts `RightsManagementServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein string -Wert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` angeben, sodass der `MyPolicies`-Richtliniensatz verwendet wird.
   * Ein string -Wert, der den Namen der Richtlinie angibt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren Sie die Richtlinie, indem Sie die `updatePolicyFromSDK` -Methode des `RightsManagementServiceClient` -Objekts aufrufen und das `PolicySpec` -Objekt übergeben, das die zu aktualisierende Richtlinie darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Ändern einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Ändern einer Richtlinie mithilfe der Webdienst-API&quot;

## Löschen von Richtlinien {#deleting-policies}

Sie können eine vorhandene Richtlinie mithilfe der Document Security Java-API oder der Web Service-API löschen. Nachdem eine Richtlinie gelöscht wurde, kann sie nicht mehr zum Schutz von Dokumenten verwendet werden. Vorhandene richtliniengeschützte Dokumente, die die Richtlinie verwenden, sind jedoch weiterhin geschützt. Sie können eine Richtlinie löschen, wenn eine neuere verfügbar ist.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

Um eine vorhandene Richtlinie zu löschen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Löschen Sie die Richtlinie.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` -Objekt.

**Richtlinie löschen**

Um eine Richtlinie zu löschen, geben Sie die zu löschende Richtlinie und den Richtliniensatz an, zu dem die Richtlinie gehört. Der Benutzer, dessen Einstellungen zum Aufrufen von AEM Forms verwendet werden, muss über die Berechtigung zum Löschen der Richtlinie verfügen. andernfalls tritt eine Ausnahme auf. Wenn Sie versuchen, eine nicht vorhandene Richtlinie zu löschen, tritt ebenfalls eine Ausnahme auf.

### Richtlinien mithilfe der Java-API löschen {#delete-policies-using-the-java-api}

Löschen Sie eine Richtlinie mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Löschen Sie die Richtlinie.

   * Erstellen Sie ein `PolicyManager` -Objekt, indem Sie die `getPolicyManager` -Methode des Objekts `RightsManagementClient` aufrufen.
   * Löschen Sie die Richtlinie, indem Sie die `deletePolicy` -Methode des Objekts `PolicyManager` aufrufen und die folgenden Werte übergeben:

      * Ein string -Wert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` angeben, sodass der `MyPolicies`-Richtliniensatz verwendet wird.
      * Ein string -Wert, der den Namen der zu löschenden Richtlinie angibt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Löschen einer Richtlinie mithilfe der Java-API&quot;

### Richtlinien mithilfe der Webdienst-API löschen {#delete-policies-using-the-web-service-api}

Löschen Sie eine Richtlinie mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `RightsManagementServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Löschen Sie die Richtlinie.

   Löschen Sie eine Richtlinie, indem Sie die `deletePolicy` -Methode des Objekts `RightsManagementServiceClient` aufrufen und die folgenden Werte übergeben:

   * Ein string -Wert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können `null` angeben, sodass der `MyPolicies`-Richtliniensatz verwendet wird.
   * Ein string -Wert, der den Namen der zu löschenden Richtlinie angibt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Löschen einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Löschen einer Richtlinie mithilfe der Webdienst-API&quot;

## Anwenden von Richtlinien auf PDF-Dokumente {#applying-policies-to-pdf-documents}

Sie können eine Richtlinie auf ein PDF-Dokument anwenden, um das Dokument zu schützen. Durch Anwendung einer Richtlinie auf ein PDF-Dokument können Sie den Zugriff auf das Dokument einschränken. Sie können eine Richtlinie nicht auf ein Dokument anwenden, wenn das Dokument bereits mit einer Richtlinie gesichert ist.

Während das Dokument geöffnet ist, können Sie auch den Zugriff auf Acrobat- und Adobe Reader-Funktionen einschränken, einschließlich der Möglichkeit, Text zu drucken und zu kopieren, Änderungen vorzunehmen und Signaturen und Kommentare zu einem Dokument hinzuzufügen. Darüber hinaus können Sie ein richtliniengeschütztes PDF-Dokument sperren, wenn Benutzer nicht mehr auf das Dokument zugreifen sollen.

Sie können die Verwendung eines richtliniengeschützten Dokuments nach dessen Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So wenden Sie eine Richtlinie auf ein PDF-Dokument an:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument ab, auf das eine Richtlinie angewendet wird.
1. Anwenden einer vorhandenen Richtlinie auf das PDF-Dokument.
1. Speichern Sie das richtliniengeschützte PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` -Objekt.

**Abrufen eines PDF-Dokuments**

Sie können ein PDF-Dokument abrufen, um eine Richtlinie anzuwenden. Nachdem Sie eine Richtlinie auf das PDF-Dokument angewendet haben, sind Benutzer bei der Verwendung des Dokuments eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offline-Modus aktiviert, müssen die Benutzer online sein, um das Dokument zu öffnen.

**Anwenden einer vorhandenen Richtlinie auf das PDF-Dokument**

Um eine Richtlinie auf ein PDF-Dokument anzuwenden, verweisen Sie auf eine vorhandene Richtlinie und geben Sie an, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften festlegt, muss Zugriff auf die angegebene Richtlinie haben. Wenn nicht, tritt eine Ausnahme auf.

**PDF-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie auf ein PDF-Dokument angewendet hat, können Sie das richtliniengeschützte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API {#apply-a-policy-to-a-pdf-document-using-the-java-api}

Wenden Sie mithilfe der Document Security-API (Java) eine Richtlinie auf ein PDF-Dokument an:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das PDF-Dokument mithilfe des zugehörigen Konstruktors darstellt. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Anwenden einer vorhandenen Richtlinie auf das PDF-Dokument.

   * Erstellen Sie ein `DocumentManager` -Objekt, indem Sie die `getDocumentManager` -Methode des Objekts `RightsManagementClient` aufrufen.
   * Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `protectDocument` -Methode des Objekts `DocumentManager` aufrufen und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document`-Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Ein string -Wert, der den Namen des Dokuments angibt.
      * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` -Wert angeben, der dazu führt, dass der `MyPolicies`-Richtliniensatz verwendet wird.
      * Ein string -Wert, der den Richtliniennamen angibt.
      * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert null sein.)
      * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null` sein.)
      * Ein `com.adobe.livecycle.rightsmanagement.Locale` -Gebietsschema, das für die Auswahl der MS Office-Vorlage verwendet wird. Dieser Parameterwert ist optional und wird nicht für PDF-Dokumente verwendet. Um ein PDF-Dokument zu sichern, geben Sie `null` an.

      Die `protectDocument`-Methode gibt ein `RMSecureDocumentResult`-Objekt zurück, das das richtliniengeschützte PDF-Dokument enthält.


1. Speichern Sie das PDF-Dokument.

   * Rufen Sie die `getProtectedDoc`-Methode des Objekts `RMSecureDocumentResult` auf, um das richtliniengeschützte PDF-Dokument abzurufen. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück.
   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateierweiterung PDF ist.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `getProtectedDoc` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (EJB-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API&quot;
* &quot;Schnellstart (SOAP-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API&quot;

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API {#apply-a-policy-to-a-pdf-document-using-the-web-service-api}

Wenden Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie auf ein PDF-Dokument an:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `RightsManagementServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Rufen Sie ein PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines PDF-Dokuments verwendet, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Bestimmen Sie die Größe des Byte-Arrays, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Anwenden einer vorhandenen Richtlinie auf das PDF-Dokument.

   Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `protectDocument` -Methode des Objekts `RightsManagementServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Ein string -Wert, der den Namen des Dokuments angibt.
   * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` -Wert angeben, der dazu führt, dass der `MyPolicies`-Richtliniensatz verwendet wird.
   * Ein string -Wert, der den Richtliniennamen angibt.
   * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert `null` sein.)
   * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null` sein.)
   * Ein `RMLocale` -Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein string -Ausgabeparameter, der zum Speichern des Richtlinienkennungswerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des richtliniengeschützten Bezeichnerwerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des MIME-Typs verwendet wird (z. B. `application/pdf`).

   Die `protectDocument`-Methode gibt ein `BLOB`-Objekt zurück, das das richtliniengeschützte PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des richtliniengeschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `protectDocument` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API&quot;

## Entfernen von Richtlinien aus PDF-Dokumenten {#removing-policies-from-pdf-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, wenn das Dokument nicht mehr durch eine Richtlinie geschützt werden soll. Wenn Sie ein richtliniengeschütztes Dokument mit einer neueren Richtlinie aktualisieren möchten, ist es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entfernen Sie eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Abrufen eines richtliniengeschützten PDF-Dokuments.
1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.
1. Speichern Sie das ungesicherte PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Sie können ein richtliniengeschütztes PDF-Dokument abrufen, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem PDF-Dokument zu entfernen, das nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme verursacht.

**Richtlinie aus dem PDF-Dokument entfernen**

Sie können eine Richtlinie aus einem richtliniengeschützten PDF-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Andernfalls muss die zum Schützen eines Dokuments verwendete Richtlinie die Berechtigung `SWITCH_POLICY` enthalten, damit eine Richtlinie aus einem PDF-Dokument entfernt werden kann. Außerdem muss der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Ungesichertes PDF-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie aus einem PDF-Dokument entfernt hat, können Sie das ungesicherte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Eine Richtlinie mithilfe der Java-API {#remove-a-policy-from-a-pdf-document-using-the-java-api} aus einem PDF-Dokument entfernen

Entfernen Sie mithilfe der Document Security-API (Java) eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten PDF-Dokuments.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   * Erstellen Sie ein `DocumentManager` -Objekt, indem Sie die `getDocumentManager` -Methode des Objekts `DocumentSecurityClient` aufrufen.
   * Entfernen Sie eine Richtlinie aus dem PDF-Dokument, indem Sie die `removeSecurity`-Methode des Objekts `DocumentManager` aufrufen und das `com.adobe.idp.Document`-Objekt übergeben, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das ungesicherte PDF-Dokument.

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateierweiterung PDF ist.
   * Rufen Sie die `copyToFile` -Methode des `Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `removeSecurity` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Java-API&quot;

### Eine Richtlinie mithilfe der Webdienst-API {#remove-a-policy-using-the-web-service-api} entfernen

Entfernen Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DocumentSecurityServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Abrufen eines richtliniengeschützten PDF-Dokuments.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des richtliniengeschützten PDF-Dokuments verwendet, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   Entfernen Sie die Richtlinie aus dem PDF-Dokument, indem Sie die `removePolicySecurity`-Methode des Objekts `DocumentSecurityServiceClient` aufrufen und das `BLOB`-Objekt übergeben, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `BLOB` -Objekt zurück, das ein nicht gesichertes PDF-Dokument enthält.

1. Speichern Sie das ungesicherte PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des ungesicherten PDF-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `removePolicySecurity` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zugriff auf Dokumente sperren {#revoking-access-to-documents}

Sie können den Zugriff auf ein richtliniengeschütztes PDF-Dokument sperren, sodass alle Kopien des Dokuments für Benutzer nicht zugänglich sind. Wenn ein Benutzer versucht, ein gesperrtes PDF-Dokument zu öffnen, wird er an eine angegebene URL umgeleitet, wo ein überarbeitetes Dokument angezeigt werden kann. Die URL, an die der Benutzer umgeleitet wird, muss programmatisch angegeben werden. Wenn Sie den Zugriff auf ein Dokument sperren, wird die Änderung wirksam, wenn sich der Benutzer das nächste Mal mit dem Document Security-Dienst synchronisiert, indem er das richtliniengeschützte Dokument online öffnet.

Die Möglichkeit, den Zugriff auf ein Dokument zu sperren, bietet zusätzliche Sicherheit. Angenommen, eine neuere Version eines Dokuments ist verfügbar, und Sie möchten nicht mehr, dass jemand die veraltete Version anzeigt. In diesem Fall kann der Zugriff auf das ältere Dokument widerrufen werden und niemand kann das Dokument anzeigen, es sei denn, der Zugriff wird wieder aktiviert.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

Um ein richtliniengeschütztes Dokument zu sperren, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Abrufen eines richtliniengeschützten PDF-Dokuments.
1. Sperren Sie das richtliniengeschützte Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Sie müssen ein richtliniengeschütztes PDF-Dokument abrufen, um es zu widerrufen. Sie können ein Dokument, das bereits gesperrt wurde oder nicht richtliniengeschützt ist, nicht sperren.

Wenn Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments kennen, ist es nicht erforderlich, das richtliniengeschützte PDF-Dokument abzurufen. In den meisten Fällen müssen Sie jedoch das PDF-Dokument abrufen, um den Wert der Lizenzkennung zu erhalten.

**Richtliniengeschütztes Dokument sperren**

Um ein richtliniengeschütztes Dokument zu sperren, geben Sie die Lizenzkennung des richtliniengeschützten Dokuments an. Darüber hinaus können Sie die URL eines Dokuments angeben, das der Benutzer anzeigen kann, wenn er versucht, das gesperrte Dokument zu öffnen. Angenommen, ein veraltetes Dokument wird widerrufen. Wenn ein Benutzer versucht, das gesperrte Dokument zu öffnen, wird ihm anstelle des gesperrten Dokuments ein aktualisiertes Dokument angezeigt.

>[!NOTE]
>
>Wenn Sie versuchen, ein bereits gesperrtes Dokument zu widerrufen, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Neuer Zugriff auf gesperrte Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents)

### Zugriff auf Dokumente mithilfe der Java-API sperren {#revoke-access-to-documents-using-the-java-api}

Sperren Sie den Zugriff auf ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security-API (Java):

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Richtliniengeschütztes Dokument sperren

   * Erstellen Sie ein `DocumentManager` -Objekt, indem Sie die `getDocumentManager` -Methode des Objekts `DocumentSecurityClient` aufrufen.
   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `getLicenseId` -Methode des Objekts `DocumentManager` aufrufen. Übergeben Sie das `com.adobe.idp.Document`-Objekt, das das richtliniengeschützte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Lizenzkennung darstellt.
   * Erstellen Sie ein `LicenseManager` -Objekt, indem Sie die `getLicenseManager` -Methode des Objekts `DocumentSecurityClient` aufrufen.
   * Rufen Sie das richtliniengeschützte Dokument auf, indem Sie die `revokeLicense` -Methode des Objekts `LicenseManager` aufrufen und die folgenden Werte übergeben:

      * Ein string -Wert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert der `DocumentManager` -Methode des Objekts `getLicenseId` an).
      * Ein statisches Datenelement der `License`-Schnittstelle, das den Grund zum Sperren des Dokuments angibt. Sie können beispielsweise `License.DOCUMENT_REVISED` angeben.
      * Ein `java.net.URL` -Wert, der den Speicherort angibt, an dem sich ein überarbeitetes Dokument befindet. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie `null` übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Aufrufen eines Dokuments mithilfe der Java-API&quot;

### Sperren des Zugriffs auf Dokumente mithilfe der Webdienst-API {#revoke-access-to-documents-using-the-web-service-api}

Rufen Sie mithilfe der Document Security-API (Webdienst) den Zugriff auf ein richtliniengeschütztes PDF-Dokument auf:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DocumentSecurityServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines richtliniengeschützten PDF-Dokuments verwendet, das gesperrt ist.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des zu widerrufenden richtliniengeschützten PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Richtliniengeschütztes Dokument sperren

   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `getLicenseID` -Methode des Objekts `DocumentSecurityServiceClient` aufrufen und das `BLOB` -Objekt übergeben, das das richtliniengeschützte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Rufen Sie das richtliniengeschützte Dokument auf, indem Sie die `revokeLicense` -Methode des Objekts `DocumentSecurityServiceClient` aufrufen und die folgenden Werte übergeben:

      * Ein string -Wert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert der `DocumentSecurityServiceService` -Methode des Objekts `getLicenseId` an).
      * Ein statisches Datenelement der Enum `Reason` , das den Grund für das Sperren des Dokuments angibt. Sie können beispielsweise `Reason.DOCUMENT_REVISED` angeben.
      * Ein `string` -Wert, der den URL-Speicherort angibt, an dem sich ein überarbeitetes Dokument befindet. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie `null` übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Sperren eines Dokuments mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Sperren eines Dokuments mithilfe der Webdienst-API&quot;

**Siehe auch**

[Entfernen von Richtlinien aus Word-Dokumenten](protecting-documents-policies.md#removing-policies-from-word-documents)

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Neuer Zugriff auf gesperrte Dokumente {#reinstating-access-to-revoked-documents}

Sie können den Zugriff auf ein gesperrtes PDF-Dokument reaktivieren, sodass alle Kopien des gesperrten Dokuments für Benutzer zugänglich sind. Wenn ein Benutzer ein reaktiviertes Dokument öffnet, das widerrufen wurde, kann er das Dokument anzeigen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

Führen Sie die folgenden Schritte aus, um den Zugriff auf ein gesperrtes PDF-Dokument wiederherzustellen:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.
1. Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` -Objekt.

**Lizenzkennung des gesperrten PDF-Dokuments abrufen**

Sie müssen die Lizenzkennung des gesperrten PDF-Dokuments abrufen, um ein gesperrtes PDF-Dokument erneut zu aktivieren. Nachdem Sie den Wert der Lizenzkennung erhalten haben, können Sie ein gesperrtes Dokument erneut aktivieren. Wenn Sie versuchen, ein Dokument erneut zu aktivieren, das nicht gesperrt ist, wird eine Ausnahme verursacht.

**Zugriff auf das gesperrte PDF-Dokument reaktivieren**

Um den Zugriff auf ein gesperrtes PDF-Dokument erneut zu aktivieren, müssen Sie die Lizenzkennung des gesperrten Dokuments angeben. Wenn Sie versuchen, den Zugriff auf ein nicht widerrufenes PDF-Dokument erneut zu aktivieren, wird eine Ausnahme verursacht.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Zugriff auf gesperrte Dokumente mit der Java-API {#reinstate-access-to-revoked-documents-using-the-java-api} reaktivieren

Reaktivieren Sie den Zugriff auf ein gesperrtes Dokument mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das gesperrte PDF-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `DocumentManager` -Objekt, indem Sie die `getDocumentManager` -Methode des Objekts `DocumentSecurityClient` aufrufen.
   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `getLicenseId` -Methode des Objekts `DocumentManager` aufrufen und das `com.adobe.idp.Document` -Objekt übergeben, das das gesperrte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.

1. Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument.

   * Erstellen Sie ein `LicenseManager` -Objekt, indem Sie die `getLicenseManager` -Methode des Objekts `DocumentSecurityClient` aufrufen.
   * Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument, indem Sie die `unrevokeLicense`-Methode des Objekts `LicenseManager` aufrufen und den Wert der Lizenzkennung des gesperrten Dokuments übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Zugriff auf ein gesperrtes Dokument mit der Web-Dienst-API reaktivieren&quot;

### Zugriff auf gesperrte Dokumente mithilfe der Webdienst-API {#reinstate-access-to-revoked-documents-using-the-web-service-api} reaktivieren

Reaktivieren Sie den Zugriff auf ein gesperrtes Dokument mithilfe der Document Security API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DocumentSecurityServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines gesperrten PDF-Dokuments verwendet, auf das der Zugriff reaktiviert wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des gesperrten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument.

   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `getLicenseID` -Methode des Objekts `DocumentSecurityServiceClient` aufrufen und das `BLOB` -Objekt übergeben, das das gesperrte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Reaktivieren Sie den Zugriff auf das gesperrte PDF-Dokument, indem Sie die `unrevokeLicense` -Methode des Objekts `DocumentSecurityServiceClient` aufrufen und einen Zeichenfolgenwert übergeben, der den Lizenzkennungswert des gesperrten PDF-Dokuments angibt (übergeben Sie den Rückgabewert der `DocumentSecurityServiceClient` -Methode des Objekts `getLicenseId`).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Zugriff auf ein gesperrtes Dokument mit der Web-Dienst-API reaktivieren&quot;
* &quot;Schnellstart (SwaRef): Zugriff auf ein gesperrtes Dokument mit der Web-Dienst-API reaktivieren&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Überprüfen von richtliniengeschützten PDF-Dokumenten {#inspecting-policy-protected-pdf-documents}

Sie können die Document Security Service-API (Java- und Webdienst) verwenden, um richtliniengeschützte PDF-Dokumente zu überprüfen. Beim Überprüfen richtliniengeschützter PDF-Dokumente werden Informationen zum richtliniengeschützten PDF-Dokument zurückgegeben. Sie können beispielsweise die Richtlinie bestimmen, die zum Schützen des Dokuments verwendet wurde, sowie das Datum, an dem das Dokument gesichert wurde.

Sie können diese Aufgabe nicht ausführen, wenn Ihre LiveCycle-Version 8.x oder eine frühere Version ist. In AEM Forms wird die Überprüfung richtliniengeschützter Dokumente unterstützt. Wenn Sie versuchen, ein richtliniengeschütztes Dokument mit LiveCycle 8.x (oder früher) zu überprüfen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

So prüfen Sie ein richtliniengeschütztes PDF-Dokument:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.
1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` -Objekt.

**Abrufen eines richtliniengeschützten Dokuments zum Überprüfen**

Rufen Sie ein richtliniengeschütztes Dokument ab, um es zu überprüfen. Wenn Sie versuchen, ein Dokument zu überprüfen, das nicht mit einer Richtlinie gesichert ist oder gesperrt ist, wird eine Ausnahme ausgelöst.

**Inspect des Dokuments**

Nachdem Sie ein richtliniengeschütztes Dokument abgerufen haben, können Sie es überprüfen.

**Informationen zum richtliniengeschützten Dokument abrufen**

Nachdem Sie ein richtliniengeschütztes PDF-Dokument geprüft haben, können Sie Informationen dazu abrufen. Sie können beispielsweise die Richtlinie bestimmen, die zum Schützen des Dokuments verwendet wird.

Wenn Sie ein Dokument mit einer Richtlinie sichern, die zu &quot;Meine Richtlinien&quot;gehört, und dann `RMInspectResult.getPolicysetName` oder `RMInspectResult.getPolicysetId` aufrufen, wird null zurückgegeben.

Wenn das Dokument mit einer Richtlinie gesichert wird, die in einem Richtliniensatz (außer &quot;Meine Richtlinien&quot;) enthalten ist, geben `RMInspectResult.getPolicysetName` und `RMInspectResult.getPolicysetId` gültige Zeichenfolgen zurück.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Inspect Policy Protected PDF Documents using the Java API {#inspect-policy-protected-pdf-documents-using-the-java-api}

Inspect ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security Service-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-rightsmanagement-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte PDF-Dokument mithilfe seines Konstruktors darstellt. Übergeben Sie einen string -Wert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Inspect das Dokument.

   * Erstellen Sie ein `DocumentManager` -Objekt, indem Sie die `getDocumentManager` -Methode des Objekts `RightsManagementClient` aufrufen.
   * Inspect das richtliniengeschützte Dokument durch Aufrufen der `inspectDocument` -Methode des Objekts `LicenseManager`. Übergeben Sie das `com.adobe.idp.Document`-Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `RMInspectResult` -Objekt zurück, das Informationen zum richtliniengeschützten Dokument enthält.

1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

   Um Informationen zum richtliniengeschützten Dokument zu erhalten, rufen Sie die entsprechende Methode auf, die zum `RMInspectResult` -Objekt gehört. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie die `getPolicyName` -Methode des Objekts `RMInspectResult` auf.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Überprüfen richtliniengeschützter PDF-Dokumente mit der Java-API&quot;

### Inspect Policy Protected PDF Documents using the web service API {#inspect-policy-protected-pdf-documents-using-the-web-service-api}

Inspect ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security Service-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `RightsManagementServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Rufen Sie ein richtliniengeschütztes Dokument zum Überprüfen ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines zu prüfenden PDF-Dokuments verwendet.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen. Übergeben Sie einen string -Wert, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die Stream-Länge zum Lesen.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Inspect das Dokument.

   Inspect das richtliniengeschützte Dokument durch Aufrufen der `inspectDocument` -Methode des Objekts `RightsManagementServiceClient`. Übergeben Sie das `BLOB`-Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `RMInspectResult` -Objekt zurück, das Informationen zum richtliniengeschützten Dokument enthält.

1. Erhalten Sie Informationen zum richtliniengeschützten Dokument.

   Um Informationen zum richtliniengeschützten Dokument zu erhalten, rufen Sie den Wert des entsprechenden Felds ab, das zum `RMInspectResult` -Objekt gehört. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie den Wert des Felds `RMInspectResult` des Objekts `policyName` ab.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Untersuchen richtliniengeschützter PDF-Dokumente mit der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Untersuchen richtliniengeschützter PDF-Dokumente mit der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Erstellen von Wasserzeichen {#creating-watermarks}

Wasserzeichen tragen dazu bei, die Sicherheit eines Dokuments zu gewährleisten, indem sie das Dokument eindeutig identifizieren und die Verletzung des Urheberrechts kontrollieren. Sie können beispielsweise ein Wasserzeichen mit dem Status &quot;Vertraulich&quot;auf allen Seiten eines Dokuments erstellen und platzieren. Nachdem ein Wasserzeichen erstellt wurde, können Sie es als Teil einer Richtlinie einbeziehen. Das heißt, Sie können das Wasserzeichenattribut der Richtlinie mit dem neu erstellten Wasserzeichen festlegen. Nachdem eine Richtlinie, die ein Wasserzeichen enthält, auf ein Dokument angewendet wurde, wird das Wasserzeichen im richtliniengeschützten Dokument angezeigt.

>[!NOTE]
>
>Nur Benutzer mit Administratorrechten für Document Security können Wasserzeichen erstellen. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Client-Objekts des Document Security-Dienstes erforderlich sind.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

Gehen Sie wie folgt vor, um ein Wasserzeichen zu erstellen:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Legen Sie die Wasserzeichenattribute fest.
1. Registrieren Sie das Wasserzeichen beim Document Security-Dienst.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` -Objekt.

**Festlegen der Wasserzeichenattribute**

Um ein neues Wasserzeichen zu erstellen, müssen Sie Wasserzeichenattribute festlegen. Das Attribut name muss immer definiert sein. Zusätzlich zum Attribut name müssen Sie mindestens eines der folgenden Attribute festlegen:

* Benutzerdefinierter Text
* DateIncluded
* UserIdIncluded
* UserNameIncluded

In der folgenden Tabelle sind Schlüssel-Wert-Paare aufgeführt, die zum Erstellen eines Wasserzeichens mit Webdiensten erforderlich sind.

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
   <td><p>Wenn dieser Wert wahr ist, muss der Wert des benutzerdefinierten Texts mit <code>WaterBackCmd:SRCTEXT</code> angegeben werden.</p></td>
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
   <td><p>Wenn dieser Wert angegeben ist, muss <code>WaterBackCmd:IS_SIZE_ENABLED</code> vorhanden sein und der Wert muss "true"lauten. Wenn dieses Attribut nicht angegeben ist, passt das Standardverhalten zur Seite.</p></td>
   <td><p>Ein Wert größer als 0.0 und kleiner gleich 1.0.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:HORIZ_ALIGN</code></p></td>
   <td><p>Gibt die horizontale Ausrichtung des Wasserzeichens an. Der Standardwert ist "center".</p></td>
   <td><p>links, zentriert oder rechts</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:VERT_ALIGN</code></p></td>
   <td><p>Gibt die vertikale Ausrichtung des Wasserzeichens an. Der Standardwert ist "center".</p></td>
   <td><p>oben, zentriert oder unten</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_USE_BACKGROUND</code></p></td>
   <td><p>Gibt an, ob das Wasserzeichen ein Hintergrund ist. Der Standardwert lautet false.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_SIZE_ENABLED</code></p></td>
   <td><p>True , wenn eine benutzerdefinierte Skala angegeben ist. Wenn dieser Wert "true"ist, muss auch "SCALE"angegeben werden. Wenn dieser Wert false ist, passt der Standardwert zur Seite.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:SRCTEXT</code></p></td>
   <td><p>Gibt den benutzerdefinierten Text für ein Wasserzeichen an. Wenn dieser Wert vorhanden ist, muss <code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code> ebenfalls vorhanden und auf "true"gesetzt sein.</p></td>
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

**Wasserzeichen registrieren**

Ein neues Wasserzeichen muss beim Document Security-Dienst registriert sein, bevor es verwendet werden kann. Nachdem Sie ein Wasserzeichen registriert haben, können Sie es in Richtlinien verwenden.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Erstellen von Wasserzeichen mit der Java-API {#create-watermarks-using-the-java-api}

Erstellen Sie mit der Document Security-API (Java) ein Wasserzeichen:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie `adobe-rightsmanagement-client.jar` in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen der Wasserzeichenattribute

   * Erstellen Sie ein `Watermark` -Objekt, indem Sie die statische `createWatermark` -Methode des `InfomodelObjectFactory` -Objekts aufrufen. Diese Methode gibt ein `Watermark` -Objekt zurück.
   * Legen Sie das Attribut name des Wasserzeichens fest, indem Sie die Methode `setName` des Objekts `Watermark` aufrufen und einen string -Wert übergeben, der den Richtliniennamen angibt.
   * Legen Sie das Hintergrundattribut des Wasserzeichens fest, indem Sie die `setBackground` -Methode des Objekts `Watermark` aufrufen und `true` übergeben. Durch Festlegen dieses Attributs wird das Wasserzeichen im Hintergrund des Dokuments angezeigt.
   * Legen Sie das benutzerdefinierte Textattribut des Wasserzeichens fest, indem Sie die `setCustomText` -Methode des Objekts `Watermark` aufrufen und einen Zeichenfolgenwert übergeben, der den Text des Wasserzeichens darstellt.
   * Legen Sie das Deckkraftattribut des Wasserzeichens fest, indem Sie die `setOpacity` -Methode des Objekts `Watermark` aufrufen und einen ganzzahligen Wert übergeben, der den Deckkraftwert angibt. Der Wert 100 zeigt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 zeigt an, dass das Wasserzeichen vollständig transparent ist.

1. Registrieren Sie das Wasserzeichen.

   * Erstellen Sie ein `WatermarkManager` -Objekt, indem Sie die `getWatermarkManager` -Methode des Objekts `RightsManagementClient` aufrufen. Diese Methode gibt ein `WatermarkManager` -Objekt zurück.
   * Registrieren Sie das Wasserzeichen, indem Sie die `registerWatermark`-Methode des `WatermarkManager`-Objekts aufrufen und das `Watermark`-Objekt übergeben, das das zu registrierende Wasserzeichen darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Identifizierungswert des Wasserzeichens darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP-Modus): Erstellen eines Wasserzeichens mit der Java-API&quot;

### Erstellen von Wasserzeichen mit der Webdienst-API {#create-watermarks-using-the-web-service-api}

Erstellen Sie ein Wasserzeichen mithilfe der Document Security-API (Webdienst):

1. Erstellen Sie ein Document Security Client-API-Objekt.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `RightsManagementServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie ein `WatermarkSpec`-Objekt, indem Sie den `WatermarkSpec`-Konstruktor aufrufen.
   * Legen Sie den Namen des Wasserzeichens fest, indem Sie dem `name`-Datenelement des `WatermarkSpec`-Objekts einen Zeichenfolgenwert zuweisen.
   * Legen Sie das Attribut `id` des Wasserzeichens fest, indem Sie dem `id`-Datenelement des Objekts `WatermarkSpec` einen Zeichenfolgenwert zuweisen.
   * Erstellen Sie für jede festzulegende Wasserzeicheneigenschaft ein separates `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `key` -Datenelement des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Wert zuweisen (z. B. `WaterBackCmd:OPACITY)`.
   * Legen Sie den Wert fest, indem Sie dem `value` -Datenelement des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Wert zuweisen (z. B. `.25`).
   * Erstellen Sie ein `MyArrayOf_xsd_anyType` -Objekt. Rufen Sie für jedes `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt die `MyArrayOf_xsd_anyType`-Methode des Objekts `Add` auf. Übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie das `MyArrayOf_xsd_anyType`-Objekt dem `WatermarkSpec`-Datenelement des `values`-Objekts zu.

1. Registrieren Sie das Wasserzeichen.

   Registrieren Sie das Wasserzeichen, indem Sie die `registerWatermark`-Methode des `RightsManagementServiceClient`-Objekts aufrufen und das `WatermarkSpec`-Objekt übergeben, das das zu registrierende Wasserzeichen darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Erstellen eines Wasserzeichens mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Erstellen eines Wasserzeichens mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Ändern von Wasserzeichen {#modifying-watermarks}

Sie können ein vorhandenes Wasserzeichen mithilfe der Document Security Java-API oder der Web Service-API ändern. Um Änderungen an einem vorhandenen Wasserzeichen vorzunehmen, rufen Sie es ab, ändern dessen Attribute und aktualisieren Sie es dann auf dem Server. Angenommen, Sie rufen ein Wasserzeichen ab und ändern dessen Deckkraftattribut. Bevor die Änderung wirksam wird, müssen Sie das Wasserzeichen aktualisieren.

Wenn Sie ein Wasserzeichen ändern, wirkt sich die Änderung auf zukünftige Dokumente aus, auf die das Wasserzeichen angewendet wird. Vorhandene PDF-Dokumente, die das Wasserzeichen enthalten, sind also nicht betroffen.

>[!NOTE]
>
>Nur Benutzer mit Administratorrechten für Document Security können Wasserzeichen ändern. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Client-Objekts des Document Security-Dienstes erforderlich sind.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-9}

Gehen Sie wie folgt vor, um ein Wasserzeichen zu ändern:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie das zu ändernde Wasserzeichen ab.
1. Legen Sie die Wasserzeichenattribute fest.
1. Aktualisieren Sie das Wasserzeichen.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` -Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` -Objekt.

**Abrufen des zu ändernden Wasserzeichens**

Um ein Wasserzeichen zu ändern, müssen Sie ein vorhandenes Wasserzeichen abrufen. Sie können ein Wasserzeichen abrufen, indem Sie dessen Namen angeben oder dessen Bezeichnerwert angeben.

**Festlegen der Wasserzeichenattribute**

Um ein vorhandenes Wasserzeichen zu ändern, ändern Sie den Wert eines oder mehrerer Wasserzeichenattribute. Beim programmatischen Aktualisieren eines Wasserzeichens mithilfe eines Webdiensts müssen Sie alle ursprünglich festgelegten Attribute festlegen, auch wenn sich der Wert nicht ändert. Angenommen, die folgenden Wasserzeichenattribute sind festgelegt: `WaterBackCmd:IS_USERID_ENABLED`, `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`, `WaterBackCmd:OPACITY` und `WaterBackCmd:SRCTEXT`. Obwohl das einzige Attribut, das Sie ändern möchten, `WaterBackCmd:OPACITY` ist, müssen Sie die anderen Werte festlegen.

>[!NOTE]
>
>Wenn Sie die Java-API zum Ändern eines Wasserzeichens verwenden, müssen Sie nicht alle Attribute angeben. Legen Sie das Wasserzeichenattribut fest, das Sie ändern möchten.

>[!NOTE]
>
>Weitere Informationen zu den Namen der Wasserzeichenattribute finden Sie unter [Erstellen von Wasserzeichen](protecting-documents-policies.md#creating-watermarks).

**Aktualisieren des Wasserzeichens**

Nachdem Sie die Attribute eines Wasserzeichens geändert haben, müssen Sie das Wasserzeichen aktualisieren.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Wasserzeichen erstellen](protecting-documents-policies.md#creating-watermarks)

### Ändern von Wasserzeichen mithilfe der Java-API {#modify-watermarks-using-the-java-api}

Ändern Sie ein Wasserzeichen mithilfe der Document Security-API (Java):

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie die Datei &quot;adobe-rightsmanagement-client.jar&quot;in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Erstellen Sie ein `WatermarkManager` -Objekt, indem Sie die `DocumentSecurityClient` -Methode des Objekts `getWatermarkManager` aufrufen und einen string -Wert übergeben, der den Wasserzeichennamen angibt. Diese Methode gibt ein `Watermark` -Objekt zurück, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   Legen Sie das Deckkraftattribut des Wasserzeichens fest, indem Sie die `setOpacity` -Methode des Objekts `Watermark` aufrufen und einen ganzzahligen Wert übergeben, der den Deckkraftwert angibt. Der Wert 100 zeigt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 zeigt an, dass das Wasserzeichen vollständig transparent ist.

   >[!NOTE]
   >
   >In diesem Beispiel wird nur das Trübungsattribut geändert.

1. Aktualisieren Sie das Wasserzeichen.

   * Aktualisieren Sie das Wasserzeichen, indem Sie die `updateWatermark`-Methode des `WatermarkManager`-Objekts aufrufen und das `Watermark`-Objekt übergeben, dessen Attribut geändert wurde.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie im Schnellstart-Modus (SOAP-Modus): Ändern eines Wasserzeichens mithilfe des Java-API-Abschnitts.

### Ändern von Wasserzeichen mithilfe der Webdienst-API {#modify-watermarks-using-the-web-service-api}

Ändern Sie ein Wasserzeichen mithilfe der Document Security-API (Webdienst):

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DocumentSecurityServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Rufen Sie das zu ändernde Wasserzeichen ab, indem Sie die `getWatermarkByName` -Methode des Objekts `DocumentSecurityServiceClient` aufrufen. Übergeben Sie einen string -Wert, der den Namen des Wasserzeichens angibt. Diese Methode gibt ein `WatermarkSpec` -Objekt zurück, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie für jede zu aktualisierende Wasserzeicheneigenschaft ein separates `MyMapOf_xsd_string_To_xsd_anyType_Item` -Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `key` -Datenelement des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Wert zuweisen (z. B. `WaterBackCmd:OPACITY)`.
   * Legen Sie den Wert fest, indem Sie dem `value` -Datenelement des Objekts `MyMapOf_xsd_string_To_xsd_anyType_Item` einen Wert zuweisen (z. B. `.50`).
   * Erstellen Sie ein `MyArrayOf_xsd_anyType` -Objekt. Rufen Sie für jedes `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt die `MyArrayOf_xsd_anyType`-Methode des Objekts `Add` auf. Übergeben Sie das `MyMapOf_xsd_string_To_xsd_anyType_Item`-Objekt.
   * Weisen Sie das `MyArrayOf_xsd_anyType`-Objekt dem `WatermarkSpec`-Datenelement des `values`-Objekts zu.

1. Aktualisieren Sie das Wasserzeichen.

   Aktualisieren Sie das Wasserzeichen, indem Sie die `updateWatermark`-Methode des `DocumentSecurityServiceClient`-Objekts aufrufen und das `WatermarkSpec`-Objekt übergeben, das das zu ändernde Wasserzeichen darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (MTOM): Ändern eines Wasserzeichens mithilfe der Webdienst-API&quot;

## Suchen nach Ereignissen {#searching-for-events}

Der Rights Management-Dienst verfolgt bestimmte Aktionen genau nach ihrem Ablauf, z. B. das Anwenden einer Richtlinie auf ein Dokument, das Öffnen eines richtliniengeschützten Dokuments und das Sperren des Dokumentzugriffs. Die Ereignisprüfung muss für den Rights Management-Dienst aktiviert sein, sonst werden Ereignisse nicht verfolgt.

Ereignisse fallen in eine der folgenden Kategorien:

* Administrator-Ereignisse sind Aktionen, die sich auf einen Administrator beziehen, z. B. die Erstellung eines neuen Administratorkontos.
* Dokumentereignisse sind Aktionen im Zusammenhang mit einem Dokument, z. B. das Schließen eines richtliniengeschützten Dokuments.
* Richtlinienereignisse sind Aktionen im Zusammenhang mit einer Richtlinie, z. B. die Erstellung einer neuen Richtlinie.
* Dienstereignisse sind Aktionen im Zusammenhang mit dem Rights Management-Dienst, z. B. die Synchronisierung mit dem Benutzerordner.

Sie können mit der Rights Management Java-API oder der Web Service-API nach bestimmten Ereignissen suchen. Durch die Suche nach Ereignissen können Sie Aufgaben ausführen, z. B. eine Protokolldatei bestimmter Ereignisse erstellen.

>[!NOTE]
>
>Weitere Informationen zum Rights Management-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-10}

Um nach einem Rights Management-Ereignis zu suchen, führen Sie die folgenden Schritte aus:

1. Projektdateien einschließen.
1. Erstellen Sie ein Rights Management Client-API-Objekt.
1. Geben Sie das Ereignis an, nach dem gesucht werden soll.
1. Suchen Sie nach dem Ereignis.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Rights Management Client-API-Objekts**

Bevor Sie einen Rights Management-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Rights Management-Dienst-Client-Objekt erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` -Objekt. Wenn Sie die Rights Management-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` -Objekt.

**Geben Sie die Ereignisse an, nach denen gesucht werden soll**

Sie müssen das zu suchende Ereignis angeben. Sie können beispielsweise nach dem Richtlinienerstellungsereignis suchen, das beim Erstellen einer neuen Richtlinie auftritt.

**Suchen Sie nach dem Ereignis**

Nachdem Sie das zu suchende Ereignis angegeben haben, können Sie entweder die Rights Management Java-API oder die Rights Management-Webdienst-API verwenden, um nach dem Ereignis zu suchen.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Suchen Sie mithilfe der Java-API {#search-for-events-using-the-java-api} nach Ereignissen.

Suchen Sie mithilfe der Rights Management-API (Java) nach Ereignissen:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Rights Management Client-API-Objekts

   Erstellen Sie ein `DocumentSecurityClient` -Objekt, indem Sie seinen Konstruktor verwenden und ein `ServiceClientFactory` -Objekt übergeben, das Verbindungseigenschaften enthält.

1. Geben Sie die Ereignisse an, nach denen gesucht werden soll

   * Erstellen Sie ein `EventManager` -Objekt, indem Sie die `getEventManager` -Methode des Objekts `DocumentSecurityClient` aufrufen. Diese Methode gibt ein `EventManager` -Objekt zurück.
   * Erstellen Sie ein `EventSearchFilter` -Objekt, indem Sie seinen Konstruktor aufrufen.
   * Geben Sie das zu suchende Ereignis an, indem Sie die `setEventCode` -Methode des Objekts `EventSearchFilter` aufrufen und ein statisches Datenelement übergeben, das zur `EventManager` -Klasse gehört, die das zu suchende Ereignis darstellt. Um beispielsweise nach dem Richtlinienerstellungsereignis zu suchen, übergeben Sie `EventManager.POLICY_CREATE_EVENT`.

   >[!NOTE]
   >
   >Sie können zusätzliche Suchkriterien definieren, indem Sie `EventSearchFilter` -Objektmethoden aufrufen. Rufen Sie beispielsweise die Methode `setUserName` auf, um einen mit dem Ereignis verknüpften Benutzer anzugeben.

1. Suchen Sie nach dem Ereignis

   Suchen Sie nach dem Ereignis, indem Sie die `searchForEvents` -Methode des Objekts `EventManager` aufrufen und das `EventSearchFilter` -Objekt übergeben, das die Ereignissuchkriterien definiert. Diese Methode gibt ein Array von `Event` -Objekten zurück.

**Codebeispiele**

Codebeispiele, die den Rights Management-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (SOAP): Suchen nach Ereignissen mit der Java-API&quot;

### Suchen Sie mithilfe der Webdienst-API {#search-for-events-using-the-web-service-api} nach Ereignissen.

Suchen Sie mithilfe der Rights Management-API (Webdienst) nach Ereignissen:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Rights Management Client-API-Objekts

   * Erstellen Sie ein `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DocumentSecurityServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Geben Sie die Ereignisse an, nach denen gesucht werden soll

   * Erstellen Sie ein `EventSpec` -Objekt mithilfe des zugehörigen Konstruktors.
   * Geben Sie den Beginn des Zeitraums an, in dem das Ereignis auftrat, indem Sie das `firstTime.date` -Datenelement des `EventSpec` -Objekts mit der `DataTime` -Instanz festlegen, die den Beginn des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Weisen Sie den Wert `true` dem `EventSpec`-Datenelement des `firstTime.dateSpecified`-Objekts zu.
   * Geben Sie das Ende des Zeitraums an, in dem das Ereignis auftrat, indem Sie das `lastTime.date` -Datenelement des `EventSpec` -Objekts mit der `DataTime` -Instanz festlegen, die das Ende des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Weisen Sie den Wert `true` dem `EventSpec`-Datenelement des `lastTime.dateSpecified`-Objekts zu.
   * Legen Sie das zu suchende Ereignis fest, indem Sie dem `eventCode`-Datenelement des `EventSpec`-Objekts einen Zeichenfolgenwert zuweisen. In der folgenden Tabelle sind die numerischen Werte aufgeführt, die Sie dieser Eigenschaft zuweisen können:

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

1. Suchen Sie nach dem Ereignis

   Suchen Sie nach dem Ereignis, indem Sie die `searchForEvents` -Methode des Objekts `DocumentSecurityServiceClient` aufrufen und das `EventSpec` -Objekt übergeben, das das zu suchende Ereignis und die maximale Anzahl der Ergebnisse darstellt. Diese Methode gibt eine `MyArrayOf_xsd_anyType`-Sammlung zurück, bei der jedes Element eine `AuditSpec`-Instanz ist. Mithilfe einer `AuditSpec`-Instanz können Sie Informationen zum Ereignis abrufen, z. B. zu dem Zeitpunkt, zu dem es aufgetreten ist. Die `AuditSpec` -Instanz enthält ein `timestamp` -Datenelement, das diese Informationen angibt.

**Codebeispiele**

Codebeispiele, die den Rights Management-Dienst verwenden, finden Sie in den folgenden Schnellstarts:

* &quot;Schnellstart (MTOM): Suchen nach Ereignissen mithilfe der Webdienst-API&quot;
* &quot;Schnellstart (SwaRef): Suchen nach Ereignissen mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Anwenden von Richtlinien auf Word-Dokumente {#applying-policies-to-word-documents}

Zusätzlich zu PDF-Dokumenten unterstützt der Rights Management-Dienst zusätzliche Dokumentenformate wie Microsoft Word-Dokumente (DOC-Dateien) und andere Microsoft Office-Dateiformate. Sie können beispielsweise eine Richtlinie auf ein Word-Dokument anwenden, um es zu schützen. Durch Anwendung einer Richtlinie auf ein Word-Dokument können Sie den Zugriff auf das Dokument einschränken. Sie können eine Richtlinie nicht auf ein Dokument anwenden, wenn das Dokument bereits mit einer Richtlinie gesichert ist.

Sie können die Verwendung eines richtliniengeschützten Word-Dokuments nach dessen Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-11}

So wenden Sie eine Richtlinie auf ein Word-Dokument an:

1. Projektdateien einschließen.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein Word-Dokument ab, auf das eine Richtlinie angewendet wird.
1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.
1. Speichern Sie das richtliniengeschützte Word-Dokument.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert ausführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen.

**Abrufen eines Word-Dokuments**

Sie müssen ein Word-Dokument abrufen, um eine Richtlinie anwenden zu können. Nachdem Sie eine Richtlinie auf das Word-Dokument angewendet haben, sind Benutzer bei der Verwendung des Dokuments eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offline-Modus aktiviert, müssen die Benutzer online sein, um das Dokument zu öffnen.

**Vorhandene Richtlinie auf das Word-Dokument anwenden**

Um eine Richtlinie auf ein Word-Dokument anzuwenden, müssen Sie auf eine vorhandene Richtlinie verweisen und angeben, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften festlegt, muss Zugriff auf die angegebene Richtlinie haben. Wenn nicht, tritt eine Ausnahme auf.

**Word-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie auf ein Word-Dokument angewendet hat, können Sie das richtliniengeschützte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Java-API {#apply-a-policy-to-a-word-document-using-the-java-api}

Wenden Sie mithilfe der Document Security-API (Java) eine Richtlinie auf ein Word-Dokument an:

1. Projektdateien einschließen.

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein Word-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream` -Objekt, das das Word-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen string -Wert übergeben, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   * Erstellen Sie ein `DocumentManager` -Objekt, indem Sie die `getDocumentManager` -Methode des Objekts `DocumentSecurityClient` aufrufen.
   * Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `protectDocument` -Methode des Objekts `DocumentManager` aufrufen und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document`-Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Ein string -Wert, der den Namen des Dokuments angibt.
      * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` -Wert angeben, der dazu führt, dass der `MyPolicies`-Richtliniensatz verwendet wird.
      * Ein string -Wert, der den Richtliniennamen angibt.
      * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert null sein.)
      * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` sein. (Wenn dieser Parameter `null` ist, muss der vorherige Parameterwert `null` sein.)
      * Ein `com.adobe.livecycle.rightsmanagement.Locale` -Gebietsschema, das für die Auswahl der MS Office-Vorlage verwendet wird. Dieser Parameterwert ist optional und Sie können `null` angeben.

      Die `protectDocument`-Methode gibt ein `RMSecureDocumentResult`-Objekt zurück, das das richtliniengeschützte Word-Dokument enthält.


1. Speichern Sie das Word-Dokument.

   * Rufen Sie die `getProtectedDoc` -Methode des Objekts `RMSecureDocumentResult` auf, um das richtliniengeschützte Word-Dokument abzurufen. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück.
   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateierweiterung DOC ist.
   * Rufen Sie die `copyToFile` -Methode des `com.adobe.idp.Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `getProtectedDoc` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (SOAP-Modus): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Java-API&quot;

### Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Webdienst-API {#apply-a-policy-to-a-word-document-using-the-web-service-api}

Wenden Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie auf ein Word-Dokument an:

1. Projektdateien einschließen.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DocumentSecurityService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `DocumentSecurityServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `DocumentSecurityServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `DocumentSecurityServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `DocumentSecurityServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Rufen Sie ein Word-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern eines Word-Dokuments verwendet, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Bestimmen Sie die Größe des Byte-Arrays, indem Sie die Eigenschaft `Length` des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen. Übergeben Sie das Byte-Array, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `protectDocument` -Methode des Objekts `DocumentSecurityServiceClient` aufrufen und die folgenden Werte übergeben:

   * Das `BLOB`-Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Ein string -Wert, der den Namen des Dokuments angibt.
   * Ein string -Wert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` -Wert angeben, der dazu führt, dass der `MyPolicies`-Richtliniensatz verwendet wird.
   * Ein string -Wert, der den Richtliniennamen angibt.
   * Ein string -Wert für den Namen der User Manager-Domäne des Benutzers, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der nächste Parameterwert `null` sein.)
   * Ein string -Wert, der den Namen des kanonischen Benutzers des User Manager-Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein. (Wenn dieser Parameter null ist, muss der vorherige Parameterwert `null` sein.)
   * Ein `RMLocale` -Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein string -Ausgabeparameter, der zum Speichern des Richtlinienkennungswerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des richtliniengeschützten Bezeichnerwerts verwendet wird.
   * Ein string -Ausgabeparameter, der zum Speichern des MIME-Typs verwendet wird (z. B. `application/doc`).

   Die `protectDocument`-Methode gibt ein `BLOB`-Objekt zurück, das das richtliniengeschützte Word-Dokument enthält.

1. Speichern Sie das Word-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des richtliniengeschützten Word-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `protectDocument` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` -Datenelements des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine Word-Datei, indem Sie die `Write` -Methode des Objekts `System.IO.BinaryWriter` aufrufen und das Byte-Array übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (MTOM): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Webdienst-API&quot;

## Entfernen von Richtlinien aus Word-Dokumenten {#removing-policies-from-word-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, wenn das Dokument nicht mehr durch eine Richtlinie geschützt werden soll. Wenn Sie ein richtliniengeschütztes Word-Dokument mit einer neueren Richtlinie aktualisieren möchten, ist es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>Weitere Informationen zum Document Security-Dienst finden Sie unter [Dienstreferenz für AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-12}

So entfernen Sie eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Word-Dokument ab.
1. Entfernen Sie die Richtlinie aus dem Word-Dokument.
1. Speichern Sie die nicht gesicherten Word-Dokumente.

**Projektdateien einschließen**

Fügen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxy-Dateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Abrufen eines richtliniengeschützten Word-Dokuments**

Sie müssen ein richtliniengeschütztes Word-Dokument abrufen, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem Word-Dokument zu entfernen, das nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme verursacht.

**Richtlinie aus Word-Dokument entfernen**

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Andernfalls muss die zum Schützen eines Dokuments verwendete Richtlinie die Berechtigung `SWITCH_POLICY` enthalten, damit eine Richtlinie aus einem Word-Dokument entfernt werden kann. Außerdem muss der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Ungesichertes Word-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie aus einem Word-Dokument entfernt hat, können Sie das ungesicherte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Anwenden von Richtlinien auf Word-Dokumente](protecting-documents-policies.md#applying-policies-to-word-documents)

### Eine Richtlinie mithilfe der Java-API {#remove-a-policy-from-a-word-document-using-the-java-api} aus einem Word-Dokument entfernen

Entfernen Sie mithilfe der Document Security-API (Java) eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie adobe-rightsmanagement-client.jar in den Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie ein `java.io.FileInputStream`-Objekt, das das richtliniengeschützte Word-Dokument darstellt, indem Sie seinen Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Richtlinie aus Word-Dokument entfernen

   * Erstellen Sie ein `DocumentManager` -Objekt, indem Sie die `getDocumentManager` -Methode des Objekts `RightsManagementClient` aufrufen.
   * Entfernen Sie eine Richtlinie aus dem Word-Dokument, indem Sie die `removeSecurity` -Methode des Objekts `DocumentManager` aufrufen und das `com.adobe.idp.Document` -Objekt übergeben, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt ein `com.adobe.idp.Document` -Objekt zurück, das ein nicht gesichertes Word-Dokument enthält.

1. Ungesichertes Word-Dokument speichern

   * Erstellen Sie ein `java.io.File` -Objekt und stellen Sie sicher, dass die Dateierweiterung DOC ist.
   * Rufen Sie die `copyToFile` -Methode des `Document` -Objekts auf, um den Inhalt des `Document` -Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` -Objekt verwenden, das von der `removeSecurity` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (SOAP-Modus): Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Java-API&quot;

### Eine Richtlinie mithilfe der Webdienst-API {#remove-a-policy-from-a-word-document-using-the-web-service-api} aus einem Word-Dokument entfernen

Entfernen Sie mithilfe der Document Security-API (Webdienst) eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `RightsManagementServiceClient` -Objekt mithilfe des Standardkonstruktors.
   * Erstellen Sie ein `RightsManagementServiceClient.Endpoint.Address`-Objekt mit dem Konstruktor `System.ServiceModel.EndpointAddress` . Übergeben Sie einen string -Wert, der die WSDL an den AEM Forms-Dienst angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das Attribut `lc_version` nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` -Objekt, indem Sie den Wert des Felds `RightsManagementServiceClient.Endpoint.Binding` abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Setzen Sie das `System.ServiceModel.BasicHttpBinding` -Feld des Objekts `MessageEncoding` auf `WSMessageEncoding.Mtom`. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.UserName` den Benutzernamen des AEM Formulars zu.
      * Weisen Sie dem Feld `RightsManagementServiceClient.ClientCredentials.UserName.Password` den entsprechenden Kennwortwert zu.
      * Weisen Sie dem Feld `BasicHttpBindingSecurity.Transport.ClientCredentialType` den Konstantenwert `HttpClientCredentialType.Basic` zu.
   * Weisen Sie dem Feld `BasicHttpBindingSecurity.Security.Mode` den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu.


1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB`-Objekt wird zum Speichern des richtliniengeschützten Word-Dokuments verwendet, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Byte-Array, das den Inhalt des Objekts `System.IO.FileStream` speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `Length` -Eigenschaft des Objekts `System.IO.FileStream` abrufen.
   * Füllen Sie das Byte-Array mit Stream-Daten, indem Sie die `Read` -Methode des Objekts `System.IO.FileStream` aufrufen und das Byte-Array, die Startposition und die zu lesende Stream-Länge übergeben.
   * Füllen Sie das `BLOB`-Objekt, indem Sie sein `MTOM`-Feld mit dem Inhalt des Byte-Arrays zuweisen.

1. Richtlinie aus Word-Dokument entfernen

   Entfernen Sie die Richtlinie aus dem Word-Dokument, indem Sie die `removePolicySecurity`-Methode des Objekts `RightsManagementServiceClient` aufrufen und das `BLOB`-Objekt übergeben, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt ein `BLOB` -Objekt zurück, das ein nicht gesichertes Word-Dokument enthält.

1. Ungesichertes Word-Dokument speichern

   * Erstellen Sie ein `System.IO.FileStream` -Objekt, indem Sie seinen Konstruktor aufrufen und einen string -Wert übergeben, der den Dateispeicherort des ungesicherten Word-Dokuments darstellt.
   * Erstellen Sie ein Byte-Array, das den Dateninhalt des `BLOB` -Objekts speichert, das von der `removePolicySecurity` -Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des Felds `BLOB` des Objekts `MTOM` abrufen.
   * Erstellen Sie ein `System.IO.BinaryWriter` -Objekt, indem Sie seinen Konstruktor aufrufen und das `System.IO.FileStream` -Objekt übergeben.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie in der folgenden Kurzanleitung:

* &quot;Schnellstart (MTOM): Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Webdienst-API&quot;

**Siehe auch**

[AEM Forms mithilfe von MTOM aufrufen](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
