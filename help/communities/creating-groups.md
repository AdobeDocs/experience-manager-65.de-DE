---
title: Community-Gruppen
seo-title: Community Groups
description: Erstellen von Community-Gruppen
seo-description: Creating community groups
uuid: c677d23d-5edb-414c-9013-130c88c2ea52
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: d94708ee-ca6b-420c-9536-6889d752f9de
docset: aem65
exl-id: edcda6cb-df47-4afe-8a9a-82d8e386fe05
source-git-commit: 1074843a0105df39382b64defe66fc262986b9c9
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 39%

---

# Community-Gruppen {#community-groups}

Mit der Funktion &quot;Community-Gruppen&quot;kann eine Unter-Community von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenumgebung dynamisch auf einer Community-Site erstellt werden.

Diese Fähigkeit ist vorhanden, wenn die [Gruppenfunktion](/help/communities/functions.md#groups-function) ist im [Community-Site](/help/communities/sites-console.md) Struktur.

A [Community-Gruppenvorlage](/help/communities/tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Beim Hinzufügen der Gruppenfunktion zur Struktur oder Vorlage einer Community-Site werden eine oder mehrere Gruppenvorlagen ausgewählt. Die folgende Liste mit Gruppenvorlagen steht dem Mitglied oder Autor zur Verfügung, wenn auf der Community-Site dynamisch eine neue Gruppe erstellt wird.

## Neue Gruppe erstellen {#creating-a-new-group}

Die Möglichkeit, eine neue Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Gruppenfunktion enthält, z. B. eine aus dem [Referenz-Site-Vorlage](/help/communities/sites.md).

Die folgenden Beispiele verwenden die Community-Site, die aus der `Reference Site Template` wie in [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) Tutorial.

Dies ist die Seite, die beim Veröffentlichen geladen wird, wenn die **Gruppen** Menüelement ausgewählt ist:

![new-group](assets/new-group.png)

Wählen Sie das Symbol für **Neue Gruppe** aus, öffnet sich das Bearbeitungsdialogfeld.

Geben Sie auf der Registerkarte **Einstellungen** die grundlegenden Eigenschaften der Gruppe an:

![group-settings](assets/group-settings.png)

* **Gruppenname**

   Der Titel der Gruppe, die auf der Community-Site angezeigt werden soll. Vermeiden Sie Unterstrichzeichen (_) und Suchbegriffe wie Ressourcen und Konfiguration im Gruppennamen.

* **Beschreibung**

   Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt werden soll.

* **Einladen**

   Eine Liste der Mitglieder, die zur Teilnahme an der Gruppe eingeladen werden sollen. Mithilfe der Vervollständigungsfunktion erhalten Sie Vorschläge für einzuladende Mitglieder.

* **Gruppen-URL-Name**

   Der Name der Gruppenseite, die Teil der URL wird.

* **Gruppe öffnen**

   Auswählen `Open Group` gibt an, dass ein anonymer Site-Besucher den Inhalt anzeigen kann, und hebt die Auswahl auf `Member Only Group`.

* **Gruppe nur für Mitglieder**

   Auswählen `Member Only Group` gibt an, dass nur Mitglieder der Gruppe den Inhalt anzeigen können, und hebt die Auswahl auf `Open Group`.

Unter dem **Vorlage** tab bietet die Möglichkeit, aus der Liste von Community-Gruppenvorlagen auszuwählen, die angegeben wurden, als die Gruppenfunktion in der Struktur der Community-Site oder in einer Community-Site-Vorlage enthalten war.

![group-template](assets/group-template.png)

Auf der Registerkarte **Bild** können Sie ein Bild hochladen, das auf der Seite „Gruppen“ der Community-Site angezeigt werden soll. Durch das Standard-Stylesheet wird das Bild auf eine Größe von 170 x 90 Pixeln zugeschnitten.

![group-image](assets/group-image.png)

Wählen Sie die Schaltfläche **Gruppe erstellen** aus, werden die Gruppenseiten basierend auf der ausgewählten Vorlage erstellt. Es wird eine Gruppe für Mitglieder erstellt und die Seite „Gruppen“ wird so aktualisiert, dass die neue Unter-Community aufgeführt wird.

Die Seite „Gruppen“ mit einer neuen Unter-Community mit dem Namen „Focus Group“ (Gesprächsgruppe), für die ein Thumbnail hochgeladen wird, sieht beispielsweise wie folgt aus (der aktuelle Benutzer ist als Community-Gruppenadministrator angemeldet):

![group-page](assets/group-page.png)

Auswählen der `Focus Group` -Link öffnet die Seite &quot;Fokusgruppe&quot;im Browser, die basierend auf der ausgewählten Vorlage ein erstes Erscheinungsbild aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![open-group-page](assets/open-group-page.png)

### Komponente „Community-Gruppenmitgliederliste“ {#community-group-member-list-component}

Die `Community Group Member List` -Komponente ist für Entwickler von Gruppenvorlagen vorgesehen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Community-Gruppengrundlagen](/help/communities/essentials-groups.md) für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
