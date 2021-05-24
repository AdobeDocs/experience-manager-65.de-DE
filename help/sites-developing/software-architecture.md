---
title: Software-Architektur
seo-title: Software-Architektur
description: Best Practices für die Entwicklung der Architektur Ihrer Software
seo-description: Best Practices für die Entwicklung der Architektur Ihrer Software
uuid: a557f6ca-c3f1-486e-a45e-6e1f986fab41
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 92971747-1c74-4917-b5a0-7b79b3ae1e68
exl-id: cd4f3b4c-5488-4ca7-9c1e-b4c819fda8e8
source-git-commit: 423e17dadf2e506eb68b37851dde5e68ed950866
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 41%

---

# Software-Architektur{#software-architecture}

## Auslegen des Designs auf Upgrades {#design-for-upgrades}

Bei der Erweiterung der OOTB-Verhaltensweisen ist es wichtig, Upgrades zu berücksichtigen. Wenden Sie Anpassungen immer im Verzeichnis /apps an und überlagern Sie entweder über den entsprechenden Knoten im Verzeichnis /libs oder verwenden Sie sling:resourceSuperType , um das Standardverhalten zu erweitern. Zwar können Änderungen erforderlich sein, um neue AEM-Versionen zu unterstützen, doch die neue Version sollte Ihre Anpassungen nicht überschreiben, wenn diese Best Practice befolgt wird.

### Nach Möglichkeit Wiederverwenden von Vorlagen und Komponenten {#reuse-template-and-components-when-possible}

Dadurch lässt sich das Erscheinungsbild der Website vereinheitlichen und die Codepflege vereinfachen. Wenn eine neue Vorlage benötigt wird, stellen Sie sicher, dass sie von einer freigegebenen Basisvorlage erweitert wird, damit globale Anforderungen wie die clientlib-Einbindung an einem Ort kodiert werden können. Wenn eine neue Komponente benötigt wird, suchen Sie nach Möglichkeiten, um von einer vorhandenen Komponente zu erweitern.

### Gestalten von Vorlagendesigns {#design-template-designs}

Indem Sie die Komponenten definieren, die in den einzelnen Absatzsystemen auf der Seite enthalten sein können, können Sie Einfluss darauf nehmen, dass das Erscheinungsbild der Seite einheitlich ist. Durch die Beschränkung des Zugriffs auf das Design auf Seiten können &quot;Superautoren&quot;die zulässigen Komponenten pro Seite ändern, ohne dass die Entwickler eingreifen, und gleichzeitig sicherstellen, dass die anderen Autoren die Unternehmensstandards einhalten.

### Entwickeln von SOLID-Architekturen {#develop-a-solid-architecture}

SOLID ist ein Akronym, das fünf architektonische Prinzipien beschreibt, die Sie einhalten sollten:

* **** Grundsatz der einheitlichen Verantwortung - Jedes Modul, jede Klasse, jede Methode usw. sollte nur eine Verantwortung haben.
* **** Open/Closed Principle - Module sollten zur Erweiterung geöffnet und zur Änderung geschlossen sein.
* **** Liskov-Substitutionsprinzip - Typen sollten durch ihre Untertypen ersetzt werden können.
* **** Grundsatz der Schnittstellensegregation - kein Client sollte gezwungen sein, von nicht verwendeten Methoden abhängig zu sein.
* **** Abhängigkeits-Inversion-Prinzip - Module auf hoher Ebene sollten nicht von Modulen auf niedriger Ebene abhängig sein. Beide sollten von Abstraktionen abhängen. Abstraktionen sollten nicht von Details abhängen. Details sollten von Abstraktionen abhängen.

Durch die Berücksichtigung dieser fünf Prinzipien lässt sich ein System erzielen, in dem eine strikte Trennung der Anliegen gegeben ist.

>[!TIP]
>
>SOLID ist ein häufig verwendetes Konzept für objektorientierte Programmierung und jedes Element wird in der Fachliteratur umfassend diskutiert.
>
>Dies ist nur eine kurze Zusammenfassung für Bewusstsein und Sie werden ermutigt, sich mit diesen Konzepten vertiefen.

### Befolgen des Robustheitsgrundsatzes {#follow-the-robustness-principle}

Der Robustheitsgrundsatz besagt, dass Sie streng sein sollten, bei dem was Sie senden, und offen bei dem, was Sie von anderen akzeptieren. Mit anderen Worten, beim Versand von Nachrichten an einen Dritten sollten wir die Spezifikationen vollständig einhalten. Beim Empfang von Nachrichten eines Drittanbieters sollten wir jedoch nicht konforme Nachrichten akzeptieren, solange die Bedeutung der Nachricht klar ist.

### Implementierung von Sammlungen in eigenen Modulen {#implement-spikes-in-their-own-modules}

Sammlungen und Testcode sind ein integraler Bestandteil jeder agilen Software-Implementierung, allerdings sollten Sie sicherstellen, dass sie nicht ohne entsprechende Kontrolle in Ihre Produktionscodebasis gelangen. Daher wird empfohlen, Spitzen in ihrem eigenen Modul zu erstellen.

### Implementieren von Datenmigrationsskripten in ihrem eigenen Modul {#implement-data-migration-scripts-in-their-own-module}

Bei Datenmigrationsskripten handelt es sich zwar um Produktionscode, doch diese werden in der Regel nur einmal beim ersten Start einer Site ausgeführt. Sobald die Site live ist, wird dies daher toter Code. Um sicherzustellen, dass wir keinen Implementierungscode erstellen, der von den Migrationsskripten abhängig ist, sollten sie in ihrem eigenen Modul implementiert werden. Dies ermöglicht es uns auch, diesen Code unmittelbar nach dem Start zu entfernen und zu löschen, sodass toter Code aus dem System entfernt wird.

### Befolgen veröffentlichter Maven-Konventionen in POM-Dateien {#follow-published-maven-conventions-in-pom-files}

Apache hat Stilkonventionen unter [https://maven.apache.org/developers/conventions/code.html](https://maven.apache.org/developers/conventions/code.html) veröffentlicht. Es ist am besten, diese Konventionen zu befolgen, da sie es den neuen Ressourcen erleichtern werden, schnell zu arbeiten.
