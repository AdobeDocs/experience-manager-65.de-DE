---
title: Tagging benutzergenerierter Inhalte
seo-title: Tagging User Generated Content
description: Durch das Tagging benutzergenerierter Inhalte (UGC) können Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen.
seo-description: Tagging of user generated content (UGC) is how community members can help other members search for content
uuid: ce125d7c-6fc1-44c7-9f67-eca6f599d8e3
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1cc8ce66-2c03-44e4-9ddd-8d6944d85c99
role: Admin
exl-id: 1ecb41e5-c959-4380-a5c7-df9fc3a7703a
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 8%

---

# Tagging benutzergenerierter Inhalte {#tagging-user-generated-content}

## Übersicht {#overview}

Das Tagging benutzergenerierter Inhalte (UGC) ist das Mittel, mit dem Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen können.

In der Regel werden Tags von Autoren und Administratoren in der Autorenumgebung angewendet. Das Tagging von UGC ist insofern einzigartig, als UGC-Tags von Community-Mitgliedern in der Veröffentlichungsumgebung angewendet werden.

Die Tag-Namespaces und Taxonomien sind für beide Anwendungen gleich.

## Communities-Funktionen {#communities-features}

Die AEM Communities-Funktionen, die für das Tagging konfiguriert werden können, sind:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md#configuretheaddedforum)
* [Fragen und Antworten](working-with-qna.md)

## Verwalten von Tags {#administering-tags}

Siehe [Verwalten von Tags](../../help/sites-administering/tags.md#tagging-console) zum Erstellen und Verwalten von Tag-Namespaces und Taxonomien.

Siehe [Tag-Grundlagen](tag.md) für Entwicklerinformationen.

Siehe [Verwenden der Social Tag Cloud](tagcloud.md) zum Hinzufügen einer Social Tag Cloud-Komponente zu einer Seite, um die Suche nach veröffentlichten UGC mithilfe der angewendeten Tags zu erleichtern.

### Tag-Berechtigungen {#tag-permissions}

Die Standardberechtigungen sind so eingestellt, dass Tag-Namespaces nicht von allen in der Veröffentlichungsumgebung gelesen werden können.

Da Tags in der Veröffentlichungsumgebung auf UGC angewendet werden, muss die Leseberechtigung für Community-Mitglieder aktiviert sein, damit sie Tags auswählen können, die angewendet werden sollen.

Siehe [Festlegen von Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions).

Folgendes wird in CRXDE angezeigt, wenn ein Administrator Leseberechtigungen auf `/etc/tag/discussions` für die Gruppe `Community Engage Members`.

![tag-permissions](assets/tag-permissions.png)
