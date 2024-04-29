---
title: Aktivieren der einmaligen Anmeldung in AEM Forms
description: Erfahren Sie, wie Sie Single Sign-on (SSO) mithilfe von HTTP-Headern und SPNEGO aktivieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 89561ed0-d094-4ef7-9bc1-bde11f3c5bc3
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: ht
source-wordcount: '1520'
ht-degree: 100%

---

# Aktivieren der einmaligen Anmeldung in AEM Forms{#enabling-single-sign-on-in-aem-forms}

AEM Forms bietet zwei Möglichkeiten zum Aktivieren der einmaligen Anmeldung (SSO) – HTTP-Kopfzeile und SPNEGO:

Wenn SSO implementiert ist, sind die AEM Forms-Seiten für die Benutzeranmeldung nicht erforderlich und werden nicht angezeigt, sofern die Benutzerin oder der Benutzer bereits durch das eigene Firmenportal authentifiziert wurde.

Wenn AEM Forms eine Person mit keiner der Methoden authentifizieren kann, wird diese zu einer Anmeldeseite umgeleitet.

## Aktivieren von SSO mit HTTP-Headern {#enable-sso-using-http-headers}

Auf der Seite „Portalkonfiguration“ können Sie Single Sign-on (SSO) zwischen Anwendungen und jeder Anwendung aktivieren, die die Identitätsübermittlung per HTTP-Header unterstützt. Wenn SSO implementiert ist, sind die AEM Forms-Seiten für die Benutzeranmeldung nicht erforderlich und werden nicht angezeigt, sofern die Benutzerin oder der Benutzer bereits durch das eigene Firmenportal authentifiziert wurde.

