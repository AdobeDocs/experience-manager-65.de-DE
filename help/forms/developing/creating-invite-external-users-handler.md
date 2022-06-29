---
title: Erstellen eines Handlers zum Einladen externer Benutzer
description: Erstellen eines Handlers zum Einladen externer Benutzer
role: Developer
exl-id: b0416716-dcc9-4f80-986a-b9660a7c8f6b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: ht
source-wordcount: '1116'
ht-degree: 100%

---

# Erstellen eines Handlers zum Einladen externer Benutzer {#create-invite-external-users-handler}

**Die Beispiele in diesem Dokument gelten nur für eine AEM Forms on JEE-Umgebung.**

Sie können einen Handler zum Einladen externer Benutzer für den Rights Management-Service erstellen. Mit dem Handler zum Einladen externer Benutzer ist der Rights Management-Service in der Lage, externe Benutzer einzuladen, damit diese zu Rights Management-Benutzern werden. Wenn ein Benutzer zum Rights Management-Benutzer wird, kann er bestimmte Aufgaben durchführen, wie z. B. ein richtliniengeschütztes PDF-Dokument öffnen. Sobald der Handler zum Einladen externer Benutzer in AEM Forms bereitgestellt wird, können Sie diesen mit der Administration-Console steuern.

>[!NOTE]
>
>Ein Handler zum Einladen externer Benutzer ist eine AEM Forms-Komponente. Bevor Sie einen Handler zum Einladen externer Benutzer erstellen, sollten Sie sich mit dem Erstellen von Komponenten vertraut machen.

**Zusammenfassung der Schritte**

Um einen Handler zum Einladen externer Benutzer einzurichten, müssen Sie die folgenden Schritte ausführen:

1. Richten Sie Ihre Entwicklungsumgebung ein.
1. Definieren Sie die Implementierung des Handlers zum Einladen externer Benutzer.
1. Definieren Sie die XML-Komponentendatei.
1. Stellen Sie den Handler zum Einladen externer Benutzer bereit.
1. Testen Sie den Handler zum Einladen externer Benutzer.

## Einrichten der Entwicklungsumgebung {#setting-up-development-environment}

Um Ihre Entwicklungsumgebung einzurichten, müssen Sie ein neues Java-Projekt erstellen, z. B. ein Eclipse-Projekt. Es wird die Eclipse-Version `3.2.1` oder höher unterstützt.

Die Rights Management-SPI erfordert es, dass die Datei `edc-server-spi.jar` im Klassenpfad Ihres Projekts deklariert wird. Wenn Sie diese JAR-Datei nicht angeben, können Sie die Rights Management-SPI nicht in Ihrem Java-Projekt verwenden. Diese JAR-Datei wird zusammen mit dem AEM Forms-SDK im Ordner `[install directory]\Adobe\Adobe_Experience_Manager_forms\sdk\spi` installiert.

Zusätzlich zu der Datei `edc-server-spi.jar` müssen Sie auch die JAR-Dateien zum Klassenpfad Ihres Projekts hinzufügen, die zur Verwendung der Rights Management Service-API erforderlich sind. Diese Dateien sind erforderlich, um die Rights Management Service-API im Handler zum Einladen externer Benutzer verwenden zu können.

## Definieren der Implementierung des Handlers zum Einladen externer Benutzer {#define-invite-external-users-handler}

Um einen Handler zum Einladen externer Benutzer zu entwickeln, müssen Sie eine Java-Klasse erstellen, die die `com.adobe.edc.server.spi.ersp.InvitedUserProvider`-Schnittstelle implementiert. Diese Klasse enthält eine Methode namens `invitedUser`, die der Rights Management-Service aufruft, wenn E-Mail-Adressen anhand der Seite **Eingeladene Benutzer hinzufügen** empfangen werden, auf die mithilfe der Administration-Console zugegriffen werden kann.

Die `invitedUser`-Methode akzeptiert eine `java.util.List`-Instanz, die E-Mail-Adressen, die über die Seite **Eingeladene Benutzer hinzufügen** verschickt werden, in Form von Zeichenfolgen enthält. Die `invitedUser`-Methode gibt ein Array von `InvitedUserProviderResult`-Objekten zurück, bei dem es sich normalerweise um eine Zuordnung von E-Mail-Adressen zu Benutzerobjekten handelt (gibt nicht null zurück).

