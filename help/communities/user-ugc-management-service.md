---
title: Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities
seo-title: Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities
description: Verwenden Sie APIs zur Massenlöschung und zum Massenexport von benutzergenerierten Inhalten sowie zum Deaktivieren von Benutzerkonten.
seo-description: Verwenden Sie APIs zur Massenlöschung und zum Massenexport von benutzergenerierten Inhalten sowie zum Deaktivieren von Benutzerkonten.
uuid: 91180659-617d-4f6c-9a07-e680770d0d8f
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
discoiquuid: d305821d-1371-4e4a-8b28-8eee8fafa43b
docset: aem65
translation-type: tm+mt
source-git-commit: 85a3dac5db940b81da9e74902a6aa475ec8f1780

---


# Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities{#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>GDPR wird als Beispiel in den folgenden Abschnitten verwendet, aber die betreffenden Details gelten für alle Datenschutz- und Datenschutzbestimmungen. wie GDPR, CCPA usw.

AEM Communities stellt standardmäßig APIs zum Verwalten von Benutzerprofilen und zum Massenmanagement von benutzergenerierten Inhalten (UGC) bereit. Once enabled, the **UserUgcManagement** service allows the privileged users (community administrators and moderators) to disable user profiles, and bulk delete or bulk export UGC for specific users. Diese APIs ermöglichen es auch für die Verarbeitung von Kundendaten zuständigen Verantwortlichen und Verarbeitern, die allgemeinen Datenschutzbestimmungen der Europäischen Union (GDPR) und andere vom GDPR inspirierte Datenschutzauflagen einzuhalten.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Datenschutzzentrum von Adobe](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Wenn Sie [Adobe Analytics auf der AEM Communities](/help/communities/analytics.md) -Site konfiguriert haben, werden die erfassten Benutzerdaten an den Adobe Analytics-Server gesendet. Adobe Analytics bietet APIs, mit denen Sie auf Benutzerdaten zugreifen, sie exportieren und löschen und GDPR einhalten können. Weitere Informationen finden Sie unter Zugriff [senden und Anforderungen](https://marketing.adobe.com/resources/help/en_US/analytics/gdpr/gdpr_submit_access_delete.html)löschen.

To put these APIs to use, you need to enable the **/services/social/ugcmanagement** endpoint by activating the UserUgcManagement service. To activate this service, install the [sample servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet) available on [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet). Anschließend rufen Sie den Endpunkt auf der Veröffentlichungsinstanz Ihrer Communities-Site anhand einer HTTP-Anfrage mit den entsprechenden Parametern auf. Diese kann in etwa wie folgt aussehen:

**https://localhost:port/services/social/ugcmanagement?user=&lt;authorized_ID>&amp;operation=&lt;getUgc>**. Alternativ dazu können Sie auch eine grafische Benutzeroberfläche erstellen, über die Sie dann die im System vorhandenen Benutzerprofile und benutzergenerierten Inhalte verwalten können.

Mit diesen APIs können die folgenden Funktionen ausgeführt werden:

## Benutzergenerierte Inhalte abrufen {#retrieve-the-ugc-of-a-user}

**getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream) **unterstützt den Export aller UGC eines Benutzers aus dem System.

* **Benutzer**: autorisierbare ID eines Benutzers.
* **outputStream**: Das Ergebnis wird als Ausgabestream in einer ZIP-Datei ausgegeben, die die benutzergenierten Inhalte (als JSON-Datei) sowie Anhänge (vom Benutzer hochgeladene Bilder oder Videos) enthält.

Beispiel: Um die Inhalte zu exportieren, die ein Benutzer mit dem Namen „Weston McCall“ generiert hat und der für die Anmeldung bei der Communities-Site über die ID „weston.mccall@dodgit.com“ autorisiert wird, können Sie eine HTTP-GET-Anfrage senden. Diese kann in etwa wie folgt aussehen:

`https://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Benutzergenerierte Inhalte löschen {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user) **hilft, alle UGC für einen Benutzer aus dem System zu löschen.

* **user**: Die zur Autorisierung eines Benutzers verwendete ID.

Um beispielsweise die UGC eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anforderung zu löschen, verwenden Sie die folgenden Parameter:

* user= weston.mccall@dodgit.com
* operation= deleteUgc

### UGC aus Adobe Analytics löschen {#delete-ugc-from-adobe-analytics}

Um Benutzerdaten aus Adobe Analytics zu löschen, befolgen Sie den Arbeitsablauf für [GDPR-Analysen](https://marketing.adobe.com/resources/help/en_US/analytics/gdpr/an_gdpr_workflow.html). da die API keine Benutzerdaten aus Adobe Analytics löscht.

Für die von AEM Communities verwendeten Adobe Analytics-Variablenzuordnungen siehe folgende Abbildung:

![Variablenzuordnung für AEM Communities für Adobe Analytics](assets/analytics-communities-mapping.png)

## Benutzerkonto deaktivieren {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user) **hilft beim Deaktivieren eines Benutzerkontos.

* **user**: Die zur Autorisierung eines Benutzers verwendete ID.

>[!NOTE]
>
>Durch das Deaktivieren eines Benutzers wird der gesamte von diesem generierte Inhalt gelöscht, der auf dem Server vorhanden ist.

Um beispielsweise das Profil eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anforderung zu löschen, verwenden Sie die folgenden Parameter:

* user= weston.mccall@dodgit.com
* operation= deleteUser

>[!NOTE]
>
>Mit der API „deleteUserAccount()“ werden im System nur die benutzergenerierten Inhalte gelöscht, das diesen zugehörige Benutzerprofil wird damit lediglich deaktiviert. However, to delete a user profile from the system, navigate to **CRXDE Lite**: [https://&lt;server>/crx/de](https://localhost:4502/crx/de), locate the user node and delete it.

