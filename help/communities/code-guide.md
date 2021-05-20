---
title: 'Kodierungsrichtlinien '
seo-title: 'Kodierungsrichtlinien '
description: Richtlinien, Tipps und Tricks für Communities-Entwickler
seo-description: Richtlinien, Tipps und Tricks für Communities-Entwickler
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
exl-id: a23aab83-1dfa-4d91-9b6b-6246a2103896
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 4%

---

# Kodierungsrichtlinien {#coding-guidelines}

## Richtlinien, Tipps und Tricks {#guidelines-tips-and-tricks}

Die Arbeit mit AEM Communities hat sich von der Abhängigkeit von Java-Serverseiten zu Flexibilität bei der Auswahl von Vorlagenskriptsprachen entwickelt, bei denen sich Geschäftslogik, Stil und Seiteninhalt voneinander unterscheiden.

Die SocialResourceProvider-API ermöglicht eine größere Flexibilität bei der Arbeit mit benutzergenerierten Inhalten (UGC). So müssen Sie sich nicht mehr darüber im Klaren sein, welche Option [SRP](srp.md) für die Implementierung ausgewählt wurde.

Im Folgenden finden Sie verschiedene Codierungsrichtlinien und Best Practices für AEM Communities-Entwickler:

### Code {#code}

* [Zugreifen auf UGC mit SRP](accessing-ugc-with-srp.md)  - wie vermeiden Sie das Schreiben einer Anwendung, die nur funktioniert, wenn UGC in JCR (JSRP) gespeichert ist.
* [SocialUtils-Refaktorierung](socialutils.md)  - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Namenskonventionen](naming-conventions.md)  - Benennungskonventionen für benutzerdefinierte Java-Klassen.

### Skripte {#scripts}

* [Sideloading Communities Components](sideloading.md)  - wie Sie eine Komponente dynamisch hinzufügen, nachdem die Seite geladen wurde.
* [Rich-Text-Editor-Grundlagen](rte.md)  - wie Sie die Rich-Text-Benutzeroberfläche anpassen können, die Mitgliedern zum Posten von Inhalten bereitgestellt wird.

### IDE {#ide}

* [Verwenden von Maven für Communities](maven.md)  - wie Sie die Communities-API-JAR einbinden.
* [SocialUtils-Refaktorierung](socialutils.md)  - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