>[!NOTE]
>
>In diesem Abschnitt wird gezeigt, wie ein Handler zum Einladen externer Benutzer erstellt wird, und darüber hinaus wird auch die AEM Forms-API verwendet.

Die Implementierung des Handlers zum Einladen externer Benutzer enthält eine benutzerdefinierte Methode namens `createLocalPrincipalAccount`. Diese Methode akzeptiert einen Zeichenfolgenwert, in dem eine E-Mail-Adresse als Parameter enthalten ist. Die `createLocalPrincipalAccount`-Methode setzt voraus, dass eine lokale Domain namens `EDC_EXTERNAL_REGISTERED` vorhanden ist. Sie können diesen Domain-Namen nach Belieben konfigurieren. Bei einem Produktionsprogramm sollten Sie diesen jedoch in eine Unternehmens-Domain integrieren.

Die `createUsers`-Methode durchläuft die einzelnen E-Mail-Adressen und erstellt jeweils ein entsprechendes Benutzerobjekt (einen lokalen Benutzer in der Domain `EDC_EXTERNAL_REGISTERED`). Schließlich wird die `doEmails`-Methode aufgerufen. Diese Methode wird absichtlich als Stub in der Probe hinterlassen. In einer Produktionsimplementierung würde sie die Programmlogik zum Senden von Einladungs-E-Mail-Nachrichten an die neu erstellten Benutzer enthalten. Der logische Ablauf eines echten Programms wird im Beispiel demonstriert werden.

### Definieren der Implementierung des Handlers zum Einladen externer Benutzer {#user-handler-implementation}

Die folgende Implementierung des Handlers zum Einladen externer Benutzer akzeptiert E-Mail-Adressen, die von der Seite „Eingeladene Benutzer hinzufügen“ gesendet werden, auf die über Administration Console zugegriffen werden kann.

```as3
package com.adobe.livecycle.samples.inviteexternalusers.provider; 
 
import com.adobe.edc.server.spi.ersp.*; 
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory; 
import com.adobe.idp.um.api.*; 
import com.adobe.idp.um.api.infomodel.*; 
import com.adobe.idp.um.api.impl.UMBaseLibrary; 
import com.adobe.livecycle.usermanager.client.DirectoryManagerServiceClient; 
 
import java.util.ArrayList; 
import java.util.Iterator; 
import java.util.List; 
 
public class InviteExternalUsersSample implements InvitedUserProvider 
{ 
       private ServiceClientFactory _factory = null; 
 
       private User createLocalPrincipalAccount(String email_address) throws Exception 
       { 
    String ret = null; 
 
    //  Assume the local domain already exists! 
    String domain = "EDC_EXTERNAL_REGISTERED"; 
         
    List aliases = new ArrayList(); 
    aliases.add( email_address ); 
         
    User local_user = UMBaseLibrary.createUser( email_address, domain, email_address ); 
    local_user.setCommonName( email_address ); 
    local_user.setEmail( email_address ); 
    local_user.setEmailAliases( aliases ); 
         
    //  You may wish to disable the local user until, for example, his registration is processed by a confirmation link 
    //local_user.setDisabled( true ); 
 
    DirectoryManager directory_manager = new DirectoryManagerServiceClient( _factory ); 
    String ret_oid = directory_manager.createLocalUser( local_user, null ); 
     
    if( ret_oid == null ) 
    { 
        throw new Exception( "FAILED TO CREATE PRINCIPAL FOR EMAIL ADDRESS: " + email_address ); 
    } 
 
    return local_user; 
       } 
 
       protected User[] createUsers( List emails ) throws Exception 
       { 
    ArrayList ret_users = new ArrayList(); 
 
    _factory = ServiceClientFactory.createInstance(); 
 
    Iterator iter = emails.iterator(); 
 
    while( iter.hasNext() ) 
    { 
        String current_email = (String)iter.next(); 
 
        ret_users.add( createLocalPrincipalAccount( current_email ) ); 
    } 
 
    return (User[])ret_users.toArray( new User[0] ); 
       } 
 
       protected void doInvitations(List emails) 
       { 
    //  Here you may choose to send the users who were created an invitation email 
    //  This step is completely optional, depending on your requirements.   
       } 
 
       public InvitedUserProviderResult[] invitedUser(List emails) 
       { 
    //  This sample demonstrates the workflow for inviting a user via email 
 
    try 
    { 
 
        User[] principals = createUsers(emails); 
 
        InvitedUserProviderResult[] result = new InvitedUserProviderResult[principals.length]; 
        for( int i = 0; i < principals.length; i++ ) 
        { 
        result[i] = new InvitedUserProviderResult(); 
 
        result[i].setEmail( (String)emails.get( i ) ); 
        result[i].setUser( principals[i] ); 
        } 
 
        doInvitations(emails); 
 
        System.out.println( "SUCCESSFULLY INVITED " + result.length + " USERS" ); 
 
        return result; 
 
    } 
    catch( Exception e ) 
    { 
        System.out.println( "FAILED TO INVITE USERS FOR INVITE USERS SAMPLE" ); 
        e.printStackTrace(); 
 
        return new InvitedUserProviderResult[0]; 
    } 
       } 
}
 
```

