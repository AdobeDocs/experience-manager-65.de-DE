---
title: Konfigurieren von Authentifizierungsanbietern
description: Fügen Sie Authentifizierungsanbieter hinzu, bearbeiten oder löschen Sie diese, ändern Sie die Authentifizierungseinstellungen und informieren Sie sich über Just-in-time-Bereitstellung.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: d72a3977-1423-49e0-899b-234bb76be378
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 98%

---

# Konfigurieren von Authentifizierungsanbietern {#configuring-authentication-providers}

Hybrid-Domains erfordern mindestens einen Authentifizierungsanbieter und für Unternehmens-Domains ist mindestens ein Authentifizierungs- oder Ordneranbieter erforderlich.

Wenn Sie die einmalige Anmeldung mithilfe von SPNEGO aktivieren, fügen Sie einen Kerberos-Authentifizierungsanbieter mit aktiviertem SPNEGO hinzu sowie einen LDAP-Anbieter als Backup. Diese Konfiguration ermöglicht die Benutzerauthentifizierung mit einer Benutzer-ID und einem Kennwort, falls SPNEGO nicht funktioniert. (Siehe [Aktivieren von SSO mit SPNEGO](/help/forms/using/admin-help/enabling-single-sign-on-aem.md#enable-sso-using-spnego).)

## Hinzufügen eines Authentifizierungsanbieters {#add-an-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Wählen Sie die gewünschte Domain in der Liste aus. Wenn Sie die Authentifizierung für eine neue Domain einrichten möchten, lesen Sie [Eine Unternehmens-Domain hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-an-enterprise-domain) oder [Hybrid-Domain hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-a-hybrid-domain) hinzuzufügen.
1. Klicken Sie auf „Authentifizierung hinzufügen“ und wählen Sie in der Liste „Authentifizierungsanbieter“ einen der Authentifizierungsmethode Ihres Unternehmens entsprechenden Anbieter aus.
1. Geben Sie weitere auf dieser Seite angeforderte Informationen ein.  (Siehe [Authentifizierungseinstellungen](configuring-authentication-providers.md#authentication-settings).)
1. (Optional) Klicken Sie auf „Testen“, um die Konfiguration zu testen.
1. Klicken Sie auf „OK“ und dann erneut auf „OK“.

## Bearbeiten eines vorhandenen Authentifizierungsanbieters {#edit-an-existing-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Wählen Sie die gewünschte Domain in der Liste aus.
1. Wählen Sie auf der angezeigten Seite in der Liste den geeigneten Authentifizierungsanbieter aus und nehmen Sie erforderliche Änderungen vor. (Siehe [Authentifizierungseinstellungen](configuring-authentication-providers.md#authentication-settings)).
1. Klicken Sie auf OK.

## Löschen eines Authentifizierungsanbieters {#delete-an-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.
1. Wählen Sie die gewünschte Domain in der Liste aus.
1. Wählen Sie die Kontrollkästchen der Authentifizierungsanbieter aus, die gelöscht werden sollen, und klicken Sie auf „Löschen“.
1. Klicken Sie zuerst auf der angezeigten Bestätigungsseite auf „OK“ und dann erneut auf „OK“.

## Authentifizierungseinstellungen {#authentication-settings}

Die folgenden Einstellungen stehen je nach gewähltem Domain- und Authentifizierungstyp zur Verfügung.

### LDAP-Einstellungen {#ldap-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybrid-Domain konfigurieren und LDAP-Authentifizierung auswählen, können Sie den in Ihrer Ordnerkonfiguration angegebenen LDAP-Server verwenden oder einen anderen LDAP-Server auswählen, der zur Authentifizierung verwendet werden soll. Wenn Sie einen anderen Server auswählen, müssen Ihre Benutzenden auf beiden LDAP-Servern vorhanden sein.

Um den in Ihrer Verzeichniskonfiguration angegebenen LDAP-Server zu verwenden, wählen Sie LDAP als Authentifizierungsanbieter aus und klicken Sie auf „OK“.

Wenn Sie einen anderen LDAP-Server für die Authentifizierung verwenden möchten, wählen Sie LDAP als Authentifizierungsanbieter aus und aktivieren Sie das Kontrollkästchen „Benutzerdefinierte LDAP-Authentifizierung“. Die folgenden Konfigurationseinstellungen werden angezeigt.

**Server** (obligatorisch): Der vollständig qualifizierte Domain-Name (FQDN) des Verzeichnis-Servers. Für einen Computer namens x im Netzwerk example.com lautet der FQDN beispielsweise x.example.com. Anstelle des vollständig qualifizierten Servernamens kann auch eine IP-Adresse verwendet werden.

**Port** (obligatorisch): Der Port, den der Verzeichnis-Server verwendet. Dies ist in der Regel Anschluss 389 bzw. 636, falls das SSL-Protokoll (Secure Sockets Layer) zum Senden der Authentifizierungsinformationen über das Netzwerk verwendet wird.

**SSL** (obligatorisch): Gibt an, ob der Verzeichnis-Server beim Senden von Daten über das Netzwerk SSL verwendet. Die Standardeinstellung ist „Nein“. Wenn Sie „Ja“ wählen, muss das entsprechende LDAP-Serverzertifikat von der Java™-Umgebung (Java Runtime Environment, JRE) des Anwendungs-Servers als vertrauenswürdig betrachtet werden.

**Bindung** (obligatorisch): Legt fest, wie auf das Verzeichnis zugegriffen werden soll.

**Anonym**: Es ist kein Benutzername oder Kennwort erforderlich.

**Benutzer**: Authentifizierung ist erforderlich. Geben Sie im Feld „Name“ den Namen des Benutzereintrags an, der auf den Ordner zugreifen darf. Am besten geben Sie den vollständigen definierten Namen (DN) des Benutzerkontos ein, z. B. cn=Jane Doe, ou=user, dc=can, dc=com. Geben Sie im Feld „Kennwort“ das zugehörige Kennwort an. Wenn Sie „Benutzer“ als Bindungsoption auswählen, sind diese Einstellungen obligatorisch.

**Basis-DNs abrufen:** (Nicht obligatorisch) Ruft die Basis-DNs ab und zeigt sie in der Dropdown-Liste an. Diese Einstellung ist sinnvoll, wenn mehrere Basis-DNs vorhanden sind und Sie einen Wert auswählen müssen.

**Basis-DN:** (Obligatorisch) Wird als Ausgangspunkt für die Synchronisierung von Benutzern und Gruppen aus der LDAP-Hierarchie verwendet. Am besten geben Sie einen Basis-DN auf der untersten Ebene der Hierarchie an, der alle Benutzerinnen und Benutzer sowie Gruppen umfasst, die für Dienste synchronisiert werden müssen. Schließen Sie den Benutzer-DN nicht in diese Einstellung ein. Um eine bestimmte Person zu synchronisieren, verwenden Sie die Einstellung „Suchfilter“.

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

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybrid-Domain konfigurieren und die SAML-Authentifizierung wählen, sind die folgenden Einstellungen verfügbar. Informationen zu weiteren SAML-Einstellungen finden Sie unter [Konfigurieren der SAML-Dienstanbietereinstellungen](/help/forms/using/admin-help/configure-saml-service-provider-settings.md#configure-saml-service-provider-settings).

**Wählen Sie eine zu importierende Metadatendatei des SAML-Identitätsanbieters aus:** Klicken Sie auf „Durchsuchen“, um eine von Ihrem IDP generierte Metadatendatei des SAML-Identitätsanbieters auszuwählen, und klicken Sie dann auf „Importieren“. Die Details des Identitätsanbieters werden angezeigt.

**Titel:** Alias zu der von der Entitäts-ID bezeichneten URL. Der Titel wird ebenfalls auf der Anmeldeseite für Unternehmen und lokale Benutzer angezeigt.

**Identitäts-Provider unterstützt Client-Standardauthentifizierung:** Die Client Standardauthentifizierung wird verwendet, wenn der IDP ein SAML-Artefaktauflösungsprofil verwendet. In diesem Profil stellt die Benutzerverwaltung eine Rückverbindung zu einem Web-Dienst her, der beim IDP ausgeführt wird, um die aktuelle SAML-Assertion abzurufen. Für den IDP ist möglicherweise eine Authentifizierung erforderlich. Ist dies der Fall, wählen Sie diese Option aus und geben Sie in den entsprechenden Feldern einen Benutzernamen und ein Kennwort an.

**Benutzerdefinierte Eigenschaften:** Hiermit können Sie zusätzliche Eigenschaften angeben. Die zusätzlichen Eigenschaften sind durch neue Zeilen getrennte Name-Wert-Paare.

Die folgenden benutzerdefinierten Eigenschaften sind erforderlich, wenn die Artefaktbindung verwendet wird.

* Fügen Sie die folgende benutzerdefinierte Eigenschaft hinzu, um einen Benutzernamen anzugeben, der den für die Authentifizierung des IDP-Artefaktauflösungsdienstes verwendeten AEM Forms-Dienstanbieter darstellt.
  `saml.idp.resolve.username=<username>`

* Fügen Sie folgende benutzerdefinierte Eigenschaft hinzu, um das Kennwort für den Benutzer, der in `saml.idp.resolve.username` angegeben ist, anzugeben.
  `saml.idp.resolve.password=<password>`

* Fügen Sie folgende benutzerdefinierte Eigenschaft hinzu, damit der Dienstanbieter die Zertifikatsüberprüfung ignorieren kann, während er die Verbindung zum Artefaktauflösungsdienst über SSL herstellt.
  `saml.idp.resolve.ignorecert=true`

### Benutzerdefinierte Einstellungen {#custom-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybrid-Domain konfigurieren und die benutzerdefinierte Authentifizierung wählen, müssen Sie den Namen des Authentifizierungsanbieters auswählen.

## Just-in-time-Bereitstellung von Benutzenden {#just-in-time-provisioning-of-users}

Just-in-time-Bereitstellung erstellt automatisch einen Benutzer in der User Management-Datenbank, nachdem der Benutzer über einen Authentifizierungsanbieter authentifiziert wurde. Relevante Rollen und Gruppen werden außerdem der neuen Person dynamisch zugewiesen. Sie können Just-in-time-Bereitstellung für Unternehmens- und Hybrid-Domains aktivieren.

Im vorliegenden Verfahren wird beschrieben, wie die herkömmliche Authentifizierung in AEM Forms funktioniert:

1. Wenn sich jemand bei AEM Forms anmeldet, übergibt die Benutzerverwaltung die zugehörigen Anmeldeinformationen nacheinander an alle verfügbaren Authentifizierungsanbieter. (Anmeldeinformationen beinhalten Benutzername-/Kennwort-Kombination, Kerberos-Ticket und PKCS7-Signatur)
1. Der Authentifizierungsanbieter überprüft die Anmeldeinformationen.
1. Der Authentifizierungsanbieter prüft dann, ob die Benutzenden in der User Management-Datenbank vorhanden sind. Die folgenden Status sind möglich:

   **Vorhanden** Wenn der Benutzer aktuell und nicht gesperrt ist, gibt User Management an, dass die Authentifizierung erfolgreich war. Wenn der Benutzer nicht aktuell oder gesperrt ist, gibt User Management an, dass die Authentifizierung nicht erfolgreich war.

   **Nicht vorhanden** User Management gibt an, dass die Authentifizierung nicht erfolgreich war.

   **Ungültig** User Management gibt an, dass die Authentifizierung nicht erfolgreich war.

1. Das vom Authentifizierungsanbieter zurückgegebene Ergebnis wird ausgewertet. Wenn der Authentifizierungsanbieter die Authentifizierung erfolgreich zurückgibt, können sich die Benutzenden anmelden. Andernfalls fragt das User Management beim nächsten Authentifizierungsanbieter nach (Schritte 2 bis 3).
1. Ein Authentifizierungsfehler wird zurückgegeben, wenn kein verfügbarer Authentifizierungsanbieter die Benutzeranmeldeinformationen validiert.

Wenn Just-in-time-Bereitstellung aktiviert ist, werden neue Benutzende dynamisch in der Benutzerverwaltung erstellt, wenn einer der Authentifizierungsanbieter deren Anmeldedaten validiert.  (Nach Schritt 3 im obigen Verfahren.)

Ohne Just-in-time-Bereitstellung ist die Authentifizierung nicht erfolgreich, wenn jemand authentifiziert, aber nicht in der Datenbank der Benutzerverwaltung gefunden wird. Die Just-in-time-Bereitstellung fügt dem Authentifizierungsverfahren einen Schritt hinzu, um die Benutzerin bzw. den Benutzer zu erstellen und dieser Person Rollen und Gruppen zuzuweisen.

### Just-in-time-Bereitstellung für eine Domain aktivieren {#enable-just-in-time-provisioning-for-a-domain}

1. Schreiben Sie einen Dienst-Container, der IdentityCreator- und AssignmentProvider-Schnittstellen implementiert.  (Siehe [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_de).)
1. Stellen Sie den Dienst-Container auf dem Formular-Server bereit.
1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Verwaltung“.

   Wählen Sie eine vorhandene Domain oder klicken Sie auf „Neue Unternehmens-Domain“.

1. Zum Erstellen einer neuen Domain klicken Sie auf „Neue Unternehmens-Domain“ oder „Neue Hybrid-Domain“. Um eine vorhandene Domain zu bearbeiten, klicken Sie auf den Namen der Domain.
1. Wählen Sie „Just-in-time-Bereitstellung aktivieren“.

   ***Hinweis **: Wenn das Kontrollkästchen „Just-in-time-Bereitstellung aktivieren“ fehlt, klicken auf „Startseite“ > „Einstellungen“ > „User Management“ „Konfiguration“ > „Erweiterte Systemattribute“ und klicken Sie anschließend auf „Neu laden“.*

1. Fügen Sie Authentifizierungsanbieter hinzu. Wählen Sie beim Hinzufügen von Authentifizierungsanbietern auf dem Bildschirm „Neue Authentifizierung“ einen registrierten Identitätsersteller und einen Zuweisungsanbieter aus. (Siehe [Konfigurieren der Authentifizierungsanbieter](configuring-authentication-providers.md#configuring-authentication-providers).)
1. Speichern Sie die Domain.
