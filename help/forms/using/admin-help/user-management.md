---
title: Benutzerverwaltung
seo-title: Benutzerverwaltung
description: Mit User Management können Sie für AEM Forms-Module und Anwendungen, die durch Netegrity SiteMinder geschützt sind, mithilfe von SAML die einmalige Anmeldung (SSO) aktivieren. In diesem Dokument finden Sie weitere Informationen über User Management.
seo-description: Mit User Management können Sie für AEM Forms-Module und Anwendungen, die durch Netegrity SiteMinder geschützt sind, mithilfe von SAML die einmalige Anmeldung (SSO) aktivieren. In diesem Dokument finden Sie weitere Informationen über User Management.
uuid: f0c8331a-d995-483d-97b7-259df53b1a1a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 10e6177a-8228-4515-aba9-bbe59bede449
exl-id: 1da1f6de-ac0d-4e0d-b8bb-956420e42699
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 100%

---

# Benutzerverwaltung {#user-management}

Mit User Management können Sie für AEM Forms-Module und Anwendungen, die durch Netegrity SiteMinder geschützt sind, mithilfe von SAML (Security Assertion Markup Language) die einmalige Anmeldung (Single Sign-On, SSO) aktivieren. Wenn die einmalige Anmeldung implementiert ist, sind die AEM Forms-Anmeldeseiten nicht erforderlich und werden nicht angezeigt, wenn der Benutzer bereits durch das Firmenportal authentifiziert wurde.

Weitere Informationen zum Verbessern der Leistung bei der Datenbank- und Ordnersynchronisierung für DB2 finden Sie unter [IBM DB2-Datenbank: Ausführen von Befehlen zur regelmäßigen Wartung](/help/forms/using/admin-help/ibm-db2-database-running-commands.md#ibm-db2-database-running-commands-for-regular-maintenance).

## Konfigurieren von User Management für einen SSL-aktivierten LDAP-Server {#configuring-user-management-for-an-ssl-enabled-ldap-server}

Wenn Sie einen SSL-aktivierten LDAP-Server verwenden, konfigurieren Sie User Management für die Zusammenarbeit mit dem Server. (Siehe [User Management für einen SSL-aktivierten LDAP-Server konfigurieren](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)

## Zugriffsrechte für die Verwendung mit Document Security festlegen  {#setting-user-privileges-for-use-with-document-security}

Erstellen Sie einen administrativen Benutzer, der über die benötigten Berechtigungen zum Erstellen von Benutzern und Gruppen verfügt. Wenn Ihre AEM Forms-Umgebung Document Security enthält, gewähren Sie die Berechtigung zum Verwalten von eingeladenen und lokalen Benutzern einem Benutzer, der der Administrator für diese Benutzer ist. Weisen Sie außerdem die Administration Console-Benutzerrolle zu, um dem Benutzer Zugriff auf Administration Console zu ermöglichen. (Siehe [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)

Um bei Suchen anhand von Benutzerrichtlinien Benutzer und Gruppen in ausgewählten Domänen anzuzeigen, muss ein Superadministrator oder Richtliniensatzadministrator (in User Management erstellte) Domänen auswählen und der für jeden Richtliniensatz erstellten Liste der sichtbaren Benutzer und Gruppen hinzufügen.

Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Einschränken der Domänen, die der Endbenutzer beim Auswählen von Benutzern oder Gruppen durchsuchen kann, die Richtlinien hinzugefügt werden sollen. Wird dieser Schritt nicht durchgeführt, kann der Richtliniensatzkoordinator keine der Richtlinie hinzuzufügenden Benutzer oder Gruppen finden. Es kann mehrere Richtliniensatzkoordinatoren für einen Richtliniensatz geben.

>[!NOTE]
>
>Das Erstellen von Domänen muss vor dem Erstellen von Richtlinien erfolgen.

### Sichtbare Benutzer und Gruppen festlegen  {#set-visible-users-and-groups}

Richten Sie nach der Installation und Konfiguration der AEM Forms-Umgebung mit Document Security alle gewünschten Domänen in User Management ein.

1. Klicken Sie in Administration Console auf „Dienste“ > „Document Security“, und klicken Sie dann auf die Registerkarte „Richtliniensätze“.
1. Wählen Sie den globalen Richtliniensatz aus und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domäne(n) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domänen hinzu.
1. Wechseln Sie zu „Dienste“ > „Document Security“ > „Meine Richtlinien“ und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domäne(n) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domänen hinzu.

## Für den administrativen Benutzer geltende Einschränkungen  {#administrator-user-restrictions}

Benutzer mit bestimmten Arten von Administratorberechtigungen dürfen aus Sicherheitsgründen nicht auf Workspace-Webseiten für Endbenutzer zugreifen. Da sich diese Webseiten außerhalb einer Firewall befinden können, ist das Zulassen von Aufgaben auf Administratorebene möglicherweise ein Sicherheitsrisiko. Nur Benutzer mit Administrator- oder Workspace User-Berechtigungen dürfen auf die Workspace-Webseiten für Endbenutzer zugreifen.

>[!NOTE]
>
>Der Flex-Workspace für die AEM Forms-Version wird nicht mehr unterstützt.
