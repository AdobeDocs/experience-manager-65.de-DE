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

## Übersicht {#overview}

In AEM Communities können sich Benutzer in der Veröffentlichungsumgebung selbst registrieren und ihre Profile bearbeiten. Mit den entsprechenden Berechtigungen können sie auch:

* Erstellen Sie Untergruppen auf der Community-Site (siehe [Community-Gruppen](creating-groups.md)).

* [Moderieren](moderation.md) benutzergenerierte Inhalte (UGC).

* be [privilegiert](#privileged-members-group) , um Einträge für Blogs, Kalender, Fragen und Antworten und Foren zu erstellen.

In der Veröffentlichungsumgebung registrierte Benutzer werden im Allgemeinen als *Community-Mitglieder (Mitglieder)* , um sie von *Benutzer* in der Autorenumgebung.

Berechtigungen werden gewährt, indem Mitglieder einem der [Mitglieds- (Benutzer-)Gruppen](#publish-group-roles) dynamisch erstellt, wenn die Community-Site [created](sites-console.md) oder [modifiziert](sites-console.md#modifying-site-properties) aus der Autorenumgebung. Bei der Arbeit in der Autorenumgebung sind Mitglieder in der Veröffentlichungsumgebung über die [Tunneldienst](#tunnel-service).

Standardmäßig sollten in der Veröffentlichungsumgebung erstellte Mitglieder und Mitgliedergruppen nicht in der Autorenumgebung angezeigt werden. Benutzer und Benutzergruppen, die in der Autorenumgebung erstellt wurden, sind auf ähnliche Weise dazu bestimmt, in der Autorenumgebung zu bleiben.

Wenn Benutzer in der Autoren- und Veröffentlichungsumgebung aus derselben Benutzerliste stammen, z. B. aus demselben LDAP-Ordner synchronisiert, werden sie nicht als derselbe Benutzer mit denselben Berechtigungen und Gruppenmitgliedschaften in der Autoren- und Veröffentlichungsumgebung betrachtet. Die Rolle(en) der Mitglieder und Benutzer muss (müssen) je nach Bedarf separat in der Veröffentlichungs- und Autoreninstanz festgelegt werden.

Für [Veröffentlichungsfarm](topologies.md), Registrierung und Änderungen, die an einer Veröffentlichungsinstanz vorgenommen wurden, müssen mit anderen Veröffentlichungsinstanzen synchronisiert werden, damit sie Zugriff auf dieselben Benutzerdaten haben. Weitere Informationen finden Sie unter [Benutzersynchronisierung](sync.md), der einen Abschnitt mit einer Beschreibung enthält [Was passiert, wenn...](sync.md#what-happens-when).

### Anteilslimits {#contribution-limits}

Zum Schutz vor Spam ist es möglich, die Häufigkeit der Veröffentlichung von Inhalten durch die Mitglieder zu begrenzen. Außerdem ist es möglich, die Beiträge neu registrierter Mitglieder automatisch zu begrenzen.

Weitere Informationen finden Sie unter [Beitragsgrenzen der Mitgliedstaaten](limits.md).

### Dynamisch erstellte Benutzergruppen {#dynamically-created-user-groups}

Wenn eine neue Community-Site erstellt wird, werden neue Benutzergruppen dynamisch mit eindeutigen IDs (UID) und Berechtigungen erstellt, die für verschiedene Verwaltungsfunktionen geeignet sind, die zum Verwalten der Community-Site entweder in der Autorenumgebung erforderlich sind (siehe [Autorengruppen-Rollen](#author-group-roles)) oder der Veröffentlichungsumgebung (siehe [Gruppenrollen veröffentlichen](#publish-group-roles)).

Die Namen der Gruppen werden aus dem Namen generiert, der der Site während der [Community-Site-Erstellung](sites-console.md#step13asitetemplate). Die eindeutigen IDs vermeiden Namenskonflikte für ähnlich benannte Community-Sites und Community-Gruppen auf demselben Server.

Wenn der Site-Name beispielsweise &quot;*interagieren*&quot;für eine Site mit dem Namen &quot;Interagieren&quot;eine der erstellten Benutzergruppen lautet:

* Community *Engage* Mitglieder

## Authoring-Umgebung {#author-environment}

### Tunneldienst {#tunnel-service}

Bei Verwendung der Autorenumgebung zu [Erstellen von Sites](sites-console.md), [Ändern von Site-Eigenschaften](sites-console.md#modifying-site-properties) und [Community-Mitglieder und Mitgliedergruppen verwalten](members.md), ist es erforderlich, auf Benutzer und Benutzergruppen zuzugreifen, die in der Veröffentlichungsumgebung registriert sind.

Der Tunneldienst stellt diesen Zugriff mithilfe des Replikationsagenten auf der Autoreninstanz bereit.

* Weitere Informationen finden Sie unter [Konfigurationsanweisungen](deploy-communities.md#tunnel-service-on-author) auf der Bereitstellungsseite.

Die [Communitys-Mitglieder und -Gruppenkonsolen](members.md) ausschließlich zur Verwaltung von Benutzern (Mitgliedern) und Benutzergruppen (Mitgliedergruppen) dienen, die nur in der Veröffentlichungsumgebung registriert sind.

Um in der Autorenumgebung registrierte Benutzer und Benutzergruppen zu verwalten, verwenden Sie die [Sicherheitskonsole](../../help/sites-administering/security.md)

### Autorengruppen-Rollen {#author-group-roles}

| Wenn Gruppenmitglied... | Primäre Rolle |
|---|---|
| Admins | Die Gruppe Administratoren besteht aus Systemadministratoren, die über alle Fähigkeiten eines Community-Administrators und die Fähigkeit verfügen, die Gruppe Community-Administratoren zu verwalten. |
| Community-Administratoren | Die Gruppe Community-Administratoren wird automatisch Mitglied aller Community-Sites und aller auf der Site erstellten Community-Gruppen. Die Administratorgruppe ist ein erstmaliges Mitglied der Gruppe Community-Administratoren . In der Autorenumgebung können Community-Administratoren Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder aus der Community verbieten) und Inhalte moderieren. |
| Community &lt;*Site-Name*> Sitecontentmanager | Der Community-Site-Inhaltsmanager kann herkömmliche AEM erstellen, Seiten für eine Community-Site erstellen und ändern. |
| Ohne | Ein anonymer Site-Besucher kann nicht auf die Autorenumgebung zugreifen. |

### Systemadministrierende {#system-administrators}

Mitglieder der Administratorgruppe sind Systemadministratoren, die die Ersteinrichtung einer AEM für die Autoren- und Veröffentlichungsumgebung durchführen können.

Zu Demonstrations- und Entwicklungszwecken verfügt die Administratorgruppe über ein Mitglied, dessen Benutzer *admin* und das Kennwort *admin*.

In Produktionsumgebungen sollte die standardmäßige Administratorgruppe geändert werden.

Befolgen Sie unbedingt die [Sicherheitscheckliste](../../help/sites-administering/security-checklist.md).

## Veröffentlichungsumgebung {#publish-environment}

### Mitgliedschaft {#becoming-a-member}

In der Veröffentlichungsumgebung, je nach [settings](sites-console.md#user-management) der Community-Site kann ein Site-Besucher Mitglied der Community werden:

* Wenn die Community-Site privat ist (geschlossen):
   * Nach Einladung
   * Von einem Administrator

* Wenn die Community-Site öffentlich ist (geöffnet):
   * Durch Selbstregistrierung
   * Durch Anmeldung in sozialen Netzwerken mit Facebook und Twitter

>[!NOTE]
>
>Wenn sich ein Besucher der Site als Mitglied einer offenen Community-Site registriert, wird er automatisch Mitglied anderer offener Community-Sites in derselben Veröffentlichungsumgebung.

### Gruppenrollen veröffentlichen {#publish-group-roles}

| Wenn Gruppenmitglied... | Primäre Rolle |
|---|---|
| Community &lt;*Site-Name*> Mitglieder | Ein Community-Site-Mitglied ist ein registrierter Benutzer. Sie können sich anmelden, ihr Profil ändern, einer offenen Community-Gruppe beitreten, Inhalte in der Community posten, Nachrichten an andere Mitglieder senden und Site-Aktivitäten folgen. |
| Community &lt;*Site-Name*> Moderatoren | Ein Community-Site-Moderator ist ein vertrauenswürdiges Community-Mitglied, das in der Lage ist, benutzergenerierte Inhalte entweder in großen Mengen mithilfe der Moderationskonsole oder im Kontext auf der Seite zu moderieren, auf der der Inhalt veröffentlicht wird. |
| Community &lt;*Site-Name*> &lt;*Gruppenname*> Mitglieder | Ein Community-Gruppenmitglied ist ein Community-Mitglied, das entweder einer offenen Community-Gruppe beigetreten ist oder zu einer geschlossenen Community-Gruppe eingeladen wurde. Sie verfügen über die Fähigkeiten eines Mitglieds für diese Community-Gruppe innerhalb der Site. |
| Community &lt;*Site-Name*> Gruppenadministratoren | Ein Community-Site-Gruppenadministrator ist ein vertrauenswürdiges Community-Mitglied, das zum Erstellen und Verwalten von Untergruppen (Gruppen) innerhalb einer Community-Site zugewiesen ist. Dazu gehört die Möglichkeit, kontextbezogene Moderation bereitzustellen. |
| *Sicherheitsgruppe für berechtigte Mitglieder* | Eine manuell erstellte und gepflegte Benutzergruppe zur Einschränkung der Inhaltserstellung. Siehe [Gruppe privilegierter Mitglieder](#privileged-members-group). |
| Ohne | Ein anonymer Site-Besucher, der die Site entdeckt, kann Community-Sites anzeigen und durchsuchen, die einen anonymen Zugriff zulassen. Um Inhalte zu veröffentlichen und zu beteiligen, muss sich der Benutzer selbst registrieren (falls erlaubt) und Mitglied der Community werden. |

### Zuweisen von Mitgliedern zu Veröffentlichungsgruppenrollen {#assigning-members-to-publish-group-roles}

Wann [Erstellen einer Community-Site](sites-console.md) in der Autorenumgebung oder wenn [Ändern der Site-Eigenschaften,](sites-console.md#modifying-site-properties) Mitgliedern können verschiedene Rollen zugewiesen werden, die in der Veröffentlichungsumgebung ausgeführt werden, z. B. Moderatoren, Gruppenadministratoren, Ressourcenkontakte oder privilegierte Mitglieder.

[Aktivieren des Tunneldienstes](sync.md#accessingpublishusersfromauthor) führt dazu, dass Zuweisungsoptionen von Mitgliedern auf der Veröffentlichungsinstanz anstatt von Benutzern auf der Autoreninstanz angezeigt werden.

Die ausgewählten Mitglieder werden automatisch dem [geeignete Gruppe](#publish-group-roles) und ihre Mitgliedschaften werden eingeschlossen, wenn die Community-Site (erneut) veröffentlicht wird.

### Gruppe privilegierter Mitglieder {#privileged-members-group}

Der Zweck einer Sicherheitsgruppe privilegierter Mitglieder besteht darin, die Erstellung von Inhalten für bestimmte Community-Funktionen auf eine privilegierte Untergruppe der Mitglieder einer Community-Site zu beschränken.

Die Gruppe der privilegierten Mitglieder ist eine Mitgliedergruppe, die mithilfe der [Communities-Gruppenkonsole](members.md).

Nachdem eine privilegierte Mitgliedergruppe erstellt wurde, und mit der [Tunneldienst aktiviert](sync.md#accessingpublishusersfromauthor), kann die Struktur einer vorhandenen Community-Site [modifiziert](sites-console.md#modify-structure) , um die Konfiguration seiner Community-Funktionen zu &quot;Zulassen von privilegierten Mitgliedern&quot;zu bearbeiten und die erstellte Gruppe hinzuzufügen.

Die Community-Funktionen, die die Spezifikation einer oder mehrerer privilegierter Mitgliedergruppen ermöglichen, sind:

* [Blog-Funktion](functions.md#blog-function) - Beschränkung der Erstellung neuer Artikel.
* [Kalenderfunktion](functions.md#calendar-function) - Beschränkung der Erstellung neuer Ereignisse.
* [Forumsfunktion](functions.md#forum-function) - Die Erstellung neuer Themen wird eingeschränkt.
* [QnA-Funktion](functions.md#qna-function) - Beschränkung der Erstellung neuer Fragen.

Wenn eine Community-Funktion nicht gesichert ist (keine privilegierte Mitgliedergruppe zugewiesen ist), dürfen alle Community-Site-Mitglieder Funktionsinhalte (Artikel, Ereignisse, Themen, Fragen) erstellen.

>[!NOTE]
>
>Wenn Sie einen Benutzer zu einer privilegierten Mitgliedergruppe für eine Community-Site hinzufügen, werden ihm nur dann Berechtigungen gewährt, wenn er auch Mitglied derselben Community-Site ist.

## Erstellen von Community-Mitgliedern {#creating-community-members}

### Repository-Speicherort {#repository-location}

Damit bestimmte Funktionen ordnungsgemäß funktionieren, müssen Benutzer und Benutzergruppen mit den entsprechenden Berechtigungen erstellt werden.

Wenn Mitglieder in erstellt werden `/home/users/community`, erben sie die richtigen ACLs, die Leseberechtigungen für die Profile der Mitglieder gewähren.

Auf ähnliche Weise sollten benutzerdefinierte Community-Benutzergruppen (z. B. privilegierte Mitgliedergruppen) in erstellt werden. `/home/groups/community`.

Verwenden der [Communitys-Mitglieder und -Gruppenkonsolen](members.md) erstellt Benutzer und Gruppen in diesen Pfaden.

Um einen benutzerdefinierten Pfad anzugeben, müssen Sie die klassische Sicherheitsbenutzeroberfläche verwenden, auf die Sie unter [https://&lt;server>:&lt;port>/useradmin](http://localhost:4503/useradmin).

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

Um die richtigen Berechtigungen für benutzerdefinierte Mitgliedergruppenpfade wie /home/groups/mycompany zu gewähren, setzen Sie ACLs auf allen Veröffentlichungsinstanzen ähnlich wie `/home/groups/community`:

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

### Community-Administratorrolle {#community-administrators-role}

Wie im Abschnitt [Autorengruppen-Rollen](#author-group-roles) -Diagramm verwenden, können Mitglieder der Community-Administratoren-Gruppe Community-Sites erstellen, Sites verwalten, Mitglieder verwalten (sie können Mitglieder der Community verbieten) und Inhalte moderieren.

Führen Sie dieselben Schritte aus wie beim Erstellen und Zuweisen eines Benutzers zur Rolle des Aktivierungsmanagers, fügen Sie jedoch c hinzu. `ommunity-administrators` auf der Registerkarte Gruppen des Benutzers.

### LDAP-Integration {#ldap-integration}

AEM unterstützt die Verwendung von LDAP zur Authentifizierung von Benutzern und zur Erstellung von Benutzerkonten. Weitere Informationen finden Sie unter [Konfigurieren von LDAP mit AEM 6](../../help/sites-administering/ldap-config.md).

Im Folgenden finden Sie einige Konfigurationsdetails für Community-Mitglieder und Mitgliedergruppen.

1. Konfigurieren Sie LDAP für jede AEM Veröffentlichungsinstanz.
2. [Der LDAP-Identitäts-Provider](../../help/sites-administering/ldap-config.md#configuring-the-ldap-identity-provider)

   * Keine besonderen Hinweise

3. [Der Synchronisierungs-Handler](../../help/sites-administering/ldap-config.md#configuring-the-synchronization-handler)

   * Legen Sie die folgenden Eigenschaften fest:

      * **[!UICONTROL Automatische Benutzermitgliedschaft]**: `community-<site name>-<uid>-members`
      * **[!UICONTROL Benutzerpfadpräfix]**: `/community`
      * **[!UICONTROL Group Path Prefix]**: `/community`

4. [Das externe Anmeldemodul](../../help/sites-administering/ldap-config.md#the-external-login-module)

   * keine besonderen Hinweise

Dadurch werden Benutzer automatisch der Mitgliedergruppe der Community-Site und dem Repository-Speicherort zugewiesen `/home/users/community` und `/home/groups/community`, damit sie die entsprechenden Berechtigungen erben, um das Profil der anderen Person zu sehen.

* Die `User auto membership` Wert: `rep:authorizableId` -Eigenschaft, nicht die `givenName` (Anzeigename) aus dem Profil.

## Synchronisieren von Benutzern zwischen AEM Instanzen {#synchronizing-users-among-aem-instances}

Bei der Verwendung von [Veröffentlichungsfarm](topologies.md)stellen Sie sicher, dass die Benutzer in jeder Veröffentlichungsinstanz denselben Pfad haben, indem Sie die Benutzer zuerst in eine Instanz importieren und [Aktivieren der Benutzersynchronisierung](sync.md) , um die Benutzer an die anderen Veröffentlichungsinstanzen zu verteilen.

Wenn Sie Benutzergruppen importieren, um sicherzustellen, dass die Benutzergruppen in jeder Veröffentlichungsinstanz denselben Pfad haben, importieren Sie in eine Instanz, und dann [Package erstellen](../../help/sites-administering/package-manager.md#creating-a-new-package) für den Export und installieren Sie dieses Paket auf allen anderen Veröffentlichungsinstanzen.

Während die Synchronisierung von Benutzergruppen über die Benutzersynchronisierung in einer zukünftigen Version enthalten sein wird, wird derzeit nur die *Abo* einer Benutzergruppe wird synchronisiert, wenn die Benutzersynchronisierung ausgeführt wird.

## Über Community-Gruppen {#about-community-groups}

Bei der Erörterung von Gruppen gibt es zwei unterschiedliche Themen:

* **[Community-Gruppen](overview.md#communitygroups)**

  Community-Gruppen sind die Untergruppen, die in der Veröffentlichungsumgebung für eine Community-Site erstellt werden können, die die Erstellung von Community-Gruppen unterstützt. Die Erstellung einer Community-Gruppe führt zu mehr Seiten, die der Website hinzugefügt werden, und wird ähnlich wie die ihrer übergeordneten Community-Site verwaltet. Weitere Informationen unter [Community-Gruppengrundlagen](essentials-groups.md) für Entwickler und [Community-Gruppe](creating-groups.md) für Autoren.

* **[Mitgliedergruppen](../../help/sites-administering/security.md)**

  Mitgliedergruppen sind die Gruppen, denen Mitglieder angehören können, und werden über die Gruppenkonsole verwaltet. Ein Großteil der Diskussionen auf dieser Seite wurde den Mitgliedsgruppen gewidmet. Die Mitgliedergruppen, die automatisch für eine Community-Site erstellt werden und mit dem Präfix *`Community`* als Gemeinschaftsgruppe bezeichnet werden, muss daher der Kontext der Diskussion berücksichtigt werden.
