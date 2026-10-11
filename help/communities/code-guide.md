---
title: Codierungsrichtlinien
description: Entwicklerrichtlinien, Tipps und Tricks für Communities
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: a23aab83-1dfa-4d91-9b6b-6246a2103896
solution: Experience Manager
feature: Communities
role: Admin
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: b013f126-a97e-52d1-9f79-cb5bbb12114e
    internal-label: Communities
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
source-git-commit: 1880cdd6fa659c17e8efb3854b9b9441ff22c2b2
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 3%
---
# Codierungsrichtlinien {#coding-guidelines}

## Richtlinien, Tipps und Tricks {#guidelines-tips-and-tricks}

Die Arbeit mit AEM Communities hat sich von der starken Abhängigkeit von Java-Server-Seiten hin zu einer flexiblen Auswahl von Skriptsprachen entwickelt, bei denen Geschäftslogik, Stil und Seiteninhalte sich voneinander unterscheiden.

Eine weitere Flexibilität bei der Arbeit mit benutzergenerierten Inhalten (User Generated Content, UGC) wird durch die SocialResourceProvider-API erreicht, wodurch nicht mehr erkannt werden muss, welche [SRP](srp.md)-Option für die Bereitstellung ausgewählt wurde.

Im Folgenden finden Sie verschiedene Kodierungsrichtlinien und Best Practices für AEM Communities-Entwicklerinnen und -Entwickler:

### Code {#code}

* [Zugriff auf benutzergenerierten Inhalt mit SRP](accessing-ugc-with-srp.md) - wie Sie vermeiden können, eine Anwendung zu schreiben, die nur funktioniert, wenn benutzergenerierter Inhalt in JCR (JSRP) gespeichert wird.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Namenskonventionen](naming-conventions.md) - Namenskonventionen für benutzerdefinierte Java-Klassen.

### Skripte {#scripts}

* [Sideloading von Communities-](sideloading.md): Dynamisches Hinzufügen einer Komponente nach dem Laden der Seite.
* [Rich Text Editor Essentials](rte.md) - Anpassen der Rich-Text-Benutzeroberfläche, die Membern zum Posten von Inhalten bereitgestellt wird.

### IDE {#ide}

* [Verwenden von Maven für Communities](maven.md) - Einschließen der Communities-API-JAR-Datei.
* [SocialUtils-Refaktorierung](socialutils.md) - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
