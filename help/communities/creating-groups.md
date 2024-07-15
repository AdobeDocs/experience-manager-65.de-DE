---
title: Community-Gruppen
description: Erfahren Sie, wie Sie mit der Funktion "Community-Gruppen"von autorisierten Benutzern in Publish und der Autoreninstanz dynamisch eine Subcommunity auf einer Community-Site erstellen können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: edcda6cb-df47-4afe-8a9a-82d8e386fe05
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 1%

---

# Community-Gruppen {#community-groups}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht die dynamische Erstellung einer Subcommunity auf einer Community-Site durch autorisierte Benutzer (Community-Mitglieder und Autoren) aus der Veröffentlichungs- und Autorenumgebung.

Diese Funktion ist vorhanden, wenn die [Gruppenfunktion](/help/communities/functions.md#groups-function) in der Struktur der [Community-Site](/help/communities/sites-console.md) vorhanden ist.

Eine [Community-Gruppenvorlage](/help/communities/tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Eine oder mehrere Gruppenvorlagen werden für die Gruppenfunktion ausgewählt, wenn die Funktion zur Struktur einer Community-Site oder zu einer Community-Site-Vorlage hinzugefügt wird. Diese Liste von Gruppenvorlagen wird dem Mitglied oder Autor angezeigt, der dynamisch eine Gruppe aus der Community-Site erstellt.

## Erstellen einer neuen Gruppe {#creating-a-new-group}

Die Möglichkeit, eine Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Gruppenfunktion enthält, z. B. eine aus der [Referenz-Site-Vorlage](/help/communities/sites.md) erstellte.

In den folgenden Beispielen wird die aus dem `Reference Site Template` erstellte Community-Site verwendet, wie im Tutorial [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) beschrieben.

Dies ist die Seite, die bei der Veröffentlichung geladen wird, wenn das Menüelement **Gruppen** ausgewählt ist:

![new-group](assets/new-group.png)

Wenn Sie das Symbol **Neue Gruppe** auswählen, wird ein Dialogfeld zum Bearbeiten geöffnet.

Auf der Registerkarte **Einstellungen** stellen Sie die grundlegenden Funktionen der Gruppe bereit:

![group-settings](assets/group-settings.png)

* **Gruppenname**

  Der Titel der Gruppe, die auf der Community-Site angezeigt werden soll. Vermeiden Sie den Unterstrich (_) und Suchbegriffe wie Ressourcen und Konfiguration im Gruppennamen.

* **Beschreibung**

  Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt werden soll.

* **Einladen**

  Eine Liste der Mitglieder, die zur Gruppe eingeladen werden sollen. Die Suche nach einem Typ bietet Vorschläge für Community-Mitglieder, die eingeladen werden sollen.

* **Gruppen-URL-Name**

  Der Name der Gruppenseite, die Teil der URL wird.

* **Gruppe öffnen**

  Wenn Sie &quot;`Open Group`&quot; auswählen, bedeutet dies, dass ein anonymer Site-Besucher den Inhalt anzeigen kann, und dass die Auswahl von &quot;`Member Only Group`&quot;aufgehoben wird.

* **Gruppe &quot;Nur Mitglied&quot;**

  Wenn Sie &quot;`Member Only Group`&quot; auswählen, bedeutet dies, dass nur Mitglieder der Gruppe den Inhalt anzeigen können, und dass die Auswahl von &quot;`Open Group`&quot;aufgehoben wird.

Auf der Registerkarte **Vorlage** können Sie aus der Liste der Community-Gruppenvorlagen auswählen. Diese Vorlagen wurden angegeben, wenn die Funktion &quot;Gruppen&quot;in die Struktur der Community-Site oder in eine Community-Site-Vorlage aufgenommen wurde.

![group-template](assets/group-template.png)

Auf der Registerkarte **Bild** können Sie ein Bild hochladen, das für die Gruppe auf der Seite &quot;Gruppen&quot;der Community-Site angezeigt werden soll. Das Standard-Stylesheet vergrößert das Bild auf 170 x 90 Pixel.

![group-image](assets/group-image.png)

Durch Auswahl von **Gruppe erstellen** werden die Seiten für die Gruppe auf der Grundlage der ausgewählten Vorlage erstellt. Eine Benutzergruppe wird für die Mitgliedschaft erstellt und die Seite Gruppen wird aktualisiert, um die neue Subcommunity anzuzeigen.

Beispielsweise wird die Seite &quot;Gruppen&quot;mit einer neuen Untergemeinschaft mit dem Namen &quot;Fokusgruppe&quot;, für die eine Miniaturansicht hochgeladen wurde, wie folgt angezeigt (noch als Community-Gruppenadministrator angemeldet):

![group-page](assets/group-page.png)

Durch Auswahl des Links &quot;`Focus Group`&quot; wird die Seite &quot;Fokusgruppe&quot;im Browser geöffnet, die ausgehend von der ausgewählten Vorlage ein erstes Erscheinungsbild aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![open-group-page](assets/open-group-page.png)

### Komponente &quot;Community Group Member List&quot; {#community-group-member-list-component}

Die Komponente `Community Group Member List` ist für Entwickler von Gruppenvorlagen vorgesehen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Entwickler-Seite [Community-Gruppengrundlagen](/help/communities/essentials-groups.md) .

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
