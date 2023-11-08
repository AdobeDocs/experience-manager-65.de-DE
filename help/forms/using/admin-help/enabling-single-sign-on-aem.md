---
title: Aktivieren der einmaligen Anmeldung in AEM Forms
seo-title: Enabling single sign-on in AEM forms
description: Erfahren Sie, wie Sie Single Sign-On (SSO) mithilfe von HTTP-Headern und SPNEGO aktivieren.
seo-description: Learn how to enable single sign-on (SSO) using HTTP headers and SPNEGO.
uuid: 2bc08b4f-dcbe-4a16-9025-32fc14605e13
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ee54d9d4-190d-4665-925a-9740ac65fbd5
exl-id: 89561ed0-d094-4ef7-9bc1-bde11f3c5bc3
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 43%

---

# Aktivieren der einmaligen Anmeldung in AEM Forms{#enabling-single-sign-on-in-aem-forms}

AEM Forms bietet zwei Möglichkeiten zum Aktivieren der einmaligen Anmeldung (SSO) – HTTP-Kopfzeile und SPNEGO:

Wenn die einmalige Anmeldung implementiert ist, sind die Anmeldeseiten für AEM Formulare nicht erforderlich und werden nicht angezeigt, wenn der Benutzer bereits über sein Unternehmensportal authentifiziert wurde.

Wenn AEM Formulare einen Benutzer nicht mit einer dieser Methoden authentifizieren können, wird der Benutzer zu einer Anmeldeseite umgeleitet.

## Aktivieren von SSO mithilfe von HTTP-Headern {#enable-sso-using-http-headers}

Sie können die Seite &quot;Portalkonfiguration&quot;verwenden, um Single Sign-On (SSO) zwischen Anwendungen und allen Anwendungen zu aktivieren, die die Identitätsübermittlung über HTTP-Header unterstützen. Wenn die einmalige Anmeldung implementiert ist, sind die Anmeldeseiten für AEM Formulare nicht erforderlich und werden nicht angezeigt, wenn der Benutzer bereits über sein Unternehmensportal authentifiziert wurde.

