---
title: Verwalten von Benutzern und Benutzergruppen
seo-title: Verwalten von Benutzern und Benutzergruppen
description: Benutzer von AEM Communities können sich selbst registrieren und ihre Profile bearbeiten
seo-description: Benutzer von AEM Communities können sich selbst registrieren und ihre Profile bearbeiten
uuid: aeba424e-ea7e-4da5-b94f-ea8af4caa7d2
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 774c2553-b629-456b-afa7-5713490f4a0a
role: Administrator
exl-id: 4237085a-d70d-41de-975d-153f58336daa
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 1%

---

# Verwalten von Benutzern und Benutzergruppen {#managing-users-and-user-groups}

## Überblick {#overview}

In AEM Communities können sich Benutzer in der Veröffentlichungsumgebung selbst registrieren und ihre Profile bearbeiten. Mit den entsprechenden Berechtigungen können sie auch:

* Erstellen Sie Untergruppen innerhalb der Community-Site (siehe [Community-Gruppen](creating-groups.md)).

* [](moderation.md) Moderieren benutzergenerierter Inhalte (UGC).

* Sei [Aktivierungsressource](resources.md) Kontakte.

* Seien Sie [privilegiert](#privileged-members-group), um Einträge für Blogs, Kalender, QnA und Foren zu erstellen.

In der Veröffentlichungsumgebung registrierte Benutzer werden im Allgemeinen als *Community-Mitglieder (Mitglieder)* bezeichnet, um sie von *Benutzern* in der Autorenumgebung zu unterscheiden.

Berechtigungen werden gewährt, indem Mitglieder einer der [Mitglied(user)-Gruppen](#publish-group-roles) zugewiesen werden, die dynamisch erstellt werden, wenn die Community-Site [created](sites-console.md) oder [modified](sites-console.md#modifying-site-properties) aus der Autorenumgebung ist. Bei der Arbeit in der Autorenumgebung sind Mitglieder über den Dienst [tunnel](#tunnel-service) in der Veröffentlichungsumgebung sichtbar.

Standardmäßig sollten Mitglieder und Mitgliedergruppen, die in der Veröffentlichungsumgebung erstellt wurden, nicht in der Autorenumgebung angezeigt werden. Benutzer und Benutzergruppen, die in der Autorenumgebung erstellt wurden, sind auf ähnliche Weise dazu bestimmt, in der Autorenumgebung zu bleiben.

Wenn Benutzer in der Autoren- und Veröffentlichungsumgebung aus derselben Benutzerliste stammen, z. B. aus demselben LDAP-Ordner synchronisiert, werden sie nicht als derselbe Benutzer mit denselben Berechtigungen und Gruppenmitgliedschaften in der Autoren- und Veröffentlichungsumgebung betrachtet. Die Rolle(en) der Mitglieder und Benutzer muss (müssen) je nach Bedarf separat in der Veröffentlichungs- und Autoreninstanz festgelegt werden.

Für eine [Veröffentlichungsfarm](topologies.md) müssen die Registrierung und Änderungen, die an einer Veröffentlichungsinstanz vorgenommen werden, mit anderen Veröffentlichungsinstanzen synchronisiert werden, damit sie Zugriff auf dieselben Benutzerdaten haben. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md), die einen Abschnitt enthält, der [Was passiert, wenn..](sync.md#what-happens-when).

### Anteilslimits {#contribution-limits}

Zum Schutz vor Spam ist es möglich, die Häufigkeit der Veröffentlichung von Inhalten durch die Mitglieder zu begrenzen. Außerdem ist es möglich, die Beiträge neu registrierter Mitglieder automatisch zu begrenzen.

Weitere Informationen finden Sie unter [Mitgliederbeitragsbeschränkungen](limits.md).

### Dynamisch erstellte Benutzergruppen {#dynamically-created-user-groups}

Wenn eine neue Community-Site erstellt wird, werden neue Benutzergruppen dynamisch mit eindeutigen IDs (uid) und Berechtigungen erstellt, die für verschiedene Verwaltungsfunktionen geeignet sind, die zur Verwaltung der Community-Site erforderlich sind, entweder in der Autorenumgebung (siehe [Autorengruppen-Rollen](#author-group-roles)) oder in der Veröffentlichungsumgebung (siehe [Veröffentlichungsgruppenrollen](#publish-group-roles)).

Die Namen der Gruppen werden aus dem Namen generiert, der der Site während der [Community-Site-Erstellung](sites-console.md#step13asitetemplate) gegeben wird. Die eindeutigen IDs vermeiden Namenskonflikte für ähnlich benannte Community-Sites und Community-Gruppen auf demselben Server.

Wenn der Site-Name beispielsweise &quot;*engage*&quot;für eine Site mit dem Namen &quot;We.Retail Engage&quot;wäre, wäre eine der erstellten Benutzergruppen:

* Community *Engage*-Mitglieder

## Autorenumgebung {#author-environment}

### Tunnel-Dienst {#tunnel-service}

Wenn Sie die Autorenumgebung für [Sites erstellen](sites-console.md), [Siteeigenschaften ändern](sites-console.md#modifying-site-properties) und [Community-Mitglieder und Mitgliedergruppen verwalten](members.md), müssen Sie auf Benutzer und Benutzergruppen zugreifen, die in der Veröffentlichungsumgebung registriert sind.

Der Tunneldienst stellt diesen Zugriff mithilfe des Replikationsagenten auf der Autoreninstanz bereit.

* Weitere Informationen finden Sie unter [Konfigurationsanweisungen](deploy-communities.md#tunnel-service-on-author) auf der Bereitstellungsseite.

Die Konsolen [Communities-Mitglieder und -Gruppen](members.md) dienen ausschließlich der Verwaltung von Benutzern (Mitgliedern) und Benutzergruppen (Mitgliedergruppen), die nur in der Veröffentlichungsumgebung registriert sind.

Um in der Autorenumgebung registrierte Benutzer und Benutzergruppen zu verwalten, verwenden Sie die [Sicherheitskonsole](../../help/sites-administering/security.md)

### Autorengruppen-Rollen {#author-group-roles}

| Wenn Gruppenmitglied... | Primäre Rolle |
|---|---|
| administrators | Die Gruppe Administratoren besteht aus Systemadministratoren, die über alle Fähigkeiten eines Community-Administrators sowie über die Fähigkeit verfügen, die Gruppe Community-Administratoren zu verwalten. |
| Community-Administratoren | Die Gruppe Community-Administratoren wird automatisch Mitglied aller Community-Sites und aller auf der Site erstellten Community-Gruppen. Die Administratorgruppe ist ein erstmaliges Mitglied der Gruppe Community-Administratoren . In der Autorenumgebung können Community-Administratoren Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community verbieten) und Inhalte moderieren. |
| Community &lt;*Site-Name* Sitecontentmanager | Der Community-Site-Inhaltsmanager kann herkömmliche AEM erstellen, Seiten für eine Community-Site erstellen und ändern. |
| Community-Aktivierungsmanager | Die Gruppe Community-Aktivierungsmanager besteht aus Benutzern, die für die Zuweisung zur Verwaltung der Gruppe Aktivierungsmanager einer Community-Site zur Verfügung stehen. |
| Community &lt;*Site-Name* > SiteEnablementmanager | Die Gruppe Community-Site-Aktivierungsmanager besteht aus Benutzern, die zugewiesen wurden, um die Aktivierung einer Community-Site zu verwalten [Ressourcen](resources.md). |
| Kein | Ein anonymer Site-Besucher kann nicht auf die Autorenumgebung zugreifen. |

### Systemadministratoren {#system-administrators}

Mitglieder der Administratorgruppe sind Systemadministratoren, die die Ersteinrichtung einer AEM für die Autoren- und Veröffentlichungsumgebung durchführen können.

Zu Demonstrations- und Entwicklungszwecken verfügt die Administratorgruppe über ein Mitglied, dessen Benutzer *admin* und das Kennwort *admin* lautet.

In Produktionsumgebungen sollte die standardmäßige Administratorgruppe geändert werden.

Beachten Sie unbedingt die [Sicherheits-Checkliste](../../help/sites-administering/security-checklist.md).

## Veröffentlichungsumgebung {#publish-environment}

### Mitglied werden {#becoming-a-member}

In der Veröffentlichungsumgebung kann ein Site-Besucher abhängig von den [settings](sites-console.md#user-management) der Community-Site Community-Mitglied werden:

* Wenn die Community-Site privat ist (geschlossen):
   * Nach Einladung
   * Durch Maßnahmen eines Administrators

* Wenn die Community-Site öffentlich ist (geöffnet):
   * Durch Selbstregistrierung
   * Nach Anmeldung über soziale Netzwerke mit Facebook und Twitter

>[!NOTE]
>
>Wenn sich ein Besucher der Site als Mitglied einer offenen Community-Site registriert, wird er automatisch Mitglied anderer offener Community-Sites in derselben Veröffentlichungsumgebung.

### Gruppenrollen veröffentlichen {#publish-group-roles}

| Wenn Gruppenmitglied... | Primäre Rolle |
|---|---|
| Community &lt;*Site-Name*> Mitglieder | Ein Community-Site-Mitglied ist ein registrierter Benutzer. Sie können sich anmelden, ihr Profil ändern, einer offenen Community-Gruppe beitreten, Inhalte in der Community posten, Nachrichten an andere Mitglieder senden und Site-Aktivitäten folgen. |
| Community &lt;*Site-Name* Moderatoren | Ein Community-Site-Moderator ist ein vertrauenswürdiges Community-Mitglied, das in der Lage ist, benutzergenerierte Inhalte entweder in großen Mengen mithilfe der Moderationskonsole oder im Kontext auf der Seite zu moderieren, auf der der Inhalt veröffentlicht wird. |
| Community &lt;*Site-Name* &lt;*Gruppenname*> Mitglieder | Ein Community-Gruppenmitglied ist ein Community-Mitglied, das entweder einer offenen Community-Gruppe beigetreten ist oder zu einer geschlossenen Community-Gruppe eingeladen wurde. Sie verfügen über die Fähigkeiten eines Mitglieds für diese Community-Gruppe innerhalb der Site. |
| Community &lt;*Site-Name* Groupadministrators | Ein Community-Site-Gruppenadministrator ist ein vertrauenswürdiges Community-Mitglied, das zum Erstellen und Verwalten von Untergruppen (Gruppen) innerhalb einer Community-Site zugewiesen ist. Dazu gehört die Möglichkeit, kontextbezogene Moderation bereitzustellen. |
| *Sicherheitsgruppe für berechtigte Mitglieder* | Eine manuell erstellte und gepflegte Benutzergruppe zur Einschränkung der Inhaltserstellung. Siehe [Gruppe privilegierter Mitglieder](#privileged-members-group). |
| Kein | Ein anonymer Site-Besucher, der die Site entdeckt, kann Community-Sites anzeigen und durchsuchen, die einen anonymen Zugriff zulassen. Um an Inhalten teilnehmen und diese veröffentlichen zu können, muss sich der Benutzer selbst registrieren (falls erlaubt) und Mitglied der Community werden. |

### Zuweisen von Mitgliedern zu Veröffentlichungsgruppenrollen {#assigning-members-to-publish-group-roles}

Wenn [eine Community-Site](sites-console.md) in der Autorenumgebung erstellt wird oder [die Site-Eigenschaften geändert werden, können ](sites-console.md#modifying-site-properties) Mitgliedern verschiedene Rollen zugewiesen werden, die in der Veröffentlichungsumgebung ausgeführt werden, z. B. Moderatoren, Gruppenadministratoren, Ressourcenkontakte oder privilegierte Mitglieder.

[Durch die Aktivierung der Tunnel-](sync.md#accessingpublishusersfromauthor) Dienste werden Zuweisungsoptionen von Mitgliedern auf der Veröffentlichungsinstanz anstatt von Benutzern auf der Autoreninstanz angezeigt.

Die ausgewählten Mitglieder werden automatisch der [entsprechenden Gruppe](#publish-group-roles) zugewiesen und ihre Mitgliedschaften werden einbezogen, wenn die Community-Site (erneut) veröffentlicht wird.

### Gruppe privilegierter Mitglieder {#privileged-members-group}

Der Zweck einer Sicherheitsgruppe privilegierter Mitglieder besteht darin, die Erstellung von Inhalten für bestimmte Community-Funktionen auf eine privilegierte Untergruppe der Mitglieder einer Community-Site zu beschränken.

Die Gruppe der privilegierten Mitglieder ist eine Mitgliedergruppe, die mithilfe der [Communities Groups Console](members.md) erstellt und verwaltet wird.

Nachdem eine privilegierte Mitgliedergruppe erstellt wurde und der [Tunneldienst aktiviert ist](sync.md#accessingpublishusersfromauthor), kann die Struktur einer vorhandenen Community-Site [geändert](sites-console.md#modify-structure) sein, um die Konfiguration ihrer Community-Funktionen auf &quot;Berechtigte Mitglieder zulassen&quot;zu ändern und die erstellte Gruppe hinzuzufügen.

Die Community-Funktionen, die die Spezifikation einer oder mehrerer privilegierter Mitgliedergruppen ermöglichen, sind:

* [Blog-Funktion](functions.md#blog-function)  - Um die Erstellung neuer Artikel zu beschränken.
* [Kalenderfunktion](functions.md#calendar-function)  - Um die Erstellung neuer Ereignisse zu beschränken.
* [Forumsfunktion](functions.md#forum-function)  - Schränken Sie die Erstellung neuer Themen ein.
* [QnA-Funktion](functions.md#qna-function)  - Um die Erstellung neuer Fragen zu beschränken.

Wenn eine Community-Funktion nicht gesichert ist (keine privilegierte Mitgliedergruppe zugewiesen ist), dürfen alle Community-Site-Mitglieder Funktionsinhalte (Artikel, Ereignisse, Themen, Fragen) erstellen.

>[!NOTE]
>
>Wenn Sie einen Benutzer zu einer privilegierten Mitgliedergruppe für eine Community-Site hinzufügen, werden ihm nur dann Berechtigungen gewährt, wenn er auch Mitglied derselben Community-Site ist.

## Erstellen von Community-Mitgliedern {#creating-community-members}

### Repository-Speicherort {#repository-location}

Damit bestimmte Funktionen ordnungsgemäß funktionieren, müssen Benutzer und Benutzergruppen mit den entsprechenden Berechtigungen erstellt werden.

Wenn Mitglieder in `/home/users/community` erstellt werden, erben sie die richtigen ACLs, die den Profilen der Mitglieder Leseberechtigungen gewähren.

Auf ähnliche Weise sollten benutzerdefinierte Community-Benutzergruppen (z. B. privilegierte Mitgliedergruppen) in `/home/groups/community` erstellt werden.

Durch Verwendung der Konsolen [Communities-Mitglieder und -Gruppen](members.md) werden Benutzer und Gruppen in diesen Pfaden erstellt.

Um einen benutzerdefinierten Pfad anzugeben, muss die klassische Sicherheitsoberfläche verwendet werden, auf die unter [https://&lt;server>:&lt;port>/useradmin](http://localhost:4503/useradmin) zugegriffen werden kann.

Um Leseberechtigungen für benutzerdefinierte Mitgliederpfade zu gewähren, setzen Sie auf allen Veröffentlichungsinstanzen ACLs ähnlich wie `/home/users/community`:

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

Um die richtigen Berechtigungen für benutzerdefinierte Mitgliedergruppenpfade wie /home/groups/mycompany zu gewähren, legen Sie ACLs auf allen Veröffentlichungsinstanzen ähnlich wie `/home/groups/community` fest:

```xml
<allow
  jcr:primaryType="rep:GrantACE"
  rep:principalName="community-administrators"
  rep:privileges="{Name}[jcr:read]"  />
```

### Konsolen {#consoles}

Es gibt vier separate Konsolen, die nur in der Autorenumgebung verfügbar sind:

| console | Tools, Sicherheit, Benutzer | Tools, Sicherheit, Gruppen | Communities, Mitglieder | Communities, Gruppen |
|----------|-----------------------|------------------------|------------------------------------------------------------|------------------------------------------------------------|
| verwaltet | Benutzer in der Autoreninstanz | Benutzergruppen für Autor | Mitglieder in der Veröffentlichungsumgebung | Mitgliedergruppen in der Veröffentlichungsumgebung |
| erfordert | Administratorberechtigung | Administratorberechtigung | Administratorberechtigungen, Tunneldienst, Benutzersynchronisierung für Veröffentlichungsfarm | Administratorberechtigungen, Tunneldienst, Benutzersynchronisierung für Veröffentlichungsfarm |

### Community-Aktivierungsmanager-Rolle {#community-enablement-manager-role}

Die Möglichkeit für einen Site-Besucher, sich selbst zu registrieren, ist für eine [Aktivierungs-Community](overview.md#enablement-community) normalerweise nicht zulässig, da jedem Mitglied Kosten zugeordnet sind. Aktivierungslernende und -ressourcen werden von einem Benutzer verwaltet, dem die [Rolle](#author-group-roles) von `enablement manager` [während der Site-Erstellung](sites-console.md#enablement) auf der Autoreninstanz zugewiesen wurde (als Mitglied der Gruppe `Community <site-name> Siteenablementmanagers` hinzugefügt). `enablement manager` ist auch für [Zuweisen von Lernressourcen](resources.md) zu Community-Mitgliedern auf der Autoreninstanz verantwortlich.

Für eine bestimmte Community-Site können nur Benutzer ausgewählt werden, die Mitglieder der globalen Gruppe `Community Enablement Managers` sind.`enablement manager`

Um einen Benutzer zu erstellen, dem die Rolle `Community Site Enablement Manager` zugewiesen werden kann, verwenden Sie die Sicherheitskonsole der klassischen Benutzeroberfläche, um den Pfad anzugeben:

Auf der Authoring-Instanz:

1. Mit Administratorrechten angemeldet, navigieren Sie zur Sicherheitskonsole der klassischen Benutzeroberfläche.

   Beispiel: [http://localhost:4502/useradmin](http://localhost:4502/useradmin)

2. Wählen Sie im Menü Bearbeiten **[!UICONTROL Benutzer erstellen]** aus.
3. Füllen Sie das Dialogfeld `Create User` aus.
   * Der Pfad muss `/home/users/community` sein.
4. Wählen Sie **[!UICONTROL Erstellen]**.

   ![create-community-user](assets/create-community-user.png)

* Suchen Sie im linken Bereich nach dem neu erstellten Benutzer und wählen Sie aus, um im rechten Bereich angezeigt zu werden.

   ![community-user](assets/view-community-user.png)

Im linken Bereich:

1. Deaktivieren Sie das Suchfeld und wählen Sie **[!UICONTROL Benutzer ausblenden]** aus.
2. Suchen und ziehen Sie `community-enablementmanagers` auf die Registerkarte **[!UICONTROL Gruppen]** des neuen Benutzers, der im rechten Bereich angezeigt wird.

   ![assign-group](assets/assign-group.png)

### Community-Administratorrolle {#community-administrators-role}

Wie im Diagramm [Autorengruppen-Rollen](#author-group-roles) angegeben, können Mitglieder der Community-Administratorengruppe Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder der Community verbieten) und Inhalte moderieren.

Führen Sie dieselben Schritte aus wie das Erstellen und Zuweisen eines Benutzers zur Rolle von [Aktivierungsmanager](#communitysiteenablementmanagerrole), fügen Sie jedoch die Gruppe c `ommunity-administrators` auf der Registerkarte Gruppen des Benutzers hinzu.

### LDAP-Integration {#ldap-integration}

AEM unterstützt die Verwendung von LDAP für die Authentifizierung von Benutzern sowie die Erstellung von Benutzerkonten. Dies wird unter [Konfigurieren von LDAP mit AEM 6](../../help/sites-administering/ldap-config.md) beschrieben.

Im Folgenden finden Sie einige Konfigurationsdetails für Community-Mitglieder und Mitgliedergruppen.

1. Konfigurieren Sie LDAP für jede AEM Veröffentlichungsinstanz.
2. [Der LDAP-Identitäts-Provider](../../help/sites-administering/ldap-config.md#configuring-the-ldap-identity-provider)

   * Keine besonderen Hinweise

3. [Der Synchronisierungs-Handler](../../help/sites-administering/ldap-config.md#configuring-the-synchronization-handler)

   * Legen Sie die folgenden Eigenschaften fest:

      * **[!UICONTROL User auto membership]**:  `community-<site name>-<uid>-members`
      * **[!UICONTROL Benutzerpfadpräfix]**:  `/community`
      * **[!UICONTROL Group Path Prefix]**:  `/community`

4. [Das externe Anmeldemodul](../../help/sites-administering/ldap-config.md#the-external-login-module)

   * keine besonderen Hinweise

Dies führt dazu, dass Benutzer automatisch der Mitgliedergruppe der Community-Site zugewiesen werden und der Repository-Speicherort `/home/users/community` und `/home/groups/community` lautet, sodass sie die entsprechenden Berechtigungen erben, um das Profil der anderen zu sehen.

* Der Wert `User auto membership` sollte die Eigenschaft `rep:authorizableId` sein, nicht die Eigenschaft `givenName` (Anzeigename) aus dem Profil.

## Synchronisieren von Benutzern zwischen AEM Instanzen {#synchronizing-users-among-aem-instances}

Wenn Sie eine [Veröffentlichungsfarm](topologies.md) verwenden, stellen Sie sicher, dass Benutzer in jeder Veröffentlichungsinstanz denselben Pfad haben, indem Sie die Benutzer zuerst in eine Instanz importieren und [die Benutzersynchronisierung aktivieren](sync.md), um die Benutzer an die anderen Veröffentlichungsinstanzen zu verteilen.

Wenn Sie Benutzergruppen importieren, um sicherzustellen, dass die Benutzergruppen in jeder Veröffentlichungsinstanz denselben Pfad haben, importieren Sie in eine Instanz, dann erstellen Sie [ein Package](../../help/sites-administering/package-manager.md#creating-a-new-package) zum Export und installieren Sie dieses Paket auf allen anderen Veröffentlichungsinstanzen.

Während die Synchronisierung von Benutzergruppen über die Benutzersynchronisierung in einer zukünftigen Version enthalten sein wird, wird derzeit nur die *Mitgliedschaft* einer Benutzergruppe synchronisiert, wenn die Benutzersynchronisierung ausgeführt wird.

## Über Community-Gruppen {#about-community-groups}

Bei der Erörterung von Gruppen gibt es zwei unterschiedliche Themen:

* **[Community-Gruppen](overview.md#communitygroups)**

   Community-Gruppen sind die Untergruppen, die in der Veröffentlichungsumgebung für eine Community-Site erstellt werden können, die die Erstellung von Community-Gruppen unterstützt. Die Erstellung einer Community-Gruppe führt zu mehr Seiten, die der Website hinzugefügt werden, und wird ähnlich wie die ihrer übergeordneten Community-Site verwaltet. Weitere Informationen finden Sie unter [Community-Gruppengrundlagen](essentials-groups.md) für Entwickler und [Community-Gruppe](creating-groups.md) für Autoren.

* **[Mitgliedergruppen](../../help/sites-administering/security.md)**

   Mitgliedergruppen sind die Gruppen, denen Mitglieder angehören können, und werden über die Gruppenkonsole verwaltet. Ein Großteil der Diskussionen auf dieser Seite wurde den Mitgliedsgruppen gewidmet. Die automatisch für eine Community-Site erstellten Mitgliedergruppen, denen *`Community`* vorangestellt ist, können als Community-Gruppe bezeichnet werden. Daher muss der Kontext der Diskussion berücksichtigt werden.
