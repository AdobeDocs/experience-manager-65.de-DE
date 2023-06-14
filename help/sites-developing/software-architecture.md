---
title: Software-Architektur
description: Best Practices für die Architektur Ihrer Software
uuid: a557f6ca-c3f1-486e-a45e-6e1f986fab41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 92971747-1c74-4917-b5a0-7b79b3ae1e68
exl-id: cd4f3b4c-5488-4ca7-9c1e-b4c819fda8e8
source-git-commit: 78c584db8c35ea809048580fe5b440a0b73c8eea
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 41%

---

# Software-Architektur{#software-architecture}

## Design für Upgrades {#design-for-upgrades}

Bei der Erweiterung der OOTB-Verhaltensweisen ist es wichtig, Upgrades zu berücksichtigen. Nehmen Sie Anpassungen immer im Verzeichnis /apps vor und überlagern Sie entweder die entsprechenden Knoten im Verzeichnis /libs oder verwenden Sie „sling:resourceSuperType“, um das Standardverhalten zu erweitern. Zwar können einige Änderungen erforderlich sein, um eine neue AEM zu unterstützen, doch sollte die neue Version Ihre Anpassungen nicht überschreiben, wenn diese Vorgehensweise befolgt wird.

### Wiederverwenden von Vorlagen und Komponenten, sofern möglich {#reuse-template-and-components-when-possible}

Auf diese Weise kann die Site ein konsistenteres Erscheinungsbild erhalten und die Codewartung vereinfachen. Wenn eine neue Vorlage benötigt wird, stellen Sie sicher, dass sie von einer gemeinsam verwendeten Basisvorlage erweitert wird, sodass globale Anforderungen wie die clientlib-Einbindung an zentraler Stelle kodiert werden können. Wenn eine neue Komponente benötigt wird, sollten Sie versuchen, eine bestehenden Komponente zu erweitern.

### Gestalten von Vorlagen-Designs {#design-template-designs}

Indem Sie die Komponenten definieren, die in den einzelnen Absatzsystemen auf der Seite enthalten sein können, können Sie Einfluss darauf nehmen, dass das Erscheinungsbild der Seite einheitlich ist. Durch das Beschränken des Zugriffs auf das Design auf Seiten können „Superautoren“ die zulässigen Komponenten je Seite ohne Unterstützung eines Entwicklers ändern und gleichzeitig sicherstellen, dass die anderen Autoren die Unternehmensstandards einhalten.

### Entwickeln einer SOLID-Architektur {#develop-a-solid-architecture}

SOLID ist ein Akronym, das fünf architektonische Prinzipien beschreibt, die beachtet werden sollten:

* **S** Single Responsibility-Prinzip - Jedes Modul, jede Klasse, jede Methode usw. sollte nur eine Verantwortung haben.
* **O** pen/Closed-Prinzip: Module sollten sowohl offen (für Erweiterungen) als auch geschlossen (für Änderungen) sein.
* **L** iskovsches Substitutionsprinzip: Typen sollten durch ihre Untertypen ersetzbar sein.
* **Interface Segregation-Prinzip:** Clients sollten nicht gezwungen werden, von Methoden abzuhängen, die sie nicht verwenden.
* **D** ependency Inversion-Prinzip: Module höherer Ebenen sollten nicht von Modulen niedriger Ebenen abhängig sein. Beide sollten von Abstraktionen abhängen. Abstraktionen sollten nicht von Details abhängig sein. Details sollten von Abstraktionen abhängen.

Das Streben nach Einhaltung dieser fünf Grundsätze sollte zu einem System führen, das eine strikte Trennung der Bedenken aufweist.

>[!TIP]
>
>SOLID ist ein häufig verwendetes Konzept für objektorientierte Programmierung und jedes Element wird in der Fachliteratur umfassend diskutiert.
>
>Diese Information ist nur eine kurze Zusammenfassung, die für das Bewusstsein präsentiert wird, und Sie sollten sich mit diesen Konzepten besser vertraut machen.

### Befolgen des Robustheitsgrundsatzes {#follow-the-robustness-principle}

Das Robustness-Prinzip besagt, dass Sie bei dem, was Sie senden, konservativ sein sollten, aber bei dem, was Sie akzeptieren, liberal sein sollten. Anders ausgedrückt: Wenn Sie Nachrichten an einen Drittanbieter senden, sollten Sie die Spezifikationen vollständig einhalten. Wenn Sie jedoch Nachrichten von einem Drittanbieter erhalten, sollten Sie nicht konforme Nachrichten akzeptieren, solange die Bedeutung der Nachricht klar ist.

### Implementierung von Sammlungen in eigenen Modulen {#implement-spikes-in-their-own-modules}

Spitzen und Testcode sind Teil jeder Agile Software-Implementierung. Sie möchten jedoch sicherstellen, dass sie nicht ohne angemessene Aufsicht in die Produktions-Code-Basis gelangen. Daher wird empfohlen, Spitzen in ihrem eigenen Modul zu erstellen.

### Implementieren von Datenmigrationsskripten in ihrem eigenen Modul {#implement-data-migration-scripts-in-their-own-module}

Datenmigrationsskripte werden während des Produktionscodes nur einmal beim ersten Start einer Site ausgeführt. Wenn die Site live ist, werden die Skripte daher zu totem Code. Um sicherzustellen, dass Sie keinen Implementierungscode erstellen, der von den Migrationsskripten abhängig ist, sollten diese in ihrem eigenen Modul implementiert werden. Auf diese Weise können wir diesen Code unmittelbar nach dem Start entfernen und zurücksetzen, wodurch toter Code aus dem System entfernt wird.

### Befolgen veröffentlichter Maven-Konventionen in POM-Dateien {#follow-published-maven-conventions-in-pom-files}

Apache hat unter [https://maven.apache.org/developers/conventions/code.html](https://maven.apache.org/developers/conventions/code.html) Stilkonventionen veröffentlicht. Es ist am besten, diese Konventionen zu befolgen, da es für neue Ressourcen einfacher ist, schnell zu arbeiten.