Sie können die einmalige Anmeldung auch über SPNEGO aktivieren. (Siehe [SSO mit SPNEGO aktivieren](enabling-single-sign-on-aem.md#enable-sso-using-spnego).

1. Klicken Sie in Administration Console auf &quot;Einstellungen&quot;> &quot;User Management&quot;> &quot;Konfiguration&quot;> &quot;Portalattribute konfigurieren&quot;.
1. Wählen Sie Ja aus, um die einmalige Anmeldung zu aktivieren. Wenn Sie &quot;Nein&quot;auswählen, sind die restlichen Einstellungen auf der Seite nicht verfügbar.
1. Legen Sie die restlichen Optionen auf der Seite nach Bedarf fest und klicken Sie auf OK:

   * **SSO-Typ:**(Obligatorisch) Wählen Sie „HTTP-Kopfzeile“, um die einmalige Anmeldung mithilfe von HTTP-Kopfzeilen zu aktivieren.
   * **HTTP-Header für Benutzer-Bezeichner:** (Obligatorisch) Name der Kopfzeile, deren Wert den eindeutigen Bezeichner des angemeldeten Benutzers enthält. User Management verwendet diesen Wert, um den Benutzer in der User Management-Datenbank zu finden. Der aus dieser Kopfzeile abgerufene Wert sollte mit der eindeutigen Kennung des Benutzers übereinstimmen, der aus dem LDAP-Ordner synchronisiert wird. (Siehe [Benutzereinstellungen](/help/forms/using/admin-help/adding-configuring-users.md#user-settings).
   * **Bezeichnerwert wird der Benutzer-ID des Benutzers anstelle des eindeutigen Bezeichners des Benutzers zugeordnet:** Ordnet den eindeutigen Bezeichnerwert des Benutzers der Benutzer-ID zu. Wählen Sie diese Option, wenn der eindeutige Bezeichner des Benutzers ein binärer Wert ist, der nicht einfach über HTTP-Kopfzeilen (z. B. „objectGUID“, wenn Sie Benutzer aus Active Directory synchronisieren) weitergeleitet werden kann.
   * **HTTP-Kopfzeile für die Domain:**(Nicht obligatorisch) Name der Kopfzeile, deren Wert den Domain-Namen enthält. Verwenden Sie diese Einstellung nur, wenn kein einzelner HTTP-Header den Benutzer eindeutig identifiziert. Verwenden Sie diese Einstellung, wenn mehrere Domains vorhanden sind und der eindeutige Bezeichner nur innerhalb der angegebenen Domain eindeutig ist. Geben Sie in diesem Fall den Kopfzeilennamen in dieses Textfeld ein und legen Sie die Domain-Zuordnung für die verschiedenen Domains im Feld „Domain-Zuordnung“ fest. (Siehe [Bearbeiten und Konvertieren bestehender Domains](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).)
   * **Domain-Zuordnung:**(Obligatorisch) Hier können Sie die Zuordnung für mehrere Domains im Format *Kopfzeilenwert=Domain-Name* angeben.

     Betrachten wir als Beispiel einen Fall, in dem die HTTP-Kopfzeile für eine Domain „domainName“ lautet und die Werte „Domain1“, „Domain2“ oder „Domain3“ haben kann. In diesem Fall ordnen Sie die domainName-Werte mithilfe der Domain-Zuordnung User Management-Domain-Namen zu. Jede Zuordnung muss sich in einer anderen Zeile befinden:

     Domain1=UMdomain1

     Domain2=UMdomain2

     Domain3=UMdomain3

### Zulässige Referenzen konfigurieren {#configure-allowed-referers}

Die Schritte zum Konfigurieren zulässiger Referenzen finden Sie unter [Zulässige Referenzen konfigurieren](/help/forms/using/admin-help/preventing-csrf-attacks.md#configure-allowed-referers).

## SSO mit SPNEGO aktivieren {#enable-sso-using-spnego}

Sie können SPNEGO (Simple and Protected GSSAPI Negotiation Mechanism) verwenden, um Single Sign-on (SSO) zu aktivieren, wenn Sie Active Directory als LDAP-Server in einer Windows-Umgebung verwenden. Wenn SSO aktiviert ist, sind die Anmeldeseiten für AEM Formulare nicht erforderlich und werden nicht angezeigt.

Sie können die einmalige Anmeldung auch über HTTP-Header aktivieren. (Siehe [Aktivieren von SSO mithilfe von HTTP-Headern](enabling-single-sign-on-aem.md#enable-sso-using-http-headers).

>[!NOTE]
>
>AEM Forms on JEE unterstützt nicht die Konfiguration von SSO mithilfe von Kerberos/SPNEGO in einer mehrfachen untergeordneten Domain-Umgebung.

1. Legen Sie die Domain fest, in der die einmalige Anmeldung aktiviert werden soll. Der AEM Forms-Server und die Benutzer müssen zur gleichen Windows-Domäne oder vertrauenswürdigen Domäne gehören.
1. Erstellen Sie in Active Directory einen Benutzer, der den AEM Forms-Server repräsentiert. (Siehe [Benutzerkonto erstellen](enabling-single-sign-on-aem.md#create-a-user-account). Wenn Sie mehr als eine Domain zum Verwenden von SPNEGO konfigurieren, stellen Sie sicher, dass die Kennwörter für jeden einzelnen Benutzer verschieden sind. Wenn die Kennwörter nicht verschieden sind, funktioniert SPNEGO SSO nicht.
1. Ordnen Sie den Dienstprinzipalnamen zu. (Siehe [Dienstprinzipalnamen (SPN) zuordnen](enabling-single-sign-on-aem.md#map-a-service-principal-name-spn).
1. Konfigurieren Sie den Domain-Controller. (Siehe [Fehler bei der Kerberos-Integritätsprüfung verhindern](enabling-single-sign-on-aem.md#prevent-kerberos-integrity-check-failures).
1. Anschließend müssen Sie eine Unternehmens-Domain hinzufügen oder bearbeiten (siehe [Domains hinzufügen](/help/forms/using/admin-help/adding-domains.md#adding-domains) oder [Bestehende Domains bearbeiten oder umwandeln](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains)). Führen Sie beim Erstellen oder Bearbeiten der Unternehmens-Domain die folgenden Aufgaben aus:

   * Fügen Sie einen Ordner hinzu oder bearbeiten Sie ihn, der Ihre Active Directory-Informationen enthält.
   * Hinzufügen von LDAP als Authentifizierungsanbieter.
   * Fügen Sie Kerberos als Authentifizierungsanbieter hinzu. Geben Sie die folgenden Informationen auf der Seite &quot;Neu&quot;oder &quot;Authentifizierung bearbeiten&quot;für Kerberos an:

      * **Authentication Provider:** Kerberos
      * **DNS-IP**: Die DNS-IP-Adresse des Servers, auf dem AEM Forms ausgeführt wird. Sie können diese IP-Adresse bestimmen, indem Sie `ipconfig/all` in die Befehlszeile eingeben.
      * **KDC-Host:** Der voll qualifizierte Hostname bzw. die IP-Adresse des für die Authentifizierung verwendeten Active Directory-Servers.
      * **Dienstbenutzer:** Der an das Tool KtPass übergebene Dienstprinzipalname. In dem zuvor verwendeten Beispiel ist der Dienstbenutzer `HTTP/lcserver.um.lc.com`.
      * **Dienstbereich:** Der Domanin-Name für Active Directory. In dem zuvor verwendeten Beispiel ist der Domain-Name `UM.LC.COM.`
      * **Dienstkennwort:** Das Kennwort des Dienstbenutzers. In dem zuvor verwendeten Beispiel ist das Dienstkennwort `password`.
      * **SPNEGO aktivieren:** Aktiviert die Verwendung von SPNEGO für die einmalige Anmeldung (SSO). Wählen Sie diese Option aus.

1. Konfigurieren Sie die SPNEGO-Clientbrowsereinstellungen. (Siehe [SPNEGO-Clientbrowsereinstellungen konfigurieren](enabling-single-sign-on-aem.md#configuring-spnego-client-browser-settings).

### Benutzerkonto erstellen {#create-a-user-account}

1. Sie müssen in SPNEGO einen Service als Benutzer in Active Directory auf dem Domain-Controller registrieren, der AEM Forms repräsentiert. Wechseln Sie auf dem Domain-Controller zu „Start“ > „Verwaltung“ > „Active Directory-Benutzer und -Computer“. Wenn das Menü &quot;Start&quot;nicht unter &quot;Verwaltung&quot;angezeigt wird, verwenden Sie das Control Panel.
1. Klicken Sie auf den Ordner Benutzer , um eine Liste der Benutzer anzuzeigen.
1. Klicken Sie mit der rechten Maustaste auf den Benutzerordner und wählen Sie &quot;Neu&quot;> &quot;Benutzer&quot;.
1. Geben Sie den Vornamen/Nachnamen und den Benutzernamen ein und klicken Sie auf Weiter. Legen Sie beispielsweise die folgenden Werte fest:

   * **Vorname**: umspnego
   * **Benutzername**: spnegodemo

1. Geben Sie ein Kennwort ein. Setzen Sie sie beispielsweise auf *password*. Stellen Sie sicher, dass &quot;Kennwort nie abgelaufen&quot;ausgewählt ist und keine anderen Optionen ausgewählt sind.
1. Klicken Sie auf Next und dann auf Finish.

### Dienstprinzipalnamen (SPN) zuordnen {#map-a-service-principal-name-spn}

1. Rufen Sie das Dienstprogramm KtPass ab. Dieses Dienstprogramm wird verwendet, um eine SPN einem REALM zuzuordnen. Sie können das Dienstprogramm KtPass als Teil des Windows Server Tool Packs oder Resource Kits abrufen. (Siehe [Windows Server 2003 Service Pack 1 Support Tools](https://support.microsoft.com/kb/892777).
1. Führen Sie an einer Eingabeaufforderung den Befehl `ktpass` mit folgenden Argumenten aus:

   `ktpass -princ HTTP/`*host* `@`*REALM* `-mapuser`*Benutzer*

   Geben Sie beispielsweise folgenden Text ein:

   `ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo`

   Die Werte, die Sie angeben müssen, werden wie folgt beschrieben:

   **Host:** Vollqualifizierter Name des Forms-Servers oder eine eindeutige URL. In diesem Beispiel ist er auf lcserver.um.lc.com festgelegt.

   **BEREICH:** Der Active Directory-Bereich für den Domain-Controller. In diesem Beispiel ist er auf UM.LC.COM festgelegt. Stellen Sie sicher, dass Sie den Bereich in Großbuchstaben eingeben. Führen Sie die folgenden Schritte aus, um den Bereich für Windows 2003 zu bestimmen:

   * Klicken Sie mit der rechten Maustaste auf „Arbeitsplatz“ und wählen Sie „Eigenschaften“ aus.
   * Klicken Sie auf die Registerkarte Computername . Der Wert von „Domain-Name“ ist der Bereichsname.

   **user:** Der Anmeldename des in der vorherigen Aufgabe erstellten Benutzerkontos. In diesem Beispiel ist er auf spnegodemo eingestellt.

Wenn dieser Fehler auftritt:

```shell
DsCrackNames returned 0x2 in the name entry for spnegodemo.
ktpass:failed getting target domain for specified user.
```

Versuchen Sie, den Benutzer als spnegodemo@um.lc.com anzugeben:

```shell
ktpass -princ HTTP/lcserver.um.lc.com@UM.LC.COM -mapuser spnegodemo
```

### Fehler bei der Kerberos-Integritätsprüfung verhindern {#prevent-kerberos-integrity-check-failures}

1. Wechseln Sie auf dem Domain-Controller zu „Start“ > „Verwaltung“ > „Active Directory-Benutzer und -Computer“. Wenn das Menü &quot;Start&quot;nicht unter &quot;Verwaltung&quot;angezeigt wird, verwenden Sie das Control Panel.
1. Klicken Sie auf den Ordner Benutzer , um eine Liste der Benutzer anzuzeigen.
1. Klicken Sie mit der rechten Maustaste auf das Benutzerkonto, das Sie in einer vorherigen Aufgabe erstellt haben. In diesem Beispiel ist das Benutzerkonto `spnegodemo`.
1. Klicken Sie auf Kennwort zurücksetzen .
1. Geben Sie dasselbe Kennwort wie zuvor ein und bestätigen Sie es. In diesem Beispiel ist es auf `password` festgelegt.
1. Deaktivieren Sie die Option Kennwort bei nächster Anmeldung ändern und klicken Sie auf OK.

### SPNEGO-Clientbrowsereinstellungen konfigurieren {#configuring-spnego-client-browser-settings}

Damit die SPNEGO-basierte Authentifizierung funktioniert, muss der Clientcomputer zu der Domain gehören, in der das Benutzerkonto erstellt wurde. Sie müssen außerdem den Client-Browser so konfigurieren, dass SPNEGO-basierte Authentifizierung zulässig ist. Darüber hinaus muss die Site, für die SPNEGO-basierte Authentifizierung erforderlich ist, eine vertrauenswürdige Site sein.

Wenn der Zugriff auf den Server über den Computernamen erfolgt, z.B. https://lcserver:8080, sind für den Internet Explorer keine Einstellungen erforderlich. Wenn Sie eine URL eingeben, die keine Punkte (&quot;.&quot;) enthält, behandelt Internet Explorer die Site als lokale Intranet-Site. Wenn Sie einen vollständig qualifizierten Namen für die Site verwenden, muss die Site als vertrauenswürdige Site hinzugefügt werden.

**Internet Explorer 6.x konfigurieren**

1. Gehen Sie zu Tools > Internetoptionen und klicken Sie auf die Registerkarte Sicherheit .
1. Klicken Sie auf das Symbol Lokales Intranet und dann auf Sites .
1. Klicken Sie auf &quot;Erweitert&quot;und geben Sie im Feld &quot;Diese Website zur Zone hinzufügen&quot;die URL Ihres Forms-Servers ein. Geben Sie beispielsweise `https://lcserver.um.lc.com`
1. Klicken Sie auf OK , bis alle Dialogfelder geschlossen sind.
1. Testen Sie die Konfiguration, indem Sie auf die URL Ihres AEM Forms-Servers zugreifen. Geben Sie zum Beispiel in das URL-Feld des Browsers `https://lcserver.um.lc.com:8080/um/login?um_no_redirect=true` ein

**Mozilla Firefox konfigurieren**

1. Geben Sie in das URL-Feld des Browsers `about:config` ein.

   Das Mozilla Firefox-Dialogfeld „about:config“ wird angezeigt.

1. Geben Sie in das Feld „Filter“ den Wert `negotiate` ein.
1. Klicken Sie in der angezeigten Liste auf „network.negotiate-auth.trusted-uris“ und geben Sie einen der folgenden Befehle Ihrer Umgebung entsprechend ein:

   `.um.lc.com`- Konfiguriert Firefox so, dass SPNEGO für jede URL zugelassen wird, die auf um.lc.com endet. Stellen Sie sicher, dass Sie den Punkt („.“) am Anfang mit einschließen.

   `lcserver.um.lc.com` – Hierdurch wird Firefox so konfiguriert, dass SPNEGO nur für bestimmte Server zugelassen wird. Beginnen Sie diesen Wert nicht mit einem Punkt (&quot;.&quot;).

1. Testen Sie die Konfiguration durch Zugriff auf die Anwendung. Die Begrüßungsseite für die Zielanwendung sollte angezeigt werden.
