---
title: Creating an Invite External Users Handler
description: Creating an Invite External Users Handler
translation-type: tm+mt
source-git-commit: 92e5cc0b1934dad641357a22894e70a3660b774a
workflow-type: tm+mt
source-wordcount: '1102'
ht-degree: 1%

---


# Creating an Invite External Users Handler {#create-invite-external-users-handler}

You can create an Invite External Users Handler for the Rights Management service. An Invite External Users Handler enables the Rights Management service to invite external users to become Rights Management users. After a user becomes a Rights Management user, the user is able to perform tasks, such as opening a policy-protected PDF document. After the Invite External Users Handler is deployed to AEM Forms, you can use administration console to interact with it.

>[!NOTE]
>
>An Invite External Users Handler is a AEM Forms component. Before you create an Invite External Users Handler, it is recommended that you become familiar with creating components.

**Summary of steps**

To develop an Invite External Users Handler, you must perform the following steps:

1. Set up your development environment.
1. Define the Invite External Users Handler implementation.
1. Define the component XML file.
1. Deploy the Invite External Users Handler.
1. Test the Invite External Users Handler.

## Einrichten Ihrer Entwicklungs-Umgebung {#setting-up-development-environment}

Um Ihre Entwicklungs-Umgebung einzurichten, müssen Sie ein neues Java-Projekt erstellen, z. B. ein Eclipse-Projekt. Die unterstützte Eclipse-Version ist `3.2.1` oder höher.

Die Rights Management-SPI erfordert, dass die `edc-server-spi.jar` Datei im Klassenpfad des Projekts festgelegt wird. Wenn Sie diese JAR-Datei nicht referenzieren, können Sie die Rights Management-SPI nicht in Ihrem Java-Projekt verwenden. Diese JAR-Datei wird zusammen mit dem AEM Forms SDK im `[install directory]\Adobe\Adobe_Experience_Manager_forms\sdk\spi` Ordner installiert.

Zusätzlich zum Hinzufügen der `edc-server-spi.jar` Datei zum Klassenpfad Ihres Projekts müssen Sie auch die JAR-Dateien hinzufügen, die zur Verwendung der Rights Management Service API erforderlich sind. Diese Dateien werden benötigt, um die Rights Management Service API im Handler &quot;Externe Benutzer einladen&quot;zu verwenden.

## Definieren der Implementierung des Handlers für eingeladene externe Benutzer {#define-invite-external-users-handler}

Zum Entwickeln eines Handlers für eingeladene externe Benutzer müssen Sie eine Java-Klasse erstellen, die die `com.adobe.edc.server.spi.ersp.InvitedUserProvider` Schnittstelle implementiert. Diese Klasse enthält eine Methode mit dem Namen `invitedUser`, die der Rights Management-Dienst aufruft, wenn E-Mail-Adressen über die Seite &quot; **Hinzufügen eingeladene Benutzer** &quot;gesendet werden, auf die über Administration Console zugegriffen werden kann.

Die `invitedUser` Methode akzeptiert eine `java.util.List` Instanz, die als Zeichenfolge typisierte E-Mail-Adressen enthält, die von der Seite &quot; **Eingeladene Benutzer** &quot;gesendet werden. Die `invitedUser` Methode gibt ein Array von `InvitedUserProviderResult` Objekten zurück, bei dem es sich im Allgemeinen um eine Zuordnung von E-Mail-Adressen zu Benutzerobjekten handelt (geben Sie nicht null zurück).

>[!NOTE]
>
>Dieser Abschnitt demonstriert nicht nur, wie Sie einen Handler für externe eingeladene Benutzer erstellen, sondern verwendet auch die AEM Forms-API.

Die Implementierung des Handlers für eingeladene externe Benutzer enthält eine benutzerdefinierte Methode mit dem Namen `createLocalPrincipalAccount`. Diese Methode akzeptiert einen Zeichenfolgenwert, der eine E-Mail-Adresse als Parameterwert angibt. Die `createLocalPrincipalAccount` Methode setzt voraus, dass eine lokale Domäne namens `EDC_EXTERNAL_REGISTERED`vorhanden ist. Sie können diesen Domänennamen beliebig konfigurieren. Bei einer Produktionsanwendung sollten Sie jedoch möglicherweise in eine Unternehmensdomäne integrieren.

Die `createUsers` Methode durchläuft jede E-Mail-Adresse und erstellt ein entsprechendes User-Objekt (einen lokalen Benutzer in der `EDC_EXTERNAL_REGISTERED` Domäne). Schließlich wird die `doEmails` Methode aufgerufen. Diese Methode wird absichtlich als Stub in der Probe hinterlassen. In einer Produktionsimplementierung enthält sie Anwendungslogik zum Senden von Einladungs-E-Mail-Nachrichten an die neu erstellten Benutzer. Es bleibt im Beispiel, um den Ablauf der Anwendungslogik einer echten Anwendung zu demonstrieren.

### Definieren der Implementierung des Handlers für eingeladene externe Benutzer {#user-handler-implementation}

