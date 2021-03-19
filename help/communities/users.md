---
title: Verwalten von Benutzern und Benutzergruppen
seo-title: Verwalten von Benutzern und Benutzergruppen
description: Benutzer von AEM Communities können sich selbst registrieren und ihre Profil bearbeiten
seo-description: Benutzer von AEM Communities können sich selbst registrieren und ihre Profil bearbeiten
uuid: aeba424e-ea7e-4da5-b94f-ea8af4caa7d2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 774c2553-b629-456b-afa7-5713490f4a0a
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 1%

---


# Verwalten von Benutzern und Benutzergruppen {#managing-users-and-user-groups}

## Überblick {#overview}

In AEM Communities können sich Benutzer in der Umgebung zum Veröffentlichen selbst registrieren und ihre Profil bearbeiten. Mit den entsprechenden Berechtigungen können sie auch:

* Erstellen Sie Untergruppen innerhalb der Community-Site (siehe [Community-Gruppen](creating-groups.md)).

* [Von ](moderation.md) Moderateuser generierte Inhalte (UGC).

* Sei [Aktivierungsressource](resources.md) Kontakte.

* Sie können [privilegiert](#privileged-members-group) sein, um Einträge für Blogs, Kalender, QnA und Foren zu erstellen.

In der Umgebung &quot;Veröffentlichen&quot;registrierte Benutzer werden allgemein als *Community-Mitglieder (Mitglieder)* bezeichnet, um sie von *Benutzern* in der Umgebung &quot;Autor&quot;zu unterscheiden.

Berechtigungen werden gewährt, indem Mitglieder einer der [Mitglieds-(Benutzer-)Gruppen](#publish-group-roles) zugewiesen werden, die dynamisch erstellt wird, wenn die Community-Site [erstellt](sites-console.md) oder [modifiziert](sites-console.md#modifying-site-properties) aus der Autorenversion Umgebung ist. Bei der Arbeit mit der Autorenfunktion sind die Mitglieder über den [Tunneldienst](#tunnel-service) in der Veröffentlichungs-Umgebung sichtbar.

Standardmäßig sollten in der Umgebung &quot;Veröffentlichen&quot;erstellte Mitglieder und Mitgliedsgruppen nicht in der Umgebung &quot;Autor&quot;angezeigt werden. Benutzer und Benutzergruppen, die in der Autor-Umgebung erstellt wurden, sollen in ähnlicher Weise in der Autorendatei verbleiben.

Wenn Benutzer, die Autor und Mitglieder im Veröffentlichungsmodus sind, aus derselben Liste von Benutzern stammen, z. B. aus demselben LDAP-Ordner, werden sie nicht als derselbe Benutzer mit denselben Berechtigungen und derselben Gruppenmitgliedschaft in der Autor- und Veröffentlichungs-Umgebung betrachtet. Die Rolle(en) der Mitglieder und Benutzer muss (müssen) bei der Veröffentlichung und gegebenenfalls beim Autor gesondert festgelegt werden.

Bei einer [Veröffentlichungsfarm](topologies.md) müssen die Registrierungen und Änderungen, die an einer Veröffentlichungsinstanz vorgenommen wurden, mit anderen Veröffentlichungsinstanzen synchronisiert werden, damit sie Zugriff auf dieselben Benutzerdaten haben. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md), in dem ein Abschnitt beschrieben wird, in dem [Was passiert, wenn...](sync.md#what-happens-when).

### Anteilslimits {#contribution-limits}

Zum Schutz vor Spam ist es möglich, die Häufigkeit der Veröffentlichung von Inhalten durch die Mitglieder zu begrenzen. Darüber hinaus ist es möglich, die Beiträge der neu eingetragenen Mitglieder automatisch zu begrenzen.

Weitere Informationen finden Sie unter [Mitgliederbeitragsbeschränkungen](limits.md).

### Dynamisch erstellte Benutzergruppen {#dynamically-created-user-groups}

Wenn eine neue Community-Site erstellt wird, werden neue Benutzergruppen dynamisch mit eindeutigen IDs (uid) und Berechtigungen erstellt, die für verschiedene Verwaltungsfunktionen geeignet sind, die zur Verwaltung der Community-Site erforderlich sind, entweder in der Autorengruppe (siehe [Autorengruppen-Rollen](#author-group-roles)) oder in der Umgebung zum Veröffentlichen (siehe [Rollen der Veröffentlichungsgruppe](#publish-group-roles)).

Die Namen der Gruppen werden aus dem Namen generiert, der der Site während der [Community-Site-Erstellung](sites-console.md#step13asitetemplate) gegeben wird. Die eindeutigen IDs vermeiden Namenskonflikte für ähnlich benannte Community-Sites und Community-Gruppen auf demselben Server.

Wenn der Site-Name beispielsweise &quot;*engagement*&quot;für eine Site mit dem Titel &quot;We.Retail Engage&quot;wäre, würde eine der erstellten Benutzergruppen wie folgt lauten:

* Community *Interagieren*-Mitglieder

## Autorenumgebung {#author-environment}

### Tunnel-Dienst {#tunnel-service}

Wenn Sie die Umgebung zum Erstellen von Sites](sites-console.md), [zum Ändern der Site-Eigenschaften](sites-console.md#modifying-site-properties) und [zum Verwalten von Community-Mitgliedern und Mitgliedsgruppen](members.md) verwenden, müssen Sie auf in der Umgebung &quot;Veröffentlichen&quot;registrierte Benutzer und Benutzergruppen zugreifen.[

Der Tunneldienst bietet diesen Zugriff mithilfe des Replizierungsagenten beim Autor.

* Weitere Informationen finden Sie unter [Konfigurationsanweisungen](deploy-communities.md#tunnel-service-on-author) auf der Bereitstellungsseite.

Die Konsolen [Communities Mitglieder und Gruppen](members.md) dienen ausschließlich der Verwaltung von Benutzern (Mitglieder) und Benutzergruppen (Mitgliedsgruppen), die nur in der Umgebung zum Veröffentlichen registriert sind.

Um in der Autorenkonsole registrierte Benutzer und Benutzergruppen zu verwalten, verwenden Sie die [Sicherheitskonsole](../../help/sites-administering/security.md)

### Autorengruppe-Rollen {#author-group-roles}

| Wenn Mitglied der Gruppe... | Primär |
|---|---|
| administrators | Die Gruppe &quot;Administratoren&quot;besteht aus Systemadministratoren, die über alle Fähigkeiten eines Community-Administrators sowie über die Fähigkeit verfügen, die Gruppe &quot;Community-Administratoren&quot;zu verwalten. |
| Community-Administratoren | Die Gruppe &quot;Community-Administratoren&quot;wird automatisch Mitglied aller Community-Sites und aller Community-Gruppen, die auf der Site erstellt wurden. Ein erstes Mitglied der Gruppe &quot;Community-Administratoren&quot;ist die Gruppe &quot;Administratoren&quot;. In der Umgebung &quot;Autor&quot;können Community-Administratoren Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community verbieten) und Inhalte moderieren. |
| Community &lt;*Site-Name* SiteContent Manager | Der Site Content Manager der Community kann herkömmliche AEM erstellen, Inhalte erstellen und Seiten für eine Community-Site ändern. |
| Community-Aktivierungsmanager | Die Gruppe Community-Berechtigungsmanager besteht aus Benutzern, die für die Zuweisung zur Verwaltung der Gruppe der Berechtigungsmanager einer Community-Site zur Verfügung stehen. |
| Community &lt;*Site-Name* > Site-fähige Manager | Die Community-Site-Aktivierungsmanager-Gruppe besteht aus Benutzern, die mit der Verwaltung der Aktivierung einer Community-Site beauftragt wurden [Ressourcen](resources.md). |
| Kein | Ein anonymer Site-Besucher kann nicht auf die Autorendatei zugreifen. |

### Systemadministratoren {#system-administrators}

Mitglieder der Administratorgruppe sind Systemadministratoren, die sowohl für Autoren- als auch für Veröffentlichungs-Umgebung die Ersteinrichtung einer AEM durchführen können.

Zu Demonstrations- und Entwicklungszwecken verfügt die Administratorgruppe über ein Mitglied, dessen Benutzer *admin* lautet und dessen Kennwort *admin* lautet.

Bei Produktions-Umgebung sollte die Standardadministratorgruppe geändert werden.

Gehen Sie wie folgt vor: [Sicherheitscheckliste](../../help/sites-administering/security-checklist.md).

## Veröffentlichungsumgebung {#publish-environment}

### Mitglied werden {#becoming-a-member}

In der Umgebung zum Veröffentlichen kann ein Site-Besucher je nach den [Einstellungen](sites-console.md#user-management) der Community-Site Community-Mitglied werden:

* Wenn die Community-Site privat ist (geschlossen):
   * Nach Einladung
   * Durch Handlungen eines Administrators

* Wenn die Community-Site öffentlich (offen) ist:
   * Durch Selbstregistrierung
   * Durch soziale Anmeldung bei Facebook und Twitter

>[!NOTE]
>
>Wenn sich ein Site-Besucher als Mitglied einer offenen Community-Site registriert, werden sie automatisch Mitglied anderer offener Community-Sites auf derselben Umgebung zur Veröffentlichung.

### Rollen der Veröffentlichungsgruppe {#publish-group-roles}

| Wenn Mitglied der Gruppe... | Primär |
|---|---|
| Community &lt;*Site-Name*>-Mitglieder | Ein Community-Site-Mitglied ist ein registrierter Benutzer. Sie können sich anmelden, ihr Profil ändern, einer offenen Community-Gruppe beitreten, Inhalte in die Community posten, Nachrichten an andere Mitglieder senden und Site-Aktivitäten folgen. |
| Community &lt;*Site-Name* Moderatoren | Ein Community-Site-Moderator ist ein vertrauenswürdiges Community-Mitglied, das in der Lage ist, UGC entweder stapelweise über die Moderationskonsole oder im Kontext auf der Seite zu moderieren, auf der der Inhalt gepostet wird. |
| Community &lt;*Site-Name* &lt;*Gruppenname*> Mitglieder | Ein Community-Gruppenmitglied ist ein Community-Mitglied, das entweder einer offenen Community-Gruppe beigetreten ist oder zu einer geschlossenen Community-Gruppe eingeladen wurde. Sie haben die Fähigkeiten eines Mitglieds für diese Community-Gruppe innerhalb der Site. |
| Community &lt;*Site-Name*> Gruppenadministratoren | Ein Community-Site-Gruppenadministrator ist ein vertrauenswürdiges Community-Mitglied, das mit der Erstellung und Verwaltung von Untergruppen (Gruppen) innerhalb einer Community-Site betraut ist. Einbezogen ist die Fähigkeit, kontextbezogene Moderation bereitzustellen. |
| *Sicherheitsgruppe für berechtigte Mitglieder* | Eine manuell erstellte und gepflegte Benutzergruppe zur Einschränkung der Inhaltserstellung. Siehe [Gruppe der privilegierten Mitglieder](#privileged-members-group). |
| Kein | Ein anonymer Site-Besucher, der die Site entdeckt, kann Ansichten erstellen und Community-Sites suchen, die anonymen Zugriff zulassen. Um Inhalte zu nutzen und zu posten, muss sich der Benutzer selbst registrieren (falls erlaubt) und Mitglied der Community werden. |

### Zuweisen von Mitgliedern zu Veröffentlichungsgruppenrollen {#assigning-members-to-publish-group-roles}

Wenn [eine Community-Site](sites-console.md) in der Autor-Umgebung erstellt oder [die Site-Eigenschaften ändert, kann](sites-console.md#modifying-site-properties) Mitgliedern in der Veröffentlichungs-Umgebung verschiedene Rollen zugewiesen werden, z. B. Moderatoren, Gruppenadministratoren, Ressourcenkontakte oder privilegierte Mitglieder.

[Die Aktivierung des Tunneldienstes ](sync.md#accessingpublishusersfromauthor) führt dazu, dass die Zuweisungsoptionen von Mitgliedern beim Veröffentlichen anstatt von Benutzern beim Autor angezeigt werden.

Die ausgewählten Mitglieder werden automatisch der [entsprechenden Gruppe](#publish-group-roles) zugewiesen und ihre Mitgliedschaften werden einbezogen, wenn die Community-Site (erneut) veröffentlicht wird.

### Gruppe privilegierter Mitglieder {#privileged-members-group}

Der Zweck einer privilegierten Mitglieder Sicherheitsgruppe ist es, die Erstellung von Inhalten für bestimmte Community-Funktionen auf eine privilegierte Untergruppe der Mitglieder einer Community-Site zu beschränken.

Die Gruppe der privilegierten Mitglieder ist eine Mitgliedsgruppe, die mithilfe der Konsole [Communities Gruppen](members.md) erstellt und verwaltet wird.

Nachdem eine Gruppe privilegierter Mitglieder erstellt wurde und der [Tunneldienst](sync.md#accessingpublishusersfromauthor) aktiviert ist, kann die Struktur einer bestehenden Community-Site [geändert](sites-console.md#modify-structure) werden, um die Konfiguration ihrer Community-Funktionen zu &quot;Privilegierte Mitglieder zulassen&quot;zu bearbeiten und die erstellte Gruppe hinzuzufügen.

Die Community-Funktionen, die die Spezifikation einer oder mehrerer privilegierter Mitgliedergruppen ermöglichen, sind:

* [Blog-Funktion](functions.md#blog-function)  - Schränken Sie die Erstellung neuer Artikel ein.
* [Kalenderfunktion](functions.md#calendar-function)  - Zur Einschränkung der Erstellung neuer Ereignis.
* [Forenfunktion](functions.md#forum-function)  - Schränken Sie die Erstellung neuer Themen ein.
* [QnA-Funktion](functions.md#qna-function)  - Zur Einschränkung der Erstellung neuer Fragen.

Wenn keine Community-Funktion gesichert ist (keine privilegierte Mitgliedergruppe zugewiesen), dürfen alle Mitglieder der Community-Site Funktionsinhalte (Artikel, Ereignisse, Themen, Fragen) erstellen.

>[!NOTE]
>
>Wenn ein Benutzer einer Gruppe von privilegierten Mitgliedern für eine Community-Site hinzugefügt wird, werden ihm nur dann Berechtigungen erteilt, wenn er auch Mitglied derselben Community-Site ist.

## Erstellen von Community-Mitgliedern {#creating-community-members}

### Repository-Speicherort {#repository-location}

Damit bestimmte Funktionen ordnungsgemäß funktionieren, müssen Benutzer und Benutzergruppen mit den entsprechenden Berechtigungen erstellt werden.

Wenn Mitglieder in `/home/users/community` erstellt werden, erben sie die richtigen ACLs, die den Profilen der Mitglieder Leseberechtigungen gewähren.

Auf ähnliche Weise sollten benutzerspezifische Benutzergruppen der Community (z. B. privilegierte Mitgliedergruppen) in `/home/groups/community` erstellt werden.

Mithilfe der Konsolen [Communities Mitglieder und Gruppen](members.md) werden Benutzer und Gruppen in diesen Pfaden erstellt.

Um einen benutzerdefinierten Pfad anzugeben, muss die klassische Benutzeroberfläche für Sicherheit verwendet werden, auf die unter [https://&lt;server>:&lt;port>/useradmin](http://localhost:4503/useradmin) zugegriffen werden kann.

Um Leseberechtigungen für benutzerdefinierte Mitgliederpfade zu gewähren, setzen Sie in allen Veröffentlichungsinstanzen ACLs ähnlich wie `/home/users/community`:

```xml
<allow
  jcr:primaryType="rep:GrantACE"
  rep:principalName="everyone"
  rep:privileges="{Name}[jcr:read]" >
  <rep:restrictions
    jcr:primaryType="rep:Restrictions"
    rep:glob="*/profile*" />
</allow>
```

Um die richtigen Berechtigungen für benutzerdefinierte Mitgliedergruppenpfade, z. B. /home/groups/mycompany, in allen Veröffentlichungsinstanzen bereitzustellen, setzen Sie ACLs ähnlich wie `/home/groups/community`:

```xml
<allow
  jcr:primaryType="rep:GrantACE"
  rep:principalName="community-administrators"
  rep:privileges="{Name}[jcr:read]"  />
```

### Konsolen {#consoles}

Es gibt vier separate Konsolen, die nur in der Autorenversion verfügbar sind:

| console | Werkzeuge, Sicherheit, Benutzer | Werkzeuge, Sicherheit, Gruppen | Gemeinschaften, Mitglieder | Communities, Gruppen |
|----------|-----------------------|------------------------|------------------------------------------------------------|------------------------------------------------------------|
| verwaltet | Benutzer beim Autor | Benutzergruppen beim Autor | Mitglieder im Veröffentlichungsmodus | Mitgliedergruppen im Veröffentlichungsmodus |
| erfordert | Administratorberechtigung | Administratorberechtigung | Admin-Berechtigung, Tunneldienst, Benutzersynchronisierung für Veröffentlichungsfarm | Admin-Berechtigung, Tunneldienst, Benutzersynchronisierung für Veröffentlichungsfarm |

### Community-Aktivierungsmanager-Rolle {#community-enablement-manager-role}

Die Möglichkeit, dass sich ein Site-Besucher selbst registriert, ist in der Regel für eine [Aktivierungsgemeinschaft](overview.md#enablement-community) nicht zulässig, da mit jedem Mitglied Kosten verbunden sind. Die Aktivierung wird von Lernenden und Ressourcen verwaltet, die von einem Benutzer verwaltet werden, dem bei der Erstellung der Site [Rolle](#author-group-roles) von `enablement manager` [während der Erstellung](sites-console.md#enablement) (als Mitglied der Gruppe `Community <site-name> Siteenablementmanagers` hinzugefügt) zugewiesen wurden. Das `enablement manager` ist auch dafür verantwortlich, dass Lernressourcen](resources.md) Community-Mitgliedern beim Autor zugewiesen werden.[

Für eine bestimmte Community-Site können nur Benutzer ausgewählt werden, die Mitglieder der globalen `Community Enablement Managers`-Gruppe sind.`enablement manager`

Um einen Benutzer zu erstellen, dem die Rolle von `Community Site Enablement Manager` zugewiesen werden kann, verwenden Sie die klassische UI-Sicherheitskonsole, um den Pfad anzugeben:

Auf der Authoring-Instanz:

1. Wenn Sie sich mit Administratorrechten angemeldet haben, navigieren Sie zur klassischen UI-Sicherheitskonsole.

   Beispiel: [http://localhost:4502/useradmin](http://localhost:4502/useradmin)

2. Wählen Sie im Menü Bearbeiten **[!UICONTROL Benutzer erstellen]**.
3. Füllen Sie das Dialogfeld `Create User` aus.
   * Pfad muss `/home/users/community` sein.
4. Wählen Sie **[!UICONTROL Erstellen]**.

   ![create-community-user](assets/create-community-user.png)

* Suchen Sie im linken Bereich nach dem neu erstellten Benutzer und wählen Sie im rechten Bereich die Option zur Anzeige aus.

   ![community-user](assets/view-community-user.png)

Im linken Bereich:

1. Löschen Sie das Suchfeld und wählen Sie **[!UICONTROL Benutzer ausblenden]**.
2. Ziehen Sie `community-enablementmanagers` auf die Registerkarte **[!UICONTROL Gruppen]** des neuen Benutzers, der im rechten Bereich angezeigt wird.

   ![assign-group](assets/assign-group.png)

### Community-Administratoren-Rolle {#community-administrators-role}

Wie im Diagramm [Autorengruppe Rollen](#author-group-roles) angegeben, können Mitglieder der Community-Administratorgruppe Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community verbieten) und Inhalte moderieren.

Führen Sie die gleichen Schritte aus wie beim Erstellen und Zuweisen eines Benutzers zur Rolle des [Aktivierungsmanagers](#communitysiteenablementmanagerrole), fügen Sie jedoch unter der Registerkarte &quot;Gruppen&quot;des Benutzers die Gruppe c `ommunity-administrators` hinzu.

### LDAP-Integration {#ldap-integration}

AEM unterstützt die Verwendung von LDAP für die Authentifizierung von Benutzern sowie die Erstellung von Benutzerkonten. Dies wird unter [Konfigurieren von LDAP mit AEM 6](../../help/sites-administering/ldap-config.md) beschrieben.

Im Folgenden finden Sie einige Konfigurationsdetails, die spezifisch für Community-Mitglieder und Mitgliedsgruppen sind.

1. Konfigurieren Sie LDAP für jede AEM Instanz im Veröffentlichungsmodus.
2. [LDAP-Identitätsanbieter](../../help/sites-administering/ldap-config.md#configuring-the-ldap-identity-provider)

   * Keine besonderen Anweisungen

3. [Synchronisierungs-Handler](../../help/sites-administering/ldap-config.md#configuring-the-synchronization-handler)

   * Legen Sie die folgenden Eigenschaften fest:

      * **[!UICONTROL Automatische Mitgliedschaft]** des Benutzers:  `community-<site name>-<uid>-members`
      * **[!UICONTROL Benutzerpfadpräfix]**:  `/community`
      * **[!UICONTROL Gruppenpfadpräfix]**:  `/community`

4. [Das externe Anmeldemodul](../../help/sites-administering/ldap-config.md#the-external-login-module)

   * keine besonderen Anweisungen

Dies führt dazu, dass Benutzer automatisch der Mitgliedergruppe der Community-Site zugewiesen werden und der Repository-Speicherort `/home/users/community` und `/home/groups/community` lautet, sodass sie die entsprechenden Berechtigungen erben, um das Profil der anderen zu sehen.

* Der Wert `User auto membership` sollte die Eigenschaft `rep:authorizableId` sein, nicht die Eigenschaft `givenName` (Anzeigename) aus dem Profil.

## Synchronisieren von Benutzern unter AEM Instanzen {#synchronizing-users-among-aem-instances}

Wenn Sie eine [Veröffentlichungsfarm](topologies.md) verwenden, stellen Sie sicher, dass die Benutzer auf jeder Veröffentlichungsinstanz denselben Pfad haben, indem Sie die Benutzer zuerst in eine Instanz importieren und [die Benutzersynchronisierung](sync.md) aktivieren, um die Benutzer an die anderen Instanzen im Veröffentlichungsmodus zu verteilen.

Wenn Sie Benutzergruppen importieren, stellen Sie sicher, dass die Benutzergruppen auf jeder Instanz im Veröffentlichungsmodus denselben Pfad haben, importieren Sie in eine Instanz, dann [erstellen Sie ein Paket](../../help/sites-administering/package-manager.md#creating-a-new-package) für den Export und installieren Sie dieses Paket auf allen anderen Instanzen im Veröffentlichungsmodus.

Während die Synchronisierung von Benutzergruppen über die Benutzersynchronisierung in einer zukünftigen Version enthalten sein wird, wird derzeit nur die *Mitgliedschaft* einer Benutzergruppe synchronisiert, wenn die Benutzersynchronisierung ausgeführt wird.

## Info zu Community-Gruppen {#about-community-groups}

Bei der Diskussion von Gruppen gibt es zwei unterschiedliche Themen:

* **[Community-Gruppen](overview.md#communitygroups)**

   Community-Gruppen sind die Untergruppen, die in der Umgebung zum Veröffentlichen einer Community-Site erstellt werden können, die die Erstellung von Community-Gruppen unterstützt. Die Erstellung einer Community-Gruppe führt zu mehr Seiten, die der Website hinzugefügt werden, und wird auf eine Weise verwaltet, die der ihrer übergeordneten Community-Site ähnlich ist. Weitere Informationen finden Sie unter [Community Group Essentials](essentials-groups.md) für Entwickler und [Community Group](creating-groups.md) für Autoren.

* **[Mitgliedergruppen](../../help/sites-administering/security.md)**

   Mitgliedergruppen sind die Gruppen, denen Mitglieder angehören können und die über die Konsole &quot;Gruppen&quot;verwaltet werden. Ein Großteil der Diskussionen auf dieser Seite wurde den Fraktionen gewidmet. Die automatisch für eine Community-Site erstellten Mitgliedergruppen, denen *`Community`* vorangestellt wird, können als Community-Gruppe bezeichnet werden, daher muss der Kontext der Diskussion berücksichtigt werden.
