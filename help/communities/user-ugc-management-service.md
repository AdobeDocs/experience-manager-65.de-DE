---
title: User- und UGC-Verwaltungsdienst in AEM Communities
seo-title: User and UGC Management Service in AEM Communities
description: Verwenden Sie APIs, um benutzergenerierte Inhalte stapelweise zu löschen und zu exportieren und das Benutzerkonto zu deaktivieren.
seo-description: Use APIs to bulk delete and bulk export user generated content, and disable user account.
uuid: 91180659-617d-4f6c-9a07-e680770d0d8f
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
discoiquuid: d305821d-1371-4e4a-8b28-8eee8fafa43b
docset: aem65
role: Admin
exl-id: 526ef0fa-3f20-4de4-8bc5-f435c60df0d0
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '590'
ht-degree: 5%

---

# User- und UGC-Verwaltungsdienst in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel verwendet, die betroffenen Details gelten jedoch für alle Datenschutz- und Datenschutzbestimmungen wie DSGVO, CCPA usw.

AEM Communities stellt native APIs zur Verwaltung von Benutzerprofilen und zur Massenverwaltung benutzergenerierter Inhalte bereit. Nach der Aktivierung wird die **UserUgcManagement** Der -Dienst ermöglicht es berechtigten Benutzern (Community-Administratoren und -Moderatoren), Benutzerprofile zu deaktivieren und UGC-Dateien für bestimmte Benutzer per Massenlöschung oder Massenexport zu löschen. Diese APIs ermöglichen es auch den Datenverantwortlichen und Verarbeitern von Kundendaten, die Datenschutz-Grundverordnung (DSGVO) der Europäischen Union und andere DSGVO-inspirierte Datenschutzmandate einzuhalten.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Adobe Privacy Center](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Wenn Sie [Adobe Analytics in AEM Communities](/help/communities/analytics.md) Site werden die erfassten Benutzerdaten an den Adobe Analytics-Server gesendet. Adobe Analytics bietet APIs, mit denen Sie Benutzerdaten aufrufen, exportieren und löschen und die DSGVO einhalten können. Weitere Informationen finden Sie unter [Zugriffs- und Löschanfragen einreichen](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Damit diese APIs verwendet werden können, müssen Sie die `/services/social/ugcmanagement` -Endpunkt durch Aktivierung des UserUgcManagement-Dienstes. Um diesen Dienst zu aktivieren, installieren Sie die [Beispiel-Servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) verfügbar unter [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Drücken Sie dann den Endpunkt auf der Veröffentlichungsinstanz Ihrer Communities-Site mit entsprechenden Parametern mithilfe einer HTTP-Anfrage, ähnlich wie:

`https://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation=<getUgc>`. Sie können jedoch auch eine Benutzeroberfläche (Benutzeroberfläche) erstellen, um Benutzerprofile und benutzergenerierte Inhalte im System zu verwalten.

Diese APIs ermöglichen die Ausführung der folgenden Funktionen.

## Abrufen der benutzergenerierten Inhalte eines Benutzers {#retrieve-the-ugc-of-a-user}

**getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)** unterstützt den Export aller benutzergenerierten Inhalte eines Benutzers aus dem System.

* **Benutzer**: Berechenbare ID eines Benutzers.
* **outputStream**: Das Ergebnis wird als Ausgabestream zurückgegeben. Hierbei handelt es sich um eine ZIP-Datei mit dem vom Benutzer generierten Inhalt (als JSON-Datei) und Anlagen (einschließlich Bildern oder Videos, die vom Benutzer hochgeladen wurden).

Um beispielsweise die benutzergenerierte Inhalte eines Benutzers mit dem Namen Weston McCall zu exportieren, der weston.mccall@dodgit.com als autorisierbare ID verwendet, um sich bei der Communities-Site anzumelden, können Sie eine HTTP-GET-Anfrage ähnlich der folgenden senden:

`https://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Löschen der benutzergenerierten Inhalte eines Benutzers {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** hilft, alle benutzergenerierten Inhalte für einen Benutzer aus dem System zu löschen.

* **Benutzer**: Die autorisierbare ID des Benutzers.

Um beispielsweise die benutzergenerierte Inhalte eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anfrage zu löschen, verwenden Sie die folgenden Parameter:

* Benutzer = `weston.mccall@dodgit.com`
* operation = `deleteUgc`

### UGC aus Adobe Analytics löschen {#delete-ugc-from-adobe-analytics}

Gehen Sie wie folgt vor, um Benutzerdaten aus der Adobe Analytics zu löschen [DSGVO-Analyse-Workflow](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html?lang=de); da die API keine Benutzerdaten aus Adobe Analytics löscht.

Informationen zu von AEM Communities verwendeten Adobe Analytics-Variablenzuordnungen finden Sie in der folgenden Abbildung:

![Variablenzuordnung für AEM Communities in Adobe Analytics](assets/analytics-communities-mapping.png)

## Ein Benutzerkonto deaktivieren {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** hilft, ein Benutzerkonto zu deaktivieren.

* **Benutzer**: Die autorisierbare ID des Benutzers.

>[!NOTE]
>
>Durch Deaktivieren eines Benutzers werden alle vom Benutzer generierten Inhalte gelöscht, die der Benutzer auf dem Server hat.

So löschen Sie beispielsweise das Profil eines Benutzers mit autorisierbarer ID `weston.mccall@dodgit.com` Verwenden Sie die folgenden POST über die HTTP-Anforderung:

* Benutzer = `weston.mccall@dodgit.com`
* operation = `deleteUser`

>[!NOTE]
>
>Die API deleteUserAccount() deaktiviert nur ein Benutzerprofil im System und entfernt die Benutzerkontensteuerung. Um jedoch ein Benutzerprofil aus dem System zu löschen, navigieren Sie zu **CRXDE Lite**: [https://&lt;server>/crx/de](https://localhost:4502/crx/de), suchen Sie den Benutzerknoten und löschen Sie ihn.
