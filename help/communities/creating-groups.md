---
title: Community-Gruppen
description: Erfahren Sie, wie Sie mit der Funktion „Community-Gruppen“ von autorisierten Benutzenden in Publish und Author dynamisch eine Unter-Community innerhalb einer Community-Site erstellen können.
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

Die Funktion „Community-Gruppen“ bietet die Möglichkeit, dass autorisierte Benutzer (Community-Mitglieder und Autoren) aus der Veröffentlichungs- und Autorenumgebung innerhalb einer Community-Site dynamisch eine Untergemeinschaft erstellen.

Diese Fähigkeit ist vorhanden, wenn [Gruppenfunktion](/help/communities/functions.md#groups-function) in der [Community Site](/help/communities/sites-console.md)-Struktur vorhanden ist.

Eine [Community-Gruppenvorlage](/help/communities/tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Eine oder mehrere Gruppenvorlagen werden für die Gruppenfunktion ausgewählt, wenn die Funktion zur Struktur einer Community-Site oder zu einer Community-Site-Vorlage hinzugefügt wird. Diese Liste von Gruppenvorlagen wird dem Mitglied oder Autor angezeigt, das bzw. der dynamisch eine Gruppe auf der Community-Site erstellt.

## Erstellen einer neuen Gruppe {#creating-a-new-group}

Die Möglichkeit zum Erstellen einer Community-Gruppe hängt davon ab, dass eine Community-Site vorhanden ist, die die Gruppenfunktion enthält, z. B. eine aus der [Referenz-Site-Vorlage](/help/communities/sites.md) erstellte.

In den folgenden Beispielen wird die aus dem `Reference Site Template` erstellte Community-Site verwendet, wie im Tutorial [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) beschrieben.

Dies ist die Seite, die bei der Veröffentlichung geladen wird, wenn **Menüelement „Gruppen** ausgewählt wird:

![new-group](assets/new-group.png)

Wenn Sie das Symbol **Neue Gruppe** auswählen, wird ein Dialogfeld „Bearbeiten“ geöffnet.

Auf der **Einstellungen** geben Sie die grundlegenden Funktionen der Gruppe an:

![group-settings](assets/group-settings.png)

* **Gruppenname**

  Der Titel der Gruppe, die Sie auf der Community-Site anzeigen möchten. Vermeiden Sie Unterstriche (_) und Schlüsselwörter wie Ressourcen und Konfiguration im Gruppennamen.

* **Beschreibung**

  Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt werden soll.

* **Einladen**

  Eine Liste der Mitglieder, die zur Gruppe eingeladen werden sollen. Die Suche mit automatischer Textvervollständigung bietet Vorschläge für Community-Mitglieder, die eingeladen werden können.

* **Gruppen-URL-Name**

  Der Name der Gruppenseite, die Teil der URL wird.

* **Gruppe öffnen**

  Wenn Sie `Open Group` auswählen, zeigt dies an, dass anonyme Site-Besucher den Inhalt anzeigen können, und hebt die Auswahl von `Member Only Group` auf.

* **Gruppe nur für Mitglieder**

  Wenn Sie `Member Only Group` auswählen, können nur Mitglieder der Gruppe den Inhalt anzeigen, und die Auswahl wird `Open Group`.

Auf der Registerkarte **Vorlage** können Sie aus der Liste der Community-Gruppenvorlagen auswählen. Diese Vorlagen wurden angegeben, als die Funktion „Gruppen“ in die Struktur der Community-Site oder in eine Community-Site-Vorlage aufgenommen wurde.

![group-template](assets/group-template.png)

Unter der Registerkarte **Bild** können Sie ein Bild hochladen, das für die Gruppe auf der Seite Gruppen der Community-Site angezeigt werden soll. Das standardmäßige Stylesheet dimensioniert das Bild auf 170 x 90 Pixel.

![group-image](assets/group-image.png)

Wenn Sie **Gruppe erstellen** wählen, werden die Seiten für die Gruppe basierend auf der ausgewählten Vorlage erstellt, und eine Benutzergruppe wird für die Mitgliedschaft erstellt und die Seite Gruppen wird aktualisiert, um die neue Untergemeinschaft anzuzeigen.

Beispielsweise wird die Seite Gruppen mit der neuen Untergemeinschaft „Fokusgruppe“, für die ein Miniaturbild hochgeladen wurde, wie folgt angezeigt (weiterhin als Community-Gruppenadministrator angemeldet):

![group-page](assets/group-page.png)

Wenn Sie auf den Link `Focus Group` klicken, wird die Seite „Fokusgruppe“ im Browser geöffnet, die ein anfängliches Erscheinungsbild basierend auf der ausgewählten Vorlage aufweist und ein Untermenü unter dem Menü der Haupt-Community-Site enthält:

![open-group-page](assets/open-group-page.png)

### Komponente „Community-Gruppenmitgliedsliste“ {#community-group-member-list-component}

Die `Community Group Member List`-Komponente ist für die Verwendung durch Entwickler von Gruppenvorlagen vorgesehen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Community Group Essentials](/help/communities/essentials-groups.md) für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
