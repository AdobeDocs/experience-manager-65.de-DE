---
title: Just-in-time-Benutzerbereitstellung
seo-title: Just-in-time user provisioning
description: Verwenden Sie Just-in-time-Bereitstellung, um Benutzer nach erfolgreicher Authentifizierung zum User Management hinzuzufügen und relevante Rollen und Gruppen dynamisch dem neuen Benutzer zuzuweisen.
seo-description: Use just-in-time provisioning to add users to User Management after successfull authentication and dynamically assign relevant roles and groups to the new user.
uuid: a5ad4698-70bb-487b-a069-7133e2f420c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e80c3f98-baa1-45bc-b713-51a2eb5ec165
exl-id: 7bde0a09-192a-44a8-83d0-c18e335e9afa
source-git-commit: c4cd9a61a226ace2a72d60b5b7b7432de12cb873
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 41%

---

# Just-in-time-Benutzerbereitstellung {#just-in-time-user-provisioning}

AEM Forms unterstützt die Just-in-time-Bereitstellung von Benutzern, die noch nicht in User Management vorhanden sind. Bei der Just-in-time-Bereitstellung werden Benutzer automatisch zu User Management hinzugefügt, nachdem ihre Anmeldeinformationen erfolgreich authentifiziert wurden. Darüber hinaus werden relevante Rollen und Gruppen dynamisch dem neuen Benutzer zugewiesen.

## Notwendigkeit der Just-in-time-Benutzerbereitstellung {#need-for-just-in-time-user-provisioning}

So funktioniert die herkömmliche Authentifizierung:

1. Wenn ein Benutzer versucht, sich bei AEM Formularen anzumelden, übergibt User Management die Anmeldeinformationen des Benutzers sequenziell an alle verfügbaren Authentifizierungsanbieter. (Die Anmeldedaten umfassen eine Kombination aus Benutzername/Kennwort, Kerberos-Ticket, PKCS7-Signatur usw.)
1. Der Authentifizierungsanbieter überprüft die Anmeldeinformationen.
1. Der Authentifizierungsanbieter prüft dann, ob der Benutzer in der User Management-Datenbank vorhanden ist. Die folgenden Ergebnisse sind möglich:

   **Existiert:** Wenn der Benutzer aktuell und freigeschaltet ist, gibt die Benutzerverwaltung einen Authentifizierungserfolg zurück. Wenn der Benutzer nicht aktuell oder gesperrt ist, gibt User Management an, dass die Authentifizierung nicht erfolgreich war.

   **Nicht vorhanden:** Die Benutzerverwaltung meldet einen Authentifizierungsfehler.

   **Ungültig:** Das User Management meldet einen Authentifizierungsfehler.

1. Das vom Authentifizierungsanbieter zurückgegebene Ergebnis wird ausgewertet. Wenn der Authentifizierungsanbieter die Authentifizierung erfolgreich zurückgegeben hat, kann sich der Benutzer anmelden. Andernfalls prüft User Management mit dem nächsten Authentifizierungsanbieter (Schritte 2 bis 3).
1. Authentifizierungsfehler wird zurückgegeben, wenn kein verfügbarer Authentifizierungsanbieter die Benutzeranmeldeinformationen validiert.

Wenn Just-in-time-Bereitstellung implementiert ist, wird ein neuer Benutzer dynamisch in User Management erstellt, wenn einer der Authentifizierungsanbieter die Anmeldeinformationen des Benutzers überprüft. (Nach Schritt 3 im obigen herkömmlichen Authentifizierungsverfahren.)

## Just-in-time-Benutzerbereitstellung implementieren {#implement-just-in-time-user-provisioning}

### APIs für Just-in-time-Bereitstellung {#apis-for-just-in-time-provisioning}

AEM forms bietet die folgenden APIs für die Just-in-time-Bereitstellung:

```java
package com.adobe.idp.um.spi.authentication  ;
publ ic interface IdentityCreator {
/**
* Tries  to create a user with the  in formation  provided in the <code>UserProvisioningBO</code> object.
* If the user is successfully created, a valid AuthResponse is returned along with the information using which the user was created.
* It is the responsibility of the IdentityCreator to set the User obje ct  in the cre dential map with th e  ke y  <code>UMA u thenticationUtil.authenticatedUserKey</code>
* The credentials are available in the <code>UserProvisioningBO</code> object in the 'credentials' property.
* If the IdentityCreator is unable to create a user due to any reason, it returns <code>null</code>
* @param userBO An object of <code>com.adobe. i dp.um . spi.authenti c ationUserProvisioningBO</code>
* @return */public AuthResponse create(UserProvisioningBO userBO);
/**
* Returns the name of the IdentityCreator which will be registered in preferences.
* This name is used to associate the IdentityProvider with the Auth Provider Configuration in the domain.
* @return The name of the Identity Creator which is recognized in Configuration.
*/
public String getName();
}
package com.adobe.idp.um.spi.authentication;
import com.adobe.idp.um.api.infomodel.User;
public interface AssignmentProvider {
/**
* Tries to assign roles or permissions or group memberships to users created via Just-in-time provisioning.
* @param user The User created via the Just-in-time provisioning process.
* @return a Boolean flag indicating whether the assignment was successful or not.
*/
public Boolean assign(User user);
/**
* Returns the name of the AssignmentProvider through which it is registered under preferences.
* This name is used to associate the AssignmentProvider with the Auth Provider Configuration in the domain.
* @return The name of the AssignmentProvider which is recognized in Configuration.
*/public String getName();
}
```

### Überlegungen beim Erstellen einer Just-in-time-Domain {#considerations-while-creating-a-just-in-time-enabled-domain}

* Beim Erstellen eines benutzerdefinierten `IdentityCreator` für eine Hybrid-Domain stellen Sie sicher, dass für den lokalen Benutzer ein Platzhalter-Kennwort angegeben wird. Lassen Sie das Kennwortfeld nicht leer.
* Empfehlung: Verwenden Sie `DomainSpecificAuthentication`, um die Benutzerinformationen für eine bestimmte Domain zu überprüfen.

### Erstellen einer Just-in-time-Domain {#create-a-just-in-time-enabled-domain}

1. Schreiben Sie ein DSC, das die API im Abschnitt „APIs für Just-in-time-Bereitstellung“ implementiert.
1. Stellen Sie das DSC auf dem Forms-Server bereit.
1. Erstellen Sie eine Just-in-time-Domain:

   * Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Namensverwaltung“ > „Neue Unternehmens-Domain“.
   * Konfigurieren Sie die Domain und aktivieren Sie „Just-in-time-Bereitstellung aktivieren“. <!--Fix broken link (See Setting up and managing domains).-->
   * Authentifizierungsanbieter hinzufügen. Wählen Sie beim Hinzufügen von Authentifizierungsanbietern im Bildschirm &quot;Neue Authentifizierung&quot;einen registrierten Identitäts-Ersteller und einen Zuweisungsanbieter aus.

1. Speichern Sie die neue Domain.

## Hinter den Kulissen {#behind-the-scenes}

Angenommen, ein Benutzer versucht sich bei AEM Formularen anzumelden und ein Authentifizierungsanbieter akzeptiert seine Benutzeranmeldeinformationen. Wenn der Benutzer noch nicht in der User Management-Datenbank vorhanden ist, schlägt die Identitätsprüfung für den Benutzer fehl. AEM Formulare führen jetzt die folgenden Aktionen aus:

1. `UserProvisioningBO`-Objekt mit den Authentifizierungsdaten erstellen und in einer Benutzerdatenzuordnung ablegen.
1. Basierend auf den von `UserProvisioningBO` zurückgegebenen Domain-Namensdaten `IdentityCreator` und `AssignmentProvider` für die Domain laden und aufrufen.
1. Rufen Sie `IdentityCreator` auf. Wenn ein erfolgreiches`AuthResponse` zurückgegeben wird, `UserInfo` aus der Benutzerdatenzuordnung extrahieren. An `AssignmentProvider` für Gruppen-/Rollenzuweisung und andere Nachbearbeitungsvorgänge übergeben, nachdem der Benutzer erstellt wurde.
1. Wenn der Benutzer erfolgreich erstellt wurde, geben Sie den Anmeldeversuch des Benutzers als erfolgreich zurück.
1. Bei Hybrid-Domains Benutzerdaten aus den Authentifizierungsdaten extrahieren, die vom Authentifizierungsanbieter bereitgestellt wurden. Wenn diese Informationen erfolgreich abgerufen werden, erstellen Sie den Benutzer direkt.

>[!NOTE]
>
>Bei der Just-in-time-Bereitstellung ist `IdentityCreator` standardmäßig implementiert. Damit können Sie Benutzer dynamisch erstellen. Benutzer werden mit den Daten erstellt, die mit den Ordnern in der Domain verknüpft sind.
