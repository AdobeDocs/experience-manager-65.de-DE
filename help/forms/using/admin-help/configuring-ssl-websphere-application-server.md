---
title: Konfigurieren von SSL für WebSphere Application Server
description: Erfahren Sie, wie Sie SSL für WebSphere Application Server konfigurieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: b0786b52-879e-4a24-9cc9-bd9dcb2473cc
source-git-commit: 5bdf42d1ce7b2126bfb2670049deec4b6eaedba2
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 18%

---

# Konfigurieren von SSL für WebSphere Application Server {#configuring-ssl-for-websphere-application-server}

Dieser Abschnitt enthält die folgenden Schritte zum Konfigurieren von SSL mit Ihrem IBM WebSphere Application Server.

## Erstellen eines lokalen Benutzerkontos auf WebSphere {#creating-a-local-user-account-on-websphere}

Für die Aktivierung von SSL benötigt WebSphere Zugriff auf ein Benutzerkonto in der Benutzerregistrierung des lokalen Betriebssystems, das zur Verwaltung des Systems berechtigt ist:

* (Windows) Erstellen Sie einen neuen Windows-Benutzer, der der Gruppe &quot;Administratoren&quot;angehört und berechtigt ist, als Teil des Betriebssystems zu fungieren. (Siehe [Windows-Benutzer für WebSphere erstellen](configuring-ssl-websphere-application-server.md#create-a-windows-user-for-websphere).
* (Linux, UNIX) Der Benutzer kann ein Root-Benutzer oder ein anderer Benutzer mit Root-Berechtigungen sein. Wenn Sie SSL unter WebSphere aktivieren, verwenden Sie die Serverkennung und das Kennwort dieses Benutzers.

### Linux- oder UNIX-Benutzer für WebSphere erstellen {#create-a-linux-or-unix-user-for-websphere}

1. Melden Sie sich als Root-Benutzer an.
1. Erstellen Sie einen Benutzer, indem Sie den folgenden Befehl an einer Eingabeaufforderung eingeben:

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

### Windows-Benutzer für WebSphere erstellen {#create-a-windows-user-for-websphere}

1. Melden Sie sich mit einem Administrator-Benutzerkonto bei Windows an.
1. Auswählen **Start > Systemsteuerung > Verwaltung > Computerverwaltung > Lokale Benutzer und Gruppen**.
1. Klicken Sie mit der rechten Maustaste auf Benutzer und wählen Sie **Neuer Benutzer**.
1. Geben Sie einen Benutzernamen und ein Kennwort in die entsprechenden Felder ein und geben Sie in die übrigen Felder alle weiteren erforderlichen Informationen ein.
1. Auswahl deaktivieren **Der Benutzer muss das Kennwort bei der nächsten Anmeldung ändern** klicken **Erstellen** und klicken Sie anschließend auf **Schließen**.
1. Klicks **Benutzer**, klicken Sie mit der rechten Maustaste auf den soeben erstellten Benutzer und wählen Sie **Eigenschaften**.
1. Klicken Sie auf **Mitglied von** und klicken Sie auf **Hinzufügen**.
1. Geben Sie in das Feld „Geben Sie die zu verwendenden Objektnamen ein“ den Namen `Administrators`. Klicken Sie auf „Namen überprüfen“, um sicherzustellen, dass der Gruppenname richtig ist.
1. Klicks **OK** und klicken Sie anschließend auf **OK** erneut.
1. Auswählen **Start > Systemsteuerung > Verwaltung > Lokale Sicherheitsrichtlinie > Lokale Richtlinien**.
1. Klicken Sie auf &quot;Zuweisung von Benutzerrechten&quot;, klicken Sie dann mit der rechten Maustaste auf Als Teil des Betriebssystems arbeiten und wählen Sie Eigenschaften aus.
1. Klicks **Benutzer oder Gruppe hinzufügen**.
1. Geben Sie im Feld &quot;Geben Sie die zu verwendenden Objektnamen ein&quot;den Namen des Benutzers ein, den Sie in Schritt 4 erstellt haben, und klicken Sie auf **Namen überprüfen** , um sicherzustellen, dass der Name korrekt ist, und klicken Sie dann auf **OK**.
1. Klicks **OK** , um das Dialogfeld Eigenschaften des Betriebssystems zu schließen.

### WebSphere für die Verwendung des neu erstellten Benutzers als Administrator konfigurieren {#configure-websphere-to-use-the-newly-created-user-as-administrator}

1. Stellen Sie sicher, dass WebSphere ausgeführt wird.
1. Wählen Sie in WebSphere Administrative Console **Sicherheit > Globale Sicherheit**.
1. Wählen Sie unter &quot;Administrative security&quot;die Option **Administratorrollen**.
1. Klicken Sie auf Hinzufügen und führen Sie die folgenden Schritte aus:

   1. Geben Sie im Suchfeld ***** ein und klicken Sie auf „Suchen“.
   1. Klicks **Administrator** unter Rollen.
   1. Fügen Sie den neu erstellten Benutzer der Rolle &quot;Mapped to role&quot;hinzu und ordnen Sie ihn Administrator zu.

1. Klicks **OK** und speichern Sie Ihre Änderungen.
1. Starten Sie das WebSphere-Profil neu.

## Administrative Sicherheit aktivieren {#enable-administrative-security}

1. Wählen Sie in WebSphere Administrative Console **Sicherheit > Globale Sicherheit**.
1. Klicks **Sicherheitskonfigurationsassistent**.
1. Sichern **Anwendungssicherheit aktivieren** aktiviert ist. Klicken Sie auf **Weiter**.
1. Auswählen **Federated Repositorys** und klicken **Nächste**.
1. Geben Sie die festzulegenden Berechtigungen an und klicken Sie auf **Nächste**.
1. Klicken Sie auf **Beenden**.
1. Starten Sie das WebSphere-Profil neu.

   WebSphere verwendet zunächst den standardmäßigen Keystore und TrustStore.

## Aktivieren Sie SSL (benutzerdefinierten Schlüssel und TrustStore) {#enable-ssl-custom-key-and-truststore}

Truststores und Keystores können mit dem Dienstprogramm ikeyman oder der Admin Console erstellt werden. Damit ikeyman ordnungsgemäß funktioniert, stellen Sie sicher, dass der WebSphere-Installationspfad keine Klammern enthält.

1. Wählen Sie in WebSphere Administrative Console **Sicherheit > SSL-Zertifikat und Schlüsselverwaltung**.
1. Klicks **Keystores und Zertifikate** unter Verwandte Artikel.
1. Im **Schlüsselspeicherverwendung** Dropdown-Liste, stellen Sie sicher, dass **SSL-Schlüssel** ausgewählt ist. Klicken Sie auf **Neu**.
1. Geben Sie einen logischen Namen und eine Beschreibung ein.
1. Geben Sie den Pfad an, in dem Ihr Keystore erstellt werden soll. Wenn Sie bereits einen Keystore über &quot;ikeyman&quot;erstellt haben, geben Sie den Pfad zur Keystore-Datei an.
1. Geben Sie das Kennwort an und bestätigen Sie es.
1. Wählen Sie den Keystore-Typ aus und klicken Sie auf **Anwenden**.
1. Speichern Sie die Master-Konfiguration.
1. Klicks **Persönliches Zertifikat**.
1. Wenn Sie bereits einen Keystore mit ikeyman erstellt haben, wird Ihr Zertifikat angezeigt. Andernfalls müssen Sie ein neues selbstsigniertes Zertifikat hinzufügen, indem Sie die folgenden Schritte ausführen:

   1. Auswählen **Erstellen > Selbstsigniertes Zertifikat**.
   1. Geben Sie die entsprechenden Werte im Zertifikatformular an. Achten Sie darauf, Alias und den allgemeinen Namen als vollständig qualifizierten Domänennamen des Computers zu verwenden.
   1. Klicken Sie auf **Übernehmen**.

1. Wiederholen Sie die Schritte 2 bis 10 für die Erstellung eines TrustStore.

## Anwenden von benutzerdefiniertem Keystore und TrustStore auf den Server {#apply-custom-keystore-and-truststore-to-the-server}

1. Wählen Sie in WebSphere Administrative Console **Sicherheit > SSL-Zertifikat und Schlüsselverwaltung**.
1. Klicks **Konfiguration der Endpunktsicherheit verwalten**. Die lokale Topologiemap wird geöffnet.
1. Wählen Sie unter &quot;Eingehend&quot;das direkt untergeordnete Element der Knoten aus.
1. Wählen Sie unter Verwandte Elemente die Option **SSL-Konfigurationen**.
1. Auswählen **NodeDeafultSSLSetting**.
1. Wählen Sie aus den Dropdownlisten Truststore name and keystore name den von Ihnen erstellten benutzerdefinierten Truststore und Keystore aus.
1. Klicken Sie auf **Übernehmen**.
1. Speichern Sie die Master-Konfiguration.
1. Starten Sie das WebSphere-Profil neu.

   Ihr Profil wird jetzt mit benutzerdefinierten SSL-Einstellungen und Ihrem Zertifikat ausgeführt.

## Aktivieren der Unterstützung für native AEM Forms {#enabling-support-for-aem-forms-natives}

1. Wählen Sie in WebSphere Administrative Console **Sicherheit > Globale Sicherheit**.
1. Erweitern Sie im Abschnitt Authentifizierung den **RMI/IIOP-Sicherheit** und klicken **CSIv2 Inbound Communications**.
1. Stellen Sie sicher, dass **SSL-gestützt** wird in der Dropdown-Liste Transport ausgewählt.
1. Starten Sie das WebSphere-Profil neu.

## WebSphere zum Konvertieren von URLs konfigurieren, die mit https beginnen {#configuring-websphere-to-convert-urls-that-begins-with-https}

Um eine URL zu konvertieren, die mit HTTPS beginnt, fügen Sie dem WebSphere-Server ein Signiererzertifikat für diese URL hinzu.

**Erstellen eines Signiererzertifikats für eine HTTPS-aktivierte Site**

1. Stellen Sie sicher, dass WebSphere ausgeführt wird.
1. Navigieren Sie in WebSphere Administrative Console zu den Signiererzertifikaten und klicken Sie dann auf Security > SSL Certificate and Key Management > Key Stores and Certificates > NodeDefaultTrustStore > Signer Certificates.
1. Klicken Sie auf Aus Port abrufen und führen Sie die folgenden Aufgaben aus:

   * Geben Sie in das Feld &quot;Host&quot;die URL ein. Geben Sie beispielsweise `www.paypal.com`.
   * Geben Sie in das Feld „Port“ den Wert `443` ein. Dieser Port ist der standardmäßige SSL-Anschluss.
   * Geben Sie in das Feld &quot;Alias&quot;einen Alias ein.

1. Klicken Sie auf &quot;Signiererinformationen abrufen&quot;und überprüfen Sie dann, ob die Informationen abgerufen werden.
1. Klicken Sie auf Anwenden und dann auf Speichern.

Die HTML-zu-PDF-Konvertierung von der Site, deren Zertifikat hinzugefügt wird, funktioniert jetzt mit dem Generate PDF-Dienst.

>[!NOTE]
>
>Damit eine Anwendung von in WebSphere aus eine Verbindung zu SSL-Sites herstellen kann, ist ein Signiererzertifikat erforderlich. Sie wird von Java Secure Socket Extensions (JSSE) verwendet, um Zertifikate zu überprüfen, die die Remote-Seite der Verbindung während eines SSL-Handshake sendet.

## Dynamische Ports konfigurieren {#configuring-dynamic-ports}

IBM WebSphere lässt nicht mehrere Aufrufe an ORB.init() zu, wenn die globale Sicherheit aktiviert ist. Informationen über die dauerhafte Einschränkung finden Sie unter https://www-01.ibm.com/support/docview.wss?uid=swg1PK58704.

Führen Sie die folgenden Schritte aus, um den Port als dynamisch festzulegen und das Problem zu beheben:

1. Wählen Sie in WebSphere Administrative Console **Server** > **Servertypen** > **WebSphere-Anwendungsserver**.
1. Wählen Sie im Bereich Voreinstellungen den gewünschten Server aus.
1. Im **Konfiguration** Registerkarte unter **Kommunikation** Abschnitt erweitern **Ports** und klicken Sie auf **Details**.
1. Klicken Sie auf die folgenden Portnamen und ändern Sie die **Portnummer** auf 0 klicken und auf **OK**.

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
