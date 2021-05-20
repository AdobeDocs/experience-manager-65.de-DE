---
title: Aktivieren der einmaligen Anmeldung in AEM Forms
seo-title: Aktivieren der einmaligen Anmeldung in AEM Forms
description: Erfahren Sie, wie Sie die einmaligen Anmeldung (SSO) mithilfe von HTML-Kopfzeilen und SPNEGO aktivieren.
seo-description: Erfahren Sie, wie Sie die einmaligen Anmeldung (SSO) mithilfe von HTML-Kopfzeilen und SPNEGO aktivieren.
uuid: 2bc08b4f-dcbe-4a16-9025-32fc14605e13
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ee54d9d4-190d-4665-925a-9740ac65fbd5
exl-id: 89561ed0-d094-4ef7-9bc1-bde11f3c5bc3
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1538'
ht-degree: 95%

---

# Aktivieren der einmaligen Anmeldung in AEM Forms{#enabling-single-sign-on-in-aem-forms}

AEM forms bietet zwei Möglichkeiten, Single Sign-On (SSO) zu aktivieren: HTTP-Header und SPNEGO.

Wenn die einmalige Anmeldung implementiert ist, sind die AEM Forms-Anmeldeseiten nicht erforderlich und werden nicht angezeigt, sofern der Benutzer bereits durch sein Firmenportal authentifiziert wurde.

Wenn AEM Forms einen Benutzer mithilfe keiner der Methoden authentifizieren kann, wird der Benutzer zu einer Anmeldungsseite umgeleitet.

## Einmalige Anmeldung (Single Sign-On, SSO) über HTTP-Kopfzeilen aktivieren {#enable-sso-using-http-headers}

Auf der Seite „Portalkonfiguration“ können Sie die einmalige Anmeldung (SSO) zwischen Anwendungen und jeder Anwendung aktivieren, die die Identitätsübermittlung per HTTP-Kopfzeile unterstützt. Wenn die einmalige Anmeldung implementiert ist, sind die AEM Forms-Anmeldeseiten nicht erforderlich und werden nicht angezeigt, sofern der Benutzer bereits durch sein Firmenportal authentifiziert wurde.

