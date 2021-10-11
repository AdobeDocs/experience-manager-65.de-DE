---
title: Authentifizierungsanbieter konfigurieren
seo-title: Configuring authentication providers
description: Fügen Sie Authentifizierungsanbieter hinzu, bearbeiten oder löschen Sie diese, ändern Sie die Authentifizierungseinstellungen und informieren Sie sich über Just-in-time-Bereitstellung.
seo-description: Add, edit, or delete authentication providers, change authentication settings, and read about just-in-time provisioning of users.
uuid: 90e7690b-1ce0-4604-b58f-6dca4f2372cf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 31dd8db3-ddac-429e-82f8-8c5dc4ffc186
exl-id: d72a3977-1423-49e0-899b-234bb76be378
source-git-commit: 1cdd15800548362ccdd9e70847d9df8ce93ee06e
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 80%

---

# Authentifizierungsanbieter konfigurieren {#configuring-authentication-providers}

Hybriddomänen erfordern mindestens einen Authentifizierungsanbieter und für Unternehmensdomänen ist mindestens ein Authentifizierungs- oder Ordneranbieter erforderlich.

Wenn Sie die einmalige Anmeldung mithilfe von SPNEGO aktivieren, fügen Sie einen Kerberos-Authentifizierungsanbieter mit aktiviertem SPNEGO hinzu sowie einen LDAP-Anbieter als Sicherung. Diese Konfiguration ermöglicht Benutzerauthentifizierung mit einer Benutzer-ID und einem Kennwort, falls SPNEGO nicht funktioniert. (Siehe [Einmalige Anmeldung über SPNEGO aktivieren](/help/forms/using/admin-help/enabling-single-sign-on-aem.md#enable-sso-using-spnego).)

## Authentifizierungsanbieter hinzufügen {#add-an-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Wählen Sie die gewünschte Domäne in der Liste aus. Wenn Sie die Authentifizierung für eine neue Domäne einrichten möchten, lesen Sie [Eine Unternehmensdomäne hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-an-enterprise-domain) oder [Hybriddomäne hinzufügen](/help/forms/using/admin-help/adding-domains.md#add-a-hybrid-domain) hinzuzufügen.
1. Klicken Sie auf „Authentifizierung hinzufügen“ und wählen Sie in der Liste „Authentifizierungsanbieter“ einen der Authentifizierungsmethode Ihres Unternehmens entsprechenden Anbieter aus.
1. Geben Sie weitere auf dieser Seite angeforderte Informationen ein. (Siehe [Authentifizierungseinstellungen](configuring-authentication-providers.md#authentication-settings).)
1. (Optional) Klicken Sie auf „Testen“ um die Konfiguration zu testen.
1. Klicken Sie auf „OK“ und dann erneut auf „OK“.

## Einen vorhandenen Authentifizierungsanbieter bearbeiten {#edit-an-existing-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Wählen Sie die gewünschte Domäne in der Liste aus.
1. Wählen Sie auf der angezeigten Seite in der Liste den geeigneten Authentifizierungsanbieter aus und nehmen Sie erforderliche Änderungen vor. (Siehe [Authentifizierungseinstellungen](configuring-authentication-providers.md#authentication-settings).)
1. Klicken Sie auf OK.

## Einen Authentifizierungsanbieter löschen {#delete-an-authentication-provider}

1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.
1. Wählen Sie die gewünschte Domäne in der Liste aus.
1. Aktivieren Sie die Kontrollkästchen der Authentifizierungsanbieter, die gelöscht werden sollen, und klicken Sie auf „Löschen“.
1. Klicken Sie zuerst auf der angezeigten Bestätigungsseite auf „OK“ und dann erneut auf „OK“.

## Authentifizierungseinstellungen {#authentication-settings}

Die folgenden Einstellungen stehen je nach gewähltem Domänen- und Authentifizierungstyp zur Verfügung.

### LDAP-Einstellungen {#ldap-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybriddomäne konfigurieren und LDAP-Authentifizierung auswählen, können Sie den in Ihrer Ordnerkonfiguration angegebenen LDAP-Server verwenden oder einen anderen LDAP-Server auswählen, der zur Authentifizierung verwendet werden soll. Wenn Sie einen anderen Server auswählen, müssen Ihre Benutzer auf beiden LDAP-Servern vorhanden sein.

Um den in Ihrer Ordnerkonfiguration angegebenen LDAP-Server zu verwenden, wählen Sie LDAP als Authentifizierungsanbieter aus und klicken Sie auf „OK“.

Wenn Sie einen anderen LDAP-Server für die Authentifizierung verwenden möchten, wählen Sie LDAP als Authentifizierungsanbieter aus und aktivieren Sie das Kontrollkästchen „Benutzerdefinierte LDAP-Authentifizierung“. Es werden die folgenden Konfigurationseinstellungen angezeigt.

**Server:**  (Obligatorisch) Vollqualifizierter Domänenname (FQDN) des Ordnerservers. Beispiel: Für einen Computer mit dem Namen x im Netzwerk example.com lautet der FQDN x.example.com. Anstelle des vollständig qualifizierten Servernamens kann auch eine IP-Adresse verwendet werden.

**Port:**  (Obligatorisch) Der Port, den der Ordnerserver verwendet. Dies ist in der Regel Anschluss 389 bzw. 636, falls das SSL-Protokoll (Secure Sockets Layer) zum Senden der Authentifizierungsinformationen über das Netzwerk verwendet wird.

**SSL:**  (Obligatorisch) Gibt an, ob der Ordnerserver SSL beim Senden von Daten über das Netzwerk verwendet. Die Standardeinstellung ist „Nein“. Wenn Sie „Ja“ wählen, muss das entsprechende LDAP-Serverzertifikat von der Java™-Umgebung (Java Runtime Environment) des Anwendungsservers als vertrauenswürdig betrachtet werden.

**Bindung**  (Obligatorisch) Gibt an, wie auf den Ordner zugegriffen wird.

**Anonym:** Es ist kein Benutzername oder Kennwort erforderlich.

**Benutzer:** Authentifizierung ist erforderlich. Geben Sie im Feld „Name“ den Namen des Benutzereintrags an, der auf den Ordner zugreifen darf. Am besten geben Sie den vollständigen definierten  Namen (DN) des Benutzerkontos ein, z. B. cn=Jane Doe, ou=user, dc=can, dc=com. Geben Sie im Feld „Kennwort“ das zugehörige Kennwort an. Wenn Sie „Benutzer“ als Bindungsoption auswählen, sind diese Einstellungen obligatorisch.

**Basis-DNs abrufen:**  (Nicht obligatorisch) Ruft die Basis-DNs ab und zeigt sie in der Dropdownliste an. Diese Einstellung ist sinnvoll, wenn mehrere Basis-DNs vorhanden sind und Sie einen Wert auswählen müssen.

**Basis-DN:**  (Obligatorisch) Wird als Ausgangspunkt für die Synchronisierung von Benutzern und Gruppen aus der LDAP-Hierarchie verwendet. Es empfiehlt sich, einen Basis-DN auf der niedrigsten Hierarchieebene anzugeben, die sämtliche Benutzer und Gruppen enthält, die für Dienste synchronisiert werden müssen. Diese Einstellung enthält nicht den definierten Namen (DN) des Benutzers. Um einen bestimmten Benutzer zu synchronisieren, wählen Sie die Einstellung „Suchfilter“.

**Seite mit folgenden Elementen füllen:**  (Nicht obligatorisch) Wenn ausgewählt, werden Attribute auf den Seiten &quot;Benutzer- und Gruppeneinstellungen&quot;mit entsprechenden LDAP-Standardwerten gefüllt.

**Suchfilter:**  (Obligatorisch) Der Suchfilter, der verwendet werden soll, um den Datensatz zu finden, der dem Benutzer zugeordnet ist. Siehe Syntax für Suchfilter.

### Kerberos-Einstellungen {#kerberos-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybriddomäne konfigurieren und die Kerberos-Authentifizierung wählen, sind die folgenden Einstellungen verfügbar.

**DNS-IP:** Die DNS-IP-Adresse des Servers, auf dem AEM Forms ausgeführt wird. Unter Windows können Sie diese IP-Adresse bestimmen, indem Sie ipconfig /all in die Befehlszeile eingeben.

**KDC-Host:** Vollständig qualifizierter Hostname oder IP-Adresse des für die Authentifizierung verwendeten Active Directory-Servers.

**Dienstbenutzer:** Wenn Sie Active Directory 2003 verwenden, ist dieser Wert die für den Dienstprinzipal im Formular erstellte Zuordnung  `HTTP/<server name>`. Wenn Sie Active Directory 2008 verwenden, ist dieser Wert die Anmelde-ID des Dienstprinzipals. Angenommen, der Dienstprinzipal heißt um spnego, die Benutzer-ID lautet spnegodemo und die Zuordnung lautet HTTP/example.yourcompany.com. Bei Active Directory 2003 legen Sie Dienstbenutzer auf HTTP/example.yourcompany.com fest. Bei Active Directory 2008 legen Sie Dienstbenutzer auf spnegodemo fest. (Siehe Einmalige Anmeldung über SPNEGO aktivieren.)

**Dienstbereich:** Der Domänenname für Active Directory

**Dienstkennwort:** Das Kennwort des Dienstbenutzers

**SPNEGO aktivieren:** Aktiviert die Verwendung von SPNEGO für die einmalige Anmeldung (SSO). (Siehe Einmalige Anmeldung über SPNEGO aktivieren.)

### SAML-Einstellungen {#saml-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybriddomäne konfigurieren und die SAML-Authentifizierung wählen, sind die folgenden Einstellungen verfügbar. Informationen zu weiteren SAML-Einstellungen finden Sie unter [SAML-Dienstanbietereinstellungen konfigurieren](/help/forms/using/admin-help/configure-saml-service-provider-settings.md#configure-saml-service-provider-settings).

**Wählen Sie eine zu importierende Metadatendatei des SAML-Identitätsanbieters aus:**  Klicken Sie auf Durchsuchen , um eine Metadatendatei des SAML-Identitätsanbieters auszuwählen, die von Ihrem IDP generiert wurde, und klicken Sie dann auf Importieren. Die Details des Identitätsanbieters werden angezeigt.

**Titel:** Alias für die URL, die durch die EntityID gekennzeichnet wird. Der Titel wird ebenfalls auf der Anmeldeseite für Unternehmen und lokale Benutzer angezeigt.

**Identitäts-Provider unterstützt Client Basic-Authentifizierung:** Client Basic-Authentifizierung wird verwendet, wenn der IDP ein SAML-Artefaktauflösungsprofil verwendet. In diesem Profil stellt User Management eine Verbindung zurück zu einem Webdienst her, der beim IDP ausgeführt wird, um die aktuelle SAML-Bestätigung abzurufen. Der IDP erfordert möglicherweise eine Authentifizierung. Wenn der IDP eine Authentifizierung erfordert, wählen Sie diese Option aus und geben Sie in den entsprechenden Feldern einen Benutzernamen und ein Kennwort an.

**Benutzerdefinierte Eigenschaften:** Ermöglicht die Angabe zusätzlicher Eigenschaften. Die zusätzlichen Eigenschaften lauten Name=Wert, Paare durch neue Zeilen getrennt.

Die folgenden benutzerdefinierten Eigenschaften sind erforderlich, wenn Artefaktbindung verwendet wird.

* Fügen Sie folgende benutzerdefinierte Eigenschaft hinzu, um einen Benutzernamen anzugeben, der den AEM Forms-Dienstanbieter darstellt, welcher für die Authentifizierung des IDP-Artefaktauflösungsdienstes verwendet wird.
   `saml.idp.resolve.username=<username>`

* Fügen Sie folgende benutzerdefinierte Eigenschaft hinzu, um das Kennwort für den Benutzer, der in `saml.idp.resolve.username` angegeben ist, anzugeben.
   `saml.idp.resolve.password=<password>`

* Fügen Sie folgende benutzerdefinierte Eigenschaft hinzu, damit der Dienstanbieter die Zertifikatsüberprüfung ignorieren kann, während er die Verbindung zum Artefaktauflösungsdienst über SSL herstellt.
   `saml.idp.resolve.ignorecert=true`

### Benutzerdefinierte Einstellungen {#custom-settings}

Wenn Sie die Authentifizierung für eine Unternehmens- oder Hybriddomäne konfigurieren und die benutzerdefinierte Authentifizierung wählen, müssen Sie den Namen des Authentifizierungsanbieters auswählen.

## Just-in-time-Bereitstellung {#just-in-time-provisioning-of-users}

Just-in-time-Bereitstellung erstellt automatisch einen Benutzer in der User Management-Datenbank, nachdem der Benutzer über einen Authentifizierungsanbieter authentifiziert wurde. Relevante Rollen und Gruppen werden dem neuen Benutzer außerdem dynamisch zugewiesen. Sie können Just-in-time-Bereitstellung für Unternehmens- und Hybriddomänen aktivieren.

Im vorliegenden Verfahren wird beschrieben, wie herkömmliche Authentifizierung in AEM Forms funktioniert:

1. Wenn sich der Benutzer bei AEM Forms anmeldet, übergibt User Management die Anmeldeinformationen sequenziell an alle verfügbaren Authentifizierungsanbieter. (Anmeldeinformationen beinhalten Benutzername-/Kennwort-Kombination, Kerberos-Ticket, PKCS7-Signatur usw.)
1. Der Authentifizierungsanbieter überprüft die Anmeldeinformationen.
1. Der Authentifizierungsanbieter prüft anschließend, ob der Benutzer in der User Management-Datenbank vorhanden ist. Die folgenden Status sind möglich:

   **** ExistsWenn der Benutzer aktuell und entsperrt ist, gibt User Management den Authentifizierungserfolg zurück. Wenn der Benutzer nicht aktuell oder gesperrt ist, gibt User Management an, dass die Authentifizierung nicht erfolgreich war.

   **Ist nicht** vorhandenUser Management gibt Authentifizierungsfehler zurück.

   **** InvalidUser Management gibt Authentifizierungsfehler zurück.

1. Das vom Authentifizierungsanbieter zurückgegebene Ergebnis wird ausgewertet. Wenn der Authentifizierungsanbieter angibt, dass die Authentifizierung erfolgreich war, kann sich der Benutzer anmelden. Andernfalls nimmt User Management mit dem nächsten Authentifizierungsanbieter eine Überprüfung vor (Schritte 2 bis 3).
1. Die Authentifizierung war nicht erfolgreich, wenn kein verfügbarer Authentifizierungsanbieter die Anmeldeinformationen des Benutzers überprüft.

Wenn Just-in-time-Bereitstellung aktiviert ist, werden neue Benutzer dynamisch in User Management erstellt, wenn einer der Authentifizierungsanbieter deren Anmeldedaten validiert. (Nach Schritt 3 im obigen Verfahrens.)

Ohne Just-in-time-Bereitstellung ist die Authentifizierung nicht erfolgreich, wenn ein Benutzer authentifiziert wird, aber nicht in der User Management-Datenbank gefunden wird. Just-in-time-Bereitstellung fügt dem Authentifizierungsverfahren einen Schritt hinzu, um den Benutzer zu erstellen und ihm Rollen und Gruppen zuzuweisen.

### Just-in-time-Bereitstellung für eine Domäne aktivieren {#enable-just-in-time-provisioning-for-a-domain}

1. Schreiben Sie einen Dienstcontainer, der IdentityCreator- und AssignmentProvider-Schnittstelle implementiert. (Weitere Informationen finden Sie unter [Programmieren mit AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63).)
1. Stellen Sie den Dienstcontainer auf dem Formularserver bereit.
1. Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domänenverwaltung“.

   Wählen Sie eine vorhandene Domäne oder klicken Sie auf „Neue Unternehmensdomäne“.

1. Zum Erstellen einer neuen Domäne klicken Sie auf „Neue Unternehmensdomäne“ oder „Neue Hybriddomäne“. Um eine vorhandene Domäne zu bearbeiten, klicken Sie auf den Namen der Domäne.
1. Wählen Sie „Just-in-time-Bereitstellung aktivieren“.

   ***Hinweis **: Wenn das Kontrollkästchen „Just-in-time-Bereitstellung aktivieren“ fehlt, klicken auf „Startseite“ > „Einstellungen“ > „User Management“ „Konfiguration“ > „Erweiterte Systemattribute“ und klicken Sie anschließend auf „Neu laden“.*

1. Authentifizierungsanbieter hinzufügen. Wählen Sie beim Hinzufügen von Authentifizierungsanbietern auf dem Bildschirm „Neue Authentifizierung“ einen registrierten ID-Ersteller und einen Zuweisungsanbieter. (Siehe [Authentifizierungsanbieter konfigurieren](configuring-authentication-providers.md#configuring-authentication-providers).)
1. Speichern Sie die Domäne.
