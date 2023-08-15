---
title: Inhaltsarchitektur
description: 'Tipps für die Entwicklung einer Inhaltsarchitektur (Hinweis: Alles ist Inhalt.)'
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: bcebbdb4-20b9-4c2d-8a87-013549d686c1
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 45%

---

# Inhaltsarchitektur{#content-architecture}

## David&#39;s Modell folgen {#follow-david-s-model}

David&#39;s Model wurde vor Jahren von David Nuescheler geschrieben, aber die Ideen gelten heute. Die wichtigsten Grundsätze von David&#39;s Model sind:

* Erst die Daten, dann die Struktur. Zumindest gegebenenfalls.
* Gestalten Sie die Inhaltshierarchie, lassen Sie sie nicht passieren.
* Workspaces sind für `clone()`, `merge()` und `update()` vorgesehen.
* Vorsicht vor gleichnamigen Geschwistern.
* Verweise gelten als schädlich.
* Dateien sind Dateien.
* IDs sind zu vermeiden.

David&#39;s Model finden Sie im Jackrabbit Wiki unter [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Alles ist Inhalt {#everything-is-content}

Alles sollte im Repository gespeichert werden, anstatt sich auf separate Datenquellen von Drittanbietern wie Datenbanken zu verlassen. Dies gilt für erstellte Inhalte, Binärdaten wie Bilder, Code und Konfigurationen. Auf diese Weise können wir einen Satz von APIs verwenden, um alle Inhalte zu verwalten und die Promotion dieses Inhalts durch Replikation zu verwalten. Sie erhalten außerdem eine einzige Quelle für Backup, Protokollierung usw.

### Verwenden des Designprinzips &quot;Inhaltsmodell zuerst&quot; {#use-the-content-model-first-design-principle}

Wenn Sie eine neue Funktion entwickeln, beginnen Sie immer damit, zunächst die JCR-Inhaltsstruktur zu entwerfen. Befassen Sie sich dann erst mit dem Lesen und Schreiben Ihrer Inhalte mithilfe der standardmäßigen Sling-Servlets. Auf diese Weise können Sie sicherstellen, dass Ihre Implementierung gut mit vordefinierten Zugriffssteuerungsmechanismen funktioniert, und Sie können vermeiden, unnötige Servlets im CRUD-Stil zu generieren.

### RESTful statt Panik {#be-restful}

Servlets sollten auf Basis von Ressourcentypen anstelle von Pfaden definiert werden. Dies ermöglicht die Verwendung von JCR-Zugriffssteuerungen, die Anwendung der REST-Prinzipien und die Verwendung der Ressource und des Ressourcen-Resolvers, die in der Anforderung bereitgestellt werden. Damit lassen sich außerdem die Skripte ändern, die URLs auf Serverseite rendern, ohne die URLs auf Client-Seite ändern zu müssen, während die serverseitigen Implementierungsdetails vor dem Client verborgen werden, um die Sicherheit zu erhöhen.

### Vermeiden der Definition neuer Knotentypen {#avoid-defining-new-node-types}

Knotentypen setzen auf einer niedrigen Ebene der Infrastrukturschicht an und die meisten Anforderungen können erfüllt werden, indem ein „sling:resourceType“ verwendet wird, der einem Knotentyp „nt:unstructured“, „oak:Unstructured“, „sling:Folder“ oder „cq:Page“ zugewiesen ist. Knotentypen entsprechen dem Schema im Repository, und das Ändern von Knotentypen kann auf der ganzen Strecke teuer sein.

### Einhalten Sie Namenskonventionen im JCR {#adhere-to-naming-conventions-in-the-jcr}

Durch die Einhaltung von Namenskonventionen wird die Konsistenz Ihrer Codebasis erhöht, die Inzidenzrate von Fehlern verringert und die Geschwindigkeit der im System tätigen Entwickler erhöht. Adobe wendet die folgenden Konventionen bei der Entwicklung von AEM an:

* Knotennamen

   * Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen

* Eigenschaftsnamen

   * Sonderfall, beginnend mit einem Kleinbuchstaben

* Komponenten (JSP/HTML)

   * Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen
