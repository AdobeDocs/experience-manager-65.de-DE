---
title: Konfigurieren von SSL für WebSphere Application Server
description: Erfahren Sie, wie Sie SSL für WebSphere Application Server konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b0786b52-879e-4a24-9cc9-bd9dcb2473cc
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: ht
source-wordcount: '1220'
ht-degree: 100%

---

# Konfigurieren von SSL für WebSphere Application Server {#configuring-ssl-for-websphere-application-server}

In diesem Abschnitt werden die folgenden Schritte zum Konfigurieren von SSL für IBM WebSphere Application Server beschrieben.

## Erstellen eines lokalen Benutzerkontos unter WebSphere {#creating-a-local-user-account-on-websphere}

Zum Aktivieren von SSL muss WebSphere in der Benutzerregistrierung des lokalen Betriebssystems Zugriff auf ein Benutzerkonto mit Administratorrechten haben:

* (Windows) Erstellen Sie einen Windows-Benutzer oder eine -Benutzerin in der Administratorgruppe, der bzw. die berechtigt ist, als Teil des Betriebssystems zu agieren. (Siehe [Erstellen von Windows-Benutzenden für WebSphere](configuring-ssl-websphere-application-server.md#create-a-windows-user-for-websphere).)
* (Linux, UNIX) Der Benutzer bzw. die Benutzerin kann ein Root-Benutzer bzw. -Benutzerin oder eine andere Person mit Root-Berechtigungen sein. Wenn Sie SSL unter WebSphere aktivieren, verwenden Sie die Server-Kennung und das Kennwort dieser Person.

### Erstellen von Linux- oder UNIX-Benutzenden für WebSphere {#create-a-linux-or-unix-user-for-websphere}

1. Melden Sie sich als Root-Benutzer bzw. -Benutzerin an.
1. Erstellen Sie einen Benutzer oder eine Benutzerin, indem Sie an einer Eingabeaufforderung den folgenden Befehl eingeben:

   * (Linux und Sun Solaris) `useradd`
   * (IBM AIX) `mkuser`

1. Legen Sie das Kennwort des neuen Benutzers fest, indem Sie an der Eingabeaufforderung `passwd` eingeben.
1. (Linux und Solaris) Erstellen Sie eine Shadow-Kennwortdatei, indem Sie an der Eingabeaufforderung `pwconv` (ohne Parameter) eingeben.

   >[!NOTE]
   >
   >(Linux und Solaris) Die Sicherheitsregistrierung „Local OS“ für WebSphere Application Server funktioniert nur, wenn eine Shadow-Kennwortdatei vorhanden ist. Die Shadow-Kennwortdatei trägt in der Regel den Namen **/etc/shadow** und basiert auf der Datei. Wenn keine Shadow-Kennwortdatei vorhanden ist, tritt nach dem Aktivieren der globalen Sicherheit und dem Konfigurieren der Benutzerregistrierung als „Local OS“ ein Fehler auf.

1. Öffnen Sie die Gruppendatei aus dem Ordner „/etc“ in einem Texteditor.
1. Fügen Sie der Gruppe `root` den Benutzer hinzu, den Sie in Schritt 2 erstellt haben.
1. Speichern und schließen Sie die Datei.
1. (UNIX mit aktiviertem SSL) Starten und beenden Sie WebSphere als Root-Benutzer bzw. -Benutzerin.

### Erstellen von Windows-Benutzenden für WebSphere {#create-a-windows-user-for-websphere}

1. Melden Sie sich über ein Administrator-Benutzerkonto bei Windows an.
1. Wählen Sie **Start > Control Panel > Verwaltung > Computerverwaltung > Lokale Benutzer und Gruppen** aus.
1. Klicken Sie mit der rechten Maustaste auf „Benutzer“ und wählen Sie **Neuer Benutzer** aus.
1. Geben Sie in die entsprechenden Felder einen Benutzernamen und ein Kennwort ein und geben Sie weitere wichtige Informationen in die übrigen Felder ein.
1. Deaktivieren Sie die Option **Benutzer muss Kennwort bei der nächsten Anmeldung ändern**, klicken Sie auf **Erstellen** und dann auf **Schließen**.
1. Klicken Sie auf **Benutzer**, klicken Sie mit der rechten Maustaste auf die Person, die Sie erstellt haben, und wählen Sie dann **Eigenschaften** aus.
1. Klicken Sie auf die Registerkarte **Mitgliedschaft** und dann auf **Hinzufügen**.
1. Geben Sie in das Feld „Geben Sie die zu verwendenden Objektnamen ein“ den Namen `Administrators`. Klicken Sie auf „Namen überprüfen“, um sicherzustellen, dass der Gruppenname richtig ist.
1. Klicken Sie auf **OK** und dann erneut auf **OK**.
1. Wählen Sie **Start > Control Panel > Verwaltung > Lokale Sicherheitsrichtlinie > Lokale Richtlinien** aus.
1. Klicken Sie auf „Zuweisen von Benutzerrechten“ und anschließend mit der rechten Maustaste auf „Einsetzen als Teil des Betriebssystems“. Wählen Sie dann „Eigenschaften“ aus.
1. Klicken Sie auf **Benutzer oder Gruppe hinzufügen**.
1. Geben Sie in das Feld „Geben Sie die zu verwendenden Objektnamen ein“ den Namen der von Ihnen in Schritt 4 erstellten Person ein und klicken Sie auf **Namen überprüfen**, um sicherzustellen, dass der Name richtig ist. Klicken Sie dann auf **OK**.
1. Klicken Sie auf **OK**, um das Dialogfeld „Eigenschaften von Einsetzen als Teil des Betriebssystems“ zu schließen.

### Konfigurieren Sie WebSphere, um den neu erstellten Benutzer bzw. die neu erstellte Benutzerin als Admin festzulegen {#configure-websphere-to-use-the-newly-created-user-as-administrator}

1. Vergewissern Sie sich, dass WebSphere ausgeführt wird.
1. Wählen Sie in WebSphere Administrative Console **Security (Sicherheit) > Global Security (Globale Sicherheit)** aus.
1. Wählen Sie unter „Administrative security“ (Administrative Sicherheit) die Option **Administrative user roles** (Administrative Benutzerrollen) aus.
1. Klicken Sie auf „Add“ (Hinzufügen) und führen Sie folgende Schritte aus:

   1. Geben Sie im Suchfeld ***** ein und klicken Sie auf „Suchen“.
   1. Klicken Sie unter „Roles“ (Rollen) auf **Administrator** (Admin).
   1. Fügen Sie die neu erstellte Benutzerin bzw. den neu erstellten Benutzer zu „Mapped to role“ (Zugeordnet zur Rolle) hinzu und ordnen Sie diese Person der Rolle „Administrator“ (Admin) zu.

1. Klicken Sie auf **OK**, um die Änderungen zu speichern.
1. Starten Sie das WebSphere-Profil erneut.

## Aktivieren der administrativen Sicherheit {#enable-administrative-security}

1. Wählen Sie in der WebSphere Administrative Console **Security (Sicherheit) > Global Security (Globale Sicherheit)**.
1. Klicken Sie auf **Security Configuration Wizard**.
1. Stellen Sie sicher, dass das Kontrollkästchen **Enable Application Security (Anwendungssicherheit aktivieren)** aktiviert ist. Klicken Sie auf **Weiter**.
1. Wählen Sie **Federated Repositories** und klicken Sie auf **Weiter**.
1. Geben Sie die gewünschten Anmeldeinformationen an und klicken Sie auf **Weiter**.
1. Klicken Sie auf **Beenden**.
1. Starten Sie das WebSphere-Profil erneut.

   WebSphere verwendet zunächst den standardmäßigen Keystore und TrustStore.

## Aktivieren Sie SSL (Custom Key und Truststore) {#enable-ssl-custom-key-and-truststore}

Truststores und Keystores können mithilfe ides Dienstprogramms „ikeyman“ oder über die Admin Console erstellt werden. Vergewissern Sie sich, dass der WebSphere-Installationspfad keine Klammern enthält, damit „ikeyman“ ordnungsgemäß funktioniert.

1. Wählen Sie in der WebSphere Administrative Console **Security > SSL certificate and key management**.
1. Klicken Sie unter „Related items“ (Verwandte Eleme)nte auf **Keystores and certificates**.
1. Vergewissern Sie sich, dass in der Dropdown-Liste **Key store usages (Keystore-Verwendungen)** die Option **SSL Keystores** ausgewählt ist. Klicken Sie auf **Neu**.
1. Geben Sie einen logischen Namen und eine Beschreibung ein.
1. Geben Sie den Pfad an, in dem Ihr Keystore erstellt werden soll. Wenn Sie bereits ein Keystore mit „ikeyman“ erstellt haben, geben Sie den Pfad zur Keystore-Datei an.
1. Geben Sie ein Kennwort ein und bestätigen Sie es.
1. Wählen Sie den Keystore-Typ aus und klicken Sie auf **Übernehmen**.
1. Speichern Sie die primäre Konfiguration.
1. Klicken Sie auf **Persönliches Zertifikat**.
1. Wenn Sie bereits einen mithilfe von „ikeyman“ erstellten Keystore hinzugefügt haben, wird Ihr Zertifikat angezeigt. Andernfalls müssen Sie ein neues selbstsigniertes Zertifikat hinzufügen, indem Sie die folgenden Schritte ausführen:

   1. Klicken Sie auf **Erstellen > Selbstsigniertes Zertifikat**.
   1. Geben Sie die entsprechenden Werte im Zertifikatsformular an. Behalten Sie den Alias und den allgemeinen Namen als vollständig qualifizierten Domain-Namen des Computers bei.
   1. Klicken Sie auf **Übernehmen**.

1. Wiederholen Sie die Schritte 2 bis 10 zum Erstellen eines Truststores.

## Anwenden des benutzerdefinierten Keystores und Truststores auf den Server {#apply-custom-keystore-and-truststore-to-the-server}

1. Wählen Sie in der WebSphere Administrative Console **Security > SSL certificate and key management**.
1. Klicken Sie auf **Manage endpoint security configuration (Konfiguration der Endpunktsicherheit verwalten)**. Die lokale Topologiekarte wird geöffnet.
1. Wählen Sie unter „Inbound“ das direkt untergeordnete Element der Knoten.
1. Wählen Sie unter „Related items“ (Verwandte Elemente) die Option **SSL configurations**.
1. Wählen Sie **NodeDefaultSSLSetting**.
1. Wählen Sie aus den Dropdown-Listen „Truststore-Name“ und „Keystore-Name“ den benutzerdefinierten Truststore und Keystore aus, die Sie erstellt haben.
1. Klicken Sie auf **Übernehmen**.
1. Speichern Sie die primäre Konfiguration.
1. Starten Sie das WebSphere-Profil erneut.

   Ihr Profil wird jetzt mit benutzerdefinierten SSL-Einstellungen und Ihrem Zertifikat ausgeführt.

## Aktivieren der Unterstützung für native AEM Forms {#enabling-support-for-aem-forms-natives}

1. Wählen Sie in der WebSphere Administrative Console **Security > Global Security**.
1. Erweitern Sie im Abschnitt „Authentication“ die **RMI/IIOP security** und klicken Sie auf **CSIv2 inbound communications (Eingehende CSIv2-Kommunikationen)**.
1. Vergewissern Sie sich, dass **SSL-unterstützt** in der Dropdown-Liste „Transport“ ausgewählt ist.
1. Starten Sie das WebSphere-Profil erneut.

## Konfigurieren von WebSphere zum Konvertieren von URLs, die mit „https“ beginnen {#configuring-websphere-to-convert-urls-that-begins-with-https}

Um eine URL zu konvertieren, die mit „https“ beginnt, fügen Sie dem WebSphere-Server ein Signer-Zertifikat für diese URL hinzu.

**Erstellen eines Signer-Zertifikats für eine https-aktivierte Site**

1. Vergewissern Sie sich, dass WebSphere ausgeführt wird.
1. Navigieren Sie in WebSphere Administrative Console zu den Signaturgeberzertifikaten und klicken Sie auf „Security“ (Sicherheit) > „SSL Certificate and Key Management“ (Verwaltung von SSL-Zertifikaten und Schlüsseln) > „Key Stores and Certificates“ (Schlüsselspeicher und Zertifikate) > „NodeDefaultTrustStore“ > „Signer certificates“ (Signaturgeberzertifikate).
1. Klicken Sie auf „Retrieve from port“ (Abrufen von Port) und führen Sie die folgenden Aufgaben aus:

   * Geben Sie in das Feld „Host“ die URL ein. Geben Sie beispielsweise `www.paypal.com`.
   * Geben Sie in das Feld „Port“ den Wert `443` ein. Dieser Port ist der standardmäßige SSL-Port.
   * Geben Sie in das Feld „Alias“ einen Alias ein.

1. Klicken Sie auf „Retrieve Signer Information“ (Signaturgeberinformationen abrufen) und prüfen Sie, ob die Informationen abgerufen werden.
1. Klicken Sie auf „Apply“ (Anwenden) und dann auf „Save“ (Speichern).

Die Konvertierung von HTML in PDF von der Site, deren Zertifikat hinzugefügt wurde, erfolgt nun über den Generate PDF-Dienst.

>[!NOTE]
>
>Es ist ein Signaturgeberzertifikat erforderlich, damit eine Anwendung von WebSphere aus eine Verbindung zu SSL-Sites herstellen kann. Dieses wird von Java Secure Socket Extensions (JSSE) dazu verwendet, die Zertifikate zu prüfen, die die Remote-Seite der Verbindung bei einem SSL-Handshake sendet.

## Konfigurieren von dynamischen Ports {#configuring-dynamic-ports}

IBM WebSphere erlaubt nicht mehrere ORB.init()-Aufrufe, wenn die globale Sicherheit aktiviert wurde. Informationen über die dauerhafte Einschränkung finden Sie unter https://www-01.ibm.com/support/docview.wss?uid=swg1PK58704.

Führen Sie die folgenden Schritte aus, um den Port als dynamisch festzulegen und das Problem zu lösen:

1. Wählen Sie in WebSphere Administrative Console **Servers** (Server) > **Server Types** (Server-Typen) > **WebSphere application servers** (WebSphere-Anwendungs-Server) aus.
1. Wählen Sie in den Voreinstellungen Ihren Server aus.
1. Erweitern Sie auf der Registerkarte **Configuration** (Konfiguration) unter **Communications** (Kommunikation) den Abschnitt **Ports** und klicken Sie auf **Details**.
1. Klicken Sie auf die folgenden Port-Namen, ändern Sie nach Bedarf die **Port-Nummer** zu 0 und klicken Sie auf **OK**.

   * `ORB_LISTENER_ADDRESS`
   * `SAS_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_MUTUALAUTH_LISTENER_ADDRESS`

## Konfigurieren der sling.properties-Datei {#configure-the-sling-properties-file}

1. Öffnen Sie die Datei „`[aem-forms_root]`\crx-repository\launchpad\sling.properties“ zur Bearbeitung.
1. Suchen Sie die Eigenschaft `sling.bootdelegation.ibm` und fügen Sie `com.ibm.websphere.ssl.*` zu ihrem Wertfeld hinzu. Das aktualisierte Feld sieht wie folgt aus:

   ```shell
   sling.bootdelegation.ibm=com.ibm.xml.*, com.ibm.websphere.ssl.*
   ```

1. Speichern Sie die Datei und starten Sie den Server neu.