Sie können SSO auch über SPNEGO aktivieren. (Siehe [Aktivieren von SSO mit SPNEGO](enabling-single-sign-on-aem.md#enable-sso-using-spnego).)

1. Klicken Sie in der Administrationskonsole auf „Einstellungen“ > „Benutzerverwaltung“ > „Konfiguration“ > „Portalattribute konfigurieren“.
1. Wählen Sie „Ja“, um SSO zu aktivieren. Wenn Sie „Nein“ auswählen, stehen die restlichen Einstellungen auf der Seite nicht zur Verfügung.
1. Legen Sie die restlichen Einstellungen auf der Seite wie erforderlich fest und klicken Sie auf „OK“.

   * **SSO-Typ:**(Obligatorisch) Wählen Sie „HTTP-Kopfzeile“, um die einmalige Anmeldung mithilfe von HTTP-Kopfzeilen zu aktivieren.
   * **HTTP-Header für Benutzer-Bezeichner:** (Obligatorisch) Name der Kopfzeile, deren Wert den eindeutigen Bezeichner des angemeldeten Benutzers enthält. Die Benutzerverwaltung verwendet diesen Wert, um die Person in der Benutzerverwaltungsdatenbank zu suchen. Der aus diesem Header extrahierte Wert muss mit der eindeutigen Kennung der Person übereinstimmen, die mit dem LDAP-Verzeichnis synchronisiert wurde. (Siehe [Benutzereinstellungen](/help/forms/using/admin-help/adding-configuring-users.md#user-settings).)
   * **Bezeichnerwert wird der Benutzer-ID des Benutzers anstelle des eindeutigen Bezeichners des Benutzers zugeordnet:** Ordnet den eindeutigen Bezeichnerwert des Benutzers der Benutzer-ID zu. Wählen Sie diese Option, wenn der eindeutige Bezeichner des Benutzers ein binärer Wert ist, der nicht einfach über HTTP-Kopfzeilen (z. B. „objectGUID“, wenn Sie Benutzer aus Active Directory synchronisieren) weitergeleitet werden kann.
   * **HTTP-Kopfzeile für die Domain:**(Nicht obligatorisch) Name der Kopfzeile, deren Wert den Domain-Namen enthält. Verwenden Sie diese Einstellung nur, wenn die Person nicht mithilfe eines einzelnen HTTP-Headers eindeutig identifiziert werden kann. Verwenden Sie diese Einstellung, wenn mehrere Domains vorhanden sind und der eindeutige Bezeichner nur innerhalb der angegebenen Domain eindeutig ist. Geben Sie in diesem Fall den Kopfzeilennamen in dieses Textfeld ein und legen Sie die Domain-Zuordnung für die verschiedenen Domains im Feld „Domain-Zuordnung“ fest. (Siehe [Bearbeiten und Konvertieren bestehender Domains](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).)
   * **Domain-Zuordnung:**(Obligatorisch) Hier können Sie die Zuordnung für mehrere Domains im Format *Kopfzeilenwert=Domain-Name* angeben.

     Betrachten wir als Beispiel einen Fall, in dem die HTTP-Kopfzeile für eine Domain „domainName“ lautet und die Werte „Domain1“, „Domain2“ oder „Domain3“ haben kann. In diesem Fall ordnen Sie die domainName-Werte mithilfe der Domain-Zuordnung User Management-Domain-Namen zu. Jede Zuordnung muss in einer eigenen Zeile stehen:

     Domain1=UMdomain1

     Domain2=UMdomain2

     Domain3=UMdomain3

### Konfigurieren zulässiger Referrer {#configure-allowed-referers}

Die Schritte für die Konfiguration zulässiger Referrer finden Sie unter [Konfigurieren zulässiger Referrer](/help/forms/using/admin-help/preventing-csrf-attacks.md#configure-allowed-referers).

## Aktivieren von SSO mit SPNEGO {#enable-sso-using-spnego}

Über SPNEGO (Simple and Protected GSSAPI Negotiation Mechanism) können Sie Single Sign-on (SSO) aktivieren, wenn Sie Active Directory als LDAP-Server in einer Windows-Umgebung verwenden. Wenn SSO aktiviert ist, sind die Seiten für die Benutzeranmeldung bei AEM Forms nicht erforderlich und werden nicht angezeigt.

Sie können SSO auch über HTTP-Header aktivieren. (Siehe [Aktivieren von SSO mit HTTP-Headern](enabling-single-sign-on-aem.md#enable-sso-using-http-headers).)

>[!NOTE]
>
>AEM Forms on JEE unterstützt nicht die Konfiguration von SSO mithilfe von Kerberos/SPNEGO in einer mehrfachen untergeordneten Domain-Umgebung.

1. Legen Sie die Domain fest, in der die einmalige Anmeldung aktiviert werden soll. Der AEM-Formular-Server und die Benutzenden müssen alle zur selben Windows-Domain bzw. vertrauenswürdigen Domain gehören.
1. Erstellen Sie in Active Directory eine Benutzerin oder einen Benutzer, die bzw. der den AEM-Formular-Server repräsentiert. (Siehe [Erstellen eines Benutzerkontos](enabling-single-sign-on-aem.md#create-a-user-account).) Wenn Sie mehr als eine Domain zum Verwenden von SPNEGO konfigurieren, stellen Sie sicher, dass die Kennwörter für jeden einzelnen Benutzer verschieden sind. Wenn die Kennwörter nicht verschieden sind, kann SPNEGO-SSO nicht verwendet werden.
1. Weisen Sie den Dienstprinzipalnamen zu. (Siehe [Zuweisen eines Dienstprinzipalnamen (SPN)](enabling-single-sign-on-aem.md#map-a-service-principal-name-spn).)
1. Konfigurieren Sie den Domain-Controller. (Siehe [Verhindern von Fehlern bei der Kerberos-Integritätsprüfung](enabling-single-sign-on-aem.md#prevent-kerberos-integrity-check-failures).)
1. Anschließend müssen Sie eine Unternehmens-Domain hinzufügen oder bearbeiten (siehe [Domains hinzufügen](/help/forms/using/admin-help/adding-domains.md#adding-domains) oder [Bestehende Domains bearbeiten oder umwandeln](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains)). Führen Sie beim Erstellen oder Bearbeiten der Unternehmens-Domain die folgenden Aufgaben aus:

   * Erstellen oder bearbeiten Sie einen Ordner, der Ihre Active Directory-Informationen enthält.
   * Hinzufügen von LDAP als Authentifizierungsanbieter.
   * Fügen Sie Kerberos als Authentifizierungsanbieter hinzu. Geben Sie auf der Seite „Neu“ oder „Authentifizierung bearbeiten“ für Kerberos die folgenden Informationen ein:

      * **Authentifizierungsanbieter:** Kerberos
      * **DNS-IP**: Die DNS-IP-Adresse des Servers, auf dem AEM Forms ausgeführt wird. Sie können diese IP-Adresse bestimmen, indem Sie `ipconfig/all` in die Befehlszeile eingeben.
      * **KDC-Host:** Der voll qualifizierte Hostname bzw. die IP-Adresse des für die Authentifizierung verwendeten Active Directory-Servers.
      * **Dienstbenutzer:** Der an das Tool KtPass übergebene Dienstprinzipalname. In dem zuvor verwendeten Beispiel ist der Dienstbenutzer `HTTP/lcserver.um.lc.com`.
      * **Dienstbereich:** Der Domanin-Name für Active Directory. In dem zuvor verwendeten Beispiel ist der Domain-Name `UM.LC.COM.`
      * **Dienstkennwort:** Das Kennwort des Dienstbenutzers. In dem zuvor verwendeten Beispiel ist das Dienstkennwort `password`.
      * **SPNEGO aktivieren:** Aktiviert die Verwendung von SPNEGO für die einmalige Anmeldung (SSO). Wählen Sie diese Option aus.

1. Konfigurieren Sie die SPNEGO-Client-Browser-Einstellungen. (Siehe [Konfigurieren der SPNEGO-Client-Browser-Einstellungen](enabling-single-sign-on-aem.md#configuring-spnego-client-browser-settings).)

### Erstellen eines Benutzerkontos {#create-a-user-account}

1. Sie müssen in SPNEGO einen Service als Benutzer in Active Directory auf dem Domain-Controller registrieren, der AEM Forms repräsentiert. Wechseln Sie auf dem Domain-Controller zu „Start“ > „Verwaltung“ > „Active Directory-Benutzer und -Computer“. Wenn „Verwaltung“ nicht im Startmenü vorhanden ist, verwenden Sie die Systemsteuerung.
1. Klicken Sie auf den Ordner „Benutzer“, um eine Liste der Benutzenden anzuzeigen.
1. Klicken Sie mit der rechten Maustaste auf den Benutzerordner und wählen Sie „Neu“ > „Benutzer“.
1. Geben Sie den Vornamen/Nachnamen und den Benutzeranmeldenamen ein und klicken Sie auf „Weiter“. Legen Sie beispielsweise die folgenden Werte fest:

   * **Vorname**: umspnego
   * **Benutzeranmeldename**: spnegodemo

1. Geben Sie ein Kennwort ein. Legen Sie es beispielsweise auf *password* fest. Stellen Sie sicher, dass nur „Kennwort läuft nie ab“ ausgewählt ist und keine anderen Optionen ausgewählt sind.
1. Klicken Sie auf „Weiter“ und dann auf „Beenden“.

### Zuweisen eines Dienstprinzipalnamen (SPN) {#map-a-service-principal-name-spn}

1. Beziehen Sie das Dienstprogramm „KtPass“. Dieses Dienstprogramm wird verwendet, um ein SPN einem REALM zuzuweisen. Sie können das Dienstprogramm „KtPass“ als Teil des Windows Server Tool Packs oder Resource Kits erhalten. (Siehe [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777).)
1. Führen Sie an einer Eingabeaufforderung den Befehl `ktpass` mit folgenden Argumenten aus:

   `ktpass -princ HTTP/`*host* `@`*REALM* `-mapuser`*Benutzer*

   Geben Sie beispielsweise folgenden Text ein:

   `ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo`

   Die anzugebenden Werte lauten wie folgt:

   **Host:** Vollqualifizierter Name des Formular-Servers oder eine eindeutige URL. In diesem Beispiel ist er auf „lcserver.um.lc.com“ festgelegt.

   **BEREICH:** Der Active Directory-Bereich für den Domain-Controller. In diesem Beispiel ist er auf „UM.LC.COM“ festgelegt. Stellen Sie sicher, dass Sie den Bereich in Großbuchstaben eingeben. Führen Sie die folgenden Schritte aus, um den Bereich für Windows 2003 zu bestimmen:

   * Klicken Sie mit der rechten Maustaste auf „Arbeitsplatz“ und wählen Sie „Eigenschaften“ aus.
   * Klicken Sie auf die Registerkarte „Computer-Name“. Der Wert von „Domain-Name“ ist der Bereichsname.

   **Benutzer:** Der Anmeldename des in der vorherigen Aufgabe erstellten Benutzerkontos. In diesem Beispiel ist „spnegodemo“ festgelegt.

Wenn dieser Fehler auftritt, gehen Sie wie nachfolgend beschrieben vor:

```shell
DsCrackNames returned 0x2 in the name entry for spnegodemo.
ktpass:failed getting target domain for specified user.
```

Versuchen Sie, „spnegodemo@um.lc.com“ als Benutzerangabe festzulegen:

```shell
ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo
```

### Verhindern von Fehlern bei der Kerberos-Integritätsprüfung {#prevent-kerberos-integrity-check-failures}

1. Wechseln Sie auf dem Domain-Controller zu „Start“ > „Verwaltung“ > „Active Directory-Benutzer und -Computer“. Wenn „Verwaltung“ nicht im Startmenü vorhanden ist, verwenden Sie die Systemsteuerung.
1. Klicken Sie auf den Ordner „Benutzer“, um eine Liste der Benutzenden anzuzeigen.
1. Klicken Sie mit der rechten Maustaste auf das in der vorherigen Aufgabe erstellte Benutzerkonto. In diesem Beispiel ist das Benutzerkonto `spnegodemo`.
1. Klicken Sie auf „Kennwort zurücksetzen“.
1. Geben Sie dasselbe Kennwort wie das zuvor eingegebene ein und bestätigen Sie es durch erneute Eingabe. In diesem Beispiel ist es auf `password` festgelegt.
1. Deaktivieren Sie die Option „Benutzer muss Kennwort bei der nächsten Anmeldung ändern“ und klicken Sie dann auf „OK“.

### Konfigurieren der SPNEGO-Client-Browser-Einstellungen {#configuring-spnego-client-browser-settings}

Damit die SPNEGO-basierte Authentifizierung funktioniert, muss der Clientcomputer zu der Domain gehören, in der das Benutzerkonto erstellt wurde. Sie müssen außerdem den Client-Browser so konfigurieren, dass SPNEGO-basierte Authentifizierung zulässig ist. Ebenso muss die Site, die eine SPNEGO-basierte Authentifizierung erfordert, eine vertrauenswürdige Site sein.

Wenn der Zugriff auf den Server über den Computernamen erfolgt, z.B. https://lcserver:8080, sind für den Internet Explorer keine Einstellungen erforderlich. Wenn Sie eine URL eingeben, die keine Punkte („.“) enthält, wird diese Site von Internet Explorer als lokale Intranet-Site behandelt. Bei Verwendung eines vollständig qualifizierten Namens für die Site muss diese als vertrauenswürdige Site hinzugefügt werden.

**Konfigurieren von Internet Explorer 6.x**

1. Wechseln Sie zu „Extras“ > „Internetoptionen“ und klicken Sie auf die Registerkarte „Sicherheit“.
1. Klicken Sie auf das Symbol „Lokales Intranet“ und dann auf „Websites“.
1. Klicken Sie auf „Erweitert“ und geben Sie in das Feld „Diese Website zur Zone hinzufügen“ die URL Ihres Formular-Servers ein. Geben Sie beispielsweise `https://lcserver.um.lc.com`
1. Klicken Sie wiederholt auf „OK“, bis alle Dialogfelder geschlossen sind.
1. Testen Sie die Konfiguration durch Zugriff auf die URL Ihres AEM-Formular-Servers. Geben Sie zum Beispiel in das URL-Feld des Browsers `https://lcserver.um.lc.com:8080/um/login?um_no_redirect=true` ein

**Mozilla Firefox konfigurieren**

1. Geben Sie in das URL-Feld des Browsers `about:config` ein.

   Das Mozilla Firefox-Dialogfeld „about:config“ wird angezeigt.

1. Geben Sie in das Feld „Filter“ den Wert `negotiate` ein.
1. Klicken Sie in der angezeigten Liste auf „network.negotiate-auth.trusted-uris“ und geben Sie einen der folgenden Befehle Ihrer Umgebung entsprechend ein:

   `.um.lc.com`- Konfiguriert Firefox so, dass SPNEGO für jede URL zugelassen wird, die auf um.lc.com endet. Stellen Sie sicher, dass Sie den Punkt („.“) am Anfang mit einschließen.

   `lcserver.um.lc.com` – Hierdurch wird Firefox so konfiguriert, dass SPNEGO nur für bestimmte Server zugelassen wird. Beginnen Sie diesen Wert nicht mit einem Punkt („.“).

1. Testen Sie die Konfiguration, indem Sie auf die Anwendung zugreifen. Die Startseite für die Zielanwendung sollte angezeigt werden.
