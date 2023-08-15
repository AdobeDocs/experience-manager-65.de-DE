---
title: User Management
seo-title: User Management
description: Mit User Management können Sie die einmalige Anmeldung zwischen AEM Formularmodulen und Netegrity SiteMinder-geschützten Anwendungen mithilfe von SAML aktivieren. Dieses Dokument enthält weitere Informationen zur Benutzerverwaltung.
seo-description: User Management lets you enable SSO between AEM forms modules and Netegrity SiteMinder-protected applications by using SAML. This document provides more information about User Management.
uuid: f0c8331a-d995-483d-97b7-259df53b1a1a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 10e6177a-8228-4515-aba9-bbe59bede449
exl-id: 1da1f6de-ac0d-4e0d-b8bb-956420e42699
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 29%

---

# Benutzerverwaltung {#user-management}

Mit User Management können Sie mithilfe von SAML (Security Assertion Markup Language) die einmalige Anmeldung (SSO) zwischen AEM Formularmodulen und von Netegrity SiteMinder geschützten Anwendungen aktivieren. Wenn die einmalige Anmeldung implementiert ist, sind die Anmeldeseiten für AEM Formulare nicht erforderlich und werden nicht angezeigt, wenn der Benutzer bereits über das Unternehmensportal authentifiziert wurde.

Informationen zur Verbesserung der Leistung bei der Datenbank- und Ordnersynchronisierung für DB2 finden Sie unter [IBM DB2-Datenbank: Ausführen von Befehlen für die regelmäßige Wartung](/help/forms/using/admin-help/ibm-db2-database-running-commands.md#ibm-db2-database-running-commands-for-regular-maintenance).

## Konfigurieren von User Management für einen SSL-aktivierten LDAP-Server {#configuring-user-management-for-an-ssl-enabled-ldap-server}

Wenn Sie über einen SSL-aktivierten LDAP-Server verfügen, konfigurieren Sie User Management für die Verwendung mit diesem Server. (Siehe [User Management für einen SSL-aktivierten LDAP-Server konfigurieren](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server).

## Festlegen von Benutzerberechtigungen für die Verwendung mit Document Security {#setting-user-privileges-for-use-with-document-security}

Erstellen Sie einen Administrator-Benutzer mit den entsprechenden Berechtigungen zum Erstellen von Benutzern und Gruppen. Wenn Ihre AEM Forms-Umgebung Document Security enthält, gewähren Sie die Berechtigung zum Verwalten eingeladener und lokaler Benutzer einem Benutzer, der für diese Benutzer Administrator ist. Weisen Sie außerdem die Benutzerrolle &quot;Administration Console&quot;zu, damit der Benutzer Zugriff auf Administration Console erhält. (Siehe [Rollen erstellen und konfigurieren](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).

Um bei Suchen anhand von Benutzerrichtlinien Benutzer und Gruppen in ausgewählten Domains anzuzeigen, muss ein Superadministrator oder Richtliniensatzadministrator (in User Management erstellte) Domains auswählen und der für jeden Richtliniensatz erstellten Liste der sichtbaren Benutzer und Gruppen hinzufügen.

Diese Liste wird dem Richtliniensatzkoordinator angezeigt und dient zum Einschränken der Domains, die der Endbenutzer beim Auswählen von Benutzern oder Gruppen durchsuchen kann, die Richtlinien hinzugefügt werden sollen. Wenn diese Aufgabe nicht ausgeführt wird, findet der Richtliniensatzkoordinator keine Benutzer oder Gruppen, die der Richtlinie hinzugefügt werden sollen. Für jeden Richtliniensatz kann es mehr als einen Richtliniensatzkoordinator geben.

>[!NOTE]
>
>Das Erstellen von Domains muss vor dem Erstellen von Richtlinien erfolgen.

### Sichtbare Benutzer und Gruppen festlegen {#set-visible-users-and-groups}

Richten Sie nach der Installation und Konfiguration der AEM Forms-Umgebung mit Document Security alle gewünschten Domains in User Management ein.

1. Klicken Sie in Administration Console auf &quot;Dienste&quot;> &quot;Document Security&quot;> &quot;Richtlinien&quot;und dann auf die Registerkarte &quot;Richtliniensätze&quot;.
1. Wählen Sie den globalen Richtliniensatz aus und klicken Sie dann auf die Registerkarte &quot;Sichtbare Benutzer und Gruppen&quot;.
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.
1. Navigieren Sie zu Dienste > Document Security > Konfiguration > Meine Richtlinien und klicken Sie auf die Registerkarte Sichtbare Benutzer und Gruppen .
1. Klicken Sie auf „Domain(s) hinzufügen“ und fügen Sie den Anforderungen entsprechend vorhandene Domains hinzu.

## Einschränkungen für Administratoren {#administrator-user-restrictions}

Benutzer mit bestimmten Arten von Administratorberechtigungen können aus Sicherheitsgründen nicht auf die Workspace-Webseiten für Endbenutzer zugreifen. Da diese Webseiten außerhalb einer Firewall vorhanden sein können, kann das Zulassen von Aufgaben auf Administratorebene ein Sicherheitsrisiko darstellen. Nur Benutzer mit den Berechtigungen Workspace Administrator oder Workspace User können auf die Webseiten für Endbenutzer zugreifen.

>[!NOTE]
>
>Der Flex-Workspace wird für die AEM Forms-Version nicht mehr unterstützt.
