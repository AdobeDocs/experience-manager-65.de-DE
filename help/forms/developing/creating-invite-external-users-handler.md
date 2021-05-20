---
title: Erstellen eines Handlers für eingeladene externe Benutzer
description: Erstellen eines Handlers für eingeladene externe Benutzer
role: Developer
exl-id: b0416716-dcc9-4f80-986a-b9660a7c8f6b
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 1%

---

# Erstellen eines Handlers für eingeladene externe Benutzer {#create-invite-external-users-handler}

**Beispiele und Beispiele in diesem Dokument gelten nur für die AEM Forms on JEE-Umgebung.**

Sie können einen Handler für eingeladene externe Rights Management für den-Dienst erstellen. Mit dem Handler &quot;Externe Benutzer einladen&quot;kann der Rights Management-Dienst externe Benutzer einladen, Rights Management-Benutzer zu werden. Nachdem ein Rights Management Benutzer wird, kann er Aufgaben ausführen, z. B. ein richtliniengeschütztes PDF-Dokument öffnen. Nachdem der Handler &quot;Externe Benutzer einladen&quot;in AEM Forms bereitgestellt wurde, können Sie mit Administration Console interagieren.

>[!NOTE]
>
>Ein Handler für eingeladene externe Benutzer ist eine AEM Forms-Komponente. Bevor Sie einen Handler für eingeladene externe Benutzer erstellen, sollten Sie sich mit dem Erstellen von Komponenten vertraut machen.

**Zusammenfassung der Schritte**

Um einen Handler für eingeladene externe Benutzer zu entwickeln, müssen Sie die folgenden Schritte ausführen:

1. Richten Sie Ihre Entwicklungsumgebung ein.
1. Definieren Sie die Implementierung des Handlers &quot;Externe Benutzer einladen&quot;.
1. Definieren Sie die XML-Komponentendatei.
1. Stellen Sie den Handler Externe Benutzer einladen bereit.
1. Testen Sie den Handler Externe Benutzer einladen .

## Einrichten der Entwicklungsumgebung {#setting-up-development-environment}

Um Ihre Entwicklungsumgebung einzurichten, müssen Sie ein neues Java-Projekt erstellen, z. B. ein Eclipse-Projekt. Die unterstützte Eclipse-Version ist `3.2.1` oder höher.

Für das Rights Management-SPI muss die `edc-server-spi.jar`-Datei im Klassenpfad Ihres Projekts festgelegt sein. Wenn Sie diese JAR-Datei nicht referenzieren, können Sie die Rights Management-SPI nicht in Ihrem Java-Projekt verwenden. Diese JAR-Datei wird mit dem AEM Forms SDK im Ordner `[install directory]\Adobe\Adobe_Experience_Manager_forms\sdk\spi` installiert.

Zusätzlich zum Hinzufügen der Datei `edc-server-spi.jar` zum Klassenpfad Ihres Projekts müssen Sie auch die JAR-Dateien hinzufügen, die zur Verwendung der Rights Management Service-API erforderlich sind. Diese Dateien sind erforderlich, um die Rights Management Service-API im Handler &quot;Externe Benutzer einladen&quot;zu verwenden.

## Definieren der Implementierung des Handlers für eingeladene externe Benutzer {#define-invite-external-users-handler}

Um einen Einladungs-Handler für externe Benutzer zu entwickeln, müssen Sie eine Java-Klasse erstellen, die die `com.adobe.edc.server.spi.ersp.InvitedUserProvider`-Schnittstelle implementiert. Diese Klasse enthält eine Methode mit dem Namen `invitedUser`, die der Rights Management-Dienst aufruft, wenn E-Mail-Adressen über die Seite **Eingeladene  hinzufügen** gesendet werden, auf die über Administration Console zugegriffen werden kann.

Die `invitedUser`-Methode akzeptiert eine `java.util.List`-Instanz, die E-Mail-Adressen mit Zeichenfolgen enthält, die von der Seite **Eingeladene Benutzer hinzufügen** gesendet werden. Die `invitedUser` -Methode gibt ein Array von `InvitedUserProviderResult` -Objekten zurück, bei denen es sich im Allgemeinen um eine Zuordnung von E-Mail-Adressen zu Benutzerobjekten handelt (geben Sie nicht null zurück).

>[!NOTE]
>
>In diesem Abschnitt wird nicht nur gezeigt, wie ein Handler für eingeladene externe Benutzer erstellt wird, sondern auch die AEM Forms-API verwendet.

Die Implementierung des Handlers für externe eingeladene Benutzer enthält eine benutzerdefinierte Methode namens `createLocalPrincipalAccount`. Diese Methode akzeptiert einen Zeichenfolgenwert, der eine E-Mail-Adresse als Parameterwert angibt. Die `createLocalPrincipalAccount`-Methode setzt voraus, dass eine lokale Domäne namens `EDC_EXTERNAL_REGISTERED` vorhanden ist. Sie können diesen Domänennamen so konfigurieren, dass er Ihren Vorstellungen entspricht. Bei einer Produktionsanwendung können Sie jedoch eine Integration in eine Unternehmensdomäne durchführen.

Die `createUsers`-Methode iteriert über jede E-Mail-Adresse und erstellt ein entsprechendes User-Objekt (einen lokalen Benutzer in der `EDC_EXTERNAL_REGISTERED`-Domäne). Schließlich wird die `doEmails`-Methode aufgerufen. Diese Methode wird absichtlich als Stub in der Probe hinterlassen. In einer Produktionsimplementierung würde dies die Anwendungslogik zum Senden von Einladungs-E-Mail-Nachrichten an die neu erstellten Benutzer enthalten. Es bleibt im Beispiel, um den Ablauf der Anwendungslogik einer echten Anwendung zu demonstrieren.

### Definieren der Implementierung des Handlers für eingeladene externe Benutzer {#user-handler-implementation}

Die folgende Implementierung des Handlers für eingeladene externe Benutzer akzeptiert E-Mail-Adressen, die von der Seite Eingeladene Benutzer hinzufügen gesendet werden, auf die über Administration Console zugegriffen werden kann.

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

Sie müssen eine Komponenten-XML-Datei definieren, um die Handler-Komponente für eingeladene externe Benutzer bereitzustellen. Für jede Komponente ist eine XML-Komponentendatei vorhanden, die Metadaten zur Komponente enthält.

Die folgende `component.xml`-Datei wird für den Handler &quot;Externe Benutzer einladen&quot;verwendet. Beachten Sie, dass der Dienstname `InviteExternalUsersSample` lautet und der von diesem Dienst bereitgestellte Vorgang `invitedUser` heißt. Der Eingabeparameter ist eine `java.util.List` -Instanz und der Ausgabewert ist ein Array von `com.adobe.edc.server.spi.esrp.InvitedUserProviderResult` -Instanzen.

### Definieren der Komponenten-XML-Datei für den Handler für eingeladene externe Benutzer {#component-xml-invite-external-users-handler}

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

Um den Handler zum Einladen externer Benutzer in AEM Forms bereitzustellen, müssen Sie Ihr Java-Projekt in eine JAR-Datei verpacken. Sie müssen sicherstellen, dass die externen JAR-Dateien, von denen die Geschäftslogik des Handlers für externe Benutzer einladen abhängt, wie z. B. die Dateien `edc-server-spi.jar` und `adobe-rightsmanagement-client.jar` ebenfalls in der JAR-Datei enthalten sind. Außerdem muss die XML-Komponentendatei vorhanden sein. Die `component.xml`-Datei und die externen JAR-Dateien müssen sich im Stammverzeichnis der JAR-Datei befinden.

>[!NOTE]
>
>In unten stehender Abbildung wird eine `BootstrapImpl`-Klasse angezeigt. In diesem Abschnitt wird nicht beschrieben, wie Sie eine `BootstrapImpl`-Klasse erstellen.

