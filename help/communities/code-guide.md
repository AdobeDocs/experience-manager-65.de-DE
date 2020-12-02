---
title: 'Kodierungsrichtlinien '
seo-title: 'Kodierungsrichtlinien '
description: Richtlinien, Tipps und Tricks für Community-Entwickler
seo-description: Richtlinien, Tipps und Tricks für Community-Entwickler
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 4%

---


# Kodierungsrichtlinien {#coding-guidelines}

## Richtlinien, Tipps und Tricks {#guidelines-tips-and-tricks}

Die Zusammenarbeit mit AEM Communities hat sich von der starken Abhängigkeit von Java Server Pages zur Flexibilität bei der Auswahl von Vorlagen für Skriptsprachen entwickelt, bei denen Geschäftslogik, Stil und Seiteninhalt sich voneinander unterscheiden.

Eine höhere Flexibilität beim Arbeiten mit benutzergenerierten Inhalten (UGC) ist über die SocialResourceProvider-API möglich. Dadurch müssen Sie nicht mehr wissen, welche Option [SRP](srp.md) für die Bereitstellung ausgewählt wurde.

Im Folgenden finden Sie verschiedene Richtlinien und Best Practices für die Codierung von AEM Communities-Entwicklern:

### Code {#code}

* [Zugriff auf UGC mit SRP](accessing-ugc-with-srp.md)  - Wie vermeiden Sie das Schreiben einer Anwendung, die nur funktioniert, wenn UGC in JCR (JSRP) gespeichert wird.
* [SocialUtils Refactoring](socialutils.md)  - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.
* [Benennungsregeln](naming-conventions.md)  - Benennungskonventionen für benutzerdefinierte Java-Klassen.

### Skripte {#scripts}

* [Sideloading Communities Components](sideloading.md)  - Anleitung zum dynamischen Hinzufügen einer Komponente nach dem Laden der Seite.
* [Rich Text Editor Essentials](rte.md)  - Anleitung zum Anpassen der Rich-Text-Benutzeroberfläche, die Mitgliedern zum Posten von Inhalten zur Verfügung gestellt wird.

### IDE {#ide}

* [Verwenden von Maven for Communities](maven.md)  - Anleitung zum Einbeziehen der Communities API-JARs.
* [SocialUtils Refactoring](socialutils.md)  - Dienstprogrammmethoden für SRP, die SocialUtils ersetzen.

