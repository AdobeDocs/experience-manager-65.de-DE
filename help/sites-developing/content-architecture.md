---
title: Inhaltsarchitektur
description: 'Tipps für die Entwicklung einer Inhaltsarchitektur (Hinweis: Alles ist Inhalt.)'
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: bcebbdb4-20b9-4c2d-8a87-013549d686c1
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 100%

---

# Inhaltsarchitektur{#content-architecture}

## David Nüschelers Modell als Vorbild {#follow-david-s-model}

Das Model von David Nüscheler („David’s Model“) wurde vor Jahren entworfen, hat aber bis heute Gültigkeit. Die wichtigsten Grundsätze des Modells lauten:

* Erst die Daten, dann die Struktur. Zumindest gegebenenfalls.
* Steuern Sie die Inhaltshierarchie, anstatt sie dem Zufall zu überlassen.
* Workspaces sind für `clone()`, `merge()` und `update()` vorgesehen.
* Bei gleichgeordneten Elementen mit identischem Namen ist Vorsicht geboten.
* Verweise richten mehr Schaden an, als sie nutzen.
* Dateien sind Dateien.
* IDs sind zu vermeiden.

Sie finden das Modell von David Nüscheler auf Jackrabbit Wiki unter [http://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Alles ist Inhalt {#everything-is-content}

Sie sollten alles im Repository speichern, anstatt sich auf separate Datenquellen von Dritten wie etwa Datenbanken zu verlassen. Dies gilt für erstellte Inhalte und Binärdaten wie Bilder, Code und Konfigurationen. Auf diese Weise können Sie mit einem Satz von APIs alle Inhalte verwalten und die Promotion dieser Inhalte durch Replikation steuern. Außerdem profitieren Sie von nur einer einzigen Quelle für Backups, Protokollierung usw.

### Anwenden des Design-Grundsatzes „Content Model First“ {#use-the-content-model-first-design-principle}

Wenn Sie eine neue Funktion entwickeln, beginnen Sie immer damit, zunächst die JCR-Inhaltsstruktur zu entwerfen. Befassen Sie sich dann erst mit dem Lesen und Schreiben Ihrer Inhalte mithilfe der standardmäßigen Sling-Servlets. Auf diese Weise können Sie sicherstellen, dass Ihre Implementierung problemlos mit Standardmechanismen für die Zugriffssteuerung funktioniert. Darüber hinaus lässt sich die Erstellung überflüssiger CRUD-Servlets vermeiden.

### RESTful statt Panik {#be-restful}

Servlets sollten auf Basis von Ressourcentypen anstelle von Pfaden definiert werden. Dies ermöglicht die Verwendung von JCR-Zugriffssteuerungen, die Anwendung der REST-Prinzipien und die Verwendung der Ressource und des Ressourcen-Resolvers, die in der Anforderung bereitgestellt werden. Damit lassen sich außerdem die Skripte ändern, die URLs auf Serverseite rendern, ohne die URLs auf Client-Seite ändern zu müssen, während die serverseitigen Implementierungsdetails vor dem Client verborgen werden, um die Sicherheit zu erhöhen.

### Vermeiden der Definition neuer Knotentypen {#avoid-defining-new-node-types}

Knotentypen setzen auf einer niedrigen Ebene der Infrastrukturschicht an und die meisten Anforderungen können erfüllt werden, indem ein „sling:resourceType“ verwendet wird, der einem Knotentyp „nt:unstructured“, „oak:Unstructured“, „sling:Folder“ oder „cq:Page“ zugewiesen ist. Knotentypen entsprechen dem Schema im Repository, wobei sich das Ändern von Knotentypen im weiteren Verlauf als kostspielig erweisen kann.

### Einhalten Sie Namenskonventionen im JCR {#adhere-to-naming-conventions-in-the-jcr}

Durch die Einhaltung von Namenskonventionen wird die Konsistenz der Code-Basis erhöht, die Fehler-Inzidenzrate gesenkt und der Arbeitsprozess der beteiligten Entwickelnden beschleunigt. Adobe wendet die folgenden Konventionen bei der Entwicklung von AEM an:

* Knotennamen

   * Ausschließliche Verwendung von Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen

* Eigenschaftsnamen

   * Binnenmajuskeln, beginnend mit einem Kleinbuchstaben

* Komponenten (JSP/HTML)

   * Ausschließliche Verwendung von Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen
