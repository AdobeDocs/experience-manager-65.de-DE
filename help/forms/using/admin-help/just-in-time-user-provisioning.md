---
title: Just-in-time-Benutzerbereitstellung
description: Verwenden Sie die Just-in-time-Bereitstellung, um Benutzende nach erfolgreicher Authentifizierung zum User Management hinzuzufügen und relevante Rollen und Gruppen dynamisch den neuen Benutzenden zuzuweisen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 7bde0a09-192a-44a8-83d0-c18e335e9afa
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 100%

---

# Just-in-time-Benutzerbereitstellung {#just-in-time-user-provisioning}

AEM Forms unterstützt die Just-in-time-Bereitstellung von Benutzenden, die noch nicht im User Management vorhanden sind. Bei der Just-in-time-Bereitstellung werden Benutzende automatisch zum User Management hinzugefügt, nachdem ihre Anmeldeinformationen erfolgreich authentifiziert wurden. Darüber hinaus werden relevante Rollen und Gruppen dynamisch den neuen Benutzenden zugewiesen.

## Notwendigkeit der Just-in-time-Benutzerbereitstellung {#need-for-just-in-time-user-provisioning}

So funktioniert die herkömmliche Authentifizierung:

1. Wenn Benutzende versuchen, sich bei AEM Forms anzumelden, übergibt das User Management die Anmeldeinformationen der Benutzenden sequenziell an alle verfügbaren Authentifizierungsanbieter. (Die Anmeldedaten umfassen eine Kombination aus Benutzername/Kennwort, Kerberos-Ticket, PKCS7-Signatur usw.)
1. Der Authentifizierungsanbieter überprüft die Anmeldeinformationen.
1. Der Authentifizierungsanbieter prüft dann, ob die Benutzenden in der User Management-Datenbank vorhanden sind. Die folgenden Ergebnisse sind möglich:

   **Existiert:** Wenn der Benutzer aktuell und freigeschaltet ist, gibt die Benutzerverwaltung einen Authentifizierungserfolg zurück. Wenn der Benutzer nicht aktuell oder gesperrt ist, gibt User Management an, dass die Authentifizierung nicht erfolgreich war.

   **Nicht vorhanden:** Die Benutzerverwaltung meldet einen Authentifizierungsfehler.

   **Ungültig:** Das User Management meldet einen Authentifizierungsfehler.

1. Das vom Authentifizierungsanbieter zurückgegebene Ergebnis wird ausgewertet. Wenn der Authentifizierungsanbieter die Authentifizierung erfolgreich zurückgibt, können sich die Benutzenden anmelden. Andernfalls fragt das User Management beim nächsten Authentifizierungsanbieter nach (Schritte 2 bis 3).
1. Ein Authentifizierungsfehler wird zurückgegeben, wenn kein verfügbarer Authentifizierungsanbieter die Benutzeranmeldeinformationen validiert.

Wenn die Just-in-time-Bereitstellung implementiert ist, werden neue Benutzende dynamisch im User Management erstellt, wenn einer der Authentifizierungsanbieter die Anmeldeinformationen der Benutzenden validiert. (Nach Schritt 3 im obigen herkömmlichen Authentifizierungsverfahren.)

## Implementieren der Just-in-Time-Benutzerbereitstellung {#implement-just-in-time-user-provisioning}

### APIs für die Just-in-time-Bereitstellung {#apis-for-just-in-time-provisioning}

AEM Forms bietet die folgenden APIs für die Just-in-time-Bereitstellung:

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
1. Stellen Sie den DSC auf dem Forms-Server bereit.
1. Erstellen Sie eine Just-in-time-Domain:

   * Klicken Sie in Administration Console auf „Einstellungen“ > „User Management“ > „Domain-Namensverwaltung“ > „Neue Unternehmens-Domain“.
   * Konfigurieren Sie die Domain und wählen Sie „Just-in-time-Bereitstellung aktivieren“.<!--Fix broken link (See Setting up and managing domains).-->
   * Fügen Sie Authentifizierungsanbieter hinzu. Wählen Sie beim Hinzufügen von Authentifizierungsanbietern auf dem Bildschirm „Neue Authentifizierung“ einen registrierten Identitätsersteller und einen Zuweisungsanbieter aus.

1. Speichern Sie die neue Domain.

## Hinter den Kulissen {#behind-the-scenes}

Angenommen, eine Person versucht, sich bei AEM Forms anzumelden, und ein Authentifizierungsanbieter akzeptiert ihre Benutzeranmeldeinformationen. Wenn die Person noch nicht in der User Management-Datenbank vorhanden ist, schlägt die Identitätsprüfung für diese Person fehl. AEM Forms führt jetzt die folgenden Aktionen aus:

1. `UserProvisioningBO`-Objekt mit den Authentifizierungsdaten erstellen und in einer Benutzerdatenzuordnung ablegen.
1. Basierend auf den von `UserProvisioningBO` zurückgegebenen Domain-Namensdaten `IdentityCreator` und `AssignmentProvider` für die Domain laden und aufrufen.
1. Rufen Sie `IdentityCreator` auf. Wenn ein erfolgreiches`AuthResponse` zurückgegeben wird, `UserInfo` aus der Benutzerdatenzuordnung extrahieren. An `AssignmentProvider` für Gruppen-/Rollenzuweisung und andere Nachbearbeitungsvorgänge übergeben, nachdem der Benutzer erstellt wurde.
1. Wenn die Person erfolgreich erstellt wurde, wird der Anmeldeversuch der Person als erfolgreich zurückgegeben.
1. Bei Hybrid-Domains Benutzerdaten aus den Authentifizierungsdaten extrahieren, die vom Authentifizierungsanbieter bereitgestellt wurden. Wenn diese Informationen erfolgreich geladen werden, wird die Person spontan erstellt.

>[!NOTE]
>
>Bei der Just-in-time-Bereitstellung ist `IdentityCreator` standardmäßig implementiert. Damit können Sie Benutzer dynamisch erstellen. Benutzer werden mit den Daten erstellt, die mit den Ordnern in der Domain verknüpft sind.
