---
title: 'Kodierungsrichtlinien '
seo-title: Coding Guidelines
description: Richtlinien, Tipps und Tricks für Communities-Entwickler
seo-description: Communities developer guidelines, tips, and tricks
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
exl-id: a23aab83-1dfa-4d91-9b6b-6246a2103896
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 3%

---

# Kodierungsrichtlinien  {#coding-guidelines}

## Richtlinien, Tipps und Tricks {#guidelines-tips-and-tricks}

Die Arbeit mit AEM Communities hat sich von der Abhängigkeit von Java-Serverseiten zu Flexibilität bei der Auswahl von Vorlagenskriptsprachen entwickelt, bei denen sich Geschäftslogik, Stil und Seiteninhalt voneinander unterscheiden.

Mehr Flexibilität bei der Arbeit mit benutzergenerierten Inhalten (UGC) erhalten Sie über die SocialResourceProvider-API, mit der Sie nicht mehr wissen müssen, welche Inhalte [SRP](srp.md) wurde für die Implementierung ausgewählt.

Im Folgenden finden Sie verschiedene Codierungsrichtlinien und Best Practices für AEM Communities-Entwickler:

### Code {#code}

* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md) - Wie vermeiden Sie das Schreiben einer Anwendung, die nur funktioniert, wenn UGC in JCR (JSRP) gespeichert ist.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Benennungskonventionen](naming-conventions.md) - Namenskonventionen für benutzerdefinierte Java-Klassen.

### Skripte {#scripts}

* [Sideloading von Communities-Komponenten](sideloading.md) - wie Sie eine Komponente dynamisch hinzufügen, nachdem die Seite geladen wurde.
* [Grundlagen zum Rich-Text-Editor](rte.md) - wie Sie die Rich-Text-Benutzeroberfläche anpassen, die Mitgliedern zum Posten von Inhalten bereitgestellt wird.

### IDE {#ide}

* [Verwenden von Maven für Communities](maven.md) - wie Sie die Communities-API-JAR einbinden.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
