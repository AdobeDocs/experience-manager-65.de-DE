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
source-git-commit: 6337a57ea12f1e026f6c754a083307ce018a1c13
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 40%

---


# Community-Gruppen {#community-groups}

Die Funktion &quot;Community-Gruppen&quot;ermöglicht es einer Unter-Community, dynamisch innerhalb einer Community-Site von autorisierten Benutzern (Community-Mitgliedern und Autoren) aus der Veröffentlichungs- und Autorenversion der Umgebung erstellt zu werden.

Diese Fähigkeit ist vorhanden, wenn die Funktion [Gruppen](/help/communities/functions.md#groups-function) in der Struktur [Community-Site](/help/communities/sites-console.md) vorhanden ist.

Eine [Community-Gruppenvorlage](/help/communities/tools-groups.md) stellt das Design der Community-Gruppenseite bereit, wenn eine Community-Gruppe dynamisch erstellt wird.

Beim Hinzufügen der Gruppenfunktion zur Struktur oder Vorlage einer Community-Site werden eine oder mehrere Gruppenvorlagen ausgewählt. Die folgende Liste mit Gruppenvorlagen steht dem Mitglied oder Autor zur Verfügung, wenn auf der Community-Site dynamisch eine neue Gruppe erstellt wird.

## Neue Gruppe erstellen {#creating-a-new-group}

Die Möglichkeit, eine neue Community-Gruppe zu erstellen, hängt von der Existenz einer Community-Site ab, die die Funktion &quot;Gruppen&quot;enthält, z. B. eine aus der [Referenz-Site-Vorlage](/help/communities/sites.md) erstellte.

Die folgenden Beispiele verwenden die Community-Site, die mit `Reference Site Template` erstellt wurde, wie im Lehrgang [Erste Schritte mit AEM Communities](/help/communities/getting-started.md) beschrieben.

Diese Seite wird beim Veröffentlichen geladen, wenn das Menüelement **Gruppen** ausgewählt ist:

![new-group](assets/new-group.png)

Wählen Sie das Symbol für **Neue Gruppe** aus, öffnet sich das Bearbeitungsdialogfeld.

Geben Sie auf der Registerkarte **Einstellungen** die grundlegenden Eigenschaften der Gruppe an:

![group-settings](assets/group-settings.png)

* **Gruppenname**

   Der Titel der Gruppe, die auf der Community-Site angezeigt werden soll.

* **Beschreibung**

   Eine Beschreibung der Gruppe, die auf der Community-Site angezeigt werden soll.

* **Einladen**

   Eine Liste von Mitgliedern, die zur Teilnahme an der Gruppe eingeladen werden. Mithilfe der Vervollständigungsfunktion erhalten Sie Vorschläge für einzuladende Mitglieder.

* **Gruppen-URL-Name**

   Der Name der Gruppenseite, die Teil der URL wird.

* **Gruppe öffnen**

   Wenn Sie `Open Group` auswählen, wird angezeigt, dass ein anonymer Site-Besucher den Inhalt Ansicht und die Auswahl von `Member Only Group` aufhebt.

* **Gruppe nur für Mitglieder**

   Wenn Sie `Member Only Group` auswählen, wird angezeigt, dass nur Gruppenmitglieder den Inhalt Ansicht haben und die Auswahl von `Open Group` aufgehoben wird.

Auf der Registerkarte **Vorlage** können Sie
Wählen Sie aus der Liste der Community-Gruppenvorlagen, die angegeben wurden, als die Gruppenfunktion in der Community-Site-Struktur oder in einer Community-Site-Vorlage enthalten war.

![group-template](assets/group-template.png)

Auf der Registerkarte **Bild** können Sie ein Bild hochladen, das auf der Seite „Gruppen“ der Community-Site angezeigt werden soll. Durch das Standard-Stylesheet wird das Bild auf eine Größe von 170 x 90 Pixeln zugeschnitten.

![group-image](assets/group-image.png)

Wählen Sie die Schaltfläche **Gruppe erstellen** aus, werden die Gruppenseiten basierend auf der ausgewählten Vorlage erstellt. Es wird eine Gruppe für Mitglieder erstellt und die Seite „Gruppen“ wird so aktualisiert, dass die neue Unter-Community aufgeführt wird.

Die Seite „Gruppen“ mit einer neuen Unter-Community mit dem Namen „Focus Group“ (Gesprächsgruppe), für die ein Thumbnail hochgeladen wird, sieht beispielsweise wie folgt aus (der aktuelle Benutzer ist als Community-Gruppenadministrator angemeldet):

![group-page](assets/group-page.png)

Wenn Sie den Link `Focus Group` auswählen, wird die Seite &quot;Fokusgruppe&quot;im Browser geöffnet. Die Seite hat ein anfängliches Erscheinungsbild basierend auf der ausgewählten Vorlage und enthält ein Untermenü unter dem Menü der Haupt-Community-Site:

![open-group-page](assets/open-group-page.png)

### Komponente „Community-Gruppenmitgliederliste“{#community-group-member-list-component}

Die Komponente `Community Group Member List` ist für die Verwendung durch Entwickler von Gruppenvorlagen vorgesehen.

### Zusätzliche Informationen {#additional-information}

Weitere Informationen finden Sie auf der Seite [Community Group Essentials](/help/communities/essentials-groups.md) für Entwickler.

Weitere Informationen zu Community-Gruppen finden Sie unter [Verwalten von Benutzern und Benutzergruppen](/help/communities/users.md).
