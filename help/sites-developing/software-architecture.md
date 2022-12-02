---
title: Software-Architektur
seo-title: Software Architecture
description: Best Practices für die Entwicklung der Architektur Ihrer Software
seo-description: Best practices for architecting your software
uuid: a557f6ca-c3f1-486e-a45e-6e1f986fab41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 92971747-1c74-4917-b5a0-7b79b3ae1e68
exl-id: cd4f3b4c-5488-4ca7-9c1e-b4c819fda8e8
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 94%

---

# Software-Architektur{#software-architecture}

## Auslegen des Designs auf Upgrades {#design-for-upgrades}

Bei der Erweiterung der OOTB-Verhaltensweisen ist es wichtig, Upgrades zu berücksichtigen. Nehmen Sie Anpassungen immer im Verzeichnis /apps vor und überlagern Sie entweder die entsprechenden Knoten im Verzeichnis /libs oder verwenden Sie „sling:resourceSuperType“, um das Standardverhalten zu erweitern. Zwar können Änderungen erforderlich sein, um neue AEM-Versionen zu unterstützen, doch die neue Version sollte Ihre Anpassungen nicht überschreiben, wenn diese Best Practice befolgt wird.

### Wiederverwenden von Vorlagen und Komponenten, sofern möglich {#reuse-template-and-components-when-possible}

Dadurch lässt sich das Erscheinungsbild der Website vereinheitlichen und die Code-Pflege vereinfachen. Wenn eine neue Vorlage benötigt wird, stellen Sie sicher, dass sie von einer gemeinsam verwendeten Basisvorlage erweitert wird, sodass globale Anforderungen wie die clientlib-Einbindung an zentraler Stelle kodiert werden können. Wenn eine neue Komponente benötigt wird, sollten Sie versuchen, eine bestehenden Komponente zu erweitern.

### Gestalten von Vorlagen-Designs {#design-template-designs}

Indem Sie die Komponenten definieren, die in den einzelnen Absatzsystemen auf der Seite enthalten sein können, können Sie Einfluss darauf nehmen, dass das Erscheinungsbild der Seite einheitlich ist. Durch die Beschränkung des Zugriffs auf das Design auf Seiten können &quot;Superautoren&quot;die zulässigen Komponenten pro Seite ändern, ohne dass die Entwickler eingreifen, und gleichzeitig sicherstellen, dass die anderen Autoren die Unternehmensstandards einhalten.

### Entwickeln von SOLID-Architekturen {#develop-a-solid-architecture}

SOLID ist ein Akronym, das fünf architektonische Prinzipien beschreibt, die Sie einhalten sollten:

* **Single Responsibility**-Prinzip: Jedes Modul, jede Klasse, jede Methode usw. sollte nur eine einzige Verantwortung haben.
* **O** pen/Closed-Prinzip: Module sollten sowohl offen (für Erweiterungen) als auch geschlossen (für Änderungen) sein.
* **L** iskovsches Substitutionsprinzip: Typen sollten durch ihre Untertypen ersetzbar sein.
* **Interface Segregation-Prinzip:** Clients sollten nicht gezwungen werden, von Methoden abzuhängen, die sie nicht verwenden.
* **D** ependency Inversion-Prinzip: Module höherer Ebenen sollten nicht von Modulen niedriger Ebenen abhängig sein. Beide sollten von Abstraktionen abhängen. Abstraktionen sollten nicht von Details abhängen. Details sollten von Abstraktionen abhängen.

Durch die Berücksichtigung dieser fünf Prinzipien lässt sich ein System erzielen, in dem eine strikte Trennung der Anliegen gegeben ist.

>[!TIP]
>
>SOLID ist ein häufig verwendetes Konzept der objektorientierten Programmierung und jedes Element wird in der Fachliteratur umfassend diskutiert.
>
>Dies ist nur eine kurze Zusammenfassung, um Sie darauf aufmerksam zu machen. Wir empfehlen, sich intensiver mit diesen Konzepten zu beschäftigen.

### Befolgen des Robustheitsgrundsatzes {#follow-the-robustness-principle}

Der Robustheitsgrundsatz besagt, dass Sie streng sein sollten, bei dem was Sie senden, und offen bei dem, was Sie von anderen akzeptieren. Das heißt, wenn Sie Nachrichten an Dritte senden, sollten Sie sich unbedingt an die jeweiligen Spezifikationen halten. Wenn Sie aber Nachrichten von Dritten empfangen, sollten Sie nicht konforme Nachrichten akzeptieren, solange die Bedeutung der Nachricht klar ist.

### Implementierung von Sammlungen in eigenen Modulen {#implement-spikes-in-their-own-modules}

Sammlungen und Test-Code sind ein integraler Bestandteil jeder agilen Software-Implementierung, allerdings sollten Sie sicherstellen, dass sie nicht ohne entsprechende Kontrolle in Ihre Produktions-Code-Basis gelangen. Entsprechend empfiehlt es sich, Sammlungen in ihrem eigenen Modul zu erstellen.

### Implementieren von Datenmigrationsskripten in ihrem eigenen Modul {#implement-data-migration-scripts-in-their-own-module}

Bei Datenmigrationsskripten handelt es sich zwar um Produktions-Code, doch diese werden in der Regel nur einmal beim ersten Start einer Site ausgeführt. Nach der Live-Schaltung der Site wird dieser folglich zu totem Code. Um sicherzustellen, dass Sie keinen Implementierungs-Code erstellen, der von den Migrationsskripten abhängig ist, sollten diese in einem eigenen Modul implementiert werden. Dies ermöglicht es Ihnen auch, diesen Code sofort nach dem Start zu entfernen und zu löschen, wodurch toter Code aus dem System entfernt wird.

### Befolgen veröffentlichter Maven-Konventionen in POM-Dateien {#follow-published-maven-conventions-in-pom-files}

Apache hat unter [https://maven.apache.org/developers/conventions/code.html](https://maven.apache.org/developers/conventions/code.html) Stilkonventionen veröffentlicht. Es empfiehlt sich, diese Konventionen zu befolgen, da es damit neuen Mitarbeitern erleichtert wird, sich schnell zurechtzufinden.
