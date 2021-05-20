---
title: SSL für WebSphere Application Server konfigurieren
seo-title: SSL für WebSphere Application Server konfigurieren
description: Erfahren Sie, wie Sie SSL für WebSphere Application Server konfigurieren.
seo-description: Erfahren Sie, wie Sie SSL für WebSphere Application Server konfigurieren.
uuid: f939a806-346e-41e0-b2c0-6d0ba83f8f6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 7c0efcb3-5b07-4090-9119-b7318c8b7980
exl-id: b0786b52-879e-4a24-9cc9-bd9dcb2473cc
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 96%

---

# SSL für WebSphere Application Server konfigurieren {#configuring-ssl-for-websphere-application-server}

In diesem Abschnitt werden die folgenden Schritte zum Konfigurieren von SSL für IBM WebSphere Application Server beschrieben.

## Lokales Benutzerkonto unter WebSphere erstellen {#creating-a-local-user-account-on-websphere}

Zum Aktivieren von SSL muss WebSphere in der Benutzerregistrierung des lokalen Betriebssystems Zugriff auf ein Benutzerkonto mit Administratorrechten haben:

* (Windows) Erstellen Sie einen neuen Benutzer in Administratorgruppe, der berechtigt ist, als Teil des Betriebssystems zu agieren. (Siehe [Windows-Benutzers für WebSphere erstellen](configuring-ssl-websphere-application-server.md#create-a-windows-user-for-websphere).)
* (Linux, UNIX) Der Benutzer kann ein Root-Benutzer oder ein anderer Benutzer mit Root-Berechtigungen sein. Wenn Sie SSL unter WebSphere aktivieren, verwenden Sie die Serverkennung und das Kennwort dieses Benutzers.

### Linux- oder UNIX-Benutzer für WebSphere erstellen  {#create-a-linux-or-unix-user-for-websphere}

1. Melden Sie sich als Root-Benutzer an.
1. Erstellen Sie einen Benutzer, indem Sie an einer Eingabeaufforderung den folgenden Befehl eingeben:

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
1. (UNIX mit aktiviertem SSL) Starten und beenden Sie WebSphere als Root-Benutzer.

### Windows-Benutzer für WebSphere erstellen  {#create-a-windows-user-for-websphere}

1. Melden Sie sich über ein Administrator-Benutzerkonto bei Windows an.
1. Wählen Sie **Start > Systemsteuerung > Verwaltung > Computerverwaltung > Lokale Benutzer und Gruppen** aus.
1. Klicken Sie mit der rechten Maustaste auf Benutzer und wählen Sie **Neuer Benutzer** aus.
1. Geben Sie in die entsprechenden Felder einen Benutzernamen und ein Kennwort ein und geben Sie weitere wichtige Informationen in die übrigen Felder ein.
1. Deaktivieren Sie die Option **Benutzer muss Kennwort bei der nächsten Anmeldung ändern**, klicken Sie auf **Erstellen** und dann auf **Schließen**.
1. Klicken Sie auf **Benutzer**, klicken Sie mit der rechten Maustaste auf den Benutzer, den Sie gerade erstellt haben, und wählen Sie dann **Eigenschaften** aus.
1. Klicken Sie auf die Registerkarte **Mitgliedschaft** und dann auf **Hinzufügen**.
1. Geben Sie in das Feld „Geben Sie die zu verwendenden Objektnamen ein“ den Namen `Administrators`. Klicken Sie auf „Namen überprüfen“, um sicherzustellen, dass der Gruppenname richtig ist.
1. Klicken Sie auf **OK** und dann erneut auf **OK**.
1. Wählen Sie **Start > Systemsteuerung > Verwaltung > Lokale Sicherheitsrichtlinie > Lokale Richtlinien**.
1. Klicken Sie auf „Zuweisen von Benutzerrechten“ und anschließend mit der rechten Maustaste auf „Einsetzen als Teil des Betriebssystems“. Wählen Sie dann „Eigenschaften“.
1. Klicken Sie auf **Benutzer oder Gruppe hinzufügen**.
1. Geben Sie in das Feld „Geben Sie die zu verwendenden Objektnamen ein“ den Namen des von Ihnen in Schritt 4 erstellten Benutzers ein und klicken Sie auf **Namen überprüfen**, um sicherzustellen, dass der Name richtig ist. Klicken Sie dann auf **OK**.
1. Klicken Sie auf **OK**, um das Dialogfeld „Eigenschaften von Einsetzen als Teil des Betriebssystems“ zu schließen.

### Konfigurieren Sie WebSphere, um den neu erstellten Benutzer als Administrator festzulegen.  {#configure-websphere-to-use-the-newly-created-user-as-administrator}

1. Vergewissern Sie sich, dass WebSphere ausgeführt wird.
1. Wählen Sie in der WebSphere Administrative Console **Security > Global Security**.
1. Wählen Sie unter „Administrative security“ **Administrative user roles**.
1. Klicken Sie auf „Add“ und führen Sie folgende Schritte aus:

   1. Geben Sie **&amp;ast;** in das Suchfeld ein und klicken Sie auf &quot;Suchen&quot;.
   1. Klicken Sie unter „Roles“ auf **Administrator**.
   1. Fügen Sie den neu erstellten Benutzer zu „Mapped to role“ hinzu und ordnen Sie ihn zu „Administrator“ zu.

1. Klicken Sie auf **OK** und speichern Sie die Änderungen.
1. Starten Sie das WebSphere-Profil erneut.

## Administrative Sicherheit aktivieren  {#enable-administrative-security}

1. Wählen Sie in der WebSphere Administrative Console **Security > Global Security**.
1. Klicken Sie auf **Security Configuration Wizard**.
1. Stellen Sie sicher, dass das Kontrollkästchen **Enable Application Security** aktiviert ist. Klicken Sie auf **Weiter**.
1. Wählen Sie **Federated Repositories** und klicken Sie auf **Next**.
1. Geben Sie die festzulegenden Berechtigungen an und klicken Sie auf **Next**.
1. Klicken Sie auf **Beenden**.
1. Starten Sie das WebSphere-Profil erneut.

   WebSphere startet unter Verwendung des standardmäßigen Keystore und Truststore.

## Aktivieren Sie SSL (Custom Key und Truststore)  {#enable-ssl-custom-key-and-truststore}

Truststores und Keystores können mithilfe ides Dienstprogramms „ikeyman“ oder über die Admin Console erstellt werden. Vergewissern Sie sich, dass der WebSphere-Installationspfad keine Klammern enthält, damit „ikeyman“ ordnungsgemäß funtkioniert.

1. Wählen Sie in der WebSphere Administrative Console **Security > SSL certificate and key management**.
1. Klicken Sie unter „Related items“ auf **Keystores and certificates**.
1. Vergewissern Sie sich, dass in der Dropdown-Liste **Key store usages** **SSL Keystores** ausgewählt ist. Klicken Sie auf **Neu**.
1. Geben Sie einen logischen Namen und eine Beschreibung ein.
1. Geben Sie den Pfad an, in dem Ihr Keystore erstellt werden soll. Wenn Sie bereits ein Keystore mit „ikeyman“ erstellt haben, geben Sie den Pfad zur Keystore-Datei an.
1. Geben Sie ein Kennwort an und bestätigen Sie es.
1. Wählen Sie den Keystore-Typ aus und klicken Sie auf **Apply**.
1. Speichern Sie die Master-Konfiguration.
1. Klicken Sie auf **Personal Certificate**.
1. Wenn Sie bereits einen mithilfe von „ikeyman“ erstellten Keystore hinzugefügt haben, wird Ihr Zertifikat angezeigt. Andernfalls müssen Sie ein neues selbst-unterzeichnetes Zertifikat hinzufügen, indem Sie die folgenden Schritte ausführen:

   1. Wählen Sie **Create > Self-signed Certificate**.
   1. Geben Sie entsprechende Werte im Zertifikatsformular an. Behalten Sie den Alias und den allgemeinen Namen als vollständig qualifizierten Domänennamen des Computers bei.
   1. Klicken Sie auf **Übernehmen**.

1. Wiederholen Sie die Schritte 2 bis 10 zum Erstellen eines Truststore.

## Verwenden benutzerdefinierter Keystore und Truststore auf dem Server  {#apply-custom-keystore-and-truststore-to-the-server}

1. Wählen Sie in der WebSphere Administrative Console **Security > SSL certificate and key management**.
1. Klicken Sie auf **Manage endpoint security configuration**. Die lokale Topologiezuordnung wird geöffnet.
1. Wählen Sie unter „Inbound“ das direkt untergeordnete Element der Knoten.
1. Wählen Sie unter „Related items“ **SSL configurations**.
1. Wählen Sie **NodeDeafultSSLSetting**.
1. Wählen Sie aus den Dropdown-Listen „Truststore Name“ und „Keystore Name“ die benutzerdefinierten Truststore und Keystore aus, die Sie erstellt haben.
1. Klicken Sie auf **Übernehmen**.
1. Speichern Sie die Master-Konfiguration.
1. Starten Sie das WebSphere-Profil erneut.

   Ihr Profil wird jetzt mit benutzerdefinierten SSL-Einstellungen und Ihrem Zertifikat ausgeführt.

## Aktivieren der Unterstützung für native AEM Forms-Anwendungen  {#enabling-support-for-aem-forms-natives}

1. Wählen Sie in der WebSphere Administrative Console **Security > Global Security**.
1. Erweitern Sie im Abschnitt „Authentication“ **RMI/IIOP Security** und klicken Sie auf **CSIv2 Inbound Communications**.
1. Vergewissern Sie sich, dass **SSL-supported** in der Dropdown-Liste „Transport“ ausgewählt ist.
1. Starten Sie das WebSphere-Profil erneut.

## WebSphere für die Konvertierung von mit HTTPS beginnenden URLs konfigurieren  {#configuring-websphere-to-convert-urls-that-begins-with-https}

Um mit HTTPS beginnende URLs zu konvertieren, fügen Sie ein Signiererzertifikat für die URL zum WebSphere-Server hinzu.

**Signiererzertifikat für eine HTTPS-Site erstellen**

1. Vergewissern Sie sich, dass WebSphere ausgeführt wird.
1. Wechseln Sie in der WebSphere Administrative Console zu den Signiererzertifikaten und klicken Sie auf „Security“ > „SSL Certificate and Key Management“ > „Key Stores and Certificates“ > „NodeDefaultTrustStore“ > „Signer certificates“.
1. Klicken Sie auf „Retrieve from port“ und führen Sie die folgenden Aufgaben aus:

   * Geben Sie in das Feld „Host“ die URL ein. Geben Sie beispielsweise `www.paypal.com`.
   * Geben Sie in das Feld „Port“ den Wert `443` ein. Dieser Anschluss ist der SSL-Standardanschluss.
   * Geben Sie in das Feld „Alias“ einen Alias ein.

1. Klicken Sie auf „Retrieve Signer Information“ und prüfen Sie, ob die Informationen abgerufen werden.
1. Klicken Sie auf „Apply“ und dann auf „Save“.

Die Konvertierung von HTML in PDF von der Site, deren Zertifikat hinzugefügt wurde, erfolgt nun über den Generate PDF-Dienst.

>[!NOTE]
>
>Es ist ein Signiererzertifikat erforderlich, damit eine Anwendung von WebSphere aus eine Verbindung zu SSL-Sites herstellen kann. Dieses wird von Java Secure Socket Extensions (JSSE) dazu verwendet, die Zertifikate zu prüfen, die die Remote-Seite der Verbindung bei einem SSL-Handshake sendet.

## Konfigurieren von dynamischen Ports  {#configuring-dynamic-ports}

IBM WebSphere erlaubt nicht mehrere Aufrufe von ORB.init (), wenn die globale Sicherheit aktiviert wurde. Sie können über die permanente Einschränkung unter https://www-01.ibm.com/support/docview.wss?uid=swg1PK58704 nachlesen.

Führen Sie die folgenden Schritte aus, um den Port als dynamisch festzulegen und das Problem zu lösen:

1. Wählen Sie in WebSphere Administrative Console **Servers** >**Server Types** >**WebSphere application servers**.
1. Wählen Sie bei den Voreinstellungen Ihren Server aus.
1. Erweitern Sie auf der Registerkarte **Configuration** unter **Communications** den Abschnitt **Ports** und klicken Sie auf **Details**.
1. Klicken Sie auf die folgenden Portnamen, ändern Sie nach Bedarf die **Portnummer** auf 0 und klicken Sie auf **OK**.

   * `ORB_LISTENER_ADDRESS`
   * `SAS_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_SERVERAUTH_LISTENER_ADDRESS`
   * `CSIV2_SSL_MUTUALAUTH_LISTENER_ADDRESS`

## Konfigurieren der sling.properties-Datei {#configure-the-sling-properties-file}

1. Öffnen Sie die Datei `[aem-forms_root]`\crx-repository\launchpad\sling.properties zur Bearbeitung.
1. Suchen Sie die Eigenschaft `sling.bootdelegation.ibm` und fügen Sie dem Wertefeld `com.ibm.websphere.ssl.*`hinzu. Das aktualisierte Feld sieht wie folgt aus:

   ```shell
   sling.bootdelegation.ibm=com.ibm.xml.*, com.ibm.websphere.ssl.*
   ```

1. Speichern Sie die Datei und starten Sie den Server neu.
