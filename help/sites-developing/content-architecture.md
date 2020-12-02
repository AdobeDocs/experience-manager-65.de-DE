---
title: Inhaltsarchitektur
seo-title: Inhaltsarchitektur
description: Tipps zum Erstellen von Inhalten (Hinweis - alles ist Inhalt)
seo-description: Tipps zum Erstellen von Inhalten in Adobe Experience Manager (AEM). (Hinweis - alles ist Inhalt)
uuid: fef2bf0f-70ec-4621-8479-a62b7e1fbc07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: ca46b74c-6114-458b-98c0-2a93abffcdc3
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 59%

---


# Inhaltsarchitektur{#content-architecture}

## Setzen Sie das Modell von David Nuescheler um {#follow-david-s-model}

„David’s Model“ wurde vor Jahren von David Nuescheler entworfen, hat aber bis heute Gültigkeit. Die wichtigsten Grundsätze von David’s Model lauten wie folgt:

* Die Daten werden zuerst angezeigt, die Struktur später. Zumindest gegebenenfalls.
* Steuern Sie die Content-Hierarchie, anstatt sie dem Zufall zu überlassen.
* Arbeitsflächen sind für `clone()`, `merge()` und `update()` verfügbar.
* Bei gleichgeordneten Elementen mit identischem Namen ist Vorsicht geboten.
* Verweise richten mehr Schaden an, als sie nutzen.
* Dateien sind Dateien.
* IDs sind böse.

David’s Model kann im Jackrabbit Wiki unter [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel) gefunden werden.

### Alles ist Inhalt {#everything-is-content}

Sie sollten alles im Repository speichern, anstatt sich auf separate Datenquellen von Dritten wie etwa Datenbanken zu verlassen. Dies bezieht sich auf erstellte Inhalte, Binärdaten wie Bilder, Code und Konfigurationen. Auf diese Weise können Sie mit einem Satz von APIs alle Inhalte verwalten und die Promotion dieser Inhalte durch Replikation steuern. Außerdem profitieren Sie von nur einer einzigen Quelle für Backups, Protokollierung usw.

### Anwenden des Designgrundsatzes „Content Model First“ {#use-the-content-model-first-design-principle}

Wenn Sie eine neue Funktion entwickeln, beginnen Sie immer damit, zunächst die JCR-Inhaltsstruktur zu entwerfen. Befassen Sie sich dann erst mit dem Lesen und Schreiben Ihrer Inhalte mithilfe der standardmäßigen Sling-Servlets. Auf diese Weise können Sie sicherstellen, dass Ihre Implementierung problemlos mit den standardmäßigen Zugriffskontrollen funktioniert, und vermeiden, dass unnötige Servlets im CRUD-Stil generiert werden.

### RESTful statt Panik {#be-restful}

Servlets sollten auf Basis von Ressourcentypen anstelle von Pfaden definiert werden. Dies ermöglicht die Verwendung von JCR-Zugriffskontrollen, die Einhaltung der REST-Prinzipien und die Verwendung des Ressourcen- und Ressourcenauflösers, der uns in der Anforderung zur Verfügung gestellt wird. Dies ermöglicht es uns auch, die Skripten zu ändern, die URLs auf dem Server wiedergeben, ohne URLs vom Client ändern zu müssen, während serverseitige Implementierungsdetails aus dem Client ausgeblendet werden, um zusätzliche Sicherheit zu gewährleisten.

### Vermeiden der Definition neuer Knotentypen {#avoid-defining-new-node-types}

Knotentypen setzen auf einer niedrigen Ebene der Infrastrukturschicht an und die meisten Anforderungen können erfüllt werden, indem ein „sling:resourceType“ verwendet wird, der einem Knotentyp „nt:unstructured“, „oak:Unstructured“, „sling:Folder“ oder „cq:Page“ zugewiesen ist. Node-Typen entsprechen dem Schema im Repository und das Ändern von Node-Typen kann sehr teuer sein.

### Einhalten Sie Namenskonventionen im JCR {#adhere-to-naming-conventions-in-the-jcr}

Durch die Einhaltung von Namenskonventionen wird die Konsistenz der Codebasis erhöht, die Fehler-Inzidenzrate gesenkt und der Arbeitsprozess der beteiligten Entwickler beschleunigt. Die folgenden Übereinkommen werden von der Adobe bei der Entwicklung von AEM verwendet:

* Knotennamen

   * Ausschließliche Verwendung von Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen

* Eigenschaftsnamen

   * Gemischte Groß-/Kleinschreibung, beginnend mit einem Kleinbuchstaben

* Komponenten (JSP/HTML)

   * Ausschließliche Verwendung von Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen

