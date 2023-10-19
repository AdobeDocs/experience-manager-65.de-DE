---
title: Community-Gruppen
description: Erfahren Sie, wie Sie mit der Funktion "Community-Gruppen"von autorisierten Benutzern in der Veröffentlichungs- und Autoreninstanz dynamisch eine Subcommunity auf einer Community-Site erstellen können.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: edcda6cb-df47-4afe-8a9a-82d8e386fe05
source-git-commit: b8887b4a6f757352e9dbfdf074c10e9ccd6dbd4f
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 3%

---

# Community-Gruppen {#community-groups}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht die dynamische Erstellung einer Subcommunity auf einer Community-Site durch autorisierte Benutzer (Community-Mitglieder und Autoren) aus der Veröffentlichungs- und Autorenumgebung.

Diese Fähigkeit ist vorhanden, wenn die [Gruppenfunktion](/help/communities/functions.md#groups-function) ist im [Community-Site](/help/communities/sites-console.md) Struktur.

A [Community-Gruppenvorlage](/help/communities/tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Eine oder mehrere Gruppenvorlagen werden für die Gruppenfunktion ausgewählt, wenn die Funktion zur Struktur einer Community-Site oder zu einer Community-Site-Vorlage hinzugefügt wird. Diese Liste von Gruppenvorlagen wird dem Mitglied oder Autor angezeigt, der dynamisch eine Gruppe aus der Community-Site erstellt.

## Erstellen einer neuen Gruppe {#creating-a-new-group}

Die Möglichkeit, eine Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Gruppenfunktion enthält, z. B. eine von der [Referenz-Site-Vorlage](/help/communities/sites.md).

Die folgenden Beispiele verwenden die Community-Site, die aus der `Reference Site Template` wie in [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) Tutorial.

Dies ist die Seite, die beim Veröffentlichen geladen wird, wenn die **Gruppen** Menüelement ausgewählt ist:

![new-group](assets/new-group.png)

Wenn Sie die **Neue Gruppe** -Symbol angezeigt, wird ein Dialogfeld &quot;Bearbeiten&quot;geöffnet.

Unter dem **Einstellungen** -Registerkarte die grundlegenden Funktionen der Gruppe bereitstellen:

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

  Auswählen `Open Group` gibt an, dass ein anonymer Site-Besucher den Inhalt anzeigen kann, und hebt die Auswahl auf `Member Only Group`.

* **Gruppe nur für Mitglieder**

  Auswählen `Member Only Group` gibt an, dass nur Mitglieder der Gruppe den Inhalt anzeigen können, und hebt die Auswahl auf `Open Group`.

Unter dem **Vorlage** aus der Liste der Community-Gruppenvorlagen auswählen. Diese Vorlagen wurden angegeben, wenn die Funktion &quot;Gruppen&quot;in die Struktur der Community-Site oder in eine Community-Site-Vorlage aufgenommen wurde.

![group-template](assets/group-template.png)

Unter dem **Bild** -Registerkarte ein Bild hochladen, das auf der Seite Gruppen der Community-Site für die Gruppe angezeigt werden soll. Das Standard-Stylesheet vergrößert das Bild auf 170 x 90 Pixel.

![group-image](assets/group-image.png)

Durch Auswahl **Gruppe erstellen**, werden die Seiten für die Gruppe auf der Grundlage der ausgewählten Vorlage erstellt und eine Benutzergruppe für die Mitgliedschaft erstellt. Die Seite Gruppen wird aktualisiert, um die neue Subcommunity anzuzeigen.

Beispielsweise wird die Seite &quot;Gruppen&quot;mit einer neuen Untergemeinschaft mit dem Namen &quot;Fokusgruppe&quot;, für die eine Miniaturansicht hochgeladen wurde, wie folgt angezeigt (noch als Community-Gruppenadministrator angemeldet):

![group-page](assets/group-page.png)

Auswählen der `Focus Group` -Link öffnet die Seite &quot;Fokusgruppe&quot;im Browser, die basierend auf der ausgewählten Vorlage ein erstes Erscheinungsbild aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![open-group-page](assets/open-group-page.png)

### Komponente &quot;Community Group Member List&quot; {#community-group-member-list-component}

Die `Community Group Member List` -Komponente ist für Entwickler von Gruppenvorlagen vorgesehen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie unter [Community-Gruppengrundlagen](/help/communities/essentials-groups.md) -Seite für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
