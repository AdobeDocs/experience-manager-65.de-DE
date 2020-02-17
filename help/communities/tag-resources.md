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
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Tagging von Aktivierungsressourcen {#tagging-enablement-resources}

## Überblick {#overview}

Das Tagging von Ressourcen zur Aktivierung ermöglicht das Filtern von Ressourcen und Lernpfaden, wenn Mitglieder [Kataloge](functions.md#catalog-function)durchsuchen.

Im Wesentlichen:

* [Tag-Namespace](../../help/sites-administering/tags.md#creating-a-namespace) für jeden Katalog erstellen

   * [Tag-Berechtigungen festlegen](../../help/sites-administering/tags.md#setting-tag-permissions)

      * Nur für Community-Mitglieder (geschlossene Community)

         * Lesezugriff für die Mitgliedergruppe der [Community-Site zulassen](users.md#publish-group-roles)
      * Für jeden Site-Besucher, ob angemeldet oder anonym (Open Community)

         * Lesezugriff für die `Everyone`Gruppe zulassen
   * [Veröffentlichen der Tags](../../help/sites-administering/tags.md#publishing-tags)



* [Definieren des Gültigkeitsbereichs von Tags für eine Community-Site](sites-console.md#tagging)

   * [Konfigurieren von Katalogen, die in der Struktur der Site vorhanden sind](functions.md#catalog-function)

      * Kann Tags zur Kataloginstanz hinzufügen, um die Liste der Tags zu steuern, die in den UI-Filtern angezeigt werden
      * Kann [Vorfilter](catalog-developer-essentials.md#pre-filters)hinzufügen, um die im Katalog enthaltenen Ressourcen einzuschränken

* [Veröffentlichen der Community-Site](sites-console.md#publishing-the-site)
* [Tags zur Aktivierung von Ressourcen](resources.md#create-a-resource) anwenden, damit diese kategorisch gefiltert werden können
* [Ressourcen für die Aktivierung veröffentlichen](resources.md#publish)

## Community-Site-Tags {#community-site-tags}

Beim Erstellen oder Bearbeiten einer Community-Site legt die Einstellung[ für das ](sites-console.md#tagging)Tagging den Umfang der Tags fest, die für Funktionen der Site verfügbar sind, indem eine Untergruppe der vorhandenen Tag-Namespaces ausgewählt wird.

Obwohl Tags jederzeit erstellt und der Community-Site hinzugefügt werden können, wird empfohlen, vorher eine Taxonomie zu entwerfen, ähnlich wie beim Entwerfen einer Datenbank. Weitere Informationen finden Sie unter [Verwenden von Tags](../../help/sites-authoring/tags.md).

Wenn Sie später einer vorhandenen Community-Site Tags hinzufügen, müssen Sie die Bearbeitung speichern, bevor Sie das neue Tag einer Katalogfunktion in der Site-Struktur hinzufügen können.

Für eine Community-Site ist es notwendig, nach der Veröffentlichung der Site und der Veröffentlichung der Tags den Mitgliedern der Community Lesezugriff zu ermöglichen. See [Setting Tag Permissions](../../help/sites-administering/tags.md#setting-tag-permissions).

Im Folgenden sehen Sie, wie es in CRXDE angezeigt wird, wenn ein Administrator Leserechte `/etc/tags/ski-catalog` für die Gruppe anwendet `Community Enable Members`.

![chlimage_1-420](assets/chlimage_1-420.png)

## Katalog-Tag-Namespaces {#catalog-tag-namespaces}

Die Katalogfunktion verwendet Tags, um sich selbst zu definieren. Wenn Sie die Katalogfunktion auf einer Community-Site konfigurieren, werden die Tag-Namespaces, aus denen Sie auswählen können, durch den Umfang der Tag-Namespace definiert, die für die Community-Site festgelegt werden.

Die Funktion &quot;Katalog&quot;enthält eine Tag-Einstellung, mit der die in der Filter-Benutzeroberfläche für den Katalog aufgelisteten Tags definiert werden. Die Einstellung &quot;Alle Namespaces&quot;bezieht sich auf den Umfang der Tag-Namespaces, die für die Community-Site ausgewählt wurden.

![chlimage_1-421](assets/chlimage_1-421.png)

## Tags auf Aktivierungsressourcen anwenden {#applying-tags-to-enablement-resources}

Aktivierungsressourcen und Lernpfade werden in allen Katalogen angezeigt, wenn diese markiert `Show in Catalog` sind. Das Hinzufügen von Tags zu Ressourcen und Lernpfaden ermöglicht das Vorfiltern in bestimmten Katalogen sowie das Filtern in der Katalogbenutzeroberfläche.

Die Beschränkung von Ressourcen für die Aktivierung und Lernpfaden auf bestimmte Kataloge erfolgt durch Erstellen von [Vorfiltern](catalog-developer-essentials.md#pre-filters).

Die Katalogbenutzeroberfläche ermöglicht es Besuchern, einen Tag-Filter auf die Liste der Ressourcen und Lernpfade anzuwenden, die in diesem Katalog angezeigt werden.

Der Administrator, der die Tags auf die Aktivierungsressourcen anwendet, muss sich der mit den Katalogen verknüpften Tag-Namespaces sowie der Taxonomie bewusst sein, um ein Untertag für eine verfeinerte Kategorisierung auszuwählen.

Wenn beispielsweise ein `ski-catalog` Namespace für einen Katalog mit dem Namen erstellt und festgelegt wurde `Ski Catalog`, könnte er zwei untergeordnete Tags haben: `lesson-1` und `lesson-2`.

Daher werden alle Aktivierungsressourcen mit einem der folgenden Tags versehen:

* Ski-Katalog:
* Ski-Katalog:Lektion-1
* Ski-Katalog:Lektion-2

angezeigt wird, `Ski Catalog` nachdem die Aktivierungsressource veröffentlicht wurde.

![chlimage_1-422](assets/chlimage_1-422.png)

## Ansicht des Katalogs bei der Veröffentlichung {#viewing-catalog-on-publish}

Sobald alles in der Autorenumgebung eingerichtet und veröffentlicht wurde, kann die Verwendung des Katalogs zur Suche nach Ressourcen zur Aktivierung in der Veröffentlichungsumgebung erleben.

Wenn keine Tag-Namespaces in der Dropdown-Liste angezeigt werden, stellen Sie sicher, dass die Berechtigungen in der Veröffentlichungsumgebung korrekt festgelegt wurden.

Wenn Tag-Namespaces hinzugefügt wurden und fehlen, stellen Sie sicher, dass die Tags und die Site erneut veröffentlicht wurden.

Wenn nach der Auswahl eines Tags beim Anzeigen des Katalogs keine Aktivierungsressourcen angezeigt werden, stellen Sie sicher, dass ein Tag aus dem (den) Namespace(en) des Katalogs, der (die) auf die Aktivierungsressource angewendet wird, vorhanden ist.

![chlimage_1-423](assets/chlimage_1-423.png)

