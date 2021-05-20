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
exl-id: edcda6cb-df47-4afe-8a9a-82d8e386fe05
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 40%

---

# Community-Gruppen {#community-groups}

Mit der Funktion &quot;Community-Gruppen&quot;kann eine Unter-Community von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenumgebung dynamisch auf einer Community-Site erstellt werden.

Diese Möglichkeit besteht, wenn die [Gruppenfunktion](/help/communities/functions.md#groups-function) in der [Community-Site](/help/communities/sites-console.md)-Struktur vorhanden ist.

Eine [Community-Gruppenvorlage](/help/communities/tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Beim Hinzufügen der Gruppenfunktion zur Struktur oder Vorlage einer Community-Site werden eine oder mehrere Gruppenvorlagen ausgewählt. Die folgende Liste mit Gruppenvorlagen steht dem Mitglied oder Autor zur Verfügung, wenn auf der Community-Site dynamisch eine neue Gruppe erstellt wird.

## Neue Gruppe erstellen {#creating-a-new-group}

Die Möglichkeit, eine neue Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Gruppenfunktion enthält, z. B. eine, die über die [Referenz-Site-Vorlage](/help/communities/sites.md) erstellt wurde.

Die folgenden Beispiele verwenden die Community-Site, die aus `Reference Site Template` erstellt wurde, wie im Tutorial [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) beschrieben.

Dies ist die Seite, die bei der Veröffentlichung geladen wird, wenn das Menüelement **Gruppen** ausgewählt wird:

![new-group](assets/new-group.png)

Wählen Sie das Symbol für **Neue Gruppe** aus, öffnet sich das Bearbeitungsdialogfeld.

Geben Sie auf der Registerkarte **Einstellungen** die grundlegenden Eigenschaften der Gruppe an:

![group-settings](assets/group-settings.png)

* **Gruppenname**

   Der Titel der Gruppe, die auf der Community-Site angezeigt werden soll.

* **Beschreibung**

   Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt werden soll.

* **Einladen**

   Eine Liste der Mitglieder, die zur Teilnahme an der Gruppe eingeladen werden sollen. Mithilfe der Vervollständigungsfunktion erhalten Sie Vorschläge für einzuladende Mitglieder.

* **Gruppen-URL-Name**

   Der Name der Gruppenseite, die Teil der URL wird.

* **Gruppe öffnen**

   Wenn Sie `Open Group` auswählen, bedeutet dies, dass ein anonymer Site-Besucher den Inhalt anzeigen kann und die Auswahl von `Member Only Group` aufgehoben wird.

* **Gruppe nur für Mitglieder**

   Wenn Sie `Member Only Group` auswählen, wird angegeben, dass nur Mitglieder der Gruppe den Inhalt anzeigen können, und die Auswahl von `Open Group` wird aufgehoben.

Auf der Registerkarte **Vorlage** können Sie
Wählen Sie aus der Liste der Community-Gruppenvorlagen aus, die festgelegt wurden, als die Gruppenfunktion in der Struktur der Community-Site oder in einer Community-Site-Vorlage enthalten war.

![group-template](assets/group-template.png)

Auf der Registerkarte **Bild** können Sie ein Bild hochladen, das auf der Seite „Gruppen“ der Community-Site angezeigt werden soll. Durch das Standard-Stylesheet wird das Bild auf eine Größe von 170 x 90 Pixeln zugeschnitten.

![group-image](assets/group-image.png)

Wählen Sie die Schaltfläche **Gruppe erstellen** aus, werden die Gruppenseiten basierend auf der ausgewählten Vorlage erstellt. Es wird eine Gruppe für Mitglieder erstellt und die Seite „Gruppen“ wird so aktualisiert, dass die neue Unter-Community aufgeführt wird.

Die Seite „Gruppen“ mit einer neuen Unter-Community mit dem Namen „Focus Group“ (Gesprächsgruppe), für die ein Thumbnail hochgeladen wird, sieht beispielsweise wie folgt aus (der aktuelle Benutzer ist als Community-Gruppenadministrator angemeldet):

![group-page](assets/group-page.png)

Wenn Sie den Link `Focus Group` auswählen, wird die Seite &quot;Fokusgruppe&quot;im Browser geöffnet, die basierend auf der ausgewählten Vorlage ein anfängliches Erscheinungsbild aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![open-group-page](assets/open-group-page.png)

### Komponente „Community-Gruppenmitgliederliste“{#community-group-member-list-component}

Die Komponente `Community Group Member List` ist für Entwickler von Gruppenvorlagen vorgesehen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Community-Gruppengrundlagen](/help/communities/essentials-groups.md) für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
