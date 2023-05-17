---
title: Unterstützung der Adobe IMS-Authentifizierung und der [!DNL Admin Console] für AEM Managed Services
seo-title: Adobe IMS Authentication and [!DNL Admin Console] Support for AEM Managed Services
description: Erfahren Sie, wie Sie die  [!DNL Admin Console] in AEM verwenden.
seo-description: Learn how to use the [!DNL Admin Console] in AEM.
uuid: 3f5b32c7-cf62-41a4-be34-3f71bbf224eb
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: f6112dea-a1eb-4fd6-84fb-f098476deab7
exl-id: 95eae97c-01c2-4f5c-8068-f504eab7c49e
feature: Security
source-git-commit: fff35031eaf55b185870da56a0b66f9145b1ec41
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 67%

---

# Unterstützung der Adobe IMS-Authentifizierung und der [!DNL Admin Console] für AEM Managed Services {#adobe-ims-authentication-and-admin-console-support-for-aem-managed-services}

>[!NOTE]
>
>Beachten Sie, dass diese Funktion nur für Kunden von Adobe Managed Services verfügbar ist.

>[!NOTE]
>
>AEM unterstützt derzeit nicht die Zuweisung von Gruppen zu Profilen.  Benutzer sollten stattdessen einzeln hinzugefügt werden.

## Einführung {#introduction}

AEM 6.4.3.0 führt die Unterstützung der [!DNL Admin Console] für AEM-Instanzen und Adobe IMS-basierte Authentifizierung (Identity Management-System) für Kundinnen und Kunden von **AEM Managed Services** ein.

Durch das AEM-Onboarding für die [!DNL Admin Console] kann Kundschaft von AEM Managed Services alle Experience Cloud-Benutzerinnen und -Benutzer in einer Konsole verwalten. Benutzer können Produktprofilen zugewiesen werden, die mit AEM Instanzen verknüpft sind, sodass sie sich bei einer bestimmten Instanz anmelden können.

## Wichtige Highlights {#key-highlights}

* AEM IMS-Authentifizierungsunterstützung ist nur für AEM-Autoren, -Administratoren oder -Entwickler, nicht für externe Endbenutzer von Kunden-Sites wie Site-Besucher
* Die [!DNL Admin Console] zeigt Kundinnen und Kunden von AEM Managed Services als „IMS-Organisationen“ und ihre Instanzen als „Produktkontexte“ an. Kundensystem- und Produktadmins können den Zugriff auf Instanzen verwalten.
* AEM Managed Services synchronisiert Kundentopologien mit der [!DNL Admin Console]. In der [!DNL Admin Console] ist pro Instanz eine AEM Managed Services-Produktkontext-Instanz vorhanden.
* Produktprofile in der [!DNL Admin Console] legen fest, auf welche Instanzen Benutzerinnen und Benutzer zugreifen können.
* Federated Authentifizierung mit den eigenen SAML 2-kompatiblen Identitätsanbietern des Kunden wird unterstützt
* Es werden nur Enterprise IDs oder Federated IDs (für Single Sign-On für Kunden) unterstützt, nicht personenbezogene Adoben-IDs.
* [!DNL User Management] (in der Adobe [!DNL Admin Console]) ist weiterhin Aufgabe der Kundenadmins.

## Architektur {#architecture}

Die IMS-Authentifizierung funktioniert mithilfe des OAuth-Protokolls zwischen AEM und dem Adobe IMS-Endpunkt. Wenn Benutzer zu IMS hinzugefügt wurden und eine Adobe ID haben, können sie sich mit den IMS-Anmeldeinformationen bei AEM Managed Services-Instanzen anmelden.

Der Benutzer-Anmeldefluss wird unten gezeigt, der Benutzer wird zur SSO-Validierung zu IMS und optional zum Kunden-IDP weitergeleitet und dann zurück zu AEM.

![image2018-9-23_23-55-8](assets/image2018-9-23_23-55-8.png)

## Einrichtung {#how-to-set-up}

### Onboarding von Organisationen in der [!DNL Admin Console] {#onboarding-organizations-to-admin-console}

Das Onboarding von Kundschaft in der [!DNL Admin Console] ist eine Voraussetzung für die Verwendung von Adobe IMS zur AEM-Authentifizierung.

