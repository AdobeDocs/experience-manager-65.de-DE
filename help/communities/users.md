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
translation-type: tm+mt
source-git-commit: 2422ed41b18bc558f0cfc9e80f7eb6f4923aa07c

---


# Managing Users and User Groups {#managing-users-and-user-groups}

## Übersicht {#overview}

In AEM Communities können sich Benutzer in der Umgebung zum Veröffentlichen selbst registrieren und ihre Profil bearbeiten. Mit den entsprechenden Berechtigungen können sie auch:

* Erstellen Sie Untergruppen auf der Community-Site (siehe [Community-Gruppen](creating-groups.md)).

* [Moderieren Sie](moderation.md) vom Benutzer erstellte Inhalte (UGC).

* Stellen Sie [Ressourcenkontakte](resources.md) ein.

* Sie haben die [Berechtigung](#privileged-members-group) , Einträge für Blogs, Kalender, QnA und Foren zu erstellen.

Benutzer, die in der Umgebung zur Veröffentlichung registriert sind, werden im Allgemeinen als *Community-Mitglieder (Mitglieder)* bezeichnet, um sie von *Benutzern* in der Umgebung des Autors zu unterscheiden.

Berechtigungen werden erteilt, indem Mitglieder einer [Mitglieds-(Benutzer-)Gruppe](#publish-group-roles) zugewiesen werden, die dynamisch erstellt wird, wenn die Community-Site aus der Autorenbenutzerseite [erstellt](sites-console.md) oder [geändert](sites-console.md#modifying-site-properties) wird. Bei der Arbeit mit der Autorenversion sind die Mitglieder über den [Tunneldienst](#tunnel-service)von der Veröffentlichungs-Umgebung aus sichtbar.

Standardmäßig sollten in der Umgebung &quot;Veröffentlichen&quot;erstellte Mitglieder und Mitgliedsgruppen nicht in der Umgebung &quot;Autor&quot;angezeigt werden. Benutzer und Benutzergruppen, die in der Autor-Umgebung erstellt wurden, sollen in ähnlicher Weise in der Autorendatei verbleiben.

Wenn Benutzer, die Autor und Mitglieder im Veröffentlichungsmodus sind, aus derselben Liste von Benutzern stammen, z. B. aus demselben LDAP-Ordner synchronisiert, werden sie nicht als derselbe Benutzer mit denselben Berechtigungen und derselben Gruppenmitgliedschaft in der Autor- und Veröffentlichungs-Umgebung betrachtet. Die Rolle(en) der Mitglieder und Benutzer muss (müssen) bei der Veröffentlichung und gegebenenfalls beim Autor gesondert festgelegt werden.

For a [publish farm](topologies.md), registration and modifications made on one publish instance need to be synchronized with other publish instances in order for them to have access to the same user data. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md), in dem ein Abschnitt beschrieben wird, [was passiert, wenn...](sync.md#what-happens-when).

### Anteilslimits {#contribution-limits}

Zum Schutz vor Spam ist es möglich, die Häufigkeit der Veröffentlichung von Inhalten durch die Mitglieder zu begrenzen. Darüber hinaus ist es möglich, die Beiträge der neu eingetragenen Mitglieder automatisch zu begrenzen.

Weitere Informationen finden Sie unter [Beitragsbeschränkungen](limits.md)für Mitglieder.

### Dynamisch erstellte Benutzergruppen {#dynamically-created-user-groups}

Wenn eine neue Community-Site erstellt wird, werden neue Benutzergruppen dynamisch mit eindeutigen IDs (uid) und Berechtigungen erstellt, die für verschiedene Verwaltungsfunktionen geeignet sind, die zur Verwaltung der Community-Site erforderlich sind, entweder in der Autorengruppe (siehe Rollen [Autorengruppe](#author-group-roles)) oder in der Umgebung zur Veröffentlichung (siehe Rollen der [Veröffentlichungsgruppe](#publish-group-roles)).

Die Namen der Gruppen werden aus dem Namen generiert, der der Site während der [Community-Site-Erstellung](sites-console.md#step13asitetemplate)gegeben wird. Die eindeutigen IDs vermeiden Namenskonflikte für ähnlich benannte Community-Sites und Community-Gruppen auf demselben Server.

Wenn beispielsweise der Site-Name für eine Site mit dem Titel &quot;We.Retail Engage&quot;&quot;*engagement*&quot;lautete, würde eine der erstellten Benutzergruppen wie folgt lauten:

* Community- *Interaktionsmitglieder*

## Autorenumgebung {#author-environment}

### Tunnel-Dienst {#tunnel-service}

Wenn Sie mit der Autorenversion Websites [](sites-console.md)erstellen, Site-Eigenschaften [](sites-console.md#modifying-site-properties) ändern und Community-Mitglieder und -Mitgliedsgruppen [](members.md)verwalten, müssen Sie auf die in der Umgebung &quot;Veröffentlichen&quot;registrierten Benutzer und Benutzergruppen zugreifen.

Der Tunneldienst bietet diesen Zugriff mithilfe des Replizierungsagenten beim Autor.

* Weitere Informationen finden Sie unter [Konfigurationsanweisungen](deploy-communities.md#tunnel-service-on-author) auf der Bereitstellungsseite.

Die [Community-Mitglieder- und -Gruppenkonsolen](members.md) dienen ausschließlich der Verwaltung von Benutzergruppen (Mitglieder) und Benutzergruppen (Mitgliedsgruppen), die nur in der Veröffentlichungs-Umgebung registriert sind.

Verwenden Sie die [Sicherheitskonsole, um in der Authoring-Umgebung registrierte Benutzer und Benutzergruppen zu verwalten](../../help/sites-administering/security.md)

### Rollen der Autorengruppe {#author-group-roles}

| Wenn Mitglied der Gruppe... | Primäre Rolle |
|---|---|
| administrators | Die Gruppe &quot;Administratoren&quot;besteht aus Systemadministratoren, die über alle Fähigkeiten eines Community-Administrators sowie über die Fähigkeit verfügen, die Gruppe &quot;Community-Administratoren&quot;zu verwalten. |
| Community-Administratoren | Die Gruppe &quot;Community-Administratoren&quot;wird automatisch Mitglied aller Community-Sites und aller Community-Gruppen, die auf der Site erstellt wurden. Ein erstes Mitglied der Gruppe &quot;Community-Administratoren&quot;ist die Gruppe &quot;Administratoren&quot;. In der Umgebung &quot;Autor&quot;können Community-Administratoren Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community verbieten) und Inhalte moderieren. |
| Community &lt;*Site-Name*> SiteContent Manager | Der Community Site Content Manager kann herkömmliche AEM-Authoring-, Inhaltserstellung- und Änderungsseiten für eine Community-Site durchführen. |
| Community-Aktivierungsmanager | Die Gruppe Community-Berechtigungsmanager besteht aus Benutzern, die für die Zuweisung zur Verwaltung der Gruppe der Berechtigungsmanager einer Community-Site zur Verfügung stehen. |
| Community &lt;*Site-Name* > SiteEnabledManager | Die Community-Site-Aktivierungsmanager-Gruppe besteht aus Benutzern, die mit der Verwaltung der [Ressourcen](resources.md)für die Aktivierung einer Community-Site betraut wurden. |
| Keine | Ein anonymer Site-Besucher kann nicht auf die Autorendatei zugreifen. |

### Systemadministratoren {#system-administrators}

Mitglieder der Administratorgruppe sind Systemadministratoren, die die Ersteinrichtung einer AEM-Umgebung sowohl für Autoren- als auch für Veröffentlichungsfunktionen durchführen können.

Zu Demonstrations- und Entwicklungszwecken verfügt die Administratorgruppe über ein Mitglied, dessen Benutzer *admin* und Kennwort *admin* lautet.

Bei Produktions-Umgebung sollte die standardmäßige Administratorgruppe geändert werden.

Befolgen Sie die [Sicherheitscheckliste](../../help/sites-administering/security-checklist.md).

## Veröffentlichungsumgebung {#publish-environment}

### Mitglied werden {#becoming-a-member}

In der Umgebung &quot;Veröffentlichen&quot;kann je nach [Einstellungen](sites-console.md#user-management) der Community-Site ein Site-Besucher Mitglied einer Community werden:

* Wenn die Community-Site privat ist (geschlossen):
   * Nach Einladung
   * Durch Handlungen eines Administrators

* Wenn die Community-Site öffentlich (offen) ist:
   * Durch Selbstregistrierung
   * Durch soziale Anmeldung bei Facebook und Twitter

>[!NOTE]
>
>Wenn sich ein Site-Besucher als Mitglied einer offenen Community-Site registriert, werden sie automatisch Mitglied anderer offener Community-Sites auf derselben Umgebung zur Veröffentlichung.


### Rollen veröffentlichen {#publish-group-roles}

| Wenn Mitglied der Gruppe... | Primäre Rolle |
|---|---|
| Community &lt;*Site-Name*>-Mitglieder | Ein Community-Site-Mitglied ist ein registrierter Benutzer. Sie können sich anmelden, ihr Profil ändern, einer offenen Community-Gruppe beitreten, Inhalte in die Community posten, Nachrichten an andere Mitglieder senden und Site-Aktivitäten folgen. |
| Community &lt;*Site-Name*>-Moderatoren | Ein Community-Site-Moderator ist ein vertrauenswürdiges Community-Mitglied, das in der Lage ist, UGC entweder stapelweise über die Moderationskonsole oder im Kontext auf der Seite zu moderieren, auf der der Inhalt gepostet wird. |
| Community &lt;*Site-Name*> &lt;*Gruppenname*>-Mitglieder | Ein Community-Gruppenmitglied ist ein Community-Mitglied, das entweder einer offenen Community-Gruppe beigetreten ist oder zu einer geschlossenen Community-Gruppe eingeladen wurde. Sie haben die Fähigkeiten eines Mitglieds für diese Community-Gruppe innerhalb der Site. |
| Community &lt;*Site-Name*>-Gruppenadministratoren | Ein Community-Site-Gruppenadministrator ist ein vertrauenswürdiges Community-Mitglied, das mit der Erstellung und Verwaltung von Untergruppen (Gruppen) innerhalb einer Community-Site betraut ist. Einbezogen ist die Fähigkeit, kontextbezogene Moderation bereitzustellen. |
| *Sicherheitsgruppe für berechtigte Mitglieder* | Eine manuell erstellte und gepflegte Benutzergruppe zur Einschränkung der Inhaltserstellung. Siehe Gruppe [berechtigter Mitglieder](#privileged-members-group). |
| Keine | Ein anonymer Site-Besucher, der die Site entdeckt, kann Ansichten erstellen und Community-Sites suchen, die anonymen Zugriff zulassen. Um Inhalte zu nutzen und zu posten, muss sich der Benutzer selbst registrieren (falls erlaubt) und Mitglied der Community werden. |

### Zuweisen von Mitgliedern zu Rollen in Veröffentlichungsgruppen {#assigning-members-to-publish-group-roles}

Bei der [Erstellung einer Community-Site](sites-console.md) in der Authoring-Umgebung oder beim [Ändern der Site-Eigenschaften können den Mitgliedern verschiedene Rollen zugewiesen werden,](sites-console.md#modifying-site-properties) die in der Umgebung zur Veröffentlichung ausgeführt werden, z. B. Moderatoren, Gruppenadministratoren, Ressourcenkontakte oder privilegierte Mitglieder.

[Wenn Sie den Tunneldienst](sync.md#accessingpublishusersfromauthor) aktivieren, werden die Zuweisungsoptionen von Mitgliedern bei der Veröffentlichung anstatt von Benutzern bei der Autoren angezeigt.

Die ausgewählten Mitglieder werden automatisch der [entsprechenden Gruppe](#publish-group-roles) zugewiesen und ihre Mitgliedschaften werden einbezogen, wenn die Community-Site (erneut) veröffentlicht wird.

### Gruppe privilegierter Mitglieder {#privileged-members-group}

Der Zweck einer privilegierten Mitglieder Sicherheitsgruppe ist es, die Erstellung von Inhalten für bestimmte Community-Funktionen auf eine privilegierte Untergruppe der Mitglieder einer Community-Site zu beschränken.

Die Gruppe der privilegierten Mitglieder ist eine Mitgliedsgruppe, die mithilfe der [Communities Groups-Konsole](members.md)erstellt und verwaltet wird.

Nachdem eine Gruppe privilegierter Mitglieder erstellt wurde und der [Tunneldienst aktiviert](sync.md#accessingpublishusersfromauthor)ist, kann die Struktur einer bestehenden Community-Site [geändert](sites-console.md#modify-structure) werden, um die Konfiguration ihrer Community-Funktionen zu &quot;Privilegierte Mitglieder zulassen&quot;zu bearbeiten und die erstellte Gruppe hinzuzufügen.

Die Community-Funktionen, die die Spezifikation einer oder mehrerer privilegierter Mitgliedergruppen ermöglichen, sind:

* [Blog-Funktion](functions.md#blog-function) - Eingeschränkt die Erstellung neuer Artikel.
* [Kalenderfunktion](functions.md#calendar-function) - Eingeschränkt die Erstellung neuer Ereignis.
* [Forenfunktion](functions.md#forum-function) - Schränken Sie die Erstellung neuer Themen ein.
* [QnA-Funktion](functions.md#qna-function) - Eingeschränkt die Erstellung neuer Fragen.

Wenn keine Community-Funktion gesichert ist (keine privilegierte Mitgliedergruppe zugewiesen), dürfen alle Mitglieder der Community-Site Funktionsinhalte (Artikel, Ereignisse, Themen, Fragen) erstellen.

>[!NOTE]
>
>Wenn ein Benutzer einer Gruppe von privilegierten Mitgliedern für eine Community-Site hinzugefügt wird, werden ihm nur dann Berechtigungen erteilt, wenn er auch Mitglied derselben Community-Site ist.


## Community-Mitglieder erstellen {#creating-community-members}

### Repository {#repository-location}

Damit bestimmte Funktionen ordnungsgemäß funktionieren, müssen Benutzer und Benutzergruppen mit den entsprechenden Berechtigungen erstellt werden.

Wenn Mitglieder in erstellt werden, `/home/users/community`übernehmen sie die richtigen ACLs, die den Profilen der Mitglieder Leserechte gewähren.

Auf ähnliche Weise sollten benutzerspezifische Benutzergruppen der Community (z. B. privilegierte Mitgliedergruppen) in erstellt werden `/home/groups/community`.

Mithilfe der [Communities Mitglieder und Gruppen-Konsolen](members.md) werden Benutzer und Gruppen in diesen Pfaden erstellt.

Um einen benutzerdefinierten Pfad anzugeben, muss die klassische Benutzeroberfläche für Sicherheit verwendet werden, auf die unter [https://&lt;server>:&lt;port>/useradmin](http://localhost:4503/useradmin)zugegriffen werden kann.

Um Leseberechtigungen für benutzerdefinierte Mitgliederpfade zu gewähren, setzen Sie in allen Veröffentlichungsinstanzen ACLs ähnlich `/home/users/community`wie:

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

Um die richtigen Berechtigungen für benutzerdefinierte Mitgliedergruppenpfade, z. B. /home/groups/mycompany, in allen Veröffentlichungsinstanzen bereitzustellen, setzen Sie ACLs ähnlich `/home/groups/community`:

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

Die Möglichkeit, dass sich ein Site-Besucher selbst registriert, ist in der Regel für eine [Aktivierungsgemeinschaft](overview.md#enablement-community) nicht zulässig, da mit jedem Mitglied Kosten verbunden sind. Aktivierung Lernende und Ressourcen werden von einem Benutzer verwaltet, dem die [Rolle](#author-group-roles) `enablement manager` bei der Site-Erstellung [beim Autor zugewiesen wurde (als Mitglied der Gruppe hinzugefügt](sites-console.md#enablement) `Community <site-name> Siteenablementmanagers`). Der `enablement manager` ist auch für die [Zuweisung von Lernressourcen](resources.md) zu Community-Mitgliedern bei Autoren verantwortlich.

Nur Benutzer, die Mitglieder der globalen `Community Enablement Managers` Gruppe sind, können als `enablement manager` eine bestimmte Community-Site ausgewählt werden.

Um einen Benutzer zu erstellen, dem die Rolle zugewiesen werden kann, `Community Site Enablement Manager`verwenden Sie die klassische UI-Sicherheitskonsole, um den Pfad anzugeben:

Auf der Authoring-Instanz:

1. Wenn Sie sich mit Administratorrechten angemeldet haben, navigieren Sie zur klassischen UI-Sicherheitskonsole.

   For example, [http://localhost:4502/useradmin](http://localhost:4502/useradmin)

2. Wählen Sie im Menü Bearbeiten die Option Benutzer **[!UICONTROL erstellen]**.
3. Füllen Sie das `Create User` Dialogfeld aus.
   * Pfad muss sein `/home/users/community`.
4. Wählen Sie **[!UICONTROL Erstellen]**.

   ![chlimage_1-130](assets/chlimage_1-130.png)

* Suchen Sie im linken Bereich nach dem neu erstellten Benutzer und wählen Sie im rechten Bereich die Option zur Anzeige aus.

   ![chlimage_1-131](assets/chlimage_1-131.png)

Im linken Bereich:

1. Löschen Sie das Suchfeld und wählen Sie Benutzer **[!UICONTROL ausblenden]**.
2. Suchen Sie den neuen Benutzer und ziehen Sie ihn `community-enablementmanagers` auf die Registerkarte **[!UICONTROL Gruppen]** , die im rechten Bereich angezeigt wird.

   ![chlimage_1-132](assets/chlimage_1-132.png)

### Rolle der Community-Administratoren {#community-administrators-role}

Wie im Diagramm &quot;Rollen [der](#author-group-roles) Autorengruppe&quot;angegeben, können Mitglieder der Community-Administratorgruppe Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (Mitglieder können aus der Community ausgeschlossen werden) und Inhalte moderieren.

Führen Sie dieselben Schritte aus wie beim Erstellen und Zuweisen eines Benutzers zur Rolle des [Aktivierungsmanagers](#communitysiteenablementmanagerrole), fügen Sie jedoch auf der Registerkarte &quot;Gruppen&quot;des Benutzers eine `ommunity-administrators` Gruppe hinzu.

### LDAP-Integration {#ldap-integration}

AEM unterstützt die Verwendung von LDAP für die Authentifizierung von Benutzern sowie die Erstellung von Benutzerkonten. Ausführliche Informationen finden Sie unter [Konfigurieren von LDAP mit AEM 6](../../help/sites-administering/ldap-config.md).

Im Folgenden finden Sie einige Konfigurationsdetails, die spezifisch für Community-Mitglieder und Mitgliedsgruppen sind.

1. Konfigurieren Sie LDAP für jede AEM-Veröffentlichungsinstanz.
2. [LDAP-Identitätsanbieter](../../help/sites-administering/ldap-config.md#configuring-the-ldap-identity-provider)

   * Keine besonderen Anweisungen

3. [Synchronisierungs-Handler](../../help/sites-administering/ldap-config.md#configuring-the-synchronization-handler)

   * Legen Sie die folgenden Eigenschaften fest:

      * **[!UICONTROL Automatische Mitgliedschaft]** des Benutzers: `community-<site name>-<uid>-members`
      * **[!UICONTROL Benutzerpfadpräfix]**: `/community`
      * **[!UICONTROL Gruppenpfadpräfix]**: `/community`

4. [Das externe Anmeldemodul](../../help/sites-administering/ldap-config.md#the-external-login-module)

   * keine besonderen Anweisungen

Dies führt dazu, dass Benutzer automatisch der Mitgliedergruppe der Community-Site und dem Speicherort des Repositorys zugewiesen werden `/home/users/community` `/home/groups/community`und die entsprechenden Berechtigungen erben, um das Profil der anderen zu sehen.

* Der `User auto membership` Wert sollte die `rep:authorizableId` Eigenschaft sein, nicht der `givenName` (Anzeigename) des Profils.

## Synchronisieren von Benutzern unter AEM-Instanzen {#synchronizing-users-among-aem-instances}

Wenn Sie eine [Veröffentlichungsfarm](topologies.md)verwenden, stellen Sie sicher, dass die Benutzer in jeder Veröffentlichungsinstanz über denselben Pfad verfügen, indem Sie die Benutzer zuerst in eine Instanz importieren und die Benutzersynchronisierung [](sync.md) aktivieren, um Sling zu aktivieren, die Benutzer an die anderen Instanzen im Veröffentlichungsmodus zu verteilen.

Wenn Sie Benutzergruppen importieren, stellen Sie sicher, dass die Benutzergruppen auf jeder Instanz im Veröffentlichungsmodus denselben Pfad haben, importieren Sie in eine Instanz, [erstellen Sie dann ein Paket](../../help/sites-administering/package-manager.md#creating-a-new-package) für den Export und installieren Sie das Paket auf allen anderen Instanzen im Veröffentlichungsmodus.

Während die Synchronisierung von Benutzergruppen über die Benutzersynchronisierung in einer zukünftigen Version enthalten sein wird, wird derzeit nur die *Mitgliedschaft* einer Benutzergruppe synchronisiert, wenn die Benutzersynchronisierung ausgeführt wird.

## Community-Gruppen {#about-community-groups}

Bei der Diskussion von Gruppen gibt es zwei unterschiedliche Themen:

* **[Community-Gruppen](overview.md#communitygroups)**

   Community-Gruppen sind die Untergruppen, die in der Umgebung zum Veröffentlichen einer Community-Site erstellt werden können, die die Erstellung von Community-Gruppen unterstützt. Die Erstellung einer Community-Gruppe führt zu mehr Seiten, die der Website hinzugefügt werden, und wird auf eine Weise verwaltet, die der ihrer übergeordneten Community-Site ähnlich ist. Weitere Informationen finden Sie unter [Community Group Essentials](essentials-groups.md) für Entwickler und [Community Group](creating-groups.md) für Autoren.

* **[Mitgliedergruppen](../../help/sites-administering/security.md)**

   Mitgliedergruppen sind die Gruppen, denen Mitglieder angehören können und die über die Konsole &quot;Gruppen&quot;verwaltet werden. Ein Großteil der Diskussionen auf dieser Seite wurde den Fraktionen gewidmet. Die automatisch für eine Community-Site erstellten Mitgliedergruppen, denen ein Präfix vorangestellt wird, können als Community-Gruppe bezeichnet werden, daher muss der Kontext der Diskussion berücksichtigt werden. *`Community`*
