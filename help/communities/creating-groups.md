---
title: Community-Gruppen
seo-title: Community-Gruppen
description: Erstellen von Community-Gruppen
seo-description: Erstellen von Community-Gruppen
uuid: c677d23d-5edb-414c-9013-130c88c2ea52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d94708ee-ca6b-420c-9536-6889d752f9de
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Community-Gruppen{#community-groups}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenumgebung erstellt zu werden.

This ability is present when the [groups function](/help/communities/functions.md#groups-function) is present in the [community site](/help/communities/sites-console.md) structure.

A [community group template](/help/communities/tools-groups.md) provides the design of the community group page when a community group is dynamically created.

Beim Hinzufügen der Gruppenfunktion zur Struktur oder Vorlage einer Community-Site werden eine oder mehrere Gruppenvorlagen ausgewählt. Die folgende Liste mit Gruppenvorlagen steht dem Mitglied oder Autor zur Verfügung, wenn auf der Community-Site dynamisch eine neue Gruppe erstellt wird.

## Neue Gruppe erstellen {#creating-a-new-group}

The ability to create a new community group relies on the existence of a community site which includes the groups function, such as one created from the ` [Reference Site Template](/help/communities/sites.md)`.

The examples that follow use the community site created from the `Reference Site Template` as described in the [Getting Started with AEM Communities](/help/communities/getting-started.md) tutorial.

Diese Seite wird beim Veröffentlichen geladen, wenn der Menüpunkt **Gruppen **ausgewählt ist:

![chlimage_1-85](assets/chlimage_1-85.png)

Wählen Sie das Symbol für **Neue Gruppe** aus, öffnet sich das Bearbeitungsdialogfeld.

Unter der Registerkarte **Einstellungen **stellen Sie die grundlegenden Funktionen der Gruppe bereit:

![chlimage_1-86](assets/chlimage_1-86.png)

* **Gruppenname** Der Titel der Gruppe, der auf der Community-Site angezeigt wird.

* **Beschreibung** Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt wird.

* **Einladen** Eine Auflistung der Mitglieder, die zum Beitritt zur Gruppe eingeladen werden können. Mithilfe der Vervollständigungsfunktion erhalten Sie Vorschläge für einzuladende Mitglieder.

* **Gruppen-URL-Name** Der Name der Gruppenseite, der Teil ihrer URL ist.

* **Gruppe**&#x200B;öffnen Die Auswahl `Open Group` zeigt an, dass ein anonymer Sitebesucher den Inhalt anzeigen kann und die Auswahl aufhebt `Member Only Group`.

* **&quot;Nur Gruppe** auswählen&quot; `Member Only Group` bedeutet, dass nur Mitglieder der Gruppe den Inhalt anzeigen können und die Auswahl aufheben `Open Group`.

Unter der Registerkarte **Vorlage **können Sie aus der Liste der Gruppenvorlagen auswählen, die angegeben wurden, wenn die Funktion &quot;Gruppen&quot;in der Struktur der Community-Site oder in einer Community-Site-Vorlage enthalten war.

![chlimage_1-87](assets/chlimage_1-87.png)

Unter der Registerkarte **Bild **können Sie ein Bild hochladen, das für die Gruppe auf der Seite Gruppen der Community-Site angezeigt wird. Durch das Standard-Stylesheet wird das Bild auf eine Größe von 170 x 90 Pixeln zugeschnitten.

![chlimage_1-88](assets/chlimage_1-88.png)

Wählen Sie die Schaltfläche **Gruppe erstellen** aus, werden die Gruppenseiten basierend auf der ausgewählten Vorlage erstellt. Es wird eine Gruppe für Mitglieder erstellt und die Seite „Gruppen“ wird so aktualisiert, dass die neue Unter-Community aufgeführt wird.

Die Seite „Gruppen“ mit einer neuen Unter-Community mit dem Namen „Focus Group“ (Gesprächsgruppe), für die ein Thumbnail hochgeladen wird, sieht beispielsweise wie folgt aus (der aktuelle Benutzer ist als Community-Gruppenadministrator angemeldet):

![chlimage_1-89](assets/chlimage_1-89.png)

Selecting the `Focus Group` link will open the Focus Group page in the browser, which has an initial appearance based on the chosen template, and includes a submenu underneath the main community site&#39;s menu:

![chlimage_1-90](assets/chlimage_1-90.png)

### Komponente „Community-Gruppenmitgliederliste“{#community-group-member-list-component}

Die `Community Group Member List` Komponente ist für die Verwendung durch Entwickler von Gruppenvorlagen vorgesehen.

### Zusätzliche Informationen {#additional-information}

More information may be found on the [Community Group Essentials](/help/communities/essentials-groups.md) page for developers.

For other information related to community groups, visit [Managing Users and User Groups](/help/communities/users.md).