Sie können die einmalige Anmeldung auch über SPNEGO aktivieren. (Siehe [Einmalige Anmeldung über SPNEGO aktivieren](enabling-single-sign-on-aem.md#enable-sso-using-spnego).)

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Konfiguration“ > „Portalattribute konfigurieren“.
1. Wählen Sie „Ja“, um die einmalige Anmeldung zu aktivieren. Wenn Sie „Nein“ auswählen, stehen die restlichen Einstellungen auf der Seite nicht zur Verfügung.
1. Legen Sie die restlichen Einstellungen auf der Seite wie erforderlich fest und klicken Sie auf „OK“.

   * **SSO-Typ:**(Obligatorisch) Wählen Sie „HTTP-Kopfzeile“, um die einmalige Anmeldung mithilfe von HTTP-Kopfzeilen zu aktivieren.
   * **HTTP-Header für Benutzer-Bezeichner:** (Obligatorisch) Name der Kopfzeile, deren Wert den eindeutigen Bezeichner des angemeldeten Benutzers enthält. User Management verwendet diesen Wert, um den Benutzer in der User Management-Datenbank zu suchen. Der aus dieser Kopfzeile extrahierte Wert muss mit dem eindeutigen Bezeichner des Benutzers übereinstimmen, der aus der Synchronisierung mit dem LDAP-Ordner stammt. (Siehe [Benutzereinstellungen](/help/forms/using/admin-help/adding-configuring-users.md#user-settings).)
   * **Bezeichnerwert wird der Benutzer-ID des Benutzers anstelle des eindeutigen Bezeichners des Benutzers zugeordnet:** Ordnet den eindeutigen Bezeichnerwert des Benutzers der Benutzer-ID zu. Wählen Sie diese Option, wenn der eindeutige Bezeichner des Benutzers ein binärer Wert ist, der nicht einfach über HTTP-Kopfzeilen (z. B. „objectGUID“, wenn Sie Benutzer aus Active Directory synchronisieren) weitergeleitet werden kann.
   * **HTTP-Kopfzeile für die Domäne:**(Nicht obligatorisch) Name der Kopfzeile, deren Wert den Domänennamen enthält. Verwenden Sie diese Einstellung nur, wenn der Benutzer nicht mithilfe einer einzelnen HTTP-Kopfzeile eindeutig identifiziert werden kann. Verwenden Sie diese Einstellung, wenn mehrere Domänen vorhanden sind und der eindeutige Bezeichner nur innerhalb der angegebenen Domäne eindeutig ist. Geben Sie in diesem Fall den Kopfzeilennamen in dieses Textfeld ein und legen Sie die Domänenzuordnung für die verschiedenen Domänen im Feld „Domänenzuordnung“ fest. (Siehe [Bearbeiten und Konvertieren bestehender Domänen](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).)
   * **Domänenzuordnung:**(Obligatorisch) Hier können Sie die Zuordnung für mehrere Domänen im Format *Kopfzeilenwert=Domänenname* angeben.

      Betrachten wir als Beispiel einen Fall, in dem die HTTP-Kopfzeile für eine Domäne „domainName“ lautet und die Werte „Domäne1“, „Domäne2“ oder „Domäne3“ haben kann. In diesem Fall ordnen Sie die domainName-Werte mithilfe der Domänenzuordnung User Management-Domänennamen zu. Jede Zuordnung muss in einer eigenen Zeile stehen:

      Domäne1=UMdomain1

      Domäne2=UMdomain2

      Domäne3=UMdomain3

### Zulässige Referenzen konfigurieren  {#configure-allowed-referers}

Die Schritte für die Konfiguration zulässiger Referenzen finden Sie unter [Zulässige Referenzen konfigurieren](/help/forms/using/admin-help/preventing-csrf-attacks.md#configure-allowed-referers).

## Einmalige Anmeldung über SPNEGO aktivieren  {#enable-sso-using-spnego}

Über SPNEGO (Simple and Protected GSSAPI Negotiation Mechanism) können Sie die einmalige Anmeldung (SSO) aktivieren, wenn Sie Active Directory als LDAP-Server in einer Windows-Umgebung verwenden. Wenn die einmalige Anmeldung aktiviert ist, sind die AEM Forms-Seiten für die Benutzeranmeldung nicht erforderlich und werden nicht angezeigt.

Sie können die einmalige Anmeldung auch über HTTP-Kopfzeilen aktivieren. (Siehe [Einmalige Anmeldung (Single Sign-On, SSO) über HTTP-Kopfzeilen aktivieren](enabling-single-sign-on-aem.md#enable-sso-using-http-headers).)

>[!NOTE]
>
>AEM Forms on JEE unterstützt nicht die Konfiguration von SSO mithilfe von Kerberos/SPNEGO in einer mehrfahcen untergeordneten Domänenumgebung .

1. Legen Sie die Domäne fest, in der die einmalige Anmeldung aktiviert werden soll. Der AEM Forms-Server und die Benutzer müssen alle zur selben Windows-Domäne bzw. vertrauenswürdigen Domäne gehören.
1. Erstellen Sie in Active Directory einen Benutzer, der den AEM Forms-Server repräsentiert. (Siehe [Benutzerkonto erstellen](enabling-single-sign-on-aem.md#create-a-user-account).) Wenn Sie mehr als eine Domäne zum Verwenden von SPNEGO konfigurieren, stellen Sie sicher, dass die Kennwörter für jeden einzelnen Benutzer verschieden sind. Wenn die Kennwörter nicht verschieden sind, kann SPNEGO nicht verwendet werden.
1. Weisen Sie den Dienstprinzipalnamen zu. (Siehe [Dienstprinzipalnamen (SPN) zuweisen](enabling-single-sign-on-aem.md#map-a-service-principal-name-spn).)
1. Konfigurieren Sie den Domänencontroller. (Siehe [Fehler bei der Kerberos-Integritätsprüfung verhindern](enabling-single-sign-on-aem.md#prevent-kerberos-integrity-check-failures).)
1. Anschließend müssen Sie eine Unternehmensdomäne hinzufügen oder bearbeiten (siehe [Domänen hinzufügen](/help/forms/using/admin-help/adding-domains.md#adding-domains) oder [Bestehende Domänen bearbeiten oder umwandeln](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains)). Führen Sie beim Erstellen oder Bearbeiten der Unternehmensdomäne die folgenden Aufgaben aus:

   * Erstellen oder bearbeiten Sie einen Ordner, der Ihre Active Directory-Informationen enthält.
   * Fügen Sie LDAP als Authentifizierungsanbieter hinzu.
   * Fügen Sie Kerberos als Authentifizierungsanbieter hinzu. Geben Sie auf der Seite „Neu“ oder „Authentifizierung bearbeiten“ für Kerberos die folgenden Informationen ein:

      * **Authentifizierungsanbieter:** Kerberos
      * **DNS-IP:** Die DNS-IP-Adresse des Servers, auf dem AEM Forms ausgeführt wird. Sie können diese IP-Adresse bestimmen, indem Sie `ipconfig/all` in die Befehlszeile eingeben.
      * **KDC-Host:** Der voll qualifizierte Hostname bzw. die IP-Adresse des für die Authentifizierung verwendeten Active Directory-Servers.
      * **Dienstbenutzer:** Der an das Tool KtPass übergebene Dienstprinzipalname. In dem zuvor verwendeten Beispiel ist der Dienstbenutzer `HTTP/lcserver.um.lc.com`.
      * **Dienstbereich:** Der Domänenname für Active Directory. In dem zuvor verwendeten Beispiel ist der Domänenname `UM.LC.COM.`
      * **Dienstkennwort:** Das Kennwort des Dienstbenutzers. In dem zuvor verwendeten Beispiel ist das Dienstkennwort `password`.
      * **SPNEGO aktivieren:** Aktiviert die Verwendung von SPNEGO für die einmalige Anmeldung (SSO). Aktivieren Sie diese Option.

1. Konfigurieren Sie SPNEGO-Clientbrowsereinstellungen. (Siehe [Konfigurieren von SPNEGO-Clientbrowsereinstellungen](enabling-single-sign-on-aem.md#configuring-spnego-client-browser-settings).)

### Benutzerkonto erstellen  {#create-a-user-account}

1. Sie müssen in SPNEGO einen Dienst als Benutzer in Active Directory auf dem Domänencontroller registrieren, der AEM Forms repräsentiert. Wechseln Sie auf dem Domänencontroller zu „Start“ > „Verwaltung“ > „Active Directory-Benutzer und -Computer“. Wenn der Eintrag nicht im Startmenü vorhanden ist, verwenden Sie die Systemsteuerung.
1. Klicken Sie auf den Ordner „Benutzer“, um eine Liste der Benutzer anzuzeigen.
1. Klicken Sie mit der rechten Maustaste auf den Benutzerordner und wählen Sie „Neu“ > „Benutzer“.
1. Geben Sie den Vornamen/Nachnamen und den Benutzeranmeldenamen ein und klicken Sie auf „Weiter“. Legen Sie beispielsweise folgende Werte fest:

   * **Vorname**: umspnego
   * **Benutzeranmeldename:** spnegodemo

1. Geben Sie ein Kennwort ein. Legen Sie es beispielsweise auf *password* fest. Stellen Sie sicher, dass nur „Kennwort läuft nie ab“ und keine anderen Optionen aktiviert sind.
1. Klicken Sie auf „Weiter“ und dann auf „Fertig stellen“.

### Dienstprinzipalnamen (SPN) zuweisen  {#map-a-service-principal-name-spn}

1. Besorgen Sie sich das Dienstprogramm „KtPass“. Mit dessen Hilfe wird ein SPN einem Bereich zugewiesen. Sie können das Dienstprogramm „KtPass“ als Teil des Windows Server Tool Packs oder Resource Kits erhalten. (Siehe [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777).)
1. Führen Sie an einer Eingabeaufforderung den Befehl `ktpass` mit folgenden Argumenten aus:

   `ktpass -princ HTTP/`** `@`** `-mapuser`*hostREALMuser*

   Geben Sie beispielsweise folgenden Text ein:

   `ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo`

   Die Argumente, die Sie bereitstellen müssen, lauten wie folgt:

   **Host:** Voll qualifizierter Name des Formularservers oder eine eindeutige URL. In diesem Beispiel ist er auf „lcserver.um.lc.com“ festgelegt.

   **BEREICH:** Der Active Directory-Bereich für den Domänencontroller. In diesem Beispiel ist der Wert auf „UM.LC.COM“ festgelegt. Stellen Sie sicher, dass der Bereich in Großbuchstaben eingegeben wird. Führen Sie die folgenden Schritte aus, um den Bereich für Windows 2003 zu bestimmen:

   * Klicken Sie mit der rechten Maustaste auf „Arbeitsplatz“ und wählen Sie „Eigenschaften“.
   * Klicken Sie auf die Registerkarte „Computername“. Der  Wert von „Domänenname“ ist der Bereichsname.

   **Benutzer:** Der Anmeldename des in der vorherigen Aufgabe erstellten Benutzerkontos. In diesem Beispiel ist er auf „spnegodemo“ festgelegt.

Wenn dieser Fehler auftritt:

```shell
DsCrackNames returned 0x2 in the name entry for spnegodemo.
ktpass:failed getting target domain for specified user.
```

Versuchen Sie, den Benutzer als „spnegodemo@um.lc.com“ anzugeben:

```shell
ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo
```

### Fehler bei der Kerberos-Integritätsprüfung verhindern  {#prevent-kerberos-integrity-check-failures}

1. Wechseln Sie auf dem Domänencontroller zu „Start“ > „Verwaltung“ > „Active Directory-Benutzer und -Computer“. Wenn der Eintrag nicht im Startmenü vorhanden ist, verwenden Sie die Systemsteuerung.
1. Klicken Sie auf den Ordner „Benutzer“, um eine Liste der Benutzer anzuzeigen.
1. Klicken Sie mit der rechten Maustaste auf das in der vorherigen Aufgabe erstellte Benutzerkonto. In diesem Beispiel ist das Benutzerkonto `spnegodemo`.
1. Klicken Sie auf „Kennwort zurücksetzen“.
1. Geben Sie dasselbe Kennwort wie das zuvor eingegebene ein und bestätigen Sie es durch erneute Eingabe. In diesem Beispiel ist es auf `password` festgelegt.
1. Deaktivieren Sie die Option „Benutzer muss Kennwort bei der nächsten Anmeldung ändern“ und klicken Sie dann auf „OK“.

### SPNEGO-Clientbrowsereinstellungen konfigurieren  {#configuring-spnego-client-browser-settings}

Damit die SPNEGO-basierte Authentifizierung funktioniert, muss der Clientcomputer zu der Domäne gehören, in der das Benutzerkonto erstellt wurde. Sie müssen außerdem den Clientbrowser so konfigurieren, dass SPNEGO-basierte Authentifizierung zulässig ist. Ebenso muss die Site, die SPNEGO-basierte Authentifizierung erfordert, eine vertrauenswürdige Site sein.

Wenn der Zugriff auf den Server über den Computernamen erfolgt (z. B. https://lcserver:8080), sind für Internet Explorer keine Einstellungen erforderlich. Wenn Sie eine URL eingeben, die keine Punkte („.“) enthält, wird diese Site von Internet Explorer als lokale Intranetsite behandelt. Bei Verwendung eines voll qualifizierten Namens für die Site muss diese als vertrauenswürdige Site hinzugefügt werden.

**Internet Explorer 6.x konfigurieren**

1. Wechseln Sie zu „Extras“ > „Internetoptionen“ und klicken Sie auf die Registerkarte „Sicherheit“.
1. Klicken Sie auf das Symbol „Lokales Intranet“ und klicken Sie auf „Websites“.
1. Klicken Sie auf „Erweitert“ und geben Sie in das Feld „Diese Website zur Zone hinzufügen“ die URL Ihres Formularservers ein. Geben Sie beispielsweise `https://lcserver.um.lc.com`
1. Klicken Sie wiederholt auf „OK“, bis alle Dialogfelder geschlossen sind.
1. Testen Sie die Konfiguration durch Zugriff auf die URL Ihres AEM Forms-Servers. Geben Sie beispielsweise in das Feld für die Browser-URL `https://lcserver.um.lc.com:8080/um/login?um_no_redirect=true` ein.

**Mozilla Firefox konfigurieren**

1. Geben Sie in das Feld für die Browser-URL `about:config` ein.

   Das Mozilla Firefox-Dialogfeld „about:config“ wird angezeigt.

1. Geben Sie in das Feld „Filter“ den Wert `negotiate` ein.
1. Klicken Sie in der angezeigten Liste auf „network.negotiate-auth.trusted-uris“ und geben Sie einen der folgenden Befehle Ihrer Umgebung entsprechend ein:

   `.um.lc.com`- Konfiguriert Firefox so, dass SPNEGO für jede URL zugelassen wird, die auf um.lc.com endet. Stellen Sie sicher, dass Sie den Punkt (&quot;.&quot;) am Anfang.

   `lcserver.um.lc.com`–  – Hierdurch wird Firefox so konfiguriert, dass SPNEGO nur für bestimmte Server zugelassen wird. Beginnen Sie diesen Wert nicht mit einem Punkt („.“).

1. Testen Sie die Konfiguration durch Zugriff auf die Anwendung. Die Begrüßungsseite der Zielanwendung sollte angezeigt werden.