Die folgende Implementierung des Handlers für externe Benutzer akzeptiert E-Mail-Adressen, die von der Seite &quot;Hinzufügen eingeladene Benutzer&quot;gesendet werden, auf die über Administration Console zugegriffen werden kann.

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
>Diese Java-Klasse wird als JAVA-Datei mit dem Namen InviteExternalUsersSample.java gespeichert.

## Definieren der XML-Komponentendatei für den Autorisierungs-Handler {#define-component-xml-authorization-handler}

Sie müssen eine XML-Komponentendatei definieren, um die Komponente für die einladende externe Benutzerhandler bereitzustellen. Für jede Komponente ist eine XML-Datei vorhanden, die Metadaten zur Komponente enthält.

Die folgende `component.xml` Datei wird für den Handler zum Einladen externer Benutzer verwendet. Beachten Sie, dass der Dienstname `InviteExternalUsersSample` und der von diesem Dienst bereitgestellte Vorgang benannt sind `invitedUser`. Der Eingabeparameter ist eine `java.util.List` Instanz und der Ausgabewert ist ein Array von `com.adobe.edc.server.spi.esrp.InvitedUserProviderResult` Instanzen.

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

## Verpacken des Handlers für eingeladene externe Benutzer {#packaging-invite-external-users-handler}

Um den Handler für eingeladene externe Benutzer unter AEM Forms bereitzustellen, müssen Sie Ihr Java-Projekt in einer JAR-Datei verpacken. Sie müssen sicherstellen, dass die externen JAR-Dateien, von denen die Geschäftslogik des Handlers für externe eingeladene Benutzer abhängt, z. B. die Dateien `edc-server-spi.jar` und `adobe-rightsmanagement-client.jar` Dateien, ebenfalls in der JAR-Datei enthalten sind. Außerdem muss die XML-Komponentendatei vorhanden sein. Die `component.xml` Datei und die externen JAR-Dateien müssen sich im Stammverzeichnis der JAR-Datei befinden.

>[!NOTE]
>
>In unten stehender Abbildung wird eine `BootstrapImpl` Klasse angezeigt. In diesem Abschnitt wird nicht erläutert, wie eine `BootstrapImpl` Klasse erstellt wird.

Die folgende Abbildung zeigt den Inhalt des Java-Projekts, der in der JAR-Datei des Handlers für die Einladung externer Benutzer verpackt ist.

![Benutzer einladen](assets/ci_ci_InviteUsers.png)

A. Externe JAR-Dateien, die für die Komponente B erforderlich sind. JAVA-Datei

Sie müssen den Handler für eingeladene externe Benutzer in einer JAR-Datei verpacken. Beachten Sie, dass im vorherigen Diagramm .JAVA-Dateien aufgelistet sind. Nach dem Verpacken in eine JAR-Datei müssen auch die entsprechenden .CLASS-Dateien angegeben werden. Without the .CLASS files, the authorization handler does not work.

>[!NOTE]
>
>After you package the external authorization handler into a JAR file, you can deploy the component to AEM Forms. Only one invite external users handler can be deployed at a given time.

>[!NOTE]
>
>You can also programmatically deploy a component.

## Testing the invite external users handler {#testing-invite-external-users-handler}

To test the invite external users handler, you can add external users to invite by using administration console.

To add external users to invite using administration console:

1. Deploy the invite external users handler’s JAR file using Workbench.
1. Starten Sie den Anwendungsserver neu.
1. Melden Sie sich bei Administration Console an.
1. Click **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Configuration]** > Invited **[!UICONTROL User Registration]**.
1. Enable invited user registration by checking the **[!UICONTROL Enable invited user registration]** box. Under **[!UICONTROL Use Built-in registration system]**, click **[!UICONTROL No]**. Save your settings.
1. From the administration console home page, click **[!UICONTROL Settings]** > **[!UICONTROL User Management]** > **[!UICONTROL Domain Management]**.
1. Click **[!UICONTROL New Local Domain]**. On the following page, create a domain with the name and identifier value of `EDC_EXTERNAL_REGISTERED`. Speichern Sie Ihre Änderungen.
1. From the administration console home page, click **[!UICONTROL Services]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Invited and Local Users]**. Die Seite **[!UICONTROL Hinzufügen eingeladenen Benutzer]** wird angezeigt.
1. Geben Sie E-Mail-Adressen ein (da der aktuelle Einladungs-Handler für externe Benutzer keine E-Mail-Nachrichten sendet, muss die adressierte E-Mail-Adresse nicht gültig sein). Klicken Sie auf **[!UICONTROL OK]**. Die Benutzer werden zum System eingeladen.
1. Klicken Sie in der Startseite Administration Console auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Benutzerverwaltung]** > **[!UICONTROL Benutzer und Gruppen]**.
1. Geben Sie im Feld **[!UICONTROL Suchen]** eine von Ihnen angegebene E-Mail-Adresse ein. Klicken Sie auf &quot;Suchen &quot;.**** Der eingeladene Benutzer wird als Benutzer in der lokalen `EDC_EXTERNAL_REGISTERED` Domäne angezeigt.

>[!NOTE]
>
>Der Handler zum Einladen externer Benutzer schlägt fehl, wenn die Komponente beendet oder deinstalliert wird.
