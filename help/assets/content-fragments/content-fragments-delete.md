---
title: Inhaltsfragmente – Überlegungen zum Löschen
seo-title: Inhaltsfragmente – Überlegungen zum Löschen
description: Inhaltsfragmente – Überlegungen zum Löschen
seo-description: Inhaltsfragmente – Überlegungen zum Löschen
uuid: e7ac1809-159f-4d02-ad30-dc6c246e8a04
contentOwner: aheimoz
topic-tags: content-fragments
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
discoiquuid: ec21237f-9186-49b4-8039-99df4db7c14a
docset: aem65
feature: Content Fragments
role: Business Practitioner, Administrator
translation-type: tm+mt
source-git-commit: aec4530fa93eacd151ca069c2da5d1bc92408e10
workflow-type: tm+mt
source-wordcount: '460'
ht-degree: 91%

---


# Inhaltsfragmente – Überlegungen zum Löschen{#content-fragments-delete-considerations}

## Berechtigungen – Löschen oder nicht löschen {#permissions-delete-or-not-delete}

Die Möglichkeit, Inhalt zu löschen, ist wirkungsvoll, muss aber mit Bedacht verwendet werden, da viele Branchen die Erteilung dieser Berechtigungen einschränken und kontrollieren müssen. 

In Bezug auf die Berechtigung zum Löschen müssen Inhaltsfragmente aus zwei Perspektiven betrachtet werden:

1. **Das Inhaltsfragment als einzelne Entität.**

   * **Nutzungsszenario:** Ein Benutzer, der ein Inhaltsfragment bearbeiten oder aktualisieren und **ein ganzes Fragment löschen muss**. 
   * **Berechtigungen:**[](/help/sites-administering/security.md#actions)[ Die Berechtigung zum Löschen kann über die Benutzer- und/oder Gruppenverwaltung zugewiesen werden](/help/sites-administering/security.md#managing-permissions).

1. **Die verschiedenen Unterentitäten, die ein Inhaltsfragment bilden. Z. B. Varianten, Unterknoten.** 

   Die grundlegende Funktionsweise des Inhaltsfragmente-Editors erfordert, dass diese temporären Unterelemente gelöscht werden können. Beispielsweise wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

   * **Nutzungsszenario:** Ein Benutzer, der ein Inhaltsfragment bearbeiten oder aktualisieren muss, **aber kein ganzes Fragment löschen darf**.
   * **Berechtigungen:** Siehe [Nur für Editor-Funktionen erforderliche Berechtigungen](/help/assets/content-fragments/content-fragments-delete.md#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Wenn ein Benutzer keine Berechtigungen zum [Löschen](/help/sites-administering/security.md#actions) besitzt, wird der Inhaltsfragmente-Editor im *schreibgeschützten* Modus geöffnet.

>[!NOTE]
>
>Siehe auch [Prüfen von Benutzerverwaltungsvorgängen in AEM](/help/sites-administering/audit-user-management-operations.md).

## Nur für Editor-Funktionen erforderliche Berechtigungen {#permissions-required-for-editor-functionality-only}

Benutzer, die ein Fragment bearbeiten oder aktualisieren müssen, **aber keine kompletten Fragmente löschen dürfen**, benötigen bestimmte Berechtigungen, da die grundlegende Funktionsweise des Inhaltsfragmente-Editors erfordert, dass diese temporären Unterelemente gelöscht werden können.

Beispielsweise wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

>[!NOTE]
>
>Die zum Bearbeiten oder Aktualisieren eines Inhaltsfragments benötigten Rechte zum Löschen erhalten sie mit der Löschberechtigung, die[ über die Benutzer- und/oder Gruppenverwaltung zugewiesen wird](/help/sites-administering/security.md#managing-permissions).

Die zum Bearbeiten oder Aktualisieren eines Fragments benötigten Rechte müssen auf den Knoten, der das Fragment enthält, oder einen entsprechenden übergeordneten Knoten angewendet werden (auf allen Ebenen unter `/content/dam`). Wenn die Zuweisung an einen übergeordneten Knoten erfolgt, werden die Berechtigungen auf allen Knoten in dieser Verzweigung angewendet.

Beispiel: Ein Ordner, der alle Inhaltsfragmente enthält, zum Beispiel:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Die Berechtigungen können auch auf `/content/dam` festgelegt werden, weil hier alle Inhaltsfragmente gespeichert werden.
>
>Allerdings wird die Löschberechtigung dadurch auch für *alle* anderen Asset-Typen gewährt.

Damit einem bestimmten Benutzer und/oder einer bestimmten Benutzergruppe das Bearbeiten oder Aktualisieren von Inhaltsfragmenten erlaubt wird, müssen folgende Voraussetzungen erfüllt werden:

>[!NOTE]
>
>In dieser Liste werden alle erforderlichen Rechte mit Ausnahme der Löschberechtigungen aufgeführt.

* Für die Inhaltsfragmentknoten oder -ordner:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Für den `jcr:content`-Knoten aller Inhaltsfragmente:

   * `jcr:addChildNodes`, `jcr:modifyProperties` und `jcr:removeChildNodes`

* Für alle Knoten unter `jcr:content` aller Inhaltsfragmente:

   * `jcr:addChildNodes`, `jcr:modifyProperties` und `jcr:removeChildNodes`, `jcr:removeNode`

Diese `remove`-Berechtigungen müssen [mit Zugriffskontrolle-Listen innerhalb der CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management) verwaltet werden.

Die Berechtigungen `add` und `modify` können auch in CRXDE Lite oder mithilfe der User Management Console verwaltet werden.

Beispielsweise die Definition der `remove`-Berechtigungen für eine Gruppe `content-authors-no-delete`:

![cf-delete-03](assets/cf-delete-03.png)