>[!NOTE]
>
>Diese Java-Klasse wird als JAVA-Datei mit dem Namen „InviteExternalUsersSample.java“ gespeichert.

## Definieren der XML-Komponentendatei für den Autorisierungs-Handler {#define-component-xml-authorization-handler}

Sie müssen eine XML-Komponentendatei definieren, um die Handler-Komponente zum Einladen externer Benutzer bereitzustellen. Für jede Komponente ist eine XML-Komponentendatei vorhanden, die Metadaten zur Komponente bereitstellt.

Die folgende `component.xml`-Datei wird für den Handler zum Einladen externer Benutzer verwendet. Beachten Sie, dass der Service-Name `InviteExternalUsersSample` lautet und der Vorgang, den dieser Service bereitstellt, heißt `invitedUser`. Der Eingabeparameter ist eine `java.util.List`-Instanz und der Ausgabewert ist ein Array von `com.adobe.edc.server.spi.esrp.InvitedUserProviderResult`-Instanzen.

### Definieren der XML-Komponentendatei für den Handler zum Einladen externer Benutzer {#component-xml-invite-external-users-handler}

```as3
<component xmlns="http://adobe.com/idp/dsc/component/document"> 
<component-id>com.adobe.livecycle.samples.inviteexternalusers</component-id> 
<version>1.0</version> 
<bootstrap-class>com.adobe.livecycle.samples.inviteexternalusers.provider.BootstrapImpl</bootstrap-class> 
<descriptor-class>com.adobe.idp.dsc.component.impl.DefaultPOJODescriptorImpl</descriptor-class> 
<services> 
<service name="InviteExternalUsersSample"> 
<specifications> 
<specification spec-id="com.adobe.edc.server.spi.ersp.InvitedUserProvider"/> 
</specifications> 
<specification-version>1.0</specification-version> 
<implementation-class>com.adobe.livecycle.samples.inviteexternalusers.provider.InviteExternalUsersSample</implementation-class> 
<auto-deploy category-id="Samples" service-id="InviteExternalUsersSample" major-version="1" minor-version="0"/> 
<operations> 
<operation name="invitedUser"> 
<input-parameter name="input" type="java.util.List" required="true"/> 
<output-parameter name="result" type="com.adobe.edc.server.spi.esrp.InvitedUserProviderResult[]"/> 
</operation> 
</operations> 
</service> 
</services> 
</component> 
```

## Verpacken des Handlers zum Einladen externer Benutzer {#packaging-invite-external-users-handler}

Um den Handler zum Einladen externer Benutzer in AEM Forms bereitzustellen, müssen Sie Ihr Java-Projekt in eine JAR-Datei packen. Sie müssen sicherstellen, dass die externen JAR-Dateien, von denen die Geschäftslogik des Handlers zum Einladen externer Benutzer abhängt, wie z. B. die Dateien `edc-server-spi.jar` und `adobe-rightsmanagement-client.jar` auch in der JAR-Datei enthalten sind. Außerdem muss die XML-Komponentendatei vorhanden sein. Die Datei `component.xml` und die externen JAR-Dateien müssen sich im Stammverzeichnis der JAR-Datei befinden.

