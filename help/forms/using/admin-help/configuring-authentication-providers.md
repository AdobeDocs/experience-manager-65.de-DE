---
title: Konfigurieren von Authentifizierungsanbietern
description: Hinzufügen, Bearbeiten oder Löschen von Authentifizierungsanbietern, Ändern der Authentifizierungseinstellungen und Lesen Sie mehr über die Just-in-time-Bereitstellung von Benutzern.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d72a3977-1423-49e0-899b-234bb76be378
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 57%

---

# Konfigurieren von Authentifizierungsanbietern {#configuring-authentication-providers}

Hybrid-Domains erfordern mindestens einen Authentifizierungsanbieter und für Unternehmens-Domains ist mindestens ein Authentifizierungs- oder Ordneranbieter erforderlich.

Wenn Sie die einmalige Anmeldung über SPNEGO aktivieren, fügen Sie einen Kerberos-Authentifizierungsanbieter mit aktiviertem SPNEGO und einen LDAP-Provider als Sicherung hinzu. Diese Konfiguration ermöglicht die Benutzerauthentifizierung mit einer Benutzer-ID und einem Kennwort, wenn SPNEGO nicht funktioniert. (Siehe [SSO mit SPNEGO aktivieren](/help/forms/using/admin-help/enabling-single-sign-on-aem.md#enable-sso-using-spnego).

## Authentifizierungsanbieter hinzufügen {#add-an-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Wählen Sie die gewünschte Domain in der Liste aus. Wenn Sie die Authentifizierung für eine neue Domain einrichten möchten, lesen Sie [Eine Unternehmens-Domain hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-an-enterprise-domain) oder [Hybrid-Domain hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-a-hybrid-domain) hinzuzufügen.
1. Klicken Sie auf Authentifizierung hinzufügen und wählen Sie in der Liste Authentifizierungsanbieter je nach Authentifizierungsmechanismus, den Ihr Unternehmen verwendet, einen Anbieter aus.
1. Geben Sie weitere auf dieser Seite angeforderte Informationen ein.  (Siehe [Authentifizierungseinstellungen](configuring-authentication-providers.md#authentication-settings).)
1. (Optional) Klicken Sie auf Testen , um die Konfiguration zu testen.
1. Klicken Sie auf „OK“ und dann erneut auf „OK“.

## Vorhandenen Authentifizierungsanbieter bearbeiten {#edit-an-existing-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Wählen Sie die gewünschte Domain in der Liste aus.
1. Wählen Sie auf der angezeigten Seite den entsprechenden Authentifizierungsanbieter aus der Liste aus und nehmen Sie die erforderlichen Änderungen vor. (Siehe [Authentifizierungseinstellungen](configuring-authentication-providers.md#authentication-settings)).
1. Klicken Sie auf OK.

## Authentifizierungsanbieter löschen {#delete-an-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Wählen Sie die gewünschte Domain in der Liste aus.
1. Aktivieren Sie die Kontrollkästchen der Authentifizierungsanbieter, die gelöscht werden sollen, und klicken Sie auf &quot;Löschen&quot;.
1. Klicken Sie auf der angezeigten Bestätigungsseite auf OK und klicken Sie erneut auf OK .

## Authentifizierungseinstellungen {#authentication-settings}

Die folgenden Einstellungen stehen je nach gewähltem Domain- und Authentifizierungstyp zur Verfügung.

### LDAP-Einstellungen {#ldap-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybrid-Domain konfigurieren und LDAP-Authentifizierung auswählen, können Sie den in Ihrer Ordnerkonfiguration angegebenen LDAP-Server verwenden oder einen anderen LDAP-Server auswählen, der zur Authentifizierung verwendet werden soll. Wenn Sie einen anderen Server auswählen, müssen Ihre Benutzenden auf beiden LDAP-Servern vorhanden sein.

Um den in Ihrer Ordnerkonfiguration angegebenen LDAP-Server zu verwenden, wählen Sie LDAP als Authentifizierungsanbieter aus und klicken Sie auf OK.

Um einen anderen LDAP-Server für die Authentifizierung zu verwenden, wählen Sie LDAP als Authentifizierungsanbieter aus und aktivieren Sie das Kontrollkästchen Benutzerdefinierte LDAP-Authentifizierung . Die folgenden Konfigurationseinstellungen werden angezeigt.

**Server** (obligatorisch): Der vollständig qualifizierte Domain-Name (FQDN) des Verzeichnis-Servers. Für einen Computer namens x im Netzwerk example.com lautet der FQDN beispielsweise x.example.com. Anstelle des vollständig qualifizierten Servernamens kann auch eine IP-Adresse verwendet werden.

**Port** (obligatorisch): Der Port, den der Verzeichnis-Server verwendet. Dies ist in der Regel Anschluss 389 bzw. 636, falls das SSL-Protokoll (Secure Sockets Layer) zum Senden der Authentifizierungsinformationen über das Netzwerk verwendet wird.

**SSL** (obligatorisch): Gibt an, ob der Verzeichnis-Server beim Senden von Daten über das Netzwerk SSL verwendet. Der Standardwert ist &quot;Nein&quot;. Wenn &quot;Ja&quot;festgelegt ist, muss das entsprechende LDAP-Serverzertifikat von der Java™-Laufzeitumgebung (JRE) des Anwendungsservers als vertrauenswürdig eingestuft werden.

**Bindung** (obligatorisch): Legt fest, wie auf das Verzeichnis zugegriffen werden soll.

**Anonym**: Es ist kein Benutzername oder Kennwort erforderlich.

**Benutzer**: Authentifizierung ist erforderlich. Geben Sie im Feld „Name“ den Namen des Benutzereintrags an, der auf den Ordner zugreifen darf. Am besten geben Sie den vollständigen definierten Namen (DN) des Benutzerkontos ein, z. B. cn=Jane Doe, ou=user, dc=can, dc=com. Geben Sie im Feld &quot;Kennwort&quot;das zugehörige Kennwort an. Diese Einstellungen sind erforderlich, wenn Sie Benutzer als Bindungsoption auswählen.

**Basis-DNs abrufen:** (Nicht obligatorisch) Ruft die Basis-DNs ab und zeigt sie in der Dropdown-Liste an. Diese Einstellung ist sinnvoll, wenn mehrere Basis-DNs vorhanden sind und Sie einen Wert auswählen müssen.

**Basis-DN:** (Obligatorisch) Wird als Ausgangspunkt für die Synchronisierung von Benutzern und Gruppen aus der LDAP-Hierarchie verwendet. Es empfiehlt sich, einen Basis-DN auf der untersten Hierarchieebene anzugeben, der alle Benutzer und Gruppen umfasst, die für Dienste synchronisiert werden müssen. Schließen Sie den DN des Benutzers nicht in diese Einstellung ein. Verwenden Sie die Einstellung Suchfilter , um einen bestimmten Benutzer zu synchronisieren.

**Seite mit folgenden Elementen füllen:** (Nicht obligatorisch) Wenn diese Einstellung aktiviert ist, werden Attribute auf den Seiten „Benutzereinstellungen“ und „Gruppeneinstellungen“ mit entsprechenden LDAP-Standardwerten aufgefüllt.

**Suchfilter:** (Obligatorisch) Der Suchfilter, der verwendet werden soll, um den Eintrag zu finden, der dem Benutzer zugeordnet ist. Siehe Syntax für Suchfilter.

### Kerberos-Einstellungen {#kerberos-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybrid-Domain konfigurieren und die Kerberos-Authentifizierung wählen, sind die folgenden Einstellungen verfügbar.

**DNS-IP:** Die DNS-IP-Adresse des Servers, auf dem AEM Forms ausgeführt wird. Unter Windows können Sie diese IP-Adresse bestimmen, indem Sie ipconfig /all in die Befehlszeile eingeben.

**KDC-Host:** Der voll qualifizierte Hostname bzw. die IP-Adresse des für die Authentifizierung verwendeten Active Directory-Servers.

**Service-Benutzer:** Wenn Sie Active Directory 2003 verwenden, ist dieser Wert die Zuordnung, die für den Service-Prinzipal in der Form `HTTP/<server name>` erstellt wird. Wenn Sie Active Directory 2008 verwenden, ist dieser Wert die Anmelde-ID des Dienstprinzipals. Nehmen wir an, der Service-Prinzipal heißt „um spnego“, die Benutzer-ID ist „spnegodemo“ und die Zuordnung lautet HTTP/example.yourcompany.com. Bei Active Directory 2003 legen Sie Service-Benutzer auf HTTP/example.yourcompany.com fest. Bei Active Directory 2008 legen Sie Dienstbenutzer auf spnegodemo fest. (Siehe Einmalige Anmeldung über SPNEGO aktivieren.)

**Dienstbereich:** Der Domain-Name für Active Directory

**Dienstkennwort:** Das Kennwort des Dienstbenutzers

**SPNEGO aktivieren:** Aktiviert die Verwendung von SPNEGO für die einmalige Anmeldung (SSO). (Siehe Einmalige Anmeldung über SPNEGO aktivieren.)

### SAML-Einstellungen {#saml-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybrid-Domain konfigurieren und die SAML-Authentifizierung wählen, sind die folgenden Einstellungen verfügbar. Weitere Informationen zu weiteren SAML-Einstellungen finden Sie unter [SAML-Dienstanbietereinstellungen konfigurieren](/help/forms/using/admin-help/configure-saml-service-provider-settings.md#configure-saml-service-provider-settings).

**Wählen Sie eine zu importierende Metadatendatei des SAML-Identitätsanbieters aus:** Klicken Sie auf „Durchsuchen“, um eine von Ihrem IDP generierte Metadatendatei des SAML-Identitätsanbieters auszuwählen, und klicken Sie dann auf „Importieren“. Die Details des Identitätsanbieters werden angezeigt.

**Titel:** Alias zu der von der Entitäts-ID bezeichneten URL. Der Titel wird ebenfalls auf der Anmeldeseite für Unternehmen und lokale Benutzer angezeigt.

**Identitäts-Provider unterstützt Client-Standardauthentifizierung:** Die Client Standardauthentifizierung wird verwendet, wenn der IDP ein SAML-Artefaktauflösungsprofil verwendet. In diesem Profil stellt User Management eine Verbindung zu einem Webdienst her, der beim IDP ausgeführt wird, um die tatsächliche SAML-Bestätigung abzurufen. Der IDP erfordert möglicherweise eine Authentifizierung. Wenn der IDP keine Authentifizierung erfordert, wählen Sie diese Option aus und geben Sie in den angegebenen Feldern einen Benutzernamen und ein Kennwort an.

**Benutzerdefinierte Eigenschaften:** Hiermit können Sie zusätzliche Eigenschaften angeben. Die zusätzlichen Eigenschaften sind Name=Wert-Paare, getrennt durch neue Zeilen.

Die folgenden benutzerdefinierten Eigenschaften sind erforderlich, wenn die Artefaktbindung verwendet wird.

* Fügen Sie die folgende benutzerdefinierte Eigenschaft hinzu, um einen Benutzernamen anzugeben, der den AEM Forms Service Provider darstellt, der für die Authentifizierung beim IDP Artefaktauflösungsdienst verwendet wird.
  `saml.idp.resolve.username=<username>`

* Fügen Sie folgende benutzerdefinierte Eigenschaft hinzu, um das Kennwort für den Benutzer, der in `saml.idp.resolve.username` angegeben ist, anzugeben.
  `saml.idp.resolve.password=<password>`

* Fügen Sie folgende benutzerdefinierte Eigenschaft hinzu, damit der Dienstanbieter die Zertifikatsüberprüfung ignorieren kann, während er die Verbindung zum Artefaktauflösungsdienst über SSL herstellt.
  `saml.idp.resolve.ignorecert=true`

### Benutzerdefinierte Einstellungen {#custom-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybrid-Domain konfigurieren und die benutzerdefinierte Authentifizierung wählen, müssen Sie den Namen des Authentifizierungsanbieters auswählen.

## Just-in-time-Bereitstellung von Benutzern {#just-in-time-provisioning-of-users}

Just-in-time-Bereitstellung erstellt automatisch einen Benutzer in der User Management-Datenbank, nachdem der Benutzer über einen Authentifizierungsanbieter authentifiziert wurde. Relevante Rollen und Gruppen werden dem neuen Benutzer auch dynamisch zugewiesen. Sie können Just-in-time-Bereitstellung für Unternehmens- und Hybrid-Domains aktivieren.

In diesem Verfahren wird beschrieben, wie herkömmliche Authentifizierung in AEM Formularen funktioniert:

1. Wenn ein Benutzer versucht, sich bei AEM Formularen anzumelden, übergibt User Management seine Anmeldeinformationen nacheinander an alle verfügbaren Authentifizierungsanbieter. (Die Anmeldedaten umfassen die Kombination aus Benutzername und Kennwort, Kerberos-Ticket, PKCS7-Signatur usw.)
1. Der Authentifizierungsanbieter überprüft die Anmeldeinformationen.
1. Der Authentifizierungsanbieter prüft dann, ob der Benutzer in der User Management-Datenbank vorhanden ist. Die folgenden Status sind möglich:

   **Vorhanden** Wenn der Benutzer aktuell und nicht gesperrt ist, gibt User Management an, dass die Authentifizierung erfolgreich war. Wenn der Benutzer nicht aktuell oder gesperrt ist, gibt User Management an, dass die Authentifizierung nicht erfolgreich war.

   **Nicht vorhanden** User Management gibt an, dass die Authentifizierung nicht erfolgreich war.

   **Ungültig** User Management gibt an, dass die Authentifizierung nicht erfolgreich war.

1. Das vom Authentifizierungsanbieter zurückgegebene Ergebnis wird ausgewertet. Wenn der Authentifizierungsanbieter die Authentifizierung erfolgreich zurückgegeben hat, kann sich der Benutzer anmelden. Andernfalls prüft User Management mit dem nächsten Authentifizierungsanbieter (Schritte 2 bis 3).
1. Authentifizierungsfehler wird zurückgegeben, wenn kein verfügbarer Authentifizierungsanbieter die Benutzeranmeldeinformationen validiert.

Wenn Just-in-time-Bereitstellung aktiviert ist, werden neue Benutzer dynamisch in User Management erstellt, wenn einer der Authentifizierungsanbieter ihre Anmeldeinformationen validiert. (Nach Schritt 3 im obigen Verfahren.)

Ohne Just-in-time-Bereitstellung schlägt die Authentifizierung fehl, wenn ein Benutzer erfolgreich authentifiziert wurde, aber nicht in der User Management-Datenbank gefunden wird. Just-in-time-Bereitstellung fügt einen Schritt im Authentifizierungsverfahren hinzu, um den Benutzer zu erstellen und ihm Rollen und Gruppen zuzuweisen.

### Just-in-time-Bereitstellung für eine Domain aktivieren {#enable-just-in-time-provisioning-for-a-domain}

1. Schreiben Sie einen Dienstcontainer, der die IdentityCreator- und AssignmentProvider-Schnittstellen implementiert. (Siehe [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).)
1. Stellen Sie den Dienstcontainer auf dem Forms-Server bereit.
1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.

   Wählen Sie eine vorhandene Domain oder klicken Sie auf „Neue Unternehmens-Domain“.

1. Zum Erstellen einer neuen Domain klicken Sie auf „Neue Unternehmens-Domain“ oder „Neue Hybrid-Domain“. Um eine vorhandene Domain zu bearbeiten, klicken Sie auf den Namen der Domain.
1. Wählen Sie Just-in-time-Bereitstellung aktivieren aus.

   ***Hinweis **: Wenn das Kontrollkästchen „Just-in-time-Bereitstellung aktivieren“ fehlt, klicken auf „Startseite“ > „Einstellungen“ > „User Management“ „Konfiguration“ > „Erweiterte Systemattribute“ und klicken Sie anschließend auf „Neu laden“.*

1. Authentifizierungsanbieter hinzufügen. Wählen Sie beim Hinzufügen von Authentifizierungsanbietern im Bildschirm &quot;Neue Authentifizierung&quot;einen registrierten Identitäts-Ersteller und einen Zuweisungsanbieter aus. (Siehe [Authentifizierungsanbieter konfigurieren](configuring-authentication-providers.md#configuring-authentication-providers).
1. Speichern Sie die Domain.
