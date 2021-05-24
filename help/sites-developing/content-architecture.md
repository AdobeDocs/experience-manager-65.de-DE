---
title: Inhaltsarchitektur
seo-title: Inhaltsarchitektur
description: Tipps für die Architektur Ihres Inhalts (Tipp - alles ist Inhalt)
seo-description: 'Tipps für die Architektur von Inhalten in Adobe Experience Manager (AEM). (Tipp: Alles ist Inhalt.)'
uuid: fef2bf0f-70ec-4621-8479-a62b7e1fbc07
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: ca46b74c-6114-458b-98c0-2a93abffcdc3
exl-id: bcebbdb4-20b9-4c2d-8a87-013549d686c1
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 59%

---

# Inhaltsarchitektur{#content-architecture}

## Setzen Sie das Modell von David Nuescheler um {#follow-david-s-model}

„David’s Model“ wurde vor Jahren von David Nuescheler entworfen, hat aber bis heute Gültigkeit. Die wichtigsten Grundsätze des Modells von David sind:

* Die Daten kommen zuerst, die Struktur später. Zumindest gegebenenfalls.
* Steuern Sie die Content-Hierarchie, anstatt sie dem Zufall zu überlassen.
* Arbeitsbereiche sind für `clone()`, `merge()` und `update()` vorgesehen.
* Bei gleichgeordneten Elementen mit identischem Namen ist Vorsicht geboten.
* Verweise richten mehr Schaden an, als sie nutzen.
* Dateien sind Dateien.
* IDs sind böse.

Das Modell von David finden Sie im Jackrabbit Wiki unter [https://wiki.apache.org/jackrabbit/DavidsModel](https://wiki.apache.org/jackrabbit/DavidsModel).

### Alles ist Inhalt {#everything-is-content}

Sie sollten alles im Repository speichern, anstatt sich auf separate Datenquellen von Dritten wie etwa Datenbanken zu verlassen. Dies bezieht sich auf erstellte Inhalte, Binärdaten wie Bilder, Code und Konfigurationen. Auf diese Weise können Sie mit einem Satz von APIs alle Inhalte verwalten und die Promotion dieser Inhalte durch Replikation steuern. Außerdem profitieren Sie von nur einer einzigen Quelle für Backups, Protokollierung usw.

### Anwenden des Designgrundsatzes „Content Model First“  {#use-the-content-model-first-design-principle}

Wenn Sie eine neue Funktion entwickeln, beginnen Sie immer damit, zunächst die JCR-Inhaltsstruktur zu entwerfen. Befassen Sie sich dann erst mit dem Lesen und Schreiben Ihrer Inhalte mithilfe der standardmäßigen Sling-Servlets. Auf diese Weise können Sie sicherstellen, dass Ihre Implementierung gut mit vordefinierten Zugriffssteuerungsmechanismen funktioniert, und Sie können unnötige Servlets im CRUD-Stil vermeiden.

### RESTful statt Panik {#be-restful}

Servlets sollten auf Basis von Ressourcentypen anstelle von Pfaden definiert werden. Dies ermöglicht die Verwendung von JCR-Zugriffskontrollen, die Einhaltung von REST-Prinzipien und die Verwendung des Ressourcen- und Ressourcen-Resolvers, der uns in der Anfrage zur Verfügung gestellt wird. Dies ermöglicht es uns auch, die Skripte zu ändern, die URLs auf der Serverseite rendern, ohne URLs auf der Clientseite ändern zu müssen, während serverseitige Implementierungsdetails aus dem Client ausgeblendet werden, um zusätzliche Sicherheit zu bieten.

### Vermeiden der Definition neuer Knotentypen {#avoid-defining-new-node-types}

Knotentypen setzen auf einer niedrigen Ebene der Infrastrukturschicht an und die meisten Anforderungen können erfüllt werden, indem ein „sling:resourceType“ verwendet wird, der einem Knotentyp „nt:unstructured“, „oak:Unstructured“, „sling:Folder“ oder „cq:Page“ zugewiesen ist. Knotentypen entsprechen dem Schema im Repository und das Ändern von Knotentypen kann auf der ganzen Straße sehr teuer sein.

### Einhalten Sie Namenskonventionen im JCR {#adhere-to-naming-conventions-in-the-jcr}

Durch die Einhaltung von Namenskonventionen wird die Konsistenz der Codebasis erhöht, die Fehler-Inzidenzrate gesenkt und der Arbeitsprozess der beteiligten Entwickler beschleunigt. Die folgenden Konventionen werden von Adobe bei der Entwicklung von AEM verwendet:

* Knotennamen

   * Ausschließliche Verwendung von Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen

* Eigenschaftsnamen

   * Gemischte Groß-/Kleinschreibung, beginnend mit einem Kleinbuchstaben

* Komponenten (JSP/HTML)

   * Ausschließliche Verwendung von Kleinbuchstaben
   * Worttrennung mithilfe von Bindestrichen
