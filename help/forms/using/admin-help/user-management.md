---
title: User Management
description: Mit der Benutzerverwaltung können Sie für AEM Forms-Module und Anwendungen, die durch Netegrity SiteMinder geschützt sind, mithilfe von SAML die Single Sign-on(SSO)-Funktion aktivieren. Dieses Dokument enthält weitere Informationen zur Benutzerverwaltung.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 1da1f6de-ac0d-4e0d-b8bb-956420e42699
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 100%

---

# Benutzerverwaltung {#user-management}

Mit der Benutzerverwaltung können Sie für AEM Forms-Module und Anwendungen, die durch Netegrity SiteMinder geschützt sind, mithilfe von Security Assertion Markup Language (SAML) die Single Sign-on(SSO)-Funktion aktivieren. Wenn SSO implementiert ist, sind die AEM Forms-Anmeldeseiten nicht erforderlich und werden nicht angezeigt, wenn Benutzende bereits durch das Firmenportal authentifiziert wurden.

Weitere Informationen zum Verbessern der Leistung bei der Datenbank- und Verzeichnissynchronisierung für DB2 finden Sie unter [IBM DB2-Datenbank: Ausführen von Befehlen zur regelmäßigen Wartung](/help/forms/using/admin-help/ibm-db2-database-running-commands.md#ibm-db2-database-running-commands-for-regular-maintenance).

## Konfigurieren der Benutzerverwaltung für einen SSL-aktivierten LDAP-Server {#configuring-user-management-for-an-ssl-enabled-ldap-server}

Wenn Sie einen SSL-aktivierten LDAP-Server verwenden, konfigurieren Sie die Benutzerverwaltung dafür. (Siehe [Konfigurieren der Benutzerverwaltung für einen SSL-aktivierten LDAP-Server](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).)

## Festlegen von Benutzerberechtigungen für die Dokumentsicherheit {#setting-user-privileges-for-use-with-document-security}

Erstellen Sie eine Admin-Benutzerin oder einen Admin-Benutzer, die bzw. der über die entsprechenden Berechtigungen zum Erstellen von Benutzenden und Gruppen verfügt. Wenn Ihre AEM Forms-Umgebung über „Dokumentsicherheit“ verfügt, gewähren Sie die Berechtigung zum Verwalten von eingeladenen und lokalen Benutzenden einer Benutzerin oder einem Benutzer, die bzw. der als Admin für diese Benutzenden fungieren soll. Weisen Sie außerdem die Administration-Console-Benutzerrolle zu, um der Benutzerin oder dem Benutzer Zugriff auf Administration-Console zu ermöglichen. (Siehe [Erstellen und Konfigurieren von Rollen](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)

Um bei Suchen anhand von Benutzerrichtlinien Benutzer und Gruppen in ausgewählten Domains anzuzeigen, muss ein Superadministrator oder Richtliniensatzadministrator (in User Management erstellte) Domains auswählen und der für jeden Richtliniensatz erstellten Liste der sichtbaren Benutzer und Gruppen hinzufügen.

Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Einschränken der Domains, die der Endbenutzer beim Auswählen von Benutzern oder Gruppen durchsuchen kann, die Richtlinien hinzugefügt werden sollen. Wird diese Aufgabe nicht durchgeführt, kann die Richtliniensatzkoordinatorin oder der Richtliniensatzkoordinator keine der Richtlinie hinzuzufügenden Benutzenden oder Gruppen finden. Für jeden Richtliniensatz kann es mehrere Richtliniensatzkoordinierende geben.

>[!NOTE]
>
>Das Erstellen von Domains muss vor dem Erstellen von Richtlinien erfolgen.

### Festlegen von sichtbaren Benutzenden und Gruppen {#set-visible-users-and-groups}

Richten Sie nach der Installation und Konfiguration der AEM Forms-Umgebung mit Document Security alle gewünschten Domains in User Management ein.

1. Klicken Sie in Administration-Console auf „Dienste“ > „Dokumentsicherheit“ > „Richtlinien“ und dann auf die Registerkarte „Richtliniensätze“.
1. Wählen Sie „Globaler Richtliniensatz“ aus und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.
1. Navigieren Sie zu „Dienste“ > „Dokumentsicherheit“ > „Meine Richtlinien“ und klicken Sie auf die Registerkarte „Sichtbare Benutzer und Gruppen“.
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.

## Einschränkungen für Admin-Benutzende {#administrator-user-restrictions}

Benutzende mit bestimmten Arten von Administratorberechtigungen dürfen aus Sicherheitsgründen nicht auf Workspace-Web-Seiten für Endbenutzende zugreifen. Da sich diese Web-Seiten außerhalb einer Firewall befinden können, ist das Zulassen von Aufgaben auf Administratorebene möglicherweise ein Sicherheitsrisiko. Nur Benutzende mit Workspace-Administrator- oder Workspace-Benutzerberechtigungen können auf die Workspace-Web-Seiten für Endbenutzende zugreifen.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.