Als ersten Schritt sollte Kundschaft eine Organisation in Adobe IMS bereitstellen. Adobe Enterprise-Kundschaft wird in der [Adobe  [!DNL Admin Console]](https://helpx.adobe.com/de/enterprise/using/admin-console.html) als IMS-Organisation angezeigt.

Für AEM Managed Services-Kundschaft sollte bereits eine Organisation bereitgestellt sein. Im Rahmen der IMS-Bereitstellung werden die Kundeninstanzen zur Verwaltung der Benutzerberechtigungen und -zugriffe in der [!DNL Admin Console] bereitgestellt.

Der Wechsel zu IMS zur Benutzerauthentifizierung ist eine gemeinsame Maßnahme zwischen AMS und Kunden, wobei jede Seite eigene Workflows abschließen muss.

Sobald ein Kunde als „IMS-Organisation“ existiert und AMS die Bereitstellung des Kunden für IMS abgeschlossen hat, lautet die Zusammenfassung der erforderlichen Konfigurationsschritte wie folgt:

![image2018-9-23_23-33-25](assets/image2018-9-23_23-33-25.png)

1. Der festgelegte Systemadmin erhält eine Einladung zur Anmeldung bei der [!DNL Admin Console]
1. Die Systemadministrator beansprucht die Domain, um die Eigentümerschaft der Domain zu bestätigen (in diesem Beispiel acme.com).
1. Der Systemadministrator richtet Benutzerverzeichnisse ein.
1. Der Systemadmin konfiguriert den Identitätsanbieter (IDP) in der [!DNL Admin Console], um SSO einzurichten.
1. Die bzw. der AEM-Admin verwaltet die lokalen Gruppen, Berechtigungen und Zugriffsrechte wie gewohnt. Siehe „Benutzer- und Gruppensynchronisierung“.

>[!NOTE]
>
>Weitere Informationen zu den Grundlagen zur Identitätsverwaltung von Adobe, einschließlich der IDP-Konfiguration, finden Sie [auf dieser Seite](https://helpx.adobe.com/de/enterprise/using/set-up-identity.html).
>
>Weitere Informationen zur Verwaltung für Unternehmen und zur [!DNL Admin Console] finden Sie im Artikel [auf dieser Seite](https://helpx.adobe.com/de/enterprise/managing/user-guide.html).

### Onboarding von Benutzerinnen und Benutzern in der [!DNL Admin Console] {#onboarding-users-to-the-admin-console}

Je nach der Größe des Kunden und den bevorzugten Einstellungen gibt es drei Möglichkeiten, Benutzerinnen und Benutzer hinzuzufügen:

1. Manuelles Erstellen von Benutzenden und Gruppen in der [!DNL Admin Console]
1. Hochladen einer CSV-Datei mit Benutzern
1. Synchronisieren Sie Benutzer und Gruppen im Active Directory des Unternehmens des Kunden.

#### Manuelles Hinzufügen über die [!DNL Admin Console]-Benutzeroberfläche {#manual-addition-through-admin-console-ui}

Benutzerinnen und Benutzer sowie Gruppen können manuell in der [!DNL Admin Console]-Benutzeroberfläche erstellt werden. Diese Methode kann verwendet werden, wenn nicht viele Benutzer zu verwalten sind. Beispielsweise eine Anzahl von weniger als 50 AEM Benutzern.

Benutzer können auch manuell erstellt werden, wenn der Kunde diese Methode bereits zur Verwaltung anderer Adobe-Produkte wie Analytics-, Target- oder Creative Cloud-Anwendungen verwendet.

![image2018-9-23_20-39-9](assets/image2018-9-23_20-39-9.png)

#### Datei-Upload über die [!DNL Admin Console]-Benutzeroberfläche {#file-upload-in-the-admin-console-ui}

Zur einfachen Handhabung der Benutzererstellung können Sie eine CSV-Datei hochladen, um eine große Anzahl von Benutzenden hinzuzufügen:

![image2018-9-23_18-59-57](assets/image2018-9-23_18-59-57.png)

#### Tool zur Benutzersynchronisierung {#user-sync-tool}

Mit dem Tool zur Benutzersynchronisierung (kurz UST) können Unternehmenskunden Adobe-Benutzer erstellen oder verwalten, die Active Directory oder andere getestete OpenLDAP-Verzeichnisdienste verwenden. Die Zielbenutzer sind IT Identity-Administratoren (Enterprise Directory- und Systemadministratoren), die das Tool installieren und konfigurieren können. Das Open-Source-Tool ist anpassbar, sodass Kunden es an ihre jeweiligen Anforderungen anpassen können.

Wenn die Benutzersynchronisierung ausgeführt wird, ruft sie eine Liste von Benutzern aus dem Active Directory des Unternehmens (oder aus einer anderen kompatiblen Datenquelle) ab und vergleicht sie mit der Liste der Benutzer innerhalb der [!DNL Admin Console]. Anschließend wird die Adobe aufgerufen [!DNL User Management] -API, damit die [!DNL Admin Console] mit dem Verzeichnis des Unternehmens synchronisiert wird. Der Änderungsfluss ist nur unidirektional. Eventuelle Änderungen in der [!DNL Admin Console] werden nicht an das Verzeichnis gesendet.

Das Tool ermöglicht es dem Systemadministrator, Benutzergruppen im Kundenverzeichnis mit der Produktkonfiguration und den Benutzergruppen im [!DNL Admin Console], ermöglicht die neue UST-Version auch die dynamische Erstellung von Benutzergruppen im [!DNL Admin Console].

Um die Benutzersynchronisierung einzurichten, muss die Organisation Anmeldeinformationen erstellen. Die Schritte hierfür sind dieselben wie bei der [[!DNL User Management] -API](https://www.adobe.io/apis/cloudplatform/usermanagement/docs/setup.html).

![image2018-9-23_13-36-56](assets/image2018-9-23_13-36-56.png)

Die Benutzersynchronisierung steht über das Adobe Github-Repository an diesem Speicherort zur Verfügung:

[https://github.com/adobe-apiplatform/user-sync.py/releases/latest](https://github.com/adobe-apiplatform/user-sync.py/releases/latest)

Hinweis: Eine Pre-Release-Version 2.4RC1 mit Unterstützung für dynamische Gruppenerstellung steht hier zur Verfügung: [https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1](https://github.com/adobe-apiplatform/user-sync.py/releases/tag/v2.4rc1)

Die wichtigsten Funktionen dieser Version sind die Möglichkeit, neue LDAP-Gruppen für die Benutzermitgliedschaft in der [!DNL Admin Console] dynamisch zuzuordnen und dynamische Benutzergruppen zu erstellen.

Weitere Informationen zu den neuen Gruppenfunktionen finden Sie hier:

[https://adobe-apiplatform.github.io/user-sync.py/en/user-manual/advanced_configuration.html#additional-group-options](https://adobe-apiplatform.github.io/user-sync.py/en/user-manual/advanced_configuration.html#additional-group-options)

>[!NOTE]
>
>Weitere Informationen zum User Sync Tool finden Sie auf der [Dokumentationsseite](https://adobe-apiplatform.github.io/user-sync.py/en/).
>
>
>Das User Sync Tool muss mit dem [hier](https://adobe-apiplatform.github.io/umapi-documentation/en/UM_Authentication.html) beschriebenen Verfahren als Adobe I/O-Client-UMAPI registriert werden.
>
>Die Dokumentation zur Adobe I/O-Konsole finden Sie [hier](https://developer.adobe.com/developer-console/docs/guides/).
>
>
>Die [!DNL User Management]-API, die vom User Sync Tool verwendet wird, wird [hier erläutert](https://adobe-apiplatform.github.io/umapi-documentation/en/).

>[!NOTE]
>
>Die AEM IMS-Konfiguration wird vom Adobe Managed Services-Team vorgenommen. Der Kundenadministrator kann sie jedoch gemäß seinen Anforderungen ändern (z. B. automatische Gruppenmitgliedschaft oder Gruppenzuordnung). Der IMS-Client wird auch von Ihrem Managed Services-Team registriert.

## Verwendung {#how-to-use}

### Verwalten von Produkten und Benutzerzugriff in der [!DNL Admin Console] {#managing-products-and-user-access-in-admin-console}

Wenn sich Produktadmins der Kundschaft bei der [!DNL Admin Console] anmelden, sehen sie, wie unten gezeigt, mehrere Instanzen des AEM Managed Services-Produktkontexts:

![screen_shot_2018-09-17at105804pm](assets/screen_shot_2018-09-17at105804pm.png)

In diesem Beispiel hat die Organisation *AEM-MS-Onboard* 32 Instanzen mit unterschiedlichen Topologien und Umgebungen wie Staging, Produktion usw.

![screen_shot_2018-09-17at105517pm](assets/screen_shot_2018-09-17at105517pm.png)

Sie können die Instanzdetails überprüfen, um die Instanz zu identifizieren:

![screen_shot_2018-09-17at105601pm](assets/screen_shot_2018-09-17at105601pm.png)

Unter jeder Produktkontextinstanz ist ein zugehöriges Produktprofil vorhanden. Dieses Produktprofil wird für die Zuweisung des Zugriffs an Benutzer verwendet.

![image2018-9-18_7-48-50](assets/image2018-9-18_7-48-50.png)

Alle Benutzer, die unter diesem Produktprofil hinzugefügt werden, können sich wie im folgenden Beispiel bei dieser Instanz anmelden:

![screen_shot_2018-09-17at105623pm](assets/screen_shot_2018-09-17at105623pm.png)

### Anmeldung bei AEM {#logging-into-aem}

#### Lokale Administratoranmeldung {#local-admin-login}

AEM können lokale Anmeldungen für Admin-Benutzer weiterhin unterstützen, da der Anmeldebildschirm eine Option zur lokalen Anmeldung bietet:

![screen_shot_2018-09-18at121056am](assets/screen_shot_2018-09-18at121056am.png)

#### IMS-basierte Anmeldung {#ims-based-login}

Für andere Benutzende kann die IMS-basierte Anmeldung verwendet werden, sobald IMS für die Instanz konfiguriert wurde. Der Benutzer klickt zunächst auf die **Mit Adobe anmelden** wie unten gezeigt:

![image2018-9-18_0-10-32](assets/image2018-9-18_0-10-32.png)

Anschließend werden sie zum IMS-Anmeldebildschirm weitergeleitet und geben ihre Anmeldeinformationen ein:

![screen_shot_2018-09-17at115629pm](assets/screen_shot_2018-09-17at115629pm.png)

Wenn während der Ersteinrichtung der [!DNL Admin Console] Federated IDP konfiguriert wurde, werden Benutzerinnen und Benutzer zur einmaligen Anmeldung zum Kunden-IDP weitergeleitet.

Im folgenden Beispiel ist Okta der IDP:

![screen_shot_2018-09-17at115734pm](assets/screen_shot_2018-09-17at115734pm.png)

Sobald die Authentifizierung abgeschlossen ist, wird die Benutzerin bzw. der Benutzer zurück zu AEM weitergeleitet und angemeldet:

![screen_shot_2018-09-18at120124am](assets/screen_shot_2018-09-18at120124am.png)

### Migrieren vorhandener Benutzer {#migrating-existing-users}

Für bestehende AEM-Instanzen, die eine andere Authentifizierungsmethode verwenden und jetzt auf IMS migriert werden, muss ein Migrationsschritt durchgeführt werden.

Vorhandene Benutzerinnen und Benutzer im AEM-Repository (lokal über LDAP oder SAML hinzugefügt) können mit dem User Migration Utility migriert werden, damit sie auf IMS als IDP verweisen.

Dieses Dienstprogramm wird von Ihrem AMS-Team im Rahmen der IMS-Bereitstellung ausgeführt.

### Verwalten von Berechtigungen und ACLs in AEM {#managing-permissions-and-acls-in-aem}

Zugriffssteuerung und Zugriffsberechtigungen werden weiterhin in AEM verwaltet. Dies kann mithilfe separater Benutzergruppen aus IMS erreicht werden (z. B. AEM-GRP-008 im Beispiel unten), sowie durch lokale Gruppen, in denen die Berechtigungen und Zugriffsrechte definiert sind. Die von IMS synchronisierten Benutzergruppen können lokalen Gruppen zugewiesen werden und die Berechtigungen erben.

Im Beispiel unten werden der lokalen Gruppe *Dam_Users* synchronisierte Gruppen hinzugefügt.

Hier wurde ein Benutzer in der [!DNL Admin Console] auch einigen Gruppen zugewiesen. (Bitte beachten Sie, dass Benutzerinnen und Benutzer sowie Gruppen mit dem User Sync Tool aus LDAP synchronisiert oder lokal erstellt werden können. Weitere Informationen hierzu finden Sie unter **Onboarding von Benutzerinnen und Benutzern zur[!DNL Admin Console]** weiter oben).

>[!NOTE]
>
>Benutzergruppen werden nur synchronisiert, wenn sich Benutzerinnen und Benutzer bei der Instanz anmelden.

![screen_shot_2018-09-17at94207pm](assets/screen_shot_2018-09-17at94207pm.png)

Die Benutzerin bzw. der Benutzer ist Teil der folgenden Gruppen in IMS:

![screen_shot_2018-09-17at94237pm](assets/screen_shot_2018-09-17at94237pm.png)

Wenn sich die Benutzerin bzw. der Benutzer anmeldet, werden die Gruppenmitgliedschaften wie unten dargestellt synchronisiert:

![screen_shot_2018-09-17at94033pm](assets/screen_shot_2018-09-17at94033pm.png)

In AEM können die aus IMS synchronisierten Benutzergruppen vorhandenen lokalen Gruppen (z. B. DAM-Benutzern) als Mitglieder hinzugefügt werden.

![screen_shot_2018-09-17at95804pm](assets/screen_shot_2018-09-17at95804pm.png)

Wie unten gezeigt, die Gruppe *AEM-GRP_008* erbt die Berechtigungen und Berechtigungen von DAM-Benutzern. Dies ist eine effektive Möglichkeit zur Verwaltung von Berechtigungen für synchronisierte Gruppen und wird häufig auch bei LDAP-basierten Authentifizierungsmethoden verwendet.

![screen_shot_2018-09-17at110505pm](assets/screen_shot_2018-09-17at110505pm.png)