>[!NOTE]
>
>In der unten stehenden Abbildung wird eine `BootstrapImpl`-Klasse dargestellt. In diesem Abschnitt wird nicht beschrieben, wie Sie eine `BootstrapImpl`-Klasse erstellen.

Die folgende Abbildung zeigt den Inhalt des Java-Projekts, der in die JAR-Datei des Handlers zum Einladen externer Benutzer gepackt wird.

![Benutzer einladen](assets/ci_ci_InviteUsers.png)

A. Externe JAR-Dateien, die für die Komponente erforderlich sind B. JAVA-Datei

Sie müssen den Handler zum Einladen externer Benutzer in eine JAR-Datei packen. Beachten Sie, dass im vorherigen Diagramm JAVA-Dateien aufgelistet sind. Nachdem die Dateien in eine JAR-Datei gepackt wurden, müssen auch die zugehörigen CLASS-Dateien angegeben werden. Ohne die CLASS-Dateien funktioniert der Autorisierungs-Handler nicht.

>[!NOTE]
>
>Nachdem Sie den externen Autorisierungs-Handler in eine JAR-Datei gepackt haben, können Sie die Komponente in AEM Forms bereitstellen. Es kann jeweils nur ein Handler zum Einladen externer Benutzer bereitgestellt werden.

>[!NOTE]
>
>Sie können eine Komponente auch programmgesteuert bereitstellen.

## Testen des Handlers zum Einladen externer Benutzer {#testing-invite-external-users-handler}

Um den Handler zum Einladen externer Benutzer zu testen, können Sie externe Benutzer hinzufügen, die über Administration Console eingeladen werden sollen.

So fügen Sie externe Benutzer hinzu, die über Administration Console eingeladen werden sollen:

1. Stellen Sie die JAR-Datei des Handlers zum Einladen externer Benutzer mithilfe von Workbench bereit.
1. Starten Sie den Anwendungsserver neu.
1. Melden Sie sich bei Administration Console an.
1. Klicken Sie auf **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Konfiguration]** > **[!UICONTROL Registrierung für eingeladene Benutzer]**.
1. Aktivieren Sie die Registrierung für eingeladene Benutzer, indem Sie die Option **[!UICONTROL Registrierung für eingeladene Benutzer aktivieren]** markieren. Klicken Sie unter **[!UICONTROL Integriertes Registrierungssystem verwenden]** auf **[!UICONTROL Nein]**. Speichern Sie Ihre Einstellungen.
1. Klicken Sie auf der Startseite von Administration Console auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Benutzerverwaltung]** > **[!UICONTROL Domain-Verwaltung]**.
1. Klicken Sie auf **[!UICONTROL Neue lokale Domain]**. Erstellen Sie auf der folgenden Seite eine Domain mit dem Namen und Kennungswert `EDC_EXTERNAL_REGISTERED`. Speichern Sie Ihre Änderungen.
1. Klicken Sie auf der Startseite von Administration Console auf **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Eingeladene und lokale Benutzer]**. Die Seite **[!UICONTROL Eingeladenen Benutzer hinzufügen]** wird angezeigt.
1. Geben Sie E-Mail-Adressen ein (da der aktuelle Handler zum Einladen externer Benutzer keine E-Mail-Nachrichten sendet, müssen die E-Mail-Adressen nicht gültig sein). Klicken Sie auf **[!UICONTROL OK]**. Die Benutzer werden zur Anmeldung im System eingeladen.
1. Klicken Sie auf der Startseite von Administration Console auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Benutzerverwaltung]** > **[!UICONTROL Benutzer und Gruppen]**.
1. Geben Sie in das Feld **[!UICONTROL Suchen]** eine von Ihnen angegebene E-Mail-Adresse ein. Klicken Sie auf **[!UICONTROL Suchen]**. Der eingeladene Benutzer wird als Benutzer in der lokalen `EDC_EXTERNAL_REGISTERED`-Domain angezeigt.

>[!NOTE]
>
>Der Handler zum Einladen externer Benutzer schlägt fehl, wenn die Komponente angehalten oder deinstalliert wird.
