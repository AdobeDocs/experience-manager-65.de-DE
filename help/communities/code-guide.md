---
title: Codierungsrichtlinien
description: Richtlinien, Tipps und Tricks für Communities-Entwickler
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: a23aab83-1dfa-4d91-9b6b-6246a2103896
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 3%

---

# Codierungsrichtlinien  {#coding-guidelines}

## Richtlinien, Tipps und Tricks {#guidelines-tips-and-tricks}

Die Arbeit mit AEM Communities hat sich von der Abhängigkeit von Java-Serverseiten zu Flexibilität bei der Auswahl von Vorlagenskriptsprachen entwickelt, bei denen sich Geschäftslogik, Stil und Seiteninhalt voneinander unterscheiden.

Die SocialResourceProvider-API ermöglicht eine größere Flexibilität bei der Arbeit mit benutzergenerierten Inhalten (UGC). So müssen Sie nicht mehr wissen, welche [SRP](srp.md)-Option für die Implementierung ausgewählt wurde.

Im Folgenden finden Sie verschiedene Codierungsrichtlinien und Best Practices für AEM Communities-Entwickler:

### Code {#code}

* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - wie vermeiden Sie das Schreiben einer Anwendung, die nur funktioniert, wenn UGC in JCR (JSRP) gespeichert ist.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Namenskonventionen](naming-conventions.md) - Namenskonventionen für benutzerdefinierte Java-Klassen.

### Skripte {#scripts}

* [Sideloading Communities Components](sideloading.md) - wie Sie eine Komponente dynamisch hinzufügen, nachdem die Seite geladen wurde.
* [Grundlagen des Rich-Text-Editors](rte.md) - So passen Sie die Rich-Text-Benutzeroberfläche an, die Mitgliedern zum Posten von Inhalten bereitgestellt wird.

### IDE {#ide}

* [Verwenden von Maven für Communities](maven.md) - wie die Communities-API-JAR eingeschlossen wird.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