Die folgende Abbildung zeigt den Inhalt des Java-Projekts, der in die JAR-Datei des Handlers für eingeladene externe Benutzer gepackt ist.

![Benutzer einladen](assets/ci_ci_InviteUsers.png)

A. Externe JAR-Dateien, die für die Komponente erforderlich sind B. JAVA-Datei

Sie müssen den Handler für eingeladene externe Benutzer in eine JAR-Datei verpacken. Beachten Sie, dass im vorherigen Diagramm .JAVA-Dateien aufgelistet sind. Nach dem Verpacken in eine JAR-Datei müssen auch die entsprechenden .CLASS-Dateien angegeben werden. Ohne die .CLASS-Dateien funktioniert der Autorisierungs-Handler nicht.

>[!NOTE]
>
>Nachdem Sie den externen Autorisierungs-Handler in eine JAR-Datei verpackt haben, können Sie die Komponente in AEM Forms bereitstellen. Es kann jeweils nur ein einladender Handler für externe Benutzer bereitgestellt werden.

>[!NOTE]
>
>Sie können eine Komponente auch programmgesteuert bereitstellen.

## Testen des Handlers für eingeladene externe Benutzer {#testing-invite-external-users-handler}

Zum Testen des Handlers &quot;Einladen externer Benutzer&quot;können Sie externe Benutzer hinzufügen, die über Administration Console eingeladen werden sollen.

So fügen Sie externe Benutzer hinzu, die über Administration Console eingeladen werden:

1. Stellen Sie die JAR-Datei des Handlers für eingeladene externe Benutzer mithilfe von Workbench bereit.
1. Starten Sie den Anwendungsserver neu.
1. Melden Sie sich bei Administration Console an.
1. Klicken Sie auf **[!UICONTROL Dienste]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Konfiguration]** > Eingeladene **[!UICONTROL Benutzerregistrierung]**.
1. Aktivieren Sie die Registrierung für eingeladene Benutzer, indem Sie das Kontrollkästchen **[!UICONTROL Registrierung für eingeladene Benutzer aktivieren]** aktivieren. Klicken Sie unter **[!UICONTROL Integriertes Registrierungssystem verwenden]** auf **[!UICONTROL Nein]**. Speichern Sie Ihre Einstellungen.
1. Klicken Sie auf der Homepage von Administration Console auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Benutzerverwaltung]** > **[!UICONTROL Domänenverwaltung]**.
1. Klicken Sie auf **[!UICONTROL Neue lokale Domäne]**. Erstellen Sie auf der folgenden Seite eine Domäne mit dem Namen und Kennungswert `EDC_EXTERNAL_REGISTERED`. Speichern Sie Ihre Änderungen.
1. Klicken Sie auf der Homepage von Administration Console auf **[!UICONTROL Dienste]** > **[!UICONTROL Rights Management]** > **[!UICONTROL Eingeladene und lokale Benutzer]**. Die Seite **[!UICONTROL Eingeladenen Benutzer hinzufügen]** wird angezeigt.
1. Geben Sie E-Mail-Adressen ein (da der aktuelle Handler für externe Benutzer mit der Einladung keine E-Mail-Nachrichten sendet, muss die adressierte E-Mail nicht gültig sein). Klicken Sie auf **[!UICONTROL OK]**. Die Benutzer werden zum System eingeladen.
1. Klicken Sie auf der Homepage von Administration Console auf **[!UICONTROL Einstellungen]** > **[!UICONTROL Benutzerverwaltung]** > **[!UICONTROL Benutzer und Gruppen]**.
1. Geben Sie im Feld **[!UICONTROL Find]** eine von Ihnen angegebene E-Mail-Adresse ein. Klicken Sie auf &quot;Suchen &quot;.**** Der eingeladene Benutzer wird als Benutzer in der lokalen `EDC_EXTERNAL_REGISTERED`-Domäne angezeigt.

>[!NOTE]
>
>Der Handler &quot;Externe Benutzer einladen&quot;schlägt fehl, wenn die Komponente angehalten oder deinstalliert wird.
