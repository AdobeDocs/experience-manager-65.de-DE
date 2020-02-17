---
title: Dokumente mit Richtlinien schützen
seo-title: Dokumente mit Richtlinien schützen
description: 'null'
seo-description: 'null'
uuid: 6feb69ef-7b61-4d0b-8c87-d65d98bae9b5
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9b1d2bf3-f28c-41b2-9026-1f3311556422
translation-type: tm+mt
source-git-commit: 413af4ef9bc3652e05da78d622183bcf20a8bee7

---


# Dokumente mit Richtlinien schützen {#protecting-documents-with-policies}

**Informationen zum Document Security-Dienst**

Der Document Security-Dienst ermöglicht es Benutzern, Vertraulichkeitseinstellungen dynamisch auf Adobe PDF-Dokumente anzuwenden und die Kontrolle über die Dokumente zu behalten, unabhängig davon, wie weit sie verteilt werden.

Der Document Security-Dienst verhindert, dass Informationen über die Reichweite des Benutzers hinaus verbreitet werden, indem er den Benutzern ermöglicht, die Kontrolle darüber zu behalten, wie Empfänger das richtliniengeschützte PDF-Dokument verwenden. Ein Benutzer kann angeben, wer ein Dokument öffnen kann, seine Verwendung einschränken und das Dokument nach der Verteilung überwachen. Ein Benutzer kann außerdem den Zugriff auf ein richtliniengeschütztes Dokument dynamisch steuern und sogar den Zugriff auf das Dokument dynamisch sperren.

Der Document Security-Dienst schützt auch andere Dateitypen wie Microsoft Word-Dateien (DOC-Dateien). Sie können die Document Security Client-API verwenden, um mit diesen Dateitypen zu arbeiten. Die folgenden Versionen werden unterstützt:

* Microsoft Office 2003-Dateien (DOC-, XLS-, PPT-Dateien)
* Microsoft Office 2007-Dateien (DOCX-, XLSX-, PPTX-Dateien)
* PTC Pro/E-Dateien

Die folgenden beiden Abschnitte beschreiben die Arbeit mit Word-Dokumenten.

