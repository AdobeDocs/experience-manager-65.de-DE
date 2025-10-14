---
title: Verwalten von Benutzern und Benutzergruppen
description: Benutzer von AEM Communities können sich selbst registrieren und ihre Profile bearbeiten
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 4237085a-d70d-41de-975d-153f58336daa
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1910'
ht-degree: 1%

---

# Verwalten von Benutzern und Benutzergruppen {#managing-users-and-user-groups}

## Überblick {#overview}

In AEM Communities können sich Benutzende in der Veröffentlichungsumgebung selbst registrieren und ihre Profile bearbeiten. Mit den entsprechenden Berechtigungen können sie auch:

* Erstellen Sie Untergruppen innerhalb der Community-Site (siehe [Community-Gruppen](creating-groups.md)).

* [Moderat](moderation.md) benutzergenerierte Inhalte (User Generated Content, UGC).

* [privilegiert](#privileged-members-group) Einträge für Blogs, Kalender, QnA und Foren zu erstellen.

In der Veröffentlichungsumgebung registrierte Benutzer werden im Allgemeinen als *Community-Mitglieder (Mitglieder)) bezeichnet* um sie von *Benutzern* in der Autorenumgebung zu unterscheiden.

Berechtigungen werden gewährt, indem Mitglieder einer der [&#x200B; (Benutzer-)Gruppen zugewiesen werden](#publish-group-roles) die dynamisch erstellt werden, wenn die Community[Site in der Autorenumgebung erstellt &#x200B;](sites-console.md) [geändert &#x200B;](sites-console.md#modifying-site-properties). Wenn Sie in der Autorenumgebung arbeiten, werden Mitglieder von der Veröffentlichungsumgebung aus mithilfe des [Tunnelservice](#tunnel-service) angezeigt.

Standardmäßig sollten in der Veröffentlichungsumgebung erstellte Mitglieder und Mitgliedergruppen nicht in der Autorenumgebung angezeigt werden. In der Autorenumgebung erstellte Benutzer und Benutzergruppen sollen ebenfalls in der Autorenumgebung verbleiben.

Wenn Benutzer in der Autoren- und der Veröffentlichungsumgebung aus derselben Benutzerliste stammen, z. B. aus demselben LDAP-Verzeichnis synchronisiert, werden sie nicht als derselbe Benutzer mit denselben Berechtigungen und Gruppenmitgliedschaften in der Autoren- und der Veröffentlichungsumgebung betrachtet. Die Rolle(n) von Mitgliedern und Benutzern muss (müssen) bei der Veröffentlichung bzw. bei der Autoreninstanz separat festgelegt werden.

Für eine [Veröffentlichungsfarm](topologies.md) müssen Registrierung und Änderungen auf einer Veröffentlichungsinstanz mit anderen Veröffentlichungsinstanzen synchronisiert werden, damit diese auf dieselben Benutzerdaten zugreifen können. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md) in einem Abschnitt, in dem beschrieben wird[&#x200B; was passiert, wenn…](sync.md#what-happens-when).

### Anteilslimits {#contribution-limits}

Zum Schutz vor Spam ist es möglich, die Häufigkeit der Veröffentlichung von Inhalten durch Mitglieder zu begrenzen. Darüber hinaus ist es möglich, die Beiträge neu registrierter Mitglieder automatisch zu begrenzen.

Weitere Informationen finden Sie unter [Obergrenze für Mitgliederbeiträge](limits.md).

### Dynamisch erstellte Benutzergruppen {#dynamically-created-user-groups}

Wenn eine neue Community-Site erstellt wird, werden neue Benutzergruppen dynamisch mit eindeutigen IDs (UID) und Berechtigungen erstellt, die für verschiedene Verwaltungsfunktionen geeignet sind, die zur Verwaltung der Community-Site entweder in der Autorenumgebung (siehe [Autorengruppen-Rollen](#author-group-roles)) oder der Veröffentlichungsumgebung (siehe [Publish-](#publish-group-roles)) erforderlich sind.

Die Namen der Gruppen werden aus dem Namen generiert, der der Site bei der Erstellung [&#x200B; Community-Site &#x200B;](sites-console.md#step13asitetemplate) wurde. Die eindeutigen IDs vermeiden Namenskonflikte für ähnlich benannte Community-Sites und Community-Gruppen auf demselben Server.

Wenn der Site-Name beispielsweise &quot;*Engage*&quot; für eine Site mit dem Titel „Engage“ lautete, wäre eine der erstellten Benutzergruppen:

* Community *Engage*-Mitglieder

## Authoring-Umgebung {#author-environment}

### Tunnelverkehr {#tunnel-service}

Wenn Sie die Autorenumgebung zum [Erstellen von Sites](sites-console.md), [Ändern von Site-](sites-console.md#modifying-site-properties) und [Verwalten von Community-Mitgliedern und &#x200B;](members.md)) verwenden, ist es erforderlich, auf in der Veröffentlichungsumgebung registrierte Benutzer und Benutzergruppen zuzugreifen.

Der Tunnel-Service ermöglicht diesen Zugriff mithilfe des Replikationsagenten auf der Autoreninstanz.

* Weitere Informationen finden Sie [Konfigurationsanweisungen](deploy-communities.md#tunnel-service-on-author) auf der Seite „Bereitstellung“.

Die [Communities-Konsolen und -](members.md)&quot; dienen ausschließlich dem Zweck, Benutzer (Mitglieder) und Benutzergruppen (Mitgliedergruppen) zu verwalten, die nur in der Veröffentlichungsumgebung registriert sind.

Um in der Autorenumgebung registrierte Benutzer und Benutzergruppen zu verwalten, verwenden Sie die [Sicherheitskonsole](../../help/sites-administering/security.md)

### Autorengruppen-Rollen {#author-group-roles}

| Wenn Mitglied der Gruppe… | Primäre Rolle |
|---|---|
| Admins | Die Administratorgruppe besteht aus Systemadministratoren, die über alle Funktionen eines Community-Administrators verfügen und in der Lage sind, die Community-Administratorgruppe zu verwalten. |
| Community-Administratoren | Die Community-Administratorgruppe wird automatisch Mitglied aller Community-Sites und Community-Gruppen, die auf der Site erstellt werden. Ein erstes Mitglied der Community-Administratorgruppe ist die Administratorgruppe. In der Autorenumgebung können Community-Administratoren Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community ausschließen) und Inhalte moderieren. |
| Community &lt;*Site-Name*> SiteContentManager | Der Content Manager der Community-Site kann herkömmliches AEM-Authoring, Inhaltserstellung und Ändern von Seiten für eine Community-Site durchführen. |
| Keine | Ein anonymer Site-Besucher kann nicht auf die Autorenumgebung zugreifen. |

### Systemadministrierende {#system-administrators}

Mitglieder der Gruppe Administratoren sind Systemadministratoren, die in der Lage sind, die Ersteinrichtung einer AEM-Installation sowohl für die Autoren- als auch für die Veröffentlichungsumgebung durchzuführen.

Zu Demonstrations- und Entwicklungszwecken verfügt die Administratorgruppe über ein Mitglied mit der Benutzer-ID *admin* und dem Kennwort *admin*.

In Produktionsumgebungen sollte die Standardadministratorgruppe geändert werden.

Befolgen Sie unbedingt die [Sicherheitscheckliste](../../help/sites-administering/security-checklist.md).

## Veröffentlichungsumgebung {#publish-environment}

### Mitglied werden {#becoming-a-member}

In der Veröffentlichungsumgebung kann ein Site[Besucher je nach den &#x200B;](sites-console.md#user-management) der Community-Site Community-Mitglied werden:

* Wenn die Community-Site privat (geschlossen) ist:
   * Auf Einladung
   * Durch Aktionen eines Administrators

* Wenn die Community-Website öffentlich ist (offen):
   * Durch Selbstregistrierung
   * Anmeldung über Social Media mit Facebook und Twitter

>[!NOTE]
>
>Wenn sich ein Site-Besucher als Mitglied einer Open-Community-Site registriert, wird er automatisch Mitglied anderer Open-Community-Sites in derselben Veröffentlichungsumgebung.

### Publish-Gruppenrollen {#publish-group-roles}

| Wenn Mitglied der Gruppe… | Primäre Rolle |
|---|---|
| Community &lt;*site name*>-Mitglieder | Ein Community-Site-Mitglied ist ein registrierter Benutzer. Sie können sich anmelden, ihr Profil ändern, einer offenen Community-Gruppe beitreten, Inhalte in der Community posten, Nachrichten an andere Mitglieder senden und Site-Aktivitäten verfolgen. |
| Community- &lt;*Site-*> Moderatoren | Ein Community-Website-Moderator ist ein vertrauenswürdiges Community-Mitglied, das UGC entweder massenweise mithilfe der Moderationskonsole oder kontextbezogen auf der Seite moderieren kann, auf der der Inhalt veröffentlicht wird. |
| Community &lt;*Site-Name*> &lt;*Gruppenname*> Mitglieder | Ein Community-Gruppenmitglied ist ein Community-Mitglied, das entweder einer Open Community-Gruppe beigetreten ist oder zu einer geschlossenen Community-Gruppe eingeladen wurde. Sie haben die Fähigkeiten eines Mitglieds dieser Community-Gruppe innerhalb der Website. |
| Community &lt;*Site-Name*>-Gruppenadministratoren | Ein Community-Site-Gruppen-Administrator ist ein vertrauenswürdiges Community-Mitglied, das zum Erstellen und Verwalten von Untergemeinschaften (Gruppen) innerhalb einer Community-Site zugewiesen ist. Eingeschlossen ist die Möglichkeit, kontextbezogene Moderation bereitzustellen. |
| *Sicherheitsgruppe privilegierter Mitglieder* | Eine manuell erstellte und gepflegte Benutzergruppe zum Zweck der Einschränkung der Inhaltserstellung. Siehe [Gruppe privilegierter Mitglieder](#privileged-members-group). |
| Keine | Ein anonymer Site-Besucher, der die Site entdeckt, kann Community-Sites, die den anonymen Zugriff erlauben, anzeigen und durchsuchen. Um teilzunehmen und Inhalte zu posten, muss sich der Benutzer selbst registrieren (sofern erlaubt) und Community-Mitglied werden. |

### Zuweisen von Mitgliedern zu Publish-Gruppenrollen {#assigning-members-to-publish-group-roles}

Beim [Erstellen einer Community](sites-console.md)Site in der Autorenumgebung oder beim [Ändern von Site-Eigenschaften können &#x200B;](sites-console.md#modifying-site-properties) Mitgliedern verschiedene Rollen zugewiesen werden, die in der Veröffentlichungsumgebung ausgeführt werden, z. B. Moderatoren, Gruppenadministratoren, Ressourcenkontakte oder privilegierte Mitglieder.

[Aktivieren des Tunneldienstes](sync.md#accessingpublishusersfromauthor) führt dazu, dass Zuweisungsoptionen von Mitgliedern in der Veröffentlichungsinstanz anstelle von Benutzern in der Autoreninstanz angezeigt werden.

Die ausgewählten Mitglieder werden automatisch der [entsprechenden Gruppe“ zugewiesen &#x200B;](#publish-group-roles) ihre Mitgliedschaften werden bei der (erneuten) Veröffentlichung der Community-Site einbezogen.

### Gruppe privilegierter Mitglieder {#privileged-members-group}

Der Zweck einer Sicherheitsgruppe mit privilegierten Mitgliedern besteht darin, die Erstellung von Inhalten für bestimmte Community-Funktionen auf eine privilegierte Untergruppe der Mitglieder einer Community-Site zu beschränken.

Die Gruppe privilegierter Mitglieder ist eine Mitgliedergruppe, die mithilfe der [Communities-Konsole“ erstellt und &#x200B;](members.md) wird.

Nachdem eine Gruppe privilegierter Mitglieder erstellt wurde und der [Tunneldienst aktiviert](sync.md#accessingpublishusersfromauthor) kann die Struktur einer vorhandenen Community-Site [geändert](sites-console.md#modify-structure) um die Konfiguration ihrer Community-Funktionen auf „Privilegierte Mitglieder zulassen“ zu bearbeiten und die erstellte Gruppe hinzuzufügen.

Die Gemeinschaftsfunktionen, die die Spezifikation eines oder mehrerer privilegierter Mitgliedergruppen ermöglichen, sind:

* [Blog-Funktion](functions.md#blog-function) - Zum Beschränken der Erstellung neuer Artikel.
* [Kalenderfunktion](functions.md#calendar-function) - Zum Beschränken der Erstellung neuer Ereignisse.
* [Forum-Funktion](functions.md#forum-function) - Zum Beschränken der Erstellung neuer Themen.
* [QnA-Funktion](functions.md#qna-function) - Zum Beschränken der Erstellung neuer Fragen.

Wenn eine Community-Funktion nicht gesichert ist (keine privilegierte Mitgliedergruppe zugewiesen), dürfen alle Mitglieder der Community-Site Funktionsinhalte erstellen (Artikel, Ereignisse, Themen, Fragen).

>[!NOTE]
>
>Wenn Sie einen Benutzer zu einer Gruppe privilegierter Mitglieder für eine Community-Site hinzufügen, erhält er nur dann Berechtigungen zum Erstellen von Berechtigungen, wenn er auch Mitglied derselben Community-Site ist.

## Erstellen von Community-Mitgliedern {#creating-community-members}

### Repository-Speicherort {#repository-location}

Damit bestimmte Funktionen ordnungsgemäß funktionieren, müssen Benutzer und Benutzergruppen mit den entsprechenden Berechtigungen erstellt werden.

Wenn Mitglieder in `/home/users/community` erstellt werden, erben sie die richtigen ACLs, die den Profilen der Mitglieder Leseberechtigungen erteilen.

Ebenso sollten benutzerdefinierte Community-Benutzergruppen (z. B. privilegierte Mitgliedergruppen) in `/home/groups/community` erstellt werden.

Mit der [Communities-Mitglieder- und -](members.md)&quot; werden Benutzer und Gruppen in diesen Pfaden erstellt.

Um einen benutzerdefinierten Pfad anzugeben, muss die klassische Sicherheits-Benutzeroberfläche verwendet werden, auf die unter [https://&lt;server>:&lt;port>/useradmin](http://localhost:4503/useradmin) zugegriffen werden kann.

Um Leseberechtigungen für benutzerdefinierte Mitgliedspfade zu erteilen, legen Sie auf allen Veröffentlichungsinstanzen ACLs ähnlich `/home/users/community` fest:

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

Um die richtigen Berechtigungen für benutzerdefinierte Mitgliedschaftsgruppenpfade wie &quot;/home/groups/mycompany“ zu gewähren, legen Sie auf allen Veröffentlichungsinstanzen ACLs ähnlich `/home/groups/community` fest:

```xml
<allow
  jcr:primaryType="rep:GrantACE"
  rep:principalName="community-administrators"
  rep:privileges="{Name}[jcr:read]"  />
```

### Konsolen {#consoles}

Es gibt vier separate Konsolen, die nur in der Autorenumgebung verfügbar sind:

| Bedienpult | Tools, Sicherheit, Benutzer | Tools, Sicherheit, Gruppen | Communities, Mitglieder | Communities, Gruppen |
|----------|-----------------------|------------------------|------------------------------------------------------------|------------------------------------------------------------|
| verwaltet | Benutzer in der Autoreninstanz | Benutzergruppen für Autor | Mitglieder bei Veröffentlichung | Mitgliedergruppen bei der Veröffentlichung |
| Erfordert | Admin-Berechtigung | Admin-Berechtigung | Administratorberechtigung, Tunneldienst, Benutzersynchronisierung für Veröffentlichungsfarm | Administratorberechtigung, Tunneldienst, Benutzersynchronisierung für Veröffentlichungsfarm |

### Community-Administratorrolle {#community-administrators-role}

Wie im Diagramm [Autorengruppen-Rollen](#author-group-roles) angegeben, können Mitglieder der Community-Administratorgruppe Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community ausschließen) und Inhalte moderieren.

Führen Sie dieselben Schritte aus wie das Erstellen und Zuweisen eines Benutzers für die Rolle des Aktivierungs-Managers, fügen Sie jedoch eine `ommunity-administrators` Gruppe auf der Registerkarte Gruppen des Benutzers hinzu.

### LDAP-Integration {#ldap-integration}

AEM unterstützt die Verwendung von LDAP für die Authentifizierung von Benutzern und die Erstellung von Benutzerkonten. Dies wird unter &quot;[&#x200B; von LDAP mit AEM 6“ &#x200B;](../../help/sites-administering/ldap-config.md).

Im Folgenden finden Sie einige Konfigurationsdetails, die speziell für Community-Mitglieder und Mitgliedergruppen gelten.

1. Konfigurieren Sie LDAP für jede AEM-Veröffentlichungsinstanz.
2. [Der LDAP-Identitäts-Provider](../../help/sites-administering/ldap-config.md#configuring-the-ldap-identity-provider)

   * Keine besonderen Anweisungen

3. [Der Synchronisierungs-Handler](../../help/sites-administering/ldap-config.md#configuring-the-synchronization-handler)

   * Legen Sie die folgenden Eigenschaften fest:

      * **[!UICONTROL Automatische Benutzermitgliedschaft]**: `community-<site name>-<uid>-members`
      * **[!UICONTROL Benutzerpfad-Präfix]**: `/community`
      * **[!UICONTROL Gruppenpfadpräfix]**: `/community`

4. [Das externe Anmeldemodul](../../help/sites-administering/ldap-config.md#the-external-login-module)

   * Keine besonderen Anweisungen

Dies führt dazu, dass Benutzende automatisch der Mitgliedergruppe der Community-Site zugewiesen werden und der Repository-Speicherort `/home/users/community` und `/home/groups/community` wird. Sie übernehmen dann die entsprechenden Berechtigungen, um das Profil des jeweils anderen zu sehen.

* Der `User auto membership` sollte die `rep:authorizableId`-Eigenschaft sein, nicht die `givenName` (Anzeigename) aus dem Profil.

## Synchronisieren von Benutzern zwischen AEM-Instanzen {#synchronizing-users-among-aem-instances}

Stellen Sie bei Verwendung einer [Veröffentlichungsfarm](topologies.md) sicher, dass Benutzende auf jeder Veröffentlichungsinstanz denselben Pfad haben, indem Sie die Benutzenden zuerst in eine Instanz importieren und [Benutzersynchronisierung aktivieren](sync.md) um Sling die Benutzenden an die anderen Veröffentlichungsinstanzen zu verteilen.

Wenn Sie Benutzergruppen importieren, um sicherzustellen, dass die Benutzergruppen auf jeder Veröffentlichungsinstanz denselben Pfad haben, importieren Sie in eine Instanz und [&#x200B; Sie dann „Paket erstellen](../../help/sites-administering/package-manager.md#creating-a-new-package) für den Export und installieren Sie dieses Paket auf allen anderen Veröffentlichungsinstanzen.

Während die Synchronisierung von Benutzergruppen über die Benutzersynchronisierung in einer zukünftigen Version enthalten ist, wird derzeit nur die *Mitgliedschaft* einer Benutzergruppe synchronisiert, wenn die Benutzersynchronisierung ausgeführt wird.

## Über Community-Gruppen {#about-community-groups}

Bei der Gruppendiskussion gibt es zwei unterschiedliche Themen:

* **[Community-Gruppen](overview.md#communitygroups)**

  Community-Gruppen sind die Untergruppen, die in der Veröffentlichungsumgebung für eine Community-Site erstellt werden können, die die Erstellung von Community-Gruppen unterstützt. Die Erstellung einer Community-Gruppe führt dazu, dass der Website mehr Seiten hinzugefügt werden und diese ähnlich wie die übergeordnete Community-Site verwaltet werden. Weitere Informationen finden Sie unter [Community Group Essentials](essentials-groups.md) für Entwickler und [Community Group](creating-groups.md) für Autoren.

* **[Mitgliedergruppen](../../help/sites-administering/security.md)**

  Mitgliedergruppen sind die Gruppen, denen Mitglieder angehören können und die über die Gruppenkonsole verwaltet werden. Ein Großteil der Diskussionen auf dieser Seite ist den Mitgliedergruppen gewidmet. Die Mitgliedergruppen, die automatisch für eine Community-Site erstellt werden und denen das Präfix *`Community`* vorangestellt wird, können als Community-Gruppe bezeichnet werden. Daher muss der Kontext der Diskussion berücksichtigt werden.
