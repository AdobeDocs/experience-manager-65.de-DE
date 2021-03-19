---
title: Tagging von Aktivierungsressourcen
seo-title: Tagging von Aktivierungsressourcen
description: Das Tagging von Ressourcen zur Aktivierung ermöglicht das Filtern von Ressourcen und Lernpfaden, wenn Mitglieder Kataloge durchsuchen
seo-description: Das Tagging von Ressourcen zur Aktivierung ermöglicht das Filtern von Ressourcen und Lernpfaden, wenn Mitglieder Kataloge durchsuchen
uuid: daf8a4f4-486b-498c-99e9-d1533a830e64
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: c012d639-c6e6-4f73-bbd8-78a4baa38c17
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 2%

---


# Tagging von Aktivierungsressourcen {#tagging-enablement-resources}

## Überblick {#overview}

Das Tagging von Ressourcen zur Aktivierung ermöglicht das Filtern von Ressourcen und Lernpfaden, wenn Mitglieder [Kataloge](functions.md#catalog-function) durchsuchen.

Im Wesentlichen:

* [Tag-](../../help/sites-administering/tags.md#creating-a-namespace) Namespace für jeden Katalog erstellen

   * [Tag-Berechtigungen festlegen](../../help/sites-administering/tags.md#setting-tag-permissions)
   * Nur für Community-Mitglieder (geschlossene Community)

      * Lesezugriff für die [Community-Site-Mitgliedsgruppe](users.md#publish-group-roles) zulassen
   * Für jeden Site-Besucher, ob angemeldet oder anonym (Open Community)

      * Lesezugriff für die `Everyone`-Gruppe zulassen
   * [Veröffentlichen der Tags](../../help/sites-administering/tags.md#publishing-tags)



* [Definieren des Gültigkeitsbereichs von Tags für eine Community-Site](sites-console.md#tagging)

   * [Konfigurieren von Katalogen, die in der Struktur der Site vorhanden sind](functions.md#catalog-function)

      * Kann Tags zur Kataloginstanz hinzufügen, um die Liste der Tags zu steuern, die in den UI-Filtern angezeigt werden.
      * Kann [Pre-Filter](catalog-developer-essentials.md#pre-filters) hinzufügen, um die im Katalog enthaltenen Ressourcen einzuschränken.

* [Veröffentlichen der Community-Site](sites-console.md#publishing-the-site)
* [Wenden Sie Tags an, um ](resources.md#create-a-resource) Ressourcen zu aktivieren, damit sie kategorisch gefiltert werden können.
* [Ressourcen für die Aktivierung veröffentlichen](resources.md#publish)

## Community-Site-Tags {#community-site-tags}

Beim Erstellen oder Bearbeiten einer Community-Site legt die Einstellung [Tagging](sites-console.md#tagging) den Umfang der Tags fest, die für Funktionen der Site verfügbar sind, indem eine Untergruppe der vorhandenen Tag-Namensraum ausgewählt wird.

Obwohl Tags jederzeit erstellt und der Community-Site hinzugefügt werden können, wird empfohlen, vorher eine Taxonomie zu entwerfen, ähnlich wie beim Entwerfen einer Datenbank. Weitere Informationen finden Sie unter [Verwenden von Tags](../../help/sites-authoring/tags.md).

Wenn Sie später einer vorhandenen Community-Site Tags hinzufügen, müssen Sie die Bearbeitung speichern, bevor Sie das neue Tag einer Katalogfunktion in der Site-Struktur hinzufügen können.

Für eine Community-Site ist es notwendig, nach der Veröffentlichung der Site und der Veröffentlichung der Tags den Mitgliedern der Community Lesezugriff zu ermöglichen. Siehe [Einstellen der Tag-Berechtigungen](../../help/sites-administering/tags.md#setting-tag-permissions).

Im Folgenden sehen Sie, wie es in CRXDE angezeigt wird, wenn ein Administrator für die Gruppe `Community Enable Members` Leserechte auf `/etc/tags/ski-catalog` anwendet.

![site-tags](assets/site-tags.png)

## Catalog-Tag-Namensraum {#catalog-tag-namespaces}

Die Katalogfunktion verwendet Tags, um sich selbst zu definieren. Wenn Sie die Katalogfunktion auf einer Community-Site konfigurieren, werden die Tag-Namensraum, aus denen Sie auswählen können, durch den Umfang der Tag-Namespace definiert, die für die Community-Site festgelegt werden.

Die Funktion &quot;Katalog&quot;enthält eine Tag-Einstellung, mit der die in der Filter-Benutzeroberfläche für den Katalog aufgelisteten Tags definiert werden. Die Einstellung &quot;Alle Namensraum&quot;bezieht sich auf den Umfang der Tag-Namensraum, die für die Community-Site ausgewählt wurden.

![catalog-Namensraum](assets/catalog-namespace.png)

## Tags auf Aktivierungsressourcen {#applying-tags-to-enablement-resources} anwenden

Aktivierungsressourcen und Lernpfade werden im gesamten Katalog angezeigt, wenn `Show in Catalog` markiert ist. Das Hinzufügen von Tags zu Ressourcen und Lernpfaden ermöglicht das Vorfiltern in bestimmten Katalogen sowie das Filtern in der Katalogbenutzeroberfläche.

Die Einschränkung von Aktivierungsressourcen und Lernpfaden auf bestimmte Kataloge erfolgt durch Erstellen von [Pre-Filtern](catalog-developer-essentials.md#pre-filters).

Die Katalogbenutzeroberfläche ermöglicht es Besuchern, einen Tag-Filter auf die Liste von Ressourcen und Lernpfaden anzuwenden, die in diesem Katalog angezeigt werden.

Der Administrator, der die Tags auf die Aktivierungsressourcen anwendet, muss sich der mit den Katalogen verbundenen Tag-Namensraum sowie der Taxonomie bewusst sein, um ein Untertag für eine verfeinerte Kategorisierung auszuwählen.

Wenn beispielsweise ein `ski-catalog`-Namensraum erstellt und in einem Katalog mit dem Namen `Ski Catalog` festgelegt wurde, könnte er zwei untergeordnete Tags haben: `lesson-1` und `lesson-2`.

Daher werden alle Aktivierungsressourcen mit einem der folgenden Tags versehen:

* Ski-Katalog:Lektion-1
* Ski-Katalog:Lektion-2

wird in `Ski Catalog` angezeigt, nachdem die Aktivierungsressource veröffentlicht wurde.

![basic-info](assets/applytags-basicinfo.png)

## Ansicht des Katalogs bei Veröffentlichung {#viewing-catalog-on-publish}

Sobald alles in der Autorenversion eingerichtet und veröffentlicht wurde, kann die Verwendung des Katalogs zur Suche nach Ressourcen für die Aktivierung in der Umgebung &quot;Veröffentlichen&quot;erfahren werden.

Wenn keine Tag-Namensraum in der Dropdown-Liste angezeigt werden, stellen Sie sicher, dass die Berechtigungen in der Umgebung zum Veröffentlichen korrekt festgelegt wurden.

Wenn Tag-Namensraum hinzugefügt wurden und fehlen, stellen Sie sicher, dass die Tags und die Site erneut veröffentlicht wurden.

Wenn nach der Auswahl eines Tags beim Anzeigen des Katalogs keine Aktivierungsressourcen angezeigt werden, stellen Sie sicher, dass ein Tag aus dem Namensraum des Katalogs bzw. den Katalogs auf die Aktivierungsressource angewendet wurde.

![Ansicht-Katalog](assets/viewcatalog.png)