* [Richtlinien auf Word-Dokumente anwenden](protecting-documents-policies.md#applying-policies-to-word-documents)
* [Richtlinien aus Word-Dokumenten entfernen](protecting-documents-policies.md#removing-policies-from-word-documents)

Sie können diese Aufgaben mithilfe des Document Security-Dienstes ausführen:

* Erstellen von Richtlinien. Weitere Informationen finden Sie unter Richtlinien [erstellen](protecting-documents-policies.md#creating-policies).
* Richtlinien ändern. Weitere Informationen finden Sie unter Richtlinien [ändern](protecting-documents-policies.md#modifying-policies).
* Richtlinien löschen. Weitere Informationen finden Sie unter Richtlinien [löschen](protecting-documents-policies.md#deleting-policies).
* Richtlinien auf PDF-Dokumente anwenden Weitere Informationen finden Sie unter Richtlinien [auf PDF-Dokumente](protecting-documents-policies.md#applying-policies-to-pdf-documents)anwenden.
* Richtlinien aus PDF-Dokumenten entfernen Weitere Informationen finden Sie unter Richtlinien [aus PDF-Dokumenten](protecting-documents-policies.md#removing-policies-from-pdf-documents)entfernen.
* Überprüfen Sie richtliniengeschützte Dokumente. Weitere Informationen finden Sie unter [Richtliniengeschützte PDF-Dokumente](protecting-documents-policies.md#inspecting-policy-protected-pdf-documents)überprüfen.
* Zugriff auf PDF-Dokumente sperren. Weitere Informationen finden Sie unter Zugriff [auf Dokumente](protecting-documents-policies.md#revoking-access-to-documents)sperren.
* Zugriff auf gesperrte Dokumente neu zuweisen. Weitere Informationen finden Sie unter Zugriff auf [gesperrte Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents)neu aktivieren.
* Erstellen Sie Wasserzeichen. Weitere Informationen finden Sie unter [Wasserzeichen](protecting-documents-policies.md#creating-watermarks)erstellen.
* Suchen Sie nach Ereignissen. Weitere Informationen finden Sie unter [Suchen nach Ereignissen](protecting-documents-policies.md#searching-for-events).

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Richtlinien erstellen {#creating-policies}

Sie können Richtlinien programmgesteuert mit der Document Security Java-API oder der Webdienst-API erstellen. Eine *Richtlinie* ist eine Sammlung von Informationen, die Document Security-Einstellungen, autorisierte Benutzer und Verwendungsrechte enthalten. Sie können eine beliebige Anzahl von Richtlinien erstellen und speichern, indem Sie Sicherheitseinstellungen für unterschiedliche Situationen und Benutzer verwenden.

Richtlinien ermöglichen Ihnen die Durchführung folgender Aufgaben:

* Geben Sie die Personen an, die das Dokument öffnen können. Die Empfänger können Ihrer Organisation angehören oder extern sein.
* Geben Sie an, wie Empfänger das Dokument verwenden können. Sie können den Zugriff auf verschiedene Acrobat- und Adobe Reader-Funktionen einschränken. Zu diesen Funktionen gehören das Drucken und Kopieren von Text, das Hinzufügen von Unterschriften und das Hinzufügen von Kommentaren zu einem Dokument.
* Ändern Sie die Zugriffs- und Sicherheitseinstellungen jederzeit, auch nachdem Sie das richtliniengeschützte Dokument verteilt haben.
* Überwachen Sie die Verwendung des Dokuments nach der Verteilung. Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können beispielsweise herausfinden, wann ein Benutzer das Dokument geöffnet hat.

### Richtlinien mit Webdiensten erstellen {#creating-a-policy-using-web-services}

Wenn Sie eine Richtlinie mit der Webdienst-API erstellen, referenzieren Sie eine vorhandene PDRL-XML-Datei (Portable Document Rights Language), die die Richtlinie beschreibt. Richtlinienberechtigungen und der Prinzipal werden im PDRL-Dokument definiert. Das folgende XML-Dokument ist ein Beispiel für ein PDRL-Dokument.

```as3
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
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary-of-steps}

So erstellen Sie eine Richtlinie:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Legen Sie die Attribute der Richtlinie fest.
1. Erstellen Sie einen Richtlinieneintrag.
1. Registrieren Sie die Richtlinie.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

Die folgenden JAR-Dateien müssen dem Klassenpfad Ihres Projekts hinzugefügt werden:

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

For information about the location of these JAR files, see [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Attribute der Richtlinie festlegen**

Um eine Richtlinie zu erstellen, legen Sie Richtlinienattribute fest. Ein obligatorisches Attribut ist der Richtlinienname. Richtliniennamen müssen für jeden Richtliniensatz eindeutig sein. Ein Richtliniensatz ist einfach eine Sammlung von Richtlinien. Es kann zwei Richtlinien mit demselben Namen geben, wenn die Richtlinien zu separaten Richtliniensätzen gehören. Zwei Richtlinien in einem Richtliniensatz können jedoch nicht denselben Richtliniennamen haben.

Ein weiteres nützliches Attribut, das festgelegt werden soll, ist die Gültigkeitsdauer. Eine Gültigkeitsdauer ist der Zeitraum, in dem autorisierte Empfänger auf ein richtliniengeschütztes Dokument zugreifen können. Wenn Sie dieses Attribut nicht festlegen, ist die Richtlinie immer gültig.

Eine Gültigkeitsdauer kann auf eine der folgenden Optionen eingestellt werden:

* Eine bestimmte Anzahl Tage, ab dem Zeitpunkt der Veröffentlichung des Dokuments auf das Dokument zugegriffen werden kann
* Ein Enddatum, nach dem das Dokument nicht mehr verfügbar ist
* Ein bestimmter Datumsbereich, auf den das Dokument zugreifen kann
* Immer gültig

Sie können nur ein Startdatum angeben, sodass die Richtlinie nach dem Startdatum gültig ist. Wenn Sie nur ein Enddatum angeben, ist die Richtlinie bis zum Enddatum gültig. Es wird jedoch eine Ausnahme ausgelöst, wenn weder ein Startdatum noch ein Enddatum definiert sind.

Beim Festlegen von Attributen, die zu einer Richtlinie gehören, können Sie auch Verschlüsselungseinstellungen festlegen. Diese Verschlüsselungseinstellungen wirken sich darauf aus, wenn die Richtlinie auf ein Dokument angewendet wird. Sie können die folgenden Verschlüsselungswerte angeben:

* **AES 256**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 256-Bit-Schlüssel dar.
* **AES 128**: Stellt den AES-Verschlüsselungsalgorithmus mit einem 128-Bit-Schlüssel dar.
* **** NoEncryption: Stellt keine Verschlüsselung dar.

Beim Festlegen der `NoEncryption` Option können Sie die `PlaintextMetadata` Option nicht auf `false`. Wenn Sie dies versuchen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie in der `Policy` Schnittstellenbeschreibung in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Richtlinieneintrag erstellen**

Ein Richtlinieneintrag fügt Prinzipale, d. h. Gruppen und Benutzer, und Berechtigungen zu einer Richtlinie hinzu. Eine Richtlinie muss mindestens einen Richtlinieneintrag haben. Nehmen Sie beispielsweise an, dass Sie die folgenden Aufgaben ausführen:

* Erstellen und registrieren Sie einen Richtlinieneintrag, der es einer Gruppe ermöglicht, ein Dokument nur online anzuzeigen, und Empfängern das Kopieren untersagt.
* Hängen Sie den Richtlinieneintrag an die Richtlinie an.
* Sichern Sie ein Dokument mit der Richtlinie mithilfe von Acrobat.

Diese Aktionen führen dazu, dass Empfänger das Dokument nur online anzeigen und nicht kopieren können. Das Dokument bleibt solange geschützt, bis die Sicherheit entfernt wurde.

**Richtlinie registrieren**

Eine neue Richtlinie muss registriert werden, bevor sie verwendet werden kann. Nachdem Sie eine Richtlinie registriert haben, können Sie sie zum Schutz von Dokumenten verwenden.

### Eine Richtlinie mit der Java-API erstellen {#create-a-policy-using-the-java-api}

Erstellen Sie eine Richtlinie mithilfe der Document Security API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie ein `Policy` Objekt, indem Sie die statische `InfomodelObjectFactory` Objektmethode aufrufen `createPolicy` . Diese Methode gibt ein `Policy` Objekt zurück.
   * Legen Sie das Namensattribut der Richtlinie fest, indem Sie die `Policy` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Richtliniennamen angibt. `setName`
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie die `Policy` Methode des `setDescription` Objekts aufrufen und einen Zeichenfolgenwert übergeben, der die Beschreibung der Richtlinie angibt.
   * Legen Sie den Richtliniensatz, zu dem die neue Richtlinie gehört, fest, indem Sie die `Policy` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Richtliniensatznamen angibt. `setPolicySetName` (Sie können `null` für diesen Parameterwert angeben, dass die Richtlinie dem Richtliniensatz *Meine Richtlinien* hinzugefügt wird.)
   * Erstellen Sie die Gültigkeitsdauer der Richtlinie, indem Sie die statische `InfomodelObjectFactory` Methode des Objekts aufrufen `createValidityPeriod` . Diese Methode gibt ein `ValidityPeriod` Objekt zurück.
   * Legen Sie die Anzahl der Tage fest, für die auf ein richtliniengeschütztes Dokument zugegriffen werden kann, indem Sie die `ValidityPeriod` `setRelativeExpirationDays` Objektmethode aufrufen und einen Ganzzahlwert übergeben, der die Anzahl der Tage angibt.
   * Legen Sie die Gültigkeitsdauer der Richtlinie fest, indem Sie die `Policy` Methode des `setValidityPeriod` Objekts aufrufen und das `ValidityPeriod` Objekt übergeben.

1. Erstellen Sie einen Richtlinieneintrag.

   * Erstellen Sie einen Richtlinieneintrag, indem Sie die statische `InfomodelObjectFactory` Methode des Objekts aufrufen `createPolicyEntry` . Diese Methode gibt ein `PolicyEntry` Objekt zurück.
   * Geben Sie die Berechtigungen der Richtlinie an, indem Sie die statische `InfomodelObjectFactory` Methode des Objekts aufrufen `createPermission` . Übergeben Sie einen statischen Datenmember, der zur `Permission` Schnittstelle gehört, die die Berechtigung darstellt. Diese Methode gibt ein `Permission` Objekt zurück. Um beispielsweise die Berechtigung hinzuzufügen, die Benutzern das Kopieren von Daten aus einem richtliniengeschützten PDF-Dokument ermöglicht, übergeben Sie `Permission.COPY`. (Wiederholen Sie diesen Schritt für jede hinzuzufügende Berechtigung.)
   * Fügen Sie die Berechtigung zum Richtlinieneintrag hinzu, indem Sie die `PolicyEntry` Methode des `addPermission` Objekts aufrufen und das `Permission` Objekt übergeben. (Wiederholen Sie diesen Schritt für jedes erstellte `Permission` Objekt.)
   * Erstellen Sie den Richtlinienprinzipal, indem Sie die statische `InfomodelObjectFactory` Methode des Objekts aufrufen `createSpecialPrincipal` . Übergeben Sie einen Datenmember, der zu dem `InfomodelObjectFactory` Objekt gehört, das den Prinzipal darstellt. Diese Methode gibt ein `Principal` Objekt zurück. Um beispielsweise den Herausgeber des Dokuments als Prinzipal hinzuzufügen, übergeben Sie `InfomodelObjectFactory.PUBLISHER_PRINCIPAL`.
   * Fügen Sie dem Richtlinieneintrag den Prinzipal hinzu, indem Sie die `PolicyEntry`Methode des `setPrincipal` Objekts aufrufen und das `Principal` Objekt übergeben.
   * Fügen Sie der Richtlinie den Richtlinieneintrag hinzu, indem Sie die `Policy` Methode des `addPolicyEntry` Objekts aufrufen und das `PolicyEntry` Objekt übergeben.

1. Registrieren Sie die Richtlinie.

   * Erstellen Sie ein `PolicyManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getPolicyManager` aufrufen.
   * Registrieren Sie die Richtlinie, indem Sie die `PolicyManager` Methode des `registerPolicy` Objekts aufrufen und die folgenden Werte übergeben:

      * Das `Policy` Objekt, das die zu registrierende Richtlinie darstellt.
   * Ein Zeichenfolgenwert, der den Richtliniensatz darstellt, zu dem die Richtlinie gehört.
   Wenn Sie ein AEM Forms-Administratorkonto in den Verbindungseinstellungen verwenden, um das `DocumentSecurityClient` Objekt zu erstellen, geben Sie beim Aufrufen der `registerPolicy` Methode den Richtliniensatznamen an. Wenn Sie einen `null` Wert für den Richtliniensatz übergeben, wird die Richtlinie im Richtliniensatz *Meine Richtlinien* für Administratoren erstellt.

   Wenn Sie einen Document Security-Benutzer in den Verbindungseinstellungen verwenden, können Sie die `registerPolicy` Überlastungsmethode aufrufen, die nur die Richtlinie akzeptiert. Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch dem Richtliniensatz *Meine Richtlinien* hinzugefügt. Wenn Sie diesem Richtliniensatz keine neue Richtlinie hinzufügen möchten, geben Sie beim Aufrufen der `registerPolicy` Methode einen Richtliniensatznamen an.

   >[!NOTE]
   >
   >Verweisen Sie beim Erstellen einer Richtlinie auf einen vorhandenen Richtliniensatz. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie unter:

* &quot;Kurzanleitung (SOAP-Modus): Richtlinie mit der Java-API erstellen&quot;

### Eine Richtlinie mit der Webdienst-API erstellen {#create-a-policy-using-the-web-service-api}

Erstellen Sie eine Richtlinie mithilfe der Document Security API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `DocumentSecurityServiceClient` object by using its default constructor.
   * Create a `DocumentSecurityServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `RightsManagementServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Legen Sie die Attribute der Richtlinie fest.

   * Erstellen Sie ein Objekt `PolicySpec`, indem Sie den Konstruktor verwenden.
   * Legen Sie den Namen der Richtlinie fest, indem Sie dem Datenmember des `PolicySpec` Objekts einen Zeichenfolgenwert zuweisen `name` .
   * Legen Sie die Beschreibung der Richtlinie fest, indem Sie dem Datenmember des `PolicySpec` Objekts einen Zeichenfolgenwert zuweisen `description` .
   * Legen Sie den Richtliniensatz fest, zu dem die Richtlinie gehören soll, indem Sie dem `PolicySpec` Datenmember des `policySetName` Objekts einen Zeichenfolgenwert zuweisen. Sie müssen einen bestehenden Richtliniensatznamen angeben. (Sie können `null` für diesen Parameterwert angeben, dass die Richtlinie zu *Meine Richtlinien* hinzugefügt wird.)
   * Legen Sie die Offline-Nutzungsdauer der Richtlinie fest, indem Sie dem `PolicySpec` Datenmember des `offlineLeasePeriod` Objekts einen ganzzahligen Wert zuweisen.
   * Legen Sie den `PolicySpec` Datenmember des `policyXml` Objekts mit einem Zeichenfolgenwert fest, der die PDRL-XML-Daten darstellt. Erstellen Sie dazu ein .NET- `StreamReader` Objekt mit dessen Konstruktor. Übergeben Sie den Speicherort einer PDRL-XML-Datei, die die Richtlinie darstellt, an den `StreamReader` Konstruktor. Rufen Sie als Nächstes die `StreamReader` `ReadLine` Objektmethode auf und weisen Sie der Zeichenfolgen-Variablen den Rückgabewert zu. Durchlaufen des `StreamReader` Objekts, bis die `ReadLine` Methode null zurückgibt. Weisen Sie die Zeichenfolgenvariable dem `PolicySpec` Datenmember des `policyXml` Objekts zu.

1. Erstellen Sie einen Richtlinieneintrag.

   Es ist nicht erforderlich, beim Erstellen einer Richtlinie mit der Document Security-Webdienst-API einen Richtlinieneintrag zu erstellen. Der Richtlinieneintrag wird im PDRL-Dokument definiert.

1. Registrieren Sie die Richtlinie.

   Registrieren Sie die Richtlinie, indem Sie die `DocumentSecurityServiceClient` Methode des `registerPolicy` Objekts aufrufen und die folgenden Werte übergeben:

   * Das `PolicySpec` Objekt, das die zu registrierende Richtlinie darstellt.
   * Ein Zeichenfolgenwert, der den Richtliniensatz darstellt, zu dem die Richtlinie gehört. Sie können einen `null` Wert angeben, der dazu führt, dass die Richtlinie dem Richtliniensatz *MeineRichtlinien* hinzugefügt wird.
   Wenn Sie ein AEM Forms-Administratorkonto in den Verbindungseinstellungen verwenden, um das `DocumentSecurityClient` Objekt zu erstellen, geben Sie beim Aufrufen der `registerPolicy` Methode den Richtliniensatznamen an.

   Wenn Sie einen Document Security-Benutzer in den Verbindungseinstellungen verwenden, können Sie die Überlastungsmethode aufrufen, die nur die Richtlinie akzeptiert. `registerPolicy` Das heißt, Sie müssen den Richtliniensatznamen nicht angeben. Die Richtlinie wird jedoch dem Richtliniensatz *Meine Richtlinien* hinzugefügt. Wenn Sie diesem Richtliniensatz keine neue Richtlinie hinzufügen möchten, geben Sie beim Aufrufen der `registerPolicy` Methode einen Richtliniensatznamen an.

   >[!NOTE]
   >
   >Wenn Sie eine Richtlinie erstellen und einen Richtliniensatz angeben, stellen Sie sicher, dass Sie einen vorhandenen Richtliniensatz angeben. Wenn Sie einen Richtliniensatz angeben, der nicht vorhanden ist, wird eine Ausnahme ausgelöst.

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Erstellen einer Richtlinie mit der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Erstellen einer Richtlinie mit der Webdienst-API&quot;

## Richtlinien ändern {#modifying-policies}

Sie können eine vorhandene Richtlinie mit der Document Security Java-API oder der Webdienst-API ändern. Um Änderungen an einer vorhandenen Richtlinie vorzunehmen, rufen Sie sie ab, ändern sie und aktualisieren Sie dann die Richtlinie auf dem Server. Nehmen Sie beispielsweise an, Sie rufen eine vorhandene Richtlinie ab und verlängern die Gültigkeitsdauer. Bevor die Änderung wirksam wird, müssen Sie die Richtlinie aktualisieren.

Sie können eine Richtlinie ändern, wenn sich die Geschäftsanforderungen ändern und die Richtlinie diese Anforderungen nicht mehr widerspiegelt. Anstatt eine neue Richtlinie zu erstellen, können Sie einfach eine vorhandene Richtlinie aktualisieren.

Um Richtlinienattribute mithilfe eines Webdiensts zu ändern (z. B. mithilfe von Java-Proxyklassen, die mit JAX-WS erstellt wurden), müssen Sie sicherstellen, dass die Richtlinie beim Document Security-Dienst registriert ist. Sie können dann mithilfe der `PolicySpec.getPolicyXml` Methode auf die vorhandene Richtlinie verweisen und die Richtlinienattribute mithilfe der entsprechenden Methoden ändern. Sie können beispielsweise die Offline-Nutzungsdauer ändern, indem Sie die `PolicySpec.setOfflineLeasePeriod` Methode aufrufen.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-1}

So ändern Sie eine vorhandene Richtlinie:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Eine vorhandene Richtlinie abrufen.
1. Richtlinienattribute ändern
1. Aktualisieren Sie die Richtlinie.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Vorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` Objekt.

**Eine vorhandene Richtlinie abrufen**

Sie müssen eine vorhandene Richtlinie abrufen, um sie zu ändern. Um eine Richtlinie abzurufen, geben Sie den Richtliniennamen und den Richtliniensatz an, zu dem die Richtlinie gehört. Wenn Sie einen `null` Wert für den Richtliniensatznamen angeben, wird die Richtlinie aus dem Richtliniensatz &quot; *Meine Richtlinien* &quot;abgerufen.

**Attribute der Richtlinie festlegen**

Um eine Richtlinie zu ändern, ändern Sie den Wert der Richtlinienattribute. Das einzige Richtlinienattribut, das Sie nicht ändern können, ist das Attribut name. Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, können Sie den Wert des Attributs für die Offline-Nutzungsdauer der Richtlinie ändern.

Beim Ändern der Offline-Nutzungsdauer einer Richtlinie mithilfe eines Webdiensts wird das `offlineLeasePeriod` Feld auf der `PolicySpec` Oberfläche ignoriert. Um die Offline-Nutzungsdauer zu aktualisieren, ändern Sie das `OfflineLeasePeriod` Element im PDRL-XML-Dokument. Verweisen Sie anschließend mithilfe des Datenelements der `PolicySpec` Schnittstelle auf das aktualisierte PDRL-XML-Dokument `policyXML` .

>[!NOTE]
>
>Weitere Informationen zu anderen Attributen, die Sie festlegen können, finden Sie in der `Policy` Schnittstellenbeschreibung in der [AEM Forms-API-Referenz](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Richtlinie aktualisieren**

Bevor die Änderungen, die Sie an einer Richtlinie vornehmen, wirksam werden, müssen Sie die Richtlinie mit dem Document Security-Dienst aktualisieren. Änderungen an Richtlinien, die Dokumente schützen, werden aktualisiert, wenn das richtliniengeschützte Dokument das nächste Mal mit dem Document Security-Dienst synchronisiert wird.

### Vorhandene Richtlinien mit der Java-API ändern {#modify-existing-policies-using-the-java-api}

Ändern Sie eine vorhandene Richtlinie mithilfe der Document Security API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Eine vorhandene Richtlinie abrufen.

   * Erstellen Sie ein `PolicyManager` Objekt, indem Sie die `RightsManagementClient` Objektmethode `getPolicyManager` aufrufen.
   * Erstellen Sie ein `Policy` Objekt, das die zu aktualisierende Richtlinie darstellt, indem Sie die `PolicyManager` Objektmethode aufrufen `getPolicy` und die folgenden Werte übergeben.&quot;

      * Ein Zeichenfolgenwert, der den Richtliniensatznamen darstellt, zu dem die Richtlinie gehört. Sie können festlegen, `null` dass der Richtliniensatz verwendet werden `MyPolicies` soll.
      * Ein Zeichenfolgenwert, der den Richtliniennamen darstellt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen. Um beispielsweise die Offline-Nutzungsdauer der Richtlinie zu ändern, rufen Sie die `Policy` Objektmethode `setOfflineLeasePeriod` auf.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren Sie die Richtlinie, indem Sie die `PolicyManager` Objektmethode `updatePolicy` aufrufen. Übergeben Sie das `Policy` Objekt, das die zu aktualisierende Richtlinie darstellt.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie im Schnellstart-Modus (SOAP-Modus): Ändern einer Richtlinie mithilfe des Abschnitts &quot;Java-API&quot;.

### Vorhandene Richtlinien mit der Webdienst-API ändern {#modify-existing-policies-using-the-web-service-api}

Ändern Sie eine vorhandene Richtlinie mithilfe der Document Security API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `RightsManagementServiceClient` object by using its default constructor.
   * Create a `RightsManagementServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `RightsManagementServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Eine vorhandene Richtlinie abrufen.

   Erstellen Sie ein `PolicySpec` Objekt, das die zu ändernde Richtlinie darstellt, indem Sie die `RightsManagementServiceClient` `getPolicy` Objektmethode aufrufen und die folgenden Werte übergeben:

   * Ein Zeichenfolgenwert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können festlegen, `null` dass der Richtliniensatz verwendet werden `MyPolicies` soll.
   * Ein Zeichenfolgenwert, der den Namen der Richtlinie angibt.

1. Legen Sie die Attribute der Richtlinie fest.

   Ändern Sie die Attribute der Richtlinie entsprechend Ihren Geschäftsanforderungen.

1. Aktualisieren Sie die Richtlinie.

   Aktualisieren Sie die Richtlinie, indem Sie die `RightsManagementServiceClient` Methode des `updatePolicyFromSDK` Objekts aufrufen und das `PolicySpec` Objekt übergeben, das die zu aktualisierende Richtlinie darstellt.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Ändern einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Ändern einer Richtlinie mithilfe der Webdienst-API&quot;

## Löschen von Richtlinien {#deleting-policies}

Sie können eine vorhandene Richtlinie mit der Document Security Java-API oder der Webdienst-API löschen. Nachdem eine Richtlinie gelöscht wurde, kann sie nicht mehr zum Schutz von Dokumenten verwendet werden. Vorhandene richtliniengeschützte Dokumente, die die Richtlinie verwenden, sind jedoch weiterhin geschützt. Sie können eine Richtlinie löschen, wenn eine neuere verfügbar wird.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-2}

So löschen Sie eine vorhandene Richtlinie:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Löschen Sie die Richtlinie.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` Objekt.

**Richtlinie löschen**

Um eine Richtlinie zu löschen, geben Sie die zu löschende Richtlinie und den Richtliniensatz an, zu dem die Richtlinie gehört. Der Benutzer, dessen Einstellungen zum Aufrufen von AEM Forms verwendet werden, muss berechtigt sein, die Richtlinie zu löschen. andernfalls tritt eine Ausnahme auf. Wenn Sie versuchen, eine Richtlinie zu löschen, die nicht vorhanden ist, tritt eine Ausnahme auf.

### Richtlinien mit der Java-API löschen {#delete-policies-using-the-java-api}

Eine Richtlinie mithilfe der Document Security API (Java) löschen:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Löschen Sie die Richtlinie.

   * Erstellen Sie ein `PolicyManager` Objekt, indem Sie die `RightsManagementClient` Objektmethode `getPolicyManager` aufrufen.
   * Löschen Sie die Richtlinie, indem Sie die `PolicyManager` Methode des `deletePolicy` Objekts aufrufen und die folgenden Werte übergeben:

      * Ein Zeichenfolgenwert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können festlegen, `null` dass der Richtliniensatz verwendet werden `MyPolicies` soll.
      * Ein Zeichenfolgenwert, der den Namen der zu löschenden Richtlinie angibt.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (SOAP-Modus): Löschen einer Richtlinie mit der Java-API&quot;

### Richtlinien mit der Webdienst-API löschen {#delete-policies-using-the-web-service-api}

Eine Richtlinie mithilfe der Document Security API (Webdienst) löschen:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `RightsManagementServiceClient` object by using its default constructor.
   * Create a `RightsManagementServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `RightsManagementServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Löschen Sie die Richtlinie.

   Delete a policy by invoking the `RightsManagementServiceClient` object’s `deletePolicy` method and passing the following values:

   * Ein Zeichenfolgenwert, der den Richtliniensatznamen angibt, zu dem die Richtlinie gehört. Sie können festlegen, `null` dass der Richtliniensatz verwendet werden `MyPolicies` soll.
   * Ein Zeichenfolgenwert, der den Namen der zu löschenden Richtlinie angibt.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Löschen einer Richtlinie mithilfe der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Löschen einer Richtlinie mithilfe der Webdienst-API&quot;

## Richtlinien auf PDF-Dokumente anwenden {#applying-policies-to-pdf-documents}

Sie können eine Richtlinie auf ein PDF-Dokument anwenden, um das Dokument zu schützen. Durch Anwendung einer Richtlinie auf ein PDF-Dokument beschränken Sie den Zugriff auf das Dokument. Sie können eine Richtlinie nicht auf ein Dokument anwenden, wenn das Dokument bereits mit einer Richtlinie gesichert ist.

Während das Dokument geöffnet ist, können Sie den Zugriff auf Acrobat- und Adobe Reader-Funktionen einschränken, einschließlich der Möglichkeit, Text zu drucken und zu kopieren, Änderungen vorzunehmen und Signaturen und Kommentare zu einem Dokument hinzuzufügen. Darüber hinaus können Sie ein richtliniengeschütztes PDF-Dokument sperren, wenn Sie nicht mehr möchten, dass Benutzer auf das Dokument zugreifen können.

Sie können die Verwendung eines richtliniengeschützten Dokuments nach der Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-3}

So wenden Sie eine Richtlinie auf ein PDF-Dokument an:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein PDF-Dokument ab, auf das eine Richtlinie angewendet wird.
1. Eine vorhandene Richtlinie auf das PDF-Dokument anwenden
1. Speichern Sie das richtliniengeschützte PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` Objekt.

**PDF-Dokument abrufen**

Sie können ein PDF-Dokument abrufen, um eine Richtlinie anzuwenden. Nachdem Sie eine Richtlinie auf das PDF-Dokument angewendet haben, sind Benutzer bei der Verwendung des Dokuments eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offlinemodus aktiviert, müssen die Benutzer zum Öffnen des Dokuments online sein.

**Vorhandene Richtlinie auf das PDF-Dokument anwenden**

Um eine Richtlinie auf ein PDF-Dokument anzuwenden, verweisen Sie auf eine vorhandene Richtlinie und geben Sie an, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften einstellt, muss Zugriff auf die angegebene Richtlinie haben. Andernfalls tritt eine Ausnahme auf.

**PDF-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie auf ein PDF-Dokument angewendet hat, können Sie das richtliniengeschützte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Java-API {#apply-a-policy-to-a-pdf-document-using-the-java-api}

Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Document Security API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. PDF-Dokument abrufen.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das PDF-Dokument mit dem Konstruktor darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Eine vorhandene Richtlinie auf das PDF-Dokument anwenden

   * Erstellen Sie ein `DocumentManager` Objekt, indem Sie die `RightsManagementClient` Objektmethode `getDocumentManager` aufrufen.
   * Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `DocumentManager` `protectDocument` Objektmethode aufrufen und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document` Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Ein Zeichenfolgenwert, der den Namen des Dokuments angibt.
      * Ein Zeichenfolgenwert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` Wert angeben, der dazu führt, dass der `MyPolicies` Richtliniensatz verwendet wird.
      * Ein Zeichenfolgenwert, der den Richtliniennamen angibt.
      * Ein Zeichenfolgenwert, der den Namen der User Manager-Domäne des Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein (wenn dieser Parameter null ist, muss der nächste Parameterwert null sein).
      * Ein Zeichenfolgenwert, der den Namen des kanonischen Namens des Benutzers des Benutzermanagers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` (wenn dieser Parameter null ist, muss der vorherige Parameterwert `null`sein).
      * Eine `com.adobe.livecycle.rightsmanagement.Locale` Variable, die das Gebietsschema darstellt, mit dem die MS Office-Vorlage ausgewählt wird. Dieser Parameterwert ist optional und wird nicht für PDF-Dokumente verwendet. Um ein PDF-Dokument zu sichern, geben Sie `null`an.
      Die `protectDocument` Methode gibt ein `RMSecureDocumentResult` Objekt zurück, das das richtliniengeschützte PDF-Dokument enthält.


1. Speichern Sie das PDF-Dokument.

   * Rufen Sie die `RMSecureDocumentResult` Methode des `getProtectedDoc` Objekts auf, um das richtliniengeschützte PDF-Dokument abzurufen. Diese Methode gibt ein `com.adobe.idp.Document` Objekt zurück.
   * Create a `java.io.File` object and ensure that the file extension is PDF.
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf, um den Inhalt des `Document` Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` Objekt verwenden, das von der `getProtectedDoc` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (EJB-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mit der Java-API&quot;
* &quot;Kurzanleitung (SOAP-Modus): Anwenden einer Richtlinie auf ein PDF-Dokument mit der Java-API&quot;

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API {#apply-a-policy-to-a-pdf-document-using-the-web-service-api}

Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Document Security API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `RightsManagementServiceClient` object by using its default constructor.
   * Create a `RightsManagementServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `RightsManagementServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. PDF-Dokument abrufen.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern eines PDF-Dokuments, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Bestimmen Sie die Byte-Array-Größe, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Eine vorhandene Richtlinie auf das PDF-Dokument anwenden

   Wenden Sie eine Richtlinie auf das PDF-Dokument an, indem Sie die `RightsManagementServiceClient` `protectDocument` Objektmethode aufrufen und die folgenden Werte übergeben:

   * Das `BLOB` Objekt, das das PDF-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Ein Zeichenfolgenwert, der den Namen des Dokuments angibt.
   * Ein Zeichenfolgenwert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` Wert angeben, der dazu führt, dass der `MyPolicies` Richtliniensatz verwendet wird.
   * Ein Zeichenfolgenwert, der den Richtliniennamen angibt.
   * Ein Zeichenfolgenwert, der den Namen der User Manager-Domäne des Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein (wenn dieser Parameter null ist, muss der nächste Parameterwert `null`sein).
   * Ein Zeichenfolgenwert, der den Namen des kanonischen Namens des Benutzers des Benutzermanagers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein (wenn dieser Parameter null ist, muss der vorherige Parameterwert `null`sein).
   * Ein `RMLocale` Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein Zeichenfolgenausgabeparameter, mit dem der Richtlinienerkennungswert gespeichert wird.
   * Ein Zeichenfolgenausgabeparameter, mit dem der richtliniengeschützte Bezeichnerwert gespeichert wird.
   * Ein Parameter für die Zeichenfolgenausgabe, mit dem der Mime-Typ gespeichert wird (z. B. `application/pdf`).
   Die `protectDocument` Methode gibt ein `BLOB` Objekt zurück, das das richtliniengeschützte PDF-Dokument enthält.

1. Speichern Sie das PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des richtliniengeschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB` Objekts speichert, das von der `protectDocument` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine PDF-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Anwenden einer Richtlinie auf ein PDF-Dokument mithilfe der Webdienst-API&quot;

## Richtlinien aus PDF-Dokumenten entfernen {#removing-policies-from-pdf-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, wenn das Dokument nicht mehr durch eine Richtlinie geschützt werden soll. Wenn Sie ein richtliniengeschütztes Dokument mit einer neueren Richtlinie aktualisieren möchten, wird es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-4}

So entfernen Sie eine Richtlinie aus einem richtliniengeschützten PDF-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.
1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.
1. Speichern Sie das unbesicherte PDF-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Sie können ein richtliniengeschütztes PDF-Dokument abrufen, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem PDF-Dokument zu entfernen, das nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme ausgelöst.

**Richtlinie aus dem PDF-Dokument entfernen**

Sie können eine Richtlinie aus einem richtliniengeschützten PDF-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Andernfalls muss die zum Schützen eines Dokuments verwendete Richtlinie die `SWITCH_POLICY` Berechtigung enthalten, um eine Richtlinie aus einem PDF-Dokument zu entfernen. Der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer muss ebenfalls über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Ungesichertes PDF-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie aus einem PDF-Dokument entfernt hat, können Sie das unbesicherte PDF-Dokument als PDF-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Richtlinien auf PDF-Dokumente anwenden](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Eine Richtlinie mithilfe der Java-API aus einem PDF-Dokument entfernen {#remove-a-policy-from-a-pdf-document-using-the-java-api}

Entfernen Sie eine Richtlinie mithilfe der Document Security API (Java) aus einem richtliniengeschützten PDF-Dokument:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   * Erstellen Sie ein `DocumentManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getDocumentManager` aufrufen.
   * Entfernen Sie eine Richtlinie aus dem PDF-Dokument, indem Sie die `DocumentManager` Methode des `removeSecurity` Objekts aufrufen und das `com.adobe.idp.Document` Objekt übergeben, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das ein ungeschütztes PDF-Dokument enthält.

1. Speichern Sie das unbesicherte PDF-Dokument.

   * Create a `java.io.File` object and ensure that the file extension is PDF.
   * Rufen Sie die `Document` Methode des `copyToFile` Objekts auf, um den Inhalt des `Document` Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` Objekt verwenden, das von der `removeSecurity` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (SOAP-Modus): Eine Richtlinie mithilfe der Java-API aus einem PDF-Dokument entfernen&quot;

### Eine Richtlinie mithilfe der Webdienst-API entfernen {#remove-a-policy-using-the-web-service-api}

Eine Richtlinie mithilfe der Document Security API (Webdienst) aus einem richtliniengeschützten PDF-Dokument entfernen:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `DocumentSecurityServiceClient` object by using its default constructor.
   * Create a `DocumentSecurityServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `DocumentSecurityServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern des richtliniengeschützten PDF-Dokuments, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Entfernen Sie die Richtlinie aus dem PDF-Dokument.

   Entfernen Sie die Richtlinie aus dem PDF-Dokument, indem Sie die `DocumentSecurityServiceClient` Methode des `removePolicySecurity` Objekts aufrufen und das `BLOB` Objekt übergeben, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `BLOB` Objekt zurück, das ein ungeschütztes PDF-Dokument enthält.

1. Speichern Sie das unbesicherte PDF-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der die Dateiposition des nicht geschützten PDF-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB` Objekts speichert, das von der `removePolicySecurity` Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB` Objektfelds abrufen `MTOM` .
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Entfernen einer Richtlinie aus einem PDF-Dokument mithilfe der Webdienst-API&quot;

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Zugriff auf Dokumente sperren {#revoking-access-to-documents}

Sie können den Zugriff auf ein richtliniengeschütztes PDF-Dokument sperren, sodass Benutzer nicht auf alle Kopien des Dokuments zugreifen können. Wenn ein Benutzer versucht, ein gesperrtes PDF-Dokument zu öffnen, wird er an eine angegebene URL weitergeleitet, unter der ein überarbeitetes Dokument angezeigt werden kann. Die URL, zu der der Benutzer umgeleitet wird, muss programmgesteuert angegeben werden. Wenn Sie den Zugriff auf ein Dokument sperren, wird die Änderung wirksam, wenn sich der Benutzer das nächste Mal mit dem Document Security-Dienst synchronisiert, indem das richtliniengeschützte Dokument online geöffnet wird.

Die Möglichkeit, den Zugriff auf ein Dokument zu sperren, bietet zusätzliche Sicherheit. Nehmen Sie beispielsweise an, dass eine neuere Version eines Dokuments verfügbar ist und Sie möchten nicht mehr, dass sich jemand die veraltete Version ansieht. In diesem Fall kann der Zugriff auf das ältere Dokument gesperrt werden, und niemand kann das Dokument anzeigen, es sei denn, der Zugriff wird erneut aktiviert.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-5}

So sperren Sie ein richtliniengeschütztes Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes PDF-Dokument ab.
1. Sperren Sie das richtliniengeschützte Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen.

**Abrufen eines richtliniengeschützten PDF-Dokuments**

Sie müssen ein richtliniengeschütztes PDF-Dokument abrufen, um es zu sperren. Sie können ein Dokument, das bereits gesperrt wurde oder nicht richtliniengeschützt ist, nicht sperren.

Wenn Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments kennen, ist es nicht erforderlich, das richtliniengeschützte PDF-Dokument abzurufen. In den meisten Fällen müssen Sie jedoch das PDF-Dokument abrufen, um den Wert der Lizenzkennung abzurufen.

**Richtliniengeschütztes Dokument sperren**

Um ein richtliniengeschütztes Dokument zu sperren, geben Sie die Lizenzkennung des richtliniengeschützten Dokuments an. Darüber hinaus können Sie die URL eines Dokuments angeben, das der Benutzer beim Öffnen des gesperrten Dokuments anzeigen kann. Angenommen, ein veraltetes Dokument wird gesperrt. Wenn ein Benutzer versucht, das gesperrte Dokument zu öffnen, wird ihm statt des gesperrten Dokuments ein aktualisiertes Dokument angezeigt.

>[!NOTE]
>
>Wenn Sie versuchen, ein bereits gesperrtes Dokument zu sperren, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Richtlinien auf PDF-Dokumente anwenden](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Wiedereinsetzung des Zugriffs auf gesperrte Dokumente](protecting-documents-policies.md#reinstating-access-to-revoked-documents)

### Zugriff auf Dokumente mit der Java-API sperren {#revoke-access-to-documents-using-the-java-api}

Zugriff auf ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security API (Java) sperren:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das richtliniengeschützte PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Richtliniengeschütztes Dokument sperren

   * Erstellen Sie ein `DocumentManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getDocumentManager` aufrufen.
   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `DocumentManager` Objektmethode `getLicenseId` aufrufen. Übergeben Sie das `com.adobe.idp.Document` Objekt, das das richtliniengeschützte Dokument darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Wert der Lizenzkennung darstellt.
   * Erstellen Sie ein `LicenseManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getLicenseManager` aufrufen.
   * Sperren Sie das richtliniengeschützte Dokument, indem Sie die `LicenseManager` Objektmethode aufrufen und die folgenden Werte übergeben `revokeLicense` :

      * Ein Zeichenfolgenwert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert der `DocumentManager` Objektmethode `getLicenseId` an).
      * Ein statisches Datenelement der `License` Schnittstelle, das den Grund zum Sperren des Dokuments angibt. Sie können beispielsweise angeben `License.DOCUMENT_REVISED`.
      * Ein `java.net.URL` Wert, der den Speicherort des überarbeiteten Dokuments angibt. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie diese weiterleiten `null`.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (SOAP-Modus): Widerrufen eines Dokuments mit der Java-API&quot;

### Zugriff auf Dokumente mit der Webdienst-API sperren {#revoke-access-to-documents-using-the-web-service-api}

Zugriff auf ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security API (Webdienst) sperren:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security Client-API-Objekts

   * Create a `DocumentSecurityServiceClient` object by using its default constructor.
   * Create a `DocumentSecurityServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `DocumentSecurityServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Abrufen eines richtliniengeschützten PDF-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern eines richtliniengeschützten PDF-Dokuments, das gesperrt wird.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des zu widerrufenden richtliniengeschützten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Richtliniengeschütztes Dokument sperren

   * Rufen Sie den Wert der Lizenzkennung des richtliniengeschützten Dokuments ab, indem Sie die `DocumentSecurityServiceClient` Methode des `getLicenseID` Objekts aufrufen und das Objekt übergeben, das das richtliniengeschützte Dokument `BLOB` darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Sperren Sie das richtliniengeschützte Dokument, indem Sie die `DocumentSecurityServiceClient` Objektmethode aufrufen und die folgenden Werte übergeben `revokeLicense` :

      * Ein Zeichenfolgenwert, der den Wert der Lizenzkennung des richtliniengeschützten Dokuments angibt (geben Sie den Rückgabewert der `DocumentSecurityServiceService` Objektmethode `getLicenseId` an).
      * Ein statisches Datenelement der `Reason` Enum, das den Grund zum Sperren des Dokuments angibt. Sie können beispielsweise angeben `Reason.DOCUMENT_REVISED`.
      * Ein `string` Wert, der den URL-Speicherort des überarbeiteten Dokuments angibt. Wenn Sie einen Benutzer nicht zu einer anderen URL umleiten möchten, können Sie diese weiterleiten `null`.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Widerrufen eines Dokuments mit der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Widerrufen eines Dokuments mit der Webdienst-API&quot;

**Siehe auch**

[Richtlinien aus Word-Dokumenten entfernen](protecting-documents-policies.md#removing-policies-from-word-documents)

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wiedereinsetzung des Zugriffs auf gesperrte Dokumente {#reinstating-access-to-revoked-documents}

Sie können den Zugriff auf ein gesperrtes PDF-Dokument reaktivieren, sodass alle Kopien des gesperrten Dokuments für Benutzer zugänglich sind. Wenn ein Benutzer ein neu installiertes Dokument öffnet, das gesperrt wurde, kann der Benutzer das Dokument anzeigen.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-6}

So reaktivieren Sie den Zugriff auf ein gesperrtes PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.
1. Zugriff auf das gesperrte PDF-Dokument neu zuweisen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` Objekt.

**Abrufen der Lizenzkennung des gesperrten PDF-Dokuments**

Sie müssen die Lizenzkennung des gesperrten PDF-Dokuments abrufen, um ein gesperrtes PDF-Dokument erneut zu installieren. Nachdem Sie den Wert für die Lizenzkennung erhalten haben, können Sie ein gesperrtes Dokument erneut installieren. Wenn Sie versuchen, ein Dokument, das nicht widerrufen wird, erneut zu installieren, wird eine Ausnahme ausgelöst.

**Zugriff auf das gesperrte PDF-Dokument neu zuweisen**

Um den Zugriff auf ein gesperrtes PDF-Dokument erneut zu aktivieren, müssen Sie die Lizenzkennung des gesperrten Dokuments angeben. Wenn Sie versuchen, den Zugriff auf ein PDF-Dokument, das nicht gesperrt wird, erneut zu aktivieren, wird eine Ausnahme ausgelöst.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Richtlinien auf PDF-Dokumente anwenden](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Zugriff auf gesperrte Dokumente mit der Java-API neu zuordnen {#reinstate-access-to-revoked-documents-using-the-java-api}

Zugriff auf ein gesperrtes Dokument mit der Document Security API (Java) neu zuweisen:

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das gesperrte PDF-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.
   * Erstellen Sie ein `DocumentManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getDocumentManager` aufrufen.
   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `DocumentManager` Methode des `getLicenseId` Objekts aufrufen und das Objekt übergeben, das das gesperrte Dokument `com.adobe.idp.Document` darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.

1. Zugriff auf das gesperrte PDF-Dokument neu zuweisen.

   * Erstellen Sie ein `LicenseManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getLicenseManager` aufrufen.
   * Stellen Sie den Zugriff auf das gesperrte PDF-Dokument wieder her, indem Sie die `LicenseManager` Objektmethode aufrufen und den Wert für die Lizenzkennung des gesperrten Dokuments übergeben `unrevokeLicense` .

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (SOAP-Modus): Zugriff auf ein gesperrtes Dokument mit der Webdienst-API erneut aktivieren&quot;

### Zugriff auf gesperrte Dokumente mit der Webdienst-API neu zuordnen {#reinstate-access-to-revoked-documents-using-the-web-service-api}

Zugriff auf ein gesperrtes Dokument mit der Document Security API (Webdienst) neu zuweisen:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `DocumentSecurityServiceClient` object by using its default constructor.
   * Create a `DocumentSecurityServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `DocumentSecurityServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie die Lizenzkennung des gesperrten PDF-Dokuments ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt wird zum Speichern eines gesperrten PDF-Dokuments verwendet, auf das der Zugriff erneut aktiviert wird.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des gesperrten PDF-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Zugriff auf das gesperrte PDF-Dokument neu zuweisen.

   * Rufen Sie den Wert der Lizenzkennung des gesperrten Dokuments ab, indem Sie die `DocumentSecurityServiceClient` Methode des `getLicenseID` Objekts aufrufen und das Objekt übergeben, das das gesperrte Dokument `BLOB` darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der die Lizenzkennung darstellt.
   * Erneutes Zuweisen des Zugriffs auf das gesperrte PDF-Dokument durch Aufrufen der `DocumentSecurityServiceClient` Objektmethode und Übergeben eines Zeichenfolgenwerts, der den Lizenzkennungswert des gesperrten PDF-Dokuments angibt (Übergeben des Rückgabewerts der `unrevokeLicense` Objektmethode `DocumentSecurityServiceClient` `getLicenseId` ).

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Zugriff auf ein gesperrtes Dokument mit der Webdienst-API erneut aktivieren&quot;
* &quot;Kurzanleitung (SwaRef): Zugriff auf ein gesperrtes Dokument mit der Webdienst-API erneut aktivieren&quot;

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Richtliniengeschützte PDF-Dokumente überprüfen {#inspecting-policy-protected-pdf-documents}

Sie können die Document Security Service API (Java und Webdienst) verwenden, um richtliniengeschützte PDF-Dokumente zu überprüfen. Beim Überprüfen richtliniengeschützter PDF-Dokumente werden Informationen zum richtliniengeschützten PDF-Dokument zurückgegeben. Sie können beispielsweise die Richtlinie festlegen, die zum Schützen des Dokuments verwendet wurde, sowie das Datum, an dem das Dokument geschützt wurde.

Sie können diese Aufgabe nicht ausführen, wenn Ihre Version von LiveCycle 8.x oder eine frühere Version ist. Unterstützung für das Überprüfen richtliniengeschützter Dokumente wird in AEM Forms hinzugefügt. Wenn Sie versuchen, ein richtliniengeschütztes Dokument mit LiveCycle 8.x (oder früher) zu überprüfen, wird eine Ausnahme ausgelöst.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-7}

So prüfen Sie ein richtliniengeschütztes PDF-Dokument:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Dokument zur Überprüfung ab.
1. Informationen zum richtliniengeschützten Dokument abrufen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` Objekt.

**Abrufen eines richtliniengeschützten Dokuments zur Überprüfung**

Um ein richtliniengeschütztes Dokument zu überprüfen, rufen Sie es ab. Wenn Sie versuchen, ein Dokument zu überprüfen, das nicht durch eine Richtlinie geschützt ist oder gesperrt wird, wird eine Ausnahme ausgelöst.

**Dokument überprüfen**

Nachdem Sie ein richtliniengeschütztes Dokument abgerufen haben, können Sie es überprüfen.

**Informationen zum richtliniengeschützten Dokument abrufen**

Nachdem Sie ein richtliniengeschütztes PDF-Dokument geprüft haben, können Sie Informationen dazu abrufen. Sie können beispielsweise die Richtlinie festlegen, die zum Schützen des Dokuments verwendet wird.

Wenn Sie ein Dokument mit einer Richtlinie sichern, die zu &quot;Meine Richtlinien&quot;gehört, und dann aufrufen `RMInspectResult.getPolicysetName` oder `RMInspectResult.getPolicysetId`, wird null zurückgegeben.

Wenn das Dokument mit einer Richtlinie gesichert wird, die in einem Richtliniensatz enthalten ist (außer &quot;Meine Richtlinien&quot;), geben Sie gültige Zeichenfolgen zurück `RMInspectResult.getPolicysetName` und `RMInspectResult.getPolicysetId` geben Sie diese zurück.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Richtliniengeschützte PDF-Dokumente mit der Java-API überprüfen {#inspect-policy-protected-pdf-documents-using-the-java-api}

Überprüfen Sie ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security Service API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein. Weitere Informationen über den Speicherort dieser Dateien finden Sie unter [Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält. (Siehe [Einstellung von Verbindungseigenschaften](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie ein richtliniengeschütztes Dokument zur Überprüfung ab.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das richtliniengeschützte PDF-Dokument mit dessen Konstruktor darstellt. Übergeben Sie einen Zeichenfolgenwert, der den Speicherort des PDF-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Überprüfen Sie das Dokument.

   * Erstellen Sie ein `DocumentManager` Objekt, indem Sie die `RightsManagementClient` Objektmethode `getDocumentManager` aufrufen.
   * Überprüfen Sie das richtliniengeschützte Dokument, indem Sie die `LicenseManager` Objektmethode `inspectDocument` aufrufen. Übergeben Sie das `com.adobe.idp.Document` Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `RMInspectResult` Objekt zurück, das Informationen zum richtliniengeschützten Dokument enthält.

1. Informationen zum richtliniengeschützten Dokument abrufen.

   Um Informationen zum richtliniengeschützten Dokument abzurufen, rufen Sie die entsprechende Methode auf, die zum `RMInspectResult` Objekt gehört. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie die `RMInspectResult` Methode des `getPolicyName` Objekts auf.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (SOAP-Modus): Überprüfen richtliniengeschützter PDF-Dokumente mit der Java-API&quot;

### Richtliniengeschützte PDF-Dokumente mit der Webdienst-API überprüfen {#inspect-policy-protected-pdf-documents-using-the-web-service-api}

Überprüfen Sie ein richtliniengeschütztes PDF-Dokument mithilfe der Document Security Service API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `RightsManagementServiceClient` object by using its default constructor.
   * Create a `RightsManagementServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `RightsManagementServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie ein richtliniengeschütztes Dokument zur Überprüfung ab.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern eines zu prüfenden PDF-Dokuments.
   * Create a `System.IO.FileStream` object by invoking its constructor. Übergeben Sie einen Zeichenfolgenwert, der den Dateispeicherort des PDF-Dokuments und den Modus zum Öffnen der Datei darstellt.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die Stream-Länge zum Lesen.
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Überprüfen Sie das Dokument.

   Überprüfen Sie das richtliniengeschützte Dokument, indem Sie die `RightsManagementServiceClient` Objektmethode `inspectDocument` aufrufen. Übergeben Sie das `BLOB` Objekt, das das richtliniengeschützte PDF-Dokument enthält. Diese Methode gibt ein `RMInspectResult` Objekt zurück, das Informationen zum richtliniengeschützten Dokument enthält.

1. Informationen zum richtliniengeschützten Dokument abrufen.

   Um Informationen zum richtliniengeschützten Dokument abzurufen, rufen Sie den Wert des entsprechenden Felds ab, das zum `RMInspectResult` Objekt gehört. Um beispielsweise den Richtliniennamen abzurufen, rufen Sie den Wert des Felds des `RMInspectResult` Objekts `policyName` ab.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Überprüfen richtliniengeschützter PDF-Dokumente mit der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Überprüfen richtliniengeschützter PDF-Dokumente mit der Webdienst-API&quot;

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wasserzeichen erstellen {#creating-watermarks}

Wasserzeichen tragen dazu bei, die Sicherheit eines Dokuments zu gewährleisten, indem sie das Dokument eindeutig identifizieren und die Urheberrechtsverletzung kontrollieren. Sie können beispielsweise ein Wasserzeichen mit dem Status &quot;Vertraulich&quot;auf allen Seiten eines Dokuments erstellen und platzieren. Nachdem ein Wasserzeichen erstellt wurde, können Sie es als Teil einer Richtlinie einschließen. Das heißt, Sie können das Wasserzeichenattribut der Richtlinie mit dem neu erstellten Wasserzeichen festlegen. Nachdem eine Richtlinie, die ein Wasserzeichen enthält, auf ein Dokument angewendet wurde, wird das Wasserzeichen im richtliniengeschützten Dokument angezeigt.

>[!NOTE]
>
>Nur Benutzer mit Document Security-Administratorrechten können Wasserzeichen erstellen. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Document Security-Client-Objekts erforderlich sind.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-8}

So erstellen Sie ein Wasserzeichen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Legen Sie die Wasserzeichenattribute fest.
1. Registrieren Sie das Wasserzeichen beim Document Security-Dienst.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `RightsManagementClient` Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `RightsManagementServiceService` Objekt.

**Wasserzeichenattribute festlegen**

Um ein neues Wasserzeichen zu erstellen, müssen Sie Wasserzeichenattribute festlegen. Das Attribut name muss immer definiert sein. Zusätzlich zum Attribut name müssen Sie mindestens eines der folgenden Attribute festlegen:

* Benutzerdefinierter Text
* DateIncluded
* UserIdIncluded
* UserNameIncluded

In der folgenden Tabelle sind Schlüssel- und Wertpaare aufgeführt, die beim Erstellen eines Wasserzeichens mit Webdiensten erforderlich sind.

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
   <td><p>Gibt an, ob die Identifizierung des Benutzers, der das Dokument öffnet, Teil des Wasserzeichens ist.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_CURRENTDATE_ENABLED</code></p></td>
   <td><p>Gibt an, ob das aktuelle Datum Teil des Wasserzeichens ist.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code></p></td>
   <td><p>Wenn dieser Wert "true"ist, muss der Wert des benutzerdefinierten Textes mit <code>WaterBackCmd:SRCTEXT</code>angegeben werden.</p></td>
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
   <td><p>Wenn dieser Wert angegeben ist, <code>WaterBackCmd:IS_SIZE_ENABLED</code> muss er vorhanden sein und der Wert muss "true"sein. Wenn dieses Attribut nicht angegeben ist, passt das Standardverhalten auf die Seite.</p></td>
   <td><p>Ein Wert größer als 0.0 und kleiner gleich 1.0.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:HORIZ_ALIGN</code></p></td>
   <td><p>Gibt die horizontale Ausrichtung des Wasserzeichens an. Der Standardwert ist center.</p></td>
   <td><p>links, zentriert oder rechts</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:VERT_ALIGN</code></p></td>
   <td><p>Gibt die vertikale Ausrichtung des Wasserzeichens an. Der Standardwert ist center.</p></td>
   <td><p>oben, zentriert oder unten</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_USE_BACKGROUND</code></p></td>
   <td><p>Gibt an, ob das Wasserzeichen ein Hintergrund ist. Der Standardwert lautet false.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_SIZE_ENABLED</code></p></td>
   <td><p>True, wenn eine benutzerdefinierte Skala angegeben wurde. Wenn dieser Wert true ist, muss auch SCALE angegeben werden. Wenn dieser Wert "false"ist, passt der Standardwert auf die Seite.</p></td>
   <td><p>„True“ oder „False“</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:SRCTEXT</code></p></td>
   <td><p>Gibt den benutzerdefinierten Text für ein Wasserzeichen an. Ist dieser Wert vorhanden, <code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code> muss er ebenfalls vorhanden sein und auf "true"gesetzt sein.</p></td>
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

Bevor ein neues Wasserzeichen verwendet werden kann, muss es beim Document Security-Dienst registriert werden. Nachdem Sie ein Wasserzeichen registriert haben, können Sie es innerhalb von Richtlinien verwenden.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Richtlinien auf PDF-Dokumente anwenden](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Erstellen von Wasserzeichen mit der Java-API {#create-watermarks-using-the-java-api}

Erstellen Sie ein Wasserzeichen mit der Document Security API (Java):

1. Schließen Sie Projektdateien ein.

   Include client JAR files, such as the `adobe-rightsmanagement-client.jar`, in your Java project’s class path.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Festlegen der Wasserzeichenattribute

   * Erstellen Sie ein `Watermark` Objekt, indem Sie die statische `InfomodelObjectFactory` Objektmethode aufrufen `createWatermark` . Diese Methode gibt ein `Watermark` Objekt zurück.
   * Legen Sie das Namensattribut des Wasserzeichens fest, indem Sie die `Watermark` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Richtliniennamen angibt. `setName`
   * Legen Sie das Hintergrundattribut des Wasserzeichens fest, indem Sie die `Watermark` Methode des `setBackground` Objekts aufrufen und weitergeben `true`. Durch Festlegen dieses Attributs wird das Wasserzeichen im Hintergrund des Dokuments angezeigt.
   * Legen Sie das benutzerdefinierte Textattribut des Wasserzeichens fest, indem Sie die `Watermark` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Text des Wasserzeichens darstellt. `setCustomText`
   * Legen Sie das Deckkraftattribut des Wasserzeichens fest, indem Sie die `Watermark` Objektmethode aufrufen und einen ganzzahligen Wert übergeben, der die Deckkraft angibt, `setOpacity` um den Wert festzulegen. Der Wert 100 gibt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 bedeutet, dass das Wasserzeichen vollständig transparent ist.

1. Registrieren Sie das Wasserzeichen.

   * Erstellen Sie ein `WatermarkManager` Objekt, indem Sie die `RightsManagementClient` Objektmethode `getWatermarkManager` aufrufen. Diese Methode gibt ein `WatermarkManager` Objekt zurück.
   * Registrieren Sie das Wasserzeichen, indem Sie die `WatermarkManager` Methode des `registerWatermark` Objekts aufrufen und das `Watermark` Objekt übergeben, das das zu registrierende Wasserzeichen darstellt. Diese Methode gibt einen Zeichenfolgenwert zurück, der den Identifizierungswert des Wasserzeichens darstellt.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (SOAP-Modus): Erstellen eines Wasserzeichens mit der Java-API&quot;

### Erstellen von Wasserzeichen mit der Webdienst-API {#create-watermarks-using-the-web-service-api}

Erstellen Sie ein Wasserzeichen mithilfe der Document Security API (Webdienst):

1. Erstellen Sie ein Document Security Client-API-Objekt.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `RightsManagementServiceClient` object by using its default constructor.
   * Create a `RightsManagementServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `RightsManagementServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie ein `WatermarkSpec` Objekt, indem Sie den `WatermarkSpec` Konstruktor aufrufen.
   * Legen Sie den Namen des Wasserzeichens fest, indem Sie dem Datenmember des `WatermarkSpec` Objekts einen Zeichenfolgenwert zuweisen `name` .
   * Legen Sie das `id` Attribut des Wasserzeichens fest, indem Sie dem `WatermarkSpec` - `id` Datenmember des Objekts einen Zeichenfolgenwert zuweisen.
   * Erstellen Sie für jede Wasserzeicheneigenschaft ein separates `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Datenmember des `key` Objekts einen Wert zuweisen (z. B. `WaterBackCmd:OPACITY)`).
   * Legen Sie den Wert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Datenmember des `value` Objekts einen Wert zuweisen (z. B. `.25`).
   * Create a `MyArrayOf_xsd_anyType` object. Rufen Sie für jedes `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt die `MyArrayOf_xsd_anyType` Objektmethode `Add` auf. Pass the `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Weisen Sie das `MyArrayOf_xsd_anyType` Objekt dem `WatermarkSpec` Datenmember des Objekts zu `values` .

1. Registrieren Sie das Wasserzeichen.

   Registrieren Sie das Wasserzeichen, indem Sie die `RightsManagementServiceClient` Methode des `registerWatermark` Objekts aufrufen und das `WatermarkSpec` Objekt übergeben, das das zu registrierende Wasserzeichen darstellt.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Erstellen eines Wasserzeichens mit der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Erstellen eines Wasserzeichens mit der Webdienst-API&quot;

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Wasserzeichen ändern {#modifying-watermarks}

Sie können ein vorhandenes Wasserzeichen mit der Document Security Java-API oder der Webdienst-API ändern. Um Änderungen an einem vorhandenen Wasserzeichen vorzunehmen, rufen Sie es ab, ändern dessen Attribute und aktualisieren Sie es dann auf dem Server. Nehmen Sie beispielsweise an, Sie rufen ein Wasserzeichen ab und ändern dessen Deckkraftattribut. Bevor die Änderung wirksam wird, müssen Sie das Wasserzeichen aktualisieren.

Wenn Sie ein Wasserzeichen ändern, wirkt sich die Änderung auf künftige Dokumente aus, auf die das Wasserzeichen angewendet wird. Das bedeutet, dass vorhandene PDF-Dokumente, die das Wasserzeichen enthalten, nicht betroffen sind.

>[!NOTE]
>
>Nur Benutzer mit Document Security-Administratorrechten können Wasserzeichen ändern. Das heißt, Sie müssen einen solchen Benutzer angeben, wenn Sie Verbindungseinstellungen definieren, die zum Erstellen eines Document Security-Client-Objekts erforderlich sind.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-9}

So ändern Sie ein Wasserzeichen:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie das zu ändernde Wasserzeichen ab.
1. Legen Sie die Wasserzeichenattribute fest.
1. Aktualisieren Sie das Wasserzeichen.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` Objekt. Wenn Sie die Document Security-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` Objekt.

**Abrufen des zu ändernden Wasserzeichens**

Um ein Wasserzeichen zu ändern, müssen Sie ein vorhandenes Wasserzeichen abrufen. Sie können ein Wasserzeichen abrufen, indem Sie dessen Namen angeben oder dessen Bezeichnerwert angeben.

**Wasserzeichenattribute festlegen**

Um ein vorhandenes Wasserzeichen zu ändern, ändern Sie den Wert eines oder mehrerer Wasserzeichenattribute. Beim programmgesteuerten Aktualisieren eines Wasserzeichens mit einem Webdienst müssen Sie alle ursprünglich festgelegten Attribute einstellen, auch wenn sich der Wert nicht ändert. Angenommen, die folgenden Wasserzeichenattribute werden festgelegt: `WaterBackCmd:IS_USERID_ENABLED`, `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`, `WaterBackCmd:OPACITY`und `WaterBackCmd:SRCTEXT`. Obwohl das einzige Attribut, das Sie ändern möchten, `WaterBackCmd:OPACITY`müssen Sie die anderen Werte gut einstellen.

>[!NOTE]
>
>Wenn Sie ein Wasserzeichen mit der Java-API ändern, müssen Sie nicht alle Attribute angeben. Legen Sie das Wasserzeichenattribut fest, das Sie ändern möchten.

>[!NOTE]
>
>Informationen zu den Namen der Wasserzeichenattribute finden Sie unter Wasserzeichen [erstellen](protecting-documents-policies.md#creating-watermarks).

**Wasserzeichen aktualisieren**

Nachdem Sie die Attribute eines Wasserzeichens geändert haben, müssen Sie das Wasserzeichen aktualisieren.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Wasserzeichen erstellen](protecting-documents-policies.md#creating-watermarks)

### Wasserzeichen mithilfe der Java-API ändern {#modify-watermarks-using-the-java-api}

Ändern Sie ein Wasserzeichen mithilfe der Document Security API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Erstellen Sie ein `WatermarkManager` Objekt, indem Sie die `DocumentSecurityClient` `getWatermarkManager` Objektmethode aufrufen und einen Zeichenfolgenwert übergeben, der den Wasserzeichennamen angibt. Diese Methode gibt ein `Watermark` Objekt zurück, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   Legen Sie das Deckkraftattribut des Wasserzeichens fest, indem Sie die `Watermark` Objektmethode aufrufen und einen ganzzahligen Wert übergeben, der die Deckkraft angibt, `setOpacity` um den Wert festzulegen. Der Wert 100 gibt an, dass das Wasserzeichen vollständig undurchsichtig ist, und der Wert 0 bedeutet, dass das Wasserzeichen vollständig transparent ist.

   >[!NOTE]
   >
   >In diesem Beispiel wird nur das Attribut &quot;Deckkraft&quot;geändert.

1. Aktualisieren Sie das Wasserzeichen.

   * Aktualisieren Sie das Wasserzeichen, indem Sie die `WatermarkManager` Methode des `updateWatermark` Objekts aufrufen und das `Watermark` Objekt übergeben, dessen Attribut geändert wurde.

**Codebeispiele**

Codebeispiele, die den Document Security-Dienst verwenden, finden Sie im Schnellstart-Modus (SOAP-Modus): Ändern eines Wasserzeichens mithilfe des Java-API-Abschnitts

### Wasserzeichen mithilfe der Webdienst-API ändern {#modify-watermarks-using-the-web-service-api}

Ändern Sie ein Wasserzeichen mithilfe der Document Security API (Webdienst):

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `DocumentSecurityServiceClient` object by using its default constructor.
   * Create a `RightsManagementServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `DocumentSecurityServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Rufen Sie das zu ändernde Wasserzeichen ab.

   Rufen Sie das zu ändernde Wasserzeichen ab, indem Sie die `DocumentSecurityServiceClient` Objektmethode `getWatermarkByName` aufrufen. Übergeben Sie einen Zeichenfolgenwert, der den Wasserzeichennamen angibt. Diese Methode gibt ein `WatermarkSpec` Objekt zurück, das das zu ändernde Wasserzeichen darstellt.

1. Legen Sie die Wasserzeichenattribute fest.

   * Erstellen Sie für jede zu aktualisierende Wasserzeicheneigenschaft ein separates `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt.
   * Legen Sie den Schlüsselwert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Datenmember des `key` Objekts einen Wert zuweisen (z. B. `WaterBackCmd:OPACITY)`).
   * Legen Sie den Wert fest, indem Sie dem `MyMapOf_xsd_string_To_xsd_anyType_Item` Datenmember des `value` Objekts einen Wert zuweisen (z. B. `.50`).
   * Create a `MyArrayOf_xsd_anyType` object. Rufen Sie für jedes `MyMapOf_xsd_string_To_xsd_anyType_Item` Objekt die `MyArrayOf_xsd_anyType` Objektmethode `Add` auf. Pass the `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Weisen Sie das `MyArrayOf_xsd_anyType` Objekt dem `WatermarkSpec` Datenmember des Objekts zu `values` .

1. Aktualisieren Sie das Wasserzeichen.

   Aktualisieren Sie das Wasserzeichen, indem Sie die `DocumentSecurityServiceClient` Methode des `updateWatermark` Objekts aufrufen und das zu ändernde `WatermarkSpec` Objekt übergeben.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in der folgenden Kurzanleitung:

* &quot;Kurzanleitung (MTOM): Ändern eines Wasserzeichens mit der Webdienst-API&quot;

## Nach Ereignissen suchen {#searching-for-events}

Der Rights Management-Dienst verfolgt spezifische Aktionen wie das Anwenden einer Richtlinie auf ein Dokument, das Öffnen eines richtliniengeschützten Dokuments und das Sperren des Zugriffs auf Dokumente. Die Ereignisprüfung muss für den Rights Management-Dienst aktiviert sein, sonst werden Ereignisse nicht verfolgt.

Ereignisse fallen in eine der folgenden Kategorien:

* Administratorereignisse sind Aktionen, die sich auf einen Administrator beziehen, z. B. das Erstellen eines neuen Administratorkontos.
* Dokumentereignisse sind Aktionen im Zusammenhang mit einem Dokument, z. B. das Schließen eines richtliniengeschützten Dokuments.
* Richtlinienereignisse sind Aktionen im Zusammenhang mit einer Richtlinie, z. B. das Erstellen einer neuen Richtlinie.
* Dienstereignisse sind Aktionen im Zusammenhang mit dem Rights Management-Dienst, z. B. die Synchronisierung mit dem Benutzerordner.

Sie können mit der Rights Management Java-API oder der Webdienst-API nach bestimmten Ereignissen suchen. Durch Suchen nach Ereignissen können Sie Aufgaben ausführen, z. B. eine Protokolldatei bestimmter Ereignisse erstellen.

>[!NOTE]
>
>For more information about the Rights Management service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-10}

So suchen Sie nach einem Rights Management-Ereignis:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Rights Management Client-API-Objekt.
1. Geben Sie das zu suchende Ereignis an.
1. Suchen Sie nach dem Ereignis.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Rights Management Client-API-Objekt erstellen**

Bevor Sie einen Rights Management-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Rights Management-Dienstes erstellen. Wenn Sie die Java-API verwenden, erstellen Sie ein `DocumentSecurityClient` Objekt. Wenn Sie die Rights Management-Webdienst-API verwenden, erstellen Sie ein `DocumentSecurityServiceService` Objekt.

**Zu suchende Ereignisse angeben**

Sie müssen das zu suchende Ereignis angeben. Sie können beispielsweise nach dem Richtlinienerstellungsereignis suchen, das beim Erstellen einer neuen Richtlinie eintritt.

**Nach dem Ereignis suchen**

Nachdem Sie das zu suchende Ereignis angegeben haben, können Sie entweder die Rights Management Java-API oder die Rights Management-Webdienst-API verwenden, um nach dem Ereignis zu suchen.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Ereignisse mit der Java-API suchen {#search-for-events-using-the-java-api}

Suchen Sie mithilfe der Rights Management API (Java) nach Ereignissen:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Rights Management Client-API-Objekt erstellen

   Erstellen Sie ein `DocumentSecurityClient` Objekt, indem Sie dessen Konstruktor verwenden und ein `ServiceClientFactory` Objekt übergeben, das Verbindungseigenschaften enthält.

1. Zu suchende Ereignisse angeben

   * Erstellen Sie ein `EventManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getEventManager` aufrufen. Diese Methode gibt ein `EventManager` Objekt zurück.
   * Erstellen Sie ein `EventSearchFilter` Objekt, indem Sie den Konstruktor aufrufen.
   * Geben Sie das zu suchende Ereignis an, indem Sie die `EventSearchFilter` Objektmethode aufrufen und ein statisches Datenelement übergeben, das zur Klasse gehört, die das zu suchende Ereignis darstellt, und das zu durchsuchen `setEventCode` `EventManager` ist. Um beispielsweise nach dem Richtlinienerstellungsereignis zu suchen, übergeben Sie `EventManager.POLICY_CREATE_EVENT`.
   >[!NOTE]
   >
   >Sie können zusätzliche Suchkriterien definieren, indem Sie `EventSearchFilter` Objektmethoden aufrufen. Rufen Sie beispielsweise die `setUserName` Methode auf, um einen Benutzer anzugeben, der mit dem Ereignis verknüpft ist.

1. Nach dem Ereignis suchen

   Suchen Sie nach dem Ereignis, indem Sie die `EventManager` Methode des `searchForEvents` Objekts aufrufen und das `EventSearchFilter` Objekt übergeben, das die Ereignissuchkriterien definiert. Diese Methode gibt ein Array von `Event` Objekten zurück.

**Codebeispiele**

Codebeispiele für den Rights Management-Dienst finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (SOAP): Suchen nach Ereignissen mit der Java-API&quot;

### Ereignisse mithilfe der Webdienst-API suchen {#search-for-events-using-the-web-service-api}

Suchen Sie mithilfe der Rights Management API (Webdienst) nach Ereignissen:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Rights Management Client-API-Objekt erstellen

   * Create a `DocumentSecurityServiceClient` object by using its default constructor.
   * Create a `DocumentSecurityServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `DocumentSecurityServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Zu suchende Ereignisse angeben

   * Create an `EventSpec` object by using its constructor.
   * Geben Sie den Beginn des Zeitraums an, in dem das Ereignis auftrat, indem Sie den `EventSpec` Datenmember des `firstTime.date` Objekts mit der `DataTime` Instanz festlegen, die den Beginn des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Weisen Sie den Wert `true` dem `EventSpec` `firstTime.dateSpecified` Datenmember des Objekts zu.
   * Geben Sie das Ende des Zeitraums an, in dem das Ereignis auftrat, indem Sie den `EventSpec` Datenmember des `lastTime.date` `DataTime` Objekts mit einer Instanz festlegen, die das Ende des Datumsbereichs zum Zeitpunkt des Ereignisses darstellt.
   * Weisen Sie den Wert `true` dem `EventSpec` `lastTime.dateSpecified` Datenmember des Objekts zu.
   * Stellen Sie das zu suchende Ereignis ein, indem Sie dem `EventSpec` Datenmember des Objekts einen Zeichenfolgenwert zuweisen `eventCode` . In der folgenden Tabelle sind die numerischen Werte aufgeführt, die Sie dieser Eigenschaft zuweisen können:
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

1. Nach dem Ereignis suchen

   Suchen Sie nach dem Ereignis, indem Sie die `DocumentSecurityServiceClient` Methode des `searchForEvents` Objekts aufrufen und das `EventSpec` Objekt übergeben, das das zu suchende Ereignis und die maximale Anzahl von Ergebnissen darstellt. Diese Methode gibt eine `MyArrayOf_xsd_anyType` Sammlung zurück, bei der jedes Element eine `AuditSpec` Instanz ist. Mithilfe einer `AuditSpec` Instanz können Sie Informationen zum Ereignis abrufen, z. B. zu dem Zeitpunkt, zu dem es aufgetreten ist. Die `AuditSpec` Instanz enthält einen `timestamp` Datenmember, der diese Informationen angibt.

**Codebeispiele**

Codebeispiele für den Rights Management-Dienst finden Sie in den folgenden Kurzanleitungen:

* &quot;Kurzanleitung (MTOM): Suchen nach Ereignissen mit der Webdienst-API&quot;
* &quot;Kurzanleitung (SwaRef): Suchen nach Ereignissen mit der Webdienst-API&quot;

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[Aufrufen von AEM Forms mithilfe von SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Richtlinien auf Word-Dokumente anwenden {#applying-policies-to-word-documents}

Zusätzlich zu PDF-Dokumenten unterstützt der Rights Management-Dienst zusätzliche Dokumentformate wie eine Microsoft Word-Datei (DOC-Datei) und andere Microsoft Office-Dateiformate. Sie können beispielsweise eine Richtlinie auf ein Word-Dokument anwenden, um es zu schützen. Durch Anwendung einer Richtlinie auf ein Word-Dokument beschränken Sie den Zugriff auf das Dokument. Sie können eine Richtlinie nicht auf ein Dokument anwenden, wenn das Dokument bereits mit einer Richtlinie gesichert ist.

Sie können die Verwendung eines richtliniengeschützten Word-Dokuments nach der Verteilung überwachen. Das heißt, Sie können sehen, wie das Dokument verwendet wird und wer es verwendet. Sie können zum Beispiel herausfinden, wann jemand das Dokument geöffnet hat.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-11}

So wenden Sie eine Richtlinie auf ein Word-Dokument an:

1. Schließen Sie Projektdateien ein.
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein Word-Dokument ab, auf das eine Richtlinie angewendet wird.
1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.
1. Speichern Sie das richtliniengeschützte Word-Dokument.

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, müssen Sie ein Client-Objekt des Document Security-Dienstes erstellen.

**Word-Dokument abrufen**

Zum Anwenden einer Richtlinie müssen Sie ein Word-Dokument abrufen. Nachdem Sie eine Richtlinie auf das Word-Dokument angewendet haben, sind Benutzer bei der Verwendung des Dokuments eingeschränkt. Wenn die Richtlinie beispielsweise nicht das Öffnen des Dokuments im Offlinemodus aktiviert, müssen die Benutzer zum Öffnen des Dokuments online sein.

**Vorhandene Richtlinie auf Word-Dokument anwenden**

Um eine Richtlinie auf ein Word-Dokument anzuwenden, müssen Sie auf eine vorhandene Richtlinie verweisen und angeben, zu welchem Richtliniensatz die Richtlinie gehört. Der Benutzer, der die Verbindungseigenschaften einstellt, muss Zugriff auf die angegebene Richtlinie haben. Andernfalls tritt eine Ausnahme auf.

**Word-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie auf ein Word-Dokument angewendet hat, können Sie das richtliniengeschützte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Zugriff auf Dokumente sperren](protecting-documents-policies.md#revoking-access-to-documents)

### Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Java-API {#apply-a-policy-to-a-word-document-using-the-java-api}

Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Document Security API (Java):

1. Schließen Sie Projektdateien ein.

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `DocumentSecurityClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Word-Dokument abrufen.

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das Word-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   * Erstellen Sie ein `DocumentManager` Objekt, indem Sie die `DocumentSecurityClient` Objektmethode `getDocumentManager` aufrufen.
   * Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `DocumentManager` `protectDocument` Objektmethode aufrufen und die folgenden Werte übergeben:

      * Das `com.adobe.idp.Document` Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
      * Ein Zeichenfolgenwert, der den Namen des Dokuments angibt.
      * Ein Zeichenfolgenwert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` Wert angeben, der dazu führt, dass der `MyPolicies` Richtliniensatz verwendet wird.
      * Ein Zeichenfolgenwert, der den Richtliniennamen angibt.
      * Ein Zeichenfolgenwert, der den Namen der User Manager-Domäne des Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein (wenn dieser Parameter null ist, muss der nächste Parameterwert null sein).
      * Ein Zeichenfolgenwert, der den Namen des kanonischen Namens des Benutzers des Benutzermanagers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann `null` (wenn dieser Parameter `null`ist, muss der vorherige Parameterwert `null`sein).
      * Eine `com.adobe.livecycle.rightsmanagement.Locale` Variable, die das Gebietsschema darstellt, mit dem die MS Office-Vorlage ausgewählt wird. Dieser Parameterwert ist optional und Sie können ihn angeben `null`.
      Die `protectDocument` Methode gibt ein `RMSecureDocumentResult` Objekt zurück, das das richtliniengeschützte Word-Dokument enthält.


1. Speichern Sie das Word-Dokument.

   * Rufen Sie die `RMSecureDocumentResult` Methode des `getProtectedDoc` Objekts auf, um das richtliniengeschützte Word-Dokument abzurufen. Diese Methode gibt ein `com.adobe.idp.Document` Objekt zurück.
   * Create a `java.io.File` object and ensure that the file extension is DOC.
   * Rufen Sie die `com.adobe.idp.Document` Methode des `copyToFile` Objekts auf, um den Inhalt des `Document` Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` Objekt verwenden, das von der `getProtectedDoc` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in der folgenden Kurzanleitung:

* &quot;Kurzanleitung (SOAP-Modus): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Java-API&quot;

### Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Webdienst-API {#apply-a-policy-to-a-word-document-using-the-web-service-api}

Wenden Sie eine Richtlinie mithilfe der Document Security API (Webdienst) auf ein Word-Dokument an:

1. Schließen Sie Projektdateien ein.

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/DocumentSecurityService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen Sie ein Document Security Client-API-Objekt.

   * Create a `DocumentSecurityServiceClient` object by using its default constructor.
   * Create a `DocumentSecurityServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `DocumentSecurityServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Word-Dokument abrufen.

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern eines Word-Dokuments, auf das eine Richtlinie angewendet wird.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Bestimmen Sie die Byte-Array-Größe, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode `Read` aufrufen. Übergeben Sie das Bytearray, die Startposition und die zu lesende Stream-Länge.
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Wenden Sie eine vorhandene Richtlinie auf das Word-Dokument an.

   Wenden Sie eine Richtlinie auf das Word-Dokument an, indem Sie die `DocumentSecurityServiceClient` `protectDocument` Objektmethode aufrufen und die folgenden Werte übergeben:

   * Das `BLOB` Objekt, das das Word-Dokument enthält, auf das die Richtlinie angewendet wird.
   * Ein Zeichenfolgenwert, der den Namen des Dokuments angibt.
   * Ein Zeichenfolgenwert, der den Namen des Richtliniensatzes angibt, zu dem die Richtlinie gehört. Sie können einen `null` Wert angeben, der dazu führt, dass der `MyPolicies` Richtliniensatz verwendet wird.
   * Ein Zeichenfolgenwert, der den Richtliniennamen angibt.
   * Ein Zeichenfolgenwert, der den Namen der User Manager-Domäne des Benutzers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein (wenn dieser Parameter null ist, muss der nächste Parameterwert `null`sein).
   * Ein Zeichenfolgenwert, der den Namen des kanonischen Namens des Benutzers des Benutzermanagers darstellt, der Herausgeber des Dokuments ist. Dieser Parameterwert ist optional und kann null sein (wenn dieser Parameter null ist, muss der vorherige Parameterwert `null`sein).
   * Ein `RMLocale` Wert, der den Gebietsschemawert angibt (z. B. `RMLocale.en`).
   * Ein Zeichenfolgenausgabeparameter, mit dem der Richtlinienerkennungswert gespeichert wird.
   * Ein Zeichenfolgenausgabeparameter, mit dem der richtliniengeschützte Bezeichnerwert gespeichert wird.
   * Ein Parameter für die Zeichenfolgenausgabe, mit dem der Mime-Typ gespeichert wird (z. B. `application/doc`).
   Die `protectDocument` Methode gibt ein `BLOB` Objekt zurück, das das richtliniengeschützte Word-Dokument enthält.

1. Speichern Sie das Word-Dokument.

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des richtliniengeschützten Word-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB` Objekts speichert, das von der `protectDocument` Methode zurückgegeben wurde. Füllen Sie das Byte-Array, indem Sie den Wert des `BLOB` Datenelements des `MTOM` Objekts abrufen.
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.
   * Schreiben Sie den Inhalt des Byte-Arrays in eine Word-Datei, indem Sie die `System.IO.BinaryWriter` Objektmethode aufrufen und das Bytearray `Write` übergeben.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in der folgenden Kurzanleitung:

* &quot;Kurzanleitung (MTOM): Anwenden einer Richtlinie auf ein Word-Dokument mithilfe der Webdienst-API&quot;

## Richtlinien aus Word-Dokumenten entfernen {#removing-policies-from-word-documents}

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, um die Sicherheit aus dem Dokument zu entfernen. Das heißt, wenn das Dokument nicht mehr durch eine Richtlinie geschützt werden soll. Wenn Sie ein richtliniengeschütztes Word-Dokument mit einer neueren Richtlinie aktualisieren möchten, wird es effizienter, die Richtlinie zu wechseln, anstatt die Richtlinie zu entfernen und die aktualisierte Richtlinie hinzuzufügen.

>[!NOTE]
>
>For more information about the Document Security service, see [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Zusammenfassung der Schritte {#summary_of_steps-12}

So entfernen Sie eine Richtlinie aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen
1. Erstellen Sie ein Document Security Client-API-Objekt.
1. Rufen Sie ein richtliniengeschütztes Word-Dokument ab.
1. Entfernen Sie die Richtlinie aus dem Word-Dokument.
1. Ungesicherte Word-Dokumente speichern

**Projektdateien einschließen**

Schließen Sie die erforderlichen Dateien in Ihr Entwicklungsprojekt ein. Wenn Sie eine Clientanwendung mit Java erstellen, schließen Sie die erforderlichen JAR-Dateien ein. Wenn Sie Webdienste verwenden, stellen Sie sicher, dass Sie die Proxydateien einschließen.

**Erstellen eines Document Security Client-API-Objekts**

Bevor Sie einen Document Security-Dienstvorgang programmgesteuert durchführen können, erstellen Sie ein Client-Objekt des Document Security-Dienstes.

**Abrufen eines richtliniengeschützten Word-Dokuments**

Sie müssen ein richtliniengeschütztes Word-Dokument abrufen, um eine Richtlinie zu entfernen. Wenn Sie versuchen, eine Richtlinie aus einem Word-Dokument zu entfernen, das nicht durch eine Richtlinie geschützt ist, wird eine Ausnahme ausgelöst.

**Richtlinie aus dem Word-Dokument entfernen**

Sie können eine Richtlinie aus einem richtliniengeschützten Word-Dokument entfernen, sofern in den Verbindungseinstellungen ein Administrator angegeben ist. Andernfalls muss die zum Schützen eines Dokuments verwendete Richtlinie die `SWITCH_POLICY` Berechtigung enthalten, um eine Richtlinie aus einem Word-Dokument zu entfernen. Der in den AEM Forms-Verbindungseinstellungen angegebene Benutzer muss ebenfalls über diese Berechtigung verfügen. Andernfalls wird eine Ausnahme ausgelöst.

**Ungesichertes Word-Dokument speichern**

Nachdem der Document Security-Dienst eine Richtlinie aus einem Word-Dokument entfernt hat, können Sie das nicht geschützte Word-Dokument als DOC-Datei speichern.

**Siehe auch**

[Einbeziehung von AEM Forms Java-Bibliotheksdateien](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindungseigenschaften festlegen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Richtlinien auf Word-Dokumente anwenden](protecting-documents-policies.md#applying-policies-to-word-documents)

### Eine Richtlinie mithilfe der Java-API aus einem Word-Dokument entfernen {#remove-a-policy-from-a-word-document-using-the-java-api}

Entfernen Sie eine Richtlinie mithilfe der Document Security API (Java) aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Schließen Sie Client-JAR-Dateien wie &quot;adobe-rightsmanagement-client.jar&quot;im Klassenpfad Ihres Java-Projekts ein.

1. Erstellen eines Document Security Client-API-Objekts

   * Erstellen Sie ein `ServiceClientFactory`-&quot; -Objekt, das Verbindungseigenschaften enthält.
   * Erstellen Sie ein `RightsManagementClient`-Objekt, indem Sie seinen Konstruktor verwenden und das `ServiceClientFactory`-Objekt übergeben.

1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie ein `java.io.FileInputStream` Objekt, das das richtliniengeschützte Word-Dokument darstellt, indem Sie den Konstruktor verwenden und einen Zeichenfolgenwert übergeben, der den Speicherort des Word-Dokuments angibt.
   * Erstellen Sie ein `com.adobe.idp.Document`-Objekt, indem Sie seinen Konstruktor verwenden und das `java.io.FileInputStream`-Objekt übergeben.

1. Richtlinie aus dem Word-Dokument entfernen

   * Erstellen Sie ein `DocumentManager` Objekt, indem Sie die `RightsManagementClient` Objektmethode `getDocumentManager` aufrufen.
   * Entfernen Sie eine Richtlinie aus dem Word-Dokument, indem Sie die `DocumentManager` Methode des `removeSecurity` Objekts aufrufen und das `com.adobe.idp.Document` Objekt übergeben, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt ein `com.adobe.idp.Document` Objekt zurück, das ein ungeschütztes Word-Dokument enthält.

1. Ungesichertes Word-Dokument speichern

   * Create a `java.io.File` object and ensure that the file extension is DOC.
   * Rufen Sie die `Document` Methode des `copyToFile` Objekts auf, um den Inhalt des `Document` Objekts in die Datei zu kopieren (stellen Sie sicher, dass Sie das `Document` Objekt verwenden, das von der `removeSecurity` -Methode zurückgegeben wurde).

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in der folgenden Kurzanleitung:

* &quot;Kurzanleitung (SOAP-Modus): Entfernen einer Richtlinie aus einem Word-Dokument mit der Java-API&quot;

### Eine Richtlinie mithilfe der Webdienst-API aus einem Word-Dokument entfernen {#remove-a-policy-from-a-word-document-using-the-web-service-api}

Entfernen Sie eine Richtlinie mithilfe der Document Security API (Webdienst) aus einem richtliniengeschützten Word-Dokument:

1. Projektdateien einschließen

   Erstellen Sie ein Microsoft .NET-Projekt, das MTOM verwendet. Stellen Sie sicher, dass Sie die folgende WSDL-Definition verwenden: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Ersetzen Sie dies `localhost` durch die IP-Adresse des Servers, auf dem AEM Forms gehostet wird.

1. Erstellen eines Document Security Client-API-Objekts

   * Create a `RightsManagementServiceClient` object by using its default constructor.
   * Create a `RightsManagementServiceClient.Endpoint.Address` object by using the `System.ServiceModel.EndpointAddress` constructor. Übergeben Sie einen Zeichenfolgenwert, der die WSDL angibt, an den AEM Forms-Dienst (z. B. `http://localhost:8080/soap/services/RightsManagementService?WSDL`). Sie müssen das `lc_version` Attribut nicht verwenden. Dieses Attribut wird verwendet, wenn Sie eine Dienstreferenz erstellen.)
   * Erstellen Sie ein `System.ServiceModel.BasicHttpBinding` Objekt, indem Sie den Wert des `RightsManagementServiceClient.Endpoint.Binding` Felds abrufen. Wandeln Sie den Rückgabewert in `BasicHttpBinding` um.
   * Legen Sie für das `System.ServiceModel.BasicHttpBinding` Objektfeld `MessageEncoding` den Wert `WSMessageEncoding.Mtom`fest. Dieser Wert stellt sicher, dass MTOM verwendet wird.
   * Aktivieren Sie die einfache HTTP-Authentifizierung, indem Sie die folgenden Aufgaben ausführen:

      * Weisen Sie dem Feld den AEM Forms-Benutzernamen zu `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Weisen Sie dem Feld den entsprechenden Kennwortwert zu `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Weisen Sie dem Feld den Konstantenwert `HttpClientCredentialType.Basic` zu `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Weisen Sie dem Feld den Konstantenwert `BasicHttpSecurityMode.TransportCredentialOnly` zu `BasicHttpBindingSecurity.Security.Mode`.


1. Abrufen eines richtliniengeschützten Word-Dokuments

   * Erstellen Sie ein Objekt `BLOB`, indem Sie den Konstruktor verwenden. Das `BLOB` Objekt dient zum Speichern des richtliniengeschützten Word-Dokuments, aus dem die Richtlinie entfernt wird.
   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des Word-Dokuments und den Modus darstellt, in dem die Datei geöffnet werden soll.
   * Erstellen Sie ein Bytearray, das den Inhalt des `System.IO.FileStream` Objekts speichert. Sie können die Größe des Byte-Arrays bestimmen, indem Sie die `System.IO.FileStream` Objekteigenschaft `Length` abrufen.
   * Füllen Sie das Bytearray mit Stream-Daten, indem Sie die `System.IO.FileStream` Objektmethode aufrufen und das Bytearray, die Startposition und die zu lesende Stream-Länge übergeben `Read` .
   * Füllen Sie das `BLOB` Objekt, indem Sie seinem `MTOM` Feld den Inhalt des Byte-Arrays zuweisen.

1. Richtlinie aus dem Word-Dokument entfernen

   Entfernen Sie die Richtlinie aus dem Word-Dokument, indem Sie die `RightsManagementServiceClient` Methode des `removePolicySecurity` Objekts aufrufen und das `BLOB` Objekt übergeben, das das richtliniengeschützte Word-Dokument enthält. Diese Methode gibt ein `BLOB` Objekt zurück, das ein ungeschütztes Word-Dokument enthält.

1. Ungesichertes Word-Dokument speichern

   * Erstellen Sie ein `System.IO.FileStream` Objekt, indem Sie den Konstruktor aufrufen und einen Zeichenfolgenwert übergeben, der den Dateispeicherort des ungesicherten Word-Dokuments darstellt.
   * Erstellen Sie ein Bytearray, das den Dateninhalt des `BLOB` Objekts speichert, das von der `removePolicySecurity` Methode zurückgegeben wurde. Füllen Sie das Bytearray, indem Sie den Wert des `BLOB` Objektfelds abrufen `MTOM` .
   * Create a `System.IO.BinaryWriter` object by invoking its constructor and passing the `System.IO.FileStream` object.

**Codebeispiele**

Codebeispiele für die Verwendung des Document Security-Dienstes finden Sie in der folgenden Kurzanleitung:

* &quot;Kurzanleitung (MTOM): Entfernen einer Richtlinie aus einem Word-Dokument mithilfe der Webdienst-API&quot;

**Siehe auch**

[Aufrufen von AEM Forms mithilfe von MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
