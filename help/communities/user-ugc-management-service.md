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
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '617'
ht-degree: 30%

---


# Verwaltungsdienst für Benutzer und benutzergenerierte Inhalte in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>GDPR wird als Beispiel in den folgenden Abschnitten verwendet, aber die betreffenden Details gelten für alle Datenschutz- und Datenschutzbestimmungen. wie GDPR, CCPA usw.

AEM Communities stellt bereits verfügbare APIs zur Verwaltung von Profilen und Massenverwaltung benutzergenerierter Inhalte (UGC) bereit. Nach der Aktivierung ermöglicht der Dienst **UserUgcManagement** den privilegierten Benutzern (Community-Administratoren und -Moderatoren), Benutzerkonten zu deaktivieren und benutzerspezifische Profil für Massenlöschen oder Massenexport-UGC für bestimmte Benutzer zu verwenden. Diese APIs ermöglichen es den für die Verarbeitung und Verarbeitung von Kundendaten Verantwortlichen und Verarbeitern auch, die allgemeinen Datenschutzbestimmungen der Europäischen Vereinigung (GDPR) und andere vom GDPR inspirierte Datenschutzauflagen einzuhalten.

Weitere Informationen finden Sie auf der [DSGVO-Seite im Datenschutzzentrum von Adobe](https://www.adobe.com/de/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Wenn Sie die Site [Adobe Analytics in AEM Communities](/help/communities/analytics.md) konfiguriert haben, werden die erfassten Benutzerdaten an den Adobe Analytics-Server gesendet. Adobe Analytics stellt APIs bereit, mit denen Sie auf Benutzerdaten zugreifen, sie exportieren und löschen und GDPR einhalten können. Weitere Informationen finden Sie unter [Anforderungen senden und Löschen](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Damit diese APIs verwendet werden können, müssen Sie den Endpunkt `/services/social/ugcmanagement` aktivieren, indem Sie den UserUgcManagement-Dienst aktivieren. Um diesen Dienst zu aktivieren, installieren Sie das [Beispiel-Servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet), das unter [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) verfügbar ist. Dann drücken Sie den Endpunkt auf der Veröffentlichungsinstanz Ihrer Communities-Site mit den entsprechenden Parametern mithilfe einer HTTP-Anforderung, ähnlich wie:

`https://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation=<getUgc>`. Alternativ dazu können Sie auch eine grafische Benutzeroberfläche erstellen, über die Sie dann die im System vorhandenen Benutzerprofile und benutzergenerierten Inhalte verwalten können.

Mit diesen APIs können die folgenden Funktionen ausgeführt werden:

## Benutzergenerierte Inhalte abrufen {#retrieve-the-ugc-of-a-user}

**getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)** unterstützt den Export des gesamten UGC eines Benutzers aus dem System.

* **Benutzer**: Autorisierbare ID eines Benutzers.
* **outputStream**: Das Ergebnis wird als Ausgabestream zurückgegeben. Hierbei handelt es sich um eine ZIP-Datei mit dem vom Benutzer generierten Inhalt (als JSON-Datei) und Anlagen (einschließlich der vom Benutzer hochgeladenen Bilder oder Videos).

Beispiel: Um die Inhalte zu exportieren, die ein Benutzer mit dem Namen „Weston McCall“ generiert hat und der für die Anmeldung bei der Communities-Site über die ID „weston.mccall@dodgit.com“ autorisiert wird, können Sie eine HTTP-GET-Anfrage senden. Diese kann in etwa wie folgt aussehen:

`https://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## Benutzergenerierte Inhalte löschen {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** hilft beim Löschen des gesamten UGC für einen Benutzer aus dem System.

* **Benutzer**: Autorisierbare ID des Benutzers.

Um beispielsweise die UGC eines Benutzers mit autorisierbarer ID weston.mccall@dodgit.com über eine HTTP-POST-Anforderung zu löschen, verwenden Sie die folgenden Parameter:

* ist der Benutzer = `weston.mccall@dodgit.com`
* Vorgang = `deleteUgc`

### UGC aus Adobe Analytics löschen {#delete-ugc-from-adobe-analytics}

Um Benutzerdaten aus dem Adobe Analytics zu löschen, befolgen Sie den [GDPR Analytics-Arbeitsablauf](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html); da die API keine Benutzerdaten aus Adobe Analytics löscht.

Für Adobe Analytics-Variablenzuordnungen, die von AEM Communities verwendet werden, siehe folgende Abbildung:

![Variablenzuordnung AEM Communities für Adobe Analytics](assets/analytics-communities-mapping.png)

## Benutzerkonto deaktivieren {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** hilft beim Deaktivieren eines Benutzerkontos.

* **Benutzer**: Autorisierbare ID des Benutzers.

>[!NOTE]
>
>Durch das Deaktivieren eines Benutzers wird der gesamte von diesem generierte Inhalt gelöscht, der auf dem Server vorhanden ist.

Um beispielsweise das Profil eines Benutzers mit der autorisierten ID `weston.mccall@dodgit.com` über eine HTTP-POST-Anforderung zu löschen, verwenden Sie die folgenden Parameter:

* ist der Benutzer = `weston.mccall@dodgit.com`
* Vorgang = `deleteUser`

>[!NOTE]
>
>Mit der API „deleteUserAccount()“ werden im System nur die benutzergenerierten Inhalte gelöscht, das diesen zugehörige Benutzerprofil wird damit lediglich deaktiviert. Um ein Profil zu löschen, navigieren Sie jedoch zu **CRXDE Lite**: [https://&lt;server>/crx/de](https://localhost:4502/crx/de), suchen Sie den Benutzerknoten und löschen Sie ihn.
