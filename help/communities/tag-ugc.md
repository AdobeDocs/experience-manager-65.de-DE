---
title: Tagging benutzergenerierter Inhalte
description: Mit Tagging von benutzergenerierten Inhalten (UGC) können Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
role: Admin
exl-id: 1ecb41e5-c959-4380-a5c7-df9fc3a7703a
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 4%

---

# Tagging benutzergenerierter Inhalte {#tagging-user-generated-content}

## Überblick {#overview}

Mit Tagging von benutzergenerierten Inhalten (UGC) können Community-Mitglieder anderen Mitgliedern bei der Suche nach Inhalten helfen.

Normalerweise werden Tags von Autoren und Administratoren in der Autorenumgebung angewendet. Tagging von UGC ist insofern einzigartig, als UGC-Tags von Community-Mitgliedern in der Veröffentlichungsumgebung angewendet werden.

Die Tag-Namespaces und Taxonomien sind für beide Anwendungen identisch.

## Communities-Funktionen {#communities-features}

Zu den AEM Communities-Funktionen, die für Tagging konfiguriert werden können, gehören:

* [Blog](blog-feature.md)
* [Kalender](calendar.md)
* [Dateibibliothek](file-library.md)
* [Forum](forum.md#configuretheaddedforum)
* [Fragen und Antworten](working-with-qna.md)

## Verwalten von Tags {#administering-tags}

Siehe [Verwalten von Tags](../../help/sites-administering/tags.md#tagging-console) zum Erstellen und Verwalten von Tag-Namespaces und Taxonomien.

Entwicklerinformationen finden [ unter ](tag.md)Tag Essentials“.

Siehe [Verwenden von Social Tag Cloud](tagcloud.md) zum Hinzufügen einer Social-Tag-Cloud-Komponente zu einer Seite, um die Suche nach veröffentlichten benutzergenerierten Inhalten mithilfe der angewendeten Tags zu erleichtern.

### Tag-Berechtigungen {#tag-permissions}

Die Standardberechtigungen sind so eingestellt, dass Tag-Namespaces nicht von allen Personen in der Veröffentlichungsumgebung gelesen werden können.

Da Tags auf benutzergenerierten Inhalt (UGC) in der Veröffentlichungsumgebung angewendet werden, muss die Leseberechtigung für Community-Mitglieder aktiviert werden, damit sie Tags auswählen können, die angewendet werden sollen.

Siehe [Festlegen von Tag-](../../help/sites-administering/tags.md#setting-tag-permissions).

Im Folgenden wird dargestellt, wie es in CRXDE aussieht, wenn ein Administrator Leseberechtigungen auf `/etc/tag/discussions` für die `Community Engage Members` anwendet.

![tag-permissions](assets/tag-permissions.png)
