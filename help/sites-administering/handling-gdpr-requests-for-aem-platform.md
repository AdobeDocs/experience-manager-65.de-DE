---
title: Umgang mit DSGVO-Anfragen für die Adobe Experience Manager Foundation
description: Umgang mit DSGVO-Anfragen für die Adobe Experience Manager Foundation
contentOwner: sarchiz
exl-id: 411d40ab-6be8-4658-87f6-74d2ac1a4913
source-git-commit: 96e2e945012046e6eac878389b7332985221204e
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 66%

---

# Umgang mit DSGVO-Anfragen für die Adobe Experience Manager (AEM Foundation){#handling-gdpr-requests-for-the-aem-foundation}

>[!IMPORTANT]
>
>Die DSGVO dient in den folgenden Abschnitten als Beispiel, die jeweiligen Informationen gelten jedoch für alle Datenschutzvorschriften und -bestimmungen. wie DSGVO, CCPA usw.

## AEM Foundation – DSGVO-Unterstützung {#aem-foundation-gdpr-support}

Auf AEM Foundation-Ebene werden personenbezogene Daten im Benutzerprofil gespeichert. Daher wird in diesem Artikel hauptsächlich beschrieben, wie Sie auf Benutzerprofile zugreifen und diese löschen, um die DSGVO-Zugriffs- bzw. Löschanfragen zu behandeln.

## Zugreifen auf Benutzerprofile {#accessing-a-user-profile}

### Manuelle Schritte {#manual-steps}

1. Öffnen Sie die Konsole für die Benutzerverwaltung, indem Sie zu **[!UICONTROL Einstellungen > Sicherheit > Benutzer]** navigieren oder die Seite `https://<serveraddress>:<serverport>/libs/granite/security/content/useradmin.html` direkt aufrufen.

   ![useradmin2](assets/useradmin2.png)

1. Suchen Sie dann den jeweiligen Benutzer, indem Sie dessen Name in der Suchleiste oben auf der Seite eingeben:

   ![usersearch](assets/usersearch.png)

1. Klicken Sie nun auf das Benutzerprofil, um es zu öffnen, und rufen Sie die Registerkarte **[!UICONTROL Details]** auf.

   ![userprofile_small](assets/userprofile_small.png)

### HTTP-API {#http-api}

Wie bereits erwähnt, stellt Adobe APIs für den Zugriff auf Benutzerdaten bereit, um die Automatisierung zu erleichtern. Es stehen verschiedene Arten von APIs zur Verfügung:

**UserProperties-API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**Sling-API**

*Ermitteln der Benutzerstartseite:*

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

*Abrufen von Benutzerdaten*

Verwenden Sie dazu den Knotenpfad der über den vorangegangenen Befehl ausgegebenen Home-Eigenschaft der JSON-Payload:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Deaktivieren von Benutzern und Löschen der zugehörigen Profile {#disabling-a-user-and-deleting-the-associated-profiles}

### Deaktivieren von Benutzern {#disable-user}

1. Öffnen Sie die Konsole für die Benutzerverwaltung und suchen Sie nach dem entsprechenden Benutzer, wie oben beschrieben.
1. Bewegen Sie den Mauszeiger über den Benutzer und klicken Sie auf das Auswahlsymbol. Das Profil wird grau dargestellt und zeigt an, dass es ausgewählt ist.

1. Klicken Sie auf die Schaltfläche Deaktivieren im oberen Menü, um den Benutzer zu deaktivieren:

   ![userdisable](assets/userdisable.png)

1. Bestätigen Sie abschließend die Aktion:

   ![image2018-2-6_1-40-58](assets/image2018-2-6_1-40-58.png)

   Die Benutzeroberfläche zeigt an, dass der Benutzer deaktiviert wird, indem er ausgegraut wird und der Profilkarte eine Sperre hinzufügt:

   ![disableduser](assets/disableduser.png)

### Löschen von Benutzerprofilinformationen {#delete-user-profile-information}

1. Melden Sie sich bei CRXDE Lite an und suchen Sie nach `[!UICONTROL userId]`:

   ![image2018-2-6_1-57-11](assets/image2018-2-6_1-57-11.png)

1. Öffnen Sie den Benutzerknoten. Dieser befindet sich standardmäßig unter `[!UICONTROL /home/users]`:

   ![image2018-2-6_1-58-25](assets/image2018-2-6_1-58-25.png)

1. Löschen Sie die Profilknoten und alle untergeordneten Elemente. Die Profilknoten haben je nach AEM zwei Formate:

   1. Das private Standardprofil unter `[!UICONTROL /profile]`
   1. `[!UICONTROL /profiles]` für neue Profile, die mit AEM 6.5 erstellt werden

   ![image2018-2-6_2-0-4](assets/image2018-2-6_2-0-4.png)

### HTTP-API {#http-api-1}

Die folgenden Verfahren verwenden die `curl` Befehlszeilen-Tool, um zu veranschaulichen, wie der Benutzer mit der **[!UICONTROL Höhle]** `userId` und Löschen von Profilen `cavery` die am Standardspeicherort verfügbar sind.

* *Ermitteln der Benutzerstartseite*

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

* *Deaktivieren des Benutzers*

Verwenden Sie dazu den Knotenpfad der über den vorangegangenen Befehl ausgegebenen Home-Eigenschaft der JSON-Payload:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (GDPR in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

* *Löschen von Benutzerprofilen*

Verwenden Sie dazu den Knotenpfad der Home-Eigenschaft der JSON-Payload, der über den Befehl zur Ermittlung der Benutzerstartseite ausgegeben wurde, sowie die bekannten vorkonfigurierten Speicherorte des Profilknotens:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
