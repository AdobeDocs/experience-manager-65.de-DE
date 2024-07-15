---
title: User- und UGC-Verwaltungsdienst in AEM Communities
description: Verwenden Sie APIs, um benutzergenerierte Inhalte stapelweise zu löschen und zu exportieren und das Benutzerkonto zu deaktivieren.
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
docset: aem65
role: Admin
exl-id: 526ef0fa-3f20-4de4-8bc5-f435c60df0d0
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 8%

---

# User- und UGC-Verwaltungsdienst in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>Die DSGVO wird in den folgenden Abschnitten als Beispiel benutzt, aber die genannten Details lassen sich auf alle Regulierungen zum Datenschutz anwenden; zum Beispiel GDPR, CCPA usw.

AEM Communities stellt native APIs zur Verwaltung von Benutzerprofilen und zur Massenverwaltung benutzergenerierter Inhalte bereit. Nach der Aktivierung ermöglicht der Dienst **UserUgcManagement** den berechtigten Benutzern (Community-Administratoren und -Moderatoren), Benutzerprofile zu deaktivieren und benutzergenerierte Inhalte für Massenlöschungen oder Massenexporte für bestimmte Benutzer zu erstellen. Diese APIs ermöglichen es auch den Datenverantwortlichen und Verarbeitern von Kundendaten, die Datenschutz-Grundverordnung (DSGVO) der Europäischen Union und andere DSGVO-inspirierte Datenschutzmandate einzuhalten.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Adobe Privacy Center](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Wenn Sie [Adobe Analytics auf der AEM Communities](/help/communities/analytics.md)-Site konfiguriert haben, werden die erfassten Benutzerdaten an den Adobe Analytics-Server gesendet. Adobe Analytics bietet APIs, mit denen Sie Benutzerdaten aufrufen, exportieren und löschen und die DSGVO einhalten können. Weitere Informationen finden Sie unter [Zugriffs- und Löschanfragen einreichen](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Damit diese APIs verwendet werden können, müssen Sie den `/services/social/ugcmanagement` -Endpunkt aktivieren, indem Sie den UserUgcManagement-Dienst aktivieren. Um diesen Dienst zu aktivieren, installieren Sie das [Beispiel-Servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet), das auf [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) verfügbar ist. Drücken Sie dann den Endpunkt auf der Veröffentlichungsinstanz Ihrer Communities-Site mit entsprechenden Parametern mithilfe einer HTTP-Anfrage, ähnlich wie:

`https://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation=<getUgc>`. Sie können jedoch auch eine Benutzeroberfläche (Benutzeroberfläche) erstellen, um Benutzerprofile und benutzergenerierte Inhalte im System zu verwalten.

Diese APIs ermöglichen die Ausführung der folgenden Funktionen.

## Abrufen der benutzergenerierten Inhalte eines Benutzers {#retrieve-the-ugc-of-a-user}

**getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)** unterstützt den Export aller UGC eines Benutzers aus dem System.

* **user**: Die autorisierbare ID eines Benutzers.
* **outputStream**: Das Ergebnis wird als Ausgabestream zurückgegeben. Hierbei handelt es sich um eine ZIP-Datei mit dem vom Benutzer generierten Inhalt (als JSON-Datei) und Anlagen (darunter vom Benutzer hochgeladene Bilder oder Videos).

Um beispielsweise die benutzergenerierte Inhalte eines Benutzers mit dem Namen Weston McCall zu exportieren, der weston.mccall@dodgit.com als autorisierbare ID verwendet, um sich bei der Communities-Site anzumelden, können Sie eine HTTP-GET-Anfrage ähnlich der folgenden senden:

`https://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Löschen der benutzergenerierten Inhalte eines Benutzers {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** hilft beim Löschen aller UGC für einen Benutzer aus dem System.

* **user**: Die autorisierbare ID des Benutzers.

Um beispielsweise die benutzergenerierte Inhalte eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anfrage zu löschen, verwenden Sie die folgenden Parameter:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUgc`

### UGC aus Adobe Analytics löschen {#delete-ugc-from-adobe-analytics}

Um Benutzerdaten aus der Adobe Analytics zu löschen, folgen Sie dem Workflow [DSGVO-Analyse](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html?lang=de); da die API Benutzerdaten nicht aus Adobe Analytics löscht.

Informationen zu von AEM Communities verwendeten Adobe Analytics-Variablenzuordnungen finden Sie in der folgenden Abbildung:

![AEM Communities-Variablenzuordnung für Adobe Analytics](assets/analytics-communities-mapping.png)

## Ein Benutzerkonto deaktivieren {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** hilft beim Deaktivieren eines Benutzerkontos.

* **user**: Die autorisierbare ID des Benutzers.

>[!NOTE]
>
>Durch Deaktivieren eines Benutzers werden alle vom Benutzer generierten Inhalte gelöscht, die der Benutzer auf dem Server hat.

Um beispielsweise das Benutzerprofil mit der autorisierbaren ID `weston.mccall@dodgit.com` über eine HTTP-POST-Anfrage zu löschen, verwenden Sie die folgenden Parameter:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUser`

>[!NOTE]
>
>Die API deleteUserAccount() deaktiviert nur ein Benutzerprofil im System und entfernt die Benutzerkontensteuerung. Um jedoch ein Benutzerprofil aus dem System zu löschen, navigieren Sie zu &quot;**CRXDE Lite**: [https://&lt;server>/crx/de](https://localhost:4502/crx/de)&quot;, suchen Sie den Benutzerknoten und löschen Sie ihn.
