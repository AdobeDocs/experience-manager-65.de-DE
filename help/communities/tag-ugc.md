---
title: Tagging benutzergenerierter Inhalte
seo-title: Tagging benutzergenerierter Inhalte
description: Tagging von benutzergenerierten Inhalten (UGC) ist, wie Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen können
seo-description: Tagging von benutzergenerierten Inhalten (UGC) ist, wie Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen können
uuid: ce125d7c-6fc1-44c7-9f67-eca6f599d8e3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1cc8ce66-2c03-44e4-9ddd-8d6944d85c99
translation-type: tm+mt
source-git-commit: 77d00c1d6e94b257aa0533ca88b5f9a12dba0054

---


# Tagging benutzergenerierter Inhalte {#tagging-user-generated-content}

## Übersicht {#overview}

Das Tagging von benutzergenerierten Inhalten (UGC) ist das Mittel, mit dem Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen können.

Normalerweise werden Tags von Autoren und Administratoren in der Authoring-Umgebung angewendet. Das Tagging von UGC ist insofern einzigartig, als UGC-Tags von Community-Mitgliedern in der Veröffentlichungsumgebung angewendet werden.

Die Tag-Namensraum und Taxonomien sind für beide Anwendungen gleich.

## Communities - Funktionen {#communities-features}

Die AEM Communities-Funktionen, die für das Tagging konfiguriert werden können, sind:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md#configuretheaddedforum)
* [Fragen und Antworten](working-with-qna.md)

## Verwalten von Tags {#administering-tags}

Informationen zum Erstellen und Verwalten von Tag-Namensräumen und -Taxonomien finden Sie unter Tags [verwalten](../../help/sites-administering/tags.md#tagging-console) .

Informationen zum Entwickler finden Sie unter [Tag Essentials](tag.md) .

Siehe [Verwenden der Social Tag Cloud](tagcloud.md) zum Hinzufügen einer Social Tag Cloud-Komponente zu einer Seite, um die Suche nach geposteten UGC mithilfe der angewendeten Tags zu erleichtern.

### Tag-Berechtigungen {#tag-permissions}

Die Standardberechtigungen sind so eingestellt, dass Tag-Namensraum nicht von allen in der Umgebung zum Veröffentlichen gelesen werden können.

Da Tags in der Umgebung &quot;Veröffentlichen&quot;auf UGC angewendet werden, muss die Leseberechtigung für Community-Mitglieder aktiviert werden, damit sie Tags auswählen können, die angewendet werden sollen.

See [Setting Tag Permissions](../../help/sites-administering/tags.md#setting-tag-permissions).

Im Folgenden sehen Sie, wie es in CRXDE angezeigt wird, wenn ein Administrator Leserechte `/etc/tag/discussions` für die Gruppe anwendet `Community Engage Members`.

![chlimage_1-74](assets/chlimage_1-74.png)

